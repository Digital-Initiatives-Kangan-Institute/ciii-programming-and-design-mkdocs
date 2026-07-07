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
    ```javascript
    console.log(`Hello, ${name}! You are ${age} years old.`);
    console.log(name.toUpperCase());
    console.log(name.length);
    console.log(city[0]);
    ```

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

    if (score >= 90) {
        console.log("A");
    } else if (score >= 80) {
        console.log("B");
    } else if (score >= 70) {
        console.log("C");
    } else if (score >= 60) {
        console.log("D");
    } else {
        console.log("F");
    }
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
    ```javascript
    let age = 20;
    let isVerified = true;

    if (age < 18) {
        console.log("Access denied — must be 18 or older.");
    } else if (!isVerified) {
        console.log("Access denied — account not verified.");
    } else {
        console.log("Access granted.");
    }
    ```

---

## Task 5: Loops — Multiplication Table

!!! abstract "Instructions"
    Use a `for` loop to print the multiplication table for the number 7 (from 1 × 7 to 12 × 7).

    Example output:
    ```
    1 × 7 = 7
    2 × 7 = 14
    3 × 7 = 21
    ...
    ```

??? hint "Hint - Click to expand"
    ```javascript
    let number = 7;
    for (let i = 1; i <= 12; i++) {
        console.log(`${i} × ${number} = ${i * number}`);
    }
    ```

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
    ```javascript
    let numbers = [23, 5, 88, 12, 47, 3, 64, 19];

    // Print each number
    for (let num of numbers) {
        console.log(num);
    }

    // Only numbers > 20
    console.log("Numbers > 20:");
    for (let num of numbers) {
        if (num > 20) {
            console.log(num);
        }
    }

    // Sum
    let sum = 0;
    for (let num of numbers) {
        sum += num;
    }
    console.log("Sum:", sum);

    // Largest
    let largest = numbers[0];
    for (let num of numbers) {
        if (num > largest) {
            largest = num;
        }
    }
    console.log("Largest:", largest);
    ```

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
    ```javascript
    let arr = [4, 15, 8, 22, 7, 31, 12];

    arr.push(55);
    console.log("After push:", arr);

    arr.pop();
    console.log("After pop:", arr);

    arr.unshift(1);
    console.log("After unshift:", arr);

    console.log("Includes 15?", arr.includes(15));
    console.log("Index of 22:", arr.indexOf(22));
    ```

---

## Requirements

- Use `const` and `let` (no `var`)
- Use template literals for string interpolation
- Use at least one `if/else if/else` chain
- Use at least one `for` or `for...of` loop
- Use at least 3 array methods (`push`, `pop`, `includes`, `indexOf`, etc.)
- Print all results with `console.log()`
