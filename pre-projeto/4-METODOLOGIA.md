# Metodologia

<!--
CONFERIR / MODIFICAR antes de executar a busca:
- Bases escolhidas: IEEE Xplore, ACM DL, arXiv, Google Scholar. Orientador citou Scopus e PubMed como exemplos — decidir se inclui Scopus (PubMed não cabe neste tema).
- Recorte temporal 2020-2026: justificado pelo crescimento exponencial de ataques SSC desde 2020 (Williams; Hamer; Zahan, 2024). Confirmar.
- Strings booleanas: revisar antes de rodar a busca. Registrar em planilha à parte (número de resultados por base, duplicatas etc.) — ainda não feito.
- §5 (análise qualitativa-comparativa em 3 eixos): se orientador pedir mais detalhe, expandir métricas de extração (tabela por estudo).
-->

## Objetivo desta seção
A metodologia descreve **como** a pesquisa será conduzida. Conforme o template institucional e as orientações do tutor-orientador, esta pesquisa caracteriza-se como uma **revisão bibliográfica**, devendo contemplar: tipo de pesquisa, bases consultadas e justificativa da escolha, período considerado e sua justificativa, critérios de inclusão/exclusão, processo de triagem e método de análise.

## Pontos obrigatórios (orientação do tutor)
1. Especificar que se trata de uma revisão bibliográfica.
2. Citar bases de dados, repositórios e bibliotecas consultadas.
3. Justificar a escolha dessas fontes.
4. Determinar o intervalo de tempo dos estudos.
5. Justificar a escolha do período.
6. Incluir parâmetros de idioma, tipo de publicação e relevância temática.
7. Descrever a condução da triagem dos estudos.
8. Detalhar as etapas (leitura de títulos, resumos, textos completos).
9. Descrever os critérios usados para analisar e interpretar as informações.

---

## Metodologia

Esta pesquisa caracteriza-se como uma revisão bibliográfica cujo objetivo é analisar o estado da arte sobre Shift-left security com foco em técnicas de detecção de vulnerabilidades em imagens Docker. Optou-se por esse método por permitir sistematizar o conhecimento publicado, identificar convergências e lacunas entre estudos e consolidar evidências que fundamentem recomendações para a adoção de ferramentas de escaneamento.

O levantamento bibliográfico foi conduzido nas bases de dados **IEEE Xplore**, **ACM Digital Library** e **Google Scholar**. IEEE Xplore e ACM Digital Library foram selecionadas por sua abrangência em periódicos e conferências revisados por pares; e Google Scholar, por sua amplitude e capacidade de localizar relatórios técnicos e dissertações relevantes. De forma complementar, foram considerados relatórios de mercado reconhecidos como os publicados por Sonatype e pela Cloud Native Computing Foundation (CNCF), por trazerem dados quantitativos sobre adoção de containers e crescimento da cadeia de suprimentos de software, informações que raramente aparecem em publicações acadêmicas.

Os termos de busca utilizados, combinados por operadores booleanos, foram: *"software supply chain security"*, *"Docker image vulnerability scanning"*, *"container security"*, *"shift-left security"*, *"DevSecOps"*, *"Trivy"*, *"Grype"* e *"Clair"*. Adotou-se como recorte temporal o período **de 2020 a 2026**, justificado pelo crescimento exponencial dos ataques à cadeia de suprimentos de software observado desde 2020 (WILLIAMS; HAMER; ZAHAN, 2024) e pela consolidação, nesse intervalo, das ferramentas de escaneamento estudadas. Obras clássicas anteriores a 2020 foram admitidas excepcionalmente quando necessárias à fundamentação de conceitos estruturantes.

Foram estabelecidos como **critérios de inclusão**: publicações em português ou inglês; artigos científicos, dissertações, teses ou relatórios técnicos de instituições reconhecidas; trabalhos com foco em segurança de containers, imagens Docker ou cadeia de suprimentos de software. Como **critérios de exclusão**: trabalhos sem revisão por pares (exceto relatórios de mercado de reconhecida credibilidade); estudos dedicados exclusivamente à segurança de runtime de containers, sem tratar de análise estática; e trabalhos duplicados.

A triagem dos estudos foi conduzida em três etapas sucessivas:
(i) leitura de títulos e descarte dos claramente fora de escopo;
(ii) leitura de resumos para avaliação de aderência temática;
(iii) leitura integral dos estudos selecionados, com extração de dados estruturada.

Para cada estudo incluído, foram registrados: autor e ano, objetivo, método, ferramentas analisadas, métricas reportadas e principais conclusões e lacunas identificadas. 