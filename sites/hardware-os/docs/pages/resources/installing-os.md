# Installing an Operating System

Installing an operating system is a foundational IT skill. Whether setting up a new computer, upgrading an existing system, or recovering from a failure, the installation process follows a consistent pattern across all operating systems.

---

## Before You Start

### Check System Requirements

Every OS has minimum and recommended hardware requirements. Always check these before starting.

| Component | Windows 11 Minimum | Ubuntu 24.04 Minimum |
|---|---|---|
| CPU | 1 GHz, 2+ cores, 64-bit | 2 GHz, 2+ cores, 64-bit |
| RAM | 4 GB | 4 GB |
| Storage | 64 GB | 25 GB |
| Display | 720p, >9" | 1024x768 |
| Other | TPM 2.0, Secure Boot | — |

### Back Up Your Data

If you are reinstalling an OS on a computer that already has data, back up all important files to an external drive or cloud storage first. The installation process will erase existing data.

### Gather What You Need

- **Installation media** — A bootable USB drive (at least 8 GB) or DVD with the OS installer
- **Product key / licence** — Required for Windows; macOS and most Linux distros are free
- **Driver software** — Downloads for network, graphics, and chipset drivers (as a backup)
- **Internet connection** — Wired or Wi-Fi for downloading updates during installation
- **Time** — Budget 30–90 minutes depending on the system and OS

***

## Creating Installation Media

To install an OS, you need bootable installation media. The process:

### Windows

1. Download the **Windows Media Creation Tool** from Microsoft's website
2. Run the tool and select **Create installation media**
3. Choose your USB drive (it will be reformatted — all data erased)
4. The tool downloads Windows and writes it to the USB drive

### Linux (Ubuntu)

1. Download the **Ubuntu ISO file** from ubuntu.com
2. Use a tool like **Rufus** (Windows) or **balenaEtcher** (cross-platform) to write the ISO to a USB drive
3. The tool makes the USB drive bootable

***

## The Installation Process

!!! note
    The steps below describe a general installation flow. Exact screens and options vary between operating systems and versions.

### Step 1: Boot from Installation Media

1. Insert the USB drive and restart the computer
2. Enter the boot menu or BIOS/UEFI setup — usually by pressing **F2**, **F12**, **Delete**, or **Esc** during startup
3. Select the USB drive as the boot device
4. The computer loads the OS installer from the USB drive

### Step 2: Choose Language and Region

The installer prompts you to select:

- Language
- Time and currency format
- Keyboard layout

### Step 3: Partition and Format the Drive

The installer needs to prepare the storage drive. You have two main options:

- **Erase disk and install** — Removes everything and sets up a clean partition layout. Use this for new installations or when you do not need to keep any data.
- **Manual partitioning** — Lets you create, resize, or choose specific partitions. Use this for dual-boot setups or advanced configurations.

Common partition types:

| Partition | Purpose |
|---|---|
| **EFI System Partition** | Required for UEFI boot (~100 MB, FAT32) |
| **Root partition ( / )** | Where the OS is installed |
| **Swap partition** | Virtual memory overflow (Linux) |
| **Home partition ( /home )** | User files (Linux, optional but recommended) |

### Step 4: Configure User Accounts

- Create a username and password
- Set up security questions or recovery options (Windows)
- The account you create during installation becomes an administrator account

### Step 5: Wait for Installation

The installer copies files, installs features, and configures the system. This typically takes 10–30 minutes. The computer may restart several times.

***

## Post-Installation Setup

After the OS is installed, there are several configuration steps to complete:

1. **Install updates** — Run Windows Update, or on Linux run:
   
   ```bash
   sudo apt update
   sudo apt upgrade
   ```
   
   (`sudo` gives you administrator permissions — the terminal will ask for your password.)
2. **Install drivers** — Check Device Manager (Windows) or Additional Drivers (Linux) for any missing drivers
3. **Configure security** — Enable firewall, ensure antivirus is active (Windows Defender is built in)
4. **Install essential software** — Web browser, office suite, communication tools
5. **Configure backup** — Set up File History (Windows), Time Machine (macOS), or a manual backup routine
6. **Personalise settings** — Display resolution, background, power settings

***

## Verifying the Installation

Confirm that the OS is correctly installed and functioning:

- The system boots without errors
- All hardware is detected (check Device Manager or `lspci`)
- Network connectivity works (test with a web browser)
- Sound and display output are working
- User account can log in and perform basic tasks

---

## Summary

- Check hardware requirements and back up data before starting
- Create bootable installation media using official tools
- Boot from the USB drive and follow the installer prompts
- Set up partitioning, user accounts, and regional settings
- Complete post-installation tasks: updates, drivers, security, backups
- Verify the system is functional before handing it over
