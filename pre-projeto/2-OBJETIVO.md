# Objetivos - Roteiro

## Objetivo desta seção
A seção de objetivos traduz o problema de pesquisa em metas concretas. O objetivo geral responde diretamente à pergunta de pesquisa; os objetivos específicos são os passos necessários para alcançá-lo.

## Regras de escrita
- Cada objetivo começa com um **verbo no infinitivo** (analisar, comparar, identificar, propor, avaliar, mapear...).
- Objetivos devem ser **mensuráveis** — ao final do trabalho, deve ser possível verificar se foram cumpridos ou não.
- Não confunda objetivo com justificativa: objetivo é *o que* você vai fazer, não *por que* é importante.
- Linguagem impessoal e formal.
- Normalmente 1 objetivo geral + 3 a 5 específicos.

## Estrutura sugerida

### Objetivo Geral
- Deve ser **um único parágrafo curto** (1 a 3 linhas).
- Responde diretamente à pergunta de pesquisa formulada na introdução.
- Sua pergunta foi: *"Como organizações podem escolher de maneira consciente quais ferramentas usar em seu ciclo de desenvolvimento para mitigar os riscos de ataques à cadeia de suprimentos de software em imagens Docker usando shift-left e ferramentas automatizadas de escaneamento de imagens?"*
- O objetivo geral deve transformar essa pergunta em uma meta. Exemplo de estrutura (não copie, reformule com suas palavras):
  > "Analisar/Avaliar/Propor [o quê] para [qual finalidade] no contexto de [escopo]."

### Objetivos Específicos
- São as etapas que, somadas, permitem atingir o objetivo geral.
- Cada um deve ser independente e verificável.
- Pense na sequência lógica do seu trabalho — os específicos geralmente espelham os capítulos ou seções do TCC.

Sugestões de eixos para seus objetivos específicos (escolha e adapte):

1. **Mapear/Identificar** — Levantar os principais vetores de ataque à cadeia de suprimentos de software no contexto de imagens Docker (fundamentação teórica).
2. **Comparar/Analisar** — Comparar ferramentas de escaneamento de vulnerabilidades em imagens Docker (Trivy, Grype, Clair) quanto a critérios como cobertura de CVEs, integração com CI, desempenho, etc.
3. **Demonstrar/Implementar** — Implementar um pipeline de CI com escaneamento automatizado de imagens Docker usando as ferramentas selecionadas (parte prática/experimental).
4. **Avaliar/Discutir** — Avaliar a eficácia das ferramentas na detecção de vulnerabilidades conhecidas em um conjunto de imagens Docker de teste.
5. **Propor/Recomendar** — Propor critérios ou diretrizes para a escolha de ferramentas de escaneamento conforme o contexto organizacional.

## Dicas
- Os objetivos específicos devem estar **alinhados com a metodologia** — cada específico geralmente corresponde a uma etapa metodológica.
- Não exagere na quantidade: 3 a 4 objetivos específicos bem definidos são melhores que 6 vagos.
- Revise os objetivos após escrever a metodologia para garantir coerência entre as seções.

---

## Objetivos

### Objetivo Geral

Analisar, por meio de revisão bibliográfica, o estado da arte sobre detecção de vulnerabilidades em imagens Docker no contexto de shift-left security.

### Objetivos Específicos

a) Analisar, a partir da literatura, os principais vetores de ataques à cadeia de suprimentos de software em imagens Docker.
b) Comparar, com base em estudos empíricos publicados, as ferramentas de escaneamento de vulnerabilidades em imagens Docker (como Trivy, Grype e Clair) quanto a cobertura de CVEs, integração com CI/CD, desempenho e demais critérios reportados.
c) Sintetizar recomendações para a adoção de ferramentas de escaneamento considerando diferentes perfis organizacionais, com base nas evidências encontradas na literatura revisada.