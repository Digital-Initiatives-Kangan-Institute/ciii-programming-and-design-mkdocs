# Variables and Control Flow

Before working with Next.js, you need a solid understanding of JavaScript variables, data types, and control flow. These are the building blocks of all programming logic.

---

## Variables

Variables store data that your program can use, modify, and reference. Think of them as labelled boxes that hold values.

### Declaring Variables

```javascript
let name = "Alice";        // Can be reassigned
const age = 25;            // Cannot be reassigned
var city = "Melbourne";    // Old style — avoid in new code
```

| Keyword | Reassignable? | Scope | Recommendation |
|---|---|---|---|
| `let` | Yes | Block `{}` | Use when the value needs to change |
| `const` | No | Block `{}` | Default choice — prevents accidental reassignment |
| `var` | Yes | Function | Avoid — has unexpected scoping behaviour |

### Naming Rules

- Use descriptive names: `userName`, `cartTotal`, `isLoggedIn` (camelCase)
- Cannot start with a number
- Cannot contain spaces or hyphens
- Can contain letters, numbers, `$`, and `_`
- Case sensitive: `name` and `Name` are different

```javascript
// GOOD — descriptive, camelCase
let firstName = "Alice";
let shoppingCartTotal = 149.95;
let isAuthenticated = true;

// BAD — unclear, hard to read
let x = "Alice";
let sct = 149.95;
let a = true;
```

---

## Data Types

JavaScript has several fundamental types.

### Strings

Text, wrapped in quotes.

```javascript
let name = "Alice";
let greeting = 'Hello';
let template = `Hello, ${name}`;   // Template literal — can embed variables
```

Use template literals (backticks) for strings that contain variables or span multiple lines.

### Numbers

All numbers (integers and decimals) are the same type.

```javascript
let age = 25;
let price = 19.99;
let temperature = -5;
let infinity = Infinity;
let notANumber = NaN;   // Result of invalid math like 0 / 0
```

### Booleans

Only two values: `true` or `false`.

```javascript
let isLoggedIn = true;
let hasPermission = false;
```

### Arrays

Ordered lists of values.

```javascript
let colours = ["red", "green", "blue"];
let mixed = [1, "hello", true, null];
let empty = [];

// Access by index (zero-based)
colours[0];   // "red"
colours[2];   // "blue"

// Common array methods
colours.push("yellow");     // Add to end
colours.pop();              // Remove from end
colours.length;             // Number of items
colours.includes("red");    // true
```

### Objects

Collections of key-value pairs.

```javascript
let user = {
    name: "Alice",
    age: 25,
    email: "alice@example.com",
    isActive: true
};

// Access properties
user.name;          // "Alice" — dot notation
user["email"];      // "alice@example.com" — bracket notation

// Add or modify
user.city = "Melbourne";
user.age = 26;
```

### undefined and null

```javascript
let x;                  // undefined — declared but no value
let y = null;           // null — intentionally empty
```

---

## Operators

### Arithmetic

```javascript
let sum = 5 + 3;        // 8
let diff = 10 - 4;      // 6
let product = 3 * 4;    // 12
let quotient = 20 / 5;  // 4
let remainder = 10 % 3; // 1 (modulo — remainder after division)
```

### Comparison

```javascript
5 > 3;     // true
5 < 3;     // false
5 >= 5;    // true
5 <= 4;    // false
5 === 5;   // true (strict equality — checks value AND type)
5 == "5";  // true (loose equality — converts types, avoid this)
5 !== 3;   // true (strict not equal)
```

Always use `===` and `!==` (strict comparison). Loose comparison (`==`) can produce unexpected results.

### Logical

```javascript
// AND — both must be true
true && true;    // true
true && false;   // false

// OR — at least one must be true
true || false;   // true
false || false;  // false

// NOT — reverses the boolean
!true;           // false
!false;          // true
```

---

## Conditionals (If / Else)

Conditionals let your code make decisions and take different paths based on conditions.

### Basic If / Else

```javascript
let score = 85;

if (score >= 90) {
    console.log("A grade");
} else if (score >= 75) {
    console.log("B grade");
} else if (score >= 60) {
    console.log("C grade");
} else {
    console.log("F grade");
}
```

### Common Patterns

```javascript
// Checking for emptiness
let username = "";
if (!username) {
    console.log("Username is required.");
}

// Checking for existence
let user = null;
if (user) {
    console.log(user.name);   // Won't run — user is null/falsy
}

// Range check
let age = 20;
if (age >= 18 && age <= 65) {
    console.log("Eligible");
}
```

### Ternary Operator

Shorthand for simple if/else assignments:

```javascript
// Instead of:
let status;
if (isLoggedIn) {
    status = "Welcome";
} else {
    status = "Please log in";
}

// Use ternary:
let status = isLoggedIn ? "Welcome" : "Please log in";
```

---

## Loops

Loops repeat a block of code.

### For Loop

Best when you know how many iterations you need.

```javascript
for (let i = 0; i < 5; i++) {
    console.log(`Iteration ${i}`);
}
// Output: Iteration 0, 1, 2, 3, 4
```

The three parts: initialisation (`let i = 0`), condition (`i < 5`), and increment (`i++`).

### While Loop

Best when the number of iterations is unknown.

```javascript
let count = 0;
while (count < 5) {
    console.log(count);
    count++;
}
```

### For...of Loop (Arrays)

Cleaner syntax for iterating over array values.

```javascript
let fruits = ["apple", "banana", "orange"];

for (let fruit of fruits) {
    console.log(fruit);
}
```

### forEach Method

Array method — common in React/Next.js code:

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
    console.log(number * 2);
});
```

---

## Putting It Together

A practical example combining variables, conditionals, and loops:

```javascript
// Shopping cart
let cart = [
    { name: "Laptop", price: 1200, inStock: true },
    { name: "Mouse", price: 25, inStock: true },
    { name: "Keyboard", price: 80, inStock: false },
    { name: "Monitor", price: 400, inStock: true }
];

let total = 0;
let unavailableItems = [];

for (let item of cart) {
    if (item.inStock) {
        total += item.price;
    } else {
        unavailableItems.push(item.name);
    }
}

console.log(`Total: $${total}`);   // "Total: $1625"

if (unavailableItems.length > 0) {
    console.log(`Unavailable: ${unavailableItems.join(", ")}`);
    // "Unavailable: Keyboard"
}
```

---

## Debugging with console.log

`console.log()` is the simplest way to see what your code is doing:

```javascript
let x = 10;
console.log("x is:", x);        // "x is: 10"

let user = { name: "Alice" };
console.log("User:", user);     // "User: { name: 'Alice' }"

// Checkpoint — did this code run?
if (x > 5) {
    console.log("Inside if block — x is greater than 5");
}
```

Use `console.log()` liberally when learning. It helps you understand the flow of your program.

---

## Why This Matters for Next.js

In React components, you will use these concepts constantly:

- **Variables** (`const`, `let`) for state values and configuration
- **Arrays** for rendering lists with `.map()`
- **Objects** for props and state
- **Conditionals** for showing/hiding UI elements and handling edge cases
- **Loops** (especially `.map()` and `.filter()`) for processing data arrays

These fundamentals do not change — Next.js components are just JavaScript functions that happen to return HTML.

---

## Summary

- Use `const` by default, `let` when the value must change — avoid `var`
- JavaScript has **strings**, **numbers**, **booleans**, **arrays**, and **objects**
- Use `===` for strict comparison, not `==`
- **If/else** makes decisions; **loops** repeat code
- **Template literals** `` `Hello, ${name}` `` are the cleanest way to build strings
- `console.log()` is your best debugging friend
