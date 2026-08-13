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

### Check if Git is Installed

Open a terminal and run:

```bash
git --version
```

If you see a version number (e.g. `git version 2.43.0`), Git is ready to use. If not, download and install Git from [git-scm.com](https://git-scm.com) and follow the instructions for your operating system. VS Code will detect it automatically once installed.

### Install Visual Studio Code

VS Code is the editor you will use throughout this course. Download it from [code.visualstudio.com](https://code.visualstudio.com) and follow the installation instructions for your operating system.

### Create a GitHub Account

Go to [github.com/signup](https://github.com/signup) and follow the instructions to create an account. Use your student email address.

!!! tip "GitHub Student Developer Pack"
    After creating your account, sign up for the [GitHub Student Developer Pack](https://education.github.com/pack). This gives you free access to premium tools and services including GitHub Pro, GitHub Copilot, and cloud credits from multiple providers.

### Sign In to GitHub in VS Code

1. Open VS Code
2. Click the **Accounts** icon in the bottom-left corner
3. Select **Sign in to GitHub**
4. Follow the prompts in your browser to authorise VS Code

!!! success "Once signed in, VS Code can push and pull code to your GitHub repositories."

---

## Starting a New Project

!!! abstract "Step by Step"
    ### 1. Open or Create a Project Folder

    Go to **File** → **Open Folder** (or press `Ctrl+K Ctrl+O`). Navigate to where you want your project to live. To create a new folder, click the **New Folder** button in the dialog that appears and give it a name.

    Once the folder opens in VS Code, you can create files by right-clicking in the Explorer sidebar and selecting **New File**.

    ### 2. Open the Source Control Panel

    Click the **Source Control** icon in the left sidebar (it looks like a branch with circles). Or press `Ctrl+Shift+G`.

    ### 3. Initialise a Repository

    Click the **Initialise Repository** button. This creates a local Git repository in your project folder.

    ### 4. Publish to GitHub

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

    If you click commit without staging first, VS Code will automatically stage all changes for you and prompt for a commit message. To avoid this prompt in future, type your message before clicking commit.

    A good commit message: `"Add home page with cafe welcome text"`

    A bad commit message: `"stuff"` or `"changes"`

!!! tip "3. Push to GitHub"
    Click the **Sync Changes** button. This uploads your commits to GitHub.

    If you see **Publish Branch** instead, click it — this means it is your first push for this project.

---

## Cloning a Repository

Cloning creates a local copy of a GitHub repository on your computer.

1. Go to the repository on GitHub you want to clone
2. Click the green **Code** button and copy the URL
3. In VS Code, open the Source Control view and click **Clone Repository**
4. Paste the URL and choose a location on your computer
5. Click **Clone** — VS Code will download the repository and ask if you want to open it

!!! warning "Permission Required"
    You can only push changes to repositories you own or have been added to as a collaborator. Cloning someone else's public repository lets you read the code but not push changes to it.

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
| Copy a repository | **Clone Repository** + paste URL |

---

## Summary

- Install Git, VS Code, and create a GitHub account (use your student email for the Student Developer Pack)
- Sign in to GitHub in VS Code
- Initialise a repository to start tracking a project
- Workflow: stage → commit with a message → push
- Repeat this loop regularly — after every feature or at the end of each session
- Clone repositories to get a local copy of existing projects
- Your code on GitHub is your backup and your submission
