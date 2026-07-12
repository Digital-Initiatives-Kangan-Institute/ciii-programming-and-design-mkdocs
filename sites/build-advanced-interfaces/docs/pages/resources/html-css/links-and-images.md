# Links and Images

Links and images are what make the web interconnected and visual. The `<a>` element creates clickable links, and the `<img>` element embeds images.

---

## Links (`<a>`)

The anchor element creates a hyperlink — a clickable piece of text or content that navigates to another location:

```html
<a href="https://www.example.com">Visit Example</a>
```

### The `href` Attribute

`href` (hypertext reference) specifies the destination:

| Type | Example | Purpose |
|---|---|---|
| Absolute URL | `href="https://www.google.com"` | Link to an external website |
| Relative path | `href="about.html"` | Link to another page in the same folder |
| Relative path (subfolder) | `href="pages/contact.html"` | Link to a page in a subfolder |
| Root-relative | `href="/about"` | Link from the site root |
| Email | `href="mailto:hello@example.com"` | Open the user's email client |
| Telephone | `href="tel:+61300000000"` | Initiate a phone call on mobile |

### Relative vs Absolute Paths

```html
<!-- Absolute: full URL, works from anywhere -->
<a href="https://www.example.com/menu.html">Menu</a>

<!-- Relative: relative to the current page's location -->
<a href="menu.html">Menu</a>

<!-- Relative: go up one folder, then into another -->
<a href="../products/list.html">Products</a>
```

Use relative paths for links within your own site — they are shorter and more portable. Use absolute URLs for external sites.

### The `target` Attribute

```html
<a href="https://www.example.com" target="_blank">Open in new tab</a>
```

`target="_blank"` opens the link in a new browser tab. Always use this for external links sparingly — overusing it can be disorienting for users.

### Link Text

The visible text inside `<a>` is called the link text. Make it descriptive:

```html
<!-- Good: tells the user where they are going -->
<a href="menu.html">View our full menu</a>

<!-- Bad: generic and unhelpful -->
<a href="menu.html">Click here</a>
```

---

## Images (`<img>`)

The `<img>` element embeds an image into the page. It is a self-closing element:

```html
<img src="cafe-interior.jpg" alt="Our cosy cafe with wooden tables">
```

### The `src` Attribute

`src` specifies the path to the image file. It works the same way as `href` — you can use absolute URLs, relative paths, or root-relative paths:

```html
<!-- Online image -->
<img src="https://example.com/photo.jpg" alt="Photo">

<!-- Local file in the same folder -->
<img src="logo.png" alt="Company logo">

<!-- Local file in an images folder -->
<img src="images/banner.jpg" alt="Promotional banner">
```

### The `alt` Attribute

`alt` provides alternative text for the image. It serves three purposes:

1. **Accessibility** — screen readers read the alt text aloud
2. **Fallback** — displayed if the image fails to load
3. **SEO** — helps search engines understand the image content

Every `<img>` must have an `alt` attribute. If the image is purely decorative, use an empty string:

```html
<img src="decoration.png" alt="">
```

### Image Dimensions

Use the `width` and `height` attributes to reserve space before the image loads, preventing layout shifts:

```html
<img src="cafe.jpg" alt="Our cafe" width="800" height="600">
```

These should match the natural dimensions of the image. CSS can override the display size later.

---

## Linking Images

To make an image clickable, wrap it in an `<a>` element:

```html
<a href="https://www.example.com">
    <img src="banner.jpg" alt="Click to visit our sponsor">
</a>
```

---

## Summary

- `<a href="...">` creates links — use relative paths internally, absolute URLs externally
- `target="_blank"` opens links in a new tab
- `<img src="..." alt="...">` embeds images — always include `alt` text
- Images can be wrapped in links to make them clickable
- Write descriptive link text — avoid "click here"
