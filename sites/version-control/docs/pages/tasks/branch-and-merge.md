# Branch and Merge

## Work on a Feature Branch

!!! abstract "Instructions"
    Use your project from the previous task to practice branching.

    Complete the following steps:

    1. Create a new branch called `feature/add-styles`
    2. On this branch, create a `styles.css` file and link it to your `index.html`
    3. Add some CSS rules (colours, fonts, spacing — your choice)
    4. Stage and commit your changes on the feature branch
    5. Switch back to the `main` branch — notice your CSS file is gone
    6. Merge `feature/add-styles` into `main`
    7. Confirm your styles now appear on `main`
    8. Delete the `feature/add-styles` branch

    At the end, your `main` branch should have all the changes and the feature branch should be deleted.

??? hint "Hint - Click to expand"
    Create a branch by clicking the branch name in the bottom-left corner of VS Code and selecting **Create new branch**. Name it `feature/add-styles`. After making and committing changes, switch back to `main` the same way. To merge: open Source Control, click **...** > **Branch** > **Merge**, and select `feature/add-styles`. Delete the merged branch via the same **...** menu under **Branch** > **Delete Branch**.

---

## Build a Navigation Bar

!!! abstract "Instructions"
    Practice the full branching workflow again with a new feature.

    1. Create a branch called `feature/navigation`
    2. Add a navigation bar to your `index.html`
    3. Stage and commit your changes on the branch
    4. Switch to `main`, merge `feature/navigation`, then delete the branch

---

## Add a Footer

!!! abstract "Instructions"
    One more round of the branching workflow.

    1. Create a branch called `feature/footer`
    2. Add a footer with copyright text to your `index.html`
    3. Stage and commit your changes on the branch
    4. Switch to `main`, merge `feature/footer`, then delete the branch

    By now you should be comfortable with the branch → commit → merge → delete cycle.

---

## Check Your Understanding

!!! abstract "Instructions"
    Append your answers to the `answers.md` file in your project. Stage, commit, and push it to GitHub.

    - When you switched back to `main` during the first exercise, where did your CSS file go? Why?
    - What happens if you try to delete a branch that has not been merged?
    - Why is it better to work on a feature branch instead of directly on `main`?
