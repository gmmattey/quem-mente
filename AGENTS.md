# AGENTS.md — autoridade do De Migué

Este arquivo define como agentes trabalham neste repositório. O jogo público se chama **De Migué**; `quem-mente` é apenas slug técnico legado.

## 1. Fontes canônicas

Leia nesta ordem quando a demanda tocar o assunto:

1. `docs/00-nome-canonico.md` — nome público.
2. `docs/documentacao-funcional.md` — regra canônica do jogo.
3. `docs/jornada-ux-ui.md` — fluxo e UX.
4. `docs/identidade-visual.md` — direção visual.
5. `docs/regras-design-e-copy.md` — trava anti-IA; prevalece em design/copy quando houver conflito visual antigo.
6. `docs/brief-prototipo.md` — escopo do protótipo.
7. `docs/arquitetura-tecnica-zero-custo.md` — arquitetura e custo.
8. `docs/modelo-de-dados.md` e `docs/contratos-motor-jogo.md` — dados, segredo e operações autoritativas.
9. `docs/backlog-priorizado.md` e demais planos — ordem de implementação.
10. código/migrations/testes — verdade do que já está implementado; divergência com intenção deve ser explicitada, não escondida.

A documentação funcional vence README/legado. Regra do jogo vence preferência visual. Protótipo aprovado vence improviso de UI.

## 2. Squad

| Agente | Papel |
|---|---|
| **Giam** | Guardião da entrega e produto: regra, UX/UI, copy, arquitetura, prioridade, plano e aceite final |
| **Guinho** | Implementação: código, realtime, adapters Web/Android/iOS, testes e entrega técnica |
| **Marcelinho** | Qualidade independente: segurança do segredo, regressão, modularidade, fidelidade visual, copy, acessibilidade e multiplataforma |

Ordem obrigatória:

```text
GIAM planeja
  → GUINHO implementa
    → MARCELINHO valida e tenta quebrar
      → GIAM dá o aceite
        → primo aprova quando a ação exigir
```

Guinho não começa sem plano verificável. Marcelinho não dá aceite de produto. Giam não pula Marcelinho.

## 3. Multiplataforma desde o início

Uma única base React + TypeScript + Vite gera Web/PWA, Android e iOS via Capacitor.

Não criar três regras, três UIs independentes ou três repositórios. Código específico de canal fica atrás de adapter.

## 4. Regras imutáveis do produto

- jogadores comuns recebem **o mesmo segredo + categoria**;
- Mentiroso recebe **categoria e `secret: null`**;
- nenhum cliente pode descobrir o segredo/papel de outro antes da revelação;
- pistas são conteúdo transitório do jogador e não patrimônio eterno por padrão;
- voto é secreto; não mostrar contagem parcial;
- empate inicial → segundo turno entre empatados; novo empate → Mentiroso sobrevive;
- Mentiroso descoberto recebe última chance de 15 s conforme regra funcional;
- backend decide papel, segredo, voto, pontuação, avanço e resultado;
- discussão acontece fora do app: sem chat/áudio/vídeo no MVP;
- anúncio nunca interrompe rodada;
- nenhuma decisão técnica cria custo recorrente antes de receita;
- tabelas continuam `qm_*` até decisão técnica explícita.

## 5. Design e copy

`docs/regras-design-e-copy.md` é gate obrigatório.

Não passa:

- card soup, bento gratuito, glassmorphism ou SaaS genérico;
- visual infantil ou cassino;
- fonte escolhida por inércia de template/IA;
- copy que parece ChatGPT tentando ser engraçado;
- interface que compete com a conversa entre os jogadores.

Antes do protótipo aprovado, não cristalizar UI final. Pode avançar domínio, backend, realtime, testes, conteúdo e infraestrutura reversível.

## 6. Modo GOAS

Quando a demanda disser `GOAS` ou “modo goas”, seguir `.agents/workflows/GOAS.md` e a skill `executarGOAS`.

GOAS executa ponta a ponta e corrige internamente antes de entregar. Não pula segurança nem inventa produto.

Só parar por: dúvida real de produto sem resposta nas fontes, credencial, custo, ação pública/irreversível, mudança destrutiva de dados, decisão legal/comercial ou conflito canônico.

## 7. Gates mínimos

Antes de chamar implementação de pronta, rodar o que existir no projeto:

```text
test
typecheck
lint
build
```

E tentar quebrar especialmente: acesso ao segredo, papel alheio, voto parcial, dupla submissão, troca de fase, reconnect e host transfer.

Se algo não pôde ser executado, escrever **NÃO VERIFICADO**.

## 8. Git e entrega

Preferir uma fatia vertical por vez, branch/worktree isolada e PR antes de merge em trabalho real.

Não fazer automaticamente sem autorização explícita do primo:

- deploy público;
- publicação em loja;
- compra/upgrade;
- migration destrutiva;
- exclusão de ambiente/dados;
- merge quando ele pediu apenas implementação/revisão.

## 9. Comunicação

Quem fala com o primo é o Giam. Resultado e impacto em linguagem simples; detalhe técnico fica no código/PR.

Se não testou, fala. Se o Mentiroso consegue ver o segredo, a entrega está quebrada mesmo que a tela esteja linda.

## 10. Skills

Procedimentos vivem em `.agents/skills/`. Skill orienta execução; fonte canônica continua sendo a documentação acima.