# Prompts para Documentos Específicos de Arquitetura

Este documento contém prompts específicos para auxiliar na criação de documentos de arquitetura especializados para aspectos específicos do seu sistema.

## Prompt para Database Design Document

```
Atue como um arquiteto de banco de dados experiente.

Preciso criar um Database Design Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema e seu propósito] e seus dados precisam ser persistidos de forma eficiente e escalável.

Contexto do sistema:
- Volume de dados estimado: [quantidade e crescimento esperado]
- Padrões de acesso: [leitura-intensivo, escrita-intensivo, balanceado]
- Requisitos de disponibilidade: [ex: 24/7, tolerância a falhas]
- Requisitos de performance: [tempos de resposta, throughput]
- Requisitos de consistência: [forte, eventual, etc.]

Por favor, desenvolva um documento de design de banco de dados abrangente que inclua:

1. Estratégia de Persistência
   - Tipo(s) de banco de dados recomendado(s) (SQL, NoSQL, híbrido)
   - Justificativa para as escolhas tecnológicas
   - Considerações sobre cloud vs on-premises
   - Estratégia de alta disponibilidade e DR

2. Modelo de Dados
   - Modelo conceitual com principais entidades e relacionamentos
   - Modelo lógico detalhado
   - Normalização/desnormalização e justificativas
   - Diagrama ER ou equivalente (descreva textualmente)

3. Design Físico
   - Esquemas e tabelas/coleções com estrutura detalhada
   - Tipos de dados e constraints
   - Índices e justificativas
   - Particionamento/sharding (se aplicável)

4. Objetos de Banco de Dados
   - Views e sua finalidade
   - Stored procedures/functions
   - Triggers
   - Políticas de segurança em nível de banco

5. Estratégias de Otimização
   - Abordagem para consultas complexas
   - Estratégias de indexação
   - Técnicas de caching
   - Otimizações específicas para o tipo de banco escolhido

6. Gestão de Evolução
   - Estratégia de versionamento de esquema
   - Abordagem para migrações
   - Backward compatibility
   - Gestão de dados legados

7. Monitoramento e Manutenção
   - Métricas chave a monitorar
   - Estratégia de backup e restore
   - Procedimentos de manutenção rotineira
   - Alertas e health checks

O documento deve ser tecnicamente preciso, bem justificado e considerar tanto necessidades atuais quanto futuras do sistema.
```

## Prompt para Security Architecture Document

```
Atue como um arquiteto de segurança de sistemas especializado em aplicações de software.

Preciso criar um Security Architecture Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema, sua finalidade e criticidade] e precisa implementar controles de segurança robustos para proteger dados e funcionalidades.

Contexto do sistema:
- Tipos de dados processados: [dados pessoais, financeiros, proprietários, etc.]
- Regulamentações aplicáveis: [GDPR, HIPAA, PCI-DSS, etc.]
- Modelo de deployment: [cloud, on-premises, híbrido]
- Perfil de usuários: [internos, externos, parceiros]
- Pontos de acesso: [web, mobile, API, etc.]

Por favor, desenvolva um documento de arquitetura de segurança abrangente que inclua:

1. Modelo de Ameaças
   - Atores de ameaça relevantes
   - Cenários de ataque prováveis
   - Vetores de ataque potenciais
   - Classificação e priorização de riscos

2. Princípios e Estratégia de Segurança
   - Princípios fundamentais adotados
   - Abordagem geral (defense-in-depth, zero trust, etc.)
   - Políticas de segurança aplicáveis
   - Standards e frameworks seguidos (NIST, ISO, etc.)

3. Controles de Segurança por Camada
   - Segurança de aplicação
   - Segurança de dados
   - Segurança de infraestrutura
   - Segurança de rede
   - Segurança de endpoint
   - Segurança de API

4. Autenticação e Autorização
   - Mecanismos de autenticação
   - Gestão de identidade
   - Controle de acesso e privilégios
   - Federação e SSO (se aplicável)

5. Proteção de Dados
   - Classificação de dados
   - Criptografia (em trânsito e em repouso)
   - Tokenização ou anonimização
   - Ciclo de vida dos dados e retenção

6. Detecção e Resposta
   - Logging e monitoramento de segurança
   - Detecção de intrusão
   - Gestão de vulnerabilidades
   - Plano de resposta a incidentes

7. Compliance e Assurance
   - Mapeamento para requisitos regulatórios
   - Testes de segurança (SAST, DAST, pentests)
   - Auditoria e revisões
   - DevSecOps e segurança no ciclo de vida

8. Arquitetura de Segurança como Código
   - Automação de controles de segurança
   - Infraestrutura imutável e hardening
   - Configuração segura como código
   - Validação contínua

O documento deve ser detalhado, práticos e alinhado com práticas modernas de segurança, considerando tanto necessidades de proteção quanto usabilidade e viabilidade de implementação.
```

## Prompt para Network Architecture Document

```
Atue como um arquiteto de redes com experiência em arquitetura de sistemas distribuídos.

Preciso criar um Network Architecture Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema e seus requisitos de conectividade] e necessita de uma arquitetura de rede robusta, segura e de alta performance.

Contexto do sistema:
- Distribuição geográfica: [local, regional, global]
- Requisitos de disponibilidade: [SLAs, redundância necessária]
- Sensibilidade dos dados: [classificação de confidencialidade]
- Volume de tráfego: [estimativas de bandwidth, padrões de tráfego]
- Características especiais: [tempo real, streaming, transferências grandes, etc.]

Por favor, desenvolva um documento de arquitetura de rede abrangente que inclua:

1. Topologia de Rede
   - Diagrama de topologia de alto nível (descreva textualmente)
   - Zonas de rede e segmentação
   - Componentes principais (roteadores, switches, firewalls, etc.)
   - Conectividade entre sites/regiões (se aplicável)

2. Modelo de Segmentação e Acesso
   - Definição de zonas de segurança (DMZ, interna, etc.)
   - Política de firewalls e ACLs
   - Filtragem de tráfego e inspeção
   - Network Access Control

3. Conectividade Externa
   - Conexões com internet
   - VPNs e conexões site-to-site
   - Acesso remoto
   - Integração com parceiros/terceiros

4. Balanceamento de Carga e Alta Disponibilidade
   - Estratégia de balanceamento de carga
   - Redundância de componentes críticos
   - Failover e disaster recovery
   - Gestão de sessões e stickiness

5. Estratégia de Endereçamento e Naming
   - Esquema de endereçamento IP
   - VLANs e subnetting
   - DNS e resolução de nomes
   - DHCP e gestão de IPs

6. Gestão de Tráfego e QoS
   - Priorização de tráfego
   - Bandwidth management
   - Traffic shaping e policing
   - Mecanismos anti-DDoS

7. Monitoramento e Gestão
   - Ferramentas de monitoramento de rede
   - Logging e análise de tráfego
   - SNMP e alertas
   - Gestão de configuração de rede

8. Considerações de Cloud e Híbridas (se aplicável)
   - Integração com cloud providers
   - Software-defined networking
   - Modelos de conectividade híbrida
   - Gestão de identidade e acessos cross-environment

O documento deve fornecer uma visão clara da arquitetura de rede, com foco em segurança, performance, resiliência e escalabilidade, além de considerar os requisitos específicos do sistema e as melhores práticas atuais.
```

## Prompt para Integration Architecture Document

```
Atue como um arquiteto de integração especializado em conectar sistemas e serviços.

Preciso criar um Integration Architecture Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema] precisa se integrar com [mencione os principais sistemas externos] para [descreva o propósito das integrações].

Contexto das integrações:
- Sistemas a integrar: [liste os sistemas internos e externos]
- Volumes de dados: [frequência e tamanho das transações]
- Requisitos de latência: [tempo real, near real-time, batch]
- Criticidade: [impacto de falhas nas integrações]
- Restrições tecnológicas: [limitações dos sistemas envolvidos]

Por favor, desenvolva um documento de arquitetura de integração abrangente que inclua:

1. Estratégia de Integração
   - Abordagem arquitetural (SOA, EDA, API-first, etc.)
   - Padrões de integração predominantes
   - Princípios e guidelines
   - Governança de integração

2. Padrões de Comunicação
   - Sincrono vs. assíncrono
   - Push vs. pull
   - Request-reply, publish-subscribe, etc.
   - Batch vs. real-time

3. Arquitetura Técnica
   - Componentes centrais (ESB, API gateway, message broker, etc.)
   - Diagrama de arquitetura de integração (descreva textualmente)
   - Tecnologias e frameworks recomendados
   - Mediação e transformação de dados

4. APIs e Interfaces
   - Design de API (REST, GraphQL, gRPC, etc.)
   - Contratos e versionamento
   - Gestão de API
   - Documentação e discovery

5. Gestão de Dados
   - Mapeamentos entre sistemas
   - Transformações e enriquecimento
   - Validação e quality gates
   - Master data considerations

6. Segurança da Integração
   - Autenticação entre sistemas
   - Proteção de dados em trânsito
   - Autorização e controle de acesso
   - Auditoria e não-repúdio

7. Confiabilidade e Resiliência
   - Estratégia para falhas de comunicação
   - Tratamento de erros e retentativas
   - Circuit breakers e degradação graciosa
   - Monitoramento de health e SLAs

8. Integrações Específicas
   - Detalhamento das principais integrações
   - Fluxos de informação
   - Requisitos específicos
   - Considerações especiais

O documento deve ser prático, implementável e focado em criar integrações robustas e sustentáveis que permitam a comunicação eficaz entre sistemas, considerando tanto necessidades atuais quanto futuras extensões.
```

## Prompt para Infrastructure Architecture Document

```
Atue como um arquiteto de infraestrutura com experiência em ambientes modernos de TI.

Preciso criar um Infrastructure Architecture Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema e suas características] e requer uma infraestrutura robusta, escalável e gerenciável.

Contexto do sistema:
- Perfil de carga: [número de usuários, padrões de uso, sazonalidade]
- Requisitos de disponibilidade: [uptime esperado, criticidade]
- Restrições orçamentárias: [CAPEX vs OPEX, considerações de custo]
- Regulamentações relevantes: [requisitos de dados, localização, etc.]
- Considerações de crescimento: [planos de expansão, escalabilidade]

Por favor, desenvolva um documento de arquitetura de infraestrutura abrangente que inclua:

1. Estratégia e Visão Geral
   - Abordagem arquitetural (cloud-native, híbrida, on-prem)
   - Princípios de design de infraestrutura
   - Justificativa para escolhas estratégicas
   - Roadmap de longo prazo

2. Plataforma Computacional
   - Servidores/instâncias e dimensionamento
   - Virtualização/containerização
   - Orquestração e gerenciamento
   - Auto-scaling e elasticidade

3. Armazenamento e Dados
   - Estratégia de armazenamento (block, file, object)
   - Dimensionamento e provisão
   - Backup e retenção
   - Estratégias para dados de grande volume

4. Rede e Conectividade
   - Topologia de rede
   - Segurança de perímetro
   - Balanceamento de carga
   - Conectividade externa e interna

5. Ambientes Operacionais
   - Definição de ambientes (dev, test, staging, prod)
   - Isolamento e separação
   - Promoção entre ambientes
   - Paridade entre ambientes

6. Operações e Suporte
   - Monitoramento e observabilidade
   - Logging e análise
   - Backup e disaster recovery
   - Patching e manutenção

7. Segurança de Infraestrutura
   - Identity and access management
   - Hardening e baselines de segurança
   - Criptografia e gestão de chaves
   - Compliance e auditoria

8. DevOps e Automação
   - CI/CD e deployment
   - Infrastructure as Code
   - Gestão de configuração
   - Automação operacional

9. Cloud ou Específicos de Plataforma (se aplicável)
   - Serviços gerenciados vs. self-managed
   - Multi-cloud ou estratégia de vendor
   - Cloud cost optimization
   - Serviços PaaS vs. IaaS

O documento deve ser detalhado, mas prático, focando em criar uma infraestrutura que suporte os requisitos do sistema enquanto mantém flexibilidade para evolução futura, operabilidade e custo-benefício.
```

## Prompt para Microservices Architecture Document

```
Atue como um arquiteto de software especializado em arquiteturas de microserviços.

Preciso criar um Microservices Architecture Document para o sistema [nome do sistema]. Este sistema [descreva brevemente o sistema e por que uma arquitetura de microserviços foi escolhida] e precisa ser projetado seguindo as melhores práticas para arquiteturas distribuídas.

Contexto do sistema:
- Complexidade do domínio: [descreva a complexidade do domínio de negócio]
- Escala esperada: [volume de usuários, transações, dados]
- Equipes de desenvolvimento: [estrutura das equipes, tamanho, distribuição]
- Requisitos críticos: [performance, disponibilidade, etc. que influenciam o design]

Por favor, desenvolva um documento de arquitetura de microserviços abrangente que inclua:

1. Princípios e Objetivos
   - Princípios de design adotados
   - Benefícios esperados da abordagem de microserviços
   - Trade-offs aceitos
   - Visão de longo prazo

2. Decomposição de Serviços
   - Estratégia de decomposição (por domínio, subdomínio, capacidade)
   - Identificação de bounded contexts
   - Granularidade de serviços
   - Justificativa para os limites escolhidos

3. Comunicação entre Serviços
   - Padrões de comunicação (REST, gRPC, messaging, etc.)
   - Sincrono vs. assíncrono
   - Event-driven patterns
   - API design e contratos

4. Gestão de Dados
   - Estratégia de persistência (database-per-service, shared, etc.)
   - Consistência de dados distribuídos
   - Consultas entre serviços
   - CQRS e event sourcing (se aplicável)

5. Resiliência e Confiabilidade
   - Circuit breakers e bulkheads
   - Retry e timeout strategies
   - Graceful degradation
   - Monitoring e health checks

6. Autenticação e Autorização
   - Identity management distribuído
   - Service-to-service authentication
   - Centralized vs. decentralized auth
   - Token propagation e security context

7. DevOps e Operações
   - CI/CD para microserviços
   - Containerização e orquestração
   - Deployment strategies (blue/green, canary)
   - Logging e tracing distribuído

8. API Gateway e Frontend
   - Estratégia de API gateway
   - Backend for frontend (BFF) patterns
   - Composição de UI
   - Mobile/web considerations

9. Mapa de Serviços
   - Descrição dos principais microserviços
   - Responsabilidades e fronteiras
   - Diagramas de relacionamento (descreva textualmente)
   - Endpoints e comunicações principais

O documento deve ser prático, aplicável e considerar tanto os aspectos técnicos quanto organizacionais de uma arquitetura de microserviços bem-sucedida.
```

## Prompt para Mobile Architecture Document

```
Atue como um arquiteto de software especializado em aplicações móveis.

Preciso criar um Mobile Architecture Document para o aplicativo móvel [nome do app] que faz parte do sistema [nome do sistema]. Este aplicativo [descreva brevemente o propósito e funcionalidades principais do app] e será utilizado por [descreva o público-alvo].

Contexto do aplicativo:
- Plataformas-alvo: [iOS, Android, ou ambos]
- Perfil de uso: [online, offline, híbrido]
- Complexidade da UI: [simples a complexa, animações, visualizações]
- Integração com hardware: [sensores, câmera, etc. necessários]
- Requisitos críticos: [performance, offline, segurança, etc.]

Por favor, desenvolva um documento de arquitetura móvel abrangente que inclua:

1. Visão Geral da Arquitetura
   - Abordagem de desenvolvimento (nativo, híbrido, cross-platform)
   - Justificativa para a escolha tecnológica
   - Princípios arquiteturais
   - Stack tecnológico recomendado

2. Arquitetura da Aplicação
   - Padrão arquitetural (MVC, MVVM, Clean, etc.)
   - Camadas e componentes principais
   - Gerenciamento de estado
   - Responsabilidades e separação de concerns

3. Interface com o Usuário
   - Arquitetura da UI
   - Navegação e fluxo de telas
   - Reutilização de componentes
   - Responsividade e adaptação de layout

4. Comunicação com Back-end
   - Estratégia de API
   - Autenticação e autorização
   - Caching e throttling
   - Tratamento de erros e reconectividade

5. Persistência de Dados
   - Estratégia de armazenamento local
   - Sincronização offline-online
   - Gestão de conflitos
   - Criptografia de dados locais

6. Performance e Otimização
   - Estratégias para carregamento rápido
   - Otimização de memória e bateria
   - Lazy loading e virtualização
   - Background processing

7. Segurança
   - Proteção de dados sensíveis
   - Comunicação segura
   - Prevenção contra ataques comuns
   - Validação e sanitização de entrada

8. Testabilidade e Qualidade
   - Estratégia de testes (unit, UI, integration)
   - Automação de testes
   - Monitoramento e analytics
   - Crash reporting

9. Considerações Específicas de Plataforma
   - Diferenças entre iOS e Android (se aplicável)
   - Adaptações necessárias
   - Features específicas de plataforma
   - Estratégia para manter paridade

O documento deve ser detalhado, implementável e considerar todas as nuances do desenvolvimento móvel moderno, garantindo uma experiência de usuário de alta qualidade enquanto mantém o código sustentável e de fácil manutenção.
```

## Prompt para Data Warehouse/BI Architecture Document

```
Atue como um arquiteto de dados especializado em soluções analíticas e business intelligence.

Preciso criar um Data Warehouse/BI Architecture Document para o sistema [nome do sistema]. Esta solução analítica tem como objetivo [descreva o propósito: suporte à decisão, reports operacionais, análises preditivas, etc.] e precisa processar dados de [fontes de dados principais] para atender [principais stakeholders e suas necessidades].

Contexto da solução:
- Volume de dados: [tamanho atual e crescimento esperado]
- Variedade de dados: [estruturados, semi-estruturados, não estruturados]
- Velocidade dos dados: [batch, near real-time, streaming]
- Requisitos analíticos: [tipos de análises, complexidade, granularidade]
- Perfil de usuários: [técnicos vs. não-técnicos, número, distribuição]

Por favor, desenvolva um documento de arquitetura de data warehouse/BI abrangente que inclua:

1. Visão Geral da Arquitetura
   - Abordagem arquitetural (Kimball, Inmon, Data Vault, Lakehouse, etc.)
   - Camadas principais da arquitetura
   - Justificativa para as escolhas estratégicas
   - Diagrama conceitual da arquitetura (descreva textualmente)

2. Fontes de Dados e Integração
   - Inventário de fontes de dados
   - Estratégia de extração e captura de dados
   - Frequência de atualização
   - Gestão de metadados e linhagem

3. Camada de Data Storage
   - Estruturas de armazenamento (warehouse, lake, mart)
   - Tecnologias recomendadas
   - Estratégia de particionamento
   - Políticas de retenção e arquivamento

4. Processamento e Transformação
   - Framework ETL/ELT
   - Pipelines de dados principais
   - Processamento batch vs. streaming
   - Gestão de qualidade de dados

5. Modelagem de Dados
   - Abordagem de modelagem (dimensional, relacional, etc.)
   - Estrutura de modelos (fatos, dimensões, hierarquias)
   - Gestão de slowly changing dimensions
   - Agregações e materialização de views

6. Camada de Apresentação e Consumo
   - Ferramentas de visualização e BI
   - Self-service vs. relatórios predefinidos
   - Dashboards e KPIs principais
   - Mobile/web delivery

7. Governança e Operações
   - Gestão de acesso e segurança
   - Monitoramento de performance
   - Disaster recovery
   - Processos operacionais

8. Advanced Analytics (se aplicável)
   - Suporte para ciência de dados
   - Integração com ML/AI
   - Feature stores
   - Modelagem preditiva e prescritiva

9. Implementação e Evolução
   - Abordagem de implementação (iterativa, modular)
   - Priorização de áreas de negócio
   - Roadmap de implementação
   - Estratégia de evolução contínua

O documento deve ser prático, orientado a resultados de negócio, tecnicamente sólido e escalável para acomodar necessidades analíticas crescentes e em evolução.
```
