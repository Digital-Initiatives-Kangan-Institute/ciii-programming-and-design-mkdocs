# Profile Page

Build a personal profile page using the HTML elements you have learned. This page should demonstrate your understanding of HTML structure, elements, and forms.

---

## Page Structure

!!! abstract "Instructions"
    Create an HTML page called `profile.html` that includes the following sections. Use semantic HTML where possible.

    - A header with your name as the main heading and a tagline
    - A navigation bar with links to: About, Skills, Contact (these can link to sections on the same page using `#id`)
    - An About section with a paragraph about yourself and a profile image (use a placeholder URL)
    - A Skills section with a table listing your skills and experience level
    - A Contact section with a form (name, email, message)

    Use proper HTML5 document structure (`<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`).

??? code "Starter Structure"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Your Name - Profile</title>
    </head>
    <body>
        <header>
            <h1>Your Name</h1>
            <p>A short tagline about yourself</p>
        </header>

        <nav>
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#contact">Contact</a>
        </nav>

        <main>
            <section id="about">
                <h2>About Me</h2>
                <!-- Your content here -->
            </section>

            <section id="skills">
                <h2>Skills</h2>
                <!-- Your table here -->
            </section>

            <section id="contact">
                <h2>Contact</h2>
                <!-- Your form here -->
            </section>
        </main>

        <footer>
            <p>Your Name - 2026</p>
        </footer>
    </body>
    </html>
    ```

---

## Task 1: Header and Navigation

!!! abstract "Instructions"
    Add your name in an `<h1>` and a short tagline in a `<p>` inside the `<header>`. The navigation should use `<a>` tags with `href` attributes pointing to `#about`, `#skills`, and `#contact`.

??? hint "Hint - Click to expand"
    Make sure the `id` attributes on your sections match the `href` values. For example, if the link is `href="#about"`, the section needs `id="about"`.

---

## Task 2: About Section

!!! abstract "Instructions"
    Inside the About section:

    - Write a short paragraph (2-3 sentences) about yourself using `<p>`
    - Use `<b>` or `<strong>` to bold a key phrase
    - Use `<i>` or `<em>` for emphasis on a word
    - Add an image using `<img>` with a placeholder URL: `https://via.placeholder.com/150`
    - Include an `alt` attribute describing the image

??? hint "Hint - Click to expand"
    To bold text, wrap it in `<strong>` or `<b>` tags. To italicise text, use `<em>` or `<i>` tags. Both go inside your `<p>` element.

    For images: `<img src="URL" alt="description">`. The `src` attribute holds the image URL and `alt` provides a text description if the image cannot load.

    Try using `https://via.placeholder.com/150` as your placeholder image URL.

---

## Task 3: Skills Table

!!! abstract "Instructions"
    Create a table listing at least 4 skills you have (or are learning). Include columns for the skill name, category, and proficiency level (Beginner, Intermediate, Advanced).

??? code "Table Structure"
    ```html
    <table>
        <thead>
            <tr>
                <th>Skill</th>
                <th>Category</th>
                <th>Level</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>HTML</td>
                <td>Web Development</td>
                <td>Beginner</td>
            </tr>
            <!-- Add more rows here -->
        </tbody>
    </table>
    ```

---

## Task 4: Contact Form

!!! abstract "Instructions"
    Create a form with the following fields. Each field should have a `<label>` that is linked to the input using `for` and `id`.

    - Name (text input, required)
    - Email (email input, required)
    - Subject (text input)
    - Message (textarea, 4 rows)
    - Submit button

    All inputs should be inside `<div>` containers for structure.

??? code "Form Structure"
    ```html
    <form action="#" method="POST">
        <div>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
        </div>

        <!-- Add your email field here (type="email", required) -->

        <!-- Add your subject field here (type="text") -->

        <!-- Add your message textarea here (rows="4") -->

        <button type="submit">Send Message</button>
    </form>
    ```

---

## Task 5: Validate

!!! abstract "Instructions"
    Open your `profile.html` in VS Code with Live Preview. Check that:

    - All sections are visible and the navigation links work (jump to the right section)
    - The image displays correctly
    - The table has proper rows and columns
    - The form fields are clickable and the submit button works (the page may reload — that's fine for now)
    - The page has no broken HTML (use the W3C Validator if unsure)

---

## Requirements

- Proper HTML5 document structure
- Semantic elements used where appropriate (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)
- At least 4 different element types (headings, paragraphs, links, images, tables, forms)
- A table with header and body rows
- A form with at least 3 input types
- Labels linked to inputs using `for` and `id`
- Image has an `alt` attribute
