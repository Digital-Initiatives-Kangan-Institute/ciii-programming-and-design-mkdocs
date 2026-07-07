# Building a Login Page

A login page demonstrates the full architecture pattern: HTML form, CSS styling, JavaScript event handling, and fetch to an API. This combines everything from the previous resources.

---

## The Full Pattern

A complete login page follows this pattern:

```
1. User fills in the HTML form
2. JavaScript intercepts the submit event
3. Client-side validation checks the inputs
4. fetch() sends credentials to the API
5. API responds with success or failure
6. JavaScript updates the UI based on the response
```

---

## Step 1: HTML Form

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
            <button type="submit" id="loginBtn">Login</button>
        </form>
        <div id="message"></div>
    </div>
    <script src="login.js"></script>
</body>
</html>
```

---

## Step 2: CSS Styling

```css
body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
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

h1 {
    text-align: center;
    margin-bottom: 1.5rem;
    color: #333;
}

.form-group {
    margin-bottom: 1rem;
}

.form-group label {
    display: block;
    margin-bottom: 0.25rem;
    font-weight: bold;
    font-size: 0.9rem;
}

.form-group input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    font-size: 0.95rem;
}

.form-group input:focus {
    outline: none;
    border-color: #3f51b5;
    box-shadow: 0 0 0 2px rgba(63, 81, 181, 0.2);
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
    margin-top: 0.5rem;
}

button:hover {
    background-color: #303f9f;
}

button:disabled {
    background-color: #9fa8da;
    cursor: not-allowed;
}

#message {
    margin-top: 1rem;
    text-align: center;
    font-size: 0.9rem;
}
```

---

## Step 3: JavaScript Logic

```javascript
document.getElementById("loginForm").addEventListener("submit", function(event) {
    event.preventDefault();

    const username = document.getElementById("username").value.trim();
    const password = document.getElementById("password").value.trim();
    const messageDiv = document.getElementById("message");
    const button = document.getElementById("loginBtn");

    // Client-side validation
    if (!username || !password) {
        messageDiv.textContent = "Please fill in both fields.";
        messageDiv.style.color = "red";
        return;
    }

    // Show loading state
    button.disabled = true;
    button.textContent = "Logging in...";
    messageDiv.textContent = "";

    // Send to API
    fetch("https://jsonplaceholder.typicode.com/posts", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ username, password })
    })
        .then(function(response) {
            if (!response.ok) throw new Error("Server error");
            return response.json();
        })
        .then(function(data) {
            messageDiv.textContent = "Login successful! Welcome, " + username + ".";
            messageDiv.style.color = "green";
            localStorage.setItem("loggedInUser", username);
        })
        .catch(function(error) {
            messageDiv.textContent = "Invalid credentials. Please try again.";
            messageDiv.style.color = "red";
        })
        .finally(function() {
            button.disabled = false;
            button.textContent = "Login";
        });
});
```

---

## Step 4: Persist Login State

After a successful login, store the username and check for it on page load:

```javascript
document.addEventListener("DOMContentLoaded", function() {
    const savedUser = localStorage.getItem("loggedInUser");
    if (savedUser) {
        document.querySelector(".login-container").innerHTML =
            "<h1>Welcome back, " + savedUser + "!</h1>" +
            "<button onclick='logout()'>Logout</button>";
    }
});

function logout() {
    localStorage.removeItem("loggedInUser");
    location.reload();
}
```

---

## Key Concepts Demonstrated

| Concept | Where |
|---|---|
| **HTML form** | Input fields with labels and submit button |
| **CSS layout** | Flexbox centering, input focus states, disabled button |
| **Event handling** | Submit event with `preventDefault()` |
| **Validation** | Client-side check for empty fields |
| **Fetch API** | POST request with JSON body |
| **Error handling** | `.catch()` block with user-friendly message |
| **Loading state** | Button disabled + text change |
| **Persistence** | `localStorage` to remember login |

---

## Summary

- A login page combines **HTML**, **CSS**, and **JavaScript** into a complete feature
- Use **`event.preventDefault()`** to stop the form from reloading the page
- Always add **loading** and **error** states — not just the happy path
- Use **`localStorage`** to persist data across page reloads
- This pattern (form → validate → fetch → update UI) applies to **any** interactive feature
