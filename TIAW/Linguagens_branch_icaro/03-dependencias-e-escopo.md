# Dependências e escopo — icaro

## Contagem dos arquivos versionados por tipo

A contagem abaixo considera extensões e nomes conhecidos; não conta linhas, esforço, importância nem mede funcionalidade. Um arquivo HTML ou JavaScript pode conter SVG embutido.

| Tipo | Arquivos fora de node_modules |
| --- | ---: |
| CSS | 7 |
| HTML | 10 |
| JavaScript | 13 |
| JSON | 8 |
| Markdown | 14 |
| YAML/CFF | 2 |

## Bibliotecas em node_modules

O repositório também contém `1099` caminhos versionados em `node_modules`. São pacotes e arquivos distribuídos por terceiros; não são automaticamente código de autoria da equipe. Eles podem incluir JavaScript de distribuição (`.js`, `.mjs`, `.cjs`), arquivos TypeScript (`.ts`) e declarações de tipos (`.d.ts` e `.d.mts`), JSON, Markdown e scripts de execução no Windows ou em shell. Declarações TypeScript descrevem tipos para ferramentas; a presença delas não demonstra que a aplicação própria foi programada em TypeScript.

| Tipo reconhecido em dependências | Arquivos |
| --- | ---: |
| CMD | 2 |
| Declarações TypeScript | 386 |
| HTML | 1 |
| JavaScript | 483 |
| JSON | 48 |
| Markdown | 47 |
| PowerShell | 2 |
| TypeScript | 2 |

Os pacotes declarados devem ser conferidos em `package.json` e `src/package.json`; eles podem usar versões diferentes. `package-lock.json` registra a árvore resolvida de dependências. A presença de biblioteca no diretório não comprova que cada arquivo dela seja executado pela aplicação.

## Situação no momento da análise

A árvore de trabalho estava limpa na conferência; o inventário corresponde aos arquivos versionados no commit indicado.

Nenhuma alteração versionada local foi indicada na análise.

## O que esta análise cobre

O mapa lista individualmente código e configurações versionados em `src`, além de identificar as tecnologias e arquivos de terceiros por tipo. Arquivos binários, imagens, fontes, documentos PDF e arquivos locais de dados sensíveis não são código-fonte de aplicação e não têm seu conteúdo reproduzido. Não foi executada uma auditoria linha a linha das bibliotecas de terceiros, nem inferida a autoria de cada arquivo versionado.
