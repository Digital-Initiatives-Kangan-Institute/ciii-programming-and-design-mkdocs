# Mock APIs

Mock APIs provide realistic data without needing to build your own backend. They are useful for learning, prototyping, and testing front-end code.

---

## What is a Mock API?

A mock API is a hosted service that returns dummy data through standard API endpoints. You send requests the same way you would to a real backend, but the data is pre-made and the service requires no setup.

---

## DummyJSON

[DummyJSON](https://dummyjson.com) provides fake data for common scenarios.

Example endpoints:

```
GET https://dummyjson.com/products
GET https://dummyjson.com/products/1
GET https://dummyjson.com/users
GET https://dummyjson.com/posts
GET https://dummyjson.com/quotes
GET https://dummyjson.com/recipes
```

Each endpoint returns JSON data you can display in your front end:

```javascript
fetch("https://dummyjson.com/products")
    .then(function (response) {
        return response.json();
    })
    .then(function (data) {
        console.log(data.products);   // array of 30 products
    });
```

---

## MockAPI

[MockAPI](https://mockapi.io) lets you create your own custom endpoints with your own data structure. You define the fields and fill in sample records, giving you full control over the data shape.

This is useful when you want to test with data that matches your specific app's needs.

---

## Why Use Mock APIs?

- No backend setup required
- Realistic data for testing and prototyping
- Focus on building the front end first
- Safe to experiment — no risk of breaking real data
- Learn API concepts without a database

---

## Key Patterns

When building with mock APIs, the general pattern is:

1. Choose an endpoint (e.g., products, users, posts)
2. Fetch data with `fetch()`
3. Parse the JSON response
4. Select the fields you want to display
5. Build HTML elements and insert them into the page

---

## Summary

- Mock APIs like DummyJSON and MockAPI let you work with real data without a backend
- They respond to standard HTTP requests with JSON
- Use them to practice fetch, display patterns, and front-end development
