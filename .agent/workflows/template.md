# Workflow Estruturado para Desenvolvimento com GitHub Copilot: Potencializando a Engenharia de Software com IA

Este workflow apresenta uma metodologia abrangente e estruturada para o desenvolvimento de software que incorpora o GitHub Copilot como um colaborador integral em cada etapa do ciclo de vida do desenvolvimento. Projetado para maximizar a produtividade, garantir a qualidade e acelerar a entrega, este framework transforma a maneira como equipes técnicas abordam projetos complexos, aproveitando o poder da inteligência artificial para amplificar capacidades humanas.

## Índice

- [Fundamentos do Workflow](#fundamentos-do-workflow)
  - [Colaboração Homem-Máquina Otimizada](#colaboração-homem-máquina-otimizada)
  - [Sistema de Personas Especializadas](#sistema-de-personas-especializadas)
  - [Processos Estruturados e Reproduzíveis](#processos-estruturados-e-reproduzíveis)

### [Arquitetura do Workflow](#arquitetura-do-workflow)

1. [Compreensão e Definição de Requisitos](#1-compreensão-e-definição-de-requisitos)

   - [Documentos de Contexto do Usuário](#11-documentos-de-contexto-do-usuário)
   - [Documentação Técnica de Base](#12-documentação-técnica-de-base)
   - [Documentos de Design e Experiência](#13-documentos-de-design-e-experiência)
   - [Documentos Estratégicos](#14-documentos-estratégicos)
   - [Planos de Comunicação](#15-planos-de-comunicação)
   - [Documentos de Requisitos Funcionais](#16-documentos-de-requisitos-funcionais)

2. [Análise de Impacto e Alinhamento Estratégico](#2-análise-de-impacto-e-alinhamento-estratégico)

   - [Prompt para Documentos de Análise Técnica](#21-prompt-para-documentos-de-análise-técnica)
   - [Prompt para Documentos de Risco e Mitigação](#22-prompt-para-documentos-de-risco-e-mitigação)
   - [Prompt para Documentos de Alinhamento Estratégico](#23-prompt-para-documentos-de-alinhamento-estratégico)
   - [Prompt para Documentos de Planejamento de Recursos](#24-prompt-para-documentos-de-planejamento-de-recursos)
   - [Prompt para Documentos de Gerenciamento de Stakeholders](#25-prompt-para-documentos-de-gerenciamento-de-stakeholders)
   - [Prompt para Documentos de Análise de Impacto em Negócios](#26-prompt-para-documentos-de-análise-de-impacto-em-negócios)
   - [Prompt para Documentos de Impacto em Segurança e Compliance](#27-prompt-para-documentos-de-impacto-em-segurança-e-compliance)

3. [Design Arquitetural e Registros de Decisão (ADRs)](#3-design-arquitetural-e-registros-de-decisão-adrs)

   - [Documentos de Visão Arquitetural](#31-documentos-de-visão-arquitetural)
   - [Architecture Decision Records (ADRs)](#32-architecture-decision-records-adrs)
   - [Documentos de Design Técnico](#33-documentos-de-design-técnico)
   - [Documentos de Segurança e Privacidade](#34-documentos-de-segurança-e-privacidade)
   - [Documentos de Performance e Escalabilidade](#35-documentos-de-performance-e-escalabilidade)
   - [Documentos de Evolução Arquitetural](#36-documentos-de-evolução-arquitetural)
   - [Prompts para Geração de Documentação Arquitetural](#37-prompts-para-geração-de-documentação-arquitetural)

4. [Planejamento e Criação de Tarefas](#4-planejamento-e-criação-de-tarefas)

   - [Elementos Expandidos do Template de Tarefa](#41-elementos-expandidos-do-template-de-tarefa)
   - [Prompts Otimizados para Planejamento e Criação de Tarefas](#42-prompts-otimizados-para-planejamento-e-criação-de-tarefas)

5. [Estratégia de Testes e Padrões de Código](#5-estratégia-de-testes-e-padrões-de-código)

   - [Documentos de Padrões de Código](#51-documentos-de-padrões-de-código)
   - [Documentos de Estratégia de Teste](#52-documentos-de-estratégia-de-teste)
   - [Artefatos de Automação e Qualidade](#53-artefatos-de-automação-e-qualidade)
   - [Documentos de Governança de Qualidade](#54-documentos-de-governança-de-qualidade)
   - [Documentos de Especialização de Qualidade](#55-documentos-de-especialização-de-qualidade)
   - [Prompts Otimizados para Geração de Padrões de Código](#56-prompts-otimizados-para-geração-de-padrões-de-código)

6. [Implementação e Codificação](#6-implementação-e-codificação)

   - [Preparação do Ambiente de Desenvolvimento](#61-preparação-do-ambiente-de-desenvolvimento)
   - [Ciclo de Desenvolvimento Assistido](#62-ciclo-de-desenvolvimento-assistido)
   - [Evolução Guiada por Feedback](#63-evolução-guiada-por-feedback)
   - [Prompts Otimizados para Implementação e Codificação](#64-prompts-otimizados-para-implementação-e-codificação)

7. [Revisão e Refinamento de Código](#7-revisão-e-refinamento-de-código)

   - [Revisão Automatizada Inicial](#71-revisão-automatizada-inicial)
   - [Revisão Humano-IA Colaborativa](#72-revisão-humano-ia-colaborativa)
   - [Documentação e Aprendizado](#73-documentação-e-aprendizado)
   - [Prompts Otimizados para Revisão e Refinamento de Código](#74-prompts-otimizados-para-revisão-e-refinamento-de-código)

8. [Teste Automatizado Abrangente](#8-teste-automatizado-abrangente)

   - [Testes Unitários](#81-testes-unitários)
   - [Testes de Integração](#82-testes-de-integração)
   - [Testes End-to-End](#83-testes-end-to-end)
   - [Integração Contínua](#84-integração-contínua)
   - [Prompts Otimizados para Testes Automatizados](#85-prompts-otimizados-para-testes-automatizados)

9. [Documentação Técnica](#9-documentação-técnica)

   - [Documentação Arquitetural](#91-documentação-arquitetural)
   - [Documentação de API](#92-documentação-de-api)
   - [Documentação para Desenvolvedores](#93-documentação-para-desenvolvedores)
   - [Documentação Operacional](#94-documentação-operacional)
   - [Documentação para Onboarding](#95-documentação-para-onboarding)
   - [Prompts Otimizados para Documentação Técnica](#96-prompts-otimizados-para-documentação-técnica)

10. [Estratégia de Implantação](#10-estratégia-de-implantação)

    - [Documentos de Estratégia de Implantação](#101-documentos-de-estratégia-de-implantação)
    - [Artefatos de Implantação Gradual](#102-artefatos-de-implantação-gradual)
    - [Documentos de Monitoramento e Validação](#103-documentos-de-monitoramento-e-validação)
    - [Planos de Contingência](#104-planos-de-contingência)
    - [Automação de Implantação](#105-automação-de-implantação)
    - [Prompts Otimizados para Estratégia de Implantação](#106-prompts-otimizados-para-estratégia-de-implantação)

11. [Monitoramento e Manutenção](#11-monitoramento-e-manutenção)

    - [Documentos de Estratégia de Monitoramento](#111-documentos-de-estratégia-de-monitoramento)
    - [Artefatos de Detecção e Alertas](#112-artefatos-de-detecção-e-alertas)
    - [Documentos de Manutenção Preventiva](#113-documentos-de-manutenção-preventiva)
    - [Artefatos de Solução de Problemas](#114-artefatos-de-solução-de-problemas)
    - [Documentos de Evolução Contínua](#115-documentos-de-evolução-contínua)
    - [Prompts Otimizados para Monitoramento e Manutenção](#116-prompts-otimizados-para-monitoramento-e-manutenção)

12. [Retrospectiva e Aprendizado](#12-retrospectiva-e-aprendizado)
    - [Documentos de Análise de Processo](#121-documentos-de-análise-de-processo)
    - [Artefatos de Captura de Conhecimento](#122-artefatos-de-captura-de-conhecimento)
    - [Documentos de Evolução de Processo](#123-documentos-de-evolução-de-processo)
    - [Artefatos de Capacitação](#124-artefatos-de-capacitação)
    - [Documentos de Direcionamento Estratégico](#125-documentos-de-direcionamento-estratégico)
    - [Prompts Otimizados para Retrospectiva e Aprendizado](#126-prompts-otimizados-para-retrospectiva-e-aprendizado)

## Fundamentos do Workflow

O framework baseia-se em três pilares fundamentais que o diferenciam de abordagens convencionais:

### Colaboração Homem-Máquina Otimizada

Ao contrário de fluxos tradicionais que tratam ferramentas de IA como meros geradores de código, este workflow posiciona o GitHub Copilot como um parceiro de desenvolvimento multifacetado. O sistema utiliza prompts estrategicamente elaborados para extrair insights, recomendações e soluções contextualizadas em cada fase do projeto, desde a concepção inicial até a manutenção contínua.

### Sistema de Personas Especializadas

O workflow implementa um sistema inovador de "personas técnicas" - perfis especializados que podem ser invocados para direcionar a expertise do Copilot para domínios específicos. Cada persona representa um conjunto distinto de conhecimentos, habilidades e perspectivas, permitindo obter orientações altamente especializadas para diferentes aspectos do desenvolvimento.

### Processos Estruturados e Reproduzíveis

Cada fase do desenvolvimento é decomposta em processos estruturados com entradas, ações e resultados claramente definidos. Esta abordagem sistemática garante consistência, facilita onboarding, e permite a adaptação do processo para diversos contextos organizacionais enquanto mantém a qualidade de resultados.

## Arquitetura do Workflow

O workflow é dividido em doze etapas interconectadas que abrangem todo o ciclo de vida do desenvolvimento de software, formando um sistema coeso onde cada fase fornece fundamentos para as subsequentes:

### 1. Compreensão e Definição de Requisitos

A abordagem sistemática para elicitação de requisitos transforma ideias abstratas em especificações implementáveis através de um processo estruturado em múltiplas camadas. Esta fase utiliza técnicas avançadas de análise e modelagem para identificar proativamente ambiguidades, casos de borda e exceções potenciais, incorporando perspectivas diversas de stakeholders técnicos e de negócio.

Com o auxílio do GitHub Copilot, requisitos são decompostos em componentes atômicos verificáveis, enriquecidos com critérios de aceitação mensuráveis, e organizados em uma hierarquia clara de prioridades. O processo estabelece rastreabilidade bidirecional entre requisitos de negócio e especificações técnicas, reduzindo significativamente o retrabalho e proporcionando base sólida para estimativas precisas.

O resultado é uma definição de escopo cristalina, com limites bem delineados entre o que está incluído e excluído, métricas de sucesso tangíveis, e uma documentação viva que serve como contrato técnico entre todas as partes envolvidas no desenvolvimento da solução.

Esta fase também incorpora a criação de documentos complementares essenciais armazenados na pasta `.agent/contexto`, facilitada através de prompts especializados para o GitHub Copilot que garantem consistência, abrangência e alinhamento estratégico:

#### 1.1. Documentos de Contexto do Usuário

O seguinte prompt gera a documentação fundamental para compreensão do usuário-alvo:

```
Atue como um UX Researcher especializado em modelagem de usuários e suas necessidades. Estou desenvolvendo [descrição do produto/sistema] voltado para [público-alvo] e preciso criar documentação abrangente de contexto do usuário para orientar decisões de produto e desenvolvimento.

Por favor, crie os seguintes 5 documentos detalhados para armazenamento em '.agent/contexto/usuario/':

1. Um "Perfil de Personas Primárias" (personas-primarias.md) que:
   - Identifique e caracterize 3-5 personas principais que utilizarão o sistema
   - Detalhe para cada persona: dados demográficos, objetivos, frustrações, motivações e nível técnico
   - Explique como cada persona interagirá com o sistema de forma distinta
   - Inclua citações representativas ilustrando mentalidade e expectativas
   - Priorize personas com base em impacto de negócio e frequência de uso

2. Um "Mapeamento de Jornadas de Usuário" (jornadas-usuario.md) que:
   - Documente 3-5 jornadas críticas de usuário de ponta a ponta
   - Mapeie estados emocionais em cada etapa (pontos de alegria e dor)
   - Identifique claramente oportunidades de melhoria e diferenciais competitivos
   - Visualize touch points entre usuário e sistema em cada etapa
   - Conecte etapas das jornadas com funcionalidades específicas a serem implementadas

3. Um "Canvas de Proposta de Valor" (proposta-valor.md) que:
   - Articule claramente os benefícios principais oferecidos para cada segmento de usuário
   - Mapeie como o sistema resolve dores específicas de cada perfil de usuário
   - Quantifique valor entregue utilizando métricas relevantes para o usuário
   - Compare proposta de valor com alternativas existentes no mercado
   - Estabeleça elementos de diferenciação clara e memorável

4. Uma "Matriz de Requisitos de Usuário" (matriz-requisitos-usuario.md) que:
   - Catalogue necessidades fundamentais organizadas por perfil de usuário
   - Priorize requisitos utilizando frameworks como KANO ou MoSCoW
   - Estabeleça critérios de sucesso do ponto de vista do usuário para cada requisito
   - Documente justificativas baseadas em pesquisa para cada requisito incluído
   - Identifique requisitos contraditórios entre diferentes perfis e proponha conciliações

5. Um "Modelo Mental de Usuário" (modelo-mental-usuario.md) que:
   - Mapeie como usuários conceituam o domínio do problema
   - Identifique terminologia natural utilizada pelos usuários-alvo
   - Documente expectativas de fluxo e organização baseadas em experiências prévias
   - Analise potenciais descompassos entre modelo mental do usuário e implementação técnica
   - Recomende estratégias para alinhar interface com modelos mentais predominantes

Cada documento deve incluir introdução explicando seu propósito, conteúdo principal estruturado e conclusão com recomendações-chave. Use linguagem clara, incorpore elementos visuais conceituais (através de descrições para geração posterior), e conecte documentos entre si com referências cruzadas quando apropriado.
```

#### 1.2. Documentação Técnica de Base

Este prompt gera documentos técnicos fundamentais necessários para alicerçar o desenvolvimento:

```
Atue como um Arquiteto de Sistemas especializado em documentação técnica e integração de sistemas. Estou desenvolvendo [descrição do sistema] que precisa interagir com [sistemas/tecnologias existentes] e necessito documentação técnica de base que estabeleça fundamentos claros para o desenvolvimento.

Por favor, crie os seguintes 5 documentos técnicos para armazenamento em '.agent/contexto/tecnico/':

1. Um "Glossário Técnico Abrangente" (glossario-tecnico.md) que:
   - Defina todos os termos técnicos e de domínio relevantes para o projeto
   - Organize termos em categorias lógicas (arquitetura, dados, infraestrutura, domínio)
   - Estabeleça convenções de nomenclatura para entidades principais do sistema
   - Inclua traduções e mapeamentos entre termos técnicos e de negócio
   - Documente acrônimos e abreviações com suas formas expandidas

2. Um "Mapa de Sistemas e Integrações" (mapa-sistemas.md) que:
   - Identifique todos os sistemas externos e internos que se integram à solução
   - Documente fluxos de dados principais entre sistemas com direção e protocolo
   - Especifique responsabilidades e limites claros entre sistemas
   - Caracterize sistemas por disponibilidade, performance e requisitos de segurança
   - Inclua diagramas representando a topologia completa do ecossistema

3. Uma "Documentação de APIs Externas" (apis-externas.md) que:
   - Catalogue todas as APIs externas necessárias para implementação
   - Documente endpoints principais, parâmetros e formatos de resposta
   - Especifique limites de taxa, restrições de uso e requisitos de autenticação
   - Mapeie dependências entre diferentes APIs e sequências de chamadas
   - Inclua exemplos concretos de requisição/resposta para operações críticas

4. Um "Modelo Técnico de Dados" (modelo-dados.md) que:
   - Defina estruturas de dados principais com atributos, tipos e restrições
   - Documente relacionamentos entre entidades com cardinalidade e natureza
   - Especifique estratégias de persistência, caching e sincronização
   - Mapeie fluxos de transformação de dados através do sistema
   - Identifique dados críticos, sensíveis ou regulados com requisitos especiais

5. Um "Framework de Requisitos Não-Funcionais" (requisitos-nao-funcionais.md) que:
   - Estabeleça requisitos quantificáveis para performance, escalabilidade e disponibilidade
   - Defina parâmetros de segurança, privacidade e conformidade regulatória
   - Documente requisitos de manutenibilidade, testabilidade e suporte
   - Especifique expectativas para compatibilidade e interoperabilidade
   - Priorize requisitos não-funcionais com justificativas técnicas

Cada documento deve incluir metadados (autor, versão, data), sumário executivo, conteúdo principal detalhado com exemplos, e apêndices com informações complementares quando necessário. Use formato técnico preciso, inclua referências a padrões e especificações relevantes, e indique claramente áreas que requerem investigação adicional.
```

#### 1.3. Documentos de Design e Experiência

O prompt a seguir permite a criação de documentos essenciais de design e experiência:

```
Atue como um Designer de UX/UI sênior especializado em documentação de design e prototipação. Estou desenvolvendo [descrição do produto/interface] para [público-alvo] e preciso criar documentação de design e experiência para orientar a implementação visual e interativa.

Por favor, crie os seguintes 5 documentos de design para armazenamento em '.agent/contexto/design/':

1. Uma "Especificação de Wireframes e Fluxos" (wireframes-fluxos.md) que:
   - Descreva detalhadamente wireframes para 5-7 telas/interfaces principais
   - Documente fluxos de navegação completos entre telas para cenários críticos
   - Especifique componentes interativos e seus comportamentos em diferentes estados
   - Mapeie hierarquia de informação e prioridade visual em cada interface
   - Inclua anotações explicando decisões de design e alternativas consideradas

2. Uma "Especificação de Acessibilidade" (acessibilidade.md) que:
   - Estabeleça requisitos de conformidade com WCAG (nível AA/AAA)
   - Documente estratégias para navegação por teclado e tecnologia assistiva
   - Especifique requisitos de contraste, tamanho de texto e feedback visual
   - Estabeleça diretrizes para estados de foco, mensagens de erro e orientação
   - Defina estratégias de teste para validação de acessibilidade

3. Uma "Guia de Aplicação de Design System" (design-system.md) que:
   - Mapeie componentes do design system organizacional para uso na interface
   - Documente extensões ou personalizações necessárias com justificativas
   - Especifique grid, espaçamento e sistemas de alinhamento a serem aplicados
   - Detalhe paletas de cores principais e secundárias com códigos e aplicações
   - Estabeleça hierarquia e uso de tipografia para diferentes elementos

4. Uma "Especificação de Microinterações" (microinteracoes.md) que:
   - Documente 8-10 microinterações críticas que enriquecem a experiência
   - Detalhe gatilhos, regras, feedback e loops para cada interação
   - Especifique timing, easing e propriedades de animação quando aplicável
   - Estabeleça padrões consistentes para estados de hover, loading e transição
   - Inclua considerações de performance e acessibilidade para cada interação

5. Um "Framework de Design Responsivo" (design-responsivo.md) que:
   - Defina breakpoints principais e estratégia de adaptação para diferentes dispositivos
   - Documente variações de layout, navegação e conteúdo por breakpoint
   - Especifique tratamento de imagens, tabelas e elementos complexos
   - Estabeleça estratégias para touch interfaces vs. interfaces com cursor
   - Defina abordagem para conteúdo prioritário em cada formato de tela

Cada documento deve incluir uma seção de princípios orientadores, especificações técnicas detalhadas, exemplos visuais (através de descrições para geração posterior) e considerações de implementação. Use linguagem que facilite comunicação entre designers e desenvolvedores, enfatize raciocínio por trás das decisões de design, e inclua critérios de aceitação claros para validação.
```

#### 1.4. Documentos Estratégicos

Este prompt gera documentação estratégica que alinha o desenvolvimento com objetivos de negócio:

```
Atue como um Product Strategist com experiência em planejamento estratégico de produtos digitais. Estou desenvolvendo [descrição do produto] para [mercado/indústria] e preciso criar documentação estratégica que alinhe desenvolvimento técnico com objetivos de negócio.

Por favor, crie os seguintes 5 documentos estratégicos para armazenamento em '.agent/contexto/estrategia/':

1. Uma "Análise Competitiva Detalhada" (analise-competitiva.md) que:
   - Identifique e caracterize 5-7 competidores diretos e indiretos principais
   - Compare funcionalidades, preços, posicionamento e público-alvo de cada competidor
   - Avalie forças e fraquezas de cada solução com base em critérios objetivos
   - Documente oportunidades de diferenciação e vantagens competitivas sustentáveis
   - Identifique tendências emergentes e direcionamentos futuros do mercado

2. Uma "Matriz de Experimentação e Validação" (matriz-experimentacao.md) que:
   - Formule 8-10 hipóteses-chave de negócio e produto a serem validadas
   - Projete experimentos específicos para testar cada hipótese crítica
   - Defina métricas e KPIs para mensurar sucesso de cada experimento
   - Estabeleça critérios claros para pivotar vs. perseverar em cada direção
   - Crie um framework para priorização de experimentos por impacto/esforço

3. Um "Roadmap Estratégico de Produto" (roadmap-produto.md) que:
   - Defina horizontes de planejamento (curto, médio e longo prazo)
   - Organize entregas em themes estratégicos alinhados com visão de produto
   - Estabeleça marcos mensuráveis e outcomes desejados para cada fase
   - Mapeie dependências críticas entre diferentes iniciativas
   - Articule narrativa estratégica que conecte roadmap a objetivos de negócio

4. Uma "Matriz de Risco e Oportunidade de Mercado" (matriz-risco-oportunidade.md) que:
   - Identifique fatores externos que podem impactar adoção e sucesso
   - Avalie novos segmentos de mercado e oportunidades de expansão
   - Documente riscos regulatórios, tecnológicos e competitivos emergentes
   - Analise ciclos de adoção e tendências potencialmente disruptivas
   - Defina estratégias de mitigação e planos de contingência para riscos prioritários

5. Um "Framework de Métricas de Sucesso" (metricas-sucesso.md) que:
   - Estabeleça métricas North Star e leading indicators para o produto
   - Defina métricas específicas por fase de funil (aquisição, ativação, retenção)
   - Crie dashboard conceitual mapeando relações causais entre métricas
   - Estabeleça benchmarks e metas quantitativas para cada métrica principal
   - Documente estratégia de instrumentação para coleta precisa de dados

Cada documento deve incluir um resumo executivo direcionado a stakeholders, conteúdo principal com análises aprofundadas e visualizações conceituais, e recomendações acionáveis. Use linguagem estratégica com suporte de dados, estabeleça conexões explícitas entre decisões técnicas e outcomes de negócio, e proponha frameworks para avaliação contínua e adaptação.
```

#### 1.5. Planos de Comunicação

O seguinte prompt gera documentação crucial para gestão de comunicação durante o projeto:

```
Atue como um Especialista em Comunicação de Projetos com experiência em desenvolvimento de software. Estou liderando [tipo de projeto] que envolve [stakeholders internos/externos] e preciso estabelecer estratégias claras de comunicação para garantir alinhamento e transparência durante todo o desenvolvimento.

Por favor, crie os seguintes 5 documentos de comunicação para armazenamento em '.agent/contexto/comunicacao/':

1. Uma "Estratégia de Comunicação de Projeto" (estrategia-comunicacao.md) que:
   - Defina princípios orientadores para comunicação durante o projeto
   - Estabeleça cadências e rituais de comunicação (diários, semanais, mensais)
   - Documente políticas para escalação de problemas e tomada de decisão
   - Especifique ferramentas e canais oficiais para diferentes tipos de comunicação
   - Defina abordagens para comunicação em situações críticas ou emergenciais

2. Uma "Matriz de Stakeholders Detalhada" (matriz-stakeholders.md) que:
   - Identifique todos os stakeholders internos e externos relevantes
   - Classifique stakeholders por nível de influência, interesse e expertise
   - Documente necessidades informacionais específicas de cada grupo
   - Estabeleça estratégias personalizadas de engajamento por perfil
   - Defina responsáveis por manter relacionamento com cada stakeholder-chave

3. Um "Plano de Comunicação de Status" (comunicacao-status.md) que:
   - Defina template estruturado para reportes regulares de progresso
   - Estabeleça métricas e indicadores a serem incluídos consistentemente
   - Documente processo de coleta e validação de informações
   - Especifique frequência, formato e canais para diferentes audiências
   - Inclua estratégias para destacar dependências, riscos e necessidades de decisão

4. Um "Framework de Comunicação Técnica" (comunicacao-tecnica.md) que:
   - Estabeleça processos para documentação e compartilhamento de decisões técnicas
   - Defina estrutura para comunicação de mudanças arquiteturais e seu impacto
   - Documente convenções para documentação inline e técnica do código
   - Especifique abordagem para transferência de conhecimento entre equipes
   - Crie guidelines para simplificação de conceitos técnicos para audiências não-técnicas

5. Um "Plano de Gestão de Feedback" (gestao-feedback.md) que:
   - Estabeleça canais formais para coleta de feedback durante o desenvolvimento
   - Defina processo estruturado para processamento e priorização de feedback
   - Documente ciclo de comunicação para "fechar o loop" com provedores de feedback
   - Especifique critérios para incorporação de feedback em roadmap
   - Crie framework para reconciliação de feedback conflitante entre stakeholders

Cada documento deve incluir propósito e escopo claramente definidos, instruções práticas de implementação, exemplos ou templates aplicáveis, e métricas para avaliar efetividade. Use linguagem clara e direta, organize conteúdo para fácil referência, e considere diferentes contextos organizacionais onde a comunicação ocorrerá.
```

#### 1.6. Documentos de Requisitos Funcionais

Este prompt auxilia na criação de especificações funcionais detalhadas:

```
Atue como um Analista de Negócios sênior especializado em especificação de requisitos para desenvolvimento de software. Estou trabalhando em [tipo de sistema] que precisa [objetivos principais] e necessito documentação detalhada de requisitos funcionais que oriente de forma precisa a implementação.

Por favor, crie os seguintes 5 documentos de requisitos para armazenamento em '.agent/contexto/requisitos/':

1. Um "Documento de Visão e Escopo" (visao-escopo.md) que:
   - Articule claramente a visão do produto e objetivos fundamentais
   - Defina critérios explícitos de inclusão e exclusão de escopo
   - Estabeleça pressupostos e restrições que impactam requisitos
   - Documente dependências externas críticas para sucesso do projeto
   - Apresente linha do tempo de alto nível com marcos principais

2. Uma "Especificação de Casos de Uso Principais" (casos-uso.md) que:
   - Documente 8-10 casos de uso críticos com formato consistente
   - Para cada caso, especifique atores, pré-condições, fluxo principal e alternativos
   - Detalhe regras de negócio aplicáveis a cada fluxo
   - Inclua critérios objetivos de aceitação para cada caso de uso
   - Defina prioridade relativa e impacto de negócio

3. Uma "Matriz de Requisitos Funcionais" (matriz-requisitos-funcionais.md) que:
   - Catalogue requisitos funcionais com IDs únicos e rastreáveis
   - Organize requisitos em categorias lógicas e módulos funcionais
   - Especifique dependências e relacionamentos entre requisitos
   - Defina critérios de aceitação verificáveis para cada requisito
   - Atribua prioridade utilizando framework consistente (MOSCOW ou similar)

4. Um "Modelo de Regras de Negócio" (regras-negocio.md) que:
   - Documente todas as regras de negócio aplicáveis ao sistema
   - Organize regras em categorias (cálculos, validações, fluxos de trabalho)
   - Especifique parâmetros configuráveis vs. hardcoded para cada regra
   - Defina comportamentos esperados para exceções a cada regra
   - Inclua exemplos concretos ilustrando aplicação das regras principais

5. Uma "Especificação de Fluxos de Processo" (fluxos-processo.md) que:
   - Modele processos de negócio completos suportados pelo sistema
   - Documente estados, transições e ações em cada etapa do processo
   - Especifique papéis e responsabilidades em cada ponto de decisão
   - Defina gatilhos, condições e eventos que impactam o fluxo
   - Inclua tratamento de exceções e caminhos alternativos

Cada documento deve incluir histórico de revisões, tabela de referências cruzadas com outros documentos, glossário de termos específicos de domínio, e seção de questões abertas. Use linguagem precisa e inequívoca, estruture conteúdo de forma hierárquica com numeração consistente, e incorpore exemplos concretos para ilustrar requisitos complexos.
```

Esta documentação abrangente, facilitada pelo Copilot através dos prompts especializados acima, transforma a fase inicial de definição em um alicerce robusto que orienta todas as etapas subsequentes, minimizando retrabalho e garantindo alinhamento consistente entre requisitos de negócio, experiência do usuário e viabilidade técnica. Cada conjunto de documentos cria um repositório estruturado de conhecimento que serve como referência autoritativa durante todo o processo de desenvolvimento, facilitando decisões informadas e mantendo o foco nas necessidades reais dos usuários e objetivos estratégicos da organização.

### 2. Análise de Impacto e Alinhamento Estratégico

A metodologia estruturada para análise de impacto transcende avaliações superficiais, implementando um framework multidimensional que examina meticulosamente como a solução proposta interage com o ecossistema técnico e organizacional existente. Esta fase aplica técnicas de análise sistêmica para mapear completamente a rede de dependências, identificar pontos de integração críticos, e quantificar impactos potenciais em múltiplas camadas da arquitetura tecnológica e processos de negócio.

Com o suporte do GitHub Copilot, equipes técnicas conduzem análises preditivas de impacto que simulam cenários de implementação e suas consequências em diversas condições operacionais. O processo incorpora perspectivas complementares de Arquitetos de Software, Project Managers e especialistas em modernização, que trabalham colaborativamente para construir um modelo holístico das implicações técnicas, operacionais e estratégicas da implementação proposta.

O resultado é uma compreensão profunda e multifacetada das repercussões da solução, traduzida em documentação estratégica que possibilita tomadas de decisão informadas, priorização eficaz, e planejamento preciso de recursos. Esta análise estabelece um equilíbrio cuidadoso entre objetivos imediatos de implementação e considerações estratégicas de longo prazo, garantindo alinhamento consistente com a visão tecnológica da organização.

A fase culmina na criação de artefatos analíticos abrangentes, organizados na pasta `.agent/contexto/impacto`, facilitada através de prompts especializados para o GitHub Copilot que garantem análises completas e perspectivas multidimensionais:

#### 2.1. Prompt para Documentos de Análise Técnica

```
Atue como um Arquiteto de Sistemas sênior especializado em análise de impacto técnico. Estou implementando [descrição da solução] que afetará [sistemas existentes] e preciso documentar detalhadamente os impactos técnicos para garantir uma integração harmoniosa.

Por favor, crie os seguintes 5 documentos de análise técnica para armazenamento em '.agent/contexto/impacto/tecnico/':

1. Uma "Matriz de Impacto em Sistemas" (matriz-impacto-sistemas.md) que:
   - Identifique todos os sistemas e componentes afetados pela implementação
   - Classifique o impacto em cada sistema (Alto/Médio/Baixo) com justificativas técnicas
   - Documente mudanças específicas necessárias em cada componente
   - Mapeie dependências transitivas que podem ser indiretamente afetadas
   - Priorize componentes por criticidade de impacto e complexidade de adaptação

2. Um "Mapeamento de Dependências Técnicas" (mapeamento-dependencias.md) que:
   - Visualize a rede completa de dependências entre componentes afetados
   - Identifique relações cíclicas ou problemas de acoplamento excessivo
   - Documente fluxos de dados entre componentes com detalhes de interfaces
   - Especifique dependências de temporalidade e sequenciamento
   - Identifique componentes críticos que representam pontos únicos de falha

3. Uma "Análise de Compatibilidade e Interoperabilidade" (analise-compatibilidade.md) que:
   - Avalie compatibilidade entre tecnologias existentes e propostas
   - Documente potenciais conflitos de versão, frameworks ou bibliotecas
   - Identifique requisitos de adaptadores ou camadas de compatibilidade
   - Avalie impactos em protocolos e formatos de comunicação existentes
   - Especifique estratégias para garantir retrocompatibilidade quando necessário

4. Um "Relatório de Débito Técnico e Sustentabilidade" (debito-tecnico.md) que:
   - Identifique áreas onde a implementação pode aumentar ou reduzir débito técnico
   - Quantifique impactos na manutenibilidade da base de código
   - Avalie alinhamento da solução com direcionamentos arquiteturais de longo prazo
   - Documente trade-offs técnicos e suas implicações para evolução futura
   - Recomende ações específicas para mitigar débito técnico introduzido

5. Uma "Avaliação de Capacidade de Infraestrutura" (capacidade-infraestrutura.md) que:
   - Analise requisitos de recursos computacionais da nova implementação
   - Avalie capacidade atual vs. necessidades projetadas (CPU, memória, armazenamento, rede)
   - Identifique potenciais gargalos de performance ou escalabilidade
   - Documente impactos em ambientes de desenvolvimento, teste e produção
   - Recomende ajustes de infraestrutura necessários com estimativas de capacidade

Cada documento deve incluir um resumo executivo para stakeholders técnicos, análise detalhada com evidências objetivas, e recomendações claras. Use diagramas conceituais (descritos textualmente para geração posterior), tabelas comparativas, e métricas quantitativas quando apropriado. Conclua cada documento com uma seção de "Próximos Passos" que priorize ações técnicas necessárias.
```

#### 2.2. Prompt para Documentos de Risco e Mitigação

```
Atue como um Especialista em Gestão de Riscos técnicos com experiência em implementações de sistemas complexos. Estou planejando implementar [descrição da solução] e preciso identificar, avaliar e mitigar sistematicamente todos os riscos técnicos associados.

Por favor, crie os seguintes 5 documentos de análise de riscos para armazenamento em '.agent/contexto/impacto/riscos/':

1. Um "Registro de Riscos Técnicos" (registro-riscos-tecnicos.md) que:
   - Identifique pelo menos 15 riscos técnicos potenciais categorizados por tipo (segurança, performance, integração, etc.)
   - Avalie cada risco quanto a probabilidade (1-5) e impacto (1-5) com metodologia consistente
   - Calcule exposição ao risco (probabilidade x impacto) e classifique por criticidade
   - Documente gatilhos e indicadores precoces para cada risco
   - Identifique owner responsável pelo monitoramento de cada risco

2. Um documento de "Estratégias de Mitigação" (estrategias-mitigacao.md) que:
   - Desenvolva estratégias detalhadas para mitigar cada risco identificado
   - Diferencie entre medidas preventivas e corretivas para cada cenário
   - Especifique recursos necessários para implementar cada estratégia
   - Defina métricas para avaliar eficácia das medidas de mitigação
   - Priorize mitigações com melhor relação custo-benefício

3. Um "Plano de Contingência e Rollback" (plano-contingencia-rollback.md) que:
   - Detalhe procedimentos específicos para reversão em caso de falhas críticas
   - Defina pontos de verificação e critérios objetivos para decisões de rollback
   - Especifique responsabilidades e cadeia de comando para situações de crise
   - Documente requisitos para ambientes paralelos durante transição
   - Inclua checklists operacionais para procedimentos de emergência

4. Uma "Análise de Resiliência e Pontos de Falha" (resiliencia-pontos-falha.md) que:
   - Identifique todos os pontos únicos de falha na arquitetura proposta
   - Avalie impacto de falhas em componentes específicos
   - Documente estratégias de degradação graciosa para cenários críticos
   - Especifique mecanismos de redundância e failover recomendados
   - Defina padrões de design para aumentar tolerância a falhas

5. Um "Framework de Monitoramento de Riscos" (monitoramento-riscos.md) que:
   - Defina KRIs (Key Risk Indicators) específicos para monitoramento contínuo
   - Especifique limiares de alerta para cada indicador
   - Documente processo para reavaliação periódica do perfil de risco
   - Estabeleça protocolo de escalonamento para riscos emergentes
   - Detalhe requisitos de instrumentação para detecção precoce de problemas

Cada documento deve incluir uma matriz de responsabilidade, cronograma de implementação das medidas propostas, e referências a padrões da indústria relevantes. Use linguagem clara que comunique eficazmente riscos técnicos para stakeholders não-técnicos, e inclua métricas quantitativas para avaliação objetiva quando possível.
```

#### 2.3. Prompt para Documentos de Alinhamento Estratégico

```
Atue como um Estrategista Tecnológico sênior especializado em alinhamento entre iniciativas técnicas e objetivos organizacionais. Estou implementando [descrição da solução] e preciso garantir que esteja perfeitamente alinhada com a direção estratégica da organização.

Por favor, crie os seguintes 5 documentos de alinhamento estratégico para armazenamento em '.agent/contexto/impacto/estrategia/':

1. Uma "Matriz de Alinhamento com Objetivos Estratégicos" (alinhamento-objetivos.md) que:
   - Mapeie a implementação proposta para objetivos estratégicos específicos da organização
   - Quantifique a contribuição esperada para cada objetivo estratégico
   - Identifique áreas de alto e baixo alinhamento com justificativas
   - Documente como a solução suporta diretamente metas de negócio de curto e longo prazo
   - Proponha ajustes para maximizar valor estratégico da implementação

2. Uma "Avaliação de Vantagem Competitiva" (vantagem-competitiva.md) que:
   - Analise como a implementação afeta o posicionamento competitivo da organização
   - Compare capacidades resultantes com soluções concorrentes no mercado
   - Identifique elementos de diferenciação técnica e seus benefícios tangíveis
   - Avalie sustentabilidade da vantagem competitiva ao longo do tempo
   - Recomende áreas para amplificar diferenciação estratégica

3. Uma "Análise de Conformidade e Governança" (conformidade-governanca.md) que:
   - Verifique alinhamento com políticas internas e frameworks de governança
   - Avalie conformidade com regulamentações externas aplicáveis ao setor
   - Identifique requisitos de documentação e evidências para compliance
   - Documente impactos em processos de auditoria e certificações
   - Recomende ajustes para garantir total conformidade regulatória

4. Um "Roadmap de Integração Estratégica" (roadmap-integracao.md) que:
   - Alinhe a implementação proposta com outras iniciativas tecnológicas planejadas
   - Identifique sinergias potenciais e oportunidades de integração
   - Defina sequenciamento estratégico para maximizar valor incremental
   - Documente marcos de integração e dependências entre iniciativas
   - Proponha estratégia de evolução contínua após implementação inicial

5. Uma "Avaliação de Impacto em Experiência e Valor" (impacto-experiencia-valor.md) que:
   - Analise como a implementação afetará experiência de usuários e stakeholders
   - Quantifique benefícios esperados usando métricas relevantes de negócio
   - Identifique potenciais trade-offs entre diferentes dimensões de valor
   - Documente impactos em KPIs organizacionais específicos
   - Recomende abordagem para mensuração contínua de valor entregue

Cada documento deve começar com um resumo executivo direcionado a líderes seniores, incluir análises baseadas em dados sempre que possível, e terminar com recomendações acionáveis. Use visualizações conceituais (através de descrições para geração posterior) para comunicar relações complexas, e inclua referências a documentos estratégicos organizacionais específicos quando relevante.
```

#### 2.4. Prompt para Documentos de Planejamento de Recursos

```
Atue como um Gerente de Projetos Técnicos experiente especializado em planejamento de recursos para implementações de software. Estou planejando implementar [descrição da solução] e preciso documentação detalhada para planejamento preciso de recursos humanos, técnicos e temporais.

Por favor, crie os seguintes 5 documentos de planejamento de recursos para armazenamento em '.agent/contexto/impacto/recursos/':

1. Um documento de "Estimativas Refinadas de Esforço" (estimativas-esforco.md) que:
   - Decomponha a implementação em componentes e tarefas mensuráveis
   - Forneça estimativas detalhadas para cada componente (em horas/dias)
   - Utilize técnicas como PERT ou estimativa de três pontos para maior precisão
   - Documente premissas utilizadas para cada estimativa
   - Identifique áreas de maior incerteza e recomende abordagens de mitigação

2. Um "Mapeamento de Competências Necessárias" (competencias-necessarias.md) que:
   - Identifique todas as habilidades técnicas e não-técnicas necessárias
   - Categorize competências por especialização e nível de proficiência requerido
   - Especifique competências críticas vs. preferenciais para cada área
   - Documente interdependências entre diferentes perfis de competência
   - Recomende estratégias para preencher lacunas de competências identificadas

3. Uma "Análise de Capacidade e Disponibilidade" (capacidade-disponibilidade.md) que:
   - Avalie capacidade atual da equipe vs. necessidades da implementação
   - Analise disponibilidade de recursos considerando comprometimentos existentes
   - Identifique períodos de pico de demanda e potenciais gargalos
   - Documente impactos em outras iniciativas devido à alocação de recursos
   - Recomende estratégias de balanceamento e priorização de recursos

4. Um "Cronograma Preliminar Detalhado" (cronograma-preliminar.md) que:
   - Crie timeline realista com fases, tarefas e dependências claramente definidas
   - Identifique caminho crítico e margens de segurança para tarefas-chave
   - Defina marcos mensuráveis e gates de decisão no fluxo do projeto
   - Documente janelas ideais para atividades de alto risco
   - Especifique buffers estratégicos para absorver incertezas conhecidas

5. Um "Plano de Aquisição e Alocação de Recursos" (aquisicao-alocacao.md) que:
   - Detalhe necessidades de contratação, terceirização ou realocação
   - Especifique requisitos para infraestrutura, ferramentas e licenças
   - Defina estratégia para onboarding e capacitação de novos recursos
   - Documente plano de balanceamento de carga para recursos compartilhados
   - Inclua cronograma para aquisição de diferentes categorias de recursos

Cada documento deve incluir tabelas estruturadas para fácil referência, análises quantitativas baseadas em dados históricos quando disponíveis, e visualizações claras de informações complexas. Use linguagem precisa, evite ambiguidades em estimativas e requisitos, e inclua planos de contingência para cenários de restrição de recursos.
```

#### 2.5. Prompt para Documentos de Gerenciamento de Stakeholders

```
Atue como um Especialista em Gerenciamento de Stakeholders Técnicos com experiência em grandes implementações de software. Estou implementando [descrição da solução] que afetará múltiplos grupos técnicos e de negócio, e preciso uma estratégia abrangente para gerenciar stakeholders efetivamente durante todo o ciclo de vida da implementação.

Por favor, crie os seguintes 5 documentos de gerenciamento de stakeholders para armazenamento em '.agent/contexto/impacto/stakeholders/':

1. Uma "Matriz de Análise de Stakeholders Técnicos" (matriz-stakeholders.md) que:
   - Identifique todos os grupos e indivíduos afetados pela implementação
   - Classifique stakeholders por influência, interesse e atitude (apoiador/neutro/resistente)
   - Mapeie conhecimento técnico de cada stakeholder sobre a solução proposta
   - Documente preocupações específicas e motivações de cada grupo
   - Priorize stakeholders por criticidade para o sucesso da implementação

2. Um "Plano de Comunicação Técnica" (plano-comunicacao.md) que:
   - Defina estratégia de comunicação personalizada para cada grupo de stakeholders
   - Especifique canais, frequência e formato para diferentes tipos de comunicação
   - Desenvolva templates para comunicações recorrentes (status reports, atualizações técnicas)
   - Documente pontos de decisão que requerem aprovação ou input específico
   - Defina estratégia para gerenciamento de expectativas em diferentes fases

3. Uma "Matriz RACI Detalhada" (matriz-raci.md) que:
   - Mapeie todas as atividades críticas da implementação
   - Defina claramente papéis (Responsável, Aprovador, Consultado, Informado) para cada atividade
   - Especifique responsabilidades para decisões técnicas específicas
   - Documente protocolos de escalação para resolução de conflitos
   - Identifique handoffs críticos entre diferentes equipes ou departamentos

4. Um "Registro de Dependências Externas" (dependencias-externas.md) que:
   - Identifique todas as dependências de equipes ou sistemas externos
   - Documente informações de contato para cada ponto focal externo
   - Especifique contratos de serviço ou acordos de nível de serviço existentes
   - Defina protocolos para solicitação e acompanhamento de suporte externo
   - Estabeleça mecanismos de escalação para dependências críticas

5. Um "Plano de Engajamento e Adoção" (engajamento-adocao.md) que:
   - Desenvolva estratégias para obter buy-in de stakeholders críticos
   - Defina abordagens para mitigar resistência em diferentes grupos
   - Especifique iniciativas de capacitação e transferência de conhecimento
   - Documente métricas para monitorar adoção e satisfação
   - Estabeleça feedback loops para adaptação contínua baseada em input de stakeholders

Cada documento deve incluir recomendações específicas e acionáveis, exemplos de mensagens-chave adaptadas para diferentes audiências, e critérios claros para avaliar a eficácia das estratégias de engajamento. Use abordagem empática que reconheça preocupações legítimas de stakeholders, e integre perspectivas técnicas e humanas em todas as recomendações.
```

#### 2.6. Prompt para Documentos de Análise de Impacto em Negócios

```
Atue como um Analista de Negócios sênior especializado na avaliação de impactos organizacionais de implementações tecnológicas. Estou implementando [descrição da solução] e preciso compreender detalhadamente como esta mudança afetará processos de negócio, operações e resultados financeiros da organização.

Por favor, crie os seguintes 5 documentos de análise de impacto em negócios para armazenamento em '.agent/contexto/impacto/negocio/':

1. Uma "Análise de Impacto em Processos de Negócio" (impacto-processos.md) que:
   - Identifique todos os processos de negócio afetados pela implementação
   - Documente mudanças específicas em fluxos de trabalho e procedimentos
   - Quantifique melhorias esperadas em eficiência e eficácia
   - Mapeie impactos temporários durante a transição
   - Recomende ajustes em processos para maximizar benefícios da nova solução

2. Um "Estudo de ROI e Análise Financeira" (roi-analise-financeira.md) que:
   - Calcule retorno sobre investimento com metodologia transparente
   - Documente todos os custos (diretos, indiretos, iniciais, recorrentes)
   - Quantifique benefícios financeiros esperados com linhas temporais
   - Analise sensibilidade para diferentes cenários e variáveis
   - Avalie período de payback e outras métricas financeiras relevantes

3. Uma "Avaliação de Impacto Operacional" (impacto-operacional.md) que:
   - Analise mudanças em indicadores operacionais chave
   - Documente impactos em velocidade, qualidade e confiabilidade
   - Identifique potenciais riscos operacionais durante e após implementação
   - Avalie necessidades de ajustes em procedimentos operacionais
   - Recomende métricas para monitoramento contínuo de performance operacional

4. Um "Mapa de Transformação Organizacional" (transformacao-organizacional.md) que:
   - Identifique mudanças necessárias em estruturas organizacionais
   - Documente impactos em funções e responsabilidades existentes
   - Avalie necessidades de novas habilidades ou papéis
   - Mapeie resistências potenciais e áreas de adaptação cultural
   - Recomende estratégias para gestão de mudança organizacional

5. Uma "Análise de Impacto em Clientes e Parceiros" (impacto-externo.md) que:
   - Avalie mudanças na experiência de clientes externos
   - Documente impactos em interfaces e integrações com parceiros
   - Identifique oportunidades para valor adicional em relações externas
   - Analise riscos potenciais em percepção de marca ou satisfação
   - Recomende estratégias para comunicação externa e gestão de expectativas

Cada documento deve apresentar análises fundamentadas em dados, incluir métricas quantitativas e qualitativas, considerar impactos de curto e longo prazo, e oferecer recomendações específicas para otimização de resultados. Use linguagem acessível a stakeholders de negócio, e inclua exemplos concretos e estudos de caso comparáveis quando relevante.
```

#### 2.7. Prompt para Documentos de Impacto em Segurança e Compliance

```
Atue como um Consultor de Segurança e Compliance com especialização em avaliação de impacto de novas implementações tecnológicas. Estou implementando [descrição da solução] e preciso avaliar completamente como esta mudança afetará nosso perfil de segurança e postura de compliance.

Por favor, crie os seguintes 5 documentos de análise de impacto em segurança e compliance para armazenamento em '.agent/contexto/impacto/seguranca-compliance/':

1. Uma "Avaliação de Impacto em Segurança" (avaliacao-seguranca.md) que:
   - Analise mudanças no perímetro e superfície de ataque da organização
   - Identifique novas ameaças potenciais introduzidas pela implementação
   - Avalie impactos em controles de segurança existentes
   - Documente requisitos de segurança adicionais necessários
   - Recomende melhorias específicas para manter ou aumentar postura de segurança

2. Uma "Análise de Impacto em Privacidade de Dados" (privacidade-dados.md) que:
   - Identifique todos os fluxos de dados pessoais ou sensíveis afetados
   - Avalie conformidade com LGPD, GDPR e outras regulações aplicáveis
   - Documente mudanças necessárias em políticas de privacidade
   - Especifique requisitos para consentimento, retenção e exclusão
   - Recomende controles técnicos para proteção de dados sensíveis

3. Uma "Matriz de Compliance Regulatório" (matriz-compliance.md) que:
   - Mapeie a implementação contra todas as regulações aplicáveis
   - Identifique potenciais brechas de compliance introduzidas
   - Documente novos requisitos regulatórios aplicáveis
   - Especifique evidências e documentação necessárias para auditoria
   - Recomende ações específicas para garantir total conformidade

4. Um "Plano de Validação de Segurança" (validacao-seguranca.md) que:
   - Defina metodologia para avaliação de segurança pré-implementação
   - Especifique requisitos para testes de penetração e análise de vulnerabilidades
   - Documente procedimentos para revisão de código focada em segurança
   - Estabeleça critérios de aceitação de segurança para autorização de deploy
   - Recomende estratégia para monitoramento contínuo pós-implementação

5. Uma "Estratégia de Gestão de Incidentes" (gestao-incidentes.md) que:
   - Avalie mudanças necessárias em procedimentos de resposta a incidentes
   - Especifique requisitos para logging de segurança e auditoria
   - Documente cenários de resposta para novos vetores de ataque potenciais
   - Defina processos para comunicação de incidentes a reguladores e afetados
   - Recomende melhorias em capacidades de detecção e contenção

Cada documento deve aliar profundidade técnica com clareza para stakeholders não-técnicos, incluir referências a frameworks relevantes (NIST, ISO, CIS, etc.), quantificar riscos usando metodologias estruturadas, e priorizar recomendações baseadas em análise de risco. Use linguagem precisa que possa servir como documentação para auditorias e evidências de due diligence.
```

Esta análise multidimensional, potencializada pelo GitHub Copilot através de prompts especializados, transforma a avaliação de impacto em um processo estratégico que antecipa desafios, identifica oportunidades, e estabelece bases sólidas para uma implementação alinhada tanto com necessidades imediatas quanto com objetivos organizacionais de longo prazo. Cada grupo de documentos contribui para uma visão holística que permite decisões informadas, gestão eficaz de riscos, e planejamento preciso de recursos em todas as dimensões do projeto.

### 3. Design Arquitetural e Registros de Decisão (ADRs)

A metodologia estruturada para definição arquitetural transcende simples diagramas técnicos, implementando um framework multidimensional que estabelece fundações sólidas para todo o desenvolvimento subsequente. Esta fase emprega técnicas avançadas de modelagem arquitetural para analisar requisitos, explorar diversas abordagens técnicas, e criar documentação abrangente que comunica claramente decisões estruturais e seus fundamentos racionais.

Com o suporte do GitHub Copilot, arquitetos e desenvolvedores conduzem explorações sistemáticas de padrões arquiteturais, avaliando meticulosamente trade-offs entre escalabilidade, performance, segurança e manutenibilidade. O processo incorpora perspectivas complementares de Arquitetos de Software, especialistas em segurança e performance, que colaboram para construir uma visão coesa que atende tanto requisitos imediatos quanto considerações estratégicas de longo prazo.

O resultado é uma arquitetura técnica robusta, documentada através de múltiplos artefatos estruturados que capturam não apenas o design final, mas também o raciocínio por trás de cada decisão significativa. Esta documentação estabelece um contrato arquitetural entre todas as partes envolvidas e serve como referência autoritativa durante toda a implementação e ciclos de vida subsequentes.

A fase culmina na criação de artefatos arquiteturais abrangentes, organizados na pasta `.agent/contexto/arquitetura`:

#### 3.1. Documentos de Visão Arquitetural

- Diagrama de Arquitetura de Alto Nível ilustrando componentes principais e suas interações
- Matriz de Requisitos Não-Funcionais com estratégias arquiteturais correspondentes
- Visão de Componentes detalhando responsabilidades e interfaces de cada módulo
- Modelo de Domínio representando entidades principais e seus relacionamentos

#### 3.2. Architecture Decision Records (ADRs)

- ADR para cada decisão arquitetural significativa, incluindo contexto, alternativas consideradas e justificativa
- Índice de ADRs categorizando decisões por componente e impacto
- Documentação de decisões rejeitadas e suas razões, preservando o histórico decisório
- Templates padronizados para documentação consistente de novas decisões

#### 3.3. Documentos de Design Técnico

- Especificações detalhadas de interfaces entre componentes
- Diagramas de sequência para fluxos críticos de processamento
- Modelos de dados e schemas
- Padrões de design específicos a serem aplicados consistentemente

#### 3.4. Documentos de Segurança e Privacidade

- Modelo de Ameaças identificando vetores potenciais de ataque
- Estratégias de Mitigação para vulnerabilidades identificadas
- Análise de Privacidade por Design para fluxos de dados sensíveis
- Matriz de Conformidade arquitetural com requisitos regulatórios

#### 3.5. Documentos de Performance e Escalabilidade

- Análises de Capacidade e modelos de carga esperada
- Estratégias de Escalabilidade para componentes críticos
- Benchmarks e Alvos de Performance documentados
- Planos de Contingência para cenários de pico de utilização

#### 3.6. Documentos de Evolução Arquitetural

- Roadmap de Evolução Técnica alinhado com objetivos de negócio
- Análise de Áreas de Flexibilidade e pontos de extensão
- Estratégia de Gerenciamento de Dívida Técnica
- Plano de Migração para componentes legados quando aplicável

A criação desta documentação arquitetural abrangente é significativamente potencializada pelo uso de prompts especializados do GitHub Copilot. Abaixo, apresentamos diversos prompts otimizados, cada um focado em uma categoria específica de documentação arquitetural, com instruções detalhadas para gerar documentos estruturados em cada categoria:

#### 3.7. Prompts para Geração de Documentação Arquitetural

##### Prompt 1: Geração de Documentos de Visão Arquitetural

```
Atue como um Arquiteto de Software sênior especializado em modelagem arquitetural de sistemas. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentos de visão arquitetural para fornecer um panorama abrangente da solução.

Por favor, crie os seguintes 5 documentos conforme especificações, a serem armazenados em '.agent/contexto/arquitetura/visao/':

1. Um "Diagrama de Arquitetura de Alto Nível" (diagrama-arquitetura-alto-nivel.md) que:
   - Utilize notação C4 Model (ou equivalente)
   - Ilustre todos os componentes principais do sistema e suas interações
   - Destaque fronteiras do sistema e integrações externas
   - Inclua legendas explicativas para todos os símbolos e conectores
   - Represente fluxos de dados principais entre componentes

2. Uma "Matriz de Requisitos Não-Funcionais" (matriz-requisitos-nao-funcionais.md) que:
   - Identifique todos os requisitos não-funcionais críticos (performance, escalabilidade, segurança, etc.)
   - Para cada requisito, documente expectativas quantificáveis
   - Especifique estratégias arquiteturais específicas para atender cada requisito
   - Estabeleça métricas de sucesso verificáveis para cada requisito
   - Documente trade-offs e impactos entre requisitos conflitantes

3. Uma "Visão de Componentes" (visao-componentes.md) que:
   - Detalhe cada componente principal identificado no diagrama de alto nível
   - Especifique responsabilidades precisas e limites de cada componente
   - Documente interfaces públicas, contratos e protocolos de comunicação
   - Defina dependências entre componentes e natureza dessas dependências
   - Explique princípios de design aplicados em cada componente

4. Um "Modelo de Domínio" (modelo-dominio.md) que:
   - Represente todas as entidades principais do domínio e seus relacionamentos
   - Documente atributos essenciais de cada entidade
   - Identifique agregados, entidades raiz e objetos de valor
   - Defina invariantes de domínio e regras de negócio críticas
   - Mapeie o modelo para componentes técnicos da arquitetura

5. Um "Manifesto Arquitetural" (manifesto-arquitetural.md) que:
   - Articule princípios e valores arquiteturais orientadores
   - Estabeleça convenções e padrões aplicáveis a toda a arquitetura
   - Defina métricas de qualidade arquitetural para o projeto
   - Explique compromissos e prioridades arquiteturais adotados
   - Documente restrições técnicas e organizacionais consideradas

Cada documento deve seguir uma estrutura clara com introdução, conteúdo principal detalhado e conclusão. Use linguagem precisa, incorpore diagramas quando aplicável (através de notação Mermaid ou descrições para geração posterior), e inclua referências a documentos relacionados quando relevante.
```

##### Prompt 2: Geração de Architecture Decision Records (ADRs)

```
Atue como um Arquiteto de Soluções experiente especializado em documentação arquitetural e ADRs. Estou desenvolvendo um sistema [descrição do sistema] e preciso documentar decisões arquiteturais críticas que orientarão o desenvolvimento.

Por favor, crie os seguintes 10 ADRs detalhados para serem armazenados em '.agent/contexto/arquitetura/adrs/':

1. Um ADR sobre "Escolha de Padrão Arquitetural Principal" (ADR-001-padrao-arquitetural.md) que:
   - Documente a decisão entre arquiteturas candidatas (monolítica, microsserviços, etc.)
   - Explique o contexto técnico e de negócio que influenciou a decisão
   - Detalhe todas as alternativas consideradas com análise de prós e contras
   - Justifique a escolha final baseada em requisitos específicos do projeto
   - Identifique consequências, riscos e mitigações da escolha

2. Um ADR sobre "Estratégia de Persistência de Dados" (ADR-002-persistencia-dados.md) que:
   - Aborde decisões sobre tipos de bancos de dados (relacional, NoSQL, híbrido)
   - Analise padrões de acesso a dados esperados e volumes previstos
   - Compare tecnologias específicas consideradas com justificativas técnicas
   - Detalhe estratégias de particionamento, replicação e backup
   - Explique abordagens para evolução de schema e migrações

3. Um ADR sobre "Estratégia de Autenticação e Autorização" (ADR-003-autenticacao-autorizacao.md) que:
   - Documente o modelo de segurança adotado (roles, claims, policies)
   - Compare protocolos considerados (OAuth, JWT, SAML, etc.)
   - Analise abordagens para gerenciamento de identidade (interna vs. federada)
   - Detalhe fluxos de autenticação para diferentes tipos de usuários/clientes
   - Explique estratégias para armazenamento seguro de credenciais

4. Um ADR sobre "Estratégia de Comunicação entre Componentes" (ADR-004-comunicacao-componentes.md) que:
   - Compare padrões considerados (REST, GraphQL, gRPC, mensageria, etc.)
   - Analise requisitos de latência, throughput e confiabilidade
   - Justifique escolhas específicas para diferentes tipos de comunicação
   - Detalhe estratégias para resiliência e tratamento de falhas
   - Explique padrões de design aplicados (Circuit Breaker, Retry, etc.)

5. Um ADR sobre "Abordagem para Observabilidade e Monitoramento" (ADR-005-observabilidade.md) que:
   - Compare estratégias consideradas para logging, métricas e tracing
   - Analise ferramentas e frameworks avaliados
   - Detalhe padrões para instrumentação de código
   - Explique estratégias para correlação de eventos distribuídos
   - Defina abordagens para alertas e detecção de anomalias

6. Um ADR sobre "Estratégia de Escalabilidade e Performance" (ADR-006-escalabilidade-performance.md) que:
   - Compare diferentes abordagens de escalabilidade (vertical, horizontal, funcional)
   - Analise expectativas de carga e identificação de gargalos potenciais
   - Detalhe estratégias para caching em múltiplos níveis
   - Explique abordagens para otimização de performance
   - Defina métricas de performance e SLOs (Service Level Objectives)

7. Um ADR sobre "Abordagem para Gerenciamento de Configuração" (ADR-007-gerenciamento-configuracao.md) que:
   - Compare estratégias para armazenamento de configurações (arquivos, banco de dados, serviço)
   - Analise abordagens para configurações específicas por ambiente
   - Detalhe estratégias para secrets management
   - Explique mecanismos para atualização dinâmica de configurações
   - Defina processos para versionamento e auditoria de alterações

8. Um ADR sobre "Estratégia de CI/CD e Deploy" (ADR-008-ci-cd-deploy.md) que:
   - Compare abordagens de deployment (blue-green, canary, rolling, etc.)
   - Analise ferramentas e plataformas de CI/CD consideradas
   - Detalhe estratégias para automação de builds e testes
   - Explique políticas de branching e gerenciamento de versões
   - Defina processos para rollback e mitigação de falhas

9. Um ADR sobre "Abordagem para Testes Automatizados" (ADR-009-testes-automatizados.md) que:
   - Compare diferentes tipos de testes e sua aplicação no projeto
   - Analise ferramentas e frameworks de teste considerados
   - Detalhe estratégias para mocks, stubs e simulações
   - Explique abordagens para testes de integração e end-to-end
   - Defina métricas de cobertura e critérios de qualidade

10. Um ADR sobre "Estratégia de Gestão de Dependências Externas" (ADR-010-dependencias-externas.md) que:
    - Compare abordagens para integração com sistemas de terceiros
    - Analise estratégias para mitigação de riscos de indisponibilidade
    - Detalhe políticas para versionamento de dependências
    - Explique abordagens para substituição e fallback de serviços
    - Defina processos para avaliação de segurança e compliance

Cada ADR deve seguir o formato estruturado:
- Título e Número
- Status (Proposto, Aceito, Depreciado, etc.)
- Contexto (problema sendo resolvido)
- Decisão (solução escolhida)
- Alternativas Consideradas (outras opções)
- Consequências (impactos positivos e negativos)
- Referências (materiais de apoio)

Use linguagem técnica precisa, evite ambiguidades, e inclua exemplos concretos que ilustrem a implementação da decisão quando aplicável.
```

##### Prompt 3: Geração de Documentos de Design Técnico

```
Atue como um Technical Lead sênior especializado em design de sistemas e documentação técnica. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentos detalhados de design técnico que orientarão a implementação.

Por favor, crie os seguintes 5 documentos de design técnico para serem armazenados em '.agent/contexto/arquitetura/design-tecnico/':

1. Um documento de "Especificação de Interfaces de API" (especificacao-interfaces-api.md) que:
   - Defina todas as interfaces de API expostas pelo sistema
   - Documente endpoints, métodos, parâmetros e formatos de resposta
   - Especifique contratos completos usando notação OpenAPI/Swagger
   - Detalhe códigos de status, tratamento de erros e mecanismos de versionamento
   - Inclua exemplos concretos de requisições e respostas para cada operação

2. Um conjunto de "Diagramas de Sequência para Fluxos Críticos" (diagramas-sequencia-fluxos-criticos.md) que:
   - Modele interações completas para 5 fluxos críticos de negócio
   - Represente todos os componentes, serviços e sistemas externos envolvidos
   - Documente sequência exata de chamadas, respostas e processamento assíncrono
   - Identifique pontos de validação, decisão e tratamento de exceções
   - Inclua tempos esperados para operações críticas e timeouts aplicáveis

3. Um "Modelo de Dados Detalhado" (modelo-dados-detalhado.md) que:
   - Defina esquema completo para todas as entidades persistentes
   - Documente relações, cardinalidade e restrições de integridade
   - Especifique tipos de dados, tamanhos, formatos e validações
   - Detalhe índices, particionamento e estratégias de otimização
   - Inclua scripts DDL ou definições declarativas (ex: migrations)

4. Um documento de "Padrões de Design e Convenções" (padroes-design-convencoes.md) que:
   - Defina padrões arquiteturais específicos a serem aplicados consistentemente
   - Documente convenções de nomenclatura para diversos artefatos
   - Especifique padrões para tratamento de erros, logging e rastreabilidade
   - Detalhe abordagens padronizadas para problemas comuns
   - Inclua exemplos de código para implementações de referência

5. Um "Guia de Implementação de Componentes" (guia-implementacao-componentes.md) que:
   - Forneça instruções detalhadas para implementação de cada componente principal
   - Documente dependências, bibliotecas e frameworks a serem utilizados
   - Especifique abordagens para testes unitários, integração e performance
   - Detalhe considerações específicas de ambiente (dev, QA, prod)
   - Inclua checklists de implementação e critérios de aceitação técnicos

Cada documento deve incluir:
- Cabeçalho com propósito, escopo e audiência-alvo
- Conteúdo técnico detalhado com diagramas apropriados
- Exemplos concretos e código de referência quando aplicável
- Referências cruzadas a ADRs e outros documentos relevantes
- Histórico de versões e registro de alterações

Use linguagem técnica precisa, ofereça detalhes suficientes para implementação direta, e garanta consistência entre todos os documentos.
```

##### Prompt 4: Geração de Documentos de Segurança e Privacidade

```
Atue como um Arquiteto de Segurança especializado em segurança de aplicações e privacidade de dados. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre segurança e privacidade que orientará o desenvolvimento seguro.

Por favor, crie os seguintes 5 documentos de segurança e privacidade para serem armazenados em '.agent/contexto/arquitetura/seguranca-privacidade/':

1. Um "Modelo de Ameaças Abrangente" (modelo-ameacas.md) que:
   - Utilize metodologia estruturada (STRIDE, PASTA, etc.)
   - Identifique todas as superfícies de ataque do sistema
   - Documente vetores de ameaça prováveis com classificação de risco (probabilidade x impacto)
   - Mapeie ameaças para componentes específicos da arquitetura
   - Inclua diagramas de fluxo de dados com limites de confiança claramente marcados

2. Um documento de "Estratégias de Mitigação de Segurança" (estrategias-mitigacao.md) que:
   - Defina contramedidas específicas para cada ameaça identificada
   - Documente controles de segurança técnicos e procedurais
   - Especifique abordagens para proteção em camadas (defesa em profundidade)
   - Detalhe implementações recomendadas para autenticação, autorização e auditoria
   - Inclua padrões de codificação segura para prevenir vulnerabilidades comuns (OWASP Top 10)

3. Uma "Análise de Privacidade por Design" (privacidade-design.md) que:
   - Identifique todos os dados pessoais/sensíveis processados pelo sistema
   - Documente ciclo de vida completo de dados sensíveis (coleta, processamento, armazenamento, retenção, exclusão)
   - Avalie necessidade e proporcionalidade para cada categoria de dados
   - Detalhe medidas técnicas para anonimização, pseudonimização e minimização
   - Especifique controles de acesso e estratégias de compartimentalização

4. Uma "Matriz de Conformidade Regulatória" (conformidade-regulatoria.md) que:
   - Identifique todos os requisitos regulatórios aplicáveis (GDPR, LGPD, HIPAA, PCI-DSS, etc.)
   - Mapeie requisitos específicos para controles técnicos e arquiteturais
   - Documente evidências necessárias para demonstrar conformidade
   - Especifique processos para resposta a incidentes e violações
   - Detalhe requisitos de retenção e exclusão de dados

5. Um "Plano de Validação de Segurança" (validacao-seguranca.md) que:
   - Defina estratégia abrangente para testes de segurança
   - Documente abordagens para análise estática, análise dinâmica e testes de penetração
   - Especifique periodicidade e escopo para diferentes tipos de avaliação
   - Detalhe processo para gerenciamento de vulnerabilidades
   - Inclua critérios de aceitação de segurança e gates de verificação

Cada documento deve:
- Iniciar com resumo executivo destinado a stakeholders não-técnicos
- Incluir conteúdo principal técnico com nível de detalhe suficiente para implementação
- Incorporar referências a padrões da indústria (NIST, ISO, OWASP, CIS, etc.)
- Conter matriz de responsabilidades para requisitos identificados
- Incluir métricas para avaliar eficácia das medidas implementadas

Use linguagem precisa, evite jargões desnecessários, e equilibre recomendações de segurança com usabilidade e viabilidade de implementação.
```

##### Prompt 5: Geração de Documentos de Performance e Escalabilidade

```
Atue como um Arquiteto de Performance especializado em sistemas de alta disponibilidade e escalabilidade. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre performance e escalabilidade para garantir que a solução atenda requisitos de carga e crescimento.

Por favor, crie os seguintes 5 documentos relacionados a performance e escalabilidade para serem armazenados em '.agent/contexto/arquitetura/performance-escalabilidade/':

1. Uma "Análise de Capacidade e Modelagem de Carga" (analise-capacidade.md) que:
   - Defina perfis de uso esperados com métricas quantitativas (usuários concorrentes, transações por segundo, etc.)
   - Documente cenários de carga para diferentes condições (típica, pico, extrema)
   - Modele crescimento projetado em horizontes de 1, 3 e 5 anos
   - Especifique requisitos de capacidade para cada componente principal
   - Inclua análise detalhada de gargalos potenciais e pontos de saturação

2. Um documento de "Estratégias de Escalabilidade" (estrategias-escalabilidade.md) que:
   - Compare abordagens de escalabilidade vertical vs. horizontal para cada componente
   - Documente padrões de design para escalabilidade (sharding, particionamento, etc.)
   - Especifique estratégias para balanceamento de carga e distribuição de tráfego
   - Detalhe mecanismos para auto-scaling baseados em métricas específicas
   - Inclua considerações para limites físicos e econômicos de escalabilidade

3. Um documento de "Benchmarks e Metas de Performance" (benchmarks-performance.md) que:
   - Defina SLAs/SLOs específicos para latência, throughput e disponibilidade
   - Documente metodologia detalhada para testes de performance
   - Especifique cenários de benchmark padronizados e reproduzíveis
   - Estabeleça linha de base e metas de performance para operações críticas
   - Inclua estratégia para monitoramento contínuo de indicadores-chave

4. Um "Guia de Otimização de Performance" (otimizacao-performance.md) que:
   - Identifique áreas comuns de ineficiência e técnicas de otimização
   - Documente padrões e anti-padrões de performance específicos para tecnologias utilizadas
   - Forneça estratégias de otimização para diferentes camadas (frontend, backend, dados)
   - Especifique técnicas para caching, compressão e minimização de latência
   - Inclua abordagem para profiling e diagnóstico de problemas de performance

5. Um "Plano de Contingência para Cenários de Alta Carga" (contingencia-alta-carga.md) que:
   - Identifique cenários de carga excepcional e eventos planejados de alto tráfego
   - Documente estratégias de degradação graciosa e priorização de tráfego
   - Especifique mecanismos de throttling, rate limiting e filas de contenção
   - Detalhe procedimentos operacionais para resposta a picos inesperados
   - Inclua estratégias para recuperação e estabilização pós-eventos de sobrecarga

Cada documento deve:
- Começar com resumo executivo dos principais pontos e recomendações
- Incluir métricas quantitativas e critérios de sucesso mensuráveis
- Fornecer evidências e justificativas para recomendações feitas
- Considerar trade-offs entre performance, custo e complexidade
- Incluir diagramas, tabelas e visualizações relevantes

Use linguagem técnica precisa, incorpore referências a padrões e pesquisas relevantes, e garanta que as recomendações sejam práticas e implementáveis considerando as restrições do projeto.
```

##### Prompt 6: Geração de Documentos de Integração e APIs

```
Atue como um Arquiteto de Integração especializado em desenho de APIs e sistemas distribuídos. Estou desenvolvendo um sistema [descrição do sistema] que precisa se integrar com [sistemas externos/internos] e necessito documentação abrangente sobre estratégias de integração e design de APIs.

Por favor, crie os seguintes 5 documentos de integração para armazenamento em '.agent/contexto/arquitetura/integracao/':

1. Um "Mapa de Integrações do Ecossistema" (mapa-integracoes.md) que:
   - Identifique todos os pontos de integração externos e internos
   - Documente o propósito de cada integração e fluxos de dados associados
   - Especifique protocolos, formatos e mecanismos de comunicação para cada ponto
   - Classifique integrações por criticidade, volatilidade e complexidade
   - Inclua diagrama visual do ecossistema completo de integrações

2. Uma "Estratégia de Design de APIs" (estrategia-apis.md) que:
   - Defina princípios de design para APIs (RESTful, GraphQL, gRPC, etc.)
   - Estabeleça convenções de nomenclatura, versionamento e documentação
   - Especifique padrões para modelagem de recursos e operações
   - Documente abordagens para paginação, filtragem, ordenação e pesquisa
   - Defina estratégias para evolução de APIs sem quebrar compatibilidade

3. Um "Guia de Tratamento de Erros e Resiliência" (erros-resiliencia.md) que:
   - Estabeleça taxonomia padronizada de códigos de erro e mensagens
   - Defina padrões para formato de respostas de erro em diferentes protocolos
   - Documente estratégias para retry, circuit breaking e fallback
   - Especifique abordagens para lidar com latência, timeout e indisponibilidade
   - Inclua padrões para logging e rastreabilidade de erros em chamadas distribuídas

4. Uma "Estratégia de Segurança para Integrações" (seguranca-integracoes.md) que:
   - Defina abordagens para autenticação e autorização entre sistemas
   - Documente padrões para proteção de dados em trânsito e em repouso
   - Especifique estratégias para gerenciamento de credenciais e tokens
   - Defina mecanismos para auditoria e rastreabilidade de chamadas entre sistemas
   - Inclua considerações para aplicação de rate limiting e proteção contra abusos

5. Um "Framework de Contratos e Governança de APIs" (contratos-governanca.md) que:
   - Estabeleça processos para definição e manutenção de contratos de API
   - Defina abordagem para testes de contrato e validação de conformidade
   - Documente ciclo de vida de APIs (proposta, desenvolvimento, depreciação)
   - Especifique métricas de qualidade e utilização para APIs
   - Inclua estratégias para documentação, discovery e onboarding de consumidores

Cada documento deve:
- Começar com resumo executivo destacando pontos-chave para stakeholders
- Incluir diagramas ilustrativos e exemplos concretos de implementação
- Considerar tanto aspectos técnicos quanto organizacionais de integrações
- Fornecer recomendações específicas e aplicáveis ao contexto do projeto
- Incluir referências a padrões da indústria e melhores práticas relevantes

Use terminologia precisa, garanta consistência entre todos os documentos, e considere tanto necessidades atuais quanto futuras expansões do ecossistema de integrações.
```

##### Prompt 7: Geração de Documentos de Arquitetura de Dados

```
Atue como um Arquiteto de Dados especializado em modelagem, fluxos e governança de dados. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre a arquitetura de dados que guiará decisões de implementação relacionadas a persistência, transformação e acesso a dados.

Por favor, crie os seguintes 5 documentos de arquitetura de dados para armazenamento em '.agent/contexto/arquitetura/dados/':

1. Um "Modelo Conceitual e Lógico de Dados" (modelo-conceitual-logico.md) que:
   - Defina o modelo conceitual representando entidades de domínio e relacionamentos
   - Documente o modelo lógico com atributos, chaves e cardinalidades
   - Especifique regras de integridade, constraints e invariantes do domínio
   - Inclua diagramas ER ou equivalentes com notação padronizada
   - Mapeie conceitos de domínio para estruturas de dados persistentes

2. Uma "Estratégia de Persistência e Armazenamento" (estrategia-persistencia.md) que:
   - Compare abordagens de armazenamento para diferentes tipos de dados (relacional, NoSQL, time-series, etc.)
   - Documente decisões de particionamento, sharding e distribuição de dados
   - Especifique estratégias para evolução de esquema e migrações
   - Defina políticas de backup, retenção e arquivamento
   - Inclua considerações para performance, escalabilidade e custos

3. Um "Mapa de Fluxos de Dados" (fluxos-dados.md) que:
   - Identifique todos os fluxos de dados principais no sistema
   - Documente fontes, transformações e destinos para cada fluxo
   - Especifique requisitos de latência, confiabilidade e consistência
   - Defina abordagens para processamento (batch, streaming, híbrido)
   - Inclua diagramas de fluxo com volumes esperados e frequência

4. Um "Framework de Qualidade e Governança de Dados" (qualidade-governanca.md) que:
   - Estabeleça métricas e SLAs para qualidade de dados (completude, precisão, consistência)
   - Documente processos para validação, limpeza e correção de dados
   - Especifique estratégias para detecção e resolução de anomalias
   - Defina políticas para metadados, linhagem e rastreabilidade
   - Inclua abordagens para compliance e auditoria de dados

5. Uma "Estratégia de Acesso e Consumo de Dados" (acesso-consumo.md) que:
   - Compare padrões para exposição de dados (APIs, views, data feeds, etc.)
   - Documente abordagens para controle de acesso e segurança de dados
   - Especifique estratégias para caching e otimização de queries
   - Defina padrões para abstração de fonte de dados e independência de armazenamento
   - Inclua considerações para analytics, reporting e acesso por ferramentas externas

Cada documento deve:
- Incluir diagrama conceitual de alto nível seguido por detalhamento técnico
- Apresentar justificativas para decisões arquiteturais relacionadas a dados
- Considerar todo o ciclo de vida dos dados, desde a captura até o arquivamento
- Incorporar considerações sobre escalabilidade, segurança e compliance
- Fornecer exemplos concretos aplicáveis ao contexto do sistema

Use terminologia técnica precisa, garanta alinhamento com os padrões organizacionais existentes, e considere implicações de longo prazo das decisões arquiteturais relacionadas a dados.
```

##### Prompt 8: Geração de Documentos de Arquitetura de Infraestrutura

```
Atue como um Arquiteto de Infraestrutura especializado em plataformas cloud e DevOps. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre a arquitetura de infraestrutura que suportará a aplicação em ambientes de desenvolvimento, homologação e produção.

Por favor, crie os seguintes 5 documentos de arquitetura de infraestrutura para armazenamento em '.agent/contexto/arquitetura/infraestrutura/':

1. Um "Diagrama de Arquitetura de Infraestrutura" (diagrama-infraestrutura.md) que:
   - Ilustre todos os componentes de infraestrutura necessários (compute, storage, network, etc.)
   - Documente topologia de rede, zonas de segurança e fluxos de tráfego
   - Especifique diferentes ambientes (dev, staging, prod) e suas particularidades
   - Identifique componentes gerenciados internamente vs. serviços de terceiros
   - Inclua legendas detalhadas e explicações para cada elemento do diagrama

2. Uma "Estratégia de Infraestrutura como Código" (infraestrutura-como-codigo.md) que:
   - Compare abordagens e ferramentas (Terraform, CloudFormation, Pulumi, etc.)
   - Documente organização do código, modularização e reutilização
   - Especifique estratégias para gerenciamento de estado e locking
   - Defina processo para versionamento, revisão e aplicação de mudanças
   - Inclua padrões para nomeação, tagging e organização de recursos

3. Um "Plano de Capacidade e Dimensionamento" (capacidade-dimensionamento.md) que:
   - Defina requisitos de recursos para cada componente (CPU, memória, armazenamento, etc.)
   - Documente expectativas de carga, picos de utilização e sazonalidades
   - Especifique estratégias de auto-scaling e elasticidade
   - Analise relação custo-benefício de diferentes opções de dimensionamento
   - Inclua projeções de crescimento e plano de evolução da infraestrutura

4. Uma "Estratégia de Resiliência e Recuperação de Desastres" (resiliencia-recuperacao.md) que:
   - Compare abordagens para alta disponibilidade (multi-AZ, multi-região)
   - Documente estratégias de backup, retenção e restauração
   - Especifique objetivos de ponto de recuperação (RPO) e tempo de recuperação (RTO)
   - Defina planos de contingência para diferentes cenários de falha
   - Inclua procedimentos de disaster recovery e testes periódicos

5. Um "Framework de Segurança de Infraestrutura" (seguranca-infraestrutura.md) que:
   - Estabeleça princípios de defesa em profundidade para infraestrutura
   - Documente estratégias para segurança de rede, identidade e acesso
   - Especifique abordagens para proteção de dados em repouso e em trânsito
   - Defina estratégias para detecção de intrusão, logging e auditoria
   - Inclua procedimentos para patch management e gestão de vulnerabilidades

Cada documento deve:
- Começar com visão geral e objetivos claros da estratégia
- Incluir diagramas técnicos utilizando notações padronizadas
- Fornecer justificativas para escolhas arquiteturais com base em requisitos
- Considerar aspectos de custo, operação, manutenção e evolução
- Alinhar-se com melhores práticas da indústria e padrões cloud-native

Use terminologia técnica precisa, considere trade-offs entre diferentes abordagens, e garanta que as recomendações sejam implementáveis e sustentáveis no longo prazo.
```

##### Prompt 9: Geração de Documentos de Arquitetura Frontend

```
Atue como um Arquiteto Frontend especializado em arquiteturas modernas de UI/UX e aplicações web/mobile. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre a arquitetura frontend que guiará decisões de implementação relacionadas às interfaces de usuário.

Por favor, crie os seguintes 5 documentos de arquitetura frontend para armazenamento em '.agent/contexto/arquitetura/frontend/':

1. Uma "Visão Geral da Arquitetura Frontend" (visao-geral-frontend.md) que:
   - Compare padrões arquiteturais considerados (MVC, MVVM, Flux/Redux, etc.)
   - Documente decisão sobre frameworks e bibliotecas principais
   - Especifique abordagem para modularização e componentização
   - Defina estratégia para gerenciamento de estado e fluxo de dados
   - Inclua diagrama de alto nível da arquitetura frontend

2. Uma "Estratégia de Componentes e Design System" (componentes-design-system.md) que:
   - Estabeleça hierarquia de componentes (atômicos, moleculares, etc.)
   - Documente abordagem para construção e documentação de componentes reutilizáveis
   - Especifique padrões para responsividade e adaptabilidade
   - Defina estratégia para theming, variáveis de design e tokens
   - Inclua fluxo de trabalho para desenvolvimento e evolução do design system

3. Um "Framework de Performance Frontend" (performance-frontend.md) que:
   - Defina métricas-chave de performance (Core Web Vitals, etc.)
   - Documente estratégias para otimização de carregamento e renderização
   - Especifique abordagens para code-splitting, lazy-loading e caching
   - Estabeleça limites aceitáveis para diferentes métricas de performance
   - Inclua checklist de performance para desenvolvimento e revisão

4. Uma "Estratégia de Teste Frontend" (teste-frontend.md) que:
   - Compare abordagens para diferentes níveis de teste (unitário, componente, e2e)
   - Documente ferramentas e frameworks recomendados para cada tipo de teste
   - Especifique estratégias para teste de acessibilidade e compatibilidade
   - Defina critérios de cobertura e objetivos de qualidade
   - Inclua padrões para mocks, stubs e testes isolados vs. integrados

5. Um "Guia de Integração com Backend" (integracao-backend.md) que:
   - Defina abordagem para comunicação com APIs (REST, GraphQL, etc.)
   - Documente estratégias para autenticação, autorização e segurança
   - Especifique padrões para tratamento de erros e estados de loading
   - Estabeleça convenções para modelagem de dados no frontend
   - Inclua abordagens para mockar APIs durante desenvolvimento

Cada documento deve:
- Começar com resumo executivo destacando decisões-chave
- Incluir exemplos de código ou pseudocódigo quando relevante
- Considerar implicações de diferentes escolhas arquiteturais
- Abordar tanto aspectos técnicos quanto de experiência do usuário
- Fornecer diretrizes claras e acionáveis para implementação

Use terminologia técnica atual, considere as particularidades de diferentes plataformas (web, mobile, etc.), e garanta que as recomendações sejam alinhadas com as melhores práticas da indústria e objetivos específicos do projeto.
```

##### Prompt 10: Geração de Documentos de Arquitetura de Evolução e Estratégia Técnica

```
Atue como um Arquiteto Estratégico especializado em evolução de sistemas e planejamento técnico de longo prazo. Estou desenvolvendo um sistema [descrição do sistema] e preciso criar documentação abrangente sobre a estratégia de evolução arquitetural que guiará o desenvolvimento futuro e a manutenção de longo prazo.

Por favor, crie os seguintes 5 documentos de evolução arquitetural para armazenamento em '.agent/contexto/arquitetura/evolucao/':

1. Um "Roadmap Técnico Arquitetural" (roadmap-tecnico.md) que:
   - Defina horizontes de evolução (curto, médio e longo prazo)
   - Documente marcos técnicos alinhados com objetivos de negócio
   - Especifique sequência de evoluções arquiteturais planejadas
   - Identifique dependências entre diferentes iniciativas técnicas
   - Inclua timeline visual com marcos, dependências e prioridades

2. Uma "Estratégia de Gerenciamento de Débito Técnico" (gerenciamento-debito-tecnico.md) que:
   - Estabeleça framework para identificação e classificação de débito técnico
   - Documente metodologia para avaliação de impacto e custo de remediação
   - Especifique abordagem para priorização de remediação vs. novas features
   - Defina métricas para monitoramento e redução gradual de débito técnico
   - Inclua diretrizes para prevenção de novo débito técnico

3. Um "Plano de Modernização e Migração" (modernizacao-migracao.md) que:
   - Compare estratégias para modernização (strangler fig, replatforming, refatoração, etc.)
   - Documente abordagens para migração de componentes legados
   - Especifique estratégias para convivência de sistemas novos e antigos
   - Defina critérios para decisões de reconstruir vs. refatorar
   - Inclua frameworks para mitigação de riscos durante transições

4. Uma "Análise de Extensibilidade e Pontos de Flexibilidade" (extensibilidade-flexibilidade.md) que:
   - Identifique áreas do sistema projetadas para extensão futura
   - Documente mecanismos de extensibilidade (plugins, hooks, API, etc.)
   - Especifique estratégias para customização sem modificação de código-base
   - Defina abordagens para versionamento de extensões e interfaces
   - Inclua exemplos de cenários de extensão previstos e não previstos

5. Uma "Estratégia de Experimentação e Inovação Técnica" (experimentacao-inovacao.md) que:
   - Estabeleça framework para avaliação de novas tecnologias e abordagens
   - Documente processo para prototipação e validação técnica
   - Especifique critérios para adoção de inovações na arquitetura principal
   - Defina abordagem para gerenciamento de riscos em experimentações
   - Inclua metodologia para documentação e compartilhamento de aprendizados

Cada documento deve:
- Começar com resumo estratégico para lideranças técnicas e de negócio
- Incluir análise de tendências de mercado e direções tecnológicas relevantes
- Considerar tanto evolução técnica quanto alinhamento com objetivos de negócio
- Fornecer frameworks para tomada de decisão em diferentes cenários futuros
- Balancear visão de longo prazo com passos incrementais acionáveis

Use linguagem que equilibre precisão técnica com clareza estratégica, considere implicações organizacionais das recomendações, e garanta que a documentação forneça direcionamento valioso tanto para decisões imediatas quanto planejamento de longo prazo.
```

O uso sistemático destes prompts durante a fase de design arquitetural possibilita a criação de uma base documental robusta que serve como guia autoritativo para todo o ciclo de desenvolvimento subsequente. Esta abordagem estruturada para documentação arquitetural, potencializada pelo GitHub Copilot, transforma um processo tradicionalmente intensivo e propenso a inconsistências em um sistema eficiente que garante cobertura abrangente de todos os aspectos críticos da arquitetura.

### 4. Planejamento e Criação de Tarefas

A metodologia estruturada para planejamento e decomposição de trabalho transcende abordagens superficiais de criação de tarefas, implementando um framework multidimensional que transforma requisitos, análises de impacto e decisões arquiteturais em unidades de trabalho atômicas, gerenciáveis e rastreáveis. Esta fase emprega técnicas avançadas de engenharia de trabalho para decompor funcionalidades complexas em tarefas discretas com escopo claramente delimitado, dependências explícitas, e critérios de aceitação verificáveis.

Com o suporte do GitHub Copilot, Project Managers e Tech Leads conduzem análises sistemáticas que identificam paralelismos potenciais, caminhos críticos, e distribuições otimizadas de esforço. O processo incorpora perspectivas complementares de diferentes especialistas técnicos para garantir que cada tarefa seja dimensionada apropriadamente, tecnicamente viável, e alinhada tanto com requisitos funcionais quanto com considerações arquiteturais estabelecidas nas fases anteriores.

O resultado é um conjunto abrangente de tarefas bem definidas, cada uma documentada em arquivo individual seguindo o template padronizado localizado em `.agent/templates/tasks/template.md`. Esta documentação forma um contrato técnico para implementação que possibilita monitoramento preciso de progresso, identificação precoce de impedimentos, e adaptações ágeis quando necessário.

A fase culmina na criação de um repositório organizado de arquivos de tarefas na pasta `.agent/tasks`, onde cada tarefa segue rigorosamente a estrutura definida no template:

```markdown
# TASK-{número}: {Título descritivo da tarefa}

## Descrição

Descrição detalhada do que precisa ser implementado, incluindo contexto necessário.

## Categoria

[Frontend | Backend | Infraestrutura | Banco de Dados | Testes | Documentação]

## Estimativa

[Baixa | Média | Alta] - Estimativa aproximada de [X] horas

## Prioridade

[Crítica | Alta | Média | Baixa]

## Dependências

- TASK-{número}: {título da tarefa dependente}
- {Outros recursos ou serviços necessários}

## Requisitos Técnicos

- Lista de requisitos técnicos específicos
- Tecnologias que devem ser utilizadas
- Padrões a serem seguidos

## Critérios de Aceitação

- [ ] Critério 1
- [ ] Critério 2
- [ ] Critério 3

## Referências

- Link para PRD: {link ou caminho}
- Link para ADR: {link ou caminho}
- Outros documentos relevantes

## Notas Adicionais

Informações complementares, contexto, decisões ou considerações importantes.
```

#### 4.1. Elementos Expandidos do Template de Tarefa:

Além da estrutura fundamental definida no template, cada arquivo de tarefa em `.agent/tasks` deve incluir:

##### 4.1.1. Estrutura Fundamental de Cada Tarefa:

- Identificador único (TASK-{número}) e título descritivo que comunica claramente o objetivo
- Descrição detalhada contextualizada com requisitos de negócio relevantes
- Categoria técnica selecionada de opções predefinidas (Frontend, Backend, etc.)
- Estimativa de complexidade (Baixa, Média, Alta) com quantidade aproximada de horas
- Prioridade categorizada (Crítica, Alta, Média, Baixa) baseada em valor de negócio
- Referências explícitas a artefatos de contexto na pasta `.agent/contexto`

##### 4.1.2. Elementos de Rastreabilidade:

- Mapeamento para requisitos no PRD através de links específicos na seção Referências
- Referências a ADRs relevantes que impactam implementação
- Dependências claramente documentadas com identificadores de outras tarefas
- Requisitos externos ou serviços necessários para completar a tarefa

##### 4.1.3. Requisitos de Implementação:

- Especificações técnicas detalhadas na seção Requisitos Técnicos
- Tecnologias específicas que devem ser utilizadas
- Padrões de código e práticas a serem seguidos
- Considerações especiais de implementação documentadas nas Notas Adicionais

##### 4.1.4. Critérios de Qualidade:

- Lista de verificação explícita com critérios de aceitação objetivos e verificáveis
- Requisitos de testes quando aplicáveis
- Métricas de qualidade específicas para validação

#### 4.2. Prompts Otimizados para Planejamento e Criação de Tarefas

O processo de decomposição e documentação de tarefas é significativamente potencializado pelo uso de prompts especializados do GitHub Copilot. A seguir, apresentamos um conjunto abrangente de prompts otimizados para diferentes aspectos do planejamento e criação de tarefas:

##### 1. Prompt para Geração Inicial de Tarefas

Este prompt fundamental transforma requisitos de alto nível em um conjunto inicial de tarefas estruturadas:

```
Atue como um Tech Lead especializado em decomposição de requisitos de software. Preciso transformar o seguinte conjunto de requisitos em 20 tarefas técnicas estruturadas para implementação. As tarefas serão armazenadas em '.agent/tasks/'.

Requisitos do Projeto:
[Descreva aqui os requisitos funcionais e não-funcionais do projeto]

Contexto Técnico:
- Arquitetura: [Descreva a arquitetura do sistema]
- Stack tecnológica: [Liste as principais tecnologias/frameworks]
- Restrições: [Mencione limitações técnicas, de tempo ou recursos]

Para cada tarefa, crie um arquivo separado seguindo exatamente este template:

# TASK-{número}: {Título descritivo da tarefa}

## Descrição
[Descrição detalhada e contextualizada]

## Categoria
[Frontend | Backend | Infraestrutura | Banco de Dados | Testes | Documentação]

## Estimativa
[Baixa | Média | Alta] - Estimativa aproximada de [X] horas

## Prioridade
[Crítica | Alta | Média | Baixa]

## Dependências
- TASK-{número}: {título da tarefa dependente}
- {Outros recursos ou serviços necessários}

## Requisitos Técnicos
- [Lista de requisitos técnicos específicos]
- [Tecnologias que devem ser utilizadas]
- [Padrões a serem seguidos]

## Critérios de Aceitação
- [ ] [Critério 1]
- [ ] [Critério 2]
- [ ] [Critério 3]

## Referências
- Link para PRD: [link ou caminho]
- Link para ADR: [link ou caminho]
- [Outros documentos relevantes]

## Notas Adicionais
[Informações complementares, contexto, decisões ou considerações importantes]

Ao criar estas 20 tarefas, garanta que:
1. Sejam atomicamente implementáveis (preferencialmente 1-2 dias de trabalho)
2. Cubram todo o escopo dos requisitos sem lacunas
3. Identifiquem claramente dependências entre tarefas
4. Sigam uma sequência lógica de implementação
5. Sejam distribuídas entre diferentes categorias técnicas de forma equilibrada
6. Incluam tarefas de testes e documentação
7. Sejam técnicamente específicas, não genéricas
8. Tenham critérios de aceitação verificáveis
```

##### 2. Prompt para Análise de Complexidade de Tarefas Existentes

Este prompt avalia tarefas existentes e refina suas estimativas e classificações de complexidade:

```
Atue como um Analista de Engenharia especializado em estimativa e avaliação de esforço técnico. Preciso que você analise 20 tarefas técnicas existentes em '.agent/tasks/' e refine suas estimativas de complexidade, esforço e risco.

Para cada tarefa, considere:
- Complexidade técnica intrínseca
- Dependências e inter-relações
- Histórico de implementações similares
- Familiaridade da equipe com a tecnologia
- Riscos técnicos e de integração
- Requisitos de qualidade e performance

Para cada tarefa analisada, por favor:

1. Avalie a estimativa atual (Baixa/Média/Alta)
2. Sugira ajustes com justificativa técnica
3. Atribua horas específicas dentro dos seguintes ranges:
   - Baixa: 2-8 horas
   - Média: 8-16 horas
   - Alta: 16-40 horas
4. Identifique fatores de risco específicos
5. Sugira estratégias de mitigação de risco
6. Recomende ajustes na priorização se necessário

Gere um relatório de análise para 20 tarefas, com este formato para cada uma:

## Análise da TASK-{número}: {Título da tarefa}

**Avaliação Atual:**
- Estimativa atual: [Baixa/Média/Alta] - [X] horas
- Prioridade atual: [Crítica/Alta/Média/Baixa]

**Avaliação Refinada:**
- Estimativa recomendada: [Baixa/Média/Alta] - [Y] horas específicas
- Justificativa para ajuste: [Explicação técnica detalhada]
- Prioridade recomendada: [Crítica/Alta/Média/Baixa]
- Razão para mudança de prioridade: [Se aplicável]

**Análise de Risco:**
- Nível de risco: [Baixo/Médio/Alto]
- Fatores de risco específicos:
  - [Fator 1]
  - [Fator 2]
- Estratégias de mitigação recomendadas:
  - [Estratégia 1]
  - [Estratégia 2]

**Recomendações adicionais:**
[Qualquer insight ou recomendação para implementação eficiente]

Após analisar individualmente, forneça uma visão consolidada identificando:
1. Distribuição geral de complexidade (quantas tarefas em cada nível)
2. Caminhos críticos baseados em dependências e complexidade
3. Áreas de maior risco técnico no projeto
4. Recomendações para rebalanceamento de carga de trabalho
5. Sugestão de sequência otimizada de implementação
```

##### 3. Prompt para Decomposição de Tarefas Complexas

Este prompt ajuda a dividir tarefas grandes e complexas em subtarefas gerenciáveis:

```
Atue como um Arquiteto de Software especializado em decomposição de problemas complexos. Identifiquei tarefas de alta complexidade em '.agent/tasks/' que precisam ser divididas em subtarefas mais gerenciáveis para facilitar implementação, tracking e paralelização de trabalho.

Por favor, analise as seguintes tarefas complexas:
[Liste aqui as tarefas complexas com seus IDs e títulos]

Para cada tarefa complexa, decomponha-a em aproximadamente 4-5 subtarefas menores, gerando um total de 20 subtarefas entre todas as tarefas analisadas. Cada subtarefa deve:

1. Ter escopo claramente definido e limitado
2. Representar uma unidade lógica de trabalho
3. Ser individualmente implementável e testável
4. Ter dependências explícitas com outras subtarefas
5. Seguir uma sequência lógica que permita paralelização quando possível

Para cada tarefa complexa original, forneça:
1. Uma análise da complexidade e razões para decomposição
2. Uma visão de como as subtarefas se conectam
3. Um conjunto de 4-5 arquivos de subtarefas completamente definidos

Crie cada subtarefa como um arquivo separado no formato:

# TASK-{novo-número}: {Título descritivo da subtarefa}

## Descrição
[Descrição específica da subtarefa, referenciando a tarefa pai]

## Categoria
[Mesma categoria da tarefa pai]

## Estimativa
[Baixa | Média] - Estimativa aproximada de [X] horas
[Nota: subtarefas devem ter estimativa menor que a tarefa original]

## Prioridade
[Mesma prioridade da tarefa pai, ou ajustada conforme sequência]

## Dependências
- TASK-{número}: [Tarefa pai ou outras subtarefas precedentes]
- [Outras dependências específicas desta subtarefa]

## Requisitos Técnicos
- [Requisitos técnicos específicos para esta subtarefa]
- [Tecnologias específicas para esta parte]
- [Padrões relevantes para esta subtarefa]

## Critérios de Aceitação
- [ ] [Critério específico 1]
- [ ] [Critério específico 2]
- [ ] [Critério específico 3]

## Referências
- Tarefa original: TASK-{número-original}
- [Outras referências relevantes]

## Notas Adicionais
[Relação com outras subtarefas, considerações de integração]

Após decomposição, forneça um diagrama conceitual (textual) mostrando a relação entre a tarefa original e suas subtarefas, incluindo dependências e sequência de implementação.
```

##### 4. Prompt para Mapeamento de Dependências entre Tarefas

Este prompt analisa e otimiza o grafo de dependências entre tarefas:

```
Atue como um Analista de Sistemas especializado em análise de dependências e caminhos críticos. Preciso mapear e otimizar as relações de dependência entre 20 tarefas técnicas existentes em '.agent/tasks/' para identificar caminhos críticos, paralelismos possíveis e sequenciamento ótimo.

Para cada tarefa em '.agent/tasks/', analise:
- Dependências declaradas
- Dependências implícitas não documentadas
- Relações circulares ou problemáticas
- Oportunidades de paralelização
- Gargalos potenciais

Gere a seguinte documentação:

1. Um "Mapa de Dependências" abrangente contendo:
   - Matriz de dependência completa entre as 20 tarefas
   - Identificação do caminho crítico com justificativa
   - Clusters de tarefas que podem ser implementadas em paralelo
   - Identificação de dependências problematicas ou redundantes
   - Recomendações para otimização da sequência de implementação

2. Para cada tarefa que precisa de ajuste, gere uma versão atualizada do arquivo com dependências refinadas no formato:

# TASK-{número}: {Título original da tarefa}

[Conteúdo original mantido]

## Dependências (Atualizadas)
- TASK-{número}: {título da tarefa dependente}
- TASK-{número}: {título da tarefa dependente}
- {Outros recursos ou serviços necessários}

[Restante do conteúdo original mantido]

## Análise de Dependência
- Dependências originais: [Liste as originais]
- Dependências adicionadas: [Liste as novas identificadas]
- Dependências removidas: [Liste as removidas com justificativa]
- Impacto no caminho crítico: [Explique relevância para o sequenciamento geral]

3. Um "Plano de Sequenciamento Otimizado" contendo:
   - Divisão das 20 tarefas em fases claras de implementação
   - Identificação de tarefas que podem ser iniciadas imediatamente
   - Agrupamento de tarefas que deveriam ser implementadas pelo mesmo desenvolvedor
   - Estratégias para mitigar gargalos no caminho crítico
   - Visualização textual do grafo de dependências otimizado

O objetivo final é garantir maior paralelização possível sem criar bloqueios, identificar claramente o caminho crítico do projeto, e otimizar a sequência de implementação para maximum throughput.
```

##### 5. Prompt para Criação de Tarefas de Testes Abrangentes

Este prompt gera tarefas específicas para diferentes níveis e tipos de testes:

```
Atue como um Engenheiro de Qualidade especializado em estratégias de testes para software. Precisamos criar 20 tarefas de teste abrangentes para complementar as tarefas de implementação existentes em '.agent/tasks/'. Estas tarefas devem cobrir múltiplos tipos e níveis de teste para garantir qualidade completa.

Para criar estas tarefas, considere:
- As funcionalidades sendo implementadas nas tarefas existentes
- A arquitetura do sistema conforme documentada em '.agent/contexto/arquitetura/'
- Os riscos técnicos identificados em '.agent/contexto/impacto/riscos/'
- Os requisitos não-funcionais em '.agent/contexto/requisitos/'

Distribua as 20 tarefas de teste entre as seguintes categorias:
- Testes Unitários (4 tarefas)
- Testes de Integração (4 tarefas)
- Testes de API (3 tarefas)
- Testes End-to-End (3 tarefas)
- Testes de Performance (2 tarefas)
- Testes de Segurança (2 tarefas)
- Testes de Acessibilidade (1 tarefa)
- Testes de Resiliência (1 tarefa)

Para cada tarefa de teste, crie um arquivo separado seguindo este formato:

# TASK-{número}: Testes de {tipo específico} para {funcionalidade/componente}

## Descrição
[Descrição detalhada da estratégia de teste, abrangência e objetivos]

## Categoria
Testes

## Estimativa
[Baixa | Média | Alta] - Estimativa aproximada de [X] horas

## Prioridade
[Crítica | Alta | Média | Baixa]

## Dependências
- TASK-{número}: [Tarefa de implementação que precisa ser concluída antes]
- [Outras dependências técnicas para execução dos testes]

## Requisitos Técnicos
- [Frameworks e ferramentas de teste a serem utilizados]
- [Ambientes necessários]
- [Dados ou condições prévias necessárias]
- [Padrões de teste a serem seguidos]

## Critérios de Aceitação
- [ ] [Cobertura mínima de código ou funcionalidade]
- [ ] [Cenários específicos que devem ser testados]
- [ ] [Documentação de testes requerida]
- [ ] [Integração com pipeline de CI/CD]

## Referências
- Tarefas relacionadas: [Lista de TASK-{números} relacionadas]
- [Documentação de funcionalidades]
- [Especificações técnicas relevantes]

## Notas Adicionais
[Estratégias específicas de teste, considerações sobre dados de teste, mocking, etc.]

Garanta que cada tarefa de teste:
1. Tenha escopo claro e focado em um tipo específico de teste
2. Esteja vinculada a tarefas de implementação específicas
3. Tenha critérios de aceitação mensuráveis e verificáveis
4. Inclua requisitos técnicos detalhados para implementação dos testes
5. Considere edge cases e cenários de exceção importantes
6. Siga melhores práticas da indústria para cada tipo de teste
```

##### 6. Prompt para Criação de Tarefas de Refatoração e Dívida Técnica

Este prompt identifica e documenta tarefas relacionadas à melhoria da base de código existente:

```
Atue como um Arquiteto de Software especializado em refatoração e gestão de dívida técnica. Precisamos criar 20 tarefas específicas para abordar dívida técnica, melhorar qualidade de código e refatorar componentes existentes em nosso sistema. As tarefas serão armazenadas em '.agent/tasks/refatoracao/'.

Considere as seguintes categorias de dívida técnica e oportunidades de refatoração:
- Simplicidade e clareza de código
- Duplicação e redundância
- Desempenho e otimização
- Testabilidade e cobertura
- Modularidade e coesão
- Atualização de dependências
- Padrões arquiteturais inconsistentes
- Segurança e vulnerabilidades
- Documentação técnica

Para cada categoria, crie aproximadamente 2-3 tarefas específicas, totalizando 20 tarefas. Cada tarefa deve:

1. Abordar um aspecto específico de dívida técnica
2. Ter escopo claramente delimitado
3. Apresentar benefícios técnicos quantificáveis
4. Incluir estratégia clara de implementação e validação
5. Considerar riscos de regressão e estratégias de mitigação

Para cada tarefa, crie um arquivo seguindo este formato:

# TASK-{número}: Refatoração de {componente/aspecto específico}

## Descrição
[Descrição detalhada da dívida técnica ou problema atual]
[Impacto técnico negativo da situação atual]
[Descrição da abordagem de refatoração proposta]

## Categoria
Refatoração

## Estimativa
[Baixa | Média | Alta] - Estimativa aproximada de [X] horas

## Prioridade
[Crítica | Alta | Média | Baixa]

## Dependências
- [Componentes ou módulos afetados]
- [Tarefas técnicas relacionadas]

## Requisitos Técnicos
- [Padrões e práticas a serem aplicados]
- [Ferramentas ou bibliotecas necessárias]
- [Métricas técnicas a serem melhoradas]

## Critérios de Aceitação
- [ ] [Melhoria específica e mensurável 1]
- [ ] [Melhoria específica e mensurável 2]
- [ ] [Testes que validam a refatoração sem regressões]
- [ ] [Documentação atualizada conforme necessário]

## Referências
- [Código ou componentes específicos a serem refatorados]
- [ADRs ou padrões arquiteturais relevantes]
- [Melhores práticas da indústria aplicáveis]

## Benefícios Técnicos
- [Benefício específico 1: melhoria quantificável quando possível]
- [Benefício específico 2: melhoria quantificável quando possível]
- [Impacto em manutenibilidade, performance, segurança, etc.]

## Estratégia de Implementação
[Abordagem de refatoração passo a passo]
[Estratégia para testes e validação]
[Abordagem para minimizar riscos de regressão]

Inclua uma análise consolidada que priorize estas 20 tarefas de refatoração por:
1. Relação custo-benefício (value/effort)
2. Risco de não implementação
3. Impacto técnico a longo prazo
4. Viabilidade técnica
```

##### 7. Prompt para Criação de Tarefas de Documentação Técnica

Este prompt gera tarefas específicas para desenvolvimento de documentação técnica abrangente:

```
Atue como um Technical Writer especializado em documentação para equipes de desenvolvimento. Precisamos criar 20 tarefas específicas para desenvolvimento de documentação técnica abrangente para nosso sistema. As tarefas serão armazenadas em '.agent/tasks/documentacao/'.

A documentação deve cobrir diferentes aspectos e ser direcionada a múltiplas audiências:
- Desenvolvedores contribuindo para o projeto
- Equipes de operações que mantêm o sistema
- Integradores que consomem nossas APIs
- Equipes de suporte que resolvem problemas
- Novos membros da equipe em processo de onboarding

Distribua as 20 tarefas entre as seguintes categorias:
- Documentação de Arquitetura (4 tarefas)
- Documentação de APIs (4 tarefas)
- Guias de Desenvolvimento (4 tarefas)
- Runbooks Operacionais (3 tarefas)
- Guias de Troubleshooting (3 tarefas)
- Documentação de Onboarding (2 tarefas)

Para cada tarefa, crie um arquivo seguindo este formato:

# TASK-{número}: Documentação de {aspecto específico}

## Descrição
[Descrição detalhada do tipo de documentação a ser produzida]
[Audiência-alvo e seus requisitos informacionais]
[Objetivos específicos desta documentação]

## Categoria
Documentação

## Estimativa
[Baixa | Média | Alta] - Estimativa aproximada de [X] horas

## Prioridade
[Crítica | Alta | Média | Baixa]

## Dependências
- [Componentes ou módulos que precisam estar implementados]
- [Outras documentações que são pré-requisitos]
- [Informações ou recursos necessários]

## Requisitos Técnicos
- [Formato de documentação (Markdown, API spec, diagramas)]
- [Ferramentas a serem utilizadas (Swagger, PlantUML, etc.)]
- [Padrões de documentação a serem seguidos]
- [Requisitos de acessibilidade ou localização]

## Critérios de Aceitação
- [ ] [Tópicos ou seções que devem ser incluídos]
- [ ] [Exemplos ou casos de uso documentados]
- [ ] [Diagramas ou ilustrações necessários]
- [ ] [Revisão técnica por especialistas no assunto]
- [ ] [Validação com representantes da audiência-alvo]

## Referências
- [Código ou funcionalidades a serem documentadas]
- [Documentação existente relacionada]
- [Padrões de documentação da indústria]

## Entregáveis Específicos
- [Lista de artefatos de documentação a serem produzidos]
- [Localização no repositório onde serão armazenados]
- [Formatos de entrega (HTML, PDF, docs interativos)]

## Abordagem Recomendada
[Metodologia para coleta de informações]
[Técnicas de documentação aplicáveis]
[Sugestões para validação de qualidade e completude]

Garanta que cada tarefa de documentação:
1. Tenha foco claro e audiência bem definida
2. Esteja vinculada a componentes técnicos específicos
3. Inclua orientações sobre formato, estilo e conteúdo
4. Tenha critérios de aceitação relacionados à qualidade e completude
5. Considere manutenibilidade e processo de atualização
```

##### 8. Prompt para Análise e Balanceamento de Portfólio de Tarefas

Este prompt avalia o conjunto completo de tarefas para garantir cobertura e equilíbrio:

```
Atue como um Gerente de Projetos Técnicos com especialização em gerenciamento de portfólio de tarefas. Precisamos analisar o conjunto completo de tarefas em '.agent/tasks/' para garantir equilíbrio, cobertura e alinhamento com objetivos estratégicos.

Realize uma análise abrangente das tarefas existentes e identifique lacunas onde precisamos criar tarefas adicionais. Ao final, devemos ter um conjunto otimizado de 20 tarefas bem balanceadas.

Para cada tarefa existente, analise:
- Alinhamento com requisitos e objetivos do projeto
- Clareza e especificidade de escopo
- Qualidade dos critérios de aceitação
- Adequação da estimativa e prioridade
- Integridade das dependências listadas

Em seguida, analise o portfólio completo para identificar:
1. Distribuição entre categorias técnicas (frontend, backend, etc.)
2. Balanceamento entre tarefas funcionais e não-funcionais
3. Cobertura de requisitos críticos de negócio
4. Distribuição de níveis de complexidade
5. Cobertura de aspectos de qualidade e operacionais

Gere um "Relatório de Análise de Portfólio de Tarefas" contendo:

## Análise de Equilíbrio do Portfólio
- Distribuição por categoria: [Tabela com contagem por categoria]
- Distribuição por prioridade: [Tabela com contagem por prioridade]
- Distribuição por complexidade: [Tabela com contagem por estimativa]
- Cobertura de requisitos: [Análise de requisitos cobertos vs. não cobertos]
- Áreas de super-representação: [Categorias com excesso de tarefas]
- Áreas de sub-representação: [Categorias com escassez de tarefas]

## Tarefas Recomendadas para Adição
[Para cada lacuna identificada, crie nova tarefa no formato padrão]

## Tarefas Recomendadas para Ajuste
[Para cada tarefa existente que precisa ser modificada, forneça recomendações específicas]

## Tarefas Recomendadas para Remoção ou Consolidação
[Para tarefas redundantes ou fragmentadas, forneça justificativa e sugestão]

## Recomendações de Sequenciamento Estratégico
- Fase 1 (Fundacional): [Tarefas recomendadas para início]
- Fase 2 (Construção): [Próximo conjunto de tarefas]
- Fase 3 (Refinamento): [Tarefas finais]

## Métricas de Qualidade do Portfólio
- Cobertura de requisitos: [Porcentagem de requisitos cobertos]
- Índice de clareza: [Avaliação da especificidade das tarefas]
- Índice de testabilidade: [Avaliação da qualidade dos critérios de aceitação]
- Índice de rastreabilidade: [Avaliação da qualidade das referências]

Crie as novas tarefas necessárias para completar o portfólio otimizado de 20 tarefas, usando o template padrão e mantendo consistência com as tarefas existentes.
```

Estes prompts otimizados, quando aplicados sequencialmente, transformam o processo de planejamento e criação de tarefas em um sistema estruturado e abrangente que:

1. Cria tarefas iniciais bem fundamentadas
2. Analisa e refina sua complexidade e estimativas
3. Decompõe tarefas complexas em unidades gerenciáveis
4. Otimiza dependências e sequenciamento
5. Garante cobertura de testes abrangente
6. Endereça dívida técnica sistematicamente
7. Documenta conhecimento técnico essencial
8. Balanceia o portfólio completo de tarefas

O resultado é um repositório abrangente de tarefas em `.agent/tasks/` que forma uma base sólida para implementação eficiente, monitoramento preciso, e adaptação ágil durante todo o ciclo de desenvolvimento.

### 5. Estratégia de Testes e Padrões de Código

A metodologia estruturada para garantia de qualidade transcende abordagens convencionais reativas, implementando um framework multidimensional que posiciona qualidade como um pilar arquitetural desde as fases iniciais. Esta fase aplica princípios avançados de engenharia de qualidade para criar fundamentos sólidos e consistentes que guiam todo o desenvolvimento subsequente, estabelecendo tanto processos de verificação quanto convenções codificadas de implementação.

Com o suporte do GitHub Copilot, arquitetos de qualidade e desenvolvedores formulam estratégias abrangentes que antecipam desafios e estabelecem salvaguardas sistemáticas. O processo incorpora perspectivas complementares de Especialistas em Automação de Qualidade, Tech Leads, e especialistas em domínios específicos que colaboram para construir um ecossistema integrado de qualidade que permeia todas as fases do desenvolvimento.

O resultado é uma infraestrutura preventiva de qualidade que detecta e elimina problemas potenciais precocemente, reduzindo significativamente o custo de correções tardias enquanto acelera a entrega através de maior previsibilidade e confiabilidade. Esta abordagem estabelece um equilíbrio refinado entre velocidade e excelência técnica, permitindo inovação ágil dentro de parâmetros controlados de qualidade.

A fase culmina na criação de artefatos estruturados de qualidade, organizados hierarquicamente na pasta `.agent/padroes-codigo`:

#### 5.1. Documentos de Padrões de Código:

- Guias de Estilo específicos por linguagem com regras de formatação, nomenclatura e organização
- Catálogos de Padrões Arquiteturais documentando estruturas recomendadas para diferentes componentes
- Bibliotecas de Design Patterns com exemplos concretos de implementação e contextos de aplicação
- Matrizes de Anti-Padrões identificando práticas problemáticas comuns e suas alternativas recomendadas

#### 5.2. Documentos de Estratégia de Teste:

- Plano Mestre de Teste detalhando abordagens, responsabilidades e critérios de cobertura
- Frameworks de Teste Unitário com convenções, mocks padronizados e estruturas comuns
- Especificações de Teste de Integração definindo fronteiras de componentes e contratos de interface
- Arquitetura de Teste End-to-End mapeando fluxos críticos e cenários de validação

#### 5.3. Artefatos de Automação e Qualidade:

- Configurações de Linters e Analisadores Estáticos customizados para o contexto do projeto
- Definições de Quality Gates estabelecendo critérios objetivos para progressão de código
- Dashboards de Qualidade com visualizações de métricas-chave e tendências
- Templates de Test Case para diferentes tipos de funcionalidade

#### 5.4. Documentos de Governança de Qualidade:

- Matriz de Responsabilidades de Qualidade definindo papéis e accountability
- Processos de Revisão de Qualidade com checklists específicos por domínio
- Políticas de Refatoração e Gestão de Débito Técnico
- Estratégias de Debugging e Resolução de Problemas

#### 5.5. Documentos de Especialização de Qualidade:

- Guias de Testes de Segurança baseados em OWASP e padrões específicos da indústria
- Estratégias de Teste de Performance com definição de benchmarks e condições de carga
- Frameworks de Validação de Acessibilidade seguindo WCAG e melhores práticas
- Padrões de Internacionalização e Localização para garantir adaptabilidade global

#### 5.6. Prompts Otimizados para Geração de Padrões de Código

##### Prompt 1: Geração de Padrões de Código para Next.js (App Router)

```
Atue como um Arquiteto Frontend especialista em Next.js com App Router. Preciso estabelecer padrões de código consistentes para um projeto Next.js moderno utilizando TypeScript, TailwindCSS, Zod, React Hook Form, Server Actions e componentes do shadcn/ui.

Por favor, crie 10 arquivos de padrões de código detalhados que serão armazenados em '.agent/padroes-codigo/frontend/nextjs/'. Para cada arquivo:

1. Use nomes descritivos como 'server-actions-pattern.md', 'form-validation-pattern.md', etc.
2. Inclua explicação clara do padrão
3. Forneça exemplos de código completos e reutilizáveis
4. Explique quando e por que aplicar o padrão
5. Inclua anti-padrões a serem evitados

Crie especificamente os seguintes arquivos:

1. 'estrutura-diretorio.md' - Padrão para organização de diretórios em um projeto Next.js com App Router
2. 'server-components.md' - Melhores práticas para Server Components, incluindo fetching de dados
3. 'client-components.md' - Padrões para Client Components e interatividade
4. 'server-actions.md' - Padrões para implementação de Server Actions seguros e eficientes
5. 'form-validation.md' - Integração de Zod com React Hook Form para validação de formulários
6. 'data-fetching.md' - Estratégias de fetching de dados, caching e revalidação
7. 'rotas-e-middlewares.md' - Organização de rotas, middlewares e interceptação
8. 'shadcn-ui-customizacao.md' - Padrões para estender e customizar componentes do shadcn/ui
9. 'error-handling.md' - Abordagem consistente para tratamento de erros em diferentes contextos
10. 'performance-optimizacao.md' - Padrões para otimizar performance, incluindo lazy loading e bundle splitting

Cada arquivo deve ser detalhado, com exemplos de código TypeScript completos e seguir as melhores práticas atuais (2023-2024) para Next.js com App Router. Inclua configurações recomendadas de ESLint e considerações de tipagem TypeScript.
```

##### Prompt 2: Geração de Padrões de Código para React.js

```
Atue como um Tech Lead especialista em React.js moderno. Preciso estabelecer padrões de código consistentes para um projeto React.js utilizando TypeScript, TailwindCSS, Zod, e práticas atuais de desenvolvimento.

Por favor, crie 10 arquivos de padrões de código detalhados que serão armazenados em '.agent/padroes-codigo/frontend/reactjs/'. Para cada arquivo:

1. Use nomes descritivos e significativos
2. Inclua propósito e benefícios do padrão
3. Forneça exemplos de código implementáveis
4. Explique considerações de performance e manutenção
5. Destaque melhores práticas e anti-padrões

Crie especificamente os seguintes arquivos:

1. 'componentes-estrutura.md' - Estruturação e organização de componentes reutilizáveis
2. 'hooks-customizados.md' - Padrões para criação e uso de hooks customizados
3. 'gerenciamento-estado.md' - Estratégias modernas para gerenciamento de estado (local, global, servidor)
4. 'renderizacao-condicional.md' - Práticas para renderização condicional e evitar problemas comuns
5. 'formularios-validacao.md' - Integração de React Hook Form com Zod para formulários robustos
6. 'performance-memoizacao.md' - Uso apropriado de useMemo, useCallback, e memo
7. 'estilizacao-tailwind.md' - Padrões para uso eficiente do TailwindCSS em React
8. 'typescript-props.md' - Tipagem avançada de props, generics e inferência de tipos
9. 'testes-componentes.md' - Estratégias de teste para componentes React
10. 'fetching-dados.md' - Padrões para requests, cache e status de loading/error

Cada arquivo deve ser detalhado (mínimo de 500 palavras), com exemplos de código TypeScript completos, considerações de acessibilidade e alinhados com as melhores práticas da comunidade React em 2023-2024. Inclua exemplos de testes quando relevante.
```

##### Prompt 3: Geração de Padrões de Código para NestJS com TypeScript

```
Atue como um Arquiteto Backend especialista em NestJS, TypeScript e Prisma ORM. Preciso estabelecer padrões de código consistentes para um projeto NestJS enterprise-grade.

Por favor, crie 10 arquivos de padrões de código detalhados que serão armazenados em '.agent/padroes-codigo/backend/nestjs/'. Para cada arquivo:

1. Use nomes descritivos e técnicos
2. Forneça código de exemplo completo e funcional
3. Explique princípios arquiteturais subjacentes
4. Detalhe trade-offs e considerações
5. Inclua configurações e otimizações recomendadas

Crie especificamente os seguintes arquivos:

1. 'estrutura-modular.md' - Organização de módulos, serviços e controladores seguindo princípios SOLID
2. 'prisma-integration.md' - Integração do Prisma ORM com NestJS, incluindo injeção de dependência
3. 'tratamento-erros.md' - Sistema abrangente de tratamento de erros e exceções
4. 'validacao-dto.md' - Uso de DTOs com class-validator e transformação
5. 'autenticacao-autorizacao.md' - Implementação de autenticação JWT e RBAC (Role-Based Access Control)
6. 'injecao-dependencia.md' - Padrões avançados de injeção de dependência e ciclo de vida
7. 'testes-automatizados.md' - Estratégias de teste unitário, integração e e2e em aplicações NestJS
8. 'middlewares-interceptors.md' - Uso apropriado de middlewares, guards, interceptors e filtros
9. 'performance-optimizacao.md' - Técnicas de otimização de performance e caching
10. 'migracao-transacional.md' - Gestão de migrações e operações transacionais com Prisma

Cada arquivo deve ser didático, completo e seguir as melhores práticas de NestJS e TypeScript. Inclua exemplos de dependências adequadas no package.json, configurações de tsconfig.json e exemplos detalhados de implementação. Enfatize padrões que promovam testabilidade, manutenibilidade e escalabilidade.
```

##### Prompt 4: Geração de Padrões para Prisma ORM

```
Atue como um Especialista em Banco de Dados com foco em Prisma ORM. Preciso estabelecer padrões robustos para uso do Prisma em aplicações TypeScript de produção.

Por favor, crie 10 arquivos de padrões de código detalhados que serão armazenados em '.agent/padroes-codigo/banco-de-dados/prisma/'. Para cada arquivo:

1. Use nomes técnicos precisos
2. Inclua exemplos de schema.prisma relevantes
3. Forneça código TypeScript para operações relacionadas
4. Discuta considerações de performance e escalabilidade
5. Aborde questões de segurança quando aplicável

Crie especificamente os seguintes arquivos:

1. 'modelagem-schema.md' - Melhores práticas para modelagem de dados com schema.prisma
2. 'relacionamentos.md' - Padrões para definir e trabalhar com relacionamentos (1:1, 1:N, N:M)
3. 'migracao-segura.md' - Estratégias para migrações seguras em ambientes de produção
4. 'operacoes-transacionais.md' - Implementação de operações transacionais com Prisma
5. 'consultas-otimizadas.md' - Otimização de consultas, incluindo select específico e includes
6. 'paginacao-filtragem.md' - Padrões para paginação, ordenação e filtragem eficientes
7. 'soft-delete.md' - Implementação de soft delete e gestão de dados históricos
8. 'middleware-extensoes.md' - Uso de middlewares e extensões do Prisma Client
9. 'testes-banco-dados.md' - Estratégias para testes envolvendo banco de dados
10. 'seeds-fixtures.md' - Padrões para seeds e dados de teste

Cada arquivo deve ser abrangente, com exemplos práticos completos que possam ser implementados diretamente. Inclua considerações sobre diferentes bancos de dados (PostgreSQL, MySQL), estratégias de índices, e monitoramento de performance. Aborde também integração com NestJS quando relevante.
```

##### Prompt 5: Geração de Padrões para Testes com TypeScript

```
Atue como um Engenheiro de Qualidade especializado em estratégias de teste para aplicações TypeScript. Preciso estabelecer padrões de testes abrangentes para projetos full-stack usando Next.js e NestJS.

Por favor, crie 10 arquivos de padrões de teste detalhados que serão armazenados em '.agent/padroes-codigo/testes/typescript/'. Para cada arquivo:

1. Use nomes descritivos focados em tipos de teste
2. Forneça exemplos completos e prontos para implementação
3. Explique o propósito e valor do tipo de teste
4. Detalhe configurações necessárias (jest, testing-library, etc.)
5. Inclua exemplos de mocks e stubs quando aplicável

Crie especificamente os seguintes arquivos:

1. 'testes-unitarios-frontend.md' - Testes unitários para componentes React/Next.js
2. 'testes-unitarios-backend.md' - Testes unitários para serviços e controllers NestJS
3. 'testes-integracao-api.md' - Testes de integração para endpoints de API
4. 'testes-e2e-frontend.md' - Testes end-to-end para fluxos de usuário com Cypress ou Playwright
5. 'testes-hooks-react.md' - Estratégias para testar hooks customizados do React
6. 'mocks-services.md' - Abordagens para mocking de serviços e dependências externas
7. 'testes-prisma.md' - Estratégias para testar código que utiliza Prisma ORM
8. 'testes-server-actions.md' - Testes para Server Actions do Next.js
9. 'cobertura-relatorios.md' - Configuração de cobertura de código e relatórios
10. 'testes-ci-pipeline.md' - Integração de testes em pipelines CI/CD

Cada arquivo deve seguir práticas modernas de teste, incluir exemplos de código reutilizáveis e considerar tanto a eficácia quanto a eficiência dos testes. Aborde tópicos como test-driven development (TDD), arranjo-ação-asserção (AAA), e estratégias para escrever testes que resistam a refatorações.
```

##### Prompt 6: Geração de Padrões para Estilização com TailwindCSS

```
Atue como um Designer de UI/UX especializado em TailwindCSS e sistemas de design. Preciso estabelecer padrões de estilização consistentes para aplicações Next.js/React que utilizam TailwindCSS e shadcn/ui.

Por favor, crie 10 arquivos de padrões de estilização detalhados que serão armazenados em '.agent/padroes-codigo/frontend/tailwindcss/'. Para cada arquivo:

1. Use nomes focados em aspectos específicos de estilização
2. Forneça exemplos de código reutilizáveis
3. Explique princípios de design subjacentes
4. Inclua considerações de acessibilidade
5. Forneça variações para diferentes contextos

Crie especificamente os seguintes arquivos:

1. 'sistema-cores.md' - Estratégia para definir e usar um sistema de cores consistente
2. 'tipografia.md' - Hierarquia tipográfica e uso consistente de fontes
3. 'componentes-personalizados.md' - Criação de componentes estilizados reutilizáveis
4. 'layout-responsivo.md' - Padrões para layouts responsivos eficientes
5. 'dark-mode.md' - Implementação robusta de tema claro/escuro
6. 'animacoes-transicoes.md' - Uso apropriado de animações e transições
7. 'extensao-shadcn.md' - Estratégias para estender e personalizar componentes shadcn/ui
8. 'formularios-estilizacao.md' - Estilização consistente de elementos de formulário
9. 'variaveis-css.md' - Uso de variáveis CSS com TailwindCSS
10. 'organizacao-classes.md' - Organização e manutenção de classes Tailwind em projetos grandes

Cada arquivo deve incluir exemplos concretos, explicações claras e seguir as melhores práticas atuais de TailwindCSS. Inclua configurações recomendadas para o arquivo tailwind.config.js e estratégias para manter a consistência visual em toda a aplicação.
```

##### Prompt 7: Geração de Padrões para Segurança em Aplicações Full-Stack

```
Atue como um Especialista em Segurança de Aplicações Web com foco em aplicações TypeScript full-stack. Preciso estabelecer padrões de segurança robustos para aplicações que usam Next.js/React no frontend e NestJS/Prisma no backend.

Por favor, crie 10 arquivos de padrões de segurança detalhados que serão armazenados em '.agent/padroes-codigo/seguranca/typescript/'. Para cada arquivo:

1. Use nomes descritivos focados em aspectos de segurança
2. Explique a vulnerabilidade ou risco de segurança
3. Forneça exemplos de código seguro vs. inseguro
4. Inclua instruções de implementação detalhadas
5. Discuta técnicas de verificação e teste

Crie especificamente os seguintes arquivos:

1. 'autenticacao-jwt.md' - Implementação segura de autenticação JWT
2. 'validacao-entrada.md' - Estratégias robustas para validação de entrada de dados
3. 'protecao-csrf.md' - Prevenção de ataques CSRF em aplicações Next.js
4. 'seguranca-api.md' - Proteção de endpoints NestJS contra abusos
5. 'gerenciamento-sessao.md' - Padrões seguros para gerenciamento de sessão
6. 'armazenamento-senhas.md' - Técnicas seguras para hash e armazenamento de senhas
7. 'prevencao-sql-injection.md' - Prevenção de injeção SQL com Prisma ORM
8. 'cabecalhos-seguranca.md' - Configuração de cabeçalhos HTTP de segurança
9. 'sanitizacao-saida.md' - Sanitização de dados de saída para prevenção de XSS
10. 'auditoria-logging.md' - Implementação de logs de auditoria para segurança

Cada arquivo deve seguir as melhores práticas de segurança atuais, fornecer exemplos concretos de implementação, e considerar o contexto específico das tecnologias mencionadas. Inclua referências a padrões OWASP quando relevante e aborde implicações de performance ao implementar medidas de segurança.
```

##### Prompt 8: Geração de Padrões para Performance e Otimização

```
Atue como um Engenheiro de Performance especializado em aplicações web modernas. Preciso estabelecer padrões de otimização para aplicações Next.js/React no frontend e NestJS/Prisma no backend.

Por favor, crie 10 arquivos de padrões de otimização detalhados que serão armazenados em '.agent/padroes-codigo/performance/'. Para cada arquivo:

1. Use nomes técnicos focados em aspectos de performance
2. Identifique métricas-chave e benchmarks relevantes
3. Forneça implementações otimizadas com exemplos de código
4. Explique o impacto das otimizações com dados quantitativos quando possível
5. Inclua ferramentas e técnicas de medição

Crie especificamente os seguintes arquivos:

1. 'otimizacao-imagens-next.md' - Estratégias para otimização de imagens em Next.js
2. 'code-splitting.md' - Implementação eficiente de code splitting e lazy loading
3. 'caching-frontend.md' - Estratégias de caching no frontend (SWR, React Query)
4. 'caching-backend.md' - Implementação de caching em APIs NestJS
5. 'otimizacao-database.md' - Otimização de consultas Prisma e índices de banco de dados
6. 'server-side-rendering.md' - Uso eficiente de SSR, SSG e ISR em Next.js
7. 'web-vitals-optimizacao.md' - Otimização para Core Web Vitals
8. 'bundlesize-reducao.md' - Técnicas para redução de tamanho de bundle
9. 'api-performance.md' - Padrões para APIs de alto desempenho em NestJS
10. 'monitoramento-performance.md' - Implementação de monitoramento real de performance

Cada arquivo deve ser tecnicamente detalhado, com exemplos práticos e baseados em dados. Inclua configurações recomendadas, ajustes específicos de webpack/compiling e métricas para validar melhorias. Aborde cenários de escala e considerações para diferentes dispositivos e conexões.
```

##### Prompt 9: Análise e Atualização de Padrões Baseados em package.json

```
Atue como um Tech Lead especializado em ecossistemas JavaScript/TypeScript. Preciso analisar um package.json existente e gerar ou atualizar padrões de código que sejam específicos para as tecnologias utilizadas no projeto.

Abaixo está o conteúdo do package.json:

```

[COLE O CONTEÚDO DO PACKAGE.JSON AQUI]

```

Por favor:
1. Analise as dependências e devDependencies
2. Identifique as principais tecnologias e frameworks utilizados
3. Determine as versões específicas e suas implicações
4. Identifique potenciais conflitos ou problemas de compatibilidade

Com base nessa análise, gere 10 arquivos de padrões de código específicos para este conjunto de tecnologias. Os arquivos devem ser organizados em pastas apropriadas seguindo o padrão '.agent/padroes-codigo/{area}/{tecnologia}/'.

Para cada tecnologia principal identificada:
1. Crie padrões que considerem as versões específicas utilizadas
2. Forneça exemplos de código que funcionem com o conjunto exato de dependências
3. Identifique padrões emergentes ou deprecados baseados nas versões
4. Recomende atualizações de dependências quando apropriado
5. Sugira ferramentas de análise e linting específicas para o stack

Além disso, gere um arquivo 'analise-dependencias.md' na raiz de '.agent/padroes-codigo/' que contenha:
1. Uma visão geral do stack tecnológico
2. Recomendações para atualizações de dependências
3. Identificação de dependências desatualizadas ou com vulnerabilidades
4. Sugestões para otimização do package.json
5. Um roadmap de modernização tecnológica se necessário

Certifique-se de que os padrões sejam coerentes entre si e considerem as interações entre diferentes bibliotecas do projeto.
```

##### Prompt 10: Avaliação e Refinamento de Padrões Existentes

```
Atue como um Arquiteto de Software especializado em avaliação de qualidade de código e refatoração. Preciso avaliar um conjunto existente de padrões de código e identificar oportunidades de refinamento e melhoria.

Por favor, analise os padrões de código existentes na pasta '.agent/padroes-codigo/' e:

1. Identifique inconsistências entre diferentes padrões
2. Avalie a atualidade dos padrões em relação às melhores práticas atuais
3. Identifique padrões ausentes que deveriam ser documentados
4. Sugira melhorias em exemplos de código existentes
5. Recomende consolidações onde houver redundância

Gere um relatório abrangente chamado 'avaliacao-padroes-codigo.md' na raiz de '.agent/padroes-codigo/' que contenha:

1. Resumo executivo da avaliação
2. Análise detalhada por área (frontend, backend, etc.)
3. Tabela de classificação de cada padrão existente (atualidade, clareza, aplicabilidade)
4. Recomendações prioritárias para melhoria
5. Plano de ação para atualização dos padrões

Além disso, para cada área principal (frontend, backend, banco-de-dados, testes, segurança), crie um arquivo 'refinamentos-recomendados.md' que detalhe específicamente:

1. Padrões que precisam de atualização urgente (com exemplos concretos de melhorias)
2. Padrões ausentes que deveriam ser criados (com esboço de conteúdo)
3. Padrões que poderiam ser consolidados ou reestruturados
4. Atualizações baseadas em novas features de frameworks ou bibliotecas
5. Melhorias na formatação, exemplos e legibilidade

Garanta que suas avaliações sejam objetivas, baseadas em evidências, e incluam justificativas claras para cada recomendação.
```

##### Prompt 11: Geração de Padrões para Gerenciamento de Estado React/Next.js

```
Atue como um Especialista em Frontend com foco em gerenciamento de estado em aplicações React e Next.js. Preciso estabelecer padrões consistentes para gerenciamento de estado usando abordagens modernas.

Por favor, crie 10 arquivos de padrões de gerenciamento de estado detalhados que serão armazenados em '.agent/padroes-codigo/frontend/gerenciamento-estado/'. Para cada arquivo:

1. Use nomes descritivos específicos para o tipo de gerenciamento de estado
2. Explique quando e por que usar este padrão específico
3. Forneça implementações de exemplo completas
4. Discuta trade-offs, vantagens e desvantagens
5. Inclua considerações de performance e testing

Crie especificamente os seguintes arquivos:

1. 'useState-vs-useReducer.md' - Diretrizes para escolher entre useState e useReducer
2. 'context-api-patterns.md' - Padrões otimizados para uso do Context API
3. 'jotai-implementacao.md' - Padrões para gerenciamento atômico com Jotai
4. 'zustand-store-design.md' - Design de stores com Zustand
5. 'server-state-react-query.md' - Gerenciamento de estado do servidor com TanStack Query
6. 'next-server-components-state.md' - Abordagem para estado em Server Components
7. 'form-state-management.md' - Estratégias para gerenciamento de estado em formulários complexos
8. 'global-vs-local-state.md' - Decisões sobre centralização vs. localização de estado
9. 'estado-derivado.md' - Técnicas para computar e memoizar estado derivado
10. 'reatividade-performance.md' - Otimização de performance com renderizações reativas

Cada arquivo deve apresentar exemplos de código TypeScript completos que possam ser implementados diretamente, incluir discussões sobre contextos específicos de aplicação (e-commerce, dashboards, etc.) e abordar a interoperabilidade entre diferentes soluções de gerenciamento de estado.
```

##### Prompt 12: Geração de Padrões para Acessibilidade na Web

```
Atue como um Especialista em Acessibilidade Web com experiência em React e Next.js. Preciso estabelecer padrões abrangentes de acessibilidade que atendam critérios WCAG 2.1 AA para nossas aplicações.

Por favor, crie 10 arquivos de padrões de acessibilidade detalhados que serão armazenados em '.agent/padroes-codigo/frontend/acessibilidade/'. Para cada arquivo:

1. Use nomes focados em aspectos específicos de acessibilidade
2. Mencione critérios WCAG específicos sendo atendidos
3. Forneça exemplos de implementação acessível vs. inacessível
4. Inclua técnicas de teste e validação
5. Forneça soluções práticas para cenários comuns

Crie especificamente os seguintes arquivos:

1. 'semantica-html.md' - Uso adequado de elementos HTML semânticos e ARIA
2. 'formularios-acessiveis.md' - Design e implementação de formulários acessíveis
3. 'contraste-cores.md' - Garantia de contraste adequado e sistemas de cores acessíveis
4. 'foco-teclado.md' - Gerenciamento de foco e navegação por teclado
5. 'conteudo-dinamico.md' - Tornando atualizações dinâmicas de conteúdo acessíveis
6. 'componentes-interativos.md' - Implementação acessível de modais, menus, etc.
7. 'imagens-midia.md' - Padrões para imagens, vídeos e outros conteúdos de mídia
8. 'testes-acessibilidade.md' - Estratégias de teste de acessibilidade automatizado e manual
9. 'responsivo-acessivel.md' - Considerações de acessibilidade em designs responsivos
10. 'performance-acessibilidade.md' - Interseção entre performance e acessibilidade

Cada arquivo deve ser didático, incluir exemplos concretos com TypeScript e React/Next.js, e fornecer tanto o código quanto explicações contextuais. Inclua considerações específicas para shadcn/ui e outros componentes usados frequentemente.
```

##### Prompt 13: Geração de Padrões para Integração e APIs

```
Atue como um Arquiteto de Integração especializado em design e consumo de APIs RESTful e GraphQL. Preciso estabelecer padrões robustos para integração entre frontend e backend em nosso ecossistema Next.js e NestJS.

Por favor, crie 10 arquivos de padrões de integração detalhados que serão armazenados em '.agent/padroes-codigo/integracao/'. Para cada arquivo:

1. Use nomes técnicos relacionados a integrações e APIs
2. Forneça exemplos de código para ambos os lados (cliente e servidor)
3. Explique considerações de contrato e versionamento
4. Discuta tratamento de erros e resiliência
5. Inclua padrões de autenticação quando relevante

Crie especificamente os seguintes arquivos:

1. 'design-rest-api.md' - Princípios de design para APIs RESTful em NestJS
2. 'graphql-nestjs.md' - Implementação e estruturação de APIs GraphQL em NestJS
3. 'consumo-api-nextjs.md' - Padrões para consumo de APIs em Next.js (App Router)
4. 'tratamento-erros-api.md' - Estratégia consistente para tratamento de erros em APIs
5. 'autenticacao-api.md' - Implementação de autenticação em integrações API
6. 'paginacao-filtragem.md' - Padrões para paginação, ordenação e filtragem em APIs
7. 'cache-invalidacao.md' - Estratégias de cache e invalidação para dados de API
8. 'tipagem-contratos.md' - Compartilhamento de tipos entre frontend e backend
9. 'testes-integracao.md' - Estratégias para testar integrações entre front e back
10. 'resiliencia-circuitbreaker.md' - Implementação de padrões de resiliência para integrações

Cada arquivo deve incluir exemplos completos para ambos os lados da integração, considerar questões de performance, segurança e manutenibilidade, e fornecer implementações que sigam as melhores práticas atuais para TypeScript, Next.js (App Router) e NestJS.
```

##### Prompt 14: Geração de Novos Padrões Baseados em Tendências Tecnológicas

```
Atue como um Technology Evangelist especializado em tendências emergentes para desenvolvimento web full-stack. Preciso identificar e documentar padrões inovadores baseados nas tendências mais recentes (2023-2024) relevantes para nosso stack Next.js/React e NestJS/Prisma.

Por favor, pesquise as tendências mais significativas e crie 10 arquivos de padrões inovadores que serão armazenados em '.agent/padroes-codigo/tendencias/'. Para cada arquivo:

1. Identifique uma tendência tecnológica específica e emergente
2. Explique seu impacto e relevância para nosso stack
3. Forneça implementações práticas com código de exemplo
4. Discuta maturidade e considerações de adoção
5. Apresente casos de uso e benefícios concretos

Crie especificamente arquivos que abordem as seguintes áreas de tendências:

1. 'ia-assistida-desenvolvimento.md' - Integração de IA generativa no workflow de desenvolvimento
2. 'server-components-avancados.md' - Padrões avançados para React Server Components
3. 'edge-computing-nextjs.md' - Implementação de funções edge e middleware em Next.js
4. 'streaming-respostas.md' - Streaming de respostas e renderização progressiva
5. 'micro-frontends.md' - Abordagens para arquitetura de micro-frontends com React
6. 'api-hibridas-graphql-rest.md' - Estratégias para APIs híbridas combinando GraphQL e REST
7. 'web-components-react.md' - Integração de Web Components com React
8. 'observabilidade-frontend.md' - Técnicas modernas para observabilidade no frontend
9. 'web3-integracao.md' - Padrões para integração com tecnologias web3 (se relevante)
10. 'zero-runtime-css.md' - Abordagens CSS com zero ou mínimo runtime overhead

Cada arquivo deve ser forward-looking mas prático, com exemplos concretos de implementação que possam ser adotados em projetos reais. Inclua considerações sobre maturidade das tecnologias, compatibilidade com nosso stack, e estratégias de adoção incremental.
```

##### Prompt 15: Geração de Padrões para Aplicações Multilíngues e Internacionalização

```
Atue como um Especialista em Internacionalização e Localização para aplicações web. Preciso estabelecer padrões robustos para construir aplicações multilíngues usando Next.js/React e NestJS.

Por favor, crie 10 arquivos de padrões de internacionalização detalhados que serão armazenados em '.agent/padroes-codigo/i18n/'. Para cada arquivo:

1. Use nomes relacionados a aspectos específicos de internacionalização
2. Forneça exemplos de implementação para frontend e backend
3. Discuta considerações culturais além de tradução textual
4. Explique estratégias para testes de localização
5. Aborde questões de performance e UX

Crie especificamente os seguintes arquivos:

1. 'nextjs-i18n-app-router.md' - Implementação de i18n em Next.js com App Router
2. 'nestjs-internacionalizacao.md' - Estratégias para API multilíngue em NestJS
3. 'traducoes-dinamicas.md' - Gerenciamento de conteúdo dinâmico multilíngue
4. 'formatos-regionais.md' - Tratamento de datas, números e moedas para diferentes locales
5. 'rtl-suporte.md' - Suporte para línguas Right-to-Left (RTL)
6. 'estrategias-carregamento.md' - Carregamento eficiente de recursos de tradução
7. 'seo-multilingual.md' - Estratégias SEO para sites multilíngues
8. 'testes-i18n.md' - Automação de testes para aplicações internacionalizadas
9. 'fluxos-traducao.md' - Workflows para gerenciamento de traduções e colaboração
10. 'acessibilidade-i18n.md' - Interseção entre internacionalização e acessibilidade

Cada arquivo deve incluir exemplos de código completos, configurações recomendadas (next-i18next, formatjs, etc.), e considerar tanto tradução estática quanto dinâmica. Aborde especificamente questões de performance relacionadas à internacionalização e estratégias para minimizar impacto no bundle size e tempo de carregamento.
```

O uso sistemático destes prompts durante a fase de definição de estratégia de testes e padrões de código possibilita a criação de uma base documental robusta que serve como guia autoritativo para todo o desenvolvimento subsequente. Esta abordagem estruturada, potencializada pelo GitHub Copilot, transforma um processo tradicionalmente ad-hoc em um sistema consistente que garante qualidade desde as fases iniciais, minizando retrabalho e estabelecendo bases sólidas para escalabilidade e manutenção de longo prazo.

### 6. Implementação e Codificação

A fase de implementação representa o ponto onde planejamento, arquitetura e definições se transformam em código funcional através de uma metodologia sistemática potencializada pelo GitHub Copilot. Esta abordagem estruturada maximiza produtividade e qualidade através de um ciclo iterativo claramente definido:

#### 6.1. Preparação do Ambiente de Desenvolvimento

1. O desenvolvedor inicia configurando seu ambiente com todas as referências essenciais:
   - Arquivos de tarefas específicas da `.agent/tasks` que guiarão a implementação atual
   - Documentos arquiteturais e ADRs relevantes da `.agent/contexto/arquitetura`
   - Padrões de código aplicáveis da `.agent/padroes-codigo` para as tecnologias em uso
   - PRD e documentos de requisitos para referência constante
2. Para cada componente a ser implementado, o desenvolvedor seleciona a persona especializada mais adequada ao contexto técnico (Frontend Expert, Backend Developer, Especialista em Performance, etc.)

#### 6.2. Ciclo de Desenvolvimento Assistido

1. O desenvolvedor cria prompts contextualizados para o Copilot que incorporam:
   - Especificações exatas da tarefa atual (copiadas do arquivo de tarefa)
   - Referências a decisões arquiteturais relevantes (citando ADRs específicos)
   - Requisitos de qualidade e padrões aplicáveis
   - Limitações e considerações específicas do projeto
2. Implementação incremental seguindo um ciclo "prompt-avaliação-refinamento":
   - Solicita ao Copilot código inicial com prompt detalhado
   - Avalia criticamente o código gerado contra requisitos e padrões
   - Refina o prompt com feedback específico sobre o que precisa ser ajustado
   - Itera até que o componente atenda completamente os critérios de aceitação
3. Para cada bloco funcional implementado, o desenvolvedor:
   - Adiciona testes unitários correspondentes (solicitando ajuda do Copilot)
   - Implementa tratamento de erros conforme padrões estabelecidos
   - Adiciona documentação inline contextual que explica não apenas o "como", mas o "porquê"
   - Verifica conformidade com requisitos não-funcionais (performance, acessibilidade, segurança)

#### 6.3. Evolução Guiada por Feedback

1. Em pontos predefinidos de verificação, o desenvolvedor:
   - Solicita ao Copilot, usando a persona de Tech Lead ou Revisor de Código, uma análise crítica do código implementado
   - Identifica oportunidades de refatoração e otimização precoce
   - Documenta decisões técnicas significativas tomadas durante a implementação
2. Integração contínua com componentes relacionados:
   - Implementa testes de integração para verificar interações entre componentes
   - Valida que o código implementado funciona corretamente no contexto do sistema maior
   - Atualiza a documentação técnica refletindo a implementação atual

A fase de implementação representa o ponto onde planejamento, arquitetura e definições se transformam em código funcional através de uma metodologia sistemática potencializada pelo GitHub Copilot. Esta abordagem estruturada maximiza produtividade e qualidade através de um ciclo iterativo claramente definido:

##### 6.3.1. Preparação do Ambiente de Desenvolvimento:

1.  O desenvolvedor inicia configurando seu ambiente com todas as referências essenciais:

- Arquivos de tarefas específicas da `.agent/tasks` que guiarão a implementação atual
- Documentos arquiteturais e ADRs relevantes da `.agent/contexto/arquitetura`
- Padrões de código aplicáveis da `.agent/padroes-codigo` para as tecnologias em uso
- PRD e documentos de requisitos para referência constante

2.  Para cada componente a ser implementado, o desenvolvedor seleciona a persona especializada mais adequada ao contexto técnico (Frontend Expert, Backend Developer, Especialista em Performance, etc.)

##### 6.3.2. Ciclo de Desenvolvimento Assistido:

1.  O desenvolvedor cria prompts contextualizados para o Copilot que incorporam:

- Especificações exatas da tarefa atual (copiadas do arquivo de tarefa)
- Referências a decisões arquiteturais relevantes (citando ADRs específicos)
- Requisitos de qualidade e padrões aplicáveis
- Limitações e considerações específicas do projeto

2.  Implementação incremental seguindo um ciclo "prompt-avaliação-refinamento":

- Solicita ao Copilot código inicial com prompt detalhado
- Avalia criticamente o código gerado contra requisitos e padrões
- Refina o prompt com feedback específico sobre o que precisa ser ajustado
- Itera até que o componente atenda completamente os critérios de aceitação

3.  Para cada bloco funcional implementado, o desenvolvedor:

- Adiciona testes unitários correspondentes (solicitando ajuda do Copilot)
- Implementa tratamento de erros conforme padrões estabelecidos
- Adiciona documentação inline contextual que explica não apenas o "como", mas o "porquê"
- Verifica conformidade com requisitos não-funcionais (performance, acessibilidade, segurança)

##### 6.3.3. Evolução Guiada por Feedback:

1.  Em pontos predefinidos de verificação, o desenvolvedor:

- Solicita ao Copilot, usando a persona de Tech Lead ou Revisor de Código, uma análise crítica do código implementado
- Identifica oportunidades de refatoração e otimização precoce
- Documenta decisões técnicas significativas tomadas durante a implementação

2.  Integração contínua com componentes relacionados:

- Implementa testes de integração para verificar interações entre componentes
- Valida que o código implementado funciona corretamente no contexto do sistema maior
- Atualiza a documentação técnica refletindo a implementação atual

#### 6.4. Prompts Otimizados para Implementação e Codificação

##### Prompt 1: Scaffolding Inicial de Componente com Base em Arquitetura e Padrões

```
Atue como um Arquiteto de Software especializado em inicialização de componentes. Estou implementando a TASK-{número} que requer a criação de um novo {tipo de componente} para {funcionalidade}.

Contexto técnico:
- ADR relevante: .agent/contexto/arquitetura/adrs/ADR-{número}-{título}.md
- Padrão arquitetural: .agent/padroes-codigo/{tecnologia}/{padrão-específico}.md
- Requisitos: .agent/contexto/requisitos/matriz-requisitos-funcionais.md (seção {seção-específica})

Por favor, crie o scaffolding inicial completo para este componente, incluindo:
1. Estrutura de diretórios seguindo o padrão definido em .agent/padroes-codigo/{tecnologia}/estrutura-diretorio.md
2. Arquivos base com implementações de esqueleto
3. Interfaces e tipos necessários baseados no modelo de dados em .agent/contexto/arquitetura/dados/modelo-conceitual-logico.md
4. Comentários explicando decisões arquiteturais e pontos de extensão

O componente deve seguir explicitamente os princípios de design documentados em .agent/contexto/arquitetura/visao/manifesto-arquitetural.md e implementar as interfaces definidas em .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md (para o contexto de {contexto-específico}).
```

##### Prompt 2: Implementação Baseada em Requisitos Funcionais

```
Atue como um Desenvolvedor {Frontend/Backend} sênior com expertise em {tecnologia específica}. Estou implementando a TASK-{número}: "{título da tarefa}" que atende ao requisito funcional documentado em .agent/contexto/requisitos/casos-uso.md (caso de uso {ID-caso-uso}).

Referências essenciais:
- Especificação detalhada: .agent/tasks/TASK-{número}.md
- Padrões de código: .agent/padroes-codigo/{tecnologia}/{padrão-relevante}.md
- Fluxo de processo: .agent/contexto/requisitos/fluxos-processo.md (fluxo "{nome-do-fluxo}")
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md (regras {IDs-regras})

Implementações relacionadas:
- Componentes dependentes: {lista de arquivos/componentes}
- APIs consumidas: .agent/contexto/arquitetura/integracao/mapa-integracoes.md (seção {seção-específica})

Por favor, implemente o {componente/função/módulo} que satisfaça os seguintes critérios:
1. Atenda completamente ao caso de uso especificado, incluindo todos os fluxos alternativos
2. Implemente corretamente as regras de negócio aplicáveis
3. Siga o padrão de tratamento de erros definido em .agent/padroes-codigo/{tecnologia}/tratamento-erros.md
4. Utilize os padrões de design especificados em .agent/padroes-codigo/{tecnologia}/padroes-design-convencoes.md
5. Inclua logs apropriados conforme .agent/contexto/arquitetura/adrs/ADR-{número}-observabilidade.md

Considere especificamente os seguintes casos de borda identificados na análise de requisitos:
- {lista de casos de borda}
```

##### Prompt 3: Implementação de Frontend com Foco em Experiência do Usuário

```
Atue como um Especialista Frontend com foco em UX/UI e acessibilidade. Estou implementando a TASK-{número} que envolve a criação de um componente de interface "{nome-do-componente}" conforme especificado nas wireframes em .agent/contexto/design/wireframes-fluxos.md (seção {seção-específica}).

Referências de design e UX:
- Design system: .agent/contexto/design/design-system.md
- Especificações de acessibilidade: .agent/contexto/design/acessibilidade.md
- Requisitos de responsividade: .agent/contexto/design/design-responsivo.md
- Microinterações: .agent/contexto/design/microinteracoes.md

Padrões técnicos a seguir:
- Estrutura de componentes: .agent/padroes-codigo/frontend/{framework}/componentes-estrutura.md
- Gerenciamento de estado: .agent/padroes-codigo/frontend/{framework}/gerenciamento-estado.md
- Estilização: .agent/padroes-codigo/frontend/tailwindcss/sistema-cores.md e tipografia.md

Por favor, implemente este componente de interface que:
1. Siga fielmente as especificações visuais das wireframes
2. Implemente todas as microinterações especificadas para uma experiência fluida
3. Seja completamente acessível conforme WCAG AA (conforme documentado em .agent/padroes-codigo/frontend/acessibilidade/formularios-acessiveis.md)
4. Utilize corretamente o design system para consistência visual
5. Seja responsivo em todas as breakpoints definidas
6. Utilize gerenciamento de estado eficiente conforme o padrão recomendado

Considerações especiais:
- Suporte a modo escuro conforme .agent/padroes-codigo/frontend/tailwindcss/dark-mode.md
- Internacionalização conforme .agent/padroes-codigo/i18n/nextjs-i18n-app-router.md
- Performance de renderização conforme .agent/padroes-codigo/performance/web-vitals-optimizacao.md
```

##### Prompt 4: Implementação de Backend com Foco em Performance e Escalabilidade

```
Atue como um Engenheiro Backend especializado em sistemas de alta performance. Estou implementando a TASK-{número} que envolve o desenvolvimento de um serviço de {funcionalidade} que deve processar {volume} de requisições e manter latência máxima de {valor-latência}.

Referências arquiteturais:
- Especificação de API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md (endpoint {endpoint-específico})
- Modelo de dados: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md (entidades {lista-entidades})
- Requisitos de performance: .agent/contexto/arquitetura/performance-escalabilidade/benchmarks-performance.md
- Estratégia de escalabilidade: .agent/contexto/arquitetura/performance-escalabilidade/estrategias-escalabilidade.md

Padrões técnicos:
- Otimização de queries: .agent/padroes-codigo/banco-de-dados/prisma/consultas-otimizadas.md
- Caching: .agent/padroes-codigo/performance/caching-backend.md
- Tratamento de concorrência: .agent/padroes-codigo/backend/{framework}/operacoes-transacionais.md

Por favor, implemente este serviço backend que:
1. Siga a arquitetura definida no ADR-{número} (.agent/contexto/arquitetura/adrs/ADR-{número}-{título}.md)
2. Otimize queries de banco de dados para máxima eficiência
3. Implemente estratégia de caching apropriada para reduzir carga no banco de dados
4. Utilize processamento assíncrono para operações de longa duração
5. Implemente throttling/rate limiting conforme .agent/padroes-codigo/seguranca/typescript/seguranca-api.md
6. Inclua instrumentação para métricas de performance conforme .agent/contexto/arquitetura/adrs/ADR-{número}-observabilidade.md

Considerações especiais:
- Tratamento de picos de carga conforme .agent/contexto/arquitetura/performance-escalabilidade/contingencia-alta-carga.md
- Resiliência a falhas de sistemas externos conforme .agent/padroes-codigo/integracao/resiliencia-circuitbreaker.md
- Design para eventual consistência conforme necessário
```

##### Prompt 5: Implementação Segura de Autenticação e Autorização

```
Atue como um Especialista em Segurança de Aplicações com foco em autenticação e autorização. Estou implementando a TASK-{número} que envolve a criação de um sistema de {autenticação/autorização} conforme definido em .agent/contexto/arquitetura/adrs/ADR-003-autenticacao-autorizacao.md.

Referências de segurança:
- Modelo de ameaças: .agent/contexto/arquitetura/seguranca-privacidade/modelo-ameacas.md
- Estratégias de mitigação: .agent/contexto/arquitetura/seguranca-privacidade/estrategias-mitigacao.md
- Requisitos de conformidade: .agent/contexto/arquitetura/seguranca-privacidade/conformidade-regulatoria.md
- Análise de privacidade: .agent/contexto/arquitetura/seguranca-privacidade/privacidade-design.md

Padrões técnicos:
- Implementação JWT: .agent/padroes-codigo/seguranca/typescript/autenticacao-jwt.md
- Armazenamento de senhas: .agent/padroes-codigo/seguranca/typescript/armazenamento-senhas.md
- Cabeçalhos de segurança: .agent/padroes-codigo/seguranca/typescript/cabecalhos-seguranca.md

Por favor, implemente este sistema de {autenticação/autorização} que:
1. Siga os padrões de segurança OWASP para autenticação e controle de acesso
2. Implemente corretamente o esquema JWT definido no ADR-003 com todas as claims necessárias
3. Utilize armazenamento seguro de senhas com algoritmos adequados e salt
4. Implemente proteção contra ataques de força bruta e rate limiting
5. Forneça mecanismos de revogação de tokens e gestão de sessão
6. Implemente registro de auditoria para eventos de segurança conforme .agent/padroes-codigo/seguranca/typescript/auditoria-logging.md

Considerações especiais:
- Proteção contra CSRF conforme .agent/padroes-codigo/seguranca/typescript/protecao-csrf.md
- Validação segura de entrada em todas as rotas de autenticação
- Implementação de MFA conforme .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção segurança)
- Gestão de permissões baseada em roles e claims definidas em .agent/contexto/requisitos/matriz-requisitos-funcionais.md
```

##### Prompt 6: Implementação de Testes Unitários Completos

```
Atue como um Engenheiro de Qualidade especializado em testes automatizados. Estou implementando testes unitários para o componente recém-desenvolvido "{nome-do-componente}" que implementa a funcionalidade descrita na TASK-{número}.

Referências de qualidade:
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md
- Critérios de aceitação: .agent/tasks/TASK-{número}.md (seção "Critérios de Aceitação")
- Documentação do componente: {caminho para a documentação ou código do componente}

Padrões de teste:
- Estrutura de testes unitários: .agent/padroes-codigo/testes/typescript/testes-unitarios-{frontend/backend}.md
- Mocking: .agent/padroes-codigo/testes/typescript/mocks-services.md
- Cobertura: .agent/padroes-codigo/testes/typescript/cobertura-relatorios.md

Por favor, implemente um conjunto completo de testes unitários que:
1. Cubra todos os critérios de aceitação da tarefa
2. Teste todos os caminhos de execução do código, incluindo casos de erro
3. Utilize mocks apropriados para isolar o componente de suas dependências
4. Siga padrões de AAA (Arrange-Act-Assert) ou Given-When-Then
5. Verifique comportamentos específicos documentados em .agent/contexto/requisitos/regras-negocio.md (regras {IDs-regras})
6. Atinja no mínimo {percentual}% de cobertura de código (linhas e branches)

Casos de teste essenciais:
- Caminhos felizes para todas as operações principais
- Validação de entradas e tratamento de valores inválidos
- Tratamento de erros e exceções
- Casos de borda e valores limite
- Comportamentos assíncronos e timing (se aplicável)
```

##### Prompt 7: Implementação de Testes de Integração

```
Atue como um Especialista em Testes de Integração. Estou implementando testes de integração para validar a interação entre os componentes desenvolvidos nas tarefas TASK-{número1} e TASK-{número2}, conforme o fluxo de integração documentado em .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md (fluxo "{nome-do-fluxo}").

Referências técnicas:
- Interfaces de integração: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Fluxos de dados: .agent/contexto/arquitetura/dados/fluxos-dados.md
- Contratos de API: .agent/contexto/arquitetura/integracao/contratos-governanca.md

Padrões de teste:
- Framework de testes de integração: .agent/padroes-codigo/testes/typescript/testes-integracao-api.md
- Configuração de ambientes de teste: .agent/padroes-codigo/testes/typescript/testes-prisma.md
- Abordagem para mocks externos: .agent/padroes-codigo/testes/typescript/mocks-services.md

Por favor, implemente testes de integração que:
1. Validem o fluxo completo de dados entre os componentes, seguindo o diagrama de sequência
2. Testem todos os cenários de sucesso e falha documentados
3. Verifiquem a conformidade com contratos de API estabelecidos
4. Utilizem dados de teste apropriados conforme .agent/padroes-codigo/banco-de-dados/prisma/seeds-fixtures.md
5. Incluam asserções para verificar o estado do sistema após cada operação
6. Validem requisitos de performance de integração quando aplicáveis

Considerações especiais:
- Isolamento de testes e limpeza de dados entre execuções
- Simulação de latência e falhas de rede conforme .agent/padroes-codigo/testes/typescript/testes-resiliencia.md
- Validação de consistência de dados em operações transacionais
- Uso de containers ou ambientes isolados para dependências externas
```

##### Prompt 8: Implementação de Otimizações de Performance

```
Atue como um Engenheiro de Performance especializado em otimização de aplicações. Estou implementando melhorias de performance para o componente "{nome-do-componente}" conforme TASK-{número}, que apresenta problemas de desempenho documentados em .agent/contexto/impacto/riscos/avaliacao-performance.md.

Referências técnicas:
- Medidas de performance atual: {métricas ou profile de performance atual}
- Benchmarks alvo: .agent/contexto/arquitetura/performance-escalabilidade/benchmarks-performance.md
- Análise de gargalos: .agent/contexto/impacto/tecnico/capacidade-infraestrutura.md

Padrões de otimização:
- Estratégias para {frontend/backend}: .agent/padroes-codigo/performance/{contexto-específico}.md
- Caching: .agent/padroes-codigo/performance/caching-{frontend/backend}.md
- Otimização de recursos: .agent/padroes-codigo/performance/bundlesize-reducao.md
- Otimização de queries: .agent/padroes-codigo/banco-de-dados/prisma/consultas-otimizadas.md

Por favor, implemente otimizações de performance que:
1. Identifiquem e resolvam os principais gargalos documentados
2. Implementem estratégias de caching apropriadas para o contexto
3. Otimizem o uso de recursos (CPU, memória, rede, I/O de disco)
4. Apliquem lazy loading e code splitting quando aplicável (frontend)
5. Otimizem queries de banco de dados e implementem índices apropriados
6. Reduzam tempos de resposta para atender aos SLAs definidos em .agent/contexto/requisitos/requisitos-nao-funcionais.md

Considerações especiais:
- Mantenha a legibilidade e manutenibilidade do código
- Documente trade-offs de qualquer otimização não-óbvia
- Implemente instrumentação para medição de resultados
- Compare métricas antes e depois para quantificar melhorias
```

##### Prompt 9: Implementação com Responsividade e Acessibilidade

```
Atue como um Especialista em Acessibilidade e Design Responsivo. Estou implementando a TASK-{número} para o componente de interface "{nome-do-componente}" que deve atender aos requisitos WCAG 2.1 nível AA conforme documentado em .agent/contexto/design/acessibilidade.md e ser totalmente responsivo conforme .agent/contexto/design/design-responsivo.md.

Referências de design:
- Wireframes: .agent/contexto/design/wireframes-fluxos.md (seção {seção-específica})
- Design system: .agent/contexto/design/design-system.md
- Especificações de acessibilidade: .agent/contexto/design/acessibilidade.md
- Breakpoints responsivos: .agent/contexto/design/design-responsivo.md

Padrões técnicos:
- Implementação acessível: .agent/padroes-codigo/frontend/acessibilidade/semantica-html.md
- Layout responsivo: .agent/padroes-codigo/frontend/tailwindcss/layout-responsivo.md
- Contraste e cores: .agent/padroes-codigo/frontend/acessibilidade/contraste-cores.md
- Navegação por teclado: .agent/padroes-codigo/frontend/acessibilidade/foco-teclado.md

Por favor, implemente este componente de interface que:
1. Utilize HTML semântico apropriado conforme .agent/padroes-codigo/frontend/acessibilidade/semantica-html.md
2. Implemente navegação completa por teclado com gerenciamento de foco visível
3. Garanta contraste adequado para todos os textos e elementos interativos
4. Seja completamente utilizável em todos os breakpoints definidos (mobile, tablet, desktop)
5. Forneça textos alternativos para elementos não-textuais
6. Utilize corretamente ARIA quando necessário, conforme .agent/padroes-codigo/frontend/acessibilidade/componentes-interativos.md

Considerações especiais:
- Teste com leitores de tela (NVDA, VoiceOver, JAWS)
- Comportamento apropriado em zoom até 200%
- Suporte a modo alto contraste
- Testes em diferentes dispositivos e orientações
```

##### Prompt 10: Implementação de Internacionalização (i18n)

```
Atue como um Especialista em Internacionalização de Software. Estou implementando suporte multi-idioma para o componente "{nome-do-componente}" conforme TASK-{número} e de acordo com os requisitos em .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção internacionalização).

Referências técnicas:
- Estratégia i18n: .agent/contexto/impacto/negocio/impacto-externo.md (seção expansão global)
- Idiomas suportados: {lista de locales}
- Fluxos específicos de localização: .agent/contexto/design/wireframes-fluxos.md (seção multi-idioma)

Padrões de internacionalização:
- Framework i18n: .agent/padroes-codigo/i18n/nextjs-i18n-app-router.md
- Formatos regionais: .agent/padroes-codigo/i18n/formatos-regionais.md
- Suporte RTL: .agent/padroes-codigo/i18n/rtl-suporte.md (se aplicável)
- Carregamento eficiente: .agent/padroes-codigo/i18n/estrategias-carregamento.md

Por favor, implemente o suporte de internacionalização que:
1. Siga o framework i18n definido para a aplicação
2. Extraia todas as strings para arquivos de tradução separados
3. Implemente formatação correta para datas, números e moedas por locale
4. Suporte pluralização e regras gramaticais específicas por idioma
5. Considere diferenças de comprimento de texto entre idiomas no layout
6. Implemente switching de idioma conforme especificado em .agent/contexto/design/wireframes-fluxos.md

Considerações especiais:
- Performance de carregamento com múltiplos idiomas
- Fallback apropriado para traduções ausentes
- Suporte a direção RTL para idiomas como árabe e hebraico, se aplicável
- SEO multi-idioma conforme .agent/padroes-codigo/i18n/seo-multilingual.md
```

##### Prompt 11: Implementação com Tratamento Robusto de Erros

```
Atue como um Engenheiro de Software especializado em resiliência e tratamento de erros. Estou implementando o componente "{nome-do-componente}" que deve seguir os padrões robustos de tratamento de erros conforme TASK-{número} e de acordo com .agent/contexto/arquitetura/integracao/erros-resiliencia.md.

Referências técnicas:
- Estratégia de resiliência: .agent/contexto/arquitetura/integracao/erros-resiliencia.md
- Taxonomia de erros: .agent/contexto/arquitetura/integracao/erros-resiliencia.md (seção taxonomia)
- Requisitos de logging: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md

Padrões de tratamento de erros:
- Padrões gerais: .agent/padroes-codigo/{tecnologia}/tratamento-erros.md
- Resiliência em integrações: .agent/padroes-codigo/integracao/resiliencia-circuitbreaker.md
- Logging de erros: .agent/padroes-codigo/seguranca/typescript/auditoria-logging.md

Por favor, implemente tratamento de erros robusto que:
1. Captura e trata adequadamente diferentes categorias de erros conforme taxonomia
2. Implementa retry com backoff exponencial para falhas transientes
3. Utiliza circuit breaker para falhas persistentes em dependências externas
4. Fornece mensagens de erro amigáveis para o usuário final
5. Realiza logging detalhado com contexto suficiente para diagnóstico
6. Implementa degradação graciosa quando recursos não estão disponíveis

Tratamentos específicos para:
- Erros de validação de entrada
- Timeout em chamadas externas
- Falhas de banco de dados
- Problemas de autenticação/autorização
- Erros inesperados/não categorizados

Garanta que erros sensíveis nunca sejam expostos ao usuário final e que informações de segurança sejam adequadamente sanitizadas nos logs conforme .agent/contexto/seguranca-compliance/privacidade-dados.md.
```

##### Prompt 12: Implementação de Componente de Integração

```
Atue como um Especialista em Integração de Sistemas. Estou implementando um componente que integra com sistemas externos conforme TASK-{número}, seguindo a especificação em .agent/contexto/arquitetura/integracao/mapa-integracoes.md (integração "{nome-da-integração}").

Referências técnicas:
- Especificação da API externa: .agent/contexto/tecnico/apis-externas.md (seção {sistema-específico})
- Fluxos de integração: .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md (fluxo "{nome-do-fluxo}")
- Requisitos de segurança: .agent/contexto/arquitetura/integracao/seguranca-integracoes.md

Padrões de integração:
- Design de cliente API: .agent/padroes-codigo/integracao/consumo-api-nextjs.md ou .agent/padroes-codigo/backend/{framework}/consumo-api.md
- Resiliência: .agent/padroes-codigo/integracao/resiliencia-circuitbreaker.md
- Caching: .agent/padroes-codigo/performance/caching-{frontend/backend}.md
- Autenticação: .agent/padroes-codigo/integracao/autenticacao-api.md

Por favor, implemente este componente de integração que:
1. Siga o design de cliente API apropriado para a tecnologia
2. Implemente autenticação segura conforme especificado
3. Utilize circuit breaker e retries para resiliência
4. Implemente timeout apropriado para chamadas externas
5. Utilize caching eficiente para reduzir chamadas desnecessárias
6. Forneça logs detalhados para debugging de problemas de integração

Considerações especiais:
- Tratamento de erros específicos da API externa
- Validação de resposta para garantir integridade dos dados
- Mapeamento entre modelos externos e internos
- Rastreabilidade de chamadas com request/correlation IDs
- Monitoramento de health do sistema externo
```

##### Prompt 13: Implementação de Feature Flag / Toggle

```
Atue como um Engenheiro DevOps especializado em entrega contínua. Estou implementando o sistema de feature flags para a funcionalidade descrita na TASK-{número}, conforme a estratégia em .agent/contexto/implantacao/artefatos-implantacao-gradual/configuracoes-feature-toggles.md.

Referências técnicas:
- Estratégia de release: .agent/contexto/implantacao/documentos-estrategia/documento-estrategia.md
- Segmentação de usuários: .agent/contexto/implantacao/artefatos-implantacao-gradual/definicao-segmentos-usuarios.md
- Plano de rollout: .agent/contexto/implantacao/artefatos-implantacao-gradual/plano-rollout.md

Padrões técnicos:
- Implementação de toggles: .agent/padroes-codigo/{tecnologia}/feature-toggles.md
- Configuração dinâmica: .agent/padroes-codigo/backend/{framework}/gerenciamento-configuracao.md
- Avaliação de contexto: .agent/padroes-codigo/{frontend/backend}/avaliacao-contexto-toggles.md

Por favor, implemente o sistema de feature flags que:
1. Siga a arquitetura de toggles definida para o projeto
2. Suporte ativação/desativação para diferentes segmentos de usuários
3. Permita configuração em runtime sem necessidade de redeploy
4. Implemente avaliação eficiente sem impacto de performance
5. Integre-se com o sistema de analytics para medição de impacto
6. Facilite testes A/B quando aplicável

Considerações específicas:
- Comportamento de fallback quando a configuração não está disponível
- Limpeza de toggles obsoletos após adoção completa
- Persistência de estado de toggle para consistência de experiência de usuário
- Estratégia para gerenciar toggles em ambientes de desenvolvimento/teste
```

##### Prompt 14: Implementação de Logging e Telemetria

```
Atue como um Especialista em Observabilidade e Monitoramento. Estou implementando logging e telemetria para o componente "{nome-do-componente}" conforme TASK-{número} e seguindo ADR-005-observabilidade.md em .agent/contexto/arquitetura/adrs/.

Referências técnicas:
- Estratégia de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Métricas críticas: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Requisitos de auditoria: .agent/contexto/seguranca-compliance/auditoria-logging.md

Padrões técnicos:
- Estrutura de logs: .agent/padroes-codigo/{tecnologia}/logging-estruturado.md
- Instrumentação de métricas: .agent/padroes-codigo/performance/monitoramento-performance.md
- Distributed tracing: .agent/padroes-codigo/{backend/frontend}/tracing-distribuido.md

Por favor, implemente logging e telemetria que:
1. Utilize formato estruturado de logs conforme padrão definido
2. Capture métricas de performance em pontos críticos do componente
3. Inclua contextualização adequada (request ID, user ID, etc.)
4. Implemente níveis apropriados de logging (debug, info, warn, error)
5. Integre-se com o sistema de distributed tracing
6. Capture métricas de negócio relevantes para a funcionalidade

Considerações específicas:
- Sanitização de dados sensíveis em logs conforme .agent/contexto/seguranca-compliance/privacidade-dados.md
- Volume de logs e impacto em performance/armazenamento
- Correlação entre logs, métricas e traces
- Alertas baseados em thresholds para métricas críticas
```

##### Prompt 15: Implementação de Cache Otimizado

```
Atue como um Especialista em Sistemas Distribuídos com foco em estratégias de caching. Estou implementando uma solução de cache para o componente "{nome-do-componente}" conforme TASK-{número}, seguindo as diretrizes em .agent/contexto/arquitetura/performance-escalabilidade/otimizacao-performance.md e .agent/padroes-codigo/performance/caching-{frontend/backend}.md.

Referências técnicas:
- Estratégia de caching: .agent/padroes-codigo/performance/caching-{frontend/backend}.md
- Padrões de acesso a dados: .agent/contexto/arquitetura/dados/fluxos-dados.md
- Requisitos de consistência: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção performance)

Padrões técnicos:
- Invalidação de cache: .agent/padroes-codigo/integracao/cache-invalidacao.md
- Multi-nível caching: .agent/padroes-codigo/performance/estrategias-multi-nivel.md
- Métricas de eficácia: .agent/padroes-codigo/performance/monitoramento-performance.md

Por favor, implemente uma estratégia de cache que:
1. Utilize os níveis de cache apropriados (memória, distribuído, CDN, etc.)
2. Defina política de expiração baseada na natureza dos dados
3. Implemente estratégia de invalidação eficiente
4. Considere consistência eventual vs. forte conforme requisitos
5. Utilize armazenamento e serialização eficientes
6. Implemente fallback gracioso para falhas de cache

Considerações específicas:
- Cache de dados personalizados por usuário vs. compartilhados
- Estratégia para lidar com "cache stampede" / "thundering herd"
- Segurança e prevenção de cache poisoning
- Monitoramento do hit/miss ratio e eficácia do cache
- Estratégia para warming de cache após deployments
```

##### Prompt 16: Implementação de Formulários Complexos

```
Atue como um Especialista em Desenvolvimento de Formulários. Estou implementando um formulário complexo conforme TASK-{número}, seguindo os requisitos em .agent/contexto/design/wireframes-fluxos.md (seção "{nome-do-formulário}").

Referências técnicas:
- Design do formulário: .agent/contexto/design/wireframes-fluxos.md (seção específica)
- Validações requeridas: .agent/contexto/requisitos/regras-negocio.md (regras {IDs-regras})
- Requisitos de acessibilidade: .agent/contexto/design/acessibilidade.md

Padrões técnicos:
- Estrutura de formulários: .agent/padroes-codigo/frontend/{framework}/formularios-validacao.md
- Gerenciamento de estado: .agent/padroes-codigo/frontend/gerenciamento-estado/form-state-management.md
- Feedback de erro: .agent/padroes-codigo/frontend/acessibilidade/formularios-acessiveis.md
- Persistência de rascunho: .agent/padroes-codigo/frontend/{framework}/persistencia-formularios.md

Por favor, implemente este formulário complexo que:
1. Utilize o React Hook Form com Zod para validação conforme padrão do projeto
2. Implemente validação do lado cliente para feedback instantâneo
3. Também valide no servidor para segurança
4. Forneça feedback de erro acessível e contextual
5. Implemente navegação entre etapas (se for multi-etapa) com persistência de estado
6. Suporte salvamento automático de rascunho quando apropriado
7. Inclua tratamento de submissão com estados de loading e erro

Considerações específicas:
- Campos condicionais baseados em valores de outros campos
- Validações complexas e interdependentes entre campos
- Performance com grande número de campos
- Experiência em dispositivos móveis
- Recuperação de dados em caso de erro de submissão
```

Esta abordagem estruturada para implementação, potencializada pelo GitHub Copilot como parceiro de desenvolvimento, transforma o processo de codificação de uma atividade puramente manual para um diálogo colaborativo homem-máquina onde o desenvolvedor mantém controle estratégico enquanto se beneficia da capacidade do Copilot de gerar, testar e refinar código rapidamente. O resultado é uma implementação mais rápida, consistente e alinhada com os padrões organizacionais e requisitos do projeto.

### 7. Revisão e Refinamento de Código

A metodologia estruturada para revisão e refinamento de código transcende verificações superficiais de conformidade, implementando um framework multidimensional que examina o código através de múltiplas lentes especializadas. Esta fase utiliza técnicas avançadas de análise para identificar não apenas erros sintáticos, mas oportunidades estratégicas de melhoria em segurança, performance, manutenibilidade e aderência a padrões organizacionais.

Com o suporte do GitHub Copilot, revisores conduzem análises sistemáticas que aplicam perspectivas especializadas sequencialmente, examinando o código em camadas progressivas de profundidade e foco. O processo incorpora personas complementares como Tech Leads, Especialistas em Segurança, e Arquitetos de Performance que colaboram para construir uma visão holística da qualidade do código, identificando desde vulnerabilidades críticas até otimizações sutis de experiência do usuário.

O resultado é um ciclo de feedback estruturado que transforma revisões em catalisadores de excelência técnica, documentado através de relatórios detalhados de análise que não apenas apontam problemas, mas oferecem soluções concretas e contextualizadas. Este processo estabelece um equilíbrio entre padronização organizacional e inovação técnica, enquanto promove aprendizado contínuo entre desenvolvedores.

A fase incorpora um processo de revisão em múltiplas camadas, organizado em etapas progressivas:

#### 7.1. Revisão Automatizada Inicial:

1. Análise estática utilizando Copilot para identificar problemas em múltiplas dimensões:

   - Vulnerabilidades de segurança baseadas em padrões OWASP e CWE
   - Problemas de performance como operações ineficientes e gargalos potenciais
   - "Code smells" e desvios dos padrões documentados em `.agent/padroes-codigo`
   - Complexidade ciclomática e manutenibilidade
   - Conformidade com requisitos de acessibilidade

2. Verificação de cobertura de testes para garantir que todos os caminhos críticos estão adequadamente testados

#### 7.2. Revisão Humano-IA Colaborativa:

3. Revisão por personas especializadas:

   - Tech Lead avalia design, arquitetura e aderência às decisões documentadas nos ADRs
   - Especialista em Segurança foca em vulnerabilidades contextuais e fluxos de dados sensíveis
   - Especialista em Performance examina eficiência de algoritmos e otimizações específicas da plataforma
   - Especialista UI/UX verifica questões de usabilidade e consistência de interface

4. Processo iterativo de refinamento:
   - Sugestões específicas para refatoração com exemplos concretos de implementação
   - Feedback contextualizado que explica não apenas o "o quê", mas o "porquê" de cada melhoria
   - Priorização de mudanças baseada em impacto técnico e valor de negócio

#### 7.3. Documentação e Aprendizado:

5. Registro sistemático de padrões de problemas recorrentes para evolução dos padrões de código
6. Criação de snippets reutilizáveis para soluções comuns, armazenados em `.agent/snippets`
7. Atualização de diretrizes de desenvolvimento baseada em insights das revisões

#### 7.4. Prompts Otimizados para Revisão e Refinamento de Código

##### Prompt 1: Revisão Geral de Qualidade de Código e Aderência a Padrões

```
Atue como um Tech Lead sênior realizando uma revisão de código abrangente. Estou revisando a implementação da TASK-{número} que envolve [descrição breve da funcionalidade].

Referências de contexto:
- Descrição detalhada da tarefa: .agent/tasks/TASK-{número}.md
- Padrões de código relevantes: .agent/padroes-codigo/{tecnologia}/{padrões-específicos}.md
- Decisões arquiteturais: .agent/contexto/arquitetura/adrs/ADR-{número}-{título}.md

Aqui está o código para revisão:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise completa que:

1. Verifique a aderência aos padrões definidos em .agent/padroes-codigo/{tecnologia}/, destacando desvios específicos
2. Avalie o alinhamento com as decisões arquiteturais documentadas nos ADRs relevantes
3. Identifique code smells e oportunidades de refatoração, citando padrões específicos do projeto
4. Analise a clareza e legibilidade, considerando as convenções definidas pela equipe
5. Verifique a completude em relação aos critérios de aceitação da TASK-{número}
6. Avalie a modularidade e separação de responsabilidades

Para cada problema identificado:
- Explique por que é uma preocupação, referenciando padrões específicos do projeto
- Classifique a severidade (Crítica, Alta, Média, Baixa)
- Forneça uma sugestão concreta de melhoria com exemplo de código
- Quando aplicável, cite o documento específico em .agent/padroes-codigo/ que contém a recomendação relevante

Conclua com um resumo das 3-5 melhorias mais importantes a serem priorizadas.
```

##### Prompt 2: Revisão Focada em Segurança

```
Atue como um Especialista em Segurança de Aplicações com experiência em identificação de vulnerabilidades em código. Estou revisando a implementação da TASK-{número} que envolve operações sensíveis como [autenticação/manipulação de dados/operações financeiras/etc].

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Modelo de ameaças: .agent/contexto/arquitetura/seguranca-privacidade/modelo-ameacas.md
- Padrões de segurança: .agent/padroes-codigo/seguranca/typescript/{padrões-específicos}.md
- Requisitos de conformidade: .agent/contexto/seguranca-compliance/conformidade-regulatoria.md

Aqui está o código para análise de segurança:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de segurança aprofundada que:

1. Identifique vulnerabilidades específicas baseadas no OWASP Top 10 e outras fontes relevantes
2. Avalie a implementação de controles de segurança conforme definido em .agent/padroes-codigo/seguranca/
3. Verifique o tratamento adequado de dados sensíveis conforme .agent/contexto/seguranca-compliance/privacidade-dados.md
4. Analise a implementação de autenticação/autorização em relação aos padrões definidos
5. Identifique possíveis injeções, XSS, CSRF e outras vulnerabilidades contextuais
6. Avalie a validação de entrada e sanitização de saída
7. Verifique exposição de informações sensíveis em logs, mensagens de erro ou APIs

Para cada vulnerabilidade:
- Descreva o risco em termos de impacto e probabilidade
- Explique o vetor de ataque potencial
- Classifique a severidade segundo o CVSS ou metodologia similar
- Forneça uma correção específica com exemplo de código
- Referencie o padrão de segurança aplicável em .agent/padroes-codigo/seguranca/

Conclua com um resumo do perfil de segurança geral e as mitigações prioritárias.
```

##### Prompt 3: Revisão Focada em Performance

```
Atue como um Engenheiro de Performance especializado em otimização de código. Estou revisando a implementação da TASK-{número} que envolve [operações potencialmente intensivas/renderização complexa/processamento de dados/etc].

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Benchmarks de performance: .agent/contexto/arquitetura/performance-escalabilidade/benchmarks-performance.md
- Padrões de otimização: .agent/padroes-codigo/performance/{contexto-específico}.md
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção performance)

Aqui está o código para análise de performance:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de performance detalhada que:

1. Identifique operações ineficientes, loops desnecessários e gargalos potenciais
2. Avalie a complexidade algorítmica e sugira otimizações quando aplicável
3. Analise o uso de memória, incluindo possíveis vazamentos e alocações excessivas
4. Verifique implementações de caching conforme .agent/padroes-codigo/performance/caching-{frontend/backend}.md
5. Avalie estratégias de carregamento e inicialização, incluindo lazy loading quando apropriado
6. Para código frontend, analise impactos em renderização e reflows
7. Para código backend, examine eficiência de queries e uso de recursos

Para cada problema de performance:
- Quantifique o impacto potencial (quando possível com métricas específicas)
- Explique o comportamento subótimo e por que é problemático
- Sugira otimizações específicas com exemplos de código
- Referencie padrões de performance aplicáveis em .agent/padroes-codigo/performance/
- Considere trade-offs entre legibilidade, manutenibilidade e performance

Conclua com uma avaliação geral da performance esperada em relação aos requisitos não-funcionais e priorização de otimizações com melhor relação custo-benefício.
```

##### Prompt 4: Revisão de Arquitetura e Design

```
Atue como um Arquiteto de Software avaliando decisões de design e arquitetura. Estou revisando a implementação da TASK-{número} que introduz [novo componente/funcionalidade/integração].

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- ADRs relevantes: .agent/contexto/arquitetura/adrs/ADR-{números relevantes}.md
- Visão arquitetural: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Padrões arquiteturais: .agent/padroes-codigo/{tecnologia}/{padrões-arquiteturais}.md

Aqui está o código para análise arquitetural:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise arquitetural que:

1. Avalie a aderência às decisões arquiteturais documentadas nos ADRs relevantes
2. Verifique a aplicação correta dos padrões arquiteturais definidos para o projeto
3. Analise a separação de responsabilidades e aderência a princípios SOLID
4. Avalie a testabilidade da implementação
5. Verifique a extensibilidade e adaptabilidade para requisitos futuros
6. Analise a consistência com outros componentes do sistema
7. Identifique acoplamentos excessivos ou inapropriados

Para cada problema arquitetural:
- Explique por que representa um desvio dos princípios arquiteturais estabelecidos
- Descreva o impacto potencial em manutenibilidade, escalabilidade ou outros atributos de qualidade
- Sugira refatorações específicas com exemplos
- Referencie os princípios ou padrões aplicáveis documentados em .agent/contexto/arquitetura/
- Considere trade-offs entre diferentes abordagens arquiteturais

Conclua com uma avaliação da saúde arquitetural geral da implementação e recomendações para alinhamento com a visão arquitetural do projeto.
```

##### Prompt 5: Revisão de Testes

```
Atue como um Engenheiro de Qualidade especializado em estratégias de teste. Estou revisando os testes implementados para a TASK-{número} que implementa [funcionalidade].

Referências de contexto:
- Descrição da tarefa e critérios de aceitação: .agent/tasks/TASK-{número}.md
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md
- Padrões de teste: .agent/padroes-codigo/testes/typescript/{tipos-de-teste}.md
- Requisitos funcionais: .agent/contexto/requisitos/matriz-requisitos-funcionais.md

Aqui estão os testes e o código implementado para revisão:

```

[TESTES E CÓDIGO A SEREM REVISADOS]

```

Por favor, conduza uma análise abrangente dos testes que:

1. Avalie a cobertura de testes em relação aos critérios de aceitação da tarefa
2. Verifique a implementação de diferentes tipos de testes conforme a estratégia definida (unitários, integração, etc.)
3. Analise a qualidade dos testes (arranjo-ação-asserção, nomenclatura, independência)
4. Identifique casos de borda ou fluxos alternativos não cobertos
5. Avalie o uso apropriado de mocks, stubs e fixtures
6. Verifique a legibilidade e manutenibilidade dos testes
7. Analise a integração com o pipeline de CI/CD

Para cada problema identificado:
- Explique a lacuna de cobertura ou qualidade
- Descreva o risco associado à falta de testes adequados
- Sugira testes específicos adicionais com exemplos de código
- Referencie padrões de teste aplicáveis em .agent/padroes-codigo/testes/
- Quando relevante, mencione requisitos funcionais específicos que podem não estar adequadamente testados

Conclua com uma avaliação geral da estratégia de teste para esta funcionalidade, identificando oportunidades de melhoria prioritárias e comparando com as práticas definidas nos documentos de referência.
```

##### Prompt 6: Revisão de Acessibilidade e UI/UX

```
Atue como um Especialista em Acessibilidade e UX/UI revisando interfaces de usuário. Estou revisando a implementação de interface para a TASK-{número} que implementa [componente/tela/fluxo de usuário].

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Requisitos de acessibilidade: .agent/contexto/design/acessibilidade.md
- Padrões de UI: .agent/padroes-codigo/frontend/acessibilidade/{padrões-específicos}.md
- Design system: .agent/contexto/design/design-system.md
- Wireframes: .agent/contexto/design/wireframes-fluxos.md

Aqui está o código de interface para revisão:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de acessibilidade e UX/UI que:

1. Verifique a conformidade com WCAG 2.1 nível AA, conforme definido em .agent/contexto/design/acessibilidade.md
2. Avalie o uso semântico de HTML e implementação apropriada de ARIA
3. Verifique a navegabilidade por teclado e foco gerenciado adequadamente
4. Analise o contraste de cores e legibilidade conforme padrões estabelecidos
5. Avalie a consistência com o design system definido para o projeto
6. Verifique a responsividade e adaptabilidade para diferentes tamanhos de tela
7. Analise a aderência às wireframes e fluxos documentados

Para cada problema identificado:
- Descreva o impacto na acessibilidade ou experiência do usuário
- Cite o critério WCAG específico ou princípio de UX relevante
- Sugira correções específicas com exemplos de código
- Referencie padrões de acessibilidade aplicáveis em .agent/padroes-codigo/frontend/acessibilidade/
- Quando aplicável, indique como a implementação difere dos wireframes ou design system

Conclua com uma avaliação geral da interface em termos de acessibilidade e usabilidade, destacando melhorias prioritárias e reconhecendo aspectos positivos da implementação.
```

##### Prompt 7: Revisão de Código para Internacionalização

```
Atue como um Especialista em Internacionalização (i18n) e Localização. Estou revisando a implementação da TASK-{número} que deve suportar múltiplos idiomas e configurações regionais.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Requisitos de i18n: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção internacionalização)
- Padrões de i18n: .agent/padroes-codigo/i18n/{padrões-específicos}.md
- Estratégia de tradução: .agent/contexto/design/wireframes-fluxos.md (seção multi-idioma)

Aqui está o código para revisão:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de internacionalização que:

1. Verifique a externalização adequada de strings para arquivos de tradução
2. Avalie o suporte a pluralização e regras gramaticais específicas por idioma
3. Verifique o tratamento de datas, números e moedas por locale
4. Analise o tratamento de textos com direção RTL (árabe, hebraico, etc.) se aplicável
5. Avalie flexibilidade de layout para acomodar diferentes comprimentos de texto
6. Verifique a implementação de switching de idioma conforme especificado
7. Analise considerações de SEO multi-idioma

Para cada problema de internacionalização:
- Explique o impacto em diferentes locales ou cenários linguísticos
- Sugira implementação correta com exemplos de código
- Referencie padrões aplicáveis em .agent/padroes-codigo/i18n/
- Quando relevante, indique requisitos específicos de acessibilidade relacionados a i18n

Conclua com recomendações para garantir uma experiência consistente para usuários de todos os idiomas suportados, destacando melhorias prioritárias.
```

##### Prompt 8: Revisão de Integração e Componentes Interdependentes

```
Atue como um Arquiteto de Integração especializado em interações entre componentes. Estou revisando a implementação da TASK-{número} que integra com outros componentes/sistemas conforme especificado em .agent/contexto/arquitetura/integracao/mapa-integracoes.md.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Mapa de integrações: .agent/contexto/arquitetura/integracao/mapa-integracoes.md
- Fluxos críticos: .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md
- Padrões de integração: .agent/padroes-codigo/integracao/{padrões-específicos}.md
- Dependências: .agent/tasks/TASK-{número}.md (seção Dependências)

Aqui está o código para revisão:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de integração que:

1. Verifique a aderência aos contratos de API definidos em .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
2. Avalie o tratamento de erros e resiliência em integrações conforme .agent/padroes-codigo/integracao/erros-resiliencia.md
3. Analise a gestão de dependências e ordem de inicialização
4. Verifique o uso apropriado de patterns de integração (Circuit Breaker, Retry, etc.)
5. Avalie a implementação de timeouts e handling de latência
6. Verifique a consistência com fluxos de sequência documentados
7. Analise a testabilidade das integrações, incluindo capacidade de mock

Para cada problema de integração:
- Explique o impacto potencial em termos de falhas ou comportamentos inesperados
- Descreva cenários problemáticos específicos que poderiam ocorrer
- Sugira melhorias com exemplos de código
- Referencie padrões de integração aplicáveis em .agent/padroes-codigo/integracao/
- Quando aplicável, indique testes adicionais que deveriam ser implementados

Conclua com uma avaliação da robustez geral da integração e recomendações para aumentar a resiliência e confiabilidade das interações entre componentes.
```

##### Prompt 9: Revisão Pré-PR Abrangente

```
Atue como um Revisor de Código multidisciplinar preparando feedback para um Pull Request. Estou finalizando a implementação da TASK-{número} e preciso de uma revisão abrangente antes de submeter o PR.

Referências de contexto:
- Descrição completa da tarefa: .agent/tasks/TASK-{número}.md
- Critérios de aceitação: .agent/tasks/TASK-{número}.md (seção Critérios de Aceitação)
- Padrões de código: .agent/padroes-codigo/{tecnologia}/*.md
- Quality gates: .agent/contexto/arquitetura/adrs/ADR-{número relevante para qualidade}.md

Aqui está o código completo da implementação:

```

[CÓDIGO COMPLETO A SER REVISADO]

```

Por favor, conduza uma revisão pré-PR abrangente que:

1. Verifique o atendimento a todos os critérios de aceitação da tarefa
2. Avalie a aderência a todos os padrões de código relevantes (qualidade, segurança, performance)
3. Verifique a implementação e cobertura adequada de testes
4. Identifique possíveis regressões ou impactos em outras áreas do sistema
5. Avalie a completude da documentação inline e externa
6. Verifique a necessidade de atualizações em schemas, migrações ou configurações
7. Analise a implementação de logging, métricas e observabilidade
8. Verifique considerações de deployment e compatibilidade com versões anteriores

Para cada problema ou sugestão:
- Priorize por severidade/importância
- Forneça justificativa clara referenciando padrões ou requisitos específicos
- Sugira melhorias concretas com exemplos
- Indique se é um blocker para o PR ou uma sugestão de melhoria futura

Conclua com:
1. Uma avaliação geral da prontidão para o PR (Ready / Needs Work)
2. Um sumário dos pontos positivos da implementação
3. Lista priorizada das correções necessárias antes do PR
4. Sugestões para melhorias que podem ser endereçadas em tickets futuros
```

##### Prompt 10: Revisão Especializada para Refatoração

```
Atue como um Especialista em Refatoração e Design de Código. Estou analisando código existente relacionado à TASK-{número} que precisa ser refatorado para melhorar manutenibilidade, extensibilidade ou performance.

Referências de contexto:
- Descrição da tarefa de refatoração: .agent/tasks/TASK-{número}.md
- Débito técnico identificado: .agent/contexto/arquitetura/evolucao/gerenciamento-debito-tecnico.md
- Padrões ideais: .agent/padroes-codigo/{tecnologia}/{padrões-relevantes}.md
- Histórico de problemas: [referências a issues ou bugs relacionados]

Aqui está o código atual que precisa ser refatorado:

```

[CÓDIGO A SER REFATORADO]

```

Por favor, conduza uma análise focada em refatoração que:

1. Identifique problemas estruturais profundos além de sintomas superficiais
2. Avalie a aplicabilidade de padrões de design que poderiam melhorar a arquitetura
3. Identifique duplicações, acoplamentos excessivos e outras violações de princípios de design
4. Analise oportunidades para melhorar testabilidade e manutenibilidade
5. Verifique áreas de confusão ou complexidade acidental
6. Identifique partes do código que poderiam se beneficiar de maior modularização
7. Avalie oportunidades para aplicar princípios SOLID

Para cada área que precisa de refatoração:
- Explique o problema fundamental e seu impacto a longo prazo
- Proponha uma estratégia de refatoração em etapas gerenciáveis
- Forneça exemplos concretos "antes e depois" para ilustrar as melhorias
- Identifique riscos potenciais no processo de refatoração e como mitigá-los
- Sugira testes que devem ser implementados para validar a refatoração

Conclua com um plano de refatoração estruturado que:
1. Priorize as mudanças por impacto e facilidade de implementação
2. Sugira uma sequência lógica de refatorações que minimize riscos
3. Identifique pontos onde testes adicionais são críticos antes da refatoração
4. Forneça métricas ou indicadores para validar o sucesso da refatoração
```

##### Prompt 11: Revisão de Tratamento de Erros e Resiliência

```
Atue como um Especialista em Resiliência de Sistemas e Tratamento de Erros. Estou revisando a implementação da TASK-{número} com foco específico em como a aplicação lida com falhas, erros e condições excepcionais.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Estratégia de resiliência: .agent/contexto/arquitetura/integracao/erros-resiliencia.md
- Padrões de tratamento de erros: .agent/padroes-codigo/{tecnologia}/tratamento-erros.md
- Requisitos de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md

Aqui está o código para análise:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise detalhada do tratamento de erros que:

1. Identifique todos os pontos onde erros podem ocorrer (chamadas externas, operações de I/O, etc.)
2. Avalie o tratamento de exceções/erros para cada caso possível
3. Verifique se falhas em dependências externas são tratadas adequadamente
4. Analise implementações de circuit breakers, retries, e timeouts
5. Verifique se erros são classificados corretamente (transientes vs. permanentes)
6. Avalie o logging de erros e a capacidade de diagnóstico
7. Verifique a degradação graciosa em caso de falhas parciais do sistema
8. Analise tratamento de erros assíncronos e promessas rejeitadas

Para cada problema identificado:
- Descreva o cenário de falha e seu possível impacto
- Explique como o tratamento atual é inadequado ou incompleto
- Sugira implementação resiliente com exemplos concretos de código
- Referencie padrões específicos em .agent/padroes-codigo/{tecnologia}/tratamento-erros.md
- Quando aplicável, recomende melhorias em telemetria para detecção de problemas

Conclua com uma avaliação da resiliência geral da implementação e recomendações prioritárias para fortalecer o tratamento de erros e capacidade de recuperação.
```

##### Prompt 12: Revisão de Segurança de Dados e Privacidade

```
Atue como um Especialista em Privacidade de Dados e Segurança de Informações. Estou revisando a implementação da TASK-{número} com foco específico em como dados sensíveis são gerenciados, protegidos e processados.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Requisitos de privacidade: .agent/contexto/arquitetura/seguranca-privacidade/privacidade-design.md
- Classificação de dados: .agent/contexto/seguranca-compliance/classificacao-dados.md
- Padrões de segurança: .agent/padroes-codigo/seguranca/typescript/{padrões-específicos}.md
- Requisitos regulatórios: .agent/contexto/seguranca-compliance/conformidade-regulatoria.md

Aqui está o código para análise:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de privacidade e segurança de dados que:

1. Identifique todos os dados sensíveis ou pessoais processados pelo código
2. Avalie a implementação de controles de acesso e princípio do menor privilégio
3. Verifique o uso de criptografia em repouso e em trânsito para dados sensíveis
4. Analise a retenção de dados e conformidade com políticas de exclusão
5. Verifique a sanitização adequada de logs para evitar exposição de dados sensíveis
6. Avalie a implementação de anonymization/pseudonymization quando aplicável
7. Analise conformidade com requisitos regulatórios específicos (GDPR, LGPD, HIPAA, etc.)
8. Verifique a implementação de auditoria para acesso e modificação de dados sensíveis

Para cada problema de privacidade ou segurança de dados:
- Descreva o risco em termos de impacto potencial para indivíduos e organização
- Explique os requisitos regulatórios ou políticas internas relevantes
- Sugira implementação segura com exemplos de código
- Referencie padrões aplicáveis em .agent/padroes-codigo/seguranca/
- Quando aplicável, indique documentação adicional necessária para compliance

Conclua com uma avaliação da maturidade geral de privacidade da implementação e recomendações prioritárias para fortalecer a proteção de dados sensíveis.
```

##### Prompt 13: Revisão de Código Frontend Específica

```
Atue como um Desenvolvedor Frontend Sênior especializado em {React/Next.js/Angular/Vue}. Estou revisando a implementação da TASK-{número} que envolve componentes de interface e interações de usuário.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Wireframes e fluxos: .agent/contexto/design/wireframes-fluxos.md
- Padrões de frontend: .agent/padroes-codigo/frontend/{framework}/{padrões-específicos}.md
- Design system: .agent/contexto/design/design-system.md
- Padrões de gerenciamento de estado: .agent/padroes-codigo/frontend/gerenciamento-estado/{padrões-específicos}.md

Aqui está o código frontend para revisão:

```

[CÓDIGO FRONTEND A SER REVISADO]

```

Por favor, conduza uma análise frontend especializada que:

1. Avalie a implementação de componentes e sua composição
2. Verifique o gerenciamento de estado e fluxo de dados conforme padrões do projeto
3. Analise a performance de renderização e otimizações (memo, useMemo, etc.)
4. Verifique a implementação de efeitos colaterais e ciclo de vida
5. Avalie a organização de código e separação de responsabilidades
6. Verifique a implementação de interações e comportamentos de UI
7. Analise o tratamento de estados de loading, erro e vazios
8. Verifique a consistência com o design system e padrões visuais

Para cada problema identificado:
- Explique o impacto em termos de UX, performance ou manutenibilidade
- Sugira implementação melhorada com exemplos concretos de código
- Referencie padrões específicos em .agent/padroes-codigo/frontend/
- Quando aplicável, indique considerações de acessibilidade relacionadas
- Mencione impactos em testabilidade ou cobertura de testes

Conclua com uma avaliação geral da qualidade do código frontend e recomendações prioritárias para melhorias, destacando boas práticas já implementadas e áreas para refinamento.
```

##### Prompt 14: Revisão de Código Backend Específica

```
Atue como um Desenvolvedor Backend Sênior especializado em {Node.js/NestJS/Express/.NET/Java Spring}. Estou revisando a implementação da TASK-{número} que envolve lógica de servidor, processamento de dados ou APIs.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Especificação de API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Padrões de backend: .agent/padroes-codigo/backend/{framework}/{padrões-específicos}.md
- Modelo de dados: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md
- Requisitos de performance: .agent/contexto/requisitos/requisitos-nao-funcionais.md

Aqui está o código backend para revisão:

```

[CÓDIGO BACKEND A SER REVISADO]

```

Por favor, conduza uma análise backend especializada que:

1. Avalie a implementação da lógica de negócio e sua correspondência com requisitos
2. Verifique a estruturação de APIs e aderência a padrões REST/GraphQL
3. Analise as operações de banco de dados e eficiência de queries
4. Verifique o tratamento de transações e consistência de dados
5. Avalie mecanismos de validação e sanitização de entrada
6. Verifique o tratamento de concorrência e race conditions
7. Analise a implementação de caching e otimizações de performance
8. Verifique a estruturação de código em camadas (controllers, services, repositories)

Para cada problema identificado:
- Explique o impacto em termos de funcionalidade, performance ou escalabilidade
- Sugira implementação melhorada com exemplos concretos de código
- Referencie padrões específicos em .agent/padroes-codigo/backend/
- Quando aplicável, indique considerações de segurança relacionadas
- Mencione impactos em testabilidade ou cobertura de testes

Conclua com uma avaliação geral da qualidade do código backend e recomendações prioritárias para melhorias, destacando boas práticas já implementadas e áreas para refinamento.
```

##### Prompt 15: Revisão de Código para Observabilidade

```
Atue como um Especialista em Observabilidade e Monitoramento. Estou revisando a implementação da TASK-{número} com foco específico em como o código implementa logging, métricas, tracing e outros aspectos de observabilidade.

Referências de contexto:
- Descrição da tarefa: .agent/tasks/TASK-{número}.md
- Estratégia de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Padrões de logging: .agent/padroes-codigo/{tecnologia}/logging-estruturado.md
- Catálogo de métricas: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Requisitos de auditoria: .agent/contexto/seguranca-compliance/auditoria-logging.md

Aqui está o código para análise:

```

[CÓDIGO A SER REVISADO]

```

Por favor, conduza uma análise de observabilidade que:

1. Verifique a implementação de logging estruturado nos pontos apropriados
2. Avalie a granularidade e nível de detalhe dos logs
3. Analise a implementação de métricas para KPIs técnicos e de negócio
4. Verifique a instrumentação para tracing distribuído
5. Avalie a capacidade de troubleshooting baseada na telemetria implementada
6. Verifique a sanitização de dados sensíveis em logs e métricas
7. Analise a correlação entre diferentes sinais de observabilidade
8. Verifique alertas deriváveis da instrumentação implementada

Para cada lacuna ou problema de observabilidade:
- Explique o impacto em termos de capacidade de diagnóstico e monitoramento
- Descreva cenários onde seria difícil identificar ou solucionar problemas
- Sugira implementação melhorada com exemplos concretos de código
- Referencie padrões específicos em .agent/padroes-codigo/{tecnologia}/logging-estruturado.md
- Quando aplicável, indique métricas adicionais que deveriam ser capturadas

Conclua com uma avaliação da maturidade de observabilidade da implementação e recomendações prioritárias para fortalecer a capacidade de monitoramento, diagnóstico e auditoria.
```

Esta abordagem estruturada para revisão e refinamento, potencializada pelo GitHub Copilot através de prompts especializados, transforma o processo tradicional de revisão em um mecanismo sistemático de elevação de qualidade que não apenas corrige problemas, mas fundamentalmente eleva o nível técnico da base de código e das próprias equipes de desenvolvimento, criando um ciclo virtuoso de melhoria contínua.

### 8. Teste Automatizado Abrangente

A metodologia estruturada para testes automatizados transcende abordagens fragmentadas de verificação, implementando uma arquitetura de testes multidimensional que estabelece validação abrangente em cada camada da aplicação. Esta fase aplica técnicas avançadas de engenharia de qualidade para construir sistemas de verificação automatizados que detectam falhas precocemente, validam comportamentos esperados, e facilitam evolução contínua com confiança.

Com o suporte do GitHub Copilot, engenheiros de qualidade e desenvolvedores colaboram para implementar a estratégia de testes previamente definida, gerando suítes de teste robustas e abrangentes que capturam não apenas requisitos funcionais explícitos, mas também casos de borda, cenários de erro, e aspectos não-funcionais como performance e segurança. O processo utiliza personas especializadas em diferentes modalidades de teste para garantir que cada aspecto da aplicação seja verificado com a técnica mais apropriada.

O resultado é um ecossistema de verificação multinível que serve como documentação viva dos comportamentos esperados do sistema e como rede de segurança que permite refatorações e evoluções ousadas com riscos controlados. Este framework de testes não é apenas um validador passivo, mas um componente ativo do processo de desenvolvimento que guia implementações e identifica precocemente desvios de requisitos.

A fase implementa uma estratégia de testes em múltiplas camadas, cada uma servindo a propósitos específicos:

#### 8.1 Testes Unitários:

1. Criação de testes granulares para cada unidade funcional, seguindo os padrões definidos em `.agent/padroes-codigo`:

   - Testes de comportamento positivo para validar funcionalidades esperadas
   - Testes de casos de borda e condições excepcionais
   - Testes negativos para validar tratamento adequado de erros
   - Mocks e stubs para isolar unidades de suas dependências

2. Implementação de cobertura mínima conforme definido na estratégia de testes:
   - Cobertura de linhas, ramos e condições
   - Foco especial em lógica de negócio crítica
   - Verificação de invariantes e contratos internos

#### 8.2. Testes de Integração:

3. Verificação de interações entre componentes:

   - Testes de contrato para validar aderência a interfaces definidas
   - Testes de fluxo de dados entre módulos
   - Verificação de interações com dependências externas como bancos de dados e APIs
   - Casos de teste derivados diretamente de ADRs para validar decisões arquiteturais

4. Cenários de integração que combinam múltiplos componentes:
   - Fluxos completos de operações envolvendo múltiplas camadas
   - Verificação de comportamento transacional
   - Testes de resiliência para falhas em componentes dependentes

#### 8.3. Testes End-to-End:

5. Automação de fluxos críticos de usuário:

   - Simulação de interações de usuário completas
   - Validação de requisitos funcionais do ponto de vista do usuário
   - Verificação de integração frontend-backend
   - Testes de regressão para funcionalidades existentes

6. Testes especializados para requisitos não-funcionais:
   - Testes de performance para validar tempos de resposta e throughput
   - Testes de segurança automatizados baseados em OWASP
   - Verificações de acessibilidade conforme padrões WCAG
   - Testes de compatibilidade cross-browser/cross-device

#### 8.4. Integração Contínua:

7. Configuração de pipelines de CI/CD para execução automática de testes:
   - Suítes de smoke test para validação rápida de builds
   - Testes de regressão completos para integrações principais
   - Relatórios de cobertura e qualidade
   - Gates de qualidade baseados em métricas objetivas

#### 8.5. Prompts Otimizados para Testes Automatizados

##### Prompt 1: Geração de Testes Unitários com Base nos Requisitos

```
Atue como um Engenheiro de Qualidade especializado em testes unitários para {tecnologia/framework}. Estou desenvolvendo a funcionalidade descrita na TASK-{número} (veja em .agent/tasks/TASK-{número}.md) e preciso criar testes unitários abrangentes.

Referências importantes:
- Requisitos detalhados: .agent/contexto/requisitos/casos-uso.md (caso de uso {ID-específico})
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md (regras {IDs-específicas})
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-unitarios-{frontend/backend}.md
- Estrutura de mocks: .agent/padroes-codigo/testes/typescript/mocks-services.md

Aqui está o código a ser testado:

```

[INSIRA O CÓDIGO AQUI]

```

Por favor, gere um conjunto completo de testes unitários que:
1. Verifique todos os fluxos funcionais descritos no caso de uso e regras de negócio
2. Inclua testes para casos de borda identificados nos requisitos
3. Teste especificamente as condições de erro documentadas
4. Utilize os padrões de mocagem definidos em .agent/padroes-codigo/testes/typescript/mocks-services.md
5. Siga a estrutura e convenções de nomeação definidas nos padrões de teste
6. Implemente asserções precisas que validem o comportamento esperado
7. Considere estados iniciais variados conforme descrito nos casos de uso

Inclua documentação clara para cada conjunto de testes explicando:
- Qual aspecto da funcionalidade está sendo testado
- Cobertura de regras de negócio específicas
- Estratégia de isolamento e mocks utilizada
- Casos de borda considerados
```

##### Prompt 2: Criação de Testes de Integração Baseados em ADRs

```
Atue como um Especialista em Testes de Integração com experiência em {tecnologia/framework}. Estou implementando testes de integração para a funcionalidade da TASK-{número} (.agent/tasks/TASK-{número}.md) que envolve vários componentes e suas interações.

Referências arquiteturais:
- ADRs relevantes: .agent/contexto/arquitetura/adrs/ADR-{números}.md
- Diagrama de fluxo: .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md (fluxo "{nome-do-fluxo}")
- Contratos de API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-integracao-api.md

Os componentes envolvidos nesta integração são:
- [Componente 1] que implementa [funcionalidade]
- [Componente 2] que implementa [funcionalidade]
- [Dependência externa/sistema] com o qual interagimos via API

Por favor, crie testes de integração que:
1. Validem os fluxos de integração descritos no diagrama de sequência mencionado
2. Testem especificamente as decisões arquiteturais documentadas em ADR-{número}
3. Verifiquem a conformidade com os contratos de API definidos
4. Incluam cenários de falha e como o sistema deve se comportar (circuit breaking, retry, etc.)
5. Utilizem dados de teste realistas conforme definido em .agent/padroes-codigo/testes/typescript/testes-prisma.md
6. Testem os pontos de integração críticos mencionados na arquitetura

Estruture os testes em:
- Setup de ambiente isolado para testes
- Configuração de estados iniciais necessários
- Execução dos fluxos de integração
- Verificação do estado final e resultados esperados
- Teardown adequado de recursos
```

##### Prompt 3: Desenvolvimento de Testes End-to-End para Fluxos Críticos

```
Atue como um Especialista em Automação de Testes E2E com foco em {Cypress/Playwright/Selenium}. Estou implementando testes end-to-end para fluxos críticos de usuário descritos na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Fluxos de usuário: .agent/contexto/usuario/jornadas-usuario.md (jornada "{nome-da-jornada}")
- Wireframes: .agent/contexto/design/wireframes-fluxos.md (seção "{nome-da-tela}")
- Critérios de aceitação: .agent/tasks/TASK-{número}.md (seção "Critérios de Aceitação")
- Padrões de E2E: .agent/padroes-codigo/testes/typescript/testes-e2e-frontend.md

Por favor, desenvolva testes end-to-end automatizados que:
1. Implementem os fluxos completos de usuário descritos na jornada referenciada
2. Validem todos os critérios de aceitação listados na tarefa
3. Verifiquem elementos visuais e interações conforme definido nos wireframes
4. Testem fluxos alternativos e casos de erro
5. Implementem verificações de acessibilidade conforme .agent/padroes-codigo/frontend/acessibilidade/testes-acessibilidade.md
6. Sigam os padrões de organização e design de testes definidos

Cada teste deve:
- Ter descrição clara do cenário de usuário sendo testado
- Incluir setup de dados necessários (usando fixtures ou factories)
- Implementar steps reutilizáveis para operações comuns
- Conter asserções robustas que validem estado e comportamento
- Incluir screenshots ou vídeos em pontos críticos do fluxo
- Lidar adequadamente com latência e operações assíncronas
```

##### Prompt 4: Criação de Testes de Performance

```
Atue como um Engenheiro de Performance especializado em testes de carga e stress. Estou implementando testes de performance para a funcionalidade descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) que precisa atender aos requisitos não-funcionais especificados.

Referências técnicas:
- Requisitos de performance: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção performance)
- Benchmarks esperados: .agent/contexto/arquitetura/performance-escalabilidade/benchmarks-performance.md
- Cenários de carga: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Padrões de teste: .agent/padroes-codigo/performance/monitoramento-performance.md

Para esta funcionalidade específica, os SLAs de performance são:
- Tempo de resposta máximo: [X] ms para o percentil 95
- Throughput mínimo: [Y] requisições por segundo
- Capacidade de usuários concorrentes: [Z] usuários

Por favor, desenvolva testes de performance utilizando {k6/JMeter/Locust} que:
1. Simulem com precisão os padrões de acesso descritos nos cenários de carga
2. Meçam todas as métricas-chave de performance listadas no catálogo de métricas
3. Testem a escalabilidade com aumento gradual de carga até 150% da capacidade esperada
4. Implementem verificações para todos os SLAs definidos nos requisitos não-funcionais
5. Incluam cenários de pico de utilização repentina
6. Validem o comportamento sob carga sustentada por períodos prolongados

Estruture os testes com:
- Scripts parametrizáveis para diferentes ambientes (dev, staging, prod)
- Perfis de carga realistas baseados nos padrões de usuários documentados
- Coleta de métricas detalhadas (latência, throughput, utilização de recursos)
- Thresholds claros para pass/fail baseados nos SLAs
- Visualizações e dashboards para análise dos resultados
```

##### Prompt 5: Desenvolvimento de Testes de Segurança Automatizados

```
Atue como um Especialista em Segurança de Aplicações especializado em testes automatizados. Estou implementando testes de segurança para a funcionalidade da TASK-{número} (.agent/tasks/TASK-{número}.md) que envolve [login/dados sensíveis/processamento de pagamentos/etc].

Referências críticas:
- Modelo de ameaças: .agent/contexto/arquitetura/seguranca-privacidade/modelo-ameacas.md
- Requisitos de segurança: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção segurança)
- Estratégias de mitigação: .agent/contexto/arquitetura/seguranca-privacidade/estrategias-mitigacao.md
- Padrões de teste: .agent/padroes-codigo/seguranca/typescript/[arquivos relevantes].md

Por favor, desenvolva testes de segurança automatizados que:
1. Validem mitigações para as ameaças identificadas no modelo de ameaças
2. Testem vulnerabilidades específicas baseadas no OWASP Top 10 relevantes para esta funcionalidade
3. Verifiquem a implementação adequada de controles de segurança (XSS, CSRF, injeção, etc.)
4. Validem o tratamento seguro de dados sensíveis conforme requisitos
5. Testem cenários de abuso e tentativas de bypass de segurança
6. Verifiquem a correta implementação de validação de entrada em todos os pontos de entrada

Implemente os testes usando {ferramenta de segurança} e estruture em:
- Testes para validação de entrada e sanitização
- Testes para autenticação e autorização
- Testes para proteção de dados sensíveis
- Testes para configurações de segurança de infraestrutura
- Testes para proteção contra ataques comuns

Inclua documentação clara sobre:
- Quais ameaças cada teste está verificando
- Como interpretar falhas e falsos positivos
- Remediações recomendadas para problemas detectados
```

##### Prompt 6: Criação de Testes de Acessibilidade

```
Atue como um Especialista em Acessibilidade Web com foco em testes automatizados. Estou implementando testes de acessibilidade para a interface descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) que deve atender aos padrões WCAG 2.1 nível AA.

Referências importantes:
- Requisitos de acessibilidade: .agent/contexto/design/acessibilidade.md
- Wireframes e componentes: .agent/contexto/design/wireframes-fluxos.md (seção "{nome-da-tela}")
- Padrões de acessibilidade: .agent/padroes-codigo/frontend/acessibilidade/*.md
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-e2e-frontend.md

Por favor, desenvolva testes automatizados de acessibilidade utilizando {axe/jest-axe/Lighthouse/WAVE} que:
1. Verifiquem conformidade com WCAG 2.1 AA em todos os componentes da interface
2. Testem especificamente os requisitos documentados em .agent/contexto/design/acessibilidade.md
3. Validem acessibilidade por teclado para todas as funcionalidades interativas
4. Testem suporte adequado para tecnologias assistivas (leitores de tela, etc.)
5. Verifiquem contrastes de cor e legibilidade em diferentes condições
6. Testem comportamento responsivo e acessível em diferentes tamanhos de tela

Estruture os testes para verificar:
- Semântica HTML adequada e uso correto de ARIA
- Navegação lógica e gerenciamento de foco
- Textos alternativos para elementos não-textuais
- Mensagens de erro e feedback acessíveis
- Formulários e controles corretamente rotulados
- Compatibilidade com tecnologias assistivas

Inclua relatórios detalhados que:
- Identifiquem violações específicas com referência ao critério WCAG relevante
- Forneçam detalhes sobre como reproduzir e verificar cada problema
- Sugiram correções específicas alinhadas com os padrões de código do projeto
```

##### Prompt 7: Desenvolvimento de Testes para API GraphQL

```
Atue como um Especialista em Testes de API com foco em GraphQL. Estou implementando testes para a API GraphQL desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) que expõe as seguintes operações:

Referências técnicas:
- Especificação da API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md (seção GraphQL)
- Schema GraphQL: [incluir schema ou path para o arquivo]
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md (regras {IDs específicas})
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-integracao-api.md

Por favor, desenvolva testes automatizados para esta API GraphQL que:
1. Validem todas as queries, mutations e subscriptions listadas na especificação
2. Testem resolvers e funcionamento correto do schema
3. Verifiquem validações e tratamento de erros para entradas inválidas
4. Testem autorização e acesso adequado baseado em diferentes perfis de usuário
5. Validem o comportamento conforme as regras de negócio especificadas
6. Incluam testes de performance para operações complexas ou com alto volume de dados
7. Verifiquem limites de profundidade de query e proteções contra ataques de complexidade

Estruture os testes em:
- Testes para validação de schema
- Testes para cada query importante
- Testes para cada mutation importante
- Testes para resolvers específicos
- Testes para tipos customizados e enums
- Testes para lógica de autorização

Utilize as ferramentas recomendadas em .agent/padroes-codigo/testes/typescript/testes-integracao-api.md e implemente fixtures/factories para dados de teste conforme necessário.
```

##### Prompt 8: Criação de Testes para Componentes UI React/Vue/Angular

```
Atue como um Especialista em Testes de Frontend com foco em {React/Vue/Angular}. Estou implementando testes para o componente UI desenvolvido na TASK-{número} (.agent/tasks/TASK-{número}.md) que implementa [funcionalidade/interface].

Referências importantes:
- Design do componente: .agent/contexto/design/wireframes-fluxos.md (seção "{nome-do-componente}")
- Comportamentos esperados: .agent/tasks/TASK-{número}.md (seção "Critérios de Aceitação")
- Padrões de componentes: .agent/padroes-codigo/frontend/{framework}/componentes-estrutura.md
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-unitarios-frontend.md e .agent/padroes-codigo/testes/typescript/testes-hooks-react.md

Aqui está o código do componente:

```

[INSIRA O CÓDIGO DO COMPONENTE AQUI]

```

Por favor, desenvolva testes automatizados utilizando {React Testing Library/Vue Test Utils/Angular Testing Library} que:
1. Verifiquem a renderização correta do componente em diferentes estados
2. Testem todas as interações de usuário descritas nos critérios de aceitação
3. Validem o comportamento responsivo conforme especificado no design
4. Verifiquem o comportamento do componente com diferentes props e estados
5. Testem integrações com componentes filhos ou serviços quando aplicável
6. Implementem mocks adequados para dependências externas
7. Testem comportamento de gerenciamento de estado conforme .agent/padroes-codigo/frontend/gerenciamento-estado/*.md

Estruture os testes em:
- Testes de renderização para diferentes estados
- Testes de interação para eventos de usuário
- Testes para props, validações e comportamentos default
- Testes para estados de erro e comportamentos excepcionais
- Testes para hooks customizados e lógica complexa

Considere os padrões de acessibilidade ao implementar os testes, verificando se elementos interativos são acessíveis e seguem as práticas recomendadas em .agent/padroes-codigo/frontend/acessibilidade/*.md.
```

##### Prompt 9: Testes para Operações de Banco de Dados com Prisma

```
Atue como um Especialista em Testes de Banco de Dados com foco em Prisma ORM. Estou implementando testes para a camada de persistência desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) que realiza operações de [criação/leitura/atualização/exclusão] em [entidades].

Referências técnicas:
- Modelo de dados: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md
- Queries e operações: [incluir código ou descrições das operações]
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md (regras {IDs específicas})
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-prisma.md

Por favor, desenvolva testes automatizados para estas operações de banco de dados que:
1. Validem a correta implementação das operações CRUD para as entidades envolvidas
2. Testem constraints e validações definidas no modelo de dados
3. Verifiquem relacionamentos e integridade referencial
4. Testem transações e comportamento em cenários de erro
5. Validem queries complexas e otimizações implementadas
6. Testem soft deletes e histórico quando aplicável
7. Verifiquem conformidade com as regras de negócio especificadas

Estruture os testes utilizando:
- Setup adequado de banco de dados de teste isolado
- Factories para criação de dados de teste conforme .agent/padroes-codigo/banco-de-dados/prisma/seeds-fixtures.md
- Transações para isolamento de testes
- Cleanup apropriado após cada teste
- Verificações precisas dos resultados das operações

Inclua testes para casos especiais como:
- Migrações e alterações de schema
- Performance de queries com volumes maiores de dados
- Race conditions em operações concorrentes
- Recuperação de falhas e estratégias de retry
```

##### Prompt 10: Criação de Testes de Contrato para APIs

```
Atue como um Especialista em Testes de Contrato para APIs. Estou implementando testes de contrato para validar a conformidade da API desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) com sua especificação formal.

Referências técnicas:
- Especificação da API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Contratos definidos: .agent/contexto/arquitetura/integracao/contratos-governanca.md
- Cenários de uso: .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md
- Padrões de teste: .agent/padroes-codigo/integracao/tipagem-contratos.md

Por favor, desenvolva testes de contrato utilizando {Pact/Spring Cloud Contract/Postman/etc} que:
1. Validem conformidade com todos os endpoints documentados na especificação
2. Verifiquem os formatos exatos de request e response conforme contratos
3. Testem todos os casos de erro e códigos de status documentados
4. Validem headers obrigatórios e formatos de autenticação
5. Verifiquem compatibilidade com versões anteriores quando aplicável
6. Testem limites de tamanho, formatos e tipos de dados em todos os parâmetros

Estruture os testes para validar:
- Esquemas de request e response
- Validações e constraints
- Códigos de status em diferentes cenários
- Headers e metadados
- Comportamento de paginação, ordenação e filtragem
- Versionamento de API

Implemente o projeto de testes de contrato de forma que possa ser executado tanto pelo consumidor quanto pelo provedor da API, garantindo compatibilidade contínua entre ambos.
```

##### Prompt 11: Desenvolvimento de Mocks e Stubs para Testes

```
Atue como um Arquiteto de Testes especializado em técnicas avançadas de mocking. Estou implementando mocks e stubs para isolar o componente desenvolvido na TASK-{número} (.agent/tasks/TASK-{número}.md) de suas dependências externas para testes eficazes.

Referências técnicas:
- Dependências a serem mockadas: [listar dependências externas, APIs, serviços, etc.]
- Interfaces e contratos: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Comportamentos esperados: .agent/contexto/requisitos/casos-uso.md (caso de uso {ID específico})
- Padrões de mock: .agent/padroes-codigo/testes/typescript/mocks-services.md

Por favor, desenvolva implementações de mocks/stubs robustos utilizando {Jest/Sinon/Mock Service Worker/etc} que:
1. Simulem com precisão o comportamento das dependências externas
2. Implementem todos os cenários descritos nos casos de uso, incluindo casos de erro
3. Permitam configuração flexível para diferentes cenários de teste
4. Registrem interações para validação em asserções
5. Simulem latência e comportamentos assíncronos realistas
6. Implementem comportamentos idempotentes para testes determinísticos

Estruture os mocks como:
- Factories de mocks reutilizáveis
- Configurações de cenários comuns pré-definidos
- Helpers para verificação de interações
- Implementações que seguem os contratos definidos

Inclua implementações para cenários específicos como:
- Respostas de sucesso com dados válidos
- Erros de validação e formatos
- Falhas de rede e timeouts
- Respostas parciais e edge cases
```

##### Prompt 12: Criação de Framework de Testes Customizado

```
Atue como um Arquiteto de Automação de Testes com experiência em frameworks customizados. Estou desenvolvendo um framework de testes específico para o projeto descrito em .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md para padronizar e facilitar a criação de testes.

Referências técnicas:
- Arquitetura do sistema: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Padrões de teste existentes: .agent/padroes-codigo/testes/typescript/*.md
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md
- Necessidades específicas: [descrever requisitos particulares do projeto]

Por favor, projete um framework de testes customizado que:
1. Implemente abstrações para os tipos de teste mais comuns no projeto
2. Forneça utilities e helpers reutilizáveis para setup, teardown e asserções
3. Padronize a criação de mocks e fixtures para consistência
4. Facilite o teste de aspectos específicos da arquitetura do projeto
5. Implemente relatórios e visualizações customizadas
6. Integre-se ao pipeline de CI/CD conforme .agent/contexto/implantacao/automacao-implantacao/*

Os componentes do framework devem incluir:
- Classe base para diferentes tipos de teste
- Geradores de dados de teste parametrizáveis
- Abstrações para interações com componentes comuns (DB, APIs, etc.)
- DSL para expressão clara de intenção nos testes
- Sistema de tags e categorização para execução seletiva
- Mecanismos de retry para testes flaky

Implemente o framework como um pacote interno com documentação e exemplos claros de uso para cada componente e funcionalidade.
```

##### Prompt 13: Desenvolvimento de Testes de Regressão Visual

```
Atue como um Especialista em Testes de Regressão Visual. Estou implementando testes visuais para garantir consistência na UI desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) através de diferentes iterações e ambientes.

Referências importantes:
- Design system: .agent/contexto/design/design-system.md
- Interfaces a serem testadas: .agent/contexto/design/wireframes-fluxos.md (seções [especificar seções])
- Variações para teste: [listar diferentes tamanhos de tela, temas, estados, etc.]
- Padrões de teste: .agent/padroes-codigo/frontend/tailwindcss/sistema-cores.md e outros padrões visuais relevantes

Por favor, desenvolva testes de regressão visual utilizando {Cypress Visual Testing/Percy/Storybook/jest-image-snapshot} que:
1. Capturem screenshots baseline de todos os componentes principais em seus diferentes estados
2. Automatizem a comparação visual entre versões para detectar mudanças não intencionais
3. Testem a interface em diferentes tamanhos de tela conforme .agent/contexto/design/design-responsivo.md
4. Verifiquem consistência em diferentes temas (claro/escuro)
5. Testem estados específicos como loading, erro, vazio, etc.
6. Validem conformidade visual com o design system

Estruture os testes para:
- Organizar screenshots por componente e variação
- Definir thresholds apropriados para diferenças aceitáveis
- Documentar claramente o propósito de cada teste visual
- Incluir mecanismos para aprovar alterações intencionais
- Destacar áreas de interesse específicas em componentes complexos

Inclua estratégias para lidar com:
- Elementos dinâmicos que podem causar falsos positivos
- Diferentes renderizações em sistemas operacionais e navegadores diversos
- Atualização eficiente de baselines quando mudanças são intencionais
- Integração com o pipeline de CI/CD
```

##### Prompt 14: Criação de Testes para Lógica de Negócio Complexa

```
Atue como um Analista de Negócios e Especialista em Testes com profundo conhecimento de domínio. Estou implementando testes para a lógica de negócio complexa desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) que implementa [funcionalidade específica de negócio].

Referências cruciais:
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md (regras {IDs específicas})
- Fluxos de processo: .agent/contexto/requisitos/fluxos-processo.md (fluxo "{nome do fluxo}")
- Requisitos funcionais: .agent/contexto/requisitos/matriz-requisitos-funcionais.md
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-unitarios-{frontend/backend}.md

Aqui está o código que implementa a lógica de negócio:

```

[INSIRA O CÓDIGO AQUI]

```

Por favor, desenvolva testes abrangentes que:
1. Validem cada regra de negócio individual mencionada na documentação
2. Testem o fluxo completo do processo de negócio em diferentes cenários
3. Verifiquem especificamente os casos de borda e exceções documentados
4. Testem combinações complexas de condições e seus resultados esperados
5. Validem cálculos, transformações e decisões lógicas implementadas
6. Garantam conformidade com requisitos regulatórios quando aplicável

Estruture os testes como:
- Test cases organizados por regra de negócio ou aspecto funcional
- Descrições claras que referenciam a documentação de requisitos
- Dados de teste representativos que cobrem o domínio de entrada
- Asserções precisas que validam não apenas resultados mas conformidade com regras

Considere particularmente:
- Interdependências entre diferentes regras de negócio
- Consistência de estado através de múltiplas operações
- Validações temporais e dependentes de contexto
- Comportamentos específicos para diferentes perfis ou segmentos
```

##### Prompt 15: Desenvolvimento de Testes para Internacionalização (i18n)

```
Atue como um Especialista em Testes de Internacionalização e Localização. Estou implementando testes para garantir que a funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) suporte adequadamente múltiplos idiomas e localizações.

Referências importantes:
- Requisitos de i18n: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção internacionalização)
- Idiomas suportados: [listar idiomas e locales]
- Estratégia de i18n: .agent/padroes-codigo/i18n/nextjs-i18n-app-router.md (ou outro relevante)
- Padrões de teste: .agent/padroes-codigo/testes/typescript/testes-unitarios-frontend.md e outros relevantes

Por favor, desenvolva testes automatizados que:
1. Verifiquem a correta externalização de todas as strings utilizadas na interface
2. Testem o carregamento e aplicação de traduções para todos os idiomas suportados
3. Validem formatação correta de datas, números, moedas e unidades conforme locale
4. Testem suporte a pluralização e regras gramaticais específicas por idioma
5. Verifiquem layout adaptável para diferentes comprimentos de texto
6. Testem suporte a direção RTL para idiomas como árabe e hebraico quando aplicável
7. Validem funcionamento correto de pesquisa e ordenação considerando diferentes collations

Estruture os testes para cobrir:
- Renderização correta de conteúdo traduzido
- Switching de idioma e persistência de preferência
- Formatação específica por locale
- Comportamento responsivo com diferentes comprimentos de texto
- Fallbacks para traduções ausentes
- Metadata para SEO multi-idioma

Implemente automação que possa:
- Detectar strings não externalizadas (hardcoded)
- Verificar completude de arquivos de tradução
- Validar consistência de chaves entre diferentes idiomas
- Testar casos de borda como textos muito longos ou caracteres especiais
```

A abordagem estruturada para testes automatizados, potencializada pelo GitHub Copilot através destes prompts especializados, transforma o processo de verificação de um gargalo manual e propenso a falhas para um sistema abrangente e automatizado que garante qualidade em todas as dimensões da aplicação. Esta metodologia não apenas detecta problemas precocemente, mas fundamentalmente previne sua introdução através de um ciclo de feedback imediato e contínuo durante todo o desenvolvimento.

Cada categoria de teste contribui com uma camada distinta de proteção, desde a validação granular de componentes individuais até a verificação de fluxos completos de usuário, criando um ecossistema de qualidade que permite entregas frequentes com confiança enquanto mantém a capacidade de evolução rápida e segura do sistema.

### 9. Documentação Técnica

A metodologia estruturada para documentação técnica transcende abordagens convencionais que tratam documentação como atividade posterior e opcional, implementando um framework que posiciona documentação como artefato primário e contínuo do desenvolvimento. Esta fase aplica técnicas avançadas de engenharia de conhecimento para capturar, estruturar e comunicar informações técnicas complexas de forma acessível e acionável para múltiplas audiências técnicas.

Com o suporte do GitHub Copilot, desenvolvedores e especialistas técnicos geram documentação abrangente que acompanha cada aspecto do sistema, utilizando prompts especializados para diferentes tipos de conteúdo técnico. O processo incorpora personas complementares como Technical Writers, Arquitetos de Documentação e Especialistas em Developer Experience que colaboram para construir um ecossistema de conhecimento técnico coeso e navegável que atende diferentes necessidades informacionais.

O resultado é uma base de conhecimento viva e estruturada que evolui em paralelo com o código, encapsulando não apenas aspectos funcionais, mas fundamentos arquiteturais, decisões de design, padrões de uso, e procedimentos operacionais. Esta documentação estabelece um contrato de conhecimento que facilita onboarding, manutenção, colaboração entre equipes, e maximiza o valor extraído do sistema implementado.

A fase culmina na criação de artefatos de documentação abrangentes, organizados na pasta `.agent/contexto/documentacao`:

#### 9.1. Documentação Arquitetural:

- Guias Arquiteturais detalhando os princípios e padrões fundamentais do sistema
- Diagramas de Arquitetura em múltiplos níveis de abstração (C4 Model ou similar)
- Catálogo de Componentes documentando responsabilidades, interfaces e dependências
- Mapa de Integração detalhando pontos de conexão com sistemas externos

#### 9.2. Documentação de API:

- Referências de API completas (REST, GraphQL, etc.) com exemplos de requisição/resposta
- Guias de Uso detalhando fluxos comuns e implementações recomendadas
- Contratos de Serviço explicitando garantias, limitações e políticas de versionamento
- Documentação de Esquemas de Dados detalhando estruturas e validações

#### 9.3. Documentação para Desenvolvedores:

- Guias de Configuração de Ambiente detalhando setup inicial e dependências
- Documentos de Desenvolvimento explicando arquitetura de código e padrões
- Tutoriais passo-a-passo para implementações de features comuns
- Catálogo de Solução de Problemas documentando erros frequentes e suas resoluções

#### 9.4. Documentação Operacional:

- Runbooks para operações críticas e procedimentos de manutenção
- Guias de Troubleshooting organizados por subsistema e sintoma
- Procedimentos de Recuperação de Desastres com checklists detalhados
- Documentação de Monitoramento explicando métricas, alertas e thresholds

#### 9.5. Documentação para Onboarding:

- Roteiros de Onboarding para diferentes funções técnicas
- Glossário Técnico explicando terminologia específica do domínio e sistema
- Mapas de Conhecimento indicando especialistas para diferentes áreas do sistema
- Documentos de Visão Geral proporcionando orientação inicial rápida

#### 9.6. Prompts Otimizados para Documentação Técnica

##### Prompt 1: Geração de Documentação Arquitetural

```
Atue como um Arquiteto de Documentação Técnica especializado em comunicar sistemas complexos. Estou precisando criar documentação arquitetural para o componente/funcionalidade implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Decisões arquiteturais: .agent/contexto/arquitetura/adrs/ADR-{números relevantes}.md
- Visão geral da arquitetura: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Contexto técnico: .agent/contexto/tecnico/mapa-sistemas.md
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md

Por favor, gere documentação arquitetural abrangente para armazenamento em '.agent/contexto/documentacao/arquitetura/' que inclua:

1. Um documento "Visão Arquitetural do Componente" (visao-componente-{nome}.md) que:
   - Explique o propósito e responsabilidades do componente no contexto do sistema mais amplo
   - Ilustre como o componente se integra com o restante da arquitetura (usando notação C4 ou similar)
   - Destaque princípios arquiteturais aplicados conforme documentado em .agent/contexto/arquitetura/visao/manifesto-arquitetural.md

2. Um documento "Decisões de Design" (decisoes-design-{nome}.md) que:
   - Documente as principais decisões de design tomadas durante a implementação
   - Explique os trade-offs considerados e justificativas para escolhas feitas
   - Relacione estas decisões com os ADRs relevantes do projeto

3. Um documento "Mapa de Dependências" (dependencias-{nome}.md) que:
   - Liste todas as dependências internas e externas do componente
   - Explique os contratos e interfaces entre componentes
   - Detalhe o fluxo de dados e comportamento em caso de falhas nas dependências

4. Um documento "Considerações Técnicas" (consideracoes-tecnicas-{nome}.md) que:
   - Explique aspectos específicos de implementação relevantes para entendimento futuro
   - Detalhe comportamentos não-óbvios ou complexidades inerentes
   - Documente limitações técnicas conhecidas e abordagens para mitigá-las

5. Um documento "Evolução Arquitetural" (evolucao-{nome}.md) que:
   - Indique a direção futura planejada para o componente
   - Identifique áreas potenciais para refatoração ou melhoria
   - Explique como o componente deve evoluir conforme requisitos futuros previstos

Cada documento deve:
- Incluir diagramas conceituais claros (use notação de Mermaid quando aplicável)
- Referenciar explicitamente ADRs e outros documentos arquiteturais para manter consistência
- Usar linguagem técnica precisa alinhada com o glossário em .agent/contexto/tecnico/glossario-tecnico.md
- Ser compreensível para desenvolvedores que não participaram da implementação original
```

##### Prompt 2: Criação de Documentação de API

```
Atue como um Technical Writer especializado em documentação de API. Estou precisando documentar a API implementada na TASK-{número} (.agent/tasks/TASK-{número}.md) que expõe funcionalidades para {consumidores da API}.

Referências essenciais:
- Especificação da API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Modelos de dados: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md
- Padrões de API: .agent/padroes-codigo/integracao/contratos-governanca.md
- Regras de negócio: .agent/contexto/requisitos/regras-negocio.md

Aqui está o código da implementação:

```

[CÓDIGO DA API A SER DOCUMENTADA]

```

Por favor, gere documentação completa de API para armazenamento em '.agent/contexto/documentacao/api/' que inclua:

1. Um documento "Referência de API" (referencia-api-{nome}.md) no formato OpenAPI/Swagger que:
   - Documente cada endpoint com URI, métodos HTTP, headers necessários
   - Detalhe parâmetros de requisição (path, query, body) com tipos, formatos e restrições
   - Especifique todos os possíveis códigos de resposta e estruturas de retorno
   - Inclua exemplos completos de requisição e resposta para cada operação

2. Um documento "Guia de Uso da API" (guia-uso-{nome}.md) que:
   - Explique casos de uso comuns com exemplos práticos de integração
   - Forneça snippets de código em linguagens relevantes (JavaScript, Python, etc.)
   - Detalhe fluxos completos que envolvam múltiplas chamadas de API
   - Inclua melhores práticas para implementação de consumidores

3. Um documento "Contratos e Garantias" (contratos-{nome}.md) que:
   - Explique políticas de versionamento e compatibilidade
   - Documente SLAs esperados (disponibilidade, latência, throughput)
   - Detalhe limites e throttling aplicados
   - Especifique procedimentos para depreciação e descontinuação de endpoints

4. Um documento "Tratamento de Erros" (erros-{nome}.md) que:
   - Catalogue todos os possíveis erros por endpoint
   - Explique causas comuns e soluções recomendadas para cada erro
   - Detalhe o formato de resposta de erro seguindo o padrão definido em .agent/padroes-codigo/integracao/erros-resiliencia.md
   - Forneça estratégias para lidar com diferentes cenários de falha

5. Um documento "Segurança e Autenticação" (seguranca-{nome}.md) que:
   - Explique mecanismos de autenticação/autorização utilizados
   - Detalhe processo para obtenção e renovação de credenciais
   - Documente escopos/permissões e como afetam o acesso a endpoints
   - Inclua melhores práticas de segurança para consumidores

Cada documento deve:
- Ser tecnicamente preciso mas acessível para desenvolvedores de diferentes níveis
- Incluir exemplos práticos que demonstrem uso real da API
- Seguir o estilo e convenções definidos em .agent/padroes-codigo/documentacao/estilo-apis.md (se existir)
- Incluir links para outros recursos relevantes na documentação
```

##### Prompt 3: Documentação de Componentes de Frontend

```
Atue como um Especialista em Documentação de UI/Frontend com experiência em component libraries e design systems. Estou precisando documentar o componente frontend implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Design do componente: .agent/contexto/design/wireframes-fluxos.md
- Design system: .agent/contexto/design/design-system.md
- Requisitos de acessibilidade: .agent/contexto/design/acessibilidade.md
- Padrões de componentes: .agent/padroes-codigo/frontend/{framework}/componentes-estrutura.md

Aqui está o código do componente:

```

[CÓDIGO DO COMPONENTE A SER DOCUMENTADO]

```

Por favor, gere documentação completa do componente para armazenamento em '.agent/contexto/documentacao/frontend/componentes/' que inclua:

1. Um documento "Visão Geral do Componente" (visao-geral-{nome}.md) que:
   - Explique o propósito e casos de uso do componente
   - Ilustre visualmente o componente em seus diferentes estados
   - Detalhe como o componente se alinha com o design system geral
   - Documente o histórico de versões e evolução do componente

2. Um documento "API do Componente" (api-{nome}.md) que:
   - Liste todas as props/inputs com tipos, valores default e descrições
   - Documente eventos emitidos e como consumi-los
   - Explique slots/children e possibilidades de composição
   - Detalhe métodos públicos e refs expostos pelo componente

3. Um documento "Exemplos de Uso" (exemplos-{nome}.md) que:
   - Forneça exemplos de código para cenários comuns
   - Demonstre variações e customizações possíveis
   - Ilustre integração com outros componentes
   - Inclua exemplos de tratamento de erros/estados especiais

4. Um documento "Acessibilidade e Responsividade" (acessibilidade-{nome}.md) que:
   - Detalhe conformidade com padrões WCAG
   - Explique comportamento com tecnologias assistivas
   - Documente comportamento responsivo em diferentes breakpoints
   - Inclua considerações para modo escuro e alto contraste

5. Um documento "Considerações de Performance" (performance-{nome}.md) que:
   - Explique otimizações implementadas
   - Detalhe práticas para uso eficiente (memoization, etc.)
   - Documente métricas de performance (bundle size, render performance)
   - Forneça diretrizes para evitar problemas comuns

Cada documento deve:
- Incluir exemplos visuais que demonstrem claramente o componente
- Fornecer snippets de código que possam ser facilmente copiados e adaptados
- Seguir o formato de documentação estabelecido em .agent/padroes-codigo/documentacao/estilo-componentes.md (se existir)
- Referenciar outros componentes relacionados ou dependências
```

##### Prompt 4: Geração de Runbooks Operacionais

```
Atue como um Especialista em Operações de TI com experiência em Site Reliability Engineering. Estou precisando criar documentação operacional para o sistema/componente implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Arquitetura do sistema: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Requisitos operacionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Estratégia de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Métricas críticas: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md

Por favor, gere documentação operacional abrangente para armazenamento em '.agent/contexto/documentacao/operacoes/' que inclua:

1. Um "Runbook de Operações Diárias" (runbook-operacoes-{nome}.md) que:
   - Detalhe verificações diárias/periódicas necessárias
   - Explique como interpretar métricas normais vs. anormais
   - Documente procedimentos para manutenção preventiva
   - Inclua cronograma recomendado para tarefas operacionais recorrentes

2. Um "Guia de Troubleshooting" (troubleshooting-{nome}.md) que:
   - Catalogue problemas comuns e seus sintomas observáveis
   - Forneça passos detalhados para diagnóstico de cada problema
   - Detalhe soluções passo-a-passo para cenários de falha
   - Inclua árvores de decisão para orientar o processo de diagnóstico

3. Um "Plano de Recuperação de Desastres" (recuperacao-desastres-{nome}.md) que:
   - Defina cenários de desastre e seus impactos potenciais
   - Detalhe procedimentos completos de recuperação para cada cenário
   - Especifique responsabilidades e escalações durante crises
   - Inclua checklists para validar recuperação bem-sucedida

4. Um "Guia de Escalação" (escalacao-{nome}.md) que:
   - Defina claramente níveis de severidade de incidentes
   - Detalhe quem contactar em cada nível de escalação
   - Explique critérios para escalação entre níveis
   - Inclua templates para comunicação durante incidentes

5. Um "Manual de Configuração" (configuracao-{nome}.md) que:
   - Documente todos os parâmetros de configuração disponíveis
   - Explique impactos de diferentes configurações na performance/comportamento
   - Forneça valores recomendados para diferentes ambientes/cenários
   - Detalhe procedimentos seguros para alteração de configurações

Cada documento deve:
- Ser estruturado para acesso rápido durante situações críticas
- Incluir diagramas, fluxogramas e visualizações quando útil
- Conter informações específicas e acionáveis (evitar generalidades)
- Incluir comandos, consultas e scripts específicos quando aplicável
- Considerar diferentes níveis de experiência da equipe operacional
```

##### Prompt 5: Criação de Documentação de Integração

```
Atue como um Arquiteto de Integração com experiência em documentação de sistemas distribuídos. Estou precisando documentar as integrações implementadas na TASK-{número} (.agent/tasks/TASK-{número}.md) que conecta nosso sistema com {sistemas externos/internos}.

Referências essenciais:
- Mapa de integrações: .agent/contexto/arquitetura/integracao/mapa-integracoes.md
- Contratos de API: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Fluxos de dados: .agent/contexto/arquitetura/dados/fluxos-dados.md
- Estratégia de resiliência: .agent/contexto/arquitetura/integracao/erros-resiliencia.md

Aqui está o código de integração:

```

[CÓDIGO DE INTEGRAÇÃO A SER DOCUMENTADO]

```

Por favor, gere documentação completa de integração para armazenamento em '.agent/contexto/documentacao/integracoes/' que inclua:

1. Um documento "Visão Geral da Integração" (visao-geral-integracao-{sistema}.md) que:
   - Explique o propósito da integração no contexto do negócio
   - Ilustre o fluxo completo de dados entre sistemas
   - Detalhe os benefícios e capacidades habilitadas pela integração
   - Documente premissas e dependências críticas

2. Um documento "Especificação Técnica" (especificacao-tecnica-{sistema}.md) que:
   - Detalhe os endpoints/interfaces utilizados com parâmetros completos
   - Explique protocolos, formatos de dados e mecanismos de autenticação
   - Documente mapeamentos entre modelos de dados dos sistemas
   - Inclua diagramas de sequência para fluxos críticos

3. Um documento "Guia de Resiliência" (resiliencia-{sistema}.md) que:
   - Detalhe estratégias implementadas para lidar com falhas
   - Explique mecanismos de retry, circuit breaking e fallback
   - Documente comportamentos esperados em diferentes cenários de degradação
   - Inclua estratégias para recuperação após falhas prolongadas

4. Um documento "Monitoramento e Alertas" (monitoramento-{sistema}.md) que:
   - Liste todas as métricas específicas para a integração
   - Detalhe alertas configurados e seus thresholds
   - Explique como detectar e diagnosticar problemas comuns
   - Inclua queries e dashboards para visualização de saúde da integração

5. Um documento "Guia de Troubleshooting" (troubleshooting-{sistema}.md) que:
   - Catalogue problemas comuns específicos desta integração
   - Forneça passos para diagnóstico e resolução de cada problema
   - Inclua informações de contato e procedimentos de escalação
   - Detalhe logs relevantes e como interpretá-los

Cada documento deve:
- Referenciar explicitamente contratos e documentação dos sistemas externos
- Incluir exemplos concretos de payloads/mensagens em cada direção
- Destacar claramente dependências críticas e potenciais pontos de falha
- Especificar responsabilidades de cada sistema na integração
- Considerar aspectos de versionamento e compatibilidade futura
```

##### Prompt 6: Desenvolvimento de Guias de Configuração e Setup

```
Atue como um Especialista em Developer Experience com foco em onboarding e configuração de ambientes. Estou precisando criar documentação de setup para o componente/sistema implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Descrição do componente: .agent/tasks/TASK-{número}.md
- Dependências técnicas: .agent/contexto/tecnico/mapa-sistemas.md
- Padrões de desenvolvimento: .agent/padroes-codigo/{tecnologia}/*.md
- Configurações de ambiente: .agent/contexto/implantacao/automacao-implantacao/*.md (se aplicável)

Por favor, gere documentação completa de configuração para armazenamento em '.agent/contexto/documentacao/setup/' que inclua:

1. Um "Guia de Configuração de Ambiente" (configuracao-ambiente-{nome}.md) que:
   - Detalhe todos os pré-requisitos de software/hardware
   - Forneça instruções passo-a-passo para configuração inicial
   - Explique variáveis de ambiente e configurações necessárias
   - Inclua verificações para validar setup correto

2. Um "Guia de Instalação de Dependências" (dependencias-{nome}.md) que:
   - Liste todas as dependências com versões específicas
   - Forneça comandos/procedimentos para instalação em diferentes OS
   - Explique incompatibilidades conhecidas e suas soluções
   - Detalhe estratégias para resolução de conflitos de versão

3. Um "Manual de Configuração para Desenvolvimento" (configuracao-dev-{nome}.md) que:
   - Explique ferramentas recomendadas (IDE, extensões, etc.)
   - Detalhe configurações específicas para produtividade
   - Forneça snippets e templates úteis para desenvolvimento
   - Inclua dicas para debugging e testes locais

4. Um "Guia de Configuração para CI/CD" (configuracao-ci-{nome}.md) que:
   - Explique configurações necessárias para pipelines de CI/CD
   - Detalhe etapas de build, teste e deployment
   - Forneça exemplos de configuração para ambientes comuns (GitHub Actions, Jenkins, etc.)
   - Documente estratégias para otimização de pipelines

5. Um "Guia de Verificação e Troubleshooting" (verificacao-{nome}.md) que:
   - Forneça checklists para validar configuração correta
   - Detalhe problemas comuns durante setup e suas soluções
   - Explique como identificar e resolver incompatibilidades
   - Inclua recursos para suporte e escalação

Cada documento deve:
- Incluir comandos específicos e exemplos funcionais
- Considerar diferentes sistemas operacionais quando aplicável
- Conter screenshots ou diagramas para passos complexos
- Ser estruturado em formato de tutorial passo-a-passo
- Incluir tempo estimado para cada procedimento
```

##### Prompt 7: Criação de Documentação de Padrões de Código

```
Atue como um Arquiteto de Software especializado em padrões de código e convenções de desenvolvimento. Estou precisando documentar os padrões de código implementados/utilizados na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Padrões existentes: .agent/padroes-codigo/{tecnologia}/*.md
- ADRs relevantes: .agent/contexto/arquitetura/adrs/*.md
- Diretrizes arquiteturais: .agent/contexto/arquitetura/visao/manifesto-arquitetural.md
- Implementação atual: [código relacionado à tarefa]

Por favor, gere documentação abrangente de padrões de código para armazenamento em '.agent/contexto/documentacao/padroes-codigo/' que inclua:

1. Um documento "Padrões de Design Aplicados" (padroes-design-{contexto}.md) que:
   - Catalogue padrões de design utilizados (Factory, Repository, etc.)
   - Explique como e onde cada padrão foi aplicado
   - Ilustre exemplos concretos da implementação atual
   - Detalhe benefícios específicos obtidos com cada padrão

2. Um documento "Convenções de Codificação" (convencoes-{tecnologia}.md) que:
   - Detalhe convenções de nomenclatura para diferentes elementos
   - Explique estrutura de diretórios e organização de arquivos
   - Documente formatação e estilo de código esperados
   - Inclua exemplos de conformidade vs. não-conformidade

3. Um documento "Práticas Recomendadas" (praticas-recomendadas-{contexto}.md) que:
   - Liste práticas de programação preferidas no contexto específico
   - Explique abordagens para tratamento de erros, logging, etc.
   - Detalhe considerações de performance e segurança
   - Inclua exemplos concretos de implementações ideais

4. Um documento "Anti-padrões a Evitar" (anti-padroes-{contexto}.md) que:
   - Identifique práticas problemáticas no contexto específico
   - Explique os riscos e problemas associados a cada anti-padrão
   - Forneça alternativas e abordagens corretas
   - Inclua exemplos de refatoração de código problemático

5. Um documento "Guidelines para Revisão de Código" (guidelines-revisao-{contexto}.md) que:
   - Detalhe aspectos específicos a verificar durante revisões
   - Forneça checklists por categoria (segurança, performance, etc.)
   - Explique como fornecer feedback construtivo
   - Inclua exemplos de bons comentários de revisão

Cada documento deve:
- Incluir exemplos de código real e concreto do projeto
- Referenciar explicitamente padrões da indústria quando aplicável
- Explicar não apenas "como" mas "por que" certos padrões são preferidos
- Considerar trade-offs e exceções às regras gerais
- Incluir links para recursos adicionais de aprendizado
```

##### Prompt 8: Desenvolvimento de Documentação de Testes

```
Atue como um Engenheiro de Qualidade especializado em estratégias e documentação de testes. Estou precisando documentar a abordagem de testes implementada na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md
- Requisitos da funcionalidade: .agent/tasks/TASK-{número}.md
- Padrões de teste: .agent/padroes-codigo/testes/{tecnologia}/*.md
- Implementação atual: [código de teste relacionado à tarefa]

Por favor, gere documentação completa sobre testes para armazenamento em '.agent/contexto/documentacao/testes/' que inclua:

1. Um documento "Estratégia de Testes" (estrategia-testes-{nome}.md) que:
   - Explique a abordagem geral para testar esta funcionalidade
   - Detalhe os tipos de testes implementados (unitários, integração, etc.)
   - Documente a cobertura de testes esperada e alcançada
   - Explique decisões específicas sobre o que testar e o que não testar

2. Um documento "Guia de Testes Unitários" (testes-unitarios-{nome}.md) que:
   - Catalogue os cenários de teste unitário implementados
   - Explique abordagens para mocking e isolamento
   - Detalhe padrões utilizados (Arrange-Act-Assert, Given-When-Then)
   - Inclua exemplos de testes para diferentes tipos de componentes

3. Um documento "Guia de Testes de Integração" (testes-integracao-{nome}.md) que:
   - Explique interfaces e componentes testados em conjunto
   - Detalhe configuração do ambiente de teste de integração
   - Documente dependências externas e estratégias de mockup
   - Inclua exemplos de testes para fluxos críticos

4. Um documento "Testes Especializados" (testes-especializados-{nome}.md) que:
   - Documente testes de performance, segurança, acessibilidade, etc.
   - Explique ferramentas e metodologias específicas utilizadas
   - Detalhe métricas e critérios de sucesso para cada tipo de teste
   - Inclua procedimentos para execução manual quando aplicável

5. Um documento "Guia de Manutenção de Testes" (manutencao-testes-{nome}.md) que:
   - Explique como manter os testes ao longo do tempo
   - Detalhe procedimentos para atualização de testes quando a funcionalidade mudar
   - Documente abordagem para debug de testes falhos
   - Inclua boas práticas para evolução da suite de testes

Cada documento deve:
- Incluir exemplos concretos de código de teste
- Explicar claramente o propósito de cada teste ou grupo de testes
- Fornecer contexto sobre como os testes validam requisitos específicos
- Detalhar procedimentos para execução de testes localmente
- Explicar como interpretar resultados e falhas de teste
```

##### Prompt 9: Criação de Guias para Consumer-Facing APIs

```
Atue como um Developer Advocate especializado em documentação para desenvolvedores externos. Estou precisando criar documentação voltada para consumidores da API/SDK desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Especificação da API/SDK: .agent/contexto/arquitetura/design-tecnico/especificacao-interfaces-api.md
- Casos de uso: .agent/contexto/requisitos/casos-uso.md
- Exemplos de integração: [exemplos existentes]
- Feedback de usuários: [se disponível]

Por favor, gere documentação completa para desenvolvedores externos, a ser armazenada em '.agent/contexto/documentacao/consumidores/' que inclua:

1. Um "Guia de Início Rápido" (quickstart-{nome}.md) que:
   - Forneça um overview conciso da API/SDK
   - Guie a implementação de um cenário básico em menos de 5 minutos
   - Inclua exemplos de código mínimos mas funcionais
   - Destaque benefícios imediatos para mostrar valor rapidamente

2. Um "Guia de Conceitos" (conceitos-{nome}.md) que:
   - Explique os conceitos fundamentais e terminologia específica
   - Ilustre a arquitetura de alto nível da solução
   - Detalhe o modelo mental necessário para uso efetivo
   - Relacione conceitos com casos de uso comuns

3. Um "Catálogo de Exemplos" (exemplos-{nome}.md) que:
   - Forneça exemplos de código completos para diversos cenários
   - Cubra casos de uso simples até avançados
   - Inclua exemplos para diferentes linguagens/frameworks
   - Forneça código pronto para ser copiado e adaptado

4. Um "Guia de Migração e Versionamento" (migracao-{nome}.md) que:
   - Explique a política de versionamento e compatibilidade
   - Detalhe procedimentos para migração entre versões
   - Documente breaking changes e deprecações
   - Inclua exemplos de código antes/depois para mudanças significativas

5. Um "FAQ e Troubleshooting" (faq-{nome}.md) que:
   - Antecipe perguntas frequentes baseadas em pontos de confusão comuns
   - Forneça soluções para problemas recorrentes
   - Explique erros comuns e como corrigi-los
   - Inclua um guia de diagnóstico para questões mais complexas

Cada documento deve:
- Usar linguagem clara e acessível, evitando jargão interno
- Incluir exemplos funcionais e completos
- Fornecer fragmentos de código prontos para uso
- Considerar diferentes níveis de experiência dos consumidores
- Incluir links para recursos adicionais (referência completa, suporte, etc.)
```

##### Prompt 10: Geração de Documentação de Arquitetura de Dados

```
Atue como um Arquiteto de Dados especializado em modelagem e documentação de dados. Estou precisando documentar a arquitetura de dados implementada na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Modelo de dados: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md
- Fluxos de dados: .agent/contexto/arquitetura/dados/fluxos-dados.md
- Requisitos de dados: .agent/contexto/requisitos/matriz-requisitos-funcionais.md
- Implementação atual: [esquemas, migrações ou código relevante]

Por favor, gere documentação completa de arquitetura de dados para armazenamento em '.agent/contexto/documentacao/dados/' que inclua:

1. Um documento "Modelo de Dados" (modelo-dados-{contexto}.md) que:
   - Ilustre o modelo entidade-relacionamento completo
   - Detalhe cada entidade com seus atributos, tipos e restrições
   - Explique relações, cardinalidades e dependências
   - Documente índices, partições e outras otimizações de armazenamento

2. Um documento "Dicionário de Dados" (dicionario-dados-{contexto}.md) que:
   - Liste todas as entidades e atributos em formato tabular
   - Forneça descrições claras do significado de negócio de cada campo
   - Documente formatos, validações e valores default
   - Inclua exemplos de dados válidos para campos complexos

3. Um documento "Fluxos de Transformação" (transformacoes-dados-{contexto}.md) que:
   - Mapeie as transformações de dados ao longo do ciclo de vida
   - Explique processos de ETL, agregações e derivações
   - Documente regras de negócio aplicadas durante transformações
   - Detalhe gatilhos e eventos que iniciam processamentos

4. Um documento "Estratégia de Persistência" (persistencia-{contexto}.md) que:
   - Explique escolhas de armazenamento (relacional, NoSQL, etc.)
   - Detalhe estratégias de caching e sua invalidação
   - Documente políticas de retenção e arquivamento
   - Explique abordagens para evolução de schema

5. Um documento "Governança e Qualidade" (governanca-dados-{contexto}.md) que:
   - Defina procedimentos para garantir integridade dos dados
   - Explique estratégias para detectar e corrigir inconsistências
   - Documente métricas de qualidade e processos de monitoramento
   - Detalhe aspectos de segurança e privacidade específicos por categoria de dados

Cada documento deve:
- Incluir diagramas claros usando notação padronizada (ER, UML, etc.)
- Referenciar padrões da indústria e melhores práticas adotadas
- Explicar raciocínio por trás de decisões de modelagem e trade-offs
- Incluir considerações de performance e escalabilidade
- Fornecer exemplos concretos para conceitos complexos
```

##### Prompt 11: Documentação de Processos de Release e Deployment

```
Atue como um Especialista DevOps com foco em processos de release e implantação. Estou precisando documentar os procedimentos de release/deployment para o componente implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Estratégia de implantação: .agent/contexto/implantacao/documentos-estrategia/documento-estrategia.md
- Pipeline de CI/CD: .agent/contexto/implantacao/automacao-implantacao/*.md
- Feature flags: .agent/contexto/implantacao/artefatos-implantacao-gradual/configuracoes-feature-toggles.md
- Requisitos operacionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md

Por favor, gere documentação completa de release e deployment para armazenamento em '.agent/contexto/documentacao/releases/' que inclua:

1. Um "Guia de Processo de Release" (processo-release-{nome}.md) que:
   - Detalhe o fluxo completo desde commit até produção
   - Explique gates, aprovações e verificações em cada etapa
   - Documente papéis e responsabilidades durante o processo
   - Inclua cronograma típico e cadência de releases

2. Um "Manual de Deployment" (manual-deployment-{nome}.md) que:
   - Forneça instruções passo-a-passo para executar deployments
   - Detalhe comandos específicos, parâmetros e configurações
   - Explique procedimentos para diferentes ambientes
   - Inclua verificações pós-deployment para validar sucesso

3. Um "Plano de Rollback" (plano-rollback-{nome}.md) que:
   - Defina critérios claros para decisão de rollback
   - Detalhe procedimentos completos de reversão
   - Explique impactos de rollback em componentes dependentes
   - Inclua checklists e verificações pós-rollback

4. Um "Guia de Feature Flags" (feature-flags-{nome}.md) que:
   - Catalogue feature flags implementados e seus propósitos
   - Explique estratégias para teste gradual com flags
   - Detalhe processo de remoção de flags após adoção completa
   - Inclua procedimentos para troubleshooting relacionado a flags

5. Um "Guia de Releases para Stakeholders" (release-stakeholders-{nome}.md) que:
   - Explique o processo de forma acessível para não-técnicos
   - Detalhe como acompanhar o progresso de releases
   - Documente processos para solicitação de hotfixes
   - Inclua templates para notas de release e comunicações

Cada documento deve:
- Incluir diagramas de fluxo claros para processos complexos
- Fornecer comandos e scripts específicos quando aplicável
- Detalhar procedimentos para cenários excepcionais e de emergência
- Incluir métricas e KPIs para avaliar sucesso de releases
- Considerar integrações com sistemas de notificação e monitoramento
```

##### Prompt 12: Criação de Documentação de Segurança e Compliance

```
Atue como um Especialista em Segurança de Aplicações e Compliance. Estou precisando documentar aspectos de segurança e conformidade para o sistema/componente implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Modelo de ameaças: .agent/contexto/arquitetura/seguranca-privacidade/modelo-ameacas.md
- Requisitos de compliance: .agent/contexto/seguranca-compliance/conformidade-regulatoria.md
- Estratégias de mitigação: .agent/contexto/arquitetura/seguranca-privacidade/estrategias-mitigacao.md
- Padrões de segurança: .agent/padroes-codigo/seguranca/{tecnologia}/*.md

Por favor, gere documentação completa de segurança e compliance para armazenamento em '.agent/contexto/documentacao/seguranca/' que inclua:

1. Um "Overview de Segurança" (overview-seguranca-{nome}.md) que:
   - Resuma a postura de segurança do componente/sistema
   - Explique principais riscos e como são mitigados
   - Detalhe controles de segurança implementados
   - Inclua resultados de avaliações de segurança realizadas

2. Um documento "Matriz de Controles de Segurança" (controles-seguranca-{nome}.md) que:
   - Catalogue todos os controles de segurança implementados
   - Mapeie controles para ameaças e vulnerabilidades específicas
   - Referencie frameworks de segurança relevantes (OWASP, NIST, etc.)
   - Inclua evidências de implementação para cada controle

3. Um "Guia de Hardening" (hardening-{nome}.md) que:
   - Detalhe configurações de segurança recomendadas
   - Explique procedimentos para redução de superfície de ataque
   - Documente guidelines para configuração segura em diferentes ambientes
   - Inclua checklists de verificação de segurança

4. Um documento "Gestão de Dados Sensíveis" (dados-sensiveis-{nome}.md) que:
   - Identifique categorias de dados sensíveis processados
   - Explique medidas de proteção específicas por categoria
   - Detalhe ciclo de vida de dados sensíveis (coleta, processamento, exclusão)
   - Documente procedimentos para tratamento de violações

5. Um documento "Guia de Auditoria e Compliance" (auditoria-compliance-{nome}.md) que:
   - Explique requisitos regulatórios aplicáveis
   - Detalhe logs de auditoria implementados e sua finalidade
   - Documente procedimentos para resposta a auditorias
   - Inclua matriz de evidências para demonstrar conformidade

Cada documento deve:
- Usar linguagem precisa e alinhada com padrões da indústria
- Incluir referências a frameworks e regulações específicas
- Fornecer exemplos concretos de implementações de segurança
- Considerar diferentes contextos de deployment (on-prem, cloud, etc.)
- Incluir procedimentos para verificação e validação contínua
```

##### Prompt 13: Geração de Manuais do Desenvolvedor

```
Atue como um Developer Experience Lead especializado em documentação interna. Estou precisando criar um manual do desenvolvedor para o componente/sistema implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Arquitetura do sistema: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Padrões de código: .agent/padroes-codigo/{tecnologia}/*.md
- ADRs relevantes: .agent/contexto/arquitetura/adrs/*.md
- Fluxos de desenvolvimento: .agent/contexto/requisitos/casos-uso.md

Por favor, gere um manual do desenvolvedor abrangente para armazenamento em '.agent/contexto/documentacao/desenvolvedor/' que inclua:

1. Um documento "Introdução ao Sistema" (introducao-{nome}.md) que:
   - Forneça uma visão geral do propósito e funcionalidades do sistema
   - Explique a arquitetura de alto nível e principais componentes
   - Detalhe o modelo de domínio e conceitos fundamentais
   - Inclua diagrama arquitetural com explicações claras

2. Um documento "Ambiente de Desenvolvimento" (ambiente-desenvolvimento-{nome}.md) que:
   - Detalhe o setup completo do ambiente local
   - Explique ferramentas e configurações necessárias
   - Documente estrutura de diretórios e organização do código
   - Inclua dicas de produtividade e configurações recomendadas

3. Um documento "Guia de Contribuição" (guia-contribuicao-{nome}.md) que:
   - Explique o processo completo de desenvolvimento
   - Detalhe conventions de código e padrões a seguir
   - Documente o processo de revisão e merge
   - Inclua checklists de qualidade para submissão de código

4. Um documento "Arquitetura e Design" (arquitetura-design-{nome}.md) que:
   - Detalhe os padrões de design utilizados
   - Explique decisões arquiteturais e seus fundamentos
   - Documente subsistemas e suas responsabilidades
   - Inclua diagramas detalhados com explicações

5. Um documento "APIs e Interfaces" (apis-interfaces-{nome}.md) que:
   - Catalogue todas as APIs internas e externas
   - Detalhe contratos e convenções de comunicação
   - Explique mecanismos de autenticação e autorização
   - Inclua exemplos de uso para casos comuns

6. Um documento "Troubleshooting para Desenvolvedores" (troubleshooting-dev-{nome}.md) que:
   - Liste problemas comuns durante desenvolvimento
   - Forneça soluções para erros frequentes
   - Detalhe ferramentas e técnicas de debugging
   - Inclua recursos para aprofundamento e aprendizado

Cada documento deve:
- Ser escrito para audiência técnica mas acessível para novos desenvolvedores
- Incluir exemplos de código e snippets quando relevante
- Fornecer links para resources adicionais e documentação relacionada
- Usar diagramas e visualizações para conceitos complexos
- Incluir seções "Perguntas Frequentes" para pontos recorrentes
```

##### Prompt 14: Documentação de Evolução e Versões

```
Atue como um Release Manager com experiência em documentação de mudanças e versionamento. Estou precisando documentar a evolução e histórico de versões para o componente implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Histórico de mudanças: [histórico de commits/PRs relevantes]
- Requisitos implementados: .agent/tasks/TASK-{número}.md
- Roadmap técnico: .agent/contexto/arquitetura/evolucao/roadmap-tecnico.md (se disponível)
- Política de versionamento: .agent/contexto/arquitetura/integracao/contratos-governanca.md

Por favor, gere documentação completa de evolução e versões para armazenamento em '.agent/contexto/documentacao/versoes/' que inclua:

1. Um "Changelog Detalhado" (changelog-{nome}.md) que:
   - Liste todas as mudanças de forma estruturada por versão
   - Categorize mudanças (features, fixes, breaking changes, etc.)
   - Referencie requisitos e tickets relacionados a cada mudança
   - Inclua datas de lançamento e responsáveis por cada versão

2. Um documento "Política de Versionamento" (versionamento-{nome}.md) que:
   - Explique a estratégia de versionamento (Semântico, Calendário, etc.)
   - Detalhe critérios para incrementos de versão
   - Documente ciclo de vida de diferentes versões (suporte, manutenção)
   - Inclua procedimentos para deprecação e descontinuação

3. Um documento "Release Notes" (release-notes-{nome}.md) que:
   - Forneça descrições orientadas a usuário para cada versão
   - Destaque mudanças significativas e seus benefícios
   - Documente instruções de migração quando aplicável
   - Inclua screenshots ou demonstrações de novas funcionalidades

4. Um documento "Roadmap e Planejamento" (roadmap-{nome}.md) que:
   - Detalhe o plano de evolução futura do componente
   - Explique prioridades e timelines esperadas
   - Documente dependências e pré-requisitos para futuros desenvolvimentos
   - Inclua processo para sugestão e priorização de novas funcionalidades

5. Um documento "Compatibilidade e Migrações" (compatibilidade-{nome}.md) que:
   - Explique compatibilidade entre diferentes versões
   - Detalhe procedimentos de migração passo a passo
   - Documente scripts e ferramentas para auxiliar migrações
   - Inclua considerações especiais para atualizações críticas

Cada documento deve:
- Seguir formato consistente e facilmente atualizável
- Incluir datas específicas e identificadores de versão
- Referenciar tickets, PRs ou commits relevantes
- Usar linguagem clara que explique o impacto das mudanças
- Considerar diferentes audiências (desenvolvedores, operações, usuários)
```

##### Prompt 15: Documentação de Monitoramento e Métricas

```
Atue como um Especialista em Observabilidade com foco em documentação de monitoramento. Estou precisando documentar o sistema de monitoramento e métricas implementado na TASK-{número} (.agent/tasks/TASK-{número}.md).

Referências essenciais:
- Estratégia de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Catálogo de métricas: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Requisitos operacionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Implementação de telemetria: [código relevante de instrumentação]

Por favor, gere documentação completa de monitoramento para armazenamento em '.agent/contexto/documentacao/monitoramento/' que inclua:

1. Um "Guia de Observabilidade" (guia-observabilidade-{nome}.md) que:
   - Explique a abordagem geral para monitoramento do sistema
   - Detalhe os tipos de telemetria implementados (logs, métricas, traces)
   - Documente infraestrutura de observabilidade e ferramentas utilizadas
   - Inclua princípios e melhores práticas adotados

2. Um "Catálogo de Métricas" (catalogo-metricas-{nome}.md) que:
   - Liste todas as métricas coletadas com descrições detalhadas
   - Categorize métricas por finalidade (performance, negócio, saúde)
   - Documente fórmulas de cálculo e significado dos valores
   - Inclua valores esperados e thresholds para cada métrica

3. Um "Guia de Dashboards" (dashboards-{nome}.md) que:
   - Catalogue todos os dashboards disponíveis
   - Explique o propósito e audiência de cada dashboard
   - Detalhe como interpretar diferentes visualizações
   - Inclua screenshots anotados e casos de uso para cada dashboard

4. Um documento "Sistema de Alertas" (alertas-{nome}.md) que:
   - Liste todos os alertas configurados com descrições
   - Explique condições de trigger e thresholds
   - Documente procedimentos de resposta para cada alerta
   - Inclua informações sobre silenciamento e escalação

5. Um documento "Logging e Análise" (logging-{nome}.md) que:
   - Detalhe a estrutura e formato dos logs gerados
   - Explique níveis de logging e seu uso apropriado
   - Documente técnicas para consulta e análise de logs
   - Inclua exemplos de consultas para cenários comuns

Cada documento deve:
- Relacionar monitoramento com objetivos de negócio e SLOs
- Incluir exemplos visuais de dashboards e alertas
- Fornecer instruções precisas para navegação em ferramentas de observabilidade
- Detalhar procedimentos para troubleshooting usando telemetria
- Considerar diferentes perfis de usuários (desenvolvedores, operações, negócio)
```

A aplicação destes prompts especializados, potencializada pelo GitHub Copilot, transforma a documentação técnica de um processo tipicamente tedioso e frequentemente negligenciado em um fluxo sistemático e eficiente que produz artefatos de conhecimento de alta qualidade. Esta abordagem estruturada não apenas documenta o sistema como ele é hoje, mas estabelece as bases para sua manutenção, evolução e transferência de conhecimento contínuas, constituindo um multiplicador de eficiência para equipes técnicas em todo o ciclo de vida do produto.

O uso sistemático destes prompts durante a fase de documentação permite a criação de uma base documental robusta e abrangente que serve como referência autoritativa para desenvolvedores, operadores e stakeholders, reduzindo significativamente o tempo necessário para onboarding, diagnóstico de problemas e tomadas de decisão técnicas, enquanto preserva o conhecimento institucional que tipicamente seria perdido com a rotatividade natural de equipes.

### 10. Estratégia de Implantação

A metodologia estruturada para implantação transcende abordagens simplistas de deploy, implementando um framework multidimensional que trata lançamentos como operações críticas meticulosamente planejadas e rigorosamente executadas. Esta fase aplica princípios avançados de engenharia de confiabilidade para criar processos de transição que minimizam riscos, garantem validação incremental, e estabelecem capacidades robustas de reversão caso necessário.

Com o suporte do GitHub Copilot, equipes DevOps e desenvolvimento elaboram estratégias de implantação sofisticadas que consideram complexidades do ambiente, dependências entre componentes, e requisitos de continuidade de negócio. O processo incorpora perspectivas complementares de Engenheiros DevOps, Especialistas em SRE (Site Reliability Engineering), e Gestores de Operações que colaboram para construir uma abordagem holística que equilibra velocidade de entrega com estabilidade operacional.

O resultado é um sistema de implantação altamente controlado que permite introdução segura de novas funcionalidades em ambientes de produção, através de técnicas avançadas como implantação canário, lançamentos graduais, e feature toggles. Esta metodologia estabelece um equilíbrio cuidadoso entre inovação e estabilidade, permitindo validação em cenários reais enquanto mantém capacidade de mitigação rápida de problemas não detectados em ambientes de pré-produção.

A fase culmina na criação de artefatos de implantação abrangentes, organizados na pasta `.agent/contexto/implantacao`:

### 10.1. Documentos de Estratégia de Implantação:

- Documento de Estratégia detalhando abordagem geral, fases e gates de aprovação
- Matriz de Riscos de Implantação identificando cenários potenciais e mitigações
- Plano de Comunicação para gerenciamento de stakeholders durante o processo
- Definição de Métricas de Sucesso e critérios objetivos para avaliação pós-implantação

### 10.2. Artefatos de Implantação Gradual:

- Configurações de Feature Toggles para controle granular de funcionalidades
- Definição de Segmentos de Usuários para lançamentos progressivos (canary/beta)
- Plano de Rollout detalhando percentuais e critérios para expansão incremental
- Estratégia de Dark Launching para testar componentes críticos sob carga real

### 10.3. Documentos de Monitoramento e Validação:

- Dashboards de Monitoramento específicos para a nova funcionalidade
- Lista de Verificação de Validação Pós-Implantação com testes críticos
- Definição de Alertas específicos para detecção precoce de problemas
- Arquitetura de Telemetria para captura de métricas de performance e uso

### 10.4. Planos de Contingência:

- Procedimentos de Rollback detalhados com pontos de decisão claros
- Runbooks de Mitigação para problemas antecipados
- Árvores de Decisão para escalonamento e resposta a incidentes
- Lista de Contatos e Responsabilidades durante períodos críticos pós-implantação

### 10.5. Automação de Implantação:

- Scripts de Implantação e Verificação automatizados
- Pipelines de CI/CD configurados com gates de aprovação apropriados
- Testes de Smoke configurados para validação rápida pós-implantação
- Automação de Rollback para reversão rápida quando necessário

### 10.6. Prompts Otimizados para Estratégia de Implantação

A criação de artefatos de implantação é significativamente potencializada pelo uso de prompts especializados do GitHub Copilot. Abaixo, apresentamos diversos prompts otimizados, cada um focado em uma categoria específica de artefatos de implantação:

##### Prompt 1: Geração de Documento de Estratégia de Implantação

```
Atue como um DevOps Architect especializado em estratégias de implantação para sistemas críticos. Estou planejando a implantação da funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso desenvolver uma estratégia de implantação abrangente.

Referências essenciais:
- Descrição da funcionalidade: .agent/tasks/TASK-{número}.md
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Arquitetura afetada: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Dependências de sistemas: .agent/contexto/tecnico/mapa-sistemas.md
- Padrões de deploy: .agent/padroes-codigo/devops/estrategias-deploy.md

Por favor, gere um documento completo de estratégia de implantação para armazenamento em '.agent/contexto/implantacao/documentos-estrategia/' que inclua:

1. Um "Documento de Estratégia de Implantação" (documento-estrategia.md) que:
   - Analise as características da funcionalidade e recomende uma abordagem de implantação específica (blue/green, canary, feature toggles, etc.)
   - Justifique a escolha com base nos requisitos, riscos e impacto nos sistemas existentes
   - Detalhe fases de implantação com critérios claros para progressão entre fases
   - Defina gates de aprovação e responsáveis por decisões em cada estágio

2. Uma "Matriz de Riscos de Implantação" (matriz-riscos.md) que:
   - Identifique todos os riscos potenciais específicos para esta implantação
   - Classifique riscos por probabilidade e impacto usando framework definido em .agent/padroes-codigo/devops/avaliacao-riscos.md
   - Detalhe estratégias de mitigação para cada risco identificado
   - Defina indicadores de alerta precoce para monitoramento durante implantação

3. Um "Plano de Comunicação de Implantação" (plano-comunicacao.md) que:
   - Identifique todos os stakeholders impactados pela implantação
   - Defina templates e canais de comunicação para diferentes estágios (pré-implantação, durante, pós-implantação)
   - Estabeleça procedimentos para comunicação de emergência em caso de problemas
   - Detalhe responsabilidades de comunicação e escalação

4. Uma "Definição de Métricas de Sucesso" (metricas-sucesso.md) que:
   - Estabeleça KPIs técnicos e de negócio para avaliar o sucesso da implantação
   - Defina baselines e thresholds para cada métrica
   - Detalhe métodos de coleta e período de avaliação
   - Estabeleça critérios objetivos para declarar a implantação bem-sucedida

5. Um "Cronograma de Implantação" (cronograma.md) que:
   - Proponha datas e horários ideais considerando padrões de tráfego e disponibilidade de recursos
   - Detalhe duração estimada de cada fase com buffers apropriados
   - Identifique dependências temporais e janelas críticas
   - Estabeleça períodos de congelamento antes e depois de datas críticas de negócio

Cada documento deve incluir:
- Referências explícitas a requisitos específicos da TASK-{número}
- Considerações sobre o ambiente técnico documentado em .agent/contexto/tecnico/
- Alinhamento com padrões organizacionais definidos em .agent/padroes-codigo/devops/
- Identificação clara de responsabilidades e pontos de decisão
- Procedimentos para abortar a implantação se necessário
```

##### Prompt 2: Criação de Plano de Implantação Gradual e Feature Toggles

```
Atue como um Especialista em Feature Management e Implantação Gradual. Estou implementando a funcionalidade descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso de uma estratégia para lançamento gradual e controlado.

Referências essenciais:
- Detalhes da funcionalidade: .agent/tasks/TASK-{número}.md
- Segmentação de usuários: .agent/contexto/usuario/personas-primarias.md
- Arquitetura de componentes: .agent/contexto/arquitetura/visao/visao-componentes.md
- Padrões de feature toggles: .agent/padroes-codigo/devops/implementacao-feature-flags.md
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md

Por favor, crie documentação abrangente para implantação gradual para armazenamento em '.agent/contexto/implantacao/artefatos-implantacao-gradual/' que inclua:

1. Um documento "Estratégia de Feature Toggles" (estrategia-feature-toggles.md) que:
   - Identifique componentes da funcionalidade que devem ser controlados por feature flags
   - Recomende granularidade apropriada de toggles (por feature, sub-feature, ou comportamento)
   - Defina tipos de toggles necessários (release, experiment, ops, permission)
   - Explique estratégia de implementação e tecnologia recomendada conforme .agent/padroes-codigo/devops/implementacao-feature-flags.md

2. Um documento "Configurações de Feature Toggles" (configuracoes-feature-toggles.md) que:
   - Detalhe todas as flags a serem criadas com nomes, comportamentos default e descrições
   - Defina regras de targeting para cada toggle
   - Especifique comportamentos de fallback em caso de problemas
   - Inclua exemplos de configuração para cada ambiente (dev, staging, prod)

3. Um documento "Plano de Segmentação de Usuários" (segmentacao-usuarios.md) que:
   - Defina segmentos de usuários para rollout gradual baseado em .agent/contexto/usuario/personas-primarias.md
   - Estabeleça critérios para seleção de usuários beta/canary
   - Recomende porcentagens para cada fase de rollout
   - Defina critérios para expansão ou suspensão do rollout

4. Um documento "Plano de Rollout Detalhado" (plano-rollout.md) que:
   - Estabeleça fases claras de rollout com porcentagens e durações
   - Defina métricas a monitorar em cada fase
   - Especifique critérios de sucesso para progressão entre fases
   - Detalhe procedimentos para pausar ou reverter o rollout

5. Um documento "Estratégia de Dark Launching" (dark-launching.md) que:
   - Identifique componentes apropriados para dark launching
   - Detalhe métodos para capturar e analisar comportamento sem impactar usuários
   - Defina métricas para comparação com comportamento atual
   - Estabeleça critérios para transição de dark launch para disponibilidade real

Cada documento deve:
- Referenciar especificamente componentes descritos na TASK-{número}
- Alinhar-se com a arquitetura documentada em .agent/contexto/arquitetura/
- Considerar o impacto em sistemas integrados conforme .agent/contexto/tecnico/mapa-sistemas.md
- Incluir procedimentos para rollback de cada fase se necessário
- Detalhar responsabilidades para decisões de progressão de fases
```

##### Prompt 3: Desenvolvimento de Estratégia de Monitoramento para Implantação

```
Atue como um Especialista em Observabilidade e Monitoramento com foco em validação de implantações. Estou planejando o lançamento da funcionalidade descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso de uma estratégia abrangente para monitorar e validar a implantação.

Referências essenciais:
- Funcionalidade a ser implantada: .agent/tasks/TASK-{número}.md
- Estratégia de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Padrões de monitoramento: .agent/padroes-codigo/devops/monitoramento-alertas.md
- Modelo de ameaças: .agent/contexto/arquitetura/seguranca-privacidade/modelo-ameacas.md (se aplicável)

Por favor, desenvolva documentação detalhada de monitoramento e validação para armazenamento em '.agent/contexto/implantacao/monitoramento-validacao/' que inclua:

1. Um documento "Estratégia de Monitoramento de Implantação" (estrategia-monitoramento.md) que:
   - Identifique todas as métricas críticas a serem monitoradas durante e após implantação
   - Categorize métricas por tipo (performance, negócio, infraestrutura, experiência de usuário)
   - Defina baselines e thresholds de alerta para cada métrica
   - Recomende períodos de observação e frequência de coleta

2. Um documento "Configuração de Dashboards" (configuracao-dashboards.md) que:
   - Especifique dashboards a serem criados para diferentes audiências (técnica, negócios, operações)
   - Detalhe visualizações específicas para cada dashboard com justificativas
   - Inclua queries e configurações para implementação dos dashboards
   - Defina layouts otimizados para monitoramento durante implantação

3. Uma "Lista de Verificação de Validação" (verificacao-validacao.md) que:
   - Enumere todos os testes manuais e automatizados a serem executados após cada fase de implantação
   - Priorize verificações por criticidade
   - Defina critérios de aceitação específicos para cada verificação
   - Inclua procedimentos detalhados para execução de cada teste

4. Um documento "Configuração de Alertas" (configuracao-alertas.md) que:
   - Defina todos os alertas necessários durante o período de implantação
   - Especifique condições de trigger, severidade e fluxo de notificação
   - Estabeleça procedimentos de resposta inicial para cada tipo de alerta
   - Defina mecanismos para prevenir alert fatigue durante a implantação

5. Um documento "Arquitetura de Telemetria" (arquitetura-telemetria.md) que:
   - Detalhe a instrumentação específica necessária para esta funcionalidade
   - Especifique eventos de negócio a serem registrados para análise posterior
   - Defina estratégias para correlacionar telemetria entre componentes
   - Recomende retenção de dados e estratégias de análise

Cada documento deve:
- Referenciar diretamente requisitos e métricas de sucesso definidos na TASK-{número}
- Alinhar-se com a estratégia global de observabilidade em .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md
- Considerar diferentes fases de implantação conforme o plano de rollout
- Incluir procedimentos específicos para identificar problemas precocemente
- Detalhar responsabilidades para monitoramento e ação durante o período crítico
```

##### Prompt 4: Elaboração de Planos de Contingência e Rollback

```
Atue como um Especialista em Resiliência de Sistemas e Gestão de Incidentes. Estou planejando a implantação da funcionalidade descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso desenvolver planos abrangentes de contingência e rollback para mitigar riscos.

Referências essenciais:
- Detalhes da implementação: .agent/tasks/TASK-{número}.md
- Matriz de riscos: .agent/contexto/implantacao/documentos-estrategia/matriz-riscos.md
- Arquitetura do sistema: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Padrões de resiliência: .agent/padroes-codigo/devops/procedimentos-incidentes.md
- Dependências técnicas: .agent/contexto/tecnico/mapa-sistemas.md

Por favor, desenvolva documentação detalhada de contingência para armazenamento em '.agent/contexto/implantacao/planos-contingencia/' que inclua:

1. Um "Plano de Rollback Detalhado" (plano-rollback.md) que:
   - Especifique procedimentos passo-a-passo para reverter a implantação em cada fase
   - Detalhe comandos específicos, scripts ou procedimentos para cada componente
   - Defina tempos estimados para conclusão de rollback em diferentes cenários
   - Estabeleça procedimentos para validação pós-rollback

2. Um documento "Runbooks de Mitigação" (runbooks-mitigacao.md) que:
   - Catalogue problemas potenciais específicos para esta funcionalidade
   - Forneça procedimentos detalhados para mitigação sem rollback completo
   - Inclua troubleshooting para problemas comuns antecipados
   - Defina ações temporárias para manter serviços críticos funcionando

3. Uma "Árvore de Decisão para Escalonamento" (arvore-decisao.md) que:
   - Defina critérios objetivos para diferentes níveis de resposta a problemas
   - Estabeleça thresholds claros para acionar rollback vs. mitigação
   - Detalhe fluxo de escalonamento e autoridades para decisões críticas
   - Inclua templates para documentação de decisões durante incidentes

4. Um documento "Matriz de Responsabilidades" (matriz-responsabilidades.md) que:
   - Identifique todas as funções necessárias durante resposta a incidentes
   - Especifique responsáveis primários e backups para cada função
   - Detalhe responsabilidades específicas durante o período crítico
   - Inclua informações de contato e disponibilidade

5. Um "Plano de Comunicação de Incidentes" (comunicacao-incidentes.md) que:
   - Defina canais de comunicação para diferentes severidades de problemas
   - Estabeleça templates para comunicações internas e externas
   - Detalhe procedimentos para atualizações regulares durante incidentes
   - Inclua estratégias para comunicação com usuários afetados

Cada documento deve:
- Ser baseado nas características específicas da funcionalidade na TASK-{número}
- Considerar o impacto nos sistemas interconectados conforme .agent/contexto/tecnico/mapa-sistemas.md
- Incluir procedimentos que minimizem impacto ao usuário final
- Definir critérios claros para ações e pontos de decisão
- Incluir checklists práticas e procedimentos passo-a-passo para uso durante situações de estresse
```

##### Prompt 5: Desenvolvimento de Configurações de CI/CD

```
Atue como um DevOps Engineer especializado em automação de pipelines de CI/CD. Estou preparando a implantação da funcionalidade descrita na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso configurar pipelines automatizados para build, teste, e deploy.

Referências essenciais:
- Estrutura do código: .agent/tasks/TASK-{número}.md
- Padrões de CI/CD: .agent/padroes-codigo/devops/pipelines-cicd.md
- Estratégia de testes: .agent/contexto/arquitetura/adrs/ADR-009-testes-automatizados.md
- Ambientes de implantação: .agent/contexto/implantacao/documentos-estrategia/documento-estrategia.md
- Estratégia de branches: .agent/padroes-codigo/git/workflow-branching.md

Por favor, desenvolva configurações completas de CI/CD para armazenamento em '.agent/contexto/implantacao/automacao-implantacao/' que inclua:

1. Um documento "Pipeline de CI/CD Detalhado" (pipeline-cicd.md) que:
   - Defina todas as etapas necessárias do commit até produção
   - Especifique gates de qualidade e aprovação em cada estágio
   - Detalhe integrações com ferramentas de análise estática, testes e segurança
   - Estabeleça estratégias para paralelização e otimização de performance

2. "Configurações para GitHub Actions" (github-actions-config.md) (ou outra ferramenta relevante) que:
   - Forneça YAML completo para workflows de CI/CD
   - Inclua configurações específicas para diferentes ambientes
   - Detalhe secrets necessários e configurações de ambiente
   - Implemente estratégias para cache e otimização de velocidade

3. Um documento "Testes de Smoke Automatizados" (testes-smoke.md) que:
   - Defina suite de testes críticos para validação pós-deploy
   - Especifique implementação técnica e ferramentas
   - Detalhe thresholds de falha e procedimentos de notificação
   - Inclua estratégias para teste em diferentes ambientes

4. Um documento "Automação de Rollback" (automacao-rollback.md) que:
   - Forneça scripts e configurações para reverter automaticamente mudanças problemáticas
   - Detalhe mecanismos de trigger baseados em testes e alertas
   - Especifique fluxos de aprovação para rollbacks automáticos vs. manuais
   - Inclua procedimentos para validação pós-rollback

5. Um documento "Estratégia de Ambientes" (estrategia-ambientes.md) que:
   - Defina todos os ambientes no pipeline (dev, test, staging, prod)
   - Especifique estratégias de promoção entre ambientes
   - Detalhe diferenças de configuração por ambiente
   - Inclua procedimentos para sincronização e atualização de ambientes

Cada configuração deve:
- Ser específica para a tecnologia e estrutura utilizadas na TASK-{número}
- Seguir os padrões organizacionais definidos em .agent/padroes-codigo/devops/
- Implementar gates de qualidade alinhados com requisitos não-funcionais
- Incluir notificações apropriadas para cada estágio do pipeline
- Considerar estratégias para minimizar tempo de ciclo mantendo qualidade
```

Esta abordagem estruturada para estratégia de implantação, potencializada pelo GitHub Copilot através de prompts especializados em DevOps e SRE, transforma o processo de deploy de um evento de alto risco para uma operação meticulosamente planejada e controlada. Cada conjunto de prompts gera documentação abrangente que cobre diferentes aspectos da implantação, desde estratégia inicial até automação de CI/CD, garantindo que equipes técnicas possam executar transições suaves para ambientes produtivos com confiança, controle e capacidade de resposta rápida a quaisquer desafios imprevistos.

A aplicação sistemática destes prompts especializados durante a fase de planejamento de implantação estabelece um framework robusto que não apenas reduz riscos operacionais significativamente, mas também acelera o processo de entrega de valor ao usuário final através de automação inteligente, validação incremental e monitoramento proativo, alinhando práticas de DevOps modernas com os objetivos estratégicos da organização.

### 11. Monitoramento e Manutenção

A metodologia estruturada para monitoramento e manutenção transcende abordagens reativas tradicionais, implementando um framework multidimensional que estabelece vigilância proativa, detecção precoce de anomalias, e processos sistemáticos de evolução contínua. Esta fase aplica princípios avançados de engenharia de confiabilidade para criar um ecossistema de observabilidade abrangente que não apenas identifica problemas, mas fundamentalmente previne falhas através de análise preditiva e manutenção preventiva.

Com o suporte do GitHub Copilot, equipes de operações e desenvolvimento elaboram estratégias sofisticadas de monitoramento que consideram métricas técnicas, indicadores de experiência do usuário, e alinhamento com objetivos de negócio. O processo incorpora perspectivas complementares de Engenheiros de Confiabilidade de Site (SRE), Analistas de Operações, e Especialistas em Experiência do Usuário que colaboram para construir uma visão holística do comportamento do sistema em produção, identificando desde degradações sutis de performance até padrões emergentes de uso que sugerem oportunidades de otimização.

O resultado é um sistema de governança operacional que transforma dados brutos de telemetria em insights acionáveis, permitindo tanto resposta rápida a incidentes quanto evolução estratégica do produto. Esta metodologia estabelece um equilíbrio refinado entre estabilidade operacional e inovação contínua, mantendo excelência técnica enquanto o produto evolui para atender necessidades emergentes dos usuários.

A fase culmina na criação de artefatos operacionais abrangentes, organizados na pasta `.agent/contexto/operacoes`:

### 11.1. Documentos de Estratégia de Monitoramento:

- Arquitetura de Observabilidade detalhando métricas, logs e traces implementados
- Catálogo de Métricas-Chave com descrições, fórmulas e significado de negócio
- Matriz de Correlação relacionando sintomas observáveis a causas-raiz potenciais
- Plano de Instrumentação para evolução contínua de telemetria

### 11.2. Artefatos de Detecção e Alertas:

- Configurações de Alertas com limiares justificados por análise estatística
- Playbooks de Resposta a Incidentes para cenários críticos
- Matriz de Escalonamento definindo responsabilidades e canais de comunicação
- Dashboards de Monitoramento para diferentes audiências e perfis de uso

### 11.3. Documentos de Manutenção Preventiva:

- Cronograma de Manutenção com procedimentos recorrentes e janelas de execução
- Checklists de Verificação de Integridade para auditorias de sistema
- Estratégia de Gestão de Capacidade para planejamento de recursos
- Planos de Atualização de Dependências minimizando riscos de segurança

### 11.4. Artefatos de Solução de Problemas:

- Runbooks Detalhados para resolução de problemas comuns
- Árvores de Decisão para diagnóstico sistemático de falhas
- Biblioteca de Consultas e Scripts para investigação de problemas
- Registro Histórico de Incidentes com análises post-mortem e lições aprendidas

### 11.5. Documentos de Evolução Contínua:

- Roadmap de Otimizações baseado em dados de uso real
- Framework de Experimentação para validação de melhorias
- Plano de Refatoração Contínua para endereçar débito técnico
- Estratégia de Descontinuação para funcionalidades obsoletas

### 11.6. Prompts Otimizados para Monitoramento e Manutenção

O estabelecimento de processos robustos de monitoramento e manutenção é significativamente potencializado pelo uso de prompts especializados do GitHub Copilot. Abaixo, apresentamos diversos prompts otimizados, cada um focado em um aspecto essencial desta fase:

##### Prompt 1: Criação de Estratégia de Observabilidade Abrangente

```
Atue como um Engenheiro de Confiabilidade de Site (SRE) especializado em arquitetura de observabilidade. Estou implementando monitoramento para a funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) que utiliza as tecnologias documentadas em .agent/contexto/tecnico/mapa-sistemas.md.

Referências essenciais:
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Arquitetura do sistema: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Padrões de observabilidade: .agent/padroes-codigo/observabilidade/{framework-específico}/*.md
- ADR de observabilidade: .agent/contexto/arquitetura/adrs/ADR-005-observabilidade.md

Por favor, desenvolva documentação detalhada de estratégia de observabilidade para armazenamento em '.agent/contexto/operacoes/documentos-estrategia-monitoramento/' que inclua:

1. Um documento "Arquitetura de Observabilidade" (arquitetura-observabilidade.md) que:
   - Defina as três camadas fundamentais (métricas, logs, traces) para esta funcionalidade específica
   - Estabeleça padrões de correlação entre as camadas usando contexto e identificadores únicos
   - Especifique implementações técnicas alinhadas com .agent/padroes-codigo/observabilidade/
   - Inclua diagramas conceituais do fluxo de telemetria desde a geração até visualização

2. Um "Catálogo de Métricas-Chave" (catalogo-metricas-chave.md) que:
   - Defina métricas técnicas e de negócio específicas para esta funcionalidade
   - Categorize métricas usando o framework RED (Rate, Errors, Duration) para serviços e USE (Utilization, Saturation, Errors) para recursos
   - Documente fórmulas, unidades, e significado de negócio para cada métrica
   - Estabeleça baselines e valores esperados baseados nos requisitos não-funcionais

3. Uma "Matriz de Correlação de Problemas" (matriz-correlacao.md) que:
   - Mapeie sintomas observáveis para causas-raiz potenciais
   - Defina padrões de comportamento anômalo em métricas que indicam problemas específicos
   - Estabeleça correlações entre alertas que podem indicar problemas sistêmicos
   - Documente métricas de leading indicators que podem prever degradações

4. Um "Plano de Instrumentação" (plano-instrumentacao.md) que:
   - Detalhe pontos específicos no código que requerem instrumentação
   - Especifique atributos contextuais a serem capturados em cada ponto
   - Priorize instrumentação baseada em criticidade e valor diagnóstico
   - Integre com código existente respeitando padrões em .agent/padroes-codigo/observabilidade/

5. Um documento "SLIs e SLOs" (slis-slos.md) que:
   - Defina Indicadores de Nível de Serviço (SLIs) mensuráveis para esta funcionalidade
   - Estabeleça Objetivos de Nível de Serviço (SLOs) baseados nos requisitos não-funcionais
   - Documente metodologia para cálculo de error budgets
   - Estabeleça procedimentos para revisão e ajuste periódico baseado em dados operacionais

Cada documento deve:
- Referenciar especificamente a funcionalidade da TASK-{número}
- Alinhar-se com padrões estabelecidos em .agent/padroes-codigo/observabilidade/
- Considerar o contexto técnico completo documentado em .agent/contexto/tecnico/
- Incluir exemplos concretos de consultas, configurações e visualizações quando aplicável
```

##### Prompt 2: Desenvolvimento de Sistema de Alertas e Playbooks de Resposta

```
Atue como um Especialista em Monitoramento e Resposta a Incidentes. Estou implementando alertas e procedimentos de resposta para a funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso de documentação detalhada sobre alertas e procedimentos de resposta.

Referências essenciais:
- Catálogo de métricas: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Matriz de stakeholders: .agent/contexto/comunicacao/matriz-stakeholders.md
- Padrões de alertas: .agent/padroes-codigo/operacoes/configuracao-alertas.md
- Requisitos de disponibilidade: .agent/contexto/requisitos/requisitos-nao-funcionais.md (seção sobre disponibilidade)

Por favor, desenvolva documentação completa para alertas e procedimentos de resposta para armazenamento em '.agent/contexto/operacoes/alertas-resposta/' que inclua:

1. Um documento "Configuração de Alertas" (configuracao-alertas.md) que:
   - Defina todos os alertas necessários para esta funcionalidade com níveis de severidade
   - Especifique condições precisas de disparo usando consultas/expressões reais
   - Estabeleça limiares justificados por análise estatística ou requisitos de negócio
   - Documente estratégias para redução de ruído e falsos positivos

2. Um "Playbook de Resposta a Incidentes" (playbook-resposta.md) que:
   - Detalhe procedimentos passo-a-passo para cada categoria de alerta
   - Inclua árvores de decisão para diagnóstico progressivo do problema
   - Especifique ações imediatas de mitigação para restaurar serviço
   - Documente procedimentos para coleta de evidências para análise posterior

3. Uma "Matriz de Escalonamento" (matriz-escalonamento.md) que:
   - Defina níveis de escalonamento baseados em severidade e duração do incidente
   - Especifique responsáveis primários e secundários para cada componente
   - Documente canais de comunicação e templates para diferentes níveis
   - Estabeleça SLAs internos para resposta em cada nível de severidade

4. Um documento "Dashboards de Monitoramento" (dashboards-monitoramento.md) que:
   - Especifique dashboards técnicos para operações e desenvolvimento
   - Defina dashboards executivos para comunicação com stakeholders de negócio
   - Detalhe painéis de controle para gerenciamento de incidentes ativos
   - Documente visualizações específicas para análise de tendências e capacidade

5. Um "Guia de Comunicação de Incidentes" (comunicacao-incidentes.md) que:
   - Estabeleça templates para comunicação interna e externa durante incidentes
   - Defina cadência de atualizações para diferentes níveis de severidade
   - Especifique estratégias para comunicação técnica vs. não-técnica
   - Documente procedimentos para post-mortem e comunicação de lições aprendidas

Cada documento deve:
- Ser específico para a funcionalidade implementada na TASK-{número}
- Referenciar métricas específicas do catálogo de métricas-chave
- Seguir os padrões estabelecidos em .agent/padroes-codigo/operacoes/
- Incluir exemplos concretos e procedimentos acionáveis
- Considerar impactos em usuários e stakeholders documentados em .agent/contexto/comunicacao/
```

##### Prompt 3: Criação de Procedimentos de Manutenção Preventiva

```
Atue como um Especialista em Manutenção de Sistemas com foco em estratégias preventivas. Estou implementando procedimentos de manutenção para a funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso estabelecer processos sistemáticos para garantir operação confiável a longo prazo.

Referências essenciais:
- Arquitetura técnica: .agent/contexto/arquitetura/dados/modelo-dados-detalhado.md
- Dependências externas: .agent/contexto/tecnico/apis-externas.md
- Padrões de manutenção: .agent/padroes-codigo/operacoes/manutencao-preventiva.md
- Requisitos de performance: .agent/contexto/requisitos/requisitos-nao-funcionais.md

Por favor, desenvolva documentação completa para manutenção preventiva para armazenamento em '.agent/contexto/operacoes/manutencao-preventiva/' que inclua:

1. Um "Cronograma de Manutenção" (cronograma-manutencao.md) que:
   - Defina atividades recorrentes com frequência recomendada (diária, semanal, mensal, trimestral)
   - Especifique janelas ideais para execução com impacto mínimo em usuários
   - Documente dependências entre tarefas e ordenação lógica
   - Estabeleça responsáveis para aprovação e execução de cada procedimento

2. Um documento "Checklists de Verificação de Integridade" (checklists-verificacao.md) que:
   - Desenvolva verificações detalhadas para cada componente da funcionalidade
   - Especifique comandos, consultas e procedimentos específicos para cada verificação
   - Estabeleça valores esperados e limites de alerta para cada item
   - Documente procedimentos de remediação para problemas identificados

3. Uma "Estratégia de Gestão de Capacidade" (gestao-capacidade.md) que:
   - Defina métricas-chave para monitoramento de capacidade de recursos
   - Especifique metodologia para previsão de crescimento baseada em tendências históricas
   - Estabeleça limiares de planejamento para expansão proativa de recursos
   - Documente procedimentos para análise de tendências e planejamento de capacidade

4. Um "Plano de Atualização de Dependências" (atualizacao-dependencias.md) que:
   - Catalogue todas as dependências internas e externas com versões atuais
   - Estabeleça política de revisão regular para vulnerabilidades e atualizações
   - Defina procedimentos para testes de compatibilidade de novas versões
   - Especifique processo de rollback em caso de problemas após atualizações

5. Um documento "Procedimentos de Manutenção de Dados" (manutencao-dados.md) que:
   - Especifique estratégias para gerenciamento do ciclo de vida dos dados
   - Defina procedimentos para arquivamento e purga de dados históricos
   - Estabeleça estratégias para manutenção de índices e otimização de armazenamento
   - Documente procedimentos para validação de integridade de dados e reconciliação

Cada documento deve:
- Referenciar componentes específicos implementados na TASK-{número}
- Alinhar-se com padrões documentados em .agent/padroes-codigo/operacoes/
- Incluir procedimentos automatizados (scripts) quando aplicável
- Considerar impactos em disponibilidade e performance do sistema
- Estabelecer critérios claros para sucesso de cada procedimento de manutenção
```

##### Prompt 4: Elaboração de Guias de Troubleshooting e Runbooks

```
Atue como um Engenheiro de Suporte e Operações especializado em solução de problemas complexos. Estou implementando guias de troubleshooting para a funcionalidade desenvolvida na TASK-{número} (.agent/tasks/TASK-{número}.md) e preciso documentação abrangente para diagnóstico e resolução eficientes de problemas.

Referências essenciais:
- Logs e mensagens de erro: .agent/contexto/arquitetura/integracao/erros-resiliencia.md
- Arquitetura e dependências: .agent/contexto/tecnico/mapa-sistemas.md
- Padrões de runbooks: .agent/padroes-codigo/operacoes/estrutura-runbooks.md
- Fluxos críticos: .agent/contexto/arquitetura/design-tecnico/diagramas-sequencia-fluxos-criticos.md

Por favor, desenvolva documentação completa para troubleshooting para armazenamento em '.agent/contexto/operacoes/solucao-problemas/' que inclua:

1. Um documento "Runbooks Detalhados" (runbooks-detalhados.md) que:
   - Desenvolva runbooks específicos para cenários comuns de falha
   - Especifique sintomas observáveis, causas-raiz prováveis e métodos de verificação
   - Forneça comandos e consultas específicos para diagnóstico
   - Documente procedimentos passo-a-passo para resolução de cada cenário

2. Uma "Árvore de Decisão para Diagnóstico" (arvore-decisao.md) que:
   - Estruture processo sistemático de diagnóstico partindo de sintomas gerais
   - Estabeleça perguntas-chave para refinamento progressivo da causa
   - Especifique verificações a serem realizadas em cada ponto de decisão
   - Direcione para runbooks específicos baseado no diagnóstico

3. Uma "Biblioteca de Consultas e Scripts" (consultas-scripts.md) que:
   - Catalogue consultas otimizadas para diagnóstico em diferentes sistemas (banco de dados, logs, métricas)
   - Forneça scripts reutilizáveis para coleta de informações diagnósticas
   - Especifique parâmetros e opções para personalização das consultas
   - Documente interpretação correta dos resultados

4. Um "Registro Histórico de Incidentes" (registro-incidentes.md) que:
   - Estabeleça formato padronizado para documentação de incidentes
   - Especifique processo de captura de timeline, ações tomadas e resultados
   - Defina metodologia para análise post-mortem e identificação de causas-raiz
   - Documente processo para extração e implementação de lições aprendidas

5. Um documento "Matriz de Sintomas e Soluções" (matriz-sintomas-solucoes.md) que:
   - Crie matriz correlacionando sintomas observáveis a causas potenciais
   - Especifique indicadores específicos em logs, métricas e comportamento
   - Forneça soluções rápidas para problemas frequentes
   - Documente critérios para escalonamento quando soluções rápidas falharem

Cada documento deve:
- Ser específico para a funcionalidade implementada na TASK-{número}
- Referenciar logs e mensagens de erro específicas desta funcionalidade
- Seguir estrutura consistente definida em .agent/padroes-codigo/operacoes/estrutura-runbooks.md
- Incluir exemplos reais de output esperado para cada comando ou consulta
- Considerar diferentes níveis de expertise técnica na equipe de operações
```

##### Prompt 5: Desenvolvimento de Estratégia de Evolução Baseada em Dados Operacionais

```
Atue como um Arquiteto de Produto Técnico especializado em otimização contínua baseada em dados operacionais. Estou estabelecendo processos para evolução da funcionalidade implementada na TASK-{número} (.agent/tasks/TASK-{número}.md) baseados em insights obtidos durante operação em produção.

Referências essenciais:
- Métricas de negócio: .agent/contexto/estrategia/metricas-sucesso.md
- Dados de telemetria: .agent/contexto/operacoes/documentos-estrategia-monitoramento/catalogo-metricas-chave.md
- Roadmap técnico: .agent/contexto/arquitetura/evolucao/roadmap-tecnico.md
- Débito técnico: .agent/contexto/arquitetura/evolucao/gerenciamento-debito-tecnico.md

Por favor, desenvolva documentação detalhada para evolução contínua para armazenamento em '.agent/contexto/operacoes/evolucao-continua/' que inclua:

1. Um "Roadmap de Otimizações" (roadmap-otimizacoes.md) que:
   - Estabeleça processo para identificar oportunidades de melhoria baseadas em dados operacionais
   - Defina frameworks para priorização de otimizações (impacto técnico vs. valor de negócio)
   - Especifique métodos para validação de hipóteses de otimização
   - Documente formato para proposta de melhorias com evidências de dados

2. Um "Framework de Experimentação" (framework-experimentacao.md) que:
   - Desenvolva metodologia para implementação de experimentos controlados
   - Especifique técnicas para testes A/B e deployment gradual
   - Defina métricas para avaliação objetiva de experimentos
   - Documente processo decisório para implementação permanente ou rollback

3. Um "Plano de Refatoração Contínua" (refatoracao-continua.md) que:
   - Identifique indicadores operacionais que sinalizam necessidade de refatoração
   - Estabeleça critérios objetivos para priorização de débito técnico
   - Defina abordagem incremental para refatoração em componentes críticos
   - Documente processos de validação para garantir equivalência funcional

4. Uma "Estratégia de Descontinuação" (estrategia-descontinuacao.md) que:
   - Defina metodologia para identificar funcionalidades subutilizadas
   - Especifique métricas para avaliação objetiva de valor vs. custo de manutenção
   - Estabeleça processo para deprecação gradual com comunicação apropriada
   - Documente procedimentos para remoção segura de código e componentes

5. Um documento "Análise de Feedback e Comportamento" (analise-feedback.md) que:
   - Estabeleça processo para coleta e análise de feedback explícito e implícito
   - Defina métricas para mensuração de satisfação e eficácia da funcionalidade
   - Especifique técnicas para análise de padrões de uso e identificação de pain points
   - Documente metodologia para tradução de insights em requisitos técnicos

Cada documento deve:
- Referenciar diretamente a funcionalidade implementada na TASK-{número}
- Alinhar-se com objetivos estratégicos documentados em .agent/contexto/estrategia/
- Incorporar dados operacionais reais quando disponíveis
- Estabelecer processos sistemáticos e repetíveis para evolução
- Considerar impactos em usuários e stakeholders de negócio
```

Esta abordagem estruturada para monitoramento e manutenção, potencializada pelo GitHub Copilot através de prompts especializados, transforma a fase pós-implantação de um conjunto de atividades reativas para um sistema proativo de governança que maximiza valor para usuários, minimiza interrupções, e estabelece um ciclo contínuo de melhoria baseado em dados reais de uso e comportamento do sistema.

A aplicação sistemática destes prompts especializados durante a fase operacional do produto cria um ecossistema de observabilidade e manutenção que não apenas sustenta a qualidade da implementação inicial, mas fundamentalmente a evolui ao longo do tempo, respondendo a mudanças de padrões de uso, expectativas de usuários, e objetivos organizacionais. Este investimento em processos operacionais estruturados resulta em produtos mais resilientes, adaptativos e alinhados às necessidades reais dos usuários.

### 12. Retrospectiva e Aprendizado

A metodologia estruturada para retrospectiva e aprendizado transcende revisões superficiais de projeto, implementando um framework sistemático de análise que transforma experiência em conhecimento organizacional codificado. Esta fase final aplica princípios avançados de aprendizagem organizacional para criar um ciclo virtuoso de melhoria que fecha o loop do processo de desenvolvimento enquanto estabelece fundações para iterações futuras mais eficientes e eficazes.

Com o suporte do GitHub Copilot, equipes técnicas conduzem análises multidimensionais que examinam não apenas resultados finais, mas padrões emergentes, decisões críticas, e fatores contextuais que influenciaram a trajetória do desenvolvimento. O processo incorpora perspectivas diversas desde desenvolvedores individuais até líderes estratégicos, criando um mosaico rico de insights que captura tanto detalhes tácitos quanto tendências amplas no processo de engenharia.

O resultado é uma transformação sistemática de experiência em conhecimento codificado que alimenta um ciclo de melhoria contínua, refinando progressivamente tanto o produto quanto o próprio processo de desenvolvimento. Esta prática estabelece um mecanismo formal pelo qual a organização não apenas completa projetos, mas fundamentalmente evolui sua capacidade de entregar valor com cada ciclo.

A fase culmina na criação de artefatos de aprendizado e evolução, organizados na pasta `.agent/contexto/retrospectiva`:

#### 12.1. Documentos de Análise de Processo:

- Documento de Retrospectiva Estruturada com análise detalhada de sucessos e desafios
- Timeline Anotada do Projeto destacando pontos de inflexão e decisões cruciais
- Análise de Métricas de Desenvolvimento comparando projeções e resultados reais
- Mapa de Valor/Esforço avaliando retorno de investimento em diferentes componentes

#### 12.2. Artefatos de Captura de Conhecimento:

- Catálogo de Decisões Críticas documentando escolhas significativas e suas consequências
- Biblioteca de Padrões Emergentes identificando abordagens eficazes descobertas durante o desenvolvimento
- Repositório de Lições Aprendidas categorizadas por domínio e aplicabilidade
- Casos de Estudo detalhando soluções notáveis para problemas complexos

#### 12.3. Documentos de Evolução de Processo:

- Propostas de Otimização com melhorias específicas para processos e ferramentas
- Atualizações para Templates e Checklists incorporando novos insights
- Evolução de Padrões de Código baseada em descobertas durante implementação
- Refinamentos de ADRs com conhecimento posterior à implementação

#### 12.4. Artefatos de Capacitação:

- Materiais de Treinamento derivados de experiências do projeto
- Documentação de Pitfalls e Anti-padrões para evitar repetição de problemas
- Guias de Mentoria para transferência de conhecimento
- Biblioteca de Prompts Eficazes para interações otimizadas com Copilot

#### 12.5. Documentos de Direcionamento Estratégico:

- Análise de Oportunidades identificando áreas promissoras para próximas iterações
- Avaliação de Débito Técnico e estratégias de pagamento
- Recomendações para Evoluções Arquiteturais baseadas em insights operacionais
- Alinhamento de Roadmap Técnico com aprendizados estratégicos

#### 12.6. Prompts Otimizados para Retrospectiva e Aprendizado

O processo de retrospectiva e aprendizado é significativamente potencializado pelo uso de prompts especializados do GitHub Copilot. Abaixo, apresentamos diversos prompts otimizados, cada um focado em um aspecto essencial desta fase:

##### Prompt 1: Análise de Processo e Métricas de Desenvolvimento

```
Atue como um Agile Coach e Analista de Métricas de Engenharia especializado em retrospectivas baseadas em dados. Estamos concluindo o desenvolvimento das funcionalidades descritas nas seguintes tasks: [listar .agent/tasks/TASK-{números}.md relevantes] e precisamos conduzir uma análise abrangente do processo e resultados.

Referências essenciais:
- Planejamento original: .agent/contexto/implantacao/documentos-estrategia/cronograma.md
- Métricas de desenvolvimento: [dados reais coletados durante o desenvolvimento]
- Requisitos não-funcionais: .agent/contexto/requisitos/requisitos-nao-funcionais.md
- Padrões de desenvolvimento: .agent/padroes-codigo/workflow/processo-desenvolvimento.md

Por favor, desenvolva documentação detalhada de análise para armazenamento em '.agent/contexto/retrospectiva/analise-processo/' que inclua:

1. Um documento "Análise de Métricas e KPIs" (analise-metricas.md) que:
   - Compare métricas reais vs. planejadas (velocidade, defeitos, tempo de ciclo)
   - Identifique tendências, anomalias e padrões nos dados de desenvolvimento
   - Analise correlações entre eventos do projeto e mudanças em métricas
   - Forneça visualizações conceituais para representar os insights principais

2. Uma "Timeline Anotada do Projeto" (timeline-anotada.md) que:
   - Documente cronologicamente eventos significativos durante o desenvolvimento
   - Identifique pontos de inflexão onde decisões críticas mudaram a trajetória
   - Mapeie obstáculos encontrados e como foram superados
   - Correlacione eventos com impactos em cronograma e qualidade

3. Um "Mapa de Valor/Esforço" (mapa-valor-esforco.md) que:
   - Avalie os componentes desenvolvidos por esforço investido vs. valor entregue
   - Identifique áreas de alto e baixo ROI no desenvolvimento
   - Analise causas de discrepâncias entre esforço estimado e real
   - Recomende abordagens para otimizar o ROI em futuras iterações

4. Um documento "Análise de Fluxo de Trabalho" (analise-fluxo.md) que:
   - Examine o fluxo das tarefas através dos estágios de desenvolvimento
   - Identifique gargalos, bloqueios e aceleradores no processo
   - Compare eficiência entre diferentes tipos de tarefas ou componentes
   - Recomende ajustes específicos ao processo documentado em .agent/padroes-codigo/workflow/

5. Uma "Análise Comparativa de Práticas" (analise-praticas.md) que:
   - Avalie a eficácia das práticas e cerimônias utilizadas
   - Compare diferentes abordagens técnicas aplicadas durante o desenvolvimento
   - Identifique práticas que devem ser amplificadas, ajustadas ou eliminadas
   - Recomende experimentos para validar melhorias em processos

Cada documento deve:
- Basear-se em dados objetivos e observações documentadas
- Incluir tanto análises quantitativas quanto qualitativas
- Separar claramente fatos, interpretações e recomendações
- Considerar o contexto organizacional documentado em .agent/contexto/
- Fornecer insights acionáveis que possam ser implementados em futuros projetos
```

##### Prompt 2: Captura de Conhecimento e Lições Aprendidas

```
Atue como um Knowledge Manager e Especialista em Gestão de Lições Aprendidas. Estamos concluindo o ciclo de desenvolvimento das funcionalidades descritas em [listar .agent/tasks/TASK-{números}.md relevantes] e precisamos capturar sistematicamente o conhecimento gerado para benefício organizacional.

Referências essenciais:
- ADRs do projeto: .agent/contexto/arquitetura/adrs/*.md
- Documentação técnica: .agent/contexto/documentacao/
- Registro de problemas: [incidentes, bugs e desafios encontrados]
- Padrões estabelecidos: .agent/padroes-codigo/

Por favor, desenvolva documentação detalhada de captura de conhecimento para armazenamento em '.agent/contexto/retrospectiva/conhecimento/' que inclua:

1. Um "Catálogo de Decisões Críticas" (catalogo-decisoes.md) que:
   - Documente as decisões técnicas mais impactantes além das já registradas nos ADRs
   - Analise o contexto, alternativas consideradas e justificativas para cada decisão
   - Avalie retrospectivamente o impacto e consequências de cada decisão
   - Extraia princípios gerais que possam guiar decisões similares no futuro

2. Uma "Biblioteca de Padrões Emergentes" (padroes-emergentes.md) que:
   - Identifique padrões técnicos e de design descobertos durante a implementação
   - Documente soluções elegantes que emergiram organicamente
   - Formalize estes padrões em formato consistente com .agent/padroes-codigo/
   - Recomende incorporação destes padrões em projetos futuros

3. Um "Repositório de Lições Aprendidas" (licoes-aprendidas.md) que:
   - Catalogue aprendizados técnicos e de processo em formato estruturado
   - Categorize lições por domínio, severidade e aplicabilidade
   - Documente tanto sucessos (práticas a continuar) quanto desafios (armadilhas a evitar)
   - Inclua contexto suficiente para que as lições sejam aplicáveis por outras equipes

4. Um conjunto de "Casos de Estudo Técnicos" (casos-estudo-tecnicos.md) que:
   - Selecione 3-5 problemas técnicos complexos enfrentados durante o desenvolvimento
   - Documente detalhadamente o problema, abordagens tentadas e solução final
   - Analise fatores que contribuíram para o sucesso da solução
   - Extraia princípios e técnicas reutilizáveis em outros contextos

5. Um documento "Conhecimento Tácito Codificado" (conhecimento-tacito.md) que:
   - Capture insights informais, heurísticas e "truques" descobertos pela equipe
   - Documente atalhos cognitivos e modelos mentais eficazes
   - Transforme conhecimento tácito de especialistas em recursos explícitos
   - Formate este conhecimento para fácil descoberta e aplicação

Cada documento deve:
- Incluir metadados como fonte, contexto, e aplicabilidade
- Ser estruturado para facilitar recuperação e aplicação futura
- Transmitir tanto o "como" quanto o "porquê" de cada aprendizado
- Equilibrar detalhes técnicos com princípios generalizáveis
- Ser escrito considerando uma audiência que não participou do projeto original
```

##### Prompt 3: Evolução de Processos e Refinamento de Padrões

```
Atue como um Engenheiro de Processos de Software especializado em melhoria contínua. Estamos concluindo o desenvolvimento das funcionalidades descritas em [listar .agent/tasks/TASK-{números}.md relevantes] e precisamos evoluir sistematicamente nossos processos e padrões com base nas experiências deste ciclo.

Referências essenciais:
- Padrões atuais: .agent/padroes-codigo/**/*.md
- Processos documentados: .agent/padroes-codigo/workflow/*.md
- Retrospectivas anteriores: .agent/contexto/retrospectiva/ (se existirem)
- Análise de métricas: .agent/contexto/retrospectiva/analise-processo/analise-metricas.md

Por favor, desenvolva documentação detalhada para evolução de processos para armazenamento em '.agent/contexto/retrospectiva/evolucao-processo/' que inclua:

1. Um documento "Propostas de Otimização de Processo" (otimizacao-processo.md) que:
   - Identifique pontos de atrito nos processos atuais documentados em .agent/padroes-codigo/workflow/
   - Proponha melhorias específicas com justificativas baseadas em experiências recentes
   - Priorize as otimizações por impacto potencial e facilidade de implementação
   - Inclua métricas específicas para avaliar o sucesso de cada mudança proposta

2. Um documento "Atualizações para Templates e Checklists" (atualizacoes-templates.md) que:
   - Identifique lacunas, redundâncias ou ambiguidades em templates existentes
   - Proponha adições, remoções ou modificações específicas
   - Forneça versões atualizadas dos templates mais críticos
   - Inclua raciocínio para cada modificação baseado em experiências concretas

3. Um documento "Evolução de Padrões de Código" (evolucao-padroes-codigo.md) que:
   - Avalie a eficácia dos padrões atuais em .agent/padroes-codigo/
   - Proponha refinamentos baseados em insights da implementação
   - Documente novos padrões identificados durante o desenvolvimento
   - Inclua exemplos concretos demonstrando o valor dos padrões refinados

4. Um documento "Refinamentos de ADRs" (refinamentos-adrs.md) que:
   - Reavalie decisões arquiteturais à luz da experiência de implementação
   - Proponha ajustes a ADRs existentes com justificativas
   - Documente novos ADRs para decisões que emergiram durante o desenvolvimento
   - Estabeleça vínculos entre decisões relacionadas para formar um mapa de contexto arquitetural

5. Um documento "Framework de Experimentação" (framework-experimentacao.md) que:
   - Defina um processo estruturado para testar novas práticas e ferramentas
   - Identifique 3-5 experimentos específicos a serem conduzidos no próximo ciclo
   - Estabeleça métricas e critérios de avaliação para cada experimento
   - Documente metodologia para incorporar resultados bem-sucedidos em processos padrão

Cada documento deve:
- Basear-se em experiências concretas do ciclo de desenvolvimento recente
- Incluir tanto modificações imediatas quanto direções de longo prazo
- Fornecer justificativas claras para cada mudança proposta
- Considerar o impacto em diferentes perfis de membros da equipe
- Manter coerência com a cultura técnica e valores da organização
```

##### Prompt 4: Desenvolvimento de Material de Capacitação

```
Atue como um Especialista em Desenvolvimento Técnico e Criador de Conteúdo Educacional. Estamos concluindo o desenvolvimento das funcionalidades descritas em [listar .agent/tasks/TASK-{números}.md relevantes] e precisamos transformar as experiências e conhecimentos adquiridos em materiais de capacitação para toda a organização.

Referências essenciais:
- Documentação técnica: .agent/contexto/documentacao/
- Lições aprendidas: .agent/contexto/retrospectiva/conhecimento/licoes-aprendidas.md
- Padrões técnicos: .agent/padroes-codigo/
- Incidentes e desafios: [registro de problemas enfrentados e soluções]

Por favor, desenvolva materiais de capacitação para armazenamento em '.agent/contexto/retrospectiva/capacitacao/' que inclua:

1. Um "Guia de Onboarding Técnico" (onboarding-tecnico.md) que:
   - Crie um roteiro estruturado para novos membros da equipe
   - Identifique conceitos fundamentais que precisam ser compreendidos
   - Documente recursos essenciais a serem consultados em ordem lógica
   - Inclua exercícios práticos que reforcem os padrões e práticas do projeto

2. Um documento "Documentação de Pitfalls e Anti-padrões" (pitfalls-antipadroes.md) que:
   - Catalogue erros comuns, armadilhas e padrões problemáticos identificados
   - Explique o contexto e impacto negativo de cada anti-padrão
   - Forneça exemplos concretos de "antes e depois" mostrando a correção
   - Organize anti-padrões por categoria técnica e severidade

3. Um conjunto de "Guias de Mentoria Técnica" (guias-mentoria.md) que:
   - Desenvolva roteiros para transferência de conhecimento em áreas especializadas
   - Identifique habilidades críticas e como desenvolvê-las progressivamente
   - Documente perguntas orientadoras para verificar compreensão
   - Forneça recursos complementares para aprofundamento em cada área

4. Uma "Biblioteca de Prompts Eficazes para Copilot" (prompts-eficazes.md) que:
   - Catalogue os prompts mais úteis descobertos durante o desenvolvimento
   - Organize-os por caso de uso, domínio técnico e complexidade
   - Documente variações e parâmetros para customização
   - Inclua exemplos de outputs de alta qualidade para referência

5. Um conjunto de "Workshops Técnicos Estruturados" (workshops-tecnicos.md) que:
   - Desenvolva 3-5 workshops hands-on baseados em desafios reais do projeto
   - Estruture cada workshop com objetivos claros, pré-requisitos e resultados esperados
   - Inclua materiais de suporte, código de exemplo e exercícios práticos
   - Documente abordagem pedagógica e pontos de discussão para facilitadores

Cada material deve:
- Ser acessível para diferentes níveis de experiência quando apropriado
- Incorporar princípios de aprendizagem efetiva (prática, feedback, contexto)
- Refletir desafios reais enfrentados e soluções desenvolvidas
- Referenciar recursos específicos em .agent/contexto/ e .agent/padroes-codigo/
- Ser estruturado para uso tanto em aprendizagem auto-dirigida quanto em sessões facilitadas
```

##### Prompt 5: Direcionamento Estratégico e Análise de Débito Técnico

```
Atue como um Arquiteto Estratégico e Consultor de Evolução Técnica. Estamos concluindo o desenvolvimento das funcionalidades descritas em [listar .agent/tasks/TASK-{números}.md relevantes] e precisamos analisar as implicações estratégicas e técnicas para orientar os próximos ciclos de desenvolvimento.

Referências essenciais:
- Arquitetura atual: .agent/contexto/arquitetura/visao/diagrama-arquitetura-alto-nivel.md
- Roadmap existente: .agent/contexto/arquitetura/evolucao/roadmap-tecnico.md
- Monitoramento em produção: .agent/contexto/operacoes/monitoramento-validacao/
- Feedback de usuários e stakeholders: [resumo de feedback relevante]

Por favor, desenvolva documentação detalhada de direcionamento estratégico para armazenamento em '.agent/contexto/retrospectiva/estrategia/' que inclua:

1. Uma "Análise de Oportunidades Técnicas" (oportunidades-tecnicas.md) que:
   - Identifique áreas promissoras para evolução baseadas na experiência de implementação
   - Avalie tecnologias emergentes que poderiam beneficiar o sistema
   - Mapeie capacidades diferenciadoras que poderiam ser desenvolvidas
   - Priorize oportunidades por impacto potencial, viabilidade e alinhamento estratégico

2. Uma "Avaliação de Débito Técnico" (avaliacao-debito-tecnico.md) que:
   - Catalogue débito técnico intencional e não-intencional acumulado
   - Classifique cada item por impacto, risco e custo de remediação
   - Desenvolva estratégia para pagamento sistemático de débito técnico
   - Recomende práticas para minimizar acúmulo futuro de débito

3. Um documento "Recomendações para Evolução Arquitetural" (evolucao-arquitetural.md) que:
   - Avalie a adequação da arquitetura atual à luz da implementação completa
   - Identifique limitações, restrições ou desalinhamentos arquiteturais
   - Proponha refinamentos arquiteturais incrementais
   - Documente visão arquitetural de longo prazo considerando tendências de mercado

4. Um documento "Alinhamento de Roadmap Técnico" (alinhamento-roadmap.md) que:
   - Revise o roadmap técnico existente considerando aprendizados recentes
   - Proponha ajustes de prioridades e sequenciamento
   - Identifique dependências críticas para próximas evoluções
   - Recomende experimentos técnicos para validar direções estratégicas

5. Uma "Análise de Impacto em Métricas de Negócio" (impacto-metricas-negocio.md) que:
   - Avalie como as escolhas técnicas impactaram métricas de negócio
   - Identifique correlações entre decisões de engenharia e resultados de negócio
   - Recomende otimizações técnicas com potencial de maior impacto em métricas-chave
   - Estabeleça framework para avaliação contínua de ROI de iniciativas técnicas

Cada documento deve:
- Conectar observações técnicas com objetivos estratégicos da organização
- Balancear considerações de curto e longo prazo
- Considerar tanto manutenção quanto evolução do sistema
- Fornecer recomendações acionáveis com rationale claro
- Incluir critérios para avaliação de sucesso das recomendações
```

A aplicação sistemática destes prompts especializados, potencializada pelo GitHub Copilot, transforma a fase de retrospectiva e aprendizado de um ritual superficial para um mecanismo estruturado de evolução organizacional. Ao codificar experiências em conhecimento reutilizável, refinar processos, criar materiais de capacitação e alinhar direcionamento estratégico, esta prática fecha o ciclo de desenvolvimento enquanto estabelece uma fundação progressivamente mais robusta para iterações futuras.

O verdadeiro valor desta abordagem estruturada para retrospectiva não está apenas na análise do passado, mas na tradução sistemática de experiências em melhorias tangíveis que elevam continuamente a capacidade da organização de entregar valor através de software excepcional. Ao integrar este componente como fase formal do workflow, organizações estabelecem um mecanismo autorreforçador de aprendizado e evolução que transcende projetos individuais e constrói excelência técnica sustentável.
