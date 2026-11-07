# Homebroker

Projeto de estudo que simula partes de um homebroker, usando a stack comum em sistemas do mercado financeiro: Java, Spring Boot, Kafka e PostgreSQL.

O objetivo é praticar, de ponta a ponta, como dados de mercado são recebidos, tratados e entregues em tempo real, e depois evoluir para o fluxo de negociação, com ordens de compra e venda.

## O que o projeto faz

### Primeiro: cotações em tempo real

- Recebe cotações de ações subindo e descendo
- Processa e distribui essas cotações via Kafka
- Guarda o histórico de preços
- Mostra os preços atualizados e um gráfico na tela, em tempo real

### Depois: negociação

- Envio e cancelamento de ordens de compra e venda
- Motor de casamento de ordens, com livro de ofertas e prioridade preço-tempo
- Checagem de risco antes da execução
- Posição, preço médio e resultado (P&L) marcados a mercado com as cotações

## Stack

| Tecnologia | Uso |
|---|---|
| Java 21 | Linguagem |
| Spring Boot 3 | Aplicações e APIs |
| Apache Kafka | Comunicação por eventos entre os módulos |
| PostgreSQL + Flyway | Banco de dados e migrações versionadas |
| JUnit 5 + Testcontainers | Testes unitários e de integração |
| Docker Compose | Ambiente local |
| JaCoCo | Cobertura de testes |
| Maven multi-módulo | Build |

## Módulos

| Módulo | Responsabilidade |
|---|---|
| `homebroker-core` | Regras de negócio puras (ativo, cotação, ordem, conta, posição), sem dependência de framework |
| `homebroker-marketdata` | Gera ou recebe as cotações e publica no Kafka |
| `homebroker-events` | Contratos dos eventos trocados via Kafka, versionados e com schema explícito |
| `homebroker-api` | API REST e entrega das cotações em tempo real para a tela |
| `homebroker-matching` | Motor de casamento de ordens |
| `homebroker-risk` | Checagem de limites de saldo e exposição por ativo |
| `homebroker-test-e2e` | Testes de ponta a ponta com Testcontainers |

## Roadmap

1. **Fundamentos:** ambiente, Maven multi-módulo, fluxo de Git e domínio com testes
2. **Cotações em tempo real:** geração de cotações, Kafka, histórico no banco e atualização ao vivo na tela
3. **Ordens:** API de envio e cancelamento e motor de casamento
4. **Risco e resultado:** risco pré-trade, posição, P&L e marcação a mercado

O andamento de cada fase fica nas [issues](../../issues) e nos [milestones](../../milestones).

## Status

🚧 Fase 1, configuração do ambiente e estrutura do projeto.

## Como rodar

Em construção. As instruções entram junto com o ambiente Docker Compose.

## Como contribuir

Veja o [guia de contribuição](CONTRIBUTING.md).