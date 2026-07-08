# useEffect and Automatic Fetch

## Load Data Automatically on Page Load

!!! abstract "Instructions"
    Build a component that loads API data automatically when the page opens, using `useEffect`.

    Your component must:

    - Fetch data automatically using `useEffect` with a dependency array
    - NOT run the fetch in an infinite loop
    - Display the fetched data on the page
    - Include a written explanation: when is button fetch more useful, and when is page-load fetch more useful?

    Push your work to GitHub.

??? code "click to expand"

    ```tsx
    "use client";

    import { useState, useEffect } from "react";

    export default function AutoLoader() {
        const [data, setData] = useState(null);
        const [loading, setLoading] = useState(true);

        useEffect(() => {
            // TODO: Fetch data inside useEffect
            // TODO: Use the correct dependency array
        }, []);   // Why is this array important?

        if (loading) return <p>Loading...</p>;

        return (
            <div>
                {/* TODO: Display the loaded data */}
            </div>
        );
    }
    ```

??? tip "Hint - Click to expand"
    The empty dependency array `[]` means the effect runs once when the component first mounts. Without it, the effect would run after every render, causing an infinite loop (fetch updates state, which triggers re-render, which triggers fetch again). Page-load fetch is ideal for data every user needs (like a product listing). Button fetch is better for on-demand data (like search results).
