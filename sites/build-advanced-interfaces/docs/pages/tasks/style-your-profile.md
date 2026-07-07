# Style Your Profile

Take the profile page you built in the previous task and style it with CSS. This task focuses on applying selectors, the box model, and flexbox layout.

---

## Task 1: Create and Link Your Stylesheet

!!! abstract "Instructions"
    Create a file called `style.css` in the same folder as your `profile.html`. Link it in the `<head>` of your HTML page using an external stylesheet link.

??? code "In Your HTML"
    ```html
    <head>
        <link rel="stylesheet" href="style.css">
    </head>
    ```

---

## Task 2: Style the Page Body

!!! abstract "Instructions"
    Apply base styles to the page:

    - Set the body font to Arial (or similar sans-serif)
    - Set a background colour of your choice (light colours work best)
    - Remove default margin and padding from the body
    - Set a default text colour (e.g. `#333`)

??? code "Starting Styles"
    ```css
    body {
        font-family: Arial, Helvetica, sans-serif;
        background-color: #f5f5f5;
        color: #333;
        margin: 0;
        padding: 0;
    }
    ```

---

## Task 3: Style the Header

!!! abstract "Instructions"
    Style the header section:

    - Give it a background colour (e.g. `#3f51b5`)
    - Make the header text white
    - Add padding (e.g. `2rem`)
    - Centre-align the text
    - Make the tagline italic and slightly smaller

Use an **element selector** for the `<header>`, and a **class** for the tagline.

??? hint "Hint - Click to expand"
    ```html
    <!-- In your HTML -->
    <header>
        <h1>Your Name</h1>
        <p class="tagline">A short tagline about yourself</p>
    </header>
    ```

    ```css
    header {
        background-color: #3f51b5;
        color: white;
        padding: 2rem;
        text-align: center;
    }

    .tagline {
        font-style: italic;
        font-size: 1.1rem;
    }
    ```

---

## Task 4: Style the Navigation

!!! abstract "Instructions"
    Make the navigation bar look like a proper menu:

    - Give it a dark background colour
    - Remove link underlines with `text-decoration: none`
    - Make link text white
    - Add padding around the links (e.g. `1rem`)
    - Use flexbox so the links sit in a row (hint: use `nav` as the flex container)
    - Add a hover effect that changes the background colour of each link

??? hint "Hint - Click to expand"
    ```css
    nav {
        background-color: #303f9f;
        display: flex;
        justify-content: center;
    }

    nav a {
        color: white;
        text-decoration: none;
        padding: 1rem 1.5rem;
        display: inline-block;
    }

    nav a:hover {
        background-color: #5c6bc0;
    }
    ```

---

## Task 5: Style the Main Content

!!! abstract "Instructions"
    Apply styles to the main content area:

    - Limit the maximum width of `<main>` to 800px
    - Centre the main element using `margin: 0 auto`
    - Add padding
    - Add a white background to each `<section>` (use a `section` element selector or a class)
    - Give each section margin below it, padding inside, and rounded corners with `border-radius`

??? hint "Hint - Click to expand"
    ```css
    main {
        max-width: 800px;
        margin: 2rem auto;
        padding: 0 1rem;
    }

    section {
        background: white;
        margin-bottom: 1.5rem;
        padding: 1.5rem;
        border-radius: 8px;
    }
    ```

---

## Task 6: Style the Table

!!! abstract "Instructions"
    Make the skills table look professional:

    - Add a border to the table, header cells, and data cells
    - Collapse borders with `border-collapse: collapse`
    - Give header cells a background colour
    - Add padding to all cells
    - Make the table full-width
    - Add alternating row colours for readability

??? hint "Hint - Click to expand"
    ```css
    table {
        width: 100%;
        border-collapse: collapse;
    }

    th, td {
        border: 1px solid #ddd;
        padding: 0.75rem;
        text-align: left;
    }

    th {
        background-color: #3f51b5;
        color: white;
    }

    tr:nth-child(even) {
        background-color: #f9f9f9;
    }
    ```

---

## Task 7: Style the Form

!!! abstract "Instructions"
    Make the contact form look clean and modern:

    - Each form `<div>` should have space below it
    - Labels should be bold and have space below them
    - Inputs and textarea should be full-width, with padding, a border, and rounded corners
    - Add a focus effect — when an input is focused, change its border colour
    - Style the submit button with a background colour, white text, no border, padding, rounded corners, and a cursor pointer
    - Add a hover effect to the button

??? hint "Hint - Click to expand"
    ```css
    form div {
        margin-bottom: 1rem;
    }

    label {
        display: block;
        font-weight: bold;
        margin-bottom: 0.25rem;
    }

    input, textarea {
        width: 100%;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
        font-family: inherit;
        font-size: 0.95rem;
    }

    input:focus, textarea:focus {
        outline: none;
        border-color: #3f51b5;
        box-shadow: 0 0 0 2px rgba(63, 81, 181, 0.2);
    }

    button {
        background-color: #3f51b5;
        color: white;
        border: none;
        padding: 0.75rem 2rem;
        border-radius: 4px;
        cursor: pointer;
        font-size: 1rem;
    }

    button:hover {
        background-color: #303f9f;
    }
    ```

---

## Task 8: Footer

!!! abstract "Instructions"
    Style the footer:

    - Give it a dark background matching the nav
    - White text, centred
    - Padding
    - Slightly smaller font size

---

## Requirements

- Use at least 3 CSS **class selectors** (`.`)
- Use at least 1 CSS **element selector**
- Use at least 1 CSS **ID selector** (`#`)
- Use the **box model** properties: `padding`, `margin`, `border`
- Use **flexbox** for at least one layout (the nav bar)
- Use **external CSS** (the `style.css` file)
- Include at least one **hover** effect
