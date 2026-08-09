# Quem Mente? — modelo de dados

> Banco serve para sustentar a mentira do jogo. Não para vazar o segredo e estragar a brincadeira.

## 1. Princípios

- tudo deste jogo usa prefixo `qm_`;
- IDs em UUID;
- timestamps em UTC;
- RLS em toda tabela exposta;
- `auth.users.id` identifica tecnicamente o jogador;
- nickname é só identidade social da sala;
- segredo, papel e votação parcial são protegidos;
- pontuação é calculada pelo servidor;
- sala e dados transitórios expiram.

## 2. `qm_categories`

Categorias dos segredos.

Campos:

- `id uuid pk`
- `slug text unique not null`
- `name text not null`
- `description text null`
- `is_active boolean default true`
- `sort_order int default 0`
- `created_at timestamptz`
- `updated_at timestamptz`

## 3. `qm_secrets`

Conteúdo jogável.

Campos:

- `id uuid pk`
- `category_id uuid fk qm_categories not null`
- `secret text not null`
- `difficulty text not null` — `easy | medium | hard`
- `forbidden_clues text[] null`
- `status text not null` — `draft | published | disabled`
- `version int default 1`
- `created_at timestamptz`
- `updated_at timestamptz`

Regras:

- segredo publicado precisa de categoria ativa;
- segredo desativado não entra em nova rodada;
- `forbidden_clues` não precisa bloquear automaticamente no MVP, mas ajuda moderação/editorial e futuros avisos.

## 4. `qm_rooms`

Sala multiplayer.

Campos:

- `id uuid pk`
- `code text unique not null`
- `host_user_id uuid not null`
- `status text not null` — `lobby | playing | finished | expired`
- `round_count int not null`
- `clue_time_seconds int not null`
- `discussion_time_seconds int null`
- `voting_time_seconds int not null`
- `category_filter jsonb null`
- `current_round_index int default 0`
- `created_at timestamptz`
- `started_at timestamptz null`
- `finished_at timestamptz null`
- `expires_at timestamptz not null`

Regras:

- mínimo de 3 jogadores para iniciar;
- host precisa ser membro ativo;
- configurações só mudam em `lobby`;
- sala expirada não aceita nova ação de jogo.

## 5. `qm_room_players`

Participantes da sala.

Campos:

- `id uuid pk`
- `room_id uuid fk qm_rooms not null`
- `user_id uuid not null`
- `nickname text not null`
- `score int default 0`
- `liar_count int default 0`
- `correct_votes int default 0`
- `liar_wins int default 0`
- `joined_at timestamptz`
- `last_seen_at timestamptz`
- `left_at timestamptz null`
- `status text` — `active | disconnected | left`

Índices/regras:

- unique `(room_id, user_id)`;
- score e estatísticas não podem ser alterados pelo cliente;
- apelido curto e validado.

## 6. `qm_rounds`

Coração de cada rodada.

Campos:

- `id uuid pk`
- `room_id uuid fk qm_rooms not null`
- `round_index int not null`
- `secret_id uuid fk qm_secrets not null`
- `liar_player_id uuid fk qm_room_players not null`
- `status text not null`
- `clue_deadline timestamptz null`
- `discussion_deadline timestamptz null`
- `voting_deadline timestamptz null`
- `liar_guess_deadline timestamptz null`
- `created_at timestamptz`
- `finished_at timestamptz null`

Estados sugeridos:

- `role_reveal`
- `clue_submission`
- `discussion`
- `voting`
- `runoff_voting`
- `reveal`
- `liar_guess`
- `scoring`
- `finished`

Regra importantíssima:

`secret_id` e `liar_player_id` não são campos de leitura pública para membros da sala durante a rodada.

## 7. `qm_clues`

Pistas enviadas pelos jogadores.

Campos:

- `id uuid pk`
- `round_id uuid fk qm_rounds not null`
- `player_id uuid fk qm_room_players not null`
- `clue_text text not null`
- `submitted_at timestamptz not null`
- `status text default 'submitted'`

Regras:

- unique `(round_id, player_id)`;
- limite de caracteres;
- depois de confirmada, pista não muda;
- antes da fase de revelação, membros podem saber quem já respondeu sem necessariamente ler o texto dos outros.

## 8. `qm_votes`

Votos secretos.

Campos:

- `id uuid pk`
- `round_id uuid fk qm_rounds not null`
- `voter_player_id uuid fk qm_room_players not null`
- `target_player_id uuid fk qm_room_players not null`
- `stage int not null default 1`
- `submitted_at timestamptz not null`

Regras:

- unique `(round_id, voter_player_id, stage)`;
- jogador não vota em si mesmo;
- alvo precisa estar elegível na fase;
- no desempate, opções ficam limitadas aos empatados;
- voto parcial nunca é exposto antes do fechamento.

## 9. `qm_liar_guesses`

Tentativa final do Mentiroso quando descoberto.

Campos:

- `id uuid pk`
- `round_id uuid fk qm_rounds unique not null`
- `player_id uuid fk qm_room_players not null`
- `guess_text text not null`
- `submitted_at timestamptz not null`
- `is_correct boolean null`

Regras:

- somente `liar_player_id` pode inserir;
- somente na fase `liar_guess`;
- `is_correct` é definido pelo servidor.

## 10. Resultado da rodada

Não precisamos obrigatoriamente de tabela própria no MVP.

O resultado pode ser derivado e refletido em:

- estado final de `qm_rounds`;
- score e estatísticas em `qm_room_players`;
- votos e tentativa final já persistidos.

Se depois precisarmos de histórico rápido ou compartilhamento assíncrono, podemos adicionar `qm_round_results`.

Não criar antes da necessidade.

## 11. Analytics mínimo

Se usarmos analytics próprio:

### `qm_events`

- `id bigint generated`
- `user_id uuid null`
- `session_id uuid null`
- `room_id uuid null`
- `event_name text not null`
- `metadata jsonb null`
- `created_at timestamptz`

Eventos úteis:

- `game_opened`
- `room_created`
- `room_joined`
- `game_started`
- `round_finished`
- `game_finished`
- `rematch_started`
- `share_clicked`
- `invite_opened`

Não precisamos registrar `vote_button_hovered`. Ninguém merece.

## 12. Relações principais

```text
auth.users
   |
   +---- qm_room_players ---- qm_rooms
             |                   |
             |                   +---- qm_rounds ---- qm_secrets ---- qm_categories
             |                         |
             |                         +---- qm_clues
             |                         +---- qm_votes
             |                         +---- qm_liar_guesses
             |
             +---- score/estatísticas da partida
```

## 13. RLS — o que cada um enxerga

### Sala

Membro pode ler sala da qual participa.

Host pode alterar apenas configurações permitidas no lobby.

### Participantes

Membros da sala podem ver nickname, estado e score permitido.

### Segredos

A tabela `qm_secrets` não deve ter leitura ampla pelos jogadores durante a partida.

Acesso jogável acontece por RPC individualizada.

### Rodada

Campos públicos de fase podem ser lidos pelos membros.

`secret_id` e `liar_player_id` precisam ficar protegidos até a revelação.

Uma forma segura é não expor a tabela crua ao cliente e fornecer views/RPCs com payload específico.

### Pistas

Texto fica disponível conforme a fase.

### Votos

Jogador pode confirmar que o próprio voto existe, mas não consultar votos dos outros até a revelação.

## 14. Funções/RPC necessárias

Contratos conceituais:

- `qm_create_room(config, nickname)`
- `qm_join_room(code, nickname)`
- `qm_start_game(room_id)`
- `qm_start_round(room_id)`
- `qm_get_my_role(round_id)`
- `qm_submit_clue(round_id, clue)`
- `qm_begin_discussion(round_id)`
- `qm_begin_voting(round_id)`
- `qm_submit_vote(round_id, target_player_id, stage)`
- `qm_resolve_voting(round_id)`
- `qm_submit_liar_guess(round_id, guess)`
- `qm_score_round(round_id)`
- `qm_advance_round(room_id)`
- `qm_finish_game(room_id)`
- `qm_transfer_host(room_id, new_host_user_id)`

## 15. Vazamento de segredo: regra absoluta

Nenhuma query usada pelo frontend antes da revelação pode retornar simultaneamente:

- segredo;
- Mentiroso;
- todos os votos.

Nem em campo “interno”.
Nem em metadata.
Nem escondido no HTML.
Nem num preload esperto.

O dado que o jogador não pode saber não deve chegar ao dispositivo dele.

## 16. Limpeza

Sugestão inicial:

- sala não iniciada: expira em 6 horas;
- sala finalizada: manter até 7 dias se útil para resultado/revanche;
- pistas/votos de partidas antigas podem ser apagados ou agregados depois do período necessário;
- analytics bruto: retenção curta;
- contas anônimas sem uso: limpeza periódica conforme política do projeto.

## 17. Dados que não entram

No MVP não guardamos:

- áudio da discussão;
- vídeo;
- contatos do celular;
- localização precisa;
- typing indicator histórico;
- snapshot da sala a cada segundo;
- “sentimento” do jogador calculado por IA;
- qualquer outra maluquice que não ajude a rodada.

## 18. Regra final

O modelo está bom quando consegue responder três perguntas sem vazar merda:

1. quem está na sala?
2. em que fase estamos?
3. o que ESTE jogador tem permissão de saber agora?

Se resolver isso, o resto é placar e zoação.