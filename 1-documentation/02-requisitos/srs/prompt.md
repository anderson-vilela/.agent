# Prompts para Software Requirements Specification (SRS)

## Prompt para Estrutura Completa do SRS

```
Você é um analista de sistemas experiente especializado em documentação de requisitos técnicos. Preciso da sua ajuda para criar um Software Requirements Specification (SRS) completo para [nome do sistema], seguindo as melhores práticas e padrões da indústria (como IEEE 830).

Contexto do sistema:
- Descrição: [breve descrição do sistema]
- Principais funcionalidades: [lista das principais funcionalidades]
- Integrações necessárias: [sistemas ou APIs com os quais este sistema deve integrar]
- Restrições técnicas conhecidas: [quaisquer limitações técnicas]

Por favor, crie um SRS detalhado que inclua:
1. Introdução (propósito, escopo, definições, referências)
2. Descrição geral (perspectiva do produto, funções, características dos usuários, restrições, suposições)
3. Requisitos específicos:
   - Requisitos funcionais detalhados (organizados por funcionalidade)
   - Requisitos não-funcionais (desempenho, segurança, usabilidade, confiabilidade, etc.)
   - Requisitos de interface externa (usuário, hardware, software, comunicações)
4. Modelos analíticos relevantes
5. Apêndices necessários

Use linguagem técnica precisa, mas que ainda possa ser compreendida por stakeholders não-técnicos quando necessário.
```

## Prompt para Especificação de Requisitos Funcionais

```
Como analista de requisitos, preciso definir detalhadamente os requisitos funcionais para o sistema [nome do sistema] que serão incluídos no SRS.

Com base nas seguintes informações:
- Funcionalidades principais: [lista de funcionalidades]
- Usuários: [tipos de usuários do sistema]
- Processos de negócio: [descrição dos processos relevantes]

Para cada funcionalidade abaixo, ajude-me a criar uma especificação completa incluindo:
1. ID único do requisito (ex: RF-001)
2. Descrição detalhada
3. Atores envolvidos
4. Pré-condições
5. Pós-condições
6. Fluxo principal (passo a passo)
7. Fluxos alternativos
8. Fluxos de exceção
9. Requisitos especiais
10. Critérios de aceitação verificáveis

Funcionalidades para especificar:
- [Funcionalidade 1]
- [Funcionalidade 2]
- [Funcionalidade 3]
```

## Prompt para Requisitos Não-Funcionais

```
Como especialista em engenharia de requisitos, preciso definir os requisitos não-funcionais para o sistema [nome do sistema] para inclusão no SRS.

Contexto do sistema:
- Tipo de aplicação: [web, mobile, desktop, etc.]
- Escala esperada: [número de usuários, volume de dados, etc.]
- Criticidade: [baixa, média, alta]
- Ambiente de operação: [descrição do ambiente]

Por favor, ajude-me a definir requisitos não-funcionais detalhados e mensuráveis para as seguintes categorias:

1. Desempenho (tempo de resposta, throughput, utilização de recursos)
2. Segurança (autenticação, autorização, criptografia, proteção de dados)
3. Confiabilidade (disponibilidade, tolerância a falhas, recuperabilidade)
4. Usabilidade (acessibilidade, facilidade de aprendizado, eficiência de uso)
5. Manutenibilidade (modularidade, testabilidade, modificabilidade)
6. Portabilidade (adaptabilidade, instalabilidade, compatibilidade)
7. Escalabilidade (horizontal, vertical, gerenciamento de carga)
8. Conformidade (regulamentos, padrões, certificações aplicáveis)

Para cada requisito, inclua:
- ID único (ex: RNF-001)
- Descrição clara
- Justificativa
- Critério de medição/verificação
- Prioridade
```

## Prompt para Casos de Uso Detalhados

```
Como analista de sistemas, preciso desenvolver casos de uso detalhados para o sistema [nome do sistema] para inclusão no SRS.

Baseado nas seguintes funcionalidades principais:
- [Funcionalidade 1]
- [Funcionalidade 2]
- [Funcionalidade 3]

Para cada caso de uso associado a estas funcionalidades, por favor desenvolva:

1. Identificador único do caso de uso
2. Nome do caso de uso
3. Descrição breve
4. Atores (primários e secundários)
5. Pré-condições
6. Pós-condições (sucesso e falha)
7. Fluxo básico (numerado e detalhado)
8. Fluxos alternativos
9. Fluxos de exceção
10. Requisitos especiais (não-funcionais associados)
11. Frequência esperada de ocorrência
12. Regras de negócio aplicáveis
13. Considerações de implementação (opcional)
14. Notas e questões em aberto

Se possível, inclua também um diagrama de caso de uso em notação UML para contextualizar como os casos de uso se relacionam entre si.
```

## Prompt para Modelo de Dados Conceitual

```
Como arquiteto de dados, preciso desenvolver um modelo de dados conceitual para o sistema [nome do sistema] para inclusão no SRS.

O sistema possui as seguintes entidades principais:
- [Entidade 1]
- [Entidade 2]
- [Entidade 3]

Para cada entidade, considere:
- Atributos principais
- Relações com outras entidades
- Restrições e regras de integridade

Por favor, descreva:

1. Um modelo conceitual de dados em formato textual detalhado, incluindo:
   - Descrição de cada entidade
   - Atributos de cada entidade (incluindo tipos e restrições)
   - Relacionamentos entre entidades (cardinalidade, obrigatoriedade)
   - Restrições de integridade e regras de negócio aplicáveis
   - Considerações sobre volume de dados e histórico

2. Recomendações para a implementação física deste modelo, incluindo:
   - Considerações sobre normalização/desnormalização
   - Índices recomendados
   - Estratégias para performance
   - Considerações sobre escalabilidade

Se possível, inclua uma representação textual do diagrama de entidade-relacionamento.
```

## Prompt para Requisitos de Interface

```
Como especialista em interfaces de sistema, preciso documentar os requisitos de interface para o sistema [nome do sistema] no SRS.

O sistema precisa interagir com:
- [Interface externa 1]
- [Interface externa 2]
- [Interface externa 3]

Para cada interface, por favor especifique:

1. Interfaces de Usuário:
   - Tipos de interfaces (web, mobile, desktop)
   - Requisitos de design e layout
   - Fluxos de navegação essenciais
   - Requisitos de acessibilidade
   - Comportamentos esperados em diferentes dispositivos

2. Interfaces de Hardware:
   - Dispositivos suportados
   - Requisitos de conectividade
   - Restrições físicas
   - Protocolos de comunicação

3. Interfaces de Software:
   - APIs e serviços externos
   - Protocolos e formatos de comunicação
   - Frequência de comunicação
   - Tratamento de erros de comunicação
   - Requisitos de autenticação

4. Interfaces de Comunicação:
   - Protocolos de rede
   - Requisitos de largura de banda
   - Segurança na comunicação
   - Persistência de conexão

Para cada requisito de interface, inclua:
- ID único
- Descrição detalhada
- Restrições e limites
- Considerações de segurança
- Requisitos de desempenho específicos
```
