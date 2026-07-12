# Flexbox Layout

Flexbox (Flexible Box Layout) is a one-dimensional layout system for arranging items in rows or columns. It makes centring, spacing, and distributing elements simple without floats or positioning hacks.

---

## Enabling Flexbox

Set `display: flex` on a container element:

```css
.container {
    display: flex;
}
```

The container becomes a **flex container**, and its direct children become **flex items**.

---

## Main Axis and Cross Axis

Flexbox operates along two axes:

- **Main axis** — the primary direction items flow (horizontal by default)
- **Cross axis** — perpendicular to the main axis (vertical by default)

```
Main axis (→)
┌──────────────────────────────┐
│ ┌─────┐ ┌─────┐ ┌─────┐     │ ↕ Cross axis
│ │  1  │ │  2  │ │  3  │     │
│ └─────┘ └─────┘ └─────┘     │
└──────────────────────────────┘
```

By default, items flow left to right on the main axis. The `flex-direction` property controls this.

---

## Flex Direction

```css
.container {
    display: flex;
    flex-direction: row;            /* default: left to right */
}

.container {
    display: flex;
    flex-direction: column;         /* top to bottom */
}

.container {
    display: flex;
    flex-direction: row-reverse;    /* right to left */
}

.container {
    display: flex;
    flex-direction: column-reverse; /* bottom to top */
}
```

---

## Alignment on the Main Axis: `justify-content`

Controls how items are distributed along the main axis:

```css
.container {
    display: flex;
    justify-content: flex-start;    /* items at the start (default) */
}

.container {
    display: flex;
    justify-content: flex-end;      /* items at the end */
}

.container {
    display: flex;
    justify-content: center;        /* items centred */
}

.container {
    display: flex;
    justify-content: space-between; /* even spacing, no gaps at edges */
}

.container {
    display: flex;
    justify-content: space-around;  /* even spacing, half-size gaps at edges */
}

.container {
    display: flex;
    justify-content: space-evenly;  /* perfectly even spacing everywhere */
}
```

---

## Alignment on the Cross Axis: `align-items`

Controls how items are positioned along the cross axis:

```css
.container {
    display: flex;
    align-items: stretch;       /* items stretch to fill container (default) */
}

.container {
    display: flex;
    align-items: flex-start;    /* items at the start of cross axis */
}

.container {
    display: flex;
    align-items: flex-end;      /* items at the end of cross axis */
}

.container {
    display: flex;
    align-items: center;        /* items centred on cross axis */
}

.container {
    display: flex;
    align-items: baseline;      /* items aligned by their text baselines */
}
```

---

## Wrapping

By default, flex items stay on a single line. `flex-wrap` allows them to wrap onto multiple lines:

```css
.container {
    display: flex;
    flex-wrap: wrap;            /* items wrap to the next line */
}
```

Combined with `flex-direction`, this creates responsive grids where items flow naturally onto new rows.

---

## Gaps Between Items

The `gap` property adds space between flex items without needing margins:

```css
.container {
    display: flex;
    gap: 20px;                   /* gap between all items */
}

.container {
    display: flex;
    gap: 20px 10px;              /* row-gap  column-gap */
}
```

---

## Flex Item Properties

Properties applied to the items themselves:

### `flex`

The `flex` shorthand controls how items grow and shrink:

```css
.item {
    flex: 1;    /* each item takes equal space */
}

.item-wide {
    flex: 2;    /* takes twice the space of flex: 1 items */
}

.item-fixed {
    flex: 0 0 200px;    /* do not grow, do not shrink, stay at 200px */
}
```

### `align-self`

Overrides `align-items` for a single item:

```css
.item {
    align-self: center;     /* centre just this item vertically */
}
```

### `order`

Changes the visual order of items without altering the HTML:

```css
.item-first {
    order: -1;      /* appears before items with the default order of 0 */
}

.item-last {
    order: 1;       /* appears after items with the default order of 0 */
}
```

---

## Common Patterns

### Centring Content (Both Axes)

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;      /* full viewport height */
}
```

### Navigation Bar

```css
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
}
```

### Card Grid

```css
.grid {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.card {
    flex: 1 1 300px;    /* grow, shrink, basis of 300px */
}
```

---

## Summary

- Enable Flexbox with `display: flex` on the container
- `flex-direction` controls the main axis (row or column)
- `justify-content` aligns items along the main axis
- `align-items` aligns items along the cross axis
- `flex-wrap: wrap` allows items to flow onto new lines
- `gap` adds consistent spacing without margin hacks
- `flex` on items controls growing, shrinking, and base size
- Use `justify-content: center` + `align-items: center` to centre an item perfectly
