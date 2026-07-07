# Interactive Gallery

Practice events and DOM manipulation by building an interactive image gallery. Users will be able to add new images, view them in a lightbox, and remove them.

---

## Setup

!!! abstract "Instructions"
    Create `gallery.html`, `gallery.css`, and `gallery.js`. Set up the basic HTML structure below and link everything together.

??? code "Starter HTML"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Image Gallery</title>
        <link rel="stylesheet" href="gallery.css">
    </head>
    <body>
        <h1>Image Gallery</h1>

        <div id="gallery-controls">
            <input type="text" id="imageUrl" placeholder="Paste an image URL...">
            <input type="text" id="imageTitle" placeholder="Image title...">
            <button id="addBtn">Add Image</button>
        </div>

        <div id="gallery"></div>

        <!-- Lightbox -->
        <div id="lightbox" class="lightbox hidden">
            <span id="closeBtn">&times;</span>
            <img id="lightboxImage" src="" alt="">
            <p id="lightboxTitle"></p>
        </div>

        <script src="gallery.js"></script>
    </body>
    </html>
    ```

---

## Task 1: Select All Elements

!!! abstract "Instructions"
    In `gallery.js`, use `querySelector` or `getElementById` to select all the DOM elements you will need. Store them in variables (use `const`).

??? hint "Hint - Click to expand"
    Use `document.getElementById()` to select the following elements. Store each in a variable:

    - The two input fields (`imageUrl`, `imageTitle`)
    - The Add button (`addBtn`)
    - The gallery container (`gallery`)
    - The lightbox and its contents (`lightbox`, `lightboxImage`, `lightboxTitle`)
    - The close button (`closeBtn`)

    Look at the HTML `id` attributes to find the right IDs to use.

---

## Task 2: Add Images to the Gallery

!!! abstract "Instructions"
    When the user clicks "Add Image", create a new gallery item and append it to the gallery grid. Each item should be a `<div>` containing:

    - An `<img>` element with the provided URL
    - A `<p>` element with the title
    - A "Delete" button

    Clear the input fields after adding. Do not add if either field is empty.

??? hint "Hint - Click to expand"
    - Add a `click` event listener to the Add button.
    - Get the trimmed values from both inputs. If either is empty, show an alert and `return` to stop.
    - Create a new `<div>` with `document.createElement("div")` and add the class `"gallery-item"` using `classList.add()`.
    - Create an `<img>`, set its `src` to the URL and `alt` to the title.
    - Create a `<p>` and set its `textContent` to the title.
    - Create a `<button>`, set its text to "Delete", and give it the class `"delete-btn"`.
    - Append the img, p, and button to the div, then append the div to the gallery.
    - Clear both input fields by setting their `value` to `""`.

---

## Task 3: Delete Images

!!! abstract "Instructions"
    Make the "Delete" button on each gallery item remove that item from the page. Add the event listener inside the same function that creates the item.

??? hint "Hint - Click to expand"
    - Add a `click` event listener to the delete button (do this inside the same function where you create the button, so you have access to the item variable).
    - Inside the listener, call `.remove()` on the gallery item element you created.

---

## Task 4: Open the Lightbox

!!! abstract "Instructions"
    When a user clicks on an image, open a lightbox (full-size overlay) showing the image. The lightbox should display the image and its title. The lightbox is already in the HTML — you just need to show it and populate its content.

??? hint "Hint - Click to expand"
    - Add a `click` event listener to the image element (do this after creating the img).
    - Inside, set the `src` of `lightboxImage` to the image URL and the `textContent` of `lightboxTitle` to the title.
    - Remove the `"hidden"` class from the lightbox element using `classList.remove()`.

---

## Task 5: Close the Lightbox

!!! abstract "Instructions"
    Close the lightbox when:

    - The user clicks the x button
    - The user clicks the dark background outside the image

??? hint "Hint - Click to expand"
    - **Close button:** Add a `click` event listener to the close button. Inside, add the `"hidden"` class back to the lightbox using `classList.add()`.
    - **Click outside the image:** Add a `click` event listener to the lightbox itself. In the handler, check if `event.target` is the lightbox (not the image inside it). If it is, hide the lightbox.

---

## Task 6: Keyboard Navigation

!!! abstract "Instructions"
    Allow users to close the lightbox by pressing the `Escape` key.

??? hint "Hint - Click to expand"
    - Add a `keydown` event listener to `document`.
    - In the handler, check if `event.key` is `"Escape"`.
    - If it is, add the `"hidden"` class to the lightbox to hide it.

---

## Task 7: Image Error Handling

!!! abstract "Instructions"
    If an image URL is invalid (the image fails to load), replace it with a placeholder message. Use the `error` event on the image element.

??? hint "Hint - Click to expand"
    - Add an `error` event listener to the image element (add it where you create the img).
    - When the image fails to load, set its `src` to a placeholder image URL (e.g., `https://via.placeholder.com/300x200?text=Image+Not+Found`) and update the `alt` text to indicate the image was not found.

---

## Task 8: Style the Gallery

!!! abstract "Instructions"
    Create `gallery.css` and style the page:

    - The gallery should use a responsive grid (use flexbox `flex-wrap` or CSS Grid)
    - Gallery items should have a border, padding, and look like cards
    - The lightbox should cover the full screen with a dark semi-transparent background
    - The close button should be large and positioned in the top-right corner
    - Delete buttons should be small and red

??? hint "Hint - CSS"
    - **Body:** Set a `font-family`, `max-width` around 1000px, use `margin: 0 auto` to centre, and add `padding`.
    - **Gallery controls:** Use `display: flex` with `gap` to lay out the inputs and button in a row. Let the inputs grow with `flex: 1`.
    - **Gallery grid:** Use `display: flex` with `flex-wrap: wrap` and `gap` for a responsive grid.
    - **Gallery items:** Add `border`, `border-radius`, `padding`, and a fixed `width`. Centre the text.
    - **Images inside items:** Set `width: 100%`, a fixed `height`, and `object-fit: cover` so they crop nicely. Add `cursor: pointer` to indicate they're clickable.
    - **Delete button:** Use a red `background-color` with white text, remove the border, add padding and `border-radius`.
    - **Lightbox:** Use `position: fixed` to cover the full screen (`top: 0; left: 0; width: 100%; height: 100%`). Set a dark semi-transparent `background` (e.g., `rgba(0,0,0,0.85)`). Use flexbox to centre the content.
    - **Close button:** Position it with `position: absolute; top: 1rem; right: 2rem`. Make it large and white.
    - **Hidden class:** Use `display: none` to hide elements.

---

## Requirements

- Use `addEventListener` for at least 4 different event types (click, keydown, error, etc.)
- Use `document.createElement()` to add elements
- Use `element.remove()` to delete elements
- Use `classList.add()` and `classList.remove()` to toggle visibility
- Handle the image `error` event for broken URLs
- The lightbox closes with both the x button and the Escape key
