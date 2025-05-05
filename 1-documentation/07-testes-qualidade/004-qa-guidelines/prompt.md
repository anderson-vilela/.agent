# Prompts para Diretrizes de Garantia de Qualidade

Este documento contém prompts específicos para gerar Diretrizes de Garantia de Qualidade (QA Guidelines), que estabelecem padrões, processos e melhores práticas para assegurar a qualidade do software.

## Prompt para Documento Completo de Diretrizes de QA

```prompt
Atue como um especialista em garantia de qualidade de software. Preciso desenvolver um conjunto abrangente de diretrizes de QA para o projeto [nome do projeto], que utiliza [tecnologias principais] e segue metodologia [ágil/híbrida/tradicional].

Por favor, crie um documento de Diretrizes de QA completo que inclua:

1. Introdução e princípios de qualidade:
   - Definição de qualidade no contexto do projeto
   - Objetivos e metas de qualidade
   - Princípios fundamentais que guiam as práticas de QA
   - Alinhamento com objetivos de negócio

2. Estrutura e organização de QA:
   - Papéis e responsabilidades da equipe de qualidade
   - Modelo de operação (embutido, centralizado, híbrido)
   - Interfaces e colaboração com desenvolvimento, DevOps e stakeholders
   - Ferramentas e infraestrutura de qualidade

3. Processos de garantia de qualidade:
   - Fluxo de trabalho de QA integrado ao SDLC
   - Pontos de verificação e gates de qualidade
   - Procedimentos para planejamento, execução e reporting de testes
   - Integração com CI/CD
   - Processos de revisão e inspeção
   - Gestão de defeitos (ciclo de vida, classificação, priorização)

4. Padrões de qualidade e critérios de aceitação:
   - Padrões de qualidade de código
   - Requisitos de cobertura de testes
   - Requisitos de documentação
   - Critérios de entrada e saída para cada fase
   - Limiares para métricas de qualidade

5. Tipos de testes e abordagens:
   - Testes manuais vs. automatizados
   - Testes funcionais e não-funcionais
   - Testes estáticos vs. dinâmicos
   - Testes exploratórios e baseados em risco
   - Testes de acessibilidade e usabilidade

6. Métricas e medição:
   - KPIs de qualidade
   - Métricas de produto e processo
   - Métodos de coleta e análise
   - Dashboards e reporting
   - Uso de métricas para melhoria contínua

7. Boas práticas e padrões:
   - Convenções de nomenclatura para artefatos de teste
   - Padrões para escrita de casos de teste
   - Diretrizes para revisões e inspeções
   - Melhores práticas para automação de testes
   - Abordagens para testes de regressão

8. Gestão de dados de teste:
   - Estratégias para criação e manutenção de dados
   - Proteção de dados sensíveis
   - Abordagens para mascaramento e anonimização
   - Separação entre ambientes

9. Gestão de ambientes:
   - Requisitos de ambiente por fase
   - Procedimentos para configuração e manutenção
   - Gestão de configuração e controle de versão
   - Isolamento e contenção

10. Melhoria contínua e cultura de qualidade:
    - Retrospectivas e lições aprendidas
    - Compartilhamento de conhecimento
    - Treinamento e habilitação
    - Evolução das práticas de QA

O documento deve ser prático, específico para o contexto do projeto, e fornecer orientações claras que possam ser seguidas pela equipe. Use exemplos concretos e templates onde apropriado para ilustrar as práticas recomendadas.
```

## Prompt para Definição de Critérios de Qualidade

```prompt
Como especialista em qualidade de software, preciso definir critérios de qualidade claros e mensuráveis para o projeto [nome do projeto]. Estes critérios servirão como referência para avaliar se o software está pronto para ser liberado e se atende aos padrões de qualidade estabelecidos.

Considerando as características do projeto:
- [Descreva brevemente tipo de aplicação, criticidade, requisitos não-funcionais importantes]
- [Mencione restrições ou considerações especiais]
- [Informe sobre compliance ou requisitos regulatórios se aplicável]

Por favor, desenvolva um conjunto abrangente de critérios de qualidade que inclua:

1. Critérios relacionados à funcionalidade:
   - Completude funcional (definição e métricas)
   - Correção funcional (como medir a precisão)
   - Adequação funcional (alinhamento com requisitos)
   - Cobertura de casos de uso e cenários
   - Verificação de regras de negócio

2. Critérios de confiabilidade:
   - Tolerância a falhas (comportamento em condições adversas)
   - Recuperabilidade (capacidade de recuperação após falhas)
   - Disponibilidade (uptime e metas de SLA)
   - Prevenção de defeitos críticos
   - Gestão de condições excepcionais

3. Critérios de usabilidade:
   - Facilidade de aprendizado
   - Eficiência operacional
   - Satisfação do usuário
   - Acessibilidade
   - Consistência da experiência

4. Critérios de eficiência:
   - Performance e tempos de resposta
   - Utilização de recursos
   - Capacidade e escalabilidade
   - Eficiência em diferentes condições de carga

5. Critérios de manutenibilidade:
   - Qualidade do código
   - Modularidade e acoplamento
   - Testabilidade
   - Cobertura de testes automatizados
   - Documentação técnica

6. Critérios de segurança:
   - Proteção contra vulnerabilidades comuns
   - Gestão de autenticação e autorização
   - Proteção de dados sensíveis
   - Logging e auditoria
   - Conformidade com padrões de segurança

7. Critérios de compatibilidade:
   - Integração com sistemas externos
   - Compatibilidade com plataformas e browsers
   - Interoperabilidade

Para cada critério, forneça:
- Definição clara do que está sendo medido
- Método ou técnica de medição
- Ferramentas recomendadas (quando aplicável)
- Thresholds para aceitação (metas mínimas e desejáveis)
- Ações recomendadas caso os critérios não sejam atendidos

Os critérios devem ser específicos, mensuráveis, atingíveis, relevantes e temporizados (SMART). Priorize-os de acordo com a importância para o projeto e indique quais são absolutamente necessários versus desejáveis.
```

## Prompt para Processos de Revisão e Inspeção

```prompt
Como consultor de garantia de qualidade, preciso estabelecer processos robustos de revisão e inspeção para o projeto [nome do projeto], que utiliza [metodologia/stack tecnológica]. Estes processos são fundamentais para detecção precoce de defeitos, garantia de aderência a padrões e transferência de conhecimento entre a equipe.

Por favor, desenvolva um conjunto abrangente de diretrizes para revisões e inspeções que inclua:

1. Tipos de revisão e quando utilizá-los:
   - Revisões informais vs. formais
   - Peer reviews vs. revisões técnicas
   - Code reviews vs. design reviews
   - Inspeções de documentação
   - Walkthroughs e desk checks
   - Reviews baseados em checklists

2. Processo de revisão de código:
   - Preparação para submissão
   - Critérios para seleção de revisores
   - Tempo adequado e escopo de revisão
   - Checklists específicos por tecnologia
   - Padrões de comentários e feedback
   - Processo de resolução e verificação
   - Métricas para eficácia de code reviews

3. Processo para revisões de design e arquitetura:
   - Artefatos necessários para revisão
   - Composição da equipe de revisão
   - Critérios de avaliação
   - Técnicas de identificação de riscos
   - Documentação de decisões e tradeoffs

4. Revisões de requisitos e documentação:
   - Critérios para completude e clareza
   - Verificação de consistência e rastreabilidade
   - Validação de testabilidade
   - Checagem de ambiguidades e omissões

5. Inspeções formais:
   - Quando utilizar inspeções vs. revisões simples
   - Papéis e responsabilidades (moderador, autor, inspetores)
   - Preparação, condução e acompanhamento
   - Documentação de resultados
   - Métricas de qualidade da inspeção

6. Ferramentas e tecnologias de suporte:
   - Plataformas de code review
   - Ferramentas de análise estática
   - Sistemas de tracking para issues encontrados
   - Templates e checklists automatizados

7. Integração com o processo de desenvolvimento:
   - Gates de qualidade baseados em revisões
   - Incorporação em CI/CD
   - Relação com testes e outras atividades de QA
   - Balanceamento entre rigor e agilidade

8. Melhoria contínua dos processos de revisão:
   - Coleta de métricas de eficácia
   - Feedback loops
   - Evolução de checklists e critérios
   - Treinamento e calibração de revisores

Para cada componente, forneça exemplos concretos, templates reutilizáveis e checklists específicos que possam ser imediatamente aplicados. Considere aspectos culturais que promovam revisões construtivas e colaborativas em vez de confrontativas.
```

## Prompt para Gestão de Defeitos

```prompt
Como líder de qualidade, preciso estabelecer um processo abrangente de gestão de defeitos para o projeto [nome do projeto]. Este processo deve cobrir todo o ciclo de vida dos defeitos, desde sua identificação até a resolução e verificação, garantindo rastreabilidade e métricas que apoiem a melhoria contínua.

Considerando a natureza do projeto [descreva brevemente contexto, metodologia, escala], por favor desenvolva diretrizes detalhadas para gestão de defeitos que incluam:

1. Classificação e categorização de defeitos:
   - Taxonomia de tipos de defeitos
   - Níveis de severidade (definições e exemplos)
   - Níveis de prioridade (critérios e impacto)
   - Categorização por área/componente
   - Tags e atributos adicionais para análise

2. Processo de ciclo de vida de defeitos:
   - Estados (novo, atribuído, resolvido, verificado, etc.)
   - Fluxo de trabalho e transições permitidas
   - Papéis e responsabilidades em cada etapa
   - SLAs por severidade/prioridade
   - Procedimentos de escalonamento

3. Diretrizes para reporting de defeitos:
   - Informações mínimas necessárias
   - Template detalhado para descrição
   - Instruções para passos de reprodução
   - Diretrizes para evidências (logs, screenshots)
   - Exemplo de bons e maus reports

4. Triagem e priorização:
   - Processo de avaliação inicial
   - Critérios para priorização
   - Composição do comitê de triagem (se aplicável)
   - Frequência e formato de sessões de triagem
   - Tratamento de defeitos críticos e emergenciais

5. Resolução e verificação:
   - Padrões para documentação da causa raiz
   - Diretrizes para descrição da solução
   - Processo de verificação e critérios de aceitação
   - Testes de regressão necessários
   - Procedimento para rejeição/reabertura

6. Ferramentas e integração:
   - Sistema de tracking recomendado
   - Integração com ferramentas de desenvolvimento
   - Dashboards e visualizações
   - Automação de fluxos e notificações
   - Integração com CI/CD

7. Métricas e análise:
   - KPIs fundamentais (taxa de defeitos, tempo de resolução, etc.)
   - Tendências e análises periódicas
   - Relatórios para diferentes audiências
   - Processo para análise de causa raiz comum
   - Identificação de padrões e áreas problemáticas

8. Melhoria contínua:
   - Retrospectivas sobre defeitos significativos
   - Feedback loop para prevenção
   - Evolução dos processos baseada em métricas
   - Compartilhamento de lições aprendidas

Forneça templates, checklists e exemplos concretos para cada componente do processo, garantindo que as diretrizes sejam práticas e implementáveis. As recomendações devem equilibrar rigor metodológico com eficiência operacional, adaptando-se ao contexto específico do projeto.
```

## Prompt para Métricas de Qualidade e Dashboards

```prompt
Como especialista em métricas de qualidade de software, preciso definir um framework abrangente de métricas e dashboards para monitorar e melhorar a qualidade no projeto [nome do projeto]. Este framework deve fornecer visibilidade em todos os níveis e permitir decisões baseadas em dados sobre qualidade e readiness do produto.

Considerando as características do projeto [tipo de software, metodologia, escala], elabore um plano detalhado para métricas de qualidade que inclua:

1. Definição de métricas fundamentais:
   - Métricas de qualidade do produto
     - Densidade de defeitos (por severidade, componente, etc.)
     - Confiabilidade (MTBF, taxa de falhas, etc.)
     - Cobertura de testes (código, requisitos, etc.)
     - Dívida técnica e code quality
     - Performance e eficiência
     - Usabilidade e satisfação do usuário

   - Métricas de processo de qualidade
     - Eficiência de detecção de defeitos
     - Tempo de ciclo para correção
     - Eficácia de testes (defeitos encontrados/esforço)
     - Taxa de regressão
     - Aderência a processos de qualidade
     - Maturidade de testes e automação

2. Framework de coleta e análise:
   - Fontes de dados para cada métrica
   - Frequência de coleta e cálculo
   - Ferramentas e automação necessárias
   - Armazenamento e histórico de dados
   - Técnicas estatísticas para análise de tendências
   - Correlação entre métricas

3. Dashboards por audiência:
   - Dashboard executivo (KPIs de alto nível)
   - Dashboard para líderes técnicos (tendências e áreas problemáticas)
   - Dashboard operacional (métricas detalhadas para equipes)
   - Dashboard de release (readiness e gates de qualidade)
   - Visualizações específicas para diferentes stakeholders

4. Para cada dashboard, especifique:
   - Objetivo e audiência-alvo
   - Principais métricas e visualizações
   - Frequência de atualização
   - Níveis de alerta e thresholds
   - Drill-down capabilities
   - Formato e ferramentas recomendadas

5. Sistema de metas e thresholds:
   - Critérios para estabelecimento de baselines
   - Processo para definição de metas realistas
   - Thresholds de alerta e ação
   - Diferenciação por tipo de componente/módulo
   - Evolução de metas ao longo do tempo

6. Processo de revisão e ação:
   - Cadência de revisões baseadas em métricas
   - Framework para análise de causa raiz
   - Processo decisório baseado em métricas
   - Feedback loop para melhoria de processos
   - Comunicação e acompanhamento de ações

7. Implementação e adoção:
   - Roadmap para implementação incremental
   - Necessidades de infraestrutura e ferramentas
   - Treinamento e awareness
   - Gestão de mudança cultural
   - Validação e refinamento do framework

As recomendações devem ser práticas, implementáveis e fornecer valor imediato, mas também permitir evolução e maturidade ao longo do tempo. Forneça exemplos concretos de visualizações, fórmulas de cálculo para métricas complexas, e templates que possam ser adaptados ao contexto específico do projeto.
```

## Prompt para Integração de Qualidade com DevOps e CI/CD

```prompt
Como arquiteto de qualidade, preciso desenvolver uma estratégia para integrar práticas de garantia de qualidade com DevOps e pipelines de CI/CD no projeto [nome do projeto]. O objetivo é implementar quality gates automatizados que garantam um feedback rápido sobre problemas de qualidade sem comprometer a velocidade de entrega.

Considerando o ambiente tecnológico [descreva stack, infraestrutura, ferramentas atuais] e a maturidade DevOps atual [descreva estágio], por favor desenvolva diretrizes abrangentes para:

1. Estratégia de "quality as code":
   - Implementação de padrões de qualidade como código
   - Automação de políticas e checagens de qualidade
   - Versionamento de configurações de qualidade
   - Infraestrutura para testes como código

2. Quality gates integrados ao pipeline:
   - Definição de gates obrigatórios por estágio
   - Critérios claros para aprovação/falha
   - Balanceamento entre rigor e velocidade
   - Estratégia para exceções e overrides
   - Métricas e thresholds automatizados

3. Automação de testes no pipeline:
   - Estratificação de testes por estágio (pirâmide de testes)
   - Otimização para execução rápida e confiável
   - Abordagem para testes paralelos
   - Gestão de dados de teste em ambientes efêmeros
   - Estratégias para testes de longa duração

4. Feedback contínuo de qualidade:
   - Visualização em tempo real de status de qualidade
   - Alertas e notificações
   - Integração com ferramentas de desenvolvimento
   - Dashboard de qualidade de build/deploy
   - Rastreabilidade de issues de qualidade

5. Monitoramento e testes em produção:
   - Implementação de testes pós-deploy
   - Smoke tests e health checks automatizados
   - Feature toggles e lançamentos controlados
   - Monitoramento de qualidade em produção
   - Estratégias de rollback automatizado

6. Gestão de ambientes de teste:
   - Provisão automatizada de ambientes
   - Estratégias para ambiente-como-código
   - Consistência entre ambientes
   - Gestão de configuração e secrets
   - Isolamento e contenção

7. Métricas de qualidade DevOps:
   - Indicadores chave para qualidade no pipeline
   - Métricas de eficiência e confiabilidade
   - Lead time para correção de issues
   - Métricas de cobertura de qualidade
   - Dashboards integrados

8. Cultura e colaboração:
   - Práticas para responsabilidade compartilhada
   - Shift-left para qualidade
   - Inner-loop vs. outer-loop testing
   - Colaboração entre QA, Dev, e Ops
   - Treinamento e habilitação

Para cada componente, forneça:
- Recomendações específicas de ferramentas
- Exemplos de código/configuração (snippets)
- Padrões de implementação
- Práticas para evitar problemas comuns
- Considerações de escalabilidade

As diretrizes devem ser acionáveis, considerando diferentes níveis de maturidade e permitindo implementação incremental. O foco deve ser em automação, repetibilidade e integração profunda entre qualidade e entrega contínua.
```
