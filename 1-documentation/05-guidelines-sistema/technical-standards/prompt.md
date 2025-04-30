# technical-standards

# Prompt para Technical Standards

## Contexto do Projeto

Estou desenvolvendo um sistema [descreva o tipo e escopo do sistema] chamado [nome do sistema]. O projeto utilizará [mencione tecnologias iniciais, se já definidas] e deverá atender requisitos de [desempenho, escalabilidade, disponibilidade, etc. relevantes].

## Escopo do Documento

Preciso criar um documento de padrões técnicos abrangente que defina as tecnologias, arquitetura, padrões de codificação e interfaces a serem utilizadas no desenvolvimento do sistema. Este documento será a referência técnica principal para toda a equipe de desenvolvimento.

## Requisitos para Elaboração

Por favor, ajude-me a criar um documento de Technical Standards completo que inclua:

### 1. Stack Tecnológica

Por favor, forneça recomendações e justificativas para:

- **Linguagens de Programação**:

  - Linguagens principais e auxiliares
  - Versões específicas a serem utilizadas
  - Frameworks e bibliotecas padronizadas
  - Ferramentas de build e compilação

- **Tecnologias de Front-end**:

  - Frameworks e bibliotecas (React, Angular, Vue, etc.)
  - Gerenciamento de estado
  - Tecnologias CSS (pré-processadores, metodologias)
  - Empacotadores e ferramentas de build

- **Tecnologias de Back-end**:

  - Frameworks de servidor
  - Processamento assíncrono
  - Caching e otimização
  - Middlewares padrão

- **Persistência de Dados**:

  - Bancos de dados relacionais
  - Bancos de dados NoSQL
  - Estratégias de ORM/ODM
  - Caching e armazenamento de conteúdo estático

- **DevOps e Infraestrutura**:
  - Estratégias de containerização
  - Orquestração e auto-scaling
  - Pipelines de CI/CD
  - Monitoramento e observabilidade

### 2. Arquitetura de Referência

- **Padrão Arquitetural**:

  - Macro-arquitetura do sistema (monolito, microserviços, serverless)
  - Organização de componentes
  - Estratégias de modularização
  - Diagrama arquitetural de referência

- **Padrões de Comunicação**:

  - Design de APIs (REST, GraphQL, gRPC)
  - Comunicação assíncrona (filas, eventos)
  - Formatos de mensagem (JSON, Protocol Buffers)
  - Gateways e proxies

- **Estratégias de Escalabilidade**:

  - Escalabilidade horizontal vs. vertical
  - Load balancing e distribuição de carga
  - Particionamento de dados
  - Caching em múltiplos níveis

- **Mecanismos de Resiliência**:
  - Circuit breaking
  - Retry policies
  - Timeout strategies
  - Fallbacks e degradação graceful

### 3. Padrões de Codificação

- **Organização do Código**:

  - Estrutura de diretórios
  - Modularização e encapsulamento
  - Gerenciamento de dependências
  - Convenções de nomenclatura

- **Padrões de Design**:

  - Padrões recomendados (Factory, Repository, etc.)
  - Injeção de dependências
  - Abstrações e interfaces
  - Princípios SOLID e outras boas práticas

- **Qualidade de Código**:

  - Métricas a serem monitoradas
  - Coberturas mínimas de testes
  - Complexidade ciclomática
  - Ferramentas de análise estática

- **Gestão de Configuração**:
  - Estratégias para diferentes ambientes
  - Gerenciamento de segredos
  - Feature flags
  - Configuração externa vs. hardcoded

### 4. Padrões de Interface

- **Design de APIs**:

  - Convenções de URLs e recursos
  - Versionamento de APIs
  - Padrões de resposta e códigos de erro
  - Paginação, filtragem e ordenação

- **Documentação Técnica**:
  - Padrões de documentação (OpenAPI, Swagger)
  - Documentação de código
  - Níveis de documentação requeridos
  - Manutenção da documentação

## Considerações Específicas

- **Escalabilidade**: Nosso sistema precisa suportar [volume esperado] usuários concorrentes
- **Disponibilidade**: Precisamos atingir [nível de SLA] de disponibilidade
- **Latência**: Os tempos de resposta devem ser inferiores a [limite aceitável]
- **Conformidade**: Precisamos atender a [padrões ou regulamentações específicas]
- **Integração**: O sistema precisará integrar-se com [sistemas externos]

## Resultado Esperado

Um documento abrangente de padrões técnicos que forneça direção clara e específica para decisões tecnológicas, design e implementação, resultando em um sistema consistente, manutenível e que atenda aos requisitos não-funcionais estabelecidos.
