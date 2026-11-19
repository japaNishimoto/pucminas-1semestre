# Central de Ajuda, contas e atendimento

[Voltar ao guia](Guia_das_alteracoes.md)

## Central de Ajuda

A Central reúne respostas sobre cadastro, uso da plataforma e outros assuntos. Do cabeçalho compartilhado, ela pode ser aberta pelo menu **Preciso de ajuda**. O visitante vê um banner de apresentação, pesquisa de dúvidas, cartões por assunto com perguntas expansíveis, botões de **Mais informações** e canais de contato. O cartão **Outros Assuntos** oferece acesso ao chat.

A busca compara o termo com títulos e descrições dos cartões e com o texto das perguntas e respostas. Ignora diferenças de acentuação e maiúsculas, conta os resultados e permite limpar o filtro. A opção **Mais informações** abre uma janela sobre o assunto. A Central tenta carregar os conteúdos e canais dos dados do servidor e mantém os itens já escritos no HTML se a consulta falhar. O bloco de contato oferece WhatsApp e composição de e-mail, conforme os destinos configurados.

O histórico da Central começa em `7ab5a56` e `baabe65`. A grade responsiva, o rodapé e o cabeçalho móvel foram evoluindo a partir de `fc3abb6`, `897c5a2` e `a91c9ad`. A busca, as perguntas expansíveis, a faixa de contato, o banner e o atalho de chat aparecem em `dc05f0d`, `1352f7b`, `a4833fb`, `728fc8d`, `57497be`, `831f7c8` e `3a485c7`. Os primeiros ajustes de texto e foco e a carga de conteúdo por JSON aparecem em `dd4c60a`, `e7d2442` e `e5dae3e`.

Na conversa mais antiga recuperada, o primeiro pedido foi melhorar o cabeçalho e o design do `index.html` da Central. Na estrutura antiga, em `src/public/modulos/atendimento/`, houve ajustes de marca, navegação, espaçamento, banner, pesquisa e cartões. A versão relatada naquela conversa identificava a Central na marca, oferecia um botão no banner para chegar à busca e adaptava o menu a telas menores. O relato final registrou conferência no navegador em desktop e celular. Depois da integração, o servidor local passou a servir a Central de `modulos/Icaro/atendimento/` com o cabeçalho compartilhado. Os componentes atuais podem diferir dos detalhes da primeira revisão visual.

| Código atual | Função |
| --- | --- |
| `src/public/modulos/Icaro/atendimento/index.html` | Banner, busca, categorias, botões de contato, janela do chat e formulário da conta. |
| `src/public/assets/css/atendimento/central.css` | Layout da Central, cartões, pesquisa, janelas e regras para telas menores. |
| `src/public/assets/js/atendimento/central.js` | Busca, conteúdo de tópicos, janelas de informação, contato e abertura do chat pelos botões da Central. |
| `src/db/atendimento/conteudo.json` | Dados iniciais da Central, incluindo categorias, perguntas e canais. |

## Cadastro e login do cliente

O cadastro e a autenticação do cliente foram introduzidos em `0ce5940`, depois da criação da área da equipe. O mesmo commit registrou a separação do Painel do Atendente e notificações para conversas sem resposta.

1. O cliente seleciona **Entrar** no cabeçalho para acessar a página de conta. Ela oferece login e cadastro; a Central também contém uma janela de conta.
2. No cadastro, informa nome, e-mail, senha e confirmação da senha. Há opções para mostrar a senha enquanto digita. O formulário verifica os campos e exibe os erros na própria janela.
3. O servidor verifica nome de 2 a 60 caracteres, e-mail válido de até 100 caracteres e senha de 6 a 64 caracteres. O e-mail é normalizado para minúsculas e precisa ser único. A confirmação de senha é verificada na interface.
4. Se o cadastro for aceito, a conta é criada e o cliente já entra. Para retornar, basta usar o e-mail e a senha. A navegação da Central passa a mostrar uma saudação com o primeiro nome e a opção **Sair**.
5. O navegador guarda o token e o perfil em `localStorage`, na chave `ajudooce-cliente`. A página consulta a sessão no servidor ao abrir. Se a sessão estiver inválida, volta à interface de visitante. O servidor guarda o hash da senha com salt, e a sessão ativa fica em memória com validade de até sete dias. Reiniciar o servidor exige novo login.

O perfil atual exibe nome e e-mail para consulta; não há edição desses dados nessa interface nem rota de alteração de conta do cliente nesta versão. O cadastro cria uma conta de cliente. O formulário com habilidades e disponibilidade previsto para voluntários é outro fluxo e ainda não está integrado. O fluxo disponível usa e-mail e senha. Entrada com Google ou Apple, confirmação por e-mail e recuperação de senha de cliente não aparecem nas rotas implementadas. A tela avulsa `src/public/modulos/Gustavo/login.html` é um esboço separado. Ela referencia um script ausente no checkout. O cadastro funcional é o da Central.

| Código atual | Função |
| --- | --- |
| `src/public/modulos/Icaro/atendimento/index.html` e `src/public/assets/css/atendimento/conta.css` | Janela de login e cadastro, abas, campos, mensagens e visual da conta. |
| `src/public/assets/js/atendimento/cliente.js` | Validação de formulário, login, cadastro, saudação, dados da sessão e saída. |
| `src/public/assets/js/navegacao.js` | Integra o controle de conta da Central ao cabeçalho e aponta **Minha conta** para a Central nas outras páginas. |
| `src/servidor-atendimento.js` | `POST /api/cliente/cadastro`, `POST /api/cliente/login`, `GET /api/cliente/me` e `POST /api/cliente/logout`. |

## Atendimento pelo chat

O primeiro fluxo de chat com resposta automática está em `f34cba3`. O fechamento pelo **X**, por clique no fundo e a liberação da rolagem aparecem em `ac801c1`. A configuração atual está voltada à **resposta humana**. O código de resposta por perguntas frequentes permanece no arquivo com a opção automática desligada.

- **Visitante.** A janela de chat pode ser aberta sem conta, mas a navegação compartilhada solicita login antes do envio de mensagens. O código ainda possui suporte a identificadores de visitante, o que não altera essa exigência da interface atual.
- **Cliente autenticado.** O chat usa o ID da conta e mostra o nome do cliente à equipe. A mesma conta pode acessar a conversa em outro navegador conectado à mesma instalação. O histórico de visitante fica separado.
- **Troca de mensagens.** O cliente pode enviar mensagens de até 500 caracteres. A janela consulta novas mensagens a cada três segundos enquanto aberta. O painel da equipe também faz consultas periódicas.
- **Notificações.** A tela e o menu da equipe consultam o resumo de pendências. Uma conversa conta como pendente quando há mensagem do cliente posterior à última resposta da equipe. Há indicador junto ao atendimento e a contagem também pode aparecer no título da aba do painel.
- **Integração nas páginas do cliente.** A Central já contém a janela de chat. Nas outras páginas cobertas pela navegação compartilhada, o botão flutuante monta a janela e reutiliza os scripts existentes de conta e chat. Isso mantém o mecanismo de identificação e de conversa ao navegar.

Os arquivos principais são `src/public/assets/js/atendimento/chat.js`, `src/public/assets/css/atendimento/chat.css`, `src/public/assets/js/atendimento/painel.js` e `src/public/modulos/Icaro/atendimento/painel.html`. O servidor atende a leitura e o envio em `/mensagens` e o resumo em `/api/atendimento/resumo`. A área da equipe autentica a sessão antes de permitir respostas. O atendimento registrado não associa automaticamente a conversa a um voluntário específico.

## Login e usuários da equipe

O commit `7986090` registrou a área da equipe com tela inicial, perfis e acesso conforme a função. A equipe entra em `/administrativo` usando **nome de usuário e senha**. O servidor valida o login e entrega um token. O navegador guarda esse token em `sessionStorage`, na chave `ajudooce-admin-token`. A sessão da equipe fica em memória no servidor por até oito horas. As páginas protegidas conferem a sessão e o perfil, além de mostrar as opções correspondentes no menu.

| Perfil | Acesso |
| --- | --- |
| Atendente | Início, atendimento e mural de pedidos. |
| Administrador | Os módulos do atendente e gerenciamento das perguntas do quiz. |
| Master | Os módulos do administrador e gerenciamento das contas da equipe. |

O master pode consultar e cadastrar usuários da equipe, mudar perfis, redefinir senhas e excluir contas. O código atual não oferece alteração do nome de usuários existentes. O nome de usuário deve ter de 3 a 30 caracteres. As senhas de cadastro ou redefinição aceitam de 6 a 64 caracteres. As contas criadas pelo painel recebem o perfil de atendente ou administrador. A conta master tem proteção própria. Redefinir a senha ou excluir uma conta encerra as sessões existentes dessa conta.

| Código atual | Função |
| --- | --- |
| `src/public/modulos/Icaro/atendimento/login.html` e `src/public/assets/js/atendimento/login.js` | Formulário e envio do login da equipe. |
| `src/public/assets/js/atendimento/admin-comum.js` | Sessão, permissões, lista de módulos e resumo de atendimento dentro da área da equipe. |
| `src/public/modulos/Icaro/atendimento/usuarios.html` e `src/public/assets/js/atendimento/usuarios.js` | Cadastro e gestão de contas da equipe pelo master. |
| `src/servidor-atendimento.js` | `POST /api/login`, `GET /api/me`, `POST /api/logout`, `/api/usuarios` e `/api/usuarios/:usuario`. |

## Dados usados por esses fluxos

O ponto de entrada atual é `npm start` na raiz, que executa `src/servidor-atendimento.js`. As contas da equipe, as contas de clientes e as mensagens da instalação atual usam os arquivos de trabalho em `src/db/atendimento/dados/test/`, ignorados pelo Git. A pasta antiga `src/public/modulos/atendimento/dados/` apareceu separadamente como não rastreada. O guia registra o caminho sem copiar registros de clientes, mensagens ou dados de autenticação.

O histórico dos testes de cadastro, chat e acesso ao mural está no capítulo de verificações. [Histórico, documentação e verificações](Historico_e_verificacoes.md)
