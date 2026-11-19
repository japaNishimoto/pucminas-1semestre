# Ajudo Ocê — guia completo do trabalho

Este guia acompanha o projeto de TIAW desde os primeiros registros disponíveis. Ele reúne a evolução do site, os pedidos recuperados de outras conversas, o funcionamento das telas e o estado de cada entrega. A pasta `Documentacao_Ajudo_Oce` fica dentro de `TIAW`, ao lado do repositório.

| Para consultar | Onde ler |
| --- | --- |
| Central de Ajuda, cadastro do cliente, login, chat, notificações e perfis da equipe | [Central, contas e atendimento](Central_contas_e_atendimento.md) |
| Página inicial, voluntariado, triagem, avaliação, mural, certificados, quiz, segurança digital e conteúdos | [Funcionalidades do projeto](Funcionalidades_do_projeto.md) |
| Acessibilidade, temas, logo, banner, painéis da equipe, menu lateral e linha de leitura sobre o YouTube | [Acessibilidade e interface](Acessibilidade_e_interface.md) |
| Trabalhos desde a primeira solicitação recuperada, revisão dos documentos, gravações, testes e commits | [Histórico, documentação e verificações](Historico_e_verificacoes.md) |
| Código, contas, chat, servidor e integração seletiva na branch de atendimento | [Documentação da branch icaro](Branch_icaro.md) |

## O que existe no site

O **cliente** pode navegar pela página inicial, consultar as dúvidas da Central de Ajuda e abrir a janela do chat como visitante; para enviar mensagens pela interface atual, precisa entrar em uma conta. Também pode criar uma conta com nome, e-mail e senha, entrar com e-mail e senha e sair da conta. Quando está identificado, o chat usa o identificador da conta para mostrar a conversa correspondente. Os botões flutuantes dão acesso ao chat e às opções de leitura nas páginas públicas abrangidas pela navegação compartilhada.

A **equipe** entra por `/administrativo`, com usuário e senha. O atendente tem acesso ao painel de conversas e ao mural. O administrador também gerencia perguntas do quiz. O perfil master pode gerenciar contas da equipe. O menu lateral mostra as opções do perfil, destaca a seção atual e pode ser recolhido no computador.

O projeto também tem página inicial com glossário e podcast, consulta e edição local de pedidos de exemplo na área do voluntário, mural compartilhado, prévia de certificados, triagem, avaliação por estrelas, quiz com pontuação, tutoriais de segurança, relato local de golpes e páginas de conhecimento. Cada fluxo tem um nível diferente de integração. Os capítulos mostram, por exemplo, a diferença entre cadastrar um cliente e cadastrar um voluntário, entre o chat real e a tela de chat da triagem, e entre o resultado funcional do quiz e as telas de ranking e recompensas.

## Como abrir a versão local

Com o Node.js instalado, execute `npm start` na raiz do repositório. No Windows, use `npm.cmd start` se o PowerShell bloquear o executável do npm. Na porta padrão, o site abre em `http://localhost:3000` e o login da equipe fica em `http://localhost:3000/administrativo`. Para criar uma conta de cliente, selecione **Entrar** no cabeçalho público e depois **Criar conta** na tela de acesso. As instruções detalhadas para conferir a interface estão no capítulo de acessibilidade. [Roteiro manual](Acessibilidade_e_interface.md#11-como-conferir-manualmente)

As telas usam HTML, CSS e JavaScript. Na versão local atual, a conta, o atendimento, o quiz e o mural fazem consultas ao servidor Node.js. A triagem, a área pública do voluntário e o relato de golpe usam armazenamento do navegador para os respectivos fluxos. O servidor principal executado por `npm start` fica em `src/servidor-atendimento.js`. O `package.json` dentro de `src/` pertence a uma estrutura anterior de laboratório.

## De onde vieram as informações

Foram recuperadas três conversas anteriores sobre a Central de Ajuda, a documentação e as gravações de teste, e a primeira implementação da acessibilidade. A primeira solicitação encontrada nessas conversas foi a melhoria do cabeçalho e do design do `index` da Central de Ajuda. Para as etapas anteriores a esse pedido, inclusive o desenvolvimento do login e do cadastro, o guia usa o histórico do Git, os documentos da disciplina e o código disponível. A distinção entre essas fontes permite saber quais pedidos foram recuperados e quais entregas foram reconstituídas a partir dos arquivos.

A referência do funcionamento atual é a branch `test` do repositório `pbe-ads-2026-2-p1-tiawfe-5490101-Ajudooce`, no commit `493d89b`. Os caminhos de código nos capítulos partem da raiz desse repositório. O capítulo de histórico distingue registros antigos da situação atual. Conversas que não aparecem no histórico acessível não puderam ser recuperadas. Nesses pontos, o guia descreve o que as fontes do projeto permitem confirmar.
