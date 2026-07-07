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
    In `app/blog/[slug]/page.tsx`:

    ```typescript
    import { posts } from "@/data/posts";
    import { notFound } from "next/navigation";

    export default function BlogPost({ params }: { params: { slug: string } }) {
        const post = posts.find(p => p.slug === params.slug);
        if (!post) return notFound();

        return (
            <main>
                <h1>{post.title}</h1>
                <p>{post.content}</p>
            </main>
        );
    }
    ```

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
                <button onClick={() => setCount(count + 1)}>Increment</button>
                <button onClick={() => setCount(count - 1)}>Decrement</button>
                <button onClick={() => setCount(0)}>Reset</button>
                {count >= 10 && <p>You reached 10!</p>}
            </div>
        );
    }
    ```

    Remember to add `"use client"` at the top since `useState` requires client-side rendering.

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
        const res = await fetch("https://jsonplaceholder.typicode.com/users");
        if (!res.ok) throw new Error("Failed to fetch users");
        return res.json();
    }

    export default async function UsersPage() {
        const users = await getUsers();

        return (
            <main>
                <h1>Users</h1>
                <ul>
                    {users.map(user => (
                        <li key={user.id}>
                            <strong>{user.name}</strong> — {user.email}
                            <br />
                            <small>Company: {user.company.name}</small>
                        </li>
                    ))}
                </ul>
            </main>
        );
    }
    ```

??? hint "Hint - Loading State"
    Create `app/users/loading.tsx` to show a loading indicator while the data is being fetched:

    ```typescript
    export default function Loading() {
        return <p>Loading users...</p>;
    }
    ```

---

## Requirements Checklist

- Next.js project created and running locally
- Three static pages (Home, About, Contact) with shared navigation
- Dynamic blog route (`/blog/[slug]`) working
- Counter component using `useState`
- Users page fetching data from an API
- Clean, organised component structure
