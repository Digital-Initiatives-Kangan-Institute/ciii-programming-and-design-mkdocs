# Fetching Data with State

## Button Fetch with useState

!!! abstract "Instructions"
    Build a Next.js component with a button that fetches data from an API and updates the page.

    Your component must:

    - Have a button that triggers a fetch when clicked
    - Use `useState` to store the fetched data
    - Display the fetched data on the page
    - Connect to an endpoint you have not used before (e.g. `dummyjson.com/users`, `dummyjson.com/posts`, `dummyjson.com/quotes`)

??? code "click to expand"

    ```tsx
    "use client";

    import { useState } from "react";

    export default function ApiFetcher() {
        // TODO: Set up state for the fetched data
        // TODO: Write a function that fetches from an endpoint
        // TODO: Display the results

        return (
            <div>
                {/* TODO: Button and output area */}
            </div>
        );
    }
    ```

??? hint "Hint - Click to expand"
    Your state starts empty and gets updated after the fetch completes. The fetch function needs to be async. Think about where in your JSX the data should appear — the content below the button changes each time the user clicks.

---

## Handling Loading and Error States

!!! abstract "Instructions"
    Improve your fetch component so it handles all three states: **loading**, **success**, and **error**.

    Your updated component must:

    - Show a loading message while the fetch is in progress
    - Display data on success
    - Show an error message if the fetch fails
    - Clear previous results or errors when the user clicks the button again

    Include evidence of all three states working. Push your work to GitHub.

??? hint "Hint - Click to expand"
    You will need additional state for tracking loading and error. Before starting a new fetch, reset the previous data and errors. Both the success path and failure path should set loading back to false. Remember that a failed HTTP status does not throw an error on its own.
