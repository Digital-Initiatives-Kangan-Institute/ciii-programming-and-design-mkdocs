# What is Version Control

Version control is the practice of tracking and managing changes to files over time. It lets you see who changed what, when, and why — and roll back to an earlier version if something goes wrong.

---

## Why Use Version Control?

Without version control, you might save copies of files with names like `project_v1.html`, `project_v2_final.html`, and `project_v2_final_REAL.html`. This becomes messy, error-prone, and impossible to track across a team.

Version control solves this by:

- Keeping a complete **history** of every change
- Letting you **revert** to any previous version
- Enabling **collaboration** — multiple people can work on the same project without overwriting each other's work
- Providing a **backup** stored on a remote server
- Showing **who** made each change and **why** through commit messages

---

## Types of Version Control Systems

There are three generations of version control systems:

### Local Version Control

The simplest approach: a database on your computer that tracks changes to files. Tools like RCS (Revision Control System) store patches (differences between versions) in a local database.

```
Computer
  └── Local Database
       ├── version 1
       ├── version 2
       └── version 3
```

This works for a single developer but does not support collaboration.

### Centralised Version Control (CVCS)

A single server holds all versioned files, and developers check out files from that central location. Examples include **Subversion (SVN)** and **Perforce**.

```
            Central Server
           ┌──────────────┐
           │  Repository  │
           └──────┬───────┘
        ┌─────────┼─────────┐
        │         │         │
   Developer   Developer  Developer
```

This enables collaboration, but has a single point of failure: if the central server goes down, nobody can work or access the history.

### Distributed Version Control (DVCS)

Every developer has a full copy of the repository, including the complete history. Examples include **Git** and **Mercurial**.

```
Developer A                 Developer B
┌──────────────┐           ┌──────────────┐
│  Repository  │←─────────→│  Repository  │
│  (full copy) │           │  (full copy) │
└──────┬───────┘           └──────┬───────┘
       │                          │
       └──────────┬───────────────┘
                  │
          ┌──────────────┐
          │ Remote Server│
          │  (optional)  │
          └──────────────┘
```

In a distributed system:

- You can work offline — commit, branch, and view history without a network connection
- There is no single point of failure — anyone has a full backup
- Collaboration happens by sharing changes between repositories

---

## Git — The Industry Standard

Git is a distributed version control system created by Linus Torvalds in 2005 for Linux kernel development. It is now the most widely used version control system in the world.

!!! note "Why Git Dominates"
    - **Distributed** — every copy is a full repository with complete history
    - **Fast** — most operations are local, not over the network
    - **Branching** — lightweight branches make it easy to experiment and collaborate
    - **Universal** — used by individuals, startups, and every major tech company
    - **GitHub** — the largest platform for hosting Git repositories, making collaboration and sharing simple

Supporting tools and services built around Git include:

| Tool | Purpose |
|---|---|
| **GitHub** | Host repositories, review code, manage projects |
| **GitLab** | Self-hosted or cloud Git with built-in CI/CD |
| **Bitbucket** | Git hosting integrated with Jira and Trello |
| **VS Code** | Built-in Git support with visual interface |

---

## What You Will Learn

In this site you will find resources covering:

- Using Git through **VS Code's interface** — no terminal required
- The **main / dev / feature** branching strategy to organise your work

---

## Summary

- Version control tracks changes, enables rollback, and supports collaboration
- Local VCS is for single developers, CVCS adds a central server, DVCS gives everyone a full copy
- Git is the dominant distributed version control system used across the industry
- GitHub, GitLab, and Bitbucket provide hosting and collaboration on top of Git
