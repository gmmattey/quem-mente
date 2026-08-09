# Quem Mente? — privacidade e termos de uso (pré-lançamento)

> Documento de produto. Precisa de revisão jurídica antes de produção pública.

## 1. Regra de produto

O Quem Mente? deve coletar o mínimo possível e não transformar uma brincadeira de sala em rede social.

No MVP:

- sem nome real obrigatório;
- sem email obrigatório para jogar;
- sessão anônima do Supabase quando identidade técnica for necessária;
- nickname vale só na sala;
- sem perfil público;
- sem DM;
- sem chat persistente;
- sem upload de foto, vídeo ou áudio;
- sem localização precisa;
- sem lista de contatos;
- sem venda de dados pessoais;
- sem publicidade comportamental dirigida a crianças/adolescentes.

## 2. Dados tratados no MVP

### Técnicos

- `user_id` anônimo;
- sessão;
- sala;
- timestamps;
- eventos técnicos mínimos;
- sinais de segurança/abuso estritamente necessários.

### De jogo

- nickname;
- pistas digitadas;
- votos;
- papel da rodada;
- pontuação;
- participação em sala/rodada;
- tentativa final do Mentiroso.

### Analytics

Seguir `docs/analytics-e-metricas.md`.

Não enviar nickname nem texto das pistas para analytics.

## 3. Pistas são conteúdo do usuário

Pistas existem para a partida, não para virar banco de conteúdo da empresa.

Regra inicial:

- usar a pista para conduzir e resolver a rodada;
- retenção curta;
- não reutilizar pista em publicidade, treino de IA ou banco público sem nova decisão e base adequada;
- remover/expirar junto com dados transitórios da sala quando possível.

## 4. O que não coletar sem nova decisão

- data de nascimento completa;
- documento;
- biometria;
- foto;
- voz;
- localização precisa;
- contatos;
- dados sensíveis;
- perfis comportamentais para publicidade.

Se aferição de idade exigir nova operação de dados, escolher mecanismo proporcional e menos invasivo disponível.

## 5. Finalidades

Dados podem ser usados para:

- criar/entrar em sala;
- distribuir papel individual;
- manter segredo protegido;
- receber pistas e votos;
- calcular resultado;
- manter reconexão;
- impedir voto/ação duplicada;
- moderar abuso básico;
- entender falha/abandono;
- melhorar o jogo;
- cumprir obrigação legal.

## 6. Fornecedores previstos

- Supabase — Auth, Postgres e Realtime;
- Cloudflare — Pages/CDN, proteção e eventual Turnstile;
- fornecedor de publicidade somente se ads forem ativados.

A política pública deve listar o que realmente estiver em uso no lançamento.

## 7. Retenção

Regra inicial:

- salas expiram;
- pistas/votos são transitórios e devem ter retenção curta;
- analytics prefere agregação;
- logs técnicos curtos;
- usuário anônimo inativo pode ser limpo periodicamente;
- histórico permanente só nasce se virar funcionalidade explícita e útil.

Valores exatos serão definidos antes de produção.

## 8. Exclusão e direitos

Antes do lançamento público deve existir caminho simples para:

- solicitar exclusão quando dados forem tecnicamente associáveis ao usuário;
- obter informações sobre tratamento;
- comunicar abuso/privacidade;
- exercer direitos previstos pela legislação aplicável.

Contato público ainda precisa ser definido.

## 9. Crianças e adolescentes

O jogo não será posicionado como produto infantil, mas a mecânica social e simples pode atrair adolescentes e crianças.

Antes da produção pública:

- revisar ECA Digital e orientação vigente da ANPD;
- definir mecanismo proporcional de idade/sinalização;
- avaliar classificação indicativa;
- revisar interação entre usuários;
- manter modo +18 fora do MVP;
- manter publicidade comportamental para menores fora do produto.

Não presumir que “não é para criança” elimina obrigação legal se o acesso for provável.

## 10. Regras essenciais dos Termos de Uso

Os termos públicos devem deixar claro que:

- a pessoa é responsável pelo nickname e pista que envia;
- conteúdo ofensivo, discriminatório, sexual inadequado, ameaçador ou ilegal pode gerar remoção/bloqueio;
- não é permitido usar pista/nickname para expor dado pessoal de terceiro;
- automação, fraude, exploração de falha ou tentativa de acessar segredo/voto de outros pode gerar bloqueio;
- resultado pode ser corrigido em caso de erro/fraude;
- sala/link expira;
- disponibilidade contínua não é garantida, especialmente em beta;
- regras podem evoluir com transparência adequada;
- marca e conteúdo editorial do jogo permanecem protegidos.

## 11. Licença sobre pista

Evitar cláusula de cessão total e eterna.

O produto precisa apenas de autorização limitada para processar/exibir a pista dentro da partida e executar moderação/suporte necessário.

Nada de “sua frase agora é nossa para sempre”.

## 12. Pendências antes de produção

- [ ] controlador e contato;
- [ ] revisão LGPD/ECA Digital atualizada;
- [ ] mecanismo de idade;
- [ ] classificação indicativa;
- [ ] prazos de retenção;
- [ ] canal de exclusão/direitos;
- [ ] política de moderação pública mínima;
- [ ] fornecedores reais;
- [ ] revisão de publicidade;
- [ ] revisão jurídica final.

## 13. Regra final

A pista é do jogo daquela rodada. Não é convite para montar uma rede social, um data lake ou um inferno jurídico.