# JavaScript Interactivity

Add dynamic behaviour to a web page using JavaScript.

---

## Task 1: Button Counter

!!! abstract "Instructions"
    Create an HTML page with a button and a counter display. Each time the button is clicked, the counter should increase by 1.

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Counter</title>
    </head>
    <body>
        <h1>Counter: <span id="counter">0</span></h1>
        <button id="incrementBtn">Click Me</button>

        <script>
            // Your JavaScript here
        </script>
    </body>
    </html>
    ```

??? hint "Hint - Click to expand"
    Use `document.getElementById()` to get the button and counter elements, then add a `click` event listener that updates the counter's `textContent`.

---

## Task 2: Theme Toggle

!!! abstract "Instructions"
    Create a page with a button that toggles between light and dark mode. When clicked, change the background colour and text colour of the page.

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Theme Toggle</title>
        <style>
            body {
                transition: background-color 0.3s, color 0.3s;
            }
            .dark-mode {
                background-color: #1a1a1a;
                color: #ffffff;
            }
        </style>
    </head>
    <body>
        <h1>Theme Toggle</h1>
        <p>Click the button to switch themes.</p>
        <button id="themeBtn">Toggle Dark Mode</button>

        <script>
            // Your JavaScript here
        </script>
    </body>
    </html>
    ```

??? hint "Hint - Click to expand"
    Use `document.body.classList.toggle("dark-mode")` to add/remove the dark-mode class. You can change the button text based on the current mode.

---

## Task 3: Form Validation

!!! abstract "Instructions"
    Create a sign-up form with name, email, and password fields. Use JavaScript to validate that all fields are filled in before allowing submission. Show an error message if any field is empty.

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Sign Up</title>
    </head>
    <body>
        <h1>Sign Up</h1>
        <form id="signupForm">
            <div>
                <label for="name">Name:</label>
                <input type="text" id="name">
            </div>
            <div>
                <label for="email">Email:</label>
                <input type="email" id="email">
            </div>
            <div>
                <label for="password">Password:</label>
                <input type="password" id="password">
            </div>
            <button type="submit">Sign Up</button>
        </form>
        <p id="error" style="color: red;"></p>

        <script>
            // Your JavaScript here
        </script>
    </body>
    </html>
    ```

??? hint "Hint - Click to expand"
    Use `event.preventDefault()` to stop the form from submitting, then check if each input's `.value` is empty. Display an error if so, or show a success message.

---

## Task 4: To-Do List

!!! abstract "Instructions"
    Build a simple to-do list application. Users should be able to type a task into an input field, click "Add", and see the task appear in a list below. Each task should have a "Delete" button.

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>To-Do List</title>
    </head>
    <body>
        <h1>To-Do List</h1>
        <input type="text" id="taskInput" placeholder="Enter a task...">
        <button id="addBtn">Add</button>
        <ul id="taskList"></ul>

        <script>
            // Your JavaScript here
        </script>
    </body>
    </html>
    ```

??? hint "Hint - Click to expand"
    Use `document.createElement("li")` to create list items. Add a delete button inside each `<li>`. Use `element.remove()` to delete a task when its button is clicked.

---

## Task 5: Fetch and Display Data

!!! abstract "Instructions"
    Use the `fetch` API to get data from a public API and display it on your page. Try displaying a list of users or posts.

Use this public API: `https://jsonplaceholder.typicode.com/users`

??? code "click to expand"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Users</title>
    </head>
    <body>
        <h1>User List</h1>
        <div id="userList"></div>

        <script>
            // Your JavaScript here
        </script>
    </body>
    </html>
    ```

??? hint "Hint - Click to expand"
    Use `fetch()` to get the data, convert it to JSON, then loop through the results and create HTML elements for each user. Display the name, email, and company name for each user.
