---
tags: [react, hooks, frontend, aprendizado]
relacionados: [templates/arquivos/componente-react.md]
dificuldade: intermediário
atualizado: 2025-04-22
---

# Guia: React Hooks Essenciais

## Objetivo de Aprendizado

Entender os principais hooks do React, seus casos de uso corretos e como criar hooks customizados eficientes.

## Pré-requisitos

- Conhecimento básico de React
- Familiaridade com componentes funcionais
- Entendimento de JavaScript ES6+

## Conceitos Fundamentais

### Conceito 1: useState

O useState permite adicionar estado a componentes funcionais.

```jsx
import React, { useState } from "react";

function Counter() {
  // Declara uma variável de estado "count" com valor inicial 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>Clique aqui</button>
    </div>
  );
}
```

**Principais aspectos:**

- A função useState retorna um par: o valor atual do estado e uma função que o atualiza
- O único argumento para useState é o estado inicial
- O estado não precisa ser um objeto, pode ser qualquer tipo
- A função de atualização substitui o valor anterior, não o mescla (diferente do setState em componentes de classe)

### Conceito 2: useEffect

O useEffect permite executar efeitos colaterais em componentes funcionais.

```jsx
import React, { useState, useEffect } from "react";

function WindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    // Função para atualizar o estado
    const handleResize = () => setWidth(window.innerWidth);

    // Adiciona o event listener
    window.addEventListener("resize", handleResize);

    // Função de cleanup que será executada antes do componente desmontar
    // ou antes da próxima execução do efeito
    return () => {
      window.removeEventListener("resize", handleResize);
    };
  }, []); // Array vazio significa que o efeito roda apenas na montagem e desmontagem

  return <p>Largura da janela: {width}px</p>;
}
```

**Principais aspectos:**

- Substitui os ciclos de vida componentDidMount, componentDidUpdate e componentWillUnmount
- O array de dependências controla quando o efeito é executado
- Retornar uma função do efeito permite limpar recursos (eventos, timers, subscrições)
- Múltiplos useEffect podem ser usados para separar lógicas não relacionadas

### Conceito 3: useContext

O useContext permite consumir contextos do React de forma mais simples.

```jsx
import React, { useContext } from "react";

// Criação do contexto
const ThemeContext = React.createContext("light");

function ThemedButton() {
  // Uso do hook useContext para acessar o valor do contexto
  const theme = useContext(ThemeContext);

  return <button className={`btn-${theme}`}>Botão com Tema {theme}</button>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedButton />
    </ThemeContext.Provider>
  );
}
```

**Principais aspectos:**

- Simplifica o consumo de contextos em componentes funcionais
- Substitui o Context.Consumer e componentes HOC
- Permite consumir múltiplos contextos facilmente

### Conceito 4: useReducer

O useReducer é uma alternativa ao useState para estados complexos.

```jsx
import React, { useReducer } from "react";

// Reducer function
function counterReducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: 0 };
    default:
      throw new Error(`Unsupported action type: ${action.type}`);
  }
}

function Counter() {
  // useReducer com estado inicial
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });

  return (
    <div>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
}
```

**Principais aspectos:**

- Útil para estados complexos ou quando o próximo estado depende do anterior
- Segue o padrão do Redux (actions, reducer, dispatch)
- Facilita testes unitários da lógica de estado
- Pode ajudar a evitar dependências circulares em hooks customizados

### Conceito 5: Hooks Customizados

Hooks customizados permitem extrair lógica de componente para funções reutilizáveis.

```jsx
import { useState, useEffect } from "react";

// Hook customizado para obter o tamanho da janela
function useWindowSize() {
  // Estado para armazenar as dimensões
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    // Handler para atualizar o estado
    function handleResize() {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    }

    // Adiciona event listener
    window.addEventListener("resize", handleResize);

    // Remove event listener na limpeza
    return () => window.removeEventListener("resize", handleResize);
  }, []); // Array vazio = executar apenas na montagem

  return windowSize;
}

// Uso do hook customizado
function ResponsiveComponent() {
  const { width, height } = useWindowSize();

  return (
    <div>
      <p>Largura: {width}px</p>
      <p>Altura: {height}px</p>
      {width < 768 ? <MobileView /> : <DesktopView />}
    </div>
  );
}
```

**Principais aspectos:**

- Devem começar com "use" para seguir a convenção
- Permitem compartilhar lógica entre componentes
- Podem usar outros hooks internamente
- Facilitam a separação de responsabilidades

## Aplicação Prática

### Exemplo 1: Formulário com validação

Um exemplo de como usar hooks para gerenciar um formulário com validação.

```jsx
import React, { useState, useEffect } from "react";

// Hook customizado para formulários
function useForm(initialValues, validate) {
  const [values, setValues] = useState(initialValues);
  const [errors, setErrors] = useState({});
  const [touched, setTouched] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);

  // Validação quando os valores mudam e o campo foi tocado
  useEffect(() => {
    if (Object.keys(touched).length > 0) {
      const validationErrors = validate(values);
      setErrors(validationErrors);
    }
  }, [values, touched, validate]);

  // Handler para mudanças nos inputs
  const handleChange = (e) => {
    const { name, value } = e.target;
    setValues({
      ...values,
      [name]: value,
    });
  };

  // Handler para quando o campo perde o foco
  const handleBlur = (e) => {
    const { name } = e.target;
    setTouched({
      ...touched,
      [name]: true,
    });
  };

  // Handler para submissão do formulário
  const handleSubmit = (callback) => (e) => {
    e.preventDefault();
    const validationErrors = validate(values);
    setErrors(validationErrors);
    setTouched(
      Object.keys(values).reduce((acc, key) => ({ ...acc, [key]: true }), {})
    );

    if (Object.keys(validationErrors).length === 0) {
      setIsSubmitting(true);
      callback(values);
    }
  };

  return {
    values,
    errors,
    touched,
    isSubmitting,
    handleChange,
    handleBlur,
    handleSubmit,
  };
}

// Uso do hook de formulário
function SignupForm() {
  // Função de validação
  const validateForm = (values) => {
    const errors = {};

    if (!values.email) {
      errors.email = "Email é obrigatório";
    } else if (!/\S+@\S+\.\S+/.test(values.email)) {
      errors.email = "Email inválido";
    }

    if (!values.password) {
      errors.password = "Senha é obrigatória";
    } else if (values.password.length < 6) {
      errors.password = "Senha deve ter pelo menos 6 caracteres";
    }

    return errors;
  };

  // Uso do hook de formulário
  const { values, errors, touched, handleChange, handleBlur, handleSubmit } =
    useForm({ email: "", password: "" }, validateForm);

  // Handler para submissão bem-sucedida
  const submitForm = (formValues) => {
    console.log("Formulário enviado:", formValues);
    // Aqui você chamaria sua API
  };

  return (
    <form onSubmit={handleSubmit(submitForm)}>
      <div>
        <label htmlFor="email">Email</label>
        <input
          type="email"
          id="email"
          name="email"
          value={values.email}
          onChange={handleChange}
          onBlur={handleBlur}
        />
        {touched.email && errors.email && (
          <span className="error">{errors.email}</span>
        )}
      </div>

      <div>
        <label htmlFor="password">Senha</label>
        <input
          type="password"
          id="password"
          name="password"
          value={values.password}
          onChange={handleChange}
          onBlur={handleBlur}
        />
        {touched.password && errors.password && (
          <span className="error">{errors.password}</span>
        )}
      </div>

      <button type="submit">Cadastrar</button>
    </form>
  );
}
```

## Padrões Comuns e Anti-padrões

### Padrão: Hook de Fetch com Estado de Carregamento

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    let isMounted = true;

    async function fetchData() {
      try {
        setLoading(true);
        const response = await fetch(url);
        if (!response.ok) throw new Error("Falha na requisição");

        const json = await response.json();
        if (isMounted) {
          setData(json);
          setError(null);
        }
      } catch (err) {
        if (isMounted) {
          setError(err.message);
          setData(null);
        }
      } finally {
        if (isMounted) {
          setLoading(false);
        }
      }
    }

    fetchData();

    return () => {
      isMounted = false;
    };
  }, [url]);

  return { data, loading, error };
}
```

### Anti-padrão: Hooks Condicionais

```jsx
// NÃO FAÇA ISSO
function Component({ condition }) {
  // Isso viola as regras dos hooks
  if (condition) {
    const [state, setState] = useState(true);
  }

  // Resto do componente
}
```

**Por que é um problema**: Hooks devem ser chamados na mesma ordem em cada renderização. Condicionais podem alterar essa ordem.

**Correção**:

```jsx
function Component({ condition }) {
  // Sempre chame o hook
  const [state, setState] = useState(condition);

  // Use o estado de forma condicional, não o hook
  useEffect(() => {
    if (condition) {
      // Lógica condicional aqui
    }
  }, [condition]);

  // Resto do componente
}
```

## Perguntas Frequentes

**P**: Quando devo usar useState vs useReducer?
**R**: Use useState para estados simples e independentes. Use useReducer quando o estado for complexo, tiver múltiplos sub-valores inter-relacionados, ou quando o próximo estado depender do estado anterior.

**P**: Como evitar renderizações desnecessárias com hooks?
**R**: Use React.memo para memoizar componentes funcionais, useCallback para memoizar funções e useMemo para memoizar valores calculados.

**P**: Posso usar hooks em componentes de classe?
**R**: Não diretamente. Hooks só funcionam em componentes funcionais. Para componentes de classe, você ainda usa os métodos de ciclo de vida tradicionais.

## Recursos para Aprofundamento

- [Documentação oficial de Hooks do React](https://reactjs.org/docs/hooks-intro.html)
- [Regras dos Hooks](https://reactjs.org/docs/hooks-rules.html)
- [Hooks customizados](https://reactjs.org/docs/hooks-custom.html)
- [useHooks.com](https://usehooks.com/) - Exemplos de hooks customizados

## Guias Relacionados

- Padrões de Composição React
- Gerenciamento de Estado Global
- Performance em React
