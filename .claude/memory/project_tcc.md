---
name: Contexto do TCC
description: TCC sobre Segurança Shift-Left para Docker - análise de scanners e security gate em CI/CD
type: project
---

**Título definido:** "Análise e Implementação de Verificações Automatizadas de Segurança em Imagens Docker no Ciclo de Desenvolvimento"

**Decisão:** Título intencionalmente não menciona CI/CD para cobrir tanto pipeline quanto desenvolvimento local (pre-commit hooks, comandos manuais, IDE).

**Escopo planejado:**
1. Revisão bibliográfica sobre segurança shift-left e ataques à cadeia de fornecimento
2. Análise comparativa de scanners de vulnerabilidades (Trivy, Grype, Clair) - detecção, tempo, falsos positivos
3. Implementação em dois pontos: desenvolvimento local + pipeline CI/CD (GitHub Actions)
4. Security Gate automatizado em Python que bloqueia builds com vulnerabilidades críticas
5. Avaliação de eficácia do pipeline na detecção de vulnerabilidades conhecidas

**Motivações-chave do João (para justificativa):**
- Empresas não fazem scanning ou fazem pós-deploy (tarde demais)
- IA e automação eliminam o fator humano (cansaço, pular etapas)
- Ataques de supply chain crescentes (principalmente libs Node.js)
- Verificações proativas podem prevenir roubo de dados e ransomware

**Metodologia:** Pesquisa aplicada com abordagem mista (revisão bibliográfica + pesquisa experimental/laboratório)

**Documentação disponível no repositório:**
- `documentacao/guia-para-elaboracao-do-tcc.pdf` - Guia institucional para elaboração
- `documentacao/metodologia-da-pesquisa-cientifica.pdf` - Material sobre metodologia
- `documentacao/template-pre-projeto.docx` - Template do pré-projeto
- `documentacao/template-tcc.docx` - Template do TCC final

**Prazos:**
- Pré-projeto: 2026-03-27
- Segunda versão do TCC: 2026-04-16
- Versão final do TCC: 2026-05-06

**Orientador:** Designado, mas ainda não avaliou o tema. Vai avaliar junto com o pré-projeto.

**Nível técnico do João:** Experiência prática avançada em Docker, GitHub Actions e Python.

**Status em 2026-03-18:** Problema de pesquisa e objetivos definidos. Próximo passo: João vai rascunhar a justificativa em arquivo .md para revisão.

**Why:** Requisito de conclusão da pós-graduação em Cybersecurity.
**How to apply:** Prioridade imediata é o pré-projeto (deadline 27/03). Depois focar na escrita e implementação para a segunda versão (16/04). João tem nível técnico avançado, então a orientação deve focar mais no lado acadêmico/metodológico.
