# Workflow GOAS — De Migué

Quando a demanda pedir `GOAS`, executar este fluxo sem pular etapa.

## 1. Giam — plano

1. Ler `AGENTS.md` e fontes canônicas da demanda.
2. Fixar comportamento, fase da rodada e o que fica fora.
3. Definir requisitos de aceite verificáveis.
4. Se houver UI: usar jornada, identidade, regras anti-IA e protótipo aprovado.
5. Definir arquitetura, autorização, realtime e impactos Web/Android/iOS.
6. Não perguntar decisão técnica pequena ao primo.

Parar somente por condição real descrita em `AGENTS.md`.

## 2. Guinho — implementação

1. Sincronizar base limpa.
2. Trabalhar em branch/worktree isolada quando fizer mudança real.
3. Implementar uma fatia vertical completa.
4. Backend continua autoritativo para papel, segredo, fase, voto, score e resultado.
5. Nunca mandar segredo para Mentiroso nem papel alheio para cliente.
6. Realtime transporta estado permitido; não vira autoridade da regra.
7. Escrever/ajustar testes junto.

## 3. Marcelinho — revisão adversarial

Tentar quebrar especialmente:

- Mentiroso consultando o segredo;
- jogador consultando papel alheio;
- voto/contagem parcial vazando;
- pista duplicada;
- voto duplicado;
- avanço de fase sem autorização;
- empate e segundo turno;
- última chance do Mentiroso;
- reconnect/host transfer;
- XSS em nickname/pista;
- RLS/RPC/realtime;
- regressões e modularidade;
- fidelidade ao protótipo e regra anti-IA;
- Web/PWA e impacto Android/iOS.

Rodar gates existentes: `test`, `typecheck`, `lint`, `build`.

## 4. Loop de correção

Defeito não chega ao primo como pronto.

`Marcelinho → Guinho → Marcelinho`

Dúvida de produto descoberta na revisão:

`Marcelinho → Giam → Guinho → Marcelinho`

Repetir até aprovação ou bloqueio real.

## 5. Giam — aceite

Conferir cada requisito do plano. Procurar escopo acidental, mock escondido, segredo vazando, botão sem função e lacuna em “não verificado”.

Saída: `ACEITO`, `ACEITO COM PENDÊNCIA REGISTRADA` ou `DEVOLVIDO`.

## 6. Entrega

Relatar em linguagem simples o que ficou pronto, o que foi validado, o que não foi e próximo passo.

Não fazer deploy, loja, custo, merge não solicitado ou mudança destrutiva no modo GOAS sem autorização explícita.