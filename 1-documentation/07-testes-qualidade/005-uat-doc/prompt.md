# Prompts para Documentação de Testes de Aceitação de Usuário (UAT)

Este documento contém prompts específicos para gerar a Documentação de Testes de Aceitação de Usuário (UAT), que define como validar que o sistema atende às necessidades dos usuários finais.

## Prompt para Documento Completo de UAT

```prompt
Atue como um especialista em testes de aceitação de usuário. Preciso desenvolver documentação abrangente para UAT do projeto [nome do projeto]. Este sistema [descreva brevemente o sistema, funcionalidades principais e público-alvo].

Por favor, elabore um documento completo de UAT que inclua:

1. Introdução ao processo de UAT:
   - Objetivos e escopo dos testes de aceitação
   - Diferenciação entre UAT e outros tipos de teste
   - Critérios de entrada para a fase de UAT
   - Relação com o processo de aceitação formal

2. Papéis e responsabilidades:
   - Perfil dos participantes de UAT (stakeholders, usuários finais)
   - Papel da equipe de projeto durante UAT
   - Papel dos gerentes/líderes de negócio
   - Responsabilidades de facilitação e suporte
   - Processo decisório e governança

3. Planejamento detalhado:
   - Cronograma e duração da fase de UAT
   - Recursos necessários (ambientes, dados, ferramentas)
   - Treinamento e preparação dos participantes
   - Gestão de riscos específicos de UAT
   - Planos de contingência

4. Cenários de teste de aceitação:
   - Mapeamento para requisitos de negócio
   - Categorização por área funcional/fluxo de negócio
   - Priorização baseada em criticidade para o negócio
   - Cobertura de processos end-to-end
   - Validação de regras de negócio

5. Casos de teste detalhados, incluindo:
   - Objetivos específicos de cada teste
   - Pré-condições e configuração inicial
   - Dados de teste representativos do mundo real
   - Passos detalhados para execução
   - Resultados esperados em termos de negócio
   - Critérios de aprovação/rejeição

6. Processo de execução:
   - Fluxo de trabalho durante sessões de teste
   - Procedimentos para documentação de resultados
   - Rastreamento de progresso
   - Gestão de feedback e comunicação
   - Suporte durante a execução

7. Gerenciamento de issues:
   - Classificação de problemas encontrados
   - Processo para documentação de defeitos
   - Critérios para priorização
   - Fluxo de trabalho para resolução e reteste
   - Procedimentos de escalonamento

8. Critérios de aceitação:
   - Métricas para determinar sucesso do UAT
   - Critérios de saída para a fase de UAT
   - Processo formal de sign-off
   - Tratamento de funcionalidades não aprovadas
   - Condições para aceitação condicional

9. Relatórios e documentação:
   - Estrutura dos relatórios de progresso
   - Formato do relatório final de UAT
   - Documentação de lições aprendidas
   - Evidências a serem coletadas e preservadas
   - Recomendações para melhoria contínua

10. Anexos e templates:
    - Template para casos de teste de UAT
    - Checklist de prontidão para UAT
    - Formulário de feedback dos usuários
    - Template para relatório de defeito
    - Formulário de aceitação formal

O documento deve ser claro, abrangente e focado em validar que o sistema atende às necessidades reais do negócio e dos usuários. Inclua exemplos específicos relevantes para o contexto do projeto, mantendo o foco na perspectiva do usuário e nos objetivos de negócio.
```

## Prompt para Critérios de Aceitação de Usuário

```prompt
Como analista de requisitos e qualidade, preciso definir critérios de aceitação claros e verificáveis para o projeto [nome do projeto]. Estes critérios servirão como base para os testes de aceitação de usuário (UAT) e para a validação formal do sistema pelos stakeholders.

Considerando o escopo do projeto que inclui [descreva brevemente as funcionalidades principais], por favor desenvolva um conjunto abrangente de critérios de aceitação que:

1. Traduza requisitos de negócio em critérios verificáveis:
   - Derivados diretamente dos objetivos de negócio
   - Expressos em linguagem de negócio (não técnica)
   - Focados em resultados e valor para o usuário
   - Mensuráveis e observáveis

2. Cubra as principais áreas funcionais:
   - Critérios para cada grupo de funcionalidades principais
   - Validação de fluxos de trabalho completos
   - Verificação de regras de negócio críticas
   - Adequação a processos organizacionais

3. Inclua critérios para aspectos não-funcionais relevantes:
   - Experiência do usuário e usabilidade
   - Performance e tempos de resposta aceitáveis
   - Confiabilidade e disponibilidade
   - Segurança e proteção de dados
   - Conformidade com regulamentações
   - Compatibilidade com ambientes de usuário

4. Defina limites claros:
   - Condições mínimas para aceitação
   - Critérios para aceitação parcial ou condicional
   - Defeitos que são considerados bloqueadores
   - Áreas onde há flexibilidade

5. Estabeleça o processo para validação:
   - Como cada critério será verificado
   - Quem deve participar da validação
   - Evidências necessárias para comprovação
   - Processo de aprovação formal

Para cada grupo de critérios, forneça:
- Descrição clara do que constitui sucesso
- Exemplos específicos de cenários de aceitação
- Referências cruzadas para requisitos
- Priorização baseada em valor de negócio
- Stakeholders responsáveis pela aprovação

Os critérios devem ser compreensíveis para usuários não técnicos, mas precisos o suficiente para guiar o desenvolvimento e testes. O objetivo é criar um entendimento comum do que significa "pronto" e "aceito" para todas as partes envolvidas.
```

## Prompt para Planejamento de Sessões de UAT

```prompt
Como gerente de testes, preciso desenvolver um plano detalhado para conduzir sessões de Teste de Aceitação de Usuário (UAT) eficazes para o projeto [nome do projeto]. Estas sessões são críticas para validar que o sistema atende às necessidades dos usuários finais antes da liberação.

Considerando que o projeto [breve descrição do projeto, escala, público-alvo] está se aproximando da fase de UAT, por favor elabore um plano abrangente que detalhe:

1. Estrutura e organização das sessões:
   - Formato recomendado (workshops, testes individuais, remotos vs. presenciais)
   - Duração e frequência ideais das sessões
   - Divisão por áreas funcionais ou perfis de usuário
   - Número ideal de participantes por sessão
   - Sequenciamento lógico das atividades

2. Preparação do ambiente e materiais:
   - Requisitos de ambiente de teste
   - Dados de teste realistas necessários
   - Documentação de suporte a ser preparada
   - Ferramentas para registro de resultados
   - Configurações específicas por tipo de teste

3. Seleção e preparação de participantes:
   - Critérios para seleção de testadores
   - Perfis de usuário necessários para cobertura adequada
   - Treinamento prévio necessário
   - Briefing e materiais de orientação
   - Definição clara de expectativas e responsabilidades

4. Facilitação das sessões:
   - Script para condução das sessões
   - Técnicas para obtenção de feedback valioso
   - Gestão do tempo e foco nas atividades
   - Abordagem para lidar com descobertas inesperadas
   - Balanceamento entre teste estruturado e exploratório

5. Coleta e processamento de feedback:
   - Métodos para documentação de observações
   - Categorização de feedback e problemas
   - Processo para priorização de issues
   - Comunicação de resultados para a equipe
   - Gestão de expectativas dos stakeholders

6. Suporte durante as sessões:
   - Estrutura de suporte técnico
   - Procedimentos para esclarecimento de dúvidas
   - Protocolo para problemas bloqueadores
   - Canais de comunicação durante os testes

7. Análise e follow-up:
   - Consolidação dos resultados
   - Processo para decisões sobre correções
   - Sessões de reteste após ajustes
   - Documentação de melhorias identificadas
   - Processo formal de aceitação

8. Logística e cronograma:
   - Timeline detalhado para preparação e execução
   - Recursos necessários (salas, equipamentos, etc.)
   - Considerações para participantes remotos
   - Plano de contingência para problemas técnicos

Forneça também templates e checklists específicos que possam ser usados para:
- Planejamento prévio de cada sessão
- Roteiro do facilitador
- Registro de feedback durante as sessões
- Resumo de resultados pós-sessão
- Acompanhamento de issues identificados

O plano deve ser prático, adaptável a diferentes perfis de usuário, e focado em maximizar o valor obtido das sessões de UAT para validação do sistema.
```

## Prompt para Relatório Final de UAT

```prompt
Como gerente de qualidade, preciso criar um modelo de Relatório Final de UAT para o projeto [nome do projeto]. Este relatório será o documento oficial que resume os resultados dos testes de aceitação de usuário e fundamenta a decisão formal de aceitação ou rejeição do sistema pelos stakeholders.

Por favor, desenvolva um template abrangente de relatório final de UAT que inclua:

1. Sumário executivo:
   - Visão geral dos resultados do UAT
   - Recomendação clara quanto à aceitação
   - Principais pontos fortes e preocupações
   - Próximos passos recomendados
   - Declaração de adequação ao propósito

2. Visão geral do processo de UAT:
   - Escopo e objetivos dos testes realizados
   - Metodologia e abordagem utilizada
   - Período de realização e participantes
   - Ambientes e configurações testados
   - Limitações e restrições do teste

3. Resultados detalhados:
   - Sumário estatístico da execução (casos executados, aprovados, falhados)
   - Cobertura dos requisitos de negócio
   - Análise por área funcional/módulo
   - Gráficos e visualizações dos resultados
   - Tendências observadas durante o período de teste

4. Defeitos e issues:
   - Sumário de defeitos por severidade e categoria
   - Status atual dos defeitos (corrigidos, pendentes, diferidos)
   - Defeitos críticos e seu impacto
   - Problemas não resolvidos e seu impacto no negócio
   - Plano para resolução de issues pendentes

5. Feedback dos usuários:
   - Percepções gerais sobre o sistema
   - Avaliação de usabilidade e experiência
   - Sugestões e melhorias propostas
   - Nível de satisfação geral
   - Citações representativas do feedback

6. Avaliação de critérios de aceitação:
   - Status detalhado de cada critério de aceitação
   - Evidências de cumprimento ou não-cumprimento
   - Análise de gaps e desvios
   - Justificativas para exceções ou waivers
   - Impacto de critérios não atendidos

7. Riscos e mitigações:
   - Riscos identificados durante o UAT
   - Impacto potencial para o negócio
   - Estratégias de mitigação propostas
   - Itens que requerem monitoramento pós-implementação
   - Dependências e fatores externos

8. Recomendações:
   - Declaração formal de aceitação/rejeição/aceitação condicional
   - Condições específicas para aceitação (se condicional)
   - Próximos passos para implementação
   - Lições aprendidas para futuros projetos
   - Melhorias para o processo de UAT

9. Aprovações e sign-off:
   - Seção para assinaturas dos stakeholders-chave
   - Declarações formais de aprovação
   - Registro de pareceres divergentes (se houver)
   - Data efetiva da decisão
   - Termos e condições da aceitação

10. Anexos:
    - Resultados detalhados de testes
    - Logs de defeitos relevantes
    - Evidências importantes (screenshots, logs)
    - Documentos de referência
    - Detalhes técnicos complementares

Forneça exemplos de texto para cada seção e orientações sobre como preencher o relatório de forma eficaz. O documento final deve ser profissional, fundamentado em evidências, e fornecer uma base sólida para a tomada de decisão sobre a aceitação do sistema.
```

## Prompt para Preparação de Dados de Teste para UAT

```prompt
Como especialista em engenharia de dados de teste, preciso desenvolver uma estratégia abrangente para preparação de dados para os Testes de Aceitação de Usuário (UAT) do projeto [nome do projeto]. Os dados de teste adequados são fundamentais para garantir que os usuários possam validar o sistema em condições realistas que reflitam o ambiente de produção.

Considerando as características do projeto [descreva brevemente o domínio, complexidade dos dados, volume], por favor elabore um plano detalhado para preparação de dados de teste que inclua:

1. Estratégia geral para dados de teste:
   - Abordagem para obtenção de dados (sintéticos vs. cópia de produção)
   - Considerações de privacidade e conformidade
   - Escopo e volume necessário para representatividade
   - Balanceamento entre realismo e facilidade de uso
   - Gestão de dependências entre conjuntos de dados

2. Requisitos de dados por área funcional:
   - Mapeamento de cenários de negócio para necessidades de dados
   - Categorização por tipo de teste (básico, extremo, negativo)
   - Dados necessários para validar regras de negócio específicas
   - Condições especiais e casos edge que precisam ser testados
   - Variações necessárias para diferentes perfis de usuário

3. Processo de criação e obtenção:
   - Métodos para geração de dados sintéticos
   - Procedimentos para extração e mascaramento de dados reais
   - Ferramentas recomendadas para geração e manipulação
   - Scripts e automação necessários
   - Procedimentos de validação dos dados criados

4. Mascaramento e anonimização:
   - Campos sensíveis que requerem tratamento especial
   - Técnicas de anonimização para diferentes tipos de dados
   - Verificação de consistência após mascaramento
   - Conformidade com regulamentações de privacidade
   - Preservação de relacionamentos e integridade referencial

5. Carga e manutenção dos dados:
   - Procedimentos para carga inicial
   - Estratégia para reset entre ciclos de teste
   - Backup e restauração do estado inicial
   - Gestão de dados voláteis durante o UAT
   - Procedimentos para atualização de dados

6. Documentação e organização:
   - Catálogo de conjuntos de dados disponíveis
   - Mapeamento para casos de teste de UAT
   - Guias para usuários sobre dados disponíveis
   - Rastreabilidade de origem e transformações
   - Controle de versão dos conjuntos de dados

7. Considerações especiais:
   - Dados para integração com sistemas externos
   - Configurações específicas por ambiente
   - Dados para testes de performance durante UAT
   - Estratégia para dados temporais (datas, períodos)
   - Tratamento de dados calculados ou derivados

8. Validação e qualidade:
   - Critérios para verificar adequação dos dados
   - Testes prévios para confirmar usabilidade
   - Procedimentos para correção e ajustes
   - Feedback dos usuários sobre realismo dos dados
   - Iteração e melhoria contínua

Forneça exemplos concretos, templates para documentação dos dados, e procedimentos step-by-step que possam ser seguidos pela equipe. O plano deve ser prático, considerar restrições de tempo e recursos, e garantir que os dados sejam um facilitador efetivo para o sucesso do UAT.
```

## Prompt para Treinamento de Participantes de UAT

```prompt
Como especialista em facilitação de UAT, preciso desenvolver um programa de treinamento para preparar adequadamente os participantes do Teste de Aceitação de Usuário para o projeto [nome do projeto]. Este treinamento é crucial para garantir que os usuários compreendam seu papel no processo de validação e possam fornecer feedback valioso e estruturado.

Considerando o perfil dos participantes [descreva brevemente o perfil dos usuários, suas funções, nível de familiaridade com testes] e as características do sistema [breve descrição do sistema], elabore um plano de treinamento abrangente que inclua:

1. Objetivos e resultados esperados:
   - Metas específicas do programa de treinamento
   - Competências a serem desenvolvidas
   - Nível de proficiência desejado
   - Métricas para avaliar a eficácia do treinamento

2. Conteúdo programático detalhado:
   - Introdução aos conceitos de UAT
   - Diferenciação entre UAT e outros tipos de teste
   - O papel específico dos participantes no processo
   - Técnicas para teste eficaz e detecção de problemas
   - Procedimentos para documentação e reporte de issues
   - Visão geral do sistema a ser testado
   - Critérios de aceitação e seu significado

3. Formato e estrutura do treinamento:
   - Duração e cronograma recomendados
   - Balanceamento entre teoria e prática
   - Modalidades de entrega (presencial, online, híbrido)
   - Atividades interativas e exercícios
   - Simulações e prática com o sistema real
   - Sequência lógica de tópicos

4. Materiais de apoio:
   - Apresentações e guias de referência
   - Tutoriais e vídeos demonstrativos
   - Checklists e templates para uso durante o UAT
   - Glossário de termos relevantes
   - FAQ e recursos de suporte
   - Documentação de acesso e uso do ambiente de teste

5. Métodos pedagógicos:
   - Técnicas para engajamento dos participantes
   - Abordagens para diferentes estilos de aprendizagem
   - Estratégias para retenção de informação
   - Feedback e avaliação durante o treinamento
   - Suporte pós-treinamento e durante o UAT

6. Cenários práticos e exercícios:
   - Exemplos realistas baseados no sistema
   - Exercícios progressivos por complexidade
   - Simulações de problemas comuns
   - Atividades em grupo vs. individuais
   - Feedback sobre o desempenho nos exercícios

7. Avaliação e prontidão:
   - Métodos para verificar a compreensão
   - Critérios para confirmar prontidão para UAT
   - Processo para identificar necessidades adicionais
   - Certificação ou confirmação de participação
   - Feedback dos participantes sobre o treinamento

8. Estratégias para diferentes perfis:
   - Adaptações para usuários técnicos vs. não-técnicos
   - Considerações para diferentes áreas de negócio
   - Abordagem para diferentes níveis hierárquicos
   - Ajustes para variados níveis de experiência com sistemas

Forneça exemplos concretos de atividades, slides-chave, e exercícios práticos que possam ser utilizados. O programa deve ser acessível, prático e focado em habilitar os participantes a contribuir efetivamente durante o UAT, maximizando o valor obtido desta fase crítica.
```
