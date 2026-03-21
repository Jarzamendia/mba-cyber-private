## DevPhish: Exploring Social Engineering in Software Supply Chain Attacks on Developers

1 st Hossein Siadati

Computer Science Department UNCW

Wilmington, USA siadatis@uncw.edu

5 th Elijah Tripp Computer Science Department UNCW Wilmington, USA

elt8862@uncw.edu

2 nd Sima Jafarikhah

Computer Science Department UNCW

3 rd Elif Sahin

Computer Science Department

UNCW

Wilmington, USA jafarikhaht@uncw.edu

6 th Denis Khryashchev Computer Science Department NYU New York, USA denis.khryashchev@nyu.edu

Abstract -The Software Supply Chain (SSC) has captured considerable attention from attackers seeking to infiltrate systems and undermine organizations. There is evidence indicating that adversaries utilize Social Engineering (SocE) techniques specifically aimed at software developers. That is, they interact with developers at critical steps in the Software Development Life Cycle (SDLC), such as accessing Github repositories, incorporating code dependencies, and obtaining approval for Pull Requests (PR) to introduce malicious code. This paper aims to comprehensively explore the existing and emerging SocE tactics employed by adversaries to trick Software Engineers (SWEs) into delivering malicious software. By analyzing a diverse range of resources, which encompass established academic literature and real-world incidents, the paper systematically presents an overview of these manipulative strategies within the realm of the SSC. Such insights prove highly beneficial for threat modeling and security gap analysis.

## I. INTRODUCTION

Software development companies and their clients are increasingly alarmed by the prevalence of software supply chain breaches. Prominent instances, including the breach of SolarWinds' build system [46], JumpCloud's and S3CX's compromise of developer environment [15], [19], the exploitation of a critical vulnerability within the widely used Log4j open source dependency [31], unauthorized access to sensitive data via Codecov's container image creation process [26], and customer breaches stemming from vulnerabilities in Kaseya's VSA software [49], have starkly highlighted the potential for widespread disruption resulting from a single supply chain attack.

979-8-3315-4090-6/24/$31.00 ©2024 IEEE. Personal use of this material is permitted. Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.

4 th Terrence Hernandez

Computer Science Department UNCW

Wilmington, USA es5510@uncw.edu

Wilmington, USA tbh1597@uncw.edu

7 th Amin Kharaz

School of Computing and Information Sciences Florida International University Florida, USA amin@iseclab.org

These attacks encompass various intricate steps and often leverage technical expertise, frequently exploiting human vulnerabilities to initiate or progress the attack. In the eventstream hack, for instance, attackers lured maintainers of a widely used Open-Source NPM library named event-stream . They then assumed the role of maintainers and introduced a new dependency that offered a valuable functionality alongside a hidden backdoor enabling the attackers to steal Bitcoin from e-wallets [37].

Numerous studies have delved deep into its technical dimensions in the expansive domain of SSC security. Yet, a notable gap remains, where the realm of social engineering intrinsic to these incidents remains relatively unexplored. In particular, there exists a lack of research investigating the nuanced interplay of social engineering in leveraging the human element, particularly within the context of SWEs. We have coined the term DevPhish to encapsulate the act of manipulating SWEs, inducing them to unknowingly introduce malicious code into the software. This novel term draws attention to the significant vulnerability introduced by human psychology, emphasizing the need to dissect the intricate connections between technological susceptibilities and human manipulation within the SSC landscape.

To address the void in the domain, this research undertakes an in-depth examination of the realm of social engineering within the SSC by analyzing real-world incidents. This study embarks on the exploration of the following paramount questions:

- To what degree do social engineering tactics play a role in the success of SSC attacks?
- How do attackers interact with SDLC steps to launch social engineering attacks?

The structure of this paper is as follows: Chapter II provides the required background on SSC Security. Chapter III explains our data collection and labeling methodology, and Chapter IV

categorizes attack techniques that involve social engineering. Chapter V analyzes attempts at answering our research questions.

## II. SOFTWARE SUPPLY CHAIN SECURITY

## A. Software Supply Chain

SSC parallels the stages of a traditional supply chain:

- Source Code Development: Analogous to raw material acquisition, developers create the foundational source code that serves as the building blocks of the software.
- Build - Compilation and Packaging: Similar to manufacturing and assembly, the source code is compiled, processed, and packaged to create the final software product . This step involves compilation, integration, and quality checks.
- Distribution: Just as products are distributed, software is distributed through repositories, websites, or app stores. Ensuring accessibility and proper version management is crucial.
- Deployment: Like retail and point of sale, users deploying the software on their devices and infrastructure. This phase initiates user interaction with the software.
- Runtime Support and Updates: Following deployment, the software system operates on machines, engaging users in interactions with the software. This phase aligns with customers utilizing the service, ensuring system availability, and maintaining the system's currency with the latest feasible versions.

When a feature needs to be implemented, a developer crafts the necessary code to realize this functionality including custom logic written in a specific programming language and dependencies from open-source projects. The developer then initiates a PR, encompassing the new code, and requests a review from a colleague. Typically, this review process involves feedback and iterative revisions until the code aligns with established standards and can be merged into the company's code repository.

Following the merge, an automated process called Continuous Integration/Continuous Delivery (CI/CD) comes into play. This process involves recompiling or rebuilding the software and deploying the output-an application or container image-into the company's registry. Subsequent scripts retrieve these artifacts from the registry, facilitating deployment within the company's computing clusters.

The SSC also encompasses aspects such as public container registries and housing executable components that interface with a software system. Additionally, there are contributing open source developers and distinct roles, including Site Reliability Engineers (SREs) who wield substantial access privileges and often oversee operational services.

## B. Software Supply Chain Attacks

SSC attacks aim to transform a genuine software artifact into a malicious one by compromising the SDLC. Consequently, software counterfeiting, malware, and Trojans, which

Fig. 1. Software Supply Chain steps and threats based on documentations of SLSA framework [21]

<!-- image -->

are fundamentally unauthorized, do not fall under the classification of SSC attacks.

An instance of SSC attacks involving social engineering is the security breach of JumpCloud, a zero-trust directory platform service utilized for identity and access management. In this incident, a North Korean threat actor successfully executed a spear-phishing attack on a developer, leading them to download malicious code onto their device unwittingly. This provided the threat actor with developer-level access to JumpCloud environments, explicitly targeting their commands framework . This framework was subsequently exploited for injecting malicious data into customer environments [19].

The primary framework for delineating the scope of this attack is the Supply Chain Levels for Software Artifacts ( SLSA ) [21], initiated by Google and established within the Open Source Security Foundation. While this framework assists in identifying SSC threats (see Figure 1), it lacks a detailed perspective for modeling social engineering within the SSC.

## C. Scope of work

The primary emphasis of this study is DevPhish for SSC attacks, wherein developers are subjected to social engineering during their direct involvement in the software development life cycle. Figure 2 illustrates examples of these interactions.

## III. RESEARCH METHODOLOGY

The methodology employed for this study involved conducting a Systematic Literature Review (SLR) to carefully select and evaluate pertinent studies from a vast body of existing literature, including academic papers, industry reports, and real-world incidents. In addition, relevant entries from news outlets and bug bounty reports were incorporated to supplement our research. To find these resources, we used keywords such as software supply chain attacks , social engineering software supply chain , and software engineer social engineering on both the Google search engine and Google Scholar. We also used a major listing containing SSC attacks compiled by domain experts [16]. The result is a list of 198

TABLE I SUMMARY OF DEVPHISH TYPES

| DevPhish Type                        | Description                                                                                                                         |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Account Compromise                   | Stealing credentials for developer's platforms, equivalent of traditional phishing (e.g., Phishing github account)                  |
| Device Compromise                    | Compromising developer's device by luring them to install malware (e.g. Installing malicious IDE extensions)                        |
| Malicious Pull Request               | Pull request to merge malicious code (e.g., an attacker posing as an open source contributor adding a malicious dependency to code) |
| Malicious Dependency Watering hole   | Malicious dependencies that are inadvertently added to a code (e.g., importing Typosquatting packages)                              |
| Malicious Code Snippet Watering hole | Malicious code that are added to code inadvertently (e.g., copied code from StackOverflow)                                          |
| Entering the Rank of Maintainers     | Social Engineering to become an open source project maintainer                                                                      |

Fig. 2. Example interactions between software developers and Software Development Life Cycle (SDLC) critical steps

<!-- image -->

unique SSC attacks. Afterward, we categorized the attacks into buckets based on their fi rst point of impact on developers. We used multiple labeling and cross-validation to make sure the labeling aligns between a team of 4 individuals.

## IV. SOCIAL ENGINEERING TECHNIQUES IN SSC ATTACKS

We have classified the DevPhish techniques employed in SSC attacks, which are based on social engineering, into six categories outlined in Table I. Each category encompasses various variations.

1) Account Compromise : Compromised accounts are a significant vector for cyberattacks, with phishing being a common strategy employed when attackers' attempts at guessing attacks fail. While it might seem less probable to deceive someone knowledgeable in technology into surrendering their credentials, human psychology prevails when executing a meticulously crafted attack. As an illustration, Dropbox experienced a data breach resulting from an attack that targeted its employees through phishing emails. These phishing emails imitated CircleCI [13], a CI/CD platform essential to their Software Development Life Cycle (SDLC), resulting in the compromise of employee accounts. Subsequently, the attackers successfully exfiltrated 130 Github repositories containing vital business information. Notably, this attack was related to a larger GitHub phishing campaign [51] that aimed at a broader group of developers.

In addition to stealing business-critical information, compromised developer accounts are frequently exploited to inject malicious code into source codes. A notable incident involves the compromise of the official PHP Git repository, where attackers submitted code changes to the PHP source code. These commits were falsely attributed to recognized PHP developers and maintainers [41]. This compromise impacted two million websites utilizing this package. Another example is ua-parserjs hack where the attackers compromised a developer account and uploaded malicious versions of software [12].

Developers manage multiple accounts to access various platforms essential for their daily tasks. These platforms encompass those dedicated to software development (such as Github, cloud platforms, and repositories) and communication tools (such as Zoom and Docs), as illustrated in Figure 2. Of particular interest to attackers are the package repository accounts. In pursuit of this, attackers focus on developers' accounts on package repositories like PyPI and NPM, where they upload malicious versions of legitimate packages. Noteworthy instances include a phishing campaign explicitly designed to steal PyPI developers' credentials [14].

The persuasion techniques used by attackers align with developers' anticipated messaging. For example, a phishing message claims there is a new process for authentication due to 'a surge in malicious packages being uploaded to the PyPI.org domain' [14].

2) Device Compromise : Another form of phishing targeting developers involves tricking them into installing malware on their devices. Regardless of how the malware manages to infiltrate a developer's machine, the repercussions are severe. For instance, in the case of the CircleCI breach [39], an employee fell victim to an elaborate spear-phishing scheme, resulting in the download of an application supposedly for viewing/signing a critically important PTX document. The compromised device then granted unauthorized access to customers' secret tokens, which were subsequently exploited for information theft. In the JumpCloud breach, a highly skilled North Korean threat actor successfully executed a spearphishing attack on a developer, leading them to unknowingly download malicious code provided by JumpCloud onto their device. This granted the threat actor developer-level access to JumpCloud developer environments [19].

In a different iteration of this attack, the compromise of a device occurs during the installation of package dependencies, wherein a malicious pre/post-installation script infiltrates the device. In essence, an attacker could encapsulate a legitimate package with a deceptive installer. As a result, the code itself remains uncompromised, but the developer's machine falls victim to the compromise. In a specific instance, attackers exploited the NPM package installation process [9], [27] to deceive developers who only inspect the package's content.

In another scenario, device compromise occurs through Code Checkout . This method primarily aims to entice Software Engineers (SWEs) to execute a project on their device and hence compromise it, ostensibly for testing software functionality. For example, in the instance of the Fake zero-day PoC [48], attackers created a bogus account, posing as a security researcher offering a Proof of Concept (PoC) for a zero-day vulnerability. Impersonating security researchers, attackers create authentic-looking repositories using profile images, Twitter accounts, and GitHub repositories to lure victims.

Finally, an alternative method involves compromising a device through physical access. A notable example is the CCleaner attack [47], where the breach originated from an incident of physical access to a workstation. Following this breach, the compromise expanded laterally, affecting addi- tional accounts and ultimately compromising the build system.

3) Malicious Pull Requests : Attackers can manipulate contributors into approving their malicious contributions to open-source projects. Hosted on source control systems like GitHub, these contributions manifest as PRs. In a controlled experiment, researchers demonstrated that complex vulnerabilities can deceive even skilled software engineers. They submitted disguised PRs to the mailing list using the standard Linux contribution process. These concealed flaws introduced dormant vulnerabilities, such as a Use-After-Free (UAF) hidden behind apparent legitimacy, employing obfuscation and unconventional pathways. The proposed malicious changes were approved [52]. In the StatCounter breach, employing code obfuscation method was used to impede developers from easily detecting malicious code during PR reviews [3]. Numerous instances have been documented where malicious code has infiltrated open-source projects. For instance, a joint study by GitHub and Microsoft Research [29] pinpointed 15 repositories containing at least one malicious commit.

Another form of this attack involves utilizing large PRs, especially auto-generated sections, to bypass reviewer scrutiny and introduce malicious code. Auto-generated files, like npm's lockfiles for dependency installation, are susceptible to manipulations from executed commands, making them prone to malevolent changes. The intricate and frequent alterations they undergo during each PR pose challenges for a thorough review, as emphasized in [44].

A distinct form of this attack involves submitting a Pull Request to a target project, introducing a controlled malicious dependency . In such cases, the dependency may not be inherently malicious but potentially turn malicious in the future.

The Agama Wallet incident illustrates this attack, where a pull request added the electron-native-notify package. Although initially benign, the package later turned malicious, enabling attackers to steal wallet seeds and other login passphrases used in the application [5], [35].

In more sophisticated attacks, attackers might focus on a dependency of a dependency or an indirect dependency. For instance, in the event-stream attack [37], attackers aimed at a bitcoin wallet platform by exploiting its reliance on the 'event-stream' package, which in turn depended on 'flatmapstream.' The actor 'right9ctrl' gained the trust of eventstream maintainers, convincing them to merge a new package - flatmap-stream - into event-stream. Initially innocuous, this contribution later became malicious and triggered an attack. Flatmap-stream assessed explicitly if it was executed during building the Copay app [37].

Finally, attackers may leverage social engineering tactics through pull requests (PRs) to communicate with developers, potentially embedding phishing links within the PR description, as demonstrated in the work by Siadati et al. [43].

4) Malicious Dependency Watering hole : Within this type of attack, perpetrators craft and disseminate malicious packages, anticipating their use by unsuspecting individuals. In the prevalent form known as Typosquatting, developers inadvertently fall prey to the resemblance in names between a malicious component and a genuine dependency. To achieve this, the attackers deliberately select names for their malicious packages that closely mimic those of widely recognized and trusted counterparts. This strategy, also called Typosquatting, aims to exploit user typographical errors, causing them to download malicious packages or services mistakenly. Attackers replicate the names of legitimate packages within public repositories, anticipating that users or developers will inadvertently select these fraudulent alternatives. Approximately 61% of malicious packages utilize Typosquatting by imitating existing package names [38]. Several incidents are reported, such as 700 typosquatted libraries On RubyGems [33], PyPI [2], [40], golang [30], and NPM [1], [28].

Typosquatting is a cheap and easily executed tactic that significantly affects numerous developers. In one case, attackers generated eight packages with distinct names but identical functionality [25], and developers unknowingly incorporated them. In this incident, the malicious batch has been downloaded 30,000 times. Another example is [8], which targets Twillio developers and fully compromise their machine. Another attacker distributed the mathjs-min posing as a minified version of wildely-used JS library [18]. The malicious code was added to an innocuously named commit and deeply embedded in the library's files. Another example is RXDrioder SDK which presents itself as an ad-related SDK [6]. It is believed that 206 application developers were scammed to use this package. As a result of this attack, 150 million devices were infected. Similar attacks are being observed in the Ruby gem ecosystem [45]. In 2018 alone, research unveiled a cumulative 600 million downloads [10] of typosquatted packages.

Adversaries have easily scaled Typosquatting by automating the cloning of GitHub repositories and infusing them with malevolent code. They adopt names closely mirroring authentic package names, albeit within separate repositories. In a singular instance, the attacker crafted 35,000 packages using this method, intending to compromise a substantial array of software products [11]. Some of the GitHub supply chain attack forks had several stars, some dating back around five years, suggesting they had been in active use.

Brandjacking represents another form of this attack, involving the distribution of a malicious package with an identical name to a well-known one. A significant incident occurred in 2019 against iOS, targeting developers [7]. This resulted in injecting malicious code into 350 apps, including WeChat, impacting hundreds of millions of users. In another instance, attackers created web-browserify to target developers using the well-known browserify package, used for developing crossplatform Node.js-style modules [42].

5) Malicious Code Snippet Watering hole : This attack occurs when an attacker circulates vulnerable sample code, hoping others will incorporate it, making their applications vulnerable. Research has identified numerous vulnerable code snippets on technical social media platforms like Stack Overflow. Out of 72,483 scrutinized code snippets used in at least one GitHub-hosted project, 99 were found to be vulnerable. These compromised snippets, discovered on Stack Overflow, were used in 2,859 GitHub projects [50]. Although no study has determined whether these instances result from wellintentioned but misguided suggestions or intentional actions, it is conceivable that attackers might exploit this method to propose malicious code intentionally. These attackers could manipulate ranking mechanisms on these platforms to boost the visibility of their harmful code.

6) Entering the Rank of Maintainers : In this attack, attackers engage in social engineering to persuade core developers of a project to grant them the role of project maintainer. Open-source project maintainers have significant privileges and can unilaterally modify the code or project settings. An example of this attack is the compromise of the widely-used event-stream package (with 1.9 million weekly downloads on NPM). In this incident, the attacker, having gained the trust of the repository owner, obtained privileged access to the repository and injected a backdoor into the code [4], [37]. The social engineering aspect involved building trust with the repository owner by offering assistance to add a specific feature.

Certain maintainers, motivated by financial or political interests, act maliciously in a different form of this attack. An instance includes a maintainer turning rogue for political reasons, releasing a malicious version of the 'node-ipc' library with obfuscated code [34]. In some border cases, like the SSH Decorator (ssh-decorate) incident, it remains unclear whether the intentional code vulnerability resulted from a developer going rogue or if their account was compromised.

## V. ANALYSIS

As outlined in section IV, real-world SSC attacks encompass six primary social engineering types. We counted attack types in the collected dataset of SSC attack incidents. We observe that approximately 27% (53 out of 198) of SSC attack reports mentioned at least one social engineering type used by attackers. The distribution of attack types is presented in Table II. The most prevalent type of attack is the Malicious Dependency Watering Hole , with Typosquatting being the primary subcategory. The second most common type is Malicious Pull Request .

## VI. DISCUSSIONS

Although the cases examined in this paper characterize DevPhish as a current threat to SSC security, it is crucial to explain the lessons learned from these threats, their impact, and how the security community should respond to emerging threats in the future. This section delves into the implications of our investigation and provides recommendations for potential paths forward.

Community Consensus. Establishing robust auditing mechanisms on a large scale to shield SSC from DevPhish attacks is a complex undertaking that demands community consensus on the precise places and methods for implementing these auditing measures. The absence of auditing mechanisms in the intricate landscape of the modern SSC ecosystem creates opportunities for DevPhish attacks.

An emerging approach involves auditing build and publish attestations, exemplified by initiatives like those offered by NPM and the Sigstore project [17]. This technique aims to identify discrepancies during a phishing attack. For instance, if an attacker compromises a software repository account and uploads packages directly without committing the corresponding code changes to GitHub repositories, it becomes more challenging for the attacker to erase all traces.

However, enforcing the mechanism at scale is a multidimensional problem. We understand that finding the right incentives for developers, code maintainers, and repositories to implement verification policies might be challenging on a global scale, as these entities might be wary of policing the development community. However, a coalition in this direction could be helpful as today Sigstore [20] is the main or perhaps the only line of defense for protecting software systems from these attacks.

Updating Threat Models. Our analysis pipeline incorporates multiple vantage points to look at the DevPhish threats. It is critical to ensure the SSC community considers all the possible attack surfaces, including human factors. There have been several research on different aspects of the SSC ecosystem and different security systems that have been developed to characterize the threat and issues (e.g., software fuzzing methods, taint tracking). However, attackers' capabilities to influence the development lifecycle are not studied well. Given the number of incidents as well as the consequence of DevPhish attempts, it is critical to make developers more aware of adversaries'

TABLE II OCCURRENCE OF EACH TYPE OF DEVPHISH IN SOFTWARE SUPPLY CHAINS INCIDENTS

| Attack Type                          |   Number of Incidents | %    |
|--------------------------------------|-----------------------|------|
| Account Compromise                   |                     4 | 7.5% |
| Device Compromise                    |                     5 | 9%   |
| Malicious Pull Requests              |                     7 | 13%  |
| Malicious Dependency Watering hole   |                    33 | 62%  |
| Malicious Code Snippet Watering hole |                     1 | 2%   |
| Entering the Rank of Maintainers     |                     3 | 6.5% |
| Total                                |                    53 | 100% |

capabilities with a more comprehensive list of possible threats, including human factors.

Robustness and Generalizability. In our evaluation, we rely on the public account of an incident to determine the presence or absence of social engineering in an attack. It is possible that certain social engineering aspects may not be fully reflected in the report, potentially affecting our assessment of social engineering involvement in SSC attacks. Therefore, we regard our measurement as a conservative estimate.

Incomplete reports posed challenges in categorizing certain attack cases due to limitations in the available data. For instance, it remains unclear whether the SSH Decorator (sshdecorate) incident resulted from the developer going rogue or their account being compromised. Additionally, some cases involved multiple social engineering attacks, such as device compromise followed by account compromise. In our assessment, we only consider the occurrence at the initial point of impact.

The attack reports we utilized grouped instances of attacks, potentially based on attack campaigns. For instance, Typosquatting cases were mainly categorized according to the target packages they impersonate, without accounting for the number of successful instances of SSC compromise resulting from them.

## VII. RELATED WORK

This work lies at the intersection of software supply chain security and social engineering . For background on software supply chain security, we refer the reader to Section II. Numerous studies have explored how to secure the software supply chain [23], [24]. These methods aim to prevent or detect attacks at various stages [21] (see Figure 1) of the software supply chain, including Source , Build , Dependencies usage, and Package distribution. A key concept in preventing software supply chain attacks is software artifact Provenance checks. This involves verifying the origin of software at different levels to ensure they are produced by authorized systems and individuals. In-toto [22] is a framework that defines the expected sequences of software provenance in a supply chain and enables attestations that verify required software integrity constraints. However, these checks are ineffective if a developer is socially engineered to approve an attacker's actions. Similarly, several comprehensive surveys have examined attack techniques targeting software supply chains [32], [36], [38], yet none have specifically focused on the social engineering aspect of these attacks. This work addresses this gap by focusing on how social engineering can bypass existing checks and calls for further research on this prevalent issue.

## VIII. CONCLUSION

Social engineering is a factor in approximately 27% of analyzed SSC attacks, encompassing six identified categories, many of which differ from traditional social engineering attacks. This highlights the need to develop custom prevention and detection mechanisms tailored to the workflows of software developers. We are sharing our compiled dataset of SSC attack incidents with the community, encouraging additional exploration and research in this domain.

## REFERENCES

- [1] 'HackTask,' https://github.com/cncf/tag-security/blob/main/supplychain-security/compromises/2017/hacktask.md, 2017, [Online; accessed 13-August-2023].
- [2] 'Colourama,' https://github.com/cncf/tag-security/blob/main/supplychain-security/compromises/2018/colourama.md, 2018, [Online; accessed 13-August-2023].
- [3] (2018) Statcounter analytics code hijacked to steal bitcoins from cryptocurrency users. [Online]. Available: https://thehackernews.com/ 2018/11/statcounter-cryptocurrency-cyberattack.html
- [4] 'The event-stream vulnerability,' https://github.com/cncf/tag-security/ blob/main/, 2018, [Online; accessed 13-August-2023].
- [5] 'Plot to steal cryptocurrency foiled by the npm security team,' https://blog.npmjs.org/post/185397814280/plot-to-steal-cryptocurrencyfoiled-by-the-npm, 2019, [Online; accessed 13-August-2023].
- [6] 'SIMBAD: A Rouge adware campaign on google play,' https://research.checkpoint.com/2019/simbad-a-rogue-adwarecampaign-on-google-play/, 2019, [Online; accessed 13-August-2023].
- [7] 'XCodeGhost,' https://github.com/cncf/tag-security/blob/main/supplychain-security/compromises/2015/xcodeghost.md, 2019, [Online; accessed 13-August-2023].
- [8] 'Malicious npm package opens backdoors on programmers' computers,' 2020, [Online; accessed 13-August-2023]. [Online]. Available: https://www.zdnet.com/article/malicious-npm-packageopens-backdoors-on-programmers-computers/
- [9] 'Malicious npm packages caught installing remote access trojans,' 2020, [Online; accessed 13-August-2023]. [Online]. Available: https://www.zdnet.com/article/malicious-npm-packages-caughtinstalling-remote-access-trojans/
- [10] 'Beware the Package Typosquatting Supply Chain Attack,' https://www.darkreading.com/vulnerabilities-threats/beware-thepackage-typosquatting-supply-chain-attack, 2021, [Online; accessed 13-August-2023].
- [11] 'Beware the Package Typosquatting Supply Chain Attack,' https://www. thestack.technology/github-supply-chain-attack-clones/, 2021, [Online; accessed 13-August-2023].
- [12] 'Compromise of NPM package ua-parser-js,' https://github.com/cncf/ tag-security/blob/main/supply-chain-security/compromises/2021/uaparser-js.md, 2021, [Online; accessed 13-August-2023].
- [13] 'Dropbox hacker steals 130 GitHub repositories,' https: //github.com/cncf/tag-security/blob/main/supply-chain-security/ compromises/2022/dropbox-github-account-breach.md, 2022, [Online; accessed 13-August-2023].
- [14] 'Phishing Campaign Targets PyPI Users to Distribute Malicious Code,' https://www.darkreading.com/cloud/phishing-campaign-targetspypi-users-to-distribute-malicious-code, 2022, [Online; accessed 13August-2023].
- [15] (2023) 3cx software supply chain compromise initiated by a prior software supply chain compromise; suspected north korean actor responsible. [Online]. Available: https://www.mandiant.com/resources/ blog/3cx-software-supply-chain-compromise
- [16] (2023) Common oss supply chain threats. [Online]. Available: https://github.com/ossf/s2c2f/blob/main/specification/framework. md#common-oss-supply-chain-threats
- [17] (2023) Generating provenance statements. [Online]. Available: https: //docs.npmjs.com/generating-provenance-statements
- [18] 'NPM Package mathjs-min Contains Credential Stealer,' https://github.com/cncf/tag-security/blob/main/supply-chainsecurity/compromises/2023/mathjs-min.md, 2023, [Online; accessed 13-August-2023].
- [19] (2023) [security update] june 20 incident details and remediation. [Online]. Available: https://jumpcloud.com/blog/security-update-june20-incident-details-and-remediation
- [20] (2023) Sigstore. [Online]. Available: https://www.sigstore.dev/
- [21] (2023) Supply chain levels for software artifacts, or slsa (salsa). [Online]. Available: https://slsa.dev
- [22] (2024) in-toto: A framework to secure the integrity of software supply chains. [Online]. Available: https://in-toto.io
- [23] (2024) Secure software development framework (ssdf). [Online]. Available: https://csrc.nist.gov/Projects/ssdf
- [24] (2024) Securing the software supply chain, recommended practices guide for developers. [Online]. Available: https://www.cisa.gov/sites/default/files/publications/esf securing the software supply chain developers.pdf
- [25] O. K. Andrey Polkovnichenko and S. Menashe, 'JFrog Detects Malicious PyPI Packages Stealing Credit Cards and Injecting Code,' https://jfrog.com/blog/malicious-pypi-packages-stealing-creditcards-injecting-code/, 2021, [Online; accessed 13-August-2023].
- [26] bleepingcomputer, 'Popular Codecov code coverage tool hacked to steal dev credentials,' https://www.bleepingcomputer.com/news/security/ popular-codecov-code-coverage-tool-hacked-to-steal-dev-credentials/, 2021, [Online; accessed 13-August-2023].
- [27] C. Cimpan, 'Three npm packages found opening shells on Linux, Windows systems,' 2020, [Online; accessed 13-August2023]. [Online]. Available: https://www.zdnet.com/article/three-npmpackages-found-opening-shells-on-linux-windows-systems/
- [28] C. Cimpanu, 'Four npm packages found uploading user details on a GitHub page,' 2020, [Online; accessed 13-August-2023]. [Online]. Available: https://www.zdnet.com/article/four-npm-packagesfound-uploading-user-details-on-a-github-page/
- [29] D. Gonzalez, T. Zimmermann, P. Godefroid, and M. Sch¨ afer, 'Anomalicious: Automated detection of anomalous and potentially malicious commits on github,' in 2021 IEEE/ACM 43rd International Conference on Software Engineering: Software Engineering in Practice (ICSESEIP) . IEEE, 2021, pp. 258-267.
- [30] M. Henriksen, 'Finding Evil Go Packages,' 2021, [Online; accessed 13-August-2023]. [Online]. Available: https://michenriksen.com/blog/ finding-evil-go-packages/
- [31] R. Hiesgen, M. Nawrocki, T. C. Schmidt, and M. W¨ ahlisch, 'The race to the vulnerable: Measuring the log4j shell incident,' arXiv preprint arXiv:2205.02544 , 2022.
- [32] P. Ladisa, H. Plate, M. Martinez, and O. Barais, 'Sok: Taxonomy of attacks on open-source software supply chains,' in 2023 IEEE Symposium on Security and Privacy (SP) . IEEE, 2023, pp. 1509-1526.
- [33] R. Lakshmanan, 'Over 700 Malicious Typosquatted Libraries Found On RubyGems Repository,' https://thehackernews.com/2020/04/rubygemtyposquatting-malware.html, 2020, [Online; accessed 13-August-2023].
- [34] A. Leonov, 'Malicious Open Source: the cost of using someone else's code,' https://avleonov.com/2022/05/11/malicious-open-sourcethe-cost-of-using-someone-elses-code/, 2021, [Online; accessed 13August-2023].
- [35] S. Maple, 'Synk security blog,' https://snyk.io/blog/yet-anothermalicious-package-found-in-npm-targeting-cryptocurrency-wallets/, 2019, [Online; accessed 26-July-2023].
- [36] M. Mounesan, H. Siadati, and S. Jafarikhah, 'Exploring the threat of software supply chain attacks on containerized applications,' in 2023
37. 16th International Conference on Security of Information and Networks (SIN) , 2023, pp. 1-8.
- [37] npmjs, 'Details about the event-stream incident,' https://blog.npmjs.org/ post/180565383195/details-about-the-event-stream-incident, 2018, [Online; accessed 13-August-2023].
- [38] M. Ohm, H. Plate, A. Sykosch, and M. Meier, 'Backstabber's knife collection: A review of open source software supply chain attacks,' in Detection of Intrusions and Malware, and Vulnerability Assessment: 17th International Conference, DIMVA 2020, Lisbon, Portugal, June 24-26, 2020, Proceedings 17 . Springer, 2020, pp. 23-43.
- [39] perception point, 'Takeaways from the CircleCI Incident,' https://perception-point.io/blog/takeaways-from-the-circleci-incident, 2023, [Online; accessed 13-August-2023].
- [40] Shamra, 'Sonatype Catches New PyPI Cryptomining Malware,' https://blog.sonatype.com/sonatype-catches-new-pypi-cryptominingmalware-via-automated-detection, 2021, [Online; accessed 13-August2023].
- [41] Sharma, 'PHP's Git server hacked to add backdoors to PHP source code,' 2021, [Online; accessed 13-August-2023]. [Online]. Available: https://www.bleepingcomputer.com/news/security/phps-gitserver-hacked-to-add-backdoors-to-php-source-code/
- [42] A. Sharma, 'Damaging Linux and Mac Malware Bundled Within Browserify npm Brandjack Attempt,' 2021, [Online; accessed 13August-2023]. [Online]. Available: https://blog.sonatype.com/damaginglinux-mac-malware-bundled-within-browserify-npm-brandjack-attempt
- [43] H. Siadati, T. Nguyen, and N. Memon, 'X-platform phishing: Abusing trust for targeted attacks short paper,' in Financial Cryptography and Data Security: FC 2017 International Workshops, WAHC, BITCOIN, VOTING, WTSC, and TA, Sliema, Malta, April 7, 2017, Revised Selected Papers 21 . Springer, 2017, pp. 587-596.
- [44] Tal, 'Why npm lockfiles can be a security blindspot for injecting malicious modules,' 2019, [Online; accessed 13-August-2023]. [Online]. Available: https://snyk.io/blog/why-npm-lockfiles-can-be-asecurity-blindspot-for-injecting-malicious-modules/
- [45] L. Tal, 'Malicious remote code execution backdoor discovered in the popular bootstrap-sass Ruby gem,' 2019, [Online; accessed 13-August-2023]. [Online]. Available: https://snyk.io/blog/malicious-remote-code-execution-backdoordiscovered-in-the-popular-bootstrap-sass-ruby-gem/
- [46] techtarget, 'SolarWinds hack explained: Everything you need to know,' https://www.techtarget.com/whatis/feature/SolarWinds-hackexplained-Everything-you-need-to-know, 2023, [Online; accessed 13-August-2023].
- [47] thehackernews, 'CCleaner Attack Timeline-Here's How Hackers Infected 2.3 Million PCs,' https://thehackernews.com/2018/04/ccleanermalware-attack.html, 2018, [Online; accessed 27-June-2023].
- [48] B. Toulas, 'Fake zero-day PoC exploits on GitHub push Windows, Linux malware,' https://www.bleepingcomputer.com/news/security/fake-zeroday-poc-exploits-on-github-push-windows-linux-malware/, 2023, [Online; accessed 13-August-2023].
- [49] truesec, 'Kaseya Supply Chain Attack Targeting MSPs to Deliver REvil Ransomware,' https://www.truesec.com/hub/blog/kaseya-supply-chainattack-targeting-msps-to-deliver-revil-ransomware, 2021, [Online; accessed 13-August-2023].
- [50] M. Verdi, A. Sami, J. Akhondali, F. Khomh, G. Uddin, and A. K. Motlagh, 'An empirical study of c++ vulnerabilities in crowd-sourced code examples,' IEEE Transactions on Software Engineering , vol. 48, no. 5, pp. 1497-1514, 2020.
- [51] A. Wales, 'Security alert: new phishing campaign targets GitHub users,' https://github.blog/2022-09-21-security-alert-new-phishing-campaigntargets-github-users/, 2022, [Online; accessed 13-August-2023].
- [52] Q. Wu and K. Lu, 'On the feasibility of stealthily introducing vulnerabilities in open-source software via hypocrite commits,' Proc. Oakland , 2021.