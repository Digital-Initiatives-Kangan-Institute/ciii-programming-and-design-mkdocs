# Pull Request Workflow

Pull requests (PRs) let you review changes before merging. Instead of merging directly in VS Code, you push your branch and open a PR on GitHub.

## Open Your First Pull Request

!!! abstract "Instructions"
    Use a pull request to merge a feature into `dev`.

    1. Switch to `dev` and Sync to get the latest
    2. Create a branch from `dev` called `feature/services-section`
    3. Add a services section to your `index.html` listing three things your project offers
    4. Stage and commit your changes
    5. Push the feature branch to GitHub
    6. Go to your repository on GitHub — you should see a prompt to create a pull request
    7. Open a pull request to merge `feature/services-section` into `dev`
    8. Add a short description explaining what the PR adds
    9. Review the diff — does everything look correct?
    10. Merge the pull request on GitHub
    11. Back in VS Code, switch to `dev` and Sync to pull the merged changes
    12. Delete the feature branch

??? hint "Hint - Click to expand"
    After pushing, GitHub usually shows a yellow banner with a **Compare & pull request** button. If not, go to the **Pull requests** tab and click **New pull request**. Set the base to `dev` and the compare to your feature branch. Look through the **Files changed** tab to review your diff before merging.

---

## Second Pull Request

!!! abstract "Instructions"
    Practice the PR workflow again to build the habit.

    1. Switch to `dev`, Sync, then create a branch called `feature/team-section`
    2. Add a team or about-us section to your `index.html`
    3. Stage, commit, and push the branch to GitHub
    4. Open a pull request to merge `feature/team-section` into `dev`
    5. Review and merge the PR on GitHub
    6. Switch to `dev`, Sync, and delete the feature branch

---

## Release dev to main with a Pull Request

!!! abstract "Instructions"
    Now release the accumulated features from `dev` to `main` using a pull request.

    1. Make sure `dev` is up to date on GitHub (all previous PRs merged)
    2. Go to the **Pull requests** tab on GitHub
    3. Open a pull request to merge `dev` into `main`
    4. Write a description summarising what is being released
    5. Review the diff — you should see all the features that have accumulated on `dev`
    6. Merge the pull request
    7. In VS Code, switch to `main` and Sync to pull the merged changes

---

## Check Your Understanding

!!! abstract "Instructions"
    Append your answers to the `answers.md` file in your project. Stage, commit, and push it to GitHub.

    - What is the benefit of reviewing a pull request before merging, even when working alone?
    - What is the difference between the **base** branch and the **compare** branch in a pull request?
    - After merging a PR on GitHub, why do you need to Sync in VS Code?
