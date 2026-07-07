# Layouts

Layouts let you wrap pages with shared UI elements like headers, footers, and navigation bars. Instead of repeating the same code on every page, you define it once in a layout.

---

## Why Use Layouts?

Without layouts, each page would need to include the full HTML structure:

```typescript
// Every page would repeat this:
export default function Page() {
    return (
        <div>
            <nav>Home | About | Contact</nav>
            <main>
                <h1>Page Content</h1>
            </main>
            <footer>Copyright 2026</footer>
        </div>
    );
}
```

With a layout, shared elements are defined once and every page automatically gets them.

---

## Pages Router Layout

In the pages directory, create a layout component and wrap each page through `_app.tsx`.

### Step 1: Create a Layout Component

```typescript
// components/Layout.tsx
import Link from "next/link";
import { ReactNode } from "react";

interface LayoutProps {
    children: ReactNode;
}

export default function Layout({ children }: LayoutProps) {
    return (
        <div>
            <nav style={{
                padding: "1rem",
                backgroundColor: "#f5f5f5",
                marginBottom: "2rem"
            }}>
                <Link href="/" style={{ marginRight: "1rem" }}>Home</Link>
                <Link href="/about" style={{ marginRight: "1rem" }}>About</Link>
                <Link href="/contact">Contact</Link>
            </nav>

            <main style={{ padding: "0 2rem" }}>
                {children}
            </main>

            <footer style={{
                marginTop: "3rem",
                padding: "1rem",
                textAlign: "center",
                borderTop: "1px solid #eee"
            }}>
                Copyright 2026 — My Site
            </footer>
        </div>
    );
}
```

### Step 2: Wrap All Pages in \_app.tsx

```typescript
// pages/_app.tsx
import type { AppProps } from "next/app";
import Layout from "../components/Layout";

export default function App({ Component, pageProps }: AppProps) {
    return (
        <Layout>
            <Component {...pageProps} />
        </Layout>
    );
}
```

Now every page automatically gets the nav bar and footer. Each page only needs to define its own content:

```typescript
// pages/about.tsx
export default function About() {
    return (
        <>
            <h1>About</h1>
            <p>This content is wrapped by the layout.</p>
        </>
    );
}
```

---

## The App Router (Next.js 13+)

The App Router has built-in layout support via `layout.tsx` files.

```
app/
├── layout.tsx         →  Root layout (applies to all pages)
├── page.tsx           →  /
├── about/
│   └── page.tsx       →  /about
└── dashboard/
    ├── layout.tsx     →  Layout for /dashboard/* pages
    └── page.tsx       →  /dashboard
```

### Root Layout

The root layout wraps the entire application and must include `<html>` and `<body>`:

```typescript
// app/layout.tsx
export default function RootLayout({
    children,
}: {
    children: React.ReactNode;
}) {
    return (
        <html lang="en">
            <body>
                <nav>
                    <a href="/">Home</a>
                    <a href="/about">About</a>
                </nav>
                <main>{children}</main>
                <footer>Copyright 2026</footer>
            </body>
        </html>
    );
}
```

### Nested Layouts

Layouts can be nested. A layout in a sub-folder only applies to pages within that folder:

```typescript
// app/dashboard/layout.tsx
export default function DashboardLayout({
    children,
}: {
    children: React.ReactNode;
}) {
    return (
        <div className="dashboard">
            <aside>Dashboard sidebar</aside>
            <section>{children}</section>
        </div>
    );
}
```

Pages under `/dashboard` get both the root layout AND the dashboard layout.

### How Nesting Works

```
Root Layout
├── Navigation bar
├── Dashboard Layout
│   ├── Sidebar
│   └── {children}    ← Dashboard pages render here
└── Footer
```

---

## Per-Page Layouts (Pages Router)

If you need different layouts for different pages in the Pages Router, assign a layout to the page component:

```typescript
// components/AdminLayout.tsx — with sidebar
// components/MarketingLayout.tsx — with hero banner

// pages/admin.tsx
import AdminLayout from "../components/AdminLayout";

export default function Admin() {
    return <h1>Admin Panel</h1>;
}

Admin.Layout = AdminLayout;
```

Then modify `_app.tsx`:

```typescript
export default function App({ Component, pageProps }: AppProps) {
    const Layout = Component.Layout || DefaultLayout;
    return (
        <Layout>
            <Component {...pageProps} />
        </Layout>
    );
}
```

---

## Summary

- Layouts prevent code duplication by defining shared UI once
- In the **Pages Router**, create a component and wrap pages via `_app.tsx`
- In the **App Router**, use `layout.tsx` files that automatically apply to child routes
- Layouts can be **nested** — a sub-folder layout wraps within its parent layout
- The root layout must contain `<html>` and `<body>` tags
