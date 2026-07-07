# Components

Components are the building blocks of a Next.js application. Each component is a self-contained, reusable piece of UI that can be composed together to build complex interfaces.

---

## What is a Component?

A component is a JavaScript/TypeScript function that returns JSX (HTML-like syntax). Components accept inputs called **props** and return the UI that should appear on screen.

```typescript
function Welcome() {
    return <h1>Hello, World!</h1>;
}
```

This is a valid component. It takes no props and always returns the same output.

---

## Functional Components

Components can accept props to make them reusable with different data.

```typescript
interface ButtonProps {
    label: string;
    onClick: () => void;
}

export default function Button({ label, onClick }: ButtonProps) {
    return (
        <button
            onClick={onClick}
            style={{
                padding: "0.5rem 1rem",
                backgroundColor: "#3f51b5",
                color: "white",
                border: "none",
                borderRadius: "4px",
                cursor: "pointer"
            }}
        >
            {label}
        </button>
    );
}
```

The same component renders differently depending on its props:

```typescript
<Button label="Save" onClick={handleSave} />
<Button label="Delete" onClick={handleDelete} />
<Button label="Cancel" onClick={handleCancel} />
```

---

## Composing Components

Components can contain other components. Build complex UIs by combining simpler pieces.

```typescript
import Button from "./Button";

interface CardProps {
    title: string;
    description: string;
    onAction: () => void;
}

export default function Card({ title, description, onAction }: CardProps) {
    return (
        <div style={{ border: "1px solid #ccc", padding: "1rem", borderRadius: "8px" }}>
            <h2>{title}</h2>
            <p>{description}</p>
            <Button label="Learn More" onClick={onAction} />
        </div>
    );
}
```

```typescript
// Using the composed component
<Card
    title="Next.js"
    description="A React framework for production."
    onAction={() => router.push("/nextjs")}
/>
```

---

## Props Are Read-Only

Never modify props inside a component. Props flow down from parent to child.

```typescript
// WRONG — Do not mutate props
function BadCounter({ count }: { count: number }) {
    count = count + 1;   // This does not work and will throw an error
    return <p>{count}</p>;
}

// CORRECT — Props are read-only
function GoodCounter({ count }: { count: number }) {
    return <p>{count}</p>;
}
```

If you need to change a value, use **state** instead.

---

## Conditional Rendering

Components can render different UI based on conditions.

```typescript
interface AlertProps {
    type: "success" | "error" | "warning";
    message: string;
}

export default function Alert({ type, message }: AlertProps) {
    if (type === "success") {
        return <div style={{ color: "green" }}>✓ {message}</div>;
    }

    if (type === "error") {
        return <div style={{ color: "red" }}>✗ {message}</div>;
    }

    return <div style={{ color: "orange" }}>⚠ {message}</div>;
}
```

### Using Ternary Operators Inline

```typescript
export default function UserStatus({ isLoggedIn }: { isLoggedIn: boolean }) {
    return (
        <div>
            {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in.</p>}
        </div>
    );
}
```

### Conditional with &&

```typescript
export default function Notifications({ count }: { count: number }) {
    return (
        <div>
            <span>Notifications</span>
            {count > 0 && <span>({count})</span>}
        </div>
    );
}
```

---

## Rendering Lists

Use `.map()` to render arrays of data.

```typescript
interface Todo {
    id: number;
    text: string;
    done: boolean;
}

interface TodoListProps {
    items: Todo[];
}

export default function TodoList({ items }: TodoListProps) {
    return (
        <ul>
            {items.map(todo => (
                <li key={todo.id}>
                    {todo.done ? "✓" : "○"} {todo.text}
                </li>
            ))}
        </ul>
    );
}
```

Always provide a **unique `key` prop** when rendering lists. React uses keys to track which items changed.

---

## Component File Structure

Organise components in a dedicated folder:

```
src/
├── components/
│   ├── Button.tsx
│   ├── Card.tsx
│   ├── Navbar.tsx
│   └── TodoList.tsx
└── pages/
    └── index.tsx
```

A typical component file is small and focused on one purpose. If a component grows too large, split it into smaller sub-components.

---

## Summary

- Components are **reusable functions** that return JSX
- **Props** make components configurable — pass data from parent to child
- Components can be **composed** to build complex UIs from simple parts
- Use **conditional rendering** (`if`, ternary, `&&`) for dynamic output
- Use `.map()` with a **key prop** to render lists
- Keep components **small and focused** — one component per file
