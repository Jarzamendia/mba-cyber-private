# Introdução / Problematização - Rascunho

<!--
CONFERIR / MODIFICAR antes de entregar:
- Título global do pré-projeto: "Docker Imagens" (literal do orientador) vs "Imagens Docker" (ABNT natural). Confirmar na próxima devolutiva.
- §1: decidir se mantém dois blocos de dados (Sonatype + CNCF) no mesmo parágrafo ou divide.
- §4: conferir se a lacuna ("falsa sensação de segurança") está suficientemente clara.
- §5: enunciado do problema de pesquisa está idêntico ao CLAUDE.md — confirmar com orientador.
- Todas as citações já passaram pelo relatório de verificação (arquivo antigo removido — trechos originais ficam em 6-REFERENCIAS.md).
-->

<!-- 
João, será obrigatório que sua introdução comtemple os seguintes pontos: 
1 - Apresente uma visão geral sobre o tema do trabalho.
2 - Explique a relevância do assunto no contexto acadêmico, social ou tecnológico.
3 - Utilize dados, citações ou referências para fortalecer a importância.
4 - Destaque uma lacuna ou desafio existente no tema.
5 - Explique por que essa lacuna precisa ser abordada.
6 - Seja específico ao descrever o problema que o trabalho pretende investigar.
Caso voce sinta dificuldade, sugiro a leitura de artigos científicos de revisão de literatura ou pertinentes ao assunto objeto de pesquisa para melhorar sua compreensão e abordagem do texto científico, combinado?
-->


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

O número de downloads de dependências nos principais repositórios de software aberto alcançou a casa dos trilhões: somados, Maven Central, PyPI, NPM e NuGet registraram, em 2025, 9,8 trilhões de downloads de dependências (SONATYPE, 2026). Esses componentes servem de base para a construção de aplicações comerciais, sistemas de infraestrutura do setor público e projetos de código aberto em larga escala, constituindo a chamada cadeia de suprimentos de software. Em conjunto com isto, a adoção de containers tornou-se majoritária na indústria: uma pesquisa anual da Cloud Native Computing Foundation apontou que 91% das organizações entrevistadas utilizam containers em produção, representando um aumento de 14% em relação a 2023 (CNCF, 2024).

Boa parte das dependências consumidas pela indústria é incorporada a imagens Docker, publicadas em repositórios públicos ou hospedadas em nuvens públicas e privadas. Cada imagem é, em essência, um acúmulo de camadas que pode conter bibliotecas desatualizadas e pacotes de sistema com vulnerabilidades conhecidas, herdando os riscos de toda a sua árvore de dependências (LADISA et al., 2023). Esse cenário torna as imagens Docker um ponto particularmente sensível para os ataques à cadeia de suprimentos de software. A detecção de vulnerabilidades em imagens Docker ainda em estagio de desenvolvimento é o que o Shift-Left Security busca resolver.

Desde 2020, observa-se um crescimento exponencial de ataques de cadeia de suprimentos de software, o que tem impulsionado novas ações governamentais e corporativas em escala global (WILLIAMS; HAMER; ZAHAN, 2024). Casos como o backdoor do xz utils, o comprometimento do event-stream e a vulnerabilidade do Log4j demonstraram que boas práticas de segurança no código próprio não bastam para proteger aplicações em produção contra ameaças originadas em componentes de terceiros (LINS et al., 2024; ARVANITIS et al., 2022; HIESGEN et al., 2022). Em resposta, consolidou-se a abordagem de *shift-left security*, que propõe antecipar as verificações de segurança para etapas iniciais do ciclo de desenvolvimento (ANASURI, 2024).

Apesar da disponibilidade de múltiplas ferramentas maduras, estudos revelam **divergências significativas entre elas**: comparações sistemáticas indicam discrepâncias superiores a 80% na detecção de vulnerabilidades entre scanners distintos aplicados às mesmas imagens (BOLES et al., 2024), além de taxas expressivas de falsos negativos (JAVED; TOOR, 2021). Tais divergências apresentam uma lacuna que este trabalho pretende abordar: a literatura ainda não consolida, de forma sistemática, critérios que orientem a escolha da ferramenta mais adequada a diferentes contextos organizacionais. Essa lacuna precisa ser abordada porque a escolha equivocada de um scanner pode gerar falsa sensação de segurança, permitindo que vulnerabilidades críticas avancem até a produção apesar de o pipeline estar formalmente protegido.

Com isto, o problema que este trabalho pretende investigar pode ser descrito da seguinte maneira: "O que a literatura científica publicada entre 2020 e 2026 evidencia sobre a detecção de vulnerabilidades em imagens Docker no contexto de shift-left security?"
