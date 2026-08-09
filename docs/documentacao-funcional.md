# De Migué — documentação funcional

> Um jogo social de blefe, cara de pau e paranoia coletiva. Todo mundo sabe o segredo. Menos uma pessoa, que precisa fingir que sabe.

## 1. O que é

**De Migué** é um jogo multiplayer curto para amigos, presencialmente ou à distância.

Quase todos os jogadores recebem o mesmo segredo.

Uma pessoa é o **Mentiroso** e recebe apenas a categoria.

Os comuns precisam dar pistas que provem que conhecem o segredo sem entregá-lo. O Mentiroso precisa blefar.

## 2. Objetivo

### Jogadores comuns

Descobrir quem é o Mentiroso sem entregar o segredo.

### Mentiroso

Sobreviver à votação. Se for pego, ainda pode tentar adivinhar o segredo.

## 3. Jogadores

- mínimo: 3;
- recomendado: 4–8;
- máximo MVP: 10;
- sem bots no MVP.

## 4. Criação da sala

O criador vira Host.

Configurações:

- 3, 5 ou 7 rodadas;
- pacote/categorias;
- tempo de pista;
- discussão com tempo ou livre.

Entrada por código/link.

Apelido apenas. Sem login obrigatório.

## 5. Distribuição do papel

O sistema escolhe:

- categoria;
- segredo;
- Mentiroso.

### Jogador comum

Vê:

- categoria;
- segredo.

Exemplo:

**Categoria:** Lugar  
**Segredo:** Praia

### Mentiroso

Vê:

- papel: Mentiroso;
- categoria;
- `secret = null`.

Exemplo:

**VOCÊ É O MENTIROSO**  
**Categoria: LUGAR**

O segredo nunca deve chegar ao cliente do Mentiroso antes da revelação.

## 6. Pistas

Cada jogador envia **uma pista curta e indireta**.

A pista não pode ser o próprio segredo.

A interface não precisa policiar semântica complexa no MVP, mas o conteúdo editorial pode registrar termos óbvios para playtest.

## 7. Ordem das pistas

Pistas aparecem em ordem aleatória.

Padrão inicial: até 30 segundos por jogador para enviar.

A pista só fica visível ao grupo quando a fase de revelação abrir.

## 8. Discussão

Depois das pistas, o grupo conversa.

A discussão acontece fora do app — presencialmente ou em chamada externa.

Modo inicial:

- 60 segundos; ou
- livre, avançado pelo Host.

O app não precisa de chat, áudio ou vídeo.

## 9. Votação

Todos votam secretamente em quem acham que é o Mentiroso.

O Mentiroso também vota.

Não mostrar contagem parcial.

Resultado aparece de uma vez.

## 10. Empate

### Primeiro empate

Segundo turno apenas entre os empatados.

### Segundo empate

Ninguém é eliminado e o Mentiroso sobrevive à rodada.

Nada de sorteio escondido.

## 11. Revelação

Após votação:

- revelar mais votado;
- revelar quem era o Mentiroso;
- revelar o segredo;
- mostrar votos;
- resolver pontuação.

Se o Mentiroso não foi o mais votado, ele vence a rodada.

## 12. Última chance

Se o Mentiroso foi descoberto:

- recebe 15 segundos;
- tenta adivinhar o segredo;
- backend avalia a resposta.

A UI nunca decide sozinha se a resposta está correta.

## 13. Pontuação canônica

### Jogadores comuns

- votou corretamente no Mentiroso: **+100**;
- grupo pegou o Mentiroso: **+50** de bônus coletivo;
- voto errado: **0**.

Quem votou certo e o grupo pegou o Mentiroso recebe **150 pontos** na rodada.

### Mentiroso

- sobreviveu à votação: **+200**;
- foi descoberto e acertou o segredo: **+150**;
- foi descoberto e errou: **0**.

## 14. Escolha do Mentiroso

Sorteio balanceado.

Evitar repetir alguém enquanto outros ainda não foram Mentiroso quando possível.

Nunca permitir a mesma pessoa como Mentiroso três vezes seguidas.

## 15. Fim da partida

Mostrar:

- campeão;
- ranking;
- pontos;
- votos corretos no Mentiroso;
- vitórias como Mentiroso;
- destaques que os dados realmente sustentarem;
- revanche;
- compartilhar.

## 16. Desempate final

1. maior pontuação;
2. mais votos corretos no Mentiroso;
3. mais vitórias como Mentiroso;
4. persistindo empate, vitória compartilhada.

## 17. Revanche

Manter:

- sala;
- jogadores;
- configurações.

Trocar segredo e seleção de papel.

Máximo de dois toques para recomeçar.

## 18. Categorias do MVP

- lugares;
- comidas;
- animais;
- profissões;
- objetos;
- filmes e séries;
- situações do dia a dia.

Outras entram depois do playtest.

## 19. Conteúdo

Cada segredo deve ter:

- categoria;
- segredo;
- dificuldade;
- possíveis pistas óbvias para revisão editorial;
- collision group quando houver conteúdo parecido;
- status editorial.

Segredo bom permite pista indireta para quem sabe e blefe plausível para quem não sabe.

## 20. Dificuldade

### Fácil

Conhecido por quase todo mundo, várias pistas possíveis.

### Médio

Conhecido, mas exige mais cuidado.

### Difícil

Ainda justo, porém com menos pistas naturais.

## 21. Desconexão

### Antes da distribuição

Jogador pode ser removido normalmente.

### Depois do início

Esperar até 60 segundos para reconexão.

Se Mentiroso não volta, cancelar a rodada.

Se comum não volta, excluir da votação desde que ainda existam pelo menos 3 jogadores ativos.

Host pode ser transferido.

## 22. Inatividade

Pista pode ter pequena tolerância adicional.

Jogador inativo não ganha pontos da rodada.

Se o Mentiroso abandona/inativa de forma que a rodada não possa seguir, comuns vencem a rodada conforme regra de abandono definida na implementação.

## 23. Nickname e moderação

No MVP:

- filtro básico;
- limite de tamanho;
- escapar/sanitizar toda entrada;
- sem perfil público persistente obrigatório.

Relato/denúncia mais complexo pode vir depois conforme uso real.

## 24. Compartilhamento

Convite é parte central do produto.

Após partida, compartilhar situações que façam sentido sozinhas:

> “Fiquei de migué a rodada inteira e ninguém percebeu.”

> “Todo mundo acusou o Marcelo. O Mentiroso era o Pedro.”

## 25. Monetização

### Grátis

- jogo principal;
- salas;
- categorias básicas;
- compartilhamento.

### Publicidade

Somente entre partidas ou pausas naturais.

Nunca durante pista, discussão, voto ou reveal.

### Pago futuro

- remover anúncios;
- packs de temas;
- configurações extras;
- salas especiais;
- histórico/estatísticas;
- conteúdo customizado quando seguro.

Nunca vender vantagem competitiva.

## 26. Fora do MVP

- chat;
- voz/vídeo;
- clãs;
- inventário;
- skins;
- moeda virtual;
- ranking mundial complexo;
- sistema social pesado;
- modo +18;
- dois Mentiroso/Modo Caos;
- IA gerando conteúdo em tempo real sem revisão.

## 27. Jornada resumida

**Home → Criar/Entrar → Sala → Configurar → Papel secreto → Pista → Pistas reveladas → Discussão → Votação → Revelação → Última chance → Pontuação → Próxima rodada → Resultado final → Revanche.**

## 28. Multiplataforma

Uma base de código deve gerar:

- Web/PWA;
- Android;
- iOS.

Regra, conteúdo e estado compartilhados. Diferenças de canal ficam em adapters conforme a fundação do Auê Games.

## 29. Autoridade do backend

O navegador não decide:

- quem é Mentiroso;
- qual é o segredo;
- resultado da votação;
- empate;
- pontuação;
- acerto da última chance;
- avanço autoritativo de fase.

Informação secreta nunca vai para quem não deve recebê-la.

## 30. Quando está funcionando

**De Migué** funciona quando:

- a pessoa entende rápido;
- o Mentiroso sente que tem chance de blefar;
- os comuns não entregam o segredo sem querer;
- a discussão acontece naturalmente;
- a revelação gera reação;
- o grupo pede revanche;
- convidado depois vira Host.

A tecnologia é só o garçom. A diversão acontece na mesa.