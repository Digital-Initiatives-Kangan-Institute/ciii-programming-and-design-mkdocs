# Control Flow

Control flow determines which code runs and when. JavaScript provides conditionals for making decisions and loops for repeating code.

---

## If / Else Statements

Use `if` to run code only when a condition is true:

```javascript
let score = 85;

if (score >= 50) {
    console.log("You passed!");
}
```

Use `else` to handle the opposite case:

```javascript
if (score >= 50) {
    console.log("You passed!");
} else {
    console.log("Try again.");
}
```

Use `else if` to check multiple conditions:

```javascript
if (score >= 80) {
    console.log("High distinction");
} else if (score >= 60) {
    console.log("Credit");
} else if (score >= 50) {
    console.log("Pass");
} else {
    console.log("Fail");
}
```

---

## Comparison Operators

| Operator | Meaning | Example |
|---|---|---|
| `===` | equal to | `x === 5` |
| `!==` | not equal to | `x !== 5` |
| `>` | greater than | `x > 5` |
| `<` | less than | `x < 5` |
| `>=` | greater than or equal | `x >= 5` |
| `<=` | less than or equal | `x <= 5` |

Use `===` (triple equals) rather than `==` (double equals) to avoid unexpected type coercion.

---

## Logical Operators

Combine multiple conditions:

```javascript
if (score >= 50 && score <= 100) {
    console.log("Valid score");
}

if (role === "admin" || role === "editor") {
    console.log("You can edit");
}
```

- `&&` (AND) — both conditions must be true
- `||` (OR) — at least one condition must be true

---

## For Loops

Use a `for` loop when you know how many times to repeat:

```javascript
for (let i = 0; i < 5; i++) {
    console.log("Iteration: " + i);
}
```

The loop has three parts:

1. `let i = 0` — initial setup
2. `i < 5` — condition to keep running
3. `i++` — runs after each iteration

---

## While Loops

Use a `while` loop when you are not sure how many times to repeat:

```javascript
let count = 0;
while (count < 3) {
    console.log("Count: " + count);
    count++;
}
```

The loop runs as long as the condition remains true. Make sure the condition eventually becomes false to avoid infinite loops.

---

## Summary

- `if` / `else if` / `else` let you make decisions in code
- Use `===` for equality checks and `&&` / `||` to combine conditions
- `for` loops repeat a known number of times
- `while` loops repeat while a condition is true
