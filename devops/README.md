# DevOps

Pipelines de CI/CD, containers, orquestração, infraestrutura como código, observabilidade, SRE e segurança operacional.

## Escopo

- Pipelines de CI/CD e automação de deploy.
- Containers e orquestração (Docker, Kubernetes).
- Infraestrutura como código.
- Observabilidade, SRE e resposta a incidentes.
- Segurança operacional.

## Fora de escopo

- Escrita, revisão e refatoração de código de aplicação — ver [`desenvolvimento/`](../desenvolvimento/).

## Prompts

- [diagnosticar-incidente-kubernetes-k8sgpt](./diagnosticar-incidente-kubernetes-k8sgpt/) — Investiga a causa-raiz de um incidente Kubernetes usando K8sGPT como única fonte de coleta (somente leitura), priorizando o MCP Server do K8sGPT e recorrendo ao binário via terminal apenas quando uma capacidade específica não estiver exposta pelo MCP. Só executa se houver evidência positiva de que o contexto ativo do kubeconfig está vinculado a um ClusterRole estritamente de leitura, sem nenhum verbo de escrita em nenhum recurso. Entrega um RCA em três tópicos — causa-raiz, resumo da solução e procedimento técnico.
