# Prompts para Software Architecture Document (SAD)

Este documento contém prompts específicos para auxiliar na criação do Software Architecture Document (SAD) do seu sistema.

## Prompt para Introdução e Visão Geral

```
Atue como um arquiteto de software sênior especializado em documentação de arquitetura.

Estou criando um Software Architecture Document (SAD) para o sistema [nome do sistema] e preciso de ajuda para elaborar a seção de introdução e visão geral. O sistema tem como objetivo [descreva o objetivo principal] e é destinado a [descreva o público-alvo/usuários].

Por favor, elabore uma introdução abrangente que inclua:

1. Propósito do documento SAD e audiência-alvo
2. Escopo do sistema e contexto de negócio
3. Definições, siglas e abreviações relevantes
4. Referências a outros documentos importantes (como SRS, HLD, etc.)
5. Visão geral da arquitetura proposta em alto nível
6. Pressupostos e dependências arquiteturais

A introdução deve ser concisa, mas fornecer o contexto necessário para que qualquer pessoa técnica possa entender o propósito e a direção arquitetural do sistema.
```

## Prompt para Metas e Restrições Arquiteturais

```
Atue como um arquiteto de software especializado em requisitos não-funcionais.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Metas e Restrições Arquiteturais". Esta seção deve capturar os requisitos não-funcionais, requisitos de qualidade e as restrições que influenciam as decisões arquiteturais.

Contexto do sistema:
- Descrição: [breve descrição]
- Principais stakeholders: [lista de stakeholders-chave]
- Criticidade do sistema: [nível de criticidade para o negócio]

Por favor, ajude-me a elaborar esta seção abordando:

1. Requisitos de Qualidade:
   - Desempenho (tempos de resposta, throughput, etc.)
   - Escalabilidade (vertical, horizontal, projeções de crescimento)
   - Disponibilidade (uptime esperado, redundância, etc.)
   - Segurança (autenticação, autorização, confidencialidade, etc.)
   - Usabilidade (expectativas de experiência do usuário)
   - Manutenibilidade (facilidade de modificação, testabilidade)
   - Extensibilidade (capacidade de adicionar novos recursos)

2. Restrições Técnicas:
   - Limitações de plataforma ou linguagem
   - Compatibilidade com sistemas existentes
   - Limitações de infraestrutura
   - Conformidade com padrões técnicos da organização

3. Restrições de Negócio:
   - Orçamento e considerações de custo
   - Prazos e cronograma
   - Recursos de desenvolvimento disponíveis
   - Considerações regulatórias ou legais

4. Princípios Arquiteturais:
   - Princípios-chave que guiarão as decisões arquiteturais

Cada meta e restrição deve ser claramente definida, mensurável quando possível, e relacionada a como influenciará a arquitetura.
```

## Prompt para Visão de Caso de Uso

```
Atue como um arquiteto de software especializado em engenharia de requisitos.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Caso de Uso" que apresentará como a arquitetura suporta os principais casos de uso e cenários do sistema.

Contexto do sistema:
- Principais funcionalidades: [liste as principais funcionalidades]
- Casos de uso críticos: [liste casos de uso prioritários]
- Atores/usuários principais: [descreva brevemente os tipos de usuários]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Diagrama de contexto de sistema (descreva textualmente os elementos e suas relações)
2. Descrição dos casos de uso arquiteturalmente significativos, incluindo:
   - Nome e breve descrição do caso de uso
   - Requisitos não-funcionais específicos para este caso de uso
   - Fluxo básico e caminhos alternativos relevantes
   - Componentes arquiteturais envolvidos na realização do caso de uso
   - Considerações arquiteturais específicas (throughput, concorrência, etc.)

3. Mapeamento entre casos de uso e componentes arquiteturais, mostrando:
   - Quais componentes participam de cada caso de uso
   - Como os componentes colaboram para realizar o caso de uso
   - Fluxos de dados e controle relevantes

4. Priorização dos casos de uso do ponto de vista arquitetural:
   - Quais casos de uso exercitam aspectos críticos da arquitetura
   - Quais casos de uso apresentam maiores desafios técnicos

A seção deve demonstrar como a arquitetura proposta satisfaz as necessidades funcionais e não-funcionais dos casos de uso mais importantes.
```

## Prompt para Visão Lógica

```
Atue como um arquiteto de software especializado em design de sistemas.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão Lógica" que descreverá a organização do código em pacotes, componentes, camadas e classes importantes.

Contexto do sistema:
- Estilo arquitetural: [descreva o estilo arquitetural principal, ex: microsserviços, monolítico em camadas, etc.]
- Linguagens/plataformas: [liste as principais tecnologias de implementação]
- Complexidade do domínio: [descreva brevemente a complexidade do domínio de negócio]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Decomposição de Subsistemas:
   - Principais subsistemas e suas responsabilidades
   - Relacionamentos e dependências entre subsistemas
   - Justificativa para a decomposição escolhida

2. Pacotes Significativos:
   - Organização em pacotes/namespaces principais
   - Princípios para agrupamento de classes em pacotes
   - Dependências entre pacotes (descreva textualmente)

3. Abstrações-Chave:
   - Classes/interfaces fundamentais e suas responsabilidades
   - Padrões de design utilizados e sua aplicação
   - Mecanismos de extensibilidade incorporados

4. Organização em Camadas:
   - Descrição das camadas arquiteturais
   - Regras de dependência entre camadas
   - Mecanismos de comunicação entre camadas

5. Diagramas (descreva textualmente os elementos e suas relações):
   - Diagrama de pacotes para mostrar a organização de alto nível
   - Diagramas de classe para abstrações críticas
   - Diagramas de sequência para interações complexas

A visão lógica deve refletir claramente o estilo arquitetural escolhido e demonstrar como os princípios de design orientado a objetos (ou outro paradigma relevante) são aplicados no sistema.
```

## Prompt para Visão de Processo

```
Atue como um arquiteto de software especializado em sistemas concorrentes e distribuídos.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Processo" que descreverá os aspectos dinâmicos do sistema, incluindo processos, threads, concorrência e sincronização.

Contexto do sistema:
- Requisitos de concorrência: [descreva necessidades de processamento paralelo, throughput, etc.]
- Características de carga: [padrões de uso, picos de tráfego, etc.]
- Restrições de tempo/resposta: [SLAs, tempos máximos de resposta, etc.]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Decomposição de Processos:
   - Principais processos/serviços e suas responsabilidades
   - Como os processos se relacionam com a arquitetura lógica
   - Comunicação entre processos (IPC, mensageria, etc.)

2. Threads e Concorrência:
   - Estratégia de threading (thread pools, workers, etc.)
   - Mecanismos de sincronização e controle de concorrência
   - Tratamento de condições de corrida e deadlocks

3. Fluxos de Execução:
   - Descrição dos principais fluxos de execução
   - Processamento assíncrono vs. síncrono
   - Tratamento de operações de longa duração

4. Estratégias para Casos Especiais:
   - Tratamento de picos de carga
   - Throttling e backpressure
   - Graceful degradation

5. Diagramas de Atividade ou Sequência (descreva textualmente):
   - Para fluxos de processamento críticos
   - Para cenários de alta concorrência
   - Para mecanismos de recuperação de falhas

A visão de processo deve demonstrar como a arquitetura atende aos requisitos de performance, escalabilidade e disponibilidade através de decisões sobre concorrência e paralelismo.
```

## Prompt para Visão de Implantação

```
Atue como um arquiteto de software especializado em implantação e infraestrutura.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Implantação" que descreverá a topologia física em que o sistema será implantado, incluindo ambientes, servidores, e configuração de hardware.

Contexto do sistema:
- Ambiente-alvo: [cloud, on-premises, híbrido]
- Restrições de infraestrutura: [limitações de hardware, rede, etc.]
- Requisitos de disponibilidade/desempenho: [SLAs, redundância necessária, etc.]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Topologia Física:
   - Principais nós de computação (servidores, contêineres, VMs)
   - Balanceadores de carga e proxies
   - Componentes de rede (firewalls, VLANs, etc.)
   - Descrição textual do diagrama de implantação

2. Mapeamento Software-Hardware:
   - Como componentes lógicos são mapeados para nós físicos
   - Estratégias de distribuição e colocação de componentes
   - Justificativa para as decisões de alocação

3. Requisitos de Hardware/Software:
   - Especificações mínimas de hardware para cada nó
   - Software de terceiros e middleware necessários
   - Sistemas operacionais e dependências

4. Considerações por Ambiente:
   - Diferenças entre ambientes (dev, test, staging, prod)
   - Estratégia de propagação entre ambientes
   - Separação de recursos entre ambientes

5. Estratégias Específicas:
   - Alta disponibilidade e redundância
   - Disaster recovery
   - Escalabilidade (auto-scaling, redundância)
   - Backup e restore

6. Considerações sobre Cloud (se aplicável):
   - Serviços cloud utilizados
   - Estratégia multi-região ou multi-cloud
   - Segurança na cloud e compliance

A visão de implantação deve demonstrar como a infraestrutura física suportará os requisitos do sistema e garantirá níveis adequados de disponibilidade, desempenho e segurança.
```

## Prompt para Visão de Implementação

```
Atue como um arquiteto de software especializado em organização de código e processos de build.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Implementação" que descreverá como o código-fonte está organizado, como é compilado, e como os artefatos de implementação são criados e gerenciados.

Contexto do sistema:
- Linguagens e frameworks: [lista de tecnologias principais]
- Complexidade do código: [tamanho estimado, número de módulos, etc.]
- Processo de desenvolvimento: [metodologia, tamanho da equipe, etc.]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Organização do Código-fonte:
   - Estrutura de diretórios principal
   - Convenções de nomeação e organização
   - Gestão de dependências e bibliotecas

2. Processo de Build:
   - Ferramentas de build utilizadas
   - Passos no processo de build
   - Gestão de versões e artefatos
   - Automação de build (CI/CD)

3. Artefatos de Implementação:
   - Tipos de artefatos gerados (executáveis, bibliotecas, contêineres)
   - Estrutura interna dos artefatos
   - Versionamento e nomeação dos artefatos

4. Considerações Especiais:
   - Gestão de código legado (se aplicável)
   - Interoperabilidade entre linguagens (se múltiplas)
   - Estratégias para testes automatizados
   - Análise estática de código e qualidade

5. Estratégias para Casos Específicos:
   - Gestão de ativos estáticos (imagens, CSS, etc.)
   - Internacionalização e localização
   - Configuração específica por ambiente
   - Feature toggles ou configuração dinâmica

A visão de implementação deve fornecer orientação clara para os desenvolvedores sobre como o código deve ser organizado, compilado e implantado de acordo com a arquitetura estabelecida.
```

## Prompt para Visão de Dados

```
Atue como um arquiteto de dados especializado em persistência e modelos de dados.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Dados" que descreverá como os dados são armazenados, acessados e gerenciados pelo sistema.

Contexto do sistema:
- Tipos de dados: [transacionais, analíticos, conteúdo, etc.]
- Volume de dados: [estimativa de tamanho, taxa de crescimento]
- Requisitos de persistência: [consistência, disponibilidade, durabilidade]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Modelo de Dados Conceitual:
   - Principais entidades e seus relacionamentos
   - Descrição textual do modelo de domínio
   - Regras de negócio relevantes para o modelo de dados

2. Estratégia de Persistência:
   - Tipos de armazenamento utilizados (SQL, NoSQL, cache, etc.)
   - Justificativa para as escolhas de armazenamento
   - Mapeamento entre o modelo conceitual e o físico

3. Modelos Físicos de Dados:
   - Descrição das principais estruturas de dados (tabelas, coleções, etc.)
   - Estratégias de indexação e otimização
   - Considerações sobre particionamento e sharding

4. Acesso e Manipulação de Dados:
   - Padrões de acesso a dados (repositórios, DAOs, etc.)
   - Estratégias de transação e concorrência
   - Cache e otimização de acesso

5. Integração e Migração:
   - Estratégias para integração com fontes externas de dados
   - Abordagem para migração de dados
   - ETL ou processos de transformação

6. Considerações Específicas:
   - Backup e recuperação
   - Arquivamento e retenção de dados
   - Estratégias para GDPR ou outras regulamentações de dados
   - Anonimização e privacidade

A visão de dados deve demonstrar como a arquitetura de dados suporta os requisitos funcionais e não-funcionais do sistema, com atenção especial à escalabilidade, desempenho e integridade dos dados.
```

## Prompt para Visão de Segurança

```
Atue como um arquiteto de segurança especializado em sistemas de software.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Visão de Segurança" que descreverá como a arquitetura aborda os requisitos de segurança, proteção de dados e mitigação de riscos.

Contexto do sistema:
- Sensibilidade dos dados: [classificação dos dados processados]
- Requisitos regulatórios: [GDPR, HIPAA, PCI-DSS, etc. se aplicáveis]
- Ameaças principais: [tipos de ameaças mais relevantes para este sistema]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Modelo de Segurança:
   - Princípios de segurança adotados
   - Fronteiras de confiança e zonas de segurança
   - Modelo de ameaças simplificado

2. Autenticação e Autorização:
   - Mecanismos de autenticação
   - Estratégia de autorização (RBAC, ABAC, etc.)
   - Gestão de identidades e federação
   - Single Sign-On e integração com sistemas de identidade

3. Proteção de Dados:
   - Criptografia de dados em trânsito
   - Criptografia de dados em repouso
   - Tokenização ou anonimização
   - Gestão de chaves e segredos

4. Segurança em Camadas:
   - Segurança de rede (firewalls, WAF, etc.)
   - Segurança de aplicação (proteção contra OWASP Top 10)
   - Segurança de infraestrutura (hardening, configuração segura)
   - Segurança de API

5. Auditoria e Detecção:
   - Logging de eventos de segurança
   - Monitoramento e detecção de intrusão
   - Resposta a incidentes
   - Análise forense

6. Conformidade e Governança:
   - Controles para atender requisitos regulatórios
   - Processos de verificação de segurança
   - DevSecOps e segurança no ciclo de vida

A visão de segurança deve mostrar como a arquitetura implementa o princípio de "security by design" e como os controles de segurança estão integrados em todos os aspectos do sistema.
```

## Prompt para Qualidade e Crosscutting Concerns

```
Atue como um arquiteto de software especializado em qualidade e atributos transversais.

Para o Software Architecture Document (SAD) do sistema [nome do sistema], preciso elaborar a seção de "Qualidade e Crosscutting Concerns" que descreverá como a arquitetura aborda preocupações que afetam múltiplos componentes e camadas.

Contexto do sistema:
- Requisitos de qualidade prioritários: [performance, disponibilidade, manutenibilidade, etc.]
- Características especiais: [internacionalização, acessibilidade, etc. se aplicáveis]

Por favor, ajude-me a elaborar esta seção incluindo:

1. Estratégia para Qualidade:
   - Métricas e KPIs para atributos de qualidade
   - Abordagem para trade-offs entre atributos conflitantes
   - Mecanismos de monitoramento e avaliação

2. Logging e Monitoramento:
   - Estratégia de logging (níveis, formatos, destinos)
   - Monitoramento de desempenho e saúde
   - Rastreamento distribuído (se aplicável)
   - Alertas e notificações

3. Tratamento de Erros e Resiliência:
   - Estratégia para detecção e recuperação de falhas
   - Circuit breakers e bulkheads
   - Retry, timeout e fallback patterns
   - Tratamento de erros consistente

4. Configuração e Externalização:
   - Gestão de configuração em diferentes ambientes
   - Estratégia para configuração dinâmica
   - Padrões para externalização de valores

5. Internacionalização e Localização (se aplicável):
   - Estratégia para suporte a múltiplos idiomas
   - Tratamento de formatos regionais (datas, números, moedas)
   - Considerações culturais e de UX

6. Acessibilidade (se aplicável):
   - Conformidade com padrões (WCAG, Section 508)
   - Teste e validação de acessibilidade
   - Integração com tecnologias assistivas

7. Instrumentação e Analytics:
   - Métricas de negócio e técnicas coletadas
   - Estratégia para análise de dados operacionais
   - Feedback loops para melhoria contínua

A seção deve demonstrar como estas preocupações transversais são tratadas de maneira consistente em toda a arquitetura, sem duplicação e com garantia de qualidade.
```

## Prompt para Documento Completo de SAD

```
Atue como um arquiteto de software sênior especializado em documentação de arquitetura.

Preciso criar um Software Architecture Document (SAD) completo para o sistema [nome do sistema]. O sistema tem como objetivo [descreva objetivo principal] e deve atender aos seguintes requisitos não-funcionais prioritários: [liste os principais requisitos não-funcionais].

Por favor, desenvolva um SAD completo seguindo esta estrutura:

1. Introdução
   - Propósito do documento
   - Escopo do sistema
   - Definições e acrônimos
   - Referências
   - Visão geral do documento

2. Metas e Restrições Arquiteturais
   - Requisitos de qualidade (desempenho, segurança, disponibilidade, etc.)
   - Restrições técnicas e de negócio
   - Princípios arquiteturais

3. Visão de Caso de Uso
   - Casos de uso arquiteturalmente significativos
   - Mapeamento entre casos de uso e componentes

4. Visão Lógica
   - Decomposição em subsistemas e pacotes
   - Organização em camadas
   - Classes e interfaces importantes
   - Diagramas relevantes (descritos textualmente)

5. Visão de Processo
   - Processos e threads
   - Comunicação entre processos
   - Estratégias de concorrência

6. Visão de Implantação
   - Topologia física
   - Mapeamento entre software e hardware
   - Requisitos de infraestrutura

7. Visão de Implementação
   - Organização do código
   - Dependências externas
   - Processo de build e deploy

8. Visão de Dados
   - Modelo de dados conceitual
   - Estratégia de persistência
   - Considerações específicas de dados

9. Visão de Segurança
   - Modelo de segurança
   - Estratégias de autenticação e autorização
   - Proteção de dados

10. Qualidade e Crosscutting Concerns
    - Logging e monitoramento
    - Tratamento de erros
    - Outras preocupações transversais

11. Tamanho e Performance
    - Estimativas de capacidade
    - Considerações de escalabilidade
    - Otimizações planejadas

12. Apêndices
    - Glossário
    - Listas de referências
    - Material complementar

O documento deve fornecer uma visão abrangente e coerente da arquitetura, com nível adequado de detalhe para orientar a implementação e ser compreensível para toda a equipe técnica.
```
