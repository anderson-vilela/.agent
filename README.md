# Template Agent 2.0

Um framework abrangente que potencializa o desenvolvimento de software com GitHub Copilot e engenharia de prompts, estabelecendo um novo paradigma para colaboração entre desenvolvedores e ferramentas de inteligência artificial.

## Visão Geral

O Template Agent 2.0 é uma evolução do framework original, fornecendo estruturas, personas, workflows e padrões de código cuidadosamente desenvolvidos para maximizar a eficiência e qualidade em projetos de desenvolvimento assistido por IA.

### Filosofia do Projeto

O Template Agent foi concebido com base em três princípios fundamentais:

1. **Amplificação da Criatividade Humana**: O framework não busca substituir desenvolvedores, mas potencializar suas capacidades, permitindo que foquem em aspectos criativos e estratégicos do desenvolvimento.

2. **Consistência e Qualidade**: Através de personas bem definidas e workflows estruturados, o framework garante uma abordagem consistente, resultando em código mais limpo, testável e manutenível.

3. **Aceleração Responsável**: Embora a velocidade seja um benefício importante, o Template Agent prioriza a qualidade e a robustez, incentivando práticas como testes automatizados, documentação abrangente e revisões rigorosas.

### Benefícios Principais

- **Aumento de Produtividade**: Redução significativa no tempo de implementação de novas funcionalidades e correção de bugs.
- **Onboarding Acelerado**: Desenvolvedores recém-chegados podem entender rapidamente a base de código e contribuir de forma efetiva.
- **Consistência de Código**: Padronização em todo o projeto, facilitando manutenção e escalabilidade.
- **Documentação Integrada**: Geração de documentação técnica de alta qualidade como parte natural do processo de desenvolvimento.
- **Transferência de Conhecimento**: Captura e compartilhamento de expertise entre membros da equipe.

## Workflows Estruturados

O Template Agent 2.0 oferece seis workflows completos e detalhados que cobrem todo o ciclo de vida do desenvolvimento de software:

### 1. Documentação de Projeto

Um processo abrangente para criar documentação de alta qualidade em todas as fases do projeto, desde a concepção até a operação e suporte. Inclui templates para diversos tipos de documentos técnicos e de usuário.

### 2. Implementação de Software

Workflow estruturado para guiar o processo de desenvolvimento, desde a exploração inicial até commits e pull requests, garantindo código de qualidade, testável e alinhado com os padrões do projeto.

### 3. Revisão de Código

Processo detalhado para realizar code reviews eficazes, promovendo qualidade, compartilhamento de conhecimento e melhoria contínua através de feedback construtivo e verificações sistemáticas.

### 4. Correção de Bugs

Metodologia completa para identificação, diagnóstico, correção e verificação de bugs, garantindo resolução eficaz de problemas e prevenção de recorrências.

### 5. Refinamento de Ideias

Processo estruturado para transformar ideias brutas em conceitos bem definidos, incluindo exploração inicial, contextualização, desafio, aprofundamento conceitual, validação e documentação.

### 6. Descoberta de Soluções

Metodologia para identificar necessidades dos usuários, mapear oportunidades de negócio, conceber e validar soluções, com foco em resultados mensuráveis e evolução contínua.

## Estrutura do Projeto

O projeto é organizado da seguinte forma:

```
template-agent/
├── 0-docs/                                # Documentação sobre o framework
│   ├── 0-structure-agent-folder-template.md
│   ├── 1-workflow-documentation-process.md
│   ├── 2-workflow-implementation-process.md
│   ├── 3-workflow-code-review-process.md
│   ├── 4-workflow-fix-bugs-process.md
│   ├── 5-workflow-idea-refinement-process.md
│   └── 6-workflow-solution-discovery-process.md
├── 1-documentation/                       # Documentação de projeto
│   ├── 01-concepcao-planejamento/         # Fase inicial de definição de projeto
│   │   ├── 001-vision-document/           # Documento de visão do projeto
│   │   ├── 002-project-charter/           # Termo de abertura do projeto
│   │   ├── 003-estudo-viabilidade/        # Estudo de viabilidade
│   │   ├── 004-brd/                       # Business Requirements Document
│   │   └── 005-mrd/                       # Market Requirements Document
│   ├── 02-requisitos/                     # Especificação de requisitos
│   │   ├── 001-prd/                       # Product Requirements Document
│   │   ├── 002-srs/                       # Software Requirements Specification
│   │   ├── 003-ux-ui-specs/               # Especificações de UX/UI
│   │   ├── 004-fsd/                       # Functional Specification Document
│   │   └── 005-roadmap/                   # Roadmap do produto
│   ├── 03-governanca-processos/           # Estrutura de governança
│   │   ├── 001-process-guidelines/        # Diretrizes de processos
│   │   ├── 002-governance-framework/      # Framework de governança
│   │   ├── 003-raci-matrix/               # Matriz RACI
│   │   ├── 004-communication-plan/        # Plano de comunicação
│   │   ├── 005-risk-management/           # Gerenciamento de riscos
│   │   └── 006-risk-management-plan/      # Plano de gerenciamento de riscos
│   ├── 04-arquitetura-design/             # Desenho arquitetural
│   │   ├── 001-hld/                       # High-Level Design
│   │   ├── 002-adrs/                      # Architecture Decision Records
│   │   ├── 003-sad/                       # Software Architecture Document
│   │   ├── 004-lld/                       # Low-Level Design
│   │   └── 005-specific-arch-docs/        # Documentos específicos de arquitetura
│   ├── 05-guidelines-sistema/             # Diretrizes e padrões
│   │   ├── 001-ui-style-guide/            # Guia de estilo de UI
│   │   ├── 002-security-guidelines/       # Diretrizes de segurança
│   │   ├── 003-technical-standards/       # Padrões técnicos
│   │   ├── 004-accessibility-guidelines/  # Diretrizes de acessibilidade
│   │   └── 005-compliance-framework/      # Framework de conformidade
│   ├── 06-codificacao-apis/               # Codificação e APIs
│   │   ├── 001-code-style-guide/          # Guia de estilo de código
│   │   ├── 002-development-standards/     # Padrões de desenvolvimento
│   │   ├── 003-api-documentation/         # Documentação de APIs
│   │   ├── 004-data-dictionary/           # Dicionário de dados
│   │   └── 005-interface-control-doc/     # Documento de controle de interfaces
│   ├── 07-testes-qualidade/               # Testes e garantia de qualidade
│   │   ├── 001-test-strategy/             # Estratégia de testes
│   │   ├── 002-test-plan/                 # Plano de testes
│   │   ├── 003-test-case-document/        # Documentos de casos de teste
│   │   ├── 004-qa-guidelines/             # Diretrizes de garantia de qualidade
│   │   └── 005-uat-doc/                   # Documentação de testes de aceitação
│   ├── 08-documentacao-usuario/           # Manuais e guias
│   │   ├── 001-user-manual/               # Manual do usuário
│   │   ├── 002-quick-start-guide/         # Guia de início rápido
│   │   ├── 003-installation-guide/        # Guia de instalação
│   │   ├── 004-training-materials/        # Materiais de treinamento
│   │   └── 005-configuration-guide/       # Guia de configuração
│   └── 09-operacao-suporte/               # Operação e manutenção
│       ├── 001-sops/                      # Standard Operating Procedures
│       ├── 002-runbooks/                  # Runbooks operacionais
│       ├── 003-drp/                       # Disaster Recovery Plan
│       ├── 004-deployment-guide/          # Guia de implantação
│       └── 005-knowledge-base/            # Base de conhecimento
├── 2-implementation/                      # Processo de implementação
│   ├── 01-exploracao/                     # Exploração inicial
│   │   ├── 001-revisao-documentacao-tecnica/  # Revisão de documentação técnica
│   │   ├── 002-analise-codigo-existente/      # Análise de código existente
│   │   ├── 003-pesquisa-solucoes/            # Pesquisa de soluções
│   │   └── 004-prototipagem-conceitos/       # Prototipagem de conceitos
│   ├── 02-contextualizacao/                # Entendimento de contexto
│   │   ├── 001-definicao-escopo/           # Definição de escopo
│   │   ├── 002-contexto-negocio/           # Contexto de negócio
│   │   ├── 003-analise-impacto/            # Análise de impacto
│   │   └── 004-alinhamento-stakeholders/   # Alinhamento com stakeholders
│   ├── 03-tarefas-plano-acao/             # Planejamento de tarefas
│   │   ├── 001-decomposicao-problema/      # Decomposição do problema
│   │   ├── 002-priorizacao-tarefas/        # Priorização de tarefas
│   │   ├── 003-estimativa-esforco/         # Estimativa de esforço
│   │   └── 004-plano-execucao/             # Plano de execução
│   ├── 04-workflow-rules/                 # Regras de desenvolvimento
│   │   ├── 001-padroes-codificacao/        # Padrões de codificação
│   │   ├── 002-controle-versao/            # Controle de versão
│   │   ├── 003-integracao-continua/        # Integração contínua
│   │   └── 004-code-review-guidelines/     # Diretrizes de revisão de código
│   ├── 05-testing/                        # Estratégias de teste
│   │   ├── 001-unit-testing/               # Testes unitários
│   │   ├── 002-integration-testing/        # Testes de integração
│   │   ├── 003-end-to-end-testing/         # Testes de ponta a ponta
│   │   └── 004-test-automation/            # Automação de testes
│   ├── 06-debugging/                      # Depuração
│   │   ├── 001-estrategias-debug/          # Estratégias de depuração
│   │   ├── 002-ferramentas-debug/          # Ferramentas de depuração
│   │   ├── 003-logging-monitoring/         # Logging e monitoramento
│   │   └── 004-resolucao-problemas/        # Resolução de problemas comuns
│   ├── 07-refactoring/                    # Refatoração
│   │   ├── 001-identificacao-code-smells/  # Identificação de code smells
│   │   ├── 002-tecnicas-refactoring/       # Técnicas de refatoração
│   │   ├── 003-melhoria-performance/       # Melhoria de performance
│   │   └── 004-otimizacao-codigo/          # Otimização de código
│   └── 08-commit-pr/                      # Preparação de commits e PRs
│       ├── 001-mensagens-commit/           # Mensagens de commit
│       ├── 002-criacao-pull-requests/      # Criação de pull requests
│       ├── 003-code-review-process/        # Processo de revisão de código
│       └── 004-integracao-pipeline/        # Integração com pipeline CI/CD
├── 3-code-review/                         # Workflow de revisão de código
│   ├── 01-preparacao-revisao/             # Preparação para review
│   │   ├── 001-auto-revisao/               # Auto-revisão do código
│   │   ├── 002-checklist-pre-revisao/      # Checklist de pré-revisão
│   │   ├── 003-documentacao-contexto/      # Documentação de contexto
│   │   └── 004-testes-necessarios/         # Testes necessários
│   ├── 02-submissao-revisao/              # Submissão do código
│   │   ├── 001-criacao-pull-request/       # Criação do pull request
│   │   ├── 002-descricao-detalhada/        # Descrição detalhada
│   │   ├── 003-escolha-revisores/          # Escolha de revisores
│   │   └── 004-identificacao-impactos/     # Identificação de impactos
│   ├── 03-revisao-tecnica/                # Análise técnica
│   │   ├── 001-analise-codigo/             # Análise do código
│   │   ├── 002-verificacao-padronizacao/   # Verificação de padronização
│   │   ├── 003-identificacao-problemas/    # Identificação de problemas
│   │   └── 004-sugestoes-melhorias/        # Sugestões de melhorias
│   ├── 04-verificacao-qualidade/          # Verificação da qualidade
│   │   ├── 001-revisao-testes/             # Revisão de testes
│   │   ├── 002-cobertura-codigo/           # Cobertura de código
│   │   ├── 003-analise-estatica/           # Análise estática
│   │   └── 004-verificacao-performance/    # Verificação de performance
│   ├── 05-feedback-discussao/             # Discussão e feedback
│   │   ├── 001-comunicacao-problemas/      # Comunicação de problemas
│   │   ├── 002-explicacao-tecnica/         # Explicação técnica
│   │   ├── 003-discussao-alternativas/     # Discussão de alternativas
│   │   └── 004-resolucao-conflitos/        # Resolução de conflitos
│   ├── 06-atualizacoes-iteracoes/         # Iterações de melhoria
│   │   ├── 001-implementacao-feedback/     # Implementação de feedback
│   │   ├── 002-atualizacao-pr/             # Atualização do PR
│   │   ├── 003-notificacao-revisores/      # Notificação de revisores
│   │   └── 004-revisao-iterativa/          # Revisão iterativa
│   ├── 07-aprovacao-finalizacao/          # Aprovação final
│   │   ├── 001-verificacao-final/          # Verificação final
│   │   ├── 002-aprovacao-formal/           # Aprovação formal
│   │   ├── 003-merge-codigo/               # Merge do código
│   │   └── 004-fechamento-tarefas/         # Fechamento de tarefas
│   └── 08-aprendizado-melhoria/           # Lições aprendidas
│       ├── 001-retrospectiva-processo/     # Retrospectiva do processo
│       ├── 002-documentacao-aprendizado/   # Documentação do aprendizado
│       ├── 003-melhorias-futuras/          # Melhorias futuras
│       └── 004-compartilhamento-conhecimento/ # Compartilhamento de conhecimento
├── 4-fix-bugs/                            # Processo de correção de bugs
│   ├── 01-identificacao-triagem/          # Identificação do problema
│   │   ├── 001-relato-bug/                 # Relato do bug
│   │   ├── 002-classificacao-severidade/   # Classificação de severidade
│   │   ├── 003-priorizacao-bugs/           # Priorização de bugs
│   │   └── 004-atribuicao-responsavel/     # Atribuição de responsável
│   ├── 02-reproducao-analise/             # Reprodução do bug
│   │   ├── 001-ambiente-reproducao/        # Ambiente de reprodução
│   │   ├── 002-passos-reproducao/          # Passos para reprodução
│   │   ├── 003-analise-contexto/           # Análise de contexto
│   │   └── 004-coleta-informacoes/         # Coleta de informações
│   ├── 03-diagnostico-causa-raiz/         # Análise de causa raiz
│   │   ├── 001-identificacao-causa/        # Identificação da causa
│   │   ├── 002-analise-codigo-problema/    # Análise do código problemático
│   │   ├── 003-investigacao-logs-dados/    # Investigação de logs e dados
│   │   └── 004-documentacao-causa-raiz/    # Documentação da causa raiz
│   ├── 04-planejamento-correcao/          # Planejamento da correção
│   │   ├── 001-estrategia-correcao/        # Estratégia de correção
│   │   ├── 002-avaliacao-impacto/          # Avaliação de impacto
│   │   ├── 003-plano-testes/               # Plano de testes
│   │   └── 004-estimativa-tempo/           # Estimativa de tempo
│   ├── 05-implementacao-correcao/         # Implementação da solução
│   │   ├── 001-implementacao-solucao/      # Implementação da solução
│   │   ├── 002-refatoracao-necessaria/     # Refatoração necessária
│   │   ├── 003-atualizacao-documentacao/   # Atualização de documentação
│   │   └── 004-melhoria-preventiva/        # Melhoria preventiva
│   ├── 06-verificacao-validacao/          # Testes da correção
│   │   ├── 001-testes-regressao/           # Testes de regressão
│   │   ├── 002-verificacao-requisitos/     # Verificação de requisitos
│   │   ├── 003-validacao-correcao/         # Validação da correção
│   │   └── 004-testes-reproducao/          # Testes de reprodução
│   ├── 07-code-review-aprovacao/          # Revisão da solução
│   │   ├── 001-submissao-revisao/          # Submissão para revisão
│   │   ├── 002-analise-solucao/            # Análise da solução
│   │   ├── 003-aprovacao-mudancas/         # Aprovação das mudanças
│   │   └── 004-preparacao-deploy/          # Preparação para deploy
│   ├── 08-implantacao-verificacao/        # Implantação e verificação
│   │   ├── 001-plano-implantacao/          # Plano de implantação
│   │   ├── 002-procedimento-deploy/        # Procedimento de deploy
│   │   ├── 003-verificacao-producao/       # Verificação em produção
│   │   └── 004-monitoramento-pos-deploy/   # Monitoramento pós-deploy
│   └── 09-fechamento-documentacao/        # Documentação da correção
│       ├── 001-atualizacao-ticket/         # Atualização do ticket
│       ├── 002-documentacao-solucao/       # Documentação da solução
│       ├── 003-registro-conhecimento/      # Registro de conhecimento
│       └── 004-avaliacao-processo/         # Avaliação do processo
├── 5-idea-refinement/                     # Refinamento de ideias
│   ├── 01-exploracao-inicial/             # Exploração de conceitos
│   │   ├── 001-captura-ideia/              # Captura da ideia
│   │   ├── 002-pesquisa-preliminar/        # Pesquisa preliminar
│   │   ├── 003-mapeamento-conceitos/       # Mapeamento de conceitos
│   │   └── 004-analogias-referencias/      # Analogias e referências
│   ├── 02-estruturacao-contextualizacao/  # Contextualização
│   │   ├── 001-definicao-problema/         # Definição do problema
│   │   ├── 002-analise-stakeholders/       # Análise de stakeholders
│   │   ├── 003-avaliacao-mercado/          # Avaliação de mercado
│   │   └── 004-restricoes-limitacoes/      # Restrições e limitações
│   ├── 03-desafio-refinamento/            # Desafio da ideia
│   │   ├── 001-questionamento-suposicoes/  # Questionamento de suposições
│   │   ├── 002-identificacao-riscos/       # Identificação de riscos
│   │   ├── 003-perspectivas-alternativas/  # Perspectivas alternativas
│   │   └── 004-contraponto-ideia/          # Contraponto à ideia
│   ├── 04-aprofundamento-conceitual/      # Aprofundamento
│   │   ├── 001-detalhamento-funcional/     # Detalhamento funcional
│   │   ├── 002-viabilidade-tecnica/        # Viabilidade técnica
│   │   ├── 003-modelagem-solucao/          # Modelagem da solução
│   │   └── 004-identificacao-componentes/  # Identificação de componentes
│   ├── 05-validacao-simulacao/            # Validação inicial
│   │   ├── 001-prototipagem-rapida/        # Prototipagem rápida
│   │   ├── 002-teste-conceito/             # Teste de conceito
│   │   ├── 003-feedback-preliminar/        # Feedback preliminar
│   │   └── 004-ajustes-validacao/          # Ajustes pós-validação
│   ├── 06-detalhamento-especificacao/     # Detalhamento
│   │   ├── 001-requisitos-detalhados/      # Requisitos detalhados
│   │   ├── 002-especificacoes-tecnicas/    # Especificações técnicas
│   │   ├── 003-criterios-aceitacao/        # Critérios de aceitação
│   │   └── 004-dependencias-interfaces/    # Dependências e interfaces
│   ├── 07-sintese-documentacao/           # Documentação da ideia
│   │   ├── 001-documentacao-completa/      # Documentação completa
│   │   ├── 002-argumentacao-valor/         # Argumentação de valor
│   │   ├── 003-design-solution/            # Design da solução
│   │   └── 004-material-apresentacao/      # Material de apresentação
│   └── 08-planejamento-evolucao/          # Planejamento de evolução
│       ├── 001-roadmap-evolucao/           # Roadmap de evolução
│       ├── 002-fases-implementacao/        # Fases de implementação
│       ├── 003-metricas-sucesso/           # Métricas de sucesso
│       └── 004-plano-iteracao/             # Plano de iteração
└── 6-solution-discovery/                  # Descoberta de soluções
    ├── 01-imersao-contextualizacao/       # Imersão no contexto
    │   ├── 001-analise-documentacao/       # Análise de documentação
    │   ├── 002-contextualizacao-mercado/   # Contextualização de mercado
    │   └── 003-mapeamento-stakeholders/    # Mapeamento de stakeholders
    ├── 02-descoberta-dores-necessidades/  # Levantamento de necessidades
    │   ├── 001-planejamento-pesquisa/      # Planejamento de pesquisa
    │   ├── 002-pesquisa-qualitativa/       # Pesquisa qualitativa
    │   ├── 003-pesquisa-quantitativa/      # Pesquisa quantitativa
    │   └── 004-mapeamento-experiencia/     # Mapeamento de experiência
    ├── 03-diagnostico-priorizacao/        # Priorização
    │   ├── 001-sintese-insights/           # Síntese de insights
    │   ├── 002-identificacao-padroes/      # Identificação de padrões
    │   ├── 003-priorizacao-problemas/      # Priorização de problemas
    │   └── 004-definicao-criterios/        # Definição de critérios
    ├── 04-mapeamento-oportunidades/       # Mapeamento de oportunidades
    │   ├── 001-ideacao-inicial/            # Ideação inicial
    │   ├── 002-workshop-cocriacao/         # Workshop de cocriação
    │   ├── 003-mapeamento-solucoes/        # Mapeamento de soluções
    │   └── 004-avaliacao-preliminar/       # Avaliação preliminar
    ├── 05-concepcao-solucoes/             # Concepção de soluções
    │   ├── 001-detalhamento-solucoes/      # Detalhamento de soluções
    │   ├── 002-prototipagem-solucoes/      # Prototipagem de soluções
    │   ├── 003-analise-viabilidade/        # Análise de viabilidade
    │   └── 004-plano-validacao/            # Plano de validação
    ├── 06-validacao-conceito-metricas/    # Validação do conceito
    │   ├── 001-testes-usuarios/            # Testes com usuários
    │   ├── 002-feedback-estruturado/       # Feedback estruturado
    │   ├── 003-ajustes-solucao/            # Ajustes na solução
    │   └── 004-definicao-metricas/         # Definição de métricas
    ├── 07-planejamento-go-to-market/      # Estratégia de lançamento
    │   ├── 001-estrategia-lancamento/      # Estratégia de lançamento
    │   ├── 002-posicionamento-mercado/     # Posicionamento de mercado
    │   ├── 003-plano-comunicacao/          # Plano de comunicação
    │   └── 004-kpis-acompanhamento/        # KPIs de acompanhamento
    └── 08-evolucao-escalonamento/         # Evolução e escalonamento
        ├── 001-analise-resultados/         # Análise de resultados
        ├── 002-feedbacks-mercado/          # Feedbacks do mercado
        ├── 003-iteracoes-produto/          # Iterações do produto
        └── 004-estrategia-escala/          # Estratégia de escala
```

Cada diretório principal contém subdiretórios numerados que representam as etapas do workflow correspondente, com arquivos `prompt.md` para prompts específicos e `sobre.md` para explicações detalhadas.

## Como Utilizar

### 1. Escolha o Workflow Adequado

Identifique qual workflow se aplica à sua necessidade atual:

- Para criar documentação de projeto: `1-documentation`
- Para implementar código: `2-implementation`
- Para revisar código: `3-code-review`
- Para corrigir bugs: `4-fix-bugs`
- Para refinar ideias: `5-idea-refinement`
- Para descobrir e validar soluções: `6-solution-discovery`

### 2. Siga as Etapas do Workflow

Cada workflow é divido em etapas sequenciais numeradas. Navegue pelas pastas correspondentes e siga o processo passo a passo.

### 3. Utilize os Prompts

Em cada etapa, você encontrará arquivos `prompt.md` contendo prompts específicos para usar com GitHub Copilot ou outras ferramentas de IA. Estes prompts foram cuidadosamente elaborados para obter os melhores resultados.

### 4. Personalize para seu Contexto

Adapte os prompts e as orientações para o contexto específico do seu projeto, equipe e tecnologias.

## Melhores Práticas

1. **Consistência**: Siga os workflows de forma consistente para criar um ritmo de trabalho previsível.

2. **Adaptação Contextual**: Personalize os prompts para incluir detalhes específicos do seu projeto.

3. **Revisão Humana**: Sempre revise criticamente as sugestões geradas pela IA.

4. **Melhoria Contínua**: Refine os prompts com base na experiência e nos resultados obtidos.

5. **Compartilhamento de Conhecimento**: Compartilhe prompts eficazes e lições aprendidas com a equipe.

## Contribuições

Este framework é um projeto vivo que se beneficia de contribuições coletivas. Para contribuir:

1. Adicione novos prompts eficazes aos workflows existentes
2. Sugira melhorias para os workflows atuais
3. Proponha novos workflows para cenários específicos
4. Compartilhe casos de uso bem-sucedidos

## Licença

Este projeto é licenciado sob MIT - veja o arquivo LICENSE para detalhes.
