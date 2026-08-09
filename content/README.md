# Conteúdo do Quem Mente?

> Isso aqui é bancada de teste. Estar no CSV não significa ganhar o direito de aparecer numa partida.

## O que existe agora

`segredos-iniciais.csv` contém o primeiro pacote editorial.

Distribuição:

- 10 Lugares
- 10 Comidas
- 10 Animais
- 10 Profissões
- 10 Objetos
- 10 Filmes e séries
- 10 Situações do dia a dia

Total: **70 segredos candidatos**.

Todos começam como `candidate`.

## Colunas

### `key`

Identificador editorial estável.

Não precisa virar UUID do banco.

### `category`

Slug da categoria.

### `secret`

O segredo mostrado aos jogadores comuns.

### `difficulty`

- `easy`
- `medium`
- `hard`

### `forbidden_clues`

Termos separados por `|` que entregam demais o segredo.

No MVP são referência editorial. Não devem ser bloqueados automaticamente sem decisão posterior.

### `collision_group`

Grupo de conteúdo parecido.

Serve para evitar que uma mesma partida fique repetindo quase a mesma ideia.

Exemplo:

- praia → `agua-lazer`
- piscina, se entrar depois → `agua-lazer`

### `status`

Fluxo editorial:

- `candidate`
- `approved`
- `published`
- `disabled`

No Supabase:

- `candidate` → `draft`
- `approved` → `draft`
- `published` → `published`
- `disabled` → `disabled`

**Nunca importar `candidate` já como `published`.**

### `notes`

Observações de revisão.

## O teste que cada segredo precisa passar

Antes de aprovar, jogar o segredo com gente real.

Anotar:

- os comuns deram pistas naturais?
- alguém entregou a palavra sem querer?
- o Mentiroso teve chance real de blefar?
- a categoria ajudou sem praticamente revelar?
- houve confusão de significado?
- a rodada gerou discussão ou morreu rápido?

## Sinais de segredo ruim

### Entrega instantânea

Todo mundo usa pistas quase sinônimas da palavra.

Ação: revisar `forbidden_clues` ou remover o segredo.

### Mentiroso sem chance

A categoria + primeiras pistas deixam só uma resposta possível.

Ação: trocar de categoria ou remover.

### Jogadores comuns travados

Quem sabe a palavra não consegue inventar pista sem falar a resposta.

Ação: remover. Não adianta chamar isso de “difícil”.

### Ninguém conhece

Mais de uma pessoa pergunta o que a palavra significa.

Ação: remover do pacote básico.

### Discussão não acontece

As pistas são tão neutras que ninguém consegue desconfiar de ninguém.

Ação: revisar dificuldade ou segredo.

## Regra para dificuldade após playtest

A dificuldade editorial inicial é hipótese.

Depois dos testes, ela pode mudar.

Uma forma simples de observar:

- **easy:** grupo identifica ou entende a rodada facilmente, mas Mentiroso ainda consegue blefar;
- **medium:** exige pistas melhores e gera dúvida saudável;
- **hard:** aumenta bastante a tensão sem virar adivinhação aleatória.

## Filmes e séries

O pacote possui títulos conhecidos como candidatos.

Antes de publicar comercialmente, revisar o uso desses nomes dentro da experiência e da identidade do produto. Não usar logos, artes oficiais, imagens promocionais ou material protegido como se fossem assets próprios do jogo.

Se quisermos evitar qualquer dependência desse pacote no MVP, o jogo continua funcionando perfeitamente com as outras seis categorias.

## Quantidade para lançamento

70 é suficiente para desenvolvimento e primeiros playtests.

Não é suficiente para uso prolongado com repetição baixa.

Meta antes de um lançamento mais aberto:

- mínimo confortável: **150 segredos aprovados**;
- melhor: **250+**;
- nenhuma categoria com menos de 20 bons segredos.

Não preencher número com porcaria só para dizer que temos 250.

## Repetição

Mesmo com banco pequeno, uma sessão deve tentar evitar:

- segredo repetido;
- mesmo `collision_group` em rodadas consecutivas;
- excesso da mesma categoria quando modo misto estiver ativo.

## Importação

O Antigravity deve criar seed/migration a partir deste arquivo somente quando a camada de banco estiver pronta.

A importação precisa:

1. resolver/criar categorias;
2. inserir segredos como `draft`, salvo os explicitamente `published`;
3. converter `forbidden_clues` de `|` para array;
4. não publicar candidato automaticamente;
5. ser idempotente ou documentar claramente como reaplicar sem duplicar.

## Regra final

O banco de conteúdo não é coleção de palavras.

É uma coleção de **rodadas que têm potencial de gerar acusação, blefe e risada**.

Se uma palavra não gera isso, ela está só ocupando linha no CSV.