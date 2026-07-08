# Cafe Site Enhancements

## Your First JavaScript Interaction

!!! abstract "Instructions"
    Add a working JavaScript interaction to your cafe website. Your interaction must include:

    - An **event** (such as a button click)
    - A **function** that responds to the event
    - At least one **variable**

    Be prepared to explain how the event, function, and variable work together.

??? code "click to expand"

    ```html
    <!-- Add inside your existing cafe page, before </body> -->
    <script src="script.js"></script>
    ```

??? hint "Hint - Click to expand"
    There are three things happening in any interactive feature: find the element you want to change, write a function that decides what to change, and tell the browser when to run it. For example, you could create a button that changes the text of a heading when clicked.

---

## Make the Review Form Functional

!!! abstract "Instructions"
    Now that you have a review form on your Reviews page, use JavaScript to make it work.

    When the form is submitted, your JavaScript must:

    - Stop the page from reloading
    - Read the values from each input
    - Display the review in the section below the form
    - Clear the form so the next review can be entered

    Your JavaScript must use an event, a function, and at least one variable.

    Push your updated site to GitHub.

??? hint "Hint - Click to expand"
    You need to listen for the form submission and prevent the browser's default behaviour. Read the input values, then build the review content and add it to the container below the form. Consider what happens after you display the review — how do you reset the form for the next one?
