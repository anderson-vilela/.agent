# Padrão para Client Components no Next.js App Router

## Descrição

Client Components são componentes React interativos que são renderizados no navegador (cliente), permitindo o uso de estados, efeitos e eventos de interação do usuário. Este documento define padrões para implementação eficiente de Client Components no Next.js com App Router, estabelecendo práticas para gerenciamento de estado, otimização de performance e interatividade.

## Princípios Fundamentais

1. **Uso Seletivo**: Utilizar Client Components apenas quando necessário para interatividade
2. **Fronteira Cliente-Servidor**: Estabelecer limites claros entre Server e Client Components
3. **Otimização de Bundles**: Minimizar o tamanho do JavaScript enviado ao cliente
4. **Composição Eficiente**: Combinar Server e Client Components para melhor performance
5. **Estado Gerenciável**: Organizar estado de forma modular e previsível

## Implementação de Client Components

### 1. Definição Básica com diretiva 'use client'

```typescript
// app/_components/Counter.tsx
"use client";

import { useState } from "react";
import { Button } from "@/components/ui/button";

export function Counter({ initialValue = 0 }: { initialValue?: number }) {
  const [count, setCount] = useState(initialValue);

  return (
    <div className="flex items-center space-x-4">
      <Button
        variant="outline"
        size="sm"
        onClick={() => setCount((prev) => prev - 1)}
      >
        -
      </Button>

      <span className="font-medium text-lg">{count}</span>

      <Button
        variant="outline"
        size="sm"
        onClick={() => setCount((prev) => prev + 1)}
      >
        +
      </Button>
    </div>
  );
}
```

### 2. Composição com Server Components

```typescript
// app/products/[id]/page.tsx (Server Component)
import { Suspense } from "react";
import { getProduct, getProductReviews } from "@/lib/api/products";
import { ProductDetails } from "./_components/ProductDetails"; // Server Component
import { ReviewForm } from "./_components/ReviewForm"; // Client Component
import { ProductReviews } from "./_components/ProductReviews"; // Server Component
import { ReviewSkeleton } from "@/components/skeletons/ReviewSkeleton";

export default async function ProductPage({
  params,
}: {
  params: { id: string };
}) {
  // Fetch data on the server
  const product = await getProduct(params.id);

  if (!product) {
    return notFound();
  }

  return (
    <div className="container mx-auto py-8">
      <ProductDetails product={product} />

      <div className="mt-12">
        <h2 className="text-2xl font-bold mb-6">Deixe sua Avaliação</h2>
        {/* Client Component com props estáticas */}
        <ReviewForm productId={params.id} />
      </div>

      <div className="mt-12">
        <h2 className="text-2xl font-bold mb-6">Avaliações</h2>
        {/* Carregamento independente dos reviews */}
        <Suspense fallback={<ReviewSkeleton count={3} />}>
          <ProductReviews productId={params.id} />
        </Suspense>
      </div>
    </div>
  );
}

// app/products/[id]/_components/ReviewForm.tsx (Client Component)
("use client");

import { useState } from "react";
import { useForm } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { z } from "zod";
import { submitReview } from "@/lib/actions/reviews";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { StarRating } from "@/components/ui/star-rating";
import { toast } from "@/components/ui/use-toast";

const reviewSchema = z.object({
  rating: z.number().min(1).max(5),
  title: z.string().min(3, "Título muito curto").max(100),
  comment: z.string().min(10, "Comentário muito curto").max(500),
});

type ReviewFormValues = z.infer<typeof reviewSchema>;

export function ReviewForm({ productId }: { productId: string }) {
  const [isSubmitting, setIsSubmitting] = useState(false);

  const {
    register,
    handleSubmit,
    reset,
    setValue,
    formState: { errors },
  } = useForm<ReviewFormValues>({
    resolver: zodResolver(reviewSchema),
    defaultValues: {
      rating: 0,
      title: "",
      comment: "",
    },
  });

  async function onSubmit(data: ReviewFormValues) {
    try {
      setIsSubmitting(true);

      // Chama Server Action para submeter review
      await submitReview(productId, data);

      toast({
        title: "Avaliação enviada!",
        description: "Sua avaliação foi enviada com sucesso.",
        variant: "success",
      });

      reset();
    } catch (error) {
      toast({
        title: "Erro ao enviar avaliação",
        description:
          error instanceof Error ? error.message : "Ocorreu um erro inesperado",
        variant: "destructive",
      });
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-6">
      <div className="space-y-2">
        <label htmlFor="rating" className="font-medium">
          Avaliação
        </label>
        <StarRating
          value={form.watch("rating")}
          onChange={(value) => setValue("rating", value)}
        />
        {errors.rating && (
          <p className="text-sm text-red-500">{errors.rating.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="title" className="font-medium">
          Título
        </label>
        <Input
          id="title"
          {...register("title")}
          placeholder="Resumo da sua experiência"
        />
        {errors.title && (
          <p className="text-sm text-red-500">{errors.title.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="comment" className="font-medium">
          Comentário
        </label>
        <Textarea
          id="comment"
          {...register("comment")}
          placeholder="Compartilhe sua experiência com o produto"
          rows={4}
        />
        {errors.comment && (
          <p className="text-sm text-red-500">{errors.comment.message}</p>
        )}
      </div>

      <Button type="submit" disabled={isSubmitting}>
        {isSubmitting ? "Enviando..." : "Enviar Avaliação"}
      </Button>
    </form>
  );
}
```

### 3. Interoperabilidade entre Componentes

```typescript
// Padrão: Passar dados de Server Components para Client Components

// app/dashboard/analytics/page.tsx (Server Component)
import { getAnalyticsData } from "@/lib/analytics";
import { AnalyticsChart } from "./_components/AnalyticsChart"; // Client Component

export default async function AnalyticsPage() {
  // Busca dados no servidor
  const analyticsData = await getAnalyticsData();

  // Serializa os dados para passar ao Client Component
  const serializedData = {
    labels: analyticsData.dates,
    datasets: [
      {
        label: "Visitantes",
        data: analyticsData.visitors,
      },
      {
        label: "Conversões",
        data: analyticsData.conversions,
      },
    ],
  };

  return (
    <div className="container py-8">
      <h1 className="text-3xl font-bold mb-8">Análise de Desempenho</h1>

      {/* Passa dados serializados para o Client Component */}
      <AnalyticsChart data={serializedData} />
    </div>
  );
}

// app/dashboard/analytics/_components/AnalyticsChart.tsx (Client Component)
("use client");

import { useEffect, useRef } from "react";
import Chart from "chart.js/auto";

interface ChartData {
  labels: string[];
  datasets: {
    label: string;
    data: number[];
    backgroundColor?: string;
    borderColor?: string;
  }[];
}

export function AnalyticsChart({ data }: { data: ChartData }) {
  const chartRef = useRef<HTMLCanvasElement>(null);
  const chartInstance = useRef<Chart | null>(null);

  useEffect(() => {
    if (!chartRef.current) return;

    // Limpa chart anterior se existente
    if (chartInstance.current) {
      chartInstance.current.destroy();
    }

    // Cria novo chart
    const ctx = chartRef.current.getContext("2d");

    if (ctx) {
      chartInstance.current = new Chart(ctx, {
        type: "line",
        data: {
          labels: data.labels,
          datasets: data.datasets.map((dataset, index) => ({
            ...dataset,
            backgroundColor:
              index === 0
                ? "rgba(59, 130, 246, 0.2)"
                : "rgba(249, 115, 22, 0.2)",
            borderColor:
              index === 0 ? "rgba(59, 130, 246, 1)" : "rgba(249, 115, 22, 1)",
            borderWidth: 2,
            tension: 0.3,
          })),
        },
        options: {
          responsive: true,
          plugins: {
            legend: {
              position: "top",
            },
            tooltip: {
              mode: "index",
              intersect: false,
            },
          },
          scales: {
            y: {
              beginAtZero: true,
            },
          },
        },
      });
    }

    // Cleanup na desmontagem
    return () => {
      if (chartInstance.current) {
        chartInstance.current.destroy();
      }
    };
  }, [data]);

  return (
    <div className="w-full bg-white p-4 rounded-lg shadow">
      <canvas ref={chartRef} />
    </div>
  );
}
```

### 4. Gestão de Estado com Context API

```typescript
// app/_providers/CartProvider.tsx
"use client";

import React, { createContext, useContext, useState, useEffect } from "react";

interface Product {
  id: string;
  name: string;
  price: number;
  quantity: number;
  imageUrl: string;
}

interface CartContextType {
  items: Product[];
  totalItems: number;
  totalPrice: number;
  addItem: (product: Omit<Product, "quantity">) => void;
  removeItem: (productId: string) => void;
  updateQuantity: (productId: string, quantity: number) => void;
  clearCart: () => void;
}

const CartContext = createContext<CartContextType | undefined>(undefined);

export function CartProvider({ children }: { children: React.ReactNode }) {
  const [items, setItems] = useState<Product[]>([]);

  // Calcula totais derivados do estado
  const totalItems = items.reduce((total, item) => total + item.quantity, 0);
  const totalPrice = items.reduce(
    (total, item) => total + item.price * item.quantity,
    0
  );

  // Carrega carrinho do localStorage no client-side
  useEffect(() => {
    try {
      const savedCart = localStorage.getItem("cart");
      if (savedCart) {
        setItems(JSON.parse(savedCart));
      }
    } catch (error) {
      console.error("Erro ao carregar carrinho do localStorage:", error);
    }
  }, []);

  // Persiste carrinho no localStorage quando muda
  useEffect(() => {
    try {
      localStorage.setItem("cart", JSON.stringify(items));
    } catch (error) {
      console.error("Erro ao salvar carrinho no localStorage:", error);
    }
  }, [items]);

  function addItem(product: Omit<Product, "quantity">) {
    setItems((prevItems) => {
      const exists = prevItems.find((item) => item.id === product.id);

      if (exists) {
        // Incrementa quantidade se o produto já existe
        return prevItems.map((item) =>
          item.id === product.id
            ? { ...item, quantity: item.quantity + 1 }
            : item
        );
      }

      // Adiciona novo produto com quantidade 1
      return [...prevItems, { ...product, quantity: 1 }];
    });
  }

  function removeItem(productId: string) {
    setItems((prevItems) => prevItems.filter((item) => item.id !== productId));
  }

  function updateQuantity(productId: string, quantity: number) {
    if (quantity < 1) return;

    setItems((prevItems) =>
      prevItems.map((item) =>
        item.id === productId ? { ...item, quantity } : item
      )
    );
  }

  function clearCart() {
    setItems([]);
  }

  const value = {
    items,
    totalItems,
    totalPrice,
    addItem,
    removeItem,
    updateQuantity,
    clearCart,
  };

  return <CartContext.Provider value={value}>{children}</CartContext.Provider>;
}

// Hook customizado para usar o contexto
export function useCart() {
  const context = useContext(CartContext);

  if (context === undefined) {
    throw new Error("useCart deve ser usado dentro de um CartProvider");
  }

  return context;
}
```

### 5. Utilizando Server Actions em Client Components

```typescript
// lib/actions/products.ts (Server Action)
"use server";

import { revalidatePath } from "next/cache";
import { db } from "@/lib/db";
import { z } from "zod";

const productSchema = z.object({
  name: z.string().min(3).max(100),
  description: z.string().min(10).max(1000),
  price: z.number().positive(),
  categoryId: z.string().uuid(),
});

export async function addProduct(formData: FormData) {
  try {
    // Extrai e valida dados
    const validatedFields = productSchema.parse({
      name: formData.get("name"),
      description: formData.get("description"),
      price: Number(formData.get("price")),
      categoryId: formData.get("categoryId"),
    });

    // Cria produto no banco
    const product = await db.product.create({
      data: validatedFields,
    });

    // Revalida caminhos afetados
    revalidatePath("/products");
    revalidatePath(`/categories/${validatedFields.categoryId}`);

    return { success: true, data: product };
  } catch (error) {
    if (error instanceof z.ZodError) {
      return { success: false, error: error.format() };
    }

    return {
      success: false,
      error: "Falha ao adicionar produto. Tente novamente.",
    };
  }
}

// app/admin/products/new/_components/NewProductForm.tsx (Client Component)
("use client");

import { useTransition } from "react";
import { useRouter } from "next/navigation";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { addProduct } from "@/lib/actions/products";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Select } from "@/components/ui/select";
import { toast } from "@/components/ui/use-toast";

const productSchema = z.object({
  name: z.string().min(3, "Nome deve ter pelo menos 3 caracteres").max(100),
  description: z
    .string()
    .min(10, "Descrição deve ter pelo menos 10 caracteres")
    .max(1000),
  price: z.number().positive("Preço deve ser positivo"),
  categoryId: z.string().uuid("Categoria inválida"),
});

type ProductFormValues = z.infer<typeof productSchema>;

export function NewProductForm({
  categories,
}: {
  categories: { id: string; name: string }[];
}) {
  const router = useRouter();
  const [isPending, startTransition] = useTransition();

  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<ProductFormValues>({
    resolver: zodResolver(productSchema),
  });

  async function onSubmit(data: ProductFormValues) {
    // Cria FormData para enviar para o Server Action
    const formData = new FormData();

    // Adiciona campos ao FormData
    formData.append("name", data.name);
    formData.append("description", data.description);
    formData.append("price", data.price.toString());
    formData.append("categoryId", data.categoryId);

    // Usa React useTransition para indicar estado de loading
    startTransition(async () => {
      const result = await addProduct(formData);

      if (result.success) {
        toast({
          title: "Produto adicionado",
          description: "Produto criado com sucesso!",
          variant: "success",
        });

        // Redireciona para a lista de produtos
        router.push("/admin/products");
      } else {
        toast({
          title: "Erro ao adicionar produto",
          description:
            typeof result.error === "string"
              ? result.error
              : "Verifique os dados e tente novamente",
          variant: "destructive",
        });
      }
    });
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-6">
      <div className="space-y-2">
        <label htmlFor="name" className="text-sm font-medium">
          Nome do Produto
        </label>
        <Input id="name" {...register("name")} placeholder="Nome do produto" />
        {errors.name && (
          <p className="text-sm text-red-500">{errors.name.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="description" className="text-sm font-medium">
          Descrição
        </label>
        <Textarea
          id="description"
          {...register("description")}
          placeholder="Descrição detalhada do produto"
          rows={4}
        />
        {errors.description && (
          <p className="text-sm text-red-500">{errors.description.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="price" className="text-sm font-medium">
          Preço
        </label>
        <Input
          id="price"
          type="number"
          step="0.01"
          {...register("price", { valueAsNumber: true })}
          placeholder="0.00"
        />
        {errors.price && (
          <p className="text-sm text-red-500">{errors.price.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="categoryId" className="text-sm font-medium">
          Categoria
        </label>
        <Select id="categoryId" {...register("categoryId")}>
          <option value="">Selecione uma categoria</option>
          {categories.map((category) => (
            <option key={category.id} value={category.id}>
              {category.name}
            </option>
          ))}
        </Select>
        {errors.categoryId && (
          <p className="text-sm text-red-500">{errors.categoryId.message}</p>
        )}
      </div>

      <Button type="submit" disabled={isPending} className="w-full">
        {isPending ? "Adicionando..." : "Adicionar Produto"}
      </Button>
    </form>
  );
}
```

### 6. Reutilização de State com Custom Hooks

```typescript
// lib/hooks/useLocalStorage.ts
"use client";

import { useState, useEffect } from "react";

export function useLocalStorage<T>(key: string, initialValue: T) {
  // Estado para armazenar nosso valor
  const [storedValue, setStoredValue] = useState<T>(initialValue);

  // Inicializa com valor do localStorage (somente no lado cliente)
  useEffect(() => {
    try {
      if (typeof window !== "undefined") {
        const item = window.localStorage.getItem(key);
        setStoredValue(item ? JSON.parse(item) : initialValue);
      }
    } catch (error) {
      console.error(`Erro ao buscar ${key} do localStorage:`, error);
      setStoredValue(initialValue);
    }
  }, [key, initialValue]);

  // Função para atualizar o valor e salvar no localStorage
  const setValue = (value: T | ((val: T) => T)) => {
    try {
      // Verifica se value é uma função e aplica ao state atual
      const valueToStore =
        value instanceof Function ? value(storedValue) : value;

      // Salva no state
      setStoredValue(valueToStore);

      // Salva no localStorage (somente cliente)
      if (typeof window !== "undefined") {
        window.localStorage.setItem(key, JSON.stringify(valueToStore));
      }
    } catch (error) {
      console.error(`Erro ao salvar ${key} no localStorage:`, error);
    }
  };

  return [storedValue, setValue] as const;
}
```

```typescript
// app/_components/ThemeToggle.tsx
"use client";

import { useEffect } from "react";
import { useLocalStorage } from "@/lib/hooks/useLocalStorage";
import { Moon, Sun } from "lucide-react";
import { Button } from "@/components/ui/button";

export function ThemeToggle() {
  const [theme, setTheme] = useLocalStorage<"light" | "dark">("theme", "light");

  // Aplica o tema quando mudar
  useEffect(() => {
    const root = window.document.documentElement;

    if (theme === "dark") {
      root.classList.add("dark");
    } else {
      root.classList.remove("dark");
    }
  }, [theme]);

  function toggleTheme() {
    setTheme((prevTheme) => (prevTheme === "light" ? "dark" : "light"));
  }

  return (
    <Button
      variant="ghost"
      size="icon"
      onClick={toggleTheme}
      aria-label={`Alternar para modo ${
        theme === "light" ? "escuro" : "claro"
      }`}
    >
      {theme === "light" ? (
        <Moon className="h-5 w-5" />
      ) : (
        <Sun className="h-5 w-5" />
      )}
    </Button>
  );
}
```

## Padrões de Otimização

### Uso de React.memo para Componentes Pesados

```typescript
// components/data-table/DataTable.tsx
"use client";

import React from "react";
import {
  useReactTable,
  getCoreRowModel,
  getPaginationRowModel,
  getSortedRowModel,
  getFilteredRowModel,
  ColumnDef,
  SortingState,
  VisibilityState,
} from "@tanstack/react-table";

interface DataTableProps<TData, TValue> {
  columns: ColumnDef<TData, TValue>[];
  data: TData[];
  defaultSort?: SortingState;
}

// Utilizando React.memo para evitar re-renders desnecessários
export const DataTable = React.memo(function DataTable<TData, TValue>({
  columns,
  data,
  defaultSort = [],
}: DataTableProps<TData, TValue>) {
  const [sorting, setSorting] = React.useState<SortingState>(defaultSort);
  const [columnVisibility, setColumnVisibility] =
    React.useState<VisibilityState>({});
  const [rowSelection, setRowSelection] = React.useState({});
  const [globalFilter, setGlobalFilter] = React.useState("");

  const table = useReactTable({
    data,
    columns,
    getCoreRowModel: getCoreRowModel(),
    getPaginationRowModel: getPaginationRowModel(),
    getSortedRowModel: getSortedRowModel(),
    getFilteredRowModel: getFilteredRowModel(),
    onSortingChange: setSorting,
    onColumnVisibilityChange: setColumnVisibility,
    onRowSelectionChange: setRowSelection,
    onGlobalFilterChange: setGlobalFilter,
    state: {
      sorting,
      columnVisibility,
      rowSelection,
      globalFilter,
    },
  });

  // Renderização da tabela...
  return <div className="space-y-4">{/* Implementação da tabela */}</div>;
});
```

### Lazy Loading com dynamic imports

```typescript
// app/dashboard/_components/Analytics.tsx
"use client";

import dynamic from "next/dynamic";
import { Suspense } from "react";
import { Loader2 } from "lucide-react";

// Import dinâmico com lazy loading para o componente de gráficos
const Chart = dynamic(() => import("@/components/charts/Chart"), {
  loading: () => (
    <div className="h-80 flex items-center justify-center">
      <Loader2 className="h-8 w-8 animate-spin text-muted-foreground" />
    </div>
  ),
  ssr: false, // Previne SSR para bibliotecas que dependem do navegador
});

export function Analytics({ data }) {
  return (
    <div className="rounded-lg border p-6">
      <h2 className="text-xl font-semibold mb-4">Análise de Desempenho</h2>
      <div className="h-80">
        <Chart data={data} />
      </div>
    </div>
  );
}
```

### Otimização com useCallback e useMemo

```typescript
// app/_components/FilterableList.tsx
"use client";

import { useState, useMemo, useCallback } from "react";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";

interface Item {
  id: string;
  name: string;
  category: string;
}

interface FilterableListProps {
  items: Item[];
  onItemSelect: (item: Item) => void;
}

export function FilterableList({ items, onItemSelect }: FilterableListProps) {
  const [searchTerm, setSearchTerm] = useState("");
  const [categoryFilter, setCategoryFilter] = useState("");

  // Filtragem memoizada para prevenir recálculos desnecessários
  const filteredItems = useMemo(() => {
    return items.filter((item) => {
      const matchesSearch = item.name
        .toLowerCase()
        .includes(searchTerm.toLowerCase());
      const matchesCategory =
        !categoryFilter || item.category === categoryFilter;
      return matchesSearch && matchesCategory;
    });
  }, [items, searchTerm, categoryFilter]);

  // Função estável entre renders para manipular seleção
  const handleItemClick = useCallback(
    (item: Item) => {
      onItemSelect(item);
    },
    [onItemSelect]
  );

  // Lista de categorias únicas
  const categories = useMemo(() => {
    return Array.from(new Set(items.map((item) => item.category)));
  }, [items]);

  return (
    <div className="space-y-4">
      <div className="flex gap-2">
        <Input
          placeholder="Buscar itens..."
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          className="flex-1"
        />

        <select
          value={categoryFilter}
          onChange={(e) => setCategoryFilter(e.target.value)}
          className="border rounded px-3 py-2"
        >
          <option value="">Todas categorias</option>
          {categories.map((category) => (
            <option key={category} value={category}>
              {category}
            </option>
          ))}
        </select>
      </div>

      <div className="border rounded divide-y">
        {filteredItems.length === 0 ? (
          <p className="p-4 text-center text-muted-foreground">
            Nenhum item encontrado
          </p>
        ) : (
          filteredItems.map((item) => (
            <button
              key={item.id}
              className="w-full text-left p-4 hover:bg-muted/50 transition-colors"
              onClick={() => handleItemClick(item)}
            >
              <div className="font-medium">{item.name}</div>
              <div className="text-sm text-muted-foreground">
                {item.category}
              </div>
            </button>
          ))
        )}
      </div>
    </div>
  );
}
```

## Anti-padrões a Evitar

1. **❌ Uso Excessivo de Client Components**

   ```typescript
   // Incorreto: Componente inteiro marcado como Client quando apenas parte precisa ser interativa
   "use client";

   export default function ProductsPage() {
     const products = await fetchProducts(); // Erro: não pode usar await no top-level
     // ...
   }
   ```

   ✅ Correto: Dividir em Server Component para fetch e Client Component para interatividade

2. **❌ Uso Indevido de useEffect**

   ```typescript
   // Incorreto: Carregamento de dados via useEffect em vez de Server Component
   "use client";

   import { useEffect, useState } from "react";

   export function ProductList() {
     const [products, setProducts] = useState([]);
     const [loading, setLoading] = useState(true);

     useEffect(() => {
       // Fetching dados no cliente
       fetch("/api/products")
         .then((res) => res.json())
         .then((data) => {
           setProducts(data);
           setLoading(false);
         });
     }, []);

     if (loading) return <div>Carregando...</div>;

     return (
       <div>
         {products.map((product) => (
           <div key={product.id}>{product.name}</div>
         ))}
       </div>
     );
   }
   ```

   ✅ Correto: Usar Server Components para busca inicial de dados

3. **❌ Propagação Excessiva de Props**

   ```typescript
   // Incorreto: Prop drilling através de múltiplos níveis
   function ParentComponent({ user }) {
     return (
       <div>
         <Header user={user} />
         <Main user={user} />
         <Footer user={user} />
       </div>
     );
   }

   function Main({ user }) {
     return (
       <div>
         <Sidebar user={user} />
         <Content user={user} />
       </div>
     );
   }

   function Content({ user }) {
     return (
       <div>
         <UserInfo user={user} />
       </div>
     );
   }
   ```

   ✅ Correto: Usar Context API para estado compartilhado entre componentes distantes

4. **❌ Reutilização Inadequada de Instâncias**

   ```typescript
   // Incorreto: Instância de objeto recreada a cada render
   function SearchForm() {
     const [query, setQuery] = useState('');

     // Problema: objeto options recriado a cada render
     const options = {
       caseSensitive: false,
       fullWord: true,
     };

     return (
       // JSX...
     );
   }
   ```

   ✅ Correto: Usar useMemo para memoizar objetos estáveis entre renders

5. **❌ Não Utilizando Ferramentas de Otimização**
   ```typescript
   // Incorreto: Componente pesado sem memoização
   function LargeDataTable({ data, onRowClick }) {
     // Sem memoização, toda a lógica é re-executada em cada render
     const processedData = processLargeData(data);

     return <table>{/* Renderização da tabela... */}</table>;
   }
   ```
   ✅ Correto: Usar React.memo, useMemo e useCallback para otimizar performance

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals", "plugin:react-hooks/recommended"],
  "rules": {
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "react/jsx-key": "error",
    "react/jsx-no-undef": "error",
    "react/jsx-uses-react": "error",
    "react/jsx-uses-vars": "error",
    "no-unused-vars": "warn",
    "no-console": ["warn", { "allow": ["warn", "error"] }]
  }
}
```

## Quando Aplicar

- Para componentes que requerem interatividade do usuário (formulários, dropdowns, etc.)
- Quando precisar utilizar hooks do React (useState, useEffect, etc.)
- Para implementar manipuladores de eventos (onClick, onChange, etc.)
- Em componentes que necessitam acessar APIs exclusivas do navegador
- Para integrações com bibliotecas que requerem acesso à DOM ou APIs do navegador
- Quando precisar manter estado local que não afeta o renderização do servidor
