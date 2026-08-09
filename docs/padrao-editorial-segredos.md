# Quem Mente? — padrão editorial dos segredos

> O segredo precisa dar pista suficiente pra gente esperta e espaço suficiente pra um safado blefar.

## 1. Regra de ouro

O segredo ideal fica no meio do caminho entre duas merdas:

- óbvio demais → todo mundo entrega sem querer;
- específico demais → nem quem sabe o segredo consegue dar pista sem praticamente falar a resposta.

O bom segredo faz o jogador pensar:

> “Eu consigo provar que sei isso sem dizer o que é.”

E faz o Mentiroso pensar:

> “Dá pra enrolar mais um pouco.”

## 2. Teste da mesa de bar

Um segredo passa se gerar pistas indiretas naturais.

Exemplo bom: `praia`.

Pistas possíveis:

- “eu evitaria meio-dia”;
- “sempre volto com alguma coisa dentro da mochila”;
- “se o tempo vira, perde metade da graça”.

Exemplo ruim: `parafuso sextavado M8`.

A pessoa ou fala quase a resposta ou fica parecendo um maluco descrevendo peça de oficina.

## 3. Categorias do MVP

Pacote inicial:

- `lugares`
- `comidas`
- `animais`
- `profissoes`
- `objetos`
- `filmes-series`
- `situacoes-dia-a-dia`

As categorias precisam ser largas o suficiente para o Mentiroso ter espaço de blefe, mas não tão largas a ponto de ele poder falar qualquer porra.

## 4. Dificuldade

### Fácil

Segredo conhecido por praticamente qualquer adulto e com várias pistas possíveis.

Exemplos:

- praia
- pizza
- cachorro

Bom para primeira partida.

### Médio

Conhecido, mas exige um pouco mais de cuidado para não entregar.

Exemplos:

- aeroporto
- sushi
- fotógrafo

É onde o jogo provavelmente fica mais gostoso.

### Difícil

Ainda popular o suficiente para ser justo, mas com menos pistas naturais ou mais risco de confusão.

Exemplos:

- cartório
- bússola
- documentário

Difícil não significa obscuro. Se a palavra depende de conhecimento especializado, ela não é “hard”; ela é ruim.

## 5. Pistas óbvias

Cada segredo pode ter uma lista editorial de termos óbvios.

Exemplo:

`praia`

- mar
- areia
- onda
- guarda-sol

No MVP isso serve principalmente para revisão e futura orientação.

Não precisamos bloquear automaticamente uma pista só porque contém uma dessas palavras. Linguagem é contextual e um filtro burro pode encher o saco mais do que ajudar.

## 6. A pista não pode ser impossível

Antes de aprovar um segredo, o editor precisa conseguir inventar pelo menos **cinco pistas indiretas diferentes** em menos de dois minutos.

Se não consegue, o segredo é candidato a descarte.

## 7. O Mentiroso precisa ter onde se esconder

O jogador Mentiroso recebe a categoria.

Por isso, a categoria precisa permitir algum blefe plausível.

Exemplo:

Categoria `comidas`, segredo `pizza`.

O Mentiroso pode falar algo como:

> “depende muito de com quem você está”.

Pode ser pizza, churrasco, fondue, sushi… ele continua vivo.

Agora imagine categoria `instrumentos cirúrgicos`, segredo `bisturi`.

Além de ser nichado, a categoria já aponta demais. Não entra no pacote básico.

## 8. Evitar sinônimos e quase-sinônimos na mesma partida

Segredos muito parecidos precisam compartilhar um `collision_group` editorial.

Exemplos:

- `praia` e `piscina` → `agua-lazer`
- `médico` e `enfermeiro` → `saude-profissoes`
- `pizza` e `hambúrguer` → `fast-food`

O motor pode usar isso futuramente para evitar sequências repetitivas ou muito parecidas.

Não é obrigatório para a primeira implementação, mas o conteúdo já pode nascer preparado.

## 9. Coisas que não entram

No pacote básico, evitar:

- política partidária;
- religião específica como alvo de piada;
- tragédias reais;
- doenças graves;
- crimes reais recentes;
- termos sexuais explícitos;
- drogas ilícitas;
- celebridades como segredo principal;
- marcas quando um termo genérico resolve;
- conteúdo que depende de região muito específica;
- termos técnicos.

Pacotes temáticos futuros podem ampliar isso com opt-in e moderação própria.

## 10. Filmes e séries

O segredo deve ser um título extremamente reconhecível ou um conceito amplo de entretenimento.

No primeiro pacote, preferir títulos/franquias conhecidos no Brasil e evitar coisa que depende de temporada, episódio ou personagem secundário.

Também evitar colocar dois títulos muito parecidos na mesma partida.

## 11. Situações do dia a dia

Essa categoria aceita pequenas expressões, não só palavras únicas.

Exemplos:

- perder o ônibus
- ficar sem bateria
- chegar atrasado

A frase precisa ser curta e gerar experiências comuns.

## 12. Status editorial

O arquivo de conteúdo pode usar:

- `candidate`
- `approved`
- `published`
- `disabled`

No banco:

- `candidate` → `draft`
- `approved` → `draft`
- `published` → `published`
- `disabled` → `disabled`

Nada vira `published` automaticamente porque existe num CSV.

## 13. Checklist antes de aprovar

Um segredo só vira `approved` se:

- [ ] praticamente todo o público-alvo reconhece o termo;
- [ ] existem pelo menos cinco pistas indiretas possíveis;
- [ ] a categoria não entrega demais;
- [ ] a categoria também não é larga demais;
- [ ] um Mentiroso consegue blefar de forma plausível;
- [ ] não depende de conhecimento técnico;
- [ ] não cria risco desnecessário de moderação;
- [ ] não é praticamente sinônimo de outro segredo usado na mesma sequência;
- [ ] funciona em português brasileiro sem explicação adicional.

## 14. Regra final

O conteúdo não existe para mostrar criatividade editorial.

Existe para criar aquela cena em que alguém fala uma pista meio torta, todo mundo olha pra cara dele e pensa:

> “hmmm… esse filho da puta não sabe a palavra.”

Se o segredo ajuda a criar isso, ele serve.