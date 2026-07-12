# CSS Fundamentals

CSS (Cascading Style Sheets) controls the visual appearance of HTML content. It lets you define colours, fonts, spacing, layout, and more.

---

## What is CSS?

CSS is a stylesheet language that describes how HTML elements should be displayed. It separates content (HTML) from presentation (CSS), making your code cleaner and easier to maintain.

A CSS rule has three parts:

```css
selector {
    property: value;
}
```

- **Selector** — targets which HTML element(s) to style
- **Property** — what aspect of the element to change (e.g. `color`, `font-size`)
- **Value** — the setting for that property
- **Line ending** — each declaration ends with a semicolon `;`

---

## Three Ways to Add CSS

### Inline CSS

CSS is written directly inside an HTML element using the `style` attribute:

```html
<p style="color: blue; font-size: 18px;">This text is blue and 18 pixels.</p>
```

Inline CSS affects only that single element.

### Internal CSS

CSS is placed inside a `<style>` element in the `<head>` section:

```html
<head>
    <style>
        p {
            color: blue;
            font-size: 18px;
        }
    </style>
</head>
```

Internal CSS applies to all matching elements on that page.

### External CSS

CSS is written in a separate `.css` file and linked in the `<head>`:

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

External CSS can be shared across multiple pages, making it the most efficient approach for multi-page sites.

---

## Selectors

Selectors determine which elements receive the styles. There are three common types:

### Element Selector

Targets all elements of a given type:

```css
p {
    color: navy;
}

h1 {
    font-size: 32px;
}
```

### ID Selector

Targets a single element with a specific `id`. Prefixed with `#`:

```css
#hero-banner {
    background-color: #f0f0f0;
}
```

```html
<div id="hero-banner">Welcome</div>
```

### Class Selector

Targets any element with a specific `class`. Prefixed with `.`:

```css
.highlight {
    background-color: yellow;
    font-weight: bold;
}
```

```html
<p class="highlight">Important note</p>
<span class="highlight">Also highlighted</span>
```

---

## Selector Specificity

When multiple rules target the same element, the browser decides which to apply based on specificity:

1. ID selectors have the highest specificity
2. Class selectors are next
3. Element selectors have the lowest specificity

```css
p { color: black; }         /* low specificity */
.note { color: blue; }      /* higher */
#warning { color: red; }    /* highest */
```

---

## Common CSS Properties

```css
body {
    font-family: Arial, sans-serif;
    background-color: #ffffff;
    color: #333333;
    margin: 0;
    padding: 20px;
}

h1 {
    text-align: center;
}

p {
    line-height: 1.6;
}

img {
    max-width: 100%;
    height: auto;
}
```

---

## Summary

- CSS rules follow the pattern: `selector { property: value; }`
- CSS can be applied inline, internally, or externally
- External CSS is best for multi-page sites
- Element, ID, and class selectors let you target elements with different levels of specificity
- CSS handles **presentation** — it works alongside HTML (structure) and JavaScript (behaviour)
