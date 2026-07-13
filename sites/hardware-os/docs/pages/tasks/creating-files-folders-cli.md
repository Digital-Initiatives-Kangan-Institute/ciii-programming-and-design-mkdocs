# Creating Files and Folders on the Linux Command Line

---

## Exercise 1: Making Directories

!!! abstract "Instructions"
    Open a Linux terminal. You are going to create a folder structure for a small website project.

    Create the following folder structure inside your home directory. Use only the command line — no file manager.

    ```text
    ~/website/
    ├── images/
    ├── styles/
    └── pages/
        ├── about/
        └── contact/
    ```

    After creating the folders, run `ls website` to verify the top-level folders exist. Then run `ls website/pages` to check the subfolders.

??? hint "Hint - You need two commands"
    `mkdir` creates a single folder. To create a folder and its subfolders in one step, use the `-p` option. Think about which folders you can create together and which need separate commands. Check `mkdir --help` if you are unsure about the `-p` flag.

---

## Exercise 2: Creating Files

!!! abstract "Instructions"
    Now populate the website folder with files. Using the command line, create these empty files:

    ```text
    ~/website/index.html
    ~/website/styles/style.css
    ~/website/pages/about/index.html
    ~/website/pages/contact/index.html
    ~/website/pages/contact/form.html
    ```

    After creating all the files, run `ls -R website` to see the full folder tree with all files. The `-R` option lists folders recursively — it shows everything inside every subfolder.

??? hint "Hint - Creating empty files"
    The `touch` command creates an empty file. For example, `touch notes.txt` creates a file called `notes.txt` in the current folder. You will need to either navigate into each folder with `cd` first, or write the full path with the filename in one `touch` command.

---

## Exercise 3: Moving and Renaming

!!! abstract "Instructions"
    You have decided to reorganise. Make the following changes using the command line:

    1. Rename the `styles` folder to `css`
    2. Create a new folder called `scripts` inside `website`
    3. Create an empty file called `main.js` inside `scripts`
    4. Move `form.html` from `pages/contact/` into the `pages/` folder
    5. List the full folder tree again with `ls -R website` to confirm everything is in the right place

??? hint "Hint - Rename vs move"
    Renaming a file or folder uses the same command as moving: `mv`. The difference is whether the second argument is a new name (rename) or a folder path (move). To rename `styles` to `css`, you are moving `styles` to a new name: `mv styles css`. To move a file into a folder, the second argument is the folder: `mv file.txt folder/`.

---

## Exercise 4: Copying and Cleaning Up

!!! abstract "Instructions"
    You want to make a backup copy of your CSS file before making changes. Then you want to delete a folder you no longer need.

    1. Copy `style.css` to `style-backup.css` inside the same `css` folder
    2. Delete the empty `about` folder (you are not ready to work on that page yet)
    3. List the tree one last time with `ls -R website` to confirm the changes

??? hint "Hint - Copy and delete"
    `cp` copies a file. The first argument is the source, the second is the destination. `rmdir` removes an empty folder — but it only works if the folder is completely empty. If you cannot delete the folder, use `ls` to check whether any hidden files are inside it (run `ls -a` to see hidden files). The `-r` option with `rm` removes a folder and everything inside it, but use it carefully.
