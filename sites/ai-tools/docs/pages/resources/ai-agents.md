# AI Agents

AI agents go beyond the question-and-answer pattern of chatbots. An agent can read your entire project, plan a multi-step task, and make changes across multiple files — all while keeping you in control.

---

## How Agents Differ from Chatbots

| | Chatbot | Agent |
|---|---|---|
| **Interaction** | You ask, it answers | You give a task, it works through it |
| **Context** | Only what you paste or discuss | Reads your project files and structure |
| **Scope** | Single response at a time | Plans, executes, and verifies across files |
| **Output** | Text and code blocks | File edits, terminal commands, project changes |
| **Session** | Stateless conversation | Maintains context across the entire task |

An agent is like having a junior developer who can read your codebase, understand your instructions, make changes, and explain what they did.

---

## Common Agent Tools

### OpenCode

A terminal-based AI agent that works from the command line. You describe what you want to build or change, and OpenCode reads your project files, plans the work, and makes edits.

- Works across your entire project, not just one file
- Can run terminal commands to verify changes
- Maintains context about your project throughout the session
- You remain in control — review and approve changes

### Copilot Agent Mode (VS Code)

GitHub Copilot's agent capabilities work inside VS Code. You describe a task — such as "add form validation to the login page" — and Copilot can:

- Read relevant files across your project
- Plan the changes needed
- Edit multiple files in sequence
- Show you what changed and why

### Big Pickle

A conversational AI tool that can assist with planning and problem-solving for development tasks. Used alongside other tools for brainstorming and troubleshooting.

---

## What Agents Are Good At

Agents excel at tasks that span multiple files or require planning:

- **Project setup** — scaffold a new project with the right structure
- **Feature implementation** — build a complete feature across HTML, CSS, and JavaScript
- **Refactoring** — rename variables, extract functions, reorganise files
- **Debugging across files** — trace an error through imports, components, and config
- **Code review and fixes** — scan the project for issues and fix them

---

## What Agents Are Not Good At

- **Understanding unwritten requirements** — an agent cannot read your mind. Be specific.
- **Creative design decisions** — agents can suggest layouts but cannot make subjective design choices
- **Guaranteeing correctness** — agent output must be reviewed and tested, just like any code
- **One-shot perfection** — complex tasks often need iteration and refinement

---

## Agent Workflow

A typical session with an agent follows this pattern:

1. **Describe the task** — be specific about what you want
2. **Agent reads the project** — it scans relevant files to understand the current state
3. **Agent proposes a plan** — it may ask clarifying questions before starting
4. **Agent makes changes** — edits files, runs commands, or generates new code
5. **You review** — check the changes, test them, and accept or refine
6. **Iterate** — ask for adjustments until the result is correct

---

## Keeping Control

Agents are tools, not replacements. You should always:

- **Review every change** — do not blindly accept edits
- **Understand what changed** — ask the agent to explain if something is unclear
- **Commit often** — commit before asking an agent to make large changes so you can revert
- **Start small** — begin with simple tasks to build trust in the tool

---

## Summary

- Agents go beyond chatbots by reading your project and making changes across files
- OpenCode, Copilot Agent, and Big Pickle are common agent tools
- Agents are best for multi-file tasks: features, refactoring, debugging
- Always review, understand, and test agent output
- Commit before making large changes so you can revert if needed
