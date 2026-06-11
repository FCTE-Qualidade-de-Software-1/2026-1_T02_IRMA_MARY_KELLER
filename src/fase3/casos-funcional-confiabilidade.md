# 2. Casos de Teste — Adequação Funcional e Confiabilidade

## CT-FUNC-01: Verificação de CRUD e Filtros Estáticos

**Métrica Associada:** M1.1 (Isolamento de Componentes e Agregação de Dados)

**Objetivo:** Garantir que o script de consolidação unifique os dados e que a interface reaja corretamente às regras de filtro por categoria sem perda de integridade.

**Pré-condições:** Arquivos `labs_fga.csv` e editais de EJs carregados na pasta de dados.

**Passos de Execução:**

1. Executar o script de unificação no terminal: `python scripts/juntar_oportunidades.py`
2. Verificar a saída gerada na pasta de destino do frontend.
3. Abrir o site local via `npm run dev` e realizar a filtragem por uma categoria específica (ex: "Laboratórios").
4. Forçar uma atualização de página (F5) e checar a persistência da listagem na tela.

**Resultado Esperado:** O script unifica os dados com sucesso. O frontend aplica os filtros isolando as categorias de forma correta sem apresentar congelamento ou loops infinitos de renderização.

---

## CT-FUNC-02: Precisão da Moderação da IA

**Métrica Associada:** M1.2 (Taxa de Precisão Semântica - Acurácia)

**Objetivo:** Medir a taxa de assertividade do pipeline utilizando embeddings para classificar e filtrar conteúdos maliciosos, ofensivos ou fora de escopo.

**Massa de Dados de Entrada:** Submissão controlada de 20 strings contendo anúncios válidos e posts nocivos (ofensas, fraude acadêmica, spams comerciais).

**Passos de Execução:**

1. Alimentar o arquivo semente `data/mock/tags_no_embeddings.json` com a lista de 20 frases de controle.
2. Rodar o pipeline no terminal:
```bash
python scripts/generate_embeddings_gemini.py
python scripts/alocar_tags_embeddings.py
```
3. Abrir a matriz resultante em `data/Labs/labs_com_tags_embeddings.json` e auditar quais tags foram vinculadas e o score associado a cada frase.

**Resultado Esperado:** O pipeline deve processar as strings através do modelo `text-embedding-004`. O algoritmo deve demonstrar alta acurácia, alocando tags acadêmicas corretas para publicações legítimas e rejeitando ou isolando publicações com conteúdo impróprio (comércio, ofensas e spams) através do cálculo correto da distância vetorial.

---

## CT-CONF-01: Resiliência do Frontend a Payloads Corrompidos

**Métrica Associada:** M2.1 (Tolerância a Falhas na Camada de Parsing)

**Objetivo:** Avaliar a robustez do frontend do Mural UnB em React/TypeScript quando submetido a arquivos JSON estáticos que sofreram corrupção de tipo, ausência de delimitadores ou valores nulos em atributos obrigatórios.

**Pré-condições:** Aplicação executando localmente via servidor de desenvolvimento Vite.

**Passos de Execução:**

1. Navegar até a pasta `data/Labs/` e abrir o arquivo contendo a estrutura de objetos dos trinta e quatro laboratórios mapeados.
2. Injetar a falha intencionalmente no primeiro bloco de dados da lista: definir o valor do campo `nome` como `null` no registro de identificador `200001` e corromper a abertura da lista `tags`, removendo o caractere de abertura de bloco de modo a transformar a primeira tag num par chave-valor isolado. Salvar o arquivo.
3. Recarregar a página da aplicação no navegador e acionar o console do desenvolvedor por meio da tecla F12.

**Resultado Esperado (Oráculo de Teste):** O ecossistema do frontend em React deve operar de forma defensiva através de mecanismos de proteção contra dados corrompidos. O sistema deve capturar a excessão de parse sem interromper a execução geral, aplicando um fallback que descarte ou oculte unicamente o nó afetado do laboratório CIP-TransEnerg (ID 200001), mantendo a renderização e o funcionamento normal dos restantes trinta e três laboratórios íntegros na interface, sem congelamento de componentes ou falhas ocultas no Console.

---

[← Voltar à Fase 3](../fase3/planejamento.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.1 | 11/06/2026 | Atualização do resultado esperado do CT-FUNC-02 | Paulo Nery Lobo |
| 1.0 | 11/06/2026 | Criação dos casos de teste de adequação funcional e confiabilidade | Paulo Nery Lobo |
