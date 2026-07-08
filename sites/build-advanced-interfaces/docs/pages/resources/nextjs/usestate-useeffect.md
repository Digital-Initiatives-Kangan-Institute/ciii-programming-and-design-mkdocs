# useState and useEffect

Two of the most important React hooks are `useState` and `useEffect`. Understanding when and how to use each one is essential for building data-driven interfaces.

---

## useState — Managing Component State

`useState` lets you add state to functional components:

```tsx
import { useState } from "react";

export default function Counter() {
    const [value, setValue] = useState(0);

    return (
        <div>
            <p>Count: {value}</p>
            <button onClick={() => setValue(value + 1)}>Add</button>
        </div>
    );
}
```

- `value` — the current state value
- `setValue` — the function to update it
- `useState(0)` — the `0` inside parentheses is the initial value

---

## useState with Objects and Arrays

State can hold objects:

```tsx
const [user, setUser] = useState({ name: "", email: "" });

setUser({ ...user, name: "Alice" });   // spread keeps existing fields
```

State can hold arrays:

```tsx
const [items, setItems] = useState<string[]>([]);

setItems([...items, "new item"]);       // add to array
```

---

## useEffect — Running Code After Render

`useEffect` runs code after the component renders. It is used for side effects like fetching data or setting up timers.

```tsx
import { useState, useEffect } from "react";

export default function Products() {
    const [products, setProducts] = useState([]);

    useEffect(() => {
        fetch("https://dummyjson.com/products")
            .then(res => res.json())
            .then(data => setProducts(data.products));
    }, []);

    return (
        <ul>
            {products.map(p => <li key={p.id}>{p.title}</li>)}
        </ul>
    );
}
```

- The fetch runs automatically when the component first renders
- `setProducts` updates state with the fetched data
- The component re-renders to show the data

---

## Dependency Arrays

The second argument to `useEffect` is the dependency array:

```tsx
useEffect(() => {
    console.log("Effect ran");
}, []);             // empty array: runs once on mount
```

```tsx
useEffect(() => {
    console.log("Count changed:", count);
}, [count]);        // runs when `count` changes
```

```tsx
useEffect(() => {
    console.log("Effect ran");
});                 // no array: runs after every render (avoid)
```

---

## Avoiding Repeated Fetch Loops

A common mistake is forgetting the dependency array, which causes an infinite loop:

```tsx
// INCORRECT - infinite loop!
useEffect(() => {
    fetch("/api/data")
        .then(res => res.json())
        .then(data => setData(data));   // setData triggers re-render,
});                                     // re-render triggers useEffect again...
```

The fix is the empty dependency array:

```tsx
// CORRECT - runs once
useEffect(() => {
    fetch("/api/data")
        .then(res => res.json())
        .then(data => setData(data));
}, []);   // empty array = run only once
```

---

## Button Fetch vs Page-Load Fetch

| Button Fetch | Page-Load Fetch (useEffect) |
|---|---|
| User triggers the fetch | Fetch runs automatically |
| Good for search, refresh, submit | Good for loading initial data |
| Uses `onClick` handler | Uses `useEffect` with `[]` |

When to use each:

- **Page-load fetch** — data the user always needs (product list, user profile)
- **Button fetch** — data the user requests on demand (search results, new page of results)

---

## Summary

- `useState` manages values that change over time
- `useEffect` runs code after render, commonly for fetching data
- Always provide a dependency array to control when effects run
- Empty array `[]` means "run once on mount"
- Use page-load fetch for initial data, button fetch for user-triggered requests
