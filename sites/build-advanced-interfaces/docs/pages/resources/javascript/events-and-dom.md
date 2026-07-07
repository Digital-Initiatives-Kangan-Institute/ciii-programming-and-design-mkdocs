# Events and the DOM

Events let your page respond to user actions. The DOM (Document Object Model) is the browser's representation of your HTML that JavaScript can interact with. Together, they make web pages interactive.

---

## The DOM

When a browser loads an HTML page, it creates a tree of objects representing every element. This tree is called the DOM.

```html
<html>
<body>
    <h1 id="title">Welcome</h1>
    <p class="description">This is a paragraph.</p>
    <button id="myButton">Click Me</button>
</body>
</html>
```

```
        document
           |
         <html>
           |
         <body>
        /   |   \
     <h1>  <p>  <button>
```

JavaScript can access and modify any element in this tree.

---

## Selecting Elements

You must select an element before you can interact with it.

### By ID

```javascript
let title = document.getElementById("title");
title.textContent = "New Title";
```

### By Class

```javascript
let paragraphs = document.getElementsByClassName("description");
// Returns a live HTMLCollection — like an array

for (let p of paragraphs) {
    p.style.color = "blue";
}
```

### By CSS Selector

```javascript
// First match
let button = document.querySelector("#myButton");
let firstParagraph = document.querySelector(".description");

// All matches
let allParagraphs = document.querySelectorAll("p");
allParagraphs.forEach(p => {
    p.style.fontSize = "18px";
});
```

`querySelector` and `querySelectorAll` are the most flexible — they accept any CSS selector.

---

## Modifying Elements

### Changing Content

```javascript
let heading = document.getElementById("title");

heading.textContent = "Updated Heading";         // Plain text (safe)
heading.innerHTML = "<b>Updated</b> Heading";    // HTML (use carefully)
```

Prefer `textContent` for plain text — it is safer and faster. Use `innerHTML` only when you need to insert actual HTML.

### Changing Styles

```javascript
let box = document.querySelector(".card");

box.style.backgroundColor = "#f5f5f5";
box.style.padding = "20px";
box.style.borderRadius = "8px";
box.style.display = "none";    // Hide the element
```

### Changing Attributes

```javascript
let link = document.querySelector("a");
link.href = "https://new-url.com";
link.target = "_blank";

let image = document.querySelector("img");
image.src = "new-photo.jpg";
image.alt = "Updated description";
```

### Adding and Removing CSS Classes

```javascript
let element = document.querySelector(".card");

element.classList.add("highlight");      // Add a class
element.classList.remove("hidden");      // Remove a class
element.classList.toggle("dark-mode");   // Toggle on/off
element.classList.contains("active");    // Check if class exists (true/false)
```

Using `classList` is cleaner than setting `element.className` directly — it preserves existing classes.

---

## Creating and Removing Elements

### Creating

```javascript
// Create a new element
let newParagraph = document.createElement("p");
newParagraph.textContent = "I was created by JavaScript!";
newParagraph.classList.add("dynamic-content");

// Add it to the page
document.body.appendChild(newParagraph);

// Or insert it into a specific container
let container = document.getElementById("content");
container.appendChild(newParagraph);
```

### Removing

```javascript
let element = document.getElementById("old-banner");
element.remove();   // Modern, simple

// Older approach (still works):
// element.parentNode.removeChild(element);
```

---

## Events

Events are notifications that something happened — a click, a keypress, a form submission. You write **event handlers** to respond.

### Adding Event Listeners

```javascript
let button = document.getElementById("myButton");

button.addEventListener("click", function() {
    console.log("Button was clicked!");
});
```

The pattern: select the element, then call `addEventListener(eventType, handlerFunction)`.

### The Event Object

Every event handler receives an event object with information about what happened:

```javascript
button.addEventListener("click", function(event) {
    console.log(event.type);           // "click"
    console.log(event.target);         // The element that was clicked
    console.log(event.clientX);        // Mouse X position
    console.log(event.clientY);        // Mouse Y position
});

document.addEventListener("keydown", function(event) {
    console.log(event.key);            // "Enter", "a", "Escape", etc.
    console.log(event.code);           // "KeyA", "Space", "Enter"
    console.log(event.shiftKey);       // true if Shift was held
});
```

---

## Common Events

### Click

```javascript
button.addEventListener("click", function() {
    alert("Clicked!");
});
```

### Input Change

```javascript
let input = document.getElementById("search");

input.addEventListener("input", function(event) {
    console.log("Current value:", event.target.value);
});
```

### Form Submit

```javascript
let form = document.getElementById("loginForm");

form.addEventListener("submit", function(event) {
    event.preventDefault();   // Stop the page from reloading!

    let username = document.getElementById("username").value;
    let password = document.getElementById("password").value;

    console.log("Logging in:", username);
    // Send to API...
});
```

`event.preventDefault()` is essential for forms — without it, the browser navigates away.

### Keyboard

```javascript
document.addEventListener("keydown", function(event) {
    if (event.key === "Escape") {
        console.log("Escape pressed — closing modal");
    }

    if (event.key === "Enter" && event.ctrlKey) {
        console.log("Ctrl+Enter pressed");
    }
});
```

### Mouse Events

```javascript
let hoverElement = document.querySelector(".tooltip");

hoverElement.addEventListener("mouseenter", function() {
    console.log("Mouse entered");
});

hoverElement.addEventListener("mouseleave", function() {
    console.log("Mouse left");
});
```

---

## Load Order

JavaScript runs as soon as the browser encounters it. If your script runs before the HTML elements exist, `document.getElementById()` returns `null`.

### Solution 1: Place Scripts at the Bottom

```html
<body>
    <!-- All HTML content -->
    <script src="app.js"></script>
</body>
```

### Solution 2: Use defer

```html
<head>
    <script src="app.js" defer></script>
</head>
```

`defer` downloads the script in parallel but waits to execute until the DOM is fully built.

### Solution 3: DOMContentLoaded Event

```javascript
document.addEventListener("DOMContentLoaded", function() {
    // DOM is ready — safe to access elements
    let button = document.getElementById("myButton");
    button.addEventListener("click", handleClick);
});
```

---

## Common Patterns

### Toggle Visibility

```javascript
let toggleBtn = document.getElementById("toggleBtn");
let content = document.getElementById("content");

toggleBtn.addEventListener("click", function() {
    content.classList.toggle("hidden");
});
```

```css
.hidden {
    display: none;
}
```

### Character Counter

```javascript
let textarea = document.getElementById("message");
let counter = document.getElementById("charCount");
let maxLength = 200;

textarea.addEventListener("input", function() {
    let remaining = maxLength - textarea.value.length;
    counter.textContent = `${remaining} characters remaining`;

    if (remaining < 20) {
        counter.style.color = "red";
    } else {
        counter.style.color = "black";
    }
});
```

### Dynamic List

```javascript
let addBtn = document.getElementById("addBtn");
let input = document.getElementById("itemInput");
let list = document.getElementById("itemList");

addBtn.addEventListener("click", function() {
    let text = input.value.trim();
    if (!text) return;

    let li = document.createElement("li");
    li.textContent = text;

    let deleteBtn = document.createElement("button");
    deleteBtn.textContent = "Delete";
    deleteBtn.addEventListener("click", function() {
        li.remove();
    });

    li.appendChild(deleteBtn);
    list.appendChild(li);
    input.value = "";
});
```

---

## Why This Matters for Next.js

Next.js handles events differently (camelCase props like `onClick`), but the underlying concepts are identical:

- You still listen for user actions
- You still prevent default form behaviour
- You still access input values from event objects
- You still conditionally show/hide elements

The syntax changes — the mental model stays the same.

---

## Summary

- The **DOM** is the browser's tree of HTML elements — JavaScript can read and modify it
- Use `querySelector()` and `querySelectorAll()` to find elements
- Use `addEventListener(eventType, handler)` to respond to user actions
- Always `event.preventDefault()` on form submissions
- Handle **load order** with `defer`, `DOMContentLoaded`, or placing scripts at the bottom
- Modify the DOM with `textContent`, `classList`, `style`, `createElement`, and `remove()`
