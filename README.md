# Catálogo de prompts

Coleção de prompts em Markdown organizados por categoria/área de domínio. Cada prompt vive em sua própria pasta, contendo o arquivo `prompt.md` (texto puro, pronto para copiar e colar) e um `README.md` com metadados, variáveis e exemplos de uso.

Convenções de estrutura, nomenclatura e manutenção estão em [`CLAUDE.md`](./CLAUDE.md).

## Como usar

1. Navegar até a categoria de interesse.
2. Abrir o `README.md` do prompt para entender objetivo, variáveis esperadas e limitações.
3. Copiar o conteúdo do `prompt.md` e substituir os placeholders `{{nome_variavel}}` pelos valores desejados.

## Adicionando um prompt

Use o slash command [`/catalogar`](./.claude/commands/catalogar.md) passando o texto do prompt como argumento. Ele analisa, propõe organização (categoria, slug, frontmatter) e, após sua aprovação, escreve os arquivos e atualiza os índices — sem commitar. Convenções completas em [`CLAUDE.md`](./CLAUDE.md).

## Categorias

### [Desenvolvimento](./desenvolvimento/)

Escrita, revisão e refatoração de código, design de APIs e arquitetura, debugging, testes e documentação técnica.

_Nenhum prompt cadastrado ainda._

### [DevOps](./devops/)

Pipelines de CI/CD, containers, orquestração, infraestrutura como código, observabilidade, SRE e segurança operacional.

- [diagnosticar-incidente-kubernetes-k8sgpt](./devops/diagnosticar-incidente-kubernetes-k8sgpt/) — Investiga a causa-raiz de um incidente Kubernetes usando K8sGPT como única fonte de coleta (somente leitura), priorizando o MCP Server do K8sGPT e recorrendo ao binário via terminal apenas quando uma capacidade específica não estiver exposta pelo MCP. Entrega um RCA em três tópicos — causa-raiz, resumo da solução e procedimento técnico.

<!--
Ao adicionar um prompt, substituir "Nenhum prompt cadastrado ainda" pela lista:

- [nome-do-prompt](./<slug-da-categoria>/<slug-do-prompt>/) — o que o prompt faz, em uma linha.
-->

## Contribuindo

Antes de adicionar ou alterar um prompt, revisar [`CLAUDE.md`](./CLAUDE.md) — a seção **Manutenção da documentação** lista todos os arquivos que precisam ser atualizados junto com a mudança (este índice incluso).
