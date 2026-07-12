# HTML Fundamentals

HTML (HyperText Markup Language) is the foundation of every web page. It gives structure and meaning to content by using elements and tags.

---

## What is HTML?

HTML is a markup language that tells the browser how to structure and display content. Every web page you visit is built with HTML.

- HTML documents are plain text files saved with a `.html` extension
- Browsers read HTML and render it as a visual page
- HTML works together with CSS (for styling) and JavaScript (for interactivity)

---

## Basic HTML Document Structure

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
- `<title>` sets the text shown in the browser tab
- `<body>` contains all visible page content

---

## Elements, Tags, and Content

HTML elements are made up of a start tag, content, and an end tag:

```html
<p>This is a paragraph.</p>
```

- `<p>` is the **start tag**
- `This is a paragraph.` is the **content**
- `</p>` is the **end tag**

Some elements are self-closing and don't need an end tag:

```html
<br>
<hr>
<img src="photo.jpg" alt="A photo">
```

---

## Common Text Elements

### Headings

```html
<h1>Main Heading</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>
```

### Paragraphs

```html
<p>This is a paragraph of text.</p>
```

### Text Formatting

```html
<p>This is <strong>bold text</strong> and <em>italic text</em>.</p>
```

- `<strong>` makes text bold
- `<em>` makes text italic (emphasised)

### Horizontal Rules

```html
<p>Content above the line.</p>
<hr>
<p>Content below the line.</p>
```

---

## Nested Elements

Elements can be placed inside other elements. The element that contains another is called the **parent**, and the contained element is the **child**.

```html
<div>
    <h2>Welcome</h2>
    <p>This paragraph is nested inside the div.</p>
</div>
```

Proper nesting means closing tags in the reverse order they were opened.

***

## Divs and Spans

Divs and spans are general-purpose containers:

- `<div>` is a **block-level** container — it takes up the full width available and starts on a new line
- `<span>` is an **inline** container — it only takes up as much width as needed and stays within the flow of text

```html
<div>
    <p>This is inside a div.</p>
    <p>A <span>span</span> sits inline within text.</p>
</div>
```

---

## Navigation and Links

Links connect pages together using the `<a>` (anchor) element:

```html
<a href="menu.html">View our menu</a>
<a href="https://www.w3schools.com">W3Schools</a>
```

The `href` attribute specifies the destination — either a relative path to another page in your project or a full URL.

---

## Images

```html
<img src="cafe-photo.jpg" alt="Our cozy cafe interior">
```

- `src` specifies the image file location
- `alt` provides alternative text for accessibility and when the image fails to load

---

## Summary

- HTML uses elements made of start tags, content, and end tags
- Every page follows a standard structure with `<head>` and `<body>`
- Headings (`<h1>` to `<h6>`) create a document outline
- `<div>` and `<span>` are containers for grouping content
- Links (`<a>`) connect pages and images (`<img>`) add visual content
- HTML provides **structure** — CSS handles appearance
