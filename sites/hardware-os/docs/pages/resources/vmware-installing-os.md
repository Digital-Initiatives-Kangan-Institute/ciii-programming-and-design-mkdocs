# Installing an OS in VMware

This tutorial walks through installing **Windows 10** as a virtual machine in **VMware Workstation**, and setting it up with a **local account** so you can bypass the Microsoft account sign-in requirement.

If you are new to virtualization, read [Introduction to Virtual Machines](virtual-machines.md) first for the background concepts. The process below follows the same general idea as [Installing an OS in VirtualBox](virtualbox-installing-os.md), but using VMware's interface instead.

!!! note "Why a local account?"
    Modern Windows 10 and 11 setup tries to force you to sign in with a Microsoft account, which requires an internet connection. By keeping the network adapter disabled during the initial setup, Windows presents the offline **local account** path instead. This is a common technique in labs and classrooms where you want a standalone account.

---

## Before You Start

Make sure you have the following before beginning:

- **VMware Workstation** installed on your host computer. Both Workstation Player and Workstation Pro follow the same steps.
- **A Windows 10 ISO file.** You can download the official image from Microsoft's [Download Windows 10](https://www.microsoft.com/software-download/windows10) page. You do not need a product key to download or install it.
- **At least 60 GB of free disk space** for the virtual machine.
- **Enough free RAM.** The memory assigned to the VM is borrowed from your host while the VM runs, so leave enough for the host operating system.

---

## Set Up the Virtual Machine

**Step 1:** Open VMware Workstation from your desktop or Start menu.

![VMware Workstation main window](../../assets/vmware-step-01.png)

**Step 2:** Go to **File → New Virtual Machine**.

![File menu with New Virtual Machine highlighted](../../assets/vmware-step-02.png)

**Step 3:** Choose **Typical (recommended)** and click **Next**.

![New Virtual Machine wizard with Typical selected](../../assets/vmware-step-03.png)

**Step 4:** Choose **I will install the operating system later** and click **Next** — this avoids VMware's *Easy Install*, which pre-fills Microsoft account information.

![Installer disc selection with I will install the operating system later selected](../../assets/vmware-step-04.png)

**Step 5:** Select **Microsoft Windows** as the guest operating system and choose **Windows 10 x64** as the version. Click **Next**.

![Guest operating system selection: Microsoft Windows, Windows 10 x64](../../assets/vmware-step-05.png)

**Step 6:** Give the virtual machine a name and choose where to store it. Click **Next**.

![Name the virtual machine and location fields](../../assets/vmware-step-06.png)

**Step 7:** Set the maximum disk size (**60 GB** is the recommended size for Windows 10 x64) and choose **Split virtual disk into multiple files**. Click **Next**.

![Disk capacity settings with 60 GB and split into multiple files](../../assets/vmware-step-07.png)

**Step 8:** On the **Ready to Create Virtual Machine** screen, click **Customize Hardware** before finishing.

![Ready to Create Virtual Machine summary screen](../../assets/vmware-step-08.png)

!!! tip "Adjusting hardware later"
    The **Customize Hardware** screen is also where you can change the VM's **memory** and **processors**. The Typical defaults are fine for this tutorial, and you can change them later from **Edit virtual machine settings** if the VM feels slow or you need more resources.

**Step 9:** In the Hardware window, select the **New CD/DVD (SATA)** device, choose **Use ISO image file**, and click **Browse** to select your Windows 10 ISO. Click **Close**.

![Hardware settings showing CD/DVD set to use an ISO image file](../../assets/vmware-step-09.png)

**Step 10:** Close the Hardware window, then click **Finish** to create the virtual machine.

![Finish button on the New Virtual Machine wizard](../../assets/vmware-step-10.png)

---

## Disable the Network Adapter Before Booting

Disabling the network adapter before the first boot prevents Windows from requiring a Microsoft account during the Out-of-Box Experience (OOBE) setup.

**Step 11:** From the virtual machine summary screen, click **Edit virtual machine settings** to open the Hardware panel.

![Virtual machine summary with Edit virtual machine settings highlighted](../../assets/vmware-step-11.png)

**Step 12:** Select **Network Adapter** in the device list. Under **Device status**, uncheck both **Connected** and **Connect at power on**. Click **OK** to apply. The network will be disconnected when the VM boots.

![Network Adapter settings with Connected and Connect at power on unchecked](../../assets/vmware-step-12.png)

---

## Install Windows 10

!!! tip "Releasing the mouse and keyboard"
    When you click inside the VM window, VMware captures your mouse and keyboard so they control the guest OS. Press **Ctrl + Alt** to release them back to your host computer. This is handy during installation if you need to look something up on your host.

**Step 13:** Power on the virtual machine. When the Boot Manager appears, select **EFI VMware Virtual SATA CDROM Drive (1.0)** and press **Enter** to boot from the ISO.

![Boot Manager showing the VMware virtual SATA CDROM drive](../../assets/vmware-step-13.png)

**Step 14:** When prompted, press any key to boot from the CD or DVD.

![Prompt to press any key to boot from CD or DVD](../../assets/vmware-step-14.png)

**Step 15:** The Windows Setup screen appears. Set the **Language to install**, **Time and currency format**, and **Keyboard or input method** to your preferences, then click **Next**.

![Windows Setup language, time, and keyboard selection screen](../../assets/vmware-step-15.png)

**Step 16:** Click **Install now** on the Windows Setup screen.

![Windows Setup with Install now button](../../assets/vmware-step-16.png)

**Step 17:** On the **Activate Windows** screen, click **I don't have a product key** to skip activation for now — you can activate later.

![Activate Windows screen with I don't have a product key highlighted](../../assets/vmware-step-17.png)

**Step 18:** Select the edition of Windows 10 you want to install (for example, **Windows 10 Pro**) and click **Next**.

![Windows 10 edition selection screen](../../assets/vmware-step-18.png)

**Step 19:** Read the license terms, tick **I accept the license terms**, and click **Next**.

![License terms screen with accept checkbox](../../assets/vmware-step-19.png)

**Step 20:** Choose **Custom: Install Windows only (advanced)** to perform a clean installation.

![Installation type screen with Custom selected](../../assets/vmware-step-20.png)

**Step 21:** Select **Drive 0 Unallocated Space** (the virtual disk you created) and click **Next**. Windows will begin copying files and rebooting automatically. Wait for the installation to complete.

![Drive selection showing Drive 0 Unallocated Space](../../assets/vmware-step-21.png)

!!! tip "Be patient"
    The installation copies files, installs features, and reboots the VM several times. Do not interrupt it — just let it run.

---

## Complete OOBE Setup with a Local Account

After installation, Windows launches the Out-of-Box Experience (OOBE). Because the network adapter is disabled, Windows presents the offline local-account path.

**Step 22:** On the **Let's start with region** screen, select your region (for example, **Australia**) and click **Yes**.

![Region selection screen during OOBE](../../assets/vmware-step-22.png)

**Step 23:** Confirm your keyboard layout (for example, **US**) and click **Yes**.

![Keyboard layout confirmation screen](../../assets/vmware-step-23.png)

**Step 24:** On the **Want to add a second keyboard layout?** screen, click **Skip**.

![Second keyboard layout screen with Skip button](../../assets/vmware-step-24.png)

**Step 25:** The **Let's connect you to a network** screen will show Ethernet0 as **Not connected**. Click **I don't have internet** at the bottom-left.

![Network connection screen with I don't have internet highlighted](../../assets/vmware-step-25.png)

**Step 26:** Windows will try to persuade you to connect. Click **Continue with limited setup** at the bottom-left to proceed without a Microsoft account.

![Limited setup screen with Continue with limited setup highlighted](../../assets/vmware-step-26.png)

**Step 27:** Enter a username for your local account (for example, your name) and click **Next**.

![Username entry screen for the local account](../../assets/vmware-step-27.png)

**Step 28:** Create a password for the local account and click **Next**. You may leave it blank if you prefer no password, though a password is recommended.

![Password creation screen](../../assets/vmware-step-28.png)

**Step 29:** Set up three security questions for account recovery, then click **Next** after each question.

![Security questions setup screen](../../assets/vmware-step-29.png)

**Step 30:** Choose your privacy settings (location, diagnostics, and so on). Turn off any settings you don't want, then click **Accept**.

![Privacy settings screen with Accept button](../../assets/vmware-step-30.png)

**Step 31:** On the **Let Cortana help you get things done** screen, click **Not now** to skip Cortana setup.

![Cortana setup screen with Not now highlighted](../../assets/vmware-step-31.png)

---

## Install VMware Tools

VMware Tools improves display resolution, mouse integration, clipboard sharing, and overall VM performance. Install it as soon as Windows is running.

**Step 32:** In VMware Workstation, click the **VM** menu and select **Install VMware Tools...**

![VM menu with Install VMware Tools selected](../../assets/vmware-step-32.png)

**Step 33:** Inside the Windows VM, open **File Explorer** from the taskbar.

![File Explorer opened inside the Windows VM](../../assets/vmware-step-33.png)

**Step 34:** In File Explorer, go to **This PC**. You will see a DVD drive labelled **VMware Tools**. Double-click it to open the installer.

![This PC showing the VMware Tools DVD drive](../../assets/vmware-step-34.png)

**Step 35:** A User Account Control (UAC) prompt will appear asking permission for the VMware installation launcher. Click **Yes**.

![User Account Control prompt for VMware Tools](../../assets/vmware-step-35.png)

**Step 36:** The VMware Tools Setup wizard opens. Click **Next** to begin.

![VMware Tools Setup wizard welcome screen](../../assets/vmware-step-36.png)

**Step 37:** Choose **Typical** as the setup type and click **Next**.

![Setup type selection with Typical selected](../../assets/vmware-step-37.png)

**Step 38:** On the **Ready to install VMware Tools** screen, click **Install**.

![Ready to install VMware Tools screen](../../assets/vmware-step-38.png)

**Step 39:** When prompted to restart the system, click **Yes** to reboot the VM. VMware Tools will be fully active after the restart.

![Restart prompt after VMware Tools installation](../../assets/vmware-step-39.png)

---

## Re-enable the Network Adapter

**Step 40:** After the VM restarts, return to VMware Workstation. Click the **VM** menu and select **Settings** (or press **Ctrl+D**).

![VM menu with Settings highlighted](../../assets/vmware-step-40.png)

**Step 41:** Select **Network Adapter**. Under **Device status**, check both **Connected** and **Connect at power on**. Set the network connection type to **NAT** (or your preferred mode) and click **OK**. Your VM now has internet access.

![Network Adapter re-enabled with NAT selected](../../assets/vmware-step-41.png)

---

## Summary

- Create the VM with **Typical** settings, but choose **I will install the operating system later** to avoid Easy Install
- Attach the Windows 10 ISO to the virtual CD/DVD drive
- **Disable the network adapter** before the first boot so Windows offers the local-account path
- Install Windows 10 as a clean (**Custom**) installation onto the virtual disk
- During OOBE, choose **I don't have internet** → **Continue with limited setup** to create a **local account**
- Install **VMware Tools** inside the guest for better performance and integration
- Finally, **re-enable the network adapter** to give the VM internet access
