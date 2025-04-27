# Error Handling

## Descrição

Este documento descreve os padrões recomendados para tratamento de erros em aplicações Next.js, abrangendo tanto componentes do lado do servidor quanto do cliente, rotas de API e manipulação global de erros. Um tratamento de erros robusto melhora a experiência do usuário, facilita a depuração e aumenta a resiliência da aplicação.

## Princípios Fundamentais

- **Tratamento gracioso**: Apresente mensagens de erro amigáveis para os usuários
- **Granularidade adequada**: Implemente tratamento de erros em diferentes níveis da aplicação
- **Logging informativo**: Capture detalhes relevantes para facilitar a depuração
- **Isolamento de falhas**: Evite que erros em um componente afetem toda a aplicação
- **Recuperação quando possível**: Forneça alternativas ou tentativas automáticas de recuperação

## Implementação

### 1. Error Boundaries para componentes do cliente

Com o App Router do Next.js, use o arquivo `error.tsx` para criar um limite de erro:

```tsx
// app/dashboard/error.tsx
"use client"; // Error boundaries devem ser Client Components

import { useEffect } from "react";
import { Button } from "@/components/ui/button";

interface ErrorBoundaryProps {
  error: Error & { digest?: string };
  reset: () => void;
}

export default function DashboardError({ error, reset }: ErrorBoundaryProps) {
  useEffect(() => {
    // Registrar o erro em um serviço de monitoramento
    console.error("Dashboard error:", error);
  }, [error]);

  return (
    <div className="flex h-[50vh] flex-col items-center justify-center space-y-4">
      <div className="text-center">
        <h2 className="text-2xl font-bold tracking-tight">Algo deu errado!</h2>
        <p className="mt-2 text-muted-foreground">
          Ocorreu um erro ao carregar o dashboard.
        </p>
        {process.env.NODE_ENV === "development" && (
          <div className="mt-4 rounded-md bg-slate-950 p-4">
            <p className="text-sm text-white">{error.message}</p>
          </div>
        )}
      </div>
      <Button onClick={reset}>Tentar novamente</Button>
    </div>
  );
}
```

### 2. Página 404 global personalizada

Crie uma página 404 customizada para lidar com rotas não encontradas:

```tsx
// app/not-found.tsx
import Link from "next/link";
import { Button } from "@/components/ui/button";

export default function NotFound() {
  return (
    <div className="flex h-screen flex-col items-center justify-center space-y-4 text-center">
      <h2 className="text-4xl font-bold">404</h2>
      <p className="text-xl">Página não encontrada</p>
      <p className="text-muted-foreground">
        A página que você está procurando não existe ou foi movida.
      </p>
      <Button asChild>
        <Link href="/">Retornar à página inicial</Link>
      </Button>
    </div>
  );
}
```

### 3. Páginas 404 específicas para segmentos

Para personalizar 404 em segmentos específicos da aplicação:

```tsx
// app/produtos/not-found.tsx
import Link from "next/link";
import { Button } from "@/components/ui/button";

export default function ProdutoNotFound() {
  return (
    <div className="flex flex-col items-center justify-center space-y-4 py-12 text-center">
      <h2 className="text-2xl font-bold">Produto não encontrado</h2>
      <p className="text-muted-foreground">
        O produto que você está procurando não existe ou foi removido.
      </p>
      <div className="flex gap-4">
        <Button variant="outline" asChild>
          <Link href="/produtos">Ver todos os produtos</Link>
        </Button>
        <Button asChild>
          <Link href="/">Página inicial</Link>
        </Button>
      </div>
    </div>
  );
}
```

Para acionar essa página em rotas dinâmicas:

```tsx
// app/produtos/[id]/page.tsx
import { notFound } from "next/navigation";

export default async function ProdutoPage({
  params,
}: {
  params: { id: string };
}) {
  const produto = await fetchProduto(params.id);

  if (!produto) {
    // Isso aciona o not-found.tsx mais próximo
    notFound();
  }

  return (
    <div>
      <h1>{produto.nome}</h1>
      {/* Conteúdo do produto */}
    </div>
  );
}
```

### 4. Tratamento global de erros

Use o arquivo `global-error.tsx` na raiz da pasta app para capturar erros que ocorrem em qualquer parte da aplicação:

```tsx
// app/global-error.tsx
"use client";

import { useEffect } from "react";
import { Button } from "@/components/ui/button";

export default function GlobalError({
  error,
  reset,
}: {
  error: Error & { digest?: string };
  reset: () => void;
}) {
  useEffect(() => {
    // Log do erro para serviço externo
    console.error("Erro global:", error);
  }, [error]);

  return (
    <html>
      <body>
        <div className="flex h-screen flex-col items-center justify-center p-4 text-center">
          <h2 className="mb-2 text-2xl font-bold">Algo deu muito errado!</h2>
          <p className="mb-8 text-muted-foreground">
            Ocorreu um erro inesperado. Nossa equipe foi notificada.
          </p>
          <Button onClick={reset}>Tentar novamente</Button>
        </div>
      </body>
    </html>
  );
}
```

### 5. Loading states para melhorar a UX durante carregamentos

Crie estados de carregamento para reduzir a percepção de erro durante operações assíncronas:

```tsx
// app/dashboard/loading.tsx
import { Skeleton } from "@/components/ui/skeleton";

export default function DashboardLoading() {
  return (
    <div className="space-y-4 p-4">
      <Skeleton className="h-8 w-[250px]" />
      <div className="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3">
        {Array.from({ length: 6 }).map((_, i) => (
          <Skeleton key={i} className="h-[180px]" />
        ))}
      </div>
    </div>
  );
}
```

### 6. Hook de tratamento de erros para componentes do cliente

Crie hooks reutilizáveis para gerenciar erros no lado do cliente:

```tsx
// hooks/use-async-error.ts
"use client";

import { useState, useCallback } from "react";

interface UseAsyncErrorOptions {
  onError?: (error: Error) => void;
  errorMessage?: string;
}

export function useAsyncError<T>(options: UseAsyncErrorOptions = {}) {
  const [error, setError] = useState<Error | null>(null);
  const [isLoading, setIsLoading] = useState(false);

  const handleAsync = useCallback(
    async (asyncFn: () => Promise<T>): Promise<T | null> => {
      try {
        setIsLoading(true);
        setError(null);
        return await asyncFn();
      } catch (err) {
        const error =
          err instanceof Error
            ? err
            : new Error(options.errorMessage || "Ocorreu um erro inesperado");

        setError(error);
        options.onError?.(error);
        return null;
      } finally {
        setIsLoading(false);
      }
    },
    [options]
  );

  const clearError = useCallback(() => {
    setError(null);
  }, []);

  return {
    error,
    isLoading,
    handleAsync,
    clearError,
  };
}
```

Usando o hook:

```tsx
// components/profile-form.tsx
"use client";

import { useAsyncError } from "@/hooks/use-async-error";
import { Button } from "@/components/ui/button";
import { toast } from "@/components/ui/use-toast";

export function ProfileForm() {
  const { handleAsync, error, isLoading } = useAsyncError({
    onError: (error) => {
      toast({
        title: "Erro ao atualizar perfil",
        description: error.message,
        variant: "destructive",
      });
    },
  });

  async function updateProfile(data: FormData) {
    await handleAsync(async () => {
      const response = await fetch("/api/profile", {
        method: "PUT",
        body: data,
      });

      if (!response.ok) {
        const errorData = await response.json();
        throw new Error(errorData.message || "Falha ao atualizar perfil");
      }

      toast({
        title: "Perfil atualizado",
        description: "Suas informações foram atualizadas com sucesso.",
      });
    });
  }

  return (
    <form action={updateProfile}>
      {/* Campos de formulário */}
      {error && (
        <p className="text-destructive text-sm mt-2">{error.message}</p>
      )}
      <Button type="submit" disabled={isLoading}>
        {isLoading ? "Atualizando..." : "Salvar alterações"}
      </Button>
    </form>
  );
}
```

### 7. Tratamento de erros em Server Actions

Para Server Actions, utilize try/catch e retorne objetos de resultado padronizados:

```tsx
// app/actions/user-actions.ts
"use server";

import { revalidatePath } from "next/cache";
import { z } from "zod";

// Esquema de validação com Zod
const userFormSchema = z.object({
  name: z.string().min(2, { message: "Nome deve ter pelo menos 2 caracteres" }),
  email: z.string().email({ message: "Email inválido" }),
  bio: z
    .string()
    .max(500, { message: "Bio deve ter no máximo 500 caracteres" })
    .optional(),
});

type UserFormData = z.infer<typeof userFormSchema>;

export type ActionResponse<T = void> = {
  success: boolean;
  data?: T;
  error?: {
    message: string;
    errors?: Record<string, string[]>;
    code?: string;
  };
};

export async function updateUserProfile(
  prevState: any,
  formData: FormData
): Promise<ActionResponse<{ user: { id: string; name: string } }>> {
  try {
    // Converter FormData para objeto
    const rawData = Object.fromEntries(formData.entries());

    // Validar dados com Zod
    const validationResult = userFormSchema.safeParse(rawData);

    if (!validationResult.success) {
      return {
        success: false,
        error: {
          message: "Dados de formulário inválidos",
          errors: validationResult.error.flatten().fieldErrors,
        },
      };
    }

    const data = validationResult.data;

    // Simulação de chamada de banco de dados
    // Na implementação real, substitua por chamada ao seu banco de dados
    const user = await updateUser(data);

    // Revalidar cache de páginas que mostram os dados do usuário
    revalidatePath("/profile");
    revalidatePath("/dashboard");

    return {
      success: true,
      data: { user },
    };
  } catch (error) {
    console.error("Error updating user profile:", error);

    // Determinar tipo de erro para mensagem apropriada
    if (error instanceof Error) {
      return {
        success: false,
        error: {
          message: error.message,
          code: "INTERNAL_ERROR",
        },
      };
    }

    return {
      success: false,
      error: {
        message: "Ocorreu um erro ao atualizar o perfil",
        code: "UNKNOWN_ERROR",
      },
    };
  }
}

// Função simulada
async function updateUser(data: UserFormData) {
  // Na implementação real, substitua por chamada ao seu banco de dados
  return { id: "123", name: data.name };
}
```

Utilizando o Server Action com tratamento de erros:

```tsx
// app/profile/page.tsx
"use client";

import { useFormState } from "react-dom";
import { updateUserProfile } from "@/app/actions/user-actions";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Alert, AlertDescription, AlertTitle } from "@/components/ui/alert";
import { CheckCircle, AlertTriangle } from "lucide-react";

export default function ProfilePage() {
  const [state, formAction] = useFormState(updateUserProfile, {
    success: false,
  });

  return (
    <div className="max-w-2xl mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Editar Perfil</h1>

      {state.success && (
        <Alert className="mb-4 bg-green-50 border-green-200">
          <CheckCircle className="h-4 w-4 text-green-600" />
          <AlertTitle>Sucesso!</AlertTitle>
          <AlertDescription>
            Seu perfil foi atualizado com sucesso.
          </AlertDescription>
        </Alert>
      )}

      {state.error && (
        <Alert variant="destructive" className="mb-4">
          <AlertTriangle className="h-4 w-4" />
          <AlertTitle>Erro</AlertTitle>
          <AlertDescription>{state.error.message}</AlertDescription>
        </Alert>
      )}

      <form action={formAction} className="space-y-4">
        <div>
          <label htmlFor="name" className="block text-sm font-medium mb-1">
            Nome
          </label>
          <Input id="name" name="name" defaultValue="" />
          {state.error?.errors?.name && (
            <p className="text-destructive text-sm mt-1">
              {state.error.errors.name[0]}
            </p>
          )}
        </div>

        <div>
          <label htmlFor="email" className="block text-sm font-medium mb-1">
            Email
          </label>
          <Input id="email" name="email" type="email" defaultValue="" />
          {state.error?.errors?.email && (
            <p className="text-destructive text-sm mt-1">
              {state.error.errors.email[0]}
            </p>
          )}
        </div>

        <div>
          <label htmlFor="bio" className="block text-sm font-medium mb-1">
            Bio
          </label>
          <Textarea id="bio" name="bio" rows={4} defaultValue="" />
          {state.error?.errors?.bio && (
            <p className="text-destructive text-sm mt-1">
              {state.error.errors.bio[0]}
            </p>
          )}
        </div>

        <Button type="submit" className="w-full">
          Salvar Alterações
        </Button>
      </form>
    </div>
  );
}
```

### 8. Tratamento de erros em rotas de API

Implemente um wrapper para padronizar os erros em rotas de API:

```tsx
// lib/api-error.ts
export class ApiError extends Error {
  statusCode: number;
  code?: string;
  errors?: Record<string, string[]>;

  constructor({
    message,
    statusCode = 500,
    code,
    errors,
  }: {
    message: string;
    statusCode?: number;
    code?: string;
    errors?: Record<string, string[]>;
  }) {
    super(message);
    this.name = "ApiError";
    this.statusCode = statusCode;
    this.code = code;
    this.errors = errors;
  }
}

export function handleApiRoute(
  handler: (
    req: Request,
    context: { params: Record<string, string> }
  ) => Promise<Response>
) {
  return async (req: Request, context: { params: Record<string, string> }) => {
    try {
      return await handler(req, context);
    } catch (error) {
      console.error("API route error:", error);

      if (error instanceof ApiError) {
        return Response.json(
          {
            error: {
              message: error.message,
              code: error.code,
              errors: error.errors,
            },
          },
          { status: error.statusCode }
        );
      }

      // Para erros desconhecidos
      return Response.json(
        {
          error: {
            message: "Ocorreu um erro interno no servidor",
            code: "INTERNAL_SERVER_ERROR",
          },
        },
        { status: 500 }
      );
    }
  };
}
```

Exemplo de uso em uma rota de API:

```tsx
// app/api/posts/[id]/route.ts
import { ApiError, handleApiRoute } from "@/lib/api-error";
import { NextResponse } from "next/server";

export const GET = handleApiRoute(async (request, { params }) => {
  const { id } = params;

  // Validar ID
  if (!id || !/^\d+$/.test(id)) {
    throw new ApiError({
      message: "ID de post inválido",
      statusCode: 400,
      code: "INVALID_POST_ID",
    });
  }

  try {
    const post = await fetchPost(id);

    if (!post) {
      throw new ApiError({
        message: "Post não encontrado",
        statusCode: 404,
        code: "POST_NOT_FOUND",
      });
    }

    return NextResponse.json(post);
  } catch (error) {
    // Re-lançar erros ApiError para serem tratados pelo wrapper
    if (error instanceof ApiError) {
      throw error;
    }

    // Converter outros erros para ApiError
    console.error(`Error fetching post ${id}:`, error);
    throw new ApiError({
      message: "Erro ao buscar post",
      statusCode: 500,
      code: "DATABASE_ERROR",
    });
  }
});

// Função simulada
async function fetchPost(id: string) {
  // Na implementação real, substitua por chamada ao seu banco de dados
  if (id === "999") return null; // Simular post não encontrado
  return { id, title: "Post de exemplo", content: "Conteúdo do post..." };
}
```

### 9. Classe de utilidade para tratamento de erros assíncronos

Crie uma classe utilitária para funções assíncronas reutilizáveis:

```tsx
// lib/async-utils.ts
export class Result<T> {
  private constructor(
    private readonly _value: T | null,
    private readonly _error: Error | null
  ) {}

  static success<T>(value: T): Result<T> {
    return new Result<T>(value, null);
  }

  static failure<T>(error: Error): Result<T> {
    return new Result<T>(null, error);
  }

  static async fromPromise<T>(promise: Promise<T>): Promise<Result<T>> {
    try {
      const value = await promise;
      return Result.success(value);
    } catch (error) {
      return Result.failure(
        error instanceof Error ? error : new Error(String(error))
      );
    }
  }

  isSuccess(): boolean {
    return this._error === null;
  }

  isFailure(): boolean {
    return this._error !== null;
  }

  getValue(): T {
    if (this._value === null) {
      throw new Error("Cannot get value from failure result");
    }
    return this._value;
  }

  getError(): Error {
    if (this._error === null) {
      throw new Error("Cannot get error from success result");
    }
    return this._error;
  }

  match<U>(onSuccess: (value: T) => U, onFailure: (error: Error) => U): U {
    return this.isSuccess()
      ? onSuccess(this.getValue())
      : onFailure(this.getError());
  }
}
```

Exemplo de uso da classe Result:

```tsx
// app/products/page.tsx
import { Result } from "@/lib/async-utils";
import ProductList from "@/components/product-list";
import ProductError from "@/components/product-error";

async function fetchProducts() {
  const response = await fetch("https://api.example.com/products");

  if (!response.ok) {
    throw new Error(`Failed to fetch products: ${response.statusText}`);
  }

  return response.json();
}

export default async function ProductsPage() {
  const result = await Result.fromPromise(fetchProducts());

  return result.match(
    (products) => <ProductList products={products} />,
    (error) => <ProductError error={error} />
  );
}
```

## Anti-padrões a evitar

### 1. Try/catch excessivos

❌ **Não faça isso**:

```tsx
// Try/catch aninhados com lógica repetitiva
async function fetchData() {
  try {
    const userData = await fetch("/api/user");
    try {
      const userJson = await userData.json();
      try {
        const posts = await fetch(`/api/posts?userId=${userJson.id}`);
        // mais try/catch aninhados...
      } catch (error) {
        console.error("Error fetching posts:", error);
      }
    } catch (error) {
      console.error("Error parsing user data:", error);
    }
  } catch (error) {
    console.error("Error fetching user:", error);
  }
}
```

✅ **Prefira**:

```tsx
// Utilizar funções com responsabilidade única e wrappers de erro
async function fetchData() {
  const userResult = await Result.fromPromise(fetchUser());

  if (userResult.isFailure()) {
    console.error("Error fetching user:", userResult.getError());
    return null;
  }

  const user = userResult.getValue();
  const postsResult = await Result.fromPromise(fetchPosts(user.id));

  if (postsResult.isFailure()) {
    console.error("Error fetching posts:", postsResult.getError());
    return { user, posts: [] };
  }

  return { user, posts: postsResult.getValue() };
}
```

### 2. Mensagens de erro genéricas

❌ **Não faça isso**:

```tsx
try {
  // Operação complexa
} catch (error) {
  // Mensagem vaga que não ajuda na depuração
  console.error("Algo deu errado");
  throw new Error("Erro no sistema");
}
```

✅ **Prefira**:

```tsx
try {
  // Operação complexa
} catch (error) {
  // Mensagem específica com contexto e detalhes para depuração
  console.error("Falha ao processar pagamento:", error);

  // Mensagem amigável para o usuário, mas com código para rastreamento
  const errorId = generateErrorId();
  throw new ApiError({
    message: `Não foi possível processar o pagamento. Tente novamente ou entre em contato com o suporte (Ref: ${errorId})`,
    statusCode: 500,
    code: "PAYMENT_PROCESSING_FAILED",
  });
}
```

### 3. Falhar silenciosamente

❌ **Não faça isso**:

```tsx
async function fetchData() {
  try {
    const response = await fetch("/api/data");
    if (!response.ok) {
      // Erro ignorado sem tratamento adequado
      console.log("Erro na API");
      return []; // Retorno vazio sem informar o erro
    }
    return await response.json();
  } catch (error) {
    // Erro ignorado completamente
    return [];
  }
}
```

✅ **Prefira**:

```tsx
async function fetchData() {
  try {
    const response = await fetch("/api/data");

    if (!response.ok) {
      // Analisar erro da API para fornecer informações úteis
      const errorData = await response.json().catch(() => ({}));
      const message = errorData.message || response.statusText;
      throw new Error(`API error (${response.status}): ${message}`);
    }

    return await response.json();
  } catch (error) {
    // Registrar erro e rethrow para tratamento adequado na UI
    console.error("Error fetching data:", error);
    throw error;
  }
}
```

### 4. Não usar validação de esquema para dados de entrada

❌ **Não faça isso**:

```tsx
export async function createUser(formData: FormData) {
  const name = formData.get("name");
  const email = formData.get("email");

  // Validação ad-hoc sujeita a erros
  if (!name) throw new Error("Nome é obrigatório");
  if (!email) throw new Error("Email é obrigatório");
  if (typeof email !== "string" || !email.includes("@"))
    throw new Error("Email inválido");

  // Continuar com a criação do usuário...
}
```

✅ **Prefira**:

```tsx
import { z } from "zod";

const userSchema = z.object({
  name: z.string().min(1, "Nome é obrigatório"),
  email: z.string().email("Email inválido"),
});

export async function createUser(formData: FormData) {
  // Converter FormData para objeto
  const data = Object.fromEntries(formData.entries());

  // Validar com Zod
  const result = userSchema.safeParse(data);

  if (!result.success) {
    // Erros estruturados que são fáceis de mostrar na UI
    const errors = result.error.flatten().fieldErrors;
    throw new ApiError({
      message: "Dados de formulário inválidos",
      statusCode: 400,
      code: "VALIDATION_ERROR",
      errors,
    });
  }

  const validatedData = result.data;
  // Continuar com a criação do usuário...
}
```

### 5. Ocultar erros de servidor em produção

❌ **Não faça isso**:

```tsx
// Mostrar stack trace completo em produção
export default function ErrorComponent({ error }: { error: Error }) {
  return (
    <div>
      <h1>Erro</h1>
      <p>{error.message}</p>
      <pre>{error.stack}</pre>
    </div>
  );
}
```

✅ **Prefira**:

```tsx
// Mostrar informações sensíveis apenas em ambiente de desenvolvimento
export default function ErrorComponent({ error }: { error: Error }) {
  // Gerar um ID para o erro para facilitar a busca nos logs
  const errorId =
    typeof error.digest === "string"
      ? error.digest.substring(0, 8)
      : Math.random().toString(36).substring(2, 10);

  return (
    <div>
      <h1>Erro</h1>
      <p>Algo deu errado. Nossa equipe foi notificada.</p>
      <p>Referência do erro: {errorId}</p>

      {process.env.NODE_ENV === "development" && (
        <div>
          <p>
            <strong>Mensagem:</strong> {error.message}
          </p>
          <pre className="text-xs mt-2 p-4 bg-slate-100 rounded overflow-auto">
            {error.stack}
          </pre>
        </div>
      )}
    </div>
  );
}
```

## Configuração de ESLint recomendada

```json
{
  "rules": {
    "no-console": ["warn", { "allow": ["warn", "error"] }],
    "no-empty-catch": "warn",
    "no-throw-literal": "error",
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/explicit-function-return-type": [
      "warn",
      {
        "allowExpressions": true,
        "allowTypedFunctionExpressions": true
      }
    ],
    "prefer-promise-reject-errors": "warn"
  }
}
```

## Quando Aplicar

- Em aplicações de produção com expectativas de alta disponibilidade
- Quando lidar com operações assíncronas, como chamadas de API
- Ao implementar formulários com validação do lado do servidor
- Para proteger dados sensíveis de usuários
- Ao construir interfaces onde a experiência do usuário não deve ser interrompida por falhas
- Em aplicações com múltiplas integrações de terceiros que podem falhar
