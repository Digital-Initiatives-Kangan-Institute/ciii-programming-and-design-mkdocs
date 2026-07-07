# Data and Decisions

Practice JavaScript variables, data types, conditionals, and loops by solving a series of coding exercises.

---

## Setup

!!! abstract "Instructions"
    Create a file called `practice.js` and link it to an HTML file. Open the browser console (`F12` → Console) to see your output.

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>JS Practice</title>
    </head>
    <body>
        <h1>Check the Console</h1>
        <script src="practice.js"></script>
    </body>
    </html>
    ```

    Use `console.log()` to display your answers.

---

## Task 1: Variables

!!! abstract "Instructions"
    Create variables to store the following information about yourself. Use `const` where the value will never change and `let` where it might.

    - Your full name
    - Your age
    - Whether you are a student (true/false)
    - Your city
    - Your favourite programming languages (as an array)
    - Your contact details (as an object with email and phone)

    Print each variable to the console.

??? code "Starter"
    ```javascript
    const name = "Alice";
    let age = 25;
    const isStudent = true;
    let city = "Melbourne";
    const favouriteLanguages = ["JavaScript", "Python", "HTML"];
    const contact = {
        email: "alice@example.com",
        phone: "0400 000 000"
    };

    console.log("Name:", name);
    console.log("Age:", age);
    console.log("Student:", isStudent);
    console.log("City:", city);
    console.log("Languages:", favouriteLanguages);
    console.log("Contact:", contact);
    ```

---

## Task 2: String Operations

!!! abstract "Instructions"
    Using string operations, generate the following outputs:

    1. A greeting that says "Hello, [your name]! You are [age] years old." using a template literal
    2. Your name in uppercase
    3. The number of characters in your full name
    4. The first character of your city

??? hint "Hint - Click to expand"
    - Template literals use backticks and `${}` to embed variables: `` `Hello, ${name}!` ``
    - To convert a string to uppercase, use the `.toUpperCase()` method.
    - The `.length` property gives you the number of characters in a string.
    - You can access individual characters using bracket notation: `string[index]` — remember that indexing starts at 0.

---

## Task 3: Conditionals — Grade Calculator

!!! abstract "Instructions"
    Write code that takes a numeric score (0-100) and logs the corresponding grade:

    - 90-100: "A"
    - 80-89: "B"
    - 70-79: "C"
    - 60-69: "D"
    - Below 60: "F"

    Test your code with at least 5 different scores: 95, 82, 74, 61, 45.

??? code "Starter"
    ```javascript
    let score = 85;

    // Write an if/else if/else chain to check the score:
    // 90-100 → "A"
    // 80-89  → "B"
    // 70-79  → "C"
    // 60-69  → "D"
    // Below 60 → "F"

    // Test with scores: 95, 82, 74, 61, 45
    ```

??? question "Hint"
    Change the value of `score` and re-run to test each grade. Or wrap it in a function and call it with different arguments.

---

## Task 4: Conditionals — Access Check

!!! abstract "Instructions"
    Write code that checks whether a user can access a website. The conditions are:

    - Must be at least 18 years old
    - Must have their account verified (`isVerified = true`)
    - If both pass, log "Access granted". Otherwise, log "Access denied" with the specific reason.

    Test with different values for age and isVerified.

??? hint "Hint - Click to expand"
    - Use an `if` statement to check the first condition (age < 18). If true, log an "Access denied" message that mentions the age requirement.
    - Use `else if` to check the second condition (isVerified is false). Remember the `!` (NOT) operator to check if something is false.
    - Use `else` for the case where both conditions pass — log "Access granted".
    - Test with different values: try age = 16, try isVerified = false, try both valid.

---

## Task 5: Loops — Multiplication Table

!!! abstract "Instructions"
    Use a `for` loop to print the multiplication table for the number 7 (from 1 x 7 to 12 x 7).

    Example output:
    ```
    1 x 7 = 7
    2 x 7 = 14
    3 x 7 = 21
    ...
    ```

??? hint "Hint - Click to expand"
    - Set up a variable for the number (e.g., `let number = 7`).
    - Use a `for` loop with `let i = 1; i <= 12; i++`.
    - Inside the loop, use a template literal to format the output: `` `${i} x ${number} = ${i * number}` ``
    - Print each line with `console.log()`.

---

## Task 6: Loops — Array Processing

!!! abstract "Instructions"
    You have an array of numbers: `[23, 5, 88, 12, 47, 3, 64, 19]`. Write code to:

    1. Print each number
    2. Print only the numbers greater than 20
    3. Calculate and print the sum of all numbers
    4. Find and print the largest number

    Use a `for` loop or `for...of` loop.

??? hint "Hint - Click to expand"
    - **Print each number:** Use a `for...of` loop (`for (let num of numbers)`) and log each one.
    - **Numbers greater than 20:** Inside your loop, add an `if` statement that checks `num > 20` before logging.
    - **Sum:** Create a variable `sum` starting at 0. Inside the loop, add each number to it with `sum += num`. Log the sum after the loop.
    - **Largest number:** Start with `let largest = numbers[0]`. Inside the loop, compare each number to `largest` — if it's bigger, update `largest`. Log the result after the loop.

---

## Task 7: Array Methods Challenge

!!! abstract "Instructions"
    Use array methods to solve these problems with `[4, 15, 8, 22, 7, 31, 12]`:

    1. Add `55` to the end of the array
    2. Remove the last item
    3. Add `1` to the start of the array
    4. Check if the array includes the number `15`
    5. Find the index of `22`

??? hint "Hint - Click to expand"
    - To add to the end of an array, use `.push(item)`.
    - To remove the last item, use `.pop()`. You don't need to pass anything.
    - To add to the start, use `.unshift(item)`.
    - To check if an array contains a value, use `.includes(value)` — it returns `true` or `false`.
    - To find the position of a value, use `.indexOf(value)`. It returns the index (starting at 0), or -1 if not found.

    Log the array after each step so you can see the changes.

---

## Requirements

- Use `const` and `let` (no `var`)
- Use template literals for string interpolation
- Use at least one `if/else if/else` chain
- Use at least one `for` or `for...of` loop
- Use at least 3 array methods (`push`, `pop`, `includes`, `indexOf`, etc.)
- Print all results with `console.log()`
