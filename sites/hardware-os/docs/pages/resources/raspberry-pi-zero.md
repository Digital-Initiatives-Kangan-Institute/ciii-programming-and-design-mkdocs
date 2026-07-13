# Raspberry Pi Zero

The Raspberry Pi is a series of small, low-cost, single-board computers developed by the Raspberry Pi Foundation. The Pi Zero is the smallest and most affordable model in the range — a fully functional computer about the size of a stick of gum.

---

## What is a Single-Board Computer?

A single-board computer (SBC) packs all the core components of a computer onto one circuit board:

- CPU and RAM (soldered directly to the board)
- GPU for graphics output
- USB ports for peripherals
- Video output (mini HDMI)
- Storage via microSD card

Unlike a desktop PC, there are no expansion slots, no separate graphics card, and no internal drive bays. Everything you need is on one board, and you add only what you need via USB.

***

## Raspberry Pi Zero Specifications

The Pi Zero is available in several variants:

| Specification | Pi Zero | Pi Zero W | Pi Zero 2 W |
|---|---|---|---|
| CPU | 1 GHz single-core ARM11 | 1 GHz single-core ARM11 | 1 GHz quad-core Cortex-A53 |
| RAM | 512 MB | 512 MB | 512 MB |
| Wi-Fi | No | 802.11 b/g/n (2.4 GHz) | 802.11 b/g/n (2.4 GHz) |
| Bluetooth | No | 4.1 | 4.2 |
| Video Output | Mini HDMI | Mini HDMI | Mini HDMI |
| USB | 1 × Micro-USB OTG | 1 × Micro-USB OTG | 1 × Micro-USB OTG |
| Storage | MicroSD | MicroSD | MicroSD |
| Power | Micro-USB (5V) | Micro-USB (5V) | Micro-USB (5V) |
| Size | 65 mm × 30 mm | 65 mm × 30 mm | 65 mm × 30 mm |

The **Pi Zero 2 W** is the most capable current model, with a quad-core processor that handles light desktop use, web browsing, and programming tasks.

***

## Pi Zero vs a Normal Computer

The Pi Zero works like any other computer, but there are important differences to be aware of:

| Feature | Pi Zero 2 W | Typical Desktop / Laptop |
|---|---|---|
| **Size** | 65 mm × 30 mm (credit card sized) | Tower case or laptop chassis |
| **Cost** | ~$25 AUD | $500–$2000+ AUD |
| **CPU** | 1 GHz quad-core ARM | 2–5 GHz multi-core Intel/AMD |
| **RAM** | 512 MB | 8–32 GB |
| **Storage** | MicroSD card (you supply it) | Built-in SSD or HDD |
| **Operating System** | Raspberry Pi OS (Linux) | Windows, macOS, or Linux |
| **Power** | 2.5 W, powered via USB | 65–500+ W, plugged into mains |
| **Expandability** | USB ports only; no internal slots | Internal PCIe slots, drive bays, RAM slots |

The Pi Zero is not a replacement for a normal desktop or laptop. It is designed for projects where a full-sized computer would be too large, too expensive, or uses too much power. For everyday tasks like word processing, web browsing, and watching videos, a standard computer is the better choice.

***

## Setting Up a Raspberry Pi Zero

### What You Need

To get a Pi Zero up and running, you will need:

- **Raspberry Pi Zero** board (any variant)
- **MicroSD card** (8 GB minimum, 16 GB or more recommended)
- **Micro-USB power supply** (5V, at least 1.2A; a phone charger often works)
- **Mini HDMI to HDMI adapter** (to connect a monitor)
- **Micro-USB OTG adapter** (to connect a standard USB keyboard/mouse or hub)
- **Optional** — A case to protect the board

### Installing the Operating System

The Raspberry Pi runs Raspberry Pi OS (formerly called Raspbian), a Debian-based Linux distribution optimised for the Pi hardware. Other operating systems are also available, including Ubuntu and specialised media centre and retro-gaming distributions.

#### Using Raspberry Pi Imager

The easiest way to prepare a microSD card is with the **Raspberry Pi Imager** tool:

1. Download and install Raspberry Pi Imager from [raspberrypi.com/software](https://www.raspberrypi.com/software/)
2. Insert your microSD card into your computer
3. Open Raspberry Pi Imager
4. Click **Choose Device** → Select **Raspberry Pi Zero 2 W** (or Pi Zero)
5. Click **Choose OS** → Select **Raspberry Pi OS (32-bit)** (the Lite version if using headless)
6. Click **Choose Storage** → Select your microSD card
7. Click the gear icon to configure advanced settings:
   - Set a hostname
   - Enable SSH for remote access
   - Configure Wi-Fi (SSID and password)
   - Set username and password
8. Click **Write** and wait for the process to complete

#### Headless Setup

A **headless** setup means running the Pi without a monitor, keyboard, or mouse attached. This is common for projects where the Pi is embedded in a device or accessed remotely.

For a headless setup, choose **Raspberry Pi OS Lite** (no desktop) and enable both SSH and Wi-Fi in the Imager settings. Once the Pi boots, you can connect to it from another computer via SSH:

```bash
ssh pi@raspberrypi.local
```

Replace `raspberrypi.local` with the hostname you set in Imager, and `pi` with your username.

---

## What Can You Do with a Pi Zero?

The Pi Zero's small size, low cost, and low power consumption make it ideal for embedded and portable projects:

| Project | Description |
|---|---|
| **Retro gaming console** | Run RetroPie to emulate classic consoles (NES, SNES, Game Boy, etc.) |
| **Network ad blocker (Pi-hole)** | Block ads and trackers for every device on your home network |
| **Home automation controller** | Run Home Assistant to control smart lights, sensors, and switches |
| **Security camera** | Connect a Raspberry Pi Camera Module for a compact surveillance camera |
| **Media server** | Stream music, video, or photos to devices on your network |
| **Portable NAS** | Turn a USB drive into network-attached storage |
| **Weather station** | Connect temperature, humidity, and pressure sensors to log environmental data |
| **Desktop computer** | With a hub, keyboard, mouse, and monitor, browse the web and edit documents |

***

## Raspberry Pi Zero vs Other Pi Models

| Feature | Pi Zero 2 W | Pi 4 Model B | Pi 5 |
|---|---|---|---|
| CPU | Quad-core 1 GHz | Quad-core 1.8 GHz | Quad-core 2.4 GHz |
| RAM | 512 MB | 1–8 GB | 4–8 GB |
| USB Ports | 1 × Micro-USB OTG | 2 × USB 2.0, 2 × USB 3.0 | 2 × USB 2.0, 2 × USB 3.0 |
| Video | Mini HDMI | 2 × Micro HDMI | 2 × Micro HDMI |
| Ethernet | No | Gigabit | Gigabit |
| Wi-Fi | 2.4 GHz only | Dual-band (2.4/5 GHz) | Dual-band (2.4/5 GHz) |
| Price (approx.) | ~$25 AUD | ~$55–$120 AUD | ~$80–$130 AUD |
| Best For | Embedded projects, low power | Desktop use, servers, general purpose | Desktop replacement, heavy workloads |

Choose the Pi Zero when size, cost, and power consumption are priorities. Choose the Pi 4 or Pi 5 when you need more RAM, faster USB, dual displays, or a smoother desktop experience.

---

## Summary

- The Raspberry Pi Zero is a full computer on a single small board, starting at about $25 AUD
- It runs Linux (Raspberry Pi OS) from a microSD card
- Use Raspberry Pi Imager to write the OS and pre-configure Wi-Fi and SSH
- The Pi Zero excels at embedded, portable, and low-power projects
- For desktop computing or heavier workloads, consider a Pi 4 or Pi 5 instead
