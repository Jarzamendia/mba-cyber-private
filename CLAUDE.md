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

### Título (atualizado 2026-04-15 pelo orientador)
**Shift-Left Security: Detecção de Vulnerabilidades em Docker Imagens**

> ⚠️ Nota: "Docker Imagens" é o termo literal proposto pelo orientador. Em português ABNT o natural seria "Imagens Docker" — confirmar na próxima devolutiva.

### Tipo de pesquisa
**Revisão bibliográfica pura** (decisão do orientador, 2026-04-15). Testes práticos foram removidos do escopo.

### Problema de pesquisa
> O que a literatura científica publicada entre 2020 e 2026 evidencia sobre a detecção de vulnerabilidades em imagens Docker no contexto de shift-left security e sobre os critérios que devem orientar a escolha de ferramentas automatizadas de escaneamento?

### Objetivo geral
Analisar, por meio de revisão bibliográfica, o estado da arte sobre detecção de vulnerabilidades em imagens Docker no contexto de shift-left security.

### Objetivos específicos (3, após remoção do item de testes práticos)
1. Analisar, a partir da literatura, os principais vetores de ataques à cadeia de suprimentos de software em imagens Docker.
2. Comparar, com base em estudos empíricos publicados, as ferramentas de escaneamento (Trivy, Grype, Clair) quanto a cobertura de CVEs, integração com CI/CD, desempenho e demais critérios reportados.
3. Sintetizar recomendações para a adoção de ferramentas considerando diferentes perfis organizacionais, com base nas evidências da literatura.

### Hipótese
A literatura científica publicada entre 2020 e 2026 oferece evidências suficientes para caracterizar divergências de desempenho, cobertura e integração entre as principais ferramentas de escaneamento de vulnerabilidades em imagens Docker, permitindo consolidar critérios que orientem a escolha dessas ferramentas conforme o perfil organizacional no contexto de shift-left security.

---

## Estrutura do pré-projeto

Segue o template institucional (`documentacao/template-pre-projeto.pdf`). A ordem obrigatória é:

| # | Seção | Arquivo | Status |
|---|---|---|---|
| 1 | Tema | `TEMA.md` (raiz) | Pronto |
| 2 | Introdução – Problematização | `pre-projeto/1-INTRODUCAO.md` | Pronto |
| 3 | Justificativa | `pre-projeto/0-JUSTIFICATIVA.md` | Pronto |
| 4 | Objetivos (Geral + Específicos) | `pre-projeto/2-OBJETIVO.md` | Pronto |
| 5 | Metodologia | `pre-projeto/4-METODOLOGIA.md` | Pronto (revisão bibliográfica, 9 pontos do orientador) |
| 6 | Cronograma | `pre-projeto/5-CRONOGRAMA.md` | Pronto (sem testes práticos) |
| 7 | Referências | `pre-projeto/999 - BIBLIOGRAFICA.md` | Pronto (17 refs ABNT) |
| — | Referencial Teórico | `pre-projeto/3-REFERENCIAL-TEORICO.md` | **Removido do pré-projeto** — conteúdo preservado para o TCC |

**Decisão do orientador (2026-04-15):** Referencial Teórico **não** será incluído no pré-projeto (não consta no template). O conteúdo fica preservado no arquivo, com aviso, para reuso no TCC final.

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
