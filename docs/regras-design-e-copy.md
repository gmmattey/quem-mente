# De Migué — regras de design e copy

> Este documento é trava de qualidade para protótipo, Design System e implementação. Se alguma orientação visual anterior conflitar com ele, **este documento prevalece** até revisão explícita.

## 1. O jogo não pode parecer gerado por IA

Se escondermos o logo, ainda precisa parecer um jogo social de suspeita, blefe, pista e acusação.

Se puder virar app financeiro, ferramenta de IA ou SaaS trocando só cor e texto, falhou.

## 2. Proibido o kit visual automático de IA

Não usar como solução padrão:

- card para cada frase;
- card dentro de card;
- bento grid;
- glassmorphism;
- blur decorativo;
- degradê roxo/azul de startup;
- glow neon;
- bolhas 3D;
- ilustração genérica de personagem sorrindo;
- ícones em círculos coloridos sem motivo;
- pills/badges em excesso;
- sombra macia em toda superfície;
- cantos arredondados idênticos em tudo;
- hero de landing page com benefícios em cards;
- dashboard para organizar uma rodada social.

Cards só existem quando representam um objeto real do jogo, como:

- uma pista;
- um jogador selecionável;
- um papel secreto;
- uma unidade clara de resultado.

Mesmo nesses casos, não transformar a experiência inteira em caixas flutuantes.

## 3. Tipografia precisa ter personalidade

Direção preferida:

- **Anybody** — títulos, revelações, palavras de impacto e papel secreto;
- **Archivo** — interface, pistas, botões, apelidos e textos funcionais.

Evitar escolher por inércia:

- Inter;
- Manrope;
- Space Grotesk;
- Poppins;
- DM Sans;
- Sora.

### Testes obrigatórios

- “VOCÊ É O MENTIROSO” com impacto sem parecer infantil;
- apelidos longos legíveis;
- pistas de uma ou duas linhas em tela pequena;
- nomes longos sem quebrar votação;
- cronômetro e placar sem cara bancária;
- pesos claramente diferentes.

## 4. Copy não pode parecer ChatGPT tentando ser engraçado

Evitar:

- “Prepare-se para uma experiência cheia de mistério”;
- “Descubra quem está mentindo entre seus amigos”;
- “Desafie sua percepção e divirta-se”;
- “Uma experiência social envolvente e intuitiva”;
- “Será que você consegue descobrir a verdade?”;
- “Reúna seus amigos para momentos inesquecíveis”;
- “Sua missão é simples…”;
- três adjetivos genéricos vendendo a tela;
- explicar o botão em parágrafo;
- meme datado em toda tela;
- emoji como personalidade;
- piada forçada em cada erro;
- tutorial corporativo.

## 5. Como a copy deve soar

Parece conversa de gente jogando.

Boas direções:

- “Tem alguém de migué nessa mesa.”
- “Só você pode ver isso.”
- “VOCÊ É O MENTIROSO.”
- “Finge que sabe.”
- “Manda tua pista.”
- “Agora sustenta essa história.”
- “Vai de Marcelo mesmo?”
- “Pegaram o safado.”
- “Vocês acusaram a pessoa errada.”
- “Mais uma?”

A expressão `de migué` é parte da marca, não bordão obrigatório em toda tela.

## 6. Uma tela, uma tensão principal

Cada fase tem um protagonista:

- papel;
- pista;
- discussão;
- voto;
- revelação.

Não criar uma coleção de cards iguais onde tudo tem o mesmo peso.

Na tela de papel, o papel é o acontecimento.

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
- informação parcialmente revelada.

Pequenas irregularidades são bem-vindas. Bagunça sem propósito, não.

## 8. Nada de mascote genérico de IA

Não criar personagem automático para “dar personalidade”.

Também evitar caricatura óbvia de malandro, Pinóquio, nariz crescendo ou bandido de desenho.

No MVP, personalidade vem de:

- tipografia;
- ritmo;
- copy;
- votação;
- movimento;
- contraste;
- comportamento dos elementos.

## 9. Design System não é catálogo de cards

Precisa definir:

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
- contraste e acessibilidade.

Uma página com 30 componentes arredondados não é Design System completo.

## 10. Desktop não vira site de startup

Evitar:

- hero gigante;
- subtítulo publicitário;
- três benefícios em cards;
- seção “como funciona” com ícones redondos;
- depoimentos inventados;
- números falsos de usuários;
- FAQ para preencher espaço.

Conteúdo de SEO pode existir sem destruir a personalidade do jogo.

## 11. Protótipo usa situações reais

Nada de lorem ipsum.

Usar:

- apelidos naturais;
- segredos reais do pacote candidato;
- pistas plausíveis;
- empates;
- votos reais de exemplo;
- reconexão;
- erros reais.

Uma votação com `Player 1 / Player 2 / Player 3` mascara problema de design.

## 12. Critério anti-IA

Antes de aprovar uma tela, perguntar:

1. poderia ser qualquer app se trocarmos o logo?
2. tem card demais?
3. a fonte tem relação com o jogo?
4. a copy parece gente falando?
5. existe blur/degradê/glow sem função?
6. a fase está óbvia em dois segundos?
7. a tensão social aparece visualmente?
8. existe algum elemento só porque “fica bonito” em template?

Se três ou mais respostas forem ruins, redesenhar.

## 13. Regra para OpenDesign / Figma / qualquer agente

O agente deve:

- ler `docs/00-nome-canonico.md` antes de tudo;
- ler este documento antes de criar tela;
- não “profissionalizar” a copy apagando a voz;
- não preencher vazio com cards;
- não adicionar feature para deixar tela completa;
- não usar fonte padrão por conveniência;
- evitar estética infantil;
- evitar estética SaaS/IA;
- priorizar tensão, hierarquia e jogabilidade;
- explicar qualquer desvio relevante.

## 14. Nome e marca

O nome canônico é **De Migué**.

Não usar `Quem Mente?` em novos artefatos visuais.

O papel funcional do jogo continua se chamando **Mentiroso**. Não renomear o papel para “Migué” só para forçar a marca dentro da regra.

A identidade deve explorar **suspeita + blefe + acusação + alguém fingindo que sabe**.

## 15. Regra final

Se o protótipo parece “bonito” mas não parece especificamente **De Migué**, ainda não está pronto.