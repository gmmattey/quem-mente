# Quem Mente? — segurança, idade e moderação

> Aqui o maior risco não é um hacker de filme. É gente digitando merda, tentando espiar segredo ou usando a sala como desculpa pra encher o saco dos outros.

## 1. Superfície de risco do MVP

Principais riscos:

- nickname ofensivo;
- pista ofensiva/sexual/discriminatória;
- exposição de dado pessoal de terceiro;
- tentativa de descobrir o segredo pelo cliente;
- tentativa de ver voto parcial;
- voto duplicado;
- bot/abuso de sala;
- jogador removido tentando retornar em loop;
- spam de criação de sala;
- abuso em links públicos;
- menores em ambiente com conteúdo inadequado.

## 2. O que reduz risco por design

O MVP não terá:

- DM;
- chat livre persistente;
- upload de mídia;
- perfil público;
- feed;
- busca de usuários;
- amizade/seguidores;
- voz/vídeo hospedados;
- localização.

Isso não é falta de feature. É economia de escopo e de problema.

## 3. Nickname

- limite curto;
- filtro de termos claramente abusivos;
- sem nome global persistente por padrão;
- host pode remover participante;
- nickname não pode se passar por mensagem oficial/sistema;
- nickname não deve aceitar URL clicável.

## 4. Pistas

Pista precisa ter:

- limite de caracteres;
- normalização básica;
- filtro mínimo de conteúdo claramente proibido;
- possibilidade de ocultar/bloquear termos críticos;
- nenhuma renderização de HTML enviado pelo jogador;
- sem link clicável;
- sem markdown rico no MVP.

### Conteúdo proibido

Bloquear/moderar, quando detectado:

- ameaça real;
- discurso de ódio;
- sexualização de menor;
- dado pessoal exposto com intenção abusiva;
- incentivo claro a violência/crime;
- spam/link malicioso;
- assédio grave.

Palavrão entre amigos não precisa transformar o app numa freira. O foco é dano, não moralismo automático.

## 5. Host

No MVP o host pode:

- remover jogador no lobby;
- encerrar sala;
- iniciar quando requisitos forem cumpridos.

Durante rodada ativa, remoção precisa respeitar regras funcionais para não quebrar o estado.

Host não ganha acesso administrativo a:

- segredo de outros;
- papel de outros;
- voto parcial;
- service key;
- ferramentas internas.

## 6. Integridade do segredo

- `liar_player_id` protegido;
- `secret_id` protegido;
- RPC individualizado para papel;
- cliente comum não recebe papel dos outros;
- Mentiroso nunca recebe segredo escondido no payload;
- realtime não transmite segredo;
- RLS fechado;
- service role fora do frontend;
- endpoint de debug não existe em produção.

## 7. Integridade da votação

- um voto por jogador/estágio;
- sem auto-voto quando regra proíbe;
- parcial nunca visível;
- segundo turno limitado aos elegíveis;
- resolução autoritativa;
- voto repetido não cria duplicata;
- reconexão mantém identidade.

## 8. Idade

O Quem Mente? não é direcionado a crianças, mas pode ser atraente a adolescentes e crianças pela natureza social.

Antes de produção pública:

1. revisar ECA Digital e orientação vigente da ANPD;
2. avaliar mecanismo confiável/proporcional de aferição/sinalização etária;
3. avaliar classificação indicativa;
4. verificar regras específicas para interação entre usuários;
5. manter conteúdo base apropriado a público geral/adolescente;
6. manter pacote +18 fora até revisão separada.

Não usar autodeclaração de 18 anos como única resposta sem validar se atende à regra aplicável naquele momento.

## 9. Conteúdo +18 futuro

Só pode existir depois de decisão explícita.

Se um dia entrar:

- pacote isolado;
- não ativado por padrão;
- idade tratada de forma adequada;
- sem mistura com conteúdo geral;
- revisão jurídica/classificação;
- ads compatíveis;
- compartilhamento sem preview sexual explícito.

## 10. Publicidade

No lançamento inicial: preferencialmente desligada.

Depois:

- somente entre partidas/resultado final;
- nunca durante papel, pista, discussão, votação ou revelação;
- sem perfilamento publicitário de menores;
- categorias sensíveis bloqueadas;
- impacto na revanche medido.

## 11. Rate limit

Criar limites em:

- criação de sala;
- tentativas de entrar em código inexistente;
- troca repetitiva de nickname;
- envio de pista;
- voto;
- tentativa final;
- geração de sessões anônimas.

Turnstile entra quando necessário, não como decoração.

## 12. Denúncia e bloqueio

No MVP privado entre amigos, sistema pesado de denúncia não é requisito inicial.

Antes de escala pública, prever:

- denunciar nickname/pista;
- bloquear reincidência técnica quando possível;
- registrar somente o necessário para investigar;
- não expor ao denunciante dados do denunciado.

## 13. Incidente

Em suspeita de vazamento/abuso:

1. fechar vetor;
2. preservar logs mínimos;
3. identificar escopo;
4. avaliar obrigação de comunicação conforme legislação vigente;
5. corrigir de forma rastreável;
6. registrar causa raiz.

## 14. Checklist de segurança

- [ ] RLS completo;
- [ ] segredo impossível de consultar por cliente não autorizado;
- [ ] papel individual;
- [ ] voto secreto;
- [ ] service key ausente do bundle;
- [ ] XSS em nickname/pista testado;
- [ ] HTML do usuário escapado;
- [ ] sala expira;
- [ ] reconexão não duplica jogador/voto;
- [ ] host transferido de forma segura;
- [ ] rate limits;
- [ ] dependências sem falha crítica conhecida;
- [ ] idade/classificação revisadas;
- [ ] privacidade/termos publicados;
- [ ] fluxo de exclusão/direitos definido.

## 15. Regra final

O jogo é sobre desconfiar do amigo. Não sobre desconfiar se o backend entregou o segredo pra qualquer maluco com DevTools.