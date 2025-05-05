# Prompts para Padrões de Desenvolvimento

Este documento contém prompts específicos para gerar documentação de Padrões de Desenvolvimento, que estabelecem práticas, processos e padrões de qualidade para o desenvolvimento de software no projeto.

## Prompt para Documento Completo de Padrões de Desenvolvimento

```prompt
Como especialista em engenharia de software, crie um documento abrangente de Padrões de Desenvolvimento para nosso projeto [nome do projeto/tecnologia]. O documento deve:

1. Estabelecer práticas de versionamento:
   - Sistema de controle de versão (Git, etc.)
   - Estratégia de branching (GitFlow, GitHub Flow, etc.)
   - Convenções para commits e mensagens
   - Política de tags e releases
   - Estratégia para lidar com conflitos

2. Definir processos de code review:
   - Critérios para submissão de código para revisão
   - Responsabilidades dos revisores
   - Checklist de verificação
   - Tempo esperado de resposta
   - Como lidar com feedback e iterações
   - Requisitos para aprovação

3. Documentar padrões de qualidade de código:
   - Métricas de qualidade (complexidade, cobertura de testes, etc.)
   - Limites aceitáveis para métricas
   - Ferramentas de análise estática
   - Política de débito técnico
   - Critérios para refatoração

4. Orientações sobre testes:
   - Tipos de testes necessários
   - Requisitos de cobertura
   - Padrões para escrita de testes
   - Mocking e isolamento de componentes
   - Automação de testes

5. Processos de integração e deploy:
   - Pipeline de CI/CD
   - Ambientes de desenvolvimento, teste e produção
   - Procedimentos de deploy
   - Política de rollback
   - Monitoramento pós-deploy

Use um tom técnico mas acessível, e inclua exemplos práticos sempre que possível. Indique claramente quais padrões são obrigatórios e quais são recomendações.
```

## Prompt para Guia de Controle de Versão

```prompt
Desenvolva um guia detalhado sobre práticas de controle de versão para nosso projeto em [tecnologia/linguagem]. Este guia deve:

1. Explicar nossa estratégia de branching, incluindo:
   - Propósito e ciclo de vida de cada tipo de branch
   - Convenções de nomenclatura
   - Fluxo de trabalho desde a criação de features até o merge em produção
   - Diagramas visuais do fluxo de trabalho

2. Definir padrões para commits:
   - Formato da mensagem de commit (prefixos, estrutura)
   - Tamanho e escopo recomendados
   - Referência a issues/tickets
   - Uso de co-autores quando aplicável

3. Estabelecer processos para pull/merge requests:
   - Template para descrição
   - Critérios para considerar o PR/MR "pronto para revisão"
   - Processo de aprovação
   - Estratégias de merge (squash, rebase, merge commit)

4. Documentar práticas para resolução de conflitos:
   - Procedimento recomendado para resolução
   - Ferramentas de apoio
   - Processo para resolver conflitos complexos ou de grande escala

5. Detalhar a estratégia de releases:
   - Versionamento semântico
   - Processo de criação de tags
   - Geração de changelogs
   - Hotfixes e patches

Inclua exemplos concretos para cada padrão e forneça explicações do raciocínio por trás de cada escolha.
```

## Prompt para Diretrizes de Revisão de Código

```prompt
Crie um conjunto abrangente de diretrizes para o processo de revisão de código em nosso projeto [tipo de projeto]. As diretrizes devem cobrir:

1. Princípios fundamentais de revisão:
   - Objetivos e benefícios das revisões de código
   - Atitude e mentalidade recomendadas
   - Como dar e receber feedback construtivo
   - Balanceamento entre rigor e pragmatismo

2. Processo detalhado:
   - Fluxo completo desde a submissão até a aprovação
   - Responsabilidades do autor do código
   - Responsabilidades dos revisores
   - Métricas e SLAs para o processo (tempo de resposta, etc.)
   - Como lidar com discordâncias técnicas

3. Checklist técnica de revisão:
   - Verificações de funcionalidade
   - Verificações de qualidade de código
   - Verificações de performance
   - Verificações de segurança
   - Verificações de testabilidade
   - Verificações de documentação

4. Ferramentas e integração:
   - Configuração da plataforma de revisão (GitHub, GitLab, etc.)
   - Integração com ferramentas de análise automática
   - Templates para comentários comuns

5. Melhoria contínua do processo:
   - Coleta de métricas sobre o processo
   - Feedback sobre a eficácia das revisões
   - Treinamento e mentoria para revisões eficientes

Use uma linguagem clara e direta, e inclua exemplos concretos de boas e más práticas de revisão.
```

## Prompt para Requisitos de Qualidade e Testes

```prompt
Desenvolva um documento que estabeleça os requisitos de qualidade e testes para nosso projeto [tipo/nome do projeto]. O documento deve incluir:

1. Estratégia de testes:
   - Pirâmide de testes (proporção entre tipos de testes)
   - Responsabilidades de teste em diferentes níveis
   - Abordagem para diferentes componentes do sistema
   - Testes automatizados vs. manuais

2. Requisitos de cobertura:
   - Métricas de cobertura por tipo de código
   - Áreas críticas com requisitos especiais
   - Exceções justificáveis
   - Ferramentas de medição e relatórios

3. Padrões para escrita de testes:
   - Nomenclatura e organização dos testes
   - Padrões para testes unitários
   - Padrões para testes de integração
   - Padrões para testes end-to-end
   - Mocking, stubs e dados de teste

4. Métricas de qualidade:
   - Limites para complexidade ciclomática
   - Limites para acoplamento e coesão
   - Limites para duplicação de código
   - Métricas específicas para a linguagem/plataforma

5. Processos de validação:
   - Gates de qualidade em diferentes estágios
   - Critérios de aceitação para merges
   - Procedimentos para exceções
   - Monitoramento contínuo da qualidade

Inclua exemplos concretos e, quando possível, justificativas para os requisitos estabelecidos.
```

## Prompt para Guia de CI/CD e Deploy

```prompt
Crie um guia técnico detalhado para nossos processos de Integração Contínua, Entrega Contínua e Deploy para o projeto [nome do projeto]. O guia deve abranger:

1. Pipeline de CI/CD:
   - Diagrama completo do pipeline
   - Detalhamento de cada estágio e suas verificações
   - Tempos esperados e limites de duração
   - Tratamento de falhas e notificações
   - Configuração e manutenção do pipeline

2. Ambientes:
   - Descrição de cada ambiente (dev, staging, prod, etc.)
   - Propósito e uso de cada ambiente
   - Configurações específicas por ambiente
   - Política de acesso e permissões
   - Gerenciamento de configurações e segredos

3. Procedimentos de deploy:
   - Pré-requisitos para iniciar um deploy
   - Passos detalhados do processo
   - Verificações pós-deploy
   - Janelas de deploy recomendadas
   - Aprovações necessárias por ambiente

4. Estratégias de rollback:
   - Critérios para acionar um rollback
   - Procedimento técnico de rollback
   - Responsabilidades e comunicação
   - Registro e análise pós-incidente

5. Monitoramento e observabilidade:
   - Métricas críticas a monitorar
   - Alertas e thresholds
   - Logs e rastreamento
   - Dashboards e relatórios

Use uma linguagem técnica precisa e inclua exemplos de comandos, configurações ou scripts quando relevante.
```
