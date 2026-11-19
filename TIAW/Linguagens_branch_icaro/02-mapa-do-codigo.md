# Mapa dos arquivos de código — icaro

Os caminhos são relativos à raiz do repositório. A lista abrange os arquivos de fonte e configuração em `src` que são versionados no Git, e usa o conteúdo atual da cópia analisada. O nome das funções foi extraído das declarações `function`; é um índice para leitura, não uma prova de que todas elas sejam chamadas.

- **`src/README.md`** — Documento Markdown de orientação ou descrição do projeto.

- **`src/db/atendimento/.gitignore`** — Regras de arquivos que o Git deve ignorar nesta pasta.

- **`src/db/atendimento/conteudo.json`** — Conteúdos estruturados da Central de Ajuda, como categorias, perguntas e canais.

- **`src/db/db.json`** — Dados de exemplo do servidor de laboratório.

- **`src/index.js`** — Servidor de exemplo do JSON Server; lê o arquivo db/db.json e expõe seus dados por HTTP.

- **`src/package.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/about.html`** — Página HTML com o título “Document”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `./assets/css/style.css`; JS `./assets/js/login.js`.

- **`src/public/assets/css/acessibilidade.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/admin.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/central.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/chat.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/conta.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/js/acessibilidade.js`** — Implementa o painel de acessibilidade, preferências visuais e linha de leitura. Funções declaradas identificadas: `restaurarTexto`, `ajustarTexto`, `aplicar`, `fechar`.

- **`src/public/assets/js/atendimento/admin-comum.js`** — Compartilha autenticação e navegação das telas da equipe. Funções declaradas identificadas: `obterToken`, `guardarToken`, `limparToken`, `podeAcessar`, `requisitar`, `exigirLogin`, `sair`, `criarSelo`, `mostrarResumo`, `atualizarResumo`, `montarMenu`, `prepararMenuLateral`, `atualizar`, `iniciarPagina`.

- **`src/public/assets/js/atendimento/central.js`** — Carrega e apresenta categorias, perguntas, busca e informações da Central de Ajuda. Funções declaradas identificadas: `normalizarTexto`, `criar`, `clicouFora`, `rotularBotoesInformacoes`, `filtrarPerguntas`, `configurarBusca`, `configurarMenu`, `configurarModalInformacoes`, `transformacao`, `cancelarAnimacao`, `fechar`, `configurarChat`, `montarCategoria`, `carregarDados`.

- **`src/public/assets/js/atendimento/chat.js`** — Abre o chat, envia e consulta mensagens e identifica a sessão da conversa. Funções declaradas identificadas: `clienteLogado`, `identificarSessao`, `cabecalhosCliente`, `saudacao`, `tratarSessaoExpirada`, `criarFalha`, `obterSessao`, `normalizar`, `formatarHora`, `mostrarMensagem`, `rolarParaFim`, `mostrarDigitando`, `mostrarAviso`, `salvarMensagem`, `carregarHistorico`, `carregarFaq`, `gerarResposta`, `iniciar`, `atualizar`, `enviar`, `abrir`.

- **`src/public/assets/js/atendimento/cliente.js`** — Gerencia a sessão da conta do cliente e os formulários de conta existentes na Central. Funções declaradas identificadas: `ler`, `gravar`, `limpar`, `primeiroNome`, `atualizarCabecalho`, `mostrarAba`, `abrirModal`, `clicouFora`, `chamar`, `enviar`, `conferirSessao`.

- **`src/public/assets/js/atendimento/inicio.js`** — Apresenta as opções do painel conforme as permissões da equipe. Funções declaradas identificadas: `iniciar`.

- **`src/public/assets/js/atendimento/login.js`** — Envia os dados de acesso ao painel da equipe. Funções declaradas identificadas: `verificarSessao`, `entrar`.

- **`src/public/assets/js/atendimento/painel.js`** — Lista e acompanha conversas no painel de atendimento. Funções declaradas identificadas: `formatarHora`, `nomeDaSessao`, `mostrarMensagem`, `buscarTodas`, `agrupar`, `contarSemResposta`, `criarSelo`, `desenharResumo`, `desenharConversas`, `selecionar`, `atualizar`, `responder`, `iniciar`.

- **`src/public/assets/js/atendimento/usuarios.js`** — Controla a interface de gestão de usuários da equipe. Funções declaradas identificadas: `avisar`, `mensagemDe`, `formatarData`, `criarCelula`, `criarBotao`, `desenharLista`, `carregar`, `cadastrar`, `alterarPerfil`, `excluir`, `redefinirSenha`, `iniciar`.

- **`src/public/assets/js/login.js`** — Script de login presente na estrutura anterior do projeto. Funções declaradas identificadas: `initLoginApp`, `carregarUsuarios`, `loginUser`, `logoutUser`, `addUser`, `showUserInfo`.

- **`src/public/index.html`** — Página HTML com o título “Document”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `./assets/css/style.css`; JS `./assets/js/login.js`.

- **`src/public/modulos/atendimento/.gitignore`** — Regras de arquivos que o Git deve ignorar nesta pasta.

- **`src/public/modulos/atendimento/index.html`** — Página HTML com o título “Central de Ajuda | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/atendimento/central.css`; CSS `../../assets/css/atendimento/chat.css`; CSS `../../assets/css/atendimento/conta.css`; JS `../../assets/js/atendimento/cliente.js`; JS `../../assets/js/atendimento/chat.js`; JS `../../assets/js/atendimento/central.js`; JS `../../assets/js/acessibilidade.js`.

- **`src/public/modulos/atendimento/inicio.html`** — Página HTML com o título “Início | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/atendimento/central.css`; CSS `../../assets/css/atendimento/admin.css`; JS `../../assets/js/atendimento/admin-comum.js`; JS `../../assets/js/atendimento/inicio.js`.

- **`src/public/modulos/atendimento/login.html`** — Página HTML com o título “Entrar | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/atendimento/central.css`; CSS `../../assets/css/atendimento/admin.css`; JS `../../assets/js/atendimento/admin-comum.js`; JS `../../assets/js/atendimento/login.js`.

- **`src/public/modulos/atendimento/package.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/modulos/atendimento/painel.html`** — Página HTML com o título “Atendimento | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/atendimento/central.css`; CSS `../../assets/css/atendimento/chat.css`; CSS `../../assets/css/atendimento/admin.css`; JS `../../assets/js/atendimento/admin-comum.js`; JS `../../assets/js/atendimento/painel.js`.

- **`src/public/modulos/atendimento/usuarios.html`** — Página HTML com o título “Usuários | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/atendimento/central.css`; CSS `../../assets/css/atendimento/admin.css`; JS `../../assets/js/atendimento/admin-comum.js`; JS `../../assets/js/atendimento/usuarios.js`.

- **`src/public/modulos/login/gerador_de_certificado/dados.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/modulos/login/gerador_de_certificado/index.html`** — Página HTML com o título “Gerador de Certificados - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `style.css`; JS `script.js`.

- **`src/public/modulos/login/gerador_de_certificado/script.js`** — Script da área indicada pelo caminho; implementa comportamento da interface ou lógica de apoio. Funções declaradas identificadas: `atualizarCertificadoSimultaneo`.

- **`src/public/modulos/login/gerador_de_certificado/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/modulos/login/index.html`** — Página HTML com o título “Desenvolvimento de Interfaces Web | Login de Usuário”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/style.css`; JS `../../assets/js/login.js`; JS `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js`; JS `https://code.jquery.com/jquery-3.2.1.slim.min.js`; JS `https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js`; JS `https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js`.

- **`src/public/modulos/login/login.html`** — Página HTML com o título “Desenvolvimento de Interfaces Web | Login de Usuário”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css`; CSS `https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css`; JS `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js`; JS `../../assets/js/login.js`; JS `https://code.jquery.com/jquery-3.2.1.slim.min.js`; JS `https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js`; JS `https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js`.

- **`src/servidor-atendimento.js`** — Servidor Node.js existente: serve arquivos, atende rotas HTTP, gerencia sessões, contas, mensagens e dados do atendimento. Funções declaradas identificadas: `semBom`, `lerDados`, `gravarDados`, `lerConteudo`, `criarHash`, `conferirSenha`, `salvarUsuarios`, `carregarUsuarios`, `ehAdministrador`, `dadosPublicos`, `salvarClientes`, `carregarClientes`, `dadosCliente`, `carregarMensagens`, `criarSessao`, `encerrarSessoesDe`, `sessaoDoCabecalho`, `autenticar`, `autenticarCliente`, `estaBloqueado`, `registrarFalha`, `limparFalhas`, `enviarJson`, `erro`, `lerCorpo`, `filtrar`, `rotaLogin`, `rotaCliente`, `resumoAtendimento`, `rotaApi`, `rotaMensagens`, `rotaConteudo`, `servirArquivo`, `tratar`.
