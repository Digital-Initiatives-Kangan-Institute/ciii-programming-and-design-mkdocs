# Mock APIs

During frontend development, the real backend is often not ready yet. Mock APIs let you simulate server responses so you can build and test the frontend independently.

---

## Why Use Mock APIs?

| Reason | Benefit |
|---|---|
| **Independent development** | Frontend and backend teams work in parallel |
| **Test scenarios** | Simulate success, errors, empty data, and slow responses |
| **No backend setup** | No need to install databases or configure servers |
| **Faster prototyping** | Quickly iterate on UI without waiting for API changes |
| **Offline development** | Work without an internet connection |

---

## Approach 1: Static JSON File

The simplest mock: create a `.json` file and fetch it.

```json
// data/products.json
[
    { "id": 1, "name": "Laptop", "price": 1200 },
    { "id": 2, "name": "Mouse", "price": 25 },
    { "id": 3, "name": "Keyboard", "price": 80 }
]
```

```javascript
fetch("data/products.json")
    .then(response => response.json())
    .then(products => {
        products.forEach(p => console.log(p.name));
    });
```

Limitations: static data only, no POST/PUT/DELETE, no filtering or search.

---

## Approach 2: JSON Server

JSON Server creates a full fake REST API from a single JSON file. It supports GET, POST, PUT, PATCH, and DELETE.

### Setup

```bash
# Install globally
npm install -g json-server

# Create a database file
echo '{
  "users": [
    { "id": 1, "name": "Alice", "email": "alice@example.com" }
  ],
  "products": [
    { "id": 1, "name": "Laptop", "price": 1200 },
    { "id": 2, "name": "Mouse", "price": 25 }
  ]
}' > db.json
```

### Start the Server

```bash
json-server --watch db.json --port 3000
```

Now you have a full REST API:

```
GET    http://localhost:3000/users
GET    http://localhost:3000/users/1
POST   http://localhost:3000/users
PUT    http://localhost:3000/users/1
DELETE http://localhost:3000/users/1
GET    http://localhost:3000/products
GET    http://localhost:3000/products?name=Laptop
GET    http://localhost:3000/products?price_gte=100
```

### Using It from the Frontend

```javascript
// GET all users
fetch("http://localhost:3000/users")
    .then(res => res.json())
    .then(users => console.log(users));

// POST a new user
fetch("http://localhost:3000/users", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ name: "Bob", email: "bob@example.com" })
})
    .then(res => res.json())
    .then(newUser => console.log("Created:", newUser));

// DELETE a user
fetch("http://localhost:3000/users/1", { method: "DELETE" });
```

---

## Approach 3: Mock Service Worker (MSW)

MSW intercepts network requests at the service worker level — no mock server needed. Best for testing.

```bash
npm install msw --save-dev
```

MSW lets you define handlers that intercept requests:

```typescript
import { http, HttpResponse } from "msw";

export const handlers = [
    http.get("/api/users", () => {
        return HttpResponse.json([
            { id: 1, name: "Alice" },
            { id: 2, name: "Bob" }
        ]);
    }),

    http.post("/api/users", async ({ request }) => {
        const body = await request.json();
        return HttpResponse.json({ id: 3, ...body });
    })
];
```

---

## Approach 4: Built-in Next.js API Routes

Next.js can serve as its own mock API. Create files in `pages/api/`:

```typescript
// pages/api/users.ts
import type { NextApiRequest, NextApiResponse } from "next";

const users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" }
];

export default function handler(req: NextApiRequest, res: NextApiResponse) {
    if (req.method === "GET") {
        res.status(200).json(users);
    } else if (req.method === "POST") {
        const newUser = { id: users.length + 1, ...req.body };
        users.push(newUser);
        res.status(201).json(newUser);
    } else {
        res.status(405).json({ error: "Method not allowed" });
    }
}
```

Now you can `fetch("/api/users")` from your frontend components.

---

## Simulating Errors and Delays

### Simulate a Slow Network

```javascript
// Add a delay to your mock
fetch("http://localhost:3000/users")
    .then(res => new Promise(r => setTimeout(() => r(res), 2000)))  // 2s delay
    .then(res => res.json())
    .then(data => console.log(data));
```

### Simulate an Error

```javascript
// Return a 500 error for testing error handling
fetch("http://localhost:3000/users")
    .then(res => {
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        return res.json();
    })
    .catch(error => {
        console.error("Failed to load users:", error.message);
        // Show error message to the user
    });
```

---

## Summary

- Mock APIs let you **develop the frontend independently** from the backend
- **Static JSON files** are the simplest approach — good for prototyping
- **JSON Server** creates a full REST API from a JSON file with zero code
- **MSW** intercepts requests at the network level — ideal for testing
- **Next.js API routes** serve as built-in mock endpoints within your project
- Always test **loading**, **error**, and **empty** states, not just success
