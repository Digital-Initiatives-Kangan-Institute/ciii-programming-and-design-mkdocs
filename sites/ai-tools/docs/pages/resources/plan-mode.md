# Plan Mode in Agents

Plan mode is a toggle that switches an AI agent into a read-only mode. While plan mode is active, the agent can read your project, ask questions, and propose solutions — but it **cannot make any changes** to your files or run commands. This means you can discuss and design freely without worrying about the agent accidentally modifying something.

When you are happy with the plan, you switch out of plan mode and the agent can begin implementing it.

---

## Why Plan Before Building

Jumping straight into code without a plan leads to:

- **Rework** — you build something, realise it does not fit, and start over
- **Inconsistent structure** — each piece is built in isolation without a shared design
- **Missed requirements** — you forget edge cases, error handling, or accessibility
- **Accidental changes** — without plan mode, a vague instruction could trigger unwanted edits

A few minutes of planning saves hours of rework. This is true whether you are coding solo or with an agent.

---

## How Plan Mode Works

Plan mode turns the agent into a design partner. You switch it on, and the agent is locked into a read-only state where it:

- Reads relevant files to understand the current state of your project
- Asks clarifying questions about what you want
- Proposes an approach — what files to create or modify, in what order
- Identifies potential problems or edge cases before they become bugs
- Waits for your approval before any code is touched

You stay in control. You can reject the plan, ask the agent to revise it, or suggest a different approach — safe in the knowledge that nothing is being changed while you discuss. When you are ready, switch out of plan mode and the agent can start implementing.

---

## When to Use Plan Mode

Plan mode is most valuable when:

- **Adding a new feature** — before touching multiple files, agree on the structure
- **Refactoring** — before renaming things across the project, decide on the new names and patterns
- **Fixing a complex bug** — before chasing symptoms, identify the root cause and the fix
- **Starting a new project** — before writing any code, sketch the folder structure, pages, and components
- **You are unsure of the best approach** — explore options without committing to one

For small, single-file changes — like adding a CSS rule or fixing a typo — plan mode is unnecessary. Jump straight in.

---

## How to Use Plan Mode Effectively

### Start with Context

Tell the agent what you want and why. Include any constraints.

```
I want to add a contact form to my cafe website. It needs name, email,
and message fields, plus client-side validation. The site already has a
consistent header and footer across all pages. I want to keep the same
styling. Plan this before making any changes.
```

### Let the Agent Read the Project

In plan mode, the agent should first explore your files to understand the existing structure, patterns, and conventions. This means it can propose a plan that fits your project rather than one that works in theory.

### Review the Plan

A good plan should answer:

- Which files will be created or modified?
- What is the order of work?
- How does this fit with the existing code?
- Are there any risks or edge cases?

If the plan is vague, ask the agent to be more specific. If it misses something, point it out.

### Refine Before Building

You do not need to accept the first plan. Push back:

```
That plan uses a separate CSS file, but all our styles are in a single
styles.css. Can you revise the plan to keep styles in the existing file?
```

```
You mentioned form validation but did not say what happens when validation
fails. Where should the error messages appear?
```

### Approve and Build

Once the plan is solid, tell the agent to proceed. It will follow the plan step by step, and you can review each change as it goes.

---

## Plan Mode in OpenCode

OpenCode has a dedicated plan mode (`--plan` flag, or can be configured in your project). When plan mode is active:

- OpenCode reads your project files to understand the current state
- You describe what you want to build or change
- OpenCode asks clarifying questions if the requirements are unclear
- It produces a written plan of the files to create or modify, in order
- No files are changed until you confirm the plan
- You can refine the plan through conversation before giving the go-ahead

---

## Example: Plan Mode in Action

**User:**
```
I want to add a dark mode toggle to my cafe site. Plan before making changes.
```

**Agent:**
```
I will read your project to understand the current structure and styles.

[reads files]

Here is my plan:

1. Add a CSS custom property block on :root in styles.css for light mode colours
2. Add a [data-theme="dark"] block with dark mode colour overrides
3. Add a <button> in the header of index.html with id="theme-toggle"
4. Create a script that listens for clicks on the button and toggles
   the data-theme attribute on <html>
5. Use localStorage to remember the user's preference

Does this approach work for you? Any preferences on where the toggle
button should appear?
```

**User:**
```
Good plan. Put the toggle button in the top-right corner of the nav bar.
Proceed with the implementation.
```

---

## Summary

- Plan mode lets you design a solution with the agent before writing any code
- Planning prevents rework, catches edge cases, and ensures consistency
- Use it for features, refactoring, and complex bugs — skip it for small tweaks
- Review the plan, ask for revisions, and only approve when you are confident
- A few minutes of planning saves hours of rework
