# Web Application Architecture

Understanding how data flows from a database through an API to the frontend is essential for building modern web applications. This resource covers the key architectural patterns.

---

## Data to API to Frontend

A modern web application has three main layers:

```
[Database] → [API Server] → [Frontend]
```

### The Three Layers

1. **Database** — Stores persistent data (users, products, orders)
2. **API (Application Programming Interface)** — Handles business logic and serves data
3. **Frontend** — Renders the user interface in the browser

### How Data Flows

```
1. User clicks "View Products" in the browser
2. Frontend sends a GET request to /api/products
3. API queries the database for all products
4. API returns JSON data to the frontend
5. Frontend renders the products as HTML
```

### Fetch API

The `fetch` function is the modern way to make HTTP requests from JavaScript:

```javascript
// GET request
fetch("https://api.example.com/products")
    .then(response => response.json())
    .then(data => {
        console.log(data);
        // Render data to the page
    })
    .catch(error => console.error("Error:", error));
```

```javascript
// POST request
fetch("https://api.example.com/login", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        username: "alice",
        password: "secret"
    })
})
    .then(response => response.json())
    .then(data => console.log(data));
```

---

## Mock APIs

During development, you often need to work with an API before the real backend is ready. Mock APIs let you simulate server responses.

### Why Use Mock APIs?

- Develop the frontend independently from the backend
- Test different response scenarios (success, error, empty data)
- No need to set up a real database
- Faster iteration during prototyping

### Simple Mock with JSON

Create a `data.json` file and fetch it:

```javascript
fetch("data.json")
    .then(response => response.json())
    .then(data => renderPage(data));
```

### Mock API Services

Tools like MockAPI.io or JSON Server let you create a fake REST API quickly:

```bash
# Install JSON Server
npm install -g json-server

# Create a db.json file
echo '{ "users": [{ "id": 1, "name": "Alice" }] }' > db.json

# Start the mock server
json-server --watch db.json
```

Now you can make fetch requests to `http://localhost:3000/users`.

---

## Building a Login Page

A login page demonstrates the full architecture pattern using HTML, CSS, and JavaScript.

### HTML Structure

```html
<form id="loginForm">
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" required>

    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required>

    <button type="submit">Login</button>
</form>

<div id="message"></div>
```

### JavaScript with Fetch

```javascript
document.getElementById("loginForm").addEventListener("submit", function(event) {
    event.preventDefault();

    let username = document.getElementById("username").value;
    let password = document.getElementById("password").value;

    fetch("https://api.example.com/login", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ username, password })
    })
        .then(response => {
            if (!response.ok) {
                throw new Error("Login failed");
            }
            return response.json();
        })
        .then(data => {
            document.getElementById("message").textContent = "Welcome, " + data.name;
        })
        .catch(error => {
            document.getElementById("message").textContent = "Invalid credentials.";
        });
});
```

This pattern — HTML form, JavaScript event handler, fetch to API — is the foundation for all interactive web applications.

---

## Server-Side Rendering (SSR)

SSR generates HTML on the server rather than in the browser, providing faster initial page loads and better SEO.

### Client-Side Rendering (CSR)

```
Browser → Empty HTML → Downloads JS → JS renders page
```

### Server-Side Rendering (SSR)

```
Browser → Full HTML page immediately
```

| Feature | CSR | SSR |
|---|---|---|
| Initial load | Slower | Faster |
| SEO | Poorer | Better |
| Interactivity | Native SPA feel | Requires hydration |
| Server load | Lower | Higher |

---

## Frameworks

Modern frameworks handle routing, state management, and server-side rendering for you.

### Popular Frameworks

| Framework | Type | Key Feature |
|---|---|---|
| React | Library (CSR/SSR) | Component-based UI |
| Next.js | Framework (SSR/SSG) | Built on React with routing and SSR |
| Vue / Nuxt | Framework | Progressive, easy to learn |
| SvelteKit | Framework | Compile-time approach |

In this course, we use **Next.js** because it provides:
- File-based routing
- Server-side rendering out of the box
- API routes in the same project
- Excellent developer experience

---

## Summary

- Data flows from **Database → API → Frontend**
- **Fetch API** is the standard way to make HTTP requests
- **Mock APIs** let you develop the frontend independently
- A **login page** demonstrates the full architecture pattern
- **SSR** improves initial load speed and SEO
- **Frameworks** like Next.js simplify building full-stack applications
