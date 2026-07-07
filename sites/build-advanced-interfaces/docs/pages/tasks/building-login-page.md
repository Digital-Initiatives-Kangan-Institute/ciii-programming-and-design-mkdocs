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
    ```css
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background-color: #f0f2f5;
        font-family: Arial, sans-serif;
    }

    .login-container {
        background: white;
        padding: 2rem;
        border-radius: 8px;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        width: 320px;
    }

    .form-group {
        margin-bottom: 1rem;
    }

    .form-group label {
        display: block;
        margin-bottom: 0.25rem;
        font-weight: bold;
    }

    .form-group input {
        width: 100%;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
    }

    button {
        width: 100%;
        padding: 0.75rem;
        background-color: #3f51b5;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        font-size: 1rem;
    }

    button:hover {
        background-color: #303f9f;
    }
    ```

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

        // Client-side validation
        if (!username || !password) {
            messageDiv.textContent = "Please fill in both fields.";
            messageDiv.style.color = "red";
            return;
        }

        // Send to API
        fetch("https://jsonplaceholder.typicode.com/posts", {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                username: username,
                password: password
            })
        })
        .then(function(response) {
            if (response.ok) {
                return response.json();
            } else {
                throw new Error("Login failed");
            }
        })
        .then(function(data) {
            messageDiv.textContent = "Login successful! Welcome.";
            messageDiv.style.color = "green";
            console.log("Response:", data);
        })
        .catch(function(error) {
            messageDiv.textContent = "Invalid credentials. Please try again.";
            messageDiv.style.color = "red";
        });
    });
    ```

??? hint "Hint - Error Handling"
    The `.catch()` block handles both network errors and HTTP errors. Test by temporarily disconnecting your internet or changing the URL to an invalid one.

---

## Task 4: Add Loading State

!!! abstract "Instructions"
    Enhance the login page by adding a loading state. While the fetch request is in progress, disable the button and show "Logging in..." text. Re-enable it when the request completes.

??? hint "Hint - Click to expand"
    Before the fetch call:

    ```javascript
    const button = document.querySelector("button");
    button.disabled = true;
    button.textContent = "Logging in...";
    ```

    In the `.finally()` block:

    ```javascript
    .finally(function() {
        button.disabled = false;
        button.textContent = "Login";
    });
    ```

---

## Task 5: Persist Login State

!!! abstract "Instructions"
    After a successful login, store the user's username in `localStorage` and display a welcome message instead of the login form on subsequent visits.

??? hint "Hint - Click to expand"
    Storing on login success:

    ```javascript
    localStorage.setItem("username", username);
    ```

    Checking on page load:

    ```javascript
    document.addEventListener("DOMContentLoaded", function() {
        const savedUser = localStorage.getItem("username");
        if (savedUser) {
            document.querySelector(".login-container").innerHTML =
                "<h1>Welcome back, " + savedUser + "!</h1>" +
                "<button onclick='localStorage.clear(); location.reload();'>Logout</button>";
        }
    });
    ```
