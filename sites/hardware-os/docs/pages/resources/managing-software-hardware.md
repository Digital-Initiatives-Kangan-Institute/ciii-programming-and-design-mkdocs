# Managing Software and Hardware

Once an operating system is installed, the next tasks are installing application software and configuring hardware peripherals. This page covers how applications and drivers are installed across different operating systems, and how to connect and configure hardware components.

---

## Installing Application Software

Applications are the programs users run to perform tasks: web browsers, office suites, communication tools, and specialist software. The installation method varies by operating system.

### Windows

Windows offers several ways to install software:

| Method | Description |
|---|---|
| **Microsoft Store** | Built-in app store with curated, sandboxed applications |
| **Executable installer (.exe, .msi)** | Download from the vendor's website and run the installer |
| **Portable applications** | Self-contained programs that require no installation — just run the .exe |
| **Package managers (winget)** | CLI tool to search, install, and update software from a central repository |

**winget example:**
```cmd
winget install Mozilla.Firefox
```

The installer typically prompts for:
- Licence agreement acceptance
- Installation location (default is usually `C:\Program Files\`)
- Optional components or features
- Start menu shortcuts and desktop icons

### macOS

| Method | Description |
|---|---|
| **App Store** | Built-in curated marketplace for macOS applications |
| **DMG files** | Downloaded disk images — open, then drag the app to the Applications folder |
| **PKG installers** | Guided installation wizard, similar to Windows .msi files |
| **Homebrew** | Popular third-party CLI package manager (`brew install firefox`) |

### Linux

Linux distributions use package managers that download and install software from central repositories. This ensures compatibility and automatic updates. The command needs `sudo` because installing software affects the whole system — you will be asked for your password.

| Distro | Install Command |
|---|---|
| Ubuntu / Debian | `sudo apt install firefox` |
| Fedora | `sudo dnf install firefox` |
| Arch | `sudo pacman -S firefox` |

***

## Installing and Managing Hardware Drivers

A device driver is software that tells the operating system how to communicate with a specific piece of hardware. Without the correct driver, hardware either will not work or will work with limited functionality.

### How Drivers Work

```text
Application  →  OS  →  Driver  →  Hardware Device
```

When you plug in a printer, the OS needs a driver that understands the printer's communication protocol, print language, and capabilities. The application does not need to know any of this — it just sends a generic "print" command to the OS.

### Finding and Installing Drivers

| Source | When to Use |
|---|---|
| **Windows Update** | Automatically installs drivers for most common hardware |
| **Manufacturer's website** | Download the latest driver directly (e.g. NVIDIA, HP, Logitech) |
| **Device Manager** | Right-click a device → Update driver → Search automatically |
| **Included with the device** | Some hardware ships with a driver CD or USB drive |
| **Linux kernel** | Most drivers are built into the kernel and work automatically |
| **Additional Drivers (Ubuntu)** | GUI tool for installing proprietary drivers (NVIDIA, Wi-Fi) |

### Checking Driver Status

**Windows — Device Manager:**
- Devices with a yellow exclamation mark have driver issues
- Right-click any device → Properties → Driver tab for version and date
- Use **Action** → **Scan for hardware changes** after connecting a new device

**Linux — Command line:**
```bash
lspci      # Lists internal hardware and their drivers
lsusb      # Lists USB devices connected
```

***

## Connecting and Configuring Peripherals

### Common Connection Types

| Connection | Typical Devices | Setup Required |
|---|---|---|
| **USB** | Keyboard, mouse, printer, flash drive, webcam | Usually plug-and-play |
| **Bluetooth** | Wireless keyboard, mouse, headphones, speakers | Pairing required |
| **HDMI / DisplayPort** | Monitor, projector | May need to adjust resolution |
| **Wi-Fi** | Network access | Select network, enter password |
| **Ethernet** | Wired network | Usually plug-and-play; configure IP if not using DHCP |

### Configuring a New Monitor

1. Connect the monitor to the computer via HDMI, DisplayPort, or USB-C
2. The OS should detect it automatically
3. Open Display Settings to:
   - Set the correct resolution
   - Choose duplicate or extend desktop
   - Arrange monitor positions if using multiple displays
   - Adjust scaling if text and icons are too small or large

### Configuring a Printer

1. Connect via USB or add as a network printer
2. Windows: **Settings → Bluetooth & devices → Printers & scanners → Add device**
3. macOS: **System Settings → Printers & Scanners → Add Printer**
4. Linux: **Settings → Printers → Add Printer**
5. Install drivers if prompted; set as default printer if desired

### Configuring Audio Devices

- **System tray / menu bar** — Click the speaker icon to switch between output devices
- **Sound Settings** — Set input (microphone) and output (speakers/headphones) devices
- **Test** — Play a test sound to confirm the correct device is selected

***

## Software Configuration

After installing software, it often needs to be configured. Common configuration tasks include:

- **Set as default** — Make a browser, mail client, or media player the default for file types
- **Startup behaviour** — Control whether the app launches when you log in
- **File associations** — Specify which application opens which file types
- **User preferences** — Theme, language, autosave, privacy settings
- **Licence activation** — Enter a product key or sign in with an account

***

## Organisational Procedures

In a workplace environment, software and hardware installation must follow organisational procedures. These typically include:

- Only installing software from an approved list
- Obtaining authorisation before installing new hardware
- Documenting what was installed, when, and on which computer
- Using standard configurations so all workstations are consistent
- Testing that the installed software or hardware works correctly before handing over

---

## Summary

- Applications can be installed via app stores, downloaded installers, or package managers
- Drivers enable the OS to communicate with hardware — check Device Manager (Windows) or `lspci` (Linux)
- Most USB devices are plug-and-play; Bluetooth requires pairing
- Configure monitors, printers, and audio through system settings
- Follow organisational procedures when installing anything in a workplace
