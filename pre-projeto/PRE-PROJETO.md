# Pré-Projeto de TCC

**Título:** Critérios para a Escolha de Ferramentas de Escaneamento de Vulnerabilidades em Imagens Docker no Contexto de Shift-Left Security

---

## 1. Introdução / Problematização

O número de downloads de dependências nos principais repositórios de software aberto do mercado chegou na casa dos trilhões. Somados, Maven Central, PyPI, NPM e NuGet tiveram em 2025 9,8 trilhões de downloads de dependências (SONATYPE, 2026). Estas dependências servem de base para a construção de todo tipo de softwares, de aplicações comerciais feitas em empresas privadas, aplicações de infraestrutura do setor público até softwares abertos em grandes projetos open source.

Boa parte destes downloads é usada durante a criação de imagens Docker, que então serão publicadas em repositórios públicos de imagem Docker ou hospedados em nuvens públicas e privadas ao redor do mundo. Uma pesquisa anual feita pela CNCF apontou que 91% das organizações entrevistadas usavam containers em produção, mostrando um aumento de 14% dos dados de 2023 (CNCF, 2024). Estas imagens de container podem esconder em suas camadas dependências desatualizadas e vulneráveis a toda sorte de ataques.

Desde 2020, observa-se um aumento exponencial de ataques à cadeia de suprimentos de software (SSC), o que tem impulsionado novas ações governamentais e corporativas globais (WILLIAMS; HAMER; ZAHAN, 2024). Casos como do xz utils, event-stream e Log4j mostraram que boas práticas de segurança em código próprio não são suficientes para proteger aplicações em produção contra ataques vindos de grupos criminosos ou mesmo de estado-nações (LINS et al., 2024; ARVANITIS et al., 2022; HIESGEN et al., 2022).

Evitar que vulnerabilidades cheguem à produção é o objetivo do shift-left security, que propõe a integração de práticas de segurança desde as fases iniciais do ciclo de desenvolvimento de software (ANASURI, 2024; LADISA et al., 2023). Softwares como o Clair, Trivy e Grype são capazes de escanear imagens Docker em busca de vulnerabilidades conhecidas em suas diversas camadas (ANASURI, 2024; WILLIAMS et al., 2025) e podem ser integrados em esteiras de integração contínua (CI) para automatizar a detecção de vulnerabilidades.

Como organizações podem escolher de maneira consciente quais ferramentas usar em seu ciclo de desenvolvimento para mitigar os riscos de ataques à cadeia de suprimentos de software em imagens Docker usando shift-left e ferramentas automatizadas de escaneamento de imagens?

---

## 2. Justificativa

Com o rápido crescimento do ecossistema de criação de softwares de código aberto e comerciais e de suas bases de usuário, o mundo tem visto um incrível aumento na escala da criação e uso de cadeias de suprimento de software (SONATYPE, 2026), isto é dependências de software reutilizáveis que são usadas diariamente por equipes de engenharia de software do mundo todo.

Casos como o backdoor do xz utils (LINS et al., 2024) e do event-stream (ARVANITIS et al., 2022) demonstram que atores mal-intencionados podem passar anos se passando por contribuidores legítimos para, de forma ofuscada, adicionar backdoors de acesso remoto e roubo de criptomoedas. Há também o caso do Log4j (HIESGEN et al., 2022), com uma vulnerabilidade que possibilita acesso remoto a milhões de softwares pelo mundo através de um comportamento não intencional a partir de uma determinada versão.

Com o amplo uso de softwares de código aberto ao longo de todo o ciclo de vida de desenvolvimento de software (LADISA et al., 2023), garantir que nenhuma das dependências usadas esteja comprometida se tornou um trabalho árduo e custoso. Muitas vezes as equipes não têm mãos suficientes para tal demanda ou mesmo acabam negligenciando etapas críticas, como boas práticas de cibersegurança.

Em resposta a esse cenário, ferramentas de código aberto como Trivy, Grype e Clair buscam mitigar os riscos envolvendo cadeias de suprimento de software através de scanners automatizados de imagens Docker, sistemas de arquivos e listas de materiais de software (SBOM). Essas ferramentas podem atuar tanto no ciclo de desenvolvimento quanto em esteiras de entrega contínua (CD).

**Hipótese:** A integração de scanners de vulnerabilidades em pipelines de integração contínua permite detectar vulnerabilidades conhecidas em imagens de container Docker antes da publicação em produção. Para tanto, serão analisadas métricas como velocidade de execução, cobertura de verificação e taxa de falsos positivos e negativos dos scanners, além de literatura acadêmica publicada, a fim de propor critérios que orientem a escolha da ferramenta mais adequada para diferentes contextos organizacionais.

---

## 3. Objetivos

### Objetivo Geral

Propor critérios para a escolha de ferramentas de escaneamento de vulnerabilidades em imagens Docker no contexto de shift-left security.

### Objetivos Específicos

a) Analisar os principais vetores de ataques à cadeia de suprimentos de software em imagens Docker.

b) Comparar ferramentas de escaneamento de vulnerabilidades em imagens Docker quanto a critérios como cobertura de CVEs, integração com CI, desempenho, entre outros critérios.

c) Executar testes práticos para avaliação das ferramentas de escaneamento na detecção de falhas de segurança em pipelines de CI/CD.

d) Elaborar recomendações práticas para a adoção de ferramentas de escaneamento considerando diferentes perfis organizacionais.

---

## 4. Metodologia

Esta pesquisa é de natureza exploratória e qualitativa, com abordagem mista, combinando revisão bibliográfica e testes práticos com ferramentas de código aberto. Propõe-se a busca empírica de literatura em agregadores e periódicos de relevância na área, incluindo informes de mercado como Sonatype e CNCF. As bases de dados a serem consultadas são: IEEE Xplore, ACM Digital Library, arXiv, Google Scholar. Os termos de busca a serem utilizados são: "Software Supply Chain", "Container Security", "Vulnerability Scanning", "DevSecOps", "Shift Left Security", "Docker Security", "Container Vulnerability Scanning", "Trivy", "Grype" e "Clair".

Para artigos que tratem sobre definições e conceitos, serão utilizados trabalhos mais antigos para fundamentar o estudo. Os critérios de inclusão adotados são: artigos publicados entre 2021 e 2026, em inglês ou português, com foco em segurança de containers ou cadeia de suprimentos de software. Os critérios de exclusão são: artigos sem revisão por pares (exceto relatórios de mercado relevantes como Sonatype e CNCF) e trabalhos focados exclusivamente em segurança de runtime.

Os testes práticos serão realizados em um ambiente que simula um pipeline CI/CD na plataforma GitHub Actions, utilizando imagens Docker públicas com vulnerabilidades conhecidas disponíveis no Docker Hub e em repositórios públicos oficiais. As ferramentas avaliadas serão Trivy, Grype e Clair. As métricas de comparação incluirão cobertura de CVEs detectadas, taxa de falsos positivos/negativos, tempo de execução do escaneamento, facilidade de integração com CI/CD.

A análise bibliográfica e os testes práticos serão utilizados para a proposta de critérios de seleção de ferramentas de escaneamento de vulnerabilidades em imagens Docker no contexto de shift-left security, na análise dos vetores de ataque, na comparação de ferramentas e na elaboração de recomendações práticas para a adoção de ferramentas de escaneamento considerando diferentes perfis organizacionais.

---

## 5. Cronograma

<!-- TODO: preencher com as datas reais do AVA -->

| Etapas | Sem 1 | Sem 2 | Sem 3 | Sem 4 | Sem 5 |
|---|---|---|---|---|---|
| Escolha do tema e pesquisa bibliográfica | X | X | | | |
| **Etapa 1** — Elaboração do pré-projeto e postagem no AVA | X | X | | | |
| Devolutiva do tutor-orientador | | | X | | |
| **Etapa 2** — Redação do artigo: revisão bibliográfica e testes práticos | | X | X | X | |
| Postagem no AVA do artigo estruturado | | | | X | |
| Devolutiva do tutor-orientador | | | | X | |
| **Etapa 3** — Elaboração da versão final do artigo | | | | X | X |
| Postagem no AVA do artigo científico (TCC) finalizado | | | | | X |

---

## Referências

ANASURI, S. Secure Software Supply Chains in Open-Source Ecosystems. **International Journal of Emerging Trends in Computer Science and Information Technology**, v. 4, n. 1, p. 62-74, 2024. DOI: 10.63282/3050-9246.IJETCSIT-V4I1P108.

ARVANITIS, I. et al. A Systematic Analysis of the Event-Stream Incident. In: EUROPEAN WORKSHOP ON SYSTEMS SECURITY (EUROSEC), 15., 2022, Rennes. **Proceedings [...]**. New York: ACM, 2022.

BOLES, B. et al. Deciphering Discrepancies: A Comparative Analysis of Docker Image Security. In: IEEE INTERNATIONAL CONFERENCE ON SOURCE CODE ANALYSIS AND MANIPULATION (SCAM), 2024, Flagstaff. **Proceedings [...]**. IEEE, 2024. p. 254-259. DOI: 10.1109/SCAM63643.2024.00034.

BHARDWAJ, P. **Detecting Container vulnerabilities leveraging the CICD pipeline**. 2023. Dissertação (MSc em Cybersecurity) – National College of Ireland, Dublin, 2023.

CLOUD NATIVE COMPUTING FOUNDATION (CNCF). **Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change**. CNCF Annual Survey, 2024. Disponível em: https://www.cncf.io/reports/cncf-annual-survey-2024/. Acesso em: mar. 2026.

DOCKER. **Docker Documentation: Base images**. 2025. Disponível em: https://docs.docker.com/build/building/base-images/. Acesso em: mar. 2026.

GOKKAYA, B.; ANIELLO, L.; HALAK, B. Software supply chain: review of attacks, risk assessment strategies and security controls. **arXiv preprint** arXiv:2305.14157, 2023.

HIESGEN, R. et al. The Race to the Vulnerable: Measuring the Log4j Shell Incident. **arXiv preprint** arXiv:2205.02544, 2022.

JAIN, V. et al. Static Vulnerability Analysis of Docker Images. **IOP Conference Series: Materials Science and Engineering**, v. 1131, n. 1, p. 012018, 2021. DOI: 10.1088/1757-899X/1131/1/012018.

JAVED, O.; TOOR, S. Understanding the Quality of Container Security Vulnerability Detection Tools. In: ACM INTERNATIONAL CONFERENCE ON CLOUD AND BIG DATA COMPUTING (ICCBDC), 5., 2021, Liverpool. **Proceedings [...]**. ACM, 2021. DOI: 10.1145/3481646.3481661.

LADISA, P. et al. SoK: Taxonomy of Attacks on Open-Source Software Supply Chains. In: IEEE SYMPOSIUM ON SECURITY AND PRIVACY (SP), 2023. **Proceedings [...]**. IEEE, 2023.

LINS, S. et al. On the critical path to implant backdoors and the effectiveness of potential mitigation techniques: Early learnings from XZ. 2024.

MARTINEZ, J. A. **Software Supply Chain Attacks, a Threat to Global Cybersecurity: SolarWinds' Case Study**. 2021.

PARDO MINAYA, S. D. **Open source tools for container vulnerability analysis**. 2024. Dissertação (Mestrado em Engenharia Informática) – Universitat Politècnica de València, València, 2024.

SONATYPE. **2026 State of the Software Supply Chain**. 10. ed. Sonatype, 2026. Disponível em: https://www.sonatype.com/state-of-the-software-supply-chain. Acesso em: mar. 2026.

WILLIAMS, L.; HAMER, S.; ZAHAN, N. Can the Rising Tide of Software Supply Chain Attacks Raise All Software Engineering Boats? In: ACM CONFERENCE, 2024. **Proceedings [...]**. ACM, 2024.

WILLIAMS, L. et al. Research Directions in Software Supply Chain Security. **ACM Computing Surveys**, 2025.
