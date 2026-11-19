# Acessibilidade e interface

[Voltar ao guia](Guia_das_alteracoes.md)

Este capítulo explica os ajustes na interface pública, no painel de acessibilidade e na área da equipe. O desenvolvimento da conta do cliente, do login da equipe e do chat é detalhado no capítulo de atendimento. [Central, contas e atendimento](Central_contas_e_atendimento.md)

## 1. Onde estão os arquivos

A organização é esta:

```text
TIAW/
├── Documentacao_Ajudo_Oce/
│   ├── Guia_das_alteracoes.md
│   ├── Central_contas_e_atendimento.md
│   ├── Funcionalidades_do_projeto.md
│   ├── Acessibilidade_e_interface.md
│   └── Historico_e_verificacoes.md
└── pbe-ads-2026-2-p1-tiawfe-5490101-Ajudooce/
    ├── docs/
    ├── src/
    ├── package.json
    └── ...
```

Ao longo deste guia, os caminhos que começam por `src/` são relativos à pasta do repositório `pbe-ads-2026-2-p1-tiawfe-5490101-Ajudooce`.

**Importante:** manter este guia ao lado do repositório significa que ele não é incluído nos commits desse repositório. Ele também não será enviado junto com o código caso a pasta do projeto seja enviada para o GitHub.

## 2. Visão geral do que mudou

O trabalho da conversa envolveu as seguintes áreas:

1. Botões flutuantes de acessibilidade e de chat nas páginas do cliente.
2. Opções de acessibilidade: tamanho e espaçamento do texto, tema escuro, alto contraste e linha de leitura.
3. Aparência do site com tema escuro e alto contraste, incluindo logo, ícones, banner e bordas.
4. Layout dos painéis do administrador e do atendente.
5. Menu lateral da equipe, com opções de acordo com o perfil e possibilidade de recolher o menu.
6. Organização, por categoria, das alterações que estavam pendentes em commits locais.
7. Ajuste da linha de leitura sobre o vídeo do YouTube na página inicial.

O primeiro painel de acessibilidade foi criado em uma conversa anterior. A conversa seguinte começou pelo ajuste da posição do botão e pela recuperação do chat nas páginas públicas. A sequência completa está no capítulo de histórico. [Histórico, documentação e verificações](Historico_e_verificacoes.md)

## 3. Acessibilidade e chat nas páginas do cliente

### 3.1. Qual era o problema

O botão de acessibilidade ficava na mesma região do botão de chat e o encobria. Além disso, ele exibia a palavra “Acessibilidade” junto com o símbolo de cadeira de rodas. Foi pedido que o chat continuasse disponível e que o botão de acessibilidade ficasse logo acima dele, mostrando somente o ícone de uma pessoa.

### 3.2. Como ficou

- Na parte inferior direita da tela ficam dois botões flutuantes: **acessibilidade em cima** e **chat embaixo**.
- O botão de acessibilidade mostra um ícone de pessoa, desenhado em SVG; não há texto visível junto ao ícone.
- O botão mantém uma descrição para leitores de tela por meio de `aria-label="Acessibilidade"`.
- Os dois botões têm formato circular e recebem ajustes de posição em telas pequenas.
- A aparência e as opções dos botões mudam conforme as preferências de tema e contraste.
- Nas áreas identificadas como páginas da equipe, o script que cria esses botões não é carregado. Isso inclui os painéis de administração e atendimento e as páginas de mural e perguntas do quiz identificadas no código de navegação.

**Onde está:**

- `src/public/assets/js/acessibilidade.js`: cria os botões, o painel de opções, a linha de leitura e a integração do chat.
- `src/public/assets/css/acessibilidade.css`: estilos aplicados às páginas para as opções de acessibilidade.
- `src/public/assets/js/navegacao.js`: carrega o script de acessibilidade nas páginas do cliente e identifica as páginas da equipe.

### 3.3. Como o chat foi disponibilizado

O chat já existia na central de ajuda. O ajuste passou a disponibilizá-lo também nas demais páginas que carregam a navegação compartilhada:

1. Ao clicar no botão de chat, o código chama a função existente `abrirChatAtendimento`.
2. Nas páginas que ainda não têm a janela do chat, o script cria a janela e carrega os arquivos existentes de cliente e atendimento.
3. A identificação e o histórico continuam usando os mecanismos já presentes no projeto; o chat precisa do servidor de atendimento para suas operações de rede.
4. Na própria central, onde a janela já existe, o script a reutiliza em vez de criar uma segunda janela.

Os controles de acessibilidade e chat usam **Shadow DOM**: uma área isolada de HTML e CSS criada pelo JavaScript. Esse isolamento ajuda a evitar que estilos das outras páginas alterem diretamente os botões e o painel. Já as preferências que devem afetar o conteúdo da página usam regras em `acessibilidade.css`.

## 4. Opções do painel de acessibilidade

### 4.1. Tamanho do texto

Os botões **A−** e **A+** diminuem ou aumentam o tamanho do texto em passos de 10%, entre 80% e 150%. O percentual atual aparece no painel.

O JavaScript guarda os tamanhos originais dos elementos alterados para conseguir restaurá-los antes de aplicar outro tamanho. Ele também tenta alcançar o conteúdo da navegação e do rodapé compartilhados, que usam Shadow DOM.

**Para o usuário:** abrir o botão de acessibilidade, escolher A− ou A+ e conferir o percentual mostrado.

### 4.2. Espaçamento do texto

A opção permite escolher entre **Padrão** e **Ampliado**. O ajuste original foi considerado insuficiente porque deixava a leitura com aparência ruim e dava destaque excessivo ao espaço entre linhas.

Foi feita uma revisão para aplicar espaçamento de letras, palavras e linhas a elementos de texto e controles. Parágrafos, itens de lista, descrições e citações também recebem um ajuste de margem inferior. A intenção é melhorar a separação do conteúdo sem aplicar a mesma mudança indiscriminadamente a todos os elementos da página.

**Onde está:** regras com `data-ajudo-espacamento="amplo"` em `src/public/assets/css/acessibilidade.css`.

### 4.3. Tema escuro

O tema escuro foi adicionado para oferecer uma apresentação com menos áreas claras e cores coordenadas.

- No tema claro, o botão apresenta **“Tema escuro”**.
- No tema escuro, o botão apresenta **“Tema claro”**.
- Assim, o texto informa a ação que será feita ao clicar.
- O tema usa fundos em azul-escuro, texto claro, links claros e bordas em tons de azul.
- Campos, botões, cartões, navegação, rodapé e mensagens do chat receberam regras próprias para acompanhar a paleta.
- Imagens não são convertidas automaticamente para preto e branco; isso preserva, por exemplo, a pessoa no banner.
- A logo da navegação e do rodapé recebeu tratamento visual para que as letras fiquem claras no tema escuro, sem o retângulo branco que aparecia antes.

As preferências são guardadas no `localStorage` do navegador, na chave `ajudooce-acessibilidade`. Isso significa que a escolha é lembrada naquele navegador quando a pessoa volta a outras páginas que usam o recurso. O armazenamento pode estar indisponível em algumas condições; nesse caso, o código continua funcionando sem garantir que a escolha seja lembrada.

**Onde está:**

- Estado, botão e salvamento: `src/public/assets/js/acessibilidade.js`.
- Cores do conteúdo: `src/public/assets/css/acessibilidade.css`.
- Cores e logo da navegação e rodapé: `src/public/assets/css/navegacao.css`.

### 4.4. Alto contraste

O alto contraste oferece outra apresentação: fundo preto, texto branco e amarelo para alguns destaques, links e foco do teclado.

- Quando está desligado, o botão diz **“Alto contraste”**.
- Quando está ligado, o botão diz **“Contraste padrão”**.
- O painel de acessibilidade acompanha essa escolha, inclusive nos controles e no contorno do foco.
- Cartões, campos, banner, ícones e botões flutuantes foram ajustados para manter contornos visíveis e arredondados.
- A logo da navegação e do rodapé é apresentada com letras claras.
- Os ícones de categoria recebem tratamento visual para se destacarem melhor.

O tema escuro e o alto contraste são escolhas separadas: ao ativar um, o outro é desligado. Desligar o alto contraste volta ao contraste padrão; isso não reativa automaticamente o tema escuro anterior.

### 4.5. Linha de leitura

A linha de leitura é uma linha horizontal que ajuda a acompanhar o conteúdo. Ela pode ser ativada ou desativada no painel de acessibilidade.

- Quando ativa, acompanha a posição do ponteiro ou do toque.
- Com o botão da linha selecionado, as setas para cima e para baixo também podem movê-la.
- A linha não recebe cliques nem bloqueia os elementos que estão atrás dela.
- Sua cor muda para amarelo nos modos escuro e de alto contraste, para ficar visível.
- A preferência também é salva na mesma chave de acessibilidade do navegador.

O comportamento específico sobre o vídeo foi alterado no último pedido e está explicado na seção 9. Essa alteração ainda estava sem commit na data da conferência.

### 4.6. Restaurar configurações

O botão **“Restaurar configurações padrão”** volta o texto a 100%, o contraste e o espaçamento ao padrão, desliga o tema escuro e desativa a linha de leitura. A nova escolha também é salva no navegador.

## 5. Correções de aparência no site do cliente

### 5.1. Logo

Ao testar o tema escuro, foi percebido um fundo branco retangular atrás da logo. A imagem original da logo possui fundo branco e letras escuras. Foram aplicados efeitos de CSS na logo usada pela navegação e pelo rodapé para apresentá-la com letras claras e integrá-la ao fundo escuro ou preto.

Essa mudança se aplica à logo nesses componentes compartilhados. Não significa que todos os arquivos de imagem de logo do projeto tenham sido editados.

### 5.2. Banner da central de ajuda

O fundo e a área de texto do banner foram coordenados com o tema escuro. Em uma tentativa intermediária, a imagem da pessoa foi ocultada para deixar o fundo uniforme. Isso não era o desejado: depois da correção solicitada, a imagem foi **recolocada** e a área do texto continuou azul-escura.

Os cantos externos do banner foram arredondados e o conteúdo é recortado dentro deles. O alto contraste mantém a imagem e apresenta contorno claro ao redor do banner.

### 5.3. Bordas e botão circular

O tema escuro estava aplicando cor ao elemento retangular que envolve os controles flutuantes. Por isso apareciam pontas escuras atrás do botão circular de acessibilidade.

O contêiner desses controles foi excluído da regra geral que pintava blocos da página. Também foram mantidos os cantos arredondados do banner e de componentes específicos, como cartões, campos e janela do chat. A mesma exclusão foi considerada nas regras de alto contraste.

### 5.4. Ícones e contornos

Foram adicionadas regras para harmonizar cores de ícones e contornos com o tema escuro. No alto contraste, ícones e contornos relevantes foram ajustados para se destacar contra o fundo preto. Isso não significa que todas as imagens ou todos os ícones de todas as páginas tenham sido revisados individualmente.

## 6. Painel administrativo e painel do atendente

### 6.1. Por que o layout mudou

Foi pedido um painel da equipe com identidade visual mais elaborada e sem o botão de acessibilidade do site do cliente. O trabalho se concentrou na página inicial da equipe e nas telas de atendimento e usuários, preservando as funcionalidades que já existiam.

### 6.2. O que mudou visualmente

- A página inicial recebeu uma área de boas-vindas com destaque para o nome do usuário.
- As ferramentas disponíveis aparecem em cartões com ícones, título, descrição e indicação de acesso.
- O fundo, as cores, bordas e espaçamentos foram atualizados para criar uma identidade visual consistente.
- As áreas de conversas, mensagens, formulários e tabela de usuários receberam ajustes visuais.
- O layout tem regras para telas menores, como empilhamento das áreas de conversa e limitação da altura da lista.
- As opções exibidas nos cartões continuam condicionadas às permissões definidas no projeto.

**Onde está:**

- `src/public/modulos/Icaro/atendimento/inicio.html`: estrutura da página inicial da equipe.
- `src/public/assets/js/atendimento/inicio.js`: montagem dos cartões e dos ícones conforme os módulos permitidos.
- `src/public/assets/css/atendimento/admin.css`: estilos dos painéis, cartões, conversas e formulários.

### 6.3. Menu lateral

As opções da equipe foram colocadas em um menu lateral. Ele pode apresentar:

- Início.
- Atendimento, com indicador de conversas sem resposta quando houver informação disponível.
- Mural de pedidos.
- Perguntas do quiz, para perfil autorizado.
- Usuários, para o perfil master.
- Voltar ao site e sair da sessão.

As opções dependem do perfil retornado pelo servidor. A navegação usa os caminhos já existentes; o trabalho visual não substituiu o controle de acesso do servidor.

No computador, o menu pode ser recolhido pelo botão ao lado da logo. Quando recolhido, a área principal recebe mais espaço. O estado aberto ou fechado fica guardado na `sessionStorage`, na chave `ajudooce-menu-equipe`, durante a sessão do navegador. O botão continua disponível para abrir o menu novamente.

No celular, a navegação da equipe fica recolhida e é aberta pelo botão de menu no topo. O código também mantém atributos como `aria-expanded` para indicar o estado do controle.

**Onde está:**

- `src/public/assets/js/navegacao.js`: identifica a área da equipe, monta as opções e controla a abertura do menu lateral.
- `src/public/assets/css/navegacao.css`: aparência do menu, ícones e comportamento em diferentes larguras.
- `src/public/assets/css/navegacao-local.css`: ajuste de espaço para o conteúdo quando o menu está aberto ou recolhido.

## 7. Ajuste na tela de triagem

Havia também uma alteração pendente no CSS da triagem. Ela ajusta a grade para permitir que as colunas encolham e que textos longos quebrem, reduzindo o risco de corte ou transbordamento, especialmente em telas menores.

**Onde está:** `src/public/assets/css/Pedro/Filtro/style.css`.

A correção veio da conversa sobre a primeira implementação de acessibilidade. Ela foi incluída no commit específico da triagem quando as mudanças foram organizadas.

## 8. Documentação do projeto e commits

### 8.1. Alterações de documentação que já estavam pendentes

As mudanças nos documentos da disciplina, nos arquivos README e no `AGENTS.md` foram reunidas no commit **“Alteração na documentação do projeto”**. O trabalho com as mídias de teste e o pedido de restaurar o modelo original do documento 09 estão detalhados no capítulo de histórico. [Histórico, documentação e verificações](Historico_e_verificacoes.md)

O `AGENTS.md` registra restrições do projeto, como o uso de HTML, CSS e JavaScript e a orientação de não implementar backend diretamente. O projeto existente já possui um servidor de atendimento; essa restrição não deve ser confundida com uma afirmação de que não existe servidor no código atual.

### 8.2. Commits registrados à época

Os commits foram refeitos a pedido, para separar melhor os assuntos e deixar os nomes mais claros. Na data da conferência, os commits atuais eram:

| Commit | Mensagem | Conteúdo principal |
| --- | --- | --- |
| `ba18991` | Adiciona acessibilidade e chat nas páginas do cliente | Controles, preferências, chat flutuante e regras de aparência do site do cliente. |
| `c995ad8` | Melhora os painéis de administrador e atendente com menu lateral | Visual da equipe e navegação lateral recolhível. |
| `b9e654f` | Evita corte de texto nas opções da triagem | Ajustes de grade e quebra de texto na tela de triagem. |
| `92803d5` | Alteração na documentação do projeto | Alterações de documentação e orientações que estavam pendentes. |

Os commits anteriores, com outros nomes e uma divisão diferente, foram substituídos localmente. Depois de refazê-los, foi conferido que a árvore de arquivos versionados resultante continuava igual à da sequência anterior. Não houve envio ao repositório remoto durante essa operação.

### 8.3. Arquivos locais de atendimento que não foram commitados

Na conferência, a pasta antiga `src/public/modulos/atendimento/dados/` aparecia como não rastreada pelo Git. Ela ficou fora dos commits porque contém arquivos de clientes, mensagens e usuários. A estrutura que o servidor atual usa para esses dados é `src/db/atendimento/dados/test/`.

Isso significa que o estado do repositório não estava completamente limpo. Antes de compartilhar ou versionar esses arquivos, é necessário revisar seu conteúdo e o destino desejado.

## 9. Última alteração: linha de leitura sobre o YouTube

### 9.1. O problema

O vídeo do podcast na página inicial é carregado dentro de um `iframe` do YouTube. Um `iframe` é uma página incorporada dentro de outra. Quando o ponteiro entra nesse conteúdo, o navegador passa os eventos para a página incorporada; por isso, a página principal deixa de receber os movimentos usados para atualizar a linha de leitura.

### 9.2. Como o ajuste foi implementado

Na página inicial do cliente:

1. Ao ativar a linha de leitura, o documento recebe a indicação `data-ajudo-linha="ativa"`.
2. Enquanto essa indicação estiver ativa, o `iframe` dentro de `.video-moldura` deixa de receber eventos do ponteiro. Assim, o movimento continua chegando à página, inclusive sobre a área do vídeo.
3. Nessa situação, aparece sobre o vídeo o botão **“Desativar linha e usar vídeo”**.
4. Ao clicar nesse botão, a linha é desativada, a preferência é atualizada e o foco é direcionado ao vídeo. Os controles do vídeo voltam a receber o ponteiro.
5. Ao desligar a linha pelo painel de acessibilidade, os controles também voltam a ficar disponíveis.

Essa solução tem uma consequência importante: **a linha e os controles de mouse do vídeo não ficam ativos ao mesmo tempo**. O botão sobre o vídeo deixa essa troca disponível sem que a pessoa precise procurar novamente o painel de acessibilidade.

O ajuste está ligado à estrutura `.video-moldura` usada atualmente na página inicial. Caso outros vídeos sejam incorporados com outra estrutura, será preciso verificar se eles precisam de adaptação semelhante.

### 9.3. Arquivos alterados nessa última etapa

- `src/public/modulos/Kayllon/usuario.html`: acrescenta o botão junto ao vídeo.
- `src/public/assets/css/Kayllon/usuario.css`: posiciona e estiliza o botão sobre o vídeo.
- `src/public/assets/css/acessibilidade.css`: impede que o `iframe` receba o ponteiro enquanto a linha está ativa.
- `src/public/assets/js/acessibilidade.js`: controla a visibilidade do botão, desativa a linha ao usá-lo e atualiza a preferência.

**Situação histórica:** esses quatro arquivos estavam modificados quando o guia foi escrito. O ajuste foi depois registrado no commit `d31a731`, presente na branch `test` conferida.

## 10. O que foi verificado e o que ainda falta

### Verificações feitas durante a conversa

- Foi executada a verificação de sintaxe do JavaScript de acessibilidade e de navegação com `node --check` em momentos apropriados.
- Foi usado `git diff --check` para conferir espaços e formatação dos arquivos das alterações correspondentes.
- Foram feitas capturas em navegador sem interface visível para examinar a central de ajuda em tema escuro e em alto contraste no computador. Nessas capturas foram observados o banner, a logo, os cartões e os botões flutuantes.
- Foi conferido que os commits refeitos produziam a mesma árvore de arquivos versionados da sequência anterior.

### Limites dessas verificações

- As capturas da central não provam que todas as páginas do site foram conferidas visualmente.
- A tentativa de captura em largura de celular não permitiu uma validação confiável da viewport; portanto, não foi considerada um teste completo de celular.
- A tentativa automatizada de testar a interação da linha de leitura com o vídeo não concluiu. A alteração da seção 9 ainda precisa de teste manual no navegador.
- As verificações realizadas não equivalem, por si só, a uma auditoria de acessibilidade nem a testes com pessoas do público-alvo.
- Para verificar o chat e funções que dependem de dados, é necessário executar o servidor do projeto; verificar somente a aparência não confirma o envio ou recebimento de mensagens.

## 11. Como conferir manualmente

Dentro da pasta do repositório, o projeto informa que pode ser iniciado com:

```powershell
npm start
```

Se o PowerShell bloquear o executável `npm`, o README do projeto sugere:

```powershell
npm.cmd start
```

Depois, abra o endereço informado pelo servidor. Para verificar as alterações:

1. Abra uma página do cliente e confirme que acessibilidade e chat aparecem no canto inferior direito, um acima do outro.
2. Abra a acessibilidade, altere o tamanho e o espaçamento do texto e restaure as configurações.
3. Ative o tema escuro e confirme que o botão passa a dizer “Tema claro”; depois volte ao tema claro.
4. Ative o alto contraste e confirme que o botão passa a dizer “Contraste padrão”. Confira a logo, as bordas e os ícones.
5. Na central de ajuda, confira se a imagem da pessoa permanece no banner e se os cantos estão arredondados.
6. Entre no painel da equipe com uma conta autorizada. Confira as opções disponíveis para o perfil, abra e recolha o menu no computador e teste o menu em largura de celular.
7. Na página inicial do cliente, ative a linha de leitura e mova o ponteiro sobre o vídeo do podcast. A linha deve continuar se movendo.
8. Clique em “Desativar linha e usar vídeo” e confira se a linha desaparece e se os controles do YouTube podem ser usados. O carregamento do vídeo depende da conexão e da disponibilidade do YouTube.
9. Repita as verificações relevantes em um celular real ou em uma emulação confiável, incluindo navegação por teclado quando possível.

Este roteiro descreve o resultado esperado; os itens que ainda não foram validados não devem ser tratados como testes já aprovados.
