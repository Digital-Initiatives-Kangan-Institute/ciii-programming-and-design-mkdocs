# Linking JavaScript

Before you can write interactive features, you need to connect JavaScript to your HTML page. This page covers the basics of linking a `.js` file and running your first line of code.

---

## Writing Your First JavaScript

Create a file called `script.js`:

```javascript
console.log("Hello world");
```

`console.log()` prints a message to the browser's developer console. It is the simplest way to see output from your JavaScript code.

---

## Linking an External JavaScript File

The recommended way to add JavaScript to a page is through an external file using the `<script>` tag with a `src` attribute:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Page</title>
</head>
<body>
    <h1>Welcome</h1>

    <script src="script.js"></script>
</body>
</html>
```

The `<script>` tag is placed just before the closing `</body>` tag so that the HTML loads before the JavaScript runs.

---

## Load Order

The browser reads HTML from top to bottom. If a `<script>` appears in the `<head>`, it runs before the body content exists:

```html
<head>
    <script src="script.js"></script>   <!-- runs before body loads -->
</head>
<body>
    <h1 id="title">Hello</h1>
</body>
```

```javascript
// This fails because #title does not exist yet
let heading = document.querySelector("#title");
```

Placing `<script>` at the end of `<body>` avoids this problem:

```html
<body>
    <h1 id="title">Hello</h1>
    <script src="script.js"></script>   <!-- runs after body loads -->
</body>
```

---

## Internal vs External JavaScript

### Internal

JavaScript written directly inside a `<script>` tag in the HTML file:

```html
<body>
    <h1>Welcome</h1>
    <script>
        console.log("Hello world");
    </script>
</body>
```

Useful for quick tests, but harder to maintain across multiple pages.

### External

JavaScript in a separate `.js` file linked with `<script src="...">`:

```html
<body>
    <h1>Welcome</h1>
    <script src="script.js"></script>
</body>
```

The same file can be linked from multiple pages. This is the standard approach for real projects.

---

## Viewing the Console

To see the output of `console.log()`, open your browser's developer tools:

1. Right-click anywhere on the page and select **Inspect**
2. Click the **Console** tab
3. You should see `Hello world` printed

The console is your main tool for debugging and testing JavaScript as you develop.

---

## A Working Example

```
my-site/
├── index.html
└── script.js
```

`index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Site</title>
</head>
<body>
    <h1>JavaScript Linked</h1>
    <p>Open the console to see the message.</p>

    <script src="script.js"></script>
</body>
</html>
```

`script.js`:

```javascript
console.log("Hello world");
console.log("JavaScript is linked and working!");
```

---

## Summary

- Link a JavaScript file with `<script src="script.js"></script>`
- Place the `<script>` tag at the end of `<body>` so HTML loads first
- Use `console.log()` to print messages to the browser console
- External `.js` files are the standard approach for real projects
- Open the browser console (F12 > Console) to see your output
