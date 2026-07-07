# Cafe Website

Build a two-page cafe website from scratch using HTML and CSS.

---

## Page 1: Home

!!! abstract "Instructions"
    Create a `index.html` page for a cafe called "The Daily Grind". The page should include:

    - A header with the cafe name and a navigation bar linking to Home and Menu
    - A hero section with a welcome message and a background colour
    - A brief "About Us" paragraph
    - Opening hours displayed in a list

    Use an external stylesheet (`style.css`) for all styling.

??? code "Starter Structure"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>The Daily Grind</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <header>
            <h1>The Daily Grind</h1>
            <nav>
                <a href="index.html">Home</a>
                <a href="menu.html">Menu</a>
            </nav>
        </header>

        <section class="hero">
            <!-- Your hero content here -->
        </section>

        <section class="about">
            <!-- Your about content here -->
        </section>

        <section class="hours">
            <!-- Your hours content here -->
        </section>

        <footer>
            <p>The Daily Grind - Your local cafe</p>
        </footer>
    </body>
    </html>
    ```

??? hint "Hint - Hero Section"
    Use a `<div>` with a background colour for the hero section. Add a heading and a paragraph inside it. Use padding to give it height.

??? tip "Hint - Navigation Styling"
    Style your navigation links with:

    ```css
    nav a {
        text-decoration: none;
        margin: 0 10px;
        color: #333;
    }
    ```

---

## Page 2: Menu

!!! abstract "Instructions"
    Create a `menu.html` page that displays the cafe's menu. Include:

    - The same header and navigation bar as the home page
    - Menu items organised into categories (Coffee, Tea, Food)
    - Each item should have a name, description, and price
    - Use the same `style.css` stylesheet from the home page

??? code "Starter Structure"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Menu - The Daily Grind</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <header>
            <h1>The Daily Grind</h1>
            <nav>
                <a href="index.html">Home</a>
                <a href="menu.html">Menu</a>
            </nav>
        </header>

        <main>
            <h2>Our Menu</h2>

            <section class="menu-category">
                <h3>Coffee</h3>
                <!-- Add coffee items here -->
            </section>

            <section class="menu-category">
                <h3>Tea</h3>
                <!-- Add tea items here -->
            </section>

            <section class="menu-category">
                <h3>Food</h3>
                <!-- Add food items here -->
            </section>
        </main>

        <footer>
            <p>The Daily Grind - Your local cafe</p>
        </footer>
    </body>
    </html>
    ```

??? hint "Hint - Menu Item Layout"
    Use a `<div>` with class `menu-item` for each item:

    ```html
    <div class="menu-item">
        <h4>Espresso</h4>
        <p>A rich and bold single-origin shot</p>
        <span class="price">$4.00</span>
    </div>
    ```

---

## Requirements Checklist

- Two HTML pages that link to each other
- One external `style.css` file shared by both pages
- Use at least 3 different CSS selectors (element, class, id)
- Include headings, paragraphs, lists, and links
- Use a consistent colour scheme throughout
- Test in VS Code with Live Preview
