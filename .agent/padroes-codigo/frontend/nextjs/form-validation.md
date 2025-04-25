# Padrão para Validação de Formulários com Zod e React Hook Form

## Descrição

Este documento define padrões avançados para implementação de validação de formulários em aplicações Next.js (App Router, versão mais recente) utilizando Zod para definição de esquemas de validação e React Hook Form para gerenciamento de estado e interações do formulário. A combinação dessas ferramentas proporciona uma solução robusta, tipada, escalável e com excelente experiência de desenvolvimento, alinhada às melhores práticas recomendadas pela documentação oficial de cada biblioteca.

## Princípios Fundamentais

1. **Esquemas Reutilizáveis**: Definir esquemas Zod centralizados e compartilháveis entre cliente e servidor.
2. **Tipagem Forte**: Utilizar TypeScript para garantir consistência, autocompletação e segurança de tipos.
3. **Feedback Imediato**: Proporcionar feedback visual instantâneo e específico para o usuário.
4. **Acessibilidade**: Garantir que formulários sejam acessíveis para todos os usuários, seguindo as recomendações do WAI-ARIA.
5. **Integração com Server Actions**: Manter consistência entre validação no cliente e no servidor, utilizando Server Actions do Next.js.
6. **Escalabilidade**: Estruturar os formulários para fácil manutenção e extensão.
7. **Performance**: Otimizar o ciclo de validação para evitar re-renderizações desnecessárias.
8. **Testabilidade**: Garantir que os formulários sejam facilmente testáveis com ferramentas modernas.
9. **Documentação e Padronização**: Documentar padrões, decisões e exemplos para promover reuso e alinhamento entre times.

---

## Estrutura Recomendada de Pastas

```plaintext
.
├── app/
│   └── (auth)/
│       └── login/
│           └── _components/
│               └── LoginForm.tsx
│   └── admin/
│       └── products/
│           └── new/
│               └── _components/
│                   └── ProductForm.tsx
├── lib/
│   └── schemas/
│       ├── user.ts
│       └── product.ts
│   └── actions/
│       ├── auth.ts
│       └── products.ts
├── components/
│   └── ui/
│       ├── form.tsx
│       ├── input.tsx
│       ├── button.tsx
│       ├── checkbox.tsx
│       ├── select.tsx
│       ├── textarea.tsx
│       ├── card.tsx
│       └── use-toast.ts
├── .eslintrc.json
└── ...
```

---

## 1. Definição de Schemas Zod Centralizados

### Exemplo: `lib/schemas/user.ts`

```typescript
import { z } from "zod";

export const loginSchema = z.object({
  email: z.string().email("Email inválido"),
  password: z.string().min(8, "A senha deve ter pelo menos 8 caracteres"),
  rememberMe: z.boolean().optional().default(false),
});

export type LoginFormValues = z.infer<typeof loginSchema>;

export const registerSchema = z
  .object({
    name: z.string().min(2, "Nome deve ter pelo menos 2 caracteres"),
    email: z.string().email("Email inválido"),
    password: z
      .string()
      .min(8, "A senha deve ter pelo menos 8 caracteres")
      .regex(/[A-Z]/, "A senha deve conter pelo menos uma letra maiúscula")
      .regex(/[a-z]/, "A senha deve conter pelo menos uma letra minúscula")
      .regex(/[0-9]/, "A senha deve conter pelo menos um número"),
    confirmPassword: z.string(),
    terms: z.literal(true, {
      errorMap: () => ({ message: "Você deve aceitar os termos e condições" }),
    }),
  })
  .refine((data) => data.password === data.confirmPassword, {
    message: "As senhas não correspondem",
    path: ["confirmPassword"],
  });

export type RegisterFormValues = z.infer<typeof registerSchema>;
```

### Exemplo: `lib/schemas/product.ts`

```typescript
import { z } from "zod";

export const productSchema = z.object({
  name: z.string().min(3, "Nome deve ter pelo menos 3 caracteres").max(100),
  description: z
    .string()
    .min(10, "Descrição deve ter pelo menos 10 caracteres"),
  price: z.coerce.number().positive("Preço deve ser maior que zero"),
  categoryId: z.string().uuid("Categoria inválida"),
  attributes: z
    .array(
      z.object({
        name: z.string().min(1, "Nome do atributo é obrigatório"),
        value: z.string().min(1, "Valor do atributo é obrigatório"),
      })
    )
    .optional()
    .default([]),
  isPublished: z.boolean().optional().default(false),
});

export type ProductFormValues = z.infer<typeof productSchema>;
```

---

## 2. Integração com React Hook Form e Zod Resolver

### Instalação das Dependências

```bash
npm install react-hook-form zod @hookform/resolvers
```

### Exemplo de Uso Básico

```typescript
import { useForm } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { loginSchema, LoginFormValues } from "@/lib/schemas/user";

const form = useForm<LoginFormValues>({
  resolver: zodResolver(loginSchema),
  defaultValues: {
    email: "",
    password: "",
    rememberMe: false,
  },
});
```

---

## 3. Implementação de Formulários Validados

### 3.1 Formulário de Login

#### `app/(auth)/login/_components/LoginForm.tsx`

```typescript
"use client";

import { useState } from "react";
import { useRouter } from "next/navigation";
import { useForm } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { login } from "@/lib/actions/auth";
import { loginSchema, LoginFormValues } from "@/lib/schemas/user";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Checkbox } from "@/components/ui/checkbox";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { toast } from "@/components/ui/use-toast";

export function LoginForm() {
  const router = useRouter();
  const [isSubmitting, setIsSubmitting] = useState(false);

  const form = useForm<LoginFormValues>({
    resolver: zodResolver(loginSchema),
    defaultValues: {
      email: "",
      password: "",
      rememberMe: false,
    },
    mode: "onBlur", // Validação recomendada para performance e UX
  });

  async function onSubmit(values: LoginFormValues) {
    setIsSubmitting(true);

    try {
      const formData = new FormData();
      formData.append("email", values.email);
      formData.append("password", values.password);

      if (values.rememberMe) {
        formData.append("rememberMe", "on");
      }

      const result = await login(formData);

      if (result.success) {
        toast({
          title: "Login realizado com sucesso",
          variant: "success",
        });

        router.push("/dashboard");
        router.refresh();
      } else {
        if (result.field) {
          form.setError(result.field as keyof LoginFormValues, {
            message: result.error,
          });
        } else {
          toast({
            title: "Erro de autenticação",
            description: result.error,
            variant: "destructive",
          });
        }
      }
    } catch (error) {
      console.error("Erro ao processar login:", error);
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
    <Form {...form}>
      <form
        onSubmit={form.handleSubmit(onSubmit)}
        className="space-y-6"
        noValidate
      >
        <FormField
          control={form.control}
          name="email"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Email</FormLabel>
              <FormControl>
                <Input
                  type="email"
                  placeholder="exemplo@email.com"
                  autoComplete="email"
                  aria-invalid={!!form.formState.errors.email}
                  aria-describedby="email-error"
                  {...field}
                />
              </FormControl>
              <FormMessage id="email-error" />
            </FormItem>
          )}
        />

        <FormField
          control={form.control}
          name="password"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Senha</FormLabel>
              <FormControl>
                <Input
                  type="password"
                  placeholder="********"
                  autoComplete="current-password"
                  aria-invalid={!!form.formState.errors.password}
                  aria-describedby="password-error"
                  {...field}
                />
              </FormControl>
              <FormMessage id="password-error" />
            </FormItem>
          )}
        />

        <FormField
          control={form.control}
          name="rememberMe"
          render={({ field }) => (
            <FormItem className="flex flex-row items-center space-x-3 space-y-0">
              <FormControl>
                <Checkbox
                  checked={field.value}
                  onCheckedChange={field.onChange}
                  aria-checked={field.value}
                />
              </FormControl>
              <FormLabel className="text-sm font-normal">
                Lembrar de mim
              </FormLabel>
            </FormItem>
          )}
        />

        <Button type="submit" className="w-full" disabled={isSubmitting}>
          {isSubmitting ? "Entrando..." : "Entrar"}
        </Button>
      </form>
    </Form>
  );
}
```

#### Pontos de Atenção

- Utilize `noValidate` no `<form>` para evitar validação nativa do navegador.
- Sempre utilize `aria-invalid` e `aria-describedby` para acessibilidade.
- Utilize `mode: "onBlur"` ou `"onSubmit"` para evitar validação excessiva.

---

### 3.2 Formulário com Campos Dinâmicos

#### `app/admin/products/new/_components/ProductForm.tsx`

```typescript
"use client";

import { useState } from "react";
import { useRouter } from "next/navigation";
import { useForm, useFieldArray } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { Plus, Trash2 } from "lucide-react";
import { createProductFromForm } from "@/lib/actions/products";
import { productSchema, ProductFormValues } from "@/lib/schemas/product";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Select } from "@/components/ui/select";
import { Checkbox } from "@/components/ui/checkbox";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { toast } from "@/components/ui/use-toast";
import { Card, CardContent } from "@/components/ui/card";

interface ProductFormProps {
  categories: { id: string; name: string }[];
  initialData?: Partial<ProductFormValues>;
}

export function ProductForm({ categories, initialData }: ProductFormProps) {
  const router = useRouter();
  const [isSubmitting, setIsSubmitting] = useState(false);

  const form = useForm<ProductFormValues>({
    resolver: zodResolver(productSchema),
    defaultValues: {
      name: initialData?.name || "",
      description: initialData?.description || "",
      price: initialData?.price || 0,
      categoryId: initialData?.categoryId || "",
      attributes: initialData?.attributes || [],
      isPublished: initialData?.isPublished || false,
    },
    mode: "onBlur",
  });

  const { fields, append, remove } = useFieldArray({
    control: form.control,
    name: "attributes",
  });

  async function onSubmit(values: ProductFormValues) {
    setIsSubmitting(true);

    try {
      const formData = new FormData();

      formData.append("name", values.name);
      formData.append("description", values.description);
      formData.append("price", values.price.toString());
      formData.append("categoryId", values.categoryId);

      if (values.isPublished) {
        formData.append("isPublished", "on");
      }

      if (values.attributes.length > 0) {
        formData.append("attributes", JSON.stringify(values.attributes));
      }

      const result = await createProductFromForm(formData);

      if (result.success) {
        toast({
          title: "Produto criado com sucesso",
          variant: "success",
        });

        router.push(`/admin/products/${result.data?.id || ""}`);
        router.refresh();
      } else {
        const error = result.error;

        if (typeof error === "string") {
          toast({
            title: "Erro",
            description: error,
            variant: "destructive",
          });
        } else {
          const formattedErrors = error as Record<string, string[]>;

          Object.entries(formattedErrors).forEach(([path, messages]) => {
            if (path !== "_errors" && messages?.length > 0) {
              const fieldPath = path.split(".");
              if (fieldPath.length > 1 && fieldPath[0] === "attributes") {
                const index = parseInt(fieldPath[1]);
                const subField = fieldPath[2];

                form.setError(`attributes.${index}.${subField}` as any, {
                  message: messages[0],
                });
              } else {
                form.setError(path as keyof ProductFormValues, {
                  message: messages[0],
                });
              }
            }
          });

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
    <Form {...form}>
      <form
        onSubmit={form.handleSubmit(onSubmit)}
        className="space-y-8"
        noValidate
      >
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
          <FormField
            control={form.control}
            name="name"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Nome do Produto</FormLabel>
                <FormControl>
                  <Input
                    placeholder="Nome do produto"
                    {...field}
                    aria-invalid={!!form.formState.errors.name}
                    aria-describedby="name-error"
                  />
                </FormControl>
                <FormMessage id="name-error" />
              </FormItem>
            )}
          />

          <FormField
            control={form.control}
            name="price"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Preço</FormLabel>
                <FormControl>
                  <div className="relative">
                    <span className="absolute left-3 top-1/2 -translate-y-1/2">
                      R$
                    </span>
                    <Input
                      type="number"
                      step="0.01"
                      min="0"
                      placeholder="0.00"
                      className="pl-8"
                      {...field}
                      aria-invalid={!!form.formState.errors.price}
                      aria-describedby="price-error"
                    />
                  </div>
                </FormControl>
                <FormMessage id="price-error" />
              </FormItem>
            )}
          />
        </div>

        <FormField
          control={form.control}
          name="description"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Descrição</FormLabel>
              <FormControl>
                <Textarea
                  placeholder="Descrição detalhada do produto"
                  rows={4}
                  {...field}
                  aria-invalid={!!form.formState.errors.description}
                  aria-describedby="description-error"
                />
              </FormControl>
              <FormMessage id="description-error" />
            </FormItem>
          )}
        />

        <FormField
          control={form.control}
          name="categoryId"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Categoria</FormLabel>
              <Select
                defaultValue={field.value}
                onValueChange={field.onChange}
                aria-invalid={!!form.formState.errors.categoryId}
                aria-describedby="category-error"
              >
                <option value="">Selecione uma categoria</option>
                {categories.map((category) => (
                  <option key={category.id} value={category.id}>
                    {category.name}
                  </option>
                ))}
              </Select>
              <FormMessage id="category-error" />
            </FormItem>
          )}
        />

        <div className="space-y-4">
          <div className="flex justify-between items-center">
            <h3 className="text-lg font-medium">Atributos</h3>
            <Button
              type="button"
              variant="outline"
              size="sm"
              onClick={() => append({ name: "", value: "" })}
            >
              <Plus className="h-4 w-4 mr-2" />
              Adicionar
            </Button>
          </div>

          {fields.length === 0 ? (
            <p className="text-sm text-muted-foreground">
              Nenhum atributo adicionado.
            </p>
          ) : (
            <div className="space-y-4">
              {fields.map((field, index) => (
                <Card key={field.id}>
                  <CardContent className="p-4">
                    <div className="flex justify-between items-start mb-3">
                      <h4 className="text-sm font-medium">
                        Atributo {index + 1}
                      </h4>
                      <Button
                        type="button"
                        variant="ghost"
                        size="sm"
                        onClick={() => remove(index)}
                        aria-label={`Remover atributo ${index + 1}`}
                      >
                        <Trash2 className="h-4 w-4 text-destructive" />
                      </Button>
                    </div>

                    <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                      <FormField
                        control={form.control}
                        name={`attributes.${index}.name`}
                        render={({ field }) => (
                          <FormItem>
                            <FormLabel>Nome</FormLabel>
                            <FormControl>
                              <Input
                                placeholder="Ex: Cor"
                                {...field}
                                aria-invalid={
                                  !!form.formState.errors.attributes?.[index]
                                    ?.name
                                }
                                aria-describedby={`attr-name-error-${index}`}
                              />
                            </FormControl>
                            <FormMessage id={`attr-name-error-${index}`} />
                          </FormItem>
                        )}
                      />

                      <FormField
                        control={form.control}
                        name={`attributes.${index}.value`}
                        render={({ field }) => (
                          <FormItem>
                            <FormLabel>Valor</FormLabel>
                            <FormControl>
                              <Input
                                placeholder="Ex: Azul"
                                {...field}
                                aria-invalid={
                                  !!form.formState.errors.attributes?.[index]
                                    ?.value
                                }
                                aria-describedby={`attr-value-error-${index}`}
                              />
                            </FormControl>
                            <FormMessage id={`attr-value-error-${index}`} />
                          </FormItem>
                        )}
                      />
                    </div>
                  </CardContent>
                </Card>
              ))}
            </div>
          )}
        </div>

        <FormField
          control={form.control}
          name="isPublished"
          render={({ field }) => (
            <FormItem className="flex flex-row items-center space-x-3 space-y-0">
              <FormControl>
                <Checkbox
                  checked={field.value}
                  onCheckedChange={field.onChange}
                  aria-checked={field.value}
                />
              </FormControl>
              <FormLabel className="font-normal">
                Publicar imediatamente
              </FormLabel>
            </FormItem>
          )}
        />

        <div className="flex justify-end space-x-4">
          <Button type="button" variant="outline" onClick={() => router.back()}>
            Cancelar
          </Button>
          <Button type="submit" disabled={isSubmitting}>
            {isSubmitting ? "Salvando..." : "Salvar Produto"}
          </Button>
        </div>
      </form>
    </Form>
  );
}
```

---

## 4. Integração com Server Actions (Next.js App Router)

- Utilize Server Actions para processar submissão de formulários e garantir validação no servidor.
- Sempre reutilize os mesmos schemas Zod do cliente no servidor.
- Retorne erros estruturados para feedback granular no frontend.

### Exemplo de Server Action

```typescript
// lib/actions/products.ts
"use server";

import { productSchema } from "@/lib/schemas/product";
import { z } from "zod";

export async function createProductFromForm(formData: FormData) {
  try {
    const raw = {
      name: formData.get("name"),
      description: formData.get("description"),
      price: Number(formData.get("price")),
      categoryId: formData.get("categoryId"),
      attributes: formData.get("attributes")
        ? JSON.parse(formData.get("attributes") as string)
        : [],
      isPublished: formData.get("isPublished") === "on",
    };

    const parsed = productSchema.safeParse(raw);

    if (!parsed.success) {
      const formatted = parsed.error.format();
      return { success: false, error: formatted };
    }

    // Persistência no banco de dados...
    const product = await saveProduct(parsed.data);

    return { success: true, data: product };
  } catch (error) {
    return { success: false, error: "Erro inesperado ao criar produto." };
  }
}
```

---

## 5. Anti-padrões a Evitar

1. **❌ Validação Apenas no Cliente**
2. **❌ Esquemas de Validação Duplicados**
3. **❌ Feedback Visual Insuficiente**
4. **❌ Performance Comprometida**
5. **❌ Acessibilidade Ignorada**
6. **❌ Não Utilizar Server Actions**
7. **❌ Não Centralizar Mensagens de Erro**
8. **❌ Não Testar Fluxos de Erro**
9. **❌ Não Utilizar Tipos Inferidos do Zod**
10. **❌ Não Documentar Decisões de Validação**

---

## 6. Acessibilidade

- Utilize sempre `aria-invalid`, `aria-describedby`, `aria-checked` e outros atributos ARIA relevantes.
- Garanta contraste adequado e navegação por teclado.
- Mensagens de erro devem ser claras e associadas ao campo correspondente.
- Utilize componentes de UI que respeitem padrões de acessibilidade.

---

## 7. Testes Automatizados

- Utilize Testing Library para testes de interação e validação.
- Teste fluxos de sucesso, erro de campo, erro geral e acessibilidade.
- Exemplo de teste:

```typescript
import { render, screen, fireEvent } from "@testing-library/react";
import { LoginForm } from "@/app/(auth)/login/_components/LoginForm";

test("exibe erro ao submeter email inválido", async () => {
  render(<LoginForm />);
  fireEvent.change(screen.getByPlaceholderText(/exemplo@email.com/i), {
    target: { value: "invalido" },
  });
  fireEvent.blur(screen.getByPlaceholderText(/exemplo@email.com/i));
  expect(await screen.findByText(/email inválido/i)).toBeInTheDocument();
});
```

---

## 8. Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals", "plugin:react-hook-form/recommended"],
  "plugins": ["react-hook-form"],
  "rules": {
    "react-hook-form/destructuring-formstate": "error",
    "react-hook-form/no-nested-props": "warn",
    "react-hook-form/prefer-register-with-validation-mode": "warn",
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn"
  }
}
```

---

## 9. Boas Práticas Avançadas

- Utilize `useFormContext` para formulários complexos ou multi-step.
- Prefira componentes controlados e desacoplados.
- Centralize mensagens de erro e traduções.
- Utilize lazy validation para campos dependentes.
- Implemente debounce em campos de busca ou autocomplete.
- Documente decisões de validação e regras de negócio.

---

## 10. Exemplos de Formulários Avançados

### Multi-Step Form

```typescript
// Exemplo de uso de useFormContext e FormProvider para multi-step
import { FormProvider, useForm, useFormContext } from "react-hook-form";

function Step1() {
  const { register } = useFormContext();
  return <input {...register("step1Field")} />;
}

function Step2() {
  const { register } = useFormContext();
  return <input {...register("step2Field")} />;
}

export function MultiStepForm() {
  const methods = useForm({
    /* ... */
  });
  return (
    <FormProvider {...methods}>
      <form>{/* Renderizar steps condicionalmente */}</form>
    </FormProvider>
  );
}
```

---

## 11. Referências Oficiais

- [React Hook Form Docs](https://react-hook-form.com/)
- [Zod Docs](https://zod.dev/)
- [Next.js App Router Docs](/vercel/next.js)
- [Acessibilidade WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/)
- [Testing Library Docs](https://testing-library.com/docs/react-testing-library/intro/)

---

## 12. Quando Aplicar

- Para qualquer formulário que requer validação de entrada do usuário.
- Quando for necessário implementar lógica de validação complexa.
- Para manter consistência entre validações no cliente e no servidor.
- Em cenários que exigem feedback imediato ao usuário.
- Para formulários com múltiplos passos ou lógica condicional.
- Quando a experiência do usuário e a acessibilidade são prioridades.
- Em aplicações Next.js com App Router e Server Actions.

---

## 13. Checklist de Qualidade

- [ ] Schemas Zod centralizados e reutilizados.
- [ ] Tipos inferidos do Zod utilizados em todo o código.
- [ ] Feedback visual claro e específico.
- [ ] Acessibilidade garantida.
- [ ] Validação no cliente e no servidor.
- [ ] Testes automatizados cobrindo fluxos de erro e sucesso.
- [ ] ESLint configurado para React Hook Form.
- [ ] Documentação de decisões de validação.
- [ ] Server Actions implementadas para submissão de dados.
- [ ] Performance otimizada (validação onBlur/onSubmit, debounce onde necessário).

---

## 14. Exemplos de Mensagens de Erro Centralizadas

```typescript
export const errorMessages = {
  required: "Este campo é obrigatório",
  email: "Email inválido",
  minLength: (min: number) => `Mínimo de ${min} caracteres`,
  maxLength: (max: number) => `Máximo de ${max} caracteres`,
  passwordMismatch: "As senhas não correspondem",
  // ...
};
```

---

## 15. Estrutura de Componentes de UI

- Todos os componentes de UI devem aceitar props de acessibilidade.
- Mensagens de erro devem ser renderizadas com `role="alert"` para leitores de tela.
- Inputs devem ser associados a labels e mensagens de erro via `htmlFor` e `aria-describedby`.

---

## 16. Observações Finais

- Sempre consulte a documentação oficial das bibliotecas para atualizações.
- Adapte os exemplos conforme a stack e padrões do seu projeto.
- Promova revisões de código focadas em validação, acessibilidade e experiência do usuário.
- Documente padrões e decisões para facilitar onboarding e manutenção.

---

## 17. Sugestão de Templates

- Template de formulário básico
- Template de formulário multi-step
- Template de Server Action com validação Zod
- Template de teste automatizado para formulários

---

## 18. Fluxo de Trabalho Recomendado

1. Definir schema Zod centralizado.
2. Inferir tipos para uso no frontend e backend.
3. Implementar formulário com React Hook Form e zodResolver.
4. Garantir feedback visual e acessibilidade.
5. Submeter dados via Server Action reutilizando schema.
6. Tratar erros específicos e gerais.
7. Testar fluxos de sucesso e erro.
8. Documentar decisões e padrões.
9. Revisar código com foco em validação, UX e acessibilidade.

---

## 19. Exemplo de Formulário Multi-Step com Persistência de Estado

```typescript
// Exemplo simplificado de multi-step com persistência no localStorage
import { useForm, FormProvider } from "react-hook-form";
import { useEffect } from "react";

export function MultiStepForm() {
  const methods = useForm({ defaultValues: { step1: "", step2: "" } });

  useEffect(() => {
    const saved = localStorage.getItem("multiStepForm");
    if (saved) {
      methods.reset(JSON.parse(saved));
    }
  }, []);

  useEffect(() => {
    localStorage.setItem("multiStepForm", JSON.stringify(methods.getValues()));
  }, [methods.watch()]);

  // Renderização dos steps...
}
```

---

## 20. Dicas de Performance

- Utilize `mode: "onBlur"` para evitar validação excessiva.
- Utilize `useMemo` para schemas Zod complexos.
- Prefira componentes desacoplados e memoizados.
- Evite re-renderizações desnecessárias utilizando `Controller` apenas quando necessário.

---

## 21. Considerações sobre Internacionalização

- Centralize mensagens de erro para facilitar tradução.
- Utilize bibliotecas como `next-intl` para internacionalização de formulários.
- Garanta que feedback visual e mensagens estejam no idioma do usuário.

---

## 22. Observações sobre Server Actions

- Sempre trate erros inesperados e retorne mensagens amigáveis.
- Utilize schemas Zod para parsing e validação de dados recebidos.
- Retorne erros estruturados para feedback granular no frontend.

---

## 23. Referências Complementares

- [React Hook Form - Advanced Usage](https://react-hook-form.com/advanced-usage)
- [Zod - Error Formatting](https://zod.dev/?id=error-formatting)
- [Next.js - Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions)
- [React Hook Form - Accessibility](https://react-hook-form.com/get-started#Accessibility)

---

## 24. Conclusão

A validação de formulários em aplicações Next.js modernas deve ser robusta, tipada, acessível e consistente entre cliente e servidor. O uso combinado de Zod, React Hook Form e Server Actions, seguindo os padrões e recomendações deste documento, garante qualidade, escalabilidade e excelente experiência para desenvolvedores e usuários.

---
