# Prompts para High-Level Design (HLD)

Este documento contém prompts específicos para auxiliar na criação do High-Level Design (HLD) do seu sistema.

## Prompt para Visão Geral da Arquitetura

```
Atue como um arquiteto de software experiente especializado em desenhar arquiteturas de alto nível.

Contexto do projeto:
- Nome do sistema: [nome do sistema]
- Propósito principal: [descreva o propósito principal]
- Requisitos não-funcionais prioritários: [escalabilidade, performance, segurança, etc.]
- Contexto tecnológico: [tecnologias/plataformas obrigatórias ou preferidas]

Com base nessas informações, preciso que você me ajude a criar a seção "Visão Geral da Arquitetura" do documento de High-Level Design (HLD) do sistema, incluindo:

1. Recomendação do estilo arquitetural mais adequado (microserviços, monolítico, event-driven, serverless, etc.) com justificativa
2. Um diagrama de arquitetura de alto nível (descreva textualmente os elementos e suas relações)
3. Princípios arquiteturais que devem ser seguidos neste projeto
4. Considerações técnicas importantes e possíveis restrições

Forneça sua resposta em formato estruturado e priorize clareza sobre complexidade desnecessária.
```

## Prompt para Componentes Principais

```
Atue como um arquiteto de sistemas especializado em identificar e estruturar componentes de software.

Com base na arquitetura geral [descreva brevemente a arquitetura escolhida] para o sistema [nome do sistema], preciso que você me ajude a identificar e descrever os componentes principais para a seção de "Componentes Principais" do HLD.

Para cada componente principal, forneça:
1. Nome do componente
2. Propósito e responsabilidades principais
3. Funcionalidades-chave que o componente oferece
4. Dependências com outros componentes
5. Considerações especiais ou restrições

Organizados em categorias lógicas como:
- Componentes de interface do usuário
- Componentes de lógica de negócio
- Componentes de acesso a dados
- Componentes de infraestrutura/suporte
- Integrações externas

Mantenha o nível de detalhe apropriado para um documento de alto nível, evitando especificidades de implementação.
```

## Prompt para Interfaces e Comunicação

```
Atue como um especialista em integração de sistemas e design de APIs.

Para o sistema [nome do sistema] com a arquitetura [descreva brevemente], preciso definir como os componentes principais se comunicarão entre si. Ajude-me a elaborar a seção "Interfaces e Comunicação" do HLD, abordando:

1. APIs principais entre componentes:
   - Quais componentes expõem quais APIs
   - Propósito de cada API
   - Padrões de design de API recomendados (REST, GraphQL, gRPC, etc.)

2. Protocolos de comunicação:
   - Quais protocolos serão utilizados (HTTP, WebSockets, mensageria, etc.)
   - Justificativa para a escolha de cada protocolo

3. Formatos de dados:
   - Formatos para troca de informações (JSON, XML, Protocol Buffers, etc.)
   - Exemplos conceituais de estruturas de dados importantes

4. Padrões de integração:
   - Estratégias para comunicação síncrona vs. assíncrona
   - Mecanismos de reliable messaging, se aplicáveis
   - Estratégias para resiliência na comunicação

Mantenha o foco em decisões de alto nível, sem entrar em detalhes de implementação.
```

## Prompt para Dados e Persistência

```
Atue como um arquiteto de dados experiente.

Para o sistema [nome do sistema], preciso definir a estratégia de dados e persistência em alto nível. Ajude-me a elaborar a seção "Dados e Persistência" do HLD, incluindo:

1. Visão geral do modelo de dados:
   - Principais entidades e seus relacionamentos
   - Categorização de dados (transacionais, analíticos, etc.)
   - Considerações sobre volume e crescimento de dados

2. Estratégia de armazenamento:
   - Tipos de armazenamento recomendados (SQL, NoSQL, híbrido)
   - Justificativa para as escolhas com base nos requisitos
   - Abordagem para distribuição de dados, se aplicável

3. Mecanismos de persistência:
   - Recomendações para bancos de dados específicos
   - Estratégias de cache
   - Considerações sobre armazenamento de estado

4. Fluxos de dados principais:
   - Como os dados fluem entre componentes
   - Transformações de dados importantes
   - Mecanismos de sincronização ou replicação

Mantenha as recomendações em nível arquitetural, sem especificar detalhes de implementação como esquemas ou queries.
```

## Prompt para Mapeamento de Requisitos Não-Funcionais

```
Atue como um arquiteto de sistemas especializado em requisitos não-funcionais.

Para o sistema [nome do sistema], preciso mapear como a arquitetura proposta atenderá aos requisitos não-funcionais críticos. Ajude-me a elaborar a seção "Mapeamento de Requisitos Não-Funcionais" do HLD, abordando:

1. Performance:
   - Como a arquitetura suportará os requisitos de performance
   - Estratégias para otimização de desempenho
   - Considerações sobre tempos de resposta e throughput

2. Escalabilidade:
   - Abordagem para escala horizontal e vertical
   - Estratégias para lidar com aumento de carga
   - Componentes que exigirão atenção especial para escalabilidade

3. Segurança:
   - Princípios de segurança incorporados na arquitetura
   - Estratégias para autenticação e autorização
   - Proteção de dados e comunicações
   - Compliance com regulamentações relevantes

4. Disponibilidade e Resiliência:
   - Estratégias para alta disponibilidade
   - Mecanismos de tolerância a falhas
   - Abordagem para recuperação de desastres
   - Estratégias de redundância

Relate cada solução arquitetural diretamente aos requisitos não-funcionais específicos do projeto, explicando como a arquitetura os atende.
```

## Prompt para Considerações de Implantação

```
Atue como um especialista em DevOps e arquitetura de implantação.

Para o sistema [nome do sistema] com a arquitetura [descreva brevemente], preciso definir considerações de implantação em alto nível. Ajude-me a elaborar a seção "Considerações de Implantação" do HLD, abordando:

1. Ambientes-alvo:
   - Recomendações para plataformas de implantação (cloud específica, on-premises, híbrido)
   - Justificativa para as escolhas com base nos requisitos

2. Estrutura de implantação:
   - Visão geral da topologia de implantação
   - Abordagem para segregação de ambientes (dev, staging, prod)
   - Considerações para multi-região ou multi-cloud, se aplicável

3. Requisitos de infraestrutura:
   - Recursos computacionais estimados
   - Necessidades de rede
   - Requisitos de armazenamento

4. Considerações de DevOps:
   - Abordagem para continuous integration/deployment
   - Estratégias para monitoramento e observabilidade
   - Gestão de configuração e secrets
   - Estratégias para deployment com zero-downtime

Mantenha o foco em decisões arquiteturais relevantes para implantação, sem entrar em detalhes específicos de ferramentas ou scripts.
```

## Prompt para Documento Completo de HLD

```
Atue como um arquiteto de software sênior especializado na criação de documentação de arquitetura.

Preciso criar um documento completo de High-Level Design (HLD) para o sistema [nome do sistema]. O sistema tem como objetivo [descreva objetivo principal] e deve atender aos seguintes requisitos não-funcionais prioritários: [liste os principais requisitos não-funcionais].

O documento deve seguir a estrutura padrão de um HLD:

1. Visão Geral da Arquitetura
   - Estilo arquitetural adotado e justificativa
   - Diagrama de arquitetura de alto nível (descreva textualmente)
   - Princípios arquiteturais seguidos
   - Considerações e restrições tecnológicas

2. Componentes Principais
   - Descrição dos subsistemas e componentes
   - Responsabilidades de cada componente
   - Agrupamento lógico de funcionalidades
   - Dependências entre componentes

3. Interfaces e Comunicação
   - APIs entre componentes
   - Protocolos de comunicação
   - Formatos de dados trocados
   - Padrões de integração

4. Dados e Persistência
   - Visão geral do modelo de dados
   - Estratégia de armazenamento
   - Abordagem de persistência
   - Fluxos de dados principais

5. Mapeamento de Requisitos Não-Funcionais
   - Como a arquitetura atende a requisitos de performance
   - Estratégias para escalabilidade
   - Abordagem para segurança
   - Mecanismos de disponibilidade e resiliência

6. Considerações de Implantação
   - Ambientes-alvo
   - Estrutura de implantação
   - Requisitos de infraestrutura
   - Considerações de DevOps

Para cada seção, forneça um nível adequado de detalhe para um documento de arquitetura de alto nível, evitando especificidades de implementação.
```
