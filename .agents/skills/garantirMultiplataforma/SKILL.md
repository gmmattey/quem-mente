---
name: garantirMultiplataforma
description: Garante que a mesma feature nasca preparada para Web/PWA, Android e iOS via Capacitor.
---

# garantirMultiplataforma

Procedimento do **Guinho**; Marcelinho revisa.

- regra/estado/realtime compartilhados;
- APIs específicas ficam em adapters;
- web continua produto completo;
- Android: back, teclado, background, safe area, share/deep link;
- iOS: safe area, teclado, share sheet, background, WebView/deep link;
- indisponibilidade de recurso degrada sem quebrar a rodada.

Não criar três implementações da mesma regra.

Na entrega, separar o que foi validado em navegador, Android e iOS. Sem aparelho/simulador, marcar **NÃO VERIFICADO EM APARELHO**.