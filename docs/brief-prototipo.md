# De Migué — brief do protótipo

> Objetivo: provar o jogo inteiro sem narrador humano. A pessoa entra, descobre o papel, dá pista, desconfia, vota e sente a revelação. A interface organiza a bagunça e sai da frente.

## 1. Fonte da verdade

Antes de desenhar, ler nesta ordem:

1. `docs/00-nome-canonico.md`
2. `docs/documentacao-funcional.md`
3. `docs/jornada-ux-ui.md`
4. `docs/identidade-visual.md`
5. `docs/regras-design-e-copy.md`

Se houver conflito visual, `regras-design-e-copy.md` prevalece.

## 2. Jornada principal

**Home → Criar sala → Sala → Iniciar → Papel secreto → Pista → Pistas reveladas → Discussão → Votação → Revelação → Última chance, se houver → Pontuação → Próxima rodada → Resultado final → Revanche.**

Também precisa existir:

**Home → Entrar em sala → Apelido → Sala.**

## 3. O que o protótipo precisa provar

- conceito entendido sem tutorial longo;
- criar/entrar em sala é ridiculamente fácil;
- papel parece realmente secreto;
- ser Mentiroso dá um micro “fodeu”;
- pista é rápida de enviar;
- discussão fica entre as pessoas, não dentro do app;
- votar é claro e difícil de fazer por acidente;
- revelação tem tensão;
- revanche leva no máximo dois toques.

## 4. Direção visual

Usar:

- base escura;
- vermelho `#F04444` para suspeita/acusação;
- amarelo `#F6C445` para atenção/pista;
- verde `#40C878` só em confirmação/vitória;
- **Anybody** para impacto/revelação;
- **Archivo** para interface;
- olhares, papel escondido, voto, marcação, sobreposição e dúvida como repertório gráfico.

Não usar Pinóquio, nariz crescendo, mascote de malandro ou “personagem IA”.

## 5. Regra anti-IA

Não entregar:

- card para cada frase;
- bento grid;
- glassmorphism;
- degradê roxo/azul;
- glow neon;
- hero SaaS;
- Inter/Manrope/Space Grotesk por inércia;
- copy publicitária genérica;
- personagem sorrindo só para preencher espaço.

Espaço vazio é tensão. Não preencher por ansiedade.

## 6. Mobile primeiro

Artboard de referência: **390 × 844 px**.

Precisa funcionar bem a partir de 360 px.

- CTA principal perto do polegar;
- alvos de toque grandes;
- safe areas consideradas;
- teclado não esconde campo/CTA;
- desktop é adaptação, não origem.

## 7. Home

Marca: **De Migué**.

Frase curta possível:

> “Tem alguém de migué nessa mesa.”

CTAs:

- **Criar sala**
- **Entrar em sala**

Secundário:

- **Como joga**

Nada de landing page com três benefícios em cards.

## 8. Sala

Mostrar:

- código;
- copiar;
- compartilhar;
- participantes;
- host;
- configuração resumida;
- CTA **Começar partida** para host.

Quem não é host pode ver algo na energia de:

> “Esperando o Luiz começar essa porra.”

A versão final pode ajustar palavrão conforme contexto, mas não trocar por voz corporativa.

## 9. Papel secreto

Proteção inicial:

**Só você pode ver isso.**

CTA:

**Ver meu papel**

### Comum

Categoria discreta + segredo enorme.

Exemplo:

**PRAIA**

CTA:

**Entendi. Esconder**

### Mentiroso

Entrada visual mais forte.

**VOCÊ É O MENTIROSO**

Categoria:

**LUGAR**

Texto:

**Finge que sabe.**

O papel funcional continua chamado **Mentiroso**. Não forçar `Migué` como nome de papel só porque virou marca.

## 10. Pista

Uma ação principal:

**Manda tua pista.**

Campo grande, contador discreto e cronômetro visível.

CTA:

**Mandar pista**

Depois:

**Agora sustenta essa história.**

## 11. Pistas reveladas

Pistas entram em sequência.

Cada pista mostra apenas o necessário:

- apelido;
- pista;
- identificação visual do jogador.

Não precisa de card pesado para cada uma se linha/ritmo resolverem.

## 12. Discussão

A tela não tenta substituir a conversa.

Mostrar pistas + cronômetro quando houver.

CTA ao final:

**Bora votar**

## 13. Votação

Jogadores grandes e fáceis de tocar.

Não mostrar o próprio jogador como opção.

Ao selecionar:

**Acusar Marcelo**

Confirmação curta:

**Vai de Marcelo mesmo?**

Ações:

- **Sim, acusa esse aí**
- **Pensando melhor…**

## 14. Espera

Mostrar progresso sem vazar voto:

**4 de 6 já votaram.**

Nunca mostrar contagem parcial por candidato.

## 15. Revelação

Ritmo sugerido:

1. votos entram;
2. mais votado ganha foco;
3. pausa curta;
4. identidade real aparece;
5. segredo é mostrado.

Se acertaram:

**Pegaram o safado.**

Se erraram:

**Vocês condenaram um inocente.**

## 16. Última chance

Se o Mentiroso foi descoberto:

**Ainda dá pra estragar a festa.**

Pergunta:

**Qual era o segredo?**

15 segundos.

A avaliação da resposta é do backend, não da UI.

## 17. Resultado

Mostrar pontuação sem planilha.

Destaques possíveis:

- Mentiroso descoberto;
- caiu no papo;
- acertou o segredo mesmo ferrado;
- acusou inocente com confiança demais.

## 18. Resultado final

Campeão em destaque + ranking curto.

Estatísticas divertidas quando sustentadas pelos dados:

- melhor caçador;
- melhor blefador;
- mais acusado injustamente.

CTAs:

- **Revanche**
- **Compartilhar**

## 19. Compartilhamento

Criar pelo menos dois modelos:

### Blefe

> “Fiquei de migué a rodada inteira e ninguém percebeu.”

### Caos da sala

> “Todo mundo acusou o Marcelo. O Mentiroso era o Pedro.”

Marca pequena, história grande.

## 20. Estados obrigatórios

- sala cheia;
- código inválido;
- apelido repetido;
- jogador reconectando;
- jogador saiu;
- host mudou;
- tempo acabou;
- pista não enviada;
- votação empatada;
- segundo turno;
- Mentiroso desconectou.

Não transformar cada estado em modal enorme.

## 21. Movimento obrigatório

Simular:

- proteção/virada do papel;
- entrada das pistas;
- registro do voto;
- sequência da revelação;
- resultado final.

Sem apresentação da Pixar entre fases.

## 22. O que não desenhar agora

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

## 23. Multiplataforma

O mesmo design precisa servir à base única que será entregue como:

- Web/PWA;
- Android;
- iOS.

Não criar três UIs independentes. Adaptar safe areas, teclado, compartilhamento, back e integrações nativas quando necessário.

## 24. Critério de aprovação

Alguém que nunca viu o projeto consegue:

1. criar/entrar na sala;
2. entender o papel;
3. mandar pista;
4. votar;
5. entender a revelação;
6. saber quem ganhou;
7. pedir revanche.

Sem narrador humano.

Se a mesa não ganhar aquele clima de “esse filho da puta tá de migué”, o protótipo ainda não resolveu **De Migué**.