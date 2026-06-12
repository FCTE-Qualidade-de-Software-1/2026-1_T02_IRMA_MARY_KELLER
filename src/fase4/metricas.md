# 2. Cálculo das Métricas Definidas na Fase 2

Esta seção apresenta os resultados quantitativos gerados pela aplicação das fórmulas estruturadas no framework GQM, confrontando os dados obtidos com os limites de tolerância estabelecidos.

---

## M1.1 — Índice de Completude Funcional (ICF)

| Atributo | Valor |
|----------|-------|
| Cenários Especificados | Operações de CRUD unificadas e controle de filtros estáticos de exibição |
| Cenários Homologados | Unificação estática via script executada e filtros funcionais no React |
| Cálculo | (2 / 2) × 100 = **100%** |
| Critério de Julgamento | Excelente |

---

## M1.2 — Taxa de Precisão da Moderação (TPM)

| Atributo | Valor |
|----------|-------|
| Total de Postagens Injetadas | 20 frases de controle |
| Classificações Corretas | 9 aprovações legítimas |
| Classificações Incorretas | 11 aprovações de conteúdos impróprios (falsos negativos) |
| Cálculo | (9 / 20) × 100 = **45%** |
| Critério de Julgamento | Insatisfatório |

---

## M2.1 — Densidade de Defeitos Críticos (DDC)

| Atributo | Valor |
|----------|-------|
| Casos de Teste Executados | 1 (injeção de payload corrompido) |
| Falhas Críticas Encontradas | 1 colapso total (tela preta) |
| Cálculo | 1 / 1 = **1.00** |
| Critério de Julgamento | Insatisfatório |

---

## M3.1 — Complexidade Ciclomática Média (CCM)

| Atributo | Valor |
|----------|-------|
| Soma das Complexidades | 176 (scripts principais de IA) |
| Total de Funções Avaliadas | 13 funções |
| Cálculo | 176 / 13 = **13.53** |
| Critério de Julgamento | Bom |

---

## M3.2 — Percentual de Cobertura de Testes (PCT)

| Atributo | Valor |
|----------|-------|
| Backend | 126 testes lógicos ativos cobrindo funções de similaridade vetorial |
| Frontend | 0% de linhas cobertas por testes automatizados |
| Cálculo Consolidado | Abaixo de 50% pela ausência total de cobertura no React |
| Critério de Julgamento | Insatisfatório |

---

## Respostas às Questões e Objetivos GQM

Com base nos valores calculados e nos critérios de julgamento da Fase 2, é possível responder diretamente a cada Questão (Q) e a cada Objetivo (G) do framework GQM.

### Respostas por Questão (Q)

| Questão | Enunciado resumido | Resposta | Evidência |
|---------|-------------------|----------|-----------|
| Q1 — Completude | O sistema executa todas as operações de CRUD e filtragem? | **Sim** — ICF = 100% | M1.1 Excelente: todos os cenários especificados foram homologados |
| Q2 — Correção | A IA classifica e modera anúncios de forma precisa? | **Não** — TPM = 45% | M1.2 Insatisfatório: 11 de 20 conteúdos impróprios foram aprovados (100% de falsos negativos) |
| Q3 — Maturidade | Qual a estabilidade da API/banco ao processar payloads JSON corrompidos? | **Insatisfatória** — DDC = 1,00 | M2.1 Insatisfatório: o único caso de teste gerou colapso total do frontend |
| Q4 — Modularidade | O código-fonte apresenta baixo acoplamento e distribuição adequada de responsabilidades? | **Parcialmente** — CCM = 13,53 (Bom na média) | M3.1 Bom na média geral; porém duas funções atingiram Rank F (CC = 72 e CC = 66), indicando monolitismo localizado |
| Q5 — Testabilidade | A base de código possui salvaguardas suficientes contra regressões? | **Não** — PCT < 50% | M3.2 Insatisfatório: frontend com 0% de cobertura; backend com 126 testes (100% de aprovação) |

### Respostas por Objetivo (G)

| Objetivo | Julgamento Final | Justificativa |
|----------|-----------------|---------------|
| G1 — Adequação Funcional | **Parcialmente Satisfatório** | Completude funcional excelente (M1.1 = 100%), mas correção comprometida pela falha crítica da moderação por IA (M1.2 = 45%) |
| G2 — Confiabilidade | **Insatisfatório** | Tolerância a falhas ausente no frontend: colapso total diante de payload corrompido (M2.1 = 1,00) |
| G3 — Manutenibilidade | **Parcialmente Satisfatório** | Complexidade média aceitável (M3.1 = 13,53 — Bom), mas cobertura de testes crítica (M3.2 < 50% — Insatisfatório) |

---

[← Voltar à Fase 4](../fase4.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 2.0 | 12/06/2026 | Adição das respostas explícitas às Questões e Objetivos GQM | [Ranni Heler](https://github.com/AkaeRanni) |
| 1.0 | 12/06/2026 | Criação do cálculo das métricas | Matheus Rodrigues |
