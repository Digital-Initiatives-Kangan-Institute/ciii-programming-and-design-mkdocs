# Selectors and Specificity

Selectors determine which HTML elements receive CSS styles. Understanding them is essential for writing maintainable stylesheets.

---

## Basic Selectors

### Element (Type) Selector

Targets all elements of a given type:

```css
p {
    color: navy;
    line-height: 1.6;
}

h1 {
    font-size: 32px;
}
```

Every `<p>` on the page gets navy text; every `<h1>` gets 32px size.

### Class Selector

Targets elements with a specific `class` attribute. Prefixed with `.` (dot):

```css
.highlight {
    background-color: yellow;
    font-weight: bold;
}

.button-primary {
    background-color: #3f51b5;
    color: white;
}
```

```html
<p class="highlight">Important note</p>
<button class="button-primary">Submit</button>
```

A single element can have multiple classes:

```html
<div class="card featured">...</div>
```

When multiple HTML elements share the same class, **all of them** receive the styles from that class:

```html
<p class="highlight">This paragraph gets yellow background.</p>
<p class="highlight">So does this one.</p>
<p class="highlight">And this one too — every element with class="highlight".</p>
```

This is what makes classes so powerful: define a style once and apply it to as many elements as you need.

### ID Selector

Targets a single element with a specific `id`. Prefixed with `#` (hash):

```css
#hero-banner {
    background-image: url("hero.jpg");
    height: 400px;
}
```

```html
<div id="hero-banner">Welcome</div>
```

An `id` must be unique — only one element per page should use a given `id`.

---

## Universal Selector

The `*` selector matches every element:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

Commonly used in CSS resets to strip default browser styling.

---

## Combinator Selectors

Combinators express relationships between elements:

### Descendant Combinator (space)

Targets elements nested anywhere inside another:

```css
article p {
    color: #444;
}
```

Matches any `<p>` that is inside an `<article>`, no matter how deeply nested.

### Child Combinator (`>`)

Targets elements that are *direct children* only:

```css
nav > ul > li {
    display: inline-block;
}
```

Matches `<li>` elements that are direct children of `<ul>`, which is a direct child of `<nav>`. Deeper nesting is ignored.

### Adjacent Sibling Combinator (`+`)

Targets an element directly after another (same parent):

```css
h2 + p {
    margin-top: 0;
}
```

Matches a `<p>` that immediately follows an `<h2>`, sharing the same parent.

### General Sibling Combinator (`~`)

Targets all siblings after an element:

```css
h2 ~ p {
    font-style: italic;
}
```

Matches all `<p>` elements that come after an `<h2>` at the same level.

---

## Grouping Selectors

Apply the same styles to multiple selectors by separating them with commas:

```css
h1, h2, h3 {
    font-family: Georgia, serif;
    color: #333;
}
```

---

## Attribute Selectors

Target elements based on the presence or value of an attribute:

```css
/* All inputs with a type attribute */
input[type] { border: 1px solid #ccc; }

/* Inputs of type text specifically */
input[type="text"] { background-color: #fafafa; }

/* Links where href starts with https */
a[href^="https"] { color: green; }

/* Links where href ends with .pdf */
a[href$=".pdf"] { font-weight: bold; }

/* Links where href contains "example" */
a[href*="example"] { text-decoration: underline; }
```

---

## Specificity

When multiple rules target the same element, the browser decides which to apply based on specificity. Think of it as a scoring system:

| Selector Type | Specificity Weight | Example |
|---|---|---|
| Inline styles | 1,0,0,0 | `style="color: red"` |
| ID | 0,1,0,0 | `#header` |
| Class, attribute, pseudo-class | 0,0,1,0 | `.nav`, `[type="text"]`, `:hover` |
| Element, pseudo-element | 0,0,0,1 | `div`, `p`, `::before` |

Higher specificity wins. If specificity is equal, the rule that appears **last** in the stylesheet wins.

### Examples

```css
p { color: black; }                /* 0,0,0,1 */
.note { color: blue; }             /* 0,0,1,0 — wins over p */
#warning { color: red; }           /* 0,1,0,0 — wins over .note */
div p { color: green; }            /* 0,0,0,2 */
div .note { color: orange; }       /* 0,0,1,1 — wins over div p */
```

### The `!important` Exception

Adding `!important` overrides normal specificity:

```css
p {
    color: red !important;
}
```

Avoid `!important` whenever possible — it breaks the cascade and makes debugging difficult.

---

## Pseudo-Classes

Pseudo-classes target elements in a specific state:

```css
/* Unvisited link */
a:link { color: blue; }

/* Visited link */
a:visited { color: purple; }

/* Mouse hovering over element */
a:hover { text-decoration: underline; }

/* Element being clicked */
button:active { transform: scale(0.98); }

/* Element with keyboard focus */
input:focus { outline: 2px solid blue; }

/* First child of its parent */
li:first-child { font-weight: bold; }

/* Last child of its parent */
li:last-child { border-bottom: none; }

/* nth child (every odd row) */
tr:nth-child(odd) { background-color: #f9f9f9; }
```

---

## Summary

- Element, class (`.`), and ID (`#`) are the three basic selector types
- Combinators (` `, `>`, `+`, `~`) target elements based on their relationships
- Specificity determines which rule wins — ID > class > element
- Pseudo-classes (`:hover`, `:focus`, `:nth-child`) style elements based on state
- Prefer class selectors in most cases — they strike the best balance of specificity and reusability
