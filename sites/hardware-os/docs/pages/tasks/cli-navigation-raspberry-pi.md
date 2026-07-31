# Navigating the Raspberry Pi CLI

---

## Scenario

You have just set up a Raspberry Pi Zero W running Raspberry Pi OS Lite and connected to it via SSH. You need to get familiar with the command-line interface — navigating folders, exploring the filesystem, and understanding where things are stored on a Linux system.

---

## Exercise 1: Exploring Your Location

!!! abstract "Instructions"
    When you first log in, you are placed in your home directory. Run each of the following commands and write down what each one shows you.

    1. `pwd` — What does this show? Where are you?
    2. `ls` — What files and folders are listed?
    3. `ls -a` — What additional items appear with the `-a` flag? What are the `.` and `..` entries?
    4. `ls -la` — What does the `-l` flag add? What information is shown for each file or folder?

    In your own words, describe the difference between `ls`, `ls -a`, and `ls -la`.

??? hint "Hint - What the flags mean"
    The `-a` flag stands for "all" — it shows hidden files and folders, which are names that start with a dot (`.`). The `-l` flag stands for "long" — it shows a detailed list format with permissions, owner, size, and modification date. Think about what information would be useful to a system administrator.

---

## Exercise 2: Moving Between Directories

!!! abstract "Instructions"
    Using the command line, complete the following tasks. After each step, run `pwd` to confirm where you are.

    1. Navigate into the `/etc` directory. List its contents — how many items are there?
    2. Navigate into the `ssh` subfolder inside `/etc`. What files are in there?
    3. Navigate back to your home directory in one command (not by pressing `cd` multiple times)
    4. Navigate to the root directory `/`. List its contents. What top-level folders do you see?

??? hint "Hint - Going up and going home"
    `cd ..` moves you up one level (into the parent folder). `cd ~` or just `cd` with no arguments takes you straight to your home directory. `cd /` takes you to the very top of the filesystem — the root.

---

## Exercise 3: Finding Files and Folders

!!! abstract "Instructions"
    Linux has powerful tools for finding files. Complete the following:

    1. Use `find /etc -name "hostname"` to locate the file called `hostname` inside `/etc`. What is the full path? What does the file contain? (Use `cat` to read it)
    2. Use `find /etc -name "*.conf"` to find all files ending in `.conf` inside `/etc`. How many results do you get?
    3. Use `find / -name "sshd_config" 2>/dev/null` to search the entire filesystem for `sshd_config`. Where is it located? The `2>/dev/null` part hides permission error messages — this is normal.
    4. Use `which python3` to find where the `python3` command is located on the system.

??? hint "Hint - The find command"
    `find` searches through directories. The general form is `find <where> -name "<what>"`. The `*` character is a wildcard — it matches any characters. So `"*.conf"` means "any filename that ends in `.conf`". The `which` command is simpler — it tells you where a specific program is installed.

---

## Exercise 4: Reading File Contents

!!! abstract "Instructions"
    Linux provides several commands for reading files. Practice using them:

    1. Run `cat /etc/os-release` — what operating system information is shown?
    2. Run `head /etc/passwd` — how many lines does `head` show by default? What information is in each line?
    3. Run `tail /etc/passwd` — what does `tail` show compared to `head`?
    4. Run `wc -l /etc/passwd` — how many lines are in the file? What does `wc` stand for?
    5. Use `grep` to search for your username inside `/etc/passwd`:

    ```bash
    grep <your-username> /etc/passwd
    ```

    What information does it return about your user?

??? hint "Hint - cat, head, tail, and grep"
    `cat` displays the entire file contents at once. `head` shows just the beginning (10 lines by default). `tail` shows the end. `wc -l` counts the number of lines. `grep` searches for a pattern inside a file — it is like a text search tool. Each of these commands is useful in different situations: `cat` for small files, `head`/`tail` for large files, and `grep` for finding specific information.

---

## Exercise 5: Understanding File Permissions

!!! abstract "Instructions"
    Run `ls -l /etc/passwd` and examine the output. The first column shows permissions like `-rw-r--r--`.

    1. Write down the permissions string for `/etc/passwd`
    2. How many characters is it? Break it into groups and describe what each group means
    3. Now run `ls -l ~/` and look at your home directory permissions. What is different about directories compared to files?
    4. Run `ls -ld /etc` to see the permissions of the `/etc` directory itself (without listing its contents). What does the `d` at the start mean?

??? hint "Hint - Permission groups"
    Permissions are divided into three groups: **owner**, **group**, and **others**. Each group has three permission types: `r` (read), `w` (write), and `x` (execute). A `-` means that permission is not granted. For the owner of `/etc/passwd`, notice which permissions are present and which are not — the file is readable and writable but not executable. The `d` at the start of a permissions string means the item is a directory, not a regular file.
