# Prompts para Documentos de Projeto

Este arquivo contém prompts gerais para auxiliar na criação dos principais documentos de projeto. Para prompts mais específicos, consulte as pastas individuais de cada tipo de documento.

## Prompt Geral para Geração de Documentação

```
Como especialista em documentação de projetos, preciso criar um [TIPO DE DOCUMENTO] para o projeto [NOME DO PROJETO].

Contexto do projeto:
- Descrição: [BREVE DESCRIÇÃO]
- Objetivos principais: [OBJETIVOS]
- Stakeholders: [STAKEHOLDERS]
- Metodologia: [METODOLOGIA (ÁGIL/TRADICIONAL)]
- Fase atual: [FASE DO PROJETO]
- Complexidade: [BAIXA/MÉDIA/ALTA]

Por favor, gere um documento estruturado que:
1. Siga as melhores práticas para [TIPO DE DOCUMENTO]
2. Seja adequado à metodologia [METODOLOGIA] que estamos usando
3. Tenha nível de formalidade e detalhamento apropriado para nossa organização
4. Inclua todas as seções essenciais com exemplos de conteúdo
5. Forneça orientações sobre como preencher cada seção corretamente

Aspectos específicos que precisam ser abordados:
- [LISTAR ASPECTOS ESPECÍFICOS OU DESAFIOS]

O documento deve ser claro, conciso e focado em comunicar efetivamente as informações necessárias aos stakeholders relevantes.
```

## Prompt para Adaptação de Documentação Existente

```
Como especialista em documentação de projetos, preciso adaptar nosso template de [TIPO DE DOCUMENTO] para o contexto específico do projeto [NOME DO PROJETO].

Contexto do projeto:
- Natureza do projeto: [SOFTWARE/HARDWARE/SERVIÇO/OUTRO]
- Tamanho da equipe: [TAMANHO]
- Complexidade: [BAIXA/MÉDIA/ALTA]
- Duração estimada: [DURAÇÃO]
- Restrições principais: [RESTRIÇÕES]
- Metodologia: [METODOLOGIA]

Template atual:
[INCLUIR ESTRUTURA OU LINK PARA O TEMPLATE ATUAL]

Por favor, analise nosso template atual e:
1. Sugira adaptações para torná-lo mais adequado a este projeto específico
2. Indique seções que poderiam ser simplificadas ou expandidas
3. Recomende abordagens para personalizar o documento às necessidades dos stakeholders
4. Identifique potenciais lacunas no template considerando a natureza deste projeto
5. Forneça exemplos de conteúdo para as seções mais críticas

O objetivo é ter um documento que mantenha a consistência com nossos padrões, mas seja otimizado para este projeto específico.
```

## Prompt para Revisão de Documentação

```
Como especialista em qualidade de documentação, preciso revisar criticamente o [TIPO DE DOCUMENTO] do projeto [NOME DO PROJETO].

Documento atual:
[INCLUIR CONTEÚDO DO DOCUMENTO ATUAL]

Por favor, realize uma análise detalhada que aborde:

1. Completude
   - Há seções importantes faltando?
   - Existem informações cruciais ausentes?
   - O nível de detalhamento é adequado?

2. Clareza e Comunicação
   - A linguagem é clara e concisa?
   - Há jargões excessivos ou não explicados?
   - O documento é compreensível para seu público-alvo?

3. Estrutura e Organização
   - A estrutura lógica faz sentido?
   - A informação flui de maneira natural?
   - A formatação facilita a leitura e compreensão?

4. Consistência
   - Há inconsistências internas no documento?
   - O documento está alinhado com outros documentos do projeto?
   - A terminologia é usada de forma consistente?

5. Rastreabilidade
   - Os requisitos/informações são rastreáveis?
   - As dependências entre elementos são claras?
   - As referências a outros documentos são adequadas?

6. Acionabilidade
   - O documento fornece informações suficientes para ação?
   - As responsabilidades estão claramente atribuídas?
   - Os próximos passos são evidentes?

Por favor, forneça recomendações específicas para melhorias, organizadas por prioridade (alta, média, baixa).
```

## Prompt para Integração entre Documentos

```
Como arquiteto de documentação, preciso garantir a integração e consistência entre os diversos documentos do projeto [NOME DO PROJETO].

Documentos existentes:
- [LISTA DE DOCUMENTOS JÁ CRIADOS COM BREVE DESCRIÇÃO]

Documento que estou criando/atualizando agora:
- [TIPO DE DOCUMENTO ATUAL]

Por favor, analise como o [TIPO DE DOCUMENTO ATUAL] deve se integrar com os documentos existentes e:

1. Identifique dependências e referências cruzadas importantes
   - Quais informações devem ser consistentes entre os documentos?
   - Onde este documento deve referenciar outros documentos?
   - Onde outros documentos deverão referenciar este?

2. Sugira abordagem para garantir rastreabilidade
   - Como manter a rastreabilidade de requisitos/decisões através dos documentos?
   - Que sistema de ID ou referência deve ser utilizado?
   - Como facilitar a navegação entre documentos relacionados?

3. Recomende estratégia para gerenciar mudanças
   - Como garantir que mudanças em um documento sejam refletidas nos dependentes?
   - Que processo de revisão deve ser seguido ao atualizar documentos interconectados?
   - Como comunicar efetivamente mudanças aos stakeholders?

4. Forneça exemplos concretos de integração
   - Exemplos de referências cruzadas bem formatadas
   - Modelo para seções que dependem de outros documentos
   - Exemplos de como manter a consistência de terminologia e conceitos

O objetivo é criar um ecossistema de documentação coeso onde as informações fluam logicamente de um documento para outro, mantendo consistência e facilitando a manutenção.
```

## Prompt para Documentação Adaptada a Metodologias Ágeis

```
Como especialista em documentação ágil, preciso criar um [TIPO DE DOCUMENTO] que seja efetivo em nosso ambiente ágil para o projeto [NOME DO PROJETO].

Contexto do framework ágil:
- Metodologia específica: [SCRUM/KANBAN/SCRUMBAN/SAFe/OUTRO]
- Tamanho da equipe: [TAMANHO]
- Duração das iterações: [DURAÇÃO]
- Ferramentas utilizadas: [FERRAMENTAS]
- Nível de maturidade ágil: [BAIXO/MÉDIO/ALTO]

Por favor, desenvolva um [TIPO DE DOCUMENTO] que:

1. Siga os valores ágeis
   - Seja leve mas suficiente
   - Priorize informação útil sobre documentação abrangente
   - Facilite a colaboração e feedback
   - Seja adaptável a mudanças

2. Integre-se ao fluxo de trabalho ágil
   - Conecte-se ao backlog e user stories quando relevante
   - Seja compatível com o ritmo de iterações
   - Suporte refinamento progressivo
   - Possa ser atualizado incrementalmente

3. Equilibre as necessidades divergentes
   - Atenda requisitos de conformidade/governança
   - Mantenha-se ágil e não burocrático
   - Sirva tanto para necessidades internas quanto externas
   - Forneça valor real à equipe e stakeholders

4. Defina processo de manutenção
   - Quem atualiza e quando
   - Como incorporar feedback
   - Como manter relevante ao longo do tempo
   - Como validar durante cerimônias ágeis

Forneça exemplos concretos de como o documento seria utilizado durante o ciclo de vida ágil e como evitar que se torne obsoleto ou irrelevante.
```

## Prompt para Criação de Documentação Visual

```
Como especialista em comunicação visual, preciso enriquecer o [TIPO DE DOCUMENTO] do projeto [NOME DO PROJETO] com elementos visuais eficazes.

Contexto do documento:
- Propósito principal: [PROPÓSITO]
- Audiência primária: [AUDIÊNCIA]
- Complexidade do conteúdo: [COMPLEXIDADE]
- Desafios de comunicação: [DESAFIOS]
- Uso previsto: [COMO SERÁ UTILIZADO]

Por favor, recomende elementos visuais apropriados que:

1. Tipos de visualizações recomendadas
   - Diagramas (quais tipos e para quais seções)
   - Gráficos e charts (quais tipos para quais dados)
   - Fluxogramas e mapas de processo
   - Infográficos e representações conceituais
   - Tabelas e matrizes comparativas
   - Mapas mentais e hierarquias

2. Para cada visualização sugerida:
   - Propósito específico e valor agregado
   - Conteúdo a ser visualizado
   - Complexidade adequada
   - Estilo e direcionamento visual
   - Integrações com o texto
   - Acessibilidade e inclusão

3. Abordagem para criação
   - Ferramentas recomendadas
   - Processo de desenvolvimento iterativo
   - Validação com stakeholders
   - Consistência entre elementos visuais
   - Atualização e manutenção

4. Exemplos concretos
   - Esboços iniciais para visualizações prioritárias
   - Descrições detalhadas de cada elemento
   - Alternativas para consideração
   - Integrações com o fluxo narrativo do documento

O objetivo é utilizar visualizações que realmente aumentem a compreensão e retenção da informação, tornando o documento mais eficaz e acessível para todos os stakeholders.
```

## Navegação para Documentos Específicos

Para prompts mais detalhados e específicos, consulte as pastas de cada tipo de documento:

- **Concepção e Planejamento**: Vision Document, Project Charter, Estudo de Viabilidade, BRD, MRD
- **Requisitos**: PRD, SRS, FSD, Roadmap, UX/UI Specs
- **Governança e Processos**: Communication Plan, Governance Framework, Process Guidelines
- **Arquitetura e Design**: Architecture Document, Design Patterns, Integration Specs
- **Guidelines de Sistema**: Coding Standards, Security Guidelines, Performance Guidelines
- **Documentação de Usuário**: User Manuals, Training Materials, Quick Start Guides
- **Operação e Suporte**: Operations Manual, Troubleshooting Guide, SLA Documentation
