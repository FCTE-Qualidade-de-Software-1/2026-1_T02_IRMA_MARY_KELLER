# Fase 4 — Execução da Avaliação

Esta fase registra a execução do plano de avaliação definido na Fase 3. Os dados brutos foram coletados conforme as instruções dos casos de teste, as métricas foram calculadas e os resultados são confrontados com os critérios de julgamento estabelecidos na Fase 2, conduzindo ao julgamento final da qualidade do Mural UnB.

## Seções

- [1. Dados Brutos Coletados](fase4/dados-brutos.md)
- [2. Cálculo das Métricas](fase4/metricas.md)
- [3. Avaliação das Hipóteses](fase4/hipoteses.md)
- [4. Melhorias Sugeridas](fase4/melhorias.md)

---

## Resumo dos Resultados

A tabela a seguir consolida os resultados de todas as métricas definidas no framework GQM e aplicadas nesta fase de execução.

| Métrica | Descrição | Resultado | Julgamento |
|---------|-----------|-----------|------------|
| M1.1 — ICF | Índice de Completude Funcional | 100% | **Excelente** |
| M1.2 — TPM | Taxa de Precisão da Moderação (IA) | 45% | **Insatisfatório** |
| M2.1 — DDC | Densidade de Defeitos Críticos | 1,00 | **Insatisfatório** |
| M3.1 — CCM | Complexidade Ciclomática Média | 13,53 | **Bom** |
| M3.2 — PCT | Percentual de Cobertura de Testes | < 50% | **Insatisfatório** |

---

## Julgamento Global por Característica

### Adequação Funcional — Parcialmente Satisfatória

A completude funcional do sistema (CRUD e filtros) atingiu 100% de aprovação, demonstrando que o Mural UnB executa corretamente todas as operações essenciais de sua proposta de valor. No entanto, a precisão da moderação por IA apresentou resultado crítico (45%), comprometendo a característica de correção funcional: o sistema aprova automaticamente todo conteúdo impróprio submetido, comprometendo a integridade do conteúdo publicado e a confiança dos usuários na plataforma.

### Confiabilidade — Insatisfatória

A densidade de defeitos críticos atingiu o valor máximo possível (DDC = 1,00): o único caso de teste de tolerância a falhas executado resultou em colapso total da interface. A ausência de programação defensiva no frontend expõe o sistema a falhas irreversíveis em cenários de dados corrompidos, invalidando a subcaracterística de Tolerância a Falhas do modelo ISO/IEC 25010.

### Manutenibilidade — Parcialmente Satisfatória

A complexidade ciclomática média do código-fonte foi classificada como Bom (CCM = 13,53), indicando que a base de código em geral está dentro de limites aceitáveis de manutenção. Contudo, a cobertura de testes automatizados está Insatisfatória (PCT < 50%), devido à ausência total de um framework de testes no frontend React. Essa assimetria deixa a camada de interface vulnerável a regressões e compromete a evolução segura do projeto por novos desenvolvedores.

---

## Coerência com o Propósito da Avaliação (Fase 1)

O propósito declarado na Fase 1 foi **documentar o estado atual de qualidade do Mural UnB, identificar não-conformidades e fornecer insumos para decisões de melhoria** — sem caráter punitivo ou classificatório do software.

Os resultados obtidos atendem integralmente a esse propósito:

1. **Documentação do estado atual**: as cinco métricas calculadas oferecem um retrato quantitativo e auditável da qualidade nas três características priorizadas.
2. **Identificação de não-conformidades**: três métricas atingiram classificação Insatisfatório (TPM = 45%, DDC = 1,00, PCT < 50%), e duas funções do backend apresentaram complexidade crítica de Rank F (CC = 72 e CC = 66), evidenciando falhas concretas com localização precisa no código.
3. **Insumos para melhoria**: a Fase 4 entrega um plano de ações corretivas detalhado com sete medidas de engenharia, cada uma referenciando a subcaracterística ISO 25010 afetada e o módulo de código específico a ser modificado.

O requisitante (Profa. Cristiane Ramos) e as partes interessadas (equipe de desenvolvimento do Mural UnB) dispõem, ao final desta avaliação, de evidências auditáveis e recomendações acionáveis para elevar os índices de qualidade do sistema nas áreas críticas identificadas.

---

## Relação entre as Características Avaliadas

A Fase 1 antecipou uma hipótese sobre a inter-relação entre as três características: *"espera-se que baixa manutenibilidade aumente a incidência de defeitos funcionais e de confiabilidade."* Os resultados da Fase 4 permitem analisar essa relação com base em evidências.

A relação foi **confirmada no caso da confiabilidade**: a ausência de cobertura de testes automatizados no frontend (M3.2 < 50% — Manutenibilidade insatisfatória) deixou a camada de interface sem salvaguardas contra regressões, o que contribuiu diretamente para o colapso total observado no CT-CONF-01 (M2.1 = 1,00 — Confiabilidade insatisfatória). Um frontend com testes configurados teria detectado a ausência de programação defensiva antes de chegar ao ambiente de execução.

A relação foi **parcialmente observada no caso da adequação funcional**: as duas funções com Rank F de complexidade (CC = 72 e CC = 66) concentram parte da lógica de moderação de dados, e a falha de precisão da IA (M1.2 = 45%) ocorre exatamente nessa cadeia de processamento. Embora a causa principal seja a ausência de um classificador binário, a alta complexidade ciclomática das funções de moderação dificulta a análise e correção do problema.

Em síntese, a Manutenibilidade insatisfatória (PCT) atuou como fator amplificador das falhas de Confiabilidade, confirmando a hipótese da Fase 1 para esse eixo.

---

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 2.0 | 12/06/2026 | Adição da seção "Relação entre as Características Avaliadas" | [Ranni Heler](https://github.com/AkaeRanni) |
| 1.0 | 12/06/2026 | Criação da visão geral, resumo de resultados e julgamento final da Fase 4 | [Ranni Heler](https://github.com/AkaeRanni) |
