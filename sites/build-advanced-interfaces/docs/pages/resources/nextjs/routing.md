# Routing

Next.js uses a **file-system based router**. This means files and folders you create inside the `pages/` (or `app/`) directory automatically become URL routes. No configuration is needed.

---

## How It Works

```
pages/
├── index.tsx       →  /
├── about.tsx       →  /about
├── contact.tsx     →  /contact
└── blog/
    └── index.tsx   →  /blog
```

Each file exports a default React component. When a user visits that route, the exported component renders.

---

## Static Routes

A static route is a fixed URL path that always shows the same content.

```typescript
// pages/about.tsx
export default function About() {
    return (
        <main>
            <h1>About Us</h1>
            <p>We build great software.</p>
        </main>
    );
}
```

Visiting `/about` renders this component. No routing code needed — the file name determines the URL.

### Index Routes

Files named `index.tsx` serve as the default page for their folder:

- `pages/index.tsx` → `/`
- `pages/blog/index.tsx` → `/blog`

---

## Dynamic Routes

Dynamic routes let you match variable segments in the URL. Use square brackets `[param]` to define a dynamic segment.

```
pages/
└── products/
    ├── index.tsx       →  /products
    └── [id].tsx        →  /products/1, /products/2, /products/42
```

Any value in place of `[id]` matches this route.

### Accessing the Dynamic Parameter

Use the `useRouter` hook to read the parameter value:

```typescript
// pages/products/[id].tsx
import { useRouter } from "next/router";

export default function Product() {
    const router = useRouter();
    const { id } = router.query;

    return (
        <main>
            <h1>Product {id}</h1>
            <p>Displaying details for product {id}.</p>
        </main>
    );
}
```

- `router.query` is an object containing all dynamic parameters
- The parameter name matches the filename (`[id]` → `router.query.id`)

### Multiple Dynamic Segments

You can combine multiple dynamic parameters:

```
pages/
└── blog/
    └── [category]/
        └── [slug].tsx   →  /blog/tech/my-post, /blog/sports/game-review
```

```typescript
// pages/blog/[category]/[slug].tsx
import { useRouter } from "next/router";

export default function BlogPost() {
    const router = useRouter();
    const { category, slug } = router.query;

    return (
        <main>
            <h1>{slug}</h1>
            <p>Category: {category}</p>
        </main>
    );
}
```

---

## Catch-All Routes

Use three dots `[...param]` to match multiple path segments:

```
pages/
└── docs/
    └── [...slug].tsx   →  /docs, /docs/getting-started, /docs/api/auth
```

```typescript
// pages/docs/[...slug].tsx
import { useRouter } from "next/router";

export default function Docs() {
    const router = useRouter();
    const { slug } = router.query;

    // slug is an array: ["getting", "started"] for /docs/getting-started
    return (
        <main>
            <h1>Documentation</h1>
            <p>Path: {Array.isArray(slug) ? slug.join(" / ") : slug}</p>
        </main>
    );
}
```

---

## Linking Between Pages

Use the `Link` component for client-side navigation between routes.

```typescript
import Link from "next/link";

export default function Home() {
    return (
        <nav>
            <Link href="/">Home</Link>
            <Link href="/about">About</Link>
            <Link href="/products/42">Product 42</Link>
        </nav>
    );
}
```

`Link` prefetches pages in the background, making navigation feel instant.

### Programmatic Navigation

Use `router.push()` to navigate in response to an event:

```typescript
import { useRouter } from "next/router";

export default function Login() {
    const router = useRouter();

    function handleLogin() {
        // Perform login logic, then redirect:
        router.push("/dashboard");
    }

    return <button onClick={handleLogin}>Log In</button>;
}
```

---

## The App Router (Next.js 13+)

Newer Next.js versions use the `app/` directory. The router works the same way, but folders replace files:

```
app/
├── page.tsx          →  /
├── about/
│   └── page.tsx      →  /about
└── products/
    ├── page.tsx      →  /products
    └── [id]/
        └── page.tsx  →  /products/1, etc.
```

Special files in the App Router:

| File | Purpose |
|---|---|
| `page.tsx` | The route's UI component |
| `layout.tsx` | Shared layout wrapping child pages |
| `loading.tsx` | Shown while the page loads |

---

## Summary

- Next.js routes are determined by your **file structure** — no router configuration needed
- **Static routes** use fixed filenames like `about.tsx`
- **Dynamic routes** use `[param].tsx` for variable URL segments
- **Catch-all routes** (`[...param].tsx`) match any number of segments
- Use `<Link>` for navigation, `router.push()` for programmatic redirects
