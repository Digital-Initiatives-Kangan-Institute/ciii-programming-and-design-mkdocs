# CSS Fundamentals

CSS (Cascading Style Sheets) controls the visual appearance of HTML elements. Every React and Next.js component uses CSS — whether through stylesheets, inline styles, or CSS-in-JS libraries.

---

## What is CSS?

CSS describes how HTML elements should look. It controls colours, fonts, spacing, layout, animations, and responsive behaviour across different screen sizes.

A webpage without CSS is just unstyled text and images. CSS transforms it into a designed interface.

---

## Linking CSS to HTML

There are three ways to apply CSS:

### 1. Inline CSS

Applied directly to an element via the `style` attribute.

```html
<p style="color: red; font-size: 18px;">This text is red and 18 pixels.</p>
```

Use inline styles sparingly (or never in production). They mix content with presentation and are hard to maintain.

### 2. Internal CSS

Placed inside a `<style>` element in the `<head>`.

```html
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }

        .highlight {
            background-color: yellow;
        }
    </style>
</head>
```

Better than inline, but still tied to a single page. Not reusable across pages.

### 3. External CSS (Recommended)

Linked from a separate `.css` file.

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

```css
/* styles.css */
p {
    color: blue;
    font-size: 16px;
}

.highlight {
    background-color: yellow;
}
```

External stylesheets are reusable across every page, easy to maintain, and cached by the browser for fast loading.

---

## CSS Rule Structure

Every CSS rule has two parts:

```css
selector {
    property: value;
    property: value;
}
```

| Part | What It Does |
|---|---|
| **Selector** | Which elements to style |
| **Declaration block** | The styles to apply (inside `{}`) |
| **Property** | What aspect to change (`color`, `font-size`) |
| **Value** | What to set it to (`red`, `16px`) |

Each declaration must end with a semicolon `;`.

---

## Selectors

Selectors determine which elements receive the styles.

### Element Selector

Targets all instances of a tag.

```css
p {
    color: #333;
    line-height: 1.6;
}

h1, h2, h3 {
    font-family: Arial, sans-serif;
}
```

### Class Selector

Targets elements with a specific `class` attribute. Prefixed with `.`.

```css
.card {
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 16px;
    margin-bottom: 16px;
}

.text-center {
    text-align: center;
}
```

```html
<div class="card text-center">
    <p>I am a styled card.</p>
</div>
```

A single element can have multiple classes (space-separated). Classes are the most commonly used selector — they are reusable and descriptive.

### ID Selector

Targets a single unique element. Prefixed with `#`.

```css
#hero-banner {
    background-color: #1a1a2e;
    color: white;
    padding: 48px 24px;
}
```

```html
<div id="hero-banner">Welcome!</div>
```

Use IDs sparingly. Each ID must be unique on the page. Classes are preferred for styling.

### Descendant Selector

Targets elements nested inside another element.

```css
/* All <p> elements inside an <article> */
article p {
    color: #555;
}

/* All <li> elements inside a <nav> */
nav li {
    display: inline-block;
}
```

---

## The Box Model

Every HTML element is a rectangular box. Understanding the box model is essential for layout.

```
+------------------------------------------+
|               margin (outside)            |
|   +----------------------------------+   |
|   |        border                     |   |
|   |   +--------------------------+   |   |
|   |   |    padding                |   |   |
|   |   |   +------------------+   |   |   |
|   |   |   |    content       |   |   |   |
|   |   |   +------------------+   |   |   |
|   |   |                          |   |   |
|   |   +--------------------------+   |   |
|   |                                  |   |
|   +----------------------------------+   |
|                                          |
+------------------------------------------+
```

| Property | What It Controls |
|---|---|
| `content` | The actual text or image |
| `padding` | Space inside the border, around the content |
| `border` | The line around the padding and content |
| `margin` | Space outside the border, separating elements |

```css
div {
    width: 200px;
    padding: 16px;
    border: 2px solid black;
    margin: 20px;
}
/* Total width = 200 + 32 (padding) + 4 (border) + 40 (margin) = 276px */
```

Use `box-sizing: border-box` to include padding and border in the width:

```css
* {
    box-sizing: border-box;
}
```

---

## Common CSS Properties

### Text and Font

```css
p {
    color: #333;
    font-family: "Helvetica Neue", Arial, sans-serif;
    font-size: 16px;
    font-weight: 700;         /* bold */
    line-height: 1.5;
    text-align: center;       /* left, right, center, justify */
    text-decoration: underline;
    text-transform: uppercase;
}
```

### Background

```css
div {
    background-color: #f5f5f5;
    background-image: url("pattern.png");
    background-size: cover;
    background-position: center;
}
```

### Spacing

```css
.card {
    padding: 20px;            /* All sides */
    padding: 20px 10px;       /* Top/bottom | Left/right */
    padding: 10px 20px 10px 20px;  /* Top | Right | Bottom | Left */

    margin: 16px 0;           /* Top/bottom 16px, left/right 0 */
    margin: 0 auto;           /* Auto left and right = centre the element */
}
```

### Borders

```css
.box {
    border: 1px solid #ccc;
    border-radius: 8px;       /* Rounded corners */
    border-bottom: 3px solid red;  /* Override one side */
}
```

---

## Layout: Flexbox

Flexbox is the most common way to arrange elements in rows and columns.

```css
.container {
    display: flex;
    justify-content: space-between;  /* Horizontal alignment */
    align-items: center;             /* Vertical alignment */
    gap: 16px;                       /* Space between items */
    flex-wrap: wrap;                 /* Allow wrapping to next line */
}

.item {
    flex: 1;   /* Each item takes equal space */
}
```

```html
<div class="container">
    <div class="item">Left</div>
    <div class="item">Centre</div>
    <div class="item">Right</div>
</div>
```

### Common Flexbox Properties

| Property | Purpose |
|---|---|
| `display: flex` | Enables flexbox on a container |
| `justify-content` | Horizontal alignment (`center`, `space-between`, `space-around`) |
| `align-items` | Vertical alignment (`center`, `start`, `end`, `stretch`) |
| `flex-direction` | Row (default) or column |
| `gap` | Consistent spacing between items |
| `flex-wrap` | Allow items to wrap to multiple lines |

---

## CSS and Next.js

Next.js supports several ways to write CSS:

### Global CSS (imported in layout or _app)

```css
/* styles/globals.css */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}
```

### CSS Modules (scoped to one component)

```css
/* Button.module.css */
.primary {
    background-color: #3f51b5;
    color: white;
    padding: 8px 16px;
    border: none;
    border-radius: 4px;
}
```

```typescript
import styles from "./Button.module.css";

export default function Button() {
    return <button className={styles.primary}>Click</button>;
}
```

CSS Modules automatically generate unique class names, preventing style conflicts between components.

---

## Summary

- CSS controls the **visual appearance** of HTML elements
- Use **external stylesheets** for maintainability and caching
- **Selectors** target elements by tag, class (`.`), or ID (`#`)
- The **box model** defines how elements occupy space (content → padding → border → margin)
- **Flexbox** handles layout — rows, columns, alignment, and spacing
- In Next.js, use **global CSS** for site-wide styles and **CSS Modules** for component-scoped styles
