# AI Coding Assistants

AI coding assistants help you write, understand, and debug code faster. This page covers the three main tools used in this course.

---

## GitHub Copilot

Copilot is the most widely used AI coding assistant, deeply integrated into VS Code and the terminal.

### In the IDE

After installing the Copilot extension in VS Code:

- **Inline completions** — Start typing and Copilot suggests code as ghost text. Press `Tab` to accept.
- **Copilot Chat** (`Ctrl+Shift+I`) — Ask questions about your code, get explanations, or request code generation.
- **Agent mode** — Copilot can read your project files, run terminal commands, and make edits across multiple files.

### In the CLI

```bash
# Ask Copilot for a command
gh copilot suggest "list all files modified in the last 7 days"

# Explain a command
gh copilot explain "git rebase -i HEAD~3"
```

### Best Practices

- Write descriptive **comments** describing what you want — Copilot uses them as context
- Use meaningful **function and variable names** — they guide Copilot's suggestions
- Always **review** generated code before using it
- Use **Copilot Chat** to ask "What does this code do?" when reading unfamiliar code

---

## Claude Code

Claude Code (by Anthropic) is an agentic coding tool that runs in the terminal. It can handle complex multi-step tasks autonomously.

### Starting Claude Code

```bash
# From your project directory
claude
```

Claude Code opens an interactive session where you can describe tasks in natural language.

### What It Can Do

- Read and understand your entire project
- Edit files, create new files, delete files
- Run shell commands and interpret the output
- Search the codebase for specific patterns
- Manage git operations (commits, branches)
- Execute multi-step workflows (e.g., "Add a dark mode toggle to every page")

### Best Practices

- Give Claude Code **clear, specific instructions** with context
- Include **file paths** when referencing specific code
- Ask Claude to **explain its changes** before making them
- Use Claude Code for **multi-file refactors** that would be tedious manually

---

## OpenAI Codex / ChatGPT

OpenAI's models can assist from the terminal, browser, or IDE.

### In the Terminal

The Codex CLI can generate shell commands:

```bash
# Describe what you want to do
codex "find all TypeScript files and count the lines of code"
```

### With the OpenAI API

You can integrate Codex models into your own tools:

```javascript
const response = await fetch("https://api.openai.com/v1/chat/completions", {
    method: "POST",
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer YOUR_API_KEY"
    },
    body: JSON.stringify({
        model: "gpt-4",
        messages: [{ role: "user", content: "Explain recursion with an example." }]
    })
});
```

---

## Comparing the Tools

| Feature | Copilot | Claude Code | ChatGPT/Codex |
|---|---|---|---|
| Best for | Inline code completion | Complex multi-step tasks | Explanations and learning |
| Integration | VS Code, CLI | Terminal | Web, API, CLI |
| Context | Open files + workspace | Entire project | Conversation history |
| File editing | Inline suggestions | Full file read/write | Copy-paste |
| Cost | Subscription | API usage | API usage |

---

## Choosing the Right Tool

- **Writing new code**: Use Copilot for inline completions
- **Refactoring across files**: Use Claude Code for multi-file changes
- **Learning a concept**: Use ChatGPT/Codex for explanations and examples
- **Debugging**: Use any — paste the error message and ask for help
- **Researching packages/libraries**: Ask any assistant "What library should I use for X?"

You do not need to use all of them. Start with Copilot in VS Code and expand as needed.

---

## Summary

- **Copilot** provides inline suggestions in your editor — great for writing code faster
- **Claude Code** handles multi-step tasks from the terminal — powerful for refactoring
- **ChatGPT/Codex** excels at explanations and learning new concepts
- All tools work best when you provide **clear context** and **review their output**
