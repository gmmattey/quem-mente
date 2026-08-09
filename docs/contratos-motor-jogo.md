# Quem Mente? — contratos do motor de jogo

> O motor não precisa saber se o botão é vermelho, redondo ou piscante. Ele só precisa saber quem pode fazer o quê e quem se fodeu na votação.

## 1. Objetivo

Separar as regras do Quem Mente? da interface.

O motor controla:

- elegibilidade da partida;
- escolha do Mentiroso;
- escolha do segredo;
- fases da rodada;
- envio de pista;
- votação;
- desempate;
- última chance do Mentiroso;
- pontuação;
- ranking final;
- reconexão e abandono.

A interface só apresenta estado e envia comandos.

## 2. Fonte de verdade

Toda regra que afeta segredo, papel, voto ou ponto é autoritativa no backend/RPC.

O cliente não escolhe o Mentiroso.
O cliente não calcula quem foi eliminado.
O cliente não informa quantos pontos ganhou.

Ele pede e recebe o resultado.

## 3. Tipos básicos

Exemplo conceitual:

```ts
type PlayerId = string;
type RoomId = string;
type RoundId = string;
type SecretId = string;

type PlayerRole = 'common' | 'liar';

type RoomStatus = 'lobby' | 'playing' | 'finished' | 'expired';

type RoundStatus =
  | 'role_reveal'
  | 'clue_submission'
  | 'discussion'
  | 'voting'
  | 'runoff_voting'
  | 'reveal'
  | 'liar_guess'
  | 'scoring'
  | 'finished';
```

## 4. Máquina de estados da rodada

Fluxo padrão:

```text
role_reveal
   -> clue_submission
   -> discussion
   -> voting
      -> runoff_voting (se necessário)
   -> reveal
      -> liar_guess (se Mentiroso descoberto)
   -> scoring
   -> finished
```

Nem toda rodada passa por `runoff_voting` ou `liar_guess`.

Transição inválida falha.

Exemplo: enviar pista durante votação não vira “ah, deixa passar”. Retorna erro.

## 5. `validateGameStart`

Responsabilidade: dizer se uma sala pode começar.

Entrada:

```ts
validateGameStart({
  roomStatus,
  activePlayers,
  roundCount,
  config
})
```

Condições mínimas:

- sala em `lobby`;
- pelo menos 3 jogadores ativos;
- host ativo;
- configuração válida;
- conteúdo disponível para a quantidade de rodadas.

Saída:

```ts
{ ok: true }
```

ou erro de domínio.

## 6. `selectSecret`

Responsabilidade: escolher segredo elegível.

Entrada conceitual:

```ts
selectSecret({
  availableSecrets,
  usedSecretIds,
  categoryFilter,
  difficultyMix,
  rng
}): SecretId
```

Regras:

- não repetir na mesma partida;
- usar apenas `published`;
- respeitar categorias escolhidas;
- aceitar RNG injetável para teste.

## 7. `selectLiar`

Responsabilidade: escolher quem será o Mentiroso.

Entrada:

```ts
selectLiar({
  activePlayers,
  liarHistory,
  previousLiarId,
  rng
}): PlayerId
```

Regra do MVP:

1. priorizar jogadores que ainda não foram Mentiroso;
2. evitar o Mentiroso da rodada anterior quando houver alternativa;
3. entre os elegíveis, sortear;
4. quando todos já tiverem sido, reiniciar o equilíbrio pelo menor número de vezes no papel.

Não precisa ser matematicamente perfeito. Precisa não parecer roubado.

## 8. `getRoleViewForPlayer`

Responsabilidade: devolver somente o que um jogador específico pode saber.

Entrada:

```ts
getRoleViewForPlayer({
  playerId,
  liarPlayerId,
  secret,
  category
})
```

Se comum:

```ts
{
  role: 'common',
  category: 'Lugar',
  secret: 'Praia'
}
```

Se Mentiroso:

```ts
{
  role: 'liar',
  category: 'Lugar',
  secret: null
}
```

Esse contrato é importante pra caralho: `secret` é `null` para o Mentiroso. Não “vem preenchido mas a UI ignora”.

## 9. `validateClue`

Responsabilidade: validar envio de pista.

Entrada:

```ts
validateClue({
  roundStatus,
  clueText,
  deadline,
  now,
  alreadySubmitted,
  playerActive
})
```

Erros possíveis:

- `ROUND_NOT_ACCEPTING_CLUES`
- `CLUE_EMPTY`
- `CLUE_TOO_LONG`
- `CLUE_TOO_LATE`
- `CLUE_ALREADY_SUBMITTED`
- `PLAYER_NOT_ACTIVE`

Bloqueio automático de pista óbvia não é obrigatório no MVP.

## 10. `canAdvanceFromClues`

A fase de pistas pode acabar quando:

- todos os jogadores ativos enviaram; ou
- deadline venceu.

Jogador que não respondeu fica inativo na rodada conforme regra funcional.

Se o Mentiroso não enviar pista dentro da tolerância e for considerado inativo, a rodada pode ser resolvida como vitória dos comuns.

## 11. `startDiscussion`

Responsabilidade: mudar fase e definir deadline quando a discussão for cronometrada.

Não existe engine de conversa.

O motor não precisa transcrever, moderar argumento nem dar nota pra cara de pau.

## 12. `validateVote`

Entrada:

```ts
validateVote({
  voterId,
  targetId,
  eligibleTargets,
  stage,
  roundStatus,
  alreadyVoted,
  deadline,
  now
})
```

Regras:

- votante precisa estar ativo;
- alvo precisa ser outro jogador;
- alvo precisa estar elegível;
- um voto por estágio;
- voto dentro do prazo;
- estágio 2 só existe no desempate.

## 13. `resolveVotes`

Responsabilidade: contar votos sem revelar parcial antes da hora.

Entrada:

```ts
resolveVotes({
  eligiblePlayers,
  votes
})
```

Saída conceitual:

```ts
{
  counts: Record<PlayerId, number>,
  topPlayerIds: PlayerId[],
  tied: boolean
}
```

Se apenas um `topPlayerId`, votação resolvida.

Se dois ou mais empatados, existe runoff.

## 14. `resolveRunoff`

Entrada: votos da segunda votação apenas entre empatados.

Se surgir vencedor único, ele é o acusado final.

Se houver novo empate:

```ts
{
  accusedPlayerId: null,
  liarSurvived: true,
  reason: 'SECOND_TIE'
}
```

O Mentiroso sobrevive porque o grupo teve duas chances e conseguiu continuar perdido.

## 15. `resolveAccusation`

Responsabilidade: comparar acusado final com o Mentiroso.

Entrada:

```ts
resolveAccusation({
  accusedPlayerId,
  liarPlayerId
})
```

Saída:

```ts
{
  liarCaught: boolean
}
```

Se `liarCaught = false`, rodada segue direto para pontuação.

Se `true`, abre `liar_guess`.

## 16. `validateLiarGuess`

Somente o Mentiroso pode usar.

Condições:

- rodada em `liar_guess`;
- jogador é `liar_player_id`;
- prazo válido;
- tentativa ainda não enviada.

## 17. `evaluateLiarGuess`

No MVP, a regra canônica é comparação normalizada.

Normalização recomendada:

- trim;
- lowercase;
- remover acentos;
- colapsar espaços;
- aceitar aliases editoriais cadastrados futuramente.

Exemplo:

`" PRAIA "` e `"praia"` devem ser iguais.

Não usar LLM para decidir se “beira-mar” quer dizer “praia” no MVP. Isso cria custo e inconsistência onde um alias resolve.

## 18. `scoreRound`

Pontuação canônica do MVP.

### Jogador comum

- votou corretamente no Mentiroso: `+100`;
- Mentiroso foi descoberto: `+50` de bônus de equipe;
- votou errado: `0` de votação.

Logo, comum que acertou numa rodada resolvida contra o Mentiroso recebe `150`.

### Mentiroso

- sobreviveu à votação: `+200`;
- foi descoberto, mas acertou o segredo: `+150`;
- foi descoberto e errou/expirou: `0`.

Contrato:

```ts
scoreRound({
  players,
  liarPlayerId,
  finalVotes,
  liarCaught,
  liarGuessedSecret
}): RoundScore[]
```

O motor também atualiza estatísticas:

- `correct_votes`;
- `liar_wins`;
- `liar_count`.

## 19. Exemplo canônico de pontuação

Jogadores: Ana, Bruno, Carla, Diego.

Mentiroso: Bruno.

Votos:

- Ana -> Bruno
- Carla -> Bruno
- Diego -> Bruno
- Bruno -> Diego

Bruno foi descoberto e errou o segredo.

Resultado:

```text
Ana   +150
Carla +150
Diego +150
Bruno +0
```

Se Bruno acertasse o segredo:

```text
Ana   +150
Carla +150
Diego +150
Bruno +150
```

Se Diego fosse acusado no lugar de Bruno:

```text
Bruno +200
```

Os comuns recebem apenas seus pontos individuais de voto correto — neste exemplo, ninguém acertou se todos foram em Diego.

## 20. `resolveGameRanking`

Critérios finais:

1. maior pontuação total;
2. maior número de votos corretos;
3. maior número de vitórias como Mentiroso;
4. persistindo empate, vitória compartilhada.

Contrato:

```ts
resolveGameRanking(playerStats): FinalStanding[]
```

## 21. Abandono

### Jogador comum sai durante rodada

Se ainda houver pelo menos 3 ativos e a regra funcional permitir, rodada continua.

Ele não vota nem pontua a partir do momento em que ficou inativo.

### Mentiroso sai durante rodada

Rodada é cancelada.

Não adianta manter todo mundo acusando uma cadeira vazia.

### Host sai

`selectNextHost` escolhe outro membro ativo.

Critério simples inicial: participante ativo há mais tempo.

## 22. Reconexão

`reconnectPlayer(userId, roomId)` recupera o mesmo participante.

O retorno precisa fornecer uma visão segura do estado atual.

Exemplos:

- se ainda está em pista, pode recuperar seu próprio papel;
- se votação já começou, não recebe segredo por acidente só porque reconectou;
- se já votou, não vota de novo.

## 23. Idempotência

Operações críticas precisam aguentar retry de rede:

- `submitClue`;
- `submitVote`;
- `submitLiarGuess`;
- `startRound`;
- `scoreRound`.

Constraints únicas no banco ajudam.

Dois cliques não podem criar dois votos.

## 24. Erros de domínio

Padronizar códigos como:

- `ROOM_NOT_FOUND`
- `ROOM_EXPIRED`
- `ROOM_FULL`
- `NOT_ROOM_MEMBER`
- `NOT_HOST`
- `INSUFFICIENT_PLAYERS`
- `INVALID_ROUND_STATE`
- `CLUE_ALREADY_SUBMITTED`
- `VOTE_ALREADY_SUBMITTED`
- `INVALID_VOTE_TARGET`
- `VOTE_TOO_LATE`
- `NOT_THE_LIAR`
- `LIAR_GUESS_ALREADY_SUBMITTED`

UI traduz isso para copy humana.

## 25. Testes obrigatórios

O motor precisa testar:

- partida com menos de 3 jogadores não inicia;
- Mentiroso não recebe segredo;
- comum recebe segredo;
- mesmo jogador não vira Mentiroso repetidamente quando há alternativa;
- uma pista por jogador;
- voto em si mesmo rejeitado;
- voto duplicado rejeitado;
- empate inicial gera runoff;
- segundo empate salva Mentiroso;
- Mentiroso acusado abre última chance;
- Mentiroso não acusado recebe 200;
- última chance correta recebe 150;
- última chance errada recebe 0;
- ranking e desempate;
- Mentiroso desconectado cancela rodada;
- host desconectado transfere host;
- reconexão não duplica jogador;
- segredo/votos não vazam nos payloads errados.

## 26. Teste de vazamento

Além de teste de regra, precisa existir teste de segurança funcional:

Para cada fase e papel, verificar exatamente quais campos chegam ao cliente.

Exemplo:

```text
Mentiroso + clue_submission -> category SIM, secret NÃO, liar_player_id NÃO
Comum + clue_submission      -> category SIM, secret SIM, liar_player_id NÃO
Todos + reveal               -> category SIM, secret SIM, liar_player_id SIM
```

Esse teste vale ouro. Uma regressão aqui destrói o jogo sem dar erro 500 nenhum.

## 27. Regra final

Se conseguirmos rodar todos esses contratos em teste sem montar uma tela, o jogo tem regra de verdade.

Depois o protótipo pode trocar botão, cor, animação e layout à vontade.

A mentira continua funcionando.