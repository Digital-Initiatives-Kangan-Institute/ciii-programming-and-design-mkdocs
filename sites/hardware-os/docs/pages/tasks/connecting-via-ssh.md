# Connecting to a Raspberry Pi via SSH

---

## Scenario

You have set up a Raspberry Pi Zero W with Raspberry Pi OS Lite using the Raspberry Pi Imager. The Pi is connected to your Wi-Fi network and running headlessly — no monitor, no keyboard, no mouse. Your task is to connect to it from your computer, set it up for remote use, and perform basic system administration over SSH.

Make sure you have:

- A Raspberry Pi powered on and connected to the same network as your computer
- SSH enabled (configured via the Imager gear icon before writing the OS)
- Your computer connected to the same Wi-Fi network as the Pi

---

## Exercise 1: Finding Your Pi's IP Address

!!! abstract "Instructions"
    Before you can connect to the Pi, you need to find its IP address. There are two ways to do this — from the Pi itself, or from your router.

    **From the Pi (if you have a keyboard and monitor):**

    Run the following command to list network interfaces:

    ```bash
    ifconfig
    ```

    Look for the `wlan0` section — this is the wireless interface. The IP address is shown on the line starting with `inet`. It will look something like `192.168.1.45`.

    **From your router (if the Pi is headless):**

    Log in to your router's admin page (usually by typing `192.168.1.1` or `192.168.0.1` into a web browser). Look for a list of connected devices — the Pi will appear with its hostname (default: `raspberrypi`) and its assigned IP address.

    Write down the IP address — you will need it for all SSH connections.

??? hint "Hint - What is an IP address?"
    An IP address is a unique number assigned to every device on a network. It works like a postal address — it tells the network where to send data. Your Pi's IP address on your home network will usually start with `192.168.` followed by two more numbers. The address may change if the Pi disconnects and reconnects to the network.

---

## Exercise 2: Connecting to Your Pi

!!! abstract "Instructions"
    Now that you have the Pi's IP address, connect to it from your computer.

    1. Open a terminal on your computer and run:

    ```bash
    ssh <username>@<ip-address>
    ```

    Replace `<username>` with the username you set in the Imager, and `<ip-address>` with the IP address you found in Exercise 1. For example:

    ```bash
    ssh pi@192.168.1.45
    ```

    2. On first connection, you will see a message about the host key fingerprint. What does it say? Type `yes` to continue.

    3. Enter your password when prompted.

    4. Once connected, you should see the command prompt. Confirm you are on the Pi by running:

    ```bash
    hostname
    uname -a
    ```

    What do these commands tell you about the system?

    5. Disconnect from the Pi with the `exit` command.

??? hint "Hint - Connection refused?"
    If you get "Connection refused", SSH may not be enabled on the Pi. Check that you enabled SSH in the Imager settings, or see the [Enabling SSH](../resources/enabling-ssh.md) page for how to enable it after the fact. If you get "No route to host", make sure your computer is on the same network as the Pi and that the IP address is correct.

---

## Exercise 3: SSH Options

!!! abstract "Instructions"
    SSH has several useful options. Practice using them with your Pi's IP address.

    1. Connect with a custom hostname shown in the terminal title:

    ```bash
    ssh <username>@<ip-address> -t "echo 'Connected to Pi' && bash"
    ```

    What happens when you run this?

    2. Run a single command on the Pi without opening a full session:

    ```bash
    ssh <username>@<ip-address> "uptime"
    ```

    What does `uptime` tell you?

    3. Disconnect immediately after — you should be back at your local terminal. Use `exit` if you are still in a session.

??? hint "Hint - Running remote commands"
    SSH can run a single command without starting an interactive session — just put the command in quotes after the connection details. This is useful for quick checks. The `-t` flag forces a terminal allocation, which is needed for some interactive commands. `uptime` shows how long the system has been running, how many users are logged in, and the system load averages.

---

## Exercise 4: Transferring Files with SCP

!!! abstract "Instructions"
    SCP (Secure Copy Protocol) uses SSH to transfer files between your computer and the Pi. Complete the following:

    1. Create a small test file on your **local** computer (not the Pi):

    ```bash
    echo "Hello from my computer" > test.txt
    ```

    2. Copy it to the Pi's home directory using the IP address:

    ```bash
    scp test.txt <username>@<ip-address>:~/
    ```

    3. Connect to the Pi with SSH and verify the file arrived:

    ```bash
    ssh <username>@<ip-address>
    ls -l ~/test.txt
    cat ~/test.txt
    ```

    4. Now create a file on the Pi:

    ```bash
    echo "Hello from the Pi" > ~/pi-file.txt
    ```

    5. Copy the file back to your **local** computer:

    ```bash
    scp <username>@<ip-address>:~/pi-file.txt ./
    ```

    6. Verify the file on your local machine:

    ```bash
    cat pi-file.txt
    ```

??? hint "Hint - SCP syntax"
    The general form of `scp` is `scp <source> <destination>`. To copy a local file to the Pi, the source is the local file path and the destination is `<user>@<ip>:<path>`. To copy from the Pi to your computer, swap them around — the source is the Pi path and the destination is a local path (`./` means the current folder). The colon `:` is what tells `scp` that the path is on the remote machine.

---

## Exercise 5: Keeping Your Session Alive

!!! abstract "Instructions"
    SSH connections can time out if left idle. Configure your connection to prevent disconnections.

    1. Connect to the Pi with a keepalive option:

    ```bash
    ssh -o ServerAliveInterval=60 <username>@<ip-address>
    ```

    This sends a signal every 60 seconds to keep the connection alive.

    2. On your **local** computer, create or edit the file `~/.ssh/config` to make this automatic. Create a shortcut for your Pi:

    ```text
    Host pi
        HostName <ip-address>
        User <username>
        ServerAliveInterval 60
    ```

    Replace `<ip-address>` and `<username>` with your actual values.

    3. Save the file, then try connecting with just:

    ```bash
    ssh pi
    ```

    Did it connect using the shorthand? You can now use `ssh pi` instead of the full command every time.

??? hint "Hint - SSH config file"
    The SSH config file lets you define shortcuts for connections you use often. Each block starts with `Host` followed by a nickname (like `pi`). Inside the block, you specify the IP address, username, and any options. After saving the file, `ssh pi` automatically uses the settings you defined. This is much easier than typing the full connection command every time.

---

## Exercise 6: Basic System Administration

!!! abstract "Instructions"
    While connected to the Pi via SSH, perform these basic administration tasks:

    1. Check the system's IP address (confirm it matches what you used to connect):

    ```bash
    ifconfig
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
    `ifconfig` shows all network interfaces. `wlan0` is the wireless interface — look for the `inet` line to find the IP address. `df -h` shows disk usage in human-readable format — the "Avail" column is what matters. `free -h` shows memory — "available" is the memory that can be used without the system needing to swap. The Pi's temperature should normally be below 70°C under light use.

---

## Exercise 7: Rebooting and Reconnecting

!!! abstract "Instructions"
    When performing system maintenance, you sometimes need to reboot the Pi. Practice doing this remotely.

    1. While connected via SSH, reboot the Pi:

    ```bash
    sudo reboot
    ```

    2. The SSH connection will close immediately. Wait about 30 seconds for the Pi to restart, then reconnect using the IP address:

    ```bash
    ssh <username>@<ip-address>
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
    When you run `reboot` over SSH, the connection drops immediately because the remote system is shutting down. You cannot wait for it to come back in the same session. After rebooting, wait 30–60 seconds before reconnecting to give the Pi time to start up and reconnect to Wi-Fi. If the Pi does not reconnect, check that it is still powered on. Remember that the IP address may change after a reboot if the router assigns a different one — check your router's admin page if the old IP no longer works.
