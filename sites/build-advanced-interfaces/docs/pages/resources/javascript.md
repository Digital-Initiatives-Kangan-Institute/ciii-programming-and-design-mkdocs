# JavaScript

JavaScript adds interactivity and dynamic behaviour to web pages. This resource introduces the core concepts of the language.

---

## Variables

Variables store data that your program can use and manipulate.

```javascript
let name = "Alice";
const age = 25;
var city = "Melbourne";
```

- `let` — block-scoped, can be reassigned
- `const` — block-scoped, cannot be reassigned
- `var` — function-scoped (older style, avoid in new code)

---

## Logic and Control Flow

### If / Else

Conditional statements allow your code to make decisions.

```javascript
let score = 85;

if (score >= 90) {
    console.log("A grade");
} else if (score >= 70) {
    console.log("B grade");
} else {
    console.log("C grade");
}
```

### For Loops

Loops repeat a block of code multiple times.

```javascript
for (let i = 0; i < 5; i++) {
    console.log("Iteration: " + i);
}
```

Other loop types include `while` and `do...while`.

---

## Functions

Functions group code into reusable blocks.

### Defining a Function

```javascript
function greet(name) {
    return "Hello, " + name + "!";
}
```

### Calling a Function

```javascript
let message = greet("Alice");
console.log(message);  // "Hello, Alice!"
```

### Breaking Code into Functions

Instead of one long script, break your logic into smaller, single-purpose functions:

```javascript
function calculateTotal(items) {
    let total = 0;
    for (let item of items) {
        total += item.price;
    }
    return total;
}

function applyDiscount(total, discount) {
    return total - (total * discount);
}

let cart = [{ price: 10 }, { price: 20 }, { price: 30 }];
let subtotal = calculateTotal(cart);
let final = applyDiscount(subtotal, 0.1);
console.log(final);
```

---

## Events

Events let your page respond to user actions like clicks, key presses, and form submissions.

```html
<button id="myButton">Click Me</button>

<script>
    document.getElementById("myButton").addEventListener("click", function() {
        alert("Button was clicked!");
    });
</script>
```

Common events:

| Event | Description |
|---|---|
| `click` | Element is clicked |
| `submit` | Form is submitted |
| `keydown` | Key is pressed |
| `load` | Page finishes loading |
| `mouseover` | Mouse enters an element |

---

## Load Order

JavaScript execution order matters. Code runs from top to bottom, and the DOM must be ready before you can interact with page elements.

Place `<script>` tags just before the closing `</body>` tag, or use the `defer` attribute:

```html
<script src="app.js" defer></script>
```

Alternatively, wrap your code in a `DOMContentLoaded` event:

```javascript
document.addEventListener("DOMContentLoaded", function() {
    // DOM is ready — safe to access elements
});
```

---

## Using External Libraries

You can incorporate existing JavaScript libraries to add functionality without writing everything from scratch.

### Bootstrap

Bootstrap is a popular CSS and JS framework for building responsive, mobile-first websites.

Add Bootstrap via CDN:

```html
<head>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <button class="btn btn-primary">Bootstrap Button</button>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
```

Bootstrap provides pre-built components like navbars, cards, modals, and a responsive grid system.

---

## AI-Assisted Development

When using tools like Copilot to write JavaScript:

- Provide clear context through comments and function names
- Break problems into small, well-named functions
- Review and understand all generated code before using it
- Test generated code thoroughly

```javascript
// Good context for AI assistance:
// Create a function that takes an array of numbers
// and returns the average, ignoring negative values

function averagePositive(numbers) {
    let positives = numbers.filter(n => n >= 0);
    let sum = positives.reduce((a, b) => a + b, 0);
    return sum / positives.length;
}
```

---

## Summary

- **Variables** (`let`, `const`) store data
- **Conditionals** (`if/else`) and **loops** (`for`) control flow
- **Functions** organise code into reusable blocks
- **Events** respond to user interaction
- **Load order** affects when code executes
- **Libraries** like Bootstrap accelerate development
