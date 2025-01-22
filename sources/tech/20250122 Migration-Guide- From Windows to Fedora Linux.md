[#]: subject: "Migration-Guide: From Windows to Fedora Linux"
[#]: via: "https://fedoramagazine.org/migration-guide-from-windows-to-fedora-linux/"
[#]: author: "Simon Bachenberg https://fedoramagazine.org/author/bachenberg/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Migration-Guide: From Windows to Fedora Linux
======

![][1]

Photo by [Brandon][2] on [Unsplash][3]

This article provides a step-by-step guide to transitioning from Windows to Fedora Linux.

### Motivation

Switching operating systems is a big step for many people – often accompanied by uncertainties. This is exactly the situation my parents are facing right now: Windows 10 will soon stop receiving updates, and Windows 11 hasn’t won them over. The design, new hardware requirements, and overall usability of Windows 11 just don’t align with what they want. At the same time, my mother still vividly remembers a frustrating experience she had with Ubuntu years ago, which convinced her that Linux, in general, was not for her.

This is where Fedora Linux comes into play. Fedora offers a modern, user-friendly, and stable platform that is ideal for both Linux newcomers and experienced users. Unlike Ubuntu, Fedora strikes a well-balanced mix of innovation and reliability without overwhelming the user with unnecessary restrictions. Fedora avoids proprietary software and privacy concerns often associated with other operating systems and provides an open, transparent environment that can be tailored to individual needs.

In this article, I want to demonstrate how the transition can be made as smooth as possible. Ultimately, Fedora should prove that Linux is not just a powerful tool for developers but also an excellent alternative for everyday use, even for skeptical users.

### Step-by-Step Guide:

Before you start, check the [][4][recommended][4] requirements for Fedora:

  * 2GHz dual core processor or faster
  * 4GB System Memory
  * 20GB unallocated drive space



#### Start

Switching to Fedora Linux can breathe new life into an older PC, and the process is easier than many people think. By following these steps, you can set up Fedora quickly and efficiently, without risking existing data or running into compatibility issues.

##### Get a new hard disk (Preferably an SSD):

For a fresh start, it’s highly recommended to use a new hard drive for the installation. This approach ensures that any existing data or configurations on the current drive remain untouched, providing peace of mind during the transition. An SSD (Solid State Drive) is the best choice for this purpose. SSDs are faster, more reliable, and have become very affordable. A 500GB SSD, for example, costs around 35€ and provides ample space for Fedora, applications, and personal files.

##### Prepare a Bootable Linux USB Stick:

The next step is to create a bootable USB stick with Fedora Linux. This will be used to install the operating system onto the new drive. Tools like [Fedora Media Writer][5] make this process incredibly simple.

  * Download the Fedora Media Writer and install it on any available PC or laptop.
  * Insert a USB stick with at least 8GB of free space.
  * Use the tool to download and load the Fedora installation image onto the USB stick.



This creates a portable installer that can be used to boot directly into Fedora on the target PC.

##### Install the New SSD in the Old PC:

With the USB stick ready, the next step is to install the new SSD in the PC. Opening the PC case and replacing or adding a drive is a straightforward process for most systems. Generally, this involves securing the SSD in an available slot and connecting it to the motherboard and power supply using the provided cables. For those unfamiliar with this process, online guides and videos can be very helpful.

##### Boot from the USB Stick:

After installing the new drive, power on the PC and access the boot menu (usually by pressing a key like F12, ESC, or DEL during startup). From the boot menu, select the USB stick as the boot device. If the USB device is listed in both a legacy/BIOS mode section and a UEFI section, it is recommended to select the UEFI option, as it is the more modern and secure boot method. This will load the Fedora live environment, allowing the system to boot into Fedora directly from the USB stick.

##### Install Fedora Linux:

Once in the live environment, the Fedora installer will guide you through the setup process step by step. The steps include:

  * Choosing basic settings such as language, keyboard layout, and time zone.
  * Selecting the new SSD as the target drive for installation. It is crucial to ensure that Fedora is installed on the new SSD and not on the old drive, especially if the old drive still contains important data or an existing operating system. Carefully review the drive selection in the installer to avoid overwriting the wrong drive.
  * Allowing the installer to automatically partition the SSD (a user-friendly option for most cases).



The installation process is quick and straightforward. After the installation is complete, the PC will prompt you to remove the USB stick and restart. On reboot, Fedora will launch from the new SSD.

#### Post Install steps:

##### Update your system & setup [auto-updates][6]

Keeping your system up-to-date is essential to ensure security, stability, and access to the latest features Fedora Linux has to offer. Fedora provides two easy ways to manage updates: through the graphical Software application and via the command line.

###### Updating Your System Using the Software Application

The graphical Software application makes updating your system simple and user-friendly. Here’s how you can update Fedora and set up auto-updates:

  * Open the **Software** application (you can find it in the application menu, often labeled “Software” or “Software Center”).
  * Navigate to the **Updates** tab, usually located at the top or in a side menu.
  * If updates are available, a list will be displayed. Review the updates and click Install to apply them.
  * To enable automatic updates:
    * Click on the menu icon (usually three dots or lines) in the top-right corner of the Software application.
    * Select **Software Preferences** or **Settings**.
    * Toggle the option for Automatic Updates to enable background updates for your system.



###### Updating Your System Using the Command Line

For users who prefer the command line, Fedora’s DNF package manager makes updating and enabling auto-updates simple and efficient. Follow these steps:

###### Update Your System Manually:

Open a terminal and run the following command to update all installed packages:

```

    sudo dnf update

```

This command will list all available updates and prompt you to confirm their installation. Once confirmed, the system will download and install the updates.

###### Enable Automatic Updates:

To set up automatic updates, install the dnf-automatic package, which handles updates in the background:

```

    sudo dnf install dnf-automatic

```

Once installed, enable and start the automatic update service:

```

    sudo systemctl enable --now dnf-automatic.timer

```

This will schedule the system to check for and apply updates automatically based on Fedora’s default timer settings.

###### Customize Auto-Update Behavior (Optional):

If you want more control over how automatic updates work (e.g., applying updates silently or only notifying you about them), you can edit the configuration
file:

```

    sudo nano /etc/dnf/automatic.conf

```

Adjust settings like apply_updates or download_updates as needed, save the file, and restart the service:

```

    sudo systemctl restart dnf-automatic.timer

```

###### Which Method Should You Choose?

Both the Software application and the command line offer easy ways to keep your Fedora system updated. The Software application is perfect for beginners or those who prefer a graphical interface, while the command line is ideal for users who want more control or automation over their updates. Keeping your system updated is an important habit, and Fedora makes it simple, no matter which method you choose!

##### Other Desktops

The default desktop environment of Fedora Workstation is GNOME. It has a modern and unique design that doesn’t resemble the traditional look and feel of Windows. For users transitioning from Windows, this might feel unfamiliar at first. Fortunately, Fedora offers a variety of alternative desktop environments through its [Fedora Spins][7]. The Spins provide a curated list of officially supported desktop environments tailored to different preferences and workflows.

I recommend the Budgie Desktop for those switching from Windows. Its layout and functionality are intuitive, offering a familiar experience while retaining the performance and stability of GNOME.

To install the Budgie desktop environment, run the following command:

```

    sudo dnf install @budgie-desktop

```

After the installation is complete, log out of your current session. On the login screen, select your user and look for a gear icon in the bottom right corner. Click it, and then select **Budgie** from the list of available desktop environments. Once you’ve selected Budgie, enter your password and log in. Your system will now start with the Budgie desktop environment.

##### How to Mount your old Windows Hard Drive and Enable Auto-Mounting

If you want to access your old Windows Hard Drive, you can easily mount it using the Disks application.

  1. **Open the ‘Disks’ Application:**
In the Disks application, you will see a list of all connected storage devices in the left panel. Locate your Windows hard drive in the list (it will usually be listed by its model name or size). Click on the hard drive to see detailed information about it, including the partitions.
  2. **Mount the Windows Partition:**
Under the drive, you’ll see a list of partitions. Look for the NTFS partition (Windows typically uses NTFS for its file system). Select the NTFS partition and click on the Play button (a small triangle icon) to mount it. Fedora will mount the drive, and you should now be able to access the contents of the partition.
  3. **Enable Automatic Mounting on Startup:**
To make sure that the Windows drive mounts automatically every time you boot up your system, follow these steps:
    * With the partition selected in the Disks application, click the Settings (gear) icon in the top-right corner.
    * Choose Edit Mount Options from the drop-down menu.
    * In the Mount Options window, uncheck User Session Defaults if it’s enabled.
    * Then, check the box for Mount at startup to ensure the drive is automatically mounted every time Fedora starts.
    * You can also adjust the Mount Point if you want the drive to mount to a specific folder.
    * Click OK to save the changes.
  4. **Access the Mounted Drive**
Open the Files (Nautilus) application from the Activities overview. In the Devices section of the left sidebar, you will see the mounted Windows drive listed. Click on it to browse the contents of the drive and access your files.



#### Setting Up Additional Repositories (RPM Fusion) and Installing NVIDIA Drivers

> **Disclaimer:**
>  This guide will help you install additional software using the RPM Fusion repositories. Please be aware that some of the software available through RPM Fusion is proprietary and may require proprietary online services. Such software and services might employ aggressive monetization strategies and raise privacy concerns due to anti-tamper tools and user analytics. The choice to use or not to use this software and services is entirely yours.

To enhance the functionality of your Fedora system, you may want to install additional software, such as proprietary drivers (like NVIDIA graphics drivers) and multimedia codecs, which are not available in the official Fedora repositories due to licensing restrictions. This can be easily done by enabling the [**RPM Fusion** repositories][8].

##### Enabling RPM Fusion Repositories

RPM Fusion provides free and non-free software packages for Fedora, including software for multimedia, gaming, and drivers.

  1. **Open a Terminal** and run the following command to enable the **free** RPM Fusion repository (for open-source software):

```
     sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

```

  2. For **non-free** software (such as proprietary NVIDIA drivers, Flash, etc.), run:

```
     sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

```




These commands will install both the free and non-free RPM Fusion repositories on your system, giving you access to a wide range of additional software.

##### Installing NVIDIA Drivers

If you are using an NVIDIA graphics card, you can install the official proprietary drivers for better performance, particularly for gaming or heavy graphical tasks.

> **Important:**
>  If your NVIDIA graphics card is older than 2014, please visit the [RPM Fusion NVIDIA How-to-Page][9] for the correct packages for your card. Follow the instructions provided on the page to ensure compatibility with your system.

  1. **Enable the RPM Fusion Non-Free repository** as shown in the previous section.

  2. **Install the NVIDIA driver** by running the following command:

```
     sudo dnf install akmod-nvidia

```

This package will automatically build the NVIDIA kernel module on your system, ensuring compatibility with new kernel versions.

> **Important:**
>  After installing the NVIDIA driver using akmod-nvidia, the system will build the kernel module. This process might take some time. The system typically warns you if this process is still running when you attempt a reboot, but using sudo reboot will bypass this warning, which can lead to unexpected issues. To ensure the build process has completed before rebooting, check if akmods is still running by using the commands top or ps -e | grep akmod

  3. **Optional: Install additional NVIDIA packages** for a more complete setup (such as utilities):

```
     sudo dnf install xorg-x11-drv-nvidia-cuda

```

  4. **Reboot your system** to apply the changes. The NVIDIA drivers should now be active, and you can confirm this by running:

```
     nvidia-smi

```

This command ( provided by the xorg-x11-drv-nvidia-cuda package ) should show you the details of your NVIDIA GPU.




##### Further information:

  * Other Guides: <https://fedoramagazine.org/category/faqs-and-guides/>
  * Gaming on Fedora: <https://fedoramagazine.org/gaming-on-fedora-linux-2024/>
  * Fedora Editions: <https://fedoramagazine.org/fedora-linux-editions-part-1-official-editions/>
  * Fedora Spins:
    * <https://fedoramagazine.org/fedora-linux-editions-part-2-spins/>
    * <https://fedoraproject.org/spins>
  * Parental Controls: <https://fedoramagazine.org/fedora-36-and-parental-controls/>



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/migration-guide-from-windows-to-fedora-linux/

作者：[Simon Bachenberg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/bachenberg/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/01/migration_guide-816x345.jpg
[2]: https://unsplash.com/@greener_30?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/gray-fish-on-water-during-daytime-enPHTN3OPRw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://docs.fedoraproject.org/en-US/fedora/latest/release-notes/hardware_overview/#_recommended_system_configuration
[5]: https://docs.fedoraproject.org/en-US/fedora/latest/preparing-boot-media/#_fedora_media_writer
[6]: https://docs.fedoraproject.org/en-US/quick-docs/autoupdates/
[7]: https://fedoraproject.org/spins
[8]: https://rpmfusion.org/Configuration
[9]: https://rpmfusion.org/Howto/NVIDIA
