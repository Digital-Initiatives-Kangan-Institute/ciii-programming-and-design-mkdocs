# Events and the DOM

JavaScript can respond to user actions like clicks and key presses. To make that happen, you work with the Document Object Model (DOM) and event listeners.

---

## What is the DOM?

The DOM is a programming interface for HTML. When a browser loads a page, it creates a tree-like model of the document. JavaScript can access and change any part of this tree.

```html
<body>
    <h1 id="title">Welcome</h1>
    <button class="btn">Click me</button>
</body>
```

---

## Selecting DOM Elements

Use `document.querySelector()` to select an element:

```javascript
let heading = document.querySelector("#title");
let button = document.querySelector(".btn");
```

- Pass a CSS selector string (`#` for ID, `.` for class, tag name for element)
- `querySelector` returns the first matching element

To select multiple elements:

```javascript
let allParagraphs = document.querySelectorAll("p");
```

---

## Changing Content

Once you have a reference to an element, you can change its content:

```javascript
let heading = document.querySelector("#title");
heading.textContent = "Goodbye";
heading.style.color = "blue";
```

---

## The Load Order

JavaScript runs as soon as the browser encounters it. If your script tries to select an element that has not loaded yet, it will fail. Solutions:

Place your `<script>` tag just before the closing `</body>`:

```html
<body>
    <h1>Hello</h1>
    <script src="script.js"></script>
</body>
```

Or wrap your code in a `DOMContentLoaded` event:

```javascript
document.addEventListener("DOMContentLoaded", function () {
    let heading = document.querySelector("h1");
    heading.textContent = "Page loaded!";
});
```

---

## Events

Events are things that happen in the browser — clicks, key presses, page loads, form submissions.

### Click Events

```javascript
let button = document.querySelector(".btn");

button.addEventListener("click", function () {
    console.log("Button was clicked!");
});
```

### Input Events

```javascript
let input = document.querySelector("#name");

input.addEventListener("input", function () {
    console.log("User typed: " + input.value);
});
```

---

## Event, Function, and Variables

Every interactive feature follows the same pattern:

1. **Select** an element (variable)
2. **Write** a function that does something
3. **Attach** the function to an event

```javascript
let btn = document.querySelector("#submitBtn");       // variable

function showMessage() {                              // function
    alert("Form submitted!");
}

btn.addEventListener("click", showMessage);           // event
```

---

## Summary

- The DOM is the browser's representation of the HTML page
- Use `querySelector()` to find elements
- `addEventListener()` runs code in response to user actions
- Place scripts at the end of `<body>` or use `DOMContentLoaded` for correct load order
