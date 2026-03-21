# CLAUDE.md

## Sobre este repositório
Repositório de apoio ao TCC da pós-graduação (MBA) em Cybersecurity do João Arzamendia.
O Claude atua como **orientador/mentor**, ajudando na estruturação acadêmica e técnica — nunca escrevendo o texto do TCC diretamente.

## Memória
Todos os arquivos de memória (contexto do projeto, decisões, feedback) ficam em `.claude/memory/` dentro deste repositório.
O índice está em `.claude/memory/MEMORY.md`.

**Regra:** Sempre salvar memórias em `.claude/memory/` (no repositório), nunca no diretório global do Claude (`~/.claude/projects/`).

---

## O TCC

### Título
**Critérios para a Escolha de Ferramentas de Escaneamento de Vulnerabilidades em Imagens Docker no Contexto de Shift-Left Security**

### Pergunta de pesquisa
> Como organizações podem escolher de maneira consciente quais ferramentas usar em seu ciclo de desenvolvimento para mitigar os riscos de ataques à cadeia de suprimentos de software em imagens Docker usando shift-left e ferramentas automatizadas de escaneamento de imagens?

### Objetivo geral
Propor critérios para a escolha de ferramentas de escaneamento de vulnerabilidades em imagens Docker no contexto de shift-left security.

### Objetivos específicos
1. Analisar os principais vetores de ataques à cadeia de suprimentos de software em imagens Docker.
2. Comparar ferramentas de escaneamento (Trivy, Grype, Clair) quanto a cobertura de CVEs, integração com CI, desempenho, entre outros critérios.
3. Executar testes práticos para a escolha de ferramentas de escaneamento na detecção de falhas de segurança em pipelines de CI/CD.
4. Elaborar recomendações práticas para a adoção de ferramentas de escaneamento considerando diferentes perfis organizacionais.

### Hipótese
A integração de scanners de vulnerabilidades em pipelines de integração contínua permite detectar vulnerabilidades conhecidas em imagens Docker antes da publicação em produção.

---

## Estrutura do pré-projeto

Segue o template institucional (`documentacao/template-pre-projeto.pdf`). A ordem obrigatória é:

| # | Seção | Arquivo | Status |
|---|---|---|---|
| 1 | Tema | `TEMA.md` (raiz) | Pronto |
| 2 | Introdução – Problematização | `pre-projeto/1-INTRODUCAO.md` | Pronto |
| 3 | Justificativa | `pre-projeto/0-JUSTIFICATIVA.md` | Pronto |
| 4 | Objetivos (Geral + Específicos) | `pre-projeto/2-OBJETIVO.md` | Pronto |
| 5 | Metodologia | `pre-projeto/4-METODOLOGIA.md` | Roteiro criado, falta rascunho |
| 6 | Cronograma | `pre-projeto/5-CRONOGRAMA.md` | Roteiro criado, falta rascunho |
| 7 | Referências | `pre-projeto/999 - BIBLIOGRAFICA.md` | Pronto (17 refs ABNT) |
| — | Referencial Teórico (extra) | `pre-projeto/3-REFERENCIAL-TEORICO.md` | Pronto (5 subseções), não é obrigatório no pré-projeto |

**Nota:** O Referencial Teórico (seção 3) não consta no template do pré-projeto, mas foi incluído para demonstrar maturidade da pesquisa. Avaliar com o orientador se deve ser mantido ou removido na entrega.

---

## Estrutura do repositório

```
.
├── CLAUDE.md                  # Este arquivo
├── TEMA.md                    # Guia inicial do tema
├── documentacao/              # Templates e guias institucionais
│   ├── template-pre-projeto.docx/pdf
│   ├── template-tcc.docx
│   ├── guia-para-elaboracao-do-tcc.pdf
│   └── metodologia-da-pesquisa-cientifica.pdf
├── pre-projeto/               # Seções do pré-projeto (markdown)
│   ├── 0-JUSTIFICATIVA.md
│   ├── 1-INTRODUCAO.md
│   ├── 2-OBJETIVO.md
│   ├── 3-REFERENCIAL-TEORICO.md
│   ├── 4-METODOLOGIA.md
│   ├── 5-CRONOGRAMA.md
│   └── 999 - BIBLIOGRAFICA.md
├── papers/                    # PDFs e markdowns dos papers lidos
│   ├── 00-REPORT.md           # Índice de todos os papers
│   └── autor_ano_descricao.{pdf,md}
└── .claude/memory/            # Memória das conversas e decisões
```

### Convenção de nomes dos papers
Formato: `autor_ano_descricao.{pdf,md}`
Exemplos: `boles_2024_docker-image-security.pdf`, `ladisa_2023_taxonomy-attacks.md`

### Conversão de PDFs
- Ferramenta preferida: `pymupdf4llm` (com `write_images=False`)
- Alternativa: `docling` (pode dar OOM em PDFs grandes)
- Nunca incluir imagens base64 nos markdowns

---

## Referências utilizadas (17 papers)

### Cadeia de suprimentos e ataques
- Ladisa et al. (2023) — Taxonomia de ataques SSC
- Gokkaya, Aniello, Halak (2023) — Revisão de ataques SSC
- Williams, Hamer, Zahan (2024) — Crescimento exponencial de ataques desde 2020
- Williams et al. (2025) — Direções de pesquisa em segurança SSC
- Sonatype (2026) — Relatório anual (9,8 trilhões de downloads)
- Martinez (2021) — SolarWinds e dependência de código de terceiros (85-97%)

### Casos de ataque
- Arvanitis et al. (2022) — event-stream
- Lins et al. (2024) — xz utils
- Hiesgen et al. (2022) — Log4j

### Containers e Docker
- CNCF (2024) — 91% de organizações usando containers
- Docker (2025) — Documentação oficial de imagens-base
- Anasuri (2024) — Shift-left e ferramentas de escaneamento

### Ferramentas de escaneamento (comparações)
- Boles et al. (2024) — Trivy vs Grype em 927 imagens (84,6% discrepância)
- Pardo (2024) — Comparação Grype, Trivy, Clair, Snyk (dissertação)
- Bhardwaj (2023) — Clair e Trivy em CI/CD (dissertação)
- Javed, Toor (2021) — Qualidade de scanners (~34% CVEs perdidas)
- Jain et al. (2021) — Revisão de mecanismos de segurança Docker

---

## Decisões tomadas

1. **Citação CHEN et al. 2024 estava errada** → O paper "Can the Rising Tide..." é de Williams, Hamer, Zahan. Corrigido.
2. **ANASURI; RUSUM 2024 incorreto** → Rusum não é coautor do paper IJETCSIT. Corrigido para ANASURI, 2024.
3. **GOKKAYA removido da citação de SLSA** → O paper não menciona SLSA. Removido.
4. **CNCF 2024 não suporta claim de dependências transitivas** → Substituído por LADISA + SONATYPE.
5. **Referencial Teórico não é obrigatório no pré-projeto** → Incluído como extra; avaliar com orientador.

---

## Regras de atuação do Claude

- **Orientador/mentor**: nunca escrever o texto do TCC diretamente. Criar roteiros, revisar rascunhos, corrigir ortografia, verificar citações.
- **Exceção**: quando o João pedir explicitamente para implementar/redigir, pode fazê-lo (ele revisará depois).
- **Citações**: sempre verificar nos papers originais se o trecho citado realmente existe.
- **Bibliografia**: manter `999 - BIBLIOGRAFICA.md` atualizada com trechos originais em inglês.
- **Formato**: ABNT para citações e referências.
