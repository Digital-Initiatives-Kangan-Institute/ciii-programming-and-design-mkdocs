# The Box Model

Every HTML element is a rectangular box. The CSS Box Model describes how these boxes are sized and how they interact with surrounding elements.

---

## The Four Layers

Each element's box consists of four concentric layers:

```
+-----------------------------+
|           margin            |
|   +---------------------+   |
|   |       border        |   |
|   |   +-----------+    |   |
|   |   |  padding  |    |   |
|   |   | +-------+ |    |   |
|   |   | |content| |    |   |
|   |   | +-------+ |    |   |
|   |   +-----------+    |   |
|   +---------------------+   |
+-----------------------------+
```

1. **Content** — the actual text, image, or child elements
2. **Padding** — space between the content and the border (inside the element)
3. **Border** — the line surrounding the padding and content
4. **Margin** — space between the border and neighbouring elements (outside the element)

---

## Setting Width and Height

The `width` and `height` properties set the size of the **content area**:

```css
div {
    width: 300px;
    height: 200px;
}
```

The total space an element takes up is:

```
total width  = width + padding-left + padding-right + border-left + border-right + margin-left + margin-right
total height = height + padding-top + padding-bottom + border-top + border-bottom + margin-top + margin-bottom
```

---

## `box-sizing`

By default, `width` sets the content width only. Adding padding and border increases the total size. This often causes layout surprises.

`box-sizing: border-box` changes this behaviour so `width` includes content, padding, and border:

```css
/* Apply universally */
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

With `border-box`:

```css
div {
    width: 300px;
    padding: 20px;
    border: 5px solid #333;
    /* Total width = 300px (content shrinks to 250px) */
}
```

Most modern CSS resets start with `box-sizing: border-box` on all elements. It makes layout maths far more predictable.

---

## Margin

Margin creates space **outside** the element's border:

```css
div {
    margin-top: 20px;
    margin-right: 15px;
    margin-bottom: 20px;
    margin-left: 15px;
}
```

Shorthand syntax:

```css
div { margin: 20px; }              /* all four sides */
div { margin: 20px 15px; }         /* top/bottom  right/left */
div { margin: 20px 15px 10px; }    /* top  right/left  bottom */
div { margin: 20px 15px 10px 5px; } /* top  right  bottom  left (clockwise) */
```

### Margin Collapse

Vertical margins of adjacent elements collapse — the larger margin wins, they do not add together:

```css
.top { margin-bottom: 30px; }
.bottom { margin-top: 20px; }
/* The gap between them is 30px, not 50px */
```

Margin collapse only affects vertical (top/bottom) margins, not horizontal ones.

### Auto Margins

Setting left and right margins to `auto` centres a block element horizontally:

```css
div {
    width: 600px;
    margin: 0 auto;
}
```

---

## Padding

Padding creates space **inside** the element's border, between the border and the content:

```css
div {
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 10px;
    padding-left: 20px;
}
```

The same shorthand applies:

```css
div { padding: 10px; }              /* all four sides */
div { padding: 10px 20px; }         /* top/bottom  right/left */
div { padding: 10px 20px 5px; }     /* top  right/left  bottom */
div { padding: 10px 20px 5px 15px; } /* top  right  bottom  left */
```

Unlike margins, padding never collapses.

---

## Border

The `border` property draws a line around the padding and content:

```css
div {
    border: 2px solid #333333;
}
```

The three values are: `width` `style` `colour`.

Border styles include: `solid`, `dashed`, `dotted`, `double`, `none`.

Individual sides:

```css
div {
    border-top: 3px solid red;
    border-bottom: 1px dashed #ccc;
    border-left: none;
}
```

### Border Radius

Rounded corners:

```css
div {
    border: 2px solid #333;
    border-radius: 8px;
}
```

A `border-radius` of `50%` on a square element creates a circle.

---

## Visualising the Box Model

To help visualise while developing, add temporary outlines:

```css
/* See all boxes */
* {
    outline: 1px solid red;
}
```

Browser DevTools (F12) also let you inspect the box model of any element visually.

---

## Summary

- Every element is a box with four layers: content, padding, border, margin
- `box-sizing: border-box` makes `width` include padding and border — use it globally
- Margins create space outside; padding creates space inside
- Vertical margins collapse; padding and horizontal margins do not
- `margin: 0 auto` centres a block element horizontally
- `border-radius` creates rounded corners
