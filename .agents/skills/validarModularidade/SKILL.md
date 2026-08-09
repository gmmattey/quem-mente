---
name: validarModularidade
description: Revisa coesao, dependencia, duplicacao de regra e responsabilidade misturada.
---

# validarModularidade

Procedimento do **Marcelinho**.

Procure regra duplicada entre UI/backend/realtime, componente decidindo jogo, SDK vazando para domínio, arquivo monolítico, dependência circular, estado global desnecessário e abstração prematura.

Pergunte:

1. existe uma única fonte para cada transição de fase?
2. mudar pontuação/papel exige mexer em quantos lugares?
3. realtime só transporta ou começou a decidir?
4. Web/Android/iOS compartilham domínio?
5. a abstração reduz manutenção real?

Reprovar complexidade sem ganho de clareza, segurança ou teste.