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

## Gestão de Estado Avançada

### 7. Gerenciamento de Estado com Zustand

```typescript
// lib/stores/useCartStore.ts
"use client";

import { create } from "zustand";
import { persist, createJSONStorage } from "zustand/middleware";

interface Product {
  id: string;
  name: string;
  price: number;
  imageUrl: string;
}

interface CartItem extends Product {
  quantity: number;
}

interface CartState {
  items: CartItem[];
  totalItems: number;
  totalPrice: number;
  addItem: (product: Product) => void;
  removeItem: (productId: string) => void;
  updateQuantity: (productId: string, quantity: number) => void;
  clearCart: () => void;
}

export const useCartStore = create<CartState>()(
  persist(
    (set, get) => ({
      items: [],

      // Valores calculados derivados do estado
      totalItems: 0,
      totalPrice: 0,

      // Ações para modificar o estado
      addItem: (product) => {
        const currentItems = get().items;
        const existingItem = currentItems.find(
          (item) => item.id === product.id
        );

        if (existingItem) {
          // Atualiza quantidade se o item já existe
          const updatedItems = currentItems.map((item) =>
            item.id === product.id
              ? { ...item, quantity: item.quantity + 1 }
              : item
          );

          set((state) => ({
            items: updatedItems,
            totalItems: state.totalItems + 1,
            totalPrice: state.totalPrice + product.price,
          }));
        } else {
          // Adiciona novo item
          const newItem = { ...product, quantity: 1 };

          set((state) => ({
            items: [...state.items, newItem],
            totalItems: state.totalItems + 1,
            totalPrice: state.totalPrice + product.price,
          }));
        }
      },

      removeItem: (productId) => {
        const currentItems = get().items;
        const itemToRemove = currentItems.find((item) => item.id === productId);

        if (!itemToRemove) return;

        set((state) => ({
          items: state.items.filter((item) => item.id !== productId),
          totalItems: state.totalItems - itemToRemove.quantity,
          totalPrice:
            state.totalPrice - itemToRemove.price * itemToRemove.quantity,
        }));
      },

      updateQuantity: (productId, quantity) => {
        if (quantity < 1) {
          get().removeItem(productId);
          return;
        }

        const currentItems = get().items;
        const itemToUpdate = currentItems.find((item) => item.id === productId);

        if (!itemToUpdate) return;

        const quantityDiff = quantity - itemToUpdate.quantity;

        set((state) => ({
          items: state.items.map((item) =>
            item.id === productId ? { ...item, quantity } : item
          ),
          totalItems: state.totalItems + quantityDiff,
          totalPrice: state.totalPrice + itemToUpdate.price * quantityDiff,
        }));
      },

      clearCart: () => set({ items: [], totalItems: 0, totalPrice: 0 }),
    }),
    {
      name: "cart-storage", // nome para armazenamento no localStorage
      storage: createJSONStorage(() => localStorage),
    }
  )
);
```

#### Exemplo de uso do store em componentes:

```typescript
// app/(shop)/_components/AddToCartButton.tsx
"use client";

import { useState } from "react";
import { Button } from "@/components/ui/button";
import { useCartStore } from "@/lib/stores/useCartStore";
import { toast } from "@/components/ui/use-toast";

interface AddToCartButtonProps {
  product: {
    id: string;
    name: string;
    price: number;
    imageUrl: string;
  };
}

export function AddToCartButton({ product }: AddToCartButtonProps) {
  const [isAdding, setIsAdding] = useState(false);
  const addItem = useCartStore((state) => state.addItem);

  function handleAddToCart() {
    setIsAdding(true);

    setTimeout(() => {
      addItem(product);

      toast({
        title: "Produto adicionado",
        description: `${product.name} foi adicionado ao carrinho`,
        variant: "success",
      });

      setIsAdding(false);
    }, 500); // Simulação de delay para feedback visual
  }

  return (
    <Button onClick={handleAddToCart} disabled={isAdding} className="w-full">
      {isAdding ? "Adicionando..." : "Adicionar ao Carrinho"}
    </Button>
  );
}
```

```typescript
// app/(shop)/_components/CartWidget.tsx
"use client";

import { ShoppingCart } from "lucide-react";
import { Badge } from "@/components/ui/badge";
import { Button } from "@/components/ui/button";
import { useCartStore } from "@/lib/stores/useCartStore";

export function CartWidget() {
  const totalItems = useCartStore((state) => state.totalItems);

  return (
    <Button variant="ghost" size="icon" aria-label="Carrinho de compras">
      <div className="relative">
        <ShoppingCart className="h-6 w-6" />
        {totalItems > 0 && (
          <Badge
            variant="destructive"
            className="absolute -top-2 -right-2 h-5 w-5 flex items-center justify-center p-0 text-xs"
          >
            {totalItems > 99 ? "99+" : totalItems}
          </Badge>
        )}
      </div>
    </Button>
  );
}
```

### Vantagens do Zustand sobre Context API

1. **API Mais Simples**: Menos boilerplate e mais intuitivo que Context + useReducer
2. **Performance Superior**: Atualizações seletivas via selectors para evitar re-renders desnecessários
3. **Sem Providers**: Não precisa envolver componentes em providers, facilitando o acesso ao estado
4. **Middleware Integrado**: Sistema de middleware para persistência, imutabilidade e devtools
5. **TypeScript Nativo**: Excelente suporte para TypeScript com inferência de tipos
6. **Bundle Size Pequeno**: Menos de 1KB (minificado + gzipped)
7. **DevTools**: Integração fácil com Redux DevTools
8. **Compatibilidade com React 18**: Suporte completo para Concurrent Mode e Suspense

### Escolhendo entre Context API e Zustand

| Context API                                  | Zustand                                                |
| -------------------------------------------- | ------------------------------------------------------ |
| Embutido no React                            | Biblioteca externa                                     |
| Ideal para temas, autenticação, preferências | Ideal para estado complexo, com múltiplas atualizações |
| Melhor para estado raramente atualizado      | Melhor para estado frequentemente atualizado           |
| Pode causar re-renders desnecessários        | Atualizações seletivas para evitar re-renders          |
| Precisa de providers aninhados               | Sem providers necessários                              |
| Sem persistência nativa                      | Persistência integrada via middleware                  |

### Zustand com Server Components

Como Zustand é utilizado no lado do cliente, certifique-se de usar a diretiva 'use client' quando necessário:

```typescript
// app/_components/CartSummary.tsx
"use client";

import { useCartStore } from "@/lib/stores/useCartStore";

export function CartSummary() {
  const { items, totalItems, totalPrice } = useCartStore();

  if (totalItems === 0) {
    return <p>Seu carrinho está vazio</p>;
  }

  return (
    <div className="space-y-4">
      <h2 className="text-xl font-bold">Resumo do Carrinho</h2>
      <p>{totalItems} item(s) no carrinho</p>
      <p className="text-lg font-semibold">Total: R$ {totalPrice.toFixed(2)}</p>
    </div>
  );
}
```

### Integração com React Query para Dados Externos

Para gerenciamento de estado do servidor com React Query e Zustand:

```typescript
// lib/stores/useUserStore.ts
import { create } from "zustand";
import { User } from "@/types";

interface UserState {
  user: User | null;
  setUser: (user: User | null) => void;
}

export const useUserStore = create<UserState>((set) => ({
  user: null,
  setUser: (user) => set({ user }),
}));
```

```typescript
// app/(authenticated)/_components/ProfileData.tsx
"use client";

import { useQuery } from "@tanstack/react-query";
import { useUserStore } from "@/lib/stores/useUserStore";
import { fetchUserProfile } from "@/lib/api/users";

export function ProfileData() {
  const { user, setUser } = useUserStore();

  const { data, isLoading, error } = useQuery({
    queryKey: ["userProfile"],
    queryFn: fetchUserProfile,
    onSuccess: (data) => {
      setUser(data);
    },
  });

  if (isLoading) return <div>Carregando...</div>;
  if (error) return <div>Erro ao carregar perfil</div>;

  return (
    <div>
      <h2>Perfil de {user?.name}</h2>
      {/* Resto do componente */}
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

## Performance Metrics e Monitoramento

### Medindo e Monitorando Performance de Client Components

Para garantir que os Client Components entreguem uma experiência otimizada, é essencial medir e monitorar seu desempenho. A seguir, apresentamos estratégias recomendadas:

#### 1. Web Vitals

```typescript
// app/_components/WebVitalsReporter.tsx
"use client";

import { useReportWebVitals } from "next/web-vitals";
import { useEffect } from "react";

export function WebVitalsReporter() {
  useReportWebVitals((metric) => {
    // Exemplo de envio para serviço de analytics
    const body = JSON.stringify(metric);

    // Usando Beacon API quando disponível
    if (navigator.sendBeacon) {
      navigator.sendBeacon("/api/analytics/web-vitals", body);
    } else {
      // Fallback para fetch
      fetch("/api/analytics/web-vitals", {
        body,
        method: "POST",
        keepalive: true,
      });
    }

    // Log durante desenvolvimento
    if (process.env.NODE_ENV === "development") {
      console.log(`Web Vital: ${metric.name}`, metric);
    }
  });

  return null;
}
```

Integre este componente no layout raiz:

```typescript
// app/layout.tsx
import { WebVitalsReporter } from "./_components/WebVitalsReporter";

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="pt-BR">
      <body>
        {children}
        <WebVitalsReporter />
      </body>
    </html>
  );
}
```

#### 2. Uso da React Profiler API

Para componentes críticos e com muita interatividade, use a Profiler API do React para medir o tempo de renderização:

```typescript
// app/_components/ProfiledComponent.tsx
"use client";

import { Profiler, ProfilerOnRenderCallback } from "react";

const onRender: ProfilerOnRenderCallback = (
  id,
  phase,
  actualDuration,
  baseDuration,
  startTime,
  commitTime
) => {
  // Enviar para sistema de monitoramento
  if (actualDuration > 16) {
    // Mais de 1 frame (16.67ms)
    console.warn(
      `Componente ${id} levou ${actualDuration.toFixed(2)}ms para renderizar`
    );

    // Exemplo: enviar para sistema de monitoramento
    reportPerformanceIssue({
      componentId: id,
      actualDuration,
      baseDuration,
      timestamp: new Date().toISOString(),
    });
  }
};

export function ProfiledDataTable({ data }) {
  return (
    <Profiler id="DataTable" onRender={onRender}>
      <DataTable data={data} />
    </Profiler>
  );
}

// Função fictícia para relatar problemas
function reportPerformanceIssue(data: any) {
  // Implementação real enviaria para New Relic, Datadog, etc.
  console.info("Performance issue reported:", data);
}
```

#### 3. Ferramenta de Monitoramento de Re-renderizações

```typescript
// lib/hooks/useRenderCounter.ts
"use client";

import { useRef, useEffect } from "react";

export function useRenderCounter(componentName: string, threshold: number = 3) {
  const renderCount = useRef(0);

  useEffect(() => {
    renderCount.current += 1;

    if (
      renderCount.current > threshold &&
      process.env.NODE_ENV === "development"
    ) {
      console.warn(
        `%c${componentName} re-renderizou ${renderCount.current} vezes`,
        "color: orange; font-weight: bold;"
      );
    }

    return () => {
      // Reset em componentWillUnmount para evitar alertas falsos
      renderCount.current = 0;
    };
  });

  return renderCount.current;
}
```

#### 4. Integração com ferramentas de observabilidade

```typescript
// lib/monitoring/index.ts
export function trackComponentPerformance(data: {
  componentName: string;
  renderTime: number;
  eventType: "mount" | "update" | "unmount";
  additionalData?: Record<string, any>;
}) {
  // Em produção, integre com Sentry, New Relic, Datadog, etc.
  if (process.env.NODE_ENV === "production") {
    // Exemplo de integração com Sentry
    if (typeof window !== "undefined" && window.Sentry) {
      window.Sentry.addBreadcrumb({
        category: "performance",
        message: `Componente ${data.componentName} ${data.eventType} em ${data.renderTime}ms`,
        level: data.renderTime > 50 ? "warning" : "info",
        data: data.additionalData,
      });

      if (data.renderTime > 100) {
        window.Sentry.captureMessage(
          `Componente lento detectado: ${data.componentName}`,
          "warning"
        );
      }
    }
  }
}
```

### Estratégias para Mobile-First e Otimização de Dispositivos Móveis

Em um mundo onde mais de 60% do tráfego web vem de dispositivos móveis, otimizar Client Components para estas plataformas é essencial.

#### 1. Code Splitting Responsivo

```typescript
// app/_components/ProductGallery.tsx
"use client";

import dynamic from "next/dynamic";
import { useMediaQuery } from "@/lib/hooks/useMediaQuery";
import { Skeleton } from "@/components/ui/skeleton";

// Versão leve para dispositivos móveis
const MobileGallery = dynamic(() => import("./MobileGallery"), {
  loading: () => <Skeleton className="h-[300px] w-full rounded-lg" />,
});

// Versão completa para desktop
const DesktopGallery = dynamic(() => import("./DesktopGallery"), {
  loading: () => <Skeleton className="h-[500px] w-full rounded-lg" />,
});

export function ProductGallery({ images }) {
  const isMobile = useMediaQuery("(max-width: 768px)");

  return isMobile ? (
    <MobileGallery images={images} />
  ) : (
    <DesktopGallery images={images} />
  );
}
```

Hook de media query:

```typescript
// lib/hooks/useMediaQuery.ts
"use client";

import { useState, useEffect } from "react";

export function useMediaQuery(query: string): boolean {
  const [matches, setMatches] = useState(false);

  useEffect(() => {
    if (typeof window !== "undefined") {
      const media = window.matchMedia(query);

      // Definir valor inicial
      setMatches(media.matches);

      // Callback para mudanças
      const listener = (e: MediaQueryListEvent) => {
        setMatches(e.matches);
      };

      // Adicionar listener
      if (media.addEventListener) {
        media.addEventListener("change", listener);
      } else {
        // Para navegadores mais antigos
        media.addListener(listener);
      }

      // Cleanup
      return () => {
        if (media.removeEventListener) {
          media.removeEventListener("change", listener);
        } else {
          // Para navegadores mais antigos
          media.removeListener(listener);
        }
      };
    }

    // Valor padrão para SSR
    return () => {};
  }, [query]);

  return matches;
}
```

#### 2. Otimização de Interações Touch

```typescript
// lib/hooks/useSwipeGesture.ts
"use client";

import { useCallback, useRef } from "react";

interface SwipeOptions {
  onSwipeLeft?: () => void;
  onSwipeRight?: () => void;
  onSwipeUp?: () => void;
  onSwipeDown?: () => void;
  threshold?: number; // distância mínima em pixels
}

export function useSwipeGesture(options: SwipeOptions = {}) {
  const { threshold = 50 } = options;

  // Coordenadas iniciais do toque
  const touchStart = useRef({ x: 0, y: 0 });

  const handleTouchStart = useCallback((e: React.TouchEvent) => {
    touchStart.current = {
      x: e.touches[0].clientX,
      y: e.touches[0].clientY,
    };
  }, []);

  const handleTouchEnd = useCallback(
    (e: React.TouchEvent) => {
      const touchEndX = e.changedTouches[0].clientX;
      const touchEndY = e.changedTouches[0].clientY;

      const deltaX = touchStart.current.x - touchEndX;
      const deltaY = touchStart.current.y - touchEndY;

      // Detectar direção com base na maior distância
      if (Math.abs(deltaX) > Math.abs(deltaY)) {
        // Movimento horizontal
        if (Math.abs(deltaX) > threshold) {
          if (deltaX > 0 && options.onSwipeLeft) {
            options.onSwipeLeft();
          } else if (deltaX < 0 && options.onSwipeRight) {
            options.onSwipeRight();
          }
        }
      } else {
        // Movimento vertical
        if (Math.abs(deltaY) > threshold) {
          if (deltaY > 0 && options.onSwipeUp) {
            options.onSwipeUp();
          } else if (deltaY < 0 && options.onSwipeDown) {
            options.onSwipeDown();
          }
        }
      }
    },
    [options, threshold]
  );

  return {
    handlers: {
      onTouchStart: handleTouchStart,
      onTouchEnd: handleTouchEnd,
    },
  };
}
```

Exemplo de uso:

```typescript
// app/(shop)/_components/ProductCarousel.tsx
"use client";

import { useState } from "react";
import { useSwipeGesture } from "@/lib/hooks/useSwipeGesture";

export function ProductCarousel({ products }) {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextSlide = () => {
    setCurrentIndex((prev) => (prev + 1) % products.length);
  };

  const prevSlide = () => {
    setCurrentIndex((prev) => (prev - 1 + products.length) % products.length);
  };

  const { handlers } = useSwipeGesture({
    onSwipeLeft: nextSlide,
    onSwipeRight: prevSlide,
  });

  return (
    <div className="relative overflow-hidden w-full" {...handlers}>
      <div
        className="flex transition-transform duration-300 ease-in-out"
        style={{ transform: `translateX(-${currentIndex * 100}%)` }}
      >
        {products.map((product) => (
          <div key={product.id} className="w-full flex-shrink-0 p-4">
            <img
              src={product.imageUrl}
              alt={product.name}
              className="w-full h-auto object-cover rounded-lg"
            />
          </div>
        ))}
      </div>

      {/* Indicadores e controles */}
    </div>
  );
}
```

#### 3. Otimizações de Input para Dispositivos Móveis

```typescript
// app/(shop)/_components/SearchInput.tsx
"use client";

import { useState, useRef, useEffect } from "react";
import { Search, X } from "lucide-react";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { useDebounce } from "@/lib/hooks/useDebounce";

export function SearchInput({ onSearch }) {
  const [query, setQuery] = useState("");
  const [isFocused, setIsFocused] = useState(false);
  const inputRef = useRef<HTMLInputElement>(null);

  const debouncedQuery = useDebounce(query, 300);

  // Efeito para aplicar a busca após o debounce
  useEffect(() => {
    if (debouncedQuery) {
      onSearch(debouncedQuery);
    }
  }, [debouncedQuery, onSearch]);

  // Otimizações para teclado móvel
  const handleFocus = () => {
    setIsFocused(true);
    // Scroll para manter o input visível quando o teclado abre
    setTimeout(() => {
      if (inputRef.current) {
        inputRef.current.scrollIntoView({ behavior: "smooth" });
      }
    }, 100);
  };

  const handleClear = () => {
    setQuery("");
    inputRef.current?.focus();
    onSearch("");
  };

  return (
    <div
      className={`relative transition-all duration-200 ${
        isFocused ? "w-full" : "w-3/4"
      }`}
    >
      <Input
        ref={inputRef}
        type="search"
        placeholder="Buscar produtos..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        onFocus={handleFocus}
        onBlur={() => setIsFocused(false)}
        className="pr-8"
        // Melhorar experiência em dispositivos móveis
        inputMode="search"
        enterKeyHint="search"
      />

      {query && (
        <Button
          variant="ghost"
          size="sm"
          className="absolute right-0 top-0 h-full"
          onClick={handleClear}
          aria-label="Limpar busca"
        >
          <X className="h-4 w-4" />
        </Button>
      )}
    </div>
  );
}
```

#### 4. Script de Monitoring de Performance

```typescript
// lib/monitoring/performance.ts
export function initPerformanceMonitoring() {
  if (typeof window === "undefined") return;

  // Capturar FID (First Input Delay)
  const onFirstInputDelay = (entry: PerformanceEventTiming) => {
    // Capture e reporta o tempo de resposta ao primeiro input
    if (entry.processingStart && entry.startTime) {
      const inputDelay = entry.processingStart - entry.startTime;

      if (inputDelay > 100) {
        console.warn(`Alto First Input Delay: ${inputDelay.toFixed(2)}ms`);
        // Enviar para sistema de monitoramento
      }
    }
  };

  // Capturar LCP (Largest Contentful Paint)
  const onLargestContentfulPaint = (entry: PerformanceEntry) => {
    // @ts-ignore - LCP não está completamente tipado no TypeScript padrão
    const lcp = entry.startTime;

    if (lcp > 2500) {
      console.warn(`LCP lento: ${lcp.toFixed(2)}ms`);
      // Enviar para sistema de monitoramento
    }
  };

  // Capturar CLS (Cumulative Layout Shift)
  const onLayoutShift = (entry: PerformanceEntry) => {
    // @ts-ignore - Layout Shift não está completamente tipado no TypeScript padrão
    if (entry.value > 0.1) {
      console.warn(`Layout shift significativo: ${entry.value.toFixed(3)}`);
      // Enviar para sistema de monitoramento
    }
  };

  // Registrar observadores se a API estiver disponível
  if ("PerformanceObserver" in window) {
    try {
      // FID observer
      new PerformanceObserver((entryList) => {
        for (const entry of entryList.getEntries()) {
          onFirstInputDelay(entry as PerformanceEventTiming);
        }
      }).observe({ type: "first-input", buffered: true });

      // LCP observer
      new PerformanceObserver((entryList) => {
        for (const entry of entryList.getEntries()) {
          onLargestContentfulPaint(entry);
        }
      }).observe({ type: "largest-contentful-paint", buffered: true });

      // CLS observer
      new PerformanceObserver((entryList) => {
        for (const entry of entryList.getEntries()) {
          onLayoutShift(entry);
        }
      }).observe({ type: "layout-shift", buffered: true });
    } catch (e) {
      console.error("Erro ao configurar PerformanceObserver", e);
    }
  }
}
```

Para utilizar este script, adicione-o ao seu layout principal:

```typescript
// app/layout.tsx
"use client";

import { useEffect } from "react";
import { initPerformanceMonitoring } from "@/lib/monitoring/performance";

function PerformanceMonitor() {
  useEffect(() => {
    initPerformanceMonitoring();
  }, []);

  return null;
}

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="pt-BR">
      <body>
        {children}
        <PerformanceMonitor />
      </body>
    </html>
  );
}
```

### Implications de SSR vs CSR

É crucial entender as implicações de Server-Side Rendering (SSR) versus Client-Side Rendering (CSR) ao trabalhar com Client Components no Next.js:

#### 1. O Ciclo de Hidratação

Client Components passam por um processo de hidratação após serem renderizados no servidor. Isso pode levar a problemas como:

```typescript
// app/_components/HydrationAwareComponent.tsx
"use client";

import { useState, useEffect } from "react";

export function HydrationAwareComponent({ initialData }) {
  // Problema: valores diferentes entre servidor e cliente
  const [isClient, setIsClient] = useState(false);
  const [data, setData] = useState(initialData);

  // Solução: usar useEffect para atualizar estado apenas no cliente
  useEffect(() => {
    setIsClient(true);

    // Agora é seguro usar lógica específica do cliente
    if (typeof window !== "undefined") {
      const savedData = localStorage.getItem("userData");
      if (savedData) {
        try {
          setData(JSON.parse(savedData));
        } catch (e) {
          console.error("Erro ao parsear dados salvos", e);
        }
      }
    }
  }, []);

  // Evitar erros de hidratação usando a mesma saída do servidor
  // até que o cliente esteja totalmente hidratado
  if (!isClient) {
    return <div>{initialData.summary}</div>;
  }

  return (
    <div>
      <h3>{data.title}</h3>
      <p>{data.summary}</p>
      {isClient && (
        <button onClick={() => console.log("Clicado!")}>
          Interagir (disponível apenas após hidratação)
        </button>
      )}
    </div>
  );
}
```

#### 2. Estratégias para Evitar Erros de Hidratação

```typescript
// lib/hooks/useSafeLayoutEffect.ts
"use client";

import { useEffect, useLayoutEffect } from "react";

// Versão segura de useLayoutEffect que não causa alertas em SSR
export const useSafeLayoutEffect =
  typeof window !== "undefined" ? useLayoutEffect : useEffect;
```

```typescript
// app/_components/ClientOnlyPortal.tsx
"use client";

import { useState, useEffect } from "react";
import { createPortal } from "react-dom";

export function ClientOnlyPortal({ children, selector }) {
  const [mounted, setMounted] = useState(false);

  useEffect(() => {
    setMounted(true);
    return () => setMounted(false);
  }, []);

  // Não renderiza nada no servidor
  if (!mounted) return null;

  // No cliente, render como Portal
  const element = document.querySelector(selector);
  if (!element) return null;

  return createPortal(children, element);
}
```

#### 3. Progressive Hydration

```typescript
// app/_components/ProgressiveHydration.tsx
"use client";

import { useState, useEffect, Suspense } from "react";
import { useInView } from "react-intersection-observer";

export function ProgressiveHydration({
  children,
  fallback,
  triggerOnce = true,
}) {
  const { ref, inView } = useInView({
    triggerOnce,
    rootMargin: "200px", // Pré-carrega quando estiver a 200px da viewport
  });

  return (
    <div ref={ref}>
      {inView ? <Suspense fallback={fallback}>{children}</Suspense> : fallback}
    </div>
  );
}
```

Exemplo de uso:

```tsx
<ProgressiveHydration fallback={<ProductCardSkeleton />}>
  <ProductRecommendations />
</ProgressiveHydration>
```

Estas estratégias ajudam a otimizar a performance e a experiência do usuário em dispositivos móveis e lidar com os desafios de hidratação em aplicações Next.js.

## Padrões de Otimização
