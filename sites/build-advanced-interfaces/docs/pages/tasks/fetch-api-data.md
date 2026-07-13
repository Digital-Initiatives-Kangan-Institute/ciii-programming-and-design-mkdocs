# Cafe Recipes Page

## Create the Recipes Page

!!! abstract "Instructions"
    The cafe wants to share their recipes online so customers can make them at home. Create a new page for the cafe website that will display recipes fetched from an API.

    Your page must include:

    - A heading introducing the recipes
    - A container element for recipe cards (use a `<div>` with an `id`)
    - A link back to the cafe home page
    - Consistent styling with your existing cafe site

    Link the recipes page from your other cafe pages in the navigation.

    Push your work to GitHub. See the [Version Control](/version-control) site if you need help with staging, committing, and pushing.

??? hint "Hint - Click to expand"
    Create a new file such as `recipes.html`. The container for cards should be a `<div>` with an `id` attribute so you can target it with JavaScript later. Add a link to this page from your other cafe pages (Home, Menu, Reviews, Login). Style the page heading to match your existing cafe theme.

---

## Add JavaScript to Fetch and Display Recipes

!!! abstract "Instructions"
    Use the DummyJSON Recipes API to fetch and display recipes. Each recipe should appear as a **card** inside a vertical flex list — do not hardcode any recipe data.

    Fetch recipes from this endpoint:

    ```
    https://dummyjson.com/recipes
    ```

    Each recipe card must show only the following information:

    - **Name** — the recipe title
    - **Image** — the recipe photo
    - **Cuisine** — type of cuisine
    - **Difficulty** — cooking difficulty
    - **Prep and cook time** — preparation and cooking time in minutes
    - **Rating** — star rating
    - **Calories per serving** — calorie count
    - **Servings** — how many people it serves

    Display all 30 recipes from the response. Use CSS Flexbox so the cards form a vertical list (single column). Add spacing and borders to make each card readable.

    Push your work to GitHub.

??? hint "Hint - Click to expand"
    Use `fetch()` to call the URL, then `response.json()` to parse the data. The returned object has a `recipes` array — loop through it and create a card for each one. For each card, create a `<div>`, populate its `innerHTML` with the required fields, and append it to your container. The image URL is in the `image` field. For prep and cook time, combine `prepTimeMinutes` and `cookTimeMinutes` into one display. Use CSS `display: flex; flex-direction: column; gap: 16px;` on the container to stack cards vertically. Do not show fields like `instructions`, `ingredients`, `tags`, `userId`, `reviewCount`, or `mealType` — only the ones listed above.
