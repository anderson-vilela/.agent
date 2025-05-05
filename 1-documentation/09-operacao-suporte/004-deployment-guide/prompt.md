# deployment-guide

# Prompt para Deployment Guide

## Contexto

Estamos desenvolvendo o Deployment Guide para o sistema [NOME_DO_SISTEMA]. Este documento é essencial para garantir implantações consistentes, confiáveis e reproduzíveis nos diferentes ambientes (desenvolvimento, teste, homologação e produção).

## Objetivo

Criar um guia de implantação detalhado e prático que permita que equipes técnicas realizem o deployment do sistema de forma eficiente, minimizando erros e tempo de inatividade.

## Instruções

Por favor, ajude-me a desenvolver um Deployment Guide abrangente que inclua os seguintes componentes:

1. **Requisitos de Sistema**

   - Especificações de hardware (servidores, armazenamento, rede)
   - Software de base (sistema operacional, middlewares)
   - Dependências externas (bibliotecas, frameworks)
   - Configurações de ambiente (variáveis, acessos)

2. **Arquitetura de Deployment**

   - Topologia dos ambientes
   - Componentes do sistema e suas relações
   - Diagrama de infraestrutura
   - Configurações de rede e segurança

3. **Procedimento de Implantação Inicial**

   - Preparação do ambiente
   - Instalação de componentes
   - Configuração inicial
   - Carga de dados iniciais
   - Verificações pós-instalação

4. **Procedimento de Atualização**

   - Verificações pré-atualização
   - Processo de backup
   - Passos de atualização
   - Migração de dados (se aplicável)
   - Verificações pós-atualização

5. **Procedimento de Rollback**

   - Critérios para decisão de rollback
   - Passos para reversão
   - Restauração de dados
   - Verificações pós-rollback

6. **Configurações por Ambiente**

   - Parâmetros específicos para cada ambiente
   - Variáveis de ambiente
   - Controles de feature flags
   - Configurações de segurança específicas

7. **Verificação e Validação**
   - Testes de smoke
   - Verificações de sanidade
   - Checklist de validação
   - Monitoramento inicial

## Formato do Deployment Guide

O guia deve seguir esta estrutura:

1. **Visão Geral**

   - Introdução ao sistema
   - Componentes principais
   - Pré-requisitos gerais
   - Considerações importantes

2. **Matriz de Ambientes**

   - Tabela de ambientes (dev, teste, homologação, produção)
   - Diferenças entre ambientes
   - Responsáveis por cada ambiente
   - Janelas de manutenção

3. **Procedimentos Detalhados**

   - Instruções passo a passo com capturas de tela
   - Comandos exatos a serem executados
   - Arquivos de configuração de exemplo
   - Pontos de verificação

4. **Automação**

   - Scripts de deployment
   - Arquivos de configuração para ferramentas de CI/CD
   - Parâmetros de automação
   - Testes automatizados

5. **Troubleshooting**
   - Problemas comuns e soluções
   - Logs a serem verificados
   - Procedimentos de diagnóstico
   - Contatos para suporte

## Detalhes Específicos do Sistema

O sistema [NOME_DO_SISTEMA] possui as seguintes características que devem ser consideradas:

- Arquitetura: [DESCRIÇÃO_DA_ARQUITETURA]
- Bancos de dados: [INFORMAÇÕES_SOBRE_BANCO_DE_DADOS]
- Frameworks principais: [FRAMEWORKS_UTILIZADOS]
- Integrações: [SISTEMAS_INTEGRADOS]
- Considerações de segurança: [REQUISITOS_DE_SEGURANÇA]

## Requisitos de Disponibilidade

- Tempo máximo de inatividade para deployment: [TEMPO_MÁXIMO]
- Janelas de manutenção: [HORÁRIOS_PREFERENCIAIS]
- Notificações necessárias: [REQUISITOS_DE_NOTIFICAÇÃO]
- SLAs a serem mantidos: [SLAS_APLICÁVEIS]

## Entregáveis Esperados

Um guia de deployment completo seguindo a estrutura definida, incluindo diagramas de arquitetura, scripts de automação, checklists de verificação e exemplos de configuração para cada ambiente.
