# Prompts para Estratégia de Testes

Este documento contém prompts específicos para gerar a Estratégia de Testes do projeto, que define a abordagem geral para garantir a qualidade do software.

## Prompt para Documento Completo de Estratégia de Testes

```prompt
Atue como um especialista em qualidade de software. Preciso que você desenvolva uma Estratégia de Testes abrangente para o projeto [nome do projeto]. Este sistema [descreva brevemente o sistema, tecnologias e requisitos críticos].

Por favor, crie um documento de Estratégia de Testes que inclua:

1. Visão geral e objetivos de teste:
   - Propósito e escopo da estratégia de testes
   - Objetivos principais de qualidade
   - Alinhamento com metas de negócio e requisitos

2. Abordagem de testes:
   - Metodologia de testes (ágil, tradicional, híbrida)
   - Pirâmide de testes e balanceamento entre níveis
   - Abordagem baseada em riscos para priorização
   - Estratégia para testes manuais vs. automatizados

3. Níveis de teste detalhados:
   - Testes unitários (escopo, responsabilidades, cobertura alvo)
   - Testes de integração (abordagem, interfaces críticas)
   - Testes de sistema (funcionalidade end-to-end, performance, segurança)
   - Testes de aceitação (validação de requisitos de negócio)

4. Tipos de teste específicos:
   - Testes funcionais
   - Testes de performance e carga
   - Testes de segurança
   - Testes de usabilidade
   - Testes de acessibilidade
   - Testes de compatibilidade
   - Testes de resiliência e recuperação

5. Ambientes e infraestrutura de teste:
   - Descrição dos ambientes necessários
   - Estratégia de dados de teste
   - Ferramentas e frameworks
   - Requisitos de infraestrutura

6. Processo de gestão de testes:
   - Planejamento e estimativa
   - Monitoramento e controle
   - Rastreabilidade (requisitos até casos de teste)
   - Gestão de defeitos
   - Critérios de entrada e saída para cada fase

7. Métricas e relatórios:
   - KPIs de qualidade e performance
   - Métricas de cobertura
   - Métricas de defeitos
   - Estrutura e frequência de relatórios

8. Papéis e responsabilidades:
   - Equipe de QA
   - Desenvolvedores
   - DevOps
   - Stakeholders e usuários

9. Fatores de risco e mitigação:
   - Riscos principais para a qualidade
   - Estratégias de mitigação
   - Planos de contingência

10. Integração com DevOps e CI/CD:
    - Automação no pipeline
    - Verificações de qualidade automatizadas
    - Feedback contínuo e gates de qualidade

Por favor, apresente este documento em formato estruturado, com seções e subseções claramente definidas. Inclua introdução e resumo executivo. O documento deve ser abrangente mas prático, com foco em diretrizes e estratégias que possam ser efetivamente implementadas pela equipe.
```

## Prompt para Definição da Abordagem de Testes

```prompt
Como especialista em estratégias de teste, preciso definir uma abordagem equilibrada para os testes do projeto [nome do projeto]. Este é um [tipo de sistema] que [principais características e criticidade].

Por favor, ajude-me a elaborar uma seção de "Abordagem de Testes" que:

1. Recomende a proporção ideal entre os diferentes níveis de teste (unitário, integração, sistema, aceitação) considerando:
   - A arquitetura do sistema [descreva brevemente]
   - Riscos técnicos e de negócio
   - Restrições de recursos e tempo

2. Detalhe a implementação da pirâmide de testes, incluindo:
   - Justificativa para a distribuição proposta
   - Cobertura esperada em cada nível
   - Trade-offs e compromissos

3. Explique como balancear testes manuais e automatizados:
   - Critérios para decidir o que automatizar
   - Estratégia de automação progressiva
   - Abordagem para testes exploratórios

4. Proponha uma estratégia baseada em riscos, detalhando:
   - Processo para identificação e classificação de riscos
   - Matriz de priorização de testes
   - Como ajustar a intensidade de testes conforme o risco

A abordagem deve ser pragmática, considerar limitações reais de projetos, e fornecer flexibilidade para adaptação conforme o projeto evolui.
```

## Prompt para Especificação de Níveis de Teste

```prompt
Como arquiteto de qualidade, preciso detalhar os níveis de teste para nosso projeto [nome do projeto]. Considerando que estamos utilizando [tecnologias/frameworks] e seguindo uma metodologia [ágil/híbrida/tradicional], elabore uma especificação completa dos níveis de teste a serem implementados.

Para cada nível de teste (unitário, integração, sistema, aceitação), por favor detalhe:

1. Escopo e objetivos específicos:
   - O que será testado neste nível
   - Objetivos de qualidade a serem atingidos
   - Limites e fronteiras do escopo

2. Responsabilidades e execução:
   - Quem será responsável pela criação e execução
   - Quando estes testes serão executados no ciclo
   - Pré-requisitos para execução

3. Ferramentas e técnicas:
   - Frameworks e bibliotecas recomendados
   - Abordagens de design de teste (BDD, TDD, etc.)
   - Práticas específicas para este nível

4. Métricas e critérios:
   - Métricas de cobertura esperadas
   - Critérios de aprovação/falha
   - Como medir eficácia dos testes

5. Integração com o processo:
   - Requisitos de entrada e saída
   - Gates de qualidade relacionados
   - Fluxo de informação e feedback

Forneça exemplos concretos sempre que possível para ilustrar conceitos. O objetivo é ter uma especificação que possa guiar efetivamente a implementação dos diferentes níveis de teste no projeto.
```

## Prompt para Estratégia de Automação de Testes

```prompt
Como especialista em automação de testes, ajude-me a desenvolver uma estratégia abrangente de automação para o projeto [nome do projeto]. O sistema utiliza [tecnologias principais] e tem requisitos específicos de [performance/segurança/disponibilidade/etc.].

Por favor, elabore uma estratégia de automação de testes que inclua:

1. Objetivos e benefícios da automação:
   - Resultados esperados e métricas de sucesso
   - ROI esperado da automação
   - Benefícios específicos para o projeto

2. Escopo da automação:
   - Níveis de teste a serem automatizados
   - Funcionalidades prioritárias para automação
   - Exclusões e limitações

3. Framework e arquitetura de automação:
   - Ferramentas e tecnologias recomendadas
   - Arquitetura da solução de automação
   - Padrões de design (Page Object, etc.)
   - Estratégia para dados de teste

4. Implementação e processo:
   - Abordagem para desenvolvimento dos scripts
   - Integração com CI/CD
   - Execução e agendamento
   - Manutenção e evolução dos testes

5. Best practices específicas:
   - Padrões de codificação
   - Estratégias para testes robustos e estáveis
   - Gerenciamento de dependências externas
   - Tratamento de flakiness e instabilidades

6. Gestão e relatórios:
   - Dashboards e visualização de resultados
   - Análise de tendências e insights
   - Rastreabilidade para requisitos

7. Plano de implementação:
   - Roadmap de adoção e desenvolvimento
   - Abordagem gradual e marcos
   - Capacitação da equipe

A estratégia deve ser prática, considerar o contexto real do projeto, e fornecer diretrizes claras para implementação. Foque em criar uma abordagem sustentável que possa evoluir com o projeto.
```

## Prompt para Definição de Métricas de Qualidade

```prompt
Como especialista em métricas de qualidade de software, ajude-me a definir um conjunto abrangente de métricas para monitorar e melhorar a qualidade do nosso projeto [nome do projeto]. Precisamos de métricas que:

1. Forneçam visibilidade efetiva sobre o estado atual da qualidade
2. Ajudem a prever e prevenir problemas futuros
3. Permitam tomadas de decisão baseadas em dados
4. Estejam alinhadas com nossos objetivos de negócio

Considerando que nosso projeto [descreva características relevantes], por favor elabore:

1. Métricas de cobertura de teste:
   - Tipos de cobertura relevantes para nosso contexto
   - Metas e thresholds para cada tipo
   - Como interpretar e agir com base nos resultados

2. Métricas de defeitos:
   - Classificação e categorização de defeitos
   - Indicadores de densidade, severidade e tendências
   - Métricas de eficácia de testes (taxa de detecção)

3. Métricas de processo:
   - Ciclo de vida dos defeitos
   - Eficiência do processo de teste
   - Progresso e velocidade

4. Métricas de produto:
   - Confiabilidade e estabilidade
   - Performance e eficiência
   - Segurança e conformidade

5. Framework de dashboards e relatórios:
   - Visualizações recomendadas
   - Frequência e formato de relatórios
   - Audiência e foco para diferentes níveis

Para cada métrica proposta, indique:
- Definição clara e fórmula de cálculo
- Fonte dos dados e método de coleta
- Interpretação e limiares recomendados
- Ações sugeridas baseadas nos resultados

O objetivo é criar um framework de métricas prático, que forneça insights acionáveis e promova melhoria contínua de qualidade sem sobrecarga excessiva.
```
