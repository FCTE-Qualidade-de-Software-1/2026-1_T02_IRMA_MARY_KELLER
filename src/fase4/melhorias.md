# 4. Melhorias Sugeridas e Plano de Ações Mitigadoras

Com base nas inconformidades detectadas e nos resultados insatisfatórios das métricas TPM, DDC e PCT, a equipe de avaliação propõe um conjunto de ações de engenharia corretiva para elevar os índices de qualidade do ecossistema.

---

## Módulo de Inteligência Artificial (M1.2)

### Implementação de Barreira Matemática (Corte por Threshold)

Configurar uma cláusula de barreira no script `alocar_tags_embeddings.py` baseada no score numérico de proximidade espacial. As análises mostram que os falsos negativos obtiveram média de score de **0.654**, enquanto os alinhamentos legítimos pontuaram acima de **0.720**. Definir um limite mínimo de corte de 0.720 mitigará a aprovação automática de conteúdos nocivos.

**Subcaracterística ISO 25010:** Segurança Semântica e Completude Funcional

---

### Introdução de Camada Ativa de Moderação (Guardrails)

Substituir a dependência exclusiva de modelos de embedding para a função de moderação. Recomenda-se acionar uma chamada prévia a um modelo classificador binário (LLM como Gemini Pro) através de um prompt de sistema estrito, responsável por validar e barrar fraudes acadêmicas e termos ofensivos antes da etapa de vetorização.

**Subcaracterística ISO 25010:** Correção Funcional e Integridade de Dados

---

## Frontend e Tolerância a Falhas (M2.1)

### Refatoração com Programação Defensiva no Loop de Tags

Alterar a linha 135 do arquivo `fetchOpportunities.ts` para envelopar a chamada do método `.map()`. Utilizar uma checagem explícita com `Array.isArray(lab.tags)` ou aplicar encadeamento opcional com operador de fallback (`lab.tags?.map(...) || []`), garantindo que estruturas corrompidas não quebrem o interpretador JavaScript.

**Subcaracterística ISO 25010:** Robustez e Tolerância a Falhas

---

### Saneamento de Requisições Assíncronas (NS_BINDING_ABORTED)

Implementar um mecanismo de tratamento de erros nas requisições assíncronas do frontend para evitar o cancelamento em cascata. Utilizar blocos `try/catch` ou interceptores globais para capturar falhas de vinculação de recursos de mídia, garantindo que componentes periféricos não congelem silenciosamente e que os erros sejam expostos de forma legivel ao desenvolvedor, não apenas no painel F12.

**Subcaracterística ISO 25010:** Resiliência de Interface e Maturidade de Produto

---

### Configuração de Fronteiras de Erro Globais (Error Boundaries)

Implementar componentes do tipo `Error Boundary` na raiz da árvore do React. Esta infraestrutura isolará falhas de renderização locais em componentes específicos, impedindo que uma exceção não tratada propague por todo o ecossistema e cause o colapso completo do sistema em tela preta.

**Subcaracterística ISO 25010:** Disponibilidade e Recuperabilidade

---

## Manutenibilidade e Infraestrutura (M3.2 & M3.3)

### Provisionamento de Framework de Testes no Frontend

Configurar a infraestrutura de automação de testes no diretório `site/` utilizando **Jest** ou **Vitest** integrado à React Testing Library. Mapear o script `"test"` no `package.json` para eliminar a zona escura de 0% de cobertura, mitigando riscos de erros de regressão visual na listagem de cards.

**Subcaracterística ISO 25010:** Testabilidade e Coexistência

---

### Descentralização de Fluxo Lógico (Refatoração de Complexidade)

Aplicar o padrão de refatoração *Extract Method* nas funções `encontrar_imagem_para_lab` e `extrair_laboratorios_fga_pdf` do arquivo `extrair_labs_fga.py`. A quebra de blocos procedurais com complexidades de 72 e 66 em subfunções menores e coesas reduzirá o acoplamento e elevará o índice de manutenibilidade do código backend.

**Subcaracterística ISO 25010:** Modularidade e Modificabilidade

---

### Padronização do Barramento de Credenciais

Uniformizar as chamadas de configuração da API da Google em todos os scripts Python do repositório, elegendo uma chave única (`GEMINI_API_KEY`) e adaptando a leitura automática via biblioteca `dotenv`, encerrando a colisão de nomenclaturas no terminal.

**Subcaracterística ISO 25010:** Instabilidade e Analisabilidade

---

[← Voltar à Fase 4](../fase4/dados-brutos.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 12/06/2026 | Criação do plano de ações mitigadoras | Matheus Rodrigues |
