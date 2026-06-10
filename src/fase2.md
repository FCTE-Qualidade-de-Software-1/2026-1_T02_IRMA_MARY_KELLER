# Fase 2 — Especificação da Avaliação

## 1.1. Metodologia GQM (Goal Question Metric)

Para a realização da etapa de especificação da avaliação, utilizaremos o paradigma GQM. O GQM é uma abordagem de cima para baixo (top-down) para estabelecer um sistema de medição direcionado a metas para o desenvolvimento de software, em que a equipe começa com metas organizacionais, define a medição das metas, levanta questões para abordar os objetivos e identifica as métricas que proporcionem respostas às perguntas (SILVA et al., 2009, p. 4).

O software objeto da avaliação é o Mural UnB, uma aplicação web de gestão de conteúdo acadêmico. Como marco rastreável e auditável para esta avaliação, define-se a release *qualidade-de-software-mural*, implantada no repositório oficial da disciplina em 08/06/2026 (disponível em [https://github.com/unb-mds/2025-2-Mural-UnB](https://github.com/unb-mds/2025-2-Mural-UnB)).

A análise é conduzida sob a perspectiva de desenvolvedores técnicos e usuários finais, concentrando-se nas características de Adequação Funcional, Confiabilidade e Manutenibilidade, mapeadas de acordo com o modelo de qualidade ISO/IEC 25010.

---

## 1.2. Objetivos de Medição (Goals)

Neste nível conceitual, o objetivo é formulado para um determinado objeto de medição, podendo ser analisado sob diferentes perspectivas de produtos, processos ou recursos (BASILI et al., 1994, p. 528).

### GOAL 1: Adequação Funcional

| Atributo | Descrição |
|----------|-----------|
| Objeto de Medição | Módulo de postagens, filtros e sistema de moderação via API do Gemini |
| Propósito | Avaliar a completude e a correção das regras de negócio |
| Perspectiva de Qualidade | Adequação Funcional (ISO/IEC 25010) |
| Ponto de Vista | Comunidade discente e moderadores do sistema |
| Ambiente/Contexto | Ambiente de homologação simulando cenários reais de uso acadêmico |

### GOAL 2: Confiabilidade

| Atributo | Descrição |
|----------|-----------|
| Objeto de Medição | Persistência de dados e endpoints da API de integração |
| Propósito | Avaliar a estabilidade do sistema sob carga de requisições |
| Perspectiva de Qualidade | Confiabilidade (Maturidade e Disponibilidade) |
| Ponto de Vista | Equipe de infraestrutura técnica |
| Ambiente/Contexto | Execução de rotinas de testes integrados e simulação de falhas |

### GOAL 3: Manutenibilidade

| Atributo | Descrição |
|----------|-----------|
| Objeto de Medição | Repositório de código-fonte (React, TypeScript e Python) |
| Propósito | Avaliar a viabilidade de evolução do ecossistema por novos desenvolvedores |
| Perspectiva de Qualidade | Manutenibilidade (Modularidade e Analisabilidade) |
| Ponto de Vista | Engenheiros de software e avaliadores de qualidade |
| Ambiente/Contexto | Análise estática de código e suítes de testes automatizados via GitHub Actions |

---

## 1.3. Questões (Questions) e Hipóteses

As perguntas buscam caracterizar o produto em relação a aspectos específicos da qualidade, permitindo compreender seu desempenho sob o ponto de vista selecionado, funcionando como uma ponte entre o objetivo estratégico e a coleta de dados (BASILI et al., 1994, p. 528).

**Q1 (Completude):** O sistema executa todas as operações de CRUD de anúncios e filtragem por categorias conforme o especificado?

> **Hipótese 1.1 (H1.1):** Falhas na comunicação com a API de dados impedem que ações de atualização (Update) reflitam instantaneamente na interface.

**Q2 (Correção):** A inteligência artificial da API do Gemini classifica e modera os anúncios de forma precisa, evitando desvios éticos?

> **Hipótese 2.1 (H2.1):** A IA falha ao analisar textos ambíguos, gerando taxas elevadas de falsos positivos na moderação.

**Q3 (Maturidade):** Qual é a estabilidade da API e do banco de dados ao processar payloads estruturados em JSON?

> **Hipótese 3.1 (H3.1):** O recebimento de campos nulos ou corrompidos resulta em interrupções abruptas (HTTP 500) por ausência de tratamento de exceções.

**Q4 (Modularidade):** A arquitetura do Frontend em React/TypeScript minimiza o acoplamento entre os componentes de interface?

> **Hipótese 4.1 (H4.1):** A lógica de negócio está excessivamente concentrada em componentes globais, ferindo a manutenibilidade.

**Q5 (Analisabilidade/Testabilidade):** A base de código possui salvaguardas suficientes para prevenir defeitos durante processos de refatoração?

> **Hipótese 5.1 (H5.1):** A ausência de uma suíte robusta de testes automatizados expõe o sistema a erros de regressão.

---

## 1.4. Métricas (Metrics) e Critérios de Julgamento

As métricas fornecem os dados necessários para responder às perguntas, permitindo uma análise quantitativa ou qualitativa (BASILI et al., 1994, p. 529).

### M1.1: Índice de Completude Funcional (ICF)

**Fórmula:** `ICF = (Nº de cenários de CRUD e filtros homologados / Nº total de cenários especificados) × 100`

| Classificação | Valor |
|---------------|-------|
| Excelente | 100% |
| Bom | ≥ 90% |
| Regular | ≥ 75% |
| Insatisfatório | < 75% |

### M1.2: Taxa de Precisão da Moderação (TPM)

**Fórmula:** `TPM = (Nº de classificações corretas da IA / Nº total de postagens de teste) × 100`

| Classificação | Valor |
|---------------|-------|
| Excelente | ≥ 95% |
| Bom | ≥ 85% |
| Regular | ≥ 70% |
| Insatisfatório | < 70% |

### M2.1: Densidade de Defeitos Críticos (DDC)

**Fórmula:** `DDC = (Nº de falhas críticas encontradas / Nº total de casos de teste executados)`

| Classificação | Valor |
|---------------|-------|
| Excelente | 0 |
| Bom | ≤ 0,05 |
| Regular | ≤ 0,15 |
| Insatisfatório | > 0,15 |

### M3.1: Complexidade Ciclomática Média (CCM)

**Fórmula:** `CCM = (Soma da Complexidade de todas as funções / Nº total de funções)`

| Classificação | Valor |
|---------------|-------|
| Excelente | ≤ 10 |
| Bom | ≤ 15 |
| Regular | ≤ 20 |
| Insatisfatório | > 20 |

### M3.2: Percentual de Cobertura de Testes (PCT)

**Fórmula:** `PCT = (Linhas de código cobertas por testes / Total de linhas de código do sistema) × 100`

| Classificação | Valor |
|---------------|-------|
| Excelente | ≥ 80% |
| Bom | ≥ 70% |
| Regular | ≥ 50% |
| Insatisfatório | < 50% |

---

## 1.5. Escopo da Avaliação

| Elemento | Descrição |
|----------|-----------|
| O que será avaliado | O sistema Mural UnB com base na release *qualidade-de-software-mural* de 08/06/2026. O foco técnico recai sobre as operações de CRUD de postagens, o processamento de categorização via API do Gemini com payloads JSON e a análise estática da base de código. |
| O que não será avaliado | Características de Usabilidade da interface (vetada pela instrução pedagógica), Desempenho de rede sob estresse extremo e Segurança avançada contra invasões (Pentest). |
| Ambiente de teste e condições | Coleta realizada em ambiente controlado utilizando: Sistemas Operacionais: Ubuntu 22.04 LTS e Windows 11. Navegadores: Google Chrome e Mozilla Firefox em suas versões estáveis mais recentes. Infraestrutura: Automação via GitHub Actions para análise estática. |
| Responsáveis e papéis | Equipe de Avaliação: Paulo Nery, Ranni Heler, Thiago Melo, Matheus Rodrigues e Guilherme Zanella (divisão equitativa de 20% de participação). Supervisão: Professora da disciplina de Qualidade de Software. |

---

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 08/06/2026 | Criação da estrutura inicial da página com metodologia GQM, goals, questões, métricas e escopo da avaliação | Grupo Irmã Mary Keller |
