# Quem Mente? — regras de design e copy

> Este documento é uma trava de qualidade para protótipo, Design System e implementação. Se alguma orientação visual anterior conflitar com ele, **este documento prevalece até a próxima revisão explícita**.

## 1. O jogo não pode parecer gerado por IA

O resultado final precisa parecer um jogo social com personalidade própria, não um template de app “bonitinho” montado por prompt.

Teste simples:

> se escondermos o logo, ainda parece um jogo de suspeita, blefe e acusação?

Se puder virar app de finanças, ferramenta de IA ou SaaS trocando só cor e texto, falhou.

## 2. Proibido o kit visual automático de IA

Não usar como solução padrão:

- card para cada frase;
- card dentro de card;
- bento grid;
- glassmorphism;
- blur decorativo;
- degradê roxo/azul de startup;
- glow neon;
- fundo com bolas 3D;
- ilustração genérica de personagem sorrindo;
- ícones em círculos coloridos sem motivo;
- pills/badges em excesso;
- sombra macia em toda superfície;
- cantos arredondados idênticos em tudo;
- hero de landing page com três benefícios em cards;
- dashboard para organizar uma rodada social.

Cards só existem quando representam algo que faz sentido como objeto do jogo, por exemplo:

- uma pista;
- um jogador selecionável;
- um papel secreto;
- uma unidade clara de resultado.

Mesmo nesses casos, não transformar tudo em caixas flutuantes.

## 3. Tipografia precisa ter personalidade do jogo

As combinações anteriores `Fredoka + Manrope` deixam de ser direção preferencial.

`Fredoka` pode puxar o produto para infantil e `Manrope` cai fácil em estética genérica de produto digital.

Evitar usar automaticamente:

- Inter;
- Manrope;
- Space Grotesk;
- Poppins;
- DM Sans;
- Sora.

Essas fontes não são proibidas universalmente; apenas não serão escolhidas por inércia.

### Direção tipográfica preferida do Quem Mente?

Ponto de partida:

- **Anybody** — títulos, revelações, palavras-chave e momentos de suspeita;
- **Archivo** — interface, pistas, botões, nomes e textos funcionais.

Por quê:

- `Anybody` permite personalidade e pequenas variações de largura sem parecer desenho infantil;
- funciona bem em frases curtas e fortes como “VOCÊ É O MENTIROSO”;
- `Archivo` segura legibilidade e densidade social sem ter cara de dashboard;
- o contraste entre as duas famílias reforça jogo + conversa, não produto corporativo.

Usar variação tipográfica com controle. Não distorcer texto só porque a fonte permite.

### Testes obrigatórios

- “VOCÊ É O MENTIROSO” precisa ter impacto sem parecer jogo infantil;
- apelidos precisam continuar muito legíveis;
- pistas de uma ou duas linhas precisam funcionar em tela pequena;
- nomes longos não podem desmontar votação;
- cronômetro e placar não podem parecer interface bancária;
- pesos precisam ser claramente diferentes.

## 4. Copy não pode parecer ChatGPT tentando ser divertido

Evitar frases como:

- “Prepare-se para uma experiência cheia de mistério”;
- “Descubra quem está mentindo entre seus amigos”;
- “Desafie sua percepção e divirta-se”;
- “Uma experiência social envolvente e intuitiva”;
- “Será que você consegue descobrir a verdade?”;
- “Reúna seus amigos para momentos inesquecíveis”;
- “Sua missão é simples…”;
- qualquer frase com três adjetivos genéricos vendendo o próprio jogo.

Também evitar:

- explicar o botão em um parágrafo;
- meme datado em toda tela;
- emoji como personalidade padrão;
- piada forçada em cada erro;
- títulos motivacionais desnecessários;
- voz de tutorial corporativo.

## 5. Como a copy deve soar

Parece conversa entre gente jogando.

Curta, específica e situacional.

Boas direções:

- “Tem alguém enrolando essa mesa.”
- “Só você pode ver isso.”
- “VOCÊ É O MENTIROSO.”
- “Finge que sabe.”
- “Manda tua pista.”
- “Agora sustenta essa história.”
- “Vai de Marcelo mesmo?”
- “Pegaram o safado.”
- “Vocês acusaram a pessoa errada.”
- “Mais uma?”

A copy pode ser sacana. Não pode parecer redator tentando ganhar prêmio.

## 6. Uma tela, uma tensão principal

Cada fase precisa ter um protagonista:

- papel;
- pista;
- discussão;
- voto;
- revelação.

Não criar uma coleção de cards iguais onde tudo tem o mesmo peso.

Na tela de papel secreto, o papel é o acontecimento.

Na votação, os jogadores são o acontecimento.

Na revelação, o Mentiroso é o acontecimento.

## 7. Formas vêm da mecânica

A linguagem visual pode nascer de:

- olhar;
- dúvida;
- marcação;
- acusação;
- carta;
- papel escondido;
- rabisco;
- seta;
- voto;
- ponto de interrogação.

Não inventar decoração que não tenha relação com blefe ou interação social.

Pequenas irregularidades são bem-vindas. Bagunça sem propósito, não.

## 8. Nada de “personagem IA” como identidade

Não criar mascote genérico gerado por IA para dar personalidade ao jogo.

Se algum personagem/mascote surgir no futuro, precisa nascer de conceito próprio e linguagem consistente.

No MVP, a personalidade vem de:

- tipografia;
- ritmo;
- copy;
- votação;
- movimento;
- contraste;
- comportamento dos elementos.

## 9. Componentes não são o Design System inteiro

O Design System precisa definir:

- hierarquia por fase;
- tipografia;
- espaçamento;
- grid;
- densidade;
- estados de segredo;
- estados de voto;
- seleção de jogador;
- movimento da revelação;
- safe areas;
- comportamento de teclado;
- tratamento de nickname/pista;
- regras de contraste e acessibilidade.

Uma página com 30 componentes em cards não é um Design System completo.

## 10. Desktop não vira site de startup

A home desktop não deve virar:

- hero gigante;
- subtítulo publicitário;
- três benefícios em cards;
- seção de ícones “como funciona”;
- depoimentos inventados;
- números falsos de usuários;
- FAQ para preencher espaço.

Conteúdo de SEO pode existir, mas deve continuar com a personalidade do jogo.

## 11. Protótipo usa situações reais

Não usar lorem ipsum nas telas principais.

Usar:

- apelidos naturais;
- segredos reais do pacote candidato;
- pistas plausíveis;
- empates;
- votos reais de exemplo;
- mensagens de reconexão;
- situações de erro.

Uma tela de votação com “Player 1 / Player 2 / Player 3” esconde problema de design.

## 12. Critério anti-IA antes de aprovar uma tela

Perguntar:

1. poderia ser qualquer app se trocarmos o logo?
2. tem card demais?
3. a fonte tem relação com o jogo?
4. a copy parece gente falando?
5. existe algum blur/degradê/glow sem função?
6. a fase atual está óbvia em dois segundos?
7. a tensão social aparece visualmente?
8. tem algum elemento só porque “fica bonito” em template?

Se três ou mais respostas forem ruins, redesenhar.

## 13. Regra para OpenDesign / Figma / qualquer agente

O agente deve:

- ler este documento antes de criar qualquer tela;
- não “profissionalizar” a copy apagando a voz do jogo;
- não preencher espaços vazios com cards;
- não adicionar features para deixar a tela mais completa;
- não usar fonte padrão por conveniência;
- evitar estética infantil;
- evitar estética SaaS/IA;
- priorizar tensão, hierarquia e jogabilidade;
- explicar qualquer desvio relevante destas regras.

## 14. Estado do nome

`Quem Mente?` deve ser tratado, por enquanto, como **working title**.

Não fechar wordmark definitivo, domínio pago ou assets finais de loja antes da validação de naming.

O Design System pode avançar em cima dos conceitos **suspeita + blefe + acusação + dúvida**, que continuam válidos mesmo se o nome mudar.