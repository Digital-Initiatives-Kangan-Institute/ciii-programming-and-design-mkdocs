# Forms and Inputs

Forms allow users to enter and submit data. Login pages, search bars, contact forms, and checkout pages are all built with HTML forms.

---

## The `<form>` Element

A form is a container for input elements. It wraps everything the user interacts with:

```html
<form>
    <label for="name">Name</label>
    <input type="text" id="name" name="name">

    <label for="email">Email</label>
    <input type="email" id="email" name="email">

    <button type="submit">Submit</button>
</form>
```

### Key Attributes

| Attribute | Purpose |
|---|---|
| `action` | URL where the form data is sent |
| `method` | HTTP method — `GET` (data in URL) or `POST` (data in request body) |

```html
<form action="/submit-form" method="POST">
    <!-- form fields -->
</form>
```

---

## Input Types

The `<input>` element's behaviour changes based on its `type` attribute:

```html
<input type="text" placeholder="Enter your name">
<input type="email" placeholder="Enter your email">
<input type="password" placeholder="Enter your password">
```

| Type | Description |
|---|---|
| `text` | Single-line text input (default) |
| `email` | Email input with built-in validation |
| `password` | Masked input (characters hidden) |
| `number` | Numeric input with increment/decrement arrows |
| `tel` | Telephone number input |
| `url` | URL input with validation |
| `date` | Date picker |
| `checkbox` | Single checkbox (on/off) |
| `radio` | Radio button (select one from a group) |
| `file` | File upload control |
| `submit` | Form submission button |
| `reset` | Resets all form fields to defaults |

### Checkboxes and Radio Buttons

```html
<!-- Checkboxes: multiple selections allowed -->
<input type="checkbox" id="newsletter" name="newsletter" checked>
<label for="newsletter">Subscribe to newsletter</label>

<!-- Radio buttons: only one per group -->
<input type="radio" id="small" name="size" value="small">
<label for="small">Small</label>

<input type="radio" id="medium" name="size" value="medium" checked>
<label for="medium">Medium</label>

<input type="radio" id="large" name="size" value="large">
<label for="large">Large</label>
```

Radio buttons in the same group share the same `name` attribute. Only one can be selected at a time.

---

## Labels

`<label>` describes what an input is for. It improves accessibility and usability — clicking the label focuses the associated input:

```html
<!-- Method 1: for attribute links to id -->
<label for="username">Username</label>
<input type="text" id="username" name="username">

<!-- Method 2: wrap the input inside the label -->
<label>
    Email
    <input type="email" name="email">
</label>
```

Always associate labels with inputs. Forms without labels are difficult for screen reader users to understand.

---

## Other Form Elements

### Textarea

For multi-line text input:

```html
<label for="message">Your message</label>
<textarea id="message" name="message" rows="4" cols="50"></textarea>
```

### Select Dropdown

For choosing from a list of options:

```html
<label for="drink">Choose a drink</label>
<select id="drink" name="drink">
    <option value="">-- Select --</option>
    <option value="espresso">Espresso</option>
    <option value="cappuccino">Cappuccino</option>
    <option value="latte">Latte</option>
</select>
```

### Fieldset and Legend

Group related fields together:

```html
<fieldset>
    <legend>Delivery Address</legend>

    <label for="street">Street</label>
    <input type="text" id="street" name="street">

    <label for="city">City</label>
    <input type="text" id="city" name="city">
</fieldset>
```

### Buttons

There are three ways to create a button:

```html
<!-- Submit button (submits the form) -->
<button type="submit">Place Order</button>

<!-- Reset button (clears the form) -->
<button type="reset">Clear</button>

<!-- Plain button (for JavaScript actions) -->
<button type="button">Show Details</button>

<!-- Input-based buttons -->
<input type="submit" value="Submit">
<input type="reset" value="Reset">
```

The `<button>` element is preferred over `<input type="submit">` because it can contain HTML content (icons, images).

---

## Common Input Attributes

| Attribute | Purpose | Example |
|---|---|---|
| `placeholder` | Hint text shown when the field is empty | `placeholder="Enter your name"` |
| `required` | Field must be filled before submission | `required` |
| `disabled` | Field is greyed out and not editable | `disabled` |
| `readonly` | Field is readable but not editable | `readonly` |
| `value` | Default or pre-filled value | `value="Australia"` |
| `checked` | Pre-selects a checkbox or radio | `checked` |
| `maxlength` | Maximum number of characters | `maxlength="50"` |
| `min` / `max` | Numeric range for number/date inputs | `min="1" max="100"` |

---

## Summary

- `<form>` wraps all input elements; use `action` and `method` to control submission
- `<input>` supports many `type` values — `text`, `email`, `password`, `number`, `checkbox`, `radio`, and more
- `<label>` must be associated with every input for accessibility
- `<textarea>` for multi-line text, `<select>` for dropdowns, `<fieldset>` for grouping
- `<button type="submit">` is the preferred way to create a submit button
- Use `placeholder`, `required`, `disabled`, and other attributes to control behaviour
