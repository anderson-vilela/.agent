# Prompts para Functional Specification Document (FSD)

## Prompt para Estrutura Completa do FSD

```
Você é um analista de sistemas experiente especializado em documentação funcional de software. Preciso da sua ajuda para criar um Functional Specification Document (FSD) completo para [nome do sistema].

Contexto do sistema:
- Descrição: [breve descrição do sistema]
- Principais funcionalidades: [lista das principais funcionalidades]
- Usuários-alvo: [tipos de usuários]
- Integrações: [sistemas com os quais este sistema interage]

Por favor, crie um FSD detalhado que inclua:
1. Introdução e visão geral do sistema
2. Descrição funcional dos principais módulos e componentes
3. Detalhamento de cada funcionalidade (incluindo comportamento esperado, regras de negócio, validações)
4. Fluxos de processo para as principais operações
5. Descrição das interfaces de usuário e outras interfaces
6. Comportamento operacional (operações de rotina, monitoramento)
7. Considerações de segurança funcional
8. Apêndices relevantes

Use linguagem clara e inclua exemplos concretos para ilustrar como as funcionalidades devem se comportar do ponto de vista do usuário.
```

## Prompt para Detalhamento de Funcionalidades

```
Como analista funcional, preciso detalhar as especificações funcionais para o módulo de [nome do módulo] do sistema [nome do sistema].

As funcionalidades deste módulo são:
- [Funcionalidade 1]
- [Funcionalidade 2]
- [Funcionalidade 3]

Para cada funcionalidade, por favor crie uma especificação funcional detalhada incluindo:

1. Descrição geral da funcionalidade
2. Objetivo e valor para o usuário
3. Comportamento esperado em diferentes cenários
4. Regras de negócio aplicáveis
5. Validações e restrições
6. Tratamento de exceções e erros
7. Fluxo detalhado de operação (passo a passo)
8. Mensagens exibidas ao usuário
9. Formatos de entrada e saída de dados
10. Requisitos de armazenamento de dados
11. Considerações de performance
12. Exemplos de uso com dados reais
13. Rastreabilidade para requisitos de negócio

Os detalhes devem ser específicos o suficiente para orientar tanto o desenvolvimento quanto os testes de aceitação, mas ainda centrados no comportamento funcional (não em implementação técnica).
```

## Prompt para Fluxos de Processo

```
Como especialista em análise de processos, preciso documentar os fluxos de processo para o sistema [nome do sistema] como parte do FSD.

Os principais processos de negócio suportados pelo sistema são:
- [Processo 1]
- [Processo 2]
- [Processo 3]

Para cada processo, por favor crie:

1. Descrição geral do processo
2. Objetivo e valor para o negócio
3. Atores e sistemas envolvidos
4. Pré-condições
5. Pós-condições
6. Fluxo detalhado do processo:
   - Etapas sequenciais numeradas
   - Pontos de decisão e ramificações (com condições claras)
   - Processamento paralelo (se aplicável)
   - Pontos de espera e continuação
   - Tratamento de exceções
7. Estados do processo e transições
8. Pontos de integração com outros sistemas
9. Duração típica e timeouts
10. Considerações de performance e escalabilidade
11. Métricas para monitoramento do processo
12. Exemplos de cenários comuns e excepcionais

Descreva cada processo em detalhe suficiente para que tanto usuários de negócio quanto implementadores técnicos possam entender completamente o fluxo de operações.
```

## Prompt para Interfaces do Sistema

```
Como analista de interfaces, preciso documentar as interfaces do sistema [nome do sistema] para inclusão no FSD.

O sistema possui os seguintes tipos de interfaces:
- Interfaces de usuário
- Interfaces com outros sistemas
- Interfaces de dados
- [outros tipos relevantes]

Para cada tipo de interface, por favor forneça:

1. Interfaces de Usuário:
   - Descrição funcional das principais telas
   - Elementos de interface e controles
   - Comportamento de navegação
   - Validações em nível de interface
   - Mensagens e notificações ao usuário
   - Variações para diferentes perfis de usuário

2. Interfaces com Outros Sistemas:
   - Sistemas externos com os quais o sistema se comunica
   - Tipo de comunicação (síncrona, assíncrona)
   - Formato dos dados trocados
   - Frequência e gatilhos de comunicação
   - Tratamento de falhas de comunicação
   - Requisitos de segurança

3. Interfaces de Dados:
   - Formatos de importação/exportação
   - Estrutura dos arquivos/mensagens
   - Validações de dados
   - Procedimentos de processamento

Para cada interface, inclua:
- Identificador único
- Propósito
- Atores/sistemas envolvidos
- Comportamento funcional detalhado
- Restrições e limitações
- Exemplos representativos
```

## Prompt para Regras de Negócio

```
Como analista de negócios, preciso documentar detalhadamente as regras de negócio para o sistema [nome do sistema] como parte do FSD.

Contexto do domínio:
- Área de negócio: [área de aplicação]
- Processos principais: [processos relevantes]
- Regulamentações aplicáveis: [regulamentações, se relevante]

Por favor, ajude-me a documentar as regras de negócio organizadas nas seguintes categorias:

1. Regras de Definição de Fatos:
   - Definições e classificações de entidades de negócio
   - Relações entre entidades
   - Estados válidos e transições

2. Regras de Restrição:
   - Limitações e restrições nos dados
   - Condições que devem ser satisfeitas
   - Validações obrigatórias

3. Regras de Derivação:
   - Cálculos e fórmulas
   - Derivação de informações
   - Inferências lógicas

4. Regras de Processo:
   - Sequências de operações
   - Condições para iniciar processos
   - Condições para concluir processos

Para cada regra de negócio, inclua:
- Identificador único (ex: RN-001)
- Descrição clara e concisa
- Justificativa ou fonte da regra
- Exemplos concretos de aplicação
- Exceções, se houver
- Impacto no comportamento do sistema
- Prioridade ou criticidade
```
