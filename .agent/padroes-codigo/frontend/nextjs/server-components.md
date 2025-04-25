# Padrão para Server Components no Next.js App Router

## Descrição

Server Components representam um paradigma fundamental no Next.js moderno, permitindo renderização no servidor para melhorar performance, SEO e segurança. Este documento define padrões para implementação eficiente de Server Components, com foco em fetching de dados, separação de responsabilidades, escalabilidade e manutenção, alinhado à documentação oficial do Next.js ([Next.js Docs](https://nextjs.org/docs/app/building-your-application/rendering/server-components)).

---

## Índice

1. [Princípios Fundamentais](#princípios-fundamentais)
2. [Estrutura e Organização de Pastas](#estrutura-e-organização-de-pastas)
3. [Implementação de Server Components](#implementação-de-server-components)

- Estrutura Básica
- Fetch de Dados em Paralelo
- Suspense e Streaming
- Revalidação de Dados
- Metadados Dinâmicos
- Route Handlers para APIs
- Server Actions
- Compartilhamento de Estado

4. [Padrões para Fetch de Dados](#padrões-para-fetch-de-dados)

- Fetch API
- ORM/Database Client
- SWR e React Query (quando usar)

5. [Padrões para Error Handling](#padrões-para-error-handling)
6. [Padrões para Compartilhamento de Estado](#padrões-para-compartilhamento-de-estado)
7. [Padrões para Server Actions](#padrões-para-server-actions)
8. [Padrões para Autenticação e Autorização](#padrões-para-autenticação-e-autorização)
9. [Padrões para SEO e Metadados](#padrões-para-seo-e-metadados)
10. [Padrões para Testes](#padrões-para-testes)
11. [Anti-padrões a Evitar](#anti-padrões-a-evitar)
12. [Configuração do ESLint Recomendada](#configuração-do-eslint-recomendada)
13. [Quando Aplicar](#quando-aplicar)
14. [Referências e Links Úteis](#referências-e-links-úteis)

---

## Princípios Fundamentais

1. **Renderização por Padrão no Servidor**: Todos os componentes no App Router são Server Components por padrão.
2. **Zero JavaScript enviado ao cliente**: Server Components não aumentam o bundle JavaScript no cliente.
3. **Acesso direto a recursos do servidor**: Acesso a banco de dados, filesystem e recursos protegidos.
4. **Busca de dados colocada**: Fetching de dados próximo de onde é utilizado.
5. **Stream e Suspense nativos**: Carregamento progressivo da UI.
6. **Separação clara entre Server e Client Components**: Use `"use client"` explicitamente quando necessário.
7. **Revalidação e cache**: Utilize as estratégias de cache e revalidação do Next.js para otimizar performance.
8. **Segurança por padrão**: Nunca exponha dados sensíveis em Client Components.
9. **Escalabilidade e manutenção**: Estruture o código para facilitar evolução e manutenção.
10. **Documentação e rastreabilidade**: Documente decisões e padrões adotados.

---

## Estrutura e Organização de Pastas

Organize sua aplicação para separar claramente Server Components, Client Components, APIs e utilitários:

```
app/
  products/
   page.tsx           // Server Component
   _components/
    ProductCard.tsx  // Client ou Server Component
    ProductFilters.tsx // Client Component
  dashboard/
   page.tsx
   _components/
    DashboardContent.tsx
    DashboardError.tsx
  api/
   products/
    [id]/
      route.ts       // Route Handler (API)
  lib/
   api/
    products.ts      // Funções de fetch de dados (API externa)
   db/
    products.ts      // Funções de acesso ao banco de dados
  components/
   ui/
    loading-spinner.tsx
    skeleton.tsx
    error-boundary.tsx
```

**Padrão:** Use a pasta `_components` para componentes internos de cada rota. Componentes reutilizáveis devem ficar em `components/`.

---

## Implementação de Server Components

### 1. Estrutura Básica

```typescript
// app/products/page.tsx
import { ProductCard } from "@/components/ProductCard";
import { getProducts } from "@/lib/api/products";

export default async function ProductsPage() {
  const products = await getProducts();

  return (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
      {products.map((product) => (
        <ProductCard key={product.id} product={product} />
      ))}
    </div>
  );
}
```

**Notas:**

- Não utilize hooks do React em Server Components.
- Busque dados diretamente no componente.

---

### 2. Fetch de Dados em Paralelo

```typescript
// app/dashboard/page.tsx
import { Suspense } from "react";
import { getUser } from "@/lib/api/user";
import { getNotifications } from "@/lib/api/notifications";
import { getStats } from "@/lib/api/stats";
import {
  UserProfile,
  NotificationList,
  StatsDisplay,
} from "@/components/dashboard";
import { LoadingSpinner } from "@/components/ui/loading-spinner";

export default async function DashboardPage() {
  const [userData, statsData] = await Promise.all([getUser(), getStats()]);

  return (
    <div className="grid grid-cols-1 md:grid-cols-4 gap-6">
      <div className="md:col-span-1">
        <UserProfile user={userData} />
      </div>
      <div className="md:col-span-3">
        <StatsDisplay stats={statsData} />
        <Suspense fallback={<LoadingSpinner />}>
          <NotificationsList />
        </Suspense>
      </div>
    </div>
  );
}

async function NotificationsList() {
  const notifications = await getNotifications();

  return (
    <div className="mt-6">
      <h2 className="text-xl font-bold">Notificações</h2>
      <ul className="mt-2 space-y-2">
        {notifications.map((notification) => (
          <li key={notification.id} className="p-3 bg-gray-50 rounded-lg">
            {notification.message}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

**Padrão:** Use `Promise.all` para buscar múltiplos dados em paralelo.

---

### 3. Utilização de Suspense e Streaming

```typescript
// app/blog/page.tsx
import { Suspense } from "react";
import { BlogPosts } from "./_components/BlogPosts";
import { PopularTags } from "./_components/PopularTags";
import { FeaturedAuthors } from "./_components/FeaturedAuthors";
import { Skeleton } from "@/components/ui/skeleton";

export default function BlogPage() {
  return (
    <div className="container mx-auto py-12">
      <h1 className="text-3xl font-bold mb-8">Blog</h1>
      <div className="grid grid-cols-1 md:grid-cols-12 gap-8">
        <div className="md:col-span-8">
          <Suspense fallback={<PostsLoadingSkeleton />}>
            <BlogPosts />
          </Suspense>
        </div>
        <div className="md:col-span-4 space-y-8">
          <Suspense fallback={<TagsLoadingSkeleton />}>
            <PopularTags />
          </Suspense>
          <Suspense fallback={<AuthorsLoadingSkeleton />}>
            <FeaturedAuthors />
          </Suspense>
        </div>
      </div>
    </div>
  );
}

function PostsLoadingSkeleton() {
  return (
    <div className="space-y-8">
      {Array.from({ length: 5 }).map((_, i) => (
        <div key={i} className="space-y-3">
          <Skeleton className="h-8 w-3/4" />
          <Skeleton className="h-4 w-full" />
          <Skeleton className="h-4 w-full" />
          <Skeleton className="h-4 w-2/3" />
        </div>
      ))}
    </div>
  );
}
```

**Padrão:** Use `<Suspense>` para carregamento progressivo e streaming.

---

### 4. Buscando Dados com Revalidação

```typescript
// app/products/[id]/page.tsx
import { notFound } from "next/navigation";
import { getProduct } from "@/lib/api/products";
import { ProductDetails } from "./_components/ProductDetails";
import { RelatedProducts } from "./_components/RelatedProducts";

export const revalidate = 3600;

export default async function ProductPage({
  params,
}: {
  params: { id: string };
}) {
  const product = await getProduct(params.id);

  if (!product) {
    notFound();
  }

  return (
    <div className="container mx-auto py-12">
      <ProductDetails product={product} />
      <RelatedProducts
        categoryId={product.categoryId}
        currentProductId={product.id}
      />
    </div>
  );
}
```

**Padrão:** Use a exportação `revalidate` para controlar a revalidação dos dados.

---

### 5. Gerando Metadados Dinâmicos

```typescript
// app/products/[id]/page.tsx
import { Metadata } from "next";
import { getProduct } from "@/lib/api/products";

export async function generateMetadata({
  params,
}: {
  params: { id: string };
}): Promise<Metadata> {
  const product = await getProduct(params.id);

  if (!product) {
    return {
      title: "Produto não encontrado",
      description: "O produto que você está procurando não foi encontrado",
    };
  }

  return {
    title: `${product.name} | Nossa Loja`,
    description: product.description.substring(0, 160),
    openGraph: {
      images: [{ url: product.imageUrl }],
    },
  };
}
```

**Padrão:** Use `generateMetadata` para SEO dinâmico.

---

### 6. Route Handlers para APIs

```typescript
// app/api/products/[id]/route.ts
import { NextResponse } from "next/server";
import { z } from "zod";
import { getProductById, updateProduct } from "@/lib/db/products";

export async function GET(
  request: Request,
  { params }: { params: { id: string } }
) {
  try {
    const product = await getProductById(params.id);

    if (!product) {
      return NextResponse.json(
        { error: "Produto não encontrado" },
        { status: 404 }
      );
    }

    return NextResponse.json(product);
  } catch (error) {
    console.error("Erro ao buscar produto:", error);
    return NextResponse.json(
      { error: "Erro interno do servidor" },
      { status: 500 }
    );
  }
}

const updateProductSchema = z.object({
  name: z.string().min(3).optional(),
  price: z.number().positive().optional(),
  description: z.string().min(10).optional(),
  stock: z.number().int().min(0).optional(),
});

export async function PUT(
  request: Request,
  { params }: { params: { id: string } }
) {
  try {
    const body = await request.json();
    const validation = updateProductSchema.safeParse(body);

    if (!validation.success) {
      return NextResponse.json(
        { errors: validation.error.format() },
        { status: 400 }
      );
    }

    const updatedProduct = await updateProduct(params.id, validation.data);

    if (!updatedProduct) {
      return NextResponse.json(
        { error: "Produto não encontrado" },
        { status: 404 }
      );
    }

    return NextResponse.json(updatedProduct);
  } catch (error) {
    console.error("Erro ao atualizar produto:", error);
    return NextResponse.json(
      { error: "Erro interno do servidor" },
      { status: 500 }
    );
  }
}
```

**Padrão:** Use Route Handlers para APIs RESTful, com validação de entrada.

---

### 7. Server Actions

Server Actions permitem executar código do lado do servidor a partir de formulários ou eventos do cliente, mantendo a segurança e performance.

```typescript
// app/products/_components/ProductForm.tsx
"use client";

import { useFormState } from "react-dom";
import { createProduct } from "@/app/products/actions";

export default function ProductForm() {
  const [state, formAction] = useFormState(createProduct, { error: null });

  return (
    <form action={formAction}>
      <input name="name" required />
      <input name="price" type="number" required />
      <button type="submit">Salvar</button>
      {state.error && <p>{state.error}</p>}
    </form>
  );
}

// app/products/actions.ts
("use server");

import { z } from "zod";
import { db } from "@/lib/db";

const productSchema = z.object({
  name: z.string().min(3),
  price: z.number().positive(),
});

export async function createProduct(prevState: any, formData: FormData) {
  const data = {
    name: formData.get("name"),
    price: Number(formData.get("price")),
  };

  const validation = productSchema.safeParse(data);

  if (!validation.success) {
    return { error: "Dados inválidos" };
  }

  await db.product.create({ data: validation.data });
  return { error: null };
}
```

**Padrão:** Use `"use server"` para Server Actions, sempre validando dados.

---

### 8. Compartilhando Estado Entre Server e Client Components

```typescript
// app/products/page.tsx (Server Component)
import { ProductFilters } from "./_components/ProductFilters"; // Client Component
import { ProductGrid } from "./_components/ProductGrid"; // Server Component
import { getProducts } from "@/lib/api/products";

export default async function ProductsPage({
  searchParams,
}: {
  searchParams: { category?: string; sort?: string };
}) {
  const products = await getProducts({
    category: searchParams.category,
    sort: searchParams.sort,
  });

  return (
    <div>
      <ProductFilters
        initialCategory={searchParams.category}
        initialSort={searchParams.sort}
      />
      <ProductGrid products={products} />
    </div>
  );
}
```

**Padrão:** Passe dados do Server Component para o Client Component via props.

---

## Padrões para Fetch de Dados

### Utilizando a Fetch API

```typescript
// lib/api/products.ts
import { cache } from "react";

export const getProducts = cache(async () => {
  const response = await fetch("https://api.example.com/products", {
    next: { revalidate: 3600 },
  });

  if (!response.ok) {
    throw new Error("Falha ao buscar produtos");
  }

  return response.json();
});

export async function getProduct(id: string) {
  const response = await fetch(`https://api.example.com/products/${id}`, {
    next: { revalidate: 3600 },
  });

  if (response.status === 404) {
    return null;
  }

  if (!response.ok) {
    throw new Error(`Falha ao buscar produto ${id}`);
  }

  return response.json();
}
```

**Padrão:** Use a função `cache` do React para evitar requisições duplicadas.

---

### Utilizando ORM ou Cliente de Banco de Dados

```typescript
// lib/db/products.ts
import { db } from "@/lib/db";
import { cache } from "react";

export const getProducts = cache(async () => {
  try {
    const products = await db.product.findMany({
      where: { isActive: true },
      orderBy: { createdAt: "desc" },
    });

    return products;
  } catch (error) {
    console.error("Erro ao buscar produtos:", error);
    throw new Error("Falha ao buscar produtos do banco de dados");
  }
});

export async function getProductById(id: string) {
  try {
    const product = await db.product.findUnique({
      where: { id },
      include: {
        category: true,
        reviews: {
          take: 5,
          orderBy: { createdAt: "desc" },
        },
      },
    });

    return product;
  } catch (error) {
    console.error(`Erro ao buscar produto ${id}:`, error);
    throw new Error(`Falha ao buscar produto ${id} do banco de dados`);
  }
}
```

---

### SWR e React Query

**Nota:** SWR e React Query são recomendados apenas em Client Components. Para Server Components, use fetch/cache.

---

## Padrões para Error Handling

```typescript
// app/dashboard/page.tsx
import { ErrorBoundary } from "@/components/ErrorBoundary";
import { DashboardContent } from "./_components/DashboardContent";
import { DashboardError } from "./_components/DashboardError";

export default function DashboardPage() {
  return (
    <ErrorBoundary fallback={<DashboardError />}>
      <DashboardContent />
    </ErrorBoundary>
  );
}

// app/dashboard/_components/DashboardContent.tsx
export async function DashboardContent() {
  try {
    const data = await fetchDashboardData();
    return <div>{/* Renderização do conteúdo do dashboard */}</div>;
  } catch (error) {
    console.error("Erro ao carregar dados do dashboard:", error);
    throw error;
  }
}
```

**Padrão:** Use Error Boundaries para capturar erros em Client Components.

---

## Padrões para Compartilhamento de Estado

- Compartilhe estado do servidor para o cliente via props.
- Use contextos apenas em Client Components.
- Para sincronizar estado entre múltiplos Client Components, utilize contextos ou stores (ex: Zustand).

---

## Padrões para Server Actions

- Sempre valide dados recebidos.
- Use `"use server"` no topo do arquivo.
- Retorne mensagens de erro amigáveis.
- Nunca exponha lógica sensível no cliente.

---

## Padrões para Autenticação e Autorização

- Use bibliotecas como [NextAuth.js](https://next-auth.js.org/) ou [Auth0](https://auth0.com/docs/quickstart/webapp/nextjs).
- Faça checagem de autenticação em Server Components para proteger rotas.
- Nunca exponha tokens ou segredos em Client Components.

```typescript
// app/dashboard/page.tsx
import { getServerSession } from "next-auth";
import { redirect } from "next/navigation";

export default async function DashboardPage() {
  const session = await getServerSession();

  if (!session) {
    redirect("/login");
  }

  // ...restante do componente
}
```

---

## Padrões para SEO e Metadados

- Use `generateMetadata` para títulos, descrições e Open Graph.
- Prefira Server Components para páginas com requisitos de SEO.
- Utilize o arquivo `robots.txt` e sitemaps automáticos.

---

## Padrões para Testes

- Use [Vitest](https://vitest.dev/) ou [Jest](https://jestjs.io/) para testes unitários.
- Use [Testing Library](https://testing-library.com/) para testes de integração.
- Teste Server Components isoladamente usando mocks para dependências externas.
- Teste Client Components com simulação de interações do usuário.

---

## Anti-padrões a Evitar

1. **❌ Importar Hooks do React em Server Components**
2. **❌ Operações Pesadas de Processamento no Component Principal**
3. **❌ Não Utilizar Tratamento de Erros**
4. **❌ Misturar Lógica de Servidor em Client Components**
5. **❌ Dados Repetidos Entre Componentes**
6. **❌ Expor dados sensíveis em Client Components**
7. **❌ Fazer fetch de dados em Client Components quando possível no servidor**
8. **❌ Não utilizar Suspense para carregamento progressivo**
9. **❌ Não usar cache/revalidação em fetches**
10. **❌ Não documentar decisões técnicas**

---

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals"],
  "rules": {
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "no-unused-vars": "warn",
    "no-console": ["warn", { "allow": ["warn", "error"] }]
  },
  "overrides": [
    {
      "files": ["app/**/*.ts", "app/**/*.tsx"],
      "excludedFiles": ["app/**/_components/**/*", "app/**/*/client/**/*"],
      "rules": {
        "react-hooks/rules-of-hooks": "off",
        "no-restricted-imports": [
          "error",
          {
            "paths": [
              {
                "name": "react",
                "importNames": [
                  "useState",
                  "useEffect",
                  "useReducer",
                  "useContext"
                ],
                "message": "Hooks não podem ser usados em Server Components. Considere mover este código para um Client Component ('use client')."
              }
            ]
          }
        ]
      }
    }
  ]
}
```

---

## Quando Aplicar

- Ao criar páginas com requisitos de SEO e performance.
- Para operações que requerem acesso direto a recursos do servidor.
- Quando a interatividade do cliente não é necessária.
- Ao buscar dados de APIs externas ou banco de dados.
- Para processamento de dados pesados antes de enviar ao cliente.
- Geração de metadados dinâmicos (título da página, descrição, etc.).

---

## Referências e Links Úteis

- [Documentação Oficial Next.js - Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components)
- [Next.js App Router](https://nextjs.org/docs/app/building-your-application/routing)
- [Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions)
- [Route Handlers](https://nextjs.org/docs/app/building-your-application/routing/route-handlers)
- [Data Fetching](https://nextjs.org/docs/app/building-your-application/data-fetching/fetching)
- [Streaming & Suspense](https://nextjs.org/docs/app/building-your-application/rendering/composition-patterns#streaming)
- [Error Handling](https://nextjs.org/docs/app/building-your-application/rendering/error-handling)
- [SEO](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)
- [NextAuth.js](https://next-auth.js.org/)
- [Auth0 Next.js SDK](/auth0/nextjs-auth0)
- [Apollo Client Next.js App Router Integration](/apollographql/apollo-client-integrations)
- [Next.js Boilerplate](/ixartz/next-js-boilerplate.git)
- [Next.js Argentina Docs](/nextjsargentina/next.js-docs)
- [OpenNext.js Docs](/opennextjs/docs)
- [Open Next.js Cloudflare](/opennextjs/opennextjs-cloudflare)
- [Next.js (Vercel)](/vercel/next.js)

---

## Exemplos Avançados

### Server Component com Server Action e Suspense

```typescript
// app/orders/page.tsx
import { Suspense } from "react";
import { OrdersList } from "./_components/OrdersList";
import { CreateOrderForm } from "./_components/CreateOrderForm";
import { LoadingSpinner } from "@/components/ui/loading-spinner";

export default function OrdersPage() {
  return (
    <div>
      <h1>Pedidos</h1>
      <Suspense fallback={<LoadingSpinner />}>
        <OrdersList />
      </Suspense>
      <CreateOrderForm />
    </div>
  );
}

// app/orders/_components/OrdersList.tsx
import { getOrders } from "@/lib/api/orders";

export async function OrdersList() {
  const orders = await getOrders();
  return (
    <ul>
      {orders.map((order) => (
        <li key={order.id}>{order.description}</li>
      ))}
    </ul>
  );
}

// app/orders/_components/CreateOrderForm.tsx
("use client");
import { useFormState } from "react-dom";
import { createOrder } from "../actions";

export function CreateOrderForm() {
  const [state, formAction] = useFormState(createOrder, { error: null });

  return (
    <form action={formAction}>
      <input name="description" required />
      <button type="submit">Criar Pedido</button>
      {state.error && <p>{state.error}</p>}
    </form>
  );
}

// app/orders/actions.ts
("use server");
import { db } from "@/lib/db";
import { z } from "zod";

const orderSchema = z.object({
  description: z.string().min(5),
});

export async function createOrder(prevState: any, formData: FormData) {
  const data = { description: formData.get("description") as string };
  const validation = orderSchema.safeParse(data);

  if (!validation.success) {
    return { error: "Descrição inválida" };
  }

  await db.order.create({ data: validation.data });
  return { error: null };
}
```
