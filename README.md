# De Migué

> Um jogo social de blefe, suspeita e cara de pau pra descobrir quem está fingindo que sabe.

> **Nota técnica:** o repositório ainda se chama `quem-mente`. Esse slug é legado e não define mais o nome do produto.

## A ideia, sem powerpoint

Todo mundo recebe o mesmo segredo.

Todo mundo, menos uma pessoa.

Essa pessoa é o **Mentiroso** e recebe apenas a categoria. A missão dela é fingir que sabe do que a mesa está falando sem entregar a cara.

Os outros precisam provar que conhecem o segredo sem facilitar demais a vida do Mentiroso.

A diversão acontece entre as pessoas. O app só organiza a bagunça.

## Nome canônico

O nome oficial do produto é **De Migué**.

Não usar `Quem Mente?` em novos materiais de produto, design, marketing ou loja. Referências antigas ainda existentes em documentos históricos devem ser interpretadas como **De Migué** até serem naturalmente revisadas.

## Como joga

1. Uma pessoa cria a sala e compartilha link/código.
2. A galera entra com apelido, sem login obrigatório.
3. O jogo escolhe categoria, segredo e Mentiroso.
4. Jogadores comuns veem o segredo.
5. O Mentiroso vê somente a categoria.
6. Cada pessoa manda uma pista curta e indireta.
7. As pistas são reveladas.
8. O grupo discute e tenta descobrir quem está de migué.
9. Todo mundo vota em segredo.
10. O jogo resolve a votação e revela o Mentiroso.
11. Se o Mentiroso foi pego, ainda ganha uma última chance de adivinhar o segredo.
12. Pontos são distribuídos e começa a próxima rodada.

Exemplo:

**Categoria:** Lugar  
**Segredo:** Praia

Os jogadores comuns veem `PRAIA`.

O Mentiroso vê apenas `LUGAR`.

Uma pessoa manda “eu evitaria meio-dia”. Outra: “sempre volto com alguma coisa dentro da mochila”. O Mentiroso precisa se virar sem saber exatamente o que é.

Aí começa a paranoia.

## Onde está a diversão

O jogo é sobre **ler gente**.

Quem sabe o segredo precisa dar uma pista boa sem entregar tudo.

Quem não sabe precisa blefar.

Depois a mesa acusa, se defende, muda de ideia e geralmente condena algum inocente com convicção assustadora.

## Regras principais

- mínimo: 3 jogadores;
- recomendado: 4 a 8;
- máximo do MVP: 10;
- partidas de 3, 5 ou 7 rodadas;
- Mentiroso sorteado de forma balanceada;
- voto secreto;
- empate inicial gera segundo turno entre empatados;
- novo empate faz o Mentiroso sobreviver;
- se descoberto, o Mentiroso tem 15 segundos para tentar adivinhar o segredo.

## Pontuação canônica

### Jogadores comuns

- votou corretamente no Mentiroso: **+100**;
- grupo pegou o Mentiroso: **+50** de bônus coletivo;
- voto errado: **0**.

Quem votou certo numa rodada em que o grupo pegou o Mentiroso recebe **150 pontos**.

### Mentiroso

- sobreviveu à votação: **+200**;
- foi descoberto, mas acertou o segredo na última chance: **+150**;
- foi descoberto e errou: **0**.

## A experiência que precisamos entregar

O ciclo é:

**entrou → descobriu o papel → deu pista → desconfiou → votou → revelou → quis outra.**

Uma tela, uma tensão principal.

O jogador deve olhar mais para os amigos do que para o celular.

Nada de dashboard, card pra cada frase ou UI tentando ser protagonista da brincadeira.

## Multiplataforma desde o começo

Uma única base de código por jogo deve gerar:

- Web/PWA;
- Android;
- iOS.

A implementação segue a fundação compartilhada do **Auê Games**: React + TypeScript + Vite + Capacitor, com diferenças de plataforma isoladas em adapters.

## Conteúdo

O pacote editorial usa categorias como:

- lugares;
- comidas;
- animais;
- profissões;
- objetos;
- filmes e séries;
- situações do dia a dia.

Segredo bom dá espaço para pista indireta e também deixa o Mentiroso blefar.

Segredo ruim ou entrega instantaneamente ou faz todo mundo ficar olhando pra tela sem saber o que escrever.

## Design

A identidade nasce de:

- suspeita;
- blefe;
- acusação;
- dúvida;
- olhar;
- voto;
- segredo escondido.

O design não pode parecer template gerado por IA. A regra específica está em `docs/regras-design-e-copy.md`.

A direção tipográfica atual é **Anybody** para impacto/revelação e **Archivo** para interface, sujeita a validação no protótipo — nunca escolhida por inércia.

## Distribuição

Canais planejados a partir da mesma base:

- Web/PWA;
- Google Play;
- Apple App Store;
- itch.io;
- CrazyGames;
- Microsoft Store via PWA;
- outros canais conforme encaixe.

## Monetização

O jogo principal é gratuito.

Publicidade só aparece entre partidas ou em pausas naturais, nunca no meio de pista, discussão ou votação.

No futuro, pago pode incluir remoção de anúncios, packs de tema, personalização e configurações extras — nunca vantagem competitiva.

## O que NÃO entra agora

- chat interno;
- voz/vídeo;
- clãs;
- loja de moeda;
- avatar 3D;
- ranking mundial complexo;
- modo +18 no MVP;
- IA inventando segredo em tempo real sem revisão;
- feature só porque “ficaria legal”.

## Documentação principal

Ler nesta ordem:

1. `docs/00-nome-canonico.md`
2. `docs/documentacao-funcional.md`
3. `docs/jornada-ux-ui.md`
4. `docs/identidade-visual.md`
5. `docs/regras-design-e-copy.md`
6. `docs/brief-prototipo.md`
7. arquitetura, conteúdo, monetização e handoff conforme a fase.

## A régua

**De Migué** merece continuar se uma turma consegue entrar, jogar algumas rodadas, acusar amigos, rir e apertar “revanche” sem ninguém precisar convencer.

Se quem entrou por convite depois cria a própria sala, melhor ainda.