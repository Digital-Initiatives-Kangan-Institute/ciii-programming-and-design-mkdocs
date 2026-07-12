# .gitignore

Not every file in your project should be tracked by Git. A `.gitignore` file tells Git which files and folders to ignore.

---

## Why Use .gitignore?

Some files should never be committed to a repository:

- Files containing **secrets** — API keys, passwords, tokens
- **Build output** — compiled files, production bundles
- **Dependencies** — `node_modules`, `vendor`, packages installed by a package manager
- **Operating system files** — `.DS_Store` (macOS), `Thumbs.db` (Windows)
- **Editor settings** — `.vscode/settings.json` (sometimes), IDE-specific config
- **Environment files** — `.env` files containing local configuration

Committing these files clutters your repository, exposes secrets, and can cause conflicts between different machines.

---

## Creating a .gitignore File

Create a file called `.gitignore` in the root of your project. Each line is a pattern that Git should ignore:

```
# Dependencies
node_modules/

# Build output
dist/
build/
.next/

# Environment files
.env
.env.local

# OS files
.DS_Store
Thumbs.db

# Editor
*.swp
*.swo
```

- Lines starting with `#` are comments
- A trailing `/` matches directories
- `*` matches any sequence of characters

Once a file is listed in `.gitignore`, it will not appear in the Source Control panel and will not be committed.

---

## Common Patterns

| Pattern | Ignores |
|---|---|
| `node_modules/` | The entire node_modules folder |
| `*.log` | Any file ending in .log |
| `dist/` | The dist directory and its contents |
| `!.gitkeep` | Exception — track this file even if the folder pattern matches |

The `!` prefix creates an exception. This is useful when you want to keep an otherwise empty folder in the repository by adding a `.gitkeep` file.

---

## Already Tracked Files

If a file was committed before it was added to `.gitignore`, Git will continue tracking it. To stop tracking it:

1. Add the file to `.gitignore`
2. Delete the file from your repository (in VS Code, delete it and commit the delete)
3. The file still exists on your computer but Git no longer tracks it

!!! warning
    Never commit `.env` files. If you have already committed one, change any exposed keys or passwords immediately. Simply adding it to `.gitignore` afterwards does not remove it from the Git history.

---

## VS Code and .gitignore

When you create a `.gitignore` file in VS Code, the Source Control panel updates immediately. Files matching the patterns will disappear from the **Changes** list.

VS Code also highlights ignored files in the file explorer with a greyed-out name, so you can tell at a glance what Git is tracking and what it is not.

---

## Summary

- `.gitignore` tells Git which files and folders to skip
- Always ignore `node_modules/`, `.env` files, and OS files
- One pattern per line, `#` for comments
- Adding a file to `.gitignore` after it is committed does not remove it from history
