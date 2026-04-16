# Planilha de Controle — Buscas Bibliográficas

<!--
Como usar:
- Uma linha por execução de query. Atualizar após cada rodada.
- "Pós título": restaram após descartar títulos claramente fora de escopo.
- "Pós resumo": restaram após leitura dos abstracts.
- "Pós integral": aprovados após leitura do texto completo → vão para papers/.
- Ao aprovar um paper, adicionar no 6-REFERENCIAS.md e baixar PDF em papers/.
-->

## Filtros globais aplicados a todas as buscas

- **Período:** 2020–2026 (exceções clássicas admitidas com justificativa)
- **Idiomas:** inglês ou português
- **Tipo:** artigos revisados por pares, dissertações, teses, relatórios técnicos de instituições reconhecidas
- **Exclusões:** foco exclusivo em runtime de containers (sem análise estática); duplicatas entre bases

---

## Registro de execuções

| # | Data | Base | Obj. | Query (resumo) | Total | Pós título | Pós resumo | Pós integral | Arquivo de saída |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-04-16 | arXiv | Geral | A AND B (ampla) | 31 | 10 | 8 | — | `arxiv-2026-04-16-ampla-AB.md` |
| 2 | 2026-04-16 | arXiv | Obj.2 | E AND comparação | 15 | 1 | 1 | — | `arxiv-2026-04-16-ferramentas-obj2.md` |
| 3 | | arXiv | Obj.1 | A AND D | | | | | |
| 4 | | arXiv | Obj.3 | A AND B AND C | | | | | |
| 5 | | IEEE | Geral | A AND B (ampla) | | | | | |
| 6 | | IEEE | Obj.1 | A AND D | | | | | |
| 7 | | IEEE | Obj.2 | E AND comparação | | | | | |
| 8 | | IEEE | Obj.3 | A AND B AND C | | | | | |
| 9 | | ACM | Geral | A AND B (ampla) | | | | | |
| 10 | | ACM | Obj.1 | A AND D | | | | | |
| 11 | | ACM | Obj.2 | E AND comparação | | | | | |
| 12 | | ACM | Obj.3 | A AND B AND C | | | | | |
| 13 | | Scholar | Geral | A AND B (ampla) | | | | | |
| 14 | | Scholar | Obj.2 | E AND comparação | | | | | |

---

## Deduplicação entre bases

<!-- Preencher ao consolidar os resultados. Um paper encontrado em múltiplas bases conta apenas uma vez no corpus final. -->

| Paper (autor, ano, arxiv_id/DOI) | arXiv | IEEE | ACM | Scholar | Scopus | Incluído? |
|---|---|---|---|---|---|---|
| Javed, Toor 2021 (2101.03844) | ✅ | | | | | ✅ já tínhamos |
| Churakova et al. 2025 (2503.14388) | ✅ | | | | | pendente leitura |
| Haque, Babar 2021 (2112.12597) | ✅ | | | | | pendente leitura |
| Wist et al. 2020 (2006.02932) | ✅ | | | | | pendente leitura |

---

## Candidatos ordenados por prioridade de leitura

<!-- Ranking após todas as buscas concluídas. Por enquanto, só arXiv. -->

### Alta prioridade (⭐⭐⭐)
1. **Churakova, Ekstedt, Schmid (2025)** — Vexed by VEX tools: consistência entre scanners com SBOM/VEX. Obj. 2.
2. **Haque, Babar (2021)** — Base-Image Vulnerabilities exploitability. Obj. 1.
3. **Wist, Helsem, Gligoroski (2020)** — Análise de 2500 imagens Docker Hub. Obj. 1/2.

### Média (⭐⭐)
4. **Mills, White, Legg (2025)** — gh0stEdit layer-based attack. Obj. 1.
5. **Wong et al. (2021)** — Threat Modeling Containers Survey. Obj. 1.
6. **Mullinix et al. (2020)** — Security measures Docker. Obj. 1/3.

### Baixa (⭐)
7. **Kaur et al. (2020)** — Vulnerabilities scientific container images. Contexto específico.

### A avaliar
- **Bufalino et al. (2025)** — ORCA obscure containers.
- **Tan et al. (2026)** — LLM pipelines (provavelmente fora de escopo).
