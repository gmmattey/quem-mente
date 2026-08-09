---
name: auditarSegurancaETestes
description: Gate do Marcelinho para testes, build, segredo, autorizacao, privacidade e fluxo real.
---

# auditarSegurancaETestes

Procedimento do **Marcelinho**.

Rodar o que existir: `test`, `typecheck`, `lint`, `build`.

Tentar quebrar:

- Mentiroso lendo segredo;
- jogador lendo papel alheio;
- contagem/voto parcial;
- dupla pista/voto;
- avanço de fase indevido;
- payload/realtime/log vazando segredo;
- XSS em nickname/pista;
- RLS/RPC;
- reconnect e host transfer;
- segredo em analytics;
- service role/credencial no cliente.

Também validar UX/copy/protótipo quando aplicável.

Relatório em: **automático**, **leitura**, **aparelho/navegador real**, **não verificado**.

Falha de segredo/autorização é crítica e devolve ao Guinho; não vira “pendência futura”.