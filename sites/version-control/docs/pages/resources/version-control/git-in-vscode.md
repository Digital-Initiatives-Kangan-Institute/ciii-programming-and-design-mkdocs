# Git with VS Code

Version control tracks changes to your code over time and lets you back up your work to GitHub. VS Code has built-in tools that let you do this without typing any commands.

!!! note "Why Use Version Control?"
    - **Back up your work** — your code is stored safely on GitHub
    - **Track changes** — see what changed, when, and why
    - **Revert mistakes** — go back to an earlier working version
    - **Submit assessments** — trainers review your work through GitHub links

    You should use version control from day one of any project.

---

## One-Time Setup

### Install Git

Download and install Git from [git-scm.com](https://git-scm.com). VS Code will detect it automatically.

### Sign In to GitHub in VS Code

1. Open VS Code
2. Click the **Accounts** icon in the bottom-left corner
3. Select **Sign in to GitHub**
4. Follow the prompts in your browser to authorise VS Code

!!! success "Once signed in, VS Code can push and pull code to your GitHub repositories."

---

## Starting a New Project

!!! abstract "Step by Step"
    ### 1. Open the Source Control Panel

    Click the **Source Control** icon in the left sidebar (it looks like a branch with circles). Or press `Ctrl+Shift+G`.

    ### 2. Initialise a Repository

    Click the **Initialise Repository** button. This creates a local Git repository in your project folder.

    ### 3. Publish to GitHub

    After initialising, you will see a **Publish Branch** button. Click it, choose whether the repository should be **private**, and VS Code will create a repository on your GitHub account and push your code to it.

---

## Daily Workflow

Every time you make progress, follow these three steps:

!!! tip "1. Stage Your Changes"
    In the Source Control panel, you will see a list of changed files under **Changes**.

    - Click the **+** next to a file to stage it individually
    - Or click the **+** next to **Changes** to stage everything at once

    Staged files move to a section called **Staged Changes**.

!!! tip "2. Commit Your Changes"
    Type a short message describing what you changed in the message box at the top of the Source Control panel. Then click the **Commit** button.

    A good commit message: `"Add home page with cafe welcome text"`

    A bad commit message: `"stuff"` or `"changes"`

!!! tip "3. Push to GitHub"
    Click the **Sync Changes** button. This uploads your commits to GitHub.

    If you see **Publish Branch** instead, click it — this means it is your first push for this project.

---

## Quick Reference

| Action | Where to Click |
|---|---|
| Open Source Control | Sidebar icon (branch) or `Ctrl+Shift+G` |
| Start tracking a project | **Initialise Repository** |
| Stage a file | **+** next to the file |
| Save a snapshot | Type message + click **Commit** |
| Upload to GitHub | **Sync Changes** or **Publish Branch** |
| Get latest from GitHub | **Sync Changes** (pulls automatically) |

---

## Summary

- Set up once: install Git and sign in to GitHub in VS Code
- Initialise a repository to start tracking a project
- Workflow: stage → commit with a message → push
- Repeat this loop regularly — after every feature or at the end of each session
- Your code on GitHub is your backup and your submission
