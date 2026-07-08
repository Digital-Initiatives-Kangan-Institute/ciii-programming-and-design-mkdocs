# Git Tools and Clients

There are many ways to use Git. You can type commands in a terminal, use a graphical desktop application, or work inside your code editor. Each approach has its strengths and suits different preferences.

---

## Why Use a Tool?

Git itself is a command-line tool. While the terminal is powerful and available everywhere, graphical tools can:

- Make complex operations more visible and discoverable
- Reduce the need to memorise commands
- Show you the state of your repository at a glance
- Help you visualise branches, commits, and diffs

The best tool is the one you are comfortable with and will actually use.

---

## Git in VS Code

The source control features built into VS Code let you stage, commit, push, and manage branches without leaving the editor.

| Strengths | Limitations |
|---|---|
| Already installed with VS Code | Limited to basic operations |
| No extra setup required | Advanced features require the terminal |
| Tight integration with your code | Merge conflict resolution is basic |
| Perfect for the daily stage-commit-push cycle | |

This is the tool we focus on throughout this site because it is available to everyone using VS Code and covers the most common workflows.

---

## GitHub Desktop

A free, open-source desktop application from GitHub. It provides a visual interface for common Git operations and deep integration with GitHub repositories.

| Strengths | Limitations |
|---|---|
| Clean, straightforward interface | GitHub-focused (limited with GitLab/Bitbucket) |
| Easy to see diffs and history | Slower for power users who know the terminal |
| Great for resolving merge conflicts visually | Less flexible than a full-featured Git client |
| Free and actively maintained | |

GitHub Desktop is a good choice if you want a dedicated Git application that stays out of your way and focuses on the core workflow.

---

## GitKraken

A professional Git client with a strong focus on visualising branch history. The commit graph is its standout feature, making it easy to understand complex branching structures.

| Strengths | Limitations |
|---|---|
| Beautiful branch visualisation | Paid for private repositories (free for public) |
| Built-in merge conflict editor | Heavier than simpler clients |
| Supports GitHub, GitLab, Bitbucket, Azure DevOps | Can feel overwhelming for beginners |
| Drag-and-drop branch management | |

GitKraken is well-suited for teams working with many branches and for learners who benefit from seeing the branch structure visually.

---

## Choosing a Tool

| If you want... | Try... |
|---|---|
| Everything in one place, no extra apps | Git in VS Code |
| A simple dedicated Git app | GitHub Desktop |
| Visual branch management | GitKraken |

There is no wrong choice. Many developers use a combination — VS Code for daily commits, GitHub Desktop for reviewing pull requests, and the terminal for one-off advanced operations. Start with what feels natural and explore other tools as your needs grow.
