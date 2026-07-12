# Functions

Functions are reusable blocks of code that perform a specific task. They help you avoid repetition and keep your code organised.

---

## What is a Function?

A function is a named set of instructions that you can call whenever you need it. Instead of writing the same code multiple times, you write a function once and call it as many times as needed.

---

## Declaring a Function

```javascript
function greet() {
    console.log("Hello, welcome to our cafe!");
}
```

- `function` is the keyword
- `greet` is the function name
- `{ }` contains the function body

---

## Calling a Function

To run the function code, call it by name with parentheses:

```javascript
greet();   // Output: Hello, welcome to our cafe!
greet();   // Can be called multiple times
```

---

## Parameters and Arguments

Functions can accept input values through **parameters**:

```javascript
function greet(name) {
    console.log("Hello, " + name + "!");
}

greet("Alice");   // Hello, Alice!
greet("Bob");     // Hello, Bob!
```

- `name` is the **parameter** (placeholder in the function definition)
- `"Alice"` is the **argument** (actual value passed when calling)

Multiple parameters:

```javascript
function orderSum(item, quantity, price) {
    let total = quantity * price;
    console.log(quantity + "x " + item + " = $" + total);
}

orderSum("latte", 2, 4.5);   // 2x latte = $9
```

---

## Return Values

Functions can send a value back using `return`:

```javascript
function calculateTotal(price, quantity) {
    return price * quantity;
}

let total = calculateTotal(4.5, 3);
console.log("$" + total);   // $13.5
```

Once `return` runs, the function stops executing.

---

## Why Use Functions?

- Avoid repeating code
- Make changes in one place
- Break complex problems into smaller pieces
- Give descriptive names to blocks of code

```javascript
function displayTotal() {
    let subtotal = calculateTotal(4.5, 2);
    let tax = subtotal * 0.1;
    console.log("Total with tax: $" + (subtotal + tax));
}
```

---

## Summary

- Functions group reusable code and are called by name
- Parameters let functions accept input
- `return` sends a value back to the caller
- Functions make code more organised and easier to maintain
