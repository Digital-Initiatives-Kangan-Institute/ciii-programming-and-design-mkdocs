# System Optimisation and Maintenance

Over time, computer performance can degrade. Files accumulate, storage fills up, startup programs multiply, and outdated software creates vulnerabilities. Regular system optimisation and maintenance keeps a computer running smoothly, securely, and efficiently.

---

## Why Optimise Your System?

Optimisation improves:

- **Boot time** — The computer starts faster after pressing the power button
- **Responsiveness** — Applications open and respond more quickly
- **Storage space** — Removing unnecessary files frees up disk capacity
- **Stability** — Fewer crashes, hangs, and unexpected behaviour
- **Security** — Updates close vulnerabilities that attackers could exploit

Optimisation is not a one-time task. It should be performed regularly — monthly for most users, more often on heavily used systems.

***

## Disk Cleanup

Temporary files, system caches, downloads, and old update files consume disk space over time.

### Windows — Disk Cleanup

1. Open **Disk Cleanup** from the Start menu
2. Select the drive you want to clean (usually C:)
3. Tick the file types to remove:
   - Temporary Internet Files
   - Downloaded Program Files
   - Recycle Bin
   - Temporary files
   - Thumbnails
   - Previous Windows installations (can free 10+ GB)
4. Click **OK**, then **Delete Files**

For a deeper clean, use **Storage Sense** in Settings — it can automatically delete temporary files and old Recycle Bin contents on a schedule.

### Linux — Cleaning Up

Linux keeps downloaded package files and system caches that can be cleaned. Use the graphical **Disk Usage Analyzer** tool, or run these commands in the terminal:

```bash
sudo apt autoremove    # Removes packages that are no longer needed
sudo apt clean          # Clears the downloaded package cache
```

***

## Managing Startup Programs

Every program that launches at startup adds to boot time and consumes memory. Reviewing and disabling unnecessary startup items is one of the easiest ways to improve performance.

### Windows

1. Press **Ctrl+Shift+Esc** to open Task Manager
2. Go to the **Startup** tab
3. Review the list — each entry shows its startup impact (Low / Medium / High)
4. Right-click any unnecessary program and select **Disable**

Common candidates for disabling: chat apps, cloud sync tools, update checkers.

### macOS

1. **System Settings → General → Login Items**
2. Review the list and remove anything unnecessary

### Linux

Startup programs vary by desktop environment. In GNOME:
1. Open **Tweaks** (install via `sudo apt install gnome-tweaks` if needed)
2. Go to **Startup Applications**
3. Toggle off unnecessary entries

***

## Task Manager and System Monitoring

Task Manager (Windows) and its equivalents help you understand what is consuming system resources right now.

### Windows Task Manager

Open with **Ctrl+Shift+Esc**:

| Tab | What It Shows |
|---|---|
| **Processes** | Running apps and background processes with CPU, RAM, disk, and network usage |
| **Performance** | Real-time graphs of CPU, memory, disk, network, and GPU usage |
| **Startup** | Programs that launch at boot (see above) |
| **Users** | Resource usage per logged-in user |

If the CPU is stuck at 100% or RAM is full, sort the Processes tab by that column to find the culprit. You can right-click any process and select **End task** to force it to close.

### Linux — System Monitoring

These terminal commands show what your computer is doing right now:

```bash
top             # Shows running processes and resource usage (press Q to quit)
free -h         # Shows how much memory is used and free
```

***

## Using Vendor Utilities

Most hardware manufacturers provide tools to maintain and optimise their products.

| Vendor | Tool | Purpose |
|---|---|---|
| **Samsung** | Samsung Magician | SSD health, firmware updates, performance optimisation |
| **Western Digital** | WD Dashboard | Drive health monitoring, firmware updates |
| **NVIDIA** | GeForce Experience | GPU driver updates, game optimisation |
| **Intel** | Driver & Support Assistant | CPU, chipset, and integrated graphics driver updates |
| **HP / Dell / Lenovo** | Support Assist / SupportAssist / Vantage | System diagnostics, driver updates, warranty checks |

These tools can:
- Check for and install firmware updates
- Monitor drive health and predict failures
- Optimise performance settings
- Run diagnostic tests to identify hardware issues

***

## Keeping the System Updated

Operating system and software updates deliver security patches, bug fixes, and performance improvements.

### Windows Update

1. Open **Settings → Windows Update**
2. Click **Check for updates**
3. Install any available updates
4. Restart if prompted

Configure **Active hours** to prevent unexpected restarts during your working day.

### Linux Updates

```bash
sudo apt update          # Refreshes the list of available updates
sudo apt upgrade         # Installs all available updates
```

### Third-Party Software

Many applications include built-in updaters. Package managers (winget on Windows, APT on Linux, Homebrew on macOS) can also keep third-party software up to date from a single place.

***

## Additional System Tools

### Disk Defragmentation (HDDs Only)

Over time, files on a traditional hard disk become fragmented — split across different physical locations on the disk. Defragmentation reorganises the data so files are stored contiguously, improving read speed.

!!! note
    Never defragment an SSD. SSDs have no moving parts and fragmentation does not affect their performance. Defragmentation adds unnecessary write cycles that shorten SSD lifespan.

Windows automatically defragments HDDs on a weekly schedule. To check or run manually:
1. Open **Defragment and Optimise Drives**
2. Select a drive and click **Optimise**

### Disk Error Checking

- **Windows**: Right-click drive → Properties → Tools → Check
- **Linux**: Use the **Disks** application (GUI) to check drive health

### Backup

Regular backups protect against data loss from hardware failure, theft, or ransomware.

| OS | Built-in Backup Tool |
|---|---|
| Windows | File History or Windows Backup |
| macOS | Time Machine |
| Linux | Déjà Dup, rsync, or Timeshift |

At minimum, back up documents, photos, and any files that cannot be recreated. Store backups on an external drive or cloud service.

---

## Summary

- Run Disk Cleanup regularly to free space from temporary and unnecessary files
- Review startup programs and disable anything that does not need to run at boot
- Use Task Manager or `htop` to monitor CPU, RAM, and disk utilisation
- Install manufacturer utilities to maintain hardware health and firmware
- Keep the OS and all software up to date with the latest patches
- Back up important data to an external drive or cloud service
