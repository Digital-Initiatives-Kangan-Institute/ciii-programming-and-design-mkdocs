# Supabase as a CMS

## Design a Content Model

!!! abstract "Instructions"
    Draft a content model for a web application that will use Supabase as a content management system.

    Your content model must include:

    - At least **two tables** (e.g. products and categories, or posts and authors)
    - At least **four fields** per table
    - Sample records showing what real data would look like

    This is a planning exercise — focus on the structure of your data before building.

??? hint "Hint - Click to expand"
    Plan your tables on paper or in a document first. For each table, list: table name, field names, data types (text, number, boolean), and a few sample rows. For example, a `products` table might have: id, title, price, description, and image_url. A `categories` table might have: id and name. Think about how the tables relate — does a product belong to a category?

---

## Display CMS Content

!!! abstract "Instructions"
    Using your content model from the previous exercise, display CMS-style content in your app. If Supabase access is available, connect it. Otherwise, mock the data.

    Your work must include:

    - Content displayed in your front end (from Supabase or a mock)
    - A description or diagram of how content would be created and updated
    - Notes explaining how the front end uses the data

    Push your work and planning notes to GitHub.

??? code "click to expand"

    ```tsx
    "use client";

    import { useState, useEffect } from "react";

    export default function CmsDisplay() {
        const [content, setContent] = useState([]);

        useEffect(() => {
            // TODO: Fetch content from Supabase or a mock source
            // TODO: Store in state
        }, []);

        return (
            <div>
                <h1>CMS Content</h1>
                {/* TODO: Display content as cards, articles, or list */}
                {/* TODO: Outline create/update workflow in comments or a note */}
            </div>
        );
    }
    ```

??? hint "Hint - Click to expand"
    For the create/update workflow, describe how new content gets into the system: either through the Supabase dashboard (a person edits data directly) or through forms in your app (a user submits a form that inserts/updates records). If mocking, create a JavaScript array matching your content model structure and display it as if it came from a database.
