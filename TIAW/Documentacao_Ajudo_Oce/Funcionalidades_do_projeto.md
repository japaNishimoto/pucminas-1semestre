# Funcionalidades do projeto

[Voltar ao guia](Guia_das_alteracoes.md)

O Ajudo Ocê foi concebido para apoiar pessoas com dificuldades no uso da tecnologia. Os módulos cobrem aprendizagem, segurança digital, atendimento e trabalho voluntário. As descrições abaixo refletem a branch `test` e indicam até onde cada fluxo funciona.

## Página inicial e aprendizagem

O endereço inicial do servidor leva à página do cliente. Ela apresenta o projeto, atalhos para a Central, quiz e dicas de segurança, além de um glossário com exemplos do dia a dia. A gaveta do glossário permite escolher entre navegador, internet, hardware e aplicativo. O conteúdo também gira automaticamente. A opção **Ouvir explicação** usa a voz em português do navegador, quando disponível. A rotação pausa durante a narração. A página inclui um podcast incorporado do YouTube sobre segurança digital e um link para a cartilha de segurança.

O conteúdo introdutório da página e a área de voluntariado vieram da entrega de Kayllon, registrada em `be56c28`. O layout final da página inicial e o cabeçalho compartilhado podem ser vistos em `src/public/modulos/Kayllon/usuario.html`, `src/public/assets/css/Kayllon/usuario.css` e `src/public/assets/js/Kayllon/usuario.js`. A adaptação da linha de leitura sobre o podcast está no capítulo de interface. [Acessibilidade e interface](Acessibilidade_e_interface.md#9-última-alteração-linha-de-leitura-sobre-o-youtube)

## Voluntariado e pedidos

### Área do voluntário

O voluntário encontra pedidos de exemplo. Pode pesquisar por palavras no título, resumo, descrição ou etiquetas e filtrar os urgentes. A tela exibe detalhes e um gráfico baseado nos itens disponíveis. O formulário permite editar prioridade e etiquetas. Essas mudanças ficam no navegador, em `localStorage`. O botão **Ajudar** ainda está desabilitado, e os itens dessa área não são enviados automaticamente ao mural da equipe.

Arquivos principais `src/public/modulos/Kayllon/index.html` e `src/public/assets/js/Kayllon/script.js`. O guia de avaliação nessa pasta descreve cenários manuais para o módulo.

### Mural da equipe

O mural, que aparece no histórico em `492850a`, usa três colunas. **Disponíveis** reúne as solicitações que aguardam atendimento. **Em andamento** identifica as que foram iniciadas. **Concluídas** registra as que foram encerradas. A equipe pode mover cartões para frente ou para trás, remover itens e adicionar um exemplo pela interface. O mural verifica a sessão da equipe e usa `/api/mural`, com dados compartilhados pelo servidor da instalação. Na inicialização, o módulo pode importar pedidos do armazenamento antigo do navegador. O mural funciona com seus próprios dados. A triagem e a área pública do voluntário ainda não alimentam esse fluxo automaticamente.

Arquivos principais `src/public/modulos/Guilherme/mural_de_certificados/index.html`, `src/public/assets/js/Guilherme/mural_de_certificados/script.js` e `src/db/mural/conteudo.json`.

### Certificados

O gerador permite preencher nome, tipo de atividade e horas e acompanhar a prévia. Com os campos preenchidos, chama a impressão do navegador. É possível salvar um PDF quando o navegador oferece essa opção. O compartilhamento usa texto ou link, via recurso nativo ou área de transferência. As horas são preenchidas pela pessoa que usa a tela. O gerador não confere essas horas contra o histórico de atendimento nem envia um PDF pronto.

Arquivos principais `src/public/modulos/Guilherme/gerador_de_certificado/index.html` e `src/public/assets/js/Guilherme/gerador_de_certificado/script.js`.

## Triagem e avaliação do atendimento

A **triagem** foi registrada em `4b56e3a`. O formulário passa por dificuldades na internet, redes sociais, um aviso de etapa em desenvolvimento e um campo para descrever o caso. As respostas ficam temporariamente na sessão do navegador. Após terminar, a página leva à tela de chat do próprio fluxo, que ainda é um protótipo. As respostas da triagem não são transferidas para o chat principal. O ajuste de responsividade em `b9e654f` permite que textos longos quebrem dentro das opções quando o espaço diminui, inclusive com texto ampliado.

Arquivos principais `src/public/modulos/Pedro/Filtro/index.html`, `src/public/modulos/Pedro/Filtro/chat.html`, `src/public/assets/js/Pedro/Filtro/triagem.js` e `src/public/assets/css/Pedro/Filtro/style.css`.

A **avaliação** entrou em `a879972`. O cliente escolhe de uma a cinco estrelas com o ponteiro ou teclado e recebe confirmação na interface. O código emite um evento no navegador. A avaliação ainda não é salva no servidor nem vinculada a uma conversa específica.

Arquivos principais `src/public/modulos/Pedro/Avaliar_Chat/index.html` e `src/public/assets/js/Pedro/Avaliar_Chat/script.js`.

## Quiz, resultados e gestão de perguntas

O quiz aparece em `d1b4268`. A implementação evoluiu com o registro de resultado em `6b7699b` e o trabalho visual das telas de resultados, ranking e recompensas em `589ca8d`.

1. O usuário abre o quiz pelo menu **Aprender** ou pelos atalhos.
2. A página consulta `/api/quiz/perguntas` e apresenta perguntas de múltipla escolha. A experiência mostra o progresso, feedback sobre a resposta e pontuação.
3. Ao final, o script registra o resultado em `/api/quiz/resultados` e guarda identificadores do jogador e do resultado. A tela seguinte recupera a pontuação e a porcentagem.
4. A área de perguntas da equipe permite listar, cadastrar, editar e excluir perguntas para os perfis administrador e master.

Ranking e recompensas têm telas, mas seus scripts na branch conferida estão vazios. O formato de múltipla escolha difere do verdadeiro ou falso previsto no requisito original RF-010.

Arquivos principais `src/public/modulos/Willer/quiz/`, `src/public/modulos/Willer/Resultados_Estilização/`, `src/public/assets/js/Willer/` e `src/db/quiz/conteudo.json`. O arquivo de trabalho `src/db/quiz/dados.json` é gerado e ignorado pelo Git.

## Segurança digital e relato de golpe

O módulo de Gustavo reuniu tutoriais e relatos na integração `52ea3f1`.

- **Tutoriais.** A página `src/public/modulos/Gustavo/game.html` apresenta cartões interativos com exemplos de segurança e uso da tecnologia. A atividade que calcula a força de uma senha roda no navegador e faz parte do exercício.
- **Registro.** Em `src/public/modulos/Gustavo/index.html`, a pessoa preenche um relato de golpe. O script guarda os dados no navegador e abre uma tela de confirmação em `concluido.html`. A confirmação exibe o relato e conteúdos de exemplo. Esses dados ainda não formam uma base de relatos compartilhada nem geram estatísticas em tempo real.
- **Tela avulsa de login.** `src/public/modulos/Gustavo/login.html` tem uma interface antiga de entrar e cadastrar, mas depende de um script ausente. A conta integrada ao atendimento é a da Central. [Central, contas e atendimento](Central_contas_e_atendimento.md#cadastro-e-login-do-cliente)

## Área de conhecimento

As páginas de Rayssa em `src/public/modulos/Rayssa/` apresentam a área de conhecimento e de cuidados de segurança digital. Na versão integrada à branch `test`, há links e componentes de carrossel, com temas que ainda apontam para endereços vazios. A branch `origin/Rayssa` guarda uma versão mais desenvolvida, com páginas e dados adicionais sobre segurança, finanças, navegação na internet e organização de dispositivos. Ela é distinta de `origin/rayssa`, que foi integrada. Veja o histórico em `f31f73f`, `f3ea6f3` e `7d0ef94`.

## Outras partes previstas

Os documentos da disciplina preveem cadastro completo e histórico do voluntário, agendamento, acompanhamento de horas, um modo sem distrações e atendimento com limite de tempo definido. Os fluxos atuais não cobrem esses requisitos integralmente. Por exemplo, a prévia do certificado usa horas informadas manualmente, e a atualização periódica do chat não garante um prazo para a resposta humana. O [histórico de verificações](Historico_e_verificacoes.md) mantém separados os testes executados, os resultados parciais e os casos planejados.
