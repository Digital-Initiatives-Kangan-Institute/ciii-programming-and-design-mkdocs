# Installing and Managing Software on Raspberry Pi

---

## Scenario

Your Raspberry Pi is set up and connected, but it has a minimal installation. You need to install tools and software for a project — a text editor, a web server, and a Python library. You will use the APT package manager to manage all software on the system.

Before you begin, make sure your system is up to date by running:

```bash
sudo apt update && sudo apt upgrade -y
```

!!! warning "The upgrade will take a while"
    On a Raspberry Pi Zero W the first `sudo apt upgrade` will take a while — often 15 minutes or more — because the single-core CPU and 512 MB of RAM have to download and install every available update. A slow SD card or network connection can make it even longer. Do not switch off the Pi or close the SSH session while it is running; interrupting it can leave the system in a broken state.

---

## Exercise 1: Searching for Packages

!!! abstract "Instructions"
    Before installing anything, you need to find the right package names. Use `apt search` to answer the following:

    1. Search for a text editor called `nano` — what is the full package description?
    2. Search for packages related to "web server". What are the first three results?
    3. Search for packages related to "python3 pillow" (a Python image library). Is it available?
    4. Use `apt show` to get detailed information about the `git` package. How much disk space does it say it will need?

??? hint "Hint - search vs show"
    `apt search <keyword>` returns a list of packages matching that keyword — use it when you are not sure of the exact package name. `apt show <package-name>` gives you detailed information about one specific package, including its version, size, dependencies, and description. Use `apt search` first to find the name, then `apt show` to learn more.

---

## Exercise 2: Installing Software

!!! abstract "Instructions"
    Install the following packages one at a time. After each installation, confirm it was successful by running the command that starts the program (e.g. `nano --version`).

    1. Install `nano` — a simple command-line text editor
    2. Install `htop` — an interactive process viewer
    3. Install `git` — a version control system
    4. Install all three in a single command instead:

    ```bash
    sudo apt install nano htop git -y
    ```

    What is the advantage of installing multiple packages in one command?

??? hint "Hint - Confirming installation"
    After installing a package, you can check it worked by running the program. For `nano`, try `nano --version`. For `htop`, try `htop --version`. For `git`, try `git --version`. The `-y` flag in `apt install` automatically answers "yes" to the confirmation prompt — useful when you know exactly what you are installing.

---

## Exercise 3: Installing a Web Server

!!! abstract "Instructions"
    You are going to install and start the Apache web server — one of the most common web servers on Linux.

    1. Search for the Apache web server package — what is the package name?
    2. Install it using `apt install`
    3. Check if the service is running with:

    ```bash
    systemctl status apache2
    ```

    4. If it says "active (running)", the server is working. If it is stopped, start it with:

    ```bash
    sudo systemctl start apache2
    ```

    5. Use `curl localhost` to request the web page from your Pi. What does it return?

??? hint "Hint - systemctl and services"
    `systemctl` is the command for managing services (background programs) on Linux. `systemctl status <service>` checks if it is running. `systemctl start <service>` starts it. `systemctl stop <service>` stops it. `systemctl enable <service>` makes it start automatically when the Pi boots. The Apache web server package on Debian-based systems is called `apache2` (not `apache`).

---

## Exercise 4: Managing Services

!!! abstract "Instructions"
    Now that Apache is installed, practice managing it:

    1. Stop the Apache service. Verify it is stopped using `systemctl status`
    2. Try `curl localhost` again — what happens when the web server is stopped?
    3. Start the Apache service again
    4. Enable Apache to start automatically when the Pi boots with:

    ```bash
    sudo systemctl enable apache2
    ```

    5. Disable it from starting automatically with:

    ```bash
    sudo systemctl disable apache2
    ```

    6. Check the status one more time — is it still running? What changed?

??? hint "Hint - enable vs start"
    `start` and `stop` control whether a service is running right now. `enable` and `disable` control whether it starts automatically at boot. A service can be running but not enabled (it will stop if you reboot), or enabled but not running (it will start next time you reboot). These are independent settings.

---

## Exercise 5: Checking Installed Software and Disk Space

!!! abstract "Instructions"
    Managing software also means knowing what is installed and how much space it uses.

    1. List all installed packages on your system — there will be hundreds. How many are there? (Count the lines)

    ```bash
    apt list --installed | wc -l
    ```

    2. Check how much disk space is used and available on your Pi:

    ```bash
    df -h
    ```

    What does the `-h` flag do? How much space is available on the root partition?

    3. Use `du -sh /var/cache/apt` to check how much space the APT cache is using. This folder stores downloaded package files.

    4. Free up space by removing cached package files:

    ```bash
    sudo apt clean
    ```

    Check the cache size again — how much space did you free?

??? hint "Hint - df and du"
    `df` (disk free) shows filesystem-level disk usage. The `-h` flag makes sizes human-readable (e.g. "1.2G" instead of "1200000"). `du` (disk usage) shows the size of specific directories. The `-s` flag gives a summary (just the total), and `-h` makes it human-readable. `apt clean` removes downloaded package files that are no longer needed — it is safe to run and frees space.

---

## Exercise 6: Removing Software

!!! abstract "Instructions"
    You no longer need Apache on your Pi. Remove it and clean up:

    1. Stop the Apache service if it is running
    2. Remove Apache with `apt remove`. What is the package name?
    3. After removing it, check if the package is still listed as installed
    4. Search for any remaining Apache configuration files and remove them with `apt purge`
    5. Run `sudo apt autoremove` to clean up any dependencies that were installed with Apache but are no longer needed
    6. Check your disk space again with `df -h` — has the available space increased?

??? hint "Hint - remove vs purge vs autoremove"
    `apt remove` uninstalls a package but keeps its configuration files (in case you want to reinstall later). `apt purge` removes both the package and its configuration files. `apt autoremove` finds packages that were installed as dependencies of other packages but are no longer needed. Running all three in sequence is the standard way to fully clean up a package.
