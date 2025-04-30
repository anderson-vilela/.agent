# Template Agent 2.0

Um framework abrangente que potencializa o desenvolvimento de software com GitHub Copilot e engenharia de prompts, estabelecendo um novo paradigma para colaboração entre desenvolvedores e ferramentas de inteligência artificial.

## Visão Geral

O Template Agent 2.0 é uma evolução do framework original, fornecendo estruturas, personas, workflows e padrões de código cuidadosamente desenvolvidos para maximizar a eficiência e qualidade em projetos de desenvolvimento assistido por IA.

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

## Workflows Estruturados

O Template Agent 2.0 oferece seis workflows completos e detalhados que cobrem todo o ciclo de vida do desenvolvimento de software:

### 1. Documentação de Projeto

Um processo abrangente para criar documentação de alta qualidade em todas as fases do projeto, desde a concepção até a operação e suporte. Inclui templates para diversos tipos de documentos técnicos e de usuário.

### 2. Implementação de Software

Workflow estruturado para guiar o processo de desenvolvimento, desde a exploração inicial até commits e pull requests, garantindo código de qualidade, testável e alinhado com os padrões do projeto.

### 3. Revisão de Código

Processo detalhado para realizar code reviews eficazes, promovendo qualidade, compartilhamento de conhecimento e melhoria contínua através de feedback construtivo e verificações sistemáticas.

### 4. Correção de Bugs

Metodologia completa para identificação, diagnóstico, correção e verificação de bugs, garantindo resolução eficaz de problemas e prevenção de recorrências.

### 5. Refinamento de Ideias

Processo estruturado para transformar ideias brutas em conceitos bem definidos, incluindo exploração inicial, contextualização, desafio, aprofundamento conceitual, validação e documentação.

### 6. Descoberta de Soluções

Metodologia para identificar necessidades dos usuários, mapear oportunidades de negócio, conceber e validar soluções, com foco em resultados mensuráveis e evolução contínua.

## Estrutura do Projeto

O diretório `.agent` é organizado da seguinte forma:

```
.agent/
├── 1-documentation/           # Documentação de projeto
├── 2-implementation/          # Processo de implementação de código
├── 3-code-review/             # Workflow de revisão de código
├── 4-fix-bugs/                # Processo de correção de bugs
├── 5-idea-refinement/         # Refinamento de ideias e brainstorming
└── 6-solution-discovery/      # Descoberta e implementação de soluções
```

Cada diretório principal contém subdiretórios numerados que representam as etapas do workflow correspondente, com arquivos `prompt.md` para prompts específicos e `sobre.md` para explicações detalhadas.

## Como Utilizar

### 1. Escolha o Workflow Adequado

Identifique qual workflow se aplica à sua necessidade atual:

- Para criar documentação de projeto: `1-documentation`
- Para implementar código: `2-implementation`
- Para revisar código: `3-code-review`
- Para corrigir bugs: `4-fix-bugs`
- Para refinar ideias: `5-idea-refinement`
- Para descobrir e validar soluções: `6-solution-discovery`

### 2. Siga as Etapas do Workflow

Cada workflow é divido em etapas sequenciais numeradas. Navegue pelas pastas correspondentes e siga o processo passo a passo.

### 3. Utilize os Prompts

Em cada etapa, você encontrará arquivos `prompt.md` contendo prompts específicos para usar com GitHub Copilot ou outras ferramentas de IA. Estes prompts foram cuidadosamente elaborados para obter os melhores resultados.

### 4. Personalize para seu Contexto

Adapte os prompts e as orientações para o contexto específico do seu projeto, equipe e tecnologias.

## Melhores Práticas

1. **Consistência**: Siga os workflows de forma consistente para criar um ritmo de trabalho previsível.

2. **Adaptação Contextual**: Personalize os prompts para incluir detalhes específicos do seu projeto.

3. **Revisão Humana**: Sempre revise criticamente as sugestões geradas pela IA.

4. **Melhoria Contínua**: Refine os prompts com base na experiência e nos resultados obtidos.

5. **Compartilhamento de Conhecimento**: Compartilhe prompts eficazes e lições aprendidas com a equipe.

## Contribuições

Este framework é um projeto vivo que se beneficia de contribuições coletivas. Para contribuir:

1. Adicione novos prompts eficazes aos workflows existentes
2. Sugira melhorias para os workflows atuais
3. Proponha novos workflows para cenários específicos
4. Compartilhe casos de uso bem-sucedidos

## Licença

Este projeto é licenciado sob MIT - veja o arquivo LICENSE para detalhes.
