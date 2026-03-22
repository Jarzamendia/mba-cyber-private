# Relatório de Verificação de Citações — Pré-Projeto

**Data:** 2026-03-22
**Arquivo verificado:** `pre-projeto/PRE-PROJETO.md`

---

## Citações confirmadas

| Afirmação | Citação | Trecho original |
|---|---|---|
| "9,8 trilhões de downloads" | SONATYPE, 2026 | "9.8 TRILLION downloads across Maven Central, PyPI, npm and NuGet." |
| "91% em produção, 14% crescimento" | CNCF, 2024 | "91% of organizations are using containers in production... compared to just 80% in 2023, which is a 14% growth rate year over year." |
| "aumento exponencial desde 2020, ações governamentais e corporativas" | WILLIAMS; HAMER; ZAHAN, 2024 | "Software supply chain attacks have increased exponentially since 2020, prompting worldwide government and corporate initiatives." |
| Shift-left: práticas nas fases iniciais | ANASURI, 2024 | "a shift-left security orientation is needed, which involves the implementation of security practices at the beginning stages..." |
| Roubo de criptomoedas / event-stream | ARVANITIS, 2022 | "operating on the Bitcoin mainnet." |
| Crescimento do uso de OSS | SONATYPE, 2026 | "The scale and ubiquity of open source software have transformed software ecosystems into critical global infrastructures." |

---

## Citações fracas ou imprecisas — ação necessária

### 1. "grupos criminosos ou mesmo de estado-nações" *(Introdução §3)*
- **Citado como:** LINS et al., 2024; ARVANITIS et al., 2022; HIESGEN et al., 2022
- **Problema:** Nenhum dos trechos armazenados confirma explicitamente "estado-nações". O xz utils é amplamente associado a atores estatais, mas o trecho do LINS disponível não menciona isso.
- **Ação:** Verificar no paper LINS se "estado-nação" é afirmado explicitamente. Se não, suavizar para: *"grupos com alto grau de sofisticação"*.

### 2. "passar anos se passando por contribuidores legítimos" *(Justificativa §2)*
- **Citado como:** LINS et al., 2024; ARVANITIS et al., 2022
- **Problema:** A infiltração de anos se aplica ao xz utils (Jia Tan ~2 anos). O event-stream foi diferente: o atacante pediu acesso ao mantenedor que havia abandonado o projeto — não passou anos como contribuidor falso.
- **Ação:** Separar os dois casos na frase. Ex.: *"como o xz utils, em que o atacante passou anos como contribuidor legítimo (LINS et al., 2024), ou o event-stream, em que o controle do pacote foi transferido a um ator mal-intencionado (ARVANITIS et al., 2022)"*.

### 3. LADISA citado para shift-left *(Introdução §4)*
- **Citado como:** ANASURI, 2024; LADISA et al., 2023
- **Problema:** Os trechos armazenados do LADISA tratam de definição de SSC e visibilidade de dependências — nenhum menciona shift-left.
- **Ação:** Verificar no paper LADISA se há menção a shift-left. Se não houver, remover LADISA dessa citação específica e manter apenas ANASURI.

### 4. "Clair, Trivy e Grype são capazes de escanear imagens Docker" *(Introdução §4)*
- **Citado como:** ANASURI, 2024; WILLIAMS et al., 2025
- **Problema:**
  - Trecho do ANASURI fala de shift-left em geral, não nomeia as ferramentas.
  - Trecho do WILLIAMS 2025 fala de superfície de ataque, não de capacidades dos scanners.
- **Ação:** Substituir por **PARDO (2024)**, **BOLES (2024)** e/ou **BHARDWAJ (2023)**, que têm trechos explícitos sobre essas ferramentas escaneando imagens Docker.

### 5. "vulnerabilidade que possibilita acesso remoto a milhões de softwares" / Log4j *(Justificativa §2)*
- **Citado como:** HIESGEN et al., 2022
- **Problema:** O trecho armazenado diz apenas que a vulnerabilidade *"resides in libraries deeply nested within software supply chains"* — não menciona acesso remoto (RCE). Log4Shell é de fato uma RCE, mas o trecho disponível não confirma essa afirmação específica.
- **Ação:** Localizar trecho do HIESGEN que mencione RCE/execução remota, ou complementar com o CVE-2021-44228 como referência direta.

---

## Resumo de prioridades

| Prioridade | Item |
|---|---|
| Alta | Trocar ANASURI+WILLIAMS 2025 por PARDO+BOLES+BHARDWAJ na frase sobre os scanners |
| Alta | Corrigir a frase sobre "anos como contribuidores" — separar os dois casos |
| Média | Verificar no paper LINS se "estado-nação" é afirmado; se não, suavizar |
| Média | Verificar no paper LADISA se há menção a shift-left; se não, remover da citação |
| Baixa | Verificar no HIESGEN trecho explícito sobre RCE do Log4j |
