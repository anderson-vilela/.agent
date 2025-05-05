# Prompts para Criação de Dicionário de Dados

Este documento contém prompts específicos para gerar um Dicionário de Dados abrangente, catalogando e descrevendo todas as entidades, atributos e relacionamentos de dados do sistema.

## Prompt para Dicionário de Dados Completo

```prompt
Como especialista em modelagem de dados, crie um Dicionário de Dados completo para nosso sistema [nome do sistema/projeto]. O dicionário deve:

1. Listar todas as entidades principais do sistema, com:
   - Nome formal da entidade
   - Descrição funcional e propósito no sistema
   - Ciclo de vida e estados possíveis
   - Volumetria estimada e padrões de crescimento
   - Classificação de sensibilidade dos dados
   - Responsáveis técnicos e de negócio

2. Para cada entidade, detalhar todos os atributos, incluindo:
   - Nome do atributo (técnico e de negócio)
   - Tipo de dados e formato
   - Tamanho/precisão/escala quando aplicável
   - Obrigatoriedade (requerido, opcional, condicional)
   - Valores padrão e restrições
   - Regras de validação específicas
   - Descrição clara do significado do campo
   - Exemplos de valores válidos

3. Documentar relacionamentos entre entidades:
   - Tipo de relacionamento (1:1, 1:N, N:M)
   - Entidades participantes
   - Cardinalidade e obrigatoriedade
   - Regras de integridade referencial
   - Descrição funcional do relacionamento
   - Impactos em operações (cascata, restrição, etc.)

4. Incluir informações técnicas adicionais:
   - Índices e chaves
   - Particionamentos quando aplicáveis
   - Estratégias de cache
   - Políticas de retenção de dados
   - Considerações de performance

5. Mapear integrações com sistemas externos:
   - Origem/destino dos dados
   - Mecanismos de sincronização
   - Frequência de atualização
   - Transformações aplicadas

Formate o documento de maneira clara, utilizando tabelas, listas e seções bem organizadas. Use uma linguagem técnica, mas com explicações suficientes para que profissionais de negócio também possam compreender.
```

## Prompt para Modelagem Visual do Dicionário

```prompt
Crie uma representação visual do modelo de dados para complementar nosso Dicionário de Dados do sistema [nome do sistema]. A modelagem deve incluir:

1. Diagrama de Entidade-Relacionamento (ER) ou modelo conceitual:
   - Todas as entidades principais
   - Relacionamentos com cardinalidade
   - Atributos-chave
   - Agrupamento lógico por domínios/módulos

2. Modelo lógico de dados:
   - Entidades com todos os atributos
   - Chaves primárias e estrangeiras
   - Índices principais
   - Tipos de dados
   - Restrições de integridade

3. Visualização de fluxo de dados (opcional):
   - Como os dados fluem entre entidades
   - Pontos de integração com sistemas externos
   - Transformações principais

Use uma notação padronizada (UML, IDEF1X, ou similar) e organize o diagrama para maximizar a legibilidade. Adicione uma legenda clara e utilize cores ou outros elementos visuais para distinguir diferentes tipos de entidades ou domínios.

Forneça os diagramas em formato que possa ser facilmente atualizado (como arquivo original de uma ferramenta de modelagem) e também em formato de imagem para inclusão na documentação.
```

## Prompt para Catálogo de Regras de Negócio para Dados

```prompt
Desenvolva um catálogo abrangente de regras de negócio relacionadas aos dados para o sistema [nome do sistema]. O catálogo deve:

1. Identificar e categorizar regras por tipo:
   - Regras de validação e integridade
   - Regras de cálculo e derivação
   - Regras de transformação
   - Regras de acesso e segurança
   - Regras de fluxo e processo

2. Para cada regra, documentar:
   - Identificador único da regra
   - Descrição em linguagem natural
   - Fórmula ou pseudocódigo quando aplicável
   - Entidades e atributos afetados
   - Pontos de aplicação (entrada de dados, persistência, etc.)
   - Tratamento de exceções
   - Prioridade ou ordem de execução quando relevante

3. Estabelecer relacionamentos entre regras:
   - Dependências
   - Conflitos potenciais
   - Agrupamentos lógicos

4. Incluir contexto de implementação:
   - Responsável pela implementação
   - Componentes de sistema onde a regra é aplicada
   - Mecanismos de verificação e teste

Organize o catálogo de forma hierárquica, começando com regras fundamentais e expandindo para regras mais complexas ou específicas. Inclua exemplos concretos para ilustrar a aplicação das regras mais complexas.
```

## Prompt para Documentação de Histórico e Governança de Dados

```prompt
Crie uma documentação abrangente sobre governança e versionamento de dados para nosso sistema [nome do sistema], focando nos seguintes aspectos:

1. Políticas de governança de dados:
   - Papéis e responsabilidades (data owners, stewards, etc.)
   - Processos de aprovação para mudanças no modelo
   - Classificação de dados e requisitos de segurança
   - Padrões de qualidade e métricas
   - Procedimentos de auditoria
   - Conformidade com regulamentações (LGPD, GDPR, etc.)

2. Estratégia de versionamento do modelo de dados:
   - Método de controle de versão
   - Processo para implementação de mudanças
   - Políticas de compatibilidade retroativa
   - Gestão de migrações e transformações

3. Histórico de evolução do modelo:
   - Versões principais com datas
   - Mudanças significativas em cada versão
   - Justificativas de negócio para alterações
   - Impactos em sistemas e integrações

4. Dados históricos e arquivamento:
   - Políticas de retenção por tipo de dado
   - Estratégias de arquivamento
   - Métodos de acesso a dados históricos
   - Agregações e sumarizações ao longo do tempo

5. Qualidade e integridade de dados:
   - Processos de validação e limpeza
   - Monitoramento de qualidade
   - Procedimentos para correção de inconsistências
   - Estratégias para dados ausentes ou incompletos

Formate o documento de maneira estruturada e inclua exemplos concretos de processos. Adicione diagramas de fluxo para processos complexos de governança e tabelas para resumir políticas e responsabilidades.
```

## Prompt para Dicionário de APIs e Integrações de Dados

```prompt
Crie um documento que conecte nosso Dicionário de Dados com as APIs e integrações de dados do sistema [nome do sistema]. Este documento deve:

1. Mapear entidades do dicionário para endpoints de API:
   - Para cada entidade principal, listar endpoints relacionados
   - Indicar operações suportadas (CRUD, operações em lote, etc.)
   - Documentar transformações entre o modelo de API e o modelo de dados
   - Mostrar exemplos de payloads com mapeamento para atributos

2. Documentar fluxos de dados em integrações:
   - Origens e destinos de dados
   - Frequência e gatilhos de sincronização
   - Volumes e performance esperados
   - Mapeamentos de campo entre sistemas
   - Tratamento de conflitos e erros

3. Estabelecer rastreabilidade de dados:
   - Como rastrear a origem de cada dado
   - Logs e auditoria de alterações
   - Metadados de sincronização
   - Versionamento de dados entre sistemas

4. Definir políticas específicas para APIs e integrações:
   - Caching e expiração de dados
   - Rate limiting
   - Políticas de retry
   - Priorização de sincronizações
   - Janelas de manutenção

5. Detalhar considerações de segurança:
   - Controle de acesso por entidade/campo
   - Mascaramento ou tokenização de dados sensíveis
   - Logs de acesso a dados via API
   - Requisitos de conformidade específicos

Organize o documento de forma que seja fácil navegar tanto a partir das entidades de dados quanto a partir das APIs. Utilize diagramas de fluxo para representar integrações complexas e tabelas para mapeamentos detalhados de campos.
```
