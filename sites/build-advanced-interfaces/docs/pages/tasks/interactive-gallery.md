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
    In `gallery.js`, use `querySelector` or `getElementById` to select all the DOM elements you will need. Store them in variables.

??? hint "Hint - Click to expand"
    ```javascript
    const imageUrlInput = document.getElementById("imageUrl");
    const imageTitleInput = document.getElementById("imageTitle");
    const addBtn = document.getElementById("addBtn");
    const gallery = document.getElementById("gallery");
    const lightbox = document.getElementById("lightbox");
    const lightboxImage = document.getElementById("lightboxImage");
    const lightboxTitle = document.getElementById("lightboxTitle");
    const closeBtn = document.getElementById("closeBtn");
    ```

---

## Task 2: Add Images to the Gallery

!!! abstract "Instructions"
    When the user clicks "Add Image", create a new gallery item and append it to the gallery grid. Each item should be a `<div>` containing:

    - An `<img>` element with the provided URL
    - A `<p>` element with the title
    - A "Delete" button

    Clear the input fields after adding. Do not add if either field is empty.

??? hint "Hint - Click to expand"
    ```javascript
    addBtn.addEventListener("click", function() {
        let url = imageUrlInput.value.trim();
        let title = imageTitleInput.value.trim();

        if (!url || !title) {
            alert("Please fill in both fields.");
            return;
        }

        // Create the gallery item
        let item = document.createElement("div");
        item.classList.add("gallery-item");

        let img = document.createElement("img");
        img.src = url;
        img.alt = title;

        let caption = document.createElement("p");
        caption.textContent = title;

        let deleteBtn = document.createElement("button");
        deleteBtn.textContent = "Delete";
        deleteBtn.classList.add("delete-btn");

        item.appendChild(img);
        item.appendChild(caption);
        item.appendChild(deleteBtn);
        gallery.appendChild(item);

        // Clear inputs
        imageUrlInput.value = "";
        imageTitleInput.value = "";
    });
    ```

---

## Task 3: Delete Images

!!! abstract "Instructions"
    Make the "Delete" button on each gallery item remove that item from the page. Add the event listener inside the same function that creates the item.

??? hint "Hint - Click to expand"
    ```javascript
    deleteBtn.addEventListener("click", function() {
        item.remove();
    });
    ```

---

## Task 4: Open the Lightbox

!!! abstract "Instructions"
    When a user clicks on an image, open a lightbox (full-size overlay) showing the image. The lightbox should display the image and its title. The lightbox is already in the HTML — you just need to show it and populate its content.

??? hint "Hint - Click to expand"
    ```javascript
    img.addEventListener("click", function() {
        lightboxImage.src = url;
        lightboxTitle.textContent = title;
        lightbox.classList.remove("hidden");
    });
    ```

---

## Task 5: Close the Lightbox

!!! abstract "Instructions"
    Close the lightbox when:

    - The user clicks the × button
    - The user clicks the dark background outside the image

??? hint "Hint - Click to expand"
    ```javascript
    // Close button
    closeBtn.addEventListener("click", function() {
        lightbox.classList.add("hidden");
    });

    // Click outside the image
    lightbox.addEventListener("click", function(event) {
        if (event.target === lightbox) {
            lightbox.classList.add("hidden");
        }
    });
    ```

---

## Task 6: Keyboard Navigation

!!! abstract "Instructions"
    Allow users to close the lightbox by pressing the `Escape` key.

??? hint "Hint - Click to expand"
    ```javascript
    document.addEventListener("keydown", function(event) {
        if (event.key === "Escape") {
            lightbox.classList.add("hidden");
        }
    });
    ```

---

## Task 7: Image Error Handling

!!! abstract "Instructions"
    If an image URL is invalid (the image fails to load), replace it with a placeholder message. Use the `error` event on the image element.

??? hint "Hint - Click to expand"
    ```javascript
    img.addEventListener("error", function() {
        img.src = "https://via.placeholder.com/300x200?text=Image+Not+Found";
        img.alt = "Image not found";
    });
    ```

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
    ```css
    body {
        font-family: Arial, sans-serif;
        max-width: 1000px;
        margin: 0 auto;
        padding: 1rem;
    }

    #gallery-controls {
        display: flex;
        gap: 0.5rem;
        margin-bottom: 2rem;
    }

    #gallery-controls input {
        flex: 1;
        padding: 0.5rem;
    }

    #gallery {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }

    .gallery-item {
        border: 1px solid #ddd;
        border-radius: 8px;
        padding: 0.5rem;
        width: 200px;
        text-align: center;
    }

    .gallery-item img {
        width: 100%;
        height: 150px;
        object-fit: cover;
        border-radius: 4px;
        cursor: pointer;
    }

    .delete-btn {
        background-color: #e53935;
        color: white;
        border: none;
        padding: 0.25rem 0.75rem;
        border-radius: 4px;
        cursor: pointer;
    }

    .lightbox {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.85);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .lightbox img {
        max-width: 80%;
        max-height: 70vh;
        border-radius: 4px;
    }

    .lightbox p {
        color: white;
        margin-top: 1rem;
        font-size: 1.2rem;
    }

    #closeBtn {
        position: absolute;
        top: 1rem;
        right: 2rem;
        color: white;
        font-size: 2.5rem;
        cursor: pointer;
    }

    .hidden {
        display: none;
    }
    ```

---

## Requirements

- Use `addEventListener` for at least 4 different event types (click, keydown, etc.)
- Use `document.createElement()` to add elements
- Use `element.remove()` to delete elements
- Use `classList.add()` and `classList.remove()` to toggle visibility
- Handle the image `error` event for broken URLs
- The lightbox closes with both the × button and the Escape key
