# Data, APIs, and the Frontend

Understanding how data flows from a database through an API to the user's browser is essential for building modern web applications.

---

## The Three Layers

A typical web application has three layers:

```
[Database] → [API Server] → [Frontend]
```

| Layer | Purpose | Examples |
|---|---|---|
| **Database** | Stores persistent data | PostgreSQL, MongoDB, SQLite |
| **API** | Business logic, data access | REST API, GraphQL |
| **Frontend** | User interface in the browser | HTML/CSS/JS, React, Next.js |

---

## How Data Flows

A typical request follows this path:

```
1. User clicks "View Products" in the browser
2. Frontend sends a GET request to /api/products
3. API server receives the request
4. API queries the database: SELECT * FROM products
5. Database returns the product rows
6. API formats the data as JSON
7. API sends the JSON response back to the frontend
8. Frontend parses the JSON and renders HTML
```

The frontend never talks directly to the database — the API sits in between, providing a controlled interface.

---

## HTTP and JSON

Web APIs communicate using HTTP (HyperText Transfer Protocol) and typically exchange data in JSON format.

### HTTP Methods

| Method | Purpose |
|---|---|
| `GET` | Retrieve data |
| `POST` | Create new data |
| `PUT` / `PATCH` | Update existing data |
| `DELETE` | Remove data |

### JSON (JavaScript Object Notation)

```json
{
    "products": [
        {
            "id": 1,
            "name": "Laptop",
            "price": 1200,
            "inStock": true
        }
    ]
}
```

JSON is human-readable and easily parsed by JavaScript with `JSON.parse()` or `response.json()`.

---

## The Fetch API

The `fetch()` function is the modern way to make HTTP requests from JavaScript. It returns a Promise that resolves to a Response object.

### GET Request

```javascript
fetch("https://api.example.com/products")
    .then(response => {
        if (!response.ok) {
            throw new Error("Network response was not OK");
        }
        return response.json();
    })
    .then(data => {
        console.log(data);
        // Render the products to the page
    })
    .catch(error => {
        console.error("Error fetching products:", error);
    });
```

### POST Request

```javascript
fetch("https://api.example.com/products", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        name: "New Product",
        price: 29.99
    })
})
    .then(response => response.json())
    .then(data => console.log("Created:", data))
    .catch(error => console.error("Error:", error));
```

### POST with Form Data

```javascript
document.getElementById("loginForm").addEventListener("submit", function(event) {
    event.preventDefault();

    const username = document.getElementById("username").value;
    const password = document.getElementById("password").value;

    fetch("https://api.example.com/login", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ username, password })
    })
        .then(response => {
            if (!response.ok) throw new Error("Login failed");
            return response.json();
        })
        .then(data => {
            console.log("Welcome, " + data.name);
        })
        .catch(error => {
            console.error("Invalid credentials.");
        });
});
```

---

## Key Concepts

### Promises

`fetch()` returns a Promise — an object representing a value that will be available in the future.

```javascript
// Chaining with .then()
fetch(url)
    .then(response => response.json())   // Runs when fetch completes
    .then(data => renderData(data))       // Runs when JSON is parsed
    .catch(error => handleError(error));  // Runs if anything fails
```

### Async / Await

`async/await` is syntactic sugar over Promises that makes asynchronous code look synchronous:

```javascript
async function loadProducts() {
    try {
        const response = await fetch("https://api.example.com/products");
        if (!response.ok) throw new Error("Failed to load");
        const data = await response.json();
        renderData(data);
    } catch (error) {
        console.error(error);
    }
}
```

### Response Status Codes

| Code | Meaning |
|---|---|
| `200` | OK — request succeeded |
| `201` | Created — resource was created |
| `400` | Bad Request — invalid input |
| `401` | Unauthorized — not logged in |
| `404` | Not Found — resource doesn't exist |
| `500` | Server Error — something went wrong on the server |

---

## Summary

- Data flows: **Database → API → Frontend**
- APIs communicate via **HTTP** using methods like GET, POST, PUT, DELETE
- Data is typically exchanged in **JSON** format
- Use **`fetch()`** to make HTTP requests from JavaScript
- Check `response.ok` to handle errors properly
- **Async/await** makes asynchronous code easier to read
