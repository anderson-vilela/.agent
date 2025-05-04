# Prompt para Revisão da Documentação Técnica

## Contexto

Estou iniciando a fase de exploração para implementação de uma nova funcionalidade e preciso revisar a documentação técnica disponível para garantir um entendimento completo dos requisitos e do contexto arquitetural.

## Objetivo

Utilizar o GitHub Copilot para auxiliar na análise e compreensão da documentação técnica, identificando componentes relevantes, possíveis desafios e áreas que precisam de investigação adicional.

## Prompts Específicos

### Análise de Requisitos

```
Ajude-me a analisar os seguintes requisitos para implementação de [NOME DA FUNCIONALIDADE]:

Requisitos Funcionais:
[COLAR REQUISITOS FUNCIONAIS]

Requisitos Não-Funcionais:
[COLAR REQUISITOS NÃO-FUNCIONAIS]

Por favor:
1. Identifique os componentes principais que precisarei implementar/modificar
2. Destaque pontos que parecem ambíguos ou incompletos nos requisitos
3. Sugira requisitos adicionais que possam estar implícitos mas não documentados
4. Identifique potenciais desafios técnicos na implementação destes requisitos
5. Recomende perguntas que devo fazer para clarificar aspectos críticos
```

### Compreensão da Arquitetura

```
Preciso entender como a nova funcionalidade [NOME DA FUNCIONALIDADE] se encaixa na arquitetura atual do sistema.

Aqui está a descrição da arquitetura existente:
[DESCRIÇÃO DA ARQUITETURA / DIAGRAMA]

Aqui estão os componentes principais do sistema:
[LISTAR COMPONENTES PRINCIPAIS]

Por favor:
1. Explique como a nova funcionalidade se integrará com a arquitetura existente
2. Identifique quais componentes precisarão ser modificados
3. Aponte possíveis pontos de impacto em outros sistemas
4. Sugira abordagens para minimizar alterações na arquitetura existente
5. Identifique riscos arquiteturais que devem ser considerados
```

### Análise de ADRs (Architectural Decision Records)

```
Estou revisando as seguintes decisões arquiteturais (ADRs) relacionadas ao componente que vou implementar:

[COLAR ADRs RELEVANTES]

Por favor:
1. Resuma os principais pontos de decisão documentados
2. Explique as justificativas por trás dessas decisões
3. Identifique restrições que devo observar na minha implementação
4. Aponte padrões de design mencionados que devo seguir
5. Sugira como posso manter consistência com essas decisões na nova implementação
```

### Mapeamento de Interfaces e Integrações

```
Preciso entender as interfaces e integrações relacionadas à funcionalidade [NOME DA FUNCIONALIDADE].

Aqui estão as interfaces existentes:
[LISTAR INTERFACES RELEVANTES / CONTRATOS]

Integrações com sistemas externos:
[LISTAR INTEGRAÇÕES RELEVANTES]

Por favor:
1. Explique como essas interfaces funcionam e quais são seus contratos
2. Identifique quais interfaces precisarão ser modificadas ou criadas
3. Analise possíveis impactos nas integrações existentes
4. Aponte desafios potenciais de compatibilidade
5. Sugira uma estratégia para implementar mudanças nas interfaces minimizando impactos
```

### Análise de Casos de Uso/User Stories

```
Preciso compreender profundamente os seguintes casos de uso/user stories para a funcionalidade [NOME DA FUNCIONALIDADE]:

[COLAR CASOS DE USO / USER STORIES]

Por favor:
1. Descreva o fluxo principal de cada caso de uso em termos técnicos
2. Identifique fluxos alternativos e exceções importantes
3. Mapeie quais componentes do sistema serão envolvidos em cada fluxo
4. Destaque regras de negócio críticas embutidas nesses casos de uso
5. Sugira cenários de teste que deveriam ser considerados para validação
```

### Consolidação de Dúvidas Técnicas

```
Após revisar a documentação para [NOME DA FUNCIONALIDADE], identifiquei as seguintes informações:

Requisitos: [RESUMO DOS REQUISITOS]
Arquitetura: [RESUMO DA ARQUITETURA]
Interfaces: [RESUMO DAS INTERFACES]
Decisões prévias: [RESUMO DOS ADRs]

Por favor:
1. Identifique lacunas ou inconsistências na documentação
2. Formule perguntas específicas que eu deveria fazer para stakeholders técnicos
3. Sugira áreas onde documentação adicional pode ser necessária
4. Recomende próximos passos para completar minha compreensão técnica
5. Indique quais especialistas (perfis) eu deveria consultar para esclarecer pontos específicos
```

## Dicas para Uso Efetivo

1. **Selecione documentos relevantes**: Forneça apenas documentação diretamente relacionada à funcionalidade que está sendo implementada.

2. **Seja específico**: Quanto mais detalhes você fornecer sobre a funcionalidade e o contexto, mais relevantes serão as análises do Copilot.

3. **Divida e conquiste**: Para sistemas complexos, analise um aspecto da documentação por vez (requisitos, arquitetura, interfaces, etc.).

4. **Tome notas**: Documente as insights e perguntas geradas durante a revisão para referência futura.

5. **Revise criticamente**: Avalie as análises e sugestões do Copilot com base em seu conhecimento do sistema e contexto de negócio.

6. **Itere conforme necessário**: Use as respostas iniciais para gerar novos prompts mais específicos e aprofundados.
