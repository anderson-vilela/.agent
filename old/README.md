# Template Agent

Um framework estruturado para otimizar o desenvolvimento de software com GitHub Copilot e prompts de IA, estabelecendo um novo paradigma para colaboração entre desenvolvedores e ferramentas de inteligência artificial.

## Visão Geral

Este repositório contém um framework abrangente para potencializar o desenvolvimento de software utilizando engenharia de prompts e GitHub Copilot. Ele fornece estruturas, personas, workflows e padrões de código cuidadosamente desenvolvidos para maximizar a eficiência e qualidade em projetos de desenvolvimento.

### Filosofia do Projeto

O Template Agent foi concebido com base em três princípios fundamentais:

1. **Amplificação da Criatividade Humana**: O framework não busca substituir desenvolvedores, mas potencializar suas capacidades, permitindo que foquem em aspectos criativos e estratégicos do desenvolvimento.

2. **Consistência e Qualidade**: Através de personas bem definidas e workflows estruturados, o framework garante uma abordagem consistente, resultando em código mais limpo, testável e manutenível.

3. **Aceleração Responsável**: Embora a velocidade seja um benefício importante, o Template Agent prioriza a qualidade e a robustez, incentivando práticas como testes automatizados, documentação abrangente e revisões rigorosas.

### Benefícios Principais

- **Aumento de Produtividade**: Redução significativa no tempo de implementação de novas funcionalidades e correção de bugs.
- **Onboarding Acelerado**: Desenvolvedores recém-chegados podem entender rapidamente a base de código e contribuir de forma efetiva.
- **Consistência de Código**: Padronização em todo o projeto, facilitando manutenção e escalabilidade.
- **Documentação Integrada**: Geração de documentação técnica de alta qualidade como parte natural do processo de desenvolvimento.
- **Transferência de Conhecimento**: Captura e compartilhamento de expertise entre membros da equipe.

## Casos de Uso

O Template Agent é particularmente valioso em cenários como:

- **Projetos Enterprise**: Onde a consistência e a conformidade com políticas são essenciais
- **Startups em Crescimento Acelerado**: Ajudando a manter qualidade enquanto escala rapidamente
- **Equipes Distribuídas**: Facilitando a colaboração entre desenvolvedores em diferentes fusos horários
- **Modernização de Legados**: Guiando a refatoração e atualização de sistemas antigos
- **Educação e Treinamento**: Auxiliando desenvolvedores juniores a adotar boas práticas desde o início

## Estrutura do Projeto

A organização meticulosa dos diretórios reflete a abordagem holística do framework:

```
.agent/
├── aprendizado/               # Materiais educacionais para o time
│   ├── algoritmos/            # Explicações e implementações de algoritmos comuns
│   │   ├── estruturas-dados/  # Arrays, listas ligadas, árvores, grafos, hash tables
│   │   ├── ordenacao/         # QuickSort, MergeSort, HeapSort com análise de complexidade
│   │   ├── busca/             # Busca binária, BFS, DFS, A* com casos de uso
│   │   └── otimizacao/        # Programação dinâmica, algoritmos gulosos, backtracking
│   ├── explicacoes/           # Decomposição didática de conceitos complexos
│   │   ├── arquiteturais/     # Padrões como microserviços, event-driven, CQRS
│   │   ├── concorrencia/      # Threading, processos, sincronização, deadlocks
│   │   ├── networking/        # Protocolos, modelos OSI, REST, GraphQL, gRPC
│   │   └── seguranca/         # OWASP, criptografia, autenticação, autorização
│   ├── guias-rapidos/         # Referências concisas para uso diário
│   │   ├── apis/              # Documentações simplificadas de APIs comuns
│   │   ├── cli/               # Comandos frequentes para ferramentas de linha de comando
│   │   ├── git/               # Workflows de branching, resolução de conflitos
│   │   └── debugging/         # Técnicas e ferramentas para depuração eficiente
│   └── tutoriais/             # Guias passo-a-passo para tarefas complexas
│       ├── setup-ambiente/    # Configuração de ambientes de desenvolvimento
│       ├── implementacoes/    # Tutoriais hands-on para funcionalidades comuns
│       ├── refatoracao/       # Guias para melhorar código existente
│       └── otimizacao/        # Técnicas para melhorar performance
├── contexto/                  # Informações contextuais do projeto
│   ├── arquitetura/           # Visão geral e decisões arquiteturais
│   │   ├── diagramas/         # Visualizações C4, UML, fluxos de dados
│   │   ├── adr/               # Architecture Decision Records documentando escolhas
│   │   ├── componentes/       # Especificações de componentes principais
│   │   └── integracao/        # Detalhes sobre integração com sistemas externos
│   └── impacto/               # Documentação sobre o propósito e impacto do projeto
│       ├── metricas/          # KPIs e como são medidos
│       ├── usuarios/          # Perfis de usuários e suas necessidades
│       ├── negocio/           # Relevância e alinhamento com objetivos de negócio
│       └── tecnicos/          # Desafios e conquistas técnicas notáveis
├── padroes-codigo/            # Padrões reutilizáveis e boas práticas
│   ├── backend/               # Padrões para desenvolvimento de backend
│   │   ├── api/               # Design de endpoints, versionamento, documentação
│   │   ├── error-handling/    # Estratégias para tratamento de erros
│   │   ├── logging/           # Práticas para logging efetivo
│   │   └── validation/        # Técnicas para validação de entrada
│   ├── banco-de-dados/        # Melhores práticas para operações de banco
│   │   ├── migrations/        # Padrões para evolução de schema
│   │   ├── queries/           # Otimização de consultas
│   │   ├── transactions/      # Gerenciamento de transações
│   │   └── orm/               # Uso eficiente de ORMs
│   └── frontend/              # Padrões para desenvolvimento frontend
│       ├── components/        # Estrutura de componentes reutilizáveis
│       ├── state-management/  # Estratégias de gerenciamento de estado
│       ├── styling/           # Abordagens para CSS/estilização
│       └── testing/           # Estratégias para testes de UI
├── personas/                  # Perfis especializados para prompts de IA
│   ├── analise/               # Personas focadas em análise
│   │   ├── analista-dados/    # Especialista em análise e visualização de dados
│   │   ├── qa-specialist/     # Focado em garantia de qualidade e testes
│   │   └── analista-negocios/ # Traduz requisitos de negócio para técnicos
│   ├── compostas/             # Combinação de múltiplas especialidades
│   │   ├── fullstack-devops/  # Desenvolvimento full-stack com foco em infraestrutura
│   │   ├── security-architect/ # Arquiteto com especialização em segurança
│   │   └── data-engineer/     # Engenheiro de dados com conhecimento de ML
│   ├── desenvolvimento/       # Personas para implementação de código
│   │   ├── backend/           # Especialista em lógica de servidor e APIs
│   │   ├── frontend/          # Foco em interfaces e experiência do usuário
│   │   ├── devops/            # Automação de infraestrutura e deployment
│   │   └── mobile/            # Desenvolvimento para plataformas móveis
│   ├── entrevistadores/       # Personas para validação e questionamento
│   │   ├── code-reviewer/     # Focado em revisão crítica de código
│   │   ├── security-auditor/  # Especialista em identificar vulnerabilidades
│   │   └── architecture-critic/ # Avalia decisões arquiteturais
│   ├── especificas/           # Especialidades em nichos tecnológicos
│   │   ├── cloud-security/    # Arquiteto de segurança em ambientes cloud
│   │   ├── finops/            # Otimização de custos em infraestrutura
│   │   └── edge-computing/    # Especialista em computação de borda
│   └── gestao/                # Personas com foco em liderança
│       ├── cto/               # Visão técnica estratégica
│       ├── product-manager/   # Alinhamento entre técnica e negócio
│       ├── agile-coach/       # Facilitação de processos ágeis
│       └── tech-lead/         # Liderança técnica e mentoria
├── templates/                 # Modelos para documentos e tarefas
│   ├── docs/                  # Templates de documentação
│   │   ├── arquitetura/       # Documentos de design arquitetural
│   │   ├── api/               # Documentação de APIs
│   │   ├── onboarding/        # Guias para novos membros
│   │   └── release-notes/     # Notas de versão e changelog
│   └── tasks/                 # Templates para tipos comuns de tarefas
│       ├── feature/           # Implementação de novas funcionalidades
│       ├── bug-fix/           # Correção de defeitos
│       ├── refactoring/       # Melhorias de código existente
│       └── optimization/      # Otimizações de performance
└── workflows/                 # Fluxos de trabalho estruturados
   ├── design/                # Processos de design e arquitetura
   ├── planning/              # Planejamento e estimativa
   ├── development/           # Ciclo de desenvolvimento
   ├── testing/               # Estratégias de teste
   ├── review/                # Processos de revisão
   ├── deployment/            # Fluxos de implantação
   └── maintenance/           # Operações e manutenção
```

## Personas em Detalhe

Cada persona no framework é cuidadosamente construída para representar um especialista específico, com características e conhecimentos que orientam seu uso na engenharia de prompts.

### Estrutura das Personas

Cada perfil de persona inclui:

- **Bio Profissional**: Background fictício mas realista
- **Competências Técnicas**: Habilidades específicas e níveis de proficiência
- **Abordagem de Resolução de Problemas**: Metodologia característica
- **Tom de Comunicação**: Estilo de escrita e comunicação
- **Frameworks Conceituais**: Modelos mentais utilizados
- **Conhecimentos Especializados**: Áreas de expertise particular
- **Valores Profissionais**: Princípios que guiam as recomendações
- **Prompts de Ativação**: Comandos para "ativar" a persona

### Exemplos de Personas

#### Analista de Dados

**Bio**: Especialista com 8+ anos em análise quantitativa, visualização de dados e modelagem estatística.

**Competências**:

- Análise exploratória de dados
- Modelagem estatística avançada
- Visualização de dados
- SQL, Python, R e ferramentas de BI

**Abordagem**:

1. Compreender contexto do negócio
2. Explorar dados disponíveis
3. Identificar padrões e anomalias
4. Desenvolver modelos preditivos
5. Comunicar insights de forma clara e visual

**Prompt de Ativação Básico**:

```
Atue como um Analista de Dados experiente analisando o seguinte conjunto de dados para [objetivo].
Identifique padrões relevantes, forneça visualizações adequadas e recomende próximos passos.
```

**Prompt de Ativação Avançado**:

```
Você é um Analista de Dados Sênior com especialização em [domínio específico].
Contexto: [descrição do contexto de negócio]
Dados: [descrição ou amostra dos dados]
Objetivo: [meta específica da análise]

Por favor:
1. Conduza uma análise exploratória identificando variáveis-chave
2. Destaque correlações e anomalias significativas
3. Sugira 3 visualizações específicas que melhor comunicariam os insights encontrados
4. Recomende próximos passos analíticos com justificativas
5. Indique potenciais limitações ou vieses nos dados
```

#### Arquiteto de Segurança em Nuvem

**Bio**: Profissional com certificações avançadas em plataformas cloud (AWS, Azure, GCP) e 10+ anos em design de arquiteturas seguras.

**Competências**:

- Design de arquiteturas Zero Trust
- Implementação de Políticas IAM
- Proteção de dados em trânsito e em repouso
- Compliance com regulamentações (GDPR, HIPAA, PCI-DSS)
- Automação de segurança via IaC

**Abordagem**:

1. Mapear superfície de ataque
2. Analisar riscos por criticidade
3. Aplicar princípio do menor privilégio
4. Implementar defesa em profundidade
5. Automatizar controles de segurança
6. Validar com testes de penetração

**Prompt de Ativação Avançado**:

```
Você é um Arquiteto de Segurança em Nuvem especializado em [plataforma específica].
Contexto: [descrição da aplicação/infraestrutura]
Requisitos de Compliance: [regulamentações aplicáveis]
Nível de Sensibilidade dos Dados: [classificação]

Por favor:
1. Desenvolva uma arquitetura de segurança que atenda aos requisitos
2. Especifique controles para proteção de dados, acesso, rede e monitoramento
3. Identifique 5 riscos principais e respectivas mitigações
4. Sugira implementação via IaC com exemplos de código
5. Proponha estratégia de monitoramento contínuo e resposta a incidentes
```

## Workflows Detalhados

Os workflows do Template Agent são sequências estruturadas de passos, criadas para maximizar a eficiência e a qualidade em cada fase do desenvolvimento de software.

### 1. Design Arquitetural

**Objetivo**: Estabelecer fundamentos técnicos sólidos antes da implementação.

**Passos**:

1. **Definição de Requisitos**

   - Use a persona "Analista de Negócios" para refinar requisitos
   - Crie um documento de visão baseado no template `templates/docs/arquitetura/visao.md`
   - Identifique constraints técnicas e de negócio

2. **Exploração de Alternativas**

   - Use a persona "Arquiteto de Soluções" para gerar 2-3 abordagens diferentes
   - Avalie trade-offs usando o framework de decisão DREAD
   - Documente pros/contras de cada abordagem

3. **Design de Alto Nível**

   - Crie diagramas de arquitetura (C4 recomendado)
   - Defina componentes principais e suas interações
   - Estabeleça padrões de comunicação e interfaces

4. **Validação do Design**

   - Use a persona "Architecture Critic" para revisar
   - Conduza análise de riscos e mitigações
   - Valide alinhamento com requisitos não-funcionais

5. **Documentação**
   - Crie Architecture Decision Records (ADRs)
   - Documente definições técnicas usando o formato padrão
   - Prepare apresentação para stakeholders

**Artefatos Produzidos**:

- Documento de Visão Arquitetural
- Diagramas C4 (Contexto, Container, Componente)
- ADRs documentando decisões principais
- Análise de riscos e mitigações

### 2. Planejamento

**Objetivo**: Decompor o trabalho em tarefas gerenciáveis com estimativas realistas.

**Passos**:

1. **Decomposição de Requisitos**

   - Use a persona "Product Manager" para priorizar features
   - Divida features em user stories ou tarefas técnicas
   - Identifique dependências e caminho crítico

2. **Definição de Critérios de Aceitação**

   - Estabeleça critérios claros e testáveis
   - Inclua aspectos funcionais e não-funcionais
   - Defina métricas de sucesso

3. **Estimativa**

   - Use a técnica de Planning Poker ou T-shirt sizing
   - Considere complexidade, incerteza e esforço
   - Documente premissas que embasaram estimativas

4. **Planejamento de Sprints/Iterações**

   - Organize backlog por prioridade e dependências
   - Defina metas claras para cada iteração
   - Estabeleça pontos de verificação e marcos

5. **Alocação de Recursos**
   - Mapeie tarefas para competências específicas
   - Identifique necessidades de pairing ou mentoria
   - Considere balanceamento de carga de trabalho

**Artefatos Produzidos**:

- Backlog priorizado com estimativas
- Divisão de tarefas com critérios de aceitação
- Plano de iterações com marcos
- Matriz de responsabilidades

### 3. Implementação e Codificação

**Objetivo**: Produzir código limpo, testável e manutenível que atenda aos requisitos.

**Passos**:

1. **Setup do Ambiente**

   - Configure ambiente de desenvolvimento conforme guias
   - Assegure acesso a recursos necessários
   - Verifique disponibilidade de dependências

2. **Implementação Incremental**

   - Use TDD quando apropriado (Red-Green-Refactor)
   - Siga padrões de código estabelecidos
   - Implemente em incrementos pequenos e testáveis

3. **Revisão Contínua**

   - Realize auto-revisão usando a persona "Code Reviewer"
   - Verifique cobertura de testes
   - Valide contra critérios de aceitação

4. **Refatoração**

   - Identifique débitos técnicos emergentes
   - Refatore para clareza e manutenibilidade
   - Documente decisões de design significativas

5. **Integração**
   - Integre frequentemente com a base de código principal
   - Resolva conflitos de merge promptamente
   - Verifique impactos em componentes relacionados

**Artefatos Produzidos**:

- Código fonte seguindo padrões estabelecidos
- Testes unitários, de integração e end-to-end
- Documentação inline e comentários relevantes
- Commits atômicos com mensagens descritivas

### 4. Testes e Validação

**Objetivo**: Garantir que o software atenda aos requisitos funcionais e não-funcionais com alta qualidade.

**Passos**:

1. **Planejamento de Testes**

   - Use a persona "QA Specialist" para definir estratégia
   - Identifique níveis de teste necessários
   - Determine cobertura de teste alvo

2. **Implementação de Testes**

   - Desenvolva testes unitários para componentes isolados
   - Crie testes de integração para interfaces
   - Implemente testes end-to-end para fluxos críticos

3. **Validação de Qualidade**

   - Execute análise estática de código
   - Verifique métricas de complexidade
   - Valide padrões de segurança (OWASP)

4. **Testes de Performance**

   - Identifique requisitos de performance
   - Realize testes de carga e stress
   - Analise resultados e otimize gargalos

5. **Validação de Usabilidade**
   - Avalie experiência do usuário
   - Verifique acessibilidade
   - Colete feedback qualitativo

**Artefatos Produzidos**:

- Plano de teste detalhado
- Suítes de teste automatizadas
- Relatórios de análise estática e cobertura
- Resultados de testes de performance
- Documentação de bugs encontrados

### 5. Documentação

**Objetivo**: Criar documentação abrangente e acessível para diferentes públicos.

**Passos**:

1. **Planejamento da Documentação**

   - Identifique audiências-alvo
   - Defina tipos de documentação necessários
   - Estabeleça formatos e canais

2. **Documentação Técnica**

   - Documente arquitetura e componentes
   - Crie guias de referência para APIs
   - Desenvolva documentação para contribuidores

3. **Documentação de Usuário**

   - Crie manuais de usuário
   - Desenvolva tutoriais passo-a-passo
   - Produza FAQs e troubleshooting guides

4. **Onboarding**

   - Crie guias para novos membros da equipe
   - Documente processos de desenvolvimento
   - Estabeleça recursos de aprendizado

5. **Manutenção da Documentação**
   - Estabeleça processo de atualização
   - Implemente versionamento da documentação
   - Colete feedback sobre clareza e completude

**Artefatos Produzidos**:

- Documentação técnica estruturada
- Manuais de usuário e guias
- Vídeos tutoriais quando apropriado
- Wiki interno para conhecimento da equipe

## Como Utilizar

O Template Agent foi projetado para ser flexível e adaptável a diferentes contextos de desenvolvimento. Siga estas etapas para maximizar seu valor:

### 1. Configuração Inicial

1. **Clone o Repositório**:

   ```bash
   git clone https://github.com/anderson-vilela/template-agent.git
   cd template-agent
   ```

2. **Personalize para seu Projeto**:

   - Modifique o arquivo README principal
   - Atualize informações específicas nos templates
   - Adapte a estrutura conforme necessidades do projeto

3. **Compartilhe com a Equipe**:
   - Realize uma sessão de onboarding
   - Destaque os benefícios e fluxos principais
   - Colete feedback inicial para ajustes

### 2. Seleção de Personas

1. **Identifique o Contexto**: Determine o tipo de tarefa ou desafio atual

2. **Escolha a Persona Apropriada**: Navegue pelo diretório `personas/` e selecione a mais relevante:

   - Para arquitetura: Arquiteto de Soluções ou Arquiteto de Segurança
   - Para implementação: Desenvolvedor Backend/Frontend/FullStack
   - Para otimização: Performance Engineer ou Especialista em Escalabilidade
   - Para revisão: Code Reviewer ou Security Auditor

3. **Estude o Perfil da Persona**:
   - Familiarize-se com suas competências e abordagem
   - Entenda seu estilo de comunicação e valores
   - Revise exemplos de uso bem-sucedidos

### 3. Utilização de Prompts

1. **Selecione o Prompt Apropriado**:

   - Use prompts básicos para tarefas simples e bem definidas
   - Utilize prompts avançados para desafios complexos
   - Customize conforme necessário para seu contexto específico

2. **Forneça Contexto Claro**:

   - Inclua informações relevantes sobre o projeto
   - Especifique constraints e requisitos importantes
   - Mencione tecnologias e frameworks utilizados

3. **Aplicação de Prompts com GitHub Copilot**:

   - No VSCode, insira o prompt como comentário
   - Use o formato recomendado para a persona escolhida
   - Seja específico sobre o resultado desejado

   **Exemplo**:

   ```python
   # Atuando como Security Architect, analise o seguinte código em busca de
   # vulnerabilidades OWASP Top 10 e sugira correções:

   def authenticate_user(username, password):
      query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
      user = db.execute(query).fetchone()
      if user:
         return generate_session_token(user.id)
      return None
   ```

4. **Itere e Refine**:
   - Avalie as respostas iniciais
   - Faça perguntas de follow-up para aprofundar
   - Ajuste o prompt conforme necessário para direcionar melhor

### 4. Aplicação de Workflows

1. **Selecione o Workflow Apropriado**:

   - Escolha baseado na fase atual do projeto
   - Consulte a documentação detalhada em `workflows/`

2. **Siga as Etapas Sequenciais**:

   - Execute cada passo na ordem recomendada
   - Utilize os templates sugeridos para cada etapa
   - Documente decisões e resultados

3. **Adapte Conforme Necessário**:
   - Ajuste o workflow para seu contexto específico
   - Combine elementos de diferentes workflows quando apropriado
   - Documente adaptações para referência futura

### 5. Utilização de Padrões de Código

1. **Consulte o Catálogo de Padrões**:

   - Explore `padroes-codigo/` para seu domínio específico
   - Entenda o contexto e problema que cada padrão resolve

2. **Aplique ao seu Código**:

   - Use os padrões como ponto de partida
   - Personalize para seu caso de uso específico
   - Mantenha a consistência com outras partes do projeto

3. **Contribua com Novos Padrões**:
   - Identifique soluções recorrentes no projeto
   - Documente-as seguindo o formato estabelecido
   - Compartilhe com a equipe para feedback

## Melhores Práticas

1. **Iteração Incremental**:

   - Comece com prompts simples e refine gradualmente
   - Construa sobre respostas anteriores do Copilot
   - Salve prompts eficazes para reuso

2. **Comunicação Clara**:

   - Seja específico sobre o contexto e requisitos
   - Forneça exemplos concretos quando possível
   - Esclareça terminologia específica do domínio

3. **Revisão Humana**:

   - Sempre revise criticamente as sugestões do Copilot
   - Valide soluções contra requisitos e boas práticas
   - Use personas diferentes para obter perspectivas diversas

4. **Documentação Contínua**:

   - Capture insights importantes gerados via prompts
   - Documente decisões e rationales
   - Atualize templates conforme evoluem

5. **Aprendizado e Adaptação**:
   - Compartilhe prompts eficazes com a equipe
   - Colete feedback sobre utilidade das personas
   - Evolua o framework baseado na experiência prática

## Contribuição

Este framework é um projeto vivo que se beneficia da contribuição coletiva. Para contribuir:

1. **Personas Novas**:

   - Crie perfis completos seguindo o template existente
   - Inclua exemplos de prompts testados
   - Documente casos de uso ideais

2. **Workflows**:

   - Proponha novas sequências para casos específicos
   - Melhore workflows existentes com lições aprendidas
   - Adicione exemplos concretos de uso

3. **Padrões de Código**:

   - Contribua com soluções reutilizáveis
   - Inclua contexto, problema e solução
   - Forneça exemplos de implementação

4. **Processo de Contribuição**:
   - Fork o repositório
   - Crie um branch para sua contribuição
   - Submeta PR com descrição detalhada
   - Responda a feedback dos revisores

## FAQ

**P: Como o Template Agent difere de simplesmente usar o GitHub Copilot diretamente?**

R: O Template Agent fornece uma estrutura organizada e sistemática para interações com o Copilot, com personas especializadas, workflows testados e padrões reutilizáveis que maximizam o valor gerado.

**P: Este framework substitui boas práticas de engenharia de software?**

R: Não. O Template Agent complementa e reforça boas práticas, incorporando-as em seus workflows e padrões. Revisões de código, testes automatizados e outros processos continuam essenciais.

**P: Como mensurar o impacto do uso deste framework?**

R: Recomendamos acompanhar métricas como tempo de desenvolvimento, qualidade de código (via análise estática), cobertura de testes e feedback qualitativo da equipe antes e após a implementação.

**P: O framework funciona apenas com GitHub Copilot?**

R: Embora otimizado para o Copilot, os princípios, personas e workflows podem ser adaptados para outras ferramentas de IA como ChatGPT, Claude ou Bard.

## Licença

Este projeto é licenciado sob MIT - veja o arquivo LICENSE para detalhes.

## Agradecimentos

- Aos contribuidores que ajudaram a construir e refinar este framework
- À comunidade de engenharia de prompts por insights valiosos
- Às equipes que testaram e forneceram feedback para melhoria contínua
