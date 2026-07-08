# How the Web Works

Understanding the flow of data from server to screen helps you build better web applications. This page covers the fundamental architecture of the web.

---

## The Request-Response Cycle

Every time you load a web page, a conversation happens between your browser (the **client**) and a remote computer (the **server**):

1. You type a URL or click a link
2. The browser sends a **request** to the server
3. The server processes the request
4. The server sends back a **response** (HTML, CSS, JavaScript, data)
5. The browser renders the response as a visible page

---

## Front End vs Back End

### Front End

Everything the user sees and interacts with in the browser:

- HTML (structure)
- CSS (appearance)
- JavaScript (behaviour)

### Back End

Everything that runs on the server:

- Application logic
- Database operations
- Authentication
- API endpoints

---

## How Data Moves

Data flows through several layers:

```
Database  -->  API  -->  Front End
  |            |           |
Supabase    REST/JSON    HTML/CSS/JS
```

1. **Database** stores data (users, products, posts)
2. **API** provides controlled access to that data
3. **Front End** fetches the data and displays it

---

## What is an API?

API stands for Application Programming Interface. A web API is a set of URLs that return data (usually in JSON format) rather than HTML pages.

Example API call:

```
GET https://dummyjson.com/products/1
```

Returns structured data:

```json
{
    "id": 1,
    "title": "iPhone 9",
    "price": 549,
    "description": "An apple mobile..."
}
```

---

## Fetch — The Bridge Between Front End and API

JavaScript uses `fetch()` to request data from an API:

```javascript
fetch("https://dummyjson.com/products")
    .then(function (response) {
        return response.json();
    })
    .then(function (data) {
        console.log(data);
    });
```

The front end can then take that data and display it on the page.

---

## Server-Side Rendering vs Client-Side Rendering

### Client-Side Rendering (CSR)

The browser downloads a minimal HTML shell and JavaScript, then JavaScript fetches data and builds the page. Common in React/Next.js apps.

### Server-Side Rendering (SSR)

The server builds the full HTML page (with data) and sends it to the browser. The page is ready to view immediately.

| SSR | CSR |
|---|---|
| Faster first page load | Faster subsequent navigation |
| Better for SEO | Richer interactivity |
| More server load | More client-side processing |

---

## Summary

- The web works through a request-response cycle between client and server
- Data flows from database through API to front end
- APIs return structured data (JSON) that JavaScript can use
- `fetch()` is the bridge between front-end code and APIs
- Next.js supports both client-side and server-side rendering
