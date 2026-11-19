# Mapa dos arquivos de código — test

Os caminhos são relativos à raiz do repositório. A lista abrange os arquivos de fonte e configuração em `src` que são versionados no Git, e usa o conteúdo atual da cópia analisada. O nome das funções foi extraído das declarações `function`; é um índice para leitura, não uma prova de que todas elas sejam chamadas.

- **`src/README.md`** — Documento Markdown de orientação ou descrição do projeto.

- **`src/db/atendimento/.gitignore`** — Regras de arquivos que o Git deve ignorar nesta pasta.

- **`src/db/atendimento/conteudo.json`** — Conteúdos estruturados da Central de Ajuda, como categorias, perguntas e canais.

- **`src/db/db.json`** — Dados de exemplo do servidor de laboratório.

- **`src/db/mural/conteudo.json`** — Dados do mural de pedidos.

- **`src/db/quiz/.gitignore`** — Regras de arquivos que o Git deve ignorar nesta pasta.

- **`src/db/quiz/conteudo.json`** — Coleções utilizadas pelo quiz, incluindo perguntas e alternativas.

- **`src/index.js`** — Servidor de exemplo do JSON Server; lê o arquivo db/db.json e expõe seus dados por HTTP.

- **`src/package.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/assets/css/Guilherme/gerador_de_certificado/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Guilherme/mural_de_certificados/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Gustavo/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Kayllon/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Kayllon/usuario.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Pedro/Avaliar_Chat/styles.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Pedro/Filtro/style.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Willer/ajudooce-base.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Willer/perguntas.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Willer/quiz.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/Willer/resultados.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/acessibilidade.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/acesso.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/admin.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/central.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/chat.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/atendimento/conta.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/navegacao-local.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/css/navegacao.css`** — Folha de estilos da área indicada pelo caminho; define aparência, disposição e adaptação visual dos elementos correspondentes.

- **`src/public/assets/js/Guilherme/gerador_de_certificado/script.js`** — Atualiza a prévia do certificado e aciona impressão e compartilhamento. Funções declaradas identificadas: `atualizarCertificadoSimultaneo`.

- **`src/public/assets/js/Guilherme/mural_de_certificados/script.js`** — Controla a interface do mural de pedidos. Funções declaradas identificadas: `mostrarAviso`, `requisitar`, `botaoAcao`, `alterarPedido`, `renderizar`, `carregar`, `iniciar`.

- **`src/public/assets/js/Gustavo/script.js`** — Implementa o formulário e a apresentação local de registros de golpes. Funções declaradas identificadas: `goToGolpe`, `nextGolpe`.

- **`src/public/assets/js/Kayllon/script.js`** — Controla lista, filtros e edição local das solicitações de exemplo. Funções declaradas identificadas: `carregarSolicitacoes`, `salvarSolicitacoes`, `mostrarSolicitacoes`, `criarCartao`, `atualizarGrafico`, `abrirFormulario`.

- **`src/public/assets/js/Kayllon/usuario.js`** — Contém comportamento associado à página inicial do usuário. Funções declaradas identificadas: `mostrarDuvida`.

- **`src/public/assets/js/Pedro/Avaliar_Chat/script.js`** — Controla a escolha de estrelas e a confirmação visual de avaliação. Funções declaradas identificadas: `selectRating`.

- **`src/public/assets/js/Pedro/Filtro/chat.js`** — Verifica a conclusão da triagem antes do acesso à etapa seguinte.

- **`src/public/assets/js/Pedro/Filtro/triagem.js`** — Controla as etapas e respostas da triagem. Funções declaradas identificadas: `carregar`, `salvar`, `etapaAtual`, `render`, `montarObstaculos`, `montarRedesSociais`, `montarCaso`, `atualizarControles`, `mudar`, `concluir`.

- **`src/public/assets/js/Willer/perguntas.js`** — Controla a manutenção das perguntas do quiz. Funções declaradas identificadas: `mostrarAviso`, `carregarPerguntas`, `criarCelula`, `desenharTabela`, `montarPergunta`, `formularioValido`, `editarPergunta`, `excluirPergunta`, `limparFormulario`.

- **`src/public/assets/js/Willer/quiz.js`** — Apresenta perguntas, registra respostas e calcula o resultado do quiz. Funções declaradas identificadas: `carregarQuiz`, `mostrarPergunta`, `atualizarProgresso`, `conferirResposta`, `obterJogador`, `finalizarQuiz`.

- **`src/public/assets/js/Willer/ranking.js`** — Arquivo vazio nesta versão; a apresentação dinâmica do ranking ainda precisa ser implementada.

- **`src/public/assets/js/Willer/recompensas.js`** — Arquivo vazio nesta versão; a apresentação dinâmica das recompensas ainda precisa ser implementada.

- **`src/public/assets/js/Willer/resultado.js`** — Consulta e apresenta um resultado do quiz. Funções declaradas identificadas: `mostrarErro`, `escolherMensagem`, `carregarResultado`.

- **`src/public/assets/js/acessibilidade.js`** — Implementa o painel de acessibilidade, preferências visuais e linha de leitura. Funções declaradas identificadas: `restaurarTexto`, `ajustarTexto`, `aplicar`, `fechar`.

- **`src/public/assets/js/atendimento/acesso.js`** — Controla a tela de login e cadastro e a volta à página de origem. Funções declaradas identificadas: `selecionar`.

- **`src/public/assets/js/atendimento/admin-comum.js`** — Compartilha autenticação e navegação das telas da equipe. Funções declaradas identificadas: `obterToken`, `guardarToken`, `limparToken`, `podeAcessar`, `requisitar`, `exigirLogin`, `sair`, `criarSelo`, `mostrarResumo`, `atualizarResumo`, `montarMenu`, `iniciarPagina`.

- **`src/public/assets/js/atendimento/central.js`** — Carrega e apresenta categorias, perguntas, busca e informações da Central de Ajuda. Funções declaradas identificadas: `normalizarTexto`, `criar`, `clicouFora`, `rotularBotoesInformacoes`, `filtrarPerguntas`, `configurarBusca`, `configurarModalInformacoes`, `transformacao`, `cancelarAnimacao`, `fechar`, `configurarChat`, `montarCategoria`, `carregarDados`.

- **`src/public/assets/js/atendimento/chat.js`** — Abre o chat, envia e consulta mensagens e identifica a sessão da conversa. Funções declaradas identificadas: `clienteLogado`, `identificarSessao`, `cabecalhosCliente`, `saudacao`, `tratarSessaoExpirada`, `criarFalha`, `obterSessao`, `normalizar`, `formatarHora`, `mostrarMensagem`, `rolarParaFim`, `mostrarDigitando`, `mostrarAviso`, `salvarMensagem`, `carregarHistorico`, `carregarFaq`, `gerarResposta`, `iniciar`, `atualizar`, `enviar`, `abrir`.

- **`src/public/assets/js/atendimento/cliente.js`** — Gerencia a sessão da conta do cliente e os formulários de conta existentes na Central. Funções declaradas identificadas: `ler`, `gravar`, `limpar`, `primeiroNome`, `atualizarCabecalho`, `mostrarAba`, `mostrarPerfil`, `abrirModal`, `clicouFora`, `chamar`, `enviar`, `abrirContaPorAtalho`, `conferirSessao`.

- **`src/public/assets/js/atendimento/inicio.js`** — Apresenta as opções do painel conforme as permissões da equipe. Funções declaradas identificadas: `iniciar`.

- **`src/public/assets/js/atendimento/login.js`** — Envia os dados de acesso ao painel da equipe. Funções declaradas identificadas: `verificarSessao`, `entrar`.

- **`src/public/assets/js/atendimento/painel.js`** — Lista e acompanha conversas no painel de atendimento. Funções declaradas identificadas: `formatarHora`, `nomeDaSessao`, `mostrarMensagem`, `buscarTodas`, `agrupar`, `contarSemResposta`, `criarSelo`, `desenharResumo`, `desenharConversas`, `selecionar`, `atualizar`, `responder`, `iniciar`.

- **`src/public/assets/js/atendimento/usuarios.js`** — Controla a interface de gestão de usuários da equipe. Funções declaradas identificadas: `avisar`, `mensagemDe`, `formatarData`, `criarCelula`, `criarBotao`, `desenharLista`, `carregar`, `cadastrar`, `alterarPerfil`, `excluir`, `redefinirSenha`, `iniciar`.

- **`src/public/assets/js/navegacao.js`** — Constrói o cabeçalho e o rodapé compartilhados, incluindo menus e controles de conta. Funções declaradas identificadas: `link`, `atualizarNome`, `prepararEquipe`, `atualizarLateral`, `atualizarSelo`.

- **`src/public/modulos/Guilherme/gerador_de_certificado/dados.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/modulos/Guilherme/gerador_de_certificado/index.html`** — Página HTML com o título “Gerador de Certificados - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Guilherme/gerador_de_certificado/style.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`; JS `../../../assets/js/Guilherme/gerador_de_certificado/script.js`.

- **`src/public/modulos/Guilherme/mural_de_certificados/index.html`** — Página HTML com o título “Mural de Pedidos - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Guilherme/mural_de_certificados/style.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`; JS `../../../assets/js/Guilherme/mural_de_certificados/script.js`.

- **`src/public/modulos/Gustavo/about.html`** — Página HTML com o título “Sobre - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`.

- **`src/public/modulos/Gustavo/concluido.html`** — Página HTML com o título “Cadastro Concluído - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/Gustavo/style.css`; CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`; JS `../../assets/js/Gustavo/script.js`.

- **`src/public/modulos/Gustavo/game.html`** — Página HTML com o título “Tutorial - Como usar sites com segurança”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/Gustavo/style.css`; CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`.

- **`src/public/modulos/Gustavo/index.html`** — Página HTML com o título “Ajudo Ocê - Cadastro de Golpe”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/Gustavo/style.css`; CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`; JS `../../assets/js/Gustavo/script.js`.

- **`src/public/modulos/Gustavo/login.html`** — Página HTML com o título “Desenvolvimento de Interfaces Web | Login de Usuário”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css`; CSS `https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css`; CSS `../../assets/css/navegacao-local.css`; JS `https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js`; JS `../../assets/js/navegacao.js`; JS `../../assets/js/login.js`; JS `https://code.jquery.com/jquery-3.2.1.slim.min.js`; JS `https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js`; JS `https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js`.

- **`src/public/modulos/Icaro/atendimento/.gitignore`** — Regras de arquivos que o Git deve ignorar nesta pasta.

- **`src/public/modulos/Icaro/atendimento/conta.html`** — Página HTML com o título “Entrar ou criar conta | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/acesso.css`; JS `../../../assets/js/atendimento/acesso.js`.

- **`src/public/modulos/Icaro/atendimento/index.html`** — Página HTML com o título “Central de Ajuda | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/central.css`; CSS `../../../assets/css/atendimento/chat.css`; CSS `../../../assets/css/atendimento/conta.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/atendimento/cliente.js`; JS `../../../assets/js/atendimento/chat.js`; JS `../../../assets/js/atendimento/central.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Icaro/atendimento/inicio.html`** — Página HTML com o título “Início | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/central.css`; CSS `../../../assets/css/atendimento/admin.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/atendimento/admin-comum.js`; JS `../../../assets/js/atendimento/inicio.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Icaro/atendimento/login.html`** — Página HTML com o título “Entrar | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/central.css`; CSS `../../../assets/css/atendimento/admin.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/atendimento/admin-comum.js`; JS `../../../assets/js/atendimento/login.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Icaro/atendimento/package.json`** — Arquivo JSON de dados ou configuração da área indicada pelo caminho.

- **`src/public/modulos/Icaro/atendimento/painel.html`** — Página HTML com o título “Atendimento | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/central.css`; CSS `../../../assets/css/atendimento/chat.css`; CSS `../../../assets/css/atendimento/admin.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/atendimento/admin-comum.js`; JS `../../../assets/js/atendimento/painel.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Icaro/atendimento/usuarios.html`** — Página HTML com o título “Usuários | Painel Administrativo | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/atendimento/central.css`; CSS `../../../assets/css/atendimento/admin.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/atendimento/admin-comum.js`; JS `../../../assets/js/atendimento/usuarios.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Kayllon/guia-avaliacao.md`** — Documento Markdown de orientação ou descrição do projeto.

- **`src/public/modulos/Kayllon/index.html`** — Página HTML com o título “Ajudo Ocê | Início”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/Kayllon/style.css`; CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`; JS `../../assets/js/Kayllon/script.js`.

- **`src/public/modulos/Kayllon/usuario.html`** — Página HTML com o título “Ajudo Ocê | Início”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/Kayllon/usuario.css`; CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`; JS `../../assets/js/Kayllon/usuario.js`.

- **`src/public/modulos/Pedro/Avaliar_Chat/index.html`** — Página HTML com o título “Avalie seu Atendimento | Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Pedro/Avaliar_Chat/styles.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`; JS `../../../assets/js/Pedro/Avaliar_Chat/script.js`.

- **`src/public/modulos/Pedro/Filtro/chat.html`** — Página HTML com o título “Chat - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Pedro/Filtro/style.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Pedro/Filtro/chat.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Pedro/Filtro/index.html`** — Página HTML com o título “Triagem - Ajudo Ocê”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Pedro/Filtro/style.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`; JS `../../../assets/js/Pedro/Filtro/triagem.js`.

- **`src/public/modulos/Rayssa/pagina.cuidados.segurança.digital.html`** — Página HTML com o título “Document”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`.

- **`src/public/modulos/Rayssa/pagina.princial.noticias.html`** — Página HTML com o título “Document”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../assets/css/navegacao-local.css`; JS `../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/Resultados_Estilização/Ranking.html`** — Página HTML com o título “AjudoOcê - Ranking”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Willer/ajudooce-base.css`; CSS `../../../assets/css/Willer/resultados.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Willer/ranking.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/Resultados_Estilização/Recompensas.html`** — Página HTML com o título “AjudoOcê - Recompensas”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Willer/ajudooce-base.css`; CSS `../../../assets/css/Willer/resultados.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Willer/recompensas.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/Resultados_Estilização/Resultado.html`** — Página HTML com o título “AjudoOcê - Resultado”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Willer/ajudooce-base.css`; CSS `../../../assets/css/Willer/resultados.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Willer/resultado.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/quiz/paginaanterior.html`** — Página HTML com o título “Pagina Anterior”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/quiz/paginainicial.html`** — Página HTML com o título “Tela inicial”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/quiz/perguntas.html`** — Página HTML com o título “AjudoOcê - Perguntas”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Willer/ajudooce-base.css`; CSS `../../../assets/css/Willer/perguntas.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Willer/perguntas.js`; JS `../../../assets/js/navegacao.js`.

- **`src/public/modulos/Willer/quiz/quiz.html`** — Página HTML com o título “AjudoOcê - Quiz”; define a estrutura do conteúdo e dos controles da tela. Referências: CSS `../../../assets/css/Willer/ajudooce-base.css`; CSS `../../../assets/css/Willer/quiz.css`; CSS `../../../assets/css/navegacao-local.css`; JS `../../../assets/js/Willer/quiz.js`; JS `../../../assets/js/navegacao.js`.

- **`src/servidor-atendimento.js`** — Servidor Node.js existente: serve arquivos, atende rotas HTTP, gerencia sessões, contas, mensagens e dados do atendimento. Funções declaradas identificadas: `semBom`, `lerDados`, `gravarDados`, `lerConteudo`, `criarHash`, `conferirSenha`, `salvarUsuarios`, `carregarUsuarios`, `ehAdministrador`, `dadosPublicos`, `salvarClientes`, `carregarClientes`, `dadosCliente`, `carregarMensagens`, `criarSessao`, `encerrarSessoesDe`, `sessaoDoCabecalho`, `autenticar`, `autenticarCliente`, `estaBloqueado`, `registrarFalha`, `limparFalhas`, `enviarJson`, `erro`, `lerCorpo`, `filtrar`, `rotaLogin`, `rotaCliente`, `resumoAtendimento`, `rotaApi`, `rotaMensagens`, `rotaConteudo`, `rotaMural`, `validarPedido`, `rotaQuiz`, `servirArquivo`, `tratar`.
