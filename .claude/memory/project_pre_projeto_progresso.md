---
name: Progresso do pré-projeto
description: Decisões tomadas para o pré-projeto do TCC - título, problema, objetivos, estrutura da justificativa
type: project
---

## Título definido
"Análise e Implementação de Verificações Automatizadas de Segurança em Imagens Docker no Ciclo de Desenvolvimento"
- Intencionalmente não menciona CI/CD para cobrir tanto pipeline quanto desenvolvimento local.

## Problema de pesquisa
"Como uma organização pode precaver-se contra ataques de cadeia de fornecimento de software em imagens Docker através do uso de práticas de shift-left e automatização de detecção de vulnerabilidades no ciclo de desenvolvimento?"

## Objetivo geral
Analisar o uso de scanners de verificação automatizadas de vulnerabilidades em imagens Docker durante o ciclo de desenvolvimento de software para mitigar ataques de cadeia de fornecimento de software.

## Objetivos específicos
1. Identificar o estado da arte em verificação automatizada de vulnerabilidades em imagens Docker
2. Comparar os principais scanners de vulnerabilidade com base em: tempo de execução, taxa de detecção e falsos positivos
3. Propor e implementar os pipelines automatizados em ambiente de integração contínua
4. Avaliar os resultados e definir qual é o modelo mais adequado com base nos critérios definidos

## Justificativa (estrutura acordada, João vai rascunhar)
1. Cenário problemático - organizações não fazem scanning ou fazem pós-deploy (custo alto de correção)
2. Risco crescente - ataques supply chain em alta, especialmente npm/Node.js (event-stream 2018, ua-parser-js 2021, colors.js 2022). Imagens Docker herdam dependências vulneráveis
3. Limitação humana - processos manuais falham (fadiga, negligência, pular etapas)
4. Oportunidade - ferramentas open-source + CI/CD modernas tornam automação viável sem custo adicional
5. Hipótese - integração de scanners no ciclo de desenvolvimento (shift-left) detecta e bloqueia vulnerabilidades críticas antes da produção

## Seções do pré-projeto ainda pendentes
- Justificativa (João vai rascunhar em .md)
- Introdução / Problematização
- Metodologia (pesquisa aplicada, abordagem mista: revisão bibliográfica + experimental)
- Cronograma
- Referências (ABNT)

**Why:** Deadline do pré-projeto é 2026-03-27. Próximo passo é João escrever rascunho da justificativa.
**How to apply:** Quando João enviar o rascunho em .md, revisar e dar feedback mantendo postura de orientador (não reescrever).
