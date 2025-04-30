# ux-ui-specs

# Prompts para UX/UI Specifications

## Prompt para Especificações Completas de UX/UI

```
Você é um designer UX/UI sênior com vasta experiência em documentação de design. Preciso da sua ajuda para criar especificações completas de UX/UI para [nome do produto/projeto].

Contexto do produto:
- Descrição: [breve descrição do produto]
- Público-alvo: [descrição dos usuários-alvo]
- Plataformas: [web, iOS, Android, desktop, etc.]
- Objetivos principais: [objetivos do produto]

Por favor, crie um documento de especificações de UX/UI abrangente que inclua:

1. Princípios de design que guiarão o produto
2. Arquitetura de informação (estrutura de navegação)
3. Fluxos de usuário para as principais tarefas
4. Design system completo (cores, tipografia, componentes, grid)
5. Especificações detalhadas para estados e comportamentos de interação
6. Considerações de responsividade
7. Diretrizes de acessibilidade
8. Especificações técnicas para implementação

Para cada seção, forneça detalhes específicos que possam ser usados como guia pelos desenvolvedores e outros designers.
```

## Prompt para Design System

```
Como designer de experiência, preciso criar um design system completo para [nome do produto]. Este design system será parte das especificações de UX/UI e servirá como referência para todo o desenvolvimento front-end.

Contexto:
- Marca: [informações da marca, valores, personalidade]
- Plataformas: [web, mobile, etc.]
- Público-alvo: [detalhes do público]
- Necessidades de acessibilidade: [requisitos específicos]

Por favor, desenvolva um design system abrangente que inclua:

1. Fundamentos:
   - Paleta de cores completa (primárias, secundárias, neutras, feedback) com códigos hexadecimais e usos recomendados
   - Sistema tipográfico (fontes, tamanhos, pesos, hierarquia, espaçamentos)
   - Iconografia (estilo, tamanhos, uso)
   - Grid system e layouts (número de colunas, gutters, margens)
   - Espaçamento (sistema de espaçamento, aplicações)

2. Componentes:
   - Botões (tipos, estados, tamanhos)
   - Campos de formulário (inputs, selects, checkboxes, radio buttons)
   - Cards e containers
   - Navegação (menus, tabs, breadcrumbs)
   - Modais e overlays
   - Tabelas e listas
   - Notificações e alertas
   - Loaders e indicadores de progresso

3. Padrões:
   - Padrões de interação consistentes
   - Estados (hover, active, focus, disabled)
   - Feedback visual
   - Transições e animações

4. Diretrizes de Implementação:
   - Nomenclatura de classes
   - Organização de arquivos
   - Princípios de composição
   - Extensibilidade

Para cada elemento, forneça especificações técnicas detalhadas e exemplos visuais descritos textualmente.
```

## Prompt para Fluxos de Usuário e Wireframes

```
Como UX designer, preciso documentar os fluxos de usuário e wireframes para as principais funcionalidades de [nome do produto/aplicação].

As principais funcionalidades são:
- [Funcionalidade 1]
- [Funcionalidade 2]
- [Funcionalidade 3]

Para cada funcionalidade, por favor crie:

1. Fluxo de Usuário:
   - Diagrama textual detalhado do fluxo completo
   - Pontos de entrada e saída
   - Decisões e ramificações
   - Estados de erro e recuperação
   - Feedback em cada etapa

2. Wireframes Descritivos:
   - Descrição detalhada de cada tela no fluxo
   - Layout e hierarquia dos elementos
   - Conteúdo e microcopy
   - Comportamento dos elementos interativos
   - Transições entre telas
   - Estados alternativos (carregamento, erro, vazio, etc.)

3. Anotações:
   - Justificativa das decisões de design
   - Referências a requisitos específicos
   - Considerações de acessibilidade
   - Pontos de atenção para implementação
   - Métricas de sucesso para o fluxo

Descreva cada wireframe com detalhes suficientes para que um designer visual ou desenvolvedor possa entender precisamente o layout, conteúdo e comportamento esperado.
```

## Prompt para Especificações de Interação e Microinterações

```
Como designer de interação, preciso documentar as especificações detalhadas de interação e microinterações para [nome do produto], que farão parte das especificações de UX/UI.

Contexto:
- Plataforma: [web, mobile, etc.]
- Identidade desejada: [moderna, profissional, divertida, etc.]
- Público: [descrição do público]

Para cada elemento interativo abaixo, defina especificações completas:

1. [Elemento 1] (ex: botão principal):
   - Estados (normal, hover, active, focus, disabled)
   - Timing e easing de transições
   - Feedback visual e/ou tátil
   - Comportamento em diferentes dispositivos
   - Considerações de acessibilidade

2. [Elemento 2] (ex: menu de navegação):
   - Comportamento de abertura e fechamento
   - Animações e transições
   - Feedback do item selecionado
   - Interações com submenus
   - Comportamento responsivo

3. [Elemento 3] (ex: formulário de login):
   - Validação em tempo real
   - Feedback de erros
   - Transições entre campos
   - Comportamento do submit
   - Feedback de sucesso/erro

4. Padrões globais de interação:
   - Tempo de resposta esperado
   - Princípios de feedback
   - Transições entre páginas/estados
   - Indicadores de carregamento
   - Tratamento de erros e recuperação

Para cada especificação, inclua detalhes técnicos precisos (durações em ms, curvas de easing, valores de opacidade, etc.) e o propósito da interação em termos de experiência do usuário.
```

## Prompt para Diretrizes de Acessibilidade

```
Como especialista em acessibilidade digital, preciso desenvolver diretrizes abrangentes de acessibilidade para [nome do produto] como parte das especificações de UX/UI.

Contexto:
- Tipo de produto: [web, mobile, etc.]
- Público-alvo: [incluir informações sobre usuários com necessidades especiais]
- Requisitos de conformidade: [WCAG 2.1 nível AA, Seção 508, etc.]

Por favor, crie diretrizes detalhadas que incluam:

1. Requisitos gerais de acessibilidade:
   - Nível de conformidade WCAG alvo
   - Priorização de critérios de sucesso
   - Abordagem para testes de acessibilidade

2. Diretrizes específicas por categoria:
   - Percepção:
     * Alternativas de texto para conteúdo não textual
     * Requisitos de contraste de cores (incluir rácios específicos)
     * Uso de cor e informação sensorial
     * Controle de áudio

   - Operabilidade:
     * Acesso completo por teclado (incluir padrões de navegação)
     * Tempo suficiente para interações
     * Prevenção de convulsões e reações físicas
     * Navegação e localização

   - Compreensibilidade:
     * Legibilidade do texto
     * Previsibilidade das interfaces
     * Assistência na entrada de dados
     * Prevenção e correção de erros

   - Robustez:
     * Compatibilidade com tecnologias assistivas
     * Requisitos de marcação

3. Recomendações por componente:
   - Formulários e entradas de dados
   - Navegação
   - Imagens e mídia
   - Tabelas e dados estruturados
   - Notificações e feedback
   - Conteúdo dinâmico

Para cada diretriz, inclua exemplos específicos de implementação, critérios de sucesso mensuráveis e métodos de teste recomendados.
```
