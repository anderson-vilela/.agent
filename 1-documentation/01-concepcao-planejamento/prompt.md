# 01-concepcao-planejamento

# Prompts para Fase de Concepção e Planejamento

Este arquivo contém prompts para geração assistida de documentos relacionados à fase inicial de concepção e planejamento de projetos.

## Prompt Geral para Documentos de Concepção

```
Como especialista em planejamento de projetos de software, preciso criar um documento de [TIPO DE DOCUMENTO: Vision Document/Project Charter/Estudo de Viabilidade/BRD/MRD] para um novo projeto.

Contexto do projeto:
- Nome: [NOME DO PROJETO]
- Setor de atuação: [SETOR]
- Problema principal a ser resolvido: [DESCRIÇÃO DO PROBLEMA]
- Público-alvo: [DESCRIÇÃO DO PÚBLICO]
- Restrições iniciais conhecidas: [LISTAR RESTRIÇÕES]

Por favor, gere um documento estruturado e abrangente que:
1. Siga as melhores práticas para documentos de [TIPO DE DOCUMENTO]
2. Seja compatível com metodologias [ÁGIL/TRADICIONAL]
3. Contenha todas as seções essenciais com exemplos de conteúdo
4. Inclua orientações sobre como preencher cada seção
5. Tenha nível de detalhe adequado para a fase inicial do projeto

Aspectos específicos que precisam ser abordados:
- [LISTAR ASPECTOS ESPECÍFICOS]
```

## Prompts Específicos para Cada Documento

### Vision Document

```
Como arquiteto de soluções, preciso criar um Vision Document para o projeto [NOME DO PROJETO].

Contexto do projeto:
- Descrição breve: [DESCRIÇÃO]
- Desafios atuais: [DESAFIOS]
- Oportunidades identificadas: [OPORTUNIDADES]

Por favor, gere um Vision Document completo que inclua:
1. Introdução e propósito do documento
2. Descrição do problema e justificativa do projeto
3. Visão da solução proposta
4. Principais features e benefícios
5. Pressupostos e dependências
6. Stakeholders principais e suas necessidades
7. Escopo inicial (o que está dentro e fora)
8. Visão geral de requisitos principais
9. Restrições e riscos de alto nível
10. Critérios de sucesso mensuráveis

O documento deve ser inspirador, mas realista, estabelecendo uma visão clara que possa guiar o desenvolvimento sem restringir inovações durante o processo.
```

### Project Charter

```
Como gerente de projetos, preciso desenvolver um Project Charter para obter aprovação formal para o projeto [NOME DO PROJETO].

Informações disponíveis:
- Objetivo principal: [OBJETIVO]
- Orçamento preliminar: [ORÇAMENTO]
- Timeline esperado: [TIMELINE]
- Principais stakeholders: [STAKEHOLDERS]

Por favor, crie um Project Charter profissional que inclua:
1. Propósito e justificativa do projeto
2. Objetivos mensuráveis e critérios de sucesso
3. Requisitos de alto nível
4. Riscos iniciais identificados
5. Resumo do cronograma de marcos
6. Resumo do orçamento
7. Requisitos para aprovação
8. Gerente de projeto designado e seu nível de autoridade
9. Identificação dos stakeholders principais
10. Equipe principal do projeto e recursos necessários

O documento deve ser direto e conciso, focado em obter um acordo formal para iniciar o projeto e estabelecer sua governança básica.
```

### Estudo de Viabilidade

```
Como analista de negócios, preciso criar um Estudo de Viabilidade para avaliar a solução proposta para [NOME DO PROJETO/PROBLEMA].

Contexto:
- Descrição da solução proposta: [DESCRIÇÃO]
- Orçamento disponível: [ORÇAMENTO]
- Prazo desejado: [PRAZO]
- Restrições organizacionais: [RESTRIÇÕES]

Por favor, desenvolva um Estudo de Viabilidade detalhado que cubra:
1. Resumo executivo
2. Descrição do problema e objetivos de negócio
3. Análise de viabilidade técnica
   - Tecnologias necessárias
   - Compatibilidade com sistemas existentes
   - Capacidades técnicas requeridas
4. Análise de viabilidade econômica
   - Custos estimados (desenvolvimento, implementação, operação)
   - Benefícios esperados (tangíveis e intangíveis)
   - ROI projetado e payback period
5. Análise de viabilidade operacional
   - Impacto em processos existentes
   - Necessidades de treinamento
   - Mudanças organizacionais requeridas
6. Análise de viabilidade legal/regulatória
7. Análise de prazos e cronograma viável
8. Análise de riscos principais
9. Análise de alternativas consideradas
10. Conclusões e recomendações

O estudo deve fornecer uma base sólida para decisão sobre prosseguir ou não com o projeto.
```

### Business Requirements Document (BRD)

```
Como analista de requisitos de negócio, preciso criar um Business Requirements Document (BRD) para o projeto [NOME DO PROJETO].

Contexto do negócio:
- Objetivos estratégicos relacionados: [OBJETIVOS]
- Processos de negócio afetados: [PROCESSOS]
- Stakeholders principais: [STAKEHOLDERS]
- Limitações ou restrições de negócio: [LIMITAÇÕES]

Por favor, desenvolva um BRD completo que inclua:
1. Introdução e visão geral
2. Escopo do projeto (inclui o que está fora do escopo)
3. Objetivos de negócio específicos que o projeto atenderá
4. Stakeholders e usuários
   - Perfis de stakeholders
   - Necessidades e expectativas
   - Níveis de envolvimento
5. Requisitos de negócio detalhados
   - Necessidades funcionais do negócio
   - Requisitos de dados e informações
   - Requisitos de processo
   - Requisitos de relatórios e analytics
6. Premissas e restrições de negócio
7. Impactos nos processos atuais
8. Critérios de aceitação do negócio
9. Glossário de termos de negócio relevantes
10. Apêndices (documentos de referência, organogramas, etc.)

O BRD deve focar no QUE o negócio precisa, não em COMO será implementado tecnicamente.
```

### Market Requirements Document (MRD)

```
Como product manager, preciso desenvolver um Market Requirements Document (MRD) para o produto [NOME DO PRODUTO].

Contexto de mercado:
- Segmento-alvo: [SEGMENTO]
- Principais concorrentes: [CONCORRENTES]
- Tendências relevantes: [TENDÊNCIAS]
- Oportunidade identificada: [OPORTUNIDADE]

Por favor, crie um MRD abrangente que inclua:
1. Resumo executivo
2. Visão geral do mercado
   - Tamanho e crescimento do mercado
   - Análise da concorrência
   - Tendências e direcionadores de mercado
3. Oportunidade de mercado
   - Problema que o produto resolve
   - Valor para o cliente
   - Diferenciadores
4. Segmentação de clientes e personas
   - Perfis detalhados dos segmentos-alvo
   - Necessidades e dores específicas de cada segmento
5. Análise competitiva detalhada
   - Comparativo de soluções concorrentes
   - Vantagens e desvantagens competitivas
6. Requisitos gerais do produto
   - Funcionalidades essenciais
   - Características diferenciadoras
   - Experiência do usuário desejada
7. Posicionamento e mensagem de marketing
8. Modelos de preço preliminares
9. Alinhamento com estratégia de produto e roadmap
10. Métricas de sucesso e KPIs de mercado

O MRD deve capturar a voz do mercado e do cliente, servindo como ponte entre as necessidades do mercado e os requisitos do produto.
```

Consulte as pastas específicas de cada documento para prompts mais detalhados e contextualizados.
