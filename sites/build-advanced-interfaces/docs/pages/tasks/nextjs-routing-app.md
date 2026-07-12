# Next.js App with Routing

## Build a Multi-Page Next.js App

!!! abstract "Instructions"
    Create a new Next.js application with TypeScript that includes:

    - Two **static routes** (e.g. Home and About)
    - One **dynamic route** (e.g. a product detail page that reads an ID from the URL)
    - A **shared layout** with navigation that appears on every page

    This could be a mini portfolio, a product catalogue, or any small multi-page project.

    Push your work to GitHub.

??? code "click to expand"

    ```bash
    npx create-next-app@latest my-routing-app
    ```

    ```tsx
    // app/layout.tsx — shared layout for all pages
    export default function RootLayout({ children }: { children: React.ReactNode }) {
        return (
            <html lang="en">
                <body>
                    {/* TODO: Add navigation that appears on all pages */}
                    <main>{children}</main>
                </body>
            </html>
        );
    }
    ```

    ```tsx
    // app/products/[id]/page.tsx — dynamic route
    export default function ProductPage({ params }: { params: { id: string } }) {
        // TODO: Display product info based on params.id
    }
    ```

??? hint "Hint - Click to expand"
    Static routes are folders with `page.tsx` inside (e.g. `app/about/page.tsx`). Dynamic routes use square brackets (e.g. `app/products/[id]/page.tsx`). Place your navigation inside the `layout.tsx` file so it appears on every page. Use `<Link href="...">` from `next/link` for navigation between pages.
