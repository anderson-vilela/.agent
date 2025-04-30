# Prompts para Low-Level Design (LLD)

Este documento contém prompts específicos para auxiliar na criação do Low-Level Design (LLD) do seu sistema, detalhando componentes, módulos, interfaces e algoritmos.

## Prompt para Especificação de Componente

```
Atue como um arquiteto de software especializado em design detalhado de componentes.

Preciso criar uma especificação detalhada para o componente [nome do componente] do sistema [nome do sistema]. Este componente é responsável por [descreva brevemente a responsabilidade do componente].

Contexto:
- Relacionamento com a arquitetura geral: [como este componente se encaixa na arquitetura de alto nível]
- Interações principais: [componentes/sistemas com os quais este componente interage]
- Requisitos não-funcionais específicos: [requisitos que afetam especialmente este componente]

Por favor, elabore uma especificação de design detalhada que inclua:

1. Visão Geral do Componente:
   - Propósito e responsabilidades
   - Escopo e limites
   - Comportamento esperado

2. Estrutura Interna:
   - Decomposição em classes/módulos/subcomponentes
   - Relações e dependências entre elementos internos
   - Diagrama de classes/módulos (descreva textualmente)

3. Interfaces:
   - Interfaces públicas expostas (APIs, eventos)
   - Contratos de interface detalhados (parâmetros, tipos, retornos)
   - Pré-condições e pós-condições
   - Tratamento de erros e exceções

4. Fluxos de Dados e Controle:
   - Principais fluxos de processamento
   - Estados e transições (se aplicável)
   - Algoritmos importantes em pseudocódigo

5. Persistência (se aplicável):
   - Dados armazenados por este componente
   - Estratégia de acesso a dados
   - Detalhes de mapeamento objeto-relacional

6. Considerações de Concorrência:
   - Acessos concorrentes
   - Sincronização e locks
   - Potenciais gargalos

7. Configuração:
   - Parâmetros configuráveis
   - Valores padrão
   - Impacto das configurações

8. Testabilidade:
   - Abordagem para testes unitários
   - Pontos de teste e verificação
   - Mocking de dependências

A especificação deve ser detalhada o suficiente para orientar a implementação direta, mas flexível o bastante para permitir decisões de design de menor escala durante o desenvolvimento.
```

## Prompt para Design de Interface (API)

```
Atue como um arquiteto de software especializado em design de APIs.

Preciso criar uma especificação detalhada para a interface/API [nome da interface] do sistema [nome do sistema]. Esta interface será usada por [descreva os consumidores/clientes da API] para [finalidade principal da API].

Contexto:
- Tipo de API: [REST, GraphQL, RPC, biblioteca, etc.]
- Restrições tecnológicas: [qualquer limitação ou requisito tecnológico]
- Considerações de performance: [latência esperada, throughput, etc.]

Por favor, elabore uma especificação de API detalhada que inclua:

1. Visão Geral da Interface:
   - Propósito e escopo
   - Princípios de design seguidos
   - Casos de uso principais

2. Detalhamento da API:
   - Endpoints/métodos/funções
   - Parâmetros para cada operação (incluindo tipos, formato, obrigatoriedade)
   - Formatos de resposta (estrutura, códigos, tipos)
   - Códigos de erro e mensagens

3. Comportamento:
   - Semântica detalhada de cada operação
   - Garantias e invariantes
   - Idempotência e segurança das operações
   - Ordenação e paginação (se aplicável)

4. Autenticação e Autorização:
   - Mecanismos de autenticação
   - Níveis de permissão e controle de acesso
   - Tokens e lifetime

5. Versionamento:
   - Estratégia de versionamento
   - Compatibilidade retroativa
   - Plano de descontinuação

6. Limitações e Throttling:
   - Rate limits
   - Quotas
   - Backoff strategy

7. Considerações de Implantação:
   - Ambientes (staging, prod)
   - Estratégia de rollout
   - Monitoramento específico

8. Exemplos Completos:
   - Exemplos de requisições e respostas para cenários comuns
   - Exemplos de tratamento de erros
   - Fluxos de interação completos

A especificação deve ser detalhada, consistente e adequada para servir como um contrato entre provedores e consumidores da API.
```

## Prompt para Design de Banco de Dados

```
Atue como um arquiteto de dados especializado em design de bancos de dados.

Preciso criar um design detalhado para o banco de dados que suportará o módulo/subsistema [nome do módulo] do sistema [nome do sistema]. Este banco de dados precisa armazenar [descreva brevemente os dados principais].

Contexto:
- Tipo de banco de dados: [relacional, NoSQL, híbrido]
- Volume de dados estimado: [tamanho e taxa de crescimento]
- Padrões de acesso: [leitura-intensiva, escrita-intensiva, balanceado]
- Requisitos específicos: [performance, disponibilidade, conformidade, etc.]

Por favor, elabore um design detalhado de banco de dados que inclua:

1. Modelo de Dados:
   - Entidades/tabelas/coleções principais
   - Atributos/campos detalhados com tipos de dados
   - Relacionamentos e cardinalidade
   - Chaves primárias e estrangeiras
   - Índices e justificativas

2. Normalização/Desnormalização:
   - Nível de normalização escolhido
   - Áreas específicas de desnormalização
   - Trade-offs e justificativas

3. Integridade de Dados:
   - Constraints (unique, check, etc.)
   - Regras de validação
   - Triggers (se aplicáveis)
   - Integridade referencial

4. Otimização de Performance:
   - Estratégia de indexação detalhada
   - Particionamento/sharding (se aplicável)
   - Views e procedimentos armazenados
   - Estratégias de cache

5. Escalabilidade:
   - Abordagem para crescimento horizontal
   - Estratégias para lidar com picos de carga
   - Considerações sobre eventual consistency (se NoSQL)

6. Segurança:
   - Controle de acesso granular
   - Mascaramento/criptografia de dados sensíveis
   - Auditoria e logging

7. Migração e Evolução:
   - Estratégia para mudanças de esquema
   - Backward compatibility
   - Migrações e rollbacks

8. Considerações de Operação:
   - Backup e recuperação
   - Monitoramento específico
   - Manutenção rotineira

O design deve ser implementável diretamente e deve considerar tanto as necessidades atuais quanto o crescimento futuro do sistema.
```

## Prompt para Design de Algoritmo

```
Atue como um engenheiro de software especializado em algoritmos e estruturas de dados.

Preciso desenvolver um algoritmo detalhado para a funcionalidade [nome da funcionalidade] do sistema [nome do sistema]. Esta funcionalidade deve [descreva o que a funcionalidade precisa fazer].

Contexto:
- Complexidade esperada: [requisitos de performance, ex: O(n), tempo real, etc.]
- Restrições: [limitações de memória, processamento, etc.]
- Volume de dados: [quantidade de dados que o algoritmo processará]
- Criticidade: [impacto de falhas ou degradação de performance]

Por favor, elabore um design detalhado de algoritmo que inclua:

1. Descrição de Alto Nível:
   - Abordagem geral do algoritmo
   - Técnicas ou paradigmas utilizados (dividir e conquistar, programação dinâmica, etc.)
   - Justificativa para a abordagem escolhida

2. Estruturas de Dados:
   - Estruturas de dados principais utilizadas
   - Justificativa para cada escolha
   - Representação e organização dos dados

3. Algoritmo Detalhado:
   - Pseudocódigo detalhado ou descrição algorítmica passo a passo
   - Condições de entrada e saída
   - Casos de borda e tratamento
   - Tratamento de erros

4. Análise de Complexidade:
   - Análise de tempo (melhor caso, caso médio, pior caso)
   - Análise de espaço
   - Gargalos potenciais
   - Otimizações possíveis

5. Trade-offs e Alternativas:
   - Abordagens alternativas consideradas
   - Trade-offs da solução escolhida
   - Situações onde abordagens alternativas seriam preferíveis

6. Paralelização (se aplicável):
   - Oportunidades para processamento paralelo
   - Estratégia de divisão de trabalho
   - Considerações sobre sincronização

7. Validação e Testes:
   - Estratégia para verificar a corretude
   - Casos de teste críticos
   - Benchmarking e profiling

8. Evolução Futura:
   - Como o algoritmo pode ser estendido
   - Limitações da abordagem atual
   - Direções para melhorias futuras

O design deve ser rigoroso tecnicamente, implementável diretamente, e deve equilibrar eficiência com legibilidade e manutenibilidade.
```

## Prompt para Design de Estrutura de Dados

```
Atue como um engenheiro de software especializado em estruturas de dados.

Preciso projetar uma estrutura de dados personalizada para o subsistema [nome do subsistema] do sistema [nome do sistema]. Esta estrutura precisa suportar eficientemente as seguintes operações: [liste as operações principais, ex: busca rápida por X, inserção ordenada, etc.].

Contexto:
- Características dos dados: [volume, distribuição, volatilidade]
- Operações frequentes: [quais operações são mais comuns]
- Restrições de memória/armazenamento: [limitações existentes]
- Requisitos de concorrência: [acesso simultâneo necessário]

Por favor, elabore um design detalhado para a estrutura de dados que inclua:

1. Descrição Conceitual:
   - Visão geral da estrutura proposta
   - Princípios e inspirações (estruturas conhecidas adaptadas)
   - Justificativa para a abordagem

2. Especificação Detalhada:
   - Representação interna e organização
   - Campos/atributos com tipos e propósitos
   - Relações internas entre elementos
   - Invariantes e restrições

3. Operações Suportadas:
   - API completa (métodos, parâmetros, retornos)
   - Algoritmos detalhados para cada operação
   - Complexidade de tempo e espaço para cada operação
   - Garantias e limitações

4. Otimizações:
   - Técnicas específicas de otimização
   - Cache-friendliness
   - Aproveitamento de memória
   - Lazy evaluation ou computação proativa

5. Concorrência (se aplicável):
   - Estratégia para acesso concorrente
   - Locks, atomic operations ou design lock-free
   - Consistência e isolamento

6. Persistência (se aplicável):
   - Como a estrutura é serializada/desserializada
   - Estratégia de checkpoint ou journaling
   - Recuperação após falhas

7. Considerações de Implementação:
   - Detalhes específicos da linguagem alvo
   - Bibliotecas ou frameworks auxiliares
   - Padrões de implementação recomendados

8. Testes e Validação:
   - Casos de teste críticos
   - Fuzzing e testes de stress
   - Benchmarking

O design deve ser específico o suficiente para implementação direta, com atenção especial aos trade-offs entre as diferentes operações suportadas.
```

## Prompt para Design de Interface de Usuário

```
Atue como um arquiteto de UX/UI especializado em design de interfaces.

Preciso criar um design detalhado para a interface de usuário do módulo [nome do módulo] do sistema [nome do sistema]. Esta interface será usada por [descreva os usuários] para [finalidade principal].

Contexto:
- Perfil dos usuários: [nível técnico, frequência de uso, preferências]
- Dispositivos alvo: [desktop, mobile, responsivo, etc.]
- Requisitos de usabilidade: [acessibilidade, eficiência, learnability]
- Restrições técnicas: [frameworks UI obrigatórios, limitações do browser, etc.]

Por favor, elabore um design detalhado de interface que inclua:

1. Arquitetura de Informação:
   - Hierarquia de telas/páginas
   - Navegação e fluxos de usuário
   - Organização de conteúdo e taxonomia

2. Layout e Wireframes:
   - Descrição detalhada de cada tela principal
   - Posicionamento de elementos UI
   - Sistemas de grid e responsividade
   - Densidade de informação e hierarquia visual

3. Interações e Comportamento:
   - Respostas a ações do usuário
   - Micro-interações
   - Feedback e estados do sistema
   - Animações e transições funcionais

4. Padrões e Componentes UI:
   - Biblioteca de componentes utilizados
   - Padrões de design recorrentes
   - Comportamento de formulários e validação
   - Tratamento de erros na interface

5. Considerações de Acessibilidade:
   - Conformidade com WCAG
   - Suporte a leitores de tela
   - Navegação por teclado
   - Contraste e legibilidade

6. Responsividade e Adaptabilidade:
   - Breakpoints e adaptações de layout
   - Comportamento em diferentes tamanhos de tela
   - Touch vs. mouse optimization

7. Estados e Casos Especiais:
   - Estados vazios e de erro
   - Skeletons e estados de carregamento
   - Feedback para operações longas
   - Internacionalização e localização

8. Especificações para Implementação:
   - Espaçamento e dimensões precisas
   - Tipografia detalhada
   - Paleta de cores com valores específicos
   - Assets e recursos necessários

O design deve ser detalhado o suficiente para orientar a implementação direta, coerente com os princípios de usabilidade e alinhado com a identidade visual do sistema.
```

## Prompt para Design de Mecanismo de Testes

```
Atue como um arquiteto de qualidade de software especializado em estratégias de teste.

Preciso criar um design detalhado para o mecanismo de testes do componente [nome do componente] do sistema [nome do sistema]. Este componente [descreva brevemente a função do componente] e precisa ser rigorosamente testado para garantir [requisitos de qualidade principais].

Contexto:
- Complexidade do componente: [descrição da complexidade técnica]
- Riscos principais: [áreas de maior risco]
- Ambiente de testes disponível: [infraestrutura, ferramentas, restrições]
- Integração com CI/CD: [pipeline existente, gates de qualidade]

Por favor, elabore um design detalhado de testes que inclua:

1. Estratégia Global de Testes:
   - Níveis de teste (unitário, integração, sistema, etc.)
   - Abordagem (TDD, BDD, exploratório, etc.)
   - Cobertura esperada e métricas de qualidade
   - Balanço entre testes automatizados e manuais

2. Testes Unitários:
   - Estrutura e organização
   - Frameworks e ferramentas
   - Abordagem para mocking e stubs
   - Padrões de teste por tipo de objeto (services, controllers, etc.)

3. Testes de Integração:
   - Escopo e fronteiras
   - Estratégia para dependências externas
   - Dados de teste e gerenciamento de estado
   - Orquestração de cenários complexos

4. Testes de Performance:
   - Métricas e limites aceitáveis
   - Cenários de carga e stress
   - Ferramentas e metodologia
   - Análise e interpretação de resultados

5. Testes de Segurança:
   - Áreas de foco (injeção, autenticação, etc.)
   - Técnicas e ferramentas
   - Integração com análise estática e dinâmica
   - Verificação de conformidade

6. Infraestrutura de Testes:
   - Ambientes necessários
   - Dados de teste e estratégia de geração
   - Configuração e gestão de ambiente
   - Containerização e isolamento

7. Automação e CI/CD:
   - Integração no pipeline
   - Estratégia de execução (tudo vs. smoke tests)
   - Relatórios e dashboards
   - Gestão de falhas e retrials

8. Manutenção e Evolução:
   - Estratégia para refatoração de testes
   - Gestão de testes legados
   - Processos para atualização contínua

O design deve ser abrangente mas pragmático, focando em obter o máximo de confiabilidade com uso eficiente de recursos de teste.
```

## Prompt para LLD Completo

```
Atue como um arquiteto de software especializado em design detalhado de sistemas.

Preciso criar um documento completo de Low-Level Design (LLD) para o subsistema [nome do subsistema] do sistema [nome do sistema]. Este subsistema é responsável por [descreva brevemente a responsabilidade] e foi definido no documento de High-Level Design como [referência ao HLD].

Por favor, desenvolva um LLD completo cobrindo todos os aspectos deste subsistema:

1. Introdução
   - Propósito e escopo do subsistema
   - Relação com outros subsistemas
   - Dependências e interfaces externas
   - Pressupostos e restrições

2. Arquitetura Detalhada
   - Decomposição em componentes e módulos
   - Responsabilidades específicas de cada componente
   - Diagramas detalhados de classes/componentes (descreva textualmente)
   - Padrões de design aplicados

3. Interfaces e Contratos
   - API completa de cada componente (métodos, parâmetros, retornos)
   - Protocolos de comunicação interna
   - Interfaces com sistemas externos
   - Tratamento de erros e exceções

4. Fluxos de Processamento
   - Fluxogramas detalhados para operações principais
   - Diagramas de sequência para interações complexas
   - Estados e transições
   - Manipulação de casos especiais

5. Modelos de Dados
   - Estruturas de dados internas
   - Esquema de banco de dados (se aplicável)
   - Transformações e mapeamentos
   - Estratégias de persistência

6. Algoritmos Críticos
   - Pseudocódigo detalhado para algoritmos complexos
   - Análise de complexidade
   - Otimizações implementadas
   - Justificativas para abordagens escolhidas

7. Concorrência e Sincronização
   - Modelo de threading
   - Acesso a recursos compartilhados
   - Proteção contra condições de corrida
   - Deadlock prevention

8. Considerações de Implantação
   - Requisitos de ambiente
   - Configuração e parametrização
   - Dependências de runtime
   - Sequência de inicialização

9. Testabilidade
   - Estratégias para testes unitários
   - Pontos de injeção para mocks
   - Testabilidade de casos-limite
   - Cobertura esperada

10. Considerações Não-funcionais
    - Performance e otimizações
    - Segurança em nível de componente
    - Escalabilidade horizontal/vertical
    - Monitoramento e observabilidade

O LLD deve ser detalhado o suficiente para que desenvolvedores possam implementar diretamente a partir dele, sem ambiguidades ou decisões de design significativas pendentes.
```
