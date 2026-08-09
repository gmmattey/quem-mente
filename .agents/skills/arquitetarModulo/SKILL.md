---
name: arquitetarModulo
description: Define fatia modular, segura, barata e multiplataforma antes de codificar.
---

# arquitetarModulo

Procedimento do **Giam**.

Antes da implementação, definir comportamento, requisitos, fronteira domínio/UI/backend, autorização, dados secretos, realtime, adapters por plataforma, testes e o que fica fora.

Regras:

- backend é autoritativo para Mentiroso, segredo, fase, voto, score e resultado;
- cliente recebe apenas o que seu papel/fase permitem;
- realtime transporta estado permitido, não decide regra;
- usar `qm_*` no banco;
- uma base para Web/Android/iOS;
- sem custo recorrente antes de receita;
- mudança destrutiva exige autorização.

Preferir solução simples, reversível e testável.