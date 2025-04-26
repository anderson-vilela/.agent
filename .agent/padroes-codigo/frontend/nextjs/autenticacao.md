# Padrões de Autenticação no Next.js App Router

## Descrição

Este documento define os padrões recomendados para implementação de autenticação em aplicações Next.js utilizando o App Router. Abrange estratégias de autenticação, gerenciamento de sessões, proteção de rotas, integração com provedores de identidade, e práticas de segurança. Uma implementação robusta de autenticação é fundamental para proteger recursos, garantir a identidade dos usuários e proporcionar uma experiência personalizada.

## Princípios Fundamentais

1. **Segurança Primeiro**: Priorizar sempre a segurança nas decisões de implementação
2. **Experiência Fluida**: Minimizar fricção no processo de autenticação sem comprometer a segurança
3. **Separação de Responsabilidades**: Manter clara a separação entre autenticação, autorização e lógica de negócio
4. **Consistência**: Adotar uma abordagem uniforme em toda a aplicação
5. **Performance**: Otimizar para minimizar impacto no carregamento e tempo de resposta
6. **Conformidade**: Seguir padrões da indústria e requisitos regulatórios
7. **Flexibilidade**: Permitir múltiplas estratégias de autenticação conforme necessário

## Implementação

### 1. Estrutura Básica com Next-Auth (Auth.js)

A biblioteca recomendada para autenticação em Next.js é o Auth.js (anteriormente NextAuth.js), que oferece suporte a múltiplos provedores e estratégias de autenticação.

#### Configuração Inicial

```typescript
// auth.ts (na raiz do projeto)
import NextAuth from "next-auth";
import { PrismaAdapter } from "@auth/prisma-adapter";
import { PrismaClient } from "@prisma/client";
import CredentialsProvider from "next-auth/providers/credentials";
import GoogleProvider from "next-auth/providers/google";
import GitHubProvider from "next-auth/providers/github";
import bcrypt from "bcryptjs";

const prisma = new PrismaClient();

export const { handlers, auth, signIn, signOut } = NextAuth({
  adapter: PrismaAdapter(prisma),
  providers: [
    CredentialsProvider({
      name: "Credentials",
      credentials: {
        email: { label: "Email", type: "email" },
        password: { label: "Senha", type: "password" },
      },
      async authorize(credentials) {
        if (!credentials?.email || !credentials?.password) {
          return null;
        }

        const user = await prisma.user.findUnique({
          where: { email: credentials.email },
        });

        if (!user || !user.passwordHash) {
          return null;
        }

        const passwordValid = await bcrypt.compare(
          credentials.password,
          user.passwordHash
        );

        if (!passwordValid) {
          return null;
        }

        return {
          id: user.id,
          name: user.name,
          email: user.email,
          image: user.image,
          role: user.role,
        };
      },
    }),
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
    }),
    GitHubProvider({
      clientId: process.env.GITHUB_ID!,
      clientSecret: process.env.GITHUB_SECRET!,
    }),
  ],
  callbacks: {
    async jwt({ token, user }) {
      if (user) {
        token.id = user.id;
        token.role = user.role;
      }
      return token;
    },
    async session({ session, token }) {
      if (token && session.user) {
        session.user.id = token.id as string;
        session.user.role = token.role as string;
      }
      return session;
    },
  },
  session: {
    strategy: "jwt",
    maxAge: 30 * 24 * 60 * 60, // 30 dias
  },
  pages: {
    signIn: "/login",
    signOut: "/logout",
    error: "/auth/error",
    verifyRequest: "/auth/verify-request",
    newUser: "/auth/new-user", // Nova conta
  },
  debug: process.env.NODE_ENV === "development",
  secret: process.env.NEXTAUTH_SECRET,
});
```

#### Configuração de Rotas Auth.js

```typescript
// app/api/auth/[...nextauth]/route.ts
import { handlers } from "@/auth";

export const GET = handlers.GET;
export const POST = handlers.POST;
```

### 2. Proteção de Rotas com Middleware

Utilize o middleware do Next.js para proteger rotas e redirecionar usuários não autenticados:

```typescript
// middleware.ts
import { NextResponse } from "next/server";
import { auth } from "@/auth";

export default async function middleware(request) {
  const session = await auth();

  // Verificar se o usuário está autenticado
  if (!session) {
    // Armazenar URL atual para redirecionamento após login
    const url = request.nextUrl.clone();
    url.pathname = "/login";
    url.searchParams.set("callbackUrl", request.nextUrl.pathname);
    return NextResponse.redirect(url);
  }

  // Para rotas que requerem permissões específicas
  if (
    request.nextUrl.pathname.startsWith("/admin") &&
    session.user.role !== "admin"
  ) {
    return NextResponse.redirect(new URL("/unauthorized", request.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: [
    "/dashboard/:path*",
    "/profile/:path*",
    "/admin/:path*",
    "/api/protected/:path*",
  ],
};
```

### 3. Implementação de Formulário de Login

```tsx
// app/(auth)/login/page.tsx
"use client";

import { useState } from "react";
import { useRouter, useSearchParams } from "next/navigation";
import { signIn } from "next-auth/react";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Icons } from "@/components/icons";
import { Alert, AlertDescription } from "@/components/ui/alert";

const loginSchema = z.object({
  email: z.string().email("Email inválido"),
  password: z.string().min(8, "Senha deve ter pelo menos 8 caracteres"),
});

type LoginValues = z.infer<typeof loginSchema>;

export default function LoginPage() {
  const router = useRouter();
  const searchParams = useSearchParams();
  const callbackUrl = searchParams.get("callbackUrl") || "/dashboard";
  const [error, setError] = useState<string | null>(null);
  const [isLoading, setIsLoading] = useState(false);

  const form = useForm<LoginValues>({
    resolver: zodResolver(loginSchema),
    defaultValues: {
      email: "",
      password: "",
    },
  });

  async function onSubmit(data: LoginValues) {
    setIsLoading(true);
    setError(null);

    try {
      const result = await signIn("credentials", {
        redirect: false,
        email: data.email,
        password: data.password,
      });

      if (result?.error) {
        setError("Credenciais inválidas. Verifique seu email e senha.");
        return;
      }

      router.push(callbackUrl);
      router.refresh();
    } catch (error) {
      setError("Ocorreu um erro durante o login. Tente novamente.");
      console.error("Login error:", error);
    } finally {
      setIsLoading(false);
    }
  }

  return (
    <div className="mx-auto max-w-md space-y-6 p-8">
      <div className="space-y-2 text-center">
        <h1 className="text-3xl font-bold">Entrar</h1>
        <p className="text-muted-foreground">
          Entre com suas credenciais para acessar sua conta
        </p>
      </div>

      {error && (
        <Alert variant="destructive">
          <AlertDescription>{error}</AlertDescription>
        </Alert>
      )}

      <Form {...form}>
        <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input
                    placeholder="seu@email.com"
                    type="email"
                    autoComplete="email"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
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
                    placeholder="********"
                    type="password"
                    autoComplete="current-password"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />

          <Button type="submit" className="w-full" disabled={isLoading}>
            {isLoading && (
              <Icons.spinner className="mr-2 h-4 w-4 animate-spin" />
            )}
            Entrar
          </Button>
        </form>
      </Form>

      <div className="relative">
        <div className="absolute inset-0 flex items-center">
          <span className="w-full border-t" />
        </div>
        <div className="relative flex justify-center text-xs uppercase">
          <span className="bg-background px-2 text-muted-foreground">
            Ou continue com
          </span>
        </div>
      </div>

      <div className="flex flex-col space-y-2">
        <Button
          variant="outline"
          type="button"
          onClick={() => signIn("google", { callbackUrl })}
          disabled={isLoading}
        >
          <Icons.google className="mr-2 h-4 w-4" />
          Google
        </Button>
        <Button
          variant="outline"
          type="button"
          onClick={() => signIn("github", { callbackUrl })}
          disabled={isLoading}
        >
          <Icons.github className="mr-2 h-4 w-4" />
          GitHub
        </Button>
      </div>

      <div className="text-center text-sm">
        Não tem uma conta?{" "}
        <Button
          variant="link"
          className="p-0"
          onClick={() => router.push("/register")}
        >
          Registre-se
        </Button>
      </div>
    </div>
  );
}
```

### 4. Implementação de Formulário de Registro

```tsx
// app/(auth)/register/page.tsx
"use client";

import { useState } from "react";
import { useRouter } from "next/navigation";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Icons } from "@/components/icons";
import { Alert, AlertDescription } from "@/components/ui/alert";
import { registerUser } from "@/actions/auth";

const registerSchema = z
  .object({
    name: z.string().min(2, "Nome deve ter pelo menos 2 caracteres"),
    email: z.string().email("Email inválido"),
    password: z
      .string()
      .min(8, "Senha deve ter pelo menos 8 caracteres")
      .regex(
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/,
        "Senha deve conter pelo menos uma letra maiúscula, uma minúscula, um número e um caractere especial"
      ),
    confirmPassword: z.string(),
  })
  .refine((data) => data.password === data.confirmPassword, {
    message: "Senhas não coincidem",
    path: ["confirmPassword"],
  });

type RegisterValues = z.infer<typeof registerSchema>;

export default function RegisterPage() {
  const router = useRouter();
  const [error, setError] = useState<string | null>(null);
  const [isLoading, setIsLoading] = useState(false);

  const form = useForm<RegisterValues>({
    resolver: zodResolver(registerSchema),
    defaultValues: {
      name: "",
      email: "",
      password: "",
      confirmPassword: "",
    },
  });

  async function onSubmit(data: RegisterValues) {
    setIsLoading(true);
    setError(null);

    try {
      const result = await registerUser({
        name: data.name,
        email: data.email,
        password: data.password,
      });

      if (result.error) {
        setError(result.error);
        return;
      }

      // Redirecionar para login ou fazer login automático
      router.push("/login?registered=true");
    } catch (error) {
      setError("Ocorreu um erro durante o registro. Tente novamente.");
      console.error("Register error:", error);
    } finally {
      setIsLoading(false);
    }
  }

  return (
    <div className="mx-auto max-w-md space-y-6 p-8">
      <div className="space-y-2 text-center">
        <h1 className="text-3xl font-bold">Criar Conta</h1>
        <p className="text-muted-foreground">
          Preencha os campos abaixo para criar sua conta
        </p>
      </div>

      {error && (
        <Alert variant="destructive">
          <AlertDescription>{error}</AlertDescription>
        </Alert>
      )}

      <Form {...form}>
        <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
          <FormField
            control={form.control}
            name="name"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Nome</FormLabel>
                <FormControl>
                  <Input
                    placeholder="Seu nome"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />

          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input
                    placeholder="seu@email.com"
                    type="email"
                    autoComplete="email"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
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
                    placeholder="********"
                    type="password"
                    autoComplete="new-password"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />

          <FormField
            control={form.control}
            name="confirmPassword"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Confirmar Senha</FormLabel>
                <FormControl>
                  <Input
                    placeholder="********"
                    type="password"
                    autoComplete="new-password"
                    disabled={isLoading}
                    {...field}
                  />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />

          <Button type="submit" className="w-full" disabled={isLoading}>
            {isLoading && (
              <Icons.spinner className="mr-2 h-4 w-4 animate-spin" />
            )}
            Criar Conta
          </Button>
        </form>
      </Form>

      <div className="text-center text-sm">
        Já tem uma conta?{" "}
        <Button
          variant="link"
          className="p-0"
          onClick={() => router.push("/login")}
        >
          Faça login
        </Button>
      </div>
    </div>
  );
}
```

### 5. Server Actions para Autenticação

```typescript
// actions/auth.ts
"use server";

import { z } from "zod";
import bcrypt from "bcryptjs";
import { PrismaClient } from "@prisma/client";
import { revalidatePath } from "next/cache";
import { redirect } from "next/navigation";
import { signIn, signOut } from "@/auth";

const prisma = new PrismaClient();

const userSchema = z.object({
  name: z.string().min(2),
  email: z.string().email(),
  password: z.string().min(8),
});

export async function registerUser(data: {
  name: string;
  email: string;
  password: string;
}) {
  // Validar dados
  const validation = userSchema.safeParse(data);

  if (!validation.success) {
    return {
      error: "Dados de registro inválidos",
    };
  }

  try {
    // Verificar se o usuário já existe
    const existingUser = await prisma.user.findUnique({
      where: {
        email: data.email,
      },
    });

    if (existingUser) {
      return {
        error: "Email já está em uso",
      };
    }

    // Hash da senha
    const passwordHash = await bcrypt.hash(data.password, 10);

    // Criar usuário
    const user = await prisma.user.create({
      data: {
        name: data.name,
        email: data.email,
        passwordHash,
        role: "user", // Papel padrão
      },
    });

    return {
      success: true,
      userId: user.id,
    };
  } catch (error) {
    console.error("Error registering user:", error);
    return {
      error: "Falha ao registrar usuário",
    };
  }
}

export async function loginUser(prevState: any, formData: FormData) {
  const email = formData.get("email") as string;
  const password = formData.get("password") as string;

  try {
    const result = await signIn("credentials", {
      redirect: false,
      email,
      password,
    });

    if (result?.error) {
      return {
        error: "Credenciais inválidas",
      };
    }

    revalidatePath("/");
    redirect("/dashboard");
  } catch (error) {
    return {
      error: "Falha ao fazer login",
    };
  }
}

export async function logoutUser() {
  await signOut();
  revalidatePath("/");
  redirect("/");
}

export async function updateUserProfile(
  data: {
    name?: string;
    email?: string;
    currentPassword?: string;
    newPassword?: string;
  },
  userId: string
) {
  if (!userId) {
    return {
      error: "Usuário não autenticado",
    };
  }

  try {
    // Se estiver alterando a senha
    if (data.currentPassword && data.newPassword) {
      // Verificar senha atual
      const user = await prisma.user.findUnique({
        where: { id: userId },
        select: { passwordHash: true },
      });

      if (!user) {
        return {
          error: "Usuário não encontrado",
        };
      }

      const passwordValid = await bcrypt.compare(
        data.currentPassword,
        user.passwordHash!
      );

      if (!passwordValid) {
        return {
          error: "Senha atual incorreta",
        };
      }

      // Hash da nova senha
      const newPasswordHash = await bcrypt.hash(data.newPassword, 10);

      // Atualizar senha
      await prisma.user.update({
        where: { id: userId },
        data: { passwordHash: newPasswordHash },
      });
    }

    // Atualizar outros dados do perfil
    const updateData: any = {};

    if (data.name) {
      updateData.name = data.name;
    }

    if (data.email) {
      // Verificar se o email já está em uso
      const existingUser = await prisma.user.findUnique({
        where: {
          email: data.email,
          NOT: {
            id: userId,
          },
        },
      });

      if (existingUser) {
        return {
          error: "Email já está em uso",
        };
      }

      updateData.email = data.email;
    }

    // Atualizar perfil se houver dados para atualizar
    if (Object.keys(updateData).length > 0) {
      await prisma.user.update({
        where: { id: userId },
        data: updateData,
      });
    }

    revalidatePath("/profile");
    return {
      success: true,
    };
  } catch (error) {
    console.error("Error updating user profile:", error);
    return {
      error: "Falha ao atualizar perfil",
    };
  }
}
```

### 6. Componentes de Renderização Condicional baseados em Autenticação

```tsx
// components/auth/auth-status.tsx
"use client";

import { useSession } from "next-auth/react";
import { Button } from "@/components/ui/button";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuItem,
  DropdownMenuSeparator,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";
import { Avatar, AvatarFallback, AvatarImage } from "@/components/ui/avatar";
import { Icons } from "@/components/icons";
import Link from "next/link";
import { logoutUser } from "@/actions/auth";

export function AuthStatus() {
  const { data: session, status } = useSession();
  const user = session?.user;

  if (status === "loading") {
    return (
      <Button variant="ghost" disabled>
        <Icons.spinner className="mr-2 h-4 w-4 animate-spin" />
        Carregando...
      </Button>
    );
  }

  if (!user) {
    return (
      <div className="flex items-center gap-2">
        <Button variant="outline" asChild>
          <Link href="/login">Entrar</Link>
        </Button>
        <Button asChild>
          <Link href="/register">Registrar</Link>
        </Button>
      </div>
    );
  }

  const initials = user.name
    ? user.name
        .split(" ")
        .map((n) => n[0])
        .join("")
        .toUpperCase()
        .substring(0, 2)
    : "U";

  return (
    <DropdownMenu>
      <DropdownMenuTrigger asChild>
        <Button variant="ghost" className="p-1 relative rounded-full">
          <Avatar className="h-8 w-8">
            <AvatarImage src={user.image ?? ""} alt={user.name ?? "User"} />
            <AvatarFallback>{initials}</AvatarFallback>
          </Avatar>
        </Button>
      </DropdownMenuTrigger>
      <DropdownMenuContent align="end" className="w-56">
        <div className="flex items-center justify-start gap-2 p-2">
          <div className="flex flex-col space-y-1 leading-none">
            {user.name && <p className="font-medium">{user.name}</p>}
            {user.email && (
              <p className="text-sm text-muted-foreground">{user.email}</p>
            )}
          </div>
        </div>
        <DropdownMenuSeparator />
        <DropdownMenuItem asChild>
          <Link href="/dashboard" className="w-full cursor-pointer">
            Dashboard
          </Link>
        </DropdownMenuItem>
        <DropdownMenuItem asChild>
          <Link href="/profile" className="w-full cursor-pointer">
            Perfil
          </Link>
        </DropdownMenuItem>
        {user.role === "admin" && (
          <DropdownMenuItem asChild>
            <Link href="/admin" className="w-full cursor-pointer">
              Admin
            </Link>
          </DropdownMenuItem>
        )}
        <DropdownMenuSeparator />
        <DropdownMenuItem
          className="cursor-pointer"
          onSelect={() => {
            logoutUser();
          }}
        >
          Sair
        </DropdownMenuItem>
      </DropdownMenuContent>
    </DropdownMenu>
  );
}
```

### 7. Componente de Provider de Autenticação

```tsx
// components/providers/auth-provider.tsx
"use client";

import { SessionProvider } from "next-auth/react";

export function AuthProvider({ children }: { children: React.ReactNode }) {
  return <SessionProvider>{children}</SessionProvider>;
}
```

### 8. Integração com Layout da Aplicação

```tsx
// app/layout.tsx
import { AuthProvider } from "@/components/providers/auth-provider";
import { ThemeProvider } from "@/components/providers/theme-provider";
import { Toaster } from "@/components/ui/toaster";
import { fontSans } from "@/lib/fonts";
import { cn } from "@/lib/utils";
import "@/styles/globals.css";

export default async function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="pt-BR" suppressHydrationWarning>
      <head />
      <body
        className={cn(
          "min-h-screen bg-background font-sans antialiased",
          fontSans.variable
        )}
      >
        <AuthProvider>
          <ThemeProvider
            attribute="class"
            defaultTheme="system"
            enableSystem
            disableTransitionOnChange
          >
            {children}
            <Toaster />
          </ThemeProvider>
        </AuthProvider>
      </body>
    </html>
  );
}
```

### 9. Hook Customizado de Autenticação no Cliente

```typescript
// hooks/use-auth.ts
"use client";

import { useSession, signIn, signOut } from "next-auth/react";
import { useState, useCallback } from "react";

export function useAuth() {
  const { data: session, status, update: updateSession } = useSession();
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const login = useCallback(
    async (email: string, password: string, callbackUrl?: string) => {
      setIsLoading(true);
      setError(null);

      try {
        const result = await signIn("credentials", {
          redirect: false,
          email,
          password,
        });

        if (result?.error) {
          setError("Credenciais inválidas");
          return false;
        }

        return true;
      } catch (error) {
        setError("Ocorreu um erro durante o login");
        return false;
      } finally {
        setIsLoading(false);
      }
    },
    []
  );

  const logout = useCallback(async () => {
    setIsLoading(true);
    setError(null);

    try {
      await signOut({ redirect: false });
      return true;
    } catch (error) {
      setError("Erro ao fazer logout");
      return false;
    } finally {
      setIsLoading(false);
    }
  }, []);

  const isAuthenticated = status === "authenticated" && !!session;
  const isAdmin = isAuthenticated && session?.user?.role === "admin";

  return {
    user: session?.user,
    isAuthenticated,
    isAdmin,
    isLoading: status === "loading" || isLoading,
    error,
    login,
    logout,
    updateSession,
  };
}
```

### 10. Função de Autorização baseada em Roles

```typescript
// lib/auth-utils.ts
import { auth } from "@/auth";
import { redirect } from "next/navigation";

export async function authorizeUser(requiredRole?: string) {
  const session = await auth();

  if (!session || !session.user) {
    redirect("/login");
  }

  if (requiredRole && session.user.role !== requiredRole) {
    if (requiredRole === "admin" && session.user.role !== "admin") {
      redirect("/unauthorized");
    }
  }

  return session.user;
}

// Exemplo de uso em um Server Component
// app/admin/page.tsx
import { authorizeUser } from "@/lib/auth-utils";

export default async function AdminPage() {
  const user = await authorizeUser("admin");

  return (
    <div>
      <h1>Painel Admin</h1>
      <p>Bem-vindo, {user.name}</p>
      {/* Conteúdo admin... */}
    </div>
  );
}
```

### 11. Componente Server-Side Protegido por Role

```tsx
// components/auth/role-gate.tsx
import { redirect } from "next/navigation";
import { auth } from "@/auth";

interface RoleGateProps {
  children: React.ReactNode;
  allowedRoles: string[];
  fallback?: React.ReactNode;
}

export async function RoleGate({
  children,
  allowedRoles,
  fallback,
}: RoleGateProps) {
  const session = await auth();

  if (!session || !session.user) {
    redirect("/login");
  }

  const userRole = session.user.role;
  const hasAccess = allowedRoles.includes(userRole);

  if (!hasAccess) {
    return fallback ? fallback : null;
  }

  return <>{children}</>;
}

// Exemplo de uso
// app/admin/dashboard/page.tsx
import { RoleGate } from "@/components/auth/role-gate";
import { AccessDenied } from "@/components/auth/access-denied";

export default function AdminDashboardPage() {
  return (
    <RoleGate
      allowedRoles={["admin"]}
      fallback={<AccessDenied message="Acesso restrito a administradores" />}
    >
      <div>
        <h1>Painel Administrativo</h1>
        {/* Conteúdo restrito a administradores */}
      </div>
    </RoleGate>
  );
}
```

### 12. Componente Client-Side Protegido por Role

```tsx
// components/auth/client-role-gate.tsx
"use client";

import { useAuth } from "@/hooks/use-auth";
import { useRouter } from "next/navigation";
import { useEffect } from "react";

interface ClientRoleGateProps {
  children: React.ReactNode;
  allowedRoles: string[];
  fallback?: React.ReactNode;
  redirectTo?: string;
}

export function ClientRoleGate({
  children,
  allowedRoles,
  fallback,
  redirectTo,
}: ClientRoleGateProps) {
  const { user, isAuthenticated, isLoading } = useAuth();
  const router = useRouter();

  useEffect(() => {
    if (!isLoading && !isAuthenticated && redirectTo) {
      router.push(redirectTo);
    }
  }, [isLoading, isAuthenticated, redirectTo, router]);

  if (isLoading) {
    return <div>Carregando...</div>;
  }

  if (!isAuthenticated) {
    return null;
  }

  const hasAccess = user?.role && allowedRoles.includes(user.role);

  if (!hasAccess) {
    return fallback ? fallback : null;
  }

  return <>{children}</>;
}
```

### 13. Fluxo de Recuperação de Senha

```tsx
// app/(auth)/forgot-password/page.tsx
"use client";

import { useState } from "react";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Icons } from "@/components/icons";
import { Alert, AlertDescription } from "@/components/ui/alert";
import { requestPasswordReset } from "@/actions/auth";

const forgotPasswordSchema = z.object({
  email: z.string().email("Email inválido"),
});

type ForgotPasswordValues = z.infer<typeof forgotPasswordSchema>;

export default function ForgotPasswordPage() {
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [error, setError] = useState<string | null>(null);
  const [success, setSuccess] = useState(false);

  const form = useForm<ForgotPasswordValues>({
    resolver: zodResolver(forgotPasswordSchema),
    defaultValues: {
      email: "",
    },
  });

  async function onSubmit(data: ForgotPasswordValues) {
    setIsSubmitting(true);
    setError(null);

    try {
      const result = await requestPasswordReset(data.email);

      if (result.error) {
        setError(result.error);
        return;
      }

      setSuccess(true);
    } catch (error) {
      setError("Ocorreu um erro ao processar sua solicitação");
      console.error("Password reset error:", error);
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <div className="mx-auto max-w-md space-y-6 p-8">
      <div className="space-y-2 text-center">
        <h1 className="text-3xl font-bold">Recuperar Senha</h1>
        <p className="text-muted-foreground">
          Informe seu email para receber um link de recuperação de senha
        </p>
      </div>

      {error && (
        <Alert variant="destructive">
          <AlertDescription>{error}</AlertDescription>
        </Alert>
      )}

      {success ? (
        <Alert className="bg-green-50 border-green-200">
          <AlertDescription>
            Se o email informado estiver cadastrado em nossa base de dados, você
            receberá um link para redefinir sua senha em breve.
          </AlertDescription>
        </Alert>
      ) : (
        <Form {...form}>
          <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
            <FormField
              control={form.control}
              name="email"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Email</FormLabel>
                  <FormControl>
                    <Input
                      placeholder="seu@email.com"
                      type="email"
                      autoComplete="email"
                      disabled={isSubmitting}
                      {...field}
                    />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />

            <Button type="submit" className="w-full" disabled={isSubmitting}>
              {isSubmitting && (
                <Icons.spinner className="mr-2 h-4 w-4 animate-spin" />
              )}
              Enviar Link de Recuperação
            </Button>
          </form>
        </Form>
      )}

      <div className="text-center text-sm">
        <Button variant="link" className="p-0" href="/login">
          Voltar para o login
        </Button>
      </div>
    </div>
  );
}
```

### 14. Página de Reset de Senha

```tsx
// app/(auth)/reset-password/[token]/page.tsx
"use client";

import { useState } from "react";
import { useRouter } from "next/navigation";
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import { z } from "zod";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Icons } from "@/components/icons";
import { Alert, AlertDescription } from "@/components/ui/alert";
import { resetPassword } from "@/actions/auth";

const resetPasswordSchema = z
  .object({
    password: z
      .string()
      .min(8, "Senha deve ter pelo menos 8 caracteres")
      .regex(
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/,
        "Senha deve conter pelo menos uma letra maiúscula, uma minúscula, um número e um caractere especial"
      ),
    confirmPassword: z.string(),
  })
  .refine((data) => data.password === data.confirmPassword, {
    message: "Senhas não coincidem",
    path: ["confirmPassword"],
  });

type ResetPasswordValues = z.infer<typeof resetPasswordSchema>;

export default function ResetPasswordPage({
  params,
}: {
  params: { token: string };
}) {
  const router = useRouter();
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [error, setError] = useState<string | null>(null);
  const [success, setSuccess] = useState(false);

  const form = useForm<ResetPasswordValues>({
    resolver: zodResolver(resetPasswordSchema),
    defaultValues: {
      password: "",
      confirmPassword: "",
    },
  });

  async function onSubmit(data: ResetPasswordValues) {
    setIsSubmitting(true);
    setError(null);

    try {
      const result = await resetPassword(params.token, data.password);

      if (result.error) {
        setError(result.error);
        return;
      }

      setSuccess(true);
      setTimeout(() => {
        router.push("/login");
      }, 3000);
    } catch (error) {
      setError("Ocorreu um erro ao redefinir sua senha");
      console.error("Password reset error:", error);
    } finally {
      setIsSubmitting(false);
    }
  }

  return (
    <div className="mx-auto max-w-md space-y-6 p-8">
      <div className="space-y-2 text-center">
        <h1 className="text-3xl font-bold">Redefinir Senha</h1>
        <p className="text-muted-foreground">Digite sua nova senha abaixo</p>
      </div>

      {error && (
        <Alert variant="destructive">
          <AlertDescription>{error}</AlertDescription>
        </Alert>
      )}

      {success ? (
        <Alert className="bg-green-50 border-green-200">
          <AlertDescription>
            Sua senha foi redefinida com sucesso! Você será redirecionado para a
            página de login em instantes.
          </AlertDescription>
        </Alert>
      ) : (
        <Form {...form}>
          <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
            <FormField
              control={form.control}
              name="password"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Nova Senha</FormLabel>
                  <FormControl>
                    <Input
                      placeholder="********"
                      type="password"
                      autoComplete="new-password"
                      disabled={isSubmitting}
                      {...field}
                    />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />

            <FormField
              control={form.control}
              name="confirmPassword"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Confirmar Nova Senha</FormLabel>
                  <FormControl>
                    <Input
                      placeholder="********"
                      type="password"
                      autoComplete="new-password"
                      disabled={isSubmitting}
                      {...field}
                    />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />

            <Button type="submit" className="w-full" disabled={isSubmitting}>
              {isSubmitting && (
                <Icons.spinner className="mr-2 h-4 w-4 animate-spin" />
              )}
              Redefinir Senha
            </Button>
          </form>
        </Form>
      )}
    </div>
  );
}
```

### 15. Implementação de Verificação de Email

```typescript
// actions/verification.ts
"use server";

import { v4 as uuidv4 } from "uuid";
import { PrismaClient } from "@prisma/client";
import { sendEmail } from "@/lib/email";
import { auth } from "@/auth";

const prisma = new PrismaClient();

export async function sendVerificationEmail() {
  const session = await auth();

  if (!session?.user?.id) {
    return {
      error: "Usuário não autenticado",
    };
  }

  try {
    const user = await prisma.user.findUnique({
      where: { id: session.user.id },
      select: { email: true, emailVerified: true },
    });

    if (!user) {
      return {
        error: "Usuário não encontrado",
      };
    }

    if (user.emailVerified) {
      return {
        error: "Email já verificado",
      };
    }

    // Gerar token de verificação
    const token = uuidv4();
    const expires = new Date();
    expires.setHours(expires.getHours() + 24); // Expira em 24 horas

    // Salvar token no banco de dados
    await prisma.verificationToken.create({
      data: {
        identifier: user.email,
        token,
        expires,
      },
    });

    // Enviar email de verificação
    const verificationUrl = `${process.env.NEXT_PUBLIC_APP_URL}/verify-email/${token}`;

    await sendEmail({
      to: user.email,
      subject: "Verifique seu email",
      html: `<p>Clique no link abaixo para verificar seu email:</p>
             <p><a href="${verificationUrl}">Verificar Email</a></p>
             <p>Este link expira em 24 horas.</p>`,
    });

    return {
      success: true,
    };
  } catch (error) {
    console.error("Error sending verification email:", error);
    return {
      error: "Falha ao enviar email de verificação",
    };
  }
}

export async function verifyEmail(token: string) {
  try {
    // Buscar token
    const verificationToken = await prisma.verificationToken.findUnique({
      where: { token },
    });

    if (!verificationToken) {
      return {
        error: "Token de verificação inválido",
      };
    }

    // Verificar se o token expirou
    if (new Date() > verificationToken.expires) {
      // Remover token expirado
      await prisma.verificationToken.delete({
        where: { token },
      });

      return {
        error: "Token de verificação expirado",
      };
    }

    // Atualizar status de verificação do usuário
    await prisma.user.update({
      where: { email: verificationToken.identifier },
      data: { emailVerified: new Date() },
    });

    // Remover token usado
    await prisma.verificationToken.delete({
      where: { token },
    });

    return {
      success: true,
    };
  } catch (error) {
    console.error("Error verifying email:", error);
    return {
      error: "Falha ao verificar email",
    };
  }
}
```

### 16. Implementação de Autenticação Multi-fator (MFA)

```typescript
// lib/mfa.ts
import { authenticator } from "otplib";
import { PrismaClient } from "@prisma/client";
import QRCode from "qrcode";

const prisma = new PrismaClient();

// Gerar segredo TOTP para o usuário
export async function generateTOTPSecret(userId: string) {
  const secret = authenticator.generateSecret();
  const user = await prisma.user.findUnique({
    where: { id: userId },
    select: { email: true, name: true },
  });

  if (!user) {
    throw new Error("Usuário não encontrado");
  }

  const appName = process.env.MFA_APP_NAME || "Minha Aplicação";
  const otpauth = authenticator.keyuri(user.email, appName, secret);

  // Salvar segredo temporariamente
  await prisma.user.update({
    where: { id: userId },
    data: {
      mfaSecret: secret,
      mfaEnabled: false, // Ainda não está ativado
    },
  });

  // Gerar QR code
  const qrCode = await QRCode.toDataURL(otpauth);

  return {
    secret,
    qrCode,
  };
}

// Verificar código TOTP
export async function verifyTOTP(userId: string, token: string) {
  const user = await prisma.user.findUnique({
    where: { id: userId },
    select: { mfaSecret: true },
  });

  if (!user || !user.mfaSecret) {
    return false;
  }

  try {
    const isValid = authenticator.verify({
      token,
      secret: user.mfaSecret,
    });

    return isValid;
  } catch (error) {
    console.error("TOTP verification error:", error);
    return false;
  }
}

// Ativar MFA para o usuário
export async function enableMFA(userId: string, token: string) {
  const isValid = await verifyTOTP(userId, token);

  if (!isValid) {
    return {
      success: false,
      error: "Código inválido",
    };
  }

  // Ativar MFA no perfil do usuário
  await prisma.user.update({
    where: { id: userId },
    data: { mfaEnabled: true },
  });

  // Gerar códigos de recuperação
  const recoveryCodes = generateRecoveryCodes();

  // Salvar códigos de recuperação
  await prisma.mfaRecoveryCodes.deleteMany({
    where: { userId },
  });

  await Promise.all(
    recoveryCodes.map(async (code) => {
      await prisma.mfaRecoveryCodes.create({
        data: {
          userId,
          code,
          used: false,
        },
      });
    })
  );

  return {
    success: true,
    recoveryCodes,
  };
}

// Desativar MFA para o usuário
export async function disableMFA(userId: string) {
  await prisma.user.update({
    where: { id: userId },
    data: {
      mfaEnabled: false,
      mfaSecret: null,
    },
  });

  // Remover códigos de recuperação existentes
  await prisma.mfaRecoveryCodes.deleteMany({
    where: { userId },
  });

  return { success: true };
}

// Gerar códigos de recuperação
function generateRecoveryCodes(count = 10, length = 8) {
  const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
  const codes = [];

  for (let i = 0; i < count; i++) {
    let code = "";
    for (let j = 0; j < length; j++) {
      code += chars.charAt(Math.floor(Math.random() * chars.length));
    }

    // Adicionar hífens para legibilidade
    if (length > 4) {
      code = code.slice(0, 4) + "-" + code.slice(4);
    }

    codes.push(code);
  }

  return codes;
}
```

## Anti-padrões a Evitar

### 1. Armazenamento inseguro de credenciais

❌ **Não faça isso**:

```typescript
// Armazenar senhas em texto simples
await prisma.user.create({
  data: {
    email: data.email,
    password: data.password, // Senha em texto simples
  },
});
```

✅ **Prefira**:

```typescript
// Usar hash com salt
import bcrypt from "bcryptjs";

const passwordHash = await bcrypt.hash(data.password, 10);

await prisma.user.create({
  data: {
    email: data.email,
    passwordHash, // Senha com hash seguro
  },
});
```

### 2. Expor detalhes de erro para o cliente

❌ **Não faça isso**:

```typescript
try {
  // Lógica de autenticação
} catch (error) {
  return {
    error: `Erro ao fazer login: ${error.message}`, // Expõe detalhes internos
  };
}
```

✅ **Prefira**:

```typescript
try {
  // Lógica de autenticação
} catch (error) {
  console.error("Login error:", error); // Log detalhado apenas no servidor
  return {
    error: "Ocorreu um erro durante o login. Tente novamente.",
  };
}
```

### 3. Não usar CSRF Protection

❌ **Não faça isso**:

```typescript
// Implementar autenticação sem proteção CSRF
```

✅ **Prefira**:

```typescript
// auth.ts
import NextAuth from "next-auth";

export const { handlers, auth, signIn, signOut } = NextAuth({
  // Outras configurações...
  secret: process.env.NEXTAUTH_SECRET, // Usado para assinar cookies e tokens JWT
});
```

### 4. Armazenar tokens JWT inseguros

❌ **Não faça isso**:

```typescript
// Configuração com tokens JWT inseguros
export const authOptions = {
  session: {
    strategy: "jwt",
    maxAge: 365 * 24 * 60 * 60, // 1 ano (muito longo)
  },
  // Sem rotação de tokens ou expiração adequada
};
```

✅ **Prefira**:

```typescript
// Configuração com tokens JWT seguros
export const authOptions = {
  session: {
    strategy: "jwt",
    maxAge: 24 * 60 * 60, // 24 horas
  },
  callbacks: {
    async jwt({ token, user }) {
      // Adicionar verificações adicionais aqui se necessário
      return token;
    },
  },
};
```

### 5. Implementar validação apenas no cliente

❌ **Não faça isso**:

```typescript
// Validação apenas no cliente com React Hook Form
const form = useForm({
  defaultValues: {
    email: "",
    password: "",
  },
});

// Sem validação no servidor
async function handleLogin(data) {
  // Lógica direta sem validação adicional no servidor
}
```

✅ **Prefira**:

```typescript
// Validação tanto no cliente quanto no servidor
// Cliente
const form = useForm({
  resolver: zodResolver(loginSchema),
  defaultValues: {
    email: "",
    password: "",
  },
});

// Servidor
("use server");
// Validar novamente no servidor
const validation = loginSchema.safeParse(formData);
if (!validation.success) {
  return { error: "Dados inválidos" };
}
```

### 6. Não renovar sessões corretamente

❌ **Não faça isso**:

```typescript
// Sem estratégia de renovação de sessão
```

✅ **Prefira**:

```typescript
export const authOptions = {
  callbacks: {
    async session({ session, token }) {
      // Verificar se o token ainda é válido
      // Atualizar informações da sessão se necessário
      return session;
    },
  },
};
```

### 7. Misturar estratégias de autenticação incompatíveis

❌ **Não faça isso**:

```typescript
// Misturar JWT com sessions baseadas em banco de dados incorretamente
export const authOptions = {
  adapter: PrismaAdapter(prisma),
  session: {
    strategy: "jwt", // Conflito potencial
  },
  // Configurações que assumem ambas estratégias
};
```

✅ **Prefira**:

```typescript
// Escolher uma estratégia clara e configurar adequadamente
export const authOptions = {
  adapter: PrismaAdapter(prisma),
  session: {
    strategy: "database", // Para usar sessions baseadas em banco
    // OU
    // strategy: "jwt", // Para usar apenas JWT sem persistência no banco
  },
  // Configurações consistentes com a estratégia escolhida
};
```

### 8. Não implementar rate limiting

❌ **Não faça isso**:

```typescript
// Endpoint de login sem proteção contra tentativas excessivas
```

✅ **Prefira**:

```typescript
import { Ratelimit } from "@upstash/ratelimit";
import { Redis } from "@upstash/redis";

const ratelimit = new Ratelimit({
  redis: Redis.fromEnv(),
  limiter: Ratelimit.slidingWindow(5, "60 s"),
});

export async function POST(request) {
  const ip = request.headers.get("x-forwarded-for") || "anonymous";
  const { success, limit, reset, remaining } = await ratelimit.limit(ip);

  if (!success) {
    return new Response("Too many login attempts. Try again later.", {
      status: 429,
    });
  }

  // Prosseguir com a lógica de login
}
```

## Configuração do ESLint Recomendada

```json
{
  "extends": ["next/core-web-vitals", "plugin:security/recommended"],
  "plugins": ["security"],
  "rules": {
    "security/detect-possible-timing-attacks": "error",
    "security/detect-non-literal-regexp": "warn",
    "security/detect-unsafe-regex": "error",
    "security/detect-buffer-noassert": "error",
    "security/detect-child-process": "warn",
    "security/detect-eval-with-expression": "error",
    "security/detect-pseudoRandomBytes": "warn",
    "no-console": ["warn", { "allow": ["warn", "error"] }]
  }
}
```

## Quando Aplicar

- Em qualquer aplicação que requer autenticação de usuários
- Quando precisar proteger rotas e recursos confidenciais
- Ao implementar funcionalidades específicas para usuários autenticados
- Para aplicações com diferentes níveis de acesso e permissões
- Ao lidar com dados sensíveis dos usuários
- Quando a aplicação precisa manter estado de sessão entre requisições
- Para integração com provedores de identidade externos
- Em aplicações que requerem autenticação multi-fator
- Para conformidade com regulamentos de proteção de dados
- Quando implementar flows de self-service (registro, recuperação de senha)

## Considerações de Segurança Adicionais

1. **Proteção contra CSRF**: Next.js inclui proteção CSRF por padrão, mas certifique-se de que está corretamente configurada.
2. **Uso de HTTPS**: Sempre use HTTPS em produção para proteger dados em trânsito.
3. **Segurança de Cookies**: Configure cookies com flags HttpOnly, Secure e SameSite.
4. **Atualizações Regulares**: Mantenha dependências atualizadas para evitar vulnerabilidades conhecidas.
5. **Testes de Segurança**: Realize testes de penetração e auditorias de segurança regularmente.
6. **Logs de Auditoria**: Implemente logs de atividades relacionadas à autenticação para rastreabilidade.
7. **Monitoramento de Atividades Suspeitas**: Detecte e bloqueie tentativas de login suspeitas.
8. **Compliance**: Garanta conformidade com regulamentos como GDPR, LGPD, etc.
9. **Treinamento da Equipe**: Eduque sua equipe sobre boas práticas de segurança.

## Referências

- [Next.js Auth.js (NextAuth.js) Documentação](https://authjs.dev/reference/nextjs)
- [OWASP Authentication Best Practices](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [NIST Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
- [Next.js Middleware Documentation](https://nextjs.org/docs/app/building-your-application/routing/middleware)
- [JWT Best Practices](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-jwt-bcp-07)
- [GDPR Compliance for Authentication](https://gdpr.eu/right-to-be-forgotten/)

## Exemplos de Aplicação Completa

Consulte nosso repositório de exemplos para implementações completas de autenticação:

- Autenticação básica com credenciais
- Fluxo completo com provedores OAuth
- Autenticação multi-fator
- Gerenciamento de permissões baseado em roles
- Implementação de recuperação de senha
- Verificação de email
