# Customising the Message of the Day (MOTD)

---

## Scenario

The **message of the day** (`/etc/motd`) is a text file whose contents are displayed after you log in. Your task is to add a custom login banner to a Raspberry Pi so that anyone who logs in — locally or over SSH — sees the organisation name and the machine's role.

---

## Exercise 1: Adding a Login Banner

!!! abstract "Instructions"
    Follow the steps below on your Raspberry Pi to add your own login banner.

    First, view the current message of the day:

    ```bash
    cat /etc/motd
    ```

    Open the file as root using one of these editors:

    ```bash
    sudo nano /etc/motd
    ```

    or, if `micro` is installed:

    ```bash
    sudo micro /etc/motd
    ```

    Add a line (or several) with your banner text, for example:

    ```text
    KangaByte IT Services – SOHO Workstation (Raspberry Pi Zero)
    ```

    Save and exit. Then verify the file:

    ```bash
    cat /etc/motd
    ```

    Log out and log back in:

    ```bash
    exit
    ```

    You should see your message displayed as the login banner.

??? hint "Hint - Why sudo is needed"
    `/etc/motd` is a system file owned by the root user, so editing it requires administrator privileges via `sudo`. If you open it without `sudo`, your editor will warn you that the file is read-only.

??? hint "Hint - Saving in nano vs micro"
    In **nano**: `Ctrl+O`, press Enter to confirm the filename, then `Ctrl+X` to exit. In **micro**: `Ctrl+S` to save, then `Ctrl+Q` to quit.

??? tip "Hint - What to write"
    A useful banner identifies the organisation and the machine's role, so technicians know which device they have logged in to. Keep it to one or two lines — each line appears on its own row at login.

---

## Notes

- The MOTD is shown on every login, including SSH sessions.
- To remove the banner, edit the file again and delete your text.
- If you want multiple lines, just add them one per line — each appears as its own line at login.

---

## Summary

| Command | What it does |
|---|---|
| `cat /etc/motd` | View the current message of the day |
| `sudo nano /etc/motd` | Edit it as root with nano |
| `sudo micro /etc/motd` | Edit it as root with micro |
| `exit` | Log out so you can log back in and see the banner |
