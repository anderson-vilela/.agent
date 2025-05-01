# Prompt para Disaster Recovery Plan (DRP)

## Contexto

Estamos desenvolvendo um Disaster Recovery Plan (DRP) para o sistema [NOME_DO_SISTEMA]. Este documento é essencial para garantir a continuidade operacional e rápida recuperação em caso de eventos disruptivos que afetem a disponibilidade ou integridade do sistema.

## Objetivo

Criar um DRP abrangente e prático que estabeleça procedimentos claros para recuperação do sistema em diversos cenários de desastre, minimizando tempos de inatividade e perda de dados.

## Instruções

Por favor, ajude-me a desenvolver um DRP que inclua os seguintes componentes:

1. **Análise de Impacto de Negócio (BIA)**

   - Identificação dos componentes críticos do sistema
   - Definição de RTO (Recovery Time Objective) e RPO (Recovery Point Objective)
   - Avaliação do impacto de inatividade por componente
   - Dependências entre componentes e serviços

2. **Cenários de Desastre**

   - Interrupção de serviços de infraestrutura (energia, rede)
   - Falha de hardware crítico
   - Comprometimento de segurança (ransomware, ataques cibernéticos)
   - Desastres naturais ou físicos
   - Falhas humanas críticas

3. **Estratégias de Recuperação**

   - Arquitetura de alta disponibilidade
   - Políticas e procedimentos de backup
   - Infraestrutura alternativa (DR site, cloud)
   - Configurações de redundância

4. **Procedimentos de Recuperação Detalhados**

   - Passos para restauração de dados
   - Procedimentos de failover
   - Reinicialização e verificação de serviços
   - Configurações de rede e segurança
   - Testes pós-recuperação

5. **Estrutura de Resposta a Desastres**

   - Equipe de resposta e responsabilidades
   - Fluxo de escalonamento
   - Protocolos de comunicação
   - Critérios para declaração de desastre

6. **Plano de Testes e Manutenção**
   - Calendário de testes
   - Metodologia de simulações
   - Processos de revisão e atualização
   - Documentação de resultados de testes

## Formato do DRP

O documento deve seguir esta estrutura:

1. **Resumo Executivo**

   - Propósito do plano
   - Escopo e sistemas cobertos
   - Principais métricas (RTO/RPO)
   - Visão geral da estratégia

2. **Análise de Impacto**

   - Tabela de componentes críticos
   - Impacto por tempo de inatividade
   - Prioridades de recuperação
   - Interdependências de sistemas

3. **Estratégias e Recursos**

   - Backup e retenção
   - Infraestrutura de DR
   - Recursos humanos necessários
   - Recursos técnicos e ferramentas

4. **Procedimentos por Cenário**

   - Instruções passo a passo por tipo de desastre
   - Checklists de atividades
   - Pontos de decisão e verificação
   - Critérios de sucesso

5. **Gestão do Plano**
   - Papéis e responsabilidades
   - Processos de manutenção
   - Cronograma de revisões
   - Histórico de testes e atualizações

## Considerações Específicas do Sistema

O sistema [NOME_DO_SISTEMA] possui as seguintes características críticas que devem ser abordadas:

- Arquitetura: [DETALHES_DA_ARQUITETURA]
- Dados críticos: [TIPOS_DE_DADOS_CRÍTICOS]
- Integrações: [SISTEMAS_INTEGRADOS_CRÍTICOS]
- Requisitos regulatórios: [REGULAMENTAÇÕES_APLICÁVEIS]
- Janelas de operação: [HORÁRIOS_CRÍTICOS]

## Métricas e Requisitos

- RTO máximo aceitável: [TEMPO_MÁXIMO_DE_RECUPERAÇÃO]
- RPO máximo aceitável: [PERDA_MÁXIMA_DE_DADOS]
- Disponibilidade esperada: [PERCENTUAL_DE_UPTIME]
- Frequência de testes: [FREQUÊNCIA_DE_TESTES]

## Entregáveis Esperados

Um DRP completo seguindo a estrutura definida, incluindo diagramas de processo, matrizes de responsabilidade, procedimentos detalhados, e templates para documentação de testes e incidentes.
