# Prompts para Documentos de Casos de Teste

Este documento contém prompts específicos para gerar Documentos de Casos de Teste, que detalham os cenários e procedimentos de teste a serem executados.

## Prompt para Documento Completo de Casos de Teste

```prompt
Atue como um analista de testes experiente. Preciso criar um conjunto abrangente de casos de teste para a funcionalidade [nome da funcionalidade] do sistema [nome do sistema].

Contexto da funcionalidade:
- [Descrever a funcionalidade em detalhes]
- [Especificar requisitos funcionais e não-funcionais relevantes]
- [Mencionar regras de negócio importantes]
- [Descrever interfaces e integrações envolvidas]

Por favor, desenvolva um documento de casos de teste detalhado que inclua:

1. Introdução e escopo:
   - Finalidade e objetivos dos casos de teste
   - Funcionalidades e requisitos cobertos
   - Pré-requisitos gerais para execução

2. Mapeamento de requisitos:
   - Matriz de rastreabilidade entre requisitos e casos de teste
   - Cobertura de requisitos funcionais e não-funcionais
   - Verificação de completude da cobertura

3. Ambiente de teste:
   - Configurações de hardware e software necessárias
   - Versões específicas de componentes
   - Dados e configurações pré-requisitos

4. Casos de teste detalhados, cada um incluindo:
   - Identificador único e título descritivo
   - Objetivo/propósito do teste
   - Pré-condições específicas
   - Dados de teste necessários
   - Passos detalhados para execução
   - Resultados esperados para cada passo
   - Critérios de aprovação/falha
   - Severidade e prioridade
   - Requisitos específicos de ambiente

5. Casos especiais e testes de borda:
   - Cenários de erro e exceção
   - Valores limite e casos extremos
   - Testes de carga/performance (se aplicável)
   - Testes de segurança específicos (se aplicável)

6. Dependências e sequência:
   - Ordem recomendada de execução
   - Dependências entre casos de teste
   - Agrupamentos lógicos (suites)

7. Instruções para automação (se aplicável):
   - Recomendações de frameworks
   - Considerações especiais para automação
   - Priorização para automação

Organize os casos de teste de forma estruturada, começando com cenários básicos e positivos, progredindo para casos mais complexos e negativos. Use uma numeração clara e consistente, e forneça descrições suficientemente detalhadas para que qualquer testador possa executá-los sem ambiguidade.
```

## Prompt para Casos de Teste Funcionais

```prompt
Como especialista em testes funcionais, preciso criar um conjunto abrangente de casos de teste para validar a funcionalidade [nome da funcionalidade] do nosso sistema.

Informações sobre a funcionalidade:
- Descrição: [breve descrição da funcionalidade]
- Requisitos principais: [listar requisitos funcionais principais]
- Fluxos de usuário: [descrever fluxos principais e alternativos]
- Regras de negócio: [listar regras de negócio relevantes]
- Interfaces envolvidas: [descrever interfaces de usuário/APIs]

Por favor, crie um conjunto estruturado de casos de teste funcionais que inclua:

1. Testes de fluxo principal (happy path):
   - Casos que validam o comportamento esperado no cenário ideal
   - Verificação de todas as etapas do processo normal
   - Validação de transições de estado corretas

2. Testes de fluxos alternativos:
   - Variações permitidas do fluxo principal
   - Caminhos opcionais dentro da funcionalidade
   - Diferentes combinações de entradas válidas

3. Testes de validação de entrada:
   - Verificação de campos obrigatórios
   - Validações de formato, comprimento e tipo
   - Tratamento de caracteres especiais
   - Normalização de entradas (maiúsculas/minúsculas, espaços)

4. Testes de borda e valores limite:
   - Valores mínimos e máximos permitidos
   - Valores no limite de restrições
   - Transições entre diferentes estados ou categorias

5. Testes negativos e de tratamento de erros:
   - Entradas inválidas e comportamento esperado
   - Manipulação de erros e mensagens apropriadas
   - Recuperação de estados de erro
   - Validação de integridade após erros

6. Testes de integração funcional:
   - Interações com outros módulos/componentes
   - Verificação de fluxos de dados entre componentes
   - Validação de resultados integrados

Para cada caso de teste, forneça:
- ID único e nome descritivo
- Objetivo específico do teste
- Pré-condições necessárias
- Dados de teste específicos
- Passos detalhados para execução
- Resultado esperado para cada passo
- Critérios de aprovação
- Prioridade (Alta/Média/Baixa)

Os casos de teste devem ser claros, reproduzíveis e focados em um único aspecto da funcionalidade por caso. Organize-os em uma sequência lógica e inclua campos para registro de resultados e observações.
```

## Prompt para Casos de Teste de Interface do Usuário

```prompt
Como especialista em testes de interface do usuário, preciso desenvolver casos de teste detalhados para a interface [nome da interface] do sistema [nome do sistema]. Esta interface permite aos usuários [descreva brevemente a funcionalidade principal].

Considerando as especificações de UI/UX e os requisitos funcionais, crie um conjunto completo de casos de teste de interface que abordem:

1. Verificação de elementos visuais:
   - Presença e posicionamento correto de todos os elementos
   - Consistência com o design especificado (cores, fontes, tamanhos)
   - Alinhamento e espaçamento adequados
   - Responsividade em diferentes tamanhos de tela (se aplicável)
   - Conformidade com guias de estilo do projeto

2. Testes de navegação e fluxo:
   - Funcionamento correto de links e botões
   - Navegação entre telas/páginas
   - Breadcrumbs e indicadores de localização
   - Atalhos de teclado e acessibilidade básica
   - Histórico e comportamento de voltar/avançar (se aplicável)

3. Testes de formulários e entrada de dados:
   - Validação em tempo real de campos
   - Mensagens de erro claras e posicionadas corretamente
   - Comportamento de campos obrigatórios
   - Persistência apropriada de dados entre etapas
   - Verificação de auto-completar e valores padrão

4. Testes de feedback ao usuário:
   - Loaders e indicadores de progresso
   - Mensagens de sucesso, erro e alerta
   - Tooltips e ajudas contextuais
   - Confirmações para ações destrutivas ou importantes

5. Testes de funcionalidade específica de UI:
   - Comportamento de widgets interativos (sliders, tabs, dropdowns)
   - Arrastar e soltar (drag and drop) onde aplicável
   - Carregamento dinâmico de conteúdo
   - Animações e transições
   - Atualização em tempo real de informações

6. Testes de acessibilidade (básicos):
   - Navegação por teclado
   - Textos alternativos para imagens
   - Contraste de cores adequado
   - Redimensionamento de texto
   - Compatibilidade com leitores de tela (se aplicável)

7. Testes de compatibilidade (se aplicável):
   - Diferentes navegadores
   - Diferentes dispositivos (desktop, tablet, mobile)
   - Diferentes sistemas operacionais
   - Diferentes resoluções de tela

Para cada caso de teste, inclua:
- Identificador e título descritivo
- Plataformas/ambientes específicos para teste
- Pré-condições e configuração inicial
- Passos detalhados para verificação visual e interativa
- Resultados esperados em termos de aparência e comportamento
- Critérios específicos de aprovação/falha
- Capturas de tela de referência (quando relevante)

Os casos devem ser organizados por componente ou área funcional da interface, permitindo testes modulares e focados.
```

## Prompt para Casos de Teste de Performance

```prompt
Como especialista em testes de performance, preciso desenvolver casos de teste detalhados para avaliar o desempenho do [componente/sistema]. Este [componente/sistema] tem requisitos de performance que incluem [descreva os requisitos não-funcionais relacionados a performance, como tempos de resposta, throughput, escalabilidade].

Por favor, crie um conjunto abrangente de casos de teste de performance que inclua:

1. Testes de carga (Load Testing):
   - Cenários que simulam carga típica esperada
   - Verificação de comportamento sob carga crescente
   - Monitoramento de tempo de resposta e throughput
   - Validação com múltiplos usuários concorrentes
   - Verificação de estabilidade durante operação contínua

2. Testes de stress:
   - Cenários que excedem os limites operacionais esperados
   - Comportamento próximo e além da capacidade máxima
   - Identificação de pontos de quebra e falha
   - Verificação de degradação graceful
   - Capacidade de recuperação após sobrecarga

3. Testes de escalabilidade:
   - Verificação de comportamento com aumento de usuários/dados
   - Testes com diferentes configurações de recursos
   - Validação de aumento horizontal vs. vertical
   - Identificação de gargalos de escalabilidade
   - Comportamento com balanceamento de carga

4. Testes de resistência (Endurance):
   - Comportamento durante operação prolongada
   - Detecção de memory leaks e problemas de recursos
   - Verificação de degradação de performance ao longo do tempo
   - Monitoramento de uso de recursos durante execução prolongada

5. Testes de pico (Spike Testing):
   - Resposta a aumentos repentinos e significativos de carga
   - Capacidade de absorver variações drásticas de demanda
   - Tempo de recuperação após picos de utilização

Para cada caso de teste, especifique:
- Objetivo específico e métricas alvo
- Configuração do ambiente de teste
- Volumetria e perfil de dados necessários
- Perfil de carga (usuários, transações, etc.)
- Duração do teste
- Passos detalhados para execução
- Parâmetros e métricas a serem monitorados
- Critérios de aprovação baseados em limites específicos
- Procedimentos para análise de resultados

Inclua recomendações para as ferramentas de teste de performance a serem utilizadas, configurações especiais necessárias, e instruções para a interpretação dos resultados coletados.
```

## Prompt para Testes de Segurança

```prompt
Como especialista em testes de segurança, preciso desenvolver casos de teste para avaliar a segurança do [componente/funcionalidade] no sistema [nome do sistema]. Esta parte do sistema lida com [descrever dados sensíveis/funcionalidades críticas] e precisa estar protegida contra diversas ameaças de segurança.

Por favor, crie um conjunto abrangente de casos de teste de segurança alinhados com padrões como OWASP, que incluam:

1. Testes de autenticação:
   - Verificação de políticas de senha (complexidade, histórico, expiração)
   - Proteção contra tentativas repetidas de login (lockout)
   - Segurança do processo de recuperação de senha
   - Validação de gestão de sessão (timeout, invalidação)
   - Multi-fator e mecanismos avançados (se aplicáveis)

2. Testes de autorização:
   - Verificação de controles de acesso baseado em perfis
   - Tentativas de escalação de privilégios
   - Acesso a funcionalidades restritas
   - Validação de separação de responsabilidades
   - Teste de acesso após logout/timeout

3. Testes de validação de entrada:
   - Injeção de SQL e NoSQL
   - Cross-Site Scripting (XSS)
   - Command Injection
   - Validação de upload de arquivos
   - Manipulação de parâmetros e headers

4. Testes de gerenciamento de dados sensíveis:
   - Verificação de criptografia em trânsito (HTTPS, TLS)
   - Criptografia de dados em armazenamento
   - Proteção de dados sensíveis em logs e mensagens de erro
   - Conformidade com regulações (ex: GDPR, LGPD)
   - Mascaramento/ofuscação de dados sensíveis em interfaces

5. Testes de configuração e infraestrutura:
   - Verificação de headers de segurança HTTP
   - Configurações seguras de servidores e frameworks
   - Exposição de informações sensíveis em metadados
   - Verificação de patches e atualizações de segurança
   - Configurações padrão e contas de demonstração

6. Outras verificações específicas:
   - Cross-Site Request Forgery (CSRF)
   - Vulnerabilidades de API específicas
   - Server-Side Request Forgery
   - Lógica de negócio que pode ser abusada
   - Proteções contra bots e automação maliciosa

Para cada caso de teste, especifique:
- Objetivo e tipo de vulnerabilidade alvo
- Ferramentas ou técnicas recomendadas
- Passos detalhados para reprodução
- Resultados esperados (comportamento seguro)
- Critérios para classificação de severidade
- Recomendações de mitigação em caso de falha
- Conformidade com padrões ou regulações aplicáveis

Organize os casos de teste por categoria de vulnerabilidade e inclua referências a padrões relevantes (OWASP Top 10, SANS Top 25, etc.). Enfatize que os testes devem ser realizados em ambiente controlado com autorização apropriada.
```

## Prompt para Matriz de Rastreabilidade de Requisitos

```prompt
Como analista de qualidade, preciso criar uma matriz de rastreabilidade abrangente que vincule os requisitos do [nome do projeto/funcionalidade] aos casos de teste correspondentes. Esta matriz é essencial para garantir cobertura completa dos requisitos e facilitar a gestão de impacto quando mudanças ocorrem.

Considerando o seguinte conjunto de requisitos:
[Liste os requisitos principais ou referencie o documento de requisitos]

E considerando os casos de teste já definidos:
[Liste os casos de teste ou referencie o documento de casos de teste]

Por favor, desenvolva uma matriz de rastreabilidade detalhada que:

1. Mapeie cada requisito para os casos de teste correspondentes:
   - Identificação clara do requisito (ID e breve descrição)
   - IDs dos casos de teste que verificam o requisito
   - Tipo de cobertura (completa, parcial)
   - Observações sobre aspectos específicos testados

2. Identifique a cobertura bidirecional:
   - Quais requisitos são verificados por cada caso de teste
   - Quais casos de teste verificam cada requisito
   - Identificação de redundâncias ou sobreposições

3. Análise de gaps de cobertura:
   - Requisitos sem cobertura de teste adequada
   - Casos de teste sem vínculo claro com requisitos
   - Recomendações para preencher lacunas identificadas

4. Priorização e criticidade:
   - Indicação de requisitos críticos para o negócio
   - Prioridade dos casos de teste correspondentes
   - Requisitos com cobertura insuficiente considerando sua criticidade

5. Métricas de cobertura:
   - Porcentagem de requisitos cobertos por testes
   - Distribuição de casos de teste por requisito
   - Análise de suficiência da cobertura

6. Estrutura para gestão de mudanças:
   - Processo para atualização da matriz quando requisitos mudam
   - Identificação rápida de impacto em testes quando requisitos são modificados
   - Procedimento para garantir que a matriz permaneça sincronizada

A matriz deve ser apresentada em formato tabular claro, com codificação visual (cores ou símbolos) para facilitar a identificação rápida de problemas de cobertura. Inclua também uma análise sumária que destaque as principais conclusões sobre a cobertura atual e recomendações para melhorias.
```
