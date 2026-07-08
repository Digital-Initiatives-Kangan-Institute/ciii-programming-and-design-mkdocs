# Cafe Website

## Build the Home Page

!!! abstract "Instructions"
    Create the Home page for a cafe website.

    Your page must include:

    - A heading with the cafe name
    - A welcome paragraph introducing the cafe
    - At least one image
    - A navigation section (links won't work yet — you will add the second page next)

    Link an external CSS file and use at least two selector types (element and class).

    Push your site to GitHub. See the [Version Control](/version-control) site if you need help with staging, committing, and pushing.

??? hint "Hint - Click to expand"
    Start with the standard HTML document structure. Use `<h1>` for the cafe name and `<p>` for the welcome text. For the image, use `<img>` with `src` pointing to a local image file. Your CSS should style the heading and a class-based selector — think about what you want to highlight on the page.

---

## Add a Menu Page

!!! abstract "Instructions"
    Create a second page for the cafe menu. Then link both pages together.

    Your menu page must include:

    - At least **four items**, each with a name, description, and price
    - At least one image
    - Navigation links between the Home and Menu pages on both pages

    Add a third selector type (ID) to your CSS so you now use element, class, and ID selectors.

    Push your site to GitHub. See the [Version Control](/version-control) site if you need help with staging, committing, and pushing.

??? hint "Hint - Click to expand"
    Create a new HTML file for the menu. Use anchor tags with `href` pointing to the other file (e.g. `<a href="index.html">Home</a>`) on both pages. For each menu item, think about how to structure the name, description, and price — a list or a series of sections. Your ID selector should be used on a unique element like a banner or footer.

---

## Add a Review Page

!!! abstract "Instructions"
    Create a third page for customer reviews. This page should have a form for submitting a review — the form does not need to work yet, just build the HTML and CSS structure.

    Your review page must include:

    - A **text input** for the reviewer's name with a label
    - A **number input** for a rating out of 5 with a label
    - A **textarea** for the review comment with a label
    - A **submit button**
    - A section below the form where reviews would appear
    - Navigation linking to all three pages (Home, Menu, Reviews)

    Push your updated site to GitHub. See the [Version Control](/version-control) site if you need help with staging, committing, and pushing.

??? hint "Hint - Click to expand"
    Every input needs a `<label>` with a `for` attribute matching the input's `id`. Wrap the form in a `<form>` element. The section below the form is where submitted reviews will eventually be displayed — for now, just add a heading like "What our customers say". Do not worry about making the form functional yet.
