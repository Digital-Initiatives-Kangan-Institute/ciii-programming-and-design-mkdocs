# Fetch, Async, and JSON

Fetching data from APIs is a core skill for building dynamic web applications. This page covers the fundamentals of making requests and handling responses.

---

## What is Async Code?

Most of your code runs synchronously (one line after another). Network requests are different — they take time, and you cannot block the whole page while waiting.

**Asynchronous** code lets you start a request and continue running other code while waiting for the response.

---

## Fetch with Promises

```typescript
fetch("https://dummyjson.com/products")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Fetch failed:", error));
```

- `fetch()` starts the request
- `.then()` runs when the response arrives
- `response.json()` parses the JSON body
- `.catch()` handles errors

---

## Fetch with Async/Await

`async` and `await` make asynchronous code read more like synchronous code:

```typescript
async function fetchProducts() {
    try {
        const response = await fetch("https://dummyjson.com/products");
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Fetch failed:", error);
    }
}
```

- `async` marks a function as asynchronous
- `await` pauses execution until the promise resolves
- `try/catch` replaces `.catch()` for error handling

---

## Understanding JSON Responses

When you call an API, the response body is a string. You need to parse it:

```typescript
const response = await fetch("https://dummyjson.com/products/1");
const product = await response.json();

console.log(product.title);    // "iPhone 9"
console.log(product.price);    // 549
```

---

## Displaying Useful Fields

APIs often return more data than you need. Select only the fields relevant to your UI:

```typescript
const data = await response.json();
const products = data.products;

products.forEach(product => {
    console.log(`${product.title} - $${product.price}`);
});
```

---

## Connecting to Different Endpoints

The same fetch pattern works for any REST API. Just change the URL and adjust the fields you display:

```typescript
// Products
const products = await fetch("https://dummyjson.com/products");

// Users
const users = await fetch("https://dummyjson.com/users");

// Posts
const posts = await fetch("https://dummyjson.com/posts");
```

---

## Summary

- Asynchronous code handles operations that take time (like network requests)
- `fetch()` + `.then()` or `async/await` are the two approaches
- Always parse the response with `.json()`
- Select only the fields you need to display
- The fetch pattern is the same regardless of endpoint
