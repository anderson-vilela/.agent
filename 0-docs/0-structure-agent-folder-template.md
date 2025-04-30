# Estrutura de Pastas para Documentação de Projeto

Aqui está uma proposta de estrutura de pastas para o seu diretório `.agent`, organizada de acordo com os workflows e documentos que você mencionou:

```
.agent/
│
├── 1-documentation/
│   ├── 01-concepcao-planejamento/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── vision-document/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── project-charter/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── estudo-viabilidade/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── brd/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── mrd/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   ├── 02-requisitos/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── prd/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── srs/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── ux-ui-specs/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── fsd/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── roadmap/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   ├── 03-governanca-processos/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── process-guidelines/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── governance-framework/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── raci-matrix/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── communication-plan/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── risk-management/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   ├── 04-arquitetura-design/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── hld/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── adrs/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── sad/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── lld/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── specific-arch-docs/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   ├── 05-guidelines-sistema/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── ui-style-guide/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── security-guidelines/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── technical-standards/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── accessibility-guidelines/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── compliance-framework/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   ├── 06-documentacao-usuario/
│   │   ├── prompt.md
│   │   ├── sobre.md
│   │   ├── user-manual/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── quick-start-guide/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── installation-guide/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   ├── training-materials/
│   │   │   ├── prompt.md
│   │   │   └── sobre.md
│   │   └── configuration-guide/
│   │       ├── prompt.md
│   │       └── sobre.md
│   │
│   └── 07-operacao-suporte/
│       ├── prompt.md
│       ├── sobre.md
│       ├── sops/
│       │   ├── prompt.md
│       │   └── sobre.md
│       ├── runbooks/
│       │   ├── prompt.md
│       │   └── sobre.md
│       ├── drp/
│       │   ├── prompt.md
│       │   └── sobre.md
│       ├── deployment-guide/
│       │   ├── prompt.md
│       │   └── sobre.md
│       └── knowledge-base/
│           ├── prompt.md
│           └── sobre.md
│
├── 2-implementation/
│   ├── 01-exploracao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 02-contextualizacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 03-tarefas-plano-acao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 04-workflow-rules/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 05-testing/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 06-debugging/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 07-refactoring/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   └── 08-commit-pr/
│       ├── prompt.md
│       └── sobre.md
│
├── 3-code-review/
│   ├── 01-preparacao-revisao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 02-submissao-revisao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 03-revisao-tecnica/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 04-verificacao-qualidade/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 05-feedback-discussao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 06-atualizacoes-iteracoes/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 07-aprovacao-finalizacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   └── 08-aprendizado-melhoria/
│       ├── prompt.md
│       └── sobre.md
│
├── 4-fix-bugs/
│   ├── 01-identificacao-triagem/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 02-reproducao-analise/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 03-diagnostico-causa-raiz/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 04-planejamento-correcao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 05-implementacao-correcao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 06-verificacao-validacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 07-3-code-review-aprovacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 08-implantacao-verificacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   └── 09-fechamento-documentacao/
│       ├── prompt.md
│       └── sobre.md
│
├── 5-idea-refinement/
│   ├── 01-exploracao-inicial/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 02-estruturacao-contextualizacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 03-desafio-refinamento/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 04-aprofundamento-conceitual/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 05-validacao-simulacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 06-detalhamento-especificacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   ├── 07-sintese-documentacao/
│   │   ├── prompt.md
│   │   └── sobre.md
│   │
│   └── 08-planejamento-evolucao/
│       ├── prompt.md
│       └── sobre.md
│
└── 6-solution-discovery/
    ├── 01-imersao-contextualizacao/
    │   ├── prompt.md
    │   └── sobre.md
    │   ├── mapeamento-stakeholders/
    │   │   ├── prompt.md
    │   │   └── sobre.md
    │   ├── analise-documentacao/
    │   │   ├── prompt.md
    │   │   └── sobre.md
    │   └── contextualizacao-mercado/
    │       ├── prompt.md
    │       └── sobre.md
    │
    ├── 02-descoberta-dores-necessidades/
    │   ├── prompt.md
    │   └── sobre.md
    │   ├── planejamento-pesquisa/
    │   │   ├── prompt.md
    │   │   └── sobre.md
    │   ├── pesquisa-qualitativa/
    │   │   ├── prompt.md
    │   │   └── sobre.md
    │   ├── pesquisa-quantitativa/
    │   │   ├── prompt.md
    │   │   └── sobre.md
    │   └── mapeamento-experiencia/
    │       ├── prompt.md
    │       └── sobre.md
    │
    ├── 03-diagnostico-priorizacao/
    │   ├── prompt.md
    │   └── sobre.md
    │
    ├── 04-mapeamento-oportunidades/
    │   ├── prompt.md
    │   └── sobre.md
    │
    ├── 05-concepcao-solucoes/
    │   ├── prompt.md
    │   └── sobre.md
    │
    ├── 06-validacao-conceito-metricas/
    │   ├── prompt.md
    │   └── sobre.md
    │
    ├── 07-planejamento-go-to-market/
    │   ├── prompt.md
    │   └── sobre.md
    │
    └── 08-evolucao-escalonamento/
        ├── prompt.md
        └── sobre.md
```

Nesta estrutura:

- Cada categoria principal tem sua própria pasta: `1-documentation`, `2-implementation`, `3-code-review`, `4-fix-bugs`, `5-idea-refinement` e `6-solution-discovery`.
- Dentro de cada categoria, há subpastas numeradas para cada etapa do workflow.
- Cada subpasta contém:
  - `prompt.md`: Um arquivo com prompts para gerar documentos relacionados àquela etapa específica.
  - `sobre.md`: Um arquivo explicativo sobre o tópico, incluindo sua importância, melhores práticas, e instruções gerais.
- Para `1-documentation` e `6-solution-discovery`, devido à sua natureza mais detalhada, algumas etapas têm subpastas adicionais para documentos específicos.
