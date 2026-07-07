# Server-Side Rendering and Frameworks

As applications grow, rendering everything in the browser (client-side) has drawbacks. Server-side rendering and frameworks address these challenges.

---

## Client-Side Rendering (CSR)

With CSR, the browser downloads a minimal HTML shell and JavaScript, which then renders the full page.

```
Browser → Empty HTML shell → Downloads JS bundle → JS renders the page
```

### Advantages

- Smooth page transitions (no full page reload)
- Reduced server load after initial download
- Rich interactivity

### Disadvantages

- **Slow first load** — User sees a blank page while JS downloads and executes
- **Poor SEO** — Search engine crawlers may not execute JavaScript
- **Flash of unstyled content** — Content may appear after a visible delay

---

## Server-Side Rendering (SSR)

With SSR, the server generates the complete HTML for each request. The browser receives a fully rendered page immediately.

```
Browser → Requests page → Server renders HTML → Full page delivered
```

### Advantages

- **Fast first paint** — User sees content immediately
- **SEO-friendly** — Search engines receive complete HTML
- **Works without JavaScript** — Basic content is always visible

### Disadvantages

- **Higher server load** — Every request triggers rendering
- **Slower page transitions** — Full page reloads (unless using a framework that hydrates)
- **More complex deployment** — Requires a Node.js server

---

## Comparison

| Feature | CSR | SSR |
|---|---|---|
| First contentful paint | Slow | Fast |
| Time to interactive | Delayed | Near-immediate |
| SEO | Poor | Excellent |
| Server cost | Low (static files) | Higher (rendering per request) |
| Page transitions | Instant (SPA) | Full reload |
| JavaScript required | Yes | No (for initial HTML) |

---

## Modern Frameworks

Frameworks combine the best of both approaches: SSR for the initial load, then CSR-style navigation for subsequent pages.

### Popular Frameworks

| Framework | Rendering | Key Strength |
|---|---|---|
| **Next.js** | SSR, SSG, ISR | Built on React, file-based routing |
| **Nuxt** | SSR, SSG | Built on Vue, auto-imports |
| **SvelteKit** | SSR, SSG | Compile-time, minimal JS output |
| **Remix** | SSR | Nested routes, web standards focus |
| **Astro** | SSG (default) | Ships zero JS by default |

---

## Why Next.js in This Course

| Feature | Benefit |
|---|---|
| File-based routing | No router config needed |
| SSR out of the box | Each page can choose its rendering strategy |
| API routes | Backend logic in the same project |
| TypeScript support | First-class, auto-configured |
| Large ecosystem | Most React libraries work |
| Great developer experience | Fast refresh, clear errors |

### Rendering Strategies in Next.js

| Strategy | How | Use When |
|---|---|---|
| **SSR** (Server-Side Rendering) | HTML generated per request | Dynamic data that changes often |
| **SSG** (Static Site Generation) | HTML generated at build time | Content that rarely changes (blogs, docs) |
| **ISR** (Incremental Static Regeneration) | Rebuild static pages on demand | Mostly static with occasional updates |
| **CSR** (Client-Side Rendering) | Rendered in browser with `useEffect` | User-specific, behind auth |

```typescript
// SSG — built at deploy time
export default function About() {
    return <h1>About</h1>;
}

// SSR — rendered on each request
export async function getServerSideProps() {
    const data = await fetch("https://api.example.com/latest");
    return { props: { data: await data.json() } };
}

// ISR — revalidates every 60 seconds
export async function getStaticProps() {
    const data = await fetch("https://api.example.com/trending");
    return {
        props: { data: await data.json() },
        revalidate: 60
    };
}
```

---

## When to Use What

- **Landing page, blog, docs** → Static Site Generation (SSG)
- **Dashboard, user profile** → Server-Side Rendering (SSR)
- **Admin panel behind login** → Client-Side Rendering (CSR)
- **Product catalogue** → Incremental Static Regeneration (ISR)

---

## Summary

- **CSR** renders in the browser — good for interactivity, bad for SEO and first load
- **SSR** renders on the server — fast first load, great SEO
- Modern frameworks like **Next.js** give you both — SSR for initial load, CSR for navigation
- Next.js supports **SSR, SSG, ISR, and CSR** — choose per page
- **File-based routing** means no router configuration needed
