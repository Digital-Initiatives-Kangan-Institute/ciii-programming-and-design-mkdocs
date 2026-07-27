# Text Elements

HTML provides a range of elements for displaying and formatting text. These elements create semantic meaning — they tell the browser and assistive technologies what role each piece of text plays.

---

## Headings

Headings create a document outline and range from `<h1>` (most important) to `<h6>` (least important):

```html
<h1>Page Title</h1>
<h2>Major Section</h2>
<h3>Subsection</h3>
<h4>Topic</h4>
<h5>Detail</h5>
<h6>Minor Detail</h6>
```

Best practices:

- Use only one `<h1>` per page — it represents the main topic
- Do not skip heading levels (e.g. jumping from `<h2>` to `<h4>`)
- Headings help screen reader users navigate your page

---

## Paragraphs

The `<p>` element creates a block of text with spacing above and below:

```html
<p>This is a paragraph of text. Paragraphs are separated by default margins.</p>
<p>This is another paragraph. Each paragraph starts on a new line.</p>
```

Browsers automatically add space between paragraphs. You should use `<p>` for any standalone block of text — do not use `<br>` to simulate paragraph spacing.

---

## Line Breaks

The `<br>` element inserts a single line break without starting a new paragraph:

```html
<p>123 Main Street<br>Melbourne VIC 3000</p>
```

Use `<br>` sparingly — only when the line break is part of the content (e.g. addresses, poetry). For spacing between blocks, use CSS margins instead.

---

## Text Formatting

### Bold and Strong

```html
<p>This is <strong>important</strong> information.</p>
<p>This is <b>bold</b> text.</p>
```

- `<strong>` conveys **semantic importance** — screen readers may emphasise it
- `<b>` is purely visual and carries no extra meaning

### Italic and Emphasised

```html
<p>I <em>really</em> mean it.</p>
<p>The scientific name is <i>Homo sapiens</i>.</p>
```

- `<em>` conveys **stress emphasis** — screen readers may change tone
- `<i>` is for text offset from normal prose (e.g. technical terms, foreign phrases)

---

## Horizontal Rules

The `<hr>` element creates a thematic break between sections:

```html
<p>End of section one.</p>
<hr>
<p>Start of section two.</p>
```

The `<hr>` represents a shift in topic — do not use it purely for decoration.

---

## Other Text Elements

| Element | Purpose | Example |
|---|---|---|
| `<small>` | Fine print, disclaimers | `<small>Terms apply.</small>` |
| `<sub>` | Subscript | `H<sub>2</sub>O` |
| `<sup>` | Superscript | `x<sup>2</sup>` |
| `<code>` | Inline code | `Use the <code>print()</code> function` |
| `<pre>` | Preformatted text | Preserves whitespace and line breaks |
| `<blockquote>` | Quoted content | Indents and cites a block of text |

---

## Summary

- Headings (`<h1>`–`<h6>`) create a document outline — use them in order
- `<p>` wraps blocks of text; `<br>` inserts a line break mid-content
- `<strong>` and `<em>` add semantic meaning beyond just bold/italic
- `<hr>` marks a thematic break between sections
- Prefer semantic elements over visual-only ones for accessibility
