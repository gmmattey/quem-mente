# Quem Mente? — analytics e métricas

> O dado mais importante não é quantos abriram o site. É quantos conseguiram juntar gente, terminar uma partida e falar “mais uma”.

## 1. Perguntas que os dados precisam responder

1. quem cria sala consegue colocar gente dentro?
2. a sala começa ou morre esperando?
3. a partida termina?
4. a rodada gera participação de todo mundo?
5. o grupo pede revanche?
6. convite traz jogador novo?
7. quem entrou por convite depois cria a própria sala?
8. anúncio, quando existir, derruba a revanche?

## 2. Eventos mínimos

### Entrada e sala

- `game_opened`
- `room_created`
- `invite_shared`
- `invite_opened`
- `room_joined`
- `room_left`
- `room_start_attempted`
- `game_started`

### Rodada

- `round_started`
- `role_viewed`
- `clue_submitted`
- `discussion_started`
- `vote_submitted`
- `vote_resolved`
- `liar_guess_submitted`
- `round_completed`

### Partida

- `game_completed`
- `rematch_started`
- `result_shared`

## 3. Campos úteis

Sem nome nem nickname no analytics.

Campos técnicos suficientes:

- `session_id`
- `room_id`
- `player_count`
- `round_number`
- `round_count`
- `category`
- `difficulty`
- `is_liar`
- `liar_survived`
- `liar_guessed_secret`
- `elapsed_seconds`
- `entry_source`

Evitar armazenar texto das pistas no analytics. A pista pertence à partida, não ao painel de métricas.

## 4. Funil principal

`room_created → invite_shared → room_joined → game_started → game_completed → rematch_started`

Esse é o coração do produto.

## 5. Métricas de formação da sala

### Conversão de convite

`room_joined via invite / invite_opened`

### Sala formada

Percentual de salas que chegam a pelo menos 3 jogadores.

### Sala iniciada

`game_started / salas com 3+ jogadores`

### Tempo para formar sala

Tempo entre `room_created` e `game_started`.

Se demora demais, o problema pode não ser a mecânica — pode ser só fricção de convite.

## 6. Métricas de partida

- taxa de conclusão;
- duração média;
- abandono por fase;
- rodadas concluídas por partida;
- taxa de revanche;
- jogadores médios por sala;
- reconexões;
- rodadas canceladas por abandono.

## 7. Métricas de mecânica

Por segredo/categoria:

- Mentiroso sobreviveu?;
- Mentiroso foi descoberto?;
- Mentiroso acertou a palavra na última chance?;
- quantos jogadores votaram corretamente?;
- rodada terminou em segundo turno?;
- rodada terminou em empate duplo?;
- tempo médio de envio de pista;
- abandono associado ao segredo.

Esses dados ajudam o conteúdo editorial.

## 8. Equilíbrio do Mentiroso

Não buscamos 50/50 perfeito em toda palavra.

Mas acompanhar globalmente:

- taxa de vitória do Mentiroso;
- taxa de descoberta;
- taxa de acerto na última chance.

Se o Mentiroso perde quase todas, comuns podem estar entregando demais ou a categoria está estreita.

Se ganha quase todas, pode estar fácil blefar demais.

Primeiro alvo de observação, não regra rígida:

- vitória final do Mentiroso entre 30% e 60% pode indicar tensão saudável;
- fora disso, investigar conteúdo e dinâmica antes de mudar pontuação.

## 9. Viralidade

Acompanhar:

- convites por sala;
- aberturas por convite;
- entradas por convite;
- novos usuários que vieram de convite;
- usuários convidados que depois criam outra sala.

Essa última métrica é ouro:

`convidado → host`

Ela mostra propagação real.

## 10. Metas iniciais — hipóteses

Só avaliar com volume mínimo.

Após pelo menos 50 salas com 3+ participantes:

### Verde

- >= 70% das salas formadas iniciam partida;
- >= 70% das partidas iniciadas terminam;
- revanche >= 30%;
- pelo menos 10% dos hosts compartilham resultado além do convite obrigatório/social.

### Amarelo

- início 50–69%;
- conclusão 50–69%;
- revanche 15–29%.

### Vermelho

- menos de metade das salas formadas inicia;
- menos de metade das partidas termina;
- revanche < 15%.

Antes de matar o jogo, descobrir qual fase está quebrando.

## 11. Métrica de diversão indireta

Não dá para medir risada pelo Supabase sem transformar o jogo num laboratório bizarro.

Usar proxies:

- revanche;
- número de partidas consecutivas da mesma sala;
- compartilhamento;
- retorno do host;
- convidado que vira host;
- tempo de permanência sem abandono.

Playtest qualitativo continua obrigatório.

## 12. Continua / muda / congela

### Continua

Salas formam, partidas terminam, existe revanche e convite gera novas salas.

### Muda

Existe vontade de jogar, mas uma etapa específica atrapalha: convite, papel, pista, votação, tempo, conteúdo etc.

### Congela

Depois de corrigir fricções reais, grupos entendem a mecânica mas raramente pedem revanche ou criam outra sala.

## 13. Privacidade

Não enviar para analytics:

- nickname;
- texto da pista;
- conversa do grupo;
- palavra secreta em evento genérico de terceiros;
- email;
- dado pessoal desnecessário.

Usar IDs técnicos e agregação.

## 14. Implementação inicial

Sem SaaS pago.

Pode começar com eventos controlados no `auê-games` e métricas gratuitas da infraestrutura.

Cuidado especial: Quem Mente? já consome realtime. Analytics não pode duplicar todo evento de sala e torrar quota só para fazer gráfico bonito.

## 15. Dashboard mínimo

Mostrar:

- salas criadas;
- salas formadas;
- partidas iniciadas;
- partidas concluídas;
- conclusão;
- revanche;
- jogadores por sala;
- conversão de convite;
- convidado → host;
- taxa de vitória do Mentiroso;
- erros técnicos;
- receita quando existir.

O resto entra quando houver uma pergunta concreta para responder.