# Listing Hardware and USB Devices

Linux exposes attached hardware as files under `/dev` and provides several commands for checking what the operating system has detected.

---

## List USB Devices — `lsusb`

```bash
lsusb
```

Shows every USB device the kernel can see, including hubs, keyboards, mice, Wi-Fi/Bluetooth adapters and USB storage.

Example output:

```text
Bus 001 Device 004: ID 0781:5583 SanDisk Corp. Ultra Fit
Bus 001 Device 003: ID 0424:ec00 Microchip Technology, Inc. SMSC9512/9514 Fast Ethernet Adapter
```

- Each line is one device.
- The `ID xxxx:xxxx` is the vendor ID and product ID.

To see devices in a tree (which shows how they connect through hubs):

```bash
lsusb -t
```

---

## List Storage (Block) Devices — `lsblk`

```bash
lsblk
```

Shows block devices — hard drives, SSDs, SD cards and USB storage — with their partitions and mount points.

Example output:

```text
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda           8:0    1  14.5G  0 disk
└─sda1        8:1    1  14.5G  0 part /media/pi/USBDRIVE
mmcblk0     179:0    0  29.7G  0 disk
├─mmcblk0p1 179:1    0   512M  0 part /boot
└─mmcblk0p2 179:2    0  29.2G  0 part /
```

- `mmcblk0` is typically the microSD card.
- `sda`/`sdb` are usually USB or SATA drives.

---

## Watch Hardware as It's Plugged In — `dmesg`

```bash
dmesg | tail
```

`dmesg` prints kernel messages. Plugging in a USB device produces messages showing it was detected. `| tail` shows the most recent lines.

---

## List Device Files — `ls /dev`

```bash
ls /dev
```

Shows device files the system exposes. Common patterns:

| Pattern | Meaning |
|---|---|
| `/dev/sda`, `/dev/sdb` | USB/SATA disks |
| `/dev/sda1`, `/dev/sdb1` | Partitions on those disks |
| `/dev/mmcblk0`, `/dev/mmcblk0p1` | SD card and its partitions |
| `/dev/ttyUSB0` | USB serial adapter |
| `/dev/i2c-1` | I2C interface |
| `/dev/spidev0.0` | SPI interface |

To narrow the list:

```bash
ls /dev/sd*      # disks and partitions on USB/SATA storage
ls /dev/i2c*     # I2C interfaces
ls /dev/spi*     # SPI interfaces
```

---

## Other Useful Hardware Commands

```bash
cat /proc/cpuinfo    # CPU details
free -h              # memory usage
df -h                # disk usage
vcgencmd version     # Raspberry Pi firmware version
```

---

## Summary

| Command | What it shows |
|---|---|
| `lsusb` | USB devices |
| `lsusb -t` | USB devices in a tree |
| `lsblk` | Storage/block devices |
| `dmesg \| tail` | Recent kernel/driver messages |
| `ls /dev` | Device files |
