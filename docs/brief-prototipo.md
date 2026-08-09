# Quem Mente? — brief do protótipo

> Objetivo: desenhar um protótipo mobile-first que prove o jogo inteiro sem precisar explicar a ideia em reunião. Quem clicar deve entender, entrar numa sala e sentir a tensão da votação.

## O que prototipar

Não precisamos desenhar o universo inteiro. Precisamos provar a jornada principal.

### Telas obrigatórias

1. Home
2. Criar sala
3. Entrar em sala
4. Sala de espera
5. Configuração da partida pelo dono
6. Preparação da rodada
7. Papel secreto — jogador comum
8. Papel secreto — Mentiroso
9. Digitar pista
10. Pistas reveladas
11. Discussão
12. Votação
13. Voto confirmado / aguardando outros
14. Resultado da votação
15. Revelação do Mentiroso
16. Última chance do Mentiroso
17. Resultado da rodada
18. Ranking parcial
19. Resultado final
20. Card de compartilhamento
21. Estado de reconexão
22. Estado de jogador desconectado

Não são 22 produtos diferentes. Várias dessas telas devem reaproveitar a mesma estrutura e mudar só o estado.

## Jornada que precisa estar clicável

**Home → Criar sala → Sala de espera → Iniciar → Papel secreto → Pista → Discussão → Votação → Revelação → Pontuação → Nova rodada → Resultado final → Revanche.**

Também precisa existir o caminho:

**Home → Entrar em sala → Apelido → Sala.**

## O que o protótipo precisa provar

- a pessoa entende o jogo sem tutorial longo;
- criar ou entrar numa sala é ridiculamente fácil;
- o papel secreto parece realmente secreto;
- ser escolhido como Mentiroso dá um micro “fodeu”;
- votar em alguém é claro e difícil de fazer sem querer;
- a revelação tem tensão;
- o ranking não interrompe a brincadeira;
- começar revanche leva no máximo dois toques.

## Direção visual

Usar `docs/identidade-visual.md` como fonte da verdade.

Resumo:

- base escura;
- vermelho suspeita como cor principal;
- amarelo para atenção/pista;
- verde só em acerto/vitória;
- Fredoka em títulos fortes;
- Manrope na interface;
- elementos gráficos de dúvida, olhos, cartas e “?”;
- nada de mascote obrigatório.

## Mobile primeiro

Artboard principal de referência: **390 × 844 px**.

O layout precisa funcionar bem de 360 px para cima.

Desktop é adaptação, não a origem do design.

No celular:

- CTA principal alcançável com polegar;
- texto nunca microscópico;
- alvos de toque grandes;
- nada crítico colado nas bordas;
- teclado não pode esconder o botão de enviar pista.

## Home

Precisa vender o conceito sem parágrafo de marketing.

Marca grande.

Frase curta sugerida:

**“Tem alguém enrolando essa mesa.”**

CTAs:

**Criar sala**

**Entrar em sala**

Ação secundária:

**Como joga**

Pode existir uma pequena animação de olhos/ponto de interrogação, mas sem virar desenho animado.

## Sala de espera

Mostrar:

- código grande;
- botão copiar;
- compartilhar convite;
- participantes;
- indicação clara de quem é o dono;
- CTA do dono: **Começar partida**.

Quem não é dono vê algo como:

**“Esperando o Luiz começar essa porra.”**

A frase final pode ser suavizada na produção, mas a energia é essa.

## Papel secreto

É uma das telas mais importantes.

A pessoa deve primeiro ver uma proteção do tipo:

**“Só você pode ver isso.”**

CTA:

**Ver meu papel**

Depois:

### Comum

Categoria discreta.

Segredo enorme.

Exemplo:

**PRAIA**

CTA:

**Entendi. Esconder**

### Mentiroso

Entrada visual mais forte.

**VOCÊ É O MENTIROSO**

Categoria:

**LUGAR**

Texto curto:

**Finge que sabe e não entrega a cara.**

## Pista

Uma pergunta só:

**“Qual é a sua pista?”**

Campo grande.

Contador discreto.

Cronômetro visível.

CTA:

**Mandar pista**

Após envio:

**“Agora sustenta essa história.”**

## Pistas reveladas

Pistas aparecem em sequência, não todas de uma vez imediatamente.

Cada uma mostra:

- avatar simples;
- apelido;
- pista.

A entrada pode ter pequena animação de carta.

## Discussão

A tela não tenta substituir a conversa.

Mostrar:

- pistas visíveis;
- cronômetro se ativado;
- CTA ao fim: **Bora votar**.

Se não houver cronômetro, o dono pode avançar.

## Votação

Jogadores em grid/lista grande.

Não mostrar o próprio jogador como opção.

Ao selecionar alguém:

**Acusar Marcelo**

Depois de tocar, confirmação:

**“Vai de Marcelo mesmo?”**

CTAs:

**Sim, acusa esse aí**

**Pensando melhor…**

## Espera da votação

Mostrar progresso sem revelar voto:

**4 de 6 já votaram.**

Nada de indicar em quem votaram.

## Revelação

Precisa ter ritmo:

1. votos entram;
2. mais votado ganha destaque;
3. pausa curta;
4. aparece se era ou não o Mentiroso;
5. segredo é mostrado.

Se erraram:

**“Vocês acabaram de condenar um inocente.”**

Se acertaram:

**“Pegaram o safado.”**

## Última chance

Se o Mentiroso foi descoberto:

**“Ainda dá pra estragar a festa.”**

Pergunta:

**“Qual era o segredo?”**

Campo/autocomplete simples.

15 segundos.

## Resultado da rodada

Mostrar pontuação sem planilha.

Uma lista simples de ganhos da rodada.

Destaques engraçados podem aparecer:

- “Mentiroso descoberto”;
- “Caiu no papo”;
- “Acertou o segredo mesmo ferrado”.

CTA:

**Próxima rodada**

## Resultado final

Campeão grande.

Pódio ou ranking curto.

Estatísticas divertidas:

- melhor caçador de Mentiroso;
- melhor blefador;
- pessoa mais acusada injustamente.

CTAs:

**Revanche**

**Compartilhar**

## Compartilhamento

Criar pelo menos dois modelos de card:

### Resultado individual

**“Enganei 5 pessoas e ninguém percebeu.”**

### Caos da sala

**“Todo mundo acusou o Marcelo. O Mentiroso era o Pedro.”**

Logo pequena + CTA para jogar.

## Estados que não podem ser esquecidos

- sala cheia;
- código inválido;
- apelido repetido;
- jogador reconectando;
- jogador saiu;
- dono mudou;
- tempo acabou;
- pista não enviada;
- votação empatada;
- nova votação;
- partida cancelada porque Mentiroso desconectou.

Não precisa transformar cada estado num modal enorme.

## Componentes reaproveitáveis

- botão principal;
- botão secundário;
- avatar;
- jogador selecionável;
- cronômetro;
- badge de rodada;
- card de pista;
- toast;
- modal de confirmação;
- ranking curto;
- barra de progresso dos jogadores.

## Movimento obrigatório no protótipo

Simular pelo menos:

- virar papel secreto;
- entrada das pistas;
- voto sendo registrado;
- sequência da revelação;
- resultado final.

Sem animação de apresentação da Pixar. Rápido e com propósito.

## O que NÃO desenhar agora

- loja;
- assinatura;
- perfil completo;
- ranking mundial;
- feed;
- amizade;
- chat;
- +18;
- modo Caos;
- avatar personalizável;
- painel administrativo.

Tudo isso é masturbação de roadmap antes da primeira partida funcionar.

## Critério de aprovação

O protótipo está bom quando alguém que nunca ouviu falar no projeto consegue:

1. criar uma sala;
2. entender o próprio papel;
3. enviar pista;
4. votar;
5. entender a revelação;
6. saber quem ganhou;
7. pedir revanche.

Sem alguém do projeto sentado do lado explicando.

Se precisar de narrador humano, o protótipo ainda não resolveu o jogo.