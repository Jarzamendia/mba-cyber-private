# arXiv — Obj. 2 Ferramentas (E AND comparação)

**Data:** 2026-04-16
**Base:** arXiv (via API export)
**Query:** `(abs:"Trivy" OR abs:"Grype" OR abs:"Clair") AND (abs:"comparison" OR abs:"evaluation" OR abs:"benchmark")`
**Total retornado:** 15

---

## Resultado

**1 paper relevante** (já capturado pela busca ampla):
- Churakova et al. 2025 — Vexed by VEX tools (2503.14388)

**14 falsos positivos** — "Clair" aparece como:
- Nome próprio de ferramenta de captioning/avaliação de LLM (CLAIR, CLAIR-A, CLAIRE)
- Nome de pessoa (Claire Bauche-Arnoult)
- Outras siglas não relacionadas

---

## Diagnóstico

**Query inadequada para arXiv.** No arXiv os nomes "Trivy"/"Grype"/"Clair" têm muito ruído. Em bases revisadas por pares (IEEE/ACM) a precisão deve ser maior.

## Refinamento proposto

Adicionar cluster A (Docker/container) como filtro obrigatório:

```
(abs:"Trivy" OR abs:"Grype" OR abs:"Clair") AND (abs:"Docker" OR abs:"container image" OR abs:"vulnerability scanner")
```

<!-- CONFERIR: rodar a query refinada antes de encerrar a coleta no arXiv. -->
