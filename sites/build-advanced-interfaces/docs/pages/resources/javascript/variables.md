# JavaScript Variables and Data Types

Variables are used to store and manage data in your programs. JavaScript gives you several ways to declare variables and a handful of data types to work with.

---

## What is a Variable?

A variable is a named container that holds a value. You can use the variable name to access or change the value later.

```javascript
let name = "Alice";
let age = 25;
let isStudent = true;
```

---

## Declaring Variables

JavaScript has three keywords for declaring variables:

### `let`

Use `let` when the value will change:

```javascript
let score = 0;
score = 10;
score = 20;
```

### `const`

Use `const` when the value should not change:

```javascript
const taxRate = 0.1;
const company = "BKI";
```

### `var`

`var` is the older way to declare variables. Prefer `let` and `const` in modern JavaScript.

```javascript
var oldStyle = "avoid this";
```

---

## Data Types

### Strings

Text surrounded by single or double quotes:

```javascript
let firstName = "Sarah";
let message = 'Hello World';
```

### Numbers

Integers and decimals:

```javascript
let price = 9.99;
let quantity = 3;
let total = price * quantity;   // 29.97
```

### Booleans

True or false values:

```javascript
let isLoggedIn = false;
let hasDiscount = true;
```

### Undefined and Null

```javascript
let nothing;          // undefined — declared but no value assigned
let empty = null;     // null — intentionally empty
```

---

## Variable Naming Rules

- Names can contain letters, digits, underscores, and dollar signs
- Names must begin with a letter, `$`, or `_`
- Names are case-sensitive (`score` and `Score` are different)
- Use camelCase for multi-word names: `firstName`, `itemsInCart`
- Cannot use reserved words like `let`, `const`, `if`, `function`

---

## Using Variables

```javascript
let item = "coffee";
let price = 4.5;

console.log("Item: " + item);
console.log("Price: $" + price);

let message = `The ${item} costs $${price}.`;
console.log(message);
```

The backtick syntax (`` ` ``) creates a **template literal**, letting you embed variables directly with `${}`.

---

## Summary

- Use `let` for changeable values and `const` for constants
- Data types: strings (text), numbers, booleans, undefined, null
- Name variables descriptively using camelCase
- Template literals with backticks make building strings easier
