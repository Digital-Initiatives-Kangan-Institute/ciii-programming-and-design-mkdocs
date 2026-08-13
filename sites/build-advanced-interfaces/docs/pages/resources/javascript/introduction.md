# Introduction to JavaScript

JavaScript is the programming language of the web. It brings interactivity and dynamic behaviour to HTML pages, allowing you to respond to user actions, manipulate content, and communicate with servers.

---

## What is JavaScript?

JavaScript is a high-level, interpreted programming language that runs in the browser. Every modern web browser has a built-in JavaScript engine that executes your code directly on the user's device.

- JavaScript makes pages **interactive** — responding to clicks, keystrokes, and form submissions
- JavaScript can **modify HTML and CSS** while the page is running
- JavaScript can **fetch data** from servers without reloading the page
- JavaScript is **not** the same as Java — the similar name is a historical coincidence

---

## The Three Layers of the Web

Web pages are built with three technologies working together:

| Layer | Technology | Role |
|---|---|---|
| Structure | HTML | Defines the content and elements on the page |
| Presentation | CSS | Controls colours, fonts, layout, and visual styling |
| Behaviour | JavaScript | Adds interactivity, logic, and dynamic updates |

A good way to think about it: HTML is the skeleton, CSS is the skin and clothes, and JavaScript is the muscles that make everything move.

---

## Where JavaScript Runs

JavaScript was originally created for the browser, but it now runs in many environments:

### In the Browser (Client-Side)

This is where you will be writing JavaScript. Every major browser (Chrome, Firefox, Safari, Edge) has a JavaScript engine.

### On the Server (Node.js)

Node.js allows JavaScript to run outside the browser, on a server. Tools like Next.js use Node.js under the hood.

### In This Course

You will start with browser-based JavaScript, then later use JavaScript inside Next.js applications for both the front-end and back-end.

---

## A First Look at JavaScript

Here is a simple example that changes the text of a heading when a button is clicked:

`index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Script</title>
</head>
<body>
    <h1 id="heading">Original Text</h1>
    <button id="changeBtn">Change Text</button>

    <script src="script.js"></script>
</body>
</html>
```

`script.js`:

```javascript
let heading = document.querySelector("#heading");
let button = document.querySelector("#changeBtn");

button.addEventListener("click", () => {
    heading.textContent = "Text changed by JavaScript!";
});
```

Don't worry about understanding every line yet — each piece will be covered in the resources that follow.

---

## What You Will Learn

The JavaScript section of this site is organised into these topics:

- **Linking JavaScript** — connecting `.js` files to HTML and using the browser console
- **Variables and Data Types** — storing and working with data
- **Control Flow** — making decisions and repeating actions with `if` statements and loops
- **Functions** — writing reusable blocks of code
- **Events and the DOM** — responding to user actions and modifying the page
- **Bootstrap** — using a CSS/JS framework for faster UI development

---

## Summary

- JavaScript adds interactivity and dynamic behaviour to web pages
- It is the third layer of the web, alongside HTML (structure) and CSS (presentation)
- JavaScript runs in the browser on the user's device
- This course covers JavaScript from the basics through to building full Next.js applications
- Start with **Linking JavaScript** to write and run your first line of code
