# Working with APIs and Fetch

The Fetch API is the modern way to make HTTP requests from JavaScript. It replaces older approaches like XMLHttpRequest with a simpler, promise-based interface.

---

## What is Fetch?

`fetch()` is a built-in browser function that sends a network request and returns the response. It is the standard way for front-end code to get data from APIs.

---

## Basic Fetch Request

```javascript
fetch("https://dummyjson.com/products")
    .then(function (response) {
        return response.json();
    })
    .then(function (data) {
        console.log(data);
    });
```

- `fetch(url)` sends a GET request to the URL
- `.then()` handles the response when it arrives
- `response.json()` converts the response body into a JavaScript object

---

## Understanding Promises

`fetch()` returns a **Promise** — an object that represents a value that will be available in the future. A promise can be:

- **Pending** — the request is in progress
- **Fulfilled** — the data arrived successfully
- **Rejected** — something went wrong

`.then()` runs when the promise is fulfilled. `.catch()` runs when it is rejected.

---

## Displaying Fetched Data

Once you have the data, you can display it on the page:

```javascript
fetch("https://dummyjson.com/products")
    .then(function (response) {
        return response.json();
    })
    .then(function (data) {
        let products = data.products;
        let container = document.querySelector("#product-list");

        for (let i = 0; i < 5; i++) {
            let product = products[i];
            let card = document.createElement("div");
            card.innerHTML = `
                <h3>${product.title}</h3>
                <p>$${product.price}</p>
            `;
            container.appendChild(card);
        }
    });
```

---

## Display Formats

API data can be displayed in different formats:

- **Cards** — each item as a styled box with title, image, and details
- **List** — a simple ordered or unordered list
- **Table** — rows and columns for structured comparison

Choose the format that best presents your data.

---

## JSON — JavaScript Object Notation

JSON is the standard data format for APIs. It looks similar to JavaScript objects:

```json
{
    "products": [
        { "id": 1, "title": "Laptop", "price": 999 },
        { "id": 2, "title": "Mouse", "price": 29 }
    ],
    "total": 2
}
```

- Keys and string values use double quotes
- Supports objects `{}`, arrays `[]`, strings, numbers, booleans, and null

!!! note ""
    For a detailed guide on JSON syntax, data types, and working with `JSON.parse()` and `JSON.stringify()`, see the [JSON](../json.md) page.

---

## Summary

- `fetch()` is the standard way for JavaScript to request data from APIs
- Responses are handled asynchronously with `.then()`
- Use `response.json()` to parse JSON response data
- Display fetched data using DOM manipulation — cards, lists, or tables
- JSON is the format most APIs use to send and receive data
