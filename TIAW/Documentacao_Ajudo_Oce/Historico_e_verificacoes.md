# Histórico, documentação e verificações

[Voltar ao guia](Guia_das_alteracoes.md)

## Primeiros registros do projeto

O histórico do Git começa com a estrutura da disciplina no GitHub Classroom (`c9f9f52` e `080fcc3`). Em seguida aparecem a definição do problema, público, objetivos e justificativa (`c97ded0` e `30ba400`), a descoberta e concepção do produto (`b294158` e `abf0997`), os requisitos (`db4edf5`) e o trabalho de interface (`2d9db55` e `901c1ae`).

O grupo organizou a descoberta com entrevistas, personas e propostas de valor, e passou a acompanhar as entregas em branches e no GitHub Projects. A documentação da disciplina começou pelos modelos do projeto e passou a reunir requisitos, fluxos e protótipos. Os capítulos de funcionalidades refletem o estado do código, que em alguns pontos segue caminhos diferentes do protótipo.

| Etapa encontrada no Git | O que entrou no projeto |
| --- | --- |
| Central de Ajuda | Página, banner, busca, categorias e perguntas expansíveis, contato, responsividade e atalho de chat. |
| Entregas dos módulos | Página inicial e voluntariado, triagem e avaliação, mural e certificado, quiz e resultados, conteúdos de conhecimento e segurança e relato de golpes. |
| `f34cba3` e `ac801c1` | Primeira troca de mensagens com resposta automática e correções de fechamento da janela e rolagem. |
| `7986090` | Login e funções da equipe, página inicial e separação por perfil. |
| `0ce5940` | Cadastro, login e saída do cliente, associação da conta ao chat, notificações e Painel do Atendente. |
| `e022c60` e `52ea3f1` | Integração dos módulos do grupo e reorganização das pastas na branch `test`. |
| `909c880` | Revisão de documentação e registro de 12 cenários executados parcial ou integralmente em uma cópia isolada. |
| `9b49afb` | Consolidação do servidor e dos dados dos módulos na estrutura atual. |
| `19db8cb` | Padronização da navegação e da organização dos arquivos e integração do mural e do quiz. |

Esses registros estabelecem a sequência das entregas. O Git permite identificar a mudança, mas não conserva o texto de um pedido feito em conversa. A versão `173da3e`, da branch `icaro`, registra outra reorganização do atendimento. A versão mais desenvolvida da área de conhecimento permaneceu em `origin/Rayssa`. O guia usa as pastas e os caminhos da branch `test`, que reúne a integração atual.

## Solicitações recuperadas das conversas

### Cabeçalho da Central e regra da disciplina

O primeiro pedido recuperado foi melhorar o cabeçalho e o design do `index` da Central de Ajuda. As revisões incluíram marca, navegação, banner, busca, cartões e versão móvel. Na mesma conversa, foi solicitado guardar a orientação da disciplina para as próximas tarefas. O arquivo `AGENTS.md` registrou HTML, CSS e JavaScript como base, Node.js quando necessário e a orientação de evitar implementação direta de backend. A conversa também teve um pedido sobre a execução do Codex no terminal. Ele dizia respeito à ferramenta de trabalho.

A Central foi reorganizada mais tarde para a estrutura atual. O capítulo de atendimento descreve a primeira revisão visual e a versão disponível agora. [Central, contas e atendimento](Central_contas_e_atendimento.md)

### Gravações, registro de testes e revisão dos documentos

Primeiro foi pedido refazer as gravações de testes para mostrar a movimentação do ponteiro com calma, digitação letra por letra e rolagem fluida, além de atualizar o documento 09 com os novos vídeos. O trabalho chegou a preparar gravações com ponteiro e digitação progressiva, segundo o relato intermediário.

O pedido seguinte mudou a entrega. Como o código continuaria mudando, o grupo decidiu deixar o registro para mais tarde. O documento 09 voltou ao modelo original, e as 15 imagens e os 12 vídeos de testes foram removidos da árvore atual. A versão anterior e seus resultados continuam registrados no histórico do Git. A revisão consultou os modelos da disciplina, adotou a voz do grupo, retirou datas e referências às evidências removidas e atualizou as instruções de execução. O relato de conclusão daquela conversa registra também a conferência dos links locais.

| Arquivo revisado | Mudança de conteúdo |
| --- | --- |
| `README.md` | Apresentação do Ajudo Ocê e instruções de execução local e acesso da equipe. |
| `docs/01-Contexto.md` | Introdução, problema e objetivos reescritos na voz do grupo. |
| `docs/02-Product-discovery.md` | Organiza o material de descoberta, entrevistas e personas e registra os mapas de empatia a completar. |
| `docs/03-Product-design.md` | Relaciona histórias, requisitos e restrições ao estado das funcionalidades. Explicita a questão do servidor próprio. |
| `docs/04-Metodologia.md` | Explica o trabalho com design thinking, Scrum, Git, branches e GitHub Projects. Registra que ainda falta definir a publicação. |
| `docs/05-Projeto-interface.md` | Alinha fluxos, protótipos e esboços. Distingue o login previsto no protótipo e o fluxo de e-mail e senha implementado. |
| `docs/06-Template-padrao.md` | Descreve referências de cor, tipografia e organização visual da interface. |
| `docs/07-Arquitetura-solucao.md` | Explica a estrutura, rotas, arquivos JSON, armazenamento do navegador, versão local em Node.js e recursos ainda parciais. |
| `docs/08-Plano-testes-software.md` | Mantém 21 cenários planejados, separa os que dependem de implementação e deixa o registro final para execução posterior. |
| `docs/09-Registro-testes-software.md` | Volta ao modelo inicial da disciplina, com exemplos e campos destinados ao futuro registro. |
| `docs/10-Referencias.md` | Ajusta a lista; os anos de publicação e as datas de acesso foram retirados a pedido. |
| `presentation/README.md` | Descreve a futura apresentação e a demonstração de até cinco minutos. |
| `src/README.md` | Explica a organização de `src/` e como executar a versão local. |
| `AGENTS.md` | Registra as tecnologias e a restrição da disciplina para mudanças futuras. |

A definição dos responsáveis pelos testes, os mapas de empatia e um endereço de publicação estavam pendentes na documentação conferida. O projeto já possui um servidor Node.js para a versão local. O documento de arquitetura registra a necessidade de adequar essa parte à restrição de front-end da disciplina.

### Primeira implementação da acessibilidade

Em uma conversa anterior ao reposicionamento do botão, foi pedido criar um painel com aumento e redução de texto, contraste, espaçamento, restauração e uma linha de leitura visível sem cobrir o conteúdo. A implementação incluiu preferências salvas no navegador e controle da linha pelo ponteiro, toque e teclado. Também foi corrigido o problema de largura das opções da triagem quando o texto cresce.

O relato final daquela etapa registra testes no Microsoft Edge de controles, teclado, persistência, restauração, conteúdo dinâmico e toque simulado. Em cinco páginas verificadas com largura de 320 px e texto em 150%, não foi observado transbordamento horizontal. Esse resultado se refere à versão inicial da acessibilidade, antes dos ajustes seguintes.

### Ajustes que vieram depois

1. **Acessibilidade e chat.** Subimos o botão de acessibilidade, trocamos o texto visível pelo ícone de pessoa e colocamos o chat logo abaixo. O chat passou a ser carregado nas páginas públicas cobertas pela navegação compartilhada. A janela recebeu ajustes de tamanho e o espaçamento de texto passou a tratar letras, palavras, linhas e separação de parágrafos.
2. **Área da equipe.** Retiramos os controles flutuantes dessas telas, revisamos o visual de início, conversas e usuários e passamos as opções para o menu lateral conforme o perfil. No computador, o menu passou a abrir e recolher para dar mais espaço ao conteúdo. O botão foi movido para o lado da logo após sobrepor a barra de rolagem.
3. **Tema escuro.** Criamos a opção e a preferência persistente. O botão passou a mostrar a ação seguinte. Harmonizamos azuis, ícones, contornos e fundos, tratamos a logo para exibir letras claras e corrigimos as faixas ao redor da Central. A ilustração do banner foi ocultada numa revisão intermediária e voltou após o pedido para manter a pessoa. Excluímos o contêiner dos botões da regra que pintava fundos quadrados e reforçamos os cantos arredondados.
4. **Alto contraste.** Trocamos a lista por um botão cujo texto muda para **Contraste padrão** quando ativo. Depois ajustamos fundos, ícones, bordas, logo e controles em preto, branco e amarelo. A imagem do banner foi preservada.
5. **Commits.** As mudanças pendentes foram registradas localmente. Depois do pedido de títulos mais específicos, a sequência foi refeita em quatro commits, preservando o conteúdo versionado. A retirada da mídia de testes ficou junto das mudanças de documentação.
6. **Linha de leitura e YouTube.** A linha passou a ter um modo para atravessar a área do vídeo da página inicial. Enquanto a linha estiver ligada, aparece um botão para desligá-la e usar o vídeo. Esse ajuste ainda está nos arquivos locais.
7. **Documentação externa.** O primeiro guia aprofundava a conversa mais recente. Esta revisão acrescenta o histórico disponível, os fluxos anteriores e o inventário do projeto na mesma pasta `TIAW/Documentacao_Ajudo_Oce/`.

Os detalhes dessas mudanças, arquivos e instruções para uso estão no capítulo de interface. [Acessibilidade e interface](Acessibilidade_e_interface.md)

## Histórico de testes recuperado

`git show 909c880:docs/09-Registro-testes-software.md` permite consultar, em leitura, o relatório da versão anterior. Ele descreve testes em uma cópia isolada do projeto. A tabela abaixo resume as observações daquela versão.

| Cenário | Resultado registrado na época |
| --- | --- |
| CT-001 Navegação | Cabeçalho, rodapé e link do quiz carregaram. A entrada administrativa não apareceu no menu público. |
| CT-002 Busca | A pesquisa por “certificado” encontrou duas perguntas. O conteúdo das respostas ainda era provisório. |
| CT-003 Conta de cliente | Um cadastro fictício foi aceito e o primeiro nome apareceu no cabeçalho. O caso não cobriu o cadastro completo de voluntários. |
| CT-004 Chat | Parcial. A mensagem apareceu no painel e a resposta voltou à Central. Tempo de resposta e vínculo com voluntário ficaram fora do cenário. |
| CT-005 Quiz | Parcial. O fluxo de dez perguntas exibiu a pontuação. O quiz usava alternativas em vez de verdadeiro ou falso. |
| CT-006 Certificado | Parcial. Os dados apareceram na prévia. O cenário não gerou nem conferiu um PDF final. |
| CT-007 Triagem | Parcial. O formulário avançou até a próxima tela. A etapa em desenvolvimento e a tela de chat eram protótipos. |
| CT-008 Avaliação | Parcial. Quatro estrelas exibiram confirmação. A avaliação ainda não estava vinculada nem gravada. |
| CT-009 Relato de golpe | Parcial. A confirmação exibiu o relato fictício guardado no navegador. |
| CT-010 Mural | Parcial. O acesso sem sessão foi recusado, e atendente e administrador moveram exemplos. O mural ainda não recebia pedidos públicos automaticamente. |
| CT-011 Voluntariado | O filtro de urgência mostrou dois pedidos de exemplo. |
| CT-012 Página inicial no celular | Menu abriu e a página não teve rolagem horizontal na largura simulada de 390 px. |
| CT-013 a CT-021 | Não executados naquele registro. |

Na conversa mais recente, houve conferências de sintaxe e de formatação do diff, além de capturas da Central em desktop com tema escuro e alto contraste. A tentativa de validar a interação da linha com o vídeo não concluiu. A captura móvel mais recente também não permitiu conferir a largura com precisão. O relato dos testes iniciais de 320 px e o teste histórico de 390 px são de versões anteriores.

## Commits da sequência atual

| Commit | Mensagem |
| --- | --- |
| `ba18991` | Adiciona acessibilidade e chat nas páginas do cliente |
| `c995ad8` | Melhora os painéis de administrador e atendente com menu lateral |
| `b9e654f` | Evita corte de texto nas opções da triagem |
| `92803d5` | Alteração na documentação do projeto |

A primeira sequência de seis commits foi substituída pela sequência acima. A verificação feita na ocasião confirmou que os arquivos versionados ao final continuaram com o mesmo conteúdo. Esses commits ficaram locais na branch `test`. O ajuste do YouTube e os arquivos de dados da estrutura antiga ficaram fora dos commits.
