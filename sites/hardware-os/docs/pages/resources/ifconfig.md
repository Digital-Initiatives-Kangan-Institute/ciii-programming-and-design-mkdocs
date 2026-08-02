# Using ifconfig

**ifconfig** (interface configuration) is a command-line tool used to view and configure network interfaces on a Linux system. It shows you the IP address, MAC address, and status of each network connection on your Pi.

---

## Running ifconfig

Open a terminal and run:

```bash
ifconfig
```

This displays information about every network interface on the system. On a Raspberry Pi, you will typically see two or three interfaces:

| Interface | Description |
|---|---|
| `lo` | The loopback interface — this is the computer talking to itself (always `127.0.0.1`) |
| `eth0` | The wired Ethernet connection (only present if a cable is connected) |
| `wlan0` | The wireless Wi-Fi connection |

***

## Reading the Output

Here is an example of what `ifconfig` shows for a Wi-Fi interface:

```
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.45  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a00:27ff:fe4e:66a1  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:4e:66:a1  txqueuelen 1000  (Ethernet)
        RX packets 1234  bytes 567890 (554.5 KiB)
        TX packets 567  bytes 123456 (120.5 KiB)
```

The key fields to look for:

| Field | Meaning |
|---|---|
| `UP` | The interface is active |
| `RUNNING` | The interface is connected to a network |
| `inet` | The IPv4 address — this is what you use to connect via SSH |
| `netmask` | The subnet mask (defines the size of the local network) |
| `broadcast` | The broadcast address for the local network |
| `ether` | The MAC address — a unique hardware identifier for the network card |
| `RX packets` | Data received by the interface |
| `TX packets` | Data sent by the interface |

***

## Finding Your IP Address

The most common use of `ifconfig` is finding your Pi's IP address. Look for the `inet` line under `wlan0`:

```bash
ifconfig wlan0
```

This shows only the Wi-Fi interface, making it easier to read. The IP address is the number after `inet` — for example, `192.168.1.45`.

You will need this IP address to connect to the Pi over SSH from another computer.

***

## Checking if an Interface Is Connected

If you are not sure whether your Pi is connected to Wi-Fi, check the `wlan0` interface:

```bash
ifconfig wlan0
```

- If the output shows `UP` and `RUNNING` with an `inet` address, the Pi is connected
- If there is no `inet` line, the Pi is connected to Wi-Fi but has not been assigned an IP address
- If the interface is not present or shows `DOWN`, Wi-Fi is not connected

***

## Common Options

| Command | Description |
|---|---|
| `ifconfig` | Show all interfaces |
| `ifconfig wlan0` | Show only the Wi-Fi interface |
| `ifconfig eth0` | Show only the Ethernet interface |
| `ifconfig -a` | Show all interfaces, including those that are down |

---

## Summary

- `ifconfig` displays network interface information including IP addresses, MAC addresses, and connection status
- On a Raspberry Pi, `wlan0` is the Wi-Fi interface and `eth0` is the wired Ethernet interface
- Look for the `inet` line to find the IPv4 address — this is what you use for SSH connections
- Use `ifconfig wlan0` to show only the Wi-Fi interface for easier reading
- If `UP` and `RUNNING` are present, the interface is active and connected
