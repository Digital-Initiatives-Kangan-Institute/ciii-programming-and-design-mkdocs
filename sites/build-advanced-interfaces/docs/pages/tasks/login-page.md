# Build and Improve a Login Page

## Create a Login Page for the Cafe Owner

!!! abstract "Instructions"
    The cafe owner needs a login page to access the menu management area. This is a **simulated scenario** — there is no real backend, so you are building the front-end page with client-side validation only.

    Your login page must include:

    - A heading that makes it clear this is for cafe staff (e.g. "Cafe Owner Login")
    - Inputs for **email** and **password**, each with a `<label>`
    - A styled submit button
    - A link back to the cafe home page
    - Consistent styling with your existing cafe site

    Create a new HTML page and link it from your existing cafe site navigation.

    Push your work to GitHub. See the [Version Control](/version-control) site if you need help with staging, committing, and pushing.

??? hint "Hint - Click to expand"
    Create a new file like `login.html`. Use `<input type="email">` for the email field and `<input type="password">` for the password field. Every input must have a matching `<label>`. Reuse your existing CSS file or link a new one that matches the cafe's colours and fonts. Add a navigation link to the login page from your other cafe pages.

---

## Add Input Validation

!!! abstract "Instructions"
    Now add JavaScript validation that checks the form before it would be submitted. The form does **not** need to connect to any backend — validation happens entirely in the browser.

    Your validation must check that:

    - The email field is not empty
    - The password field is not empty
    - The password is at least **8 characters** long

    Validation errors must:

    - Appear as text messages **on the page** (not browser alerts)
    - Be shown near the relevant input field
    - Prevent the form from submitting until all fields are valid

    Push your work to GitHub.

??? hint "Hint - Click to expand"
    Add an event listener on the form's `submit` event and call `event.preventDefault()` to stop the default submission. Check `input.value.trim()` for each field — whitespace should not count as valid input. Create a `<span>` or `<p>` element below each input to display error messages. Think about when to clear errors (on the next attempt? when the user starts typing?). The validation runs in the browser only — no server is involved.
