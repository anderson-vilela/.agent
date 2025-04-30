# security-guidelines

# Prompt para Security Guidelines

## Contexto do Projeto

Estou desenvolvendo um sistema [descreva o tipo de sistema] chamado [nome do sistema], que lida com [tipos de dados, especialmente dados sensíveis]. O sistema será utilizado por [perfil dos usuários] e estará disponível em [ambientes de implantação, ex: nuvem pública, on-premises].

## Escopo do Documento

Preciso criar diretrizes de segurança abrangentes que estabeleçam os requisitos e práticas de segurança que devem ser implementados durante todo o ciclo de desenvolvimento do sistema. Este documento servirá como referência para desenvolvedores, arquitetos, equipes de operações e testes.

## Requisitos para Elaboração

Por favor, ajude-me a criar Security Guidelines completas que incluam:

### 1. Princípios e Políticas de Segurança

- **Princípios Fundamentais**:

  - Modelo de segurança básico (defesa em profundidade, privilégio mínimo, etc.)
  - Abordagem de "security by design"
  - Governança e responsabilidades de segurança

- **Políticas Gerais**:
  - Classificação e tratamento de dados
  - Gestão de identidades e acessos
  - Segurança física e de infraestrutura
  - Segurança de endpoints

### 2. Requisitos de Segurança

- **Autenticação e Autorização**:

  - Métodos de autenticação aceitáveis
  - Requisitos de senhas e credenciais
  - Gerenciamento de sessões
  - Controle de acesso baseado em papéis/funções

- **Proteção de Dados**:

  - Criptografia de dados em trânsito e em repouso
  - Anonimização e pseudonimização
  - Gerenciamento de chaves
  - Proteção de dados pessoais

- **Segurança de APIs e Serviços**:

  - Autenticação e autorização de APIs
  - Proteção contra ataques (rate limiting, CORS, etc.)
  - Geração e validação de tokens
  - Documentação segura de APIs

- **Segurança da Aplicação**:
  - Proteção contra vulnerabilidades OWASP Top 10
  - Validação de entrada e sanitização de saída
  - Prevenção de ataques comuns (XSS, CSRF, injeção SQL, etc.)
  - Gerenciamento seguro de dependências

### 3. Práticas de Desenvolvimento Seguro

- **Ciclo de Vida de Desenvolvimento Seguro**:

  - Integração de segurança no processo de desenvolvimento
  - Code reviews focados em segurança
  - Ferramentas e automação para segurança

- **Requisitos de Codificação Segura**:
  - Melhores práticas por linguagem/plataforma
  - Gerenciamento de erros e exceções
  - Logging seguro
  - Proteção de configurações sensíveis

### 4. Segurança de Infraestrutura

- **Ambientes de Implantação**:

  - Hardening de servidores e contêineres
  - Configuração segura de serviços em nuvem
  - Segmentação de rede
  - Proteção de perímetro

- **Monitoramento e Detecção**:
  - Logging de eventos de segurança
  - Monitoramento de atividades suspeitas
  - Detecção de intrusão
  - Alertas e notificações

### 5. Resposta a Incidentes

- **Plano de Resposta**:

  - Procedimentos de detecção
  - Processos de contenção e erradicação
  - Recuperação e lições aprendidas
  - Comunicação e escalonamento

- **Testes de Segurança**:
  - Tipos de testes requeridos (SAST, DAST, pentests)
  - Frequência e escopo dos testes
  - Gestão de vulnerabilidades
  - Critérios de aceitação

## Considerações Específicas

- **Regulatórias**: Nosso sistema deve atender aos seguintes requisitos regulatórios [mencione regulamentações aplicáveis como GDPR, LGPD, PCI-DSS, HIPAA]
- **Indústria**: Estamos no setor de [indústria] que tem requisitos específicos como [mencione requisitos específicos da indústria]
- **Tecnologia**: Nossa stack tecnológica principal inclui [mencione tecnologias principais]
- **Ameaças**: As principais ameaças ao nosso sistema incluem [liste ameaças relevantes]

## Resultado Esperado

Um documento abrangente e prático de diretrizes de segurança que possa ser facilmente entendido e implementado por toda a equipe, resultando em um sistema que proteja efetivamente os dados e funcionalidades contra ameaças à segurança.
