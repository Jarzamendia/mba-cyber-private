# Justificativa - Rascunho

## Objetivo desta seção
A justificativa deve convencer o leitor (e o orientador) de que este estudo é **importante e necessário**. Deve responder: "por que este tema merece ser pesquisado?"

Ao final, inclua também a **hipótese** do trabalho.

## Dicas para rascunhar

1. **Comece pelo problema real** - Descreva o cenário atual: a maioria das organizações não realiza verificações de segurança em imagens Docker, ou faz apenas após o deploy. Traga dados se possível (relatórios Snyk, Sonatype, Gartner).

2. **Mostre que o risco é crescente** - Cite ataques reais de cadeia de fornecimento (supply chain) que causaram impacto: event-stream (2018), ua-parser-js (2021), colors.js (2022). Explique que imagens Docker herdam essas dependências vulneráveis.

3. **Aponte a limitação humana** - Argumente que processos manuais de revisão de segurança são falhos: humanos cansam, ficam entediados, pulam etapas. A automação resolve isso.

4. **Apresente a oportunidade** - Ferramentas open-source (Trivy, Grype, Clair) e plataformas de CI/CD modernas tornam viável automatizar verificações sem custo adicional e sem depender de intervenção humana.

5. **Feche com a hipótese** - Uma afirmação testável. Exemplo de direção: "A integração de scanners automatizados no ciclo de desenvolvimento (shift-left) permite detectar e bloquear vulnerabilidades críticas, incluindo as de cadeia de fornecimento, antes que alcancem produção."

## Dicas de escrita
- Use linguagem impessoal (evite "eu acho", "nós queremos")
- Cada parágrafo = um argumento
- Conecte os parágrafos com uma lógica de "problema → risco → limitação → solução → hipótese"
- Cite fontes sempre que trouxer dados ou afirmações (ABNT)
- 3 a 5 parágrafos é suficiente para o pré-projeto

---

## Justificativa

O rápido crescimento do ecossistema de software — tanto comercial quanto de código aberto — ampliou de forma sem precedentes a escala e a complexidade das cadeias de suprimentos de software utilizadas diariamente por equipes de engenharia no mundo todo (SONATYPE, 2026). Paralelamente, a adoção de containers Docker em produção consolidou-se como padrão da indústria (CNCF, 2024), tornando a segurança das imagens um tema central tanto na comunidade acadêmica quanto na prática profissional em cibersegurança e DevSecOps.

A relevância do tema é reforçada por um cenário de ameaças em expansão. Casos como o backdoor do *xz utils* (LINS et al., 2024), o comprometimento do *event-stream* (ARVANITIS et al., 2022) e a vulnerabilidade do *Log4j* (HIESGEN et al., 2022) demonstram que atores mal-intencionados exploram a cadeia de suprimentos para inserir códigos maliciosos em componentes amplamente utilizados. Com o uso pervasivo de bibliotecas de terceiros em todo o ciclo de desenvolvimento (LADISA et al., 2023), garantir a integridade das dependências tornou-se um desafio contínuo para organizações de qualquer porte.

Em resposta, ferramentas de escaneamento de vulnerabilidades como Trivy, Grype e Clair vêm sendo incorporadas às abordagens de *shift-left security*, atuando em esteiras de integração contínua para detectar vulnerabilidades antes da publicação em produção (ANASURI, 2024). Contudo, estudos comparativos evidenciam divergências relevantes entre essas ferramentas (BOLES et al., 2024; JAVED; TOOR, 2021; PARDO, 2024), e a literatura ainda carece de uma sistematização clara dos critérios que deveriam orientar a escolha de cada uma delas de acordo com o perfil organizacional — lacuna reconhecida tanto em dissertações recentes (PARDO, 2024; BHARDWAJ, 2023) quanto em revisões da área (WILLIAMS et al., 2025).

A revisão bibliográfica proposta contribuirá para o preenchimento dessa lacuna ao consolidar, em um único corpus analítico, os resultados empíricos reportados pela literatura. Do ponto de vista acadêmico, o trabalho poderá servir de base para novas pesquisas que investiguem de forma empírica a eficácia dos scanners em contextos específicos. Do ponto de vista prático, oferece aos profissionais de cibersegurança e DevSecOps um referencial agregado que pode subsidiar decisões de adoção de ferramentas em pipelines de CI/CD.

A revisão bibliográfica é considerada método adequado para este estudo por permitir a síntese crítica do conhecimento produzido sobre um tema em rápida evolução e por existir **material suficiente** para análise: estudos comparativos empíricos entre Trivy, Grype e Clair (BOLES et al., 2024; PARDO, 2024; BHARDWAJ, 2023; JAVED; TOOR, 2021), taxonomias e revisões sobre ataques à cadeia de suprimentos de software (LADISA et al., 2023; GOKKAYA; ANIELLO; HALAK, 2023; WILLIAMS; HAMER; ZAHAN, 2024) e publicações sobre shift-left security e práticas de DevSecOps (ANASURI, 2024; JAIN et al., 2021) oferecem base consistente para a análise pretendida.

**Hipótese:** A literatura científica publicada entre 2020 e 2026 oferece evidências suficientes para caracterizar divergências de desempenho, cobertura e integração entre as principais ferramentas de escaneamento de vulnerabilidades em imagens Docker, permitindo consolidar critérios que orientem a escolha dessas ferramentas conforme o perfil organizacional no contexto de shift-left security.