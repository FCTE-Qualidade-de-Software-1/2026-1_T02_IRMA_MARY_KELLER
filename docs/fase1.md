# Fase 1 - Processo de Avaliação

## 1. Contexto de Trabalho

Este trabalho foi desenvolvido na disciplina **Qualidade de Software** com o objetivo de aplicar na prática as técnicas, normas e boas práticas que garantem a qualidade de produtos e processos ao longo do ciclo de vida do software. 

Como atividade central, realizamos uma análise crítica de uma plataforma real, avaliando critérios técnicos fundamentados na norma **ISO/IEC 25010**. 

O resultado esperado é identificar **não conformidades** e **possibilidades de melhoria** no software, propondo recomendações objetivas para melhorar seu nível de maturidade e confiabilidade técnica.

---

## 2. Aplicação Escolhida

O software avaliado neste trabalho é o **[Mural UnB](https://github.com/unb-mds/2025-2-Mural-UnB)**, uma plataforma digital desenvolvida para centralizar e organizar a divulgação de informações, eventos e avisos dentro da comunidade acadêmica da Universidade de Brasília.

### Objetivo da Plataforma

O projeto visa **substituir ou complementar** os murais físicos e grupos informais de mensagens, oferecendo um ambiente estruturado onde discentes e docentes podem publicar e visualizar anúncios categorizados por curso, campus ou interesse geral.

### Problemas Resolvidos

Como uma aplicação moderna voltada ao contexto universitário, o Mural UnB busca resolver:
- **Dispersão de informação** entre diferentes canais
- **Falta de visibilidade** de eventos acadêmicos
- Necessidade de um **ambiente centralizado** e estruturado

### Características Principais

A plataforma permite:
- ✅ Gestão de postagens
- ✅ Filtragem por categorias
- ✅ Sistema de moderação
- ✅ Garantia de integridade dos conteúdos publicados

### Arquitetura e Escalabilidade

A arquitetura do projeto é projetada para ser **escalável** e de **fácil manutenção**, permitindo a evolução das funcionalidades conforme as demandas da comunidade universitária crescem.

### Critérios de Qualidade Avaliados

A avaliação do software considera critérios de qualidade essenciais para sistemas de gestão de conteúdo e interação comunitária, focando especificamente em:

- **Adequação Funcional**: Verifica se o conjunto de funções fornecidas atende às necessidades específicas dos usuários
- **Confiabilidade**: Avalia a capacidade do sistema de manter seu nível de desempenho sob condições estabelecidas
- **Manutenibilidade**: Mede a eficácia e eficiência com que o software pode ser modificado para correções ou melhorias

---

## 3. Requisitante e Partes Interessadas

Em conformidade com o processo **SQuaRE**, foram identificadas as partes interessadas relevantes para o software:

| Tipo | Descrição |
|------|-----------|
| **Requisitante** | Professora responsável pela disciplina de Qualidade de Software |
| **Stakeholders** | Estudantes da UnB (usuários principais), docentes e pesquisadores, equipe de desenvolvimento (MDS/GPP), administradores do sistema, Secretaria de Comunicação da UnB |

---

## 4. Classificação do Tipo de Produto

A classificação do produto **Mural UnB**, essencial para definir o escopo de implementação e manutenção, é a seguinte:

| Aspecto | Descrição |
|--------|-----------|
| **Tipo de software** | Aplicação web de gestão de conteúdo |
| **Categoria** | Sistema de Mural Digital e Avisos Acadêmicos |
| **Natureza** | Sistema multiusuário, interativo, com persistência de dados |
| **Modelo de implantação** | Baseado em nuvem (SaaS) ou hospedagem institucional via web |

### Base Tecnológica

- **Frontend**: React com TypeScript e Tailwind CSS
- **Processamento de Dados e Integração**: Python (biblioteca pandas), API REST Gemini, JSON e GitHub Actions
- **Ecossistema de Desenvolvimento e Documentação**: Git, GitHub, GitHub Pages e MkDocs

---

## 5. Propósito da Avaliação e Uso Pretendido dos Resultados

O propósito desta avaliação é analisar a qualidade do **Mural UnB** com foco nas características de **Adequação Funcional**, **Confiabilidade** e **Manutenibilidade**.

Os resultados obtidos serão utilizados para:

1. **Documentar o estado técnico atual** do software, verificando se as funcionalidades entregues são consistentes com os requisitos levantados

2. **Identificar falhas de estabilidade**, erros de lógica e gargalos de manutenção que possam comprometer a evolução do projeto

3. **Prover embasamento técnico** para a tomada de decisão sobre futuras refatorações e adições de funcionalidades

---

## 6. Modelo de Qualidade (ISO/IEC 25010) e Adaptação

O modelo de qualidade adotado segue a norma **ISO/IEC 25010**. Para esta fase, o foco será restrito a três características principais, sendo a **Usabilidade** explicitamente vetada por diretrizes metodológicas.

### Características Selecionadas para Avaliação

#### 📋 Adequação Funcional
Avalia se as funções atendem às necessidades declaradas
- Completude funcional
- Correção funcional

#### ⚙️ Confiabilidade
Mede o desempenho sob condições específicas
- Maturidade
- Disponibilidade

#### 🔧 Manutenibilidade
Avalia a facilidade de modificação do código
- Modularidade
- Analisabilidade

---

## 7. Classificação e Ênfase das Características de Qualidade

A priorização foi definida através de **consenso técnico da equipe**, utilizando uma **escala de 0 a 5**.

| Característica | Ênfase (0-5) | Justificativa |
|---|---|---|
| **Adequação Funcional** | **5** | Essencial para garantir que o mural cumpra seu papel de publicação sem erros de lógica |
| **Confiabilidade** | **4** | Garantia de que o sistema não apresente quedas em períodos de alto volume de postagens |
| **Manutenibilidade** | **4** | Fundamental para permitir que novos desenvolvedores contribuam no projeto open source |
| **Segurança** | **2** | Relevante, mas não lida com dados financeiros ou sensíveis de alta criticidade nesta etapa |

---

## 8. Escopo, Profundidade e Objetos da Avaliação

### Escopo

- ✅ Interface de usuário (Frontend)
- ✅ Operações de CRUD de anúncios e sistema de autenticação
- ✅ API de comunicação entre Frontend e Backend

### Profundidade

- 🔍 Inspeção técnica de código e análise de logs
- 🔍 Testes funcionais de caixa-preta e caixa-branca

### Objetos Avaliados

- 📦 Módulos de postagens, categorias e gerenciamento de usuários
- 📦 Documentação técnica e estrutura do repositório Git

---

## 9. Proposta de Avaliação e Melhoria de Qualidade

A proposta visa garantir que o **Mural UnB** seja uma ferramenta **robusta** e **confiável**.

A avaliação será conduzida por meio de:

- ✅ **Testes automatizados e manuais**
- ✅ **Foco na integridade dos dados**
- ✅ **Avaliação da facilidade de manutenção** da base de código

Serão aplicadas **métricas de cobertura de código** e **densidade de defeitos** para identificar áreas críticas para refatoração.

---

## 10. Conexão com ODS da ONU

O Mural UnB conecta-se aos **Objetivos de Desenvolvimento Sustentável** da Agenda 2030:

| ODS | Descrição |
|-----|-----------|
| **ODS 4 – Educação de Qualidade** | Democratiza o acesso a eventos acadêmicos e monitorias |
| **ODS 9 – Indústria, Inovação e Infraestrutura** | Fomenta o desenvolvimento de tecnologias de código aberto na universidade |
| **ODS 16 – Paz, Justiça e Instituições Eficazes** | Promove a transparência na comunicação institucional |

---

## 11. Referências Bibliográficas

- **[1]** ISO/IEC 25010. Systems and software engineering — SQuaRE — Quality models
- **[2]** ISO/IEC 25023. Measurement of system and software product quality
- **[3]** Mural UnB. Repositório: [https://github.com/unb-mds/2025-2-Mural-UnB](https://github.com/unb-mds/2025-2-Mural-UnB)
- **[4]** ONU Brasil. Objetivos de Desenvolvimento Sustentável

---

## 12. Tabela de Participação

A tabela de contribuição foi movida para a página [Tabela de Contribuição](contribuicao.md).

---
