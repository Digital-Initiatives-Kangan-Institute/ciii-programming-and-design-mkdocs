# Git Intro Walkthrough

This walkthrough takes you from an empty folder to a project on GitHub with multiple commits, then introduces cloning and repository permissions.

---

## Create Your First Repository

!!! abstract "Instructions"
    1. Create a new folder on your computer and open it in VS Code (**File** → **Open Folder**)
    2. Open the Source Control panel (`Ctrl+Shift+G`)
    3. Click **Initialise Repository**
    4. Create a file called `README.md` and add the line `# My First Git Project`

    If you need help with any of these steps, refer to the [Git with VS Code](../resources/version-control/git-in-vscode.md) resource.

??? hint "Hint - Click to expand"
    Right-click in the Explorer sidebar and select **New File** to create your README. Save the file before committing.

---

## Stage and Commit

!!! abstract "Instructions"
    Stage your `README.md` file and commit it with the message `"Initial commit with README.md"`.

    *What is a commit?* Write a short answer in a new file called `answers.md`.

??? hint "Hint - Click to expand"
    In the Source Control panel, your file appears under **Changes**. Click the **+** to stage it, type your message, and click **Commit**. If you click commit without staging first, VS Code will stage everything for you and prompt for the message.

---

## Push to GitHub

!!! abstract "Instructions"
    Push your repository to GitHub using the **Publish Branch** button in the Source Control panel. Choose **public** visibility.

    Once published, open your browser and navigate to your GitHub account to verify the repository exists with your `README.md`.

    *What is a push?* Write your answer in `answers.md`.

---

## Make Another Change

!!! abstract "Instructions"
    Add a second line to your `README.md`: `Markdown is a lightweight markup language for creating formatted text using a plain-text editor.`

    Stage, commit (with a descriptive message), and push the change. Verify the update appears on GitHub.

---

## Create a New File

!!! abstract "Instructions"
    Create a new file called `git-intro.md` in your project folder. Add some content — for example, a sentence about what you have learned so far about Git. Stage, commit, and push the change.

---

## Build a Structured Document

!!! abstract "Instructions"
    Create a folder called `extras` in your project. Inside it, create a file called `coffee.md`.

    Add the following content to `coffee.md`:

    - **Two sections** indicated by headings:
        - `Coffee Facts` — at least three facts about coffee in a bulleted list
        - `Coffee Varieties` — at least three coffee varieties or brewing methods in a **table** with two columns: name and description
    - A link to a reputable source for more information using the format `[link text](URL)`
    - An image of a cup of coffee or coffee beans. Save the image inside the `extras` folder and reference it in `coffee.md` using Markdown syntax

    Stage, commit, and push everything to GitHub.

??? hint "Hint - Click to expand"
    Markdown table syntax:
    
    ```
    | Variety | Description |
    |---|---|
    | ... | ... |
    ```

    To include an image: `![alt text](filename.jpg)`. Make sure the image file is in the same folder as your markdown file or adjust the path accordingly.

    Need a refresher on markdown? Check the [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/).

---

## Clone a Repository

!!! abstract "Instructions"
    Ask a classmate for the URL of their Git Intro Walkthrough repository. Clone it to your computer:

    1. In VS Code, open the Source Control panel and click **Clone Repository**
    2. Paste the URL and choose a location on your computer
    3. Click **Clone** and open the repository when prompted

    Explore the files — you should see everything your classmate committed.

---

## Try Pushing to a Cloned Repository

!!! abstract "Instructions"
    Make a change to one of the files in the cloned repository — add a new line of text or modify some existing content. Stage, commit, and try to push the change to GitHub.

    In `answers.md` (in your own project, not the cloned one), write down:
    
    - *What happened when you tried to push? Did it work?*
    - *Why do you think this happened?*

??? hint "Hint - Click to expand"
    Think about who owns the repository on GitHub. Cloning gives you a copy of the code, but does it give you permission to write back to the original repository?

---

## Check Your Understanding

!!! abstract "Instructions"
    In your own project's `answers.md`, write answers to the following. Stage, commit, and push.

    - What is a commit and why is it useful?
    - What is the difference between staging and committing?
    - What does pushing do? Where does your code go?
    - What is cloning? How is it different from initialising a new repository?
    - Why could you not push to your classmate's repository? What would need to happen for you to be able to push?

??? tip "Tip - Click to expand"
    For the last question, think about repository visibility (public vs private) and the concept of **collaborators** on GitHub.
