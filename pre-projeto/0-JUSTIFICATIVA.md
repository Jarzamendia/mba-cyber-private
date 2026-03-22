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

Com o rápido crescimento do ecossistema de criação de softwares de código aberto e comerciais e de suas bases de usuário, o mundo tem visto um incrível aumento na escala da criação e uso de cadeias de suprimento de software (SONATYPE, 2026), isto é dependências de software reutilizáveis que são usadas diariamente por equipes de engenharia de software do mundo todo.

Casos como o backdoor do xz utils (LINS et al., 2024) e do event-stream (ARVANITIS et al., 2022) demonstram que atores mal-intencionados podem passar anos se passando por contribuidores legítimos para, de forma ofuscada, adicionar backdoors de acesso remoto e roubo de criptomoedas. Há também o caso do Log4j (HIESGEN et al., 2022), com uma vulnerabilidade que possibilita acesso remoto a milhões de softwares pelo mundo através de um comportamento não intencional a partir de uma determinada versão.

Com o amplo uso de softwares de código aberto ao longo de todo o ciclo de vida de desenvolvimento de software (LADISA et al., 2023), garantir que nenhuma das dependências usadas esteja comprometida se tornou um trabalho árduo e custoso. Muitas vezes as equipes não têm mãos suficientes para tal demanda ou mesmo acabam negligenciando etapas críticas, como boas práticas de cibersegurança.

Em resposta a esse cenário, ferramentas de código aberto como Trivy, Grype e Clair buscam mitigar os riscos envolvendo cadeias de suprimento de software através de scanners automatizados de imagens Docker, sistemas de arquivos e listas de materiais de software (SBOM). Essas ferramentas podem atuar tanto no ciclo de desenvolvimento quanto em esteiras de entrega contínua (CD).

**Hipótese:** A integração de scanners de vulnerabilidades em pipelines de integração contínua permite detectar vulnerabilidades conhecidas em imagens de container Docker antes da publicação em produção. Para tanto, serão analisadas métricas como velocidade de execução, cobertura de verificação e taxa de falsos positivos e negativos dos scanners, além de literatura acadêmica publicada, a fim de propor critérios que orientem a escolha da ferramenta mais adequada para diferentes contextos organizacionais.