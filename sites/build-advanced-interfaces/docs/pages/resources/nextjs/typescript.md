# TypeScript in Next.js

Next.js has first-class TypeScript support. TypeScript adds static type checking to JavaScript, catching errors before your code runs and providing better autocompletion in your editor.

---

## Getting Started

Next.js automatically detects `.tsx` files and configures TypeScript for you. Just create a `.tsx` file instead of `.jsx`:

```bash
# Next.js creates tsconfig.json on first run
touch pages/index.tsx
npm run dev   # Next.js will set up TypeScript automatically
```

---

## Basic Types

### Typing Props

Define an interface for the props a component accepts:

```typescript
// components/Greeting.tsx
interface GreetingProps {
    name: string;
    age?: number;        // Optional prop (the ?)
}

export default function Greeting({ name, age }: GreetingProps) {
    return (
        <div>
            <h1>Hello, {name}!</h1>
            {age && <p>You are {age} years old.</p>}
        </div>
    );
}
```

Using the component:

```typescript
<Greeting name="Alice" />          // OK — age is optional
<Greeting name="Bob" age={25} />   // OK
<Greeting />                        // Error — name is required
<Greeting name={42} />             // Error — name must be a string
```

### Typing Function Components

```typescript
import type { NextPage } from "next";

interface Props {
    title: string;
}

const Home: NextPage<Props> = ({ title }) => {
    return <h1>{title}</h1>;
};

export default Home;
```

The `NextPage` type includes built-in Next.js page types.

---

## Common TypeScript Patterns

### Typing State with Generics

```typescript
import { useState } from "react";

// useState uses a generic to specify the state type
const [count, setCount] = useState<number>(0);
const [name, setName] = useState<string>("");
const [items, setItems] = useState<string[]>([]);
```

TypeScript infers types from the initial value, but explicit generics are useful for `null` initial values:

```typescript
const [user, setUser] = useState<User | null>(null);
```

### Typing Events

```typescript
function handleClick(event: React.MouseEvent<HTMLButtonElement>) {
    console.log(event.currentTarget);   // The button element
}

function handleChange(event: React.ChangeEvent<HTMLInputElement>) {
    console.log(event.target.value);    // The input's value
}

function handleSubmit(event: React.FormEvent<HTMLFormElement>) {
    event.preventDefault();
}
```

### Typing Array Props

```typescript
interface Post {
    id: number;
    title: string;
    author: string;
}

interface PostListProps {
    posts: Post[];
}

export default function PostList({ posts }: PostListProps) {
    return (
        <ul>
            {posts.map(post => (
                <li key={post.id}>
                    <strong>{post.title}</strong> by {post.author}
                </li>
            ))}
        </ul>
    );
}
```

---

## Async Page Components

In the App Router, page components can be `async`:

```typescript
// app/users/page.tsx
interface User {
    id: number;
    name: string;
    email: string;
}

async function getUsers(): Promise<User[]> {
    const res = await fetch("https://jsonplaceholder.typicode.com/users");
    return res.json();
}

export default async function UsersPage() {
    const users = await getUsers();

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

---

## TypeScript vs JavaScript

| Feature | JavaScript | TypeScript |
|---|---|---|
| Type checking | At runtime | At compile time |
| Autocompletion | Limited | Full, based on types |
| Refactoring safety | Manual | Editor-assisted |
| Error detection | When code runs | Before code runs |
| Prop validation | Runtime or none | Compile-time |

TypeScript does not change how your code runs — it only checks it before running. All TypeScript is compiled to plain JavaScript.

---

## Best Practices

- Define interfaces for all component props
- Use `interface` for object shapes, `type` for unions and utilities
- Keep your `tsconfig.json` as-is (Next.js defaults are well-configured)
- Let TypeScript infer types when the value is obvious — don't over-type
- Use `"use client"` directive only on components that need browser APIs

```typescript
// Avoid over-typing:
const name: string = "Alice";   // Unnecessary — TypeScript infers string

// Type where it matters:
function greet(name: string, age: number): string {
    return `Hello ${name}, you are ${age}`;
}
```

---

## Summary

- TypeScript adds **compile-time type safety** to JavaScript
- Define **interfaces** for component props and data structures
- Use **event types** (`React.MouseEvent`, `React.ChangeEvent`) for event handlers
- TypeScript **infers** types from initial values — only annotate when needed
- Next.js configures TypeScript **automatically** — just use `.tsx` files
