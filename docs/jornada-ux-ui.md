# Quem Mente? — jornada e UX/UI

> Isso aqui não é um app de produtividade com uma gravata colorida. É um jogo de festa. A tela tem que sair da frente e deixar a paranoia acontecer entre as pessoas.

## 1. A ideia visual em uma frase

**Pouca coisa por tela, informação grande, transições rápidas e clima de “todo mundo sabe de alguma coisa que você talvez não saiba”.**

O jogo precisa parecer vivo, safado e ligeiramente suspeito. Nada de interface infantil demais, nada de cara de cassino e nada de painel corporativo.

## 2. O que a experiência precisa provocar

O jogador deve sentir, nessa ordem:

1. **entendi rápido**;
2. **quero entrar nessa sala agora**;
3. **puta merda, será que eu sou o Mentiroso?**;
4. **essa pista foi estranha pra caralho**;
5. **eu sabia que era ele** ou **fui enganado bonito**;
6. **vamos outra**.

Se a interface não ajuda a produzir isso, ela está ocupando espaço à toa.

## 3. Princípios de UX

### Um objetivo por tela

Cada tela responde a uma pergunta só.

- Home: quero jogar como?
- Sala: quem já entrou?
- Papel: o que eu sei?
- Pista: o que eu vou falar?
- Discussão: quem está estranho?
- Voto: em quem eu voto?
- Revelação: quem era o safado?

Se aparecerem três CTAs principais brigando na mesma tela, alguém fez merda.

### Sem tutorial de apresentação de TCC

O primeiro contato deve ensinar jogando.

Pode existir uma explicação de três passos na home, mas não uma sequência de oito telas de onboarding.

### O celular não é o centro da festa

Em grupo presencial, a pessoa precisa olhar para os amigos. Por isso:

- textos curtos;
- botões grandes;
- estado atual muito óbvio;
- pouco conteúdo rolável durante rodada;
- nada que obrigue leitura longa.

### Tensão boa, não confusão

Segredo e papel precisam parecer secretos. O jogo pode criar suspense, mas nunca deixar o jogador sem saber o que fazer em seguida.

## 4. Estrutura geral

A navegação não precisa de menu fixo durante a partida.

### Fora da partida

- Home
- Como jogar
- Criar sala
- Entrar em sala

### Dentro da partida

A jornada é linear. Não existe menu hambúrguer para a pessoa passear enquanto todo mundo espera.

**Sala → Papel secreto → Pista → Revelação das pistas → Discussão → Votação → Resultado → Última chance do Mentiroso, quando houver → Pontuação → Próxima rodada → Placar final.**

## 5. Tela 1 — Home

### Objetivo

Colocar alguém numa partida em poucos segundos.

### Conteúdo

Topo simples com marca.

Centro:

- título curto;
- frase de apoio;
- CTA principal **Criar sala**;
- CTA secundário **Entrar em sala**.

Abaixo, de forma discreta:

- **Como joga?**

### Copy sugerida

**Descubra quem tá enrolando todo mundo.**

“Um sabe menos. Todo mundo finge normalidade. Boa sorte.”

### O que não colocar

- feed;
- ranking mundial;
- login obrigatório;
- carrossel com 12 benefícios;
- banner gigante de monetização.

## 6. Tela 2 — Como jogar

### Objetivo

Explicar sem palestra.

Três passos:

1. todo mundo recebe um segredo;
2. o Mentiroso recebe só a categoria;
3. pistas, discussão e votação.

Fechar com:

**Entendeu? Então vai mentir.**

CTA: **Criar sala**.

## 7. Tela 3 — Criar sala

### Objetivo

Configurar sem transformar o anfitrião em administrador de condomínio.

### Configurações visíveis

- rodadas: 3 / 5 / 7;
- temas: seleção simples;
- tempo da pista: 30 s padrão;
- discussão: livre ou 60 s.

### Defaults

A tela já vem pronta para jogar.

A pessoa só mexe se quiser.

CTA: **Criar sala**.

## 8. Tela 4 — Entrar em sala

### Objetivo

Entrar sem cadastro.

Campos:

- código da sala;
- apelido.

Se vier por link, o código já está resolvido e só aparece o apelido.

CTA: **Entrar**.

Erros precisam ser humanos:

- “Essa sala não existe mais.”
- “Esse apelido já está ocupado.”
- “A sala está cheia. Acontece.”

## 9. Tela 5 — Sala de espera

### Objetivo

Mostrar que está tudo pronto para começar.

### Host vê

- código;
- botão compartilhar;
- jogadores conectados;
- configurações resumidas;
- CTA **Começar partida**.

### Convidado vê

- código;
- jogadores;
- estado **Esperando o dono começar**.

### Visual

Jogadores podem aparecer como nomes/chips simples. Não precisamos inventar avatar de RPG.

Quando alguém entra, animação curta e sonora opcional.

## 10. Tela 6 — Preparação da rodada

Uma transição de 2–3 segundos limpa o estado anterior.

Exemplo:

**Rodada 2 de 5**

“Olha seu papel. E fecha essa cara.”

CTA: **Ver meu papel**.

Essa etapa evita alguém receber segredo na tela no exato momento em que o amigo está olhando por cima do ombro.

## 11. Tela 7 — Papel secreto

Essa é uma das telas mais importantes.

### Jogador comum

Mostrar categoria pequena e segredo enorme.

Exemplo:

**Lugar**

# PRAIA

Texto curto:

“Dê uma pista sem entregar essa porra de bandeja.”

### Mentiroso

Tela visualmente parecida, mas com tensão diferente.

**Você é o Mentiroso.**

Categoria:

# LUGAR

“Você não sabe o segredo. Finge costume.”

### Privacidade

O conteúdo só aparece depois de ação deliberada do jogador.

Pode existir padrão “pressione e segure para revelar” se isso funcionar bem em testes, mas não é obrigatório no MVP.

CTA: **Já vi**.

Depois de confirmar, o segredo some da tela principal.

## 12. Tela 8 — Escrever pista

### Objetivo

Responder rápido.

A tela mostra:

- “Sua pista”;
- campo curto;
- contador de caracteres;
- cronômetro;
- CTA **Enviar pista**.

O segredo não deve ficar exposto o tempo todo. Pode existir um botão discreto **ver segredo de novo** para jogador comum.

Para o Mentiroso, esse botão mostra apenas a categoria.

### Limite

Pista curta. Sugestão inicial: 60 caracteres.

Isso força a pessoa a ser objetiva e facilita a revelação.

## 13. Tela 9 — Esperando os outros

Depois de enviar:

**Pista enviada. Agora tenta parecer inocente.**

Mostrar progresso:

“4 de 6 responderam.”

Não mostrar quem ainda não respondeu se isso gerar pressão desnecessária; podemos testar depois.

## 14. Tela 10 — Revelação das pistas

As pistas aparecem uma a uma.

Cada revelação mostra:

- nome;
- pista grande;
- pequena pausa antes da próxima.

No modo presencial, o host pode tocar para avançar.

No remoto, pode avançar automaticamente em intervalo curto.

No final:

CTA **Discutir**.

## 15. Tela 11 — Discussão

Tela simples.

Mostrar:

- lista de jogadores;
- pistas dadas;
- cronômetro, quando ativo;
- CTA do host **Ir para votação**.

Nada de chat no MVP.

A conversa acontece onde as pessoas já estão: na mesa, chamada, Discord, WhatsApp, seja lá onde for.

## 16. Tela 12 — Votação

### Objetivo

Fazer a escolha sem dúvida.

Pergunta:

**Quem tá mentindo?**

Lista de jogadores em botões grandes.

O jogador não aparece como opção para si mesmo.

Depois de selecionar:

- destacar escolha;
- pedir confirmação;
- travar voto após confirmação.

CTA: **Confirmar voto**.

Depois:

**Voto registrado. Agora aguenta.**

## 17. Tela 13 — Resultado da votação

Primeiro, mostrar a distribuição dos votos.

Segurar a identidade do Mentiroso por um instante curto.

Depois revelar:

**O Mentiroso era… MARCELO.**

Ou:

**Vocês acusaram o cara errado. Parabéns pela investigação.**

A revelação pode ter animação forte, mas curta.

## 18. Tela 14 — Última chance do Mentiroso

Só aparece quando ele foi descoberto.

Os demais veem:

**Calma. O desgraçado ainda pode roubar a rodada.**

O Mentiroso vê:

**Qual era o segredo?**

- campo de resposta ou opções, conforme conteúdo;
- 15 segundos;
- CTA **É isso**.

Depois revelar acerto/erro.

## 19. Tela 15 — Pontuação da rodada

Mostrar primeiro o resultado humano, depois o número.

Exemplo:

**Luiz enganou todo mundo. +200**

ou

**4 pessoas pegaram o Mentiroso.**

Abaixo, ranking resumido.

CTA:

**Próxima rodada**.

Se não for a última.

## 20. Tela 16 — Placar final

Essa tela precisa valer print.

Mostrar:

- campeão grande;
- ranking;
- “melhor Mentiroso”;
- “detetive da noite”;
- estatística engraçada relevante.

CTAs:

- **Revanche** — principal;
- **Compartilhar resultado**;
- **Sair da sala**.

### Exemplo de frase

“Luiz enganou 7 votos e terminou campeão. Confiar nele claramente foi um erro.”

## 21. Fluxos de exceção

### Reconexão

Tela:

**Sua internet deu uma sumida. Estamos tentando te colocar de volta.**

Se voltar, entra direto no estado atual.

### Sala encerrada

**Essa festa acabou. Cria outra e chama o povo.**

### Rodada cancelada

Se o Mentiroso abandonar:

**O Mentiroso fugiu. Rodada anulada.**

CTA: **Próxima rodada**.

## 22. Direção visual

### Clima

Festa noturna, jogo social, contraste forte e identidade própria.

Não precisa ser literalmente preto + neon. O importante é evitar cara de app infantil e cara de SaaS.

### Formas

- cantos arredondados, mas sem transformar tudo em cartão;
- blocos grandes;
- botões largos;
- hierarquia por tamanho e espaço, não por dezenas de caixas.

### Tipografia

Uma fonte de display com personalidade pode aparecer em títulos e revelações.

Texto funcional precisa continuar muito legível.

### Cor

A paleta deve ter:

- fundo principal;
- superfície;
- cor de ação;
- cor de Mentiroso/perigo;
- sucesso;
- texto principal e secundário.

Não usar vermelho em tudo relacionado ao Mentiroso se isso entregar papel por reflexo de tela para quem está ao lado. A tela secreta precisa ser pensada também fisicamente.

## 23. Movimento e som

Movimento serve para suspense e recompensa.

Usar em:

- entrada de jogador;
- revelação de papel;
- pistas;
- resultado da votação;
- placar final.

Evitar animação longa em ação repetitiva.

Som deve ser opcional e respeitar aparelho silencioso.

Pode existir:

- tic discreto de cronômetro nos últimos segundos;
- impacto na revelação;
- som curto de ponto.

Nada de máquina caça-níquel tocando a cada botão.

## 24. Acessibilidade

Mesmo sendo irreverente, o produto não pode ser uma bosta de usar.

- contraste adequado;
- não depender só de cor;
- fontes legíveis;
- alvos de toque grandes;
- suporte a redução de movimento;
- textos escaláveis sem quebrar a rodada;
- cronômetro com indicação textual além de animação;
- estados de erro claros.

## 25. Responsividade

O alvo principal é celular em retrato.

Desktop funciona, mas não guia o design.

Em telas maiores:

- limitar largura do conteúdo;
- não esticar botões até parecer caixa de supermercado;
- aproveitar espaço para ranking e pistas sem inventar painel lateral obrigatório.

## 26. Tom de voz dentro do produto

Curto, provocador e natural.

### Bom

- “Finge costume.”
- “Quem tá mentindo?”
- “O desgraçado escapou.”
- “Vocês acusaram o cara errado.”

### Ruim

- “Sua jornada de descoberta começou.”
- “Prepare-se para uma experiência imersiva de dedução social.”
- “Parabéns! Você concluiu a etapa de votação com sucesso.”

Isso é jogo, não treinamento obrigatório da firma.

## 27. Telas obrigatórias do MVP

1. Home
2. Como jogar
3. Criar sala
4. Entrar em sala
5. Sala de espera
6. Preparação da rodada
7. Papel secreto
8. Pista
9. Espera
10. Revelação das pistas
11. Discussão
12. Votação
13. Resultado da votação
14. Última chance
15. Pontuação
16. Placar final
17. Estados de conexão/erro

Pode parecer muita tela listada, mas várias são estados simples da mesma estrutura. Não é licença para criar 17 layouts completamente diferentes.

## 28. Componentes que vale reaproveitar

- botão primário;
- botão secundário;
- input;
- código da sala;
- jogador/lista de jogador;
- cronômetro;
- badge de rodada;
- card de pista — um dos poucos cards que realmente fazem sentido;
- ranking;
- modal/estado de confirmação;
- toast curto.

## 29. O que o protótipo precisa provar

Antes de implementar bonito, o protótipo navegável precisa responder:

- dá para criar e entrar em sala sem explicação externa?
- o papel secreto fica claro em dois segundos?
- ninguém confunde pista com resposta?
- o estado de “estou esperando” é óbvio?
- a votação é inequívoca?
- a revelação tem impacto?
- a revanche está a um toque?

Se isso estiver redondo em tela feia, estamos no caminho. Depois a gente passa perfume.