# Building a Login Page

Build a complete login page using HTML, CSS, and JavaScript with fetch to communicate with an API.

---

## Task 1: HTML Form

!!! abstract "Instructions"
    Create an HTML login form with username and password fields. Include client-side validation to ensure both fields are filled before submission.

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Login</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div class="login-container">
            <h1>Login</h1>
            <form id="loginForm">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" name="username" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" name="password" required>
                </div>
                <button type="submit">Login</button>
            </form>
            <div id="message"></div>
        </div>
        <script src="login.js"></script>
    </body>
    </html>
    ```

---

## Task 2: Style the Login Page

!!! abstract "Instructions"
    Create a `style.css` file to make the login form look professional. Center the form on the page, style the inputs, and make the button attractive.

??? hint "Hint - Click to expand"
    - Centre the form vertically and horizontally: use `display: flex` on the body with `justify-content: center`, `align-items: center`, and `min-height: 100vh`. Give the body a light background colour.
    - Create a `.login-container` class: white `background`, `padding`, `border-radius`, `box-shadow`, and a fixed `width` around 320px.
    - Each `.form-group` needs `margin-bottom` for spacing.
    - Labels should be `display: block` and `font-weight: bold` with a small `margin-bottom`.
    - Inputs: full width (`width: 100%`), `padding`, a light `border`, `border-radius`, and `box-sizing: border-box` to include padding in the width.
    - Button: full width, `padding`, indigo background, white text, no border, `border-radius`, `cursor: pointer`. Darken slightly on `:hover`.

---

## Task 3: JavaScript with Fetch

!!! abstract "Instructions"
    Create `login.js` to handle the form submission. Use `fetch` to send the login credentials to a mock API. Display a success or error message based on the response.

    Use this mock endpoint: `https://jsonplaceholder.typicode.com/posts`

    For testing, treat any successful response (status 201) as a valid login. On error, display "Invalid credentials."

??? code "click to expand"
    ```javascript
    document.getElementById("loginForm").addEventListener("submit", function(event) {
        event.preventDefault();

        const username = document.getElementById("username").value.trim();
        const password = document.getElementById("password").value.trim();
        const messageDiv = document.getElementById("message");

        // TODO: Check if username or password is empty
        // If empty, show a red error message and use return to stop

        // TODO: Use fetch() to POST the username and password to:
        // https://jsonplaceholder.typicode.com/posts
        // Use method: "POST", Content-Type header, and JSON.stringify the body

        // TODO: If response.ok is true, parse the JSON and show a green success message
        // If not ok, throw an Error

        // TODO: Use .catch() to show a red error message
    });
    ```

??? hint "Hint - Error Handling"
    The `.catch()` block handles both network errors and HTTP errors. Test by temporarily disconnecting your internet or changing the URL to an invalid one.

---

## Task 4: Add Loading State

!!! abstract "Instructions"
    Enhance the login page by adding a loading state. While the fetch request is in progress, disable the button and show "Logging in..." text. Re-enable it when the request completes.

??? hint "Hint - Click to expand"
    - Before the `fetch` call, select the button element and disable it by setting `button.disabled = true`. Change its `textContent` to indicate loading (e.g., "Logging in...").
    - Use a `.finally()` block after your `.then()` and `.catch()` chains to re-enable the button and restore its original text. `.finally()` runs regardless of whether the request succeeded or failed, which is perfect for cleaning up the loading state.

---

## Task 5: Persist Login State

!!! abstract "Instructions"
    After a successful login, store the user's username in `localStorage` and display a welcome message instead of the login form on subsequent visits.

??? hint "Hint - Click to expand"
    - After a successful login, store the username using `localStorage.setItem("username", username)`.
    - On page load, use a `DOMContentLoaded` event listener to check if a username is already saved with `localStorage.getItem("username")`.
    - If a username exists, replace the content of the login container with a welcome message and a logout button. The logout button can call `localStorage.removeItem("username")` then reload the page with `location.reload()`.
