# Quem Mente? — monetização

> Esse jogo vive da tensão entre amigos. Se a propaganda entrar no meio da acusação, a gente matou a melhor parte para ganhar centavos.

## 1. Regra principal

Quem Mente? nasce grátis.

Criar sala, entrar por convite, jogar a partida clássica, votar e pedir revanche não podem depender de pagamento.

O jogo tem um ponto forte de aquisição: uma pessoa naturalmente puxa outras para dentro da sala. Não vamos estragar isso colocando cadastro ou cobrança antes da diversão.

## 2. Publicidade

Publicidade é a primeira hipótese de receita.

### Onde pode aparecer

- depois do placar final;
- antes de iniciar uma revanche, sem bloquear o botão;
- em área secundária da home;
- em tela de espera do host antes da partida, desde que discreta e não atrapalhe entrada dos jogadores.

### Onde NÃO pode aparecer

- durante revelação do papel;
- enquanto alguém escreve pista;
- no meio da discussão;
- durante votação;
- antes de revelar o Mentiroso;
- durante a última chance do Mentiroso;
- entre rodadas.

A regra é: **partida começou, anúncio some da mesa**.

## 3. Frequência inicial

Nos primeiros playtests e beta, anúncios podem ficar desligados.

Quando ativados:

- no máximo uma oportunidade ao final da partida;
- não exigir anúncio para revanche;
- não mostrar anúncio individual diferente no meio do fluxo de cada jogador;
- evitar criar espera artificial só para monetizar.

## 4. Produto pago futuro

Não implementar no MVP.

Um futuro `Quem Mente?+` pode oferecer:

- remover anúncios;
- pacotes de temas especiais;
- temas +18 com opt-in e tratamento adequado;
- criação de pacotes personalizados;
- histórico de partidas;
- estatísticas pessoais;
- configurações extras de sala;
- personalização visual leve.

O pago compra variedade e conforto, não vantagem.

## 5. Salas/pacotes personalizados

Esse jogo tem uma hipótese de monetização especialmente boa: **conteúdo customizado**.

Exemplos futuros:

- festa de aniversário;
- empresa/equipe;
- casal;
- família;
- grupo de amigos;
- despedida de solteiro;
- fandom específico.

O usuário poderia montar um pacote privado de segredos/temas e compartilhar com a turma.

Não construir isso antes de a mecânica básica provar retenção.

## 6. Patrocínio futuro

Marcas podem patrocinar pacotes temáticos, mas isso só funciona se parecer conteúdo e não comercial interrompendo a rodada.

Exemplo:

- pacote cinema;
- pacote futebol;
- pacote viagem;
- pacote comida.

Sempre identificado como patrocinado.

O patrocinador não ganha acesso a dados privados da sala.

## 7. O que não entra

- venda de pontos;
- vantagem para descobrir o Mentiroso;
- dica paga durante partida;
- compra de voto extra;
- loot box;
- moeda virtual;
- anúncio no meio da rodada;
- cobrança para entrar em sala normal;
- coleta agressiva de dados para publicidade.

## 8. Ordem de monetização

1. provar que grupos conseguem jogar sem explicação longa;
2. provar que pedem revanche;
3. provar que convite traz gente;
4. ativar publicidade leve no pós-partida;
5. medir impacto;
6. testar remoção de anúncios/pacotes quando houver demanda;
7. explorar patrocínio quando existir audiência.

## 9. Regra de custo

Antes da receita, nada de infraestrutura paga nova.

A monetização deve funcionar sobre a arquitetura gratuita já definida com Cloudflare + Supabase `auê-games`.

Se para ganhar R$ 20 precisamos contratar três SaaS de R$ 80, a conta está fazendo piada com a nossa cara.

## 10. Métrica financeira principal

Acompanhar:

`receita líquida por 1.000 partidas concluídas`

E também:

- receita por sala;
- receita por jogador ativo;
- impacto do anúncio na revanche;
- impacto do anúncio na criação de nova sala;
- custo de infraestrutura / receita.

O dinheiro precisa crescer junto com uso real, não só com página carregada.