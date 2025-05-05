# Prompts para Plano de Testes

Este documento contém prompts específicos para gerar o Plano de Testes do projeto, que detalha como a estratégia de testes será implementada em termos práticos.

## Prompt para Documento Completo de Plano de Testes

```prompt
Atue como um gerente de qualidade experiente. Preciso desenvolver um Plano de Testes detalhado para o projeto [nome do projeto]. Este é um sistema [descreva brevemente o tipo de sistema, tecnologias principais e requisitos críticos].

Com base na Estratégia de Testes já definida, que estabelece [resumir pontos-chave da estratégia], elabore um Plano de Testes abrangente que inclua:

1. Informações básicas e escopo:
   - Identificação do projeto e versão
   - Objetivos específicos deste plano
   - Escopo de teste (o que será e não será testado)
   - Referências a outros documentos relevantes

2. Itens e funcionalidades a serem testados:
   - Lista detalhada de funcionalidades a serem cobertas
   - Módulos, componentes e integrações
   - APIs e interfaces externas
   - Aspectos não-funcionais específicos
   - Priorização baseada em criticidade

3. Abordagem de testes:
   - Técnicas de teste a serem aplicadas
   - Ferramentas e frameworks específicos
   - Estratégia de dados de teste
   - Configurações de ambiente necessárias

4. Critérios de entrada e saída:
   - Pré-requisitos para iniciar os testes
   - Condições para considerar o teste concluído
   - Critérios de aceitação por funcionalidade
   - Nível de tolerância para defeitos

5. Processo de suspensão e retomada:
   - Condições para suspender as atividades de teste
   - Processo para retomar testes após suspensão
   - Ações corretivas necessárias

6. Entregáveis de teste:
   - Casos de teste e scripts
   - Dados de teste a serem preparados
   - Logs e evidências a serem coletados
   - Relatórios e dashboards a serem produzidos

7. Ambientes de teste:
   - Configurações de hardware e software
   - Ferramentas e infraestrutura necessárias
   - Responsabilidades pela configuração e manutenção
   - Estratégia de restauração entre ciclos de teste

8. Cronograma e estimativas:
   - Fases de teste e suas durações
   - Marcos e deliverables
   - Dependências com outras atividades do projeto
   - Buffer para contingências

9. Alocação de recursos:
   - Papéis e responsabilidades detalhados
   - Habilidades necessárias para cada fase
   - Estimativa de esforço por atividade
   - Necessidades de treinamento

10. Gestão de riscos:
    - Riscos específicos para as atividades de teste
    - Estratégias de mitigação
    - Planos de contingência

11. Comunicação e relatórios:
    - Mecanismos de comunicação
    - Frequência e formato de relatórios
    - Stakeholders envolvidos
    - Procedimentos para escalonamento de problemas

12. Aprovação e governança:
    - Processo para alterações no plano
    - Atores responsáveis por aprovações
    - Métricas para acompanhamento do progresso

Por favor, estruture este documento de forma clara, com seções e subseções bem definidas. Inclua templates para os documentos de suporte quando relevante. O plano deve ser suficientemente detalhado para permitir sua execução, mas também flexível para se adaptar às mudanças que possam ocorrer durante o desenvolvimento.
```

## Prompt para Definição do Escopo de Testes

```prompt
Como analista de teste, preciso definir com precisão o escopo de testes para o projeto [nome do projeto]. Baseado na estratégia de testes e nos requisitos do sistema, ajude-me a elaborar a seção "Escopo de Testes" do Plano de Testes.

Contexto do sistema:
- [Descreva brevemente o sistema, sua arquitetura e componentes principais]
- [Mencione requisitos críticos e áreas de alto risco]
- [Indique restrições de tempo, recursos ou técnicas relevantes]

Por favor, elabore um escopo de testes detalhado que inclua:

1. Delimitação clara do que será testado:
   - Funcionalidades específicas a serem cobertas
   - Interfaces e integrações no escopo
   - Requisitos não-funcionais a serem verificados
   - Versões, plataformas e configurações a serem testadas

2. Definição explícita do que não será testado:
   - Funcionalidades excluídas do escopo atual
   - Casos de uso ou cenários específicos não cobertos
   - Justificativa para cada exclusão

3. Priorização dentro do escopo:
   - Categorização das funcionalidades por criticidade
   - Identificação de áreas de alto risco que requerem maior cobertura
   - Estabelecimento de níveis mínimos de teste para diferentes componentes

4. Impacto das restrições:
   - Como limitações de tempo afetam o escopo
   - Compensações devido a restrições de recursos
   - Adaptações necessárias devido a limitações técnicas

O escopo deve ser específico, mensurável, alcançável, relevante e limitado no tempo (SMART). Inclua critérios objetivos que permitam determinar se um item está dentro ou fora do escopo, e forneça orientação sobre como lidar com itens no limite.
```

## Prompt para Cronograma e Alocação de Recursos

```prompt
Como gerente de testes para o projeto [nome do projeto], preciso criar um cronograma detalhado e um plano de alocação de recursos para nossas atividades de teste. Considerando que o desenvolvimento seguirá [metodologia de desenvolvimento] e terá duração estimada de [período], crie um planejamento abrangente que otimize nossos recursos de teste.

Por favor, desenvolva:

1. Cronograma de testes detalhado:
   - Identificação e sequenciamento de todas as atividades de teste
   - Marcos (milestones) principais e entregas
   - Duração estimada para cada atividade
   - Dependências internas e externas
   - Buffer para contingências e retrabalho
   - Alinhamento com entregas de desenvolvimento
   - Visualização em formato de linha do tempo

2. Plano de alocação de recursos:
   - Papéis e responsabilidades específicos
   - Distribuição de trabalho pela equipe
   - Carga de trabalho e capacidade por período
   - Habilidades necessárias para cada fase
   - Estratégia para picos de demanda
   - Necessidades de treinamento ou especialistas externos

3. Análise de restrições e otimização:
   - Identificação de gargalos potenciais
   - Estratégias para lidar com recursos limitados
   - Abordagem para priorização em caso de pressão de tempo
   - Opções para paralelização de atividades
   - Plano de contingência para atrasos ou indisponibilidade de recursos

4. Métricas e acompanhamento:
   - KPIs para monitorar progresso e aderência ao cronograma
   - Procedimentos para atualização e comunicação de status
   - Processo para ajustes no plano quando necessário
   - Método para tracking de esforço real vs. planejado

O planejamento deve ser realista, considerar a volatilidade inerente a projetos de software, e fornecer flexibilidade para adaptação a mudanças, mantendo o foco nos objetivos de qualidade estabelecidos.
```

## Prompt para Critérios de Entrada e Saída

```prompt
Como especialista em qualidade de software, preciso definir critérios claros de entrada e saída para as atividades de teste do projeto [nome do projeto]. Estes critérios são essenciais para estabelecer quando estamos prontos para iniciar os testes e quando podemos considerá-los concluídos com sucesso.

Considerando o contexto do projeto [adicione contexto relevante], por favor desenvolva:

1. Critérios de Entrada abrangentes:
   - Pré-requisitos para iniciar cada nível de teste (unitário, integração, sistema, aceitação)
   - Condições relacionadas à completude do desenvolvimento
   - Requisitos de ambiente e infraestrutura
   - Estado necessário de artefatos de entrada (código, documentação, etc.)
   - Disponibilidade de recursos e ferramentas
   - Dependências externas que devem estar resolvidas

2. Critérios de Saída detalhados:
   - Métricas e thresholds específicos para considerar os testes bem-sucedidos
   - Requisitos de cobertura por tipo de teste
   - Limites aceitáveis para defeitos (por severidade/prioridade)
   - Completude necessária da execução de casos de teste
   - Requisitos de documentação e evidências
   - Aprovações formais necessárias

3. Processo de validação de critérios:
   - Como verificar se os critérios foram efetivamente atendidos
   - Papéis responsáveis pela validação
   - Procedimentos para exceções e desvios
   - Documentação necessária

4. Diretrizes para decisão:
   - Framework para tomada de decisão quando critérios não são totalmente atendidos
   - Processo de avaliação de riscos para critérios parcialmente atendidos
   - Procedimento para aprovação condicional
   - Critérios para regressão e reteste

Os critérios devem ser objetivos, mensuráveis e alinhados com os objetivos de qualidade do projeto. Eles devem fornecer uma base clara para decisões de go/no-go em cada fase do processo de teste.
```

## Prompt para Gestão de Riscos de Teste

```prompt
Como consultor em gestão de riscos para testes de software, preciso desenvolver um plano abrangente de gestão de riscos para as atividades de teste do projeto [nome do projeto].

Considerando que este projeto [características relevantes do projeto], por favor elabore um plano de gestão de riscos para testes que inclua:

1. Identificação de riscos específicos para testes:
   - Riscos técnicos (ferramentas, automação, ambiente)
   - Riscos de processo (cronograma, recursos, dependências)
   - Riscos de produto (complexidade, tecnologias, integrações)
   - Riscos de dados e segurança
   - Riscos organizacionais (habilidades, comunicação)

2. Avaliação de riscos:
   - Matriz de probabilidade e impacto
   - Critérios para classificação de severidade
   - Priorização de riscos baseada em criticidade para o negócio
   - Análise de impacto em termos de tempo, custo e qualidade

3. Estratégias de mitigação:
   - Ações preventivas para cada categoria de risco
   - Responsáveis e prazos para implementação
   - Recursos necessários para mitigação
   - Métricas para avaliar eficácia das estratégias

4. Planos de contingência:
   - Respostas planejadas para riscos que se materializem
   - Procedimentos de escalonamento
   - Critérios para ativação de planos alternativos
   - Estratégias de recuperação

5. Monitoramento e controle:
   - Processo para tracking contínuo de riscos
   - Indicadores e alertas precoces
   - Frequência de revisão e reavaliação
   - Procedimentos para identificação de novos riscos
   - Feedback loop para melhoria do processo

6. Governança de riscos:
   - Papéis e responsabilidades na gestão de riscos
   - Comunicação e reporting
   - Integração com a gestão de riscos do projeto
   - Processo decisório para aceitar, transferir ou mitigar riscos

O plano deve ser prático, específico para o contexto do projeto, e focado em maximizar a eficácia das atividades de teste enquanto gerencia proativamente os riscos associados.
```

## Prompt para Entregáveis de Teste

```prompt
Como líder de qualidade, preciso definir claramente todos os entregáveis que serão produzidos durante o processo de teste para o projeto [nome do projeto]. Estes entregáveis são essenciais para documentar o trabalho realizado, fornecer evidências de qualidade, e permitir auditoria e rastreabilidade.

Considerando o ciclo de vida do projeto e a estratégia de testes estabelecida, por favor, desenvolva uma especificação detalhada dos entregáveis de teste que inclua:

1. Documentação de planejamento:
   - Templates e estrutura para planos de teste específicos (por nível, por sprint, etc.)
   - Formato e conteúdo dos calendários e cronogramas de teste
   - Checklists de preparação e critérios de entrada/saída
   - Matrizes de rastreabilidade

2. Especificações de teste:
   - Estrutura e formato dos casos de teste
   - Organização em suites e cenários
   - Templates para procedimentos de teste passo-a-passo
   - Especificação de dados de teste necessários
   - Padrões para scripts de automação

3. Registros de execução:
   - Formato dos logs de execução
   - Capturas de evidências (screenshots, logs, dumps)
   - Procedimentos para coleta de métricas durante execução
   - Documentação de issues e anomalias encontradas

4. Relatórios e dashboards:
   - Conteúdo e layout de relatórios diários/semanais
   - Estrutura de relatórios de progresso
   - Formatos para relatórios de defeitos
   - Dashboards para visibilidade executiva
   - Relatórios de cobertura e qualidade

5. Documentação de encerramento:
   - Estrutura do relatório final de testes
   - Templates para sumário de resultados
   - Formato para documentação de lições aprendidas
   - Pacotes de entrega e documentação de release

Para cada entregável, especifique:
- Propósito e audiência
- Conteúdo específico e formato
- Responsáveis pela criação e aprovação
- Timing e frequência
- Ferramentas utilizadas na produção
- Métodos de armazenamento e controle de versão

Os entregáveis devem ser padronizados, facilmente acessíveis, e fornecer valor real para o gerenciamento da qualidade do projeto.
```
