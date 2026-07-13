# JSON

JSON (JavaScript Object Notation) is the standard format for exchanging data between clients and servers. It is lightweight, human-readable, and natively supported by JavaScript.

---

## What is JSON?

JSON is a text format for representing structured data. It is the language most APIs speak — when you request data from a server, the response is almost always JSON.

JSON is:

- **Language-independent** — used by JavaScript, Python, Java, C#, and many others
- **Human-readable** — easy to read and write by hand
- **Lightweight** — minimal overhead compared to formats like XML

---

## JSON Syntax Rules

JSON has a strict syntax with specific rules:

### Data is in name-value pairs

```json
"title": "iPhone 9"
```

The name (key) is always a string in double quotes, followed by a colon, then the value.

### Objects are wrapped in curly braces

```json
{
    "id": 1,
    "title": "Laptop",
    "price": 999
}
```

### Arrays are wrapped in square brackets

```json
["apple", "banana", "orange"]
```

### Strings use double quotes only

```json
"name": "Alice"
```

Single quotes are **not** valid in JSON.

### No trailing commas

```json
// Correct
{ "name": "Alice", "age": 25 }

// Incorrect — trailing comma after last item
{ "name": "Alice", "age": 25, }
```

---

## JSON Data Types

JSON supports six data types:

| Type | Example |
|---|---|
| String | `"hello"` |
| Number | `42`, `3.14`, `-10` |
| Boolean | `true`, `false` |
| Null | `null` (means "no value") |
| Object | `{ "key": "value" }` |
| Array | `[1, 2, 3]` |

Note what JSON does **not** support:

- No functions or methods
- No `undefined`
- No comments
- No dates (dates are sent as strings like `"2026-07-12"`)

---

## JSON Structure Examples

### A Single Object

```json
{
    "id": 1,
    "title": "iPhone 9",
    "price": 549,
    "inStock": true,
    "description": "An apple mobile which is nothing like apple"
}
```

### An Array of Objects

```json
[
    { "id": 1, "title": "iPhone 9", "price": 549 },
    { "id": 2, "title": "Samsung Universe 9", "price": 1249 },
    { "id": 3, "title": "Huawei P30", "price": 499 }
]
```

### An Object with a Nested Array

```json
{
    "products": [
        { "id": 1, "title": "Laptop", "price": 999 },
        { "id": 2, "title": "Mouse", "price": 29 }
    ],
    "total": 2,
    "skip": 0,
    "limit": 30
}
```

This is the most common API response pattern — a wrapper object containing an array of items plus metadata (total count, pagination info).

---

## JSON vs JavaScript Objects

JSON looks like JavaScript objects but there are important differences:

| | JSON | JavaScript Object |
|---|---|---|
| Keys | Must be double-quoted | Quotes optional |
| Strings | Double quotes only | Single or double quotes |
| Trailing commas | Not allowed | Allowed |
| Functions | Not allowed | Allowed |
| Comments | Not allowed | Allowed |

```javascript
// This is a JavaScript object (valid in JS, not JSON)
let product = {
    title: "Laptop",       // unquoted key
    price: 999,           // trailing comma OK
}

// This is valid JSON
{
    "title": "Laptop",
    "price": 999
}
```

---

## Working with JSON in JavaScript

JavaScript has two built-in methods for converting between objects and JSON strings.

### `JSON.stringify()` — Object to String

Converts a JavaScript object into a JSON string (for sending data to a server):

```javascript
let product = {
    title: "Laptop",
    price: 999
};

let jsonString = JSON.stringify(product);
console.log(jsonString);
// '{"title":"Laptop","price":999}'
```

### `JSON.parse()` — String to Object

Converts a JSON string into a JavaScript object (for using data received from a server):

```javascript
let jsonString = '{"title":"Laptop","price":999}';

let product = JSON.parse(jsonString);
console.log(product.title);   // "Laptop"
console.log(product.price);   // 999
```

### Error Handling

Always wrap `JSON.parse()` in a try/catch block when parsing data from an external source:

```javascript
try {
    let data = JSON.parse(responseText);
    console.log(data);
} catch (error) {
    console.error("Failed to parse JSON:", error);
}
```

Malformed JSON or unexpected content will throw an error, which would break your page if uncaught.

---

## Accessing JSON Data

Once parsed, access JSON data the same way you access any JavaScript object:

```javascript
let data = {
    "products": [
        { "id": 1, "title": "Laptop", "price": 999 },
        { "id": 2, "title": "Mouse", "price": 29 }
    ],
    "total": 2
};

// Dot notation
console.log(data.total);                    // 2

// Bracket notation (for dynamic keys)
console.log(data["total"]);                 // 2

// Accessing nested data
console.log(data.products[0].title);        // "Laptop"

// Looping through an array
data.products.forEach(function(product) {
    console.log(product.title + " - $" + product.price);
});
// Laptop - $999
// Mouse - $29
```

---

## Common JSON Patterns

### Paginated Responses

```json
{
    "products": [...],
    "total": 100,
    "skip": 0,
    "limit": 30
}
```

These fields tell you there are 100 total products, you are viewing the first 30, and you can request the next 30 by setting `skip` to 30.

### Error Responses

```json
{
    "error": true,
    "message": "Product not found",
    "status": 404
}
```

### Nested Relationships

```json
{
    "user": {
        "id": 1,
        "name": "Alice",
        "address": {
            "street": "123 Main St",
            "city": "Melbourne",
            "postcode": "3000"
        }
    }
}
```

---

## Summary

- JSON is the standard data format for APIs — language-independent and human-readable
- Keys must be double-quoted; strings must use double quotes; no trailing commas
- JSON supports strings, numbers, booleans, null, objects, and arrays
- `JSON.stringify()` converts JavaScript objects to JSON strings
- `JSON.parse()` converts JSON strings to JavaScript objects
- Always wrap `JSON.parse()` in try/catch when parsing external data
- Access parsed JSON data with dot notation or bracket notation, just like regular objects
