# AGENTS.md

`AGENTS.md` is a file you place in the root of your project that gives AI agents standing instructions about your codebase. The agent reads it automatically every time it starts working, so you never have to re-explain your conventions, rules, or project structure.

---

## What is AGENTS.md?

An `AGENTS.md` file is a markdown document that lives at the top level of your project. When an AI agent opens your project, it reads this file first — before you even say anything. This means the agent starts every session already knowing:

- What your project does
- What conventions you follow
- What tools and frameworks you use
- What rules it should obey
- What files it should never touch

Think of it as an onboarding document that every agent gets on day one.

---

## Why Use AGENTS.md?

Without an `AGENTS.md`, every session starts from scratch. You re-explain the project, the patterns, and the boundaries. The agent makes mistakes you have already encountered before.

With an `AGENTS.md`:

- The agent follows your conventions without being told
- It avoids known pitfalls you have documented
- It works consistently across different sessions and different team members
- You spend less time explaining and more time building

The file grows with your project. Whenever the agent does something wrong that you wish it had known not to do, add a line to the file so it does not happen again.

---

## What to Include

A good `AGENTS.md` answers the questions an agent would otherwise have to ask.

### Project Overview

What is this project? What does it do?

```markdown
# AGENTS.md — My Cafe Website

This is a multi-page HTML and CSS cafe website. Students build pages
to demonstrate HTML structure, CSS selectors, and linking.
```

### Tech Stack

```markdown
## Tech Stack

- HTML5, CSS3, vanilla JavaScript
- No frameworks or build tools
- Deployed via Cloudflare Pages
```

### Conventions

What patterns should the agent match?

```markdown
## Conventions

- Use kebab-case for CSS class names
- Indent with 2 spaces
- External CSS only — no inline styles
- Images go in an `images/` folder
```

### Rules and Boundaries

What must the agent never do?

```markdown
## Rules

- Do not modify the footer — it is consistent across all pages
- Never commit changes
- Do not guess or invent URLs
- Always explain what you changed and why
```

### Verification

How should the agent check its work?

```markdown
## Verification

- After making changes, run `npm run build` to check for errors
- Confirm all linked pages are reachable
```

---

## A Complete Example

Here is the `AGENTS.md` from this project:

```markdown
# AGENTS.md — Building MkDocs Sites

This is a collection of MkDocs Material sites deployed to Cloudflare.
Each site lives in `sites/<slug>/`, gets built into `build/<slug>/`,
and the portal at `build/index.html` links them all together.

## Content Conventions

- Sites use MkDocs Material theme with specific palette colours
- Navigation is organised into Resources and Tasks
- Task pages use `!!! abstract "Instructions"` for briefs
- Starter code goes in `??? code "click to expand"` blocks
- Hints go in `??? hint` blocks
- Never use `- [ ]` checklist syntax in markdown

## Rules

- Never commit changes unless explicitly asked
- Do not build MkDocs output into the `build/` directory
- Never generate or guess URLs
- Delete temporary build artifacts after verifying

## Palette Reference

| Colour | Hex | Hover |
|---|---|---|
| purple | #7e56c2 | #9d77df |
| teal   | #009688 | #26a69a |
| indigo | #3f51b5 | #5c6bc0 |
```

---

## Variants of AGENTS.md

Some tools look for different filenames, but the idea is the same:

| File | Tool |
|---|---|
| `AGENTS.md` | OpenCode, general agents |
| `CLAUDE.md` | Claude Code, Claude |
| `.cursorrules` | Cursor editor |

If you use multiple tools, you can create multiple files — or keep one `AGENTS.md` and symlink or copy it. The content should be the same: your project's conventions and rules in one place.

---

## When to Create One

Create an `AGENTS.md` file when:

- You start a new project — set the conventions before anyone asks
- An agent keeps repeating the same mistake — document the rule
- You bring a new tool into your workflow
- You want consistent agent behaviour across sessions

Start small. Three lines of conventions are better than no file at all. Add to it whenever you think "I wish the agent already knew that."

---

## Summary

- `AGENTS.md` sits in your project root and gives agents standing instructions
- It describes your project, conventions, rules, and how to verify work
- The agent reads it automatically at the start of every session
- It saves time, prevents mistakes, and keeps behaviour consistent
- Start small and grow it alongside your project
