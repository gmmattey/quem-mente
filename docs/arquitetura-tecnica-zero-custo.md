# Quem Mente? — arquitetura técnica zero-custo

> Esse jogo precisa de gente desconfiando de gente. Não de servidor caro desconfiando do nosso cartão.

## 1. Objetivo

Construir o Quem Mente? como WebApp/PWA multiplayer sem custo recorrente obrigatório antes de existir receita.

O jogo depende mais de realtime que o Na Mosca, então aqui economia não significa desligar recurso importante. Significa usar o mínimo necessário de forma inteligente.

## 2. Stack escolhida

### Frontend

- React + TypeScript + Vite.
- WebApp/PWA mobile-first.
- Cloudflare Pages.
- `quem-mente.pages.dev` no começo.

### Backend, banco e realtime

- Supabase Free.
- o projeto Supabase hoje identificado como **20T será reaproveitado como projeto compartilhado dos jogos**.
- não criar um projeto Supabase novo para o Quem Mente?.
- tudo deste jogo com prefixo `qm_`.
- Supabase Auth com login anônimo.
- Postgres.
- Supabase Realtime com canal privado por sala.
- RLS em toda tabela exposta.
- funções Postgres/RPC para segredo, papel, votação, resolução e pontuação.

### Proteção contra abuso

- Cloudflare Turnstile no login anônimo e criação de sala quando necessário.
- rate limit em criação/entrada repetitiva.

## 3. O que fica no Cloudflare Pages

Praticamente toda a interface.

Pages entrega:

- home;
- lobby;
- tela de papel;
- pista;
- discussão;
- votação;
- revelação;
- placar;
- assets do PWA.

Não existe servidor React rodando 24 horas.

O navegador conversa com Supabase para identidade, comandos e realtime.

## 4. O que NÃO pode ficar confiado ao frontend

Aqui está a parte delicada.

O navegador não pode decidir:

- quem é o Mentiroso;
- qual é o segredo;
- se alguém pode enxergar o segredo;
- contagem final dos votos;
- se houve empate;
- pontuação;
- se o palpite final do Mentiroso está correto.

Se tudo isso vier num JSON escondido e a UI só “não mostrar”, qualquer curioso abre o DevTools e mata o jogo.

Portanto, informação secreta é entregue individualmente por RPC conforme a identidade autenticada.

## 5. Supabase compartilhado — o 20T vira a base dos jogos

O projeto Supabase 20T passa a ser a infraestrutura física compartilhada dos jogos.

Nome lógico desejado para essa função:

`buildea-games`

Isso não significa criar outro projeto. Significa reaproveitar o Supabase existente do 20T e conectar os jogos a ele quando o desenvolvimento começar.

Tabelas do Quem Mente?:

- `qm_categories`
- `qm_secrets`
- `qm_rooms`
- `qm_room_players`
- `qm_rounds`
- `qm_clues`
- `qm_votes`

O Na Mosca usa `nm_`.

Mesmo banco físico, regras e políticas separadas.

### Antes de mexer no 20T

A substituição é intencional, mas não é licença para sair apagando coisa na marra.

Antes de qualquer limpeza, deve existir uma auditoria única do projeto Supabase 20T cobrindo:

- tabelas;
- funções/RPCs;
- policies RLS;
- Edge Functions;
- Storage;
- usuários Auth;
- secrets e integrações;
- dependências externas ainda apontando para o projeto.

O que estiver comprovadamente sem uso pode ser removido por migration. O que ainda tiver dependência precisa ser resolvido antes.

A meta é **reaproveitar o projeto 20T, não criar um terceiro Supabase e também não demolir nada no escuro**.

## 6. Identidade sem cadastro chato

Ao entrar/criar sala, o app garante uma sessão anônima no Supabase.

Cada pessoa ganha um `auth.users.id`.

Isso resolve:

- jogador único;
- RLS;
- papel individual;
- voto único;
- reconexão;
- transferência de host.

O apelido continua sendo só a identidade social dentro da sala.

Ninguém precisa fornecer email para acusar o primo de mentiroso.

## 7. Canal realtime por sala

Cada sala mantém um canal privado:

`room:qm:<room_id>`

Eventos pequenos:

- jogador entrou;
- jogador saiu/desconectou;
- partida começou;
- papéis disponíveis;
- pista enviada;
- todas as pistas prontas;
- discussão começou;
- votação começou;
- voto registrado;
- votação fechou;
- revelação disponível;
- pontuação atualizada;
- próxima rodada;
- partida terminou.

Nunca transmitir pelo broadcast:

- segredo;
- papel individual;
- voto individual antes da revelação;
- tentativa final do Mentiroso antes da resolução.

## 8. Papel e segredo

Quando a rodada começa, o servidor escolhe:

- `secret_id`;
- `liar_player_id`.

Esses campos ficam protegidos.

Cada jogador chama uma operação equivalente a:

`qm_get_my_role(round_id)`

Se for comum, recebe:

```text
role: common
secret: Praia
category: Lugar
```

Se for Mentiroso:

```text
role: liar
secret: null
category: Lugar
```

Ele não recebe o segredo escondido no payload. Nem base64, nem CSS `display:none`, nem outra genialidade desse tipo.

## 9. Pistas

Cada jogador envia uma pista uma vez.

A pista é persistida em `qm_clues`.

Enquanto a fase não fechar, o sistema pode mostrar apenas estado de envio, não necessariamente o texto das pistas dos outros.

Quando todos enviarem ou o tempo acabar, o servidor muda a fase e libera a revelação das pistas.

Nada de realtime a cada caractere digitado.

## 10. Discussão

A discussão é social e acontece fora do app: presencialmente ou por chamada.

O backend só controla:

- início da fase;
- deadline, se houver;
- transição para votação.

Não precisamos criar chat, áudio ou vídeo para resolver algo que a boca humana já faz de graça.

## 11. Votação secreta

Cada jogador envia um voto em `qm_votes` por operação autoritativa.

Antes do fechamento:

- cada jogador pode saber que o próprio voto foi aceito;
- ninguém vê quem votou em quem;
- ninguém vê parcial da votação.

Mostrar parcial é destruir a graça e incentivar voto estratégico.

Quando todos votarem ou o prazo encerrar, o servidor resolve.

## 12. Empate

O servidor calcula empate.

Se houver empate inicial:

- cria estado `runoff_voting`;
- limita opções aos empatados;
- registra uma segunda votação separada ou com `vote_stage`;
- se empatar novamente, Mentiroso sobrevive.

A UI apenas apresenta as opções válidas que o backend devolveu.

## 13. Última chance do Mentiroso

Se o Mentiroso for descoberto, ele recebe a fase `liar_guess`.

Somente o Mentiroso pode enviar a tentativa.

O servidor compara com o segredo real e decide:

- acertou;
- errou;
- expirou.

Não mandar lista completa de segredos para o cliente para ele “escolher”. Se um dia usarmos múltipla escolha, as alternativas devem ser montadas pelo servidor.

## 14. Pontuação

A pontuação é calculada no backend/RPC no fechamento da rodada.

Jogador não envia pontos.

Nunca existe endpoint do tipo:

```json
{ "score": 5000 }
```

porque isso é basicamente colocar uma placa “roube aqui”.

## 15. Balanceamento do Mentiroso

A escolha do papel considera histórico da partida.

Regra inicial:

- priorizar quem ainda não foi Mentiroso;
- evitar repetição consecutiva;
- usar aleatoriedade dentro dos elegíveis.

Isso acontece no servidor.

Não depende da interface.

## 16. Reconexão

A sala não é a conexão WebSocket.

Se o jogador cair:

- registro do participante continua;
- ao voltar com o mesmo `user_id`, recupera o mesmo lugar;
- recebe apenas o estado atual permitido;
- não ganha novo voto;
- não vira outro jogador;
- se a rodada ainda permitir, continua.

Se o host sair definitivamente, a função de host passa para outro participante ativo.

## 17. Realtime com economia

Como esse jogo vive em sala, precisamos vigiar quota.

Regras:

- um canal privado por sala;
- desconectar canal ao sair;
- eventos discretos de fase;
- nada de typing indicator;
- nada de heartbeat nosso além do que a própria plataforma já exige;
- presença só se realmente necessária;
- buscar snapshot da sala ao reconectar em vez de tentar reproduzir todos os eventos perdidos.

## 18. Conteúdo

Segredos e categorias ficam no banco.

O conteúdo precisa poder ser:

- criado;
- revisado;
- publicado;
- desativado;
- marcado por dificuldade;
- associado a termos/pistas óbvias quando necessário.

Sem redeploy para corrigir um segredo ruim.

## 19. Custos proibidos no MVP

- Vercel Pro;
- Supabase Pro;
- servidor VPS;
- Redis pago;
- serviço de websocket adicional;
- banco separado só para este jogo;
- IA por rodada;
- chat/voz/vídeo hospedado;
- observabilidade paga;
- domínio obrigatório.

## 20. Limites gratuitos considerados

Premissas validadas em agosto de 2026:

- Cloudflare Pages Free: 500 builds/mês; requests de assets estáticos gratuitos.
- Workers Free, se algum endpoint futuro precisar: 100 mil requests/dia.
- Supabase Free: 2 projetos ativos, 500 MB de banco, 50 mil MAU, 5 GB de egress, 2 milhões de mensagens realtime/mês e 200 conexões simultâneas de pico.

Quem Mente? precisa ser especialmente econômico em realtime.

## 21. Se a quota apertar

A ordem é:

1. medir salas e mensagens por partida;
2. remover evento redundante;
3. fechar canais abandonados;
4. reduzir presença;
5. expirar salas antigas;
6. limitar abuso;
7. somente depois discutir upgrade.

Bater limite com salas reais cheias é um problema bom. Bater limite porque mandamos websocket a cada letra digitada é incompetência.

## 22. Deploy e migrations

`main` publica no Cloudflare Pages.

Schema e funções do Supabase vivem em migrations versionadas no Git.

O vínculo via `supabase link` fica para quando o desenvolvimento começar. Nesse momento, tanto o Quem Mente? quanto o Na Mosca devem apontar para o **mesmo projeto Supabase reaproveitado do 20T**.

Regra importante:

- frontend pode evoluir rápido;
- mudança de schema e regra de jogo precisa ser rastreável.

## 23. Regra final

O jogo só precisa de três coisas técnicas para funcionar bem: segredo protegido, estado sincronizado e regra autoritativa.

O projeto Supabase usado será o **20T reaproveitado como base compartilhada dos jogos**, não um projeto novo.

Se conseguirmos isso com R$ 0 adicional, ganhamos o direito de descobrir se alguém quer jogar antes de descobrir se alguém quer nos cobrar.