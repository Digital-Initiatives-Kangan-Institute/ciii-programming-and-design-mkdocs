# Configuring Wi-Fi

The easiest way to connect a Raspberry Pi to a wireless network is through the `raspi-config` configuration tool.

---

## Prerequisites

- A Raspberry Pi with built-in Wi-Fi (e.g. Pi Zero W, Pi 3, Pi 4) or a compatible USB Wi-Fi adapter
- The network name (SSID) and password/passphrase

---

## Using raspi-config

### Open the Configuration Tool

Log in to the Pi and run:

```bash
sudo raspi-config
```

You'll see a text-based menu. Use the **arrow keys** to move, **Enter** to select, and **Tab** to move between options.

### Open the Wireless LAN Settings

1. Select **System Options** and press Enter.
2. Select **Wireless LAN** and press Enter.

### Choose Your Country

Select your country from the list and press Enter. This sets the correct wireless regulatory settings.

### Enter the SSID (Network Name)

Type the network name and press Enter.

### Enter the Passphrase

Type the Wi-Fi password and press Enter.

### Finish and Reboot

1. Select **Finish** (use Tab if needed to reach it) and press Enter.
2. If asked whether to reboot, choose **Yes**. If it doesn't ask, reboot manually with:

    ```bash
    sudo reboot
    ```

---

## Verifying the Connection

After logging back in, check that the Pi has an IP address and can reach the internet:

```bash
ip a
```

Look for the `wlan0` interface and an `inet` address (e.g. `192.168.1.50`).

```bash
hostname -I
```

Shows the IP address(es) assigned to the Pi.

```bash
ping -c 4 8.8.8.8
```

Sends 4 test packets to Google's DNS server. Successful replies mean the Pi can reach the internet.

```bash
ping -c 4 google.com
```

Tests that **DNS** (name resolution) works too. If `8.8.8.8` works but `google.com` does not, the network is fine but there is a DNS problem.

---

## Alternative: Configuring Wi-Fi from the Imager

When writing the OS image, the Raspberry Pi Imager's **OS customisation → SERVICES** tab has a "Configure wireless LAN" option. Entering the SSID and password there applies the settings on first boot — see [Using Raspberry Pi Imager](raspberry-pi-imager.md) for details. The `raspi-config` method above is the equivalent done from the Pi itself.

---

## Troubleshooting

- **Wrong country code** — re-enter `raspi-config` and check the country setting.
- **SSID not visible** — check the network name is typed exactly, including capital letters.
- **`wlan0` has no IP** — run `sudo raspi-config`, re-enter the SSID/passphrase, then reboot.

---

## Summary

- Use `sudo raspi-config` → **System Options** → **Wireless LAN** to connect to Wi-Fi
- Set the correct country code, then enter the SSID and passphrase
- Verify the connection with `ip a`, `hostname -I`, and `ping`
- Wi-Fi can also be pre-configured when writing the image with Raspberry Pi Imager
