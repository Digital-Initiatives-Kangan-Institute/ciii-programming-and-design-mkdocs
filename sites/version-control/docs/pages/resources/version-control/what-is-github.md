# What is GitHub

GitHub is a platform for hosting, sharing, and collaborating on Git repositories. It adds a web-based interface and collaboration tools on top of Git.

---

## Git vs GitHub

A common point of confusion: **Git** and **GitHub** are not the same thing.

| Git | GitHub |
|---|---|
| A version control tool | A website that hosts Git repositories |
| Runs on your computer | Runs in the cloud |
| Tracks changes, branches, commits | Adds pull requests, issues, project boards |
| Works offline | Requires an internet connection to sync |
| Free and open-source software | Free for most uses, paid for organisations |

You can use Git without GitHub — your repository lives on your computer and you never push it anywhere. GitHub makes it easy to share your code, collaborate with others, and keep a backup in the cloud.

---

## What GitHub Provides

### Repository Hosting

GitHub stores your repository online. After pushing from VS Code, your code is visible at a URL like `github.com/your-username/your-project`. Anyone you share it with can view, clone, or contribute to it.

### Pull Requests

A pull request is a proposal to merge changes from one branch into another. It shows a diff of what changed and provides a place for discussion and review before merging.

### Issues

Issues are a built-in task tracker. You can create issues for bugs, feature requests, or any piece of work. Each issue has a number, a title, a description, labels, and can be assigned to a person.

### Actions (CI/CD)

GitHub Actions let you automate workflows. For example, you can automatically run tests every time someone pushes code, or deploy your site when changes are merged into `main`.

---

## GitHub vs Other Platforms

GitHub is the most popular, but it is not the only option:

| Platform | Notes |
|---|---|
| **GitHub** | Largest community, owned by Microsoft, free for most uses |
| **GitLab** | Built-in CI/CD, can be self-hosted, strong DevOps focus |
| **Bitbucket** | Atlassian ecosystem, integrates with Jira and Trello |

All three work the same way at the Git level — they are all hosts for Git repositories. The differences are in the collaboration features built on top.

---

## How It Connects to VS Code

When you sign in to GitHub in VS Code, the editor can:

- Publish repositories to your GitHub account
- Sync changes with `main` or any other branch
- View pull requests and issues without leaving the editor

The **Sync Changes** button in VS Code communicates with your GitHub repository in both directions — pulling down changes from others and pushing up your own.

---

## Summary

- GitHub is a platform for hosting and collaborating on Git repositories
- Git is the tool — GitHub is the place where you store and share the results
- GitHub adds pull requests, issues, and automation on top of Git
- VS Code connects directly to GitHub for publishing and syncing
