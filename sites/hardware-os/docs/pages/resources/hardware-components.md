# Computer Hardware Components

Hardware refers to the physical parts of a computer — the components you can see and touch. Every computer, from a desktop workstation to a laptop, is built from a set of standard internal and external hardware components that work together.

---

## Internal Hardware Components

Internal components are housed inside the computer case. They are connected to the motherboard, which acts as the central communication hub.

### Central Processing Unit (CPU)

The CPU is the "brain" of the computer. It executes instructions from programs and performs calculations. CPU performance is measured in clock speed (GHz) and the number of cores.

| Specification | What It Means |
|---|---|
| **Clock Speed** | How many cycles per second the CPU can execute (e.g. 3.5 GHz = 3.5 billion cycles/second) |
| **Cores** | Independent processing units within the CPU — more cores allow more simultaneous work |
| **Threads** | Virtual cores that help manage multiple tasks at once |

Common manufacturers include Intel (Core i3, i5, i7, i9) and AMD (Ryzen 3, 5, 7, 9).

### Random Access Memory (RAM)

RAM is the computer's short-term, high-speed working memory. When you open a program or file, it is loaded from storage into RAM so the CPU can access it quickly. RAM is volatile — its contents are lost when the computer is powered off.

- Measured in gigabytes (GB) — typical systems have 8 GB to 32 GB
- More RAM allows more programs to run simultaneously without slowing down
- Common types: DDR4, DDR5

### Storage Drives

Storage provides long-term, non-volatile space for the OS, applications, and user files. There are two main types:

| Type | Strengths | Weaknesses |
|---|---|---|
| **Hard Disk Drive (HDD)** | Low cost per GB, high capacities | Slower, mechanical parts that can fail |
| **Solid State Drive (SSD)** | Very fast, no moving parts, durable | Higher cost per GB |

Modern systems typically use an SSD for the operating system and applications, with an optional HDD for bulk file storage.

### Motherboard

The motherboard is the main circuit board that connects all components together. It provides:

- The CPU socket
- RAM slots
- Expansion slots (PCIe for graphics cards, Wi-Fi cards, etc.)
- Storage connectors (SATA, M.2)
- USB headers, audio connectors, and power connections
- The chipset that controls data flow between components

### Power Supply Unit (PSU)

The PSU converts AC power from the wall outlet into the DC voltages that computer components require. It is rated by wattage — a typical office PC might use 300–500 W, while a high-end workstation could need 750 W or more.

### Graphics Processing Unit (GPU)

The GPU handles rendering images, video, and 3D graphics. Many CPUs include integrated graphics suitable for office work and web browsing. A dedicated GPU is needed for gaming, video editing, 3D modelling, and machine learning.

### Cooling

CPUs and GPUs generate significant heat that must be removed to prevent damage and keep the system stable. Cooling methods fall into two categories:

#### Passive Cooling

Passive cooling relies on natural heat dissipation — no moving parts, no power, no noise. A **heatsink** is a block of metal (usually aluminium or copper) with fins that increase surface area. Heat travels from the component into the heatsink and radiates into the surrounding air.

- Found in low-power devices like routers, thin clients, and the Raspberry Pi
- Silent and maintenance-free
- Less effective at removing large amounts of heat

#### Active Cooling

Active cooling uses powered components to force heat away. A fan blows air across a heatsink, dramatically increasing how much heat can be removed. Most desktop and laptop computers use active cooling.

- Much more effective than passive cooling alone
- Fans produce noise and can fail over time
- Liquid cooling (see below) is a form of active cooling that uses a pump instead of a fan on the component itself

Common active cooling solutions:

- **Air cooling** — A heatsink paired with one or more fans. This is the standard solution for most computers.
- **Liquid cooling** — A closed-loop system where a pump circulates liquid past the component to absorb heat, then through a radiator where fans cool the liquid. Used in high-performance and gaming PCs where air cooling is not enough.

***

## External Hardware Components

External components, also called peripherals, connect to the computer from outside the case.

### Input Devices

| Device | Purpose |
|---|---|
| **Keyboard** | Text entry and keyboard shortcuts |
| **Mouse / Trackpad** | Pointing, clicking, and navigation |
| **Scanner** | Converts physical documents into digital files |
| **Microphone** | Audio input for calls, recording, voice commands |
| **Webcam** | Video input for conferencing and streaming |

### Output Devices

| Device | Purpose |
|---|---|
| **Monitor / Display** | Visual output — screen size and resolution affect clarity |
| **Printer** | Produces physical copies of documents and images |
| **Speakers / Headphones** | Audio output |
| **Projector** | Large-format display for presentations |

### External Storage

- **USB flash drives** — Portable, small capacity
- **External HDDs and SSDs** — Larger capacity for backups and file transfer
- **Memory cards (SD, microSD)** — Used in cameras, phones, and some laptops

***

## Ports and Connectors

External devices connect through standard ports:

| Port | Image | Common Uses |
|---|---|---|
| **USB-A** | Rectangular | Keyboards, mice, flash drives, printers |
| **USB-C** | Oval, reversible | Modern peripherals, charging, external displays |
| **HDMI** | Trapezoid shape | Monitors, TVs, projectors |
| **DisplayPort** | Similar to HDMI with one notched corner | High-resolution computer monitors |
| **Ethernet (RJ45)** | Wide, with clip | Wired network connection |
| **3.5 mm Audio Jack** | Round | Headphones, speakers, microphones |

***

## Hardware Specifications

When comparing or purchasing hardware, key specifications to check include:

- **CPU** — Clock speed, cores, generation
- **RAM** — Capacity and speed (MHz)
- **Storage** — Type (SSD/HDD) and capacity (GB/TB)
- **GPU** — Integrated or dedicated, video memory (VRAM)
- **Ports** — USB types, HDMI, SD card slot
- **Wireless** — Wi-Fi and Bluetooth versions

---

## Summary

- Internal components include the CPU, RAM, storage, motherboard, PSU, GPU, and cooling
- External peripherals include input devices, output devices, and external storage
- Ports and connectors provide standard ways to attach peripherals
- Understanding hardware specifications helps you select the right equipment for a given task
- The motherboard ties everything together as the central communication hub
