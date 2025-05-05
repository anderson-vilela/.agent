# Prompts para Documento de Controle de Interfaces

Este documento contém prompts específicos para gerar a documentação de Controle de Interfaces, que especifica como diferentes componentes e sistemas se comunicam e interagem entre si.

## Prompt para Documento de Controle de Interfaces Completo

```prompt
Como especialista em engenharia de software, crie um Documento de Controle de Interfaces (ICD - Interface Control Document) completo para o sistema [nome do sistema/projeto]. O documento deve especificar detalhadamente:

1. Visão geral das interfaces:
   - Arquitetura de integrações do sistema
   - Diagrama de contexto mostrando todas as interfaces externas
   - Princípios e padrões gerais adotados
   - Classificação das interfaces por criticidade
   - Matriz de responsabilidades

2. Para cada interface, documentar:
   - Identificador único e nome descritivo
   - Sistemas/componentes envolvidos (origem e destino)
   - Propósito funcional e casos de uso
   - Tipo de interface (síncrona/assíncrona, push/pull)
   - Protocolo de comunicação (REST, GraphQL, SOAP, gRPC, mensageria, etc.)
   - Formato de dados (JSON, XML, binário, etc.)
   - Frequência e gatilhos para troca de dados
   - Volumes estimados e requisitos de performance
   - Estratégias de tratamento de erros e recuperação
   - Requisitos de disponibilidade

3. Especificações técnicas detalhadas:
   - Schema completo de mensagens/payloads
   - Endpoints, tópicos ou filas
   - Cabeçalhos e metadados
   - Códigos de status e respostas esperadas
   - Sequência de chamadas para fluxos complexos
   - Tempos limite e políticas de retry
   - Compressão, criptografia e outras otimizações
   - Versionamento e estratégia de compatibilidade

4. Segurança e controle de acesso:
   - Mecanismos de autenticação e autorização
   - Proteção de dados sensíveis
   - Auditoria e logging
   - Validações de segurança
   - Conformidade com regulamentações

5. Considerações operacionais:
   - Monitoramento e alertas
   - Procedimentos de troubleshooting
   - Processos para mudanças na interface
   - Testes de integração e verificação
   - Ambientes disponíveis
   - Contatos e suporte

Use diagramas, tabelas e exemplos concretos para facilitar a compreensão. O documento deve ser técnico mas claro, permitindo que as equipes implementem corretamente as interfaces sem ambiguidades.
```

## Prompt para Diagrama de Sequência de Interfaces

```prompt
Crie diagramas de sequência detalhados para as principais interfaces do sistema [nome do sistema]. Os diagramas devem:

1. Capturar o fluxo de comunicação entre:
   - Componentes do sistema
   - Sistema e sistemas externos
   - Camadas da aplicação quando relevante

2. Para cada fluxo de interação, mostrar:
   - Ordem cronológica das chamadas
   - Parâmetros principais e formatos
   - Respostas esperadas
   - Fluxos alternativos (sucesso, erro, timeout)
   - Estados críticos e transições
   - Lógica de retry e circuit breaker quando aplicável

3. Incluir detalhes técnicos como:
   - Mecanismos de sincronização
   - Timeouts e deadlines
   - Processos assíncronos
   - Callbacks e webhooks
   - Transações e limites de transação

4. Distinguir visualmente:
   - Chamadas síncronas vs. assíncronas
   - Comunicação em lote vs. individual
   - Pontos de decisão e condições
   - Operações críticas e não-críticas

Use a notação UML padrão para diagramas de sequência, adaptando quando necessário para melhor representar aspectos específicos do sistema. Forneça legendas claras e notas explicativas para padrões complexos ou não-convencionais.

Crie diagramas separados para cada fluxo principal, mantendo um nível de detalhe adequado para implementação, mas sem sobrecarregar com informações desnecessárias.
```

## Prompt para Matriz de Compatibilidade de Interfaces

```prompt
Desenvolva uma Matriz de Compatibilidade abrangente para as interfaces do nosso sistema [nome do sistema]. A matriz deve:

1. Listar todas as versões de interfaces disponíveis:
   - Identificador da versão
   - Data de lançamento
   - Status (atual, deprecated, planejada)
   - Data prevista de descontinuação (se aplicável)

2. Documentar compatibilidade entre:
   - Diferentes versões da mesma interface
   - Interfaces dependentes entre si
   - Componentes do sistema e interfaces
   - Clientes externos e interfaces

3. Para cada combinação, especificar:
   - Compatibilidade completa, parcial ou incompatível
   - Limitações específicas
   - Funcionalidades não disponíveis
   - Adaptadores ou conversões necessários
   - Riscos conhecidos

4. Incluir orientações para:
   - Processo de migração entre versões
   - Período de suporte para cada versão
   - Testes de compatibilidade e validação
   - Documentação de mudanças entre versões

5. Fornecer uma visão de roadmap de interfaces:
   - Novas interfaces planejadas
   - Mudanças previstas em interfaces existentes
   - Plano de descontinuação de interfaces legadas

Organize a matriz de forma visual e intuitiva, usando códigos de cores para indicar níveis de compatibilidade. Inclua notas detalhadas para esclarecer situações complexas ou exceções.
```

## Prompt para Documento de Testes de Interfaces

```prompt
Crie um guia abrangente para testes de interfaces do sistema [nome do sistema], que detalhe:

1. Estratégia geral de testes:
   - Abordagem por níveis (unitário, integração, e2e)
   - Responsabilidades de teste por equipe
   - Ferramentas e frameworks recomendados
   - Ambientes de teste e configurações

2. Casos de teste para cada interface:
   - Testes de contrato e validação de schema
   - Testes de fluxos principais (happy path)
   - Testes de casos de borda e exceções
   - Testes de performance e carga
   - Testes de resiliência e recuperação
   - Testes de segurança específicos

3. Para cada caso de teste, especificar:
   - Pré-condições e setup
   - Dados de entrada
   - Passos de execução
   - Resultados esperados
   - Critérios de aprovação
   - Procedimentos de cleanup

4. Procedimentos de automação:
   - Estrutura dos testes automatizados
   - Como implementar novos testes
   - Integração com CI/CD
   - Relatórios e notificações
   - Manutenção dos testes

5. Abordagem para mocks e simuladores:
   - Quando e como usar mocks
   - Implementação de simuladores para sistemas externos
   - Geração de dados sintéticos
   - Gravação e reprodução de interações

Inclua exemplos concretos de código de teste para cada tipo de interface (REST, mensageria, etc.). Forneça templates ou snippets que as equipes possam adaptar para suas necessidades específicas.
```

## Prompt para Guia de Troubleshooting de Interfaces

```prompt
Desenvolva um guia detalhado de troubleshooting para as interfaces do sistema [nome do sistema]. O guia deve:

1. Documentar procedimentos para diagnosticar problemas comuns:
   - Falhas de conectividade
   - Erros de validação/schema
   - Problemas de desempenho
   - Timeout e latência
   - Erros de autenticação/autorização
   - Inconsistências de dados
   - Problemas de concorrência

2. Para cada tipo de problema, incluir:
   - Sintomas observáveis
   - Possíveis causas
   - Ferramentas de diagnóstico
   - Comandos e queries úteis
   - Logs relevantes a verificar
   - Métricas a monitorar
   - Procedimentos passo-a-passo para isolamento do problema

3. Fornecer guias de recuperação:
   - Procedimentos para restabelecer serviços
   - Como lidar com dados inconsistentes
   - Estratégias para processamento de backlog
   - Processos de sincronização após falha
   - Procedimentos de rollback quando necessário

4. Incluir recursos para:
   - Listas de verificação para triagem rápida
   - Árvores de decisão para diagnóstico
   - Templates para registro de incidentes
   - Protocolos de escalação
   - Contatos para suporte

5. Documentar cenários avançados:
   - Falhas cascata entre múltiplas interfaces
   - Degradação progressiva de performance
   - Recuperação de desastres
   - Problemas intermitentes

Use um formato estruturado com exemplos reais, capturas de tela de ferramentas de monitoramento, e snippets de logs reais (com dados sensíveis sanitizados). Organize o guia para permitir tanto a resolução rápida de problemas conhecidos quanto a investigação sistemática de novos problemas.
```
