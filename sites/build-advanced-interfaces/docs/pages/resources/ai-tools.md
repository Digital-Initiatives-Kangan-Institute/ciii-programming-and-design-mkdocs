# AI Tools and Development Environment

Modern web development increasingly relies on AI-assisted tools and a well-configured development environment. This resource covers the key tools and concepts you will use throughout this course.

---

## Local AI Models

Running AI models locally gives you privacy, offline access, and no usage limits.

### Ollama

Ollama is a tool for running large language models (LLMs) locally on your machine.

```bash
# Install Ollama (Linux/macOS)
curl -fsSL https://ollama.com/install.sh | sh

# Pull and run a model
ollama pull llama3
ollama run llama3
```

Ollama supports many models including Llama, Mistral, CodeLlama, and more. It exposes a local API at `http://localhost:11434`.

### LM Studio

LM Studio provides a graphical interface for discovering, downloading, and running local LLMs. It is ideal for users who prefer a visual tool over the command line.

Key features:
- Browse and download models from Hugging Face
- Built-in chat interface
- Local API server compatible with OpenAI client libraries

---

## Command Line Interface (CLI)

The CLI is essential for development workflows, Git operations, and running build tools.

### Essential Commands

| Command | Description |
|---|---|
| `pwd` | Print working directory |
| `ls` | List files |
| `cd <dir>` | Change directory |
| `mkdir <name>` | Create directory |
| `touch <file>` | Create file |
| `rm <file>` | Remove file |
| `npm install` | Install Node.js dependencies |
| `npm run dev` | Start development server |
| `git status` | Show Git status |

Learning the CLI allows you to work efficiently and use AI coding tools that operate from the terminal.

---

## AI Coding Assistants

### Claude Code

Anthropic's Claude Code is an agentic coding tool that runs in the terminal. It can read, write, and edit files, run commands, and manage complex multi-step tasks.

```bash
# Start Claude Code in your project
claude
```

### Codex (OpenAI)

OpenAI Codex powers AI-assisted coding in the terminal and IDE. It can generate commands, explain code, and help with debugging.

### GitHub Copilot

Copilot integrates directly into VS Code and the CLI:

- **IDE**: Provides inline code suggestions as you type
- **CLI**: Use `gh copilot suggest` for command suggestions
- **Chat**: Ask questions and get explanations in the editor

---

## IDE Configuration

### VS Code

VS Code is the recommended editor for this course. Key extensions:

| Extension | Purpose |
|---|---|
| Live Preview | Preview HTML pages in real time |
| GitHub Copilot | AI code completion |
| Prettier | Code formatting |
| ESLint | JavaScript linting |

### AI Integration in the IDE

Modern IDEs support AI features:

- **Inline completions** — code suggestions appear as ghost text
- **Chat panels** — ask questions about your codebase
- **Agent mode** — AI can edit files and run commands
- **Context awareness** — AI understands your project structure

---

## Project Context and Tokens

### Tokens

AI models process text in chunks called tokens. Understanding tokens helps you manage context effectively.

- 1 token ≈ 0.75 words in English
- A typical code file might be 500–2000 tokens
- Models have context windows (e.g., 128K tokens for Claude)

### Providing Good Context

When working with AI tools, the quality of output depends heavily on the context you provide:

- Use descriptive file and function names
- Include comments explaining intent
- Keep files focused and not too large
- Reference related files when asking questions
- Use `.cursorrules` or similar files to set project conventions

---

## Planning Before Coding

Before writing any code, especially with AI assistance:

1. **Define the problem** — What should the feature do?
2. **Sketch the architecture** — What components are needed?
3. **List the steps** — Break down into small, testable pieces
4. **Consider edge cases** — What could go wrong?
5. **Review the plan** — Does this approach make sense?

A good plan leads to better prompts and better AI-generated code.

---

## Summary

- **Ollama** and **LM Studio** let you run AI models locally
- **CLI** skills are essential for efficient development
- **Claude Code, Codex, Copilot** are AI coding assistants with different strengths
- **VS Code** with the right extensions provides a productive IDE
- **Tokens** measure how much context an AI can process
- **Planning** before coding leads to better results with AI tools
