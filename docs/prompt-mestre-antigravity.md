# Quem Mente? — prompt mestre para o Antigravity

> O agente executa. Produto decide.

## Prompt base

```text
Você está implementando o projeto Quem Mente? neste repositório.

Antes de alterar arquivos, leia:
- README.md
- docs/documentacao-funcional.md
- docs/jornada-ux-ui.md
- docs/identidade-visual.md
- docs/arquitetura-tecnica-zero-custo.md
- docs/modelo-de-dados.md
- docs/contratos-motor-jogo.md
- docs/padrao-editorial-segredos.md
- docs/roteiro-playtest-conteudo.md
- docs/analytics-e-metricas.md
- docs/monetizacao.md
- docs/lancamento-e-crescimento.md
- docs/backlog-priorizado.md
- docs/seguranca-idade-e-moderacao.md
- docs/checklist-producao-e-lancamento.md

Considere esses documentos fonte de verdade do produto.

Regras obrigatórias:
1. implemente somente a fase/fatia que eu indicar;
2. não invente funcionalidades;
3. não mude regra de jogo sem relatar o conflito e pedir decisão;
4. não defina UI final antes do protótipo aprovado;
5. nenhum serviço pago;
6. Supabase de destino: projeto 20T reaproveitado logicamente como auê-games;
7. antes de migration destrutiva no remoto, audite o 20T e mostre o impacto;
8. regra de jogo separada de componente visual;
9. backend/RPC é autoritativo para papel, segredo, voto, resolução e pontuação;
10. RLS fechado por padrão;
11. service key e secrets nunca no frontend/Git;
12. segredo nunca pode ser entregue ao Mentiroso ou cliente não autorizado;
13. voto parcial nunca pode vazar;
14. nickname/pista devem ser tratados como entrada não confiável;
15. execute testes/typecheck/build aplicáveis antes de concluir;
16. não faça deploy de produção sem instrução explícita;
17. não avance sozinho para a próxima fase.

Ao iniciar:
- resuma em até 8 linhas o entendimento da fase;
- liste arquivos previstos;
- aponte bloqueios reais.

Ao terminar:
- liste mudanças;
- testes realmente executados e resultado;
- pendências;
- decisões assumidas;
- qualquer risco encontrado.

Não alegue teste, deploy, integração realtime ou segurança que não validou de fato.
```

## Como usar

Depois do prompt base:

```text
Implemente somente a Fase 1 do docs/backlog-priorizado.md.
```

ou uma fatia menor:

```text
Na Fase 2, implemente apenas schema inicial, RLS e RPC de criação/entrada em sala. Não implemente início de partida ainda.
```

## Quando o protótipo chegar

Adicionar:

```text
O protótipo aprovado é a referência visual obrigatória. A documentação funcional é a referência de comportamento. Em conflito, pare e relate; não escolha sozinho.
```

## Segurança como gate

Se qualquer implementação permitir:

- Mentiroso obter segredo;
- jogador obter papel de outro;
- jogador ver voto parcial;
- alterar pontuação pelo cliente;
- executar HTML/JS de pista/nickname;

não considere a fase pronta.

## Scope creep

Sugestão boa fora da fase deve ser registrada como sugestão e não implementada.

## Regra final

O Antigravity pode ser o pedreiro mais rápido do bairro. A planta continua sendo nossa.