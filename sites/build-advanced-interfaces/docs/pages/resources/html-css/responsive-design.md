# Responsive Design

Responsive design ensures your website looks and works well on all screen sizes — from phones to desktop monitors.

---

## Why Responsive Design Matters

Users visit websites on a wide range of devices with different screen widths. A non-responsive site forces mobile users to pinch, zoom, and scroll horizontally, which is a poor experience.

Responsive design adapts the layout, typography, and interactions based on the viewport size.

---

## The Viewport Meta Tag

Every responsive page must include this in the `<head>`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Without it, mobile browsers render the page at a desktop width (typically 980px) and then shrink it down, making everything tiny.

---

## Media Queries

Media queries apply CSS rules only when certain conditions are met — most commonly based on screen width:

```css
/* Default: styles for all screen sizes go here */
.container {
    padding: 10px;
}

/* Applied when the screen is 768px or wider */
@media (min-width: 768px) {
    .container {
        padding: 20px;
    }
}

/* Applied when the screen is 1024px or wider */
@media (min-width: 1024px) {
    .container {
        padding: 40px;
    }
}
```

### Mobile-First vs Desktop-First

**Mobile-first** (recommended) starts with base styles for small screens and adds complexity as screens get larger using `min-width`:

```css
/* Base: mobile styles */
.grid { display: block; }

/* Tablet and up */
@media (min-width: 768px) {
    .grid { display: flex; }
}
```

**Desktop-first** starts with large screens and scales down using `max-width`:

```css
/* Base: desktop styles */
.grid { display: flex; }

/* Small screens */
@media (max-width: 767px) {
    .grid { display: block; }
}
```

Mobile-first is generally preferred because it forces you to prioritise content and results in leaner code on mobile.

---

## Common Breakpoints

These are typical screen-width breakpoints. Use them as a starting point, not rigid rules — design for your content, not specific devices:

| Breakpoint | Typical Device |
|---|---|
| 576px | Large phones in landscape |
| 768px | Tablets |
| 992px | Small laptops |
| 1024px | Tablets in landscape |
| 1200px | Desktop monitors |

---

## Responsive Units

### Percentage (`%`)

Relative to the parent container:

```css
img {
    max-width: 100%;
}
```

This ensures images never overflow their container.

### Viewport Units

Relative to the browser viewport:

```css
.hero {
    height: 100vh;          /* 100% of viewport height */
}

.wide-banner {
    width: 80vw;            /* 80% of viewport width */
}
```

| Unit | Relative To |
|---|---|
| `vw` | 1% of viewport width |
| `vh` | 1% of viewport height |
| `vmin` | 1% of the smaller viewport dimension |
| `vmax` | 1% of the larger viewport dimension |

### `rem` and `em`

Relative to font sizes (see the Colours and Typography page). Using relative font units means text scales naturally when users adjust their browser font size.

---

## Responsive Images

Serve appropriately sized images for different screens to save bandwidth:

```html
<img
    src="cafe-small.jpg"
    srcset="cafe-small.jpg 480w, cafe-medium.jpg 768w, cafe-large.jpg 1200w"
    sizes="(max-width: 768px) 100vw, 50vw"
    alt="Our cafe interior"
>
```

- `srcset` lists available image files and their widths
- `sizes` tells the browser how wide the image will be displayed at different breakpoints
- The browser chooses the best image based on the device's screen

For simpler cases, just use `max-width: 100%` in CSS:

```css
img {
    max-width: 100%;
    height: auto;
}
```

---

## Responsive Flexbox and Grid

Flexbox and CSS Grid are inherently responsive and work well with media queries:

```css
.grid {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
}

.card {
    flex: 1 1 250px;    /* grow, shrink, minimum 250px */
}

@media (min-width: 768px) {
    .card {
        flex: 1 1 300px;
    }
}
```

Items automatically flow onto new rows when they cannot fit at their minimum width.

---

## Testing Responsiveness

### Browser DevTools

Open DevTools (F12), then click the device toolbar icon (or press `Ctrl+Shift+M` / `Cmd+Shift+M`). This lets you simulate different screen sizes.

### Resize the Browser

Simply drag the browser window edge to see how your layout responds at different widths.

### Test on Real Devices

Nothing replaces testing on actual phones and tablets. Borrow a classmate's device if needed.

---

## Summary

- Always include the viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Use media queries (`@media`) to apply styles at specific screen widths
- Adopt a mobile-first approach — start small, then add complexity
- Use `%`, `vw`, `vh`, and `rem` for fluid sizing instead of fixed pixels
- `img { max-width: 100%; }` prevents images from overflowing
- Flexbox with `flex-wrap: wrap` creates responsive layouts without media queries
- Test on DevTools and real devices — do not assume it works everywhere
