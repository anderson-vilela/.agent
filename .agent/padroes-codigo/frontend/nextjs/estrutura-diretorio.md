# Padrão de Estrutura de Diretórios para Next.js com App Router

## Descrição

Este documento define o padrão recomendado para organização de diretórios em projetos Next.js modernos utilizando App Router. Uma estrutura bem definida é crucial para a manutenibilidade, escalabilidade e produtividade da equipe de desenvolvimento.

## Estrutura Base Recomendada

```
project-root/
├── .agent/                   # Diretório de configuração do agente (caso aplicável)
├── .github/                  # Configurações de GitHub (workflows, templates, etc.)
├── .husky/                   # Hooks do Git via Husky
├── .vscode/                  # Configurações do VS Code
├── app/                      # Diretório principal do App Router
│   ├── (auth)/               # Grupo de rotas relacionadas à autenticação
│   │   ├── login/            # Rota de login
│   │   │   ├── _components/  # Componentes específicos desta rota
│   │   │   └── page.tsx      # Página de login
│   │   └── register/         # Rota de registro
│   │       └── page.tsx      # Página de registro
│   ├── (dashboard)/          # Grupo de rotas do dashboard (autenticadas)
│   │   ├── layout.tsx        # Layout específico para o dashboard
│   │   ├── _components/      # Componentes compartilhados apenas no dashboard
│   │   └── page.tsx          # Página inicial do dashboard
│   ├── api/                  # Route Handlers (APIs)
│   │   └── [endpoint]/
│   │       └── route.ts      # Implementação da API
│   ├── _components/          # Componentes globais compartilhados
│   ├── _lib/                 # Código utilitário global (helpers, utils, etc.)
│   ├── _hooks/               # Hooks personalizados globais
│   ├── _stores/              # Estados globais (se aplicável)
│   ├── _styles/              # Estilos globais
│   ├── error.tsx             # Componente global de tratamento de erros
│   ├── favicon.ico           # Favicon do site
│   ├── globals.css           # Estilos CSS globais (incluindo Tailwind)
│   ├── layout.tsx            # Layout raiz (RootLayout)
│   ├── loading.tsx           # Componente de carregamento global
│   ├── not-found.tsx         # Página 404 customizada
│   └── page.tsx              # Página inicial (homepage)
├── public/                   # Arquivos estáticos (imagens, fontes, etc.)
├── components/               # Componentes reutilizáveis em toda a aplicação
│   ├── ui/                   # Componentes de UI reutilizáveis (shadcn/ui)
│   └── [componente]/         # Componentes específicos organizados por domínio
├── lib/                      # Código utilitário da aplicação
│   ├── actions/              # Server Actions centralizadas
│   ├── api/                  # Funções de API/fetch
│   ├── schemas/              # Schemas Zod
│   ├── utils/                # Funções utilitárias
│   └── validations/          # Funções de validação
├── types/                    # Tipagens TypeScript globais
├── .env                      # Variáveis de ambiente (local)
├── .env.example              # Exemplo de variáveis de ambiente
├── .eslintrc.json            # Configuração do ESLint
├── .gitignore                # Arquivos ignorados pelo Git
├── components.json           # Configuração do shadcn/ui
├── next.config.js            # Configuração do Next.js
├── package.json              # Dependências e scripts
├── postcss.config.js         # Configuração do PostCSS (para Tailwind)
├── tailwind.config.ts        # Configuração do Tailwind CSS
└── tsconfig.json             # Configuração do TypeScript
```

## Convenções de Nomenclatura

1. **Convenção de Pastas:**

   - Pastas de rotas: Kebab case (`blog-posts/`)
   - Pastas de grupos: Parênteses + kebab case (`(auth)/`)
   - Pastas privadas: Prefixo underscore (`_components/`)

2. **Convenção de Arquivos:**
   - Componentes React: PascalCase (`UserProfile.tsx`)
   - Utilitários/Hooks: camelCase (`useAuth.ts`, `formatDate.ts`)
   - Constantes: SNAKE_CASE_MAIÚSCULO (`API_ENDPOINTS.ts`)

## Organização de Rotas

### Grupos de Rotas (`(group)`)

Utilize grupos de rotas (com parênteses) para:

- Organizar rotas semanticamente sem afetar a URL
- Compartilhar layouts entre rotas relacionadas
- Separar seções da aplicação (autenticada vs. pública)

```typescript
// app/(auth)/layout.tsx
export default function AuthLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div className="flex min-h-screen">
      <div className="w-1/2 bg-primary-800 hidden lg:block">
        {/* Imagem decorativa ou branding */}
      </div>
      <div className="w-full lg:w-1/2 p-8">{children}</div>
    </div>
  );
}
```

### Rotas Dinâmicas

Para rotas dinâmicas, utilize colchetes:

- Parâmetro único: `[id]`
- Parâmetros catch-all: `[...slug]`
- Parâmetros catch-all opcionais: `[[...slug]]`

```
app/blog/[slug]/page.tsx     # /blog/post-1
app/shop/[...categories]/    # /shop/clothes/shirts/blue
```

## Componentes

### Localização dos Componentes

1. **Componentes Globais:**

   - `components/ui/`: Componentes de UI reutilizáveis (shadcn/ui)
   - `components/[nome]/`: Componentes compartilhados por domínio

2. **Componentes Locais:**
   - `app/_components/`: Compartilhados entre todas as rotas
   - `app/(group)/_components/`: Compartilhados apenas no grupo
   - `app/(group)/[route]/_components/`: Específicos para uma rota

### Convenção de Importação

```typescript
// Importações de externos
import { useState } from "react";
import { zodResolver } from "@hookform/resolvers/zod";

// Importações de componentes UI
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

// Importações de utilitários/hooks próprios
import { useAuth } from "@/lib/hooks/useAuth";
import { formatCurrency } from "@/lib/utils/formatters";

// Importações de componentes locais
import { UserCard } from "./_components/UserCard";
```

## Anti-padrões a Evitar

1. **❌ Misturar Lógica de Negócio com Componentes UI**

   ```typescript
   // Evitar: Lógica de negócio dentro de componentes de UI
   function UserButton() {
     // Lógica complexa de autenticação aqui...
     return <Button>Login</Button>;
   }
   ```

   ✅ Correto: Separar lógica de negócio em hooks ou serviços

2. **❌ Ignorar as Convenções de Pastas Privadas**

   ```
   // Evitar: Componentes misturados com páginas
   app/dashboard/UserTable.tsx
   app/dashboard/page.tsx
   ```

   ✅ Correto: `app/dashboard/_components/UserTable.tsx`

3. **❌ Pastas Profundamente Aninhadas**

   ```
   // Evitar estruturas muito profundas
   components/pages/dashboard/sidebar/navigation/links/LinkItem.tsx
   ```

   ✅ Correto: Manter hierarquia rasa com escopo claro

4. **❌ Duplicação de Componentes Semelhantes**

   ```
   // Evitar: componentes quase idênticos
   app/products/_components/ProductList.tsx
   app/categories/_components/CategoryProductList.tsx
   ```

   ✅ Correto: Criar componente reutilizável com props para adaptação

5. **❌ Arquivos Muito Grandes**
   ```typescript
   // Evitar: arquivos com centenas de linhas
   // page.tsx com 500+ linhas
   ```
   ✅ Correto: Extrair componentes e lógica em módulos separados

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals", "plugin:@typescript-eslint/recommended"],
  "plugins": ["@typescript-eslint", "import"],
  "rules": {
    "import/order": [
      "error",
      {
        "groups": [
          "builtin",
          "external",
          "internal",
          ["parent", "sibling", "index"]
        ],
        "pathGroups": [
          {
            "pattern": "react",
            "group": "builtin",
            "position": "before"
          },
          {
            "pattern": "@/components/**",
            "group": "internal",
            "position": "after"
          },
          {
            "pattern": "@/lib/**",
            "group": "internal",
            "position": "after"
          }
        ],
        "newlines-between": "always"
      }
    ],
    "react/jsx-sort-props": [
      "warn",
      {
        "callbacksLast": true,
        "shorthandFirst": true,
        "ignoreCase": true,
        "reservedFirst": true
      }
    ]
  }
}
```

## Quando Aplicar

- Início de novos projetos Next.js com App Router
- Refatoração de projetos existentes para melhorar a organização
- Quando a equipe precisa de padrões consistentes para colaboração
- Sempre que o projeto tiver mais de algumas páginas/rotas
