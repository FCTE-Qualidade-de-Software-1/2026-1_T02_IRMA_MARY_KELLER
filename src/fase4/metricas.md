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

[← Voltar à Fase 4](../fase4/dados-brutos.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 12/06/2026 | Criação do cálculo das métricas | Matheus Rodrigues |
