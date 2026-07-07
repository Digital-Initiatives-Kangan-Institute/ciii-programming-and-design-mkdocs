# CLI, IDE, and Project Setup

A well-configured development environment makes you faster and helps AI tools work better. This page covers CLI basics, VS Code setup, and project context management.

---

## Command Line Interface (CLI)

The CLI is essential for running development servers, managing Git, installing packages, and using AI coding tools.

### Essential Commands

| Command | Description |
|---|---|
| `pwd` | Print working directory |
| `ls` | List files in current directory |
| `ls -la` | List all files with details |
| `cd <dir>` | Change directory |
| `cd ..` | Go up one directory |
| `mkdir <name>` | Create a new directory |
| `touch <file>` | Create an empty file |
| `rm <file>` | Remove a file |
| `rm -rf <dir>` | Remove a directory and its contents |
| `cat <file>` | Display file contents |
| `npm install` | Install project dependencies |
| `npm run dev` | Start the development server |
| `git status` | Show changed files |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Commit staged changes |

### Navigation Tips

```bash
# Go to home directory
cd ~

# Go to previous directory
cd -

# Use tab completion — type part of a name and press Tab
cd Doc<Tab>   # Auto-completes to cd Documents/
```

---

## VS Code Setup

VS Code is the recommended editor. Install these extensions:

### Required Extensions

| Extension | Purpose |
|---|---|
| **Live Preview** | Preview HTML pages in real time as you edit |
| **GitHub Copilot** | AI code completion |
| **Prettier** | Automatic code formatting |
| **ESLint** | JavaScript/TypeScript linting |

### Recommended Settings

Enable format-on-save:

1. Open Settings (`Ctrl+,`)
2. Search for "format on save"
3. Enable `Editor: Format On Save`

This ensures your code is always consistently formatted.

### Window Management

Organise your workspace efficiently:

```
+-------------------+-----------+
|                   |           |
|    Editor         |  Copilot  |
|    (code)         |  Chat     |
|                   |           |
+-------------------+-----------+
|    Terminal                   |
+-------------------------------+
```

- `Ctrl+`` — Toggle terminal
- `Ctrl+Shift+I` — Open Copilot Chat
- `Ctrl+B` — Toggle sidebar
- `Ctrl+P` — Quick file open

---

## AI Integration Features

Modern IDEs integrate AI in several ways:

- **Inline completions** — Ghost text suggestions appear as you type. Press `Tab` to accept.
- **Chat panels** — Ask questions about your code. AI can see your open files.
- **Agent mode** — AI reads your project, edits files, and runs commands.
- **Context awareness** — AI understands imports, project structure, and related files.

---

## Tokens and Context

AI models process text in chunks called **tokens**. Understanding tokens helps you manage context effectively.

### What Are Tokens?

- 1 token ≈ 0.75 words in English
- A typical code file is 500–2000 tokens
- Models have context windows — the maximum tokens they can process at once

| Model | Context Window |
|---|---|
| Claude 3.5 | 200K tokens |
| GPT-4 | 128K tokens |
| Llama 3 | 8K tokens |

### Providing Good Context to AI

The quality of AI output depends heavily on context:

- Use **descriptive file and function names**
- Include **comments** explaining intent, not mechanics
- Keep files **focused and not too large** — split large files
- Reference **related files** when asking questions
- Use configuration files like `.cursorrules` to set project conventions

### Example: Good vs Bad Context

```javascript
// BAD — unclear intent
function f(x) {
    return x * 1.1;
}

// GOOD — AI can understand the purpose
/**
 * Calculates the total price including 10% GST.
 * @param subtotal - The pre-tax amount in AUD
 * @returns The total amount including tax
 */
function calculateTotalWithGST(subtotal: number): number {
    const GST_RATE = 0.10;
    return subtotal * (1 + GST_RATE);
}
```

---

## Planning Before Coding

Before writing any code, especially with AI assistance:

1. **Define the problem** — What should the feature do? Write it down in one sentence.
2. **Sketch the architecture** — What components, pages, and data are needed?
3. **List the steps** — Break the work into small, testable pieces
4. **Consider edge cases** — What happens with empty data? Error states? Loading?
5. **Review the plan** — Does this approach make sense before you start?

A clear plan leads to better prompts and better AI-generated code.

### Example Plan

```
FEATURE: User Profile Page

1. Create /profile route
2. Create Profile component with avatar, name, bio
3. Fetch user data from /api/user
4. Handle loading state (spinner)
5. Handle error state (friendly message)
6. Handle empty state (no bio set yet)
```

---

## Summary

- Learn the **CLI** — it is essential for development workflows
- Set up **VS Code** with Live Preview, Copilot, Prettier, and ESLint
- **Tokens** measure how much context an AI model can handle
- Good **naming and comments** dramatically improve AI output quality
- **Plan** before coding — a clear plan leads to clearer prompts
