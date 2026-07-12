# Bootstrap

Bootstrap is a popular CSS framework that provides pre-built components and a responsive grid system. It lets you build clean, mobile-friendly pages quickly without writing CSS from scratch.

---

## What is Bootstrap?

Bootstrap is a collection of CSS classes and optional JavaScript components. It handles layout, typography, buttons, forms, navigation, and more.

---

## Adding Bootstrap to a Page

Add the Bootstrap CSS and JavaScript in the `<head>`:

```html
<head>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</head>
```

!!! note
    Always check the [Bootstrap documentation](https://getbootstrap.com) for the latest CDN links.

---

## The Grid System

Bootstrap uses a 12-column grid. Rows and columns let you create layouts:

```html
<div class="container">
    <div class="row">
        <div class="col-6">Left half</div>
        <div class="col-6">Right half</div>
    </div>
</div>
```

- `.container` centres content and adds padding
- `.row` creates a horizontal group of columns
- `.col-6` takes up 6 out of 12 columns (half width)

---

## Common Components

### Buttons

```html
<button class="btn btn-primary">Primary</button>
<button class="btn btn-secondary">Secondary</button>
<button class="btn btn-success">Success</button>
```

### Navigation Bar

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">My Cafe</a>
        <div>
            <a class="nav-link" href="index.html">Home</a>
            <a class="nav-link" href="menu.html">Menu</a>
        </div>
    </div>
</nav>
```

### Cards

```html
<div class="card" style="width: 18rem;">
    <img src="coffee.jpg" class="card-img-top" alt="Coffee">
    <div class="card-body">
        <h5 class="card-title">Latte</h5>
        <p class="card-text">Smooth espresso with steamed milk.</p>
    </div>
</div>
```

---

## Responsive Design

Bootstrap makes pages work on mobile, tablet, and desktop:

```html
<div class="col-12 col-md-6 col-lg-4">
    Full width on mobile, half on tablet, one-third on desktop.
</div>
```

---

## Using Bootstrap with Custom CSS

You can use Bootstrap for structure and components while adding your own CSS for custom styling. Link your stylesheet **after** Bootstrap:

```html
<head>
    <link href="bootstrap.min.css" rel="stylesheet">
    <link href="styles.css" rel="stylesheet">
</head>
```

---

## Summary

- Bootstrap provides ready-made components and a responsive grid
- Link the CSS and JS from a CDN to get started
- Use `.container`, `.row`, and `.col-*` for layout
- Combine Bootstrap components with your own CSS for custom designs
