# Raspberry Pi OS Lite

Raspberry Pi OS Lite is the minimal, command-line-only version of Raspberry Pi OS. It has no desktop environment, no graphical applications, and a small disk footprint — making it ideal for headless projects, servers, and embedded devices where resources are limited.

---

## What is Raspberry Pi OS?

Raspberry Pi OS (formerly called Raspbian) is a Debian-based Linux distribution maintained by the Raspberry Pi Foundation. It is optimised to run on Raspberry Pi hardware and comes in three variants:

| Variant | Desktop | Recommended Use |
|---|---|---|
| **Raspberry Pi OS with Desktop** | Full desktop environment | General-purpose use with a monitor |
| **Raspberry Pi OS with Desktop and Recommended Software** | Desktop + pre-installed apps | Beginners, education |
| **Raspberry Pi OS Lite** | None (command line only) | Headless projects, servers, embedded devices |

Raspberry Pi OS Lite boots directly to a command-line login prompt. You interact with it entirely through the terminal — either by connecting a keyboard and monitor, or by connecting remotely over SSH.

***

## Installing Raspberry Pi OS Lite

The standard way to install Raspberry Pi OS Lite is with the **Raspberry Pi Imager** tool. See the [Using Raspberry Pi Imager](raspberry-pi-imager.md) page for a full guide on downloading, installing, and using the tool — including how to pre-configure Wi-Fi and user credentials for a headless setup.

Once the OS is written and the Pi has booted, you can connect to it remotely. See the [Connecting to a Raspberry Pi via SSH](../tasks/connecting-via-ssh.md) task for instructions on finding the Pi's IP address and connecting.

---

## Keeping Your System Up to Date

Like all Debian-based Linux systems, Raspberry Pi OS uses the **APT** (Advanced Package Tool) package manager to install, update, and remove software. Before installing any new software, it is good practice to update the package lists and upgrade existing packages.

### Updating Package Lists

```bash
sudo apt update
```

This command downloads the latest package information (names, versions, dependencies) from the repositories. It does **not** install or upgrade any packages — it only refreshes the list of what is available.

### Upgrading Installed Packages

```bash
sudo apt upgrade
```

This command installs the newest versions of all packages currently on your system. You should run `apt update` first so that APT knows which packages have newer versions available.

### Running Both Together

A common workflow is to run both commands in sequence:

```bash
sudo apt update && sudo apt upgrade -y
```

The `-y` flag automatically answers "yes" to any prompts, which is useful for scripted or remote sessions.

***

## Installing Software

### Installing a Single Package

To install a new package, use `apt install` followed by the package name:

```bash
sudo apt install nano
```

APT will show you which packages will be installed and how much disk space they will use. Confirm with `Y` (or use `-y` to skip the prompt).

### Installing Multiple Packages

You can install several packages at once by listing them separated by spaces:

```bash
sudo apt install git curl wget htop
```

### Finding Packages

If you know part of a package name but not the full name, search for it:

```bash
apt search <keyword>
```

For example:

```bash
apt search python3
```

To see detailed information about a specific package before installing:

```bash
apt show <package-name>
```

### Removing Packages

To remove a package you no longer need:

```bash
sudo apt remove <package-name>
```

To remove a package and its configuration files:

```bash
sudo apt purge <package-name>
```

To free up disk space by removing downloaded package files:

```bash
sudo apt autoremove
```

***

## Useful Packages for Beginners

Here are some commonly used packages on a headless Raspberry Pi:

| Package | Description |
|---|---|
| `nano` | Simple command-line text editor |
| `vim` | Advanced command-line text editor |
| `git` | Version control system |
| `curl` | Tool for transferring data from URLs |
| `wget` | Tool for downloading files from the web |
| `htop` | Interactive process viewer (better than `top`) |
| `tmux` | Terminal multiplexer — run multiple sessions in one window |
| `python3` | Python programming language (pre-installed on most images) |
| `build-essential` | GCC, make, and other tools for compiling software |

To install several of these at once:

```bash
sudo apt install nano git curl wget htop tmux build-essential -y
```

---

## Summary

- Raspberry Pi OS Lite is a minimal, command-line-only Linux distribution for Raspberry Pi
- Use Raspberry Pi Imager to write it to a microSD card with pre-configured SSH and Wi-Fi
- Always run `sudo apt update` before `sudo apt upgrade` to keep your system current
- Install software with `sudo apt install <package-name>`
- Remove software with `sudo apt remove <package-name>`
- Use `apt search` and `apt show` to find and learn about available packages
