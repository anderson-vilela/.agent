# Prompts para Business Requirements Document (BRD)

## Prompt para Criação de BRD Completo

```
Como analista de negócios sênior, preciso criar um Business Requirements Document (BRD) completo para o projeto [NOME DO PROJETO].

Contexto do negócio:
- Descrição da empresa/departamento: [DESCRIÇÃO]
- Problema ou oportunidade de negócio: [PROBLEMA/OPORTUNIDADE]
- Objetivos estratégicos relacionados: [OBJETIVOS]
- Stakeholders principais: [STAKEHOLDERS]
- Sistemas atuais envolvidos: [SISTEMAS]

Por favor, elabore um BRD abrangente e estruturado que inclua:

1. Introdução
   - Propósito do documento
   - Escopo do projeto
   - Definições, acrônimos e abreviações
   - Documentos relacionados
   - Visão geral do documento

2. Visão Geral do Projeto
   - Descrição do problema ou oportunidade de negócio
   - Objetivos e metas do projeto
   - Benefícios esperados
   - Alinhamento com objetivos estratégicos
   - Critérios de sucesso mensuráveis

3. Escopo do Projeto
   - Declaração de escopo de negócio
   - Processos de negócio afetados
   - Departamentos e funções impactados
   - Fronteiras e exclusões (o que não está no escopo)
   - Entregas principais esperadas

4. Stakeholders
   - Identificação e classificação dos stakeholders
   - Papéis e responsabilidades
   - Necessidades e expectativas de informação
   - Níveis de engajamento necessários

5. Requisitos de Negócio Detalhados
   - Requisitos funcionais do negócio por área/processo
   - Fluxos de processo desejados (atuais vs. futuros)
   - Regras de negócio
   - Requisitos de dados e relatórios
   - Requisitos de ambiente e infraestrutura
   - Requisitos de segurança e conformidade
   - Requisitos de desempenho de negócio

6. Restrições e Premissas de Negócio
   - Limitações orçamentárias
   - Restrições de prazo
   - Limitações legais e regulatórias
   - Restrições técnicas de alto nível
   - Premissas críticas para o planejamento

7. Impactos e Dependências
   - Impactos em processos existentes
   - Impactos organizacionais
   - Dependências de outros projetos ou iniciativas
   - Cronograma macro de implementação
   - Necessidades de transição

8. Critérios de Aceitação
   - Critérios de aceitação para requisitos críticos
   - Processo de validação de negócio
   - Aprovações necessárias

9. Análise de Riscos de Negócio
   - Riscos principais identificados
   - Impacto potencial nos objetivos de negócio
   - Estratégias de mitigação em nível de negócio

10. Apêndices
    - Organogramas relevantes
    - Fluxogramas de processos atuais
    - Modelos conceituais de dados
    - Resultados de workshops e entrevistas
    - Glossário de termos de negócio

O documento deve ter foco exclusivo nos requisitos de negócio (o "QUE"), deixando a implementação técnica (o "COMO") para documentos subsequentes como o SRS. Todos os requisitos devem ser claros, não ambíguos, testáveis e rastreáveis.
```

## Prompt para Identificação e Documentação de Stakeholders

```
Como especialista em análise de stakeholders, preciso desenvolver a seção de análise de stakeholders para o BRD do projeto [NOME DO PROJETO].

Contexto do projeto:
- Objetivo principal: [OBJETIVO]
- Escopo geral: [ESCOPO]
- Áreas da empresa afetadas: [ÁREAS]
- Sistemas impactados: [SISTEMAS]

Por favor, crie uma análise abrangente de stakeholders que inclua:

1. Metodologia de Identificação
   - Técnicas utilizadas para identificar stakeholders
   - Critérios de categorização e priorização
   - Framework de análise adotado

2. Mapeamento de Stakeholders
   - Matriz de influência vs. interesse
   - Categorização (primários, secundários, terciários)
   - Internos vs. externos
   - Atitudes previstas (apoiadores, neutros, resistentes)

3. Stakeholders Internos (para cada grupo)
   - Departamento/função
   - Papel no projeto
   - Necessidades e expectativas específicas
   - Preocupações principais
   - Nível de envolvimento requerido
   - Impacto do projeto em suas atividades
   - Poder de decisão e influência

4. Stakeholders Externos (para cada grupo)
   - Organização/entidade
   - Relação com o projeto
   - Interesses e motivações
   - Expectativas e necessidades
   - Influência no sucesso do projeto
   - Estratégia de engajamento recomendada

5. Usuários Finais
   - Perfis detalhados de usuário
   - Necessidades específicas por perfil
   - Experiência atual vs. desejada
   - Volume e frequência de uso
   - Impacto na rotina de trabalho
   - Potencial resistência à mudança

6. Decisores-Chave
   - Identificação clara dos decisores
   - Processos de aprovação relacionados
   - Critérios de decisão importantes
   - Preferências de comunicação

7. Plano de Engajamento
   - Estratégia para cada categoria de stakeholder
   - Frequência e métodos de comunicação
   - Responsáveis pelo engajamento
   - Abordagem para gestão de conflitos
   - Mecanismos de feedback contínuo

8. Matriz RACI para Requisitos
   - Responsáveis (Responsible)
   - Aprovadores (Accountable)
   - Consultados (Consulted)
   - Informados (Informed)

A análise deve ser objetiva e baseada em fatos, reconhecendo diferentes perspectivas e necessidades, e fornecendo uma base sólida para o planejamento de comunicações e engajamento durante todo o projeto.
```

## Prompt para Documentação de Fluxos de Processo (Atual vs. Futuro)

```
Como analista de processos de negócio, preciso documentar os fluxos de processo atuais e futuros para o BRD do projeto [NOME DO PROJETO].

Contexto do processo:
- Nome do processo: [NOME DO PROCESSO]
- Área de negócio: [ÁREA]
- Sistemas atuais utilizados: [SISTEMAS]
- Problemas/ineficiências conhecidos: [PROBLEMAS]
- Objetivos de melhoria: [OBJETIVOS]

Por favor, elabore uma documentação detalhada dos fluxos de processo que inclua:

1. Visão Geral do Processo
   - Propósito e objetivos do processo
   - Entradas e saídas principais
   - Métricas-chave de processo (KPIs)
   - Frequência e volume de execução
   - Criticidade para o negócio

2. Mapeamento do Processo Atual ("As Is")
   - Diagrama de fluxo detalhado (BPMN ou similar)
   - Atores e sistemas envolvidos
   - Passos sequenciais com decisões
   - Pontos de interação com outros processos
   - Pontos de controle e aprovação
   - Tempos e durações típicas
   - Dados manipulados em cada etapa
   - Gargalos e pontos de ineficiência identificados
   - Riscos e problemas conhecidos

3. Análise de Gaps e Oportunidades
   - Problemas e ineficiências do processo atual
   - Causas-raiz identificadas
   - Oportunidades de automação
   - Oportunidades de simplificação
   - Métricas comparativas (benchmarks)
   - Impacto dos problemas nos objetivos de negócio

4. Fluxo de Processo Futuro ("To Be")
   - Diagrama de fluxo proposto
   - Mudanças principais em relação ao processo atual
   - Novos atores, papéis ou sistemas
   - Automações e integrações propostas
   - Pontos de decisão revisados
   - Controles e governança aprimorados
   - Tratamento de exceções

5. Benefícios Esperados
   - Melhorias quantitativas esperadas (tempo, custo, qualidade)
   - Melhorias qualitativas
   - Impacto em outros processos relacionados
   - Realização de objetivos estratégicos

6. Requisitos Específicos por Etapa
   - Lista detalhada de requisitos para cada etapa do novo processo
   - Dados necessários e suas fontes
   - Regras de negócio aplicáveis
   - Necessidades de integração
   - Requisitos de relatórios e monitoramento

7. Impactos e Considerações de Implementação
   - Mudanças organizacionais necessárias
   - Necessidades de treinamento
   - Potenciais resistências e estratégias
   - Abordagem de transição recomendada
   - Riscos específicos do novo processo

A documentação deve ser clara o suficiente para que os stakeholders de negócio possam validar o entendimento e para que a equipe técnica possa derivar requisitos técnicos específicos posteriormente.
```

## Prompt para Elaboração de Regras de Negócio

```
Como especialista em regras de negócio, preciso documentar as regras de negócio para o BRD do projeto [NOME DO PROJETO].

Contexto do domínio:
- Área funcional: [ÁREA]
- Processos relacionados: [PROCESSOS]
- Regulamentações aplicáveis: [REGULAMENTAÇÕES]
- Políticas organizacionais relevantes: [POLÍTICAS]

Por favor, elabore uma documentação abrangente de regras de negócio que inclua:

1. Metodologia de Categorização
   - Sistema de numeração e referência
   - Categorias de regras utilizadas
   - Níveis de prioridade e aplicabilidade
   - Formato padronizado de descrição

2. Regras de Definição
   - Definições de termos e conceitos de negócio
   - Taxonomias e hierarquias
   - Relações entre entidades de negócio
   - Escopos e limites de aplicação

3. Regras de Fatos
   - Verdades fundamentais do domínio
   - Relacionamentos imutáveis
   - Restrições de domínio

4. Regras de Restrição
   - Limitações e proibições
   - Restrições de valores e faixas
   - Condições obrigatórias
   - Restrições de integridade
   - Restrições temporais

5. Regras de Derivação
   - Cálculos e fórmulas
   - Processamento de dados
   - Transformações
   - Algoritmos de negócio específicos

6. Regras de Inferência
   - Lógica condicional (Se-Então)
   - Avaliações baseadas em múltiplos fatores
   - Lógica de decisão complexa
   - Árvores de decisão

7. Regras de Processo
   - Sequenciamento de atividades
   - Condições de entrada/saída
   - Tempos de espera e timeouts
   - Tratamento de exceções
   - Regras de escalação

8. Regras de Autorização
   - Controle de acesso a funcionalidades
   - Delegação de autoridade
   - Níveis de aprovação
   - Segregação de funções

9. Regras de Conformidade
   - Requisitos regulatórios específicos
   - Políticas corporativas mandatórias
   - Requisitos de auditoria e rastreabilidade
   - Retenção de dados

10. Matriz de Rastreabilidade
    - Origem da regra (política, regulamento, requisito)
    - Processos e casos de uso afetados
    - Dependências entre regras
    - Sistemas onde a regra é implementada

Cada regra deve ser:
- Atômica (expressando apenas um conceito)
- Clara e não ambígua
- Consistente com outras regras
- Verificável/testável
- Expressa em linguagem de negócio (não técnica)
- Apresentada com exemplos quando apropriado

O documento deve servir como fonte autoritativa para as regras de negócio que governam o domínio, independente de como serão implementadas tecnicamente.
```

## Prompt para Requisitos de Relatórios e Analytics

```
Como especialista em business intelligence, preciso documentar os requisitos de relatórios e analytics para o BRD do projeto [NOME DO PROJETO].

Contexto de negócio:
- Objetivos de negócio relacionados: [OBJETIVOS]
- Indicadores-chave (KPIs): [KPIs]
- Público-alvo dos relatórios: [PÚBLICO]
- Fontes de dados disponíveis: [FONTES]
- Limitações atuais: [LIMITAÇÕES]

Por favor, elabore uma documentação completa de requisitos de relatórios e analytics que inclua:

1. Visão Geral das Necessidades Analíticas
   - Objetivos analíticos principais
   - Decisões de negócio a serem suportadas
   - Lacunas atuais no acesso a dados e insights
   - Frequência e urgência das necessidades de informação

2. Requisitos de Dados
   - Entidades e atributos de dados necessários
   - Granularidade requerida dos dados
   - Dimensões de análise importantes
   - Métricas e cálculos derivados
   - Período histórico necessário
   - Requisitos de atualização (tempo real, diário, etc.)
   - Qualidade e integridade necessárias

3. Relatórios Operacionais
   - Lista de relatórios necessários
   - Propósito e público-alvo de cada relatório
   - Conteúdo detalhado (campos, filtros, classificações)
   - Layout preferido e visualizações
   - Critérios de filtro e segmentação
   - Requisitos de formatação e exportação
   - Frequência de geração/atualização
   - Método de entrega (e-mail, portal, API, etc.)

4. Dashboards e Visualizações
   - Dashboards necessários por função/perfil
   - KPIs a serem monitorados
   - Componentes visuais requeridos
   - Interatividade esperada (drill-down, filtros, etc.)
   - Alertas e thresholds importantes
   - Visualização em dispositivos móveis
   - Personalização por usuário

5. Analytics Avançados
   - Necessidades de análise preditiva
   - Segmentações e agrupamentos desejados
   - Detecção de anomalias e exceções
   - Análises de tendências temporais
   - Comparações e benchmarking
   - Requisitos de machine learning (se aplicável)

6. Self-Service e Exploração
   - Capacidades de auto-serviço requeridas
   - Tipos de análise ad-hoc necessários
   - Perfis de usuário para self-service
   - Necessidades de customização de relatórios
   - Requisitos de exportação e manipulação

7. Requisitos de Distribuição e Acesso
   - Mecanismos de entrega (pull vs. push)
   - Agendamento de distribuição
   - Controles de acesso e segurança
   - Necessidades de compartilhamento
   - Requisitos de acesso offline
   - Notificações e alertas

8. Requisitos Não-Funcionais
   - Performance esperada (tempo de resposta)
   - Volume de usuários simultâneos
   - Disponibilidade requerida
   - Compatibilidade com dispositivos/navegadores
   - Necessidades de impressão
   - Acessibilidade e internacionalização

9. Priorização e Faseamento
   - Classificação por valor de negócio
   - Dependências entre relatórios/análises
   - Sugestão de faseamento de implementação
   - Quick wins vs. implementações complexas

10. Critérios de Aceitação
    - Critérios de validação para cada relatório/dashboard
    - Métricas de adoção esperadas
    - Feedback e mecanismos de evolução

Os requisitos devem focar nas necessidades de informação de negócio, não em ferramentas específicas ou implementações técnicas, mantendo clara a conexão entre cada requisito analítico e os objetivos/processos de negócio relacionados.
```
