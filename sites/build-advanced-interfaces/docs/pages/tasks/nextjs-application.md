# NextJS Application

Build a multi-page Next.js application with components, routing, and state management.

---

## Task 1: Create a Next.js Project

!!! abstract "Instructions"
    Create a new Next.js project using the following command. Choose TypeScript, ESLint, and the App Router when prompted.

    ```bash
    npx create-next-app@latest my-first-app
    cd my-first-app
    npm run dev
    ```

    Open `http://localhost:3000` in your browser. You should see the default Next.js welcome page.

---

## Task 2: Create Static Pages

!!! abstract "Instructions"
    Create three static pages in the `app/` directory:

    - `/` — Home page with a welcome message
    - `/about` — About page with information about yourself
    - `/contact` — Contact page with your email and a brief message

    Add a navigation bar component that appears on all pages and links to each route.

??? code "Navigation Component"
    ```typescript
    // components/Navbar.tsx
    import Link from "next/link";

    export default function Navbar() {
        return (
            <nav style={{ padding: "1rem", borderBottom: "1px solid #ccc" }}>
                <Link href="/" style={{ marginRight: "1rem" }}>Home</Link>
                <Link href="/about" style={{ marginRight: "1rem" }}>About</Link>
                <Link href="/contact">Contact</Link>
            </nav>
        );
    }
    ```

??? hint "Hint - Using the Navbar in Layout"
    Import and place the Navbar component in `app/layout.tsx` inside the `<body>` before `{children}`.

---

## Task 3: Dynamic Route

!!! abstract "Instructions"
    Create a blog section with dynamic routing. Each blog post should have its own URL based on a slug.

    - `/blog` — List all blog posts with links
    - `/blog/[slug]` — Display a single blog post

    Create an array of blog posts with `title`, `slug`, and `content`. When a user clicks a post, show the full content on the detail page.

??? code "Blog Data"
    ```typescript
    // data/posts.ts
    export interface Post {
        slug: string;
        title: string;
        content: string;
    }

    export const posts: Post[] = [
        {
            slug: "getting-started",
            title: "Getting Started with Next.js",
            content: "Next.js is a React framework that provides routing, rendering, and more out of the box."
        },
        {
            slug: "why-typescript",
            title: "Why Use TypeScript?",
            content: "TypeScript adds static type checking to JavaScript, catching errors before runtime."
        },
        {
            slug: "components",
            title: "Understanding Components",
            content: "Components are reusable pieces of UI that can be composed to build complex interfaces."
        }
    ];
    ```

??? hint "Hint - Dynamic Route Handler"
    - Create the file `app/blog/[slug]/page.tsx`. The `[slug]` folder name tells Next.js this is a dynamic route.
    - Import your posts data from the data file and `notFound` from `next/navigation`.
    - The page component receives `params` as a prop. Use `params.slug` to find the matching post in your array.
    - If no post matches, call `notFound()` to show the default 404 page.
    - Otherwise, render the post's `title` and `content` in your JSX.

---

## Task 4: Interactive Counter with useState

!!! abstract "Instructions"
    Add a counter component to the home page. It should:

    - Display the current count
    - Have an Increment button (+1)
    - Have a Decrement button (-1)
    - Have a Reset button (back to 0)
    - Show a message when the count reaches 10: "You reached 10!"

    Use the `useState` hook.

??? code "click to expand"
    ```typescript
    "use client";

    import { useState } from "react";

    export default function Counter() {
        const [count, setCount] = useState(0);

        return (
            <div style={{ marginTop: "2rem", textAlign: "center" }}>
                <h2>Counter: {count}</h2>
                {/* TODO: Add an Increment button that calls setCount(count + 1) */}
                {/* TODO: Add a Decrement button that calls setCount(count - 1) */}
                {/* TODO: Add a Reset button that calls setCount(0) */}
                {/* TODO: Show a message when count >= 10 */}
            </div>
        );
    }
    ```

---

## Task 5: Fetch Data from an API

!!! abstract "Instructions"
    Create a `/users` page that fetches and displays a list of users from an API. Use `fetch` inside a server component (no `"use client"` needed for server-side data fetching).

    Use this API: `https://jsonplaceholder.typicode.com/users`

??? code "click to expand"
    ```typescript
    // app/users/page.tsx
    interface User {
        id: number;
        name: string;
        email: string;
        company: {
            name: string;
        };
    }

    async function getUsers(): Promise<User[]> {
        // TODO: Fetch from https://jsonplaceholder.typicode.com/users
        // Check if the response is ok; throw an Error if not
        // Return the parsed JSON
    }

    export default async function UsersPage() {
        const users = await getUsers();

        return (
            <main>
                <h1>Users</h1>
                {/* TODO: Map over users and display name, email, and company */}
            </main>
        );
    }
    ```

??? hint "Hint - Loading State"
    Next.js automatically shows a loading UI if you create a `loading.tsx` file in the same directory as your page.
    
    Create `app/users/loading.tsx` and export a default component that returns a simple loading message (e.g., a `<p>` tag with text like "Loading users..."). Next.js will display this component while the data is being fetched, without any additional configuration.

---

## Requirements

- Next.js project created and running locally
- Three static pages (Home, About, Contact) with shared navigation
- Dynamic blog route (`/blog/[slug]`) working
- Counter component using `useState`
- Users page fetching data from an API
- Clean, organised component structure
