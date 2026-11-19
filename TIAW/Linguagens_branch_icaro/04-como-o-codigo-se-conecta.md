# Como o código se conecta — branch icaro

## Central de Ajuda

O HTML em `src/public/modulos/atendimento/index.html` organiza a Central: apresenta categorias, perguntas e canais de contato. O CSS de `assets/css/atendimento/central.css` define seu layout. O JavaScript `assets/js/atendimento/central.js` controla a apresentação das informações e a pesquisa. O JSON `src/db/atendimento/conteudo.json` fornece conteúdo estruturado que pode ser consultado pelas rotas disponíveis.

Esse fluxo ilustra a diferença entre linguagens: o HTML oferece lugares para mostrar as respostas, o CSS define sua aparência e o JavaScript decide o que mostrar e quando. O JSON contém os dados; ele não constrói a tela por conta própria.

## Conta, chat e equipe

`cliente.js` implementa o comportamento da conta do cliente, enquanto `chat.js` trata a conversa, as mensagens e a identificação da sessão. O acesso e as funções da equipe usam páginas HTML próprias e os scripts `login.js`, `inicio.js`, `painel.js`, `usuarios.js` e `admin-comum.js`, todos na pasta `assets/js/atendimento`.

`admin.css`, `chat.css` e `conta.css` cuidam da aparência dessas interfaces. O servidor existente em `src/servidor-atendimento.js` recebe requisições, administra sessões e lê ou grava dados locais. Não é correto tratar os arquivos HTML, CSS e JavaScript do navegador como suficientes para efetivar, por si só, uma alteração permanente na conta armazenada pelo servidor.

## Acessibilidade e exemplos

`assets/js/acessibilidade.js` e `assets/css/acessibilidade.css` concentram os controles visuais e as regras de aparência. O projeto também inclui arquivos de exemplo, páginas de login e um gerador de certificado na estrutura `src/public/modulos/login`. Consulte o mapa para identificar o caminho específico de cada arquivo.

O simples fato de existir um arquivo de exemplo não garante que ele esteja integrado a todos os caminhos de navegação. O mapa descreve a presença e a finalidade do código, sem prometer uma funcionalidade além do que foi encontrado.
