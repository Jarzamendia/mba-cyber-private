# URLs Prontas para Executar no Navegador

<!--
Como usar:
- Clique no link "Abrir" → cai na página de busca avançada do agregador.
- Cole a "String para colar" no campo indicado e execute.
- Filtros adicionais (período, tipo, idioma) devem ser aplicados na UI.
- Após executar, registre o total de resultados em buscas/PLANILHA-BUSCA.md.
-->

## IEEE Xplore

**Página base:** https://ieeexplore.ieee.org/search/advanced (aba "Command Search")
**Filtros a aplicar na UI após a busca:**
- Year Range: 2020–2026
- Content Type: Conferences, Journals, Early Access
- Publisher: IEEE (ou ampliar conforme resultado)

### 1. Ampla (A AND B)
```
("Abstract":"Docker image" OR "container image") AND ("Abstract":"vulnerability scan*" OR "CVE" OR "image scanning")
```

### 2. Obj. 1 — Ataques SSC em Docker
```
("Abstract":"Docker" OR "container image") AND ("Abstract":"software supply chain" OR "SBOM") AND ("Abstract":"attack" OR "threat" OR "taxonomy")
```

### 3. Obj. 2 — Comparação de ferramentas
```
("Abstract":"Trivy" OR "Grype" OR "Clair") AND ("Abstract":"comparison" OR "evaluation" OR "benchmark" OR "discrepanc*")
```

### 4. Obj. 3 — Shift-left e CI/CD
```
("Abstract":"Docker" OR "container") AND ("Abstract":"vulnerability scan*") AND ("Abstract":"shift-left" OR "DevSecOps" OR "CI/CD")
```

---

## ACM Digital Library

**Página base:** https://dl.acm.org/search/advanced
**Filtros a aplicar na UI após a busca:**
- Publication Date: 2020-01-01 to 2026-12-31
- Content Type: Research Article, Short Paper

### 1. Ampla (A AND B)
```
[[Abstract: "docker image"] OR [Abstract: "container image"]] AND [[Abstract: "vulnerability"] OR [Abstract: "CVE"] OR [Abstract: "image scanning"]]
```

### 2. Obj. 1 — Ataques SSC em Docker
```
[[Abstract: "docker"] OR [Abstract: "container image"]] AND [[Abstract: "supply chain attack"] OR [Abstract: "supply chain security"]]
```

### 3. Obj. 2 — Comparação de ferramentas
```
[[Abstract: "Trivy"] OR [Abstract: "Grype"] OR [Abstract: "Clair"]] AND [[Abstract: "comparison"] OR [Abstract: "evaluation"] OR [Abstract: "benchmark"]]
```

### 4. Obj. 3 — Shift-left e CI/CD
```
[[Abstract: "container"] OR [Abstract: "docker"]] AND [[Abstract: "shift-left"] OR [Abstract: "DevSecOps"]] AND [[Abstract: "vulnerability"] OR [Abstract: "CI/CD"]]
```

---

## Google Scholar (links diretos, período já filtrado)

> Filtro 2020–2026 embutido via `as_ylo` e `as_yhi`.
> Scholar não suporta busca por campo; usa apenas texto livre.

### 1. Ampla
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%22docker+image%22+%28%22vulnerability+scanning%22+OR+%22CVE+detection%22+OR+%22image+scanning%22%29

### 2. Obj. 1 — Ataques SSC em Docker
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%22software+supply+chain%22+%28%22docker%22+OR+%22container+image%22%29+%28%22attack%22+OR+%22taxonomy%22%29

### 3. Obj. 2 — Comparação de ferramentas
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%28Trivy+OR+Grype+OR+Clair%29+%28%22comparison%22+OR+%22evaluation%22+OR+%22discrepancies%22%29+docker

### 4. Obj. 3 — Shift-left e CI/CD
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%28%22shift-left+security%22+OR+%22DevSecOps%22%29+%28%22docker%22+OR+%22container%22%29+%28%22CI%2FCD%22+OR+%22pipeline%22%29

### 5. Busca por título (maior precisão)
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=intitle%3A%28%22docker%22+OR+%22container%22%29+intitle%3A%28%22vulnerability%22+OR+%22security%22%29

---

## arXiv (opcional — API pública)

<!-- Disparados em 2026-04-16; resultados em arxiv-2026-04-16-*.md -->

Busca ampla já executada: 31 resultados, 7 relevantes novos. Ver `arxiv-2026-04-16-ampla-AB.md`.

Queries pendentes (rodar com delay de 3s entre requests para não levar 429):

1. **Obj.1 — A AND D:**
   http://export.arxiv.org/api/query?search_query=%28abs%3A%22docker%22+OR+abs%3A%22container+image%22%29+AND+%28abs%3A%22software+supply+chain%22+OR+abs%3A%22SBOM%22%29&start=0&max_results=30&sortBy=relevance

2. **Obj.3 — A AND B AND C:**
   http://export.arxiv.org/api/query?search_query=%28abs%3A%22docker%22+OR+abs%3A%22container%22%29+AND+abs%3A%22vulnerability%22+AND+%28abs%3A%22shift-left%22+OR+abs%3A%22DevSecOps%22+OR+abs%3A%22CI%2FCD%22%29&start=0&max_results=30&sortBy=relevance

3. **Obj.2 refinada — E AND A:**
   http://export.arxiv.org/api/query?search_query=%28abs%3A%22Trivy%22+OR+abs%3A%22Grype%22+OR+abs%3A%22Clair%22%29+AND+%28abs%3A%22Docker%22+OR+abs%3A%22container+image%22+OR+abs%3A%22vulnerability+scanner%22%29&start=0&max_results=30&sortBy=relevance

---

## Fluxo sugerido

1. Abrir IEEE Xplore → executar query **Ampla (#1)** → copiar nº total de resultados para a planilha.
2. Fazer triagem por título diretamente na UI do IEEE; marcar os candidatos.
3. Repetir para queries **Obj.1**, **Obj.2**, **Obj.3** do IEEE.
4. Repetir todo o ciclo para ACM DL.
5. Usar Scholar para capturar dissertações/teses e papers fora de IEEE/ACM.
6. Retomar arXiv (3 queries pendentes) numa próxima rodada.
7. Consolidar duplicatas na tabela de deduplicação da PLANILHA-BUSCA.md.
