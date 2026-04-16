---
name: Progresso do pré-projeto
description: Estado atual do pré-projeto após pivot para revisão bibliográfica pura (2026-04-15)
type: project
---

## Título atual (definido pelo orientador, 2026-04-15)
**"Shift-Left Security: Detecção de Vulnerabilidades em Docker Imagens"**

⚠️ "Docker Imagens" é anglicismo; o correto em português seria "Imagens Docker". João foi avisado e deve confirmar com o orientador.

## Tipo de pesquisa
**Revisão bibliográfica pura.** Testes práticos foram removidos por decisão do orientador + alinhamento ao template institucional.

## Problema de pesquisa (reformulado)
"O que a literatura científica publicada entre 2020 e 2026 evidencia sobre a detecção de vulnerabilidades em imagens Docker no contexto de shift-left security e sobre os critérios que devem orientar a escolha de ferramentas automatizadas de escaneamento?"

## Objetivo geral (reformulado)
Analisar, por meio de revisão bibliográfica, o estado da arte sobre detecção de vulnerabilidades em imagens Docker no contexto de shift-left security.

## Objetivos específicos (3, após remoção do item de testes práticos)
1. Analisar, a partir da literatura, os principais vetores de ataques à cadeia de suprimentos de software em imagens Docker.
2. Comparar, com base em estudos empíricos publicados, as ferramentas (Trivy, Grype, Clair) quanto a cobertura de CVEs, integração com CI/CD, desempenho e demais critérios reportados.
3. Sintetizar recomendações para adoção de ferramentas conforme diferentes perfis organizacionais, com base na literatura.

## Status das seções (renumerado 2026-04-16 para alinhar à ordem do template)
| Seção | Arquivo | Status |
|---|---|---|
| Tema | TEMA.md | Desatualizado (fala de testes práticos) — avaliar se precisa atualizar ou arquivar |
| Introdução | 1-INTRODUCAO.md | Rascrito atendendo 6 pontos do orientador |
| Justificativa | 2-JUSTIFICATIVA.md | Reescrita atendendo 5 pontos; hipótese reformulada |
| Objetivos | 3-OBJETIVOS.md | Atualizado (1 geral + 3 específicos) |
| Metodologia | 4-METODOLOGIA.md | Reescrita completa (revisão bibliográfica, 9 pontos) |
| Cronograma | 5-CRONOGRAMA.md | Etapa 2 ajustada (sem testes práticos) |
| Referências | 6-REFERENCIAS.md | 17 refs ABNT, mantido |
| Referencial Teórico | _REFERENCIAL-TEORICO-TCC.md | Removido do pré-projeto; aviso no topo; preservado para o TCC (prefixo `_` indica extra) |

**Arquivos descontinuados (apagados em 2026-04-16):** `PRE-PROJETO.md` (consolidado antigo com escopo de testes práticos) e `RELATORIO-CITACOES.md` (auditava o arquivo antigo; problemas já corrigidos nos arquivos novos).

**Why:** Orientador enviou em 2026-04-15 novo título + rubricas detalhadas (6 pontos intro, 5 pontos justificativa, 9 pontos metodologia) + pediu remoção do objetivo específico de testes práticos.

**How to apply:** João pediu explicitamente para executar as mudanças (override da regra de "não escrever o texto"). Próximo passo é ele revisar os arquivos e enviar ao orientador.
