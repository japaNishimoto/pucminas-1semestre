# Linguagens, tipos e funções — icaro

## Como entender os tipos

Uma **linguagem de programação** descreve operações e decisões que o computador executa. Uma **linguagem de marcação** organiza conteúdo por elementos. Uma **linguagem de estilo** descreve a apresentação. Um **formato de dados** organiza informações para leitura e troca. Essas categorias se complementam.

## HTML — linguagem de marcação

Os arquivos `.html` descrevem a estrutura das páginas: títulos, textos, botões, formulários, imagens, links e janelas. O navegador interpreta suas tags e monta a árvore de elementos da página. Atributos como `id`, `class`, `for` e `aria-*` ligam elementos ao CSS, ao JavaScript e aos recursos de acessibilidade. Não é uma linguagem de programação: sozinho, o HTML não executa as regras do aplicativo.

No projeto, as páginas estão principalmente em `src/public` e `src/public/modulos`. As próprias páginas indicam scripts e folhas de estilo por meio de tags `script` e `link`. O mapa aponta as referências encontradas em cada arquivo.

## CSS — linguagem de folhas de estilo

Arquivos `.css` definem cores, fontes, bordas, espaçamento, posicionamento e aparência dos controles. Seletores escolhem os elementos; propriedades definem como serão exibidos. Regras `@media` permitem adaptar a apresentação para telas menores e impressão. As variáveis CSS e regras de tema ajudam a manter consistência. CSS controla a apresentação, sem substituir a estrutura do HTML ou o comportamento do JavaScript.

Exemplos incluem os estilos da Central em `src/public/assets/css/atendimento/central.css` e os estilos de acessibilidade em `src/public/assets/css/acessibilidade.css`.

## JavaScript — linguagem de programação

Os arquivos `.js` implementam ações e regras. No navegador, JavaScript acessa o DOM para ler campos, abrir janelas, reagir a cliques, validar entradas, atualizar conteúdo e acionar requisições com `fetch`. `localStorage` guarda dados no navegador entre visitas; `sessionStorage` guarda dados associados à sessão da aba. Esses dois armazenamentos não são um banco de dados compartilhado entre aparelhos.

O projeto também tem JavaScript executado no **Node.js**, que é um ambiente de execução, não outra linguagem. O arquivo `src/servidor-atendimento.js` existente usa módulos nativos como `http`, `fs`, `path` e `crypto` para servir páginas e atender rotas. Portanto, há código de servidor no repositório, embora o frontend seja desenvolvido em HTML, CSS e JavaScript. O arquivo `src/index.js` é um servidor de laboratório separado baseado em JSON Server; estar presente não significa que os dois servidores devam ser iniciados juntos na mesma porta.

As funções declaradas que foram identificadas automaticamente constam no mapa; eventos anônimos, métodos e funções de seta também podem existir e não aparecem necessariamente nessa lista.

## JSON — formato de dados e configuração

Arquivos `.json` armazenam informações em objetos, listas e valores. Não são linguagem de programação e não executam ações sozinhos. No projeto, aparecem em dados da Central e em `package.json` / `package-lock.json`, que descrevem pacotes, dependências e versões resolvidas. JavaScript lê ou envia JSON para montar interfaces e trocar informações. Arquivos locais de clientes e mensagens podem conter dados pessoais e não são reproduzidos aqui.

## Markdown — linguagem de marcação para documentação

Arquivos `.md`, como `README.md` e os documentos em `docs`, organizam texto com títulos, listas, links e tabelas. Seu objetivo é documentar; normalmente não compõem a lógica do aplicativo.

## YAML e CFF — configuração e metadados

`.classroom50.yaml` usa YAML para configuração. `CITATION.cff` usa o formato Citation File Format, baseado em YAML, para metadados de citação. Eles descrevem informações estruturadas; não são as páginas nem a lógica de interface do site.

## SVG, quando aparece no código

SVG é uma linguagem de marcação vetorial para desenhos. Ícones podem estar escritos diretamente no HTML ou em strings JavaScript com `<svg>`, mesmo que não exista um arquivo `.svg` próprio. As formas podem ser desenhadas e coloridas sem depender de uma imagem raster. PNG, JPG e WebP, por outro lado, são formatos de imagem, não linguagens de programação.

## Git ignore e arquivo de comandos

`.gitignore` descreve padrões de arquivos que o Git deve ignorar; não controla o funcionamento da página. Arquivos `.cmd`, `.ps1` e scripts sem extensão dentro das dependências são lançadores de ferramentas para terminais; não devem ser confundidos com código escrito pela equipe para as telas.

## Como as peças trabalham juntas

1. O navegador recebe HTML e identifica os elementos da página.
2. O CSS aplica a aparência e as regras para diferentes tamanhos de tela.
3. O JavaScript reage às ações e pode ler dados JSON ou conversar com rotas HTTP.
4. Quando usado, o servidor Node.js fornece arquivos e responde a essas requisições.
5. Arquivos Markdown e metadados explicam e configuram o projeto, sem serem parte visual obrigatória da página.
