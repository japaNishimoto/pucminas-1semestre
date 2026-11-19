# Documentação do código da branch icaro

Este guia explica a Central de Ajuda, as contas, o atendimento e os demais arquivos de código existentes na branch `icaro`. Ele está na pasta `TIAW/Documentacao_Ajudo_Oce`, fora do repositório do projeto.

A branch foi aberta na pasta `TIAW/icaro-integracao`. Os caminhos de código neste guia são relativos a essa pasta. A integração seletiva ficou registrada no commit `0fec041` e partiu da versão `173da3e` da `icaro`. As alterações nas páginas de outros integrantes permanecem na branch `test`.

## 1. Como executar

No terminal, entre na pasta `TIAW/icaro-integracao` e execute:

```powershell
node src/servidor-atendimento.js
```

Com a porta padrão, a Central fica em `http://localhost:3000/modulos/atendimento/index.html`. O acesso da equipe fica em `http://localhost:3000/modulos/atendimento/login.html`. A porta pode ser alterada pela variável de ambiente `PORT`. Para interromper o servidor, use `Ctrl+C` no terminal em que ele está em execução.

O servidor da Central usa módulos nativos do Node.js. A branch também contém um laboratório anterior com seu próprio `src/package.json` e `src/index.js`, baseado em JSON Server e Express. O comando acima inicia o servidor de atendimento, que é o necessário para os fluxos da Central descritos neste guia.

## 2. Organização das pastas

```text
icaro-integracao/
└── src/
    ├── servidor-atendimento.js       servidor da Central e das contas
    ├── index.js                      servidor do laboratório anterior
    ├── package.json                  dependências do laboratório anterior
    ├── db/
    │   ├── db.json                   dados do laboratório anterior
    │   └── atendimento/
    │       ├── conteudo.json         conteúdo inicial da Central
    │       └── dados/                dados locais criados durante o uso
    └── public/
        ├── index.html e about.html   páginas do laboratório anterior
        ├── assets/
        │   ├── css/atendimento/      estilos da Central e da equipe
        │   ├── js/atendimento/       scripts da Central e da equipe
        │   ├── css/acessibilidade.css
        │   └── js/acessibilidade.js
        └── modulos/
            ├── atendimento/         páginas da Central e da equipe
            └── login/               laboratório e gerador de certificado
```

O servidor lê os dados locais em `src/db/atendimento/dados/`. Essa pasta é ignorada pelo Git e pode ser criada quando o servidor inicia ou recebe dados. Ela é separada dos dados que a branch `test` usa em `src/db/atendimento/dados/test/`.

## 3. Central de Ajuda

### Objetivo e funcionamento

A Central reúne respostas sobre a plataforma e dá acesso à conta e ao atendimento. A pessoa encontra um banner de apresentação, uma pesquisa e cartões organizados por categoria. As perguntas podem ser abertas individualmente e os botões de **Mais informações** apresentam conteúdo adicional em uma janela.

A pesquisa considera os títulos, as descrições, as perguntas e as respostas. O texto é normalizado para que maiúsculas e acentos não impeçam a busca. O botão de limpeza recupera a lista. A seção **Outros Assuntos** oferece um caminho para o chat. A página também apresenta canais de contato configurados para WhatsApp e composição de e-mail.

O script tenta obter categorias, perguntas, informações e canais do servidor. Se os dados não estiverem disponíveis, a estrutura escrita na página continua servindo como apresentação inicial. Em telas menores, o cabeçalho usa um menu próprio para celular.

| Arquivo | Responsabilidade |
| --- | --- |
| `src/public/modulos/atendimento/index.html` | Estrutura da Central, formulário da conta, janela do chat, banner e canais de contato. |
| `src/public/assets/css/atendimento/central.css` | Estilos do cabeçalho, busca, cartões, janelas e versão móvel. |
| `src/public/assets/js/atendimento/central.js` | Busca, menu móvel, perguntas, janelas de informação, carregamento do conteúdo e abertura do chat. |
| `src/db/atendimento/conteudo.json` | Conteúdo inicial de categorias, perguntas, informações e canais. |
| `src/public/assets/images/atendimento/banner-ajudo-oce.png` | Ilustração usada no banner da Central. |

## 4. Conta do cliente

O botão **Entrar** abre a janela de conta. A pessoa pode escolher entre entrar ou criar uma conta. Para se cadastrar, informa nome, e-mail, senha e confirmação da senha. Há opção de exibir a senha digitada. Após o cadastro aceito, a pessoa já recebe uma sessão e a página apresenta uma saudação com seu primeiro nome. A opção **Sair** encerra a sessão do cliente.

O cliente existente entra com e-mail e senha. O formulário apresenta mensagens quando os dados não passam na validação ou quando o servidor informa erro. O servidor valida o nome, o formato e a unicidade do e-mail e o tamanho da senha. As senhas persistidas pelo servidor são processadas com `scrypt` e salt.

O navegador armazena o token e o perfil na chave `ajudooce-cliente` do `localStorage`. Ao carregar a página, o script verifica a sessão com o servidor. A sessão de cliente é mantida em memória por até sete dias e deixa de existir quando o servidor é reiniciado. A conta de cliente é usada para identificar sua conversa no chat.

| Arquivo | Responsabilidade |
| --- | --- |
| `src/public/assets/js/atendimento/cliente.js` | Abas, validação, envio dos formulários, sessão, saudação e saída. |
| `src/public/assets/css/atendimento/conta.css` | Visual da janela e dos formulários de conta. |
| `src/servidor-atendimento.js` | Cadastro, login, verificação e saída do cliente. |
| `src/db/atendimento/dados/clientes.json` | Arquivo local criado pelo servidor para os registros de clientes. |

O fluxo existente oferece cadastro e acesso com e-mail e senha. O cadastro completo de voluntários com habilidades e disponibilidade é um requisito do projeto geral e não faz parte desse formulário.

## 5. Chat de atendimento

O chat abre pela Central e pelo botão flutuante. A janela apresenta as mensagens e um campo de envio. A pessoa pode fechar a janela pelo botão de fechar ou pelas interações previstas no diálogo. Enquanto o chat está aberto, a página consulta atualizações a cada três segundos.

O visitante recebe um identificador salvo no navegador e pode manter sua conversa nesse navegador. Quando o cliente está autenticado, a conversa usa o identificador da conta. A conversa iniciada como visitante e a conversa identificada pela conta são tratadas separadamente. As mensagens aceitam até 500 caracteres.

O código contém uma opção de resposta automática baseada no conteúdo da Central. A configuração atual usa a resposta da equipe. No painel, um atendente seleciona a conversa e envia a resposta. Um resumo indica mensagens ainda sem resposta da equipe.

| Arquivo | Responsabilidade |
| --- | --- |
| `src/public/assets/js/atendimento/chat.js` | Sessão da conversa, carregamento, atualização, envio e controle da janela. |
| `src/public/assets/css/atendimento/chat.css` | Estilos da janela, mensagens, campo e botões do chat. |
| `src/public/assets/js/atendimento/painel.js` | Lista conversas da equipe, mostra mensagens e envia respostas. |
| `src/public/modulos/atendimento/painel.html` | Tela de atendimento da equipe. |
| `src/db/atendimento/dados/mensagens.json` | Arquivo local das mensagens criado pelo servidor. |

Na integração, o botão flutuante já existente na Central é ocultado depois que o controle compartilhado é criado. Dessa forma, fica um único botão de chat sob o botão de acessibilidade. Se o script de acessibilidade não carregar, o botão original da página continua presente.

## 6. Login e painel da equipe

A equipe entra pela página de login com usuário e senha. O servidor identifica o perfil e retorna um token. O navegador guarda o token em `sessionStorage` com a chave `ajudooce-admin-token`. As páginas da equipe consultam a sessão antes de mostrar o conteúdo.

| Perfil | Acesso disponível nesta branch |
| --- | --- |
| Atendente | Início e painel de atendimento. |
| Administrador | Início e painel de atendimento, com perfil administrativo. |
| Master | Início, atendimento e gerenciamento de usuários da equipe. |

O master cadastra usuários como atendentes ou administradores, pode alterar nome e perfil, redefinir senha e excluir contas permitidas. A conta master tem proteção própria no servidor. A sessão da equipe fica em memória por até oito horas. O projeto atual possui uma credencial master inicial definida no servidor; ela deve ser tratada como configuração de desenvolvimento.

O início do painel apresenta cartões conforme as permissões. O menu lateral mostra as páginas disponíveis e permite abrir ou recolher a navegação. Em telas pequenas, o menu inicia recolhido e o botão no topo permite abri-lo. No computador, a última escolha de aberto ou fechado é guardada durante a sessão do navegador. O atalho de acessibilidade do cliente não é carregado nas páginas da equipe.

| Arquivo | Responsabilidade |
| --- | --- |
| `src/public/modulos/atendimento/login.html` | Formulário de login da equipe. |
| `src/public/modulos/atendimento/inicio.html` | Boas-vindas e área para cartões dos módulos. |
| `src/public/modulos/atendimento/painel.html` | Lista de conversas e formulário de resposta. |
| `src/public/modulos/atendimento/usuarios.html` | Cadastro e gestão de usuários pelo master. |
| `src/public/assets/js/atendimento/login.js` | Envio do formulário de login. |
| `src/public/assets/js/atendimento/admin-comum.js` | Sessão, perfis, menu, resumo das conversas e saída. |
| `src/public/assets/js/atendimento/inicio.js` | Montagem dos cartões de acordo com o perfil. |
| `src/public/assets/js/atendimento/painel.js` | Conversas e respostas da equipe. |
| `src/public/assets/js/atendimento/usuarios.js` | Listagem, cadastro, edição, redefinição de senha e exclusão de usuários. |
| `src/public/assets/css/atendimento/admin.css` | Estilos do login, painel, cartões, menu e formulário de usuários. |
| `src/db/atendimento/dados/usuarios.json` | Arquivo local dos usuários da equipe criado pelo servidor. |

## 7. Acessibilidade da Central

O botão de acessibilidade fica no canto inferior direito, acima do chat. Ele usa o ícone de pessoa e abre um painel com:

- **Tamanho do texto**, de 80% a 150%, em passos de 10%.
- **Tema escuro**, com fundos azuis escuros e texto claro. O botão passa a oferecer o retorno ao tema claro.
- **Alto contraste**, com fundo preto, texto branco e realces amarelos. O botão passa a oferecer o contraste padrão.
- **Espaçamento ampliado**, aplicado ao texto e a controles selecionados.
- **Linha de leitura**, acompanhando ponteiro ou toque e podendo ser movida pelas setas com o controle selecionado.
- **Restauração**, que retorna às preferências padrão.

Tema escuro e alto contraste são alternativas separadas. Ao ativar um, o outro é desligado. As escolhas são guardadas no `localStorage` na chave `ajudooce-acessibilidade` quando o navegador permite armazenamento. O painel e os botões usam Shadow DOM para isolar seus próprios estilos. O CSS da página aplica as cores e o espaçamento ao restante da Central.

Os arquivos são `src/public/assets/js/acessibilidade.js` e `src/public/assets/css/acessibilidade.css`. Nesta branch, o script foi ligado à página da Central. A versão da página inicial com vídeo do YouTube e seu botão específico de controle pertence à outra estrutura do projeto e não existe nesta Central.

## 8. Servidor e rotas

`src/servidor-atendimento.js` entrega os arquivos públicos e atende às operações da Central. Ele usa os módulos `http`, `fs`, `path` e `crypto` do Node.js. O código lê o conteúdo inicial, guarda dados em arquivos JSON locais, cria e verifica sessões em memória e controla permissões da equipe. Há limites de tentativas para login e cadastro e restrições no tamanho das requisições.

| Rota | Uso |
| --- | --- |
| `GET /categorias`, `/perguntas`, `/informacoes` e `/canaisAtendimento` | Conteúdo da Central. |
| `POST /api/cliente/cadastro` e `/api/cliente/login` | Cadastro e autenticação do cliente. |
| `GET /api/cliente/me` e `POST /api/cliente/logout` | Verificação e saída da conta do cliente. |
| `POST /api/login`, `GET /api/me` e `POST /api/logout` | Entrada, sessão e saída da equipe. |
| `GET /api/atendimento/resumo` | Contagem de conversas com mensagens pendentes. |
| `/api/usuarios` e `/api/usuarios/:usuario` | Operações de gerenciamento da equipe pelo master. |
| `GET` e `POST /mensagens` | Consulta e envio de mensagens, com verificações da conversa e da sessão quando necessárias. |

As chamadas da Central, conta, chat e equipe usam a origem da própria página quando ela é servida por HTTP ou HTTPS. Isso permite usar a porta configurada no servidor. Ao abrir o arquivo diretamente, os scripts mantêm o endereço local padrão como alternativa.

## 9. Código anterior também presente na branch

Além da Central, a branch conserva arquivos de um laboratório anterior:

- `src/index.js`, `src/package.json` e `src/db/db.json` implementam um exemplo separado baseado em JSON Server.
- `src/public/index.html`, `src/public/about.html`, `src/public/modulos/login/login.html`, `src/public/modulos/login/index.html`, `src/public/assets/js/login.js` e `src/public/assets/css/style.css` compõem telas e código de login desse laboratório. Esse fluxo é diferente das contas de cliente e equipe da Central.
- `src/public/modulos/login/gerador_de_certificado/` contém um gerador com formulário de nome, horas e atividade, atualização da prévia, impressão pelo navegador e opção de compartilhar mensagem e link. As horas são informadas manualmente.
- As imagens em `src/public/assets/images/` incluem recursos desses exemplos e o banner de atendimento. As pastas `docs/` e `presentation/` contêm os modelos e documentos do projeto da disciplina.

Esses arquivos anteriores foram mantidos na branch. A integração desta etapa se concentrou na Central e na área de atendimento.

## 10. O que foi integrado e como foi conferido

Foram adaptados para a estrutura de `icaro` o painel de acessibilidade, os temas e o chat flutuante da Central, o visual da página inicial da equipe e o menu lateral. Os links do menu usam as áreas realmente existentes nesta branch. As chamadas de atendimento também passaram a respeitar a origem e a porta do servidor.

Os arquivos JavaScript alterados passaram por `node --check` e o diff foi conferido com `git diff --check`. Uma execução isolada com dados fictícios verificou carregamento da Central e dos recursos de acessibilidade, cadastro e sessão de cliente, login da equipe, envio de uma mensagem, resposta e consulta do histórico. Foram feitas capturas da Central em tema escuro e do painel com sessão simulada em desktop.

As capturas não substituem testes em celular real, em todas as opções de acessibilidade ou com o público do projeto. O servidor local e as contas de exemplo são uma implementação de desenvolvimento que precisa ser considerada em conjunto com as restrições da disciplina.
