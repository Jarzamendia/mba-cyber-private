# Justificativa - Rascunho

<!--
CONFERIR / MODIFICAR antes de entregar:
- §5 ("material suficiente"): a lista de papers é a resposta direta ao questionamento do orientador sobre bibliografia para tema específico. Confirmar no retorno.
- Hipótese (final do arquivo): reescrita para alinhar ao escopo de revisão bibliográfica pura (sem testes práticos). Confirmar texto.
- SOBREPOSIÇÃO COM A INTRODUÇÃO (2026-04-16): §1, §2 e §3 repetem dados, casos e argumentos já apresentados na Introdução. Comentários inline abaixo sugerem reescritas que trocam o registro "descritivo" (o que acontece no mundo) pelo registro "meta-argumentativo" (por que a literatura precisa deste estudo). §4 e §5 são específicos da justificativa — mantidos como estão.
-->

<!--
A seção de justificativa do seu trabalho acadêmico deverá apresentar:
1 - Uma explicação por que o tema é importante no contexto acadêmico, científico ou social;
2 - A justificativa da escolha do tema com base em sua relevância atual ou em lacunas identificadas na literatura;
3 - Identificação de questões ou problemas que ainda não foram suficientemente explorados na área de estudo;
4 - Descrição do impacto que a revisão bibliográfica pode gerar, como servir de base para novas pesquisas, propor insights para práticas ou contribuir para debates acadêmicos;
5 - Demonstrar que a revisão bibliográfica é um método adequado para abordar o tema e que há material suficiente disponível para a análise.
 -->

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

O crescimento do ecossistema de software, tanto comercial quanto de código aberto, aumentou de forma sem precedentes tanto em escala quanto em complexidade. A segurança das cadeias de suprimentos de software utilizadas por equipes de engenharia no mundo todo (SONATYPE, 2026) se tornou um tema central tanto na comunidade acadêmica quanto na prática profissional em cibersegurança e DevSecOps.

Incidentes de grande repercussão na última década deram origem a uma produção acadêmica substancial sobre ataques à cadeia de suprimentos de software, que vai desde taxonomias formais (LADISA et al., 2023) até revisões de literatura (GOKKAYA; ANIELLO; HALAK, 2023; WILLIAMS; HAMER; ZAHAN, 2024). Esses incidentes e seus trabalhos relacionados, demonstram que equipes de engenharia de software e segurança precisam lidar com esse tipo de vulnerabilidade de forma diaria e a literatura acadêmica tem se debruçado sobre o tema para entender melhor o problema e propor soluções.

Em resposta a esses desafios, ferramentas de escaneamento de vulnerabilidades como Trivy, Grype e Clair vêm sendo incorporadas às abordagens de shift-left security, atuando em esteiras de integração contínua para detectar vulnerabilidades antes da publicação em produção (ANASURI, 2024). Contudo estudos comparativos mostram divergências relevantes entre essas ferramentas (BOLES et al., 2024; JAVED; TOOR, 2021; PARDO, 2024), e a literatura ainda carece de uma sistematização clara dos critérios que deveriam orientar a escolha de cada uma delas de acordo com o perfil organizacional. Esta lacuna é reconhecida tanto em dissertações recentes (PARDO, 2024; BHARDWAJ, 2023) quanto em revisões da área (WILLIAMS et al., 2025).


Esta revisão bibliográfica contribuirá para o preenchimento dessa lacuna ao consolidar os resultados reportados pela literatura. Do ponto de vista acadêmico, o trabalho poderá servir de base para novas pesquisas que investiguem de forma empírica a eficácia dos scanners em contextos específicos. Do ponto de vista prático, oferece aos profissionais de engenharia e cibersegurança um referencial que pode auxiliar decisões de adoção de ferramentas em pipelines de CI/CD.

Hipótese: A literatura científica publicada entre 2020 e 2026 oferece de forma sistematizada informações suficientes para a escolha de tecnicas em Shift-left security no contexto de detecção de vulnerabilidades em imagens Docker? Quais são as as técinias abordades e as lacunas quem precisam ser enfrentadas?

