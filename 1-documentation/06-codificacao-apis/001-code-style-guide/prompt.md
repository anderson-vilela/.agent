# Prompts para Criação de Guia de Estilo de Código

Este documento contém prompts específicos para gerar um Guia de Estilo de Código abrangente, ajudando a estabelecer e documentar convenções de codificação para o projeto.

## Prompt para Guia de Estilo de Código Completo

```prompt
Como especialista em padrões de codificação, crie um Guia de Estilo de Código completo para nosso projeto de [linguagem/tecnologia principal]. O guia deve abranger:

1. Convenções de nomenclatura para:
   - Variáveis (locais, globais, constantes)
   - Funções e métodos
   - Classes e interfaces
   - Arquivos e diretórios
   - Namespaces ou packages

2. Formatação de código:
   - Indentação (espaços vs. tabs, quantidade)
   - Comprimento máximo de linha
   - Uso de quebras de linha
   - Posicionamento de chaves
   - Espaçamento (entre operadores, parâmetros, etc.)
   - Formatação de comentários

3. Práticas de organização:
   - Estrutura de arquivos
   - Organização de imports/includes
   - Ordenação de métodos em classes
   - Modularização do código

4. Práticas recomendadas específicas para [linguagem/framework]:
   - Padrões idiomáticos da linguagem
   - Uso de recursos da linguagem (por exemplo, recursos modernos vs. legados)
   - Anti-padrões a evitar

Inclua exemplos concretos de código "correto" e "incorreto" para cada regra importante.
Adicione explicações das razões por trás das convenções escolhidas quando relevante.
```

## Prompt para Configuração de Linters e Formatadores

```prompt
Crie um guia técnico para configurar ferramentas de linting e formatação automática para nossa base de código em [linguagem/tecnologia]. Inclua:

1. Ferramentas recomendadas para esta linguagem/stack
2. Arquivos de configuração base (.eslintrc, .prettierrc, etc.)
3. Regras específicas alinhadas com nosso guia de estilo
4. Como configurar/integrar com IDEs populares
5. Como configurar hooks de pré-commit para verificação automática
6. Processo para resolver conflitos ou exceções às regras

Use um tom técnico e direto, com exemplos concretos de configuração e comandos.
```

## Prompt para Exemplos de Código Seguindo o Estilo

```prompt
Com base nas convenções do nosso guia de estilo para [linguagem/tecnologia], crie exemplos completos de código que demonstrem a aplicação correta de todas as regras principais. Especificamente:

1. Um exemplo de arquivo de classe/módulo completo
2. Um exemplo de interface ou contrato
3. Um exemplo de função utilitária
4. Um exemplo de teste unitário

Cada exemplo deve seguir rigorosamente nossas convenções e incluir comentários explicativos onde relevante.
Destaque aspectos específicos do estilo que podem ser facilmente esquecidos ou mal interpretados por novos desenvolvedores.
```

## Prompt para Checklist de Conformidade com o Estilo

```prompt
Crie uma checklist abrangente para verificação de conformidade com nosso guia de estilo de código. A checklist deve:

1. Ser organizada por categorias (nomenclatura, formatação, organização, etc.)
2. Incluir todos os pontos críticos do guia de estilo
3. Ser utilizável em revisões de código
4. Incluir verificações específicas para [linguagem/tecnologia]
5. Distinguir entre problemas críticos e recomendações

Formate a checklist de maneira que possa ser facilmente incorporada em templates de pull request ou ferramentas de revisão.
```

## Prompt para FAQ de Estilo de Código

```prompt
Desenvolva uma seção de Perguntas Frequentes (FAQ) para complementar nosso guia de estilo de código em [linguagem/tecnologia]. A FAQ deve:

1. Abordar cenários comuns onde a aplicação do guia pode ser ambígua
2. Explicar o raciocínio por trás de decisões controversas no guia
3. Fornecer orientação sobre como lidar com código legado que não segue o guia
4. Responder a questões sobre exceções às regras
5. Incluir perguntas sobre como resolver conflitos entre diferentes regras

As respostas devem ser concisas, diretas e incluir exemplos quando relevante.
```
