# Prompts para Análise de Impacto

## Mapeamento de Áreas Afetadas

```
Como Arquiteto de Sistemas especializado em análise de impacto, preciso da sua ajuda para mapear todas as áreas e componentes que serão afetados pela seguinte implementação:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Por favor, forneça:

1. Uma lista hierárquica e estruturada de todos os componentes, módulos, serviços ou subsistemas que serão afetados diretamente
2. Uma lista de componentes que poderão ser afetados indiretamente
3. Para cada componente afetado, descreva:
   - A natureza do impacto (mudança de API, alteração de comportamento, etc.)
   - A extensão do impacto (menor, moderado, significativo)
   - Se o impacto é em runtime, buildtime ou ambos
4. Identifique interfaces e contratos que precisarão ser modificados ou que serão impactados
5. Crie uma representação visual (descrita em texto) que mostre as relações entre os componentes e como o impacto se propaga

Organize sua resposta em formato de tabela ou matriz quando aplicável para facilitar a visualização do impacto.
```

## Análise de Riscos de Integração

```
Como Especialista em Gestão de Riscos Técnicos, preciso da sua ajuda para identificar e analisar riscos de integração para a seguinte implementação:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Com base nas áreas de impacto identificadas:

[RESUMO DAS ÁREAS AFETADAS]

Por favor, desenvolva:

1. Uma matriz de riscos completa que identifique:
   - Descrição detalhada de cada risco de integração
   - Probabilidade de ocorrência (Alta/Média/Baixa)
   - Impacto potencial se ocorrer (Alto/Médio/Baixo)
   - Pontuação de risco global (combinação de probabilidade e impacto)
2. Para cada risco identificado, forneça:
   - Estratégias de mitigação específicas
   - Indicadores ou triggers que sinalizariam que o risco está se materializando
   - Planos de contingência
3. Identifique os 3-5 riscos mais críticos que requerem atenção prioritária

Estruture sua resposta em forma de relatório de análise de riscos, começando com um sumário executivo dos principais riscos.
```

## Análise de Compatibilidade

```
Como Especialista em Versionamento e Compatibilidade de API, preciso da sua ajuda para analisar as implicações de compatibilidade para a seguinte implementação:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Por favor, forneça uma análise detalhada que considere:

1. Impactos potenciais na compatibilidade com versões anteriores
2. Mudanças que podem quebrar APIs ou integrações existentes
3. Estratégias específicas para:
   - Manter compatibilidade para trás quando possível
   - Implementar compatibilidade transitória para mudanças inevitáveis
   - Planejar a depreciação e fim de vida de componentes que serão substituídos
4. Recomendações para versionamento semântico adequado
5. Necessidades específicas de documentação para comunicar mudanças

Considere tanto consumidores internos quanto externos das interfaces afetadas, e ofereça uma estratégia de migração para cada caso onde a compatibilidade para trás não pode ser mantida.
```

## Análise de Impactos não-funcionais

```
Como Arquiteto de Performance e Qualidade de Software, preciso da sua ajuda para analisar como a seguinte implementação impactará os atributos não-funcionais do sistema:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Por favor, forneça uma análise completa dos seguintes aspectos:

1. Performance:
   - Impacto esperado em tempo de resposta, throughput e utilização de recursos
   - Identificação de potenciais gargalos introduzidos
   - Estratégias para monitorar e mitigar problemas de performance

2. Segurança:
   - Novas superfícies de ataque ou vulnerabilidades potenciais
   - Considerações de autenticação, autorização e auditoria
   - Recomendações para manter ou melhorar a postura de segurança

3. Escalabilidade:
   - Como a implementação afeta a capacidade de escalar horizontal e verticalmente
   - Potenciais limitações de escalabilidade introduzidas
   - Estratégias para garantir escalabilidade adequada

4. Outros atributos de qualidade:
   - Impacto na manutenibilidade, confiabilidade, disponibilidade
   - Efeitos na observabilidade e capacidade de diagnóstico
   - Considerações de acessibilidade ou internacionalização, se relevantes

Para cada aspecto, identifique o impacto específico, métricas para monitorá-lo e recomendações para manter ou melhorar o atributo de qualidade.
```

## Análise de Dependências Externas

```
Como Especialista em Integração de Sistemas, preciso da sua ajuda para analisar as dependências externas relevantes para a seguinte implementação:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Por favor, forneça uma análise que inclua:

1. Um inventário completo de todas as dependências externas que:
   - Serão utilizadas diretamente na implementação
   - Serão afetadas pela implementação
   - Poderiam criar restrições ou riscos para a implementação

2. Para cada dependência identificada:
   - O propósito e importância para a implementação
   - Nível de acoplamento e criticidade
   - Riscos associados (disponibilidade, performance, licenciamento, etc.)
   - Alternativas possíveis em caso de problemas

3. Recomendações para:
   - Estratégias de versionamento para dependências
   - Abordagens para isolamento e testabilidade
   - Planos de contingência para falhas de dependências críticas

Organize as dependências por categorias (bibliotecas, serviços externos, sistemas internos, etc.) e priorize-as por criticidade.
```

## Plano de Testes de Impacto

```
Como Especialista em Testes de Regressão e Qualidade, preciso da sua ajuda para desenvolver um plano de testes que valide adequadamente o impacto da seguinte implementação:

[DESCREVA BREVEMENTE A FUNCIONALIDADE/COMPONENTE A SER IMPLEMENTADO]

Com base nas áreas de impacto identificadas:

[RESUMO DAS ÁREAS AFETADAS]

Por favor, crie um plano de testes abrangente que:

1. Identifique as áreas e cenários prioritários para teste de regressão
2. Descreva testes específicos para validar que:
   - A funcionalidade existente não foi comprometida
   - A nova funcionalidade se integra corretamente ao sistema
   - Requisitos não-funcionais são atendidos após a implementação
3. Recomende tipos de testes específicos (unitários, integração, end-to-end, performance)
4. Sugira métricas e critérios para determinar se os testes são suficientes
5. Inclua estratégias para automação e incorporação destes testes no pipeline de CI/CD

O plano de testes deve ser prático e focado nas áreas de maior risco, seguindo uma abordagem baseada em risco para priorização.
```
