# Document Structure

Every HTML document follows a standard skeleton that tells the browser what it is and how to interpret it.

---

## The DOCTYPE Declaration

The very first line of every HTML document is the doctype:

```html
<!DOCTYPE html>
```

This tells the browser to render the page in **standards mode** using the HTML5 specification. Without it, browsers fall back to quirks mode, which can cause inconsistent rendering.

---

## The `<html>` Element

The `<html>` element is the root of the document. Everything else goes inside it:

```html
<html lang="en">
    <!-- head and body go here -->
</html>
```

The `lang` attribute tells browsers and assistive technologies what language the content is written in. This helps with screen readers, search engines, and translation tools.

---

## The `<head>` Section

The `<head>` contains metadata — information *about* the page, not visible content:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="A page about our cafe">
    <title>Cafe Homepage</title>
    <link rel="stylesheet" href="styles.css">
</head>
```

### Key `<head>` Elements

| Element | Purpose |
|---|---|
| `<meta charset="UTF-8">` | Declares character encoding so special characters display correctly |
| `<meta name="viewport">` | Controls how the page scales on mobile devices |
| `<meta name="description">` | Provides a summary for search engine results |
| `<title>` | Sets the text shown in the browser tab |
| `<link>` | Connects external resources like CSS stylesheets |

### The Viewport Meta Tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Without this tag, mobile browsers render pages at a desktop width and then shrink them down, making text tiny. This tag tells the browser to match the page width to the device width, which is essential for responsive design.

---

## The `<body>` Section

The `<body>` contains everything the user sees on the page — text, images, buttons, forms, navigation, and embedded content:

```html
<body>
    <header>
        <h1>Welcome to Our Cafe</h1>
    </header>
    <main>
        <p>We serve the best coffee in town.</p>
    </main>
    <footer>
        <p>Open 7 days a week</p>
    </footer>
</body>
```

---

## Comments

Comments are notes for developers that the browser ignores:

```html
<!-- This is a comment. It does not appear on the page. -->

<!-- TODO: Add a navigation menu here -->
```

Comments are useful for documenting your code, leaving reminders, or temporarily disabling parts of a page during development.

---

## Summary

- `<!DOCTYPE html>` must be the first line of every HTML page
- `<html lang="en">` wraps the entire document and declares the language
- `<head>` contains metadata — charset, viewport, title, and links to stylesheets
- `<body>` contains all visible content
- The viewport meta tag is essential for mobile-friendly pages
- Comments start with `<!--` and end with `-->`
