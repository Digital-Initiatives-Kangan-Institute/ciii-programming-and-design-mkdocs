# Building Forms and Validation

Forms are how users send data to your application. Good forms need clear labels, helpful validation messages, and an accessible design.

---

## HTML Form Basics

```html
<form id="login-form">
    <label for="username">Username</label>
    <input type="text" id="username" name="username">

    <label for="password">Password</label>
    <input type="password" id="password" name="password">

    <button type="submit">Log In</button>
</form>
```

Key elements:

- `<form>` wraps the entire form
- `<label>` associates text with an input (use `for` matching the input's `id`)
- `<input>` accepts user data
- `<button type="submit">` triggers form submission

---

## Accessible Labels

Every input should have a visible, descriptive label. Labels improve accessibility and usability:

```html
<label for="email">Email address</label>
<input type="email" id="email" name="email">
```

When a user clicks the label, the browser focuses the associated input. This is especially helpful on mobile.

---

## Input Types

Use the right input type for the data you are collecting:

| Type | Use for |
|---|---|
| `text` | Names, general text |
| `email` | Email addresses |
| `password` | Masked password entry |
| `number` | Numeric values |
| `date` | Date selection |
| `checkbox` | Yes/no toggles |

```html
<input type="email" id="email" name="email" placeholder="you@example.com">
<input type="password" id="password" name="password" required>
```

---

## Preventing Default Form Behaviour

By default, submitting a form reloads the page. In a single-page or JavaScript-driven app, you want to handle the submission yourself:

```javascript
let form = document.querySelector("#login-form");

form.addEventListener("submit", function (event) {
    event.preventDefault();

    let username = document.querySelector("#username").value;
    let password = document.querySelector("#password").value;

    console.log("Username: " + username);
});
```

`event.preventDefault()` stops the browser from reloading the page.

---

## Client-Side Validation

Validate input before sending it to a server:

```javascript
form.addEventListener("submit", function (event) {
    event.preventDefault();

    let username = document.querySelector("#username").value;
    let password = document.querySelector("#password").value;

    if (username.trim() === "") {
        alert("Please enter a username.");
        return;
    }

    if (password.length < 6) {
        alert("Password must be at least 6 characters.");
        return;
    }

    console.log("Form is valid!");
});
```

---

## Displaying Validation Messages

Instead of `alert()`, show messages directly in the page for a better user experience:

```html
<p id="username-error" style="color: red; display: none;">
    Please enter a username.
</p>
```

```javascript
let errorMsg = document.querySelector("#username-error");

if (username.trim() === "") {
    errorMsg.style.display = "block";
}
```

---

## Visual Design Tips

- Labels should sit above or beside their inputs
- Use consistent spacing between form fields
- Validation messages should appear near the relevant input
- Use colour (red for errors, green for success) to guide the user
- Ensure sufficient contrast between text and background

---

## Summary

- Every input needs a descriptive `<label>` with a matching `for`/`id`
- Use `event.preventDefault()` to handle form submission with JavaScript
- Validate input on the client side before sending
- Show validation messages directly on the page
- Good forms are accessible, clear, and visually well-designed
