# Quem Mente? — checklist de produção e lançamento

> Sala funcionando em dois celulares não é produção. Produção é o jogo sobreviver quando quatro amigos fazem tudo fora da ordem enquanto um cai da internet.

## 1. Produto

- [ ] criar sala;
- [ ] entrar por link/código;
- [ ] nickname simples;
- [ ] host configurando partida;
- [ ] distribuição de papel;
- [ ] segredo protegido;
- [ ] pista;
- [ ] discussão;
- [ ] votação;
- [ ] desempate;
- [ ] revelação;
- [ ] última chance do Mentiroso;
- [ ] pontuação;
- [ ] próxima rodada;
- [ ] ranking final;
- [ ] revanche;
- [ ] transferência de host;
- [ ] reconexão.

## 2. Conteúdo

- [ ] 40+ segredos aprovados por playtest;
- [ ] categorias equilibradas;
- [ ] nenhum `candidate` publicado automaticamente;
- [ ] segredos ambíguos removidos;
- [ ] `forbidden_clues` revisados;
- [ ] colisões evitadas dentro da mesma partida;
- [ ] pacote base sem conteúdo +18.

## 3. Backend

- [ ] Supabase correto: 20T reaproveitado como `auê-games`;
- [ ] auditoria antes de migration destrutiva;
- [ ] migrations rastreáveis;
- [ ] RLS completo;
- [ ] Auth anônimo;
- [ ] RPC de papel individual;
- [ ] segredo nunca vazando ao Mentiroso;
- [ ] votação autoritativa;
- [ ] segundo turno autoritativo;
- [ ] pontuação autoritativa;
- [ ] sala expira;
- [ ] host transferível;
- [ ] reconexão não duplica jogador.

## 4. Realtime

- [ ] um canal por sala;
- [ ] nenhum segredo em broadcast;
- [ ] nenhum voto individual antes da revelação;
- [ ] eventos pequenos;
- [ ] canal fechado ao sair;
- [ ] snapshot correto na reconexão;
- [ ] teste com 4–6 dispositivos reais;
- [ ] quota observável.

## 5. Frontend/PWA

- [ ] mobile-first;
- [ ] Safari iPhone;
- [ ] Chrome Android;
- [ ] Chrome/Edge desktop básico;
- [ ] estados de espera claros;
- [ ] timer robusto a aba em background;
- [ ] loading/erro/reconexão;
- [ ] Open Graph do convite;
- [ ] link de sala funciona ao abrir do WhatsApp;
- [ ] PWA manifest/ícones;
- [ ] sem UI de debug em produção.

## 6. Moderação e segurança

Executar `docs/seguranca-idade-e-moderacao.md` integralmente.

- [ ] nickname filtrado;
- [ ] pista escapada contra XSS;
- [ ] texto do jogador sem HTML;
- [ ] host pode remover abuso no lobby;
- [ ] rate limits;
- [ ] tentativa de consultar segredo via DevTools falha;
- [ ] tentativa de consultar votação parcial falha;
- [ ] tentativa de votar duas vezes falha.

## 7. Legal/privacidade

- [ ] controlador e contato;
- [ ] privacidade pública;
- [ ] termos públicos;
- [ ] política de conteúdo/moderação mínima;
- [ ] retenção definida;
- [ ] exclusão/direitos;
- [ ] idade/classificação revisadas conforme regra vigente;
- [ ] fornecedores listados;
- [ ] publicidade desligada no baseline;
- [ ] revisão jurídica antes de escala/ads.

## 8. Analytics

- [ ] funil `room_created → invite_shared → room_joined → game_started → game_completed → rematch_started`;
- [ ] `invite_opened → room_joined` medido;
- [ ] convidado → host medido;
- [ ] sem nickname/pista nos eventos;
- [ ] abandono por fase;
- [ ] duração de formação da sala;
- [ ] taxa de conclusão;
- [ ] taxa de revanche.

## 9. Infra zero-custo

- [ ] Cloudflare Pages Free;
- [ ] Supabase Free;
- [ ] nenhum websocket pago externo;
- [ ] nenhum storage de mídia;
- [ ] nenhum serviço pago automático;
- [ ] realtime econômico;
- [ ] quota acompanhada;
- [ ] domínio próprio não bloqueia lançamento.

## 10. Círculos de teste

### Círculo 1 — equipe/primos

Objetivo: quebrar regra e estado.

### Círculo 2 — 3 grupos conhecidos

Objetivo: jogar sem ninguém explicar a interface.

### Círculo 3 — 10 a 30 salas reais

Objetivo: entender formação, conclusão e revanche.

Só depois abrir divulgação ampla.

## 11. Gate de lançamento público

Não lançar se:

- Mentiroso consegue descobrir segredo pelo cliente;
- votação parcial vaza;
- partida trava em reconexão;
- host derruba sala ao sair;
- pista permite XSS;
- legal/privacidade básico ausente;
- analytics principal não funciona;
- conteúdo ainda não passou playtest;
- infraestrutura exige gasto não aprovado.

## 12. Primeiras 72 horas

Observar:

- salas criadas que nunca chegam a 3 pessoas;
- tempo para formar sala;
- abandono por fase;
- Mentiroso ganhando/perdendo demais;
- pistas denunciadas;
- revanche;
- convite convertido;
- convidado virando host;
- consumo realtime.

## 13. Regra final

A primeira missão do lançamento é provar que um grupo consegue entrar, rir, terminar e querer outra. O resto pode esperar.