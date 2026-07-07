# NextJS Fundamentals

Next.js is a React framework that provides routing, rendering strategies, and a great developer experience out of the box. This resource covers the core concepts.

---

## TypeScript in Next.js

Next.js has first-class TypeScript support. Files use the `.tsx` extension (TypeScript + JSX).

```typescript
// pages/index.tsx
import type { NextPage } from "next";

interface Props {
    title: string;
}

const Home: NextPage<Props> = ({ title }) => {
    return <h1>{title}</h1>;
};

export default Home;
```

TypeScript adds static type checking, making your code more robust and providing better IDE autocompletion.

---

## Components

Components are the building blocks of a React/Next.js application. Each component is a reusable piece of UI.

### Functional Component

```typescript
// components/Button.tsx
interface ButtonProps {
    label: string;
    onClick: () => void;
}

export default function Button({ label, onClick }: ButtonProps) {
    return (
        <button onClick={onClick}>
            {label}
        </button>
    );
}
```

### Using Components

```typescript
import Button from "../components/Button";

export default function Page() {
    return (
        <div>
            <h2>My Page</h2>
            <Button label="Click Me" onClick={() => alert("Hello!")} />
        </div>
    );
}
```

Components can be nested, passed as props, and composed to build complex UIs.

---

## Routing

Next.js uses a **file-system based router**. Files placed in the `pages/` (or `app/`) directory automatically become routes.

### Static Routes

```
pages/
├── index.tsx       →  /
├── about.tsx       →  /about
├── contact.tsx     →  /contact
```

Each file exports a default React component that renders when that route is visited.

### Dynamic Routes

Use square brackets `[param]` for dynamic segments:

```
pages/
└── products/
    ├── index.tsx       →  /products
    └── [id].tsx        →  /products/1, /products/2, etc.
```

```typescript
// pages/products/[id].tsx
import { useRouter } from "next/router";

export default function Product() {
    const router = useRouter();
    const { id } = router.query;

    return <h1>Product {id}</h1>;
}
```

---

## Layouts

Layouts wrap pages with shared UI like headers, footers, and navigation.

### App Router Layout (Next.js 13+)

```typescript
// app/layout.tsx
export default function RootLayout({
    children,
}: {
    children: React.ReactNode;
}) {
    return (
        <html lang="en">
            <body>
                <header>
                    <nav>My Site</nav>
                </header>
                <main>{children}</main>
                <footer>Copyright 2026</footer>
            </body>
        </html>
    );
}
```

### Pages Router Layout

For the pages directory approach, create a layout component and wrap each page:

```typescript
// components/Layout.tsx
export default function Layout({ children }: { children: React.ReactNode }) {
    return (
        <div>
            <nav>Navigation bar</nav>
            <main>{children}</main>
        </div>
    );
}
```

```typescript
// pages/_app.tsx
import type { AppProps } from "next/app";
import Layout from "../components/Layout";

export default function App({ Component, pageProps }: AppProps) {
    return (
        <Layout>
            <Component {...pageProps} />
        </Layout>
    );
}
```

---

## Events

React uses camelCase event handlers passed as props.

```typescript
export default function Counter() {
    function handleClick() {
        console.log("Button clicked");
    }

    function handleChange(event: React.ChangeEvent<HTMLInputElement>) {
        console.log(event.target.value);
    }

    return (
        <div>
            <button onClick={handleClick}>Click</button>
            <input onChange={handleChange} placeholder="Type here" />
        </div>
    );
}
```

Common React events: `onClick`, `onChange`, `onSubmit`, `onKeyDown`, `onMouseEnter`.

---

## Arrow Functions

Arrow functions are a concise syntax commonly used in React.

```typescript
// Traditional function
function add(a: number, b: number): number {
    return a + b;
}

// Arrow function
const add = (a: number, b: number): number => a + b;
```

Arrow functions are particularly useful for inline event handlers and callbacks:

```typescript
<button onClick={() => setCount(count + 1)}>
    Increment
</button>
```

**Note**: Arrow functions create a new function reference on every render. For performance-critical handlers, use `useCallback`.

---

## Hooks — State

Hooks are functions that let you use React features in functional components.

### useState

`useState` adds local state to a component.

```typescript
import { useState } from "react";

export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <button onClick={() => setCount(0)}>Reset</button>
        </div>
    );
}
```

- `useState(initialValue)` returns an array: `[value, setterFunction]`
- Calling the setter triggers a re-render with the new value
- State is preserved across re-renders

### useState with Objects

```typescript
const [form, setForm] = useState({ name: "", email: "" });

function handleNameChange(e: React.ChangeEvent<HTMLInputElement>) {
    setForm({ ...form, name: e.target.value });
}
```

Always spread the existing state (`...form`) when updating object state to avoid losing other fields.

---

### Other Common Hooks

| Hook | Purpose |
|---|---|
| `useEffect` | Side effects (data fetching, subscriptions) |
| `useContext` | Access context values |
| `useRef` | Mutable reference that persists across renders |
| `useMemo` | Memoize expensive calculations |
| `useCallback` | Memoize function references |

---

## Summary

- **TypeScript** adds type safety with `.tsx` files
- **Components** are reusable building blocks
- **File-based routing** maps files to URLs (static with named files, dynamic with `[param]`)
- **Layouts** wrap pages with shared UI
- **Events** use camelCase handlers (`onClick`, `onChange`)
- **Arrow functions** provide concise syntax for handlers
- **Hooks** like `useState` manage component state
