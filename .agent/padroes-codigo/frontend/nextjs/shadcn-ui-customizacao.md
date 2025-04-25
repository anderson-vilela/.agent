# shadcn/ui Customização

## Descrição

Este documento descreve os padrões recomendados para customização e extensão dos componentes do shadcn/ui em aplicações Next.js. O shadcn/ui é uma coleção de componentes reutilizáveis baseados no Radix UI, projetados para serem acessíveis, customizáveis e com bom desempenho, utilizando Tailwind CSS para estilização.

## Princípios Fundamentais

- **Código-fonte disponível**: Aproveite o modelo de "não é uma dependência" para customização total
- **Design system consistente**: Mantenha uma experiência visual e comportamental unificada
- **Acessibilidade**: Preserve os atributos de acessibilidade dos componentes originais
- **Composabilidade**: Crie componentes complexos a partir de primitivos mais simples
- **Personalização incremental**: Modifique apenas o necessário, mantendo a base estável

## Implementação

### 1. Instalação e setup inicial

Configure o shadcn/ui em seu projeto Next.js usando a CLI:

```bash
# Instalar CLI do shadcn/ui
npm install -D @shadcn/ui

# Inicializar configuração (interativo)
npx shadcn-ui init
```

Ou usando a abordagem manual, configurando o Tailwind CSS e o arquivo `components.json`:

```json
// components.json
{
  "$schema": "https://ui.shadcn.com/schema.json",
  "style": "default",
  "rsc": true,
  "tsx": true,
  "tailwind": {
    "config": "tailwind.config.js",
    "css": "app/globals.css",
    "baseColor": "slate",
    "cssVariables": true
  },
  "aliases": {
    "components": "@/components",
    "utils": "@/lib/utils"
  }
}
```

### 2. Modificação do tema base

Customize as variáveis CSS para o tema global no arquivo de estilos globais:

```css
/* app/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 222.2 84% 4.9%;

    --card: 0 0% 100%;
    --card-foreground: 222.2 84% 4.9%;

    --popover: 0 0% 100%;
    --popover-foreground: 222.2 84% 4.9%;

    --primary: 221.2 83.2% 53.3%;
    --primary-foreground: 210 40% 98%;

    --secondary: 210 40% 96.1%;
    --secondary-foreground: 222.2 47.4% 11.2%;

    --muted: 210 40% 96.1%;
    --muted-foreground: 215.4 16.3% 46.9%;

    --accent: 210 40% 96.1%;
    --accent-foreground: 222.2 47.4% 11.2%;

    --destructive: 0 84.2% 60.2%;
    --destructive-foreground: 210 40% 98%;

    --border: 214.3 31.8% 91.4%;
    --input: 214.3 31.8% 91.4%;
    --ring: 221.2 83.2% 53.3%;

    --radius: 0.5rem;
  }

  .dark {
    --background: 222.2 84% 4.9%;
    --foreground: 210 40% 98%;

    --card: 222.2 84% 4.9%;
    --card-foreground: 210 40% 98%;

    --popover: 222.2 84% 4.9%;
    --popover-foreground: 210 40% 98%;

    --primary: 217.2 91.2% 59.8%;
    --primary-foreground: 222.2 47.4% 11.2%;

    --secondary: 217.2 32.6% 17.5%;
    --secondary-foreground: 210 40% 98%;

    --muted: 217.2 32.6% 17.5%;
    --muted-foreground: 215 20.2% 65.1%;

    --accent: 217.2 32.6% 17.5%;
    --accent-foreground: 210 40% 98%;

    --destructive: 0 62.8% 30.6%;
    --destructive-foreground: 210 40% 98%;

    --border: 217.2 32.6% 17.5%;
    --input: 217.2 32.6% 17.5%;
    --ring: 224.3 76.3% 48%;
  }
}

@layer base {
  * {
    @apply border-border;
  }
  body {
    @apply bg-background text-foreground;
  }
}
```

### 3. Criação de tema personalizado

Para aplicações com múltiplos temas, considere criar um sistema de temas:

```tsx
// lib/themes.ts
import { type ClassValue, clsx } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}

export const themes = {
  default: "light",
  list: ["light", "dark", "brand", "accent"] as const,
};

export type Theme = (typeof themes.list)[number];

export const getThemeClass = (theme: Theme) => {
  return theme === "light" ? "" : theme;
};

export function useTheme() {
  // Implementação usando React context ou similar
  // para permitir troca de temas em tempo real
}
```

### 4. Extensão e customização de componentes específicos

Exemplo de modificação do componente Button para incluir variantes adicionais:

```tsx
// components/ui/button.tsx
import * as React from "react";
import { Slot } from "@radix-ui/react-slot";
import { cva, type VariantProps } from "class-variance-authority";

import { cn } from "@/lib/utils";

const buttonVariants = cva(
  "inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive:
          "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline:
          "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        secondary:
          "bg-secondary text-secondary-foreground hover:bg-secondary/80",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",
        // Variante personalizada adicional
        brand:
          "bg-blue-600 text-white hover:bg-blue-700 dark:bg-blue-500 dark:hover:bg-blue-600",
        // Variante alternativa com gradiente
        gradient:
          "bg-gradient-to-r from-blue-600 to-indigo-600 text-white hover:from-blue-700 hover:to-indigo-700",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 rounded-md px-3",
        lg: "h-11 rounded-md px-8",
        xl: "h-12 rounded-md px-10 text-base",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
);

export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean;
}

const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    const Comp = asChild ? Slot : "button";
    return (
      <Comp
        className={cn(buttonVariants({ variant, size, className }))}
        ref={ref}
        {...props}
      />
    );
  }
);
Button.displayName = "Button";

export { Button, buttonVariants };
```

### 5. Criação de componentes compostos

Expandindo componentes existentes para criar interfaces mais complexas:

```tsx
// components/ui/data-card.tsx
import * as React from "react";
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { cn } from "@/lib/utils";

interface DataCardProps extends React.HTMLAttributes<HTMLDivElement> {
  title: string;
  description?: string;
  footer?: React.ReactNode;
  action?: {
    label: string;
    onClick: () => void;
    variant?:
      | "default"
      | "outline"
      | "secondary"
      | "ghost"
      | "link"
      | "destructive";
  };
  icon?: React.ReactNode;
}

export function DataCard({
  title,
  description,
  className,
  footer,
  action,
  icon,
  children,
  ...props
}: DataCardProps) {
  return (
    <Card className={cn("overflow-hidden", className)} {...props}>
      <CardHeader className="flex flex-row items-center gap-4">
        {icon && <div className="rounded-full p-2 bg-muted">{icon}</div>}
        <div className="flex-1">
          <CardTitle>{title}</CardTitle>
          {description && <CardDescription>{description}</CardDescription>}
        </div>
        {action && (
          <Button
            variant={action.variant || "outline"}
            size="sm"
            onClick={action.onClick}
          >
            {action.label}
          </Button>
        )}
      </CardHeader>
      <CardContent>{children}</CardContent>
      {footer && <CardFooter>{footer}</CardFooter>}
    </Card>
  );
}
```

### 6. Integração com formulários

Criando componentes de formulário que estendem os componentes básicos do shadcn/ui:

```tsx
// components/ui/form-field.tsx
import * as React from "react";
import { useFormContext, Controller } from "react-hook-form";
import {
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";
import { cn } from "@/lib/utils";

interface FormInputFieldProps
  extends React.InputHTMLAttributes<HTMLInputElement> {
  name: string;
  label?: string;
  description?: string;
}

export function FormInputField({
  name,
  label,
  description,
  className,
  ...props
}: FormInputFieldProps) {
  const { control } = useFormContext();

  return (
    <FormField
      control={control}
      name={name}
      render={({ field }) => (
        <FormItem>
          {label && <FormLabel>{label}</FormLabel>}
          <FormControl>
            <Input className={cn(className)} {...props} {...field} />
          </FormControl>
          {description && <FormDescription>{description}</FormDescription>}
          <FormMessage />
        </FormItem>
      )}
    />
  );
}
```

### 7. Criação de derivações específicas para domínio

Adaptando componentes para necessidades específicas do domínio:

```tsx
// components/ui/marketing-button.tsx
import { Button, ButtonProps } from "@/components/ui/button";
import { cn } from "@/lib/utils";
import { ArrowRight } from "lucide-react";

interface MarketingButtonProps extends ButtonProps {
  showArrow?: boolean;
  arrowIcon?: React.ReactNode;
}

export function MarketingButton({
  children,
  className,
  showArrow = true,
  arrowIcon,
  ...props
}: MarketingButtonProps) {
  return (
    <Button
      className={cn(
        "group relative overflow-hidden px-6 transition-all duration-300 ease-out hover:pl-4 hover:pr-8",
        className
      )}
      {...props}
    >
      <span className="relative z-10">{children}</span>
      {showArrow && (
        <span className="absolute right-3 top-1/2 -translate-y-1/2 translate-x-full opacity-0 transition-all duration-200 ease-out group-hover:translate-x-0 group-hover:opacity-100">
          {arrowIcon || <ArrowRight className="h-4 w-4" />}
        </span>
      )}
    </Button>
  );
}
```

### 8. Sistema de tokens de design

Crie um sistema de design tokens consistente para usar com shadcn/ui:

```tsx
// lib/design-tokens.ts
export const spacing = {
  0: "0px",
  0.5: "0.125rem",
  1: "0.25rem",
  1.5: "0.375rem",
  2: "0.5rem",
  2.5: "0.625rem",
  3: "0.75rem",
  3.5: "0.875rem",
  4: "1rem",
  5: "1.25rem",
  6: "1.5rem",
  8: "2rem",
  10: "2.5rem",
  12: "3rem",
  16: "4rem",
  20: "5rem",
  24: "6rem",
};

export const fontWeights = {
  thin: "100",
  extralight: "200",
  light: "300",
  normal: "400",
  medium: "500",
  semibold: "600",
  bold: "700",
  extrabold: "800",
  black: "900",
};

export const fontSizes = {
  xs: "0.75rem",
  sm: "0.875rem",
  base: "1rem",
  lg: "1.125rem",
  xl: "1.25rem",
  "2xl": "1.5rem",
  "3xl": "1.875rem",
  "4xl": "2.25rem",
  "5xl": "3rem",
  "6xl": "3.75rem",
};

export const breakpoints = {
  xs: "320px",
  sm: "640px",
  md: "768px",
  lg: "1024px",
  xl: "1280px",
  "2xl": "1536px",
};

// Usar com tailwind.config.js para manter consistência
```

## Anti-padrões a evitar

### 1. Modificar estruturas internas dos componentes originais

❌ **Não faça isso**:

```tsx
// Modificar diretamente a estrutura interna de componentes
// Isso pode quebrar acessibilidade e comportamentos esperados
function CustomButton() {
  return (
    <div className="button-like" onClick={handleClick}>
      {children}
    </div>
  );
}
```

✅ **Prefira**:

```tsx
// Estender o componente original preservando sua estrutura
import { Button } from "@/components/ui/button";

function CustomButton({ children, ...props }) {
  return (
    <Button className="custom-styles" {...props}>
      {children}
    </Button>
  );
}
```

### 2. Ignorar a acessibilidade dos componentes

❌ **Não faça isso**:

```tsx
// Remover atributos aria ou propriedades relacionadas à acessibilidade
function CustomDialog({ children }) {
  return (
    <div className="dialog" onClick={handleClose}>
      <div>{children}</div>
    </div>
  );
}
```

✅ **Prefira**:

```tsx
// Usar componentes Radix UI que já implementam padrões de acessibilidade
import { Dialog, DialogContent, DialogHeader } from "@/components/ui/dialog";

function CustomDialog({ children, title }) {
  return (
    <Dialog>
      <DialogContent>
        <DialogHeader>{title}</DialogHeader>
        {children}
      </DialogContent>
    </Dialog>
  );
}
```

### 3. Duplicar código ao invés de estender

❌ **Não faça isso**:

```tsx
// Copiar e colar todo o código do componente só para mudar pequenos detalhes
// Cópia completa do Button com pequenas alterações
```

✅ **Prefira**:

```tsx
// Estender apenas o que precisa ser customizado
import { Button, buttonVariants } from "@/components/ui/button";
import { cn } from "@/lib/utils";

function PrimaryActionButton({ className, ...props }) {
  return <Button className={cn("font-bold", className)} {...props} />;
}
```

### 4. Usar inline styles ao invés de Tailwind

❌ **Não faça isso**:

```tsx
<Button style={{ backgroundColor: "#4a5568", padding: "12px 24px" }}>
  Click me
</Button>
```

✅ **Prefira**:

```tsx
<Button className="bg-gray-600 px-6 py-3">Click me</Button>
```

### 5. Mesclar classes de forma insegura

❌ **Não faça isso**:

```tsx
// Concatenar strings de classes diretamente
<Button className={`${buttonVariants} ${className} custom-class`}>
  Click me
</Button>
```

✅ **Prefira**:

```tsx
// Usar a função cn/clsx para lidar com classes condicionais
<Button className={cn(buttonVariants, className, "custom-class")}>
  Click me
</Button>
```

## Configuração de ESLint recomendada

```json
{
  "plugins": ["tailwindcss"],
  "extends": ["plugin:tailwindcss/recommended"],
  "rules": {
    "tailwindcss/no-custom-classname": "warn",
    "tailwindcss/classnames-order": "warn",
    "react/prop-types": "off",
    "react/no-unknown-property": ["error", { "ignore": ["css"] }]
  },
  "settings": {
    "tailwindcss": {
      "callees": ["cn", "clsx", "twMerge"]
    }
  }
}
```

## Quando Aplicar

- Ao iniciar um novo projeto com Next.js que necessita de componentes de UI consistentes
- Quando estiver migrando de outra biblioteca de componentes para shadcn/ui
- Para criar um design system personalizado baseado em shadcn/ui
- Quando precisar adicionar novas variantes a componentes existentes
- Para adaptar componentes a requisitos específicos de marca e design
- Ao implementar temas personalizados ou modo escuro
