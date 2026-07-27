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
- **Declaration** — each `property: value;` line is a declaration

---

## Three Ways to Add CSS

### Inline CSS

Written directly inside an HTML element using the `style` attribute:

```html
<p style="color: blue; font-size: 18px;">This text is blue and 18 pixels.</p>
```

Affects only that single element. Avoid for anything beyond quick tests.

### Internal CSS

Placed inside a `<style>` element in the `<head>`:

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

Applies to all matching elements on that page.

### External CSS

Written in a separate `.css` file and linked in the `<head>`:

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

External CSS can be shared across multiple pages. This is the recommended approach for any real project.

---

## The Cascade

The "Cascading" in CSS means that styles can come from multiple sources and the browser decides which to apply based on priority:

1. Inline styles (highest priority)
2. Internal and external stylesheets (order matters — later rules override earlier ones)
3. Browser default styles (lowest priority)

When two rules have the same priority, **specificity** determines the winner. More specific selectors override less specific ones.

---

## Common CSS Properties at a Glance

| Property | Purpose | Example |
|---|---|---|
| `color` | Text colour | `color: #333333;` |
| `background-color` | Background colour | `background-color: #ffffff;` |
| `font-family` | Typeface | `font-family: Arial, sans-serif;` |
| `font-size` | Text size | `font-size: 16px;` |
| `font-weight` | Boldness | `font-weight: bold;` |
| `text-align` | Horizontal alignment | `text-align: center;` |
| `margin` | Outer spacing | `margin: 20px;` |
| `padding` | Inner spacing | `padding: 10px;` |
| `border` | Element border | `border: 1px solid #ccc;` |
| `width` / `height` | Dimensions | `width: 300px;` |
| `display` | Layout behaviour | `display: flex;` |

---

## Summary

- CSS rules follow: `selector { property: value; }`
- External stylesheets are best for multi-page sites
- The cascade determines which styles win when multiple rules target the same element
- CSS handles **presentation** — it works alongside HTML (structure)
- See the pages below for detailed coverage of selectors, the box model, typography, flexbox, and responsive design
