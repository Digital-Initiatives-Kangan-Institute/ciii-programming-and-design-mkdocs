# Optimisation Tools and Vendor Utilities

Over time, computers tend to slow down. Storage fills up, unnecessary programs launch at startup, and updates go uninstalled. A range of software exists to keep systems running well, falling into two broad groups: optimisation tools built into the operating system, and utilities provided by hardware and software vendors.

---

## Keeping a System Running Well

Optimisation is about performance, efficiency, and reliability. Rather than being a one-off fix, it is a set of small, regular housekeeping tasks:

- Freeing up storage by removing temporary and unnecessary files
- Managing what launches at startup so the machine boots and responds faster
- Keeping the operating system and applications updated
- Watching resource usage — processor, memory, and disk — to spot what is slowing the machine down

Much of this is handled by tools built into the operating system. Windows includes Disk Cleanup and Storage Sense for reclaiming space and Task Manager for monitoring; Linux offers package cleanup commands and tools such as `top` and `htop`. For a step-by-step look, see [System Optimisation and Maintenance](system-optimisation.md).

---

## Tools Provided by Vendors

Beyond the built-in tools, manufacturers ship their own software for the products they make. The reasoning is simple: the vendor knows its hardware best, so it provides a utility to help users and technicians get the most out of it.

These tools do a variety of jobs, often several at once:

- Checking hardware health and running diagnostics to find faults
- Delivering firmware and driver updates
- Adjusting device settings and configuration
- Monitoring temperatures, usage, and drive health
- Viewing and managing the devices connected to a system

Rather than memorising a list of brand names, it is more useful to think in terms of *what the tool helps you do*. Some familiar examples: storage makers such as Samsung and Western Digital provide tools for drive health and firmware, graphics vendors such as NVIDIA and AMD provide tools for driver updates and performance, and Intel provides a driver and support assistant for its components. System vendors such as HP, Dell, and Lenovo bundle tools that combine diagnostics, driver updates, and warranty checks in one place.

The same activities also appear in the tools built into operating systems — Windows Update and Linux package managers handle updates, Device Manager and `lsusb`/`lspci` list devices, and Task Manager and `top`/`htop` handle monitoring. On devices such as the Raspberry Pi, `raspi-config` covers system configuration and the manufacturer provides diagnostic utilities of its own.

---

## Summary

- Optimisation tools improve performance, efficiency, and reliability through regular housekeeping such as cleanup, startup management, updates, and monitoring
- Vendor utilities are manufacturer-provided software for configuring, monitoring, maintaining, diagnosing, updating, or managing their products
- The same kinds of utilities appear across Windows, Linux, and devices such as the Raspberry Pi
- It is more useful to understand what a tool does than to memorise specific program names
