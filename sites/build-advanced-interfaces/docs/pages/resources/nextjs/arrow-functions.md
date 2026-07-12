# Arrow Functions

Arrow functions are a shorter syntax for writing functions in JavaScript and TypeScript. They are widely used in React for event handlers, callbacks, and functional patterns.

---

## Traditional vs Arrow Syntax

Traditional function:

```javascript
function add(a, b) {
    return a + b;
}
```

Arrow function:

```javascript
const add = (a, b) => {
    return a + b;
};
```

---

## Concise Body

If the function body only contains a return statement, you can use the concise syntax:

```javascript
const add = (a, b) => a + b;
```

No curly braces, no `return` keyword.

---

## Single Parameter

If there is exactly one parameter, the parentheses can be omitted:

```javascript
const double = n => n * 2;

// Same as:
const double = (n) => {
    return n * 2;
};
```

---

## Arrow Functions in React

Arrow functions are commonly used for event handlers and callbacks:

```tsx
<button onClick={() => setCount(count + 1)}>Add</button>
```

Passing arguments to a handler:

```tsx
<button onClick={() => handleDelete(item.id)}>Delete</button>
```

Without the arrow function wrapper, `handleDelete(item.id)` would run immediately on render rather than on click.

---

## Arrow Functions in Array Methods

Arrow functions make array operations cleaner:

```javascript
const prices = [10, 20, 30];
const withTax = prices.map(price => price * 1.1);

const affordable = prices.filter(price => price < 25);

const total = prices.reduce((sum, price) => sum + price, 0);
```

---

## Refactoring to Arrow Functions

Before (traditional function):

```tsx
function handleSubmit(event: React.FormEvent) {
    event.preventDefault();
    console.log("Submitted");
}
```

After (arrow function):

```tsx
const handleSubmit = (event: React.FormEvent) => {
    event.preventDefault();
    console.log("Submitted");
};
```

The arrow function syntax keeps the function assigned to a `const`, making it clear that `handleSubmit` should not be reassigned.

---

## Summary

- Arrow functions provide a shorter syntax: `(params) => { body }`
- Concise body omits `{}` and `return` for single expressions
- Widely used in React for event handlers and array methods
- Refactoring to arrow functions can make code clearer and more consistent
