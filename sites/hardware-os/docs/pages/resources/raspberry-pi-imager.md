# Using Raspberry Pi Imager

**Raspberry Pi Imager** is the official tool for writing operating system images to microSD cards for use with Raspberry Pi computers. It simplifies the process of downloading, preparing, and configuring an OS — all in one application.

---

## Downloading and Installing

Raspberry Pi Imager is available for Windows, macOS, and Linux. Download it from the official website:

[raspberrypi.com/software](https://www.raspberrypi.com/software/)

Install it like any other application on your operating system. Once installed, launch it — you will see the main screen with three buttons: **Choose Device**, **Choose OS**, and **Choose Storage**.

***

## The Three-Step Process

Writing an OS to a microSD card with Imager follows three steps:

### 1. Choose Device

Click **Choose Device** and select the Raspberry Pi model you are writing for. This tells Imager which hardware the OS image should be optimised for.

If you are unsure which model you have, check the label printed on the circuit board — the model name is usually written in white text.

### 2. Choose OS

Click **Choose OS** to browse the available operating systems. The main options are:

| Option | Description |
|---|---|
| **Raspberry Pi OS (32-bit)** | Full desktop with recommended software — best for beginners with a monitor |
| **Raspberry Pi OS (32-bit) Lite** | Command-line only, no desktop — ideal for headless and server projects |
| **Raspberry Pi OS (64-bit)** | 64-bit version — requires a Pi 3 or newer |
| **Other general-purpose OS** | Ubuntu, Manjaro, and other Linux distributions |
| **Emulation and game OS** | RetroPie, Lakka, and similar retro-gaming distributions |
| **Media player OS** | LibreELEC, OSMC, and other media centre distributions |
| **Other specific-purpose OS** | Pi-hole, OctoPrint, Home Assistant, and more |

You can also click **Use custom** to select a downloaded `.img` or `.img.xz` file from your computer — useful for operating systems not listed in the Imager menu.

### 3. Choose Storage

Click **Choose Storage** and select the microSD card you want to write to.

!!! warning "Double-check your selection"
    The Imager will overwrite **everything** on the selected drive. Make sure you have chosen the correct microSD card — not an external hard drive or USB stick with important data on it.

---

## Advanced Settings (The Gear Icon)

After selecting your device, OS, and storage, click the **gear icon** (⚙) in the bottom-right corner of the Imager window. This opens the **Advanced Options** menu, which lets you pre-configure settings that would otherwise require a monitor, keyboard, and mouse.

### General Options

| Setting | Description |
|---|---|
| **Set hostname** | Sets the network name of your Pi (e.g. `raspberrypi`). Other devices on the network will see it as `<hostname>.local` |
| **Set username and password** | Creates a user account with your chosen credentials. If you do not set this, the default `pi` / `raspberry` credentials are used (not recommended) |
| **Set locale settings** | Configure timezone and keyboard layout |

### Service Options

| Setting | Description |
|---|---|
| **Set SSH** | Enables the SSH server so you can connect to your Pi remotely over the network. Choose **Use password authentication** or **Use public-key authentication** |
| **Set Wi-Fi** | Enter your Wi-Fi network name (SSID), password, and country code so the Pi connects to Wi-Fi automatically on first boot |

!!! tip "Headless setup"
    For a headless setup (no monitor, keyboard, or mouse), enable **SSH** and **Set Wi-Fi** in the advanced options. This allows you to connect to your Pi over the network as soon as it boots.

### Other Options

| Setting | Description |
|---|---|
| **Skip first-run actions** | Disables the automatic setup wizard that runs on first boot |

---

## Writing the OS

Once your device, OS, storage, and advanced settings are all configured, click **Next**. Imager will show a summary of what it is about to do.

Click **Yes** to confirm. Imager will:

1. Download the OS image (if it is not already cached)
2. Write the image to the microSD card
3. Verify that the write was successful

This process can take several minutes depending on the size of the OS image and the speed of your microSD card and card reader.

When the process is complete, you will see a confirmation message. Click **Continue** and safely eject the microSD card from your computer.

---

## Inserting the Card and Booting

1. Insert the microSD card into the microSD slot on your Raspberry Pi
2. Connect peripherals (monitor, keyboard, mouse) if you are not running headless
3. Connect power — the Pi will boot automatically

If you pre-configured SSH and Wi-Fi in the Imager, you can connect remotely from another computer:

```bash
ssh <username>@<hostname>.local
```

For example:

```bash
ssh pi@raspberrypi.local
```

On the first connection, your computer may ask you to confirm the host key fingerprint. Type `yes` to continue.

---

## Troubleshooting

### The Imager does not detect my microSD card

- Remove and reinsert the card
- Try a different card reader or USB port
- On Linux, check that you have the necessary permissions — you may need to run the Imager with `sudo` or add your user to the `disk` group

### The write fails or gets stuck

- Try a different microSD card — some cards have unreliable write performance
- Use a high-quality card reader connected directly to your computer (not through a USB hub)
- Close other applications that might be accessing the card

### The Pi does not boot

- Make sure you selected the correct device model in the Imager
- Try writing the OS image again with a fresh card
- Check that the microSD card is fully inserted in the Pi
- If using a Pi Zero W, make sure you are using a micro-USB power supply providing at least 1.2A

### I forgot the username or password I set

Re-insert the microSD card into your computer, open the Imager again, and write a fresh image with new credentials. There is no way to recover a lost password from the Imager — you would need to mount the card on a Linux system and reset it manually.

---

## Summary

- Raspberry Pi Imager is the official tool for writing OS images to microSD cards
- It works on Windows, macOS, and Linux
- The three-step process is: **Choose Device** → **Choose OS** → **Choose Storage**
- Use the **gear icon** (⚙) to pre-configure SSH, Wi-Fi, hostname, and user credentials
- Pre-configuring SSH and Wi-Fi enables a fully headless setup with no monitor or keyboard needed
- Always double-check the selected storage device before writing — the process overwrites the entire card
