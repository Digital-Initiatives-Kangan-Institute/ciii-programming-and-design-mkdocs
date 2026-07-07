# Hooks

Hooks are functions that let you use React features — like state and side effects — inside functional components. They are the primary way to add interactivity and manage data in modern React.

---

## What Are Hooks?

Hooks are special functions that:

- Start with the word `use` (e.g., `useState`, `useEffect`)
- Can only be called at the **top level** of a component (not inside loops or conditions)
- Can only be called from **React function components** or other custom hooks

---

## useState — Managing State

`useState` adds local state to a component. State persists across re-renders and updates trigger re-renders.

```typescript
import { useState } from "react";

export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <button onClick={() => setCount(count - 1)}>Decrement</button>
            <button onClick={() => setCount(0)}>Reset</button>
        </div>
    );
}
```

`useState(initialValue)` returns an array with two items:

1. The **current state value** (`count`)
2. A **setter function** (`setCount`) — calling it triggers a re-render with the new value

### State with Objects

When your state is an object, spread the existing state when updating to avoid losing fields:

```typescript
const [form, setForm] = useState({
    name: "",
    email: ""
});

function handleNameChange(e: React.ChangeEvent<HTMLInputElement>) {
    setForm({
        ...form,               // Copy existing fields
        name: e.target.value   // Override the one you want to change
    });
}
```

### State with Arrays

```typescript
const [items, setItems] = useState<string[]>([]);

function addItem(text: string) {
    setItems([...items, text]);       // Add to end
}

function removeItem(index: number) {
    setItems(items.filter((_, i) => i !== index));   // Remove by index
}
```

---

## useEffect — Side Effects

`useEffect` runs code after the component renders. Use it for fetching data, subscribing to events, or interacting with browser APIs.

### Basic Usage

```typescript
import { useEffect, useState } from "react";

export default function Clock() {
    const [time, setTime] = useState(new Date());

    useEffect(() => {
        const interval = setInterval(() => {
            setTime(new Date());
        }, 1000);

        return () => clearInterval(interval);   // Cleanup
    }, []);   // Empty array = run once on mount

    return <p>{time.toLocaleTimeString()}</p>;
}
```

### The Dependency Array

The second argument controls when the effect re-runs:

```typescript
// Runs after EVERY render
useEffect(() => { /* ... */ });

// Runs ONCE after first render (mount)
useEffect(() => { /* ... */ }, []);

// Runs when count or user changes
useEffect(() => { /* ... */ }, [count, user]);
```

### Fetching Data

```typescript
export default function UserList() {
    const [users, setUsers] = useState([]);

    useEffect(() => {
        fetch("/api/users")
            .then(res => res.json())
            .then(data => setUsers(data));
    }, []);   // Empty array: fetch once

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

### Cleanup

Return a function from `useEffect` to clean up subscriptions or timers:

```typescript
useEffect(() => {
    function handleResize() {
        console.log(window.innerWidth);
    }

    window.addEventListener("resize", handleResize);

    return () => {
        window.removeEventListener("resize", handleResize);
    };
}, []);
```

Without cleanup, event listeners would accumulate on every render.

---

## Other Common Hooks

### useRef

Stores a mutable value that persists across renders without triggering re-renders.

```typescript
import { useRef } from "react";

export default function FocusInput() {
    const inputRef = useRef<HTMLInputElement>(null);

    function handleClick() {
        inputRef.current?.focus();
    }

    return (
        <div>
            <input ref={inputRef} type="text" />
            <button onClick={handleClick}>Focus Input</button>
        </div>
    );
}
```

### useContext

Shares data across the component tree without passing props through every level.

```typescript
import { createContext, useContext } from "react";

const ThemeContext = createContext("light");

export default function App() {
    return (
        <ThemeContext.Provider value="dark">
            <Page />
        </ThemeContext.Provider>
    );
}

function Page() {
    const theme = useContext(ThemeContext);
    return <div className={theme}>The current theme is {theme}</div>;
}
```

---

## Rules of Hooks

1. **Only call hooks at the top level** — never inside loops, conditions, or nested functions
2. **Only call hooks from React functions** — components or custom hooks
3. **Hooks must be called in the same order every render**

```typescript
// WRONG — hook inside a condition
if (isLoggedIn) {
    const [user, setUser] = useState(null);   // Breaks rules
}

// CORRECT — condition inside the hook's logic
const [user, setUser] = useState(null);
if (isLoggedIn) {
    // Use the state
}
```

---

## Hooks Summary

| Hook | Purpose |
|---|---|
| `useState` | Local component state |
| `useEffect` | Side effects and lifecycle |
| `useContext` | Access context values |
| `useRef` | Mutable persistent reference |
| `useMemo` | Memoize expensive calculations |
| `useCallback` | Memoize function references |

---

## Summary

- **Hooks** let functional components use React features
- `useState(initialValue)` returns `[value, setter]` — call the setter to update
- `useEffect(callback, dependencies)` runs after render — use for data fetching, timers, and subscriptions
- Always **spread** object state when updating to preserve other fields
- Return a **cleanup function** from `useEffect` to prevent memory leaks
- Follow the **rules of hooks** — call at the top level, not inside conditions
