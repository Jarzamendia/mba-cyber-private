# Referencial Teórico - Roteiro

## Objetivo desta seção
O referencial teórico apresenta os conceitos, definições e trabalhos existentes que fundamentam a pesquisa. É onde você mostra ao leitor que domina o tema e que seu trabalho se apoia em uma base sólida. No pré-projeto, não precisa ser exaustivo — mas deve cobrir os pilares do trabalho e mostrar que você já tem leituras relevantes.

## Regras de escrita
- Não é um resumo de cada artigo lido — é uma **síntese organizada por tema**.
- Sempre que apresentar um conceito ou dado, cite a fonte (ABNT).
- Estabeleça conexões entre os autores: onde concordam, onde divergem, o que um complementa do outro.
- Linguagem impessoal e formal.
- No pré-projeto, 2 a 4 páginas costumam ser suficientes.

## Estrutura sugerida

O referencial deve cobrir os conceitos que sustentam seus objetivos. Baseado no seu objetivo geral ("Propor critérios para a escolha de ferramentas de escaneamento de vulnerabilidades em imagens Docker no contexto de shift-left security"), sugiro os seguintes eixos:

### 3.1 — Cadeia de suprimentos de software (Software Supply Chain)
- Definição de cadeia de suprimentos de software.
- Componentes: código-fonte, dependências, build systems, repositórios de artefatos, distribuição.
- Como o ecossistema open source ampliou a superfície de ataque.
- Taxonomia de ataques SSC (o framework do Ladisa et al., 2023 é uma boa referência aqui).
- **Conexão com seu trabalho**: este eixo fundamenta o objetivo específico 1 (analisar vetores de ataque).

### 3.2 — Segurança em imagens Docker
- O que é uma imagem Docker: camadas, imagem-base, Dockerfile.
- Como vulnerabilidades entram nas imagens: imagens-base desatualizadas, pacotes do SO, dependências da aplicação.
- Registros de imagens (Docker Hub, registros privados) e riscos associados (typosquatting, imagens maliciosas).
- CVEs e bases de dados de vulnerabilidades (NVD, OSV, etc.).
- **Conexão com seu trabalho**: contextualiza o objeto de estudo — imagens Docker como artefato da cadeia de suprimentos.

### 3.3 — Shift-left security e DevSecOps
- Definição de shift-left security: antecipar práticas de segurança para as fases iniciais do desenvolvimento.
- Relação com DevSecOps: segurança como responsabilidade compartilhada no ciclo de vida do software.
- Integração contínua (CI) como ponto de integração natural para verificações automatizadas de segurança.
- Benefícios: detecção precoce reduz custo de correção e exposição a riscos.
- **Conexão com seu trabalho**: fundamenta a abordagem proposta — escaneamento automatizado em CI.

### 3.4 — Ferramentas de escaneamento de vulnerabilidades em imagens Docker
- Panorama das ferramentas disponíveis: Trivy, Grype, Clair (e outras relevantes).
- Como funcionam: análise de SBOMs, comparação com bases de CVEs, análise de camadas.
- Critérios de comparação encontrados na literatura: cobertura de CVEs, taxa de falsos positivos, desempenho, facilidade de integração com CI, suporte a diferentes ecossistemas.
- **Conexão com seu trabalho**: fundamenta os objetivos específicos 2 e 3 (comparação e testes práticos).

### 3.5 — Trabalhos relacionados
- Apresente estudos que já compararam ferramentas de escaneamento ou abordaram segurança de imagens Docker.
- Mostre o que já foi feito e **onde há lacunas** que seu trabalho pretende preencher.
- Diferencie seu trabalho dos existentes: o que você faz de diferente ou complementar?
- **Conexão com seu trabalho**: justifica a relevância e originalidade da pesquisa.

## Fontes que você já tem
Você já leu diversos papers que podem alimentar esta seção. Organize-os por eixo:
- **SSC e ataques**: Ladisa et al. (2023), Chen et al. (2024), Arvanitis et al., Lins et al. (2024)
- **Segurança Docker/containers**: Hiesgen et al. (2022), Uncovering SSC Vulnerability
- **Ferramentas e comparações**: Williams et al. (2025), Anasuri & Rusum (2024)
- **Panorama geral**: Sonatype (2026), CNCF (2024)

## Dicas
- Comece pelos eixos que você tem mais material — não precisa escrever na ordem.
- Se um conceito já foi explicado na introdução, não repita — aprofunde.
- O referencial do pré-projeto será expandido no TCC final, então não se preocupe em ser exaustivo agora.
- Cada subseção deve ter no mínimo 2-3 referências.

---

## Referencial Teórico

### 3.1 — Cadeia de suprimentos de software (Software Supply Chain)

Cadeia de suprimentos de software (SSC, do inglês Software Supply Chain) pode ser definida como um conjunto de processos necessários para selecionar e obter componentes de software de terceiros, englobando também organizações e indivíduos envolvidos no processo de distribuição desses recursos (GOKKAYA; ANIELLO; HALAK, 2023). De forma mais abrangente, Ladisa et al. (2023) descreve SSC como um amplo ecossistema que envolve tanto o desenvolvimento quanto a construção e entrega de software, abrangendo ferramentas, pessoas, componentes e infraestruturas que contribuem para a criação de um produto final.

Esse ecossistema é frequentemente visualizado como uma extensa rede que acompanha o ciclo de vida de desenvolvimento de software. Segundo Williams et al. (2025), a cadeia de suprimentos engloba desde o código comercial e configurações até binários de código aberto, plugins, dependências de containers, além de ferramentas críticas como compiladores, analisadores de código e orquestradores de build.

Nos últimos anos, a escala e a ubiquidade do software de código aberto (OSS, do inglês Open Source Software) transformaram os ecossistemas de software em infraestruturas críticas globais, o que, consequentemente, gerou um risco estrutural (SONATYPE, 2026). Estima-se que aplicações modernas dependam de terceiros para 85% a 97% de sua base de código, criando uma superfície de ataque vasta e muitas vezes invisível (MARTINEZ, 2021).

A popularização da tecnologia de containers como o Docker introduziu camadas adicionais de abstração que aumentaram a complexidade da cadeia de suprimentos de software. Segundo Williams et al. (2025), a dependência de imagens de containers em pipelines de implantação contínua amplia a superfície de ataque, tornando o ecossistema suscetível a vetores como envenenamento de dependências (dependency poisoning) e injeção de código malicioso.

Esse cenário é agravado pela inclusão de imagens-base, pacotes de sistema e bibliotecas de aplicação aninhadas, cujas dependências transitivas o desenvolvedor frequentemente não controla nem audita diretamente, tornando a segurança desses artefatos um elo crítico na infraestrutura moderna (LADISA et al., 2023; SONATYPE, 2026).

### 3.2 — Segurança em imagens Docker

Imagens de containers são binários compostos por camadas imutáveis sobrepostas. Cada camada adiciona a anterior novos arquivos, bibliotecas e configurações, formando uma imagem completa e isolada que pode ser executada em qualquer ambiente compatível com a tecnologia de containers (HIESGEN et al., 2022). Comumente imagens-base são usadas para abstrair a complexidade de configurar aplicações e suas dependências. Ao invés de se preocupar em configurar um sistema operacional do zero, o desenvolvedor pode simplesmente utilizar uma imagem-base que já contenha o sistema operacional e as bibliotecas necessárias para a aplicação de uma determinada linguagem (DOCKER, 2025).

Nesse sentido, as imagens de containers devem ser tratadas como artefatos fundamentais da cadeia de suprimentos de software, de forma análoga às dependências tradicionais de uma aplicação, herdando e, em muitos casos, amplificando os riscos de segurança (WILLIAMS et al., 2025). Conforme destacado pelo relatório da Sonatype (2026), essas imagens representam um ponto cego crítico devido à complexidade inerente e à frequente falta de visibilidade sobre as centenas de componentes e dependências aninhadas que compõem suas camadas imutáveis. Essa opacidade torna a superfície de ataque em ambientes de containers maior e mais difícil de auditar diretamente pelos desenvolvedores do que o código-fonte proprietário (HIESGEN et al., 2022).

Para mitigar os riscos associados à opacidade das imagens de containers, são usadas ferramentas de escaneamento de vulnerabilidades como Trivy, Grype e Clair. Esses softwares realizam análises para identificar falhas de segurança conhecidas (CVEs) tanto em pacotes do sistema operacional quanto em bibliotecas de aplicação (WILLIAMS et al., 2025). No entanto, a literatura alerta que a precisão dos resultados pode variar devido ao uso de diferentes bases de dados de vulnerabilidades, o que pode gerar discrepâncias nos relatórios e exigir critérios claros de seleção (SONATYPE, 2026).

### 3.3 - Shift-Left Security e DevSecOps
O conceito de Shift-Left Security (SLS) propõe que devemos antecipar as práticas de segurança da informação para as fases iniciais do ciclo de desenvolvimento de software (ANASURI, 2024; LADISA et al., 2023), evitando que código, artefatos e dependências vulneráveis cheguem em produção, seja via imagem de container ou publicação direta de pacotes. No mesmo sentido, DevSecOps é uma cultura que visa integrar a segurança da informação em todas as fases do ciclo de vida de desenvolvimento de software, promovendo a colaboração entre desenvolvedores, equipes de segurança e operações (WILLIAMS et al., 2025).

Ambos os conceitos trabalham em conjunto para promover a automação de testes de segurança e a integração contínua de práticas de segurança no ciclo de desenvolvimento de software. Executar manualmente estas verificações e técnicas pode rapidamente se tornar um peso para equipes de desenvolvimento, que já possuem uma carga de trabalho considerável. Isso pode levar a falhas humanas, como pular etapas críticas ou não realizar verificações em todas as dependências, aumentando o risco de vulnerabilidades chegarem em produção (SONATYPE, 2026).

Vários trabalhos acadêmicos demonstram a importância de frameworks de confiança como o SLSA (Supply Chain Levels for Software Artifacts) para garantir a integridade e autenticidade do software (WILLIAMS; HAMER; ZAHAN, 2024; LADISA et al., 2023), materializando-se em pipelines automáticas com verificação de dependências, assinaturas digitais e registros de auditoria de forma completamente autônoma.


### 3.4 — Ferramentas de escaneamento de vulnerabilidades em imagens Docker

Para automatizar a verificação de vulnerabilidades em imagens de containers, diversas ferramentas de Software Composition Analysis (SCA) foram desenvolvidas. Essas ferramentas realizam análises estáticas das imagens, extraindo a lista de pacotes e dependências instaladas e comparando-as com bases de dados de vulnerabilidades conhecidas, como NVD, GHSA e OSV (BOLES et al., 2024). Entre as mais adotadas pela comunidade estão o Trivy, mantido pela Aqua Security, que se destaca pela abrangência de bases consultadas e pela capacidade de verificar também configurações incorretas; o Grype, desenvolvido pela Anchore, frequentemente utilizado em conjunto com o gerador de SBOM Syft; e o Clair, mantido pela Red Hat, projetado para atuar de forma persistente dentro de registros corporativos de imagens (PARDO, 2024).

Apesar de compartilharem o mesmo objetivo principal, essas ferramentas produzem resultados divergentes para uma mesma imagem. Em uma análise de 927 imagens Docker, Boles et al. (2024) evidenciaram que o Grype reportou mais vulnerabilidades que o Trivy em 84,6% dos casos, totalizando 603.259 achados contra 473.661. A causa dessa discrepância reside nas diferentes bases de dados utilizadas e na forma como cada ferramenta interpreta e mapeia os identificadores de vulnerabilidades. Esse problema não é exclusivo dessas duas ferramentas: Javed e Toor (2021) demonstraram que a melhor ferramenta avaliada em seu estudo ainda deixava de detectar aproximadamente 34% das vulnerabilidades existentes.

Essas divergências evidenciam que a escolha de uma ferramenta de escaneamento não é trivial e pode impactar diretamente a postura de segurança de uma organização. Sem critérios claros de avaliação, equipes de desenvolvimento correm o risco de adotar ferramentas que geram uma falsa sensação de segurança ou que sobrecarregam o fluxo de trabalho com falsos positivos (SONATYPE, 2026). Esse cenário reforça a necessidade de estabelecer critérios objetivos para a seleção consciente dessas ferramentas — propósito central deste trabalho.

### 3.5 — Trabalhos relacionados

Diversos estudos abordaram a análise de vulnerabilidades em imagens Docker e a comparação de ferramentas de escaneamento. Javed e Toor (2021) foram pioneiros ao propor métricas de cobertura e acurácia para avaliar a qualidade dessas ferramentas, analisando 59 imagens Docker de aplicações Java com Clair, Anchore e Microscanner. Seus resultados revelaram que nenhuma das ferramentas avaliadas detectava vulnerabilidades em pacotes de aplicação, limitando-se a pacotes do sistema operacional. Bhardwaj (2023) avançou na integração com pipelines CI/CD, implementando um ambiente automatizado com Clair e Trivy para escanear imagens vulneráveis antes da implantação, embora seu escopo tenha se limitado a apenas duas imagens Docker.

Trabalhos mais recentes ampliaram a escala e o escopo dessas comparações. Boles et al. (2024) conduziram uma análise sistemática de 927 imagens comparando Trivy e Grype, revelando discrepâncias significativas nos resultados e investigando suas causas nas bases de dados subjacentes. Em paralelo, Pardo (2024) realizou uma comparação abrangente de quatro ferramentas — Grype, Trivy, Clair e Snyk — descrevendo suas arquiteturas e estratégias de detecção. Jain et al. (2021) contribuíram com uma revisão dos mecanismos de segurança existentes no Docker e das ferramentas disponíveis para análise estática.

Embora esses estudos tenham contribuído significativamente para a compreensão das capacidades e limitações das ferramentas de escaneamento, nenhum deles propõe critérios objetivos que orientem organizações na escolha consciente de qual ferramenta adotar em seu contexto específico. A maioria foca na comparação de resultados quantitativos sem considerar fatores como facilidade de integração com pipelines existentes, maturidade da comunidade ou adequação ao perfil de risco da organização. Este trabalho busca preencher essa lacuna ao propor critérios práticos de seleção no contexto de shift-left security.

