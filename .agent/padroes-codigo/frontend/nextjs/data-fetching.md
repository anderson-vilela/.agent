# Padrão para Data Fetching no Next.js App Router

## Descrição

Este documento define padrões para implementação de estratégias de fetching de dados em aplicações Next.js com App Router, incluindo abordagens para cache, revalidação e tratamento de erros. Os padrões aqui apresentados aproveitam os recursos nativos do Next.js para otimização de performance e experiência do usuário.

## Princípios Fundamentais

1. **Priorizar Server Components**: Realizar fetching de dados primariamente em Server Components para melhor performance e SEO
2. **Caching Estratégico**: Utilizar as estratégias de cache do Next.js para reduzir requisições desnecessárias
3. **Revalidação Controlada**: Implementar revalidação de dados de forma consistente e previsível
4. **Tipagem Forte**: Manter tipagem TypeScript em todas as operações de dados
5. **Tratamento de Erros**: Implementar tratamento de erros consistente e recuperação elegante

## Implementação de Estratégias de Data Fetching

### 1. Fetching de Dados em Server Components

```typescript
// app/(shop)/products/[category]/page.tsx
import { Metadata } from "next";
import { notFound } from "next/navigation";
import { db } from "@/lib/db";
import { ProductList } from "./_components/ProductList";
import { CategoryHeader } from "./_components/CategoryHeader";

interface PageProps {
  params: {
    category: string;
  };
  searchParams: {
    sort?: string;
    page?: string;
  };
}

// Gerar metadados dinâmicos
export async function generateMetadata({
  params,
}: PageProps): Promise<Metadata> {
  const category = await getCategory(params.category);

  if (!category) {
    return {
      title: "Categoria não encontrada",
    };
  }

  return {
    title: `${category.name} | Loja Online`,
    description:
      category.description || `Explore produtos na categoria ${category.name}`,
  };
}

// Função de fetching de dados para categoria
async function getCategory(slug: string) {
  try {
    return await db.category.findUnique({
      where: { slug },
      select: {
        id: true,
        name: true,
        description: true,
        imageUrl: true,
      },
    });
  } catch (error) {
    console.error("Erro ao buscar categoria:", error);
    return null;
  }
}

// Função de fetching de dados para produtos
async function getProductsByCategory(
  categorySlug: string,
  sort: string = "newest",
  page: number = 1
) {
  const pageSize = 12;

  try {
    // Obter categoria primeiro
    const category = await db.category.findUnique({
      where: { slug: categorySlug },
      select: { id: true },
    });

    if (!category) {
      return { products: [], totalProducts: 0 };
    }

    // Configurar ordenação
    const orderBy: any = {};
    switch (sort) {
      case "price-low":
        orderBy.price = "asc";
        break;
      case "price-high":
        orderBy.price = "desc";
        break;
      case "popular":
        orderBy.sales = "desc";
        break;
      case "newest":
      default:
        orderBy.createdAt = "desc";
    }

    // Buscar produtos e total para paginação
    const [products, totalProducts] = await Promise.all([
      db.product.findMany({
        where: {
          categoryId: category.id,
          isPublished: true,
        },
        select: {
          id: true,
          name: true,
          slug: true,
          price: true,
          imageUrl: true,
          averageRating: true,
        },
        orderBy,
        skip: (page - 1) * pageSize,
        take: pageSize,
      }),
      db.product.count({
        where: {
          categoryId: category.id,
          isPublished: true,
        },
      }),
    ]);

    return {
      products,
      totalProducts,
    };
  } catch (error) {
    console.error("Erro ao buscar produtos:", error);
    return { products: [], totalProducts: 0 };
  }
}

export default async function CategoryPage({
  params,
  searchParams,
}: PageProps) {
  const category = await getCategory(params.category);

  // Redirecionar para 404 se categoria não existir
  if (!category) {
    notFound();
  }

  // Processar e validar parâmetros de consulta
  const sort = ["newest", "price-low", "price-high", "popular"].includes(
    searchParams.sort || ""
  )
    ? searchParams.sort
    : "newest";

  const page =
    isNaN(Number(searchParams.page)) || Number(searchParams.page) < 1
      ? 1
      : Number(searchParams.page);

  // Buscar produtos com base nos parâmetros validados
  const { products, totalProducts } = await getProductsByCategory(
    params.category,
    sort,
    page
  );

  // Calcular paginação
  const pageSize = 12;
  const totalPages = Math.ceil(totalProducts / pageSize);

  return (
    <div className="container mx-auto py-8">
      <CategoryHeader category={category} />

      <ProductList
        products={products}
        currentSort={sort as string}
        pagination={{
          currentPage: page,
          totalPages,
          totalItems: totalProducts,
        }}
      />
    </div>
  );
}
```

### 2. Centralização de Funções de Fetching

```typescript
// lib/api/products.ts - Centralizando funções de data fetching
import "server-only";
import { cache } from "react";
import { db } from "@/lib/db";
import { notFound } from "next/navigation";

export type Product = {
  id: string;
  name: string;
  slug: string;
  description: string;
  price: number;
  imageUrl: string | null;
  categoryId: string;
  category: {
    name: string;
    slug: string;
  };
  isPublished: boolean;
  createdAt: Date;
  updatedAt: Date;
  averageRating: number | null;
};

// Opções de cache utilizando cache() do React
export const getFeaturedProducts = cache(async () => {
  try {
    const products = await db.product.findMany({
      where: {
        isFeatured: true,
        isPublished: true,
      },
      select: {
        id: true,
        name: true,
        slug: true,
        price: true,
        imageUrl: true,
        averageRating: true,
      },
      orderBy: {
        createdAt: "desc",
      },
      take: 6,
    });

    return products;
  } catch (error) {
    console.error("Erro ao buscar produtos em destaque:", error);
    return [];
  }
});

export const getProductBySlug = cache(async (slug: string) => {
  try {
    const product = await db.product.findUnique({
      where: { slug },
      include: {
        category: {
          select: {
            name: true,
            slug: true,
          },
        },
      },
    });

    if (!product || !product.isPublished) {
      return null;
    }

    return product;
  } catch (error) {
    console.error(`Erro ao buscar produto com slug ${slug}:`, error);
    return null;
  }
});

export const getRelatedProducts = cache(
  async (productId: string, categoryId: string, limit: number = 4) => {
    try {
      const relatedProducts = await db.product.findMany({
        where: {
          categoryId,
          isPublished: true,
          id: { not: productId },
        },
        select: {
          id: true,
          name: true,
          slug: true,
          price: true,
          imageUrl: true,
          averageRating: true,
        },
        orderBy: {
          averageRating: "desc",
        },
        take: limit,
      });

      return relatedProducts;
    } catch (error) {
      console.error("Erro ao buscar produtos relacionados:", error);
      return [];
    }
  }
);
```

### 3. Uso de Fetching com Revalidação

```typescript
// lib/api/posts.ts - Fetch com revalidação
import "server-only";
import { db } from "@/lib/db";

export type Post = {
  id: string;
  title: string;
  slug: string;
  excerpt: string;
  content: string;
  imageUrl: string | null;
  publishedAt: Date;
  author: {
    id: string;
    name: string;
    imageUrl: string | null;
  };
};

// Obter todos os posts com opções de revalidação
export async function getPosts(
  page: number = 1,
  limit: number = 10,
  options: { revalidate?: number | false } = {}
) {
  const { revalidate = 3600 } = options; // 1 hora por padrão

  try {
    // Calcular paginação
    const skip = (page - 1) * limit;

    // Query de contagem total (para paginação)
    const countPromise = db.post.count({
      where: {
        published: true,
      },
    });

    // Query principal dos posts
    const postsPromise = db.post.findMany({
      where: {
        published: true,
      },
      select: {
        id: true,
        title: true,
        slug: true,
        excerpt: true,
        imageUrl: true,
        publishedAt: true,
        author: {
          select: {
            id: true,
            name: true,
            imageUrl: true,
          },
        },
      },
      orderBy: {
        publishedAt: "desc",
      },
      skip,
      take: limit,
    });

    // Executar ambas as queries em paralelo
    const [totalPosts, posts] = await Promise.all([countPromise, postsPromise]);

    return {
      posts,
      metadata: {
        totalPosts,
        totalPages: Math.ceil(totalPosts / limit),
        currentPage: page,
        limit,
      },
    };
  } catch (error) {
    console.error("Erro ao buscar posts:", error);
    return {
      posts: [],
      metadata: {
        totalPosts: 0,
        totalPages: 0,
        currentPage: page,
        limit,
      },
    };
  }
}

// Obter um post específico por slug
export async function getPostBySlug(
  slug: string,
  options: { revalidate?: number | false } = {}
) {
  const { revalidate = 3600 } = options; // 1 hora por padrão

  try {
    const post = await db.post.findUnique({
      where: {
        slug,
        published: true,
      },
      include: {
        author: {
          select: {
            id: true,
            name: true,
            imageUrl: true,
          },
        },
      },
    });

    return post;
  } catch (error) {
    console.error(`Erro ao buscar post com slug ${slug}:`, error);
    return null;
  }
}
```

### 4. Uso em Componentes de Página

```typescript
// app/blog/page.tsx
import { Metadata } from "next";
import { getPosts } from "@/lib/api/posts";
import { PostGrid } from "./_components/PostGrid";
import { Pagination } from "@/components/ui/pagination";

interface PageProps {
  searchParams: {
    page?: string;
  };
}

export const metadata: Metadata = {
  title: "Blog | Nossa Empresa",
  description: "Artigos e notícias sobre nossa indústria e produtos",
};

export default async function BlogPage({ searchParams }: PageProps) {
  // Validar e processar parâmetros de consulta
  const page =
    isNaN(Number(searchParams.page)) || Number(searchParams.page) < 1
      ? 1
      : Number(searchParams.page);

  // Buscar posts com revalidação a cada 10 minutos
  const { posts, metadata } = await getPosts(page, 9, { revalidate: 600 });

  return (
    <div className="container py-8">
      <h1 className="text-3xl font-bold mb-8">Blog</h1>

      {posts.length > 0 ? (
        <>
          <PostGrid posts={posts} />

          <div className="mt-8">
            <Pagination
              currentPage={metadata.currentPage}
              totalPages={metadata.totalPages}
              baseUrl="/blog"
            />
          </div>
        </>
      ) : (
        <p className="text-muted-foreground text-center py-12">
          Nenhum artigo encontrado.
        </p>
      )}
    </div>
  );
}
```

```typescript
// app/blog/[slug]/page.tsx
import { Metadata } from "next";
import { notFound } from "next/navigation";
import Image from "next/image";
import { format } from "date-fns";
import { ptBR } from "date-fns/locale";
import { getPostBySlug, getPosts } from "@/lib/api/posts";
import { PostContent } from "./_components/PostContent";
import { RecentPosts } from "./_components/RecentPosts";

interface PageProps {
  params: {
    slug: string;
  };
}

// Gerar metadados dinâmicos
export async function generateMetadata({
  params,
}: PageProps): Promise<Metadata> {
  const post = await getPostBySlug(params.slug);

  if (!post) {
    return {
      title: "Artigo não encontrado",
    };
  }

  return {
    title: `${post.title} | Blog`,
    description: post.excerpt,
    openGraph: post.imageUrl
      ? {
          images: [post.imageUrl],
        }
      : undefined,
  };
}

// Geração de rotas estáticas
export async function generateStaticParams() {
  // Buscar todos os posts para pré-renderização
  // Limitado aos 20 posts mais recentes para evitar builds excessivamente longos
  const { posts } = await getPosts(1, 20);

  return posts.map((post) => ({
    slug: post.slug,
  }));
}

export default async function BlogPostPage({ params }: PageProps) {
  // Buscar post com revalidação ISR de 1 hora
  const post = await getPostBySlug(params.slug, { revalidate: 3600 });

  if (!post) {
    notFound();
  }

  // Formatar data
  const formattedDate = format(
    new Date(post.publishedAt),
    "d 'de' MMMM 'de' yyyy",
    { locale: ptBR }
  );

  return (
    <div className="container py-8">
      <article className="max-w-4xl mx-auto">
        <div className="mb-8">
          <h1 className="text-3xl md:text-4xl font-bold mb-4">{post.title}</h1>

          <div className="flex items-center space-x-4 text-muted-foreground">
            {post.author.imageUrl && (
              <Image
                src={post.author.imageUrl}
                alt={post.author.name}
                width={40}
                height={40}
                className="rounded-full"
              />
            )}

            <div>
              <p className="font-medium text-foreground">{post.author.name}</p>
              <p className="text-sm">{formattedDate}</p>
            </div>
          </div>
        </div>

        {post.imageUrl && (
          <div className="mb-8">
            <Image
              src={post.imageUrl}
              alt={post.title}
              width={1200}
              height={630}
              className="rounded-lg"
              priority
            />
          </div>
        )}

        <PostContent content={post.content} />
      </article>

      <div className="mt-16">
        <h2 className="text-2xl font-bold mb-8">Posts Recentes</h2>
        <RecentPosts currentPostId={post.id} />
      </div>
    </div>
  );
}
```

### 5. Fetching de Dados em Client Components

```typescript
// lib/api/client.ts - Cliente para API no lado do cliente
import { z } from "zod";

const baseUrl = process.env.NEXT_PUBLIC_API_URL || "";

// Esquemas de validação
const productSchema = z.object({
  id: z.string(),
  name: z.string(),
  price: z.number(),
  imageUrl: z.string().nullable(),
  averageRating: z.number().nullable(),
});

const searchResultSchema = z.object({
  products: z.array(productSchema),
  totalResults: z.number(),
});

type SearchParams = {
  query: string;
  page?: number;
  limit?: number;
  categoryId?: string;
};

// Função para busca de produtos no cliente
export async function searchProducts(params: SearchParams) {
  try {
    const { query, page = 1, limit = 10, categoryId } = params;

    // Construir URL de busca
    const queryParams = new URLSearchParams({
      q: query,
      page: page.toString(),
      limit: limit.toString(),
    });

    if (categoryId) {
      queryParams.append("categoryId", categoryId);
    }

    // Fazer requisição
    const response = await fetch(
      `${baseUrl}/api/search?${queryParams.toString()}`
    );

    if (!response.ok) {
      throw new Error(`Error: ${response.status}`);
    }

    // Validar dados com Zod
    const data = await response.json();
    const validated = searchResultSchema.parse(data);

    return {
      products: validated.products,
      totalResults: validated.totalResults,
      success: true,
    };
  } catch (error) {
    console.error("Erro ao buscar produtos:", error);
    return {
      products: [],
      totalResults: 0,
      success: false,
      error: error instanceof Error ? error.message : "Erro desconhecido",
    };
  }
}
```

```typescript
// app/(shop)/_components/SearchBar.tsx
"use client";

import { useState, useTransition, useEffect } from "react";
import { useRouter, useSearchParams } from "next/navigation";
import { Search, Loader2 } from "lucide-react";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import {
  CommandDialog,
  CommandInput,
  CommandList,
  CommandEmpty,
  CommandGroup,
  CommandItem,
} from "@/components/ui/command";
import { searchProducts } from "@/lib/api/client";

export function SearchBar() {
  const router = useRouter();
  const searchParams = useSearchParams();
  const [open, setOpen] = useState(false);
  const [query, setQuery] = useState("");
  const [results, setResults] = useState<
    Array<{
      id: string;
      name: string;
      price: number;
      imageUrl: string | null;
    }>
  >([]);
  const [isSearching, setIsSearching] = useState(false);
  const [isPending, startTransition] = useTransition();

  // Lidar com atalho de teclado para abrir modal
  useEffect(() => {
    const down = (e: KeyboardEvent) => {
      if (e.key === "k" && (e.metaKey || e.ctrlKey)) {
        e.preventDefault();
        setOpen((open) => !open);
      }
    };

    document.addEventListener("keydown", down);
    return () => document.removeEventListener("keydown", down);
  }, []);

  // Função de busca debounced
  useEffect(() => {
    const timer = setTimeout(async () => {
      if (query.length >= 2 && open) {
        setIsSearching(true);
        const { products, success } = await searchProducts({
          query,
          limit: 5,
        });

        if (success) {
          setResults(products);
        }
        setIsSearching(false);
      }
    }, 300);

    return () => clearTimeout(timer);
  }, [query, open]);

  // Função para submeter busca completa
  function handleSubmit(e: React.FormEvent) {
    e.preventDefault();

    if (!query.trim()) return;

    startTransition(() => {
      router.push(`/search?q=${encodeURIComponent(query.trim())}`);
      setOpen(false);
    });
  }

  // Função para navegar para produto
  function handleSelectProduct(productId: string) {
    startTransition(() => {
      router.push(`/product/${productId}`);
      setOpen(false);
    });
  }

  return (
    <>
      <div className="relative w-full max-w-sm">
        <Button
          variant="outline"
          className="relative w-full justify-start text-sm text-muted-foreground h-10"
          onClick={() => setOpen(true)}
        >
          <Search className="mr-2 h-4 w-4" />
          <span>Buscar produtos...</span>
          <kbd className="pointer-events-none absolute right-2 top-2 hidden h-6 select-none items-center gap-1 rounded border bg-muted px-1.5 font-mono text-xs font-medium opacity-100 sm:flex">
            <span className="text-xs">⌘</span>K
          </kbd>
        </Button>
      </div>

      <CommandDialog open={open} onOpenChange={setOpen}>
        <form onSubmit={handleSubmit}>
          <CommandInput
            placeholder="Buscar produtos..."
            value={query}
            onValueChange={setQuery}
          />
        </form>

        <CommandList>
          {isSearching ? (
            <div className="py-6 text-center">
              <Loader2 className="mx-auto h-6 w-6 animate-spin text-muted-foreground" />
            </div>
          ) : (
            <>
              {query.length > 0 && (
                <>
                  <CommandEmpty>Nenhum produto encontrado.</CommandEmpty>

                  {results.length > 0 && (
                    <CommandGroup heading="Produtos">
                      {results.map((product) => (
                        <CommandItem
                          key={product.id}
                          onSelect={() => handleSelectProduct(product.id)}
                        >
                          <div className="flex items-center">
                            {product.imageUrl && (
                              <div className="w-10 h-10 mr-3">
                                <img
                                  src={product.imageUrl}
                                  alt={product.name}
                                  className="w-full h-full object-cover rounded"
                                />
                              </div>
                            )}
                            <div>
                              <p>{product.name}</p>
                              <p className="text-sm text-muted-foreground">
                                R$ {product.price.toFixed(2)}
                              </p>
                            </div>
                          </div>
                        </CommandItem>
                      ))}

                      <CommandItem
                        onSelect={() => {
                          router.push(`/search?q=${encodeURIComponent(query)}`);
                          setOpen(false);
                        }}
                      >
                        <Search className="mr-2 h-4 w-4" />
                        <span>Ver todos os resultados</span>
                      </CommandItem>
                    </CommandGroup>
                  )}
                </>
              )}
            </>
          )}
        </CommandList>
      </CommandDialog>
    </>
  );
}
```

### 6. Implementação de API Routes para Client Components

```typescript
// app/api/search/route.ts
import { NextRequest, NextResponse } from "next/server";
import { db } from "@/lib/db";

export async function GET(request: NextRequest) {
  // Obter parâmetros de consulta
  const searchParams = request.nextUrl.searchParams;
  const query = searchParams.get("q");
  const page = parseInt(searchParams.get("page") || "1");
  const limit = parseInt(searchParams.get("limit") || "10");
  const categoryId = searchParams.get("categoryId");

  // Validar parâmetros
  if (!query) {
    return NextResponse.json(
      { error: "Query parameter is required" },
      { status: 400 }
    );
  }

  try {
    // Configurar paginação
    const skip = (page - 1) * limit;

    // Configurar filtro
    const where: any = {
      OR: [
        { name: { contains: query, mode: "insensitive" } },
        { description: { contains: query, mode: "insensitive" } },
      ],
      isPublished: true,
    };

    if (categoryId) {
      where.categoryId = categoryId;
    }

    // Realizar busca e contagem em paralelo
    const [products, totalResults] = await Promise.all([
      db.product.findMany({
        where,
        select: {
          id: true,
          name: true,
          slug: true,
          price: true,
          imageUrl: true,
          averageRating: true,
        },
        orderBy: {
          relevance: "desc",
        },
        skip,
        take: limit,
      }),
      db.product.count({ where }),
    ]);

    // Retornar resultados
    return NextResponse.json({
      products,
      totalResults,
      page,
      limit,
      totalPages: Math.ceil(totalResults / limit),
    });
  } catch (error) {
    console.error("Erro na API de busca:", error);
    return NextResponse.json(
      { error: "Failed to search products" },
      { status: 500 }
    );
  }
}
```

### 7. Estratégias de Cache e Revalidação

```typescript
// lib/api/config.ts
export const CACHE_TAGS = {
  products: "products",
  categories: "categories",
  orders: "orders",
  users: "users",
  settings: "settings",
  posts: "posts",
};

// Configurações de cache por entidade
export const CACHE_CONFIG = {
  products: {
    revalidate: 60 * 5, // 5 minutos
    tags: [CACHE_TAGS.products],
  },
  categories: {
    revalidate: 60 * 60, // 1 hora
    tags: [CACHE_TAGS.categories],
  },
  popularProducts: {
    revalidate: 60 * 30, // 30 minutos
    tags: [CACHE_TAGS.products],
  },
  productDetail: {
    revalidate: 60 * 10, // 10 minutos
    tags: [CACHE_TAGS.products],
  },
  homepage: {
    revalidate: 60 * 15, // 15 minutos
    tags: [CACHE_TAGS.products, CACHE_TAGS.categories, CACHE_TAGS.settings],
  },
  posts: {
    revalidate: 60 * 60, // 1 hora
    tags: [CACHE_TAGS.posts],
  },
  siteSettings: {
    revalidate: 60 * 60 * 12, // 12 horas
    tags: [CACHE_TAGS.settings],
  },
  userSpecific: {
    // Sem revalidação automática para dados específicos de usuário
    revalidate: false,
    // Sem tags - esses dados não devem ser compartilhados
  },
};
```

```typescript
// lib/api/fetch-utils.ts
import "server-only";
import { revalidateTag } from "next/cache";
import { CACHE_CONFIG, CACHE_TAGS } from "./config";

// Helper para revalidar múltiplas tags
export async function revalidateMultipleTags(tags: string[]) {
  for (const tag of tags) {
    revalidateTag(tag);
  }
}

// Helper para revalidar por entidade
export async function revalidateEntity(entity: keyof typeof CACHE_TAGS) {
  const tag = CACHE_TAGS[entity];
  if (tag) {
    revalidateTag(tag);
  }
}

// Tipos para opções de fetch
type FetchOptions = {
  cache?: "force-cache" | "no-store";
  next?: {
    revalidate?: number | false;
    tags?: string[];
  };
};

// Helper para gerar opções de fetch com base na configuração
export function getFetchOptions(
  entityType: keyof typeof CACHE_CONFIG,
  overrides?: Partial<FetchOptions>
): FetchOptions {
  const config = CACHE_CONFIG[entityType];

  return {
    next: {
      revalidate: config.revalidate,
      tags: config.tags,
    },
    ...overrides,
  };
}
```

```typescript
// lib/api/catalog.ts - Usando helpers de cache
import "server-only";
import { db } from "@/lib/db";
import { getFetchOptions } from "./fetch-utils";

// Obter categorias com configuração de cache adequada
export async function getCategories() {
  try {
    const options = getFetchOptions("categories");

    const categories = await db.category.findMany({
      where: { isActive: true },
      select: {
        id: true,
        name: true,
        slug: true,
        imageUrl: true,
      },
      orderBy: { displayOrder: "asc" },
    });

    return categories;
  } catch (error) {
    console.error("Erro ao buscar categorias:", error);
    return [];
  }
}

// Obter produto com configuração específica de cache
export async function getProduct(slug: string) {
  try {
    const options = getFetchOptions("productDetail");

    const product = await db.product.findUnique({
      where: {
        slug,
        isPublished: true,
      },
      include: {
        category: {
          select: {
            name: true,
            slug: true,
          },
        },
        images: true,
        attributes: true,
      },
    });

    return product;
  } catch (error) {
    console.error(`Erro ao buscar produto ${slug}:`, error);
    return null;
  }
}

// Obter produtos populares (cache diferente)
export async function getPopularProducts(limit: number = 8) {
  try {
    const options = getFetchOptions("popularProducts");

    const products = await db.product.findMany({
      where: {
        isPublished: true,
        isPopular: true,
      },
      select: {
        id: true,
        name: true,
        slug: true,
        price: true,
        imageUrl: true,
        averageRating: true,
      },
      orderBy: [{ sales: "desc" }, { averageRating: "desc" }],
      take: limit,
    });

    return products;
  } catch (error) {
    console.error("Erro ao buscar produtos populares:", error);
    return [];
  }
}
```

### 8. Data Fetching com SWR para Dados Dinâmicos

```typescript
// lib/hooks/useCart.ts
import { useCallback, useState } from "react";
import useSWR from "swr";
import { toast } from "@/components/ui/use-toast";

const CART_API_URL = "/api/cart";

interface CartItem {
  id: string;
  productId: string;
  name: string;
  price: number;
  quantity: number;
  imageUrl: string | null;
}

interface Cart {
  items: CartItem[];
  subtotal: number;
  totalItems: number;
}

async function fetcher(url: string) {
  const res = await fetch(url);

  if (!res.ok) {
    const error = new Error("Erro ao buscar carrinho");
    error.message = await res.text();
    throw error;
  }

  return res.json();
}

export function useCart() {
  const [isUpdating, setIsUpdating] = useState(false);

  // Configurar SWR para o carrinho
  const {
    data: cart,
    error,
    mutate,
  } = useSWR<Cart>(CART_API_URL, fetcher, {
    refreshInterval: 0, // Não atualizar automaticamente
    revalidateOnFocus: false, // Não atualizar ao focar na página
    dedupingInterval: 60000, // Deduplicar requisições em 1 minuto
  });

  // Verificar estado de carregamento
  const isLoading = !cart && !error;

  // Função para adicionar produto ao carrinho
  const addToCart = useCallback(
    async (productId: string, quantity: number = 1) => {
      try {
        setIsUpdating(true);

        // Chamar API para adicionar item
        const response = await fetch(`${CART_API_URL}/add`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({ productId, quantity }),
        });

        if (!response.ok) {
          throw new Error("Erro ao adicionar item ao carrinho");
        }

        // Atualizar cache do SWR com nova resposta
        const updatedCart = await response.json();
        mutate(updatedCart, false);

        // Notificar usuário
        toast({
          title: "Produto adicionado",
          description: `${quantity} item(s) adicionado(s) ao carrinho`,
          variant: "success",
        });

        return true;
      } catch (error) {
        console.error("Erro ao adicionar ao carrinho:", error);

        toast({
          title: "Erro",
          description:
            error instanceof Error
              ? error.message
              : "Erro ao adicionar ao carrinho",
          variant: "destructive",
        });

        return false;
      } finally {
        setIsUpdating(false);
      }
    },
    [mutate]
  );

  // Função para atualizar quantidade
  const updateQuantity = useCallback(
    async (itemId: string, quantity: number) => {
      if (quantity < 1) return removeItem(itemId);

      try {
        setIsUpdating(true);

        const response = await fetch(`${CART_API_URL}/update`, {
          method: "PUT",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({ itemId, quantity }),
        });

        if (!response.ok) {
          throw new Error("Erro ao atualizar carrinho");
        }

        const updatedCart = await response.json();
        mutate(updatedCart, false);

        return true;
      } catch (error) {
        console.error("Erro ao atualizar quantidade:", error);

        toast({
          title: "Erro",
          description: "Não foi possível atualizar o carrinho",
          variant: "destructive",
        });

        return false;
      } finally {
        setIsUpdating(false);
      }
    },
    [mutate]
  );

  // Função para remover item
  const removeItem = useCallback(
    async (itemId: string) => {
      try {
        setIsUpdating(true);

        const response = await fetch(`${CART_API_URL}/remove`, {
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({ itemId }),
        });

        if (!response.ok) {
          throw new Error("Erro ao remover item");
        }

        const updatedCart = await response.json();
        mutate(updatedCart, false);

        toast({
          title: "Item removido",
          variant: "success",
        });

        return true;
      } catch (error) {
        console.error("Erro ao remover item:", error);

        toast({
          title: "Erro",
          description: "Não foi possível remover o item",
          variant: "destructive",
        });

        return false;
      } finally {
        setIsUpdating(false);
      }
    },
    [mutate]
  );

  // Função para limpar carrinho
  const clearCart = useCallback(async () => {
    try {
      setIsUpdating(true);

      const response = await fetch(`${CART_API_URL}/clear`, {
        method: "DELETE",
      });

      if (!response.ok) {
        throw new Error("Erro ao limpar carrinho");
      }

      const emptyCart = await response.json();
      mutate(emptyCart, false);

      return true;
    } catch (error) {
      console.error("Erro ao limpar carrinho:", error);

      toast({
        title: "Erro",
        description: "Não foi possível limpar o carrinho",
        variant: "destructive",
      });

      return false;
    } finally {
      setIsUpdating(false);
    }
  }, [mutate]);

  return {
    cart,
    isLoading,
    isUpdating,
    error,
    addToCart,
    updateQuantity,
    removeItem,
    clearCart,
  };
}
```

### 9. Fetching Paralelo para Melhor Performance

```typescript
// app/(shop)/page.tsx - Home page com fetching paralelo
import { Suspense } from "react";
import { HeroSection } from "./_components/HeroSection";
import { FeaturedCategories } from "./_components/FeaturedCategories";
import { FeaturedProducts } from "./_components/FeaturedProducts";
import { NewArrivals } from "./_components/NewArrivals";
import { PopularProducts } from "./_components/PopularProducts";
import { ProductSkeleton } from "@/components/ui/product-skeleton";
import {
  getFeaturedCategories,
  getFeaturedProducts,
  getNewArrivals,
  getPopularProducts,
  getSiteSettings,
} from "@/lib/api/home";

export default async function HomePage() {
  // Fetching paralelo para melhor performance
  const [featuredCategories, featuredProducts, siteSettings] =
    await Promise.all([
      getFeaturedCategories(),
      getFeaturedProducts(),
      getSiteSettings(),
    ]);

  return (
    <div className="space-y-16 py-8">
      {/* Hero com configurações dinâmicas */}
      <HeroSection
        headline={siteSettings.heroHeadline}
        subheadline={siteSettings.heroSubheadline}
        imageUrl={siteSettings.heroImageUrl}
        buttonText={siteSettings.heroButtonText}
        buttonLink={siteSettings.heroButtonLink}
      />

      {/* Categorias em destaque */}
      <section className="container">
        <h2 className="text-3xl font-bold mb-8">Categorias</h2>
        <FeaturedCategories categories={featuredCategories} />
      </section>

      {/* Produtos em destaque */}
      <section className="container">
        <h2 className="text-3xl font-bold mb-8">Destaques</h2>
        <FeaturedProducts products={featuredProducts} />
      </section>

      {/* Novidades com Suspense Boundary */}
      <section className="container">
        <h2 className="text-3xl font-bold mb-8">Novidades</h2>
        <Suspense fallback={<ProductSkeleton count={4} />}>
          <NewArrivalsContainer />
        </Suspense>
      </section>

      {/* Produtos Populares com Suspense Boundary */}
      <section className="container">
        <h2 className="text-3xl font-bold mb-8">Mais Populares</h2>
        <Suspense fallback={<ProductSkeleton count={4} />}>
          <PopularProductsContainer />
        </Suspense>
      </section>
    </div>
  );
}

// Componentes para Suspense
async function NewArrivalsContainer() {
  // Pode esperar por promessas diretamente aqui
  const newArrivals = await getNewArrivals();
  return <NewArrivals products={newArrivals} />;
}

async function PopularProductsContainer() {
  // Pode esperar por promessas diretamente aqui
  const popularProducts = await getPopularProducts();
  return <PopularProducts products={popularProducts} />;
}
```

## Anti-padrões a Evitar

1. **❌ Fetching de Dados em Client Components Quando Possível no Servidor**

   ```typescript
   // Incorreto: Data fetching desnecessário em cliente
   'use client';

   export default function ProductsPage() {
     const [products, setProducts] = useState([]);

     useEffect(() => {
       // Fetching que poderia ser feito no servidor
       fetch('/api/products')
         .then(res => res.json())
         .then(data => setProducts(data));
     }, []);

     return (...)
   }
   ```

   ✅ Correto: Mover fetching para Server Components sempre que possível

2. **❌ Não Configurar Estratégias de Cache Adequadas**

   ```typescript
   // Incorreto: Usando configuração padrão para tudo
   async function getData() {
     // Sem configuração de cache - reverte para defaults
     const product = await db.product.findUnique({
       where: { id },
     });

     return product;
   }
   ```

   ✅ Correto: Configurar estratégias de cache específicas para cada tipo de dado

3. **❌ Fetching Dentro de Loops**

   ```typescript
   // Incorreto: Fetching sequencial em loop
   async function getProductsWithCategories() {
     const products = await db.products.findMany();

     // Fetching sequencial para cada produto - ruim!
     for (const product of products) {
       product.category = await db.category.findUnique({
         where: { id: product.categoryId },
       });
     }

     return products;
   }
   ```

   ✅ Correto: Usar includes em ORMs ou fetching paralelo com Promise.all

4. **❌ Não Tratar Erros de Fetching Adequadamente**

   ```typescript
   // Incorreto: Sem tratamento de erros
   export default async function ProductPage({ params }) {
     // Sem try/catch ou fallback
     const product = await getProduct(params.id);

     return <ProductDetails product={product} />;
   }
   ```

   ✅ Correto: Tratar erros e fornecer fallbacks ou redirecionamentos

5. **❌ Revalidação Excessiva ou Insuficiente**
   ```typescript
   // Incorreto: Invalidando cache de forma ampla demais
   export async function createComment(formData: FormData) {
     // Processar comentário...

     // Invalidar cache de forma muito ampla
     revalidatePath("/");
   }
   ```
   ✅ Correto: Invalidar apenas as rotas ou tags necessárias

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals"],
  "rules": {
    "react-hooks/exhaustive-deps": "error",
    "no-unused-vars": ["warn", { "argsIgnorePattern": "^_" }],
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/no-unused-vars": ["warn", { "argsIgnorePattern": "^_" }]
  }
}
```

## Quando Aplicar

- Para qualquer componente que necessita de dados externos
- Em páginas que exigem SEO e conteúdo pré-renderizado
- Para operações que requerem controle fino de cache e revalidação
- Quando a performance de carregamento inicial é crítica
- Para manipulação de dados dinâmicos que requerem atualizações em tempo real
- Em dashboards administrativos com múltiplas fontes de dados
