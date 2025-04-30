# roadmap

# Prompts para Roadmap Document

## Prompt para Roadmap Estratégico Completo

```
Você é um Product Manager experiente com vasta experiência em planejamento estratégico de produtos. Preciso da sua ajuda para criar um Roadmap Document abrangente para [nome do produto/projeto].

Contexto do produto:
- Descrição: [breve descrição do produto]
- Estágio atual: [novo, em desenvolvimento, em produção, etc.]
- Principais funcionalidades existentes: [funcionalidades atuais, se aplicável]
- Horizonte de planejamento: [período a ser coberto, ex: 12 meses]

Por favor, crie um roadmap estratégico detalhado que inclua:

1. Visão geral e objetivos estratégicos
2. Resumo executivo das entregas planejadas
3. Linha do tempo detalhada com marcos principais
4. Entregas planejadas por trimestre/mês, incluindo:
   - Novas funcionalidades
   - Melhorias em funcionalidades existentes
   - Correções importantes
   - Trabalho técnico necessário
5. Priorização e dependências entre itens
6. Considerações sobre go-to-market para cada release
7. Fatores de risco e planos de contingência
8. Métricas de sucesso para avaliar o progresso

Para cada item no roadmap, inclua:
- Descrição clara
- Valor esperado para usuários e para o negócio
- Estimativa de esforço relativo
- Dependências críticas
- Critérios para considerar o item concluído
```

## Prompt para Priorização do Roadmap

```
Como Product Manager, preciso priorizar as funcionalidades para o roadmap dos próximos [período] para [nome do produto].

Contexto:
- Funcionalidades candidatas: [lista de funcionalidades consideradas]
- Recursos disponíveis: [informações sobre capacidade da equipe]
- Objetivos estratégicos: [objetivos de negócio prioritários]

Por favor, ajude-me a priorizar estas funcionalidades usando múltiplas abordagens:

1. Análise RICE (Reach, Impact, Confidence, Effort):
   - Calcule a pontuação RICE para cada funcionalidade
   - Classifique as funcionalidades com base na pontuação
   - Explique o raciocínio para os valores atribuídos

2. Matriz de Valor vs. Esforço:
   - Posicione cada funcionalidade na matriz
   - Identifique os "quick wins" e os itens de alto valor
   - Recomende uma estratégia para itens de alto esforço

3. Modelo Kano:
   - Classifique as funcionalidades como básicas, de performance ou de entusiasmo
   - Identifique potenciais "delighters" e recursos obrigatórios
   - Sugira um equilíbrio entre as categorias

4. Análise de Dependências:
   - Identifique dependências críticas entre as funcionalidades
   - Desenvolva uma sequência lógica de implementação
   - Aponte bloqueadores potenciais

Com base nestas análises, recomende:
- Top 3-5 funcionalidades para implementação imediata
- Sequência sugerida para os próximos itens
- Funcionalidades que podem ser adiadas ou descartadas
- Justificativa clara para cada recomendação
```

## Prompt para Roadmap Orientado a Objetivos

```
Como estrategista de produto, preciso desenvolver um roadmap orientado a objetivos para [nome do produto] para os próximos [período].

Contexto:
- Objetivos-chave de negócio: [listar objetivos]
- Público-alvo: [informações sobre usuários]
- Métricas de sucesso: [KPIs principais]
- Limitações conhecidas: [restrições de recursos, tempo, etc.]

Por favor, ajude-me a criar um roadmap baseado em OKRs (Objectives and Key Results) que:

1. Para cada objetivo estratégico, defina:
   - Objetivo claro e inspirador
   - 3-5 key results mensuráveis
   - Horizonte de tempo para alcançar o objetivo
   - Alinhamento com a estratégia geral

2. Para cada objetivo, mapeie:
   - Iniciativas/funcionalidades que contribuirão para os key results
   - Sequência lógica de implementação
   - Marcos de progresso intermediários
   - Como o sucesso será medido

3. Organize o roadmap em:
   - Horizonte de curto prazo (próximos 3 meses): detalhado e concreto
   - Horizonte de médio prazo (3-6 meses): menos detalhado, com flexibilidade
   - Horizonte de longo prazo (6+ meses): direção estratégica geral

4. Para cada horizonte, especifique:
   - Temas principais de desenvolvimento
   - Resultados esperados para usuários e negócio
   - Critérios para reavaliar e ajustar o plano

O roadmap deve claramente comunicar "por que" estamos construindo certas funcionalidades, não apenas "o que" e "quando", mantendo o foco nos resultados ao invés de somente nas entregas.
```

## Prompt para Roadmap Técnico

```
Como Tech Lead/Arquiteto, preciso desenvolver um roadmap técnico para [nome do sistema/produto] que complementará o roadmap de produto.

Contexto técnico:
- Estado atual da arquitetura: [descrição da arquitetura atual]
- Dívidas técnicas conhecidas: [principais dívidas técnicas]
- Escalabilidade atual e projetada: [métricas atuais e projeções]
- Novas funcionalidades planejadas: [requisitos futuros conhecidos]

Por favor, ajude-me a criar um roadmap técnico detalhado que inclua:

1. Melhorias Arquiteturais:
   - Mudanças fundamentais na arquitetura
   - Justificativa e benefícios esperados
   - Riscos e estratégias de mitigação
   - Timeline para implementação gradual

2. Dívida Técnica:
   - Priorização das dívidas técnicas a serem abordadas
   - Impacto de cada item no desempenho, manutenibilidade e segurança
   - Estratégia de alocação de recursos para reduzir dívida técnica
   - Métricas para acompanhar a redução da dívida técnica

3. Infraestrutura e DevOps:
   - Melhorias no pipeline de CI/CD
   - Atualizações de infraestrutura
   - Melhorias no monitoramento e observabilidade
   - Iniciativas de segurança e conformidade

4. Tecnologias e Frameworks:
   - Atualizações de versões de frameworks e bibliotecas
   - Novas tecnologias a serem adotadas
   - Tecnologias a serem descontinuadas
   - Planos de migração e estratégias de transição

5. Necessidades de Escalabilidade:
   - Pontos de contenção previstos
   - Estratégias para escalabilidade horizontal/vertical
   - Otimizações de performance planejadas
   - Mudanças em bancos de dados e armazenamento

O roadmap deve alinhar-se com as entregas de produto enquanto garante a saúde técnica do sistema a longo prazo, com estimativas claras de esforço e impacto no desenvolvimento de novas funcionalidades.
```

## Prompt para Comunicação do Roadmap a Stakeholders

```
Como gerente de produto, preciso preparar uma comunicação eficaz do roadmap de [nome do produto] para diferentes grupos de stakeholders.

Os stakeholders incluem:
- Executivos e liderança de negócios
- Equipes de desenvolvimento
- Equipes de vendas e marketing
- Clientes e usuários finais
- [outros stakeholders relevantes]

Para cada grupo de stakeholders, por favor ajude-me a desenvolver:

1. Mensagens-chave adaptadas:
   - Principais pontos a enfatizar para cada grupo
   - Nível de detalhe apropriado
   - Foco específico (estratégico vs. tático)
   - Linguagem e terminologia adequadas

2. Formatos de apresentação recomendados:
   - Visualizações eficazes do roadmap para cada audiência
   - Estrutura da apresentação
   - Materiais de apoio necessários
   - Frequência recomendada de atualização

3. Estratégias para gerenciar expectativas:
   - Como comunicar incertezas e flexibilidade
   - Definição clara de compromissos vs. intenções
   - Abordagem para itens com alta probabilidade de mudança
   - Como lidar com perguntas sobre itens fora do roadmap

4. Plano de engajamento contínuo:
   - Mecanismos para feedback
   - Cadência de revisões e atualizações
   - Como incorporar input dos stakeholders
   - Indicadores de sucesso para a comunicação

Para cada estratégia, inclua exemplos específicos, frases-chave a utilizar e técnicas para transmitir confiança ao mesmo tempo em que gerencia expectativas sobre entregas futuras.
```
