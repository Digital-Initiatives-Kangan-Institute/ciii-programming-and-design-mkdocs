# Colours and Typography

Colour and typography are two of the most impactful aspects of web design. Together they set the tone, create visual hierarchy, and affect readability.

---

## Colour Values

CSS supports several ways to define colours:

### Named Colours

```css
p { color: red; }
div { background-color: navy; }
```

There are 140 named colours (e.g. `tomato`, `steelblue`, `seagreen`). They are easy to read but offer limited choice.

### Hexadecimal (Hex)

```css
p { color: #333333; }
div { background-color: #f0f0f0; }
```

Hex codes use `#RRGGBB` (red, green, blue) with values from `00` to `FF`. Shorthand is available when both digits of each pair are the same:

```css
#ff0000 → #f00  (red)
#333333 → #333  (dark grey)
#ffffff → #fff  (white)
```

### RGB and RGBA

```css
p { color: rgb(51, 51, 51); }
div { background-color: rgba(0, 0, 0, 0.5); }
```

The fourth value in `rgba` is **alpha** — opacity from `0` (fully transparent) to `1` (fully opaque).

### HSL and HSLA

```css
p { color: hsl(0, 100%, 50%); }           /* red */
div { background-color: hsla(240, 100%, 50%, 0.3); }
```

HSL stands for Hue (0–360 degrees on the colour wheel), Saturation (0–100%), and Lightness (0–100%).

---

## Text Colour and Background Colour

```css
body {
    color: #333333;                /* text colour */
    background-color: #ffffff;     /* page background */
}

.highlight {
    color: #ffffff;
    background-color: #3f51b5;
}
```

Ensure sufficient **contrast** between text and background colours. Low contrast makes text difficult to read, especially for users with visual impairments.

---

## Typography Properties

### `font-family`

Specifies the typeface. List fallbacks in case the preferred font is not available:

```css
body {
    font-family: "Helvetica Neue", Arial, sans-serif;
}
```

- Quote font names that contain spaces
- End the list with a generic family: `serif`, `sans-serif`, `monospace`, `cursive`, or `fantasy`

### `font-size`

Controls text size:

```css
p { font-size: 16px; }
h1 { font-size: 2rem; }
h2 { font-size: 1.5em; }
```

Common units:

| Unit | Description |
|---|---|
| `px` | Pixels — fixed size |
| `em` | Relative to the parent element's font size |
| `rem` | Relative to the root (`<html>`) element's font size |
| `%` | Percentage of the parent's font size |

`rem` is often preferred because it scales consistently regardless of nesting depth. The default browser font size is 16px, so `1rem = 16px` unless changed.

### `font-weight`

Controls boldness:

```css
p { font-weight: normal; }     /* 400 */
strong { font-weight: bold; }   /* 700 */
h1 { font-weight: 800; }
```

Values range from `100` (thin) to `900` (black). Not all fonts support all weights.

### `font-style`

```css
em { font-style: italic; }
.citation { font-style: oblique; }
```

### `line-height`

Controls the vertical space between lines of text:

```css
p {
    line-height: 1.6;
}
```

Unitless values (like `1.6`) multiply the element's font size. A `line-height` of `1.5`–`1.75` generally improves readability for body text.

### `text-align`

Horizontal alignment:

```css
.center { text-align: center; }
.right { text-align: right; }
p { text-align: justify; }     /* stretches lines to fill width */
```

### `text-decoration`

```css
a { text-decoration: none; }        /* remove underline */
.old-price { text-decoration: line-through; }
.underline { text-decoration: underline; }
```

### `letter-spacing` and `word-spacing`

```css
h1 { letter-spacing: 2px; }        /* space between letters */
p { word-spacing: 4px; }           /* space between words */
```

---

## Web Fonts

Google Fonts provides free fonts you can include in your page:

```html
<head>
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
</head>
```

Then use it in CSS:

```css
body {
    font-family: "Roboto", sans-serif;
}
```

---

## Summary

- Colours can be defined with named values, hex (`#333`), RGB, RGBA, HSL, or HSLA
- `color` sets text colour; `background-color` sets the background
- Ensure sufficient contrast between text and background
- `font-family` lists preferred fonts with fallbacks; end with a generic family
- `rem` is preferred over `px` for font sizes because it respects user preferences
- `line-height: 1.5`–`1.75` improves body text readability
- Use Google Fonts or similar services to go beyond system fonts
