# Connecting to a Raspberry Pi via SSH

---

## Scenario

You have set up a Raspberry Pi Zero W with Raspberry Pi OS Lite using the Raspberry Pi Imager. The Pi is connected to your Wi-Fi network and running headlessly — no monitor, no keyboard, no mouse. Your task is to connect to it from your computer, set it up for remote use, and perform basic system administration over SSH.

Make sure you have:

- A Raspberry Pi powered on and connected to the same network as your computer
- SSH enabled (configured via the Imager gear icon before writing the OS)
- Your computer connected to the same Wi-Fi network as the Pi

---

## Exercise 1: Finding and Connecting to Your Pi

!!! abstract "Instructions"
    Your first task is to connect to the Pi over the network.

    1. Try to connect using the default hostname:

    ```bash
    ssh <username>@raspberrypi.local
    ```

    Replace `<username>` with the username you set in the Imager. If this does not work, try connecting by IP address — run `ping raspberrypi.local` to see if the Pi responds.

    2. On first connection, you will see a message about the host key fingerprint. What does it say? Type `yes` to continue.

    3. Once connected, you should see the command prompt. Confirm you are on the Pi by running:

    ```bash
    hostname
    uname -a
    ```

    What do these commands tell you about the system?

    4. Disconnect from the Pi with the `exit` command.

??? hint "Hint - .local addresses"
    The `.local` domain uses mDNS (multicast DNS) to find devices on your local network. If `raspberrypi.local` does not resolve, make sure your computer supports Bonjour (macOS has it built in, Windows may need [Bonjour Print Services](https://support.apple.com/kb/DL999), and Linux can use `avahi-daemon`). Alternatively, check your router's admin page to find the Pi's IP address, or use `arp -a` to list devices on your network.

---

## Exercise 2: SSH Options

!!! abstract "Instructions"
    SSH has several useful options. Practice using them:

    1. Connect with a custom hostname shown in the terminal title:

    ```bash
    ssh <username>@raspberrypi.local -t "echo 'Connected to Pi' && bash"
    ```

    What happens when you run this?

    2. Run a single command on the Pi without opening a full session:

    ```bash
    ssh <username>@raspberrypi.local "uptime"
    ```

    What does `uptime` tell you?

    3. Disconnect immediately after — you should be back at your local terminal. Use `exit` if you are still in a session.

??? hint "Hint - Running remote commands"
    SSH can run a single command without starting an interactive session — just put the command in quotes after the connection details. This is useful for quick checks. The `-t` flag forces a terminal allocation, which is needed for some interactive commands. `uptime` shows how long the system has been running, how many users are logged in, and the system load averages.

---

## Exercise 3: Transferring Files with SCP

!!! abstract "Instructions"
    SCP (Secure Copy Protocol) uses SSH to transfer files between your computer and the Pi. Complete the following:

    1. Create a small test file on your **local** computer (not the Pi):

    ```bash
    echo "Hello from my computer" > test.txt
    ```

    2. Copy it to the Pi's home directory:

    ```bash
    scp test.txt <username>@raspberrypi.local:~/
    ```

    3. Connect to the Pi with SSH and verify the file arrived:

    ```bash
    ls -l ~/test.txt
    cat ~/test.txt
    ```

    4. Now create a file on the Pi:

    ```bash
    echo "Hello from the Pi" > ~/pi-file.txt
    ```

    5. Copy the file back to your **local** computer:

    ```bash
    scp <username>@raspberrypi.local:~/pi-file.txt ./
    ```

    6. Verify the file on your local machine:

    ```bash
    cat pi-file.txt
    ```

??? hint "Hint - SCP syntax"
    The general form of `scp` is `scp <source> <destination>`. To copy a local file to the Pi, the source is the local file path and the destination is `<user>@<host>:<path>`. To copy from the Pi to your computer, swap them around — the source is the Pi path and the destination is a local path (`./` means the current folder). The colon `:` is what tells `scp` that the path is on the remote machine.

---

## Exercise 4: Keeping Your Session Alive

!!! abstract "Instructions"
    SSH connections can time out if left idle. Configure your connection to prevent disconnections.

    1. Connect to the Pi with a keepalive option:

    ```bash
    ssh -o ServerAliveInterval=60 <username>@raspberrypi.local
    ```

    This sends a signal every 60 seconds to keep the connection alive.

    2. On the Pi, create a `.ssh/config` file on your **local** computer to make this automatic. Create or edit the file `~/.ssh/config` on your local machine:

    ```text
    Host pi
        HostName raspberrypi.local
        User <username>
        ServerAliveInterval 60
    ```

    3. Save the file, then try connecting with just:

    ```bash
    ssh pi
    ```

    Did it connect using the shorthand? You can now use `ssh pi` instead of the full command every time.

??? hint "Hint - SSH config file"
    The SSH config file lets you define shortcuts for connections you use often. Each block starts with `Host` followed by a nickname (like `pi`). Inside the block, you specify the hostname, username, and any options. After saving the file, `ssh pi` automatically uses the settings you defined. This is much easier than typing the full connection command every time.

---

## Exercise 5: Basic System Administration

!!! abstract "Instructions"
    While connected to the Pi via SSH, perform these basic administration tasks:

    1. Check the system's IP address:

    ```bash
    ip addr show
    ```

    Find the `wlan0` interface — what is the Pi's IP address on your Wi-Fi network?

    2. Check available disk space:

    ```bash
    df -h
    ```

    How much space is available on the root partition?

    3. Check the system's current memory usage:

    ```bash
    free -h
    ```

    How much RAM is available? What is the difference between "total", "used", and "available"?

    4. Update the system's package lists:

    ```bash
    sudo apt update
    ```

    Were any packages out of date? What does the output tell you?

    5. Check the system temperature (Raspberry Pi specific):

    ```bash
    vcgencmd measure_temp
    ```

    What temperature is the CPU running at?

??? hint "Hint - Interpreting the output"
    `ip addr show` shows all network interfaces. `wlan0` is the wireless interface — look for the `inet` line to find the IP address. `df -h` shows disk usage in human-readable format — the "Avail" column is what matters. `free -h` shows memory — "available" is the memory that can be used without the system needing to swap. The Pi's temperature should normally be below 70°C under light use.

---

## Exercise 6: Rebooting and Reconnecting

!!! abstract "Instructions"
    When performing system maintenance, you sometimes need to reboot the Pi. Practice doing this remotely.

    1. While connected via SSH, reboot the Pi:

    ```bash
    sudo reboot
    ```

    2. The SSH connection will close immediately. Wait about 30 seconds for the Pi to restart, then reconnect:

    ```bash
    ssh pi
    ```

    3. After reconnecting, verify the system is healthy by checking uptime:

    ```bash
    uptime
    ```

    The uptime should show only a minute or two — confirming the Pi recently rebooted.

    4. As a final step, check what kernel version the Pi is running:

    ```bash
    uname -r
    ```

??? hint "Hint - Remote reboots"
    When you run `reboot` over SSH, the connection drops immediately because the remote system is shutting down. You cannot wait for it to come back in the same session. After rebooting, wait 30–60 seconds before reconnecting to give the Pi time to start up and reconnect to Wi-Fi. If the Pi does not reconnect, check that it is still powered on.
