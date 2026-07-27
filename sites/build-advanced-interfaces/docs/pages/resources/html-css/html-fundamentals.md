# HTML Fundamentals

HTML (HyperText Markup Language) is the foundation of every web page. It gives structure and meaning to content by using elements and tags.

---

## What is HTML?

HTML is a markup language that tells the browser how to structure and display content. Every web page you visit is built with HTML.

- HTML documents are plain text files saved with a `.html` extension
- Browsers read HTML and render it as a visual page
- HTML works together with CSS (for styling) and JavaScript (for interactivity)

---

## Elements, Tags, and Content

HTML elements are made up of a start tag, content, and an end tag:

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **start tag**
- `This is a paragraph.` is the **content**
- `</p>` is the **end tag**

Some elements are self-closing and do not need an end tag:

```html
<br>
<hr>
<img src="photo.jpg" alt="A photo">
```

---

## Basic Document Structure

Every HTML page follows a standard structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

- `<!DOCTYPE html>` tells the browser this is an HTML5 document
- `<html>` is the root element that wraps everything
- `<head>` contains metadata (information about the page)
- `<body>` contains all visible page content

---

## Common Elements at a Glance

| Element | Purpose |
|---|---|
| `<h1>`–`<h6>` | Headings (`<h1>` is the most important) |
| `<p>` | Paragraph of text |
| `<a>` | Link to another page or website |
| `<img>` | Display an image |
| `<ul>`, `<ol>`, `<li>` | Unordered and ordered lists |
| `<div>` | Block-level container for grouping |
| `<span>` | Inline container for text |

---

## Summary

- HTML uses elements made of start tags, content, and end tags
- Every page follows a standard structure with `<head>` and `<body>`
- HTML provides **structure** — CSS handles appearance, JavaScript handles behaviour
- See the pages below for detailed coverage of each topic
