# Prompts para Architecture Decision Records (ADRs)

Este documento contém prompts específicos para auxiliar na criação de Architecture Decision Records (ADRs) para documentar decisões arquiteturais importantes do seu sistema.

## Prompt para Template Básico de ADR

```
Atue como um arquiteto de software experiente especializado em documentar decisões arquiteturais.

Preciso criar um Architecture Decision Record (ADR) para o sistema [nome do sistema] seguindo um formato padronizado. Por favor, gere um template de ADR com as seguintes seções:

1. Título
2. Status (Proposto, Aceito, Superado, etc.)
3. Contexto
4. Decisão
5. Alternativas Consideradas
6. Consequências
7. Conformidade
8. Decisões Relacionadas

Para cada seção, forneça uma breve descrição do que deve ser incluído e exemplos de perguntas que ajudem a elaborar o conteúdo.
```

## Prompt para Documentar uma Decisão Específica

```
Atue como um arquiteto de software experiente especializado em documentar decisões arquiteturais.

Preciso criar um Architecture Decision Record (ADR) para documentar a seguinte decisão arquitetural para o sistema [nome do sistema]:

Decisão: [descreva a decisão a ser documentada, por exemplo: "Adotar uma arquitetura de microserviços"]

Contexto relevante:
- [forneça informações sobre o sistema e sua complexidade]
- [descreva os desafios ou problemas que motivaram esta decisão]
- [mencione requisitos não-funcionais relevantes]
- [descreva restrições conhecidas]

Alternativas que consideramos:
- [liste as principais alternativas consideradas]

Por favor, desenvolva um ADR completo que documente esta decisão, seguindo esta estrutura:

1. Título: Um nome descritivo para a decisão
2. Status: [status atual, geralmente "Proposto" ou "Aceito"]
3. Contexto: Elaboração detalhada do problema e situação
4. Decisão: Descrição clara da decisão tomada e justificativa
5. Alternativas Consideradas: Análise de cada alternativa com prós e contras
6. Consequências: Impactos positivos e negativos esperados desta decisão
7. Conformidade: Como verificaremos que esta decisão está sendo seguida
8. Decisões Relacionadas: Referências a outras decisões arquiteturais relacionadas

Mantenha o documento conciso mas completo, com foco em clareza e justificativa sólida.
```

## Prompt para Escolha de Tecnologia

```
Atue como um arquiteto de software especializado em avaliação e seleção de tecnologias.

Preciso criar um Architecture Decision Record (ADR) para documentar a escolha da tecnologia [nome da tecnologia/framework/plataforma] para [finalidade específica] no sistema [nome do sistema].

Contexto:
- Descrição do sistema: [breve descrição]
- Necessidades específicas: [descreva as necessidades que esta tecnologia deve atender]
- Restrições: [mencione restrições como orçamento, prazos, expertise da equipe, etc.]
- Critérios de avaliação: [liste os principais critérios usados na seleção]

Por favor, desenvolva um ADR completo que:

1. Documente claramente a decisão de usar esta tecnologia
2. Forneça o contexto completo que levou a esta necessidade
3. Compare detalhadamente com pelo menos 3 alternativas viáveis
4. Apresente uma análise de prós e contras de cada opção
5. Justifique a escolha final com base em critérios objetivos
6. Descreva as consequências esperadas (positivas e negativas)
7. Identifique quaisquer riscos associados e estratégias de mitigação
8. Mencione como verificaremos o sucesso desta escolha

O ADR deve ser técnico, objetivo e demonstrar uma avaliação imparcial das opções.
```

## Prompt para Revisar e Atualizar um ADR Existente

```
Atue como um arquiteto de software experiente especializado em documentação arquitetural.

Preciso revisar e atualizar um Architecture Decision Record (ADR) existente devido a mudanças nas circunstâncias ou novos insights. Aqui está o ADR original:

[Cole o conteúdo do ADR existente]

As mudanças ou novos fatores que precisam ser considerados são:
- [liste as mudanças, como novos requisitos, problemas descobertos, etc.]
- [descreva novos insights ou informações que não estavam disponíveis antes]
- [mencione qualquer feedback da implementação da decisão original]

Por favor, produza uma versão atualizada deste ADR que:

1. Mantenha o histórico da decisão original
2. Atualize o status conforme apropriado (ex: de "Aceito" para "Superado" ou "Revisado")
3. Adicione uma seção de "Histórico de Revisões" se ainda não existir
4. Atualize as seções relevantes para refletir as novas informações ou mudanças
5. Se a decisão for fundamentalmente alterada, articule claramente as razões

O ADR atualizado deve mostrar claramente o que mudou e por quê, mantendo a rastreabilidade da decisão ao longo do tempo.
```

## Prompt para ADR sobre Padrão Arquitetural

```
Atue como um arquiteto de software especializado em padrões arquiteturais.

Preciso criar um Architecture Decision Record (ADR) para documentar a decisão de adotar o padrão arquitetural [nome do padrão, ex: CQRS, Event Sourcing, Hexagonal, etc.] para o sistema [nome do sistema].

Contexto do sistema:
- Descrição: [breve descrição do sistema]
- Domínio: [área de negócio e complexidade do domínio]
- Desafios específicos: [desafios que motivaram considerar este padrão]

Por favor, desenvolva um ADR completo que:

1. Explique sucintamente o padrão arquitetural em questão
2. Detalhe o contexto específico que levou à consideração deste padrão
3. Articule claramente a decisão de adotar este padrão e em quais partes do sistema
4. Compare com padrões alternativos que poderiam resolver os mesmos problemas
5. Analise os benefícios esperados deste padrão no contexto específico do sistema
6. Identifique potenciais desafios, riscos e trade-offs da adoção
7. Descreva como a equipe verificará a implementação correta deste padrão
8. Mencione implicações para outras decisões arquiteturais

O ADR deve ser tecnicamente preciso, demonstrar compreensão profunda do padrão escolhido, e mostrar uma análise criteriosa da adequação do padrão ao contexto específico do sistema.
```

## Prompt para Decisão de Integração entre Sistemas

```
Atue como um arquiteto de integração de sistemas experiente.

Preciso criar um Architecture Decision Record (ADR) para documentar a abordagem de integração entre o sistema [nome do sistema] e [sistema externo/terceiro].

Contexto da integração:
- Propósito: [descreva o objetivo da integração]
- Requisitos críticos: [descreva requisitos como volume de dados, latência, segurança, etc.]
- Restrições: [mencione restrições como protocolos suportados pelo sistema externo, etc.]

Por favor, desenvolva um ADR completo que:

1. Documente claramente a decisão sobre o método de integração (API REST, GraphQL, mensageria, arquivos batch, etc.)
2. Forneça o contexto completo da necessidade de integração
3. Detalhe as alternativas de integração consideradas com análise de cada uma
4. Justifique a escolha final com base em critérios técnicos e de negócio
5. Descreva o padrão de comunicação (síncrono, assíncrono, híbrido)
6. Aborde aspectos de segurança da integração
7. Discuta considerações sobre tratamento de erros e resiliência
8. Mencione implicações para monitoramento e observabilidade
9. Identifique quaisquer dependências ou decisões relacionadas

O ADR deve demonstrar uma análise completa das necessidades de integração e justificar claramente a abordagem escolhida.
```

## Prompt para Compilação de ADRs em um Log de Decisões

```
Atue como um arquiteto de software especializado em documentação arquitetural.

Estou trabalhando no sistema [nome do sistema] e já documentamos várias decisões arquiteturais importantes como ADRs individuais. Agora preciso compilar esses ADRs em um log de decisões coerente que forneça uma visão abrangente da evolução arquitetural do sistema.

Aqui estão os títulos dos ADRs existentes:
- [liste os títulos dos ADRs existentes]

Por favor, ajude-me a criar:

1. Uma introdução que explique o propósito do log de decisões e como ele deve ser usado
2. Uma estrutura organizada para apresentar as decisões (cronológica, por subsistema, por tipo de decisão, etc.)
3. Um resumo executivo das decisões mais impactantes
4. Um mapa visual ou tabela que mostre relações entre as decisões
5. Recomendações para a manutenção contínua do log de decisões

O resultado deve ser um documento que ajude novos membros da equipe a entender rapidamente as principais decisões arquiteturais e como elas se relacionam para formar a arquitetura completa do sistema.
```
