# Functions

Functions are the core organisational unit in JavaScript. They let you group code into reusable, named blocks. In Next.js, every component is a function — so mastering functions is essential.

---

## What Are Functions?

A function is a block of code that performs a specific task. You define it once and can call it many times.

```javascript
function greet() {
    console.log("Hello!");
}

greet();   // "Hello!"
greet();   // "Hello!"
greet();   // "Hello!"
```

Without functions, you would need to copy and paste the same code every time you wanted to reuse it.

---

## Defining and Calling Functions

```javascript
// 1. Define (the recipe)
function sayHello(name) {
    return `Hello, ${name}!`;
}

// 2. Call (cook the recipe)
let message = sayHello("Alice");
console.log(message);   // "Hello, Alice!"
```

- **Defining** creates the function — nothing runs yet
- **Calling** executes the function with `()` — the code inside runs
- A function can be called as many times as you need, with different arguments

---

## Parameters and Arguments

Parameters are placeholders when you define the function. Arguments are the actual values you pass when calling it.

```javascript
// name and age are parameters
function describe(name, age) {
    return `${name} is ${age} years old.`;
}

// "Alice" and 25 are arguments
describe("Alice", 25);   // "Alice is 25 years old."
describe("Bob", 30);     // "Bob is 30 years old."
```

### Default Parameters

Parameters can have default values:

```javascript
function greet(name = "Guest") {
    return `Hello, ${name}!`;
}

greet("Alice");   // "Hello, Alice!"
greet();          // "Hello, Guest!"
```

---

## Return Values

Functions can send a value back using `return`. This lets you store and use the result.

```javascript
function add(a, b) {
    return a + b;
}

let result = add(5, 3);
console.log(result);             // 8
console.log(add(10, 20) * 2);    // 60
```

### Functions Without return

A function without `return` (or with an empty `return;`) returns `undefined`.

```javascript
function logMessage(msg) {
    console.log(msg);
    // No return — returns undefined
}

let result = logMessage("Hi");   // Prints "Hi", result is undefined
```

### Early Return

Use `return` to exit a function early:

```javascript
function divide(a, b) {
    if (b === 0) {
        return "Cannot divide by zero";   // Exit early
    }
    return a / b;
}

divide(10, 0);   // "Cannot divide by zero"
divide(10, 2);   // 5
```

---

## Breaking Code into Functions

Instead of one long script, break your logic into small, single-purpose functions. This is the most important programming skill you will develop.

### Before (One big block)

```javascript
let cart = [
    { name: "Laptop", price: 1200, quantity: 1 },
    { name: "Mouse", price: 25, quantity: 2 },
    { name: "Keyboard", price: 80, quantity: 1 }
];

// Calculate items total
let itemTotal = 0;
for (let item of cart) {
    itemTotal += item.price * item.quantity;
}

// Apply discount
let discountRate = 0.1;
let discount = itemTotal * discountRate;

// Apply tax
let taxRate = 0.1;
let tax = (itemTotal - discount) * taxRate;

// Final total
let finalTotal = itemTotal - discount + tax;

// Format currency
let formattedTotal = `$${finalTotal.toFixed(2)}`;

console.log(formattedTotal);
```

### After (Functions)

```javascript
function calculateItemTotal(cart) {
    let total = 0;
    for (let item of cart) {
        total += item.price * item.quantity;
    }
    return total;
}

function applyDiscount(amount, rate) {
    return amount * rate;
}

function applyTax(amount, rate) {
    return amount * rate;
}

function formatCurrency(amount) {
    return `$${amount.toFixed(2)}`;
}

// Now the main logic reads like a story:
let cart = [
    { name: "Laptop", price: 1200, quantity: 1 },
    { name: "Mouse", price: 25, quantity: 2 },
    { name: "Keyboard", price: 80, quantity: 1 }
];

let itemTotal = calculateItemTotal(cart);
let discount = applyDiscount(itemTotal, 0.1);
let tax = applyTax(itemTotal - discount, 0.1);
let finalTotal = itemTotal - discount + tax;

console.log(formatCurrency(finalTotal));
```

Each function does **one thing** and has a clear name. The main logic is easy to read and modify.

---

## Function Expressions and Arrow Functions

Functions can also be assigned to variables:

```javascript
// Function expression
const greet = function(name) {
    return `Hello, ${name}!`;
};

// Arrow function (shorter syntax)
const greet = (name) => {
    return `Hello, ${name}!`;
};

// Arrow function with implicit return
const greet = (name) => `Hello, ${name}!`;
```

Arrow functions are common in React for event handlers and callbacks. They are covered in detail in the Next.js section.

---

## Functions in React / Next.js

Every React component is a function:

```typescript
// This is a function that returns JSX
export default function Button({ label, onClick }) {
    return (
        <button onClick={onClick}>
            {label}
        </button>
    );
}
```

The same principles apply:
- Components accept **props** (parameters)
- Components **return** JSX (HTML-like syntax)
- Break large components into smaller, single-purpose components — just like functions

---

## Pure vs Impure Functions

### Pure Functions

A pure function always returns the same output for the same input and has no side effects. It does not modify anything outside itself.

```javascript
// Pure — same input always gives same output
function add(a, b) {
    return a + b;
}

// Pure — does not modify the original array
function addItem(items, newItem) {
    return [...items, newItem];
}
```

### Impure Functions

Impure functions have side effects — they modify external state, write to the console, or make network requests.

```javascript
let total = 0;

// Impure — modifies external variable
function addToTotal(amount) {
    total += amount;
}

// Impure — side effect (console.log)
function greet(name) {
    console.log(`Hello, ${name}`);
}
```

React components are impure by nature — they can use state, make API calls, and interact with the browser. But their **render logic** should be as pure as possible.

---

## Summary

- Functions **group code** into reusable, named blocks
- Define once with `function`, call many times with `()`
- **Parameters** are placeholders; **arguments** are actual values
- Use `return` to send a value back — a function without `return` gives `undefined`
- **Break large logic into small functions** — each doing one thing
- React components are **functions that return JSX**
