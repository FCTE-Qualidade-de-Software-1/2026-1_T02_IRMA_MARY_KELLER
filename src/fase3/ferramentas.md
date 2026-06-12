# 4. Ferramentas, Ambiente e Infraestrutura de Avaliação

Esta seção descreve o ecossistema técnico controlado onde a equipe de QA realizou as auditorias, detalhando as ferramentas que viabilizaram a geração de dados auditáveis.

## 4.1. Ambiente de Hardware e Dispositivos

**Estação de Trabalho Primária (QA Head):** Notebook executando ambiente nativo Linux Ubuntu de 64-bits, utilizado para execução dos comandos do PyTest, análise estática via Radon e execução dos scripts em Python 3.12.3.

**Dispositivo de Renderização Client:** Hardware local com monitor configurado em resolução padrão de 1080p, com suporte a inspeção via DevTools para monitoramento de renderização e estouro de exceções do motor JavaScript V8.

---

## 4.2. Ambiente de Software e Versões do Ecossistema

**Interpretador de Backend:** Python versão 3.12.3 estável com gerenciador de pacotes pip rodando sobre ambiente virtual isolado (venv).

**Runtime do Frontend:** Node.js integrado ao empacotador rápido Vite para execução e deploy local do servidor de desenvolvimento React + TypeScript.

**Navegador de Auditoria:** Google Chrome (versão estável mais recente) com o painel de ferramentas do desenvolvedor (F12) ativo de forma ininterrupta para captura de capturas de tela e rastreamento de pilha (stack traces).

---

## 4.3. Ferramentas de Coleta e Auditoria de Código

| Ferramenta | Versão | Finalidade |
|------------|--------|-----------|
| Radon | v6.0.1 | Análise estática para extração de complexidade ciclomática e atribuição de Ranks de legibilidade (A a F) |
| PyTest | v9.0.1 | Framework de execução de testes automatizados |
| PyTest-Cov | — | Geração de relatórios de cobertura de código integrados ao PyTest |
| ESLint | — | Checagem estática de conformidade e boas práticas de escrita de código TypeScript via `npm run lint` |

---

[← Voltar à Fase 3](../fase3.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.1 | 12/06/2026 | Revisão de linguagem; remoção de versão não verificada do PyTest-Cov | [Ranni Heler](https://github.com/AkaeRanni) |
| 1.0 | 11/06/2026 | Criação da seção de ferramentas e ambiente de avaliação | Paulo Nery Lobo |
