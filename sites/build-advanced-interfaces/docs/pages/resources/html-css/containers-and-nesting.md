# Containers and Nesting

HTML elements can be placed inside other elements to build structure and hierarchy. Container elements like `<div>` and `<span>` are used to group content for styling and layout.

---

## Nested Elements

Nesting means placing one element inside another. The outer element is the **parent**, and the inner element is the **child**:

```html
<div>
    <h2>Menu</h2>
    <p>All our items are made fresh daily.</p>
</div>
```

### Nesting Rules

- Always close tags in the reverse order they were opened
- Block-level elements can contain other block elements and inline elements
- Inline elements should only contain other inline elements

```html
<!-- Correct: p contains strong (inline in block) -->
<p>This is <strong>important</strong> text.</p>

<!-- Incorrect: block element inside inline element -->
<strong><p>Do not do this.</p></strong>
```

---

## `<div>` — The Block Container

`<div>` is a block-level container. It takes up the full width available and starts on a new line. Use `<div>` to group sections of content:

```html
<div class="hero-section">
    <h1>Welcome to Our Cafe</h1>
    <p>Fresh coffee and homemade pastries.</p>
</div>

<div class="featured-items">
    <h2>Today's Specials</h2>
    <p>Try our new summer salad.</p>
</div>
```

`<div>` has no visual appearance by default — it exists purely to group content and provide a target for CSS styling.

---

## `<span>` — The Inline Container

`<span>` is an inline container. It stays within the flow of text and only takes up as much width as its content needs:

```html
<p>Our coffee is <span class="price">$4.50</span> per cup.</p>
```

Use `<span>` to style or target a portion of text without breaking the line.

---

## `<div>` vs `<span>`

| | `<div>` | `<span>` |
|---|---|---|
| Display | Block (full width, new line) | Inline (fits within text) |
| Use case | Grouping sections, cards, layouts | Highlighting words or phrases |
| Common with | CSS layouts, Flexbox, Grid | Styling text fragments |

---

## Semantic Containers

HTML5 introduced semantic elements that describe the *meaning* of the content they contain:

```html
<body>
    <header>
        <h1>My Website</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
        </nav>
    </header>

    <main>
        <section>
            <h2>About Us</h2>
            <p>We are a family-run business.</p>
        </section>

        <article>
            <h2>Latest News</h2>
            <p>A new store opens next month.</p>
        </article>

        <aside>
            <h3>Opening Hours</h3>
            <p>Mon–Fri: 7am–4pm</p>
        </aside>
    </main>

    <footer>
        <p>Contact: hello@example.com</p>
    </footer>
</body>
```

| Element | Purpose |
|---|---|
| `<header>` | Introductory content or navigation at the top of a page/section |
| `<nav>` | Primary navigation links |
| `<main>` | The unique content of the page (use only one per page) |
| `<section>` | A thematic grouping of content, typically with a heading |
| `<article>` | Self-contained content that could stand alone |
| `<aside>` | Content tangentially related to the main content (sidebar) |
| `<footer>` | Closing content at the bottom of a page/section |

### Why Use Semantic Elements?

- Screen readers use them to help users navigate
- Search engines use them to understand page structure
- They make your code more readable and maintainable

---

## Summary

- Nesting creates parent-child relationships between elements
- `<div>` is a block container for grouping sections
- `<span>` is an inline container for text-level styling
- Semantic elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`) describe the role of content
- Prefer semantic containers over generic `<div>` whenever possible
