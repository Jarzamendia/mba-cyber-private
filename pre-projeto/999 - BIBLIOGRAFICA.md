# Referências Bibliográficas

> Formato ABNT. Manter em ordem alfabética pelo sobrenome do primeiro autor.
> Ao adicionar novas referências, incluir também o trecho original (em inglês) que fundamenta a citação no pré-projeto, para rápida conferência.

---

ANASURI, S. Secure Software Supply Chains in Open-Source Ecosystems. **International Journal of Emerging Trends in Computer Science and Information Technology**, v. 4, n. 1, p. 62-74, 2024. DOI: 10.63282/3050-9246.IJETCSIT-V4I1P108.
- **Arquivo**: `papers/anasuri_2024_secure-ssc-opensource.pdf`
- **Citado em**: Introdução (shift-left, ferramentas de escaneamento)
- **Trecho original (shift-left)**: "To address the supply chain issue, a shift-left security orientation is needed, which involves the implementation of security practices at the beginning stages of software development and continuing to integrate security through the software life cycle."

---

BOLES, B. et al. Deciphering Discrepancies: A Comparative Analysis of Docker Image Security. In: IEEE INTERNATIONAL CONFERENCE ON SOURCE CODE ANALYSIS AND MANIPULATION (SCAM), 2024, Flagstaff. **Proceedings [...]**. IEEE, 2024. p. 254-259. DOI: 10.1109/SCAM63643.2024.00034.
- **Arquivo**: `papers/boles_2024_docker-image-security.pdf`
- **Citado em**: (disponível para Referencial Teórico 3.4 — ferramentas de escaneamento)
- **Trecho original (discrepância Trivy vs Grype)**: "Among the 865 images found to have vulnerabilities, Trivy and Grype disagreed on both the number of vulnerabilities and the vulnerability IDs found therein."
- **Trecho original (Grype encontra mais)**: "Grype found more vulnerabilities than Trivy in 84.6% of images analyzed. Trivy found 473,661 vulnerabilities total while Grype found 603,259."
- **Trecho original (bases de dados)**: "Since both tools interface with external vulnerability databases, some discrepancies can be attributed to how the tools interface with these external resources. The external vulnerability databases partially overlap and frequently contradict one another."

---

ARVANITIS, I. et al. A Systematic Analysis of the Event-Stream Incident. In: EUROPEAN WORKSHOP ON SYSTEMS SECURITY (EUROSEC), 15., 2022, Rennes. **Proceedings [...]**. New York: ACM, 2022.
- **Arquivo**: `papers/arvanitis_2022_event-stream.pdf`
- **Citado em**: Justificativa (event-stream), Introdução (ataques SSC)
- **Trecho original**: "The attack was highly targeted, activating only when the package was part of a specific dependency tree and operating on the Bitcoin mainnet."

---

BHARDWAJ, P. **Detecting Container vulnerabilities leveraging the CICD pipeline**. 2023. Dissertação (MSc em Cybersecurity) – National College of Ireland, Dublin, 2023.
- **Arquivo**: `papers/bhardwaj_2023_container-vuln-cicd.pdf`
- **Citado em**: (disponível para Referencial Teórico 3.4 — Clair e Trivy em CI/CD)
- **Trecho original**: "This paper contributed in successfully scanning two different Vulnerable docker images by Clair and Trivy."

---

CLOUD NATIVE COMPUTING FOUNDATION (CNCF). **Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change**. CNCF Annual Survey, 2024. Disponível em: https://www.cncf.io/reports/cncf-annual-survey-2024/. Acesso em: mar. 2026.
- **Arquivo**: `papers/cncf_2024_annual-survey.pdf`
- **Citado em**: Introdução (91% containers em produção)
- **Trecho original**: "91% of organizations are using containers in production (used for most or for a few apps) compared to just 80% in 2023, which is a 14% growth rate year over year."

---

DOCKER. **Docker Documentation: Base images**. 2025. Disponível em: https://docs.docker.com/build/building/base-images/. Acesso em: mar. 2026.
- **Citado em**: Referencial Teórico 3.2 (conceito de imagens-base)

---

GOKKAYA, B.; ANIELLO, L.; HALAK, B. Software supply chain: review of attacks, risk assessment strategies and security controls. **arXiv preprint** arXiv:2305.14157, 2023.
- **Arquivo**: `papers/gokkaya_2023_ssc-review.pdf`
- **Citado em**: Referencial Teórico 3.1 (definição de SSC)
- **Trecho original**: "Software Supply Chain can be defined as the set of processes necessary to select and obtain third-party software components, also encompassing the organizations and individuals involved in the distribution process of these resources."

---

JAIN, V. et al. Static Vulnerability Analysis of Docker Images. **IOP Conference Series: Materials Science and Engineering**, v. 1131, n. 1, p. 012018, 2021. DOI: 10.1088/1757-899X/1131/1/012018.
- **Arquivo**: `papers/jain_2021_static-vulnerability-docker.pdf`
- **Citado em**: (disponível para Referencial Teórico 3.4 — revisão de mecanismos de segurança Docker)

---

JAVED, O.; TOOR, S. Understanding the Quality of Container Security Vulnerability Detection Tools. In: ACM INTERNATIONAL CONFERENCE ON CLOUD AND BIG DATA COMPUTING (ICCBDC), 5., 2021, Liverpool. **Proceedings [...]**. ACM, 2021. DOI: 10.1145/3481646.3481661.
- **Arquivo**: `papers/javed_2021_container-security-quality.pdf`
- **Citado em**: (disponível para Referencial Teórico 3.4 — qualidade e acurácia de scanners)
- **Trecho original**: "Existing tools do not have high accuracy, since ≈34% vulnerabilities are being missed by the best performing tool."

---

HIESGEN, R. et al. The Race to the Vulnerable: Measuring the Log4j Shell Incident. **arXiv preprint** arXiv:2205.02544, 2022.
- **Arquivo**: `papers/hiesgen_2022_log4j.pdf`
- **Citado em**: Justificativa (Log4j), Introdução (ataques SSC), Referencial Teórico 3.2 (camadas de containers)
- **Trecho original**: "The Log4j vulnerability [...] resides in libraries deeply nested within software supply chains."

---

LADISA, P. et al. SoK: Taxonomy of Attacks on Open-Source Software Supply Chains. In: IEEE SYMPOSIUM ON SECURITY AND PRIVACY (SP), 2023. **Proceedings [...]**. IEEE, 2023.
- **Arquivo**: `papers/ladisa_2023_taxonomy-attacks.pdf`
- **Citado em**: Justificativa (uso de OSS no SDLC), Introdução (shift-left), Referencial Teórico 3.1 (definição de SSC, dependências transitivas)
- **Trecho original (definição SSC)**: "A complex ecosystem that involves both the development and the construction and delivery of software, encompassing tools, people, components and infrastructures that contribute to the creation of a final product."
- **Trecho original (visibilidade)**: "Downstream consumers have no control over and limited visibility into given projects' security practices. The sheer number of dependencies makes rigorous reviews impractical for a given consumer."

---

LINS, S. et al. On the critical path to implant backdoors and the effectiveness of potential mitigation techniques: Early learnings from XZ. 2024.
- **Arquivo**: `papers/lins_2024_xz-utils.pdf`
- **Citado em**: Justificativa (xz utils), Introdução (ataques SSC)
- **Trecho original**: Análise da tentativa de backdoor no XZ Utils, ataque sofisticado visando comprometer servidores SSH globalmente via manipulação de um mantenedor de software livre.

---

PARDO MINAYA, S. D. **Open source tools for container vulnerability analysis**. 2024. Dissertação (Mestrado em Engenharia Informática) – Universitat Politècnica de València, València, 2024.
- **Arquivo**: `papers/pardo_2024_opensource-container-analysis.pdf`
- **Citado em**: (disponível para Referencial Teórico 3.4 — comparação Grype, Trivy, Clair, Snyk)
- **Trecho original (Trivy)**: "Trivy is a vulnerability scanner specialized in container and virtual machine images, file systems and Kubernetes and AWS clusters."
- **Trecho original (Clair)**: "Clair is a vulnerability scanner for Docker and OCI containers. Its architecture is based on the ClairCore library wrapped by a web interface and notification service."
- **Trecho original (Grype)**: "Grype is a vulnerability scanner for Docker, OCI and Singularity container images. It can scan packages, file systems or SBOMs."

---

MARTINEZ, J. A. **Software Supply Chain Attacks, a Threat to Global Cybersecurity: SolarWinds' Case Study**. 2021.
- **Arquivo**: `papers/martinez_2021_solarwinds.pdf`
- **Citado em**: Referencial Teórico 3.1 (85-97% código de terceiros)
- **Trecho original**: "The dependence of third-party code (85% to 97% of current code) creates critical vulnerabilities in the development cycle."

---

SONATYPE. **2026 State of the Software Supply Chain**. 10. ed. Sonatype, 2026. Disponível em: https://www.sonatype.com/state-of-the-software-supply-chain. Acesso em: mar. 2026.
- **Arquivo**: `papers/sonatype_2026_ssc-report.pdf`
- **Citado em**: Justificativa (crescimento SSC), Introdução (9,8 trilhões downloads), Referencial Teórico 3.1 (risco estrutural, dependências transitivas), Referencial Teórico 3.2 (ponto cego, discrepâncias entre ferramentas), Referencial Teórico 3.3 (revisão manual não escala)
- **Trecho original (downloads)**: "9.8 TRILLION downloads across Maven Central, PyPI, npm and NuGet."
- **Trecho original (risco estrutural)**: "The scale and ubiquity of open source software have transformed software ecosystems into critical global infrastructures, creating structural risk."
- **Trecho original (dependências transitivas)**: "Each new package increases choice and innovation, but it also multiplies evaluation and enforcement challenges. More components mean more potential entry points for risk and greater transitive exposure as teams pull in deep dependency trees they may not fully understand or monitor."
- **Trecho original (revisão manual)**: "Teams cannot rely on manual review or reactive patching. Automation, prioritization, and rapid upgrade motion are essential to keeping pace with an ecosystem where critical risk can now propagate as quickly as the code itself."

---

WILLIAMS, L.; HAMER, S.; ZAHAN, N. Can the Rising Tide of Software Supply Chain Attacks Raise All Software Engineering Boats? In: ACM CONFERENCE, 2024. **Proceedings [...]**. ACM, 2024.
- **Arquivo**: `papers/williams_2024_rising-tide.pdf`
- **Citado em**: Introdução (aumento exponencial de ataques SSC desde 2020)
- **Trecho original**: "Software supply chain attacks have increased exponentially since 2020, prompting worldwide government and corporate initiatives."

---

WILLIAMS, L. et al. Research Directions in Software Supply Chain Security. **ACM Computing Surveys**, 2025.
- **Arquivo**: `papers/williams_2025_research-directions.pdf`
- **Citado em**: Referencial Teórico 3.1 (escopo da SSC), Referencial Teórico 3.2 (imagens como artefatos, ferramentas de escaneamento)
- **Trecho original (escopo SSC)**: "The software supply chain encompasses commercial code and configurations, open-source binaries, plugins, container dependencies, as well as critical tools such as compilers, code analyzers, and build orchestrators."
- **Trecho original (imagens como artefatos)**: "Container images in continuous deployment pipelines expand the attack surface, making the ecosystem susceptible to vectors such as dependency poisoning and malicious code injection."

---

WILLIAMS, L.; MIGUES, S. Establishing a Baseline of Software Supply Chain Security Task Adoption by Software Organizations. In: INTERNATIONAL CONFERENCE ON SOFTWARE ENGINEERING (ICSE), 47., 2025. **Proceedings [...]**. ACM, 2025.
- **Arquivo**: `papers/williams_2025_baseline-ssc.pdf`
- **Citado em**: (disponível para uso futuro)
- **Trecho original**: "Software supply chain attacks have increased exponentially since 2020. The primary attack vectors are through: (1) software components; (2) the build infrastructure; and (3) humans."

---
