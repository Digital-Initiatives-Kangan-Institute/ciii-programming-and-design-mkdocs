# HTML Fundamentals

HTML (HyperText Markup Language) is the foundation of every website. It defines the structure and meaning of content. Every Next.js component ultimately renders HTML, so understanding it is essential.

---

## What is HTML?

HTML tells a web browser what each part of a page is — headings, paragraphs, images, links, buttons, and forms. It uses **tags** to mark up content so the browser can display it correctly.

HTML is not a programming language. It cannot perform calculations or make decisions. It is a **markup language** that describes document structure.

---

## The HTML5 Document Structure

Every HTML document follows this standard skeleton:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Page</title>
</head>
<body>
    <!-- All visible content goes here -->
</body>
</html>
```

### What Each Part Does

| Element | Purpose |
|---|---|
| `<!DOCTYPE html>` | Tells the browser this is an HTML5 document |
| `<html>` | The root element wrapping everything |
| `<head>` | Metadata — title, character set, stylesheets, scripts |
| `<meta charset="UTF-8">` | Supports all languages and symbols |
| `<meta name="viewport">` | Ensures proper scaling on mobile devices |
| `<title>` | Text shown in the browser tab |
| `<body>` | All visible page content |

---

## Element Structure

Every HTML element (with a few exceptions) follows this pattern:

```
<tagname>Content goes here</tagname>
```

- **Opening tag**: `<tagname>`
- **Content**: The text or nested elements inside
- **Closing tag**: `</tagname>`

Some elements are **self-closing** (no content or closing tag):

```html
<br>       <!-- Line break -->
<hr>       <!-- Horizontal rule -->
<img src="photo.jpg" alt="A photo">   <!-- Image -->
<input type="text">   <!-- Form input -->
```

---

## Basic Elements

### Headings

Headings create a content hierarchy. Use them in order — `<h1>` is the most important, `<h6>` the least.

```html
<h1>Main Page Title</h1>
<h2>Major Section</h2>
<h3>Sub-section</h3>
<h4>Sub-sub-section</h4>
<h5>Minor heading</h5>
<h6>Least important heading</h6>
```

A page should have exactly **one** `<h1>`. Search engines and screen readers use headings to understand page structure.

### Paragraphs

```html
<p>This is a paragraph of text. Browsers automatically add spacing before and after paragraphs.</p>
<p>This is another paragraph.</p>
```

### Text Formatting

```html
<p>This text is <b>bold</b> and this is <i>italic</i>.</p>
<p>This is <strong>semantically important</strong> text.</p>
<p>This is <em>emphasised</em> text.</p>
```

- `<b>` — bold (visual)
- `<i>` — italic (visual)
- `<strong>` — important (semantic, usually bold)
- `<em>` — emphasised (semantic, usually italic)

Prefer `<strong>` and `<em>` over `<b>` and `<i>` because they convey meaning to screen readers and search engines.

### Links

```html
<a href="https://example.com">Visit Example</a>
<a href="/about">About Page</a>
<a href="mailto:hello@example.com">Email Us</a>
<a href="https://example.com" target="_blank">Open in new tab</a>
```

### Images

```html
<img src="photo.jpg" alt="A sunset over the ocean" width="400">
```

Always include the `alt` attribute — it provides a text description for screen readers and displays if the image fails to load.

### Lists

**Unordered list** (bullet points):

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

**Ordered list** (numbered):

```html
<ol>
    <li>Preheat oven to 180 degrees</li>
    <li>Mix ingredients</li>
    <li>Bake for 20 minutes</li>
</ol>
```

### Horizontal Rule

```html
<p>Section one content.</p>
<hr>
<p>Section two content.</p>
```

---

## Nested Elements

Elements can contain other elements. This is how you build complex layouts.

```html
<div>
    <h2>Article Title</h2>
    <p>This paragraph is <b>nested</b> inside the div.</p>
    <ul>
        <li>Item one</li>
        <li>Item two</li>
    </ul>
</div>
```

**Rule**: The last tag opened must be the first tag closed.

```html
<!-- CORRECT -->
<div><p><b>Hello</b></p></div>

<!-- WRONG — overlapping tags -->
<div><p><b>Hello</div></p></b>
```

---

## Block vs Inline Elements

Understanding the difference is critical for layout.

### Block Elements

Block elements start on a new line and take up the full width available.

```html
<div>I am a block</div>
<p>I am also a block</p>
<h2>Me too</h2>
<section>And me</section>
```

Common block elements: `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`, `<article>`, `<header>`, `<footer>`, `<nav>`, `<ul>`, `<ol>`, `<li>`, `<hr>`

### Inline Elements

Inline elements stay within the flow of text and only take up as much width as needed.

```html
<p>This is <span>inline</span>, and so is <a href="#">this link</a>.</p>
```

Common inline elements: `<span>`, `<a>`, `<b>`, `<i>`, `<strong>`, `<em>`, `<img>`, `<code>`

---

## Containers

Containers group related content for styling and layout.

### `<div>` — Block Container

```html
<div class="card">
    <h2>Product Name</h2>
    <p>Product description goes here.</p>
    <p>Price: $29.99</p>
</div>
```

### `<span>` — Inline Container

```html
<p>Total: <span class="price">$49.99</span></p>
```

Divs and spans have no visual meaning by themselves — their power comes from CSS classes and IDs.

---

## Semantic HTML

Semantic elements describe their purpose to both the browser and the developer.

```html
<!-- Non-semantic -->
<div class="header">...</div>
<div class="nav">...</div>
<div class="main">...</div>
<div class="footer">...</div>

<!-- Semantic -->
<header>...</header>
<nav>...</nav>
<main>...</main>
<footer>...</footer>
```

| Semantic Element | What It Represents |
|---|---|
| `<header>` | Page or section header |
| `<nav>` | Navigation links |
| `<main>` | Primary page content |
| `<section>` | Thematic grouping of content |
| `<article>` | Self-contained content (blog post, news item) |
| `<aside>` | Sidebar or tangential content |
| `<footer>` | Page or section footer |

Semantic HTML improves accessibility, SEO, and makes your code easier to read.

---

## Forms

Forms collect user input. They are fundamental to interactive web applications.

```html
<form action="/submit" method="POST">
    <div>
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
    </div>

    <div>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
    </div>

    <div>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required>
    </div>

    <div>
        <label for="message">Message:</label>
        <textarea id="message" name="message" rows="4"></textarea>
    </div>

    <button type="submit">Submit</button>
</form>
```

### Input Types

| Type | Use |
|---|---|
| `text` | Single line text |
| `email` | Email address (triggers email keyboard on mobile) |
| `password` | Masked text input |
| `number` | Numeric input |
| `checkbox` | Toggle on/off |
| `radio` | Select one from a group |
| `date` | Date picker |
| `file` | File upload |
| `submit` | Submit the form |

---

## Tables

Tables display structured data in rows and columns.

```html
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Role</th>
            <th>Department</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice</td>
            <td>Developer</td>
            <td>Engineering</td>
        </tr>
        <tr>
            <td>Bob</td>
            <td>Designer</td>
            <td>Design</td>
        </tr>
    </tbody>
</table>
```

- `<table>` — table container
- `<thead>` — header rows
- `<tbody>` — body rows
- `<tr>` — table row
- `<th>` — header cell (bold, centred)
- `<td>` — data cell

---

## Why This Matters for Next.js

Every component in Next.js ultimately returns HTML. When you write:

```typescript
export default function MyComponent() {
    return (
        <div>
            <h1>Hello</h1>
            <p>Welcome to my site.</p>
        </div>
    );
}
```

This JSX compiles down to HTML. Understanding the underlying HTML makes you a better React developer — you will know what elements to use and how they behave in the browser.

---

## Summary

- HTML defines the **structure** and **meaning** of web content
- Every HTML document starts with `<!DOCTYPE html>` and has `<head>` and `<body>`
- Elements have opening and closing tags: `<tagname>content</tagname>`
- **Block** elements start on a new line; **inline** elements flow within text
- **Semantic HTML** uses meaningful tags (`<nav>`, `<main>`, `<article>`) for better accessibility
- **Forms** and **tables** are essential for interactive applications
- Always close tags in the right order — innermost first
