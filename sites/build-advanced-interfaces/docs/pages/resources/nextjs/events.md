# Events

Events let your components respond to user actions — clicks, typing, form submissions, and more. React uses camelCase event handlers passed as props.

---

## Handling Events

In React, event handlers are functions passed as props. They use camelCase names (e.g., `onClick`, not `onclick`).

```typescript
export default function ClickMe() {
    function handleClick() {
        console.log("Button was clicked!");
    }

    return <button onClick={handleClick}>Click Me</button>;
}
```

Key differences from plain HTML:

- React events are named in **camelCase**: `onClick`, `onChange`, `onSubmit`
- You pass a **function reference**, not a string: `onClick={handleClick}` not `onclick="handleClick()"`
- React uses a **synthetic event system** that works consistently across browsers

---

## Common Events

### onClick

Fires when an element is clicked.

```typescript
export default function LikeButton() {
    function handleLike() {
        alert("Liked!");
    }

    return <button onClick={handleLike}>Like</button>;
}
```

### onChange

Fires when an input's value changes. Useful for forms and search fields.

```typescript
import { useState } from "react";

export default function SearchBar() {
    const [query, setQuery] = useState("");

    function handleChange(event: React.ChangeEvent<HTMLInputElement>) {
        setQuery(event.target.value);
    }

    return (
        <div>
            <input
                type="text"
                value={query}
                onChange={handleChange}
                placeholder="Search..."
            />
            <p>You typed: {query}</p>
        </div>
    );
}
```

Accessing `event.target.value` gives you the current input value.

### onSubmit

Fires when a form is submitted. Use `event.preventDefault()` to stop the page reload.

```typescript
export default function LoginForm() {
    function handleSubmit(event: React.FormEvent<HTMLFormElement>) {
        event.preventDefault();

        const formData = new FormData(event.currentTarget);
        const username = formData.get("username");
        const password = formData.get("password");

        console.log("Logging in:", username);
    }

    return (
        <form onSubmit={handleSubmit}>
            <input name="username" type="text" placeholder="Username" />
            <input name="password" type="password" placeholder="Password" />
            <button type="submit">Log In</button>
        </form>
    );
}
```

### onKeyDown

Fires when a key is pressed. Useful for keyboard shortcuts.

```typescript
export default function SearchInput() {
    function handleKeyDown(event: React.KeyboardEvent<HTMLInputElement>) {
        if (event.key === "Enter") {
            console.log("Search submitted!");
        }
        if (event.key === "Escape") {
            console.log("Search cancelled");
        }
    }

    return <input onKeyDown={handleKeyDown} placeholder="Press Enter to search" />;
}
```

### onMouseEnter / onMouseLeave

Fires when the mouse enters or leaves an element.

```typescript
export default function Tooltip({ text }: { text: string }) {
    const [visible, setVisible] = useState(false);

    return (
        <span
            onMouseEnter={() => setVisible(true)}
            onMouseLeave={() => setVisible(false)}
            style={{ position: "relative", cursor: "help" }}
        >
            ?
            {visible && (
                <span style={{
                    position: "absolute",
                    backgroundColor: "#333",
                    color: "white",
                    padding: "4px 8px",
                    borderRadius: "4px",
                    fontSize: "0.8rem",
                    whiteSpace: "nowrap"
                }}>
                    {text}
                </span>
            )}
        </span>
    );
}
```

---

## Event Reference

| React Event | When It Fires |
|---|---|
| `onClick` | Element is clicked |
| `onChange` | Input value changes |
| `onSubmit` | Form is submitted |
| `onKeyDown` | Key is pressed |
| `onKeyUp` | Key is released |
| `onFocus` | Element receives focus |
| `onBlur` | Element loses focus |
| `onMouseEnter` | Mouse enters element |
| `onMouseLeave` | Mouse leaves element |

---

## Passing Arguments to Handlers

Use an arrow function to pass custom arguments:

```typescript
export default function ItemList({ items }: { items: string[] }) {
    function handleDelete(name: string) {
        console.log("Deleting:", name);
    }

    return (
        <ul>
            {items.map(item => (
                <li key={item}>
                    {item}
                    <button onClick={() => handleDelete(item)}>
                        Delete
                    </button>
                </li>
            ))}
        </ul>
    );
}
```

Without the arrow function wrapper, the handler would be called immediately on render.

---

## Event Object Properties

The synthetic event object provides useful properties:

```typescript
function handleInput(event: React.ChangeEvent<HTMLInputElement>) {
    console.log(event.target.value);      // The input's current value
    console.log(event.target.name);       // The input's name attribute
    console.log(event.currentTarget);     // The element the handler is attached to
}

function handleKeyDown(event: React.KeyboardEvent) {
    console.log(event.key);               // "Enter", "Escape", "a", etc.
    console.log(event.code);              // Physical key: "KeyA", "Space"
    console.log(event.shiftKey);          // true if Shift was held
}
```

---

## Summary

- React events use **camelCase**: `onClick`, `onChange`, `onSubmit`
- Pass a **function reference**, not a function call
- Use `event.preventDefault()` to stop default browser behaviour
- `event.target.value` gives you the current input value
- Wrap handlers in **arrow functions** when passing extra arguments
