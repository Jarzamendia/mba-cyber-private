# arXiv — Busca Ampla (A AND B)

**Data:** 2026-04-16
**Base:** arXiv (via API export)
**Query:** `(abs:"docker image" OR abs:"container image") AND (abs:"vulnerability" OR abs:"scanning")`
**URL:** http://export.arxiv.org/api/query?search_query=%28abs%3A%22docker+image%22+OR+abs%3A%22container+image%22%29+AND+%28abs%3A%22vulnerability%22+OR+abs%3A%22scanning%22%29&start=0&max_results=50&sortBy=relevance
**Total retornado:** 31

---

## Papers relevantes (pós triagem por título + resumo)

### Já na bibliografia

| arXiv ID | Autores | Ano | Título |
|---|---|---|---|
| 2101.03844 | Javed, Toor | 2021 | Understanding the Quality of Container Security Vulnerability Detection Tools |

### NOVOS — candidatos para leitura integral

<!-- CONFERIR: priorizar os marcados com ⭐ -->

| arXiv ID | Autores | Ano | Título | Por que relevante | Pri |
|---|---|---|---|---|---|
| 2503.14388 | Churakova, Ekstedt, Schmid | 2025 | Vexed by VEX tools: Consistency evaluation of container vulnerability scanners | Consistência entre scanners com VEX/SBOM — direto no núcleo do Obj. 2 | ⭐⭐⭐ |
| 2112.12597 | Haque, Babar | 2021 | Well Begun is Half Done: Exploitability & Impact of Base-Image Vulnerabilities | Empírico sobre imagens-base — Obj. 1 | ⭐⭐⭐ |
| 2006.02932 | Wist, Helsem, Gligoroski | 2020 | Vulnerability Analysis of 2500 Docker Hub Images | Escala grande, Docker Hub — Obj. 1/2 | ⭐⭐⭐ |
| 2506.08218 | Mills, White, Legg | 2025 | gh0stEdit: Exploiting Layer-Based Access Vulnerability Within Docker Container Images | Vetor de ataque em camadas Docker — Obj. 1 | ⭐⭐ |
| 2111.11475 | Wong, Chekole, Ochoa, Zhou | 2021 | Threat Modeling and Security Analysis of Containers: A Survey | Survey de threat modeling — fundamentação Obj. 1 | ⭐⭐ |
| 2008.04814 | Mullinix et al. | 2020 | On Security Measures for Containerized Applications Imaged with Docker | Medidas de segurança Docker — Obj. 1/3 | ⭐⭐ |
| 2010.13970 | Kaur, Dugré, Hanna, Glatard | 2020 | An Analysis of Security Vulnerabilities in Container Images for Scientific Data Analysis | Contexto específico (científico), pode servir como estudo de caso | ⭐ |

### Avaliar caso a caso

| arXiv ID | Autores | Ano | Título | Nota |
|---|---|---|---|---|
| 2509.09322 | Bufalino, Blaise, Secci | 2025 | ORCA: Unveiling Obscure Containers In The Wild | Sobre obscure containers — ler abstract completo |
| 2603.28988 | Tan, Singer, Anagnostopoulos | 2026 | Attesting LLM Pipelines | Envolve container images mas foco é LLM pipeline — provavelmente fora de escopo |

### Descartados (falsos positivos)

- 22 papers de processamento de imagem biomédica/astronômica (ruído do termo "container image" em outros contextos).
- Zerouali 2018 (1811.12874) — fora do recorte 2020-2026; considerar como clássico se necessário.

---

## Observações

- **Taxa de relevância:** ~23% (7 relevantes novos + 1 já conhecido / 31 retornados).
- **Sugestão de refinamento:** adicionar `AND cat:cs.CR` ou incluir "security" no cluster para reduzir ruído biomédico.
