# HTML and CSS

This resource covers the fundamentals of HTML and CSS, the building blocks of every website. You will learn how to structure content with HTML and style it with CSS.

---

## HTML Structure

HTML documents follow a standard structure that every browser understands.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Page</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

The `<!DOCTYPE html>` declaration tells the browser this is an HTML5 document. The `<html>` element is the root, containing `<head>` (metadata) and `<body>` (visible content).

---

## Basic Elements

### Headings

Headings define the hierarchy of your content, from `<h1>` (most important) to `<h6>` (least important).

```html
<h1>Main Title</h1>
<h2>Section Heading</h2>
<h3>Sub-section</h3>
```

### Paragraphs and Text Formatting

```html
<p>This is a paragraph of text.</p>
<p>This text is <b>bold</b> and this is <i>italic</i>.</p>
```

- `<p>` — paragraph
- `<b>` — bold text
- `<i>` — italic text
- `<hr>` — horizontal rule (a visual divider)

### Element Structure

Every HTML element follows the same pattern:

```
<tagname>Content goes here</tagname>
```

Elements have an opening tag, content, and a closing tag.

---

## Nested Elements

Elements can be placed inside other elements to create complex layouts.

```html
<div>
    <h2>Article Title</h2>
    <p>This paragraph is <b>nested</b> inside the div.</p>
</div>
```

Always ensure tags are closed in the correct order — the last tag opened should be the first one closed.

---

## Containers

Containers group related content together for layout and styling purposes.

- `<div>` — a block-level container
- `<span>` — an inline container

```html
<div>
    <h2>Product</h2>
    <p>Price: <span>$19.99</span></p>
</div>
```

---

## Linking CSS to HTML

There are three ways to apply CSS to an HTML document:

### Inline CSS

Applied directly to an element using the `style` attribute.

```html
<p style="color: red;">This text is red.</p>
```

### Internal CSS

Placed inside a `<style>` element in the `<head>`.

```html
<head>
    <style>
        p { color: blue; }
    </style>
</head>
```

### External CSS

Linked from a separate `.css` file (recommended approach).

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

---

## CSS Selectors

Selectors determine which elements a CSS rule applies to.

### Element Selector

Targets all instances of an HTML element.

```css
p {
    color: green;
}
```

### ID Selector

Targets a single element with a specific `id`. Prefixed with `#`.

```css
#hero-banner {
    background-color: black;
}
```

```html
<div id="hero-banner">Welcome!</div>
```

### Class Selector

Targets all elements with a specific `class`. Prefixed with `.`.

```css
.highlight {
    background-color: yellow;
}
```

```html
<p class="highlight">Important text</p>
<span class="highlight">Also highlighted</span>
```

---

## CSS Structure

A CSS rule consists of a selector and a declaration block.

```css
selector {
    property: value;
}
```

- **Selector** — which element(s) to style
- **Property** — what aspect to change
- **Value** — what to set it to
- Each declaration must end with a `;`

Multiple declarations can be grouped:

```css
h1 {
    color: navy;
    font-size: 2rem;
    text-align: center;
}
```

---

## Summary

- HTML provides the **structure** and **content** of a webpage
- CSS controls the **presentation** and **styling**
- Use external stylesheets for maintainability
- Master selectors (element, class, ID) to target the right elements
