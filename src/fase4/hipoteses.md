# 3. Avaliação das Hipóteses e Discussão dos Resultados

O cruzamento dos dados brutos com as métricas calculadas permite validar as hipóteses levantadas na especificação e extrair diagnósticos profundos sobre a maturidade do Mural UnB.

---

## H1.1 — Impedimentos na Atualização da Interface

**Status: Rejeitada**

A hipótese previa impedimentos na atualização da interface por falhas em endpoints REST. Foi rejeitada pelo fato de o sistema adotar uma arquitetura de carregamento estático baseada em Jamstack. A consolidação dos arquivos JSON via script Python ocorre de forma local e pré-compilada, garantindo que os filtros funcionem de forma rápida, validando a métrica M1.1 com **100% de aproveitamento**.

---

## H2.1 — Falsos Positivos na Moderação da IA

**Status: Refutada (resultado oposto ao previsto)**

A hipótese previa que a IA falharia gerando taxas elevadas de **falsos positivos** (barrar o que deveria passar). Os dados brutos da métrica M1.2 refutaram essa hipótese de forma surpreendente, revelando o oposto: o sistema opera com **100% de falsos negativos** (aprovou todos os conteúdos impróprios).

O modelo `text-embedding-004` gerou coordenadas no espaço vetorial para frases ofensivas ou comerciais e as associou de maneira ingênua às categorias menos distantes do dicionário — como alocar o insulto na categoria *Robótica* com score de 0.6680. Isso comprova que o pipeline carece de uma barreira matemática de corte ou de um classificador lógico de segurança.

---

## H3.1 — Interrupções por Campos Nulos ou Corrompidos

**Status: Confirmada**

A hipótese foi confirmada com densidade máxima de defeitos. O frontend em React não apresentou programação defensiva para lidar com falhas no parsing de arquivos externos. O motor JavaScript V8 interrompeu o fluxo de controle da página ao tentar executar `.map()` em uma estrutura que não era um array válido (`fetchOpportunities.ts`, linha 135), seguido de um erro `NS_BINDING_ABORTED` que causou o cancelamento em cascata de todas as requisições assíncronas ativas, congelando os componentes em estado estático com falhas silenciosas visíveis apenas no painel F12.

---

## H5.1 — Ausência de Testes Automatizados

**Status: Confirmada**

A hipótese foi inteiramente confirmada pela métrica M3.2. A ausência total de um framework de automação de testes no ecossistema do frontend deixa toda a camada de interface desprotegida contra erros de regressão. Embora o backend possua 126 testes lógicos consistentes, a falta de simetria com o frontend fragiliza a evolução segura do código por novos engenheiros de software.

---

[← Voltar à Fase 4](../fase4/dados-brutos.md)

## Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 12/06/2026 | Criação da avaliação das hipóteses e discussão dos resultados | Matheus Rodrigues |
