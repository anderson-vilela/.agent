# Prompt para Análise de Código Existente

## Contexto

Estou na fase de análise de código existente durante a exploração para implementação de uma nova funcionalidade. Preciso entender profundamente o código atual relacionado à área que vou modificar ou estender.

## Objetivo

Utilizar o GitHub Copilot para me auxiliar na compreensão, análise e mapeamento da base de código atual, identificando padrões, dependências e áreas relevantes para a implementação.

## Prompts Específicos

### Compreensão do Fluxo de Código

```
Ajude-me a entender o fluxo e a lógica do seguinte código relacionado a [COMPONENTE/FUNCIONALIDADE]:

[COLAR TRECHOS DE CÓDIGO RELEVANTES]

Por favor:
1. Explique o propósito geral deste código
2. Descreva o fluxo de execução e principais caminhos lógicos
3. Identifique as estruturas de dados principais e como são manipuladas
4. Explique as operações críticas e seus efeitos
5. Destaque partes que podem precisar de atenção especial ao implementar [NOVA FUNCIONALIDADE]
```

### Identificação de Padrões e Convenções

```
Analise o código abaixo para identificar padrões de design e convenções utilizadas no projeto:

[COLAR TRECHOS DE CÓDIGO REPRESENTATIVOS]

Por favor:
1. Identifique design patterns (ex: Factory, Singleton, Observer) utilizados
2. Descreva as convenções de nomenclatura e organização do código
3. Identifique padrões de tratamento de erros e exceções
4. Explique abordagens comuns para situações recorrentes (ex: validação, logging)
5. Destaque práticas específicas deste projeto que devo seguir na minha implementação
```

### Mapeamento de Dependências

```
Ajude-me a mapear as dependências e relacionamentos no seguinte código:

[COLAR CÓDIGO COM POTENCIAIS DEPENDÊNCIAS]

Por favor:
1. Identifique as principais classes/módulos/componentes e suas relações
2. Mapeie as dependências externas utilizadas (bibliotecas, APIs)
3. Descreva como dados fluem entre os componentes identificados
4. Avalie o nível de acoplamento entre os diferentes componentes
5. Identifique pontos de extensão existentes que posso utilizar
6. Destaque possíveis desafios ao introduzir novas dependências
```

### Análise de Interfaces e Contratos

```
Analise as seguintes interfaces/contratos no código atual:

[COLAR INTERFACES/APIS/CONTRATOS RELEVANTES]

Por favor:
1. Explique o propósito e responsabilidade de cada interface
2. Descreva os contratos implícitos e explícitos (pré/pós-condições)
3. Identifique como essas interfaces são implementadas e utilizadas no sistema
4. Avalie a flexibilidade para extensão dessas interfaces
5. Sugira como posso estender ou adaptar essas interfaces para a nova funcionalidade
```

### Análise de Testes Existentes

```
Ajude-me a entender os seguintes testes para [COMPONENTE/FUNCIONALIDADE]:

[COLAR CÓDIGO DE TESTES RELEVANTES]

Por favor:
1. Explique quais comportamentos/aspectos estão sendo testados
2. Identifique cenários importantes cobertos pelos testes
3. Aponte cenários que parecem faltar nos testes atuais
4. Descreva as técnicas e padrões de teste utilizados
5. Sugira como devo abordar os testes para as modificações que farei
```

### Identificação de Potenciais Problemas

```
Analise o seguinte código em busca de potenciais problemas ou áreas de melhoria:

[COLAR CÓDIGO PARA ANÁLISE]

Por favor:
1. Identifique possíveis bugs, problemas de performance ou segurança
2. Aponte code smells ou anti-patterns que podem complicar manutenção futura
3. Destaque áreas com alta complexidade ou difícil compreensão
4. Identifique potencial código duplicado ou oportunidades de refatoração
5. Sugira melhorias que eu poderia implementar junto com a nova funcionalidade
```

### Análise de Impacto para Implementação

```
Considerando a implementação de [NOVA FUNCIONALIDADE], analise o seguinte código existente para determinar o impacto:

[COLAR CÓDIGO RELEVANTE]

Por favor:
1. Identifique quais partes do código precisarão ser modificadas
2. Avalie o escopo e a complexidade das mudanças necessárias
3. Destaque potenciais efeitos colaterais em outras partes do sistema
4. Identifique riscos e desafios técnicos para a implementação
5. Sugira uma abordagem para implementar as mudanças minimizando riscos
```

## Dicas para Uso Efetivo

1. **Forneça contexto suficiente**: Inclua código suficiente para permitir uma análise completa, incluindo classes/funções relacionadas.

2. **Seja específico sobre o foco**: Indique claramente qual aspecto do código você quer entender ou analisar.

3. **Itere e aprofunde**: Use as respostas iniciais para formular perguntas mais específicas sobre áreas que precisam de esclarecimento adicional.

4. **Compare implementações**: Quando relevante, peça análises comparativas entre diferentes partes do código que implementam funcionalidades similares.

5. **Solicite visualizações**: Peça para o Copilot descrever o código em termos de diagramas conceituais ou fluxos, mesmo que ele não possa gerar imagens.

6. **Valide entendimento**: Use as explicações do Copilot como hipóteses a serem validadas através de testes, execução do código ou consulta a outros desenvolvedores.
