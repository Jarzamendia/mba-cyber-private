# Guia de Análise de Papers

Para adicionar um novo paper ao relatório, siga estes passos:
1. Adicione o arquivo PDF na pasta `papers/` com o nome no formato `autor_ano_descricao.pdf`.
2. Converta o PDF para Markdown: `docling --to md --image-export-mode placeholder --output papers/ papers/arquivo.pdf`
3. Identifique o título, autores e temas principais.
4. Adicione uma nova entrada ao final deste arquivo seguindo o formato abaixo.

---
Nome: Titulo do Trabalho
Autores: Sobrenome1, Nome1; Sobrenome2, Nome2
Ano: AAAA
Arquivo: autor_ano_descricao.pdf
Citação ABNT: SOBRENOME. Título. Revista/Evento, v. X, n. Y, p. XX-YY, AAAA.
Temas abordados: Tema 1, Tema 2, ...
Resumo: (máximo 3 parágrafos)

---

# Relatório de Papers Analisados

---
Nome: A Systematic Analysis of the Event-Stream Incident
Autores: Arvanitis, Iosif; Ntousakis, Grigoris; Ioannidis, Sotiris; Vasilakis, Nikos
Ano: 2022
Arquivo: arvanitis_2022_event-stream.pdf
Citação ABNT: ARVANITIS, I. et al. A Systematic Analysis of the Event-Stream Incident. In: EUROPEAN WORKSHOP ON SYSTEMS SECURITY (EUROSEC), 15., 2022, Rennes. Proceedings [...]. New York: ACM, 2022.
Temas abordados: Segurança NPM, Event-Stream Incident, Pacotes Maliciosos, Ecossistema JavaScript
Resumo:
O artigo realiza um estudo detalhado do incidente envolvendo o pacote `event-stream` no ecossistema NPM, um dos casos mais emblemáticos de comprometimento da cadeia de suprimentos de software via engenharia social e transferência de propriedade de pacotes.

Os autores reconstroem a trajetória do ataque, desde o momento em que o atacante ganhou a confiança do mantenedor original até a inclusão de código obfuscado destinado a roubar carteiras de criptomoedas em aplicações específicas.

A análise destaca as vulnerabilidades inerentes ao modelo de confiança de gerenciadores de dependências modernos e discute melhorias necessárias nas políticas de governança e monitoramento de pacotes para evitar incidentes semelhantes no futuro.

---
Nome: SoK: Taxonomy of Attacks on Open-Source Software Supply Chains
Autores: Ladisa, Piergiorgio; Plate, Henrik; Martinez, Matias; Barais, Olivier
Ano: 2023
Arquivo: ladisa_2023_taxonomy-attacks.pdf
Citação ABNT: LADISA, P. et al. SoK: Taxonomy of Attacks on Open-Source Software Supply Chains. In: IEEE SYMPOSIUM ON SECURITY AND PRIVACY (SP), 2023. Proceedings [...]. IEEE, 2023.
Temas abordados: Segurança de Software de Código Aberto (OSS), Ataques à Cadeia de Suprimentos, Taxonomia de Segurança, SDLC
Resumo:
Este artigo (SoK) propõe uma taxonomia abrangente de ataques a cadeias de suprimentos de software de código aberto (OSS), independente de linguagem de programação ou ecossistema. A taxonomia é estruturada como uma árvore de ataque, cobrindo 107 vetores únicos, vinculados a 94 incidentes do mundo real e mapeados para 33 salvaguardas mitigadoras.

O estudo define sistemas (VCS, sistemas de build, repositórios) e stakeholders (mantenedores, contribuidores, administradores) envolvidos, analisando a superfície de ataque técnica e social.

As principais contribuições incluem a sistematização de vetores de ataque desde a contribuição de código até a distribuição, e a avaliação qualitativa de salvaguardas em termos de utilidade e custo.

---
Nome: SoK: Taxonomia de Ataques a Cadeias de Suprimentos de Software Open-Source (Tese/Extensão)
Autores: Ladisa, Piergiorgio
Ano: 2023
Arquivo: ladisa_2023_thesis.pdf
Temas abordados: Taxonomia de Ataques, Segurança de Código Aberto, Gestão de Vulnerabilidades, Defesa em Profundidade
Resumo:
Este documento aprofunda o trabalho de taxonomia de Piergiorgio Ladisa, fornecendo uma base teórica robusta para entender como os ataques em cadeias de suprimentos de software evoluem. O foco recai sobre a fragilidade dos ecossistemas de código aberto e a facilidade com que atores maliciosos podem se infiltrar.

O estudo detalha os vetores de ataque em cada estágio do SDLC, propondo salvaguardas específicas e analisando a eficácia de cada uma em cenários reais.

---
Nome: Software supply chain: review of attacks, risk assessment strategies and security controls
Autores: Gokkaya, Betul; Aniello, Leonardo; Halak, Basel
Ano: 2023
Arquivo: gokkaya_2023_ssc-review.pdf
Citação ABNT: GOKKAYA, B.; ANIELLO, L.; HALAK, B. Software supply chain: review of attacks, risk assessment strategies and security controls. arXiv preprint arXiv:2305.14157, 2023.
Temas abordados: Systematic Literature Review, SSC Attacks, Risk Assessment, Security Controls, Open Source vs Third-Party
Resumo:
Este artigo apresenta uma revisão sistemática da literatura sobre a segurança da cadeia de suprimentos de software (SSC), focando não apenas na prevenção de ataques, mas também na avaliação de riscos e controles de segurança.

O estudo utiliza um conjunto de dados do Atlantic Council, abrangendo 161 incidentes entre 2010 e 2021, para mapear estratégias de ataque. O trabalho categoriza vetores de ataque em diferentes estágios do ciclo de vida do software e propõe um framework de avaliação de risco para vendedores de software.

A principal contribuição é a introdução de controles de segurança vinculados a incidentes reais, oferecendo recomendações práticas para organizações mitigarem ataques à SSC.

---
Nome: The Race to the Vulnerable: Measuring the Log4j Shell Incident
Autores: Hiesgen, Raphael; Nawrocki, Marcin; Schmidt, Thomas C.; Wählisch, Matthias
Ano: 2022
Arquivo: hiesgen_2022_log4j.pdf
Citação ABNT: HIESGEN, R. et al. The Race to the Vulnerable: Measuring the Log4j Shell Incident. arXiv preprint arXiv:2205.02544, 2022.
Temas abordados: Vulnerabilidade Log4j, Medição de Segurança na Internet, Exploração de Vulnerabilidades, Análise de Patching
Resumo:
Este artigo analisa empiricamente o impacto da vulnerabilidade Log4j Shell, focando na dinâmica entre atacantes e defensores após a divulgação pública do exploit.

A pesquisa utiliza dados coletados em "telescópios de rede" para observar quanto tempo levou para os primeiros ataques aparecerem e quão rápido as organizações aplicaram patches ou mitigações em larga escala.

Os resultados fornecem insights valiosos sobre a resiliência da infraestrutura da Internet e as dificuldades práticas de responder a vulnerabilidades críticas em bibliotecas profundamente aninhadas dentro das cadeias de suprimentos de software.

---
Nome: On the critical path to implant backdoors and the effectiveness of potential mitigation techniques: Early learnings from XZ
Autores: Lins, Samuel; et al.
Ano: 2024
Arquivo: lins_2024_xz-utils.pdf
Citação ABNT: LINS, S. et al. On the critical path to implant backdoors and the effectiveness of potential mitigation techniques: Early learnings from XZ. 2024.
Temas abordados: Incidente XZ Utils, Backdoors em Código Aberto, Ataques Críticos à Infraestrutura, Mitigação de Ataques
Resumo:
Este trabalho analisa as lições aprendidas com a tentativa de backdoor no utilitário XZ Utils, um ataque sofisticado que visava comprometer servidores SSH em todo o mundo através da manipulação de um mantenedor de software livre.

Os autores exploram os métodos técnicos utilizados para esconder o código malicioso dentro do sistema de build de forma que evitasse detecção manual e ferramentas de análise estática tradicionais.

O artigo serve como um alerta para a fragilidade da infraestrutura crítica global que depende de projetos mantidos por voluntários.

---
Nome: Software Supply Chain Attacks, a Threat to Global Cybersecurity: SolarWinds' Case Study
Autores: Martinez, Jose A.
Ano: 2021
Arquivo: martinez_2021_solarwinds.pdf
Citação ABNT: MARTINEZ, J. A. Software Supply Chain Attacks, a Threat to Global Cybersecurity: SolarWinds' Case Study. 2021.
Temas abordados: Software Supply Chain Attack, SolarWinds, Cybersecurity, C-SCRM, NIST SP 800-161, Zero Trust, SBOM
Resumo:
Este artigo utiliza o ataque à SolarWinds como estudo de caso para analisar as ameaças crescentes às cadeias de suprimentos de software global. A exploração do sistema Orion demonstrou como agentes maliciosos podem comprometer códigos-fonte legítimos e inserir backdoors.

O estudo enfatiza que a dependência de códigos de terceiros (85% a 97% do código atual) cria vulnerabilidades críticas no ciclo de desenvolvimento.

O trabalho propõe boas práticas mitigadoras baseadas em diretrizes da CISA e padrões como o NIST SP 800-161.

---
Nome: 2026 State of the Software Supply Chain
Autores: Sonatype (Brian Fox, CTO)
Ano: 2026
Arquivo: sonatype_2026_ssc-report.pdf
Citação ABNT: SONATYPE. 2026 State of the Software Supply Chain. 10. ed. Sonatype, 2026. Disponível em: https://www.sonatype.com/state-of-the-software-supply-chain. Acesso em: mar. 2026.
Temas abordados: Software Supply Chain Security, AI in Development, Malware, Vulnerability Management, Open Source Governance, Regulatory Compliance
Resumo:
Relatório da Sonatype (10a edição) com panorama da segurança da cadeia de suprimentos de software. Destaca que a escala do open source tornou-se um risco estrutural, com ecossistemas atuando como infraestruturas críticas.

Registra 9,8 trilhões de downloads em Maven Central, PyPI, npm e NuGet em 2025. Discute o impacto de regulamentações como o EU Cyber Resilience Act e o amadurecimento do uso de SBOMs.

Enfatiza a necessidade de transição para o modelo "Zero Trust" no desenvolvimento de software e a importância da automação.

---
Nome: Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change
Autores: CNCF (Cloud Native Computing Foundation)
Ano: 2024
Arquivo: cncf_2024_annual-survey.pdf
Citação ABNT: CLOUD NATIVE COMPUTING FOUNDATION (CNCF). Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change. CNCF Annual Survey, 2024. Disponível em: https://www.cncf.io/reports/cncf-annual-survey-2024/. Acesso em: mar. 2026.
Temas abordados: Cloud Native, Kubernetes, Containerização, Tendências de Mercado, Adoção de Projetos CNCF
Resumo:
Relatório anual da CNCF com visão abrangente do estado da adoção de tecnologias nativas em nuvem. 91% das organizações usam containers em produção (aumento de 14% em relação a 2023).

Destaca o crescimento contínuo de projetos como Kubernetes e a migração de workloads críticas para ambientes de container.

---
Nome: DevPhish: Exploring Social Engineering in Software Supply Chain Attacks on Developers
Autores: Siadati, Hossein; Jafarikhah, Sima; Sahin, Elif; Hernandez, Terrence; Tripp, Elijah; Khryashchev, Denis; Kharaz, Amin
Ano: 2024
Arquivo: siadati_2024_devphish.pdf
Citação ABNT: SIADATI, H. et al. DevPhish: Exploring Social Engineering in Software Supply Chain Attacks on Developers. In: IEEE CONFERENCE, 2024. Proceedings [...]. IEEE, 2024.
Temas abordados: Software Supply Chain Security, Social Engineering, DevPhish, Developer Targeting, Malware, Phishing
Resumo:
Introduz o termo "DevPhish" para descrever ataques de engenharia social direcionados a desenvolvedores de software no contexto da cadeia de suprimentos (SSC).

Categoriza as táticas em seis tipos principais: compromisso de conta, compromisso de dispositivo, Pull Requests maliciosos, "Watering holes" de dependências e trechos de código maliciosos, e infiltração no quadro de mantenedores.

---
Nome: What are Weak Links in the npm Supply Chain?
Autores: Zahan, Nusrat; Zimmermann, Thomas; Godefroid, Patrice; Murphy, Brendan; Maddila, Chandra; Williams, Laurie
Ano: 2022
Arquivo: zahan_2022_npm-weak-links.pdf
Citação ABNT: ZAHAN, N. et al. What are Weak Links in the npm Supply Chain? In: INTERNATIONAL CONFERENCE ON SOFTWARE ENGINEERING (ICSE), 44., 2022. Proceedings [...]. ACM, 2022.
Temas abordados: Software Supply Chain Security, npm, JavaScript packages, Weak link Signals, Package Metadata
Resumo:
Analisa metadados de 1,63 milhão de pacotes JavaScript do ecossistema npm para identificar "elos fracos" que aumentam o risco de ataques à cadeia de suprimentos.

Revela que mais de 2.800 endereços de e-mail de mantenedores estão associados a domínios expirados, permitindo sequestro de cerca de 8.500 pacotes. Valida achados com questionário a 470 desenvolvedores.

---
Nome: Can the Rising Tide of Software Supply Chain Attacks Raise All Software Engineering Boats?
Autores: Williams, Laurie; Hamer, Sivana; Zahan, Nusrat
Ano: 2024
Arquivo: williams_2024_rising-tide.pdf
Citação ABNT: WILLIAMS, L.; HAMER, S.; ZAHAN, N. Can the Rising Tide of Software Supply Chain Attacks Raise All Software Engineering Boats? In: ACM CONFERENCE, 2024. Proceedings [...]. ACM, 2024.
Temas abordados: Software Supply Chain Security, Government Regulations, Software Engineering Practices, US Executive Order 14028, EU Cyber Resilience Act (CRA), P-SSCRM Framework
Resumo:
Fornece visão geral das ações governamentais e corporativas globais em resposta ao aumento exponencial de ataques à SSC desde 2020. Descreve o framework P-SSCRM com 73 práticas de segurança recomendadas.

Conclui que o foco crescente em segurança da SSC atua como catalisador para melhorias sistêmicas na engenharia de software.

**NOTA:** Este paper foi citado como "CHEN et al., 2024" no pré-projeto, mas os autores reais são Williams, Hamer e Zahan. Verificar e corrigir a citação.

---
Nome: Research Directions in Software Supply Chain Security
Autores: Williams, Laurie; Benedetti, Giacomo; Hamer, Sivana; Paramitha, Ranindya; Rahman, Imranur
Ano: 2025
Arquivo: williams_2025_research-directions.pdf
Citação ABNT: WILLIAMS, L. et al. Research Directions in Software Supply Chain Security. ACM Computing Surveys, 2025.
Temas abordados: Software Supply Chain Security, Vulnerabilities, Build Infrastructure, Human Factors, LLMs, SBOM, SLSA, in-toto
Resumo:
Mapeia o estado atual e as direções futuras da pesquisa em segurança da cadeia de suprimentos de software. Identifica três vetores de ataque principais: dependências de código, infraestrutura de build e o fator humano.

Detalha tecnologias de proteção (SBOM, SLSA, in-toto, TUF) e destaca desafios como a baixa qualidade de SBOMs gerados automaticamente.

---
Nome: Establishing a Baseline of Software Supply Chain Security Task Adoption by Software Organizations
Autores: Williams, Laurie; Migues, Sammy
Ano: 2025
Arquivo: williams_2025_baseline-ssc.pdf
Citação ABNT: WILLIAMS, L.; MIGUES, S. Establishing a Baseline of Software Supply Chain Security Task Adoption by Software Organizations. In: INTERNATIONAL CONFERENCE ON SOFTWARE ENGINEERING (ICSE), 47., 2025. Proceedings [...]. ACM, 2025.
Temas abordados: Software Development Practice, Software Framework, Software Security, Security Outcome, Software Supply Chain Attack
Resumo:
Estudo com entrevistas de 61 profissionais em 9 organizações sobre adoção de tarefas de segurança para mitigar riscos da cadeia de suprimentos. Ataques SSC aumentaram exponencialmente desde 2020.

As tarefas mais adotadas são aquelas implementadas antes do foco em SSC (mais maduras). Tarefas que mitigam vetores novos (componentes e infraestrutura de build) estão em estágio inicial de adoção.

---
Nome: Secure Software Supply Chains in Open-Source Ecosystems
Autores: Anasuri, Sunil
Ano: 2024
Arquivo: anasuri_2024_secure-ssc-opensource.pdf
Citação ABNT: ANASURI, S. Secure Software Supply Chains in Open-Source Ecosystems. International Journal of Emerging Trends in Computer Science and Information Technology, v. 4, n. 1, p. 62-74, 2024. DOI: 10.63282/3050-9246.IJETCSIT-V4I1P108.
Temas abordados: Open-Source Security, Dependency Management, SBOM, DevSecOps, SLSA, Sigstore, Kubernetes
Resumo:
Examina o ambiente de ameaças nas cadeias de suprimentos de software de código aberto. Detalha vetores como dependency confusion, typosquatting e comprometimento de mantenedores.

Avalia defesas incluindo SBOMs, assinatura de artefatos e endurecimento de pipelines de CI/CD. Menciona shift-left security como orientação para integrar segurança nas fases iniciais do desenvolvimento.

**NOTA:** Este paper foi citado como "ANASURI; RUSUM, 2024" no pré-projeto, mas Rusum NÃO é co-autor. Corrigir para "ANASURI, 2024".

---
Nome: On the prevalence of software supply chain attacks: Empirical study and investigative framework
Autores: Alfalqi, et al.
Ano: 2023
Arquivo: alfalqi_2023_prevalence-ssc.pdf
Temas abordados: Estudo Empírico, Análise Estática Binária, Detecção de Comportamento Malicioso, Forensic Framework
Resumo:
Análise empírica de ataques proeminentes à SSC, propondo framework investigativo baseado em análise estática de fluxo de dados. Comportamentos de ataques como SolarWinds podem ser identificados em binários com 86-100% de precisão.

Técnicas de ataques recentes já estavam presentes em malwares de 13 a 21 anos atrás.

---
Nome: Uncovering Software Supply Chains Vulnerability: A Review of Attack Vectors, Stakeholders, and Regulatory Frameworks
Autores: Anjum, Nafisa; Sakib, Nazmus; Rodriguez-Cardenas, Juanjose; et al.
Ano: 2023
Arquivo: anjum_2023_uncovering-ssc.pdf
Temas abordados: Vetores de Ataque, Stakeholders, Frameworks Regulatórios, Ransomware
Resumo:
Revisão sistemática sobre vulnerabilidades das cadeias de suprimentos de software. Categoriza táticas de criminosos incluindo ransomware e identifica ferramentas regulatórias como o CHIPS Act.

---
Nome: Advanced Persistent Threats (APTs) based on Supply Chain Attacks
Autores: Tan, Zhuoran; Marnerides, Angelos K.; Anagnostopoulos, Christos; Parambath, Shameem Puthiya
Ano: 2024
Arquivo: tan_2024_apt-supply-chain.pdf
Citação ABNT: TAN, Z. et al. Advanced Persistent Threats based on Supply Chain Attacks. TechRxiv preprint, 2024. DOI: 10.36227/techrxiv.170594149.97651781/v1.
Temas abordados: APTs, Ataques Direcionados, Persistência, Espionagem Industrial
Resumo:
Explora a convergência entre ataques à cadeia de suprimentos e APTs. Demonstra como vulnerabilidades em fornecedores de confiança são utilizadas para ganhar acesso inicial a alvos de alto valor.

---
Nome: Proposta de Integração de Ferramentas de Segurança na Cadeia de Suprimentos
Arquivo: proposta_integracao.pdf
Temas abordados: Integração de Ferramentas, SBOM, Automatização de Segurança, Auditoria
Resumo:
Propõe framework para integrar ferramentas de análise de segurança (SAST, DAST, SCA) no pipeline de CI/CD. Foca na geração e consumo automatizado de SBOMs.

---
Nome: Deciphering Discrepancies: A Comparative Analysis of Docker Image Security
Autores: Boles, Brittany; O'Donoghue, Eric; Manzi Muneza, A. Redempta; Perkins, Garrett; Izurieta, Clemente; Reinhold, Ann Marie
Ano: 2024
Arquivo: boles_2024_docker-image-security.pdf
Citação ABNT: BOLES, B. et al. Deciphering Discrepancies: A Comparative Analysis of Docker Image Security. In: IEEE INTERNATIONAL CONFERENCE ON SOURCE CODE ANALYSIS AND MANIPULATION (SCAM), 2024, Flagstaff. Proceedings [...]. IEEE, 2024. p. 254-259. DOI: 10.1109/SCAM63643.2024.00034.
Temas abordados: Docker Image Security, Trivy, Grype, Static Analysis, Vulnerability Databases, Microservices
Resumo:
Análise comparativa de Trivy e Grype em 927 imagens Docker. Entre as 865 imagens com vulnerabilidades, as ferramentas divergiram tanto no número quanto nos IDs das vulnerabilidades reportadas. Grype encontrou mais vulnerabilidades que Trivy em 84.6% das imagens (603.259 vs 473.661).

As discrepâncias se devem às diferentes bases de dados usadas por cada ferramenta e à forma como interfaceiam com esses recursos externos. Trivy usa 9 bases adicionais de advisories de vendors. Estudo essencial para fundamentar critérios de seleção de ferramentas.

---
Nome: Understanding the Quality of Container Security Vulnerability Detection Tools
Autores: Javed, Omar; Toor, Salman
Ano: 2021
Arquivo: javed_2021_container-security-quality.pdf
Citação ABNT: JAVED, O.; TOOR, S. Understanding the Quality of Container Security Vulnerability Detection Tools. In: ACM INTERNATIONAL CONFERENCE ON CLOUD AND BIG DATA COMPUTING (ICCBDC), 5., 2021, Liverpool. Proceedings [...]. ACM, 2021. DOI: 10.1145/3481646.3481661.
Temas abordados: Container Security, Clair, Anchore, Microscanner, Vulnerability Detection Quality, Docker Images
Resumo:
Propõe métricas de cobertura e acurácia para ferramentas de escaneamento de containers. Avalia Clair, Anchore e Microscanner em 59 imagens Docker públicas de aplicações Java no DockerHub.

Conclui que as ferramentas existentes não detectam vulnerabilidades em pacotes de aplicação e que ~34% das vulnerabilidades são perdidas pela melhor ferramenta. Estudo fundamental para discutir limitações dos scanners.

---
Nome: Static Vulnerability Analysis of Docker Images
Autores: Jain, Vipin; Singh, Baldev; Khenwar, Medha; Sharma, Milind
Ano: 2021
Arquivo: jain_2021_static-vulnerability-docker.pdf
Citação ABNT: JAIN, V. et al. Static Vulnerability Analysis of Docker Images. IOP Conference Series: Materials Science and Engineering, v. 1131, n. 1, p. 012018, 2021. DOI: 10.1088/1757-899X/1131/1/012018.
Temas abordados: Docker Security, Static Analysis, Vulnerability Detection, Container Threats
Resumo:
Revisão dos mecanismos de segurança existentes do Docker, vulnerabilidades, ameaças e ferramentas de análise estática. Aborda ameaças em imagens Docker e riscos de containers maliciosos em hosts.

---
Nome: Open source tools for container vulnerability analysis
Autores: Pardo Minaya, Sergio David
Ano: 2024
Arquivo: pardo_2024_opensource-container-analysis.pdf
Citação ABNT: PARDO MINAYA, S. D. Open source tools for container vulnerability analysis. 2024. Dissertação (Mestrado em Engenharia Informática) – Universitat Politècnica de València, València, 2024.
Temas abordados: Container Security, Grype, Trivy, Clair, Snyk, Docker Scout, Vulnerability Scanning, Open Source Tools, CI/CD
Resumo:
Dissertação de mestrado que estuda tipos de vulnerabilidades em containers e compara ferramentas open source: Grype, Trivy, Snyk Containers e Clair. Descreve detalhadamente o funcionamento de cada ferramenta, incluindo como geram SBOMs e quais bases de dados utilizam.

Realiza testes comparativos e oferece análise de adequação de cada ferramenta conforme o tipo de vulnerabilidade. Fonte muito relevante para fundamentar a seção 3.4 e a parte experimental do TCC.

---
Nome: Detecting Container vulnerabilities leveraging the CICD pipeline
Autores: Bhardwaj, Preeti
Ano: 2023
Arquivo: bhardwaj_2023_container-vuln-cicd.pdf
Citação ABNT: BHARDWAJ, P. Detecting Container vulnerabilities leveraging the CICD pipeline. 2023. Dissertação (MSc em Cybersecurity) – National College of Ireland, Dublin, 2023.
Temas abordados: Container Security, Clair, Trivy, CI/CD Pipeline, Docker Vulnerability Scanning, Shift-Left
Resumo:
Dissertação de mestrado que avalia Clair e Trivy na detecção de vulnerabilidades em imagens Docker dentro de pipelines de CI/CD. Implementa pipeline automatizada para escaneamento shift-left.

Compara resultados de ambas as ferramentas e discute a viabilidade de integração automatizada. Diretamente alinhada com o tema e os objetivos do TCC.

---
