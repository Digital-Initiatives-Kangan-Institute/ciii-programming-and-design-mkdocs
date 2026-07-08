# Interactive Component

## Build a Component That Responds to User Input

!!! abstract "Instructions"
    Build a Next.js component where the screen changes when the user interacts with it.

    Your component should include:

    - At least one **event handler** (`onClick`, `onChange`, etc.)
    - At least one **state variable** using `useState`
    - A visible change on the screen when the user interacts

    Add comments explaining how the state and events work. Then add a **second** interactive feature to the same component or app.

    Push your work to GitHub.

??? code "click to expand"

    ```tsx
    "use client";

    import { useState } from "react";

    export default function InteractiveFeature() {
        // TODO: Add state variable(s)

        // TODO: Add event handler function(s)

        return (
            <div>
                {/* TODO: Build interactive UI that changes on user action */}
            </div>
        );
    }
    ```

??? hint "Hint - Click to expand"
    Simple ideas: a counter that increases when a button is clicked, a toggle that shows/hides content, a text input that updates a heading as you type, or a list where you can add and remove items. Use `useState` to track the value and update it inside an event handler. Don't forget `"use client"` at the top.
