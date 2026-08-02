# Raspberry Pi Zero W

The Raspberry Pi is a series of small, low-cost, single-board computers developed by the Raspberry Pi Foundation. The **Pi Zero W** is a compact variant that adds built-in Wi-Fi and Bluetooth to the original Pi Zero — making it ideal for connected projects without needing additional adapters.

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

## Raspberry Pi Zero W Specifications

| Specification | Value |
|---|---|
| CPU | 1 GHz single-core ARM11 |
| RAM | 512 MB |
| Wi-Fi | 802.11 b/g/n (2.4 GHz) |
| Bluetooth | 4.1 |
| Video Output | Mini HDMI |
| USB | 1 × Micro-USB OTG |
| Storage | MicroSD |
| Power | Micro-USB (5V) |
| Size | 65 mm × 30 mm |

The Pi Zero W is not the most powerful model — the **Pi Zero 2 W** has a quad-core processor — but it is the most affordable option with built-in wireless connectivity.

***

## Pi Zero W vs Other Pi Models

| Feature | Pi Zero W | Pi Zero 2 W | Pi 4 Model B | Pi 5 |
|---|---|---|---|---|
| CPU | Single-core 1 GHz | Quad-core 1 GHz | Quad-core 1.8 GHz | Quad-core 2.4 GHz |
| RAM | 512 MB | 512 MB | 1–8 GB | 4–8 GB |
| USB Ports | 1 × Micro-USB OTG | 1 × Micro-USB OTG | 2 × USB 2.0, 2 × USB 3.0 | 2 × USB 2.0, 2 × USB 3.0 |
| Video | Mini HDMI | Mini HDMI | 2 × Micro HDMI | 2 × Micro HDMI |
| Ethernet | No | No | Gigabit | Gigabit |
| Wi-Fi | 2.4 GHz only | 2.4 GHz only | Dual-band (2.4/5 GHz) | Dual-band (2.4/5 GHz) |
| Price (approx.) | ~$15 AUD | ~$25 AUD | ~$55–$120 AUD | ~$80–$130 AUD |
| Best For | Low-cost connected projects | Embedded projects, light desktop | Desktop use, servers | Desktop replacement, heavy workloads |

Choose the Pi Zero W when you need wireless connectivity at the lowest cost. Choose the Pi Zero 2 W for more processing power, or the Pi 4/5 for desktop-class performance.

***

## Pi Zero W vs a Normal Computer

| Feature | Pi Zero W | Typical Desktop / Laptop |
|---|---|---|
| **Size** | 65 mm × 30 mm (credit card sized) | Tower case or laptop chassis |
| **Cost** | ~$15 AUD | $500–$2000+ AUD |
| **CPU** | 1 GHz single-core ARM | 2–5 GHz multi-core Intel/AMD |
| **RAM** | 512 MB | 8–32 GB |
| **Storage** | MicroSD card (you supply it) | Built-in SSD or HDD |
| **Operating System** | Raspberry Pi OS (Linux) | Windows, macOS, or Linux |
| **Power** | 2.5 W, powered via USB | 65–500+ W, plugged into mains |
| **Expandability** | USB ports only; no internal slots | Internal PCIe slots, drive bays, RAM slots |

The Pi Zero W is not a replacement for a normal desktop or laptop. It is designed for projects where a full-sized computer would be too large, too expensive, or uses too much power.

***

## Setting Up a Raspberry Pi Zero W

### What You Need

To get a Pi Zero W up and running, you will need:

- **Raspberry Pi Zero W** board
- **MicroSD card** (8 GB minimum, 16 GB or more recommended)
- **Micro-USB power supply** (5V, at least 1.2A; a phone charger often works)
- **Mini HDMI to HDMI adapter** (to connect a monitor)
- **Micro-USB OTG adapter** (to connect a standard USB keyboard/mouse or hub)
- **Optional** — A case to protect the board

### Installing the Operating System

The Raspberry Pi runs Raspberry Pi OS (formerly called Raspbian), a Debian-based Linux distribution optimised for the Pi hardware. The recommended option for the Pi Zero W is **Raspberry Pi OS Lite** — a minimal version without a desktop environment.

Use the **Raspberry Pi Imager** to write the OS to a microSD card. See the [Using Raspberry Pi Imager](raspberry-pi-imager.md) page for a full guide on downloading, installing, and using the tool — including how to pre-configure Wi-Fi and user credentials for a headless setup.

For details on using the OS, see [Raspberry Pi OS Lite](raspberry-pi-os-lite.md). To connect to the Pi remotely, see the [Connecting to a Raspberry Pi via SSH](../tasks/connecting-via-ssh.md) task.

***

## What Can You Do with a Pi Zero W?

The Pi Zero W's small size, low cost, built-in Wi-Fi, and low power consumption make it ideal for connected and embedded projects:

| Project | Description |
|---|---|
| **Retro gaming console** | Run RetroPie to emulate classic consoles (NES, SNES, Game Boy, etc.) |
| **Network ad blocker (Pi-hole)** | Block ads and trackers for every device on your home network |
| **Home automation controller** | Run Home Assistant to control smart lights, sensors, and switches |
| **Security camera** | Connect a Raspberry Pi Camera Module for a compact surveillance camera |
| **Media server** | Stream music, video, or photos to devices on your network |
| **Portable NAS** | Turn a USB drive into network-attached storage |
| **Weather station** | Connect temperature, humidity, and pressure sensors to log environmental data |

---

## Summary

- The Raspberry Pi Zero W is a full computer on a single small board, costing around $15 AUD
- It includes built-in Wi-Fi and Bluetooth — unlike the original Pi Zero
- It runs Raspberry Pi OS Lite (Linux) from a microSD card
- Use Raspberry Pi Imager to write the OS and pre-configure Wi-Fi and credentials
- It excels at low-cost, connected, and low-power projects
