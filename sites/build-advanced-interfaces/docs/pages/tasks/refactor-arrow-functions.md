# Refactor with Arrow Functions

## Improve a Component with Arrow Functions

!!! abstract "Instructions"
    Take an existing component and refactor it to use arrow functions clearly and correctly.

    Your refactored component should:

    - Use arrow function syntax for event handlers and callbacks
    - Be cleaner and easier to read than the original
    - Still work exactly the same as before

    Document three improvements you made. Push your work to GitHub.

??? code "click to expand"

    ```tsx
    // Before refactoring (example)
    function handleClick() {
        console.log("Clicked");
    }

    <button onClick={function () { handleDelete(item.id); }}>Delete</button>
    ```

??? hint "Hint - Click to expand"
    Arrow functions use the `() => { }` syntax and can be assigned to a `const`. For single-line functions, the curly braces and `return` keyword can be omitted. Look at your event handlers and callbacks — which ones can be shortened? Think about consistency: if some functions use the `function` keyword and others use arrows, pick one style.
