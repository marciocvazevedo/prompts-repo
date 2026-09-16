---
nome: Diagnosticar Causa-Raiz de Incidente Kubernetes via K8sGPT (Híbrido: MCP Server + Terminal)
descricao: Investiga a causa-raiz de um incidente Kubernetes usando K8sGPT como única fonte de coleta (somente leitura), priorizando o MCP Server do K8sGPT e recorrendo ao binário via terminal apenas quando uma capacidade específica não estiver exposta pelo MCP. Entrega um RCA em três tópicos — causa-raiz, resumo da solução e procedimento técnico.
versao: 2.0.0
tags: [kubernetes, k8sgpt, rca, sre, devops, mcp]
inputs:
  - nome: DESCRICAO_DO_PROBLEMA
    descricao: Texto descritivo livre do problema real observado no cluster.
  - nome: NAMESPACES_ALVO
    descricao: Namespaces prioritários para a investigação; se vazio, a coleta começa pelo escopo completo e reduz conforme as evidências.
  - nome: JANELA_DE_TEMPO
    descricao: Janela de tempo do incidente (ex. "2026-02-11 14:00Z a 16:30Z"); se vazio, é derivada do que o K8sGPT indicar.
---

# Diagnosticar Causa-Raiz de Incidente Kubernetes via K8sGPT (Híbrido: MCP Server + Terminal)

## Objetivo

Investigar a causa-raiz de um incidente real em um cluster Kubernetes usando exclusivamente
análises do K8sGPT em modo somente leitura — priorizando o MCP Server do K8sGPT como via de
coleta e recorrendo ao binário via terminal apenas para cobrir capacidades não expostas pelo
MCP — testando hipóteses de quatro perspectivas (DevOps, Plataforma, SRE, Backend/Full Stack)
até convergir em uma causa-raiz sustentada por evidência, e entregar um único arquivo Markdown
com três tópicos: causa-raiz, resumo da solução e procedimento técnico detalhado para o
administrador Kubernetes executar.

## Quando usar

- Quando um incidente já ocorreu no cluster e é preciso investigar a causa sem aplicar
  nenhuma alteração.
- Quando há um MCP Server do K8sGPT conectado e se quer usá-lo como via primária de coleta,
  com fallback documentado para o terminal apenas quando uma capacidade específica não
  estiver exposta pelo MCP.
- Quando o acesso disponível para o agente é limitado ao K8sGPT (sem `kubectl`/`helm`), seja
  via MCP, seja via terminal, e a coleta precisa ficar restrita a comandos de leitura.
- Quando o time quer um documento curto e acionável (causa-raiz, resumo para aprovação e
  procedimento técnico) em vez de um relatório extenso.
- Quando a causa-raiz precisa ser rastreável a evidências reais, sem suposições apresentadas
  como fato.

## Exemplo de uso

_A preencher_

## Limitações conhecidas

- Depende do K8sGPT estar acessível por pelo menos uma das duas vias (MCP Server ou terminal)
  e, idealmente, com o backend de IA autenticado; sem autenticação, a análise roda em modo
  degradado (sem `--explain`).
- Se o MCP Server não expuser uma capacidade necessária (ex.: anonimização, um filtro de
  analyzer específico), o fallback ao terminal é obrigatório e precisa ser justificado no log
  interno de evidências — sem essa via de reforço configurada, aquela capacidade específica
  fica indisponível.
- Não usa `kubectl`, `helm`, `oc`, `crictl` ou chamadas diretas à API do Kubernetes por
  nenhuma das duas vias — dados como histórico de rollout, logs completos e métricas de
  série temporal ficam fora do alcance e aparecem como `[fora do alcance do K8sGPT]`.
- Pode concluir "causa-raiz não determinada" quando as evidências disponíveis não bastam;
  nesse caso o procedimento entregue vira um roteiro de investigação manual, não de correção.
