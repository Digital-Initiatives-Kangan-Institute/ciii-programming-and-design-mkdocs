# Build a Calculator

Practice writing functions by building a simple calculator that can add, subtract, multiply, divide, and calculate percentages.

---

## Setup

!!! abstract "Instructions"
    Create `calculator.html` and `calculator.js`. Link the JS file and open the page. Use the browser console to test your functions.

---

## Task 1: Basic Arithmetic Functions

!!! abstract "Instructions"
    Create four functions: `add`, `subtract`, `multiply`, and `divide`. Each should take two numbers as parameters and return the result.

    Add error handling: `divide` should return `"Error: Cannot divide by zero"` if the second parameter is `0`.

    Test each function with `console.log()`:

    ```javascript
    console.log(add(10, 5));       // 15
    console.log(subtract(10, 5));  // 5
    console.log(multiply(10, 5));  // 50
    console.log(divide(10, 5));    // 2
    console.log(divide(10, 0));    // "Error: Cannot divide by zero"
    ```

??? code "Starter"
    ```javascript
    function add(a, b) {
        // Return the sum of a and b
    }

    function subtract(a, b) {
        // Return the difference of a and b
    }

    function multiply(a, b) {
        // Return the product of a and b
    }

    function divide(a, b) {
        // Return a / b
        // If b is 0, return the error string "Error: Cannot divide by zero"
    }
    ```

---

## Task 2: More Functions

!!! abstract "Instructions"
    Create three more functions:

    1. `percentage(value, percent)` — returns what `percent`% of `value` is. Example: `percentage(200, 15)` returns `30`.
    2. `square(n)` — returns `n` squared.
    3. `isEven(n)` — returns `true` if `n` is even, `false` otherwise.

??? hint "Hint - Click to expand"
    - **percentage(value, percent):** To find x% of a value, multiply the value by `(percent / 100)`. Return the result.
    - **square(n):** Multiply n by itself and return it.
    - **isEven(n):** A number is even if it's divisible by 2 with no remainder. Use the modulo operator `%` — `n % 2 === 0` returns `true` for even numbers. Return the result of that comparison.

---

## Task 3: A Function That Calls Other Functions

!!! abstract "Instructions"
    Create a function called `operate(a, b, operation)` that takes two numbers and an operation string (`"add"`, `"subtract"`, `"multiply"`, `"divide"`). It should call the appropriate function and return the result.

    Example:
    ```javascript
    operate(10, 5, "add");       // 15
    operate(10, 5, "multiply");  // 50
    ```

??? hint "Hint - Click to expand"
    - Your `operate` function should take three parameters: `a`, `b`, and `operation`.
    - Use `if`/`else if` to check the value of `operation` against the strings `"add"`, `"subtract"`, `"multiply"`, and `"divide"`.
    - For each match, call the corresponding function (e.g., `add(a, b)`) and return the result.
    - Add an `else` at the end to return a fallback message like `"Unknown operation"`.

---

## Task 4: Process an Array of Calculations

!!! abstract "Instructions"
    Create a function `processCalculations` that takes an array of calculation objects and returns an array of results.

    Each object has the shape: `{ a: number, b: number, operation: string }`

    ```javascript
    let calculations = [
        { a: 10, b: 5, operation: "add" },
        { a: 20, b: 4, operation: "subtract" },
        { a: 7, b: 6, operation: "multiply" },
        { a: 100, b: 5, operation: "divide" }
    ];

    console.log(processCalculations(calculations));
    // Should output: [15, 16, 42, 20]
    ```

??? hint "Hint - Click to expand"
    - Create an empty array to hold results (e.g., `let results = []`).
    - Loop through the input array using `for...of`.
    - For each calculation object, call `operate(calc.a, calc.b, calc.operation)`.
    - Push the result into your results array with `.push()`.
    - Return the results array after the loop.

---

## Task 5: Connect to a Simple UI

!!! abstract "Instructions"
    Add HTML inputs and buttons to your page so users can perform calculations without the console.

    Create:
    - Two number inputs
    - A dropdown or set of buttons for the operation
    - A "Calculate" button
    - A display area for the result

??? code "HTML Structure"
    ```html
    <div style="max-width: 400px; margin: 2rem auto; font-family: Arial;">
        <h1>Calculator</h1>

        <div>
            <input type="number" id="num1" placeholder="First number">
        </div>

        <div style="margin: 1rem 0;">
            <select id="operation">
                <option value="add">+ Add</option>
                <option value="subtract">- Subtract</option>
                <option value="multiply">x Multiply</option>
                <option value="divide">/ Divide</option>
            </select>
        </div>

        <div>
            <input type="number" id="num2" placeholder="Second number">
        </div>

        <div style="margin: 1rem 0;">
            <button id="calculateBtn">Calculate</button>
        </div>

        <h2>Result: <span id="result">-</span></h2>
    </div>

    <script src="calculator.js"></script>
    ```

??? hint "Hint - JavaScript"
    - Add a `click` event listener to the button with id `calculateBtn`.
    - Use `document.getElementById()` to get the values from `num1`, `num2`, and `operation`. Remember that input values are strings — use `Number()` to convert the number inputs.
    - Call your `operate()` function with the three values.
    - Set the `textContent` of the element with id `result` to the returned value.

---

## Requirements

- At least 7 functions with clear names
- Each function does one thing
- `divide` handles division by zero
- `operate` calls other functions based on the operation string
- `processCalculations` iterates over an array and calls `operate` for each item
- The UI connects inputs to your functions
