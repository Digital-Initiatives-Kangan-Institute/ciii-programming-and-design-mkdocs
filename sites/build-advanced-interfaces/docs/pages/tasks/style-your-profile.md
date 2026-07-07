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
    - To style the header, use an **element selector** (`header { ... }`).
    - Set `background-color`, `color` (for text), `padding`, and `text-align: center`.
    - Add `class="tagline"` to your tagline `<p>` in the HTML.
    - Use a **class selector** (`.tagline { ... }`) to make the tagline italic (`font-style: italic`) and slightly smaller (`font-size`).

    The instructions give you the hex colour `#3f51b5` — use it for the background.

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
    - Make the `<nav>` element a flex container with `display: flex` and use `justify-content: center` to centre the links.
    - Set a dark background colour on `nav`.
    - Target the links with `nav a` and remove the default underline using `text-decoration: none`. Make the text white and add padding.
    - For the hover effect, use `nav a:hover` and change the `background-color` to a slightly lighter shade.
    - Use `display: inline-block` on the links so padding works correctly.

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
    - Limit the width of `<main>` with `max-width` and centre it using `margin`. Use a top margin of `2rem` and `auto` for the left/right values.
    - For each `<section>`, set a white `background`, add `padding` inside, space them apart with `margin-bottom`, and soften the corners with `border-radius`.
    - Add horizontal padding to `<main>` so the content doesn't touch the edges on small screens.

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
    - Make the table full-width with `width: 100%`.
    - Use `border-collapse: collapse` to merge adjacent cell borders into one.
    - Apply `border`, `padding`, and `text-align: left` to both `th` and `td` elements.
    - Give `th` a background colour (e.g. the indigo `#3f51b5`) with white text.
    - For alternating row colours, use the pseudo-class `:nth-child(even)` on `tr` and set a light background colour.

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
    - Give each form `<div>` some `margin-bottom` for spacing.
    - Make labels bold with `font-weight: bold` and use `display: block` so they sit above the input. Add a small `margin-bottom`.
    - Make inputs and textareas full-width (`width: 100%`), add `padding` and a light `border`. Use `border-radius` for rounded corners and `box-sizing: border-box` so padding doesn't break the width. Set `font-family: inherit` so they match the page.
    - For the focus effect, use the `:focus` pseudo-class. Change the `border-color` to your theme colour and remove the default `outline`. Consider adding a subtle `box-shadow` for a glow effect.
    - Style the button: remove the default `border`, set `background-color` and `color`, add `padding`, `border-radius`, and `cursor: pointer`.
    - Use `button:hover` to darken the background colour slightly.

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
