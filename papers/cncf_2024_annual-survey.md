<!-- image -->

<!-- image -->

## Cloud Native 2024

Approaching a Decade of Code, Cloud, and Change

March 2025

Valerie Silverthorne, Cloud Native Computing Foundation

Stephen Hendrick, The Linux Foundation

<!-- image -->

## Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change

Cloud native adoption reaches a new high of 89%, and it's equally popular in companies of all sizes.

Kubernetes dominates CNCF's top graduated products, with ties to five of the top products: Helm, etcd, CoreDNS, Cert Manager and Argo.

<!-- image -->

<!-- image -->

Use of CI/CD in production grew 31% from 2023 to 2024.

<!-- image -->

<!-- image -->

91% of organizations use containers for production, but their deployment is challenged primarily by cultural changes in the development team.

Incubating projects tell a technologically diverse story, from workload management to security and dev/user experience.

<!-- image -->

<!-- image -->

Organizations are releasing code faster than ever before: 29% are pushing it out the door multiple times a day, up from 23% in 2023.

<!-- image -->

## It's a Kubernetes world today:

93% of companies use it in production, are piloting it or are actively evaluating it.

<!-- image -->

Survey respondents reported significant progress in making their software more secure as compared to where they were in 2023.

<!-- image -->

77% of respondents said some, much, or nearly all of their deployment practices and tools adhere to GitOps principles.

<!-- image -->

## Contents

| Introduction ������������������������������������������������������������������������������������������������������������������������������������������������������������04    | Introduction ������������������������������������������������������������������������������������������������������������������������������������������������������������04    |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Key Findings�������������������������������������������������������������������������������������������������������������������������������������������������������������05    | Key Findings�������������������������������������������������������������������������������������������������������������������������������������������������������������05    |
| Cloud Native Adoption Continues to Grow .......................................................................................................05                              | Cloud Native Adoption Continues to Grow .......................................................................................................05                              |
| Popular and Plentiful, Cloud Usage Stays Strong............................................................................................. 08                                | Popular and Plentiful, Cloud Usage Stays Strong............................................................................................. 08                                |
| Container Use Grows, Powers Production ........................................................................................................11                              | Container Use Grows, Powers Production ........................................................................................................11                              |
| Kubernetes Reach Continues to Expand ...........................................................................................................14                             | Kubernetes Reach Continues to Expand ...........................................................................................................14                             |
| AI on Kubernetes: Still Getting Started...............................................................................................................15                       | AI on Kubernetes: Still Getting Started...............................................................................................................15                       |
| CNCF Project Snapshots.......................................................................................................................................16                | CNCF Project Snapshots.......................................................................................................................................16                |
| Security and Compliance......................................................................................................................................19                | Security and Compliance......................................................................................................................................19                |
| Web Assembly........................................................................................................................................................20         | Web Assembly........................................................................................................................................................20         |
| The Technology Roadmap Snapshot��������������������������������������������������������������������������������������������������������������������22                          | The Technology Roadmap Snapshot��������������������������������������������������������������������������������������������������������������������22                          |
| Service Mesh..........................................................................................................................................................22       | Service Mesh..........................................................................................................................................................22       |
| Containers to manage stateful applications......................................................................................................23                             | Containers to manage stateful applications......................................................................................................23                             |
| Serverless and FaaS ..............................................................................................................................................24           | Serverless and FaaS ..............................................................................................................................................24           |
| Infrastructure Platforms.......................................................................................................................................25              | Infrastructure Platforms.......................................................................................................................................25              |
| CI/CD: An Increasingly Mature Cloud Native Development Process ���������������������������������������������������������������27                                               | CI/CD: An Increasingly Mature Cloud Native Development Process ���������������������������������������������������������������27                                               |
| CI/CD tools..............................................................................................................................................................28    | CI/CD tools..............................................................................................................................................................28    |
| Code check-ins for the win...................................................................................................................................29                | Code check-ins for the win...................................................................................................................................29                |
| Release cycles ........................................................................................................................................................29      | Release cycles ........................................................................................................................................................29      |
| Automated releases..............................................................................................................................................31             | Automated releases..............................................................................................................................................31             |
| GitOps .....................................................................................................................................................................32 | GitOps .....................................................................................................................................................................32 |
| Methodology �����������������������������������������������������������������������������������������������������������������������������������������������������������33      | Methodology �����������������������������������������������������������������������������������������������������������������������������������������������������������33      |
| About the authors ��������������������������������������������������������������������������������������������������������������������������������������������������37         |                                                                                                                                                                                |
| Acknowledgments��������������������������������������������������������������������������������������������������������������������������������������������������37            | Acknowledgments��������������������������������������������������������������������������������������������������������������������������������������������������37            |
| End Notes�����������������������������������������������������������������������������������������������������������������������������������������������������������������38   |                                                                                                                                                                                |

## Introduction

Since 2015, the Cloud Native Computing Foundation has worked to make cloud native ubiquitous and, in this, our latest opportunity to survey the landscape and community, it's clear the idea that began with Kubernetes is becoming a reality. This past fall, 750 of our members shared their diverse - and nuanced - cloud native experiences, and now we've distilled them for the broader community. Read on for successes, surprises, some struggles, and technology strategies that might spark innovation in your organization.

As always, we are happy to share our full dataset for the Annual Survey, available at Data.world. 1  The findings from the 2023 survey can be found at https://www.cncf.io/reports/cncf-annualsurvey-2023/.

<!-- image -->

## FIGURE 1

## ADOPTION OF CLOUD NATIVE TECHNIQUES

To what extent has your organization adopted cloud native techniques? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q15, sample size = 409, shown to end-users, SIs or consultants based on Q9 and Q10, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q15, sample size = 522, organizations whose primary revenue is not from offering cloud native technologies or services in Q14, DKNS   responses excluded from the analysis

## Key Findings

## Cloud Native Adoption Continues to Grow

The adoption of cloud native techniques ( some, much, or nearly all ) reached a new high of 89% in 2024 (Figure 1). Overall cloud native momentum is increasing across the board, as the survey highlighted in several key data points.

First, the percentage of companies reporting just *some* of their application development and deployment (AD&amp;D) was cloud native declined by 16.6% in 2024 over 2023 as they transitioned to higher levels of cloud native use, while organizations with much of their AD&amp;D cloud native saw 7.5% growth while those with nearly all of their AD&amp;D cloud native saw a nearly 19% increase.

Second, the percentage of those who are 'cloud native beginners' also decreased - from 12% to 11.4% year over year - another indication of the increasing ubiquity of cloud native.

## FIGURE 2 CLOUD NATIVE ADOPTION BY COMPANY SIZE

Extent organization has adopted cloud native techniques by How many employees does your organization have worldwide?

<!-- image -->

2024 CNCF Annual Survey, Q15a x Q13a, sample size = 400

Third, when we segment cloud adoption by organization size, we see the adoption of cloud native is similar despite company size (Figure 2). This speaks to the benefits of cloud native for organizations of all sizes, not just bigger operations. Cloud service providers have clearly made cloud native accessible for organizations of all sizes.

And finally, Europe (92%) and the Americas (89%) lead in the adoption of cloud native techniques (reporting some, much, or nearly all of their AD&amp;D is cloud native) but Asia Pacific, which was

## FIGURE 3 CLOUD NATIVE ADOPTION BY GEOGRAPHIC LOCATION

Extent organization has adopted cloud native techniques by Geographic location of headquarters

<!-- image -->

2024 CNCF Annual Survey, Q15a x Q12a, sample size = 405

significantly trailing last year (40%) has closed the gap this year, with 84% of companies reporting some, much, or nearly all of their AD&amp;D is cloud native (Figure 3).

## Popular and Plentiful, Cloud Usage Stays Strong

When it comes to processing power, organizations are choosing amongst a literal embarrassment of riches, as our survey clearly shows. When considering what combination of data centers and public clouds to employ, survey respondents were evenly split between on-prem data centers and public clouds (both 59%), with both skewing heavily toward self-managed. A CSP-managed public cloud was the next most popular choice at 46%, followed by an on-prem private cloud (40%) and a hybrid cloud at 39%. Public clouds continue to take on the characteristics of data centers,

## FIGURE 4 CLOUD VS. DATA CENTER USAGE

Which of the following combinations of datacenter and cloud environments does your organization use? (one response per row)

1

<!-- image -->

%

6

%

2024 CNCF Annual Survey, Q16, sample size = 409, shown to end-users, system integrators, and consultants based on Q9 and Q10, DKNS responses excluded from the analysis offering multiple environments to cater to availability and risk mitigation requirements, as well as the opportunity for selfmanagement. And public clouds that are CSP-managed also have considerable multi-env adoption (46%).

Hybrid clouds have also achieved significant multi-environment adoption (39%), and they are particularly appealing for organizations planning for the future. Fully 11% of survey takers are planning to use hybrid clouds, which is between two and three times higher than other planned cloud usage and ten times higher planned data center usage (Figure 4).

1

%

1

%

A full 37% of respondents use 2 cloud service providers, up from 34% in 2023, and 26% use 3, an increase of 3% from last year,

## FIGURE 5 NUMBER OF CSPS IN USE

How many unique cloud service providers (CSPs) does your organization use? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q17, sample size = 359, shown to end-users, SIs or consultants based on Q9 and Q10, AND those using public cloud or community cloud in Q16, DKNS responses excluded from the analysis, upper limit on '10 or more' response set to 15.

2023 CNCF Annual Survey, Q17, sample size = 522, organizations whose primary revenue is not from offering cloud native technologies or services, DKNS responses excluded from the analysis, upper limit on '10 or more' response set at 15.

which may reflect a growing confidence in the cloud experience (Figure 5).

The average number of machines that companies have in their datacenters (traditional or cloud) increased by 6.6% in 2024 from 1,190 in 2023 to 1,269 in 2024 (Figure 6).

## FIGURE 6 NUMBER OF MACHINES IN THE DATACENTER

On average, how many machines are in your datacenter(s)? (select one)

11%

<!-- image -->

2024 CNCF Annual Survey, Q19, sample size = 408, shown to end-users, SIs or consultants based on Q9 and Q10, DKNS responses excluded from the analysis, upper limit on '5,000 or more' response set to 10,000

2023 CNCF Annual Survey, Q18, sample size = 522, organizations whose primary revenue is not from offering cloud native technologies or services,

DKNS responses excluded from the analysis, upper limit on '5,000 or more' response set to 10,000

20%

## FIGURE 7

## CONTAINER USAGE

How are containers used within your organization? (select one)

1

%

<!-- image -->

1

1

%

2024 CNCF Annual Survey, Q20, sample size = 408, shown to end-users, SIs or consultants based on Q9 and Q10, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q19, sample size = 522, organizations whose primary revenue is not from offering cloud native technologies or services, DKNS responses excluded from the analysis

## Container Use Grows, Powers Production

Unsurprisingly, containers continued to be a production tool of choice in 2024. In fact, 91% of organizations are using containers in production (used for most or for a few apps) compared to just 80% in 2023, which is a 14% growth rate year over year.

6

%

6

%

And the average number of containers used by organizations also grew in 2024 (by 27%) to 2,341, up from 1,140 in 2023.

Much like cloud native computing, most of the growth in containers (29.5%) is occurring in the segment where containers are used for most or all production apps (Figure 7).

All that said, containers are not without their challenges, although the types of challenges have changed. In 2023, survey respondents pointed to security (42%) and complexity (38%) as the biggest problem areas with containers. But in 2024, almost half (46%) said

## FIGURE 8 THE CHALLENGES OF CONTAINER USER

What are your challenges in using / deploying containers? (select all that apply)

<!-- image -->

2024 CNCF Annual Survey, Q22, sample size = 373, Valid Cases = 373, Total Mentions = 1,425, shown to end-users, SIs or consultants based on Q9 and Q10, AND those who use or test containers in Q20, DKNS responses excluded from the analysis

2023 CNCF Annual Survey, Q21, sample size = 477, valid cases = 477, total mentions = 1,720, organizations whose primary revenue is not from offering cloud native technologies or services, DKNS response excluded from the analysis cultural challenges with the development team were the biggest problem with using containers, followed by CI/CD (40%) and lack of training (38%). Security was next at 37%, still a challenge, but less so than in 2023 (Figure 8).

When cloud native computing was maturing, technical issues like security, networking, storage, and observability were major pain points. Today, though, more seasoned cloud native practices have helped make technical challenges more manageable, meaning organizations can focus their attention on culture and process shifts. Whether it's a move to platform engineering or GitOps, or a transition from a monolithic architecture to a microservices one, these culture-change efforts are the logical, if tricky, next steps in the cloud native evolution, as the survey results reflect.

To make the point further, survey respondents with a moderate amount of experience in cloud native and containers - those who identified as some AD&amp;D is cloud native - were overwhelmingly more likely to point to cultural challenges with using/deploying containers than any other group (Figure 9). In fact 55% said cultural challenges with the development team were their biggest challenge (9% more than the average response) and 51% pointed to lack of training (13% more than the average response).

## FIGURE 9 CONTAINER USE CHALLENGES BY CLOUD NATIVE MATURITY LEVEL

<!-- image -->

2024 CNCF Annual Survey, Q22 x Q15a, sample size = 372, Valid Cases = 372, Total Mentions = 1,421, DKNS responses excluded from the analysis

## Kubernetes Reach Continues to Expand

It's a Kubernetes world and we just live in it. Production use of Kubernetes hit 80% in 2024, up from 66% in 2023 and reflecting an annual growth rate of 20.7%. But almost as impressive: production use + those piloting or actively evaluating Kubernetes = 93% of respondents, meaning it's going to be hard to find an organization not using K8s at some level (Figure 10).

## FIGURE 10 KUBERNETES USAGE

Does your organization use Kubernetes? (select one)

6

%

<!-- image -->

1

9

%

2024 CNCF Annual Survey, Q23, sample size = 373, shown to end-users, SIs or consultants based on Q9 and Q10, AND those who use or test containers in Q20, DKNS responses excluded form the analysis 2023 CNCF Annual Survey, Q22, sample size = 477, showing organizations whose primary revenue is not from offering cloud native technologies or services, DKNS responses excluded form the analysis

Also dominating this year: Namespaces and Helm. Namespaces have rapidly emerged in 2024 over clusters and labels as the preferred approach for separating applications within cloud native and containerized environments, particularly in Kubernetes. Namespaces jumped 16% year over year to 88%, with clusters up just 2% to 65% and labels down 3% to 31% (Figure 11).

## FIGURE 11 HOW APPLICATIONS ARE SEPARATED

How do you separate your applications? (select all that apply)

<!-- image -->

2024 CNCF Annual Survey, Q26, sample size = 345, Valid Cases = 345, Total Mentions = 641, shown to end-users, SIs or consultants based on Q9 and Q10, AND those who use or test containers in Q20, AND use or test Kubernetes in Q23, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q25, sample size = 397, valid cases = 397, total mentions = 689, organizations whose primary revenue is not from offering cloud native technologies or services, DKNS responses excluded from the analysis

Meanwhile Helm also ran away with its lead as the preferred package manager for Kubernetes, jumping from 56% in 2023 to 75% in 2024, with an annual growth of 33.9% (Figure 12).

## FIGURE 12 THE PREFERRED METHOD FOR PACKAGING KUBERNETES APPLICATIONS

What is your preferred method for packaging Kubernetes applications? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q27, Sample Size = 320, shown to end-users, SIs or consultants based on Q9 and Q10, AND those who use or test containers in Q20, AND use or test Kubernetes in Q23, DKNS responses excluded from the analysis

2023 CNCF Annual Survey, Q26, Sample Size = 397, organizations whose primary revenue is not from offering cloud native technologies or services, DKNS responses excluded from the analysis 2022 CNCF Annual Survey, Q20, Sample Size = 1,476 (not shown but in the underlying data)

## AI on Kubernetes: Still Getting Started

Just shy of half of those surveyed (48%) are not running AI/ML workloads on Kubernetes at this point, but early adopters are trying a variety of jobs including:

<!-- image -->

1

%

1

%

6

%

2024 CNCF Annual Survey, Q32, sample size = 689

6

%

6

%

1

6

%

9

%

6

%

## CNCF Project Snapshots

Kubernetes is of course on the top of the graduated project list with 85% using it and 9% evaluating, but of the other top 9 graduated projects, five are strongly tied to K8s including Helm, etcd, CoreDNS, Cert Manager and Argo. The others at the top of the list address monitoring and alerting (Prometheus), container runtime

## FIGURE 13 CNCF GRADUATED PROJECTS IN USE OR IN EVALUATION

Which of these graduated CNCF projects is your organization using in production or evaluating? (select one response per row)

9

%

<!-- image -->

1

%

1

%

1

%

9

%

9

%

1

9

%

(containerd), logging (Fluentd), and general purpose service mesh (Istio).

Projects with a low rate of production use (less than 10%) typically have a high evaluation ratio (100% to 400%) suggesting that they are being carefully evaluated by a significant number of organizations (Figure 13).

1

%

1

%

Incubating projects tell a very different - and far more technologically diverse - story. There's a large focus on workload management (Operator Framework, Kubeflow, Knative) as well as

Security (Keycloak, Kyverno). One common pattern that's clear is there's a continued push to improve developer and user experience (Backstage, Thanos). (Figure 14).

## FIGURE 14 CNCF INCUBATED PROJECTS IN USE OR IN EVALUATION

Which of these incubating CNCF projects is your organization using in production or evaluating?

<!-- image -->

2024 CNCF Annual Survey, Q33, Sample Size = 689

Survey respondents reported three top challenges when it came to using CNCF projects in production: the risk the project could become inactive (46%), a 9% increase over 2023, too complex to understand or run (46%), up 13% year over year, and the lack of supporting documentation (45%), a 5% increase. That said, fears about security vulnerabilities dropped 7% from 2023 to 2024,

## FIGURE 15 CHALLENGES WHEN USING CNCF PROJECTS IN PRODUCTION

What challenges have you experienced (or expect to experience) while using CNCF projects in production? (select all that apply)

<!-- image -->

2024 CNCF Annual Survey, Q34, Sample Size = 552, Valid Cases = 552, Total Mentions = 1,481, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q32, Sample Size = 823, Valid Cases = 823, Total Mentions = 2,083, DKNS responses excluded from the analysis worries about bugs in code dropped 6%, and the concern that management doesn't see value in open source dropped 5% (Figure 15). As cloud native processes become more standard, the concerns about the technology and the implementations will naturally change and this is reflected in the survey's changing responses.

## Security and Compliance

Survey respondents reported significant progress in making their software more secure across nearly every measure we asked about compared to where they were in 2023. Fully 60% check that a project has an active community, up from 49% in 2023, 57% use a tool to search for open source packages with known vulnerabilities, up from 51%, 52% look at the frequency of releases and commits, up 10% YOY, 37% look at repo ratings or package download stats, up 8%, and 33% use the information in the registration or package manager, up from 27% last year. The major outlier to this trend was using tools to examine the source code, which stayed steady at 55% in 2023 and 2024. And one last piece of relatively reassuring news: just 3% of survey takers said they don't do anything to check to see if their external software is secure (Figure 16).

## FIGURE 16 METHODS FOR EVALUATING THE SECURITY OF EXTERNAL SOFTWARE

How do you currently evaluate the security of external software that you bring in as dependencies? (select all that apply)

1

6

%

<!-- image -->

1

%

2024 CNCF Annual Survey, Q36, sample size = 689, Valid Cases = 689, Total Mentions = 2,286, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q34, sample size = 988, valid cases = 988, total mentions = 3,054, DKNS responses excluded from the analysis

## Web Assembly

Web Assembly adoption in mainstream development remains stalled in 2024, but its potential remains strong in areas like serverless, cloud computing and performance-critical applications.

Roughly 34% of respondents report some experience with Web Assembly (Figure 17). For it to see broader adoption, improvements in tooling, language support, and integration with existing developer workflows are necessary.

## FIGURE 17 WEBASSEMBLY APPLICATION DEPLOYMENT STATUS

Have you or your organization ever deployed an application using WebAssembly? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q39, Sample Size = 403, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q37, Sample Size = 988, DKNS responses excluded from the analysis 2022 CNCF Annual Survey, Q29, Sample Size = 1,694 (not shown but in the underlying data)

## FIGURE 18

REASONS WHY WEBASSEMBLY ADOPTION HAS BEEN SLOW

Why haven't you and/or your organization adopted WebAssembly? (select all that apply)

<!-- image -->

2024

2023

2024 CNCF Annual survey, Q40, Sample Size = 270, Valid Cases = 270, Total Mentions = 381, DKNS responses excluded from the analysis, shown to respondents whose organization hasn't adopted WASM in Q39

2023 CNCF Annual Survey, Q38, Sample Size = 348, Valid Cases = 348, total mentions = 485, DKNS responses excluded from the analysis, showing organizations or respondents that have not used WebAssembly

Survey respondents said their primary reasons for not using WASM include a lack of applicability (48%) and implementation complexity (23%) (Figure 18).

52%

## The Technology Roadmap Snapshot

## Service Mesh

Service mesh seems to be of somewhat less interest to organizations than in the past. It is currently in production for a few or most applications in roughly 42% of respondent organizations, down from 50% in 2023, and 50% less companies are planning to give it a test run YOY with 100% more 'no near term plans to use.' (Figure 19) There are a number of possible

## FIGURE 19 HOW SERVICE MESH IS USED

How does your organization use service mesh? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q47, sample size = 689, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q45, sample size = 988, DKNS responses excluded from the analysis explanations for this including concerns over complexity, cost, and performance. Many organizations found that implementing a service mesh introduced significant operational overhead, making it challenging to manage and maintain. Service mesh requires specialized expertise to maintain, can lead to heavy performance overhead causing latency and throughput issues, and other most cost-effective and lighter weight solutions (like Kubernetes) have sprung up.

31%

## FIGURE 20

## HOW CONTAINERS RUN STATEFUL APPLICATIONS

How does your organization use containers to run stateful applications? (select one)

9

%

<!-- image -->

1

1

%

2024 CNCF Annual Survey, Q48, sample size = 689, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q46, sample size = 988, DKNS responses excluded from the analysis

## Containers to manage stateful applications

In 2024, 74% of organizations reported using containers to manage stateful applications, up 10% from 2023 (Figure 20). Companies just beginning to use containers showed the biggest

6

%

increase (22%), though even organizations using containers for most applications had an almost 9% jump. But adoption of this may be plateauing: the number of companies planning and/or evaluating future use of containers to manage stateful applications was down 44% from 2023.

## FIGURE 21

## HOW ORGANIZATIONS USE SERVERLESS ARCHITECTURES

How does your organization use serverless architecture and/or functions as a service solutions? (select one)

1

%

<!-- image -->

9

%

2024 CNCF Annual Survey, Q49, sample size = 689, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q47, sample size = 988, DKNS responses excluded from the analysis

## Serverless and FaaS

In 2024 the greatest interest in serverless (44%) was in production for a few applications, which was an increase of 6% over 2023 (Figure 21). Other areas, including used in production for most or

1

9

%

all applications, showed minor decline (11% compared with 14% in the previous year). Future interest in serverless also seems to be weak: piloting/testing or planning to use both showed YOY declines, at the same time that plans to not use serverless in the near term increased to 23% from 19% in 2023.

## Infrastructure Platforms

While the tepid adoption of serverless seen in Figure 21 is disconcerting, interest in hosted or installable platforms for serverless shows a mix of perspectives on adoption.The percent of companies with no hosted or installable platforms for serverless increased significantly in 2024, with hosted platforms jumping from 8% in 2023 to 26% in 2024 and installable platforms growing from 13% in 2023 to 26% in 2024 (Figure 22). At the same time, the percentage of companies with four or more hosted or installable platforms for serverless also grew to 23% in 2024, up 8% from the previous year.

Obviously these metrics reflect at least some level of market ambivalence. The polarization in serverless computing adoption in 2024 - with some organizations abandoning serverless altogether and others doubling down by adopting multiple platforms reflects a mix of strategic realignments, technological maturity, and market dynamics.

## FIGURE 22 THE NUMBER OF HOSTED AND/OR INSTALLABLE PLATFORMS IN USE TO RUN SERVERLESS WORKLOADS

How many hosted and/or installable platforms is your organization using or evaluating to run serverless workloads?

1

9

%

<!-- image -->

1

2024 CNCF Annual Survey, Q50, sample size = 55, shown to those who plan to use serverless architecture in Q49, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q48, sample size = 117, DKNS responses excluded from the analysis

1

9

%

1

6

%

## FIGURE 23

## PLANS FOR HOSTED AND/OR INSTALLABLE PLATFORMS WITHIN THE NEXT YEAR

How many hosted and/or installable platforms does your organization expect to run within the next year?

<!-- image -->

2024 CNCF Annual Survey, Q51, sample size = 389, shown to those use serverless architecture in Q49, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q49, sample size = 624, DKNS responses excluded from the analysis

To add to the mixed messaging, the outlook in serverless adoption is upbeat, at least when it comes to organizational plans for 2025. The percentage of companies with no hosted or installable platforms for serverless is expected to drop to 9% in 2025 from its current level of 26% in 2024, and those without installable platforms will see a similar pattern, decreasing from 26% in 2024 to 14% in 2025 (Figure 23).

And the growth is even more impressive among organizations already supporting hosted or installable platforms: the percentage of those with four or more hosted platforms is projected to increase from 23% in 2024 to 56% in 2025 and the percentage of those with more or more installable is expected to increase from 21% in 2024 to 51% in 2025.

## CI/CD: An Increasingly Mature Cloud Native Development Process

Continuous Integration and Continuous Delivery (or Deployment) seems to be the methodology of choice for most organizations, with 60% reporting it in use for most or all applications. CI/CD use

## FIGURE 24 HOW ORGANIZATIONS USE CI/CD TOOLS TO MANAGE PIPELINES

What tools does your organization currently use to manage its CI/CD pipeline? (select all that apply) (top 15 products/projects shown)

<!-- image -->

2024 CNCF Annual Survey, Q56, sample size = 689, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q54, sample size = 988, DKNS responses excluded from the analysis in production for most or all applications had a hearty 31% growth rate in 2024, increasing from 46% in 2023 to 60% this year (Figure 24).

## CI/CD tools

The enthusiasm for CI/CD has of course carried over to the tools used to manage the pipelines. 2024 saw significant growth across all of the leading tools to manage the CI/CD pipeline (Figure 25):

<!-- image -->

1

6

%

1

6

%

## Code check-ins for the win

In a continuing sign of maturity across the cloud native landscape, the percentage of organizations who check in code multiple times per day increased dramatically in 2024 to 71%, up from 52% in 2023 (Figure 26). Not surprisingly that came at the expense of daily, weekly and monthly code check-ins, all of which saw drastic declines.

## FIGURE 26

## FREQUENCY OF CODE CHECK-INS

How often does your organization check in code? (select one)

9

<!-- image -->

%

2024 CNCF Annual Survey, Q52, sample size = 689, DKNS and 'Not applicable' excluded from the analysis

2023 CNCF Annual Survey, Q50, sample size = 988, DKNS and 'Not applicable' excluded from the analysis

## Release cycles

Organizations are releasing code faster than ever before: 29% are pushing it out the door multiple times a day, up from 23% in 2023 (Figure 27). Not unlike code check-ins, it appears that companies just went straight to multiple times a day because the daily, weekly, and monthly release cycles have all decreased in frequency YOY.

## FIGURE 27

## FREQUENCY OF RELEASE CYCLES

How often are your organization's release cycles? (select one)

9

%

<!-- image -->

6

%

2024 CNCF Annual Survey, Q53, sample size = 689, DKNS and 'Not applicable' excluded from the analysis

2023 CNCF Annual Survey, Q51, sample size = 988, DKNS and 'Not applicable' excluded from the analysis

## FIGURE 28

## FREQUENCY OF RELEASE CYCLES BY CLOUD NATIVE MATURITY LEVELS

How often are your organization's release cycles? (select one) by Extent organization has adopted cloud native techniques

<!-- image -->

2024 CNCF Annual Survey, Q53, sample size = 405

And the more mature the cloud native practice, the more often code is released. Fully 37% of companies with much or all of their AD&amp;D cloud native release multiple times a day (Figure 28). Organizations where only some of their AD&amp;D is cloud native are more likely to release weekly (28%), and those new to cloud native or that have not started are more likely to release code monthly (24%).

## Automated releases

In 2024 38% of survey takers said 80% to 100% of their releases are automated, a 10% increase over 2023 (Figure 29). Overall, the organizational average percent of automated releases increased slightly from 56.5% in 2023 to 59.2% in 2024.

## FIGURE 29 PERCENTAGE OF AUTOMATED RELEASE CYCLES

What percentage of your organization's releases are automated? (select one)

<!-- image -->

2024

2023

2024 CNCF Annual Survey, Q54, sample size = 689, DKNS and 'Not applicable' excluded from the analysis 2023 CNCF Annual Survey, Q52, sample size = 988, DKNS and 'Not applicable' excluded from the analysis

28%

38%

## FIGURE 30

## A LOOK AT GITOPS PRACTICE AND TOOL ADOPTION

To what extent has your organization adopted practices and tools that adhere to GitOps principles? (select one)

<!-- image -->

2024 CNCF Annual Survey, Q55, sample size = 689, DKNS responses excluded from the analysis 2023 CNCF Annual Survey, Q53, sample size = 988, DKNS responses excluded from the analysis

## GitOps

The infrastructure automation practice GitOps had a good year in 2024. All told, 77% of respondents said some, much, or nearly all of their deployment practices and tools adhere to GitOps principles (Figure 30).

## Methodology

This study is based on a web survey conducted by Linux Foundation Research and its partners during November and December 2024. The survey's goal was to understand developer perspectives on containers, Kubernetes, and other cloud native adoption trends. In this section, we present the study methodology and context regarding how we analyzed the data followed by the demographics of the respondents.

From a research perspective, it was important to eliminate any perception of sample bias and ensure high data quality. We handled the elimination of sample bias by sourcing our usable sample from Linux Foundation subscribers, members, partner communities, and social media. We addressed data quality through extensive prescreening, survey screening questions, and data quality checks to ensure that respondents had sufficient professional experience to answer questions accurately on behalf of the organization they worked for.

We collected survey data from industry-specific companies, IT vendors and service providers, nonprofit, academic, and government organizations. Respondents spanned many vertical industries and companies of all sizes, and we collected data from several geographies, including the Americas, Europe, Asia-Pacific, and the Middle East and Africa.

The 2024 CNCF Annual Survey comprised 61 questions that addressed screening, respondent demographics, cloud native computing, containers, Kubernetes, CNCF projects, and six other topical areas. The high-level design of the survey is shown in Table 1.

## TABLE 1 SURVEY DESIGN

| Section        | Questions   | Question categorles                                   | Whoanswers the questions                       |
|----------------|-------------|-------------------------------------------------------|------------------------------------------------|
| Demographics   | Q1 - Q14    | Tell us about yourself &the organization you work for | All respondents except unemployed students     |
| Cloud Native   | Q15 - Q19   | Cloud and cloud native computing at your organization | For orgs who are end-users, SIs or consultants |
| Containers     | Q20 - Q22   | Container use                                         | For orgs who are end-users, SIs or consultants |
| Kubernetes     | Q23 - Q31   | Kubernetes use, follow-up,& autoscaling               | For orgs who are end-users, SIs or consultants |
| CNCF Projects  | Q32 - Q34   | CNCF projects                                         | All respondents                                |
| Security       | Q35 - Q36   | Security and compliance                               | All respondents                                |
| Observability  | Q37 - Q38   | Observability                                         | All respondents                                |
| WebAssembly    | Q39 - Q45   | WebAssembly                                           | All respondents                                |
| Tech Roadmap   | Q46 - Q49   | Technology roadmap                                    | All respondents                                |
| Infrastructure | Q50 - Q51   | Infrastructure platforms                              | All respondents                                |
| CI/CD          | Q52 - Q56   | Code, release cycles, and automation                  | All respondents                                |
| Students only  | Q56 - Q61   | Student only technology questions                     | Students only                                  |

Survey screening involves the use of three variables to select respondents who have sufficient experience that will allow them to answer some or all questions in the survey.

- Must be familiar with cloud native technologies
- Must identify as a human
- Must be employed full-time or part-time

A total of 689 respondents completed the survey. The margin of error for this sample size was +/- 3.2% at a 90% confidence level and +/- 3.8% at a 95% confidence level. The data was primarily segmented by geographic region, company size, type of organization, and extent of organizational adoption of cloud native techniques.

Although respondents were required to answer nearly all questions in the survey, a provision was made when a respondent was unable to answer a question. This is accomplished by adding a 'Don't know or not sure' (DKNS) response to the list of responses for every question. However, this creates a variety of analytical challenges.

One approach was to treat a DKNS just like any other response so that the percentage of respondents that answered the DKNS is known. The advantage of this approach is that it shows the exact distribution of data collected. The challenge with this approach is that it can distort the distribution of valid responses, i.e., responses where respondents could answer the question.

Some of the analyses in this report exclude DKNS responses. This is done when comparing data year-over-year because the sample size and percentage of DKNS responses always varies from year to year. Excluding DKNS responses enables us to normalize the data so that year-over-year comparisons and growth rates can be accurately calculated.

The percentage values in this report may not total to exactly 100% due to rounding.

## Data�World access

LF Research makes each of its empirical project datasets and this 2024 CNCF Annual Survey available on Data.World. Included in this dataset are the survey instrument, raw survey data, screening and filtering criteria, and frequency charts for each question in the survey. LF research datasets, including this project, can be found at data.world/thelinuxfoundation. Access to Linux Foundation datasets is free but does require you to create a data.world account.

## Respondent demographics

These demographics provide you with a profile of the 2024 CNCF Annual Survey respondents. All of the demographics in Figures D1 and D2 have been regrouped to facilitate a more insightful analysis. For the original source data and study frequencies, please see the data.world access described above.

<!-- image -->

## FIGURE D2

DEMOGRAPHICS II

How many years of professional experience in IT (Information Technology) do you have? (select one)

<!-- image -->

2024 CNCF Annual Survey, sample size = 689

Which option best describes the organization you work for? (select one)

<!-- image -->

2024 CNCF Annual Survey, sample size = 689

About how much of your organization's main source of revenue is derived from providing cloud native technologies, products, or services? (select one)

<!-- image -->

2024 CNCF Annual Survey, sample size = 689

## About the authors

Valerie Silverthorne is a longtime writer and editor in the technology space with SME in AppDev (Agile, DevOps, containers, software testing, platform engineering, observability, APIs) as well as healthcare technology, AI, IoT and HR software. She is a multiple ASBPE Award winner. Previously she's covered business, trade, technology, real estate and lifestyle trends. Valerie was an award-winning Business Writer for The San Jose Mercury News and was a Forbes Magazine top '30 under 30' journalist. She was the Editor of ZDNet.com and PC Week/Inside, and a Senior Executive Editor of PC Week and Electronic Business.

Stephen Hendrick is vice president of research at the Linux Foundation, where he is the principal investigator on a variety of research projects core to the Linux Foundation's understanding of

## Acknowledgments

We thank all the survey participants for sharing their stories, insights, and experiences. Special thanks to peer reviewers and colleagues including:

- Katie Greenley
- Jeffrey Sica
- Jorge Castro
- Anna Hermansen
- Christina Oliviero

how OSS is an engine of innovation for producers and consumers of IT. Steve specializes in primary research techniques developed over 30 years as a software industry analyst. Steve is a subjectmatter expert in application development and deployment topics, including DevOps, application management, and decision analytics. Steve brings experience in a variety of quantitative and qualitative research techniques that enable deep insight into market dynamics and has pioneered research across many application development and deployment domains. Steve has authored over 1,000 publications and provided market guidance through syndicated research and custom consulting to the world's leading software vendors and high-profile start-ups.

## Endnotes

## 1 https://data.world/thelinuxfoundation

<!-- image -->

<!-- image -->

Cloud native computing leverages an open source software stack to deploy applications as microservices, where each component is packaged into its own container and orchestrated dynamically to optimize resource utilization. The Cloud Native Computing Foundation (CNCF) hosts key projects within the cloud native ecosystem, including Kubernetes, Envoy, Prometheus, and many others. CNCF serves as a neutral hub for collaboration, bringing together leading developers, end users, and vendors-from the world's largest public cloud providers and enterprise software companies to innovative startups. As part of The Linux Foundation, a nonprofit organization, CNCF fosters the growth and adoption of cloud-native technologies across industries. For more information, visit www.cncf.io.

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

https://twitter.com/cloudnativefdn https://www.facebook.com/ CloudNativeComputingFoundation/

https://www.linkedin.com/company/ cloud-native-computing-foundation/

https://www.youtube.com/c/cloudnativefdn

<!-- image -->

https://github.com/cncf

Copyright © 2025 The Linux Foundation

<!-- image -->

This report is licensed under the Creative Commons Attribution-NoDerivatives 4.0 International Public License .

To reference this work, please cite as follows: Valerie Silverthorne and Stephen Hendrick, 'Cloud Native 2024: Approaching a Decade of Code, Cloud, and Change,' The Linux Foundation, March 2025.

<!-- image -->

Founded in 2021, Linux Foundation Research explores the growing scale of open source collaboration, providing insight into emerging technology trends, best practices, and the global impact of open source projects. Through leveraging project databases and networks, and a commitment to best practices in quantitative and qualitative methodologies, Linux Foundation Research is creating the go-to library for open source insights for the benefit of organizations the world over.

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

twitter.com/linuxfoundation facebook.com/TheLinuxFoundation

linkedin.com/company/the-linux-foundation youtube.com/user/TheLinuxFoundation

github.com/LF-Engineering