# Quem Mente? — backlog priorizado

> A ordem existe para impedir que a gente comece por cosmético enquanto o Mentiroso ainda recebe o segredo por acidente.

## Fase 0 — fundação

- scaffold saudável;
- TypeScript estrito;
- CI;
- configuração local;
- Supabase CLI preparado;
- destino `auê-games` definido;
- documentação carregada;
- sem UI final antes do protótipo.

**Gate:** teste/typecheck/build aplicáveis verdes.

## Fase 1 — domínio e estado

- tipos de sala/jogador/rodada;
- máquina de estados;
- validação de início;
- seleção balanceada do Mentiroso;
- seleção de segredo;
- pontuação;
- testes unitários.

**Gate:** uma rodada inteira pode ser simulada sem interface.

## Fase 2 — schema e segurança

- migrations `qm_*`;
- RLS fechado;
- Auth anônimo;
- RPC criar sala;
- RPC entrar;
- RPC iniciar;
- RPC `get_my_role`;
- segredo/papel protegidos;
- testes de autorização.

**Gate:** Mentiroso não consegue consultar segredo e jogador não consegue consultar papel de outro.

## Fase 3 — pistas e votação

- enviar pista uma vez;
- fechar fase;
- liberar pistas no momento correto;
- discussão/timer;
- voto secreto;
- desempate;
- resolução;
- última chance;
- pontuação final.

**Gate:** rodada completa via chamadas/backend sem UI final.

## Fase 4 — conteúdo

- importar apenas segredos aprovados;
- categorias;
- dificuldade;
- evitar collision group repetido;
- seed repetível;
- playtest contínuo.

**Gate:** 40+ segredos aprovados.

## Fase 5 — realtime

- canal privado por sala;
- eventos pequenos;
- sincronização de fase;
- reconexão por snapshot;
- desconexão/abandono;
- transferência de host;
- nenhuma informação secreta no broadcast.

**Gate:** 4–6 clientes completam rodada com queda/reentrada sem corromper estado.

## Fase 6 — UI

Depende do protótipo aprovado.

- home;
- criar/entrar;
- lobby;
- papel secreto;
- pista;
- discussão;
- voto;
- segundo turno;
- revelação;
- última chance;
- pontuação;
- ranking final;
- revanche.

**Gate:** grupo novo joga sem alguém narrar o aplicativo.

## Fase 7 — analytics baseline

- funil da sala;
- convite;
- formação;
- abandono por fase;
- conclusão;
- revanche;
- convidado → host;
- sem anúncio.

## Fase 8 — segurança/legal/lançamento

- moderação mínima;
- XSS;
- rate limits;
- Turnstile quando necessário;
- privacidade/termos;
- idade/classificação;
- expiração/limpeza;
- checklist de produção.

## Fase 9 — beta público

- 3 grupos conhecidos;
- 10–30 salas reais;
- medir formação/conclusão/revanche;
- calibrar conteúdo;
- corrigir problemas de estado;
- zero mídia paga.

## Fase 10 — monetização experimental

Somente depois de baseline.

- um ponto natural de anúncio entre partidas/resultado;
- medir impacto na revanche;
- bloquear categorias inadequadas;
- sem ads comportamentais para menores;
- opção futura sem anúncios.

## Depois — se os dados pedirem

- modo Caos;
- desafios personalizados;
- packs especiais;
- histórico;
- conta permanente;
- estatísticas;
- temas pagos;
- pacote +18 com revisão separada.

## Fora até segunda ordem

- chat;
- DM;
- voz/vídeo;
- feed;
- seguidores;
- clan;
- moeda;
- loot box;
- aposta;
- IA gerando segredo ao vivo;
- avatar 3D;
- serviço pago antes de receita.

## Regra de prioridade

Nova ideia só fura fila se:

1. ajuda formar sala;
2. melhora conclusão;
3. aumenta revanche;
4. aumenta convite/convidado → host;
5. resolve segurança/integridade;
6. ajuda receita sem destruir os anteriores.

Senão vai pro estacionamento.