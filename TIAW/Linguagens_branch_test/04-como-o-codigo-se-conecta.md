# Como o código se conecta — branch test

## Navegação, entrada e conta

`src/public/assets/js/navegacao.js` monta a navegação comum. As páginas usam HTML para a estrutura; `navegacao.css` e `navegacao-local.css` definem a apresentação e o encaixe do cabeçalho. `acesso.js`, `conta.html` e `acesso.css` formam a tela de login e cadastro. `cliente.js` guarda e consulta a identificação usada pelo cliente na interface.

As escolhas do navegador podem ser guardadas com `localStorage` ou `sessionStorage`. Isso não significa que todas as informações foram sincronizadas entre aparelhos. A existência de uma interface de edição também não garante que o servidor em execução ofereça a rota correspondente: a versão do servidor precisa ser compatível com a tela.

## Central de Ajuda e chat

`src/public/modulos/Icaro/atendimento/index.html` contém a estrutura da Central; `central.css` cuida de sua aparência; `central.js` implementa busca e apresentação de conteúdo. O arquivo `src/db/atendimento/conteudo.json` reúne dados estruturados como categorias e perguntas. `chat.js` e `chat.css` cuidam da conversa e da aparência do chat.

## Conteúdos, solicitações e triagem

Os diretórios `Kayllon`, `Rayssa` e `Gustavo` reúnem páginas e recursos de início, conteúdo educativo, segurança digital e solicitações. O diretório `Pedro` contém a triagem e a interface de avaliação de atendimento. Seus arquivos HTML, CSS e JavaScript são listados individualmente no mapa; a pasta no caminho identifica a área à qual pertencem.

Algumas dessas telas usam exemplos ou dados salvos localmente. A presença de uma tela não comprova integração completa com atendimento real nem armazenamento compartilhado entre aparelhos. Em particular, o resultado de ações locais deve ser entendido conforme o script específico que o salva.

## Quiz e certificados

O módulo `Willer` inclui telas e scripts de perguntas, quiz, resultado, ranking e recompensas. `src/db/quiz/conteudo.json` reúne dados relacionados ao quiz. O módulo `Guilherme` contém gerador de certificado e mural. No gerador, o JavaScript atualiza uma prévia e usa a impressão do navegador; o preenchimento informado não implica, por si, validação automática das horas.

## Servidor existente

`src/servidor-atendimento.js` é JavaScript executado em Node.js, separado do JavaScript das páginas. Ele serve recursos e implementa rotas de atendimento e contas. `src/index.js` é um servidor de laboratório separado baseado em JSON Server. Há uma alteração local pendente no servidor desta cópia de `test`; os documentos indicam essa situação para distinguir o que está no commit daquilo que estava apenas no disco durante a leitura.
