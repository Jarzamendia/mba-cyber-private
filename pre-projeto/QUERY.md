# Strings de Busca — Revisão Bibliográfica

<!--
CONFERIR antes de executar:
- Bases: IEEE Xplore, ACM Digital Library, Google Scholar (arXiv e Scopus removidos).
- Testar cada string; ajustar se resultado for >500 (restringir) ou <10 (ampliar).
- Filtros globais em todas as bases: período 2020–2026; idioma EN ou PT.
- Registrar resultados em buscas/PLANILHA-BUSCA.md.
-->

## Estratégia geral

Foco central: **Shift-Left Security** aplicado à **detecção de vulnerabilidades em imagens Docker**.
Nomes de ferramentas específicas não compõem a busca primária — aparecem apenas como filtro opcional (ver seção final).

**Clusters de conceitos:**

| Cluster | Termos |
|---|---|
| **A.** Imagem de container | `"Docker image" OR "container image" OR "OCI image"` |
| **B.** Shift-left / DevSecOps | `"shift-left" OR "shift left security" OR "DevSecOps" OR "secure SDLC"` |
| **C.** Detecção de vulnerabilidades | `"vulnerability detection" OR "vulnerability scanning" OR "static analysis" OR "CVE detection" OR "SBOM"` |
| **D.** Cadeia de suprimentos | `"software supply chain" OR "supply chain security" OR "supply chain attack"` |

**Combinações por objetivo:**

| Objetivo | Combinação |
|---|---|
| Busca geral | A **AND** C |
| Obj. a) — Vetores de ataque SSC em Docker | A **AND** D |
| Obj. b) — Técnicas de detecção em Docker no contexto shift-left | A **AND** B **AND** C |
| Obj. c) — Lacunas na literatura | A **AND** C **AND** ("research gap" OR "future work" OR "open issues") |

---

## 1. IEEE Xplore — Command Search

> Acesso: https://ieeexplore.ieee.org/search/advanced/command
> Sintaxe: `("Campo":"termo")`; operadores `AND`, `OR`, `NOT`; coringa `*`.
> Filtros na UI: Year Range 2020–2026; Content Type: Journals + Conferences.

**Busca geral (A AND C):**
```
("Abstract":"Docker image" OR "container image") AND ("Abstract":"vulnerability detection" OR "vulnerability scanning" OR "static analysis" OR "CVE")
```

**Obj. a) — Vetores de ataque SSC em Docker (A AND D):**
```
("Abstract":"Docker" OR "container image") AND ("Abstract":"software supply chain" OR "supply chain security" OR "supply chain attack")
```

**Obj. b) — Técnicas de detecção no contexto shift-left (A AND B AND C):**
```
("Abstract":"Docker image" OR "container image") AND ("Abstract":"shift-left" OR "DevSecOps") AND ("Abstract":"vulnerability detection" OR "vulnerability scanning" OR "static analysis")
```

**Obj. c) — Lacunas na literatura (A AND C AND lacunas):**
```
("Abstract":"Docker" OR "container image") AND ("Abstract":"vulnerability detection" OR "vulnerability scanning") AND ("Abstract":"research gap" OR "future work" OR "open issues" OR "limitation*")
```

---

## 2. ACM Digital Library — Advanced Search

> Acesso: https://dl.acm.org/search/advanced
> Sintaxe: `[[Abstract: "termo"]]`; operadores `AND`, `OR`.
> Filtros na UI: Publication Date 2020–2026; Content Type: Research Article.

**Busca geral (A AND C):**
```
[[Abstract: "docker image"] OR [Abstract: "container image"]] AND [[Abstract: "vulnerability detection"] OR [Abstract: "vulnerability scanning"] OR [Abstract: "static analysis"] OR [Abstract: "CVE"]]
```

**Obj. a) — Vetores de ataque SSC em Docker:**
```
[[Abstract: "docker"] OR [Abstract: "container image"]] AND [[Abstract: "software supply chain"] OR [Abstract: "supply chain security"] OR [Abstract: "supply chain attack"]]
```

**Obj. b) — Técnicas de detecção no contexto shift-left:**
```
[[Abstract: "docker image"] OR [Abstract: "container image"]] AND [[Abstract: "shift-left"] OR [Abstract: "DevSecOps"]] AND [[Abstract: "vulnerability detection"] OR [Abstract: "vulnerability scanning"] OR [Abstract: "static analysis"]]
```

**Obj. c) — Lacunas na literatura:**
```
[[Abstract: "docker"] OR [Abstract: "container image"]] AND [[Abstract: "vulnerability detection"] OR [Abstract: "vulnerability scanning"]] AND [[Abstract: "research gap"] OR [Abstract: "future work"] OR [Abstract: "limitation"]]
```

---

## 3. Google Scholar — Busca livre (links diretos)

> Filtro 2020–2026 via `as_ylo` e `as_yhi`. Verificar idioma manualmente.
> Scholar não suporta busca por campo — usar frases exatas e operadores simples.

**Busca geral:**
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%22docker+image%22+%28%22vulnerability+detection%22+OR+%22vulnerability+scanning%22+OR+%22static+analysis%22%29

**Obj. a) — Vetores de ataque SSC em Docker:**
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%22software+supply+chain%22+%28%22docker%22+OR+%22container+image%22%29+%28%22attack%22+OR+%22taxonomy%22%29

**Obj. b) — Técnicas de detecção no contexto shift-left:**
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%28%22shift-left+security%22+OR+%22DevSecOps%22%29+%22docker%22+%22vulnerability%22

**Obj. c) — Lacunas na literatura:**
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=%22docker+image%22+%22vulnerability%22+%28%22research+gap%22+OR+%22future+work%22+OR+%22open+issues%22%29

**Por título — alta precisão:**
https://scholar.google.com/scholar?as_ylo=2020&as_yhi=2026&q=intitle%3A%22docker%22+intitle%3A%22vulnerability%22+%28%22shift-left%22+OR+%22DevSecOps%22%29

---

## Filtro opcional — nomes de ferramentas

<!--
Só use se uma busca de Obj. b) ou geral retornar muitos resultados (>200) e for preciso reduzir ao subconjunto que nomeia ferramentas concretas.
Não é a busca primária: o foco é Shift-Left + detecção em Docker.
-->

**Lista de ferramentas recorrentes na literatura:** `Trivy`, `Grype`, `Clair`, `Anchore`, `Snyk`.

Para aplicar como filtro, acrescente à query original a cláusula:
```
AND ("Abstract":"Trivy" OR "Grype" OR "Clair" OR "Anchore" OR "Snyk")
```
(ajustando a sintaxe conforme a base.)
