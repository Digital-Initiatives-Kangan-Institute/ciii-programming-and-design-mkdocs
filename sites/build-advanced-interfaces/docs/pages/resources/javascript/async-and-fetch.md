# Async JavaScript and Fetch

Web applications constantly communicate with servers — loading data, submitting forms, checking authentication. JavaScript handles these operations **asynchronously**, meaning it does not freeze the page while waiting for a response.

---

## Why Asynchronous?

Network requests take time. If JavaScript waited (blocked) for each one, the entire page would freeze.

```javascript
// DON'T DO THIS — synchronous, would freeze the page
let response = fetchSync("https://api.example.com/data");   // Blocks until done
console.log(response);

// DO THIS — asynchronous, page stays responsive
fetch("https://api.example.com/data")
    .then(response => response.json())
    .then(data => console.log(data));
console.log("This runs immediately, before the data arrives!");
```

The second example does not wait — it registers a callback and continues executing.

---

## Promises

A Promise is an object representing a value that will be available **later**. It has three states:

| State | Meaning |
|---|---|
| **Pending** | The operation is in progress |
| **Fulfilled** | The operation completed successfully |
| **Rejected** | The operation failed |

### Creating a Promise

```javascript
let promise = fetch("https://api.example.com/data");
// promise is now "pending"

promise
    .then(response => {
        // Runs when the fetch succeeds
        return response.json();
    })
    .then(data => {
        // Runs when JSON parsing succeeds
        console.log(data);
    })
    .catch(error => {
        // Runs if anything fails
        console.error("Error:", error);
    });
```

### Chaining

`.then()` returns a new Promise, so you can chain operations:

```javascript
fetch("/api/user")
    .then(response => response.json())
    .then(user => fetch(`/api/posts?userId=${user.id}`))
    .then(response => response.json())
    .then(posts => console.log(posts))
    .catch(error => console.error(error));
```

---

## The Fetch API

`fetch()` is the modern way to make HTTP requests. It returns a Promise.

### GET Request (Read Data)

```javascript
fetch("https://jsonplaceholder.typicode.com/users")
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
    })
    .then(users => {
        // Render users to the page
        users.forEach(user => {
            console.log(`${user.name} — ${user.email}`);
        });
    })
    .catch(error => {
        console.error("Failed to load users:", error.message);
    });
```

### POST Request (Create Data)

```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        title: "New Post",
        body: "This is the content of the new post.",
        userId: 1
    })
})
    .then(response => {
        if (!response.ok) throw new Error("Failed to create post");
        return response.json();
    })
    .then(newPost => console.log("Created:", newPost))
    .catch(error => console.error("Error:", error));
```

### PUT / PATCH Request (Update Data)

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", {
    method: "PUT",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
        id: 1,
        title: "Updated Title",
        body: "Updated content.",
        userId: 1
    })
})
    .then(response => response.json())
    .then(updatedPost => console.log("Updated:", updatedPost));
```

### DELETE Request (Remove Data)

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", {
    method: "DELETE"
})
    .then(response => {
        if (response.ok) {
            console.log("Post deleted successfully.");
        }
    });
```

---

## Async / Await

`async/await` is syntactic sugar over Promises — it makes asynchronous code look synchronous.

### Converting .then() to Async/Await

```javascript
// With .then()
function getUsers() {
    fetch("https://jsonplaceholder.typicode.com/users")
        .then(response => response.json())
        .then(users => console.log(users))
        .catch(error => console.error(error));
}

// With async/await
async function getUsers() {
    try {
        let response = await fetch("https://jsonplaceholder.typicode.com/users");
        let users = await response.json();
        console.log(users);
    } catch (error) {
        console.error("Error:", error);
    }
}
```

### Key Rules

- `await` only works inside `async` functions
- `await` pauses the function until the Promise resolves (but does not block the rest of the page)
- Always wrap `await` calls in `try/catch` for error handling

### Real Example: Loading User Data

```javascript
async function loadUserProfile(userId) {
    try {
        // Show loading state
        document.getElementById("loading").style.display = "block";

        let response = await fetch(`https://api.example.com/users/${userId}`);

        if (!response.ok) {
            throw new Error(`User not found (${response.status})`);
        }

        let user = await response.json();

        // Render to the page
        document.getElementById("name").textContent = user.name;
        document.getElementById("email").textContent = user.email;
    } catch (error) {
        document.getElementById("error").textContent = error.message;
    } finally {
        // Hide loading state — always runs
        document.getElementById("loading").style.display = "none";
    }
}

loadUserProfile(1);
```

The `finally` block runs regardless of success or failure — perfect for hiding loading spinners.

---

## HTTP Status Codes

| Code | Meaning | Typical response |
|---|---|---|
| **200** | OK | Request succeeded |
| **201** | Created | Resource was created (POST) |
| **204** | No Content | Success but no body (DELETE) |
| **400** | Bad Request | Invalid input from client |
| **401** | Unauthorized | Not logged in |
| **403** | Forbidden | Logged in but not allowed |
| **404** | Not Found | Resource doesn't exist |
| **500** | Internal Server Error | Something broke on the server |

Always check `response.ok` (which is true for status 200–299) before trying to parse the body.

---

## Working with External Libraries (Bootstrap)

Libraries provide pre-built functionality you can include without writing everything yourself.

### Including Bootstrap

```html
<head>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <button class="btn btn-primary">Bootstrap Button</button>

    <!-- Bootstrap JS (at end of body) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
```

Bootstrap provides pre-built components: navbars, cards, modals, alerts, and a responsive 12-column grid.

### Bootstrap Grid Example

```html
<div class="container">
    <div class="row">
        <div class="col-md-4">Column 1</div>
        <div class="col-md-4">Column 2</div>
        <div class="col-md-4">Column 3</div>
    </div>
</div>
```

---

## Why This Matters for Next.js

Next.js data fetching uses the same `fetch` API and `async/await` pattern:

```typescript
// Server Component — fetches data at request time
export default async function UsersPage() {
    let res = await fetch("https://api.example.com/users");
    let users = await res.json();

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

The Promise and async/await concepts you learn here transfer directly to Next.js. The only difference is where the code runs (server vs. browser).

---

## Summary

- JavaScript uses **asynchronous** operations so the page stays responsive
- A **Promise** represents a future value — it can be pending, fulfilled, or rejected
- **`fetch()`** makes HTTP requests and returns a Promise
- Chain `.then()` for sequential async operations; use `.catch()` for errors
- **`async/await`** makes asynchronous code read like synchronous code
- Always wrap `await` in `try/catch` and check `response.ok`
- The `finally` block runs regardless of success or failure
