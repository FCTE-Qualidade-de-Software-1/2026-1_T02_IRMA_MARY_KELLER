# 1. Planejamento da Avaliação

## 1.1. Objetivo da Fase

Esta fase detalha o plano de execução para a coleta de dados da Fase 4. O objetivo é traduzir as métricas definidas no framework GQM em um conjunto de Casos de Teste (CTs) auditáveis, assegurando que a avaliação da qualidade do Mural UnB seja sistemática, repetível e empiricamente verificável. Esta página centraliza o planejamento, a matriz de rastreabilidade de engenharia, o cronograma operacional das sprints de auditoria e a divisão de tarefas da equipe.

---

## 1.2. Método de Avaliação

Adota-se uma abordagem orientada pelo método GQM (Goal-Question-Metric). A coleta de dados engloba múltiplas fontes de evidência do ecossistema: análise estática de código via ferramenta Radon, testes de cobertura lógica estrutural com PyTest-Cov, injeção proposital de falhas semânticas na base de dados JSON e engenharia reversa de logs de exceção JavaScript via console do navegador (DevTools).

### Matriz Geral de Rastreabilidade

| Característica | Questão do GQM | Métrica | Escopo Técnico | Ferramenta / Fonte de Dados | Caso de Teste |
|----------------|---------------|---------|----------------|-----------------------------|---------------|
| Adequação Funcional | Q1. Completude — Operação do Feed | M1.1 | Comportamento de CRUD e Isolamento de Filtros | `scripts/juntar_oportunidades.py` | CT-FUNC-01 |
| Adequação Funcional | Q2. Correção — Precisão da IA | M1.2 | Taxa de Precisão Semântica da Moderação da IA | `scripts/generate_embeddings_gemini.py` | CT-FUNC-02 |
| Confiabilidade | Q3. Maturidade — Tolerância a Falhas | M2.1 | Resiliência do Frontend a Payloads Corrompidos | Injeção Manual de Falhas e DevTools (F12) | CT-CONF-01 |
| Manutenibilidade | Q4. Modularidade — Distribuição de Responsabilidades | M3.1 | Índice de Complexidade Ciclomática por Bloco | Radon (Módulos Python) | CT-MAIN-02 |
| Manutenibilidade | Q5. Testabilidade — Cobertura de Código | M3.2 | Percentual de Cobertura de Código (Lines/Branches) | PyTest-Cov / Framework do Frontend | CT-MAIN-01 |

---

## 1.3. Cronograma de Execução e Divisão de Tarefas

O cronograma detalha as atividades da equipe de auditoria técnica. As datas refletem a janela de execução real das sprints de garantia de qualidade (QA), desde o isolamento de ambiente até a consolidação estatística dos defeitos encontrados.

| Fase | Etapa Operacional | Métricas Alvo | Responsáveis | Início | Fim |
|------|-------------------|---------------|--------------|--------|-----|
| Fase 3 | Configuração e Saneamento de Infraestrutura | Levantamento de caminhos rígidos e variáveis de ambiente despadronizadas | Paulo Lobo | 10/06/2026 | 10/06/2026 |
| Fase 3 | Execução de Auditoria Estática e Lógica | Complexidade Ciclomática (Radon) e Cobertura de Código (PyTest) | Paulo Lobo | 10/06/2026 | 11/06/2026 |
| Fase 3 | Injeção de Falhas e Validação da IA | Precisão Semântica (M1.2) e Robustez a Dados Nulos (M2.1) | Paulo Lobo | 11/06/2026 | 11/06/2026 |
| Fase 4 | Consolidação Estatística de Dados | Mapeamento de Falsos Negativos e Logs de Crash (DevTools) | Matheus Rodrigues | 11/06/2026 | 12/06/2026 |
| Fase 4 | Elaboração do Plano de Mitigação | Engenharia Defensiva (React) e Alinhamento de Thresholds | Matheus Rodrigues | 11/06/2026 | 12/06/2026 |

---

## 1.4. Fontes de Evidência e Rastreabilidade

Os seguintes artefatos e ferramentas são utilizados como repositórios de dados para fins de auditoria acadêmica:

| Fonte de Evidência | Localização / Mecanismo | Utilização no Plano de Medição |
|--------------------|-------------------------|-------------------------------|
| Código-Fonte (Python/React) | Repositório Local `2025-2-Mural-UnB` | Base estrutural para inspeção automática de complexidade e acoplamento |
| Matriz Semântica | `data/tags.json` | Mapeamento de alta dimensão gerado pelo modelo `text-embedding-004` |
| Massa de Dados de Homologação | Planilha CSV / 20 Frases de Controle | Entrada padrão para testar os limites de falso positivo e falso negativo da IA |
| Logs de Depuração | Console do Navegador (F12) | Captura de mensagens vermelhas de exceção unhandled JavaScript |
| Relatório Estatístico | Diretório `htmlcov/index.html` | Comprovação física e quantitativa de Statement Coverage do PyTest |

---

---

## 1.5. Rastreabilidade com a Fase 2 — Consistência do Plano

A consistência entre a Fase 2 (Especificação da Avaliação) e este Plano de Avaliação (Fase 3) é total: cada Caso de Teste (CT) foi projetado para coletar os dados necessários ao cálculo de exatamente uma métrica definida no framework GQM, garantindo que nenhuma métrica fique sem instrução de coleta e que nenhum CT execute atividade desvinculada de uma métrica especificada.

| Métrica (Fase 2) | Fórmula / Atributo | Caso de Teste (Fase 3) | Método de coleta |
|------------------|--------------------|------------------------|-----------------|
| **M1.1** — ICF | Cenários CRUD e filtros homologados / Total especificado | CT-FUNC-01 | Execução do script de unificação + inspeção de filtros no React |
| **M1.2** — TPM | Classificações corretas da IA / Total de postagens de teste | CT-FUNC-02 | 20 frases de controle injetadas no pipeline `text-embedding-004` |
| **M2.1** — DDC | Falhas críticas / Total de casos de teste de confiabilidade | CT-CONF-01 | Injeção de payload JSON corrompido + observação via DevTools (F12) |
| **M3.1** — CCM | Soma de complexidades / Total de funções | CT-MAIN-02 | Varredura Radon (`radon cc scripts/ -a -s`) |
| **M3.2** — PCT | Linhas cobertas / Total de linhas × 100 | CT-MAIN-01 | `pytest --cov` (backend) + `npm run test -- --coverage` (frontend) |

Os critérios de julgamento (Excelente / Bom / Regular / Insatisfatório) definidos para cada métrica na Fase 2 são aplicados diretamente aos dados coletados nesta Fase 3 e analisados na Fase 4, garantindo rastreabilidade ponta a ponta sem lacunas.

---

[← Voltar à Fase 3](../fase3.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 2.0 | 12/06/2026 | Correção de referência M3.3→M3.1 e adição da seção de rastreabilidade F2→F3 | [Ranni Heler](https://github.com/AkaeRanni) |
| 1.0 | 11/06/2026 | Criação do planejamento da avaliação | Paulo Nery Lobo |
