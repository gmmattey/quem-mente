# De Migué — jornada e UX/UI

> Isso aqui não é aplicativo de produtividade com gravata colorida. É jogo de festa. A tela organiza a rodada e sai da frente para a paranoia acontecer entre as pessoas.

## 1. Ideia visual em uma frase

**Pouca coisa por tela, informação grande, transições rápidas e clima de “todo mundo sabe alguma coisa que talvez você não saiba”.**

## 2. Princípio de UX

O ciclo principal é:

**entrou → descobriu o papel → deu pista → desconfiou → votou → revelou → quis outra.**

Cada fase tem uma tensão principal.

## 3. Home

Prioridade:

1. **Criar sala**;
2. **Entrar em sala**;
3. **Como joga** como secundário.

Frase possível:

> **Tem alguém de migué nessa mesa.**

Sem hero SaaS, três cards de benefício ou texto de marketing genérico.

## 4. Entrada na sala

Poucos campos:

- código quando necessário;
- apelido;
- entrar.

Link de convite deve preencher o máximo possível automaticamente.

## 5. Sala de espera

Mostrar:

- código grande;
- compartilhar/copiar;
- jogadores;
- Host;
- configurações resumidas;
- CTA **Começar partida** para Host.

Nada de painel administrativo.

## 6. Preparação da rodada

Transição curta para criar expectativa.

Não revelar papel/segredo sem ação consciente da pessoa se houver risco de alguém ao lado ver a tela.

## 7. Papel secreto

Proteção inicial:

**Só você pode ver isso.**

CTA:

**Ver meu papel**

### Comum

Categoria discreta + segredo enorme.

### Mentiroso

**VOCÊ É O MENTIROSO**

Categoria abaixo.

Texto curto:

**Finge que sabe.**

A pessoa precisa sentir um micro “fodeu”.

## 8. Pista

Uma ação principal:

**Manda tua pista.**

Campo grande, contador discreto e cronômetro quando aplicável.

Depois do envio:

**Agora sustenta essa história.**

## 9. Pistas reveladas

Entram em sequência.

Mostrar apenas:

- jogador;
- pista;
- identificação suficiente.

A entrada pode lembrar papel/carta, mas sem transformar tudo em coleção de cards pesados.

## 10. Discussão

O app não substitui a conversa.

Mostrar:

- pistas;
- cronômetro se existir;
- CTA **Bora votar**.

A atenção deve voltar para as pessoas.

## 11. Votação

Jogadores grandes e fáceis de tocar.

Não mostrar o próprio jogador como opção.

Selecionou Marcelo:

**Acusar Marcelo**

Confirmação:

**Vai de Marcelo mesmo?**

Voto enviado trava.

## 12. Espera da votação

Mostrar progresso, nunca voto parcial:

> **4 de 6 já votaram.**

Nada de “Marcelo tem 3 votos” antes do fechamento.

## 13. Empate

Primeiro empate:

- segundo turno entre empatados;
- tela deixa isso óbvio sem explicar um regulamento inteiro.

Segundo empate:

- Mentiroso sobrevive;
- reveal segue.

## 14. Revelação

É o grande momento teatral.

Sequência:

1. votos aparecem;
2. mais votado ganha foco;
3. pausa curta;
4. identidade real aparece;
5. segredo é mostrado.

Se acertaram:

**Pegaram o safado.**

Se erraram:

**Vocês condenaram um inocente.**

## 15. Última chance

Se o Mentiroso foi pego:

**Ainda dá pra estragar a festa.**

Pergunta:

**Qual era o segredo?**

15 segundos.

## 16. Resultado da rodada

Pontuação sem planilha.

Mostrar ganhos com linguagem rápida.

Destaques possíveis:

- pegou o Mentiroso;
- caiu no papo;
- acertou o segredo mesmo ferrado;
- acusou inocente.

## 17. Resultado final

Campeão em destaque + ranking curto.

Destaques só quando os dados sustentarem:

- melhor caçador;
- melhor blefador;
- mais acusado injustamente.

CTAs:

- **Revanche**;
- **Compartilhar**.

## 18. Revanche

Manter sala, jogadores e configurações.

Nova partida em no máximo dois toques.

## 19. Compartilhamento

Situação precisa funcionar sozinha.

Exemplos:

> “Fiquei de migué a rodada inteira e ninguém percebeu.”

> “Todo mundo acusou o Marcelo. O Mentiroso era o Pedro.”

Marca pequena, história grande.

## 20. Copy

Curta, falada e situacional.

Evitar voz de IA/marketing.

Direções:

- “Tem alguém de migué nessa mesa.”
- “Finge que sabe.”
- “Manda tua pista.”
- “Vai de Marcelo mesmo?”
- “Pegaram o safado.”
- “Mais uma?”

Não repetir `de migué` em toda tela só porque é o nome.

## 21. Anti-template

Não usar como padrão:

- cards em excesso;
- bento grid;
- glassmorphism;
- glow;
- degradê roxo/azul;
- hero SaaS;
- mascote genérico;
- fonte padrão de produto de IA.

Ver `docs/regras-design-e-copy.md`.

## 22. Mobile e plataformas

Design nasce mobile-first, referência 390×844 e mínimo 360 px.

Considerar desde o começo:

- safe areas;
- teclado;
- botão voltar;
- compartilhamento nativo;
- deep links;
- Web/PWA;
- Android;
- iOS.

Uma UI principal, adaptações por plataforma quando necessárias.

## 23. Movimento

Movimento serve suspense:

- papel descoberto;
- pistas entrando;
- voto registrado;
- reveal;
- resultado.

Suspense curto é tensão. Longo é lentidão.

## 24. Estados de erro

- sala cheia;
- código inválido;
- apelido repetido;
- jogador caiu;
- jogador voltou;
- Host mudou;
- tempo acabou;
- pista não enviada;
- empate;
- Mentiroso desconectou.

Resolver com comunicação humana, não modal gigante.

## 25. Critério final

A jornada está boa quando uma pessoa sem explicação consegue criar/entrar, entender o papel, mandar pista, votar, entender a revelação e pedir revanche.

Se o grupo fica olhando mais para a interface do que uns para os outros, fizemos merda.