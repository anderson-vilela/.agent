# Padrão para Server Actions no Next.js App Router

## Descrição

Server Actions são uma funcionalidade poderosa do Next.js que permite executar código de forma segura no servidor a partir de componentes React, tanto Server quanto Client Components. Este documento define padrões para implementação de Server Actions seguros, eficientes e bem estruturados, integrando-os com React Hook Form, Zod e TypeScript.

## Princípios Fundamentais

1. **Segurança em Primeiro Lugar**: Priorizar validação rigorosa e proteção contra vulnerabilidades
2. **Tipagem Forte**: Utilizar TypeScript para garantir consistência de dados e autocompletação
3. **Validação Consistente**: Implementar validação com Zod tanto no cliente quanto no servidor
4. **Organização Modular**: Estruturar Server Actions de forma coesa e organizada
5. **Feedback Claro**: Fornecer respostas claras sobre o resultado das operações

## Implementação de Server Actions

### 1. Estrutura Básica com a Diretiva 'use server'

#### Em Arquivo Separado (Recomendado)

```typescript
// lib/actions/auth.ts
"use server";

import { cookies } from "next/headers";
import { redirect } from "next/navigation";
import { z } from "zod";
import { db } from "@/lib/db";
import { hashPassword, comparePasswords } from "@/lib/auth/passwords";

// Schema para validação
const loginSchema = z.object({
  email: z.string().email("Email inválido"),
  password: z.string().min(8, "Senha deve ter pelo menos 8 caracteres"),
  rememberMe: z.boolean().optional(),
});

// Tipagem para retorno
type LoginResult =
  | { success: true; userId: string }
  | { success: false; error: string; field?: string };

export async function login(formData: FormData): Promise<LoginResult> {
  // Extrair e validar dados
  const validationResult = loginSchema.safeParse({
    email: formData.get("email"),
    password: formData.get("password"),
    rememberMe: formData.get("rememberMe") === "on",
  });

  if (!validationResult.success) {
    // Retorna erro de validação
    const firstError = validationResult.error.issues[0];
    return {
      success: false,
      error: firstError.message,
      field: firstError.path[0]?.toString(),
    };
  }

  const { email, password, rememberMe } = validationResult.data;

  try {
    // Buscar usuário
    const user = await db.user.findUnique({
      where: { email },
    });

    // Verificar senha
    if (!user || !(await comparePasswords(password, user.passwordHash))) {
      return {
        success: false,
        error: "Email ou senha inválidos",
      };
    }

    // Criar sessão
    const session = await db.session.create({
      data: {
        userId: user.id,
        expiresAt: rememberMe
          ? new Date(Date.now() + 30 * 24 * 60 * 60 * 1000) // 30 dias
          : new Date(Date.now() + 24 * 60 * 60 * 1000), // 1 dia
      },
    });

    // Definir cookie de sessão
    cookies().set("sessionId", session.id, {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "lax",
      path: "/",
      expires: session.expiresAt,
    });

    return {
      success: true,
      userId: user.id,
    };
  } catch (error) {
    console.error("Erro ao realizar login:", error);
    return {
      success: false,
      error: "Ocorreu um erro durante o login. Tente novamente.",
    };
  }
}

export async function logout() {
  // Obter cookie de sessão
  const sessionId = cookies().get("sessionId")?.value;

  if (sessionId) {
    try {
      // Remover sessão do banco
      await db.session.delete({
        where: { id: sessionId },
      });
    } catch (error) {
      console.error("Erro ao excluir sessão:", error);
    }
  }

  // Remover cookie
  cookies().delete("sessionId");

  // Redirecionar para login
  redirect("/login");
}
```

#### Em Componentes de Formulário

```typescript
// app/(auth)/login/page.tsx
import { login } from "@/lib/actions/auth";
import { LoginForm } from "./_components/LoginForm";

export default function LoginPage() {
  return (
    <div className="max-w-md mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Entrar</h1>
      <LoginForm loginAction={login} />
    </div>
  );
}

// app/(auth)/login/_components/LoginForm.tsx
("use client");

import { useState } from "react";
import { useRouter } from "next/navigation";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Checkbox } from "@/components/ui/checkbox";
import { Alert, AlertDescription } from "@/components/ui/alert";

// Schema de validação correspondente ao do Server Action
const loginSchema = z.object({
  email: z.string().email("Email inválido"),
  password: z.string().min(8, "Senha deve ter pelo menos 8 caracteres"),
  rememberMe: z.boolean().optional().default(false),
});

type LoginFormValues = z.infer<typeof loginSchema>;

export function LoginForm({
  loginAction,
}: {
  loginAction: (
    formData: FormData
  ) => Promise<{ success: boolean; error?: string; field?: string }>;
}) {
  const router = useRouter();
  const [serverError, setServerError] = useState<string | null>(null);
  const [isSubmitting, setIsSubmitting] = useState(false);

  const {
    register,
    handleSubmit,
    setError,
    formState: { errors },
  } = useForm<LoginFormValues>({
    resolver: zodResolver(loginSchema),
    defaultValues: {
      email: "",
      password: "",
      rememberMe: false,
    },
  });

  async function onSubmit(data: LoginFormValues) {
    setIsSubmitting(true);
    setServerError(null);

    // Criar FormData para passar ao Server Action
    const formData = new FormData();
    formData.append("email", data.email);
    formData.append("password", data.password);

    if (data.rememberMe) {
      formData.append("rememberMe", "on");
    }

    try {
      const result = await loginAction(formData);

      if (result.success) {
        // Redirecionar para o dashboard após login bem-sucedido
        router.push("/dashboard");
        router.refresh();
      } else {
        // Tratar erro específico de campo
        if (result.field) {
          setError(result.field as keyof LoginFormValues, {
            message: result.error,
          });
        } else {
          // Tratar erro geral
          setServerError(result.error);
        }
      }
    } catch (error) {
      setServerError("Ocorreu um erro inesperado. Tente novamente.");
      console.error("Erro ao processar login:", error);
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-4">
      {serverError && (
        <Alert variant="destructive">
          <AlertDescription>{serverError}</AlertDescription>
        </Alert>
      )}

      <div className="space-y-2">
        <label htmlFor="email" className="text-sm font-medium">
          Email
        </label>
        <Input
          id="email"
          type="email"
          {...register("email")}
          autoComplete="email"
          aria-invalid={!!errors.email}
        />
        {errors.email && (
          <p className="text-sm text-red-500">{errors.email.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="password" className="text-sm font-medium">
          Senha
        </label>
        <Input
          id="password"
          type="password"
          {...register("password")}
          autoComplete="current-password"
          aria-invalid={!!errors.password}
        />
        {errors.password && (
          <p className="text-sm text-red-500">{errors.password.message}</p>
        )}
      </div>

      <div className="flex items-center space-x-2">
        <Checkbox id="rememberMe" {...register("rememberMe")} />
        <label htmlFor="rememberMe" className="text-sm">
          Lembrar de mim
        </label>
      </div>

      <Button type="submit" className="w-full" disabled={isSubmitting}>
        {isSubmitting ? "Entrando..." : "Entrar"}
      </Button>
    </form>
  );
}
```

### 2. Server Actions com Argumentos Tipados

```typescript
// lib/actions/products.ts
"use server";

import { revalidatePath } from "next/cache";
import { z } from "zod";
import { db } from "@/lib/db";
import { auth } from "@/lib/auth";

// Schema de validação
const productSchema = z.object({
  name: z.string().min(3, "Nome deve ter pelo menos 3 caracteres"),
  description: z
    .string()
    .min(10, "Descrição deve ter pelo menos 10 caracteres"),
  price: z.number().positive("Preço deve ser maior que zero"),
  categoryId: z.string().uuid("Categoria inválida"),
  isPublished: z.boolean().optional().default(false),
});

// Tipagem para os dados a serem processados
type ProductData = z.infer<typeof productSchema>;

// Tipagem para o retorno
type ProductActionResult =
  | { success: true; data: { id: string } }
  | { success: false; error: string | Record<string, string[]> };

// Versão com argumento tipado diretamente
export async function createProduct(
  data: ProductData
): Promise<ProductActionResult> {
  // Verificar autenticação
  const user = await auth();

  if (!user || !user.isAdmin) {
    return {
      success: false,
      error: "Não autorizado",
    };
  }

  try {
    // Validação (redundante, mas garantida)
    const validatedData = productSchema.parse(data);

    // Criar produto
    const product = await db.product.create({
      data: {
        ...validatedData,
        createdById: user.id,
      },
      select: {
        id: true,
      },
    });

    // Revalidar caminhos afetados
    revalidatePath("/products");
    revalidatePath("/admin/products");

    return {
      success: true,
      data: {
        id: product.id,
      },
    };
  } catch (error) {
    console.error("Erro ao criar produto:", error);

    if (error instanceof z.ZodError) {
      return {
        success: false,
        error: error.format(),
      };
    }

    return {
      success: false,
      error: "Falha ao criar produto. Tente novamente.",
    };
  }
}

// Versão com FormData
export async function createProductFromForm(
  formData: FormData
): Promise<ProductActionResult> {
  try {
    // Extrair e validar dados do FormData
    const validationResult = productSchema.safeParse({
      name: formData.get("name"),
      description: formData.get("description"),
      price: Number(formData.get("price")),
      categoryId: formData.get("categoryId"),
      isPublished: formData.get("isPublished") === "on",
    });

    if (!validationResult.success) {
      return {
        success: false,
        error: validationResult.error.format(),
      };
    }

    // Delega para a função principal
    return createProduct(validationResult.data);
  } catch (error) {
    console.error("Erro ao processar formulário:", error);
    return {
      success: false,
      error: "Falha ao processar formulário. Tente novamente.",
    };
  }
}
```

### 3. Server Actions Otimizadas com react-hook-form e TypeScript

```typescript
// app/admin/products/new/page.tsx
import { getCategories } from "@/lib/api/categories";
import { createProductFromForm } from "@/lib/actions/products";
import { ProductForm } from "./_components/ProductForm";

export default async function NewProductPage() {
  // Buscar dados necessários para o formulário
  const categories = await getCategories();

  return (
    <div className="max-w-2xl mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Novo Produto</h1>
      <ProductForm
        submitAction={createProductFromForm}
        categories={categories}
      />
    </div>
  );
}

// app/admin/products/new/_components/ProductForm.tsx
("use client");

import { useState } from "react";
import { useRouter } from "next/navigation";
import { useForm } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { z } from "zod";
import { toast } from "@/components/ui/use-toast";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Select } from "@/components/ui/select";
import { Checkbox } from "@/components/ui/checkbox";

// Schema de validação (deve corresponder ao do Server Action)
const productSchema = z.object({
  name: z.string().min(3, "Nome deve ter pelo menos 3 caracteres"),
  description: z
    .string()
    .min(10, "Descrição deve ter pelo menos 10 caracteres"),
  price: z
    .string()
    .refine((val) => !isNaN(Number(val)) && Number(val) > 0, {
      message: "Preço deve ser um número positivo",
    }),
  categoryId: z.string().uuid("Categoria inválida"),
  isPublished: z.boolean().optional().default(false),
});

type ProductFormValues = z.infer<typeof productSchema>;

interface ProductFormProps {
  submitAction: (formData: FormData) => Promise<{
    success: boolean;
    error?: string | Record<string, string[]>;
    data?: { id: string };
  }>;
  categories: { id: string; name: string }[];
  initialData?: Partial<ProductFormValues>;
}

export function ProductForm({
  submitAction,
  categories,
  initialData,
}: ProductFormProps) {
  const router = useRouter();
  const [isSubmitting, setIsSubmitting] = useState(false);

  const form = useForm<ProductFormValues>({
    resolver: zodResolver(productSchema),
    defaultValues: {
      name: initialData?.name || "",
      description: initialData?.description || "",
      price: initialData?.price?.toString() || "",
      categoryId: initialData?.categoryId || "",
      isPublished: initialData?.isPublished || false,
    },
  });

  const {
    register,
    handleSubmit,
    formState: { errors },
  } = form;

  async function onSubmit(data: ProductFormValues) {
    setIsSubmitting(true);

    try {
      // Criar FormData
      const formData = new FormData();

      // Adicionar campos ao FormData
      Object.entries(data).forEach(([key, value]) => {
        if (key === "isPublished" && value === true) {
          formData.append(key, "on");
        } else if (value !== undefined && value !== null) {
          formData.append(key, value.toString());
        }
      });

      // Chamar Server Action
      const result = await submitAction(formData);

      if (result.success) {
        toast({
          title: "Produto criado com sucesso",
          variant: "success",
        });

        router.push(`/admin/products/${result.data?.id || ""}`);
        router.refresh();
      } else {
        // Tratar erros
        if (typeof result.error === "string") {
          toast({
            title: "Erro",
            description: result.error,
            variant: "destructive",
          });
        } else {
          // Mapear erros de campos específicos
          const formattedErrors = result.error as Record<string, string[]>;

          // Percorrer erros e definir no formulário
          Object.entries(formattedErrors).forEach(([path, messages]) => {
            if (path !== "_errors" && messages?.length > 0) {
              form.setError(path.split(".").pop() as keyof ProductFormValues, {
                message: messages[0],
              });
            }
          });

          // Mostrar erro geral se houver
          const generalErrors = formattedErrors._errors;
          if (generalErrors?.length > 0) {
            toast({
              title: "Erro de validação",
              description: generalErrors[0],
              variant: "destructive",
            });
          }
        }
      }
    } catch (error) {
      console.error("Erro ao submeter formulário:", error);
      toast({
        title: "Erro",
        description: "Ocorreu um erro inesperado. Tente novamente.",
        variant: "destructive",
      });
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-6">
      <div className="space-y-2">
        <label htmlFor="name" className="text-sm font-medium">
          Nome do Produto
        </label>
        <Input id="name" {...register("name")} aria-invalid={!!errors.name} />
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
          rows={4}
          aria-invalid={!!errors.description}
        />
        {errors.description && (
          <p className="text-sm text-red-500">{errors.description.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="price" className="text-sm font-medium">
          Preço
        </label>
        <div className="relative">
          <span className="absolute left-3 top-1/2 -translate-y-1/2">R$</span>
          <Input
            id="price"
            {...register("price")}
            className="pl-8"
            placeholder="0.00"
            aria-invalid={!!errors.price}
          />
        </div>
        {errors.price && (
          <p className="text-sm text-red-500">{errors.price.message}</p>
        )}
      </div>

      <div className="space-y-2">
        <label htmlFor="categoryId" className="text-sm font-medium">
          Categoria
        </label>
        <Select
          id="categoryId"
          {...register("categoryId")}
          aria-invalid={!!errors.categoryId}
        >
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

      <div className="flex items-center space-x-2">
        <Checkbox id="isPublished" {...register("isPublished")} />
        <label htmlFor="isPublished" className="text-sm">
          Publicar imediatamente
        </label>
      </div>

      <div className="flex justify-end space-x-3">
        <Button type="button" variant="outline" onClick={() => router.back()}>
          Cancelar
        </Button>
        <Button type="submit" disabled={isSubmitting}>
          {isSubmitting ? "Salvando..." : "Salvar Produto"}
        </Button>
      </div>
    </form>
  );
}
```

### 4. Server Actions com Manipulação de Arquivos

```typescript
// lib/actions/uploads.ts
"use server";

import { writeFile } from "fs/promises";
import { join } from "path";
import { nanoid } from "nanoid";
import { auth } from "@/lib/auth";
import { z } from "zod";

// Schemas de validação
const imageSchema = z
  .instanceof(File)
  .refine(
    (file) => file.size > 0 && file.size < 5 * 1024 * 1024, // 5MB
    "O arquivo deve ter menos de 5MB"
  )
  .refine(
    (file) => ["image/jpeg", "image/png", "image/webp"].includes(file.type),
    "Formato de imagem inválido. Use JPEG, PNG ou WebP"
  );

// Tipagem para o retorno
type UploadResult =
  | { success: true; filePath: string; url: string }
  | { success: false; error: string };

export async function uploadProductImage(
  formData: FormData
): Promise<UploadResult> {
  try {
    // Verificar autenticação
    const user = await auth();

    if (!user || !user.isAdmin) {
      return {
        success: false,
        error: "Não autorizado",
      };
    }

    // Obter arquivo
    const file = formData.get("image") as File;

    // Validar arquivo
    const validationResult = imageSchema.safeParse(file);

    if (!validationResult.success) {
      return {
        success: false,
        error: validationResult.error.message,
      };
    }

    // Gerar nome único para o arquivo
    const fileExtension = file.name.split(".").pop();
    const fileName = `${nanoid()}.${fileExtension}`;

    // Definir caminho do arquivo
    const relativePath = `/uploads/products/${fileName}`;
    const absolutePath = join(process.cwd(), "public", relativePath);

    // Ler conteúdo do arquivo
    const fileBuffer = await file.arrayBuffer();

    // Salvar arquivo
    await writeFile(absolutePath, Buffer.from(fileBuffer));

    return {
      success: true,
      filePath: relativePath,
      url: relativePath,
    };
  } catch (error) {
    console.error("Erro ao fazer upload de imagem:", error);
    return {
      success: false,
      error: "Falha ao fazer upload da imagem. Tente novamente.",
    };
  }
}
```

```typescript
// app/admin/products/[id]/images/_components/ImageUploadForm.tsx
"use client";

import { useState, useRef } from "react";
import { useRouter } from "next/navigation";
import { toast } from "@/components/ui/use-toast";
import { Button } from "@/components/ui/button";
import { uploadProductImage } from "@/lib/actions/uploads";

interface ImageUploadFormProps {
  productId: string;
  onSuccess?: (imageUrl: string) => void;
}

export function ImageUploadForm({
  productId,
  onSuccess,
}: ImageUploadFormProps) {
  const [isUploading, setIsUploading] = useState(false);
  const [previewUrl, setPreviewUrl] = useState<string | null>(null);
  const fileInputRef = useRef<HTMLInputElement>(null);
  const router = useRouter();

  // Função para visualizar imagem selecionada
  function handleFileChange(e: React.ChangeEvent<HTMLInputElement>) {
    const file = e.target.files?.[0];

    if (file) {
      // Criar URL temporária para preview
      const tempUrl = URL.createObjectURL(file);
      setPreviewUrl(tempUrl);

      // Limpar URL quando componente desmontar
      return () => URL.revokeObjectURL(tempUrl);
    } else {
      setPreviewUrl(null);
    }
  }

  async function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
    e.preventDefault();
    setIsUploading(true);

    try {
      const formData = new FormData(e.currentTarget);
      formData.append("productId", productId);

      const result = await uploadProductImage(formData);

      if (result.success) {
        toast({
          title: "Imagem enviada com sucesso",
          variant: "success",
        });

        // Limpar formulário
        setPreviewUrl(null);
        if (fileInputRef.current) {
          fileInputRef.current.value = "";
        }

        // Callback de sucesso
        if (onSuccess) {
          onSuccess(result.url);
        }

        // Atualizar interface
        router.refresh();
      } else {
        toast({
          title: "Erro ao enviar imagem",
          description: result.error,
          variant: "destructive",
        });
      }
    } catch (error) {
      console.error("Erro ao enviar imagem:", error);
      toast({
        title: "Erro",
        description: "Ocorreu um erro inesperado. Tente novamente.",
        variant: "destructive",
      });
    } finally {
      setIsUploading(false);
    }
  }

  return (
    <form onSubmit={handleSubmit} className="space-y-4">
      <div className="space-y-2">
        <label htmlFor="image" className="text-sm font-medium">
          Selecione uma imagem
        </label>

        <input
          ref={fileInputRef}
          id="image"
          name="image"
          type="file"
          accept="image/jpeg,image/png,image/webp"
          onChange={handleFileChange}
          className="w-full text-sm text-slate-500
                     file:mr-4 file:py-2 file:px-4
                     file:rounded-md file:border-0
                     file:text-sm file:font-semibold
                     file:bg-primary-50 file:text-primary-700
                     hover:file:bg-primary-100"
          required
        />

        <p className="text-xs text-muted-foreground">
          Formatos aceitos: JPEG, PNG, WebP. Tamanho máximo: 5MB.
        </p>
      </div>

      {previewUrl && (
        <div className="mt-4">
          <p className="text-sm font-medium mb-2">Preview:</p>
          <img
            src={previewUrl}
            alt="Preview"
            className="max-h-40 rounded-md border"
          />
        </div>
      )}

      <Button type="submit" disabled={isUploading || !previewUrl}>
        {isUploading ? "Enviando..." : "Enviar Imagem"}
      </Button>
    </form>
  );
}
```

### 5. Server Actions com Operações em Lote

```typescript
// lib/actions/products-batch.ts
"use server";

import { revalidatePath } from "next/cache";
import { z } from "zod";
import { db } from "@/lib/db";
import { auth } from "@/lib/auth";

// Schema de validação
const batchOperationSchema = z.object({
  productIds: z.array(z.string().uuid()),
  operation: z.enum(["publish", "unpublish", "delete", "moveCategoryTo"]),
  targetCategoryId: z.string().uuid().optional(),
});

type BatchOperationResult = {
  success: boolean;
  processedCount: number;
  error?: string;
};

export async function batchOperationOnProducts(
  formData: FormData
): Promise<BatchOperationResult> {
  try {
    // Verificar autenticação
    const user = await auth();

    if (!user || !user.isAdmin) {
      return {
        success: false,
        processedCount: 0,
        error: "Não autorizado",
      };
    }

    // Extrair IDs de produtos (formato especial serializado)
    const rawProductIds = formData.get("productIds") as string;
    let productIds: string[] = [];

    try {
      // Deserializar string JSON para array
      productIds = JSON.parse(rawProductIds);
    } catch (e) {
      return {
        success: false,
        processedCount: 0,
        error: "IDs de produtos em formato inválido",
      };
    }

    // Validar dados
    const validationResult = batchOperationSchema.safeParse({
      productIds,
      operation: formData.get("operation"),
      targetCategoryId: formData.get("targetCategoryId"),
    });

    if (!validationResult.success) {
      return {
        success: false,
        processedCount: 0,
        error: "Dados de operação inválidos",
      };
    }

    const { operation, targetCategoryId } = validationResult.data;

    // Executar operação com base no tipo
    switch (operation) {
      case "publish":
        await db.product.updateMany({
          where: {
            id: { in: productIds },
          },
          data: {
            isPublished: true,
            publishedAt: new Date(),
          },
        });
        break;

      case "unpublish":
        await db.product.updateMany({
          where: {
            id: { in: productIds },
          },
          data: {
            isPublished: false,
            publishedAt: null,
          },
        });
        break;

      case "delete":
        await db.product.deleteMany({
          where: {
            id: { in: productIds },
          },
        });
        break;

      case "moveCategoryTo":
        if (!targetCategoryId) {
          return {
            success: false,
            processedCount: 0,
            error: "Categoria alvo não especificada",
          };
        }

        // Verificar se categoria existe
        const categoryExists = await db.category.findUnique({
          where: { id: targetCategoryId },
        });

        if (!categoryExists) {
          return {
            success: false,
            processedCount: 0,
            error: "Categoria alvo não existe",
          };
        }

        await db.product.updateMany({
          where: {
            id: { in: productIds },
          },
          data: {
            categoryId: targetCategoryId,
          },
        });
        break;

      default:
        return {
          success: false,
          processedCount: 0,
          error: "Operação não suportada",
        };
    }

    // Revalidar caminhos afetados
    revalidatePath("/products");
    revalidatePath("/admin/products");

    return {
      success: true,
      processedCount: productIds.length,
    };
  } catch (error) {
    console.error("Erro na operação em lote:", error);
    return {
      success: false,
      processedCount: 0,
      error: "Falha ao processar operação em lote. Tente novamente.",
    };
  }
}
```

```typescript
// app/admin/products/_components/ProductBatchActions.tsx
"use client";

import { useState } from "react";
import { useRouter } from "next/navigation";
import { toast } from "@/components/ui/use-toast";
import { Button } from "@/components/ui/button";
import { Select } from "@/components/ui/select";
import { batchOperationOnProducts } from "@/lib/actions/products-batch";

interface ProductBatchActionsProps {
  selectedProductIds: string[];
  categories: { id: string; name: string }[];
  onComplete?: () => void;
}

export function ProductBatchActions({
  selectedProductIds,
  categories,
  onComplete,
}: ProductBatchActionsProps) {
  const [operation, setOperation] = useState("");
  const [targetCategoryId, setTargetCategoryId] = useState("");
  const [isProcessing, setIsProcessing] = useState(false);
  const router = useRouter();

  // Verificar se há produtos selecionados
  const hasSelection = selectedProductIds.length > 0;

  // Mapeamento de operações para rótulos amigáveis
  const operationLabels: Record<string, string> = {
    publish: "Publicar produtos",
    unpublish: "Despublicar produtos",
    delete: "Excluir produtos",
    moveCategoryTo: "Mover para categoria",
  };

  async function handleApplyOperation() {
    if (!operation) {
      toast({
        title: "Operação não selecionada",
        description: "Selecione uma operação para continuar",
        variant: "destructive",
      });
      return;
    }

    if (operation === "moveCategoryTo" && !targetCategoryId) {
      toast({
        title: "Categoria não selecionada",
        description: "Selecione uma categoria de destino",
        variant: "destructive",
      });
      return;
    }

    // Confirmar operação de exclusão
    if (operation === "delete") {
      if (
        !confirm(
          `Tem certeza que deseja excluir ${selectedProductIds.length} produtos?`
        )
      ) {
        return;
      }
    }

    setIsProcessing(true);

    try {
      // Criar FormData para Server Action
      const formData = new FormData();
      formData.append("productIds", JSON.stringify(selectedProductIds));
      formData.append("operation", operation);

      if (targetCategoryId) {
        formData.append("targetCategoryId", targetCategoryId);
      }

      // Chamar Server Action
      const result = await batchOperationOnProducts(formData);

      if (result.success) {
        toast({
          title: "Operação concluída",
          description: `${result.processedCount} produtos processados com sucesso.`,
          variant: "success",
        });

        // Reset seleções
        setOperation("");
        setTargetCategoryId("");

        // Callback opcional
        if (onComplete) {
          onComplete();
        }

        // Atualizar UI
        router.refresh();
      } else {
        toast({
          title: "Erro na operação",
          description:
            result.error || "Ocorreu um erro ao processar a operação.",
          variant: "destructive",
        });
      }
    } catch (error) {
      console.error("Erro ao processar operação em lote:", error);
      toast({
        title: "Erro",
        description: "Ocorreu um erro inesperado. Tente novamente.",
        variant: "destructive",
      });
    } finally {
      setIsProcessing(false);
    }
  }

  // Se não houver produtos selecionados, mostrar mensagem
  if (!hasSelection) {
    return (
      <div className="text-sm text-muted-foreground">
        Selecione produtos para realizar operações em lote
      </div>
    );
  }

  return (
    <div className="flex flex-col sm:flex-row gap-3 items-start sm:items-end">
      <div className="space-y-2 min-w-40">
        <label htmlFor="batch-operation" className="text-sm font-medium">
          Operação em Lote
        </label>
        <Select
          id="batch-operation"
          value={operation}
          onChange={(e) => setOperation(e.target.value)}
          disabled={isProcessing}
        >
          <option value="">Selecione uma operação</option>
          {Object.entries(operationLabels).map(([value, label]) => (
            <option key={value} value={value}>
              {label}
            </option>
          ))}
        </Select>
      </div>

      {operation === "moveCategoryTo" && (
        <div className="space-y-2 min-w-40">
          <label htmlFor="target-category" className="text-sm font-medium">
            Categoria de Destino
          </label>
          <Select
            id="target-category"
            value={targetCategoryId}
            onChange={(e) => setTargetCategoryId(e.target.value)}
            disabled={isProcessing}
          >
            <option value="">Selecione uma categoria</option>
            {categories.map((category) => (
              <option key={category.id} value={category.id}>
                {category.name}
              </option>
            ))}
          </Select>
        </div>
      )}

      <Button
        onClick={handleApplyOperation}
        disabled={
          isProcessing ||
          !operation ||
          (operation === "moveCategoryTo" && !targetCategoryId)
        }
      >
        {isProcessing ? "Processando..." : "Aplicar"}
      </Button>

      <div className="text-sm text-muted-foreground">
        {selectedProductIds.length} produto(s) selecionado(s)
      </div>
    </div>
  );
}
```

## Padrões para Revalidação de Dados

```typescript
// lib/actions/comments.ts
"use server";

import { revalidatePath, revalidateTag } from "next/cache";
import { z } from "zod";
import { db } from "@/lib/db";
import { auth } from "@/lib/auth";

// Schema de validação
const commentSchema = z.object({
  content: z
    .string()
    .min(3, "Comentário deve ter pelo menos 3 caracteres")
    .max(1000),
  postId: z.string().uuid(),
});

export async function addComment(formData: FormData) {
  // Verificar autenticação
  const user = await auth();

  if (!user) {
    return {
      success: false,
      error: "Você precisa estar logado para comentar",
    };
  }

  try {
    // Extrair e validar dados
    const validationResult = commentSchema.safeParse({
      content: formData.get("content"),
      postId: formData.get("postId"),
    });

    if (!validationResult.success) {
      return {
        success: false,
        error: validationResult.error.format(),
      };
    }

    const { content, postId } = validationResult.data;

    // Criar comentário
    const comment = await db.comment.create({
      data: {
        content,
        postId,
        userId: user.id,
      },
    });

    // Revalidar caminhos afetados
    revalidatePath(`/blog/${postId}`); // Revalidar página do post
    revalidateTag(`post-${postId}`); // Revalidar tag específica

    return {
      success: true,
      data: { id: comment.id },
    };
  } catch (error) {
    console.error("Erro ao adicionar comentário:", error);
    return {
      success: false,
      error: "Falha ao adicionar comentário. Tente novamente.",
    };
  }
}
```

## Anti-padrões a Evitar

1. **❌ Expor Informações Sensíveis nos Erros**

   ```typescript
   // Incorreto: Expondo detalhes de erro sensíveis
   export async function register(formData: FormData) {
     try {
       // Processamento de registro...
     } catch (error) {
       console.error("Erro no registro:", error);
       return {
         success: false,
         error: `Erro interno: ${error.message}`, // Pode expor informações sensíveis
       };
     }
   }
   ```

   ✅ Correto: Retornar mensagens de erro genéricas para o cliente

2. **❌ Falta de Validação no Servidor**

   ```typescript
   // Incorreto: Confiando apenas na validação do cliente
   export async function updateProfile(formData: FormData) {
     const name = formData.get("name");
     const bio = formData.get("bio");

     // Atualizar diretamente sem validar
     await db.user.update({
       where: { id: currentUser.id },
       data: { name, bio },
     });

     return { success: true };
   }
   ```

   ✅ Correto: Sempre validar dados no servidor, independente da validação no cliente

3. **❌ Não Tratar Cenários de Concorrência**

   ```typescript
   // Incorreto: Sem controle de concorrência
   export async function updatePost(formData: FormData) {
     const postId = formData.get("id");
     const content = formData.get("content");

     // Atualizar sem verificar versão ou timestamp
     await db.post.update({
       where: { id: postId },
       data: { content },
     });

     return { success: true };
   }
   ```

   ✅ Correto: Utilizar mecanismos como versões ou timestamps para evitar conflitos

4. **❌ Server Actions com Efeitos Colaterais Extensos**

   ```typescript
   // Incorreto: Server Action com muitos efeitos colaterais
   export async function publishArticle(formData: FormData) {
     const articleId = formData.get("id");

     // Publicar artigo
     await db.article.update({
       where: { id: articleId },
       data: { published: true },
     });

     // Notificar todos os usuários (operação pesada)
     const users = await db.user.findMany();
     for (const user of users) {
       await sendNotification(user.email, "Novo artigo publicado!");
     }

     // Gerar relatórios extensos
     await generateReports();

     // Outras operações pesadas...

     return { success: true };
   }
   ```

   ✅ Correto: Manter Server Actions focados e delegar operações pesadas para jobs em background

5. **❌ Não Lidar com Falhas de Forma Adequada**
   ```typescript
   // Incorreto: Sem feedback adequado de erro
   export async function processPayment(formData: FormData) {
     try {
       // Processar pagamento...
       if (/* condição de erro */) {
         return { success: false };  // Sem detalhes do erro
       }

       return { success: true };
     } catch (error) {
       return { success: false };  // Sem detalhes do erro
     }
   }
   ```
   ✅ Correto: Retornar informações de erro específicas e acionáveis para o cliente

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals", "plugin:@typescript-eslint/recommended"],
  "plugins": ["@typescript-eslint"],
  "rules": {
    "no-unused-vars": "off",
    "@typescript-eslint/no-unused-vars": ["warn"],
    "@typescript-eslint/no-explicit-any": "warn",
    "no-console": ["warn", { "allow": ["warn", "error"] }]
  },
  "overrides": [
    {
      "files": ["**/actions/*.ts", "**/actions/**/*.ts"],
      "rules": {
        "no-console": ["warn", { "allow": ["warn", "error"] }],
        "@typescript-eslint/explicit-function-return-type": ["warn"],
        "@typescript-eslint/no-explicit-any": "error"
      }
    }
  ]
}
```

## Quando Aplicar

- Para manipulação segura de formulários no servidor
- Quando precisar acessar recursos protegidos (banco de dados, APIs, etc.)
- Para operações de autenticação e autorização
- Em cenários que exigem validação rigorosa de dados
- Para manipulação de arquivos e uploads
- Quando precisar revalidar cache após mutações
- Para comunicação cliente-servidor sem criar endpoints API separados
