# Working with a dev Branch

The earlier tasks used `main` directly to keep things simple. Now you will add a `dev` branch as the integration point where features come together. From now on, you will not commit directly to `main`.

## Set Up dev from main

!!! abstract "Instructions"
    Create a `dev` branch from your current `main` branch.

    1. Switch to your `main` branch and Sync to get the latest
    2. Create a new branch called `dev`
    3. Push `dev` to GitHub so it exists on the remote as well

    You now have two long-lived branches: `main` and `dev`.

---

## Create a Feature the Right Way

!!! abstract "Instructions"
    Practice the full main/dev/feature workflow by adding a new feature through `dev`.

    1. Switch to `dev` and Sync to get the latest
    2. Create a branch from `dev` called `feature/hero-section`
    3. Add a hero section to your `index.html` — a large heading, a subheading, and a call-to-action paragraph
    4. Stage and commit your changes on the feature branch
    5. Switch to `dev`, then merge `feature/hero-section` into `dev`
    6. Delete the feature branch
    7. Push `dev` to GitHub

    Notice the difference: you merged into `dev`, not `main`.

---

## Add Another Feature Through dev

!!! abstract "Instructions"
    Repeat the workflow with another feature.

    1. Switch to `dev` and Sync
    2. Create a branch from `dev` called `feature/testimonials`
    3. Add a testimonials section to your `index.html` with at least two customer quotes
    4. Stage and commit your changes on the feature branch
    5. Switch to `dev`, merge `feature/testimonials`, delete the branch
    6. Push `dev` to GitHub

---

## Release to main

!!! abstract "Instructions"
    Now that `dev` has the hero section and testimonials, release it to `main`.

    1. Switch to `main` and Sync
    2. Merge `dev` into `main`
    3. Push `main` to GitHub

    Your `main` branch now contains both features, but they arrived through a single `dev` → `main` merge rather than multiple feature merges.

---

## Check Your Understanding

!!! abstract "Instructions"
    Append your answers to the `answers.md` file in your project. Stage, commit, and push it to GitHub.

    - Why merge features into `dev` instead of directly into `main`?
    - What is the difference between a long-lived branch (like `main` and `dev`) and a short-lived branch (like `feature/hero-section`)?
    - When would you merge `dev` into `main`? After every feature, or after a group of features? Why?
