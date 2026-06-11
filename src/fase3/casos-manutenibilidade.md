# 3. Casos de Teste — Manutenibilidade e Testabilidade

## CT-MAIN-01: Verificação de Cobertura de Código (Statement Coverage)

**Métrica Associada:** M3.2 (Percentual de Cobertura de Testes - PCT)

**Objetivo:** Quantificar o volume de linhas e ramificações condicionais que estão blindadas por testes automatizados contra erros de regressão.

**Passos de Execução:**

1. Instalar o plugin de cobertura no ambiente virtual:
```bash
pip install pytest-cov
```
2. Executar a suíte de testes do backend gerando a matriz em HTML:
```bash
pytest --cov=scripts --cov-report=html
```
3. Tentar executar a rotina de testes integrada no frontend React:
```bash
npm run test -- --coverage
```

**Resultado Esperado:** O pipeline deve processar as strings através do modelo `text-embedding-004`. O algoritmo deve demonstrar alta acurácia, alocando tags acadêmicas corretas para publicações legítimas e rejeitando ou isolando publicações com conteúdo impróprio (comércio, ofensas e spams) através do cálculo correto da distância vetorial.

---

## CT-MAIN-02: Avaliação de Complexidade Ciclomática (Radon)

**Métrica Associada:** M3.3 (Mapeamento de Rank de Complexidade de Fluxo)

**Objetivo:** Isolar e pontuar funções monolíticas que contenham desvios excessivos, elevando o custo de manutenção do projeto.

**Passos de Execução:**

1. Instalar a ferramenta Radon no terminal:
```bash
pip install radon
```
2. Executar a varredura de complexidade ciclomática com foco nas funções, métodos e classes:
```bash
radon cc scripts/ -a -s
```

**Resultado Esperado:** O relatório deve mapear todas as estruturas de controle do projeto. Espera-se que as funções e métodos apresentem um fluxo linear e coeso, mantendo os índices de complexidade dentro dos limites aceitáveis de desenvolvimento (Ranks A ou B), garantindo que o código seja de fácil leitura, manutenção e expansão.

---

[← Voltar à Fase 3](../fase3/planejamento.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.1 | 11/06/2026 | Atualização dos resultados esperados do CT-MAIN-01 e CT-MAIN-02 | Paulo Nery Lobo |
| 1.0 | 11/06/2026 | Criação dos casos de teste de manutenibilidade e testabilidade | Paulo Nery Lobo |
