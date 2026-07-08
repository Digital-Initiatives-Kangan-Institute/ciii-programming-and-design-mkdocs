# Merge Conflicts

A merge conflict happens when Git cannot automatically combine two sets of changes. This is normal and not a mistake — it just needs a human decision.

---

## What Causes a Merge Conflict?

A conflict occurs when two branches have edited the **same part of the same file** and Git does not know which version to keep.

For example:

- You edit line 5 of `index.html` on `feature/nav-bar`
- A teammate edits line 5 of `index.html` on `feature/footer`
- When you try to merge both into `dev`, Git sees two different versions of line 5 and cannot decide which one to use

This is not a bug — it is Git asking you to make a decision.

---

## What a Conflict Looks Like

When a conflict occurs, Git marks the file with conflict markers:

```html
<h1>Welcome to Our Cafe</h1>
<<<<<<< HEAD
<nav>
    <a href="index.html">Home</a>
    <a href="menu.html">Menu</a>
</nav>
=======
<footer>
    <p>2026 My Cafe. All rights reserved.</p>
</footer>
>>>>>>> feature/footer
```

- `<<<<<<< HEAD` marks the start of your current branch's version
- `=======` separates the two versions
- `>>>>>>> feature/footer` marks the end of the incoming branch's version

Your job is to replace this entire block with the correct final version.

---

## Resolving a Merge Conflict in VS Code

VS Code makes resolving conflicts visual and straightforward.

### 1. Open the Conflicted File

The file appears in the Source Control panel under **Merge Changes** with a `C` badge. Open it and you will see the conflict markers highlighted in colour.

### 2. Choose What to Keep

Above each conflicted section, VS Code shows clickable options:

- **Accept Current Change** — keep your version
- **Accept Incoming Change** — keep the other branch's version
- **Accept Both Changes** — keep both, one after the other
- **Compare Changes** — see a side-by-side diff of the two versions

Click the option that makes sense. You can mix and match — keep your navigation from one section and the other person's footer from another.

### 3. Review and Save

After resolving all conflicts, review the file to make sure everything looks correct. The conflict markers should be gone.

### 4. Stage the Resolved File

The resolved file moves from **Merge Changes** to **Staged Changes**. Stage it by clicking the **+**.

### 5. Complete the Merge

Commit the staged file. VS Code will suggest a default merge commit message like `Merge branch 'feature/footer' into dev`. You can accept this or write your own.

---

## Avoiding Merge Conflicts

While conflicts cannot always be prevented, these habits reduce them:

- **Pull often** — sync your branch before starting new work
- **Keep branches short-lived** — merge feature branches quickly rather than letting them drift
- **Communicate** — if you know someone else is working on the same file, coordinate
- **Commit small** — small, focused commits are easier to reconcile than large ones

---

## Summary

- Merge conflicts happen when Git cannot automatically combine two versions of the same code
- VS Code highlights conflicts and provides buttons to accept one version or both
- Resolve all conflicts, stage the file, and commit to complete the merge
- Conflicts are normal — they are not an error, just a decision point
