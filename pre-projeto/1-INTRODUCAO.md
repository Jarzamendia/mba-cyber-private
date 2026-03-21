# Introdução / Problematização - Rascunho

## Objetivo desta seção
A introdução do pré-projeto deve apresentar o tema, contextualizar o leitor e conduzi-lo até o **problema de pesquisa**. É o "funil": começa amplo e vai afunilando até a pergunta que o trabalho pretende responder.

## Estrutura sugerida

### Parágrafo 1 — Contextualização ampla
- Apresente o cenário macro: a transformação digital e a adoção massiva de containers/Docker em ambientes de desenvolvimento e produção.
- Traga dados sobre a adoção de containers na indústria (relatórios da CNCF, Datadog, Gartner, etc.).
- Objetivo: situar o leitor no universo em que o trabalho se insere.

### Parágrafo 2 — O papel das cadeias de suprimento de software
- Explique o que são cadeias de suprimento de software e como imagens Docker dependem fortemente de componentes de terceiros (imagem base, pacotes do SO, bibliotecas da aplicação).
- Mostre que uma imagem Docker é um "acúmulo de dependências" em camadas — e que qualquer camada pode conter vulnerabilidades.
- Diferencie este trabalho da justificativa: lá você argumentou *por que* é importante; aqui você explica *o que é* o problema.

### Parágrafo 3 — O cenário de ameaças (supply chain attacks)
- Apresente brevemente os ataques de cadeia de suprimento como um vetor crescente (pode referenciar os mesmos casos da justificativa: xz utils, event-stream, Log4j, mas sem repetir o texto).
- Foque em como esses ataques se manifestam no contexto de imagens Docker especificamente.

### Parágrafo 4 — Abordagem shift-left e automação
- Introduza o conceito de shift-left security: mover verificações de segurança para etapas mais iniciais do ciclo de desenvolvimento.
- Mencione que ferramentas de scanning automatizado (Trivy, Grype, Clair) tornam essa abordagem viável.
- Explique brevemente o que é integração contínua (CI) e como os scanners podem ser integrados nesse fluxo.

### Parágrafo 5 — Problema de pesquisa
- Afunile para o problema específico que o trabalho pretende responder.
- Formule a pergunta de pesquisa:
  > "Como uma organização pode precaver-se contra ataques de cadeia de fornecimento de software em imagens Docker através do uso de práticas de shift-left e automatização de detecção de vulnerabilidades no ciclo de desenvolvimento?"
- Esse parágrafo deve ser curto e direto — é o fechamento do funil.

## Dicas de escrita
- Não repita o texto da justificativa — a introdução contextualiza, a justificativa argumenta *por que* é relevante.
- Linguagem impessoal e formal.
- Cite fontes (ABNT) sempre que trouxer dados ou afirmações.
- A introdução do pré-projeto costuma ter de 4 a 6 parágrafos (1 a 2 páginas).
- Cada parágrafo deve fluir para o próximo — o leitor deve sentir que está sendo conduzido até o problema.

---

## Introdução

O número de downloads de dependências nos principais repositórios de dependência de software aberto do mercado chegou na casa dos trilhões. Somados, Maven Central, PyPI, NPM e NuGet tiveram em 2025 9,8 trilhões de downloads de dependências (SONATYPE, 2026). Estas dependências servem de base para a construção de todo tipo de softwares, de aplicações comerciais feitas em empresas privadas, aplicações de infraestrutura do setor público até softwares abertos em grandes projetos open source.

Boa parte destes downloads é usada durante a criação de imagens Docker, que então serão publicadas em repositórios públicos de imagem Docker ou hospedados em nuvens públicas e privadas ao redor do mundo. Uma pesquisa anual feita pela CNCF apontou que 91% das organizações entrevistadas usavam containers em produção, mostrando um aumento de 14% dos dados de 2023 (CNCF, 2024). Estas imagens de container podem esconder em suas camadas dependências desatualizadas e vulneráveis a toda sorte de ataques.

Desde 2020, observa-se um aumento exponencial de ataques à cadeia de suprimentos de software (SSC), o que tem impulsionado novas ações governamentais e corporativas globais (WILLIAMS; HAMER; ZAHAN, 2024). Casos como do xz utils, event-stream e Log4j mostraram que boas práticas de segurança em código próprio não são suficientes para proteger aplicações em produção contra ataques vindos de grupos criminosos ou mesmo de estado-nações (LINS et al., 2024; ARVANITIS et al., 2022; HIESGEN et al., 2022).

Evitar que vulnerabilidades cheguem à produção é o objetivo do shift-left security, que propõe a integração de práticas de segurança desde as fases iniciais do ciclo de desenvolvimento de software (ANASURI, 2024; LADISA et al., 2023). Softwares como o Clair, Trivy e Grype são capazes de escanear imagens Docker em busca de vulnerabilidades conhecidas em suas camadas ocultas (ANASURI, 2024; WILLIAMS et al., 2025) e podem ser integrados em esteiras de integração contínua (CI) para automatizar a detecção de vulnerabilidades.

Como organizações podem escolher de maneira consciente quais ferramentas usar em seu ciclo de desenvolvimento para mitigar os riscos de ataques à cadeia de suprimentos de software em imagens Docker usando shift-left e ferramentas automatizadas de escaneamento de imagens? 

