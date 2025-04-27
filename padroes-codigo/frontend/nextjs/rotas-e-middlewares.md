# Rotas e Middlewares

## Descrição

Este documento descreve os padrões recomendados para implementação de rotas, organização do roteamento dinâmico e uso de middlewares em aplicações Next.js utilizando o App Router. As rotas são fundamentais para a estrutura de navegação, enquanto os middlewares permitem executar código antes das requisições serem completadas.

> **Referências Oficiais:**
>
> - [Next.js Routing Documentation](https://nextjs.org/docs/app/building-your-application/routing)
> - [Next.js Middleware](https://nextjs.org/docs/app/building-your-application/routing/middleware)
> - [Next.js API Routes](https://nextjs.org/docs/pages/building-your-application/routing/api-routes)
> - [Next.js Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts)
> - [Next.js Dynamic Routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes)

---

## Princípios Fundamentais

- **Estrutura baseada em arquivos**: Aproveite o sistema de arquivos para definir rotas de forma intuitiva.
- **Simplicidade**: Mantenha a organização de rotas clara e previsível.
- **Separação de responsabilidades**: Use middlewares para separar lógica comum e transversal.
- **Clareza de intenção**: Nomeie arquivos e pastas seguindo convenções consistentes.
- **Otimização de performance**: Aproveite as capacidades de carregamento e pré-busca do Next.js.
- **Escalabilidade**: Estruture rotas e middlewares pensando em crescimento futuro.
- **Segurança**: Utilize middlewares para proteger rotas sensíveis e garantir autenticação/autorização.
- **Consistência**: Siga convenções de nomenclatura e estrutura recomendadas pela documentação oficial.

---

## Implementação

### 1. Estrutura básica de rotas

O Next.js App Router utiliza a estrutura de pastas para definir rotas, onde cada pasta representa um segmento de URL e o arquivo `page.tsx` define o componente React dessa rota.

```tsx
// app/dashboard/page.tsx
export default function DashboardPage() {
  return (
    <main>
      <h1>Dashboard</h1>
      <p>Bem-vindo ao seu painel de controle</p>
    </main>
  );
}
```

#### Observações

- O arquivo `page.tsx` é obrigatório para cada rota.
- O arquivo `layout.tsx` pode ser usado para layouts compartilhados.
- O arquivo `loading.tsx` pode ser usado para estados de carregamento.
- O arquivo `error.tsx` pode ser usado para tratamento de erros específicos da rota.

---

### 2. Rotas dinâmicas

Para rotas dinâmicas, use pastas com nomes entre colchetes para indicar parâmetros dinâmicos.

```tsx
// app/produtos/[id]/page.tsx
export default function ProdutoDetalhe({ params }: { params: { id: string } }) {
  return (
    <div>
      <h1>Produto {params.id}</h1>
      {/* Conteúdo do produto */}
    </div>
  );
}
```

#### Geração Estática de Rotas Dinâmicas

Implemente a função `generateStaticParams` para gerar rotas estáticas em build time:

```tsx
// app/produtos/[id]/page.tsx
export async function generateStaticParams() {
  const produtos = await fetchProdutos();

  return produtos.map((produto) => ({
    id: produto.id.toString(),
  }));
}
```

#### Rotas Catch-all e Optional Catch-all

- `[...slug]` para capturar múltiplos segmentos.
- `[[...slug]]` para capturar múltiplos segmentos opcionais.

```tsx
// app/blog/[...slug]/page.tsx
export default function BlogPost({ params }: { params: { slug: string[] } }) {
  return <div>Post: {params.slug.join("/")}</div>;
}
```

---

### 3. Rotas aninhadas e layouts

Crie layouts compartilhados para seções da aplicação usando arquivos `layout.tsx`:

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div className="dashboard-container">
      <nav className="dashboard-nav">{/* Navegação do dashboard */}</nav>
      <main className="dashboard-content">{children}</main>
    </div>
  );
}
```

#### Layouts Aninhados

Layouts podem ser aninhados para criar hierarquias de navegação e estilos:

```
app/
├── layout.tsx
├── dashboard/
│   ├── layout.tsx
│   └── page.tsx
└── settings/
        └── page.tsx
```

---

### 4. Grupos de rotas

Use grupos de rotas para organizar a estrutura sem afetar a URL final, envolvendo pastas com parênteses:

```
app/
├── (auth)/
│   ├── login/
│   │   └── page.tsx
│   ├── registro/
│   │   └── page.tsx
│   └── layout.tsx
└── (dashboard)/
        ├── perfil/
        │   └── page.tsx
        └── configuracoes/
                └── page.tsx
```

- Grupos são úteis para separar contextos (ex: autenticação, dashboard, público).
- Não afetam a URL final do usuário.

---

### 5. Middlewares globais

Crie um arquivo `middleware.ts` na raiz do projeto para lógica que deve ser executada antes das requisições:

```tsx
// middleware.ts
import { NextResponse } from "next/server";
import type { NextRequest } from "next/server";

export function middleware(request: NextRequest) {
  // Verificar autenticação
  const token = request.cookies.get("auth-token")?.value;

  // Redirecionar para login se não estiver autenticado e estiver acessando rotas protegidas
  if (!token && request.nextUrl.pathname.startsWith("/dashboard")) {
    return NextResponse.redirect(new URL("/login", request.url));
  }

  return NextResponse.next();
}

// Configurar em quais rotas o middleware deve ser executado
export const config = {
  matcher: ["/dashboard/:path*", "/api/:path*"],
};
```

#### Observações

- O middleware é executado antes de cada requisição nas rotas especificadas.
- Pode ser usado para autenticação, logging, internacionalização, etc.
- Não execute lógica de negócio complexa no middleware.

---

### 6. Middlewares específicos para rotas

Para lógica específica a determinadas rotas, utilize funções utilitárias:

```tsx
// lib/auth-middleware.ts
import { NextRequest, NextResponse } from "next/server";

export function withAuthorization(
  handler: (req: NextRequest) => NextResponse | Promise<NextResponse>,
  requiredRole = "user"
) {
  return async function (req: NextRequest) {
    // Verificar token e extrair papel do usuário
    const token = req.cookies.get("auth-token")?.value;

    if (!token) {
      return NextResponse.redirect(new URL("/login", req.url));
    }

    try {
      const decodedToken = verifyToken(token);

      if (decodedToken.role !== requiredRole && decodedToken.role !== "admin") {
        return NextResponse.redirect(new URL("/unauthorized", req.url));
      }

      // Se autorizado, continua para o handler original
      return handler(req);
    } catch (error) {
      // Token inválido
      return NextResponse.redirect(new URL("/login", req.url));
    }
  };
}

// Função de exemplo para verificação de token (implemente com sua lógica real)
function verifyToken(token: string) {
  // Na implementação real, use uma biblioteca como jose ou jsonwebtoken
  return { userId: "123", role: "user" };
}
```

#### Exemplo de uso:

```tsx
// app/api/admin/route.ts
import { NextRequest, NextResponse } from "next/server";
import { withAuthorization } from "@/lib/auth-middleware";

async function handler(req: NextRequest) {
  // Lógica do endpoint protegido
  return NextResponse.json({ message: "Dados administrativos" });
}

// Proteger rota apenas para administradores
export const GET = withAuthorization(handler, "admin");
```

---

### 7. Gerenciamento de parâmetros de URL e query

Para acessar parâmetros de query em rotas:

```tsx
// app/search/page.tsx
export default async function SearchPage({
  searchParams,
}: {
  searchParams: { q?: string; page?: string };
}) {
  const query = searchParams.q || "";
  const page = parseInt(searchParams.page || "1", 10);

  const results = await searchProducts(query, page);

  return (
    <div>
      <h1>Resultados para: {query}</h1>
      {/* Exibir resultados */}
    </div>
  );
}
```

#### Parâmetros de URL

- `params` contém os parâmetros definidos na estrutura de pastas.
- `searchParams` contém os parâmetros de query string.

---

### 8. Rotas de API

Crie endpoints de API com handlers para diferentes métodos HTTP:

```tsx
// app/api/produtos/route.ts
import { NextRequest, NextResponse } from "next/server";

export async function GET(request: NextRequest) {
  const produtos = await fetchProdutos();
  return NextResponse.json(produtos);
}

export async function POST(request: NextRequest) {
  const data = await request.json();
  const novoProduto = await criarProduto(data);

  return NextResponse.json(novoProduto, { status: 201 });
}
```

#### Rotas dinâmicas de API

```tsx
// app/api/produtos/[id]/route.ts
import { NextRequest, NextResponse } from "next/server";

export async function GET(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  const produto = await fetchProdutoPorId(params.id);

  if (!produto) {
    return NextResponse.json(
      { message: "Produto não encontrado" },
      { status: 404 }
    );
  }

  return NextResponse.json(produto);
}

export async function PUT(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  const data = await request.json();
  const produtoAtualizado = await atualizarProduto(params.id, data);

  return NextResponse.json(produtoAtualizado);
}

export async function DELETE(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  await deletarProduto(params.id);
  return NextResponse.json({ message: "Produto removido" }, { status: 200 });
}
```

#### Observações

- Use métodos HTTP (`GET`, `POST`, `PUT`, `DELETE`) exportados como funções.
- Utilize `NextRequest` e `NextResponse` para manipulação de requisições e respostas.

---

### 9. Rotas de API convencionais (Pages Router)

Se ainda utilizar o Pages Router para APIs:

```tsx
// pages/api/hello.ts
import type { NextApiRequest, NextApiResponse } from "next";

export default function handler(req: NextApiRequest, res: NextApiResponse) {
  res.status(200).json({ name: "John Doe" });
}
```

---

### 10. Rotas protegidas e autenticação

Utilize middlewares para proteger rotas sensíveis:

```tsx
// middleware.ts
import { NextResponse } from "next/server";
import type { NextRequest } from "next/server";

export function middleware(request: NextRequest) {
  const token = request.cookies.get("auth-token")?.value;

  if (!token && request.nextUrl.pathname.startsWith("/admin")) {
    return NextResponse.redirect(new URL("/login", request.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ["/admin/:path*"],
};
```

---

### 11. Internacionalização (i18n) com rotas

Configure suporte a múltiplos idiomas:

```js
// next.config.js
module.exports = {
  i18n: {
    locales: ["en", "pt-BR"],
    defaultLocale: "pt-BR",
  },
};
```

- Rotas serão prefixadas automaticamente com o idioma.
- Use middlewares para redirecionamento baseado em preferências do usuário.

---

### 12. Rotas estáticas e dinâmicas

- Rotas estáticas são geradas em build time (`generateStaticParams`).
- Rotas dinâmicas são resolvidas em tempo de execução.

#### Incremental Static Regeneration (ISR)

```tsx
export const revalidate = 60; // Revalida a cada 60 segundos
```

---

### 13. Rotas de fallback e tratamento de erros

Utilize arquivos `not-found.tsx` e `error.tsx` para tratamento de erros:

```tsx
// app/not-found.tsx
export default function NotFound() {
  return <h1>Página não encontrada</h1>;
}
```

```tsx
// app/error.tsx
"use client";
export default function Error({
  error,
  reset,
}: {
  error: Error;
  reset: () => void;
}) {
  return (
    <div>
      <h2>Ocorreu um erro!</h2>
      <button onClick={() => reset()}>Tentar novamente</button>
    </div>
  );
}
```

---

### 14. Middlewares para logging e monitoramento

Implemente middlewares para registrar acessos e monitorar métricas:

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  console.log(
    `[${new Date().toISOString()}] ${request.method} ${
      request.nextUrl.pathname
    }`
  );
  return NextResponse.next();
}
```

---

### 15. Middlewares para CORS

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const response = NextResponse.next();
  response.headers.set("Access-Control-Allow-Origin", "*");
  response.headers.set(
    "Access-Control-Allow-Methods",
    "GET,POST,PUT,DELETE,OPTIONS"
  );
  response.headers.set(
    "Access-Control-Allow-Headers",
    "Content-Type, Authorization"
  );
  return response;
}
```

---

### 16. Middlewares para manipulação de headers

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const response = NextResponse.next();
  response.headers.set("X-Frame-Options", "DENY");
  response.headers.set("X-Content-Type-Options", "nosniff");
  return response;
}
```

---

### 17. Middlewares para reescrita e redirecionamento de URLs

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  if (request.nextUrl.pathname === "/antiga") {
    return NextResponse.redirect(new URL("/nova", request.url));
  }
  return NextResponse.next();
}
```

---

### 18. Middlewares para autenticação baseada em sessão

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const session = request.cookies.get("session-id")?.value;
  if (!session) {
    return NextResponse.redirect(new URL("/login", request.url));
  }
  return NextResponse.next();
}
```

---

### 19. Middlewares para limitação de requisições (rate limiting)

> **Nota:** Para limitação avançada, utilize edge functions ou soluções externas.

```tsx
// Exemplo simplificado
const requests = new Map();

export function middleware(request: NextRequest) {
  const ip = request.ip ?? "unknown";
  const now = Date.now();
  const timestamps = requests.get(ip) || [];
  const recent = timestamps.filter((t: number) => now - t < 60000);

  if (recent.length > 100) {
    return new NextResponse("Limite de requisições excedido", { status: 429 });
  }

  requests.set(ip, [...recent, now]);
  return NextResponse.next();
}
```

---

### 20. Middlewares para internacionalização automática

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const acceptLang = request.headers.get("accept-language");
  if (
    acceptLang &&
    !request.nextUrl.pathname.startsWith("/en") &&
    acceptLang.startsWith("en")
  ) {
    return NextResponse.redirect(
      new URL("/en" + request.nextUrl.pathname, request.url)
    );
  }
  return NextResponse.next();
}
```

---

## Anti-padrões a evitar

### 1. Misturar paradigmas de roteamento

❌ **Não faça isso**:

```tsx
// Misturar Pages Router com App Router
// pages/produtos/[id].tsx E app/produtos/[id]/page.tsx
```

✅ **Prefira**:
Escolha um paradigma de roteamento (App Router é recomendado para novos projetos) e mantenha-se consistente.

---

### 2. Lógica excessiva em middlewares

❌ **Não faça isso**:

```tsx
export function middleware(request: NextRequest) {
  // Middleware com lógica de negócio complexa, operações de banco de dados, etc.
  const resultado = fazerCalculosComplexos();
  const dadosDoBanco = await consultarBancoDeDados();
  // ...mais 100 linhas de código
}
```

✅ **Prefira**:
Mantenha middlewares focados em funções específicas como autenticação, redirecionamentos e logging.

---

### 3. Negligenciar tratamento de erros em middlewares

❌ **Não faça isso**:

```tsx
export function middleware(request: NextRequest) {
  const token = verifyToken(request.cookies.get("token")?.value || "");
  // Se verifyToken lançar um erro, o middleware quebrará sem tratamento adequado

  return NextResponse.next();
}
```

✅ **Prefira**:

```tsx
export function middleware(request: NextRequest) {
  try {
    const token = verifyToken(request.cookies.get("token")?.value || "");
    // Continuar processamento com token válido
    return NextResponse.next();
  } catch (error) {
    // Lidar com erro de forma adequada
    console.error("Erro de autenticação:", error);
    return NextResponse.redirect(new URL("/login", request.url));
  }
}
```

---

### 4. Estrutura de rotas excessivamente profunda

❌ **Não faça isso**:

```
app/categoria/subcategoria/tipo/subtipo/detalhe/[id]/editar/page.tsx
```

✅ **Prefira**:
Limite a profundidade de aninhamento e considere o uso de parâmetros de query para filtros adicionais.

---

### 5. Duplicação de lógica entre middlewares e componentes

❌ **Não faça isso**:
Implementar a mesma lógica de verificação de autenticação tanto no middleware quanto nos componentes de página.

✅ **Prefira**:
Use middlewares para autenticação a nível de rota e componentes para lógica específica de UI baseada em permissões.

---

### 6. Não utilizar matcher corretamente

❌ **Não faça isso**:

```tsx
export const config = {
  matcher: ["/api/*"],
};
```

✅ **Prefira**:

```tsx
export const config = {
  matcher: ["/api/:path*"],
};
```

---

### 7. Não tratar métodos HTTP corretamente em rotas de API

❌ **Não faça isso**:

```tsx
export default function handler(req, res) {
  // Lida com todos os métodos de forma igual
}
```

✅ **Prefira**:

```tsx
export async function GET(req: NextRequest) {
  /* ... */
}
export async function POST(req: NextRequest) {
  /* ... */
}
```

---

### 8. Não utilizar layouts para compartilhamento de UI

❌ **Não faça isso**:
Repetir código de navegação ou cabeçalho em múltiplas páginas.

✅ **Prefira**:
Utilize `layout.tsx` para componentes compartilhados.

---

### 9. Não documentar middlewares e rotas

❌ **Não faça isso**:
Deixar middlewares e rotas sem comentários ou documentação.

✅ **Prefira**:
Documente a finalidade e funcionamento de cada middleware e rota.

---

### 10. Não versionar rotas de API

❌ **Não faça isso**:

```
app/api/produtos/route.ts
```

✅ **Prefira**:

```
app/api/v1/produtos/route.ts
```

---

## Configuração de ESLint recomendada

```json
{
  "rules": {
    "import/no-anonymous-default-export": "error",
    "react-hooks/rules-of-hooks": "error",
    "@next/next/no-html-link-for-pages": "error",
    "@typescript-eslint/explicit-function-return-type": [
      "warn",
      {
        "allowExpressions": true,
        "allowTypedFunctionExpressions": true
      }
    ]
  }
}
```

---

## Quando Aplicar

- Ao estruturar o roteamento de uma nova aplicação Next.js
- Quando precisa implementar lógica de autenticação/autorização entre rotas
- Para garantir segurança e consistência em APIs
- Ao migrar de Pages Router para App Router
- Quando precisa otimizar o carregamento e pré-busca de páginas
- Para implementar redirecionamentos e reescritas de URLs
- Para internacionalização e suporte a múltiplos idiomas
- Para logging, monitoramento e métricas de acesso
- Para limitação de requisições e proteção contra abusos

---

## Referências e Links Úteis

- [Documentação Oficial do Next.js](https://nextjs.org/docs)
- [Routing: App Router](https://nextjs.org/docs/app/building-your-application/routing)
- [Middleware](https://nextjs.org/docs/app/building-your-application/routing/middleware)
- [API Routes](https://nextjs.org/docs/pages/building-your-application/routing/api-routes)
- [Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts)
- [Dynamic Routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes)
- [Internationalization](https://nextjs.org/docs/app/building-your-application/routing/internationalization)
- [Error Handling](https://nextjs.org/docs/app/building-your-application/routing/error-handling)
- [Edge Middleware Examples](https://github.com/vercel/examples/tree/main/edge-middleware)

---

## Exemplos Avançados

### Middleware para autenticação JWT

```tsx
// middleware.ts
import { NextRequest, NextResponse } from "next/server";
import jwt from "jsonwebtoken";

export function middleware(request: NextRequest) {
  const token = request.cookies.get("jwt")?.value;
  if (!token) {
    return NextResponse.redirect(new URL("/login", request.url));
  }
  try {
    jwt.verify(token, process.env.JWT_SECRET!);
    return NextResponse.next();
  } catch {
    return NextResponse.redirect(new URL("/login", request.url));
  }
}
```

---

### Middleware para logging de performance

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const start = Date.now();
  const response = NextResponse.next();
  response.headers.set("X-Response-Time", `${Date.now() - start}ms`);
  return response;
}
```

---

### Middleware para headers de segurança

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const response = NextResponse.next();
  response.headers.set(
    "Strict-Transport-Security",
    "max-age=63072000; includeSubDomains; preload"
  );
  response.headers.set("Content-Security-Policy", "default-src 'self'");
  response.headers.set("Referrer-Policy", "no-referrer");
  return response;
}
```

---

### Middleware para manutenção

```tsx
// middleware.ts
export function middleware(request: NextRequest) {
  const maintenance = process.env.MAINTENANCE_MODE === "true";
  if (maintenance && !request.nextUrl.pathname.startsWith("/admin")) {
    return new NextResponse("Site em manutenção", { status: 503 });
  }
  return NextResponse.next();
}
```

---

### Estrutura recomendada de pastas para rotas e middlewares

```
app/
├── (auth)/
│   ├── login/
│   ├── registro/
│   └── layout.tsx
├── (dashboard)/
│   ├── perfil/
│   ├── configuracoes/
│   └── layout.tsx
├── api/
│   ├── v1/
│   │   ├── produtos/
│   │   └── usuarios/
│   └── v2/
│       └── produtos/
├── middleware.ts
├── not-found.tsx
├── error.tsx
└── layout.tsx
```

---

## Checklist de Boas Práticas

- [ ] Utiliza App Router para novas aplicações
- [ ] Estrutura rotas e layouts de forma clara e modular
- [ ] Utiliza middlewares para autenticação, logging e headers de segurança
- [ ] Evita lógica de negócio complexa em middlewares
- [ ] Implementa tratamento de erros e páginas de fallback
- [ ] Documenta rotas, middlewares e suas responsabilidades
- [ ] Utiliza ESLint e segue regras recomendadas
- [ ] Versiona rotas de API quando necessário
- [ ] Limita profundidade de rotas e evita duplicação de lógica

---

## Observações Finais

- Sempre consulte a [documentação oficial do Next.js](https://nextjs.org/docs) para atualizações e melhores práticas.
- Adapte os exemplos conforme a necessidade do seu projeto.
- Mantenha o código limpo, modular e seguro.

---

## Histórico de Atualizações

- 2024-06-01: Adição de exemplos avançados de middlewares.
- 2024-06-02: Revisão para alinhamento com documentação oficial Next.js 14.
- 2024-06-03: Inclusão de checklist e estrutura de pastas recomendada.

---

## Contribuidores

- Anderson Silva
- Equipe de Engenharia Visual
- Comunidade Next.js

---

## Licença

Este documento segue a licença MIT, conforme o projeto principal.

---

<!--
Este documento foi gerado e revisado de acordo com os padrões oficiais do Next.js e práticas recomendadas da comunidade.
Para sugestões ou melhorias, abra uma issue no repositório.
-->
