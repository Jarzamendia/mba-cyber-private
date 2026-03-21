# Metodologia - Roteiro

## Objetivo desta seção
A metodologia descreve **como** você vai realizar a pesquisa. Deve deixar claro o tipo de pesquisa, as fontes utilizadas, os critérios de seleção da literatura e, no seu caso, como serão conduzidos os testes práticos com as ferramentas.

## Regras de escrita
- Linguagem impessoal e formal.
- Seja específico: não basta dizer "foi feita uma pesquisa bibliográfica" — diga **onde**, **com quais termos**, **quais critérios de inclusão/exclusão**.
- Conecte cada etapa metodológica a um objetivo específico.
- 2 a 4 parágrafos são suficientes para o pré-projeto.

## Estrutura sugerida (3 parágrafos)

### Parágrafo 1 — Tipo de pesquisa e revisão bibliográfica
- Classificação: pesquisa exploratória de natureza qualitativa, com abordagem mista (revisão bibliográfica + testes práticos).
- Bases de pesquisa utilizadas: IEEE Xplore, ACM Digital Library, arXiv, Google Scholar.
- Termos de busca: "software supply chain security", "Docker image vulnerability scanning", "container security tools", "shift-left security", "Trivy", "Grype", "Clair".
- Critérios de inclusão: artigos publicados entre 2020 e 2026, em inglês ou português, com foco em segurança de containers ou cadeia de suprimentos de software.
- Critérios de exclusão: artigos sem revisão por pares (exceto relatórios de mercado relevantes como Sonatype e CNCF), trabalhos focados exclusivamente em segurança de runtime (não estática).
- **Conexão**: fundamenta os objetivos específicos 1 (vetores de ataque) e 2 (comparação de ferramentas).

### Parágrafo 2 — Testes práticos (experimental)
- Descreva o ambiente de teste: pipeline CI/CD (ex: GitHub Actions ou GitLab CI).
- Ferramentas avaliadas: Trivy, Grype e Clair.
- Conjunto de imagens de teste: selecionar imagens Docker públicas com vulnerabilidades conhecidas (ex: imagens oficiais antigas, imagens do projeto Vulhub ou similares).
- Métricas de comparação:
  - Cobertura de CVEs detectadas
  - Taxa de falsos positivos / falsos negativos
  - Tempo de execução do escaneamento
  - Facilidade de integração com CI/CD
  - Bases de dados de vulnerabilidades utilizadas
- **Conexão**: fundamenta o objetivo específico 3 (testes práticos).

### Parágrafo 3 — Síntese e proposição de critérios
- A partir da revisão bibliográfica e dos resultados dos testes práticos, serão elaborados critérios de seleção.
- Os critérios considerarão tanto os dados quantitativos (métricas dos testes) quanto fatores qualitativos encontrados na literatura (maturidade, comunidade, suporte).
- **Conexão**: fundamenta o objetivo específico 4 (recomendações práticas).

## Dicas
- Lembre-se de que a metodologia do pré-projeto é uma **proposta** — você ainda não executou. Use verbos no futuro ou no infinitivo ("serão analisadas", "pretende-se comparar").
- Os testes práticos diferenciam seu trabalho de uma revisão puramente bibliográfica.
- A tabela do cronograma (seção 6) deve refletir as etapas descritas aqui.

---

> Escreva seu rascunho abaixo:


