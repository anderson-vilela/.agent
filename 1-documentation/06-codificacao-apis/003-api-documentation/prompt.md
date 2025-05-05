# Prompts para Documentação de APIs

Este documento contém prompts específicos para gerar documentação de APIs, ajudando a definir e documentar as interfaces programáticas do sistema de forma clara e abrangente.

## Prompt para Documentação Completa de API

```prompt
Como especialista em documentação técnica, crie uma documentação abrangente para a API [nome da API] do nosso projeto. A documentação deve incluir:

1. Visão geral da API:
   - Propósito e casos de uso principais
   - Arquitetura e design (REST, GraphQL, gRPC, etc.)
   - Autenticação e autorização
   - Limitações e quotas
   - Versões disponíveis
   - Ambientes (desenvolvimento, homologação, produção)

2. Guia de início rápido:
   - Pré-requisitos
   - Processo de onboarding/registro
   - Exemplos básicos de uso
   - Fluxos de autenticação
   - Respostas a erros comuns

3. Referência detalhada de endpoints:
   - Listagem organizada por recurso/funcionalidade
   - Para cada endpoint:
     - Método HTTP e URL completa
     - Descrição da funcionalidade
     - Parâmetros de requisição (path, query, header, body)
     - Formato de resposta com status codes
     - Exemplos de request e response
     - Tratamento de erros específicos
     - Limitações ou considerações especiais

4. Guias e tutoriais:
   - Fluxos de trabalho comuns
   - Implementações para casos de uso específicos
   - Integração com outras APIs ou sistemas
   - Práticas recomendadas
   - Otimizações e dicas de performance

5. Referências técnicas:
   - Modelos de dados e schemas
   - Enumerações e constantes
   - Códigos de erro
   - Glossário de termos
   - SDKs e bibliotecas disponíveis

Use uma linguagem clara e objetiva, com exemplos de código em [linguagens relevantes para o projeto]. Organize a documentação de forma hierárquica e com navegação intuitiva.
```

## Prompt para Especificação OpenAPI/Swagger

```prompt
Crie uma especificação OpenAPI (anteriormente conhecida como Swagger) completa em formato YAML para a API [nome da API]. A especificação deve:

1. Incluir informações básicas:
   - Título e descrição da API
   - Versão
   - Servidores/ambientes disponíveis
   - Informações de contato e licença
   - Tags para agrupamento lógico

2. Definir esquemas de segurança:
   - Métodos de autenticação (API Key, OAuth2, etc.)
   - Escopos necessários
   - Fluxos de autorização

3. Detalhar todos os endpoints, incluindo:
   - Paths organizados logicamente
   - Métodos HTTP suportados
   - Descrições claras de operações
   - Parâmetros de requisição (path, query, header, body)
   - Esquemas de resposta para diferentes status codes
   - Exemplos de requisição e resposta

4. Definir modelos de dados:
   - Schemas para todos os objetos
   - Propriedades com tipos, formatos e descrições
   - Valores de exemplo
   - Relacionamentos entre schemas

5. Documentar erros:
   - Respostas de erro padronizadas
   - Códigos de erro específicos
   - Descrições claras de situações de erro

A especificação deve ser válida segundo a versão 3.0.3 do OpenAPI e pronta para importação em ferramentas como Swagger UI, Postman ou ReDoc.
```

## Prompt para Guia de Melhores Práticas de API

```prompt
Desenvolva um guia abrangente de melhores práticas para o design, desenvolvimento e manutenção de APIs em nosso projeto. O guia deve abordar:

1. Princípios de design de API:
   - Consistência e previsibilidade
   - Convenções de nomenclatura
   - Versionamento e evolução
   - Idempotência e segurança de operações
   - Granularidade de recursos
   - HATEOAS e navegabilidade

2. Práticas de segurança:
   - Autenticação e autorização
   - Validação de entrada
   - Proteção contra ataques comuns
   - Rate limiting e throttling
   - Tratamento seguro de dados sensíveis
   - Auditoria e logging

3. Performance e escalabilidade:
   - Estratégias de cache
   - Paginação e filtros
   - Compressão de resposta
   - Otimização de consultas
   - Bulk operations
   - Padrões assíncronos quando apropriado

4. Tratamento de erros e depuração:
   - Estrutura padronizada de erros
   - Códigos de status HTTP apropriados
   - Mensagens de erro claras e acionáveis
   - Logging e rastreamento
   - Suporte à depuração

5. Ciclo de vida e governança:
   - Estratégias de versionamento
   - Processo de descontinuação (deprecation)
   - Monitoramento e métricas
   - Documentação contínua
   - Testes e qualidade

Para cada tópico, inclua exemplos concretos, contra-exemplos e justificativas para as recomendações. O guia deve ser específico para nossas tecnologias e padrões organizacionais, quando aplicável.
```

## Prompt para Tutorial de Uso da API

```prompt
Crie um tutorial completo e passo a passo para desenvolvedores que estão começando a usar nossa API [nome da API]. O tutorial deve:

1. Introduzir o cenário e objetivo:
   - Descrever um caso de uso real e relevante
   - Definir o resultado esperado
   - Listar pré-requisitos técnicos

2. Guiar o processo de setup:
   - Como obter credenciais
   - Ferramentas recomendadas (Postman, curl, etc.)
   - Configuração de ambiente local

3. Explicar cada passo da integração:
   - Construção das primeiras chamadas
   - Autenticação
   - Processamento de respostas
   - Tratamento de erros

4. Mostrar exemplos completos em múltiplas linguagens:
   - [Linguagem 1]
   - [Linguagem 2]
   - [Linguagem 3, se aplicável]

5. Incluir práticas avançadas:
   - Otimizações
   - Casos de borda
   - Técnicas de depuração
   - Solução de problemas comuns

O tutorial deve ser estruturado como uma jornada lógica, com cada passo construindo sobre o anterior. Inclua snippets de código completos e prontos para uso, bem como capturas de tela quando relevante.
```

## Prompt para Changelog e Roadmap de API

```prompt
Desenvolva um documento combinando o histórico de mudanças (changelog) e plano futuro (roadmap) para nossa API [nome da API]. O documento deve:

1. Descrever o sistema de versionamento:
   - Explicar a estratégia de versionamento (semântico, data, etc.)
   - Definir políticas de compatibilidade
   - Estabelecer ciclos de lançamento e suporte

2. Detalhar o histórico de versões (das mais recentes para as mais antigas):
   - Para cada versão:
     - Número da versão e data de lançamento
     - Novas funcionalidades com descrições
     - Mudanças em funcionalidades existentes
     - Correções de bugs
     - Breaking changes e instruções de migração
     - Deprecações e planos de descontinuação

3. Apresentar o roadmap:
   - Próxima versão (em desenvolvimento):
     - Funcionalidades planejadas
     - Estimativa de lançamento
     - Status de implementação

   - Médio prazo (próximos 3-6 meses):
     - Funcionalidades principais planejadas
     - Melhorias técnicas
     - Mudanças arquiteturais

   - Longo prazo (visão estratégica):
     - Direção geral da API
     - Tecnologias futuras
     - Integrações planejadas

4. Incluir orientações para feedback e contribuições:
   - Como sugerir novas funcionalidades
   - Processo para reportar bugs
   - Canais de comunicação com a equipe

Use uma linguagem clara e objetiva, com datas específicas quando possível e indicadores visuais para destacar breaking changes ou deprecações importantes.
```
