# Arrow Functions

Arrow functions are a concise syntax for writing functions in JavaScript and TypeScript. They are widely used in React for event handlers, callbacks, and inline logic.

---

## Syntax

### Traditional Function

```typescript
function add(a: number, b: number): number {
    return a + b;
}
```

### Arrow Function

```typescript
const add = (a: number, b: number): number => {
    return a + b;
};
```

### Implicit Return

If the function body is a single expression, you can omit the braces and `return` keyword:

```typescript
const add = (a: number, b: number): number => a + b;
```

### Single Parameter

Parentheses are optional when there is exactly one parameter:

```typescript
const double = (n: number) => n * 2;
const greet = (name: string) => `Hello, ${name}!`;
```

### No Parameters

Empty parentheses are required when there are no parameters:

```typescript
const getGreeting = () => "Hello, World!";
```

---

## Why Arrow Functions in React?

Arrow functions are commonly used in React because they are shorter and have predictable `this` behaviour. They are especially useful as:

### Inline Event Handlers

```typescript
<button onClick={() => setCount(count + 1)}>
    Increment
</button>

<input onChange={(e) => setQuery(e.target.value)} />
```

### Callbacks in Array Methods

```typescript
const names = ["Alice", "Bob", "Charlie"];
const nameLengths = names.map(name => name.length);
const adults = users.filter(user => user.age >= 18);
```

### Passing Extra Arguments to Handlers

```typescript
function handleDelete(id: number) {
    console.log("Delete item:", id);
}

items.map(item => (
    <button key={item.id} onClick={() => handleDelete(item.id)}>
        Delete {item.name}
    </button>
));
```

---

## Arrow Functions vs Traditional Functions

| Feature | Traditional Function | Arrow Function |
|---|---|---|
| Syntax | `function name() {}` | `const name = () => {}` |
| `this` binding | Dynamic (caller-dependent) | Lexical (from surrounding scope) |
| `arguments` object | Available | Not available |
| Constructor (`new`) | Can be used | Cannot be used |
| Hoisting | Function declarations hoisted | Not hoisted (assigned to variable) |
| Implicit return | No | Yes (single expressions) |

---

## Common Patterns

### Transforming Data

```typescript
const prices = [10, 20, 30];
const withTax = prices.map(price => price * 1.1);
// [11, 22, 33]

const total = prices.reduce((sum, price) => sum + price, 0);
// 60
```

### Filtering

```typescript
const products = [
    { name: "Laptop", price: 1200 },
    { name: "Mouse", price: 25 },
    { name: "Keyboard", price: 80 }
];

const affordable = products.filter(p => p.price < 100);
// [{ name: "Mouse", price: 25 }, { name: "Keyboard", price: 80 }]
```

### Sorting

```typescript
const sorted = products.sort((a, b) => a.price - b.price);
// Mouse (25), Keyboard (80), Laptop (1200)
```

---

## Performance Consideration

Arrow functions create a **new function reference on every render**. This is usually fine, but can cause unnecessary re-renders in performance-critical components.

```typescript
// Creates a new function on every render
<ChildComponent onClick={() => doSomething(id)} />
```

If this causes issues, use `useCallback` to memoize the function:

```typescript
import { useCallback, useState } from "react";

export default function Parent() {
    const [count, setCount] = useState(0);

    const handleClick = useCallback(() => {
        setCount(c => c + 1);
    }, []);   // Function identity stable across renders

    return <ChildComponent onClick={handleClick} />;
}
```

Only use `useCallback` when you actually have a performance problem. For most components, inline arrow functions are perfectly acceptable.

---

## Summary

- Arrow functions use `() => {}` syntax with **implicit returns** for single expressions
- They are **concise** — ideal for inline event handlers and array methods
- Arrow functions do **not** have their own `this` — they inherit from surrounding scope
- In React, use them for `onClick`, `onChange`, `.map()`, `.filter()`, etc.
- For performance-sensitive handlers, memoize with `useCallback`
