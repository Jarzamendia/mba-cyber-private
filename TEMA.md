# Guia Completo para o TCC: Segurança Shift-Left para Docker

Este guia detalha tudo o que você precisa configurar, estudar e desenvolver para executar o seu TCC com excelência, unindo a análise de vulnerabilidades com a engenharia prática de DevSecOps.

## 1. Conhecimentos Necessários (O que estudar)
Para executar este projeto sem travamentos, você precisará dominar os seguintes conceitos:
* **Fundamentos de Docker:** Entender como as imagens são construídas (`Dockerfile`), o sistema de camadas (layers) e por que contêineres são diferentes de máquinas virtuais.
* **Integração Contínua (CI):** Compreender o fluxo de uma esteira de CI/CD. Você precisará saber escrever arquivos YAML para configurar pipelines (recomendo focar em GitHub Actions, por ser gratuito e de fácil configuração).
* **Scanners de Vulnerabilidades:** Estudar como funcionam os bancos de dados de CVEs (Common Vulnerabilities and Exposures) e como os scanners comparam os pacotes da imagem com esses bancos.
* **Python:** Conhecimento intermediário para criar o script do *Security Gate*. Você precisará lidar com manipulação de arquivos JSON (onde os relatórios dos scanners são salvos), requisições HTTP (caso queira enviar alertas para um Discord/Slack) e controle de fluxo (condicionais para quebrar a esteira).

---

## 2. O Ambiente de Laboratório (Ferramentas)
Você não precisará de hardware potente, pois tudo pode ser rodado em nuvem ou localmente de forma leve.
* **Alvos (Imagens Vulneráveis):** Não use imagens de produção reais. Utilize imagens intencionalmente vulneráveis criadas para testes, como `vulnerables/web-dvwa` ou crie um `Dockerfile` simples instalando versões antigas do Apache ou Node.js.
* **Scanners Open Source:** Instale e configure localmente para a fase de testes:
    * *Trivy* (da Aqua Security): Excelente, rápido e muito popular.
    * *Grype* (da Anchore): Ótimo para analisar dependências.
    * *Clair* (da Quay): Um pouco mais complexo de configurar, ótimo para enriquecer a comparação.
* **Plataforma de CI/CD:** Crie um repositório no GitHub para hospedar o código do seu projeto e usar o GitHub Actions para rodar a esteira.
* **Linguagem:** Python 3.x para o desenvolvimento do script de automação.

---

## 3. Passo a Passo da Execução Prática

### Fase 1: A Análise Comparativa (O "Qual?")
1.  Escreva um `Dockerfile` que instale pacotes sabidamente desatualizados.
2.  Rode o Trivy, o Grype e o Clair contra essa mesma imagem no seu terminal.
3.  Exporte os relatórios de todos eles em formato JSON.
4.  **O que medir para o TCC:** Tempo que cada um demorou para rodar, quantidade de vulnerabilidades CRÍTICAS encontradas (veja se algum deu falso positivo) e facilidade de leitura do relatório.

### Fase 2: Construção da Esteira (CI/CD)
1.  No seu repositório do GitHub, crie um arquivo `.github/workflows/main.yml`.
2.  Configure a esteira para que, toda vez que um código for empurrado (`git push`), ela construa a imagem Docker automaticamente.
3.  Adicione um passo (`step`) na esteira para rodar o scanner que venceu a sua avaliação na Fase 1, gerando o relatório JSON dentro do servidor do GitHub Actions.

### Fase 3: O *Security Gate* em Python (O "Como?")
1.  Crie um script `security_gate.py` no seu repositório.
2.  A esteira deve acionar esse script logo após o scanner terminar.
3.  **A Lógica:** O script Python vai abrir o JSON gerado pelo scanner. Ele deve varrer o arquivo procurando a contagem de vulnerabilidades.
4.  **A Regra de Negócio:** Programe o script para que, se houver 1 ou mais vulnerabilidades classificadas como "CRITICAL", o script retorne um erro (ex: `sys.exit(1)`). Isso fará a esteira do GitHub Actions quebrar e ficar vermelha, impedindo o *deploy*. Se não houver falhas críticas, ele retorna `sys.exit(0)` e a esteira fica verde.

---

## 4. Estruturação da Escrita do TCC
Com o laboratório funcionando, a escrita flui naturalmente. 
* Use capturas de tela da esteira quebrando (vermelha) e passando (verde) para ilustrar o Capítulo 4 (Implementação).
* Gere gráficos no Excel comparando o tempo de execução dos scanners para enriquecer o Capítulo 5 (Resultados).
* Documente todo o código Python em um apêndice ou crie um link para o seu repositório público no GitHub.

---

Gostaria que eu rascunhasse o código inicial em Python para esse *Security Gate* de leitura de JSON ou prefere começar definindo os objetivos gerais e específicos para o documento do TCC?