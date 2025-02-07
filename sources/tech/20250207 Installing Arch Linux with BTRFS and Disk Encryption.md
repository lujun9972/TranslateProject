[#]: subject: "Installing Arch Linux with BTRFS and Disk Encryption"
[#]: via: "https://itsfoss.com/arch-linux-install-encrypted-btrfs/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing Arch Linux with BTRFS and Disk Encryption
======

[![Warp Terminal][1]][2]

On our [Arch installation video][3], a viewer requested a tutorial on installing Arch but with BTRFS and with encryption enabled.

And hence this tutorial came into existence.

I am using the official archinstall script. Though a command line tool, this guided installer allows even a moderate system user to enjoy the "greatness" of Arch Linux.

🚧

The method discussed here ****wipes out the existing operating system**** (s) from your computer and installs Arch Linux on it. So if you are going to follow this tutorial, make sure that you have backed up your files externally, or else you’ll lose all of them. You have been warned!

### Requirements

Here's what I recommend for this tutorial:

  * An x86_64 (i.e. 64 bit) compatible machine
  * Minimum 2 GB of RAM (recommended 4-8 GB, depending upon the desktop environment or window manager you choose)
  * At least 10 GB of free disk space (recommended 20 GB for basic usage with a desktop environment)
  * An active internet connection
  * A USB drive with a minimum 4 GB of storage capacity
  * Familiarity with the Linux command line



Once you have made sure you have all the requirements, let’s install Arch Linux.

### Step 1: Download the Arch Linux ISO

Download the ISO from the official website. Both direct download and torrent links are available.

[Download Arch Linux][4]

### Step 2: Create a live USB of Arch Linux

You will have to create a live USB of Arch Linux from the ISO you just downloaded.

You may use the [Etcher GUI tool][5] to create the live USB. It is available for both Windows and Linux.

![Etcher Live USB creation][6]

Alternatively, if you are on Linux, you can [use the dd command to create a live USB][7]. Replace _/path/to/archlinux.iso_ with the path where you have downloaded the ISO file, and _/dev/sdx_ with your USB drive in the example below. You can get your drive information using [_lsblk_][8] command.

```

    dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx status=progress && sync

```

Basically, choose any live USB creation tool you like.

### Step 3: Boot from the live USB

🚧

Do note that in some cases, you may not be able to boot from live USB with secure boot enabled. If that’s the case with you, [disable secure boot first][9].

Once you have created a live USB for Arch Linux, shut down your PC. Plug in your USB and boot your system. While booting, keep pressing F2, F10 or F12 key (depending upon your system) to [access UEFI boot settings][10].

Here, select to boot from USB or removable disk. Once you do that and the system boots, you should see an option like this:

![UEFI Boot Screen][11]

Select Arch Linux UEFI (x86_64) option to start the live medium.

📋

Legacy BIOS users should select the x86_64 BIOS option.

### Step 4: Connect to Wi-Fi

You need an active internet connection for [installing Arch Linux][12].

If you have wired connection, good. Else, you need to make some effort to connect to your Wi-Fi before starting the archinstall script.

First, in the Arch Linux live prompt, enter the command:

```

    iwctl

```

This Internet Wireless daemon control is used to enrol Wi-Fi connection to your system. As soon as you enter the command, you can see that the prompt has changed to `iwd`.

Here, you need to list devices to get the name of your wireless hardware device.

![List network devices][13]

In the above screenshot, you can see the name of my Wi-Fi device is `wlan0`.

Now, use this device to scan available Wi-Fi connections in the vicinity.

```

    station wlan0 scan
    station wlan0 get-networks

```

![Connect to a Wi-Fi][14]

This will print the name of the Wi-Fi services available. Note the “Network Name”.

To connect to the network, use the command:

```

    station wlan0 connect "Network Name"

```

This will ask you to enter the Wi-Fi password. Enter it and you should be now connected to internet.

Exit the `iwd` prompt using `CTRL+D`.

You can check if the network is functioning [using the ping command][15]:

```

    ping google.com

```

![Ping Google][16]

### Step 5: Pacman download settings

Before starting the archinstall script, let's change the download limit of pacman.

Edit the pacman configuration using:

```

    nano /etc/pacman.conf

```

Here, uncomment the `parellelDownload` option and set a value according to your internet speed.

If you have a decent internet speed, set the parallel download count to 10.

📋

On my test system, I needed to run `pacman -Sy` and then `pacman -S archlinux-keyring` (install Arch Linux keyrings) before starting the installer. Otherwise, the installer crashed with some errors.
You may also need to read carefully what the prompt error says.

### Step 6: Start Archinstall script

With the network connection ready, let's start the archinstall script with the command below:

```

    archinstall

```

This will start the text-based arch installation script.

![Archinstall script][17]

#### Set the installation language

The first setting in the installer is the installation language. This option sets what language is used in the Terminal User Interface.

The latest archinstall provides a percentage value corresponding to each language, that describes how much translation has been completed.

![Installation language][18]

I will be going with the default English.

#### Locale Settings

You should set your locale and keyboard settings. Here, if you are OK with the defaults, you can skip to the next setting.

💡

Some programs like Rofi launcher may not launch if your locale is different from en_US. So, adding en_US as a locale is a good thing to avoid future headaches.

![Set keyboard and locale settings][19]

To change a setting, press the enter key to go inside and select individual items.

![Inside locale settings][20]

#### Mirror settings

Press the enter key on the **Mirrors** in the main menu of archinstall script. This will bring you to the mirror selection section.

Enter the Mirror Region.

![Select the Mirror Region option.][21]

This will provide a list of countries. You can select a country near your location for a faster network.

![Mirror Countries \(Click to expand the image\)][22]

💡

Use the "/" key to start a search. TAB key to select/mark an entry. Once multiple entries are marked, use the ENTER key to set those countries as mirrors.

The mirrors from selected countries will be listed. Move to “Back” and click enter.

![Country-wise mirror list][23]

#### Disk Configuration

Now, you need to partition your disk. The archinstall has a neat mechanism to help you here.

On the main menu, select “Disk Partition”. Inside this, select “Partitioning”.

![Select Partitioning option][24]

Here, use the option “Use a best-effort default partition layout”.

![Best-effort partitioning][25]

In the next dialog, use the TAB key to select your hard disk device and press the ENTER key.

![Select Disk][26]

Choose a partition type. Here, I am going with BTRFS partition. You can pick EXT4, a very well-tested file system, or XFS, f2fs etc.

![Select BTRFS File System][27]

On the next screen, you will be asked to use a default subvolume structure or not.

Let's say you select “Yes”.

![Create Subvolumes True][28]

You will be asked to pick compression or disable copy-on-write. It is advised to select Compression, to enable a Zstd compression.

![Use Compression option][29]

This will create a partition for you, with subvolumes for `/`, `/home`, `/var/log`, `/var/cache/pacman/pkg`, and `/.snapshots`.

![Subvolume listing \(Click to expand the image\)][30]

📋

Subvolumes are beneficial for users who want a granular control and use features like snapshots extensively.

If you are using a simple system, and not going to use such features, you can choose to avoid the subvolumes.

For this, pick “No” for BTRFS default subvolumes.

![Subvolume choice][31]

On the next screen, you should select “Use Compression” option.

Thus, you will get a simple partition for the system.

![Simple no-subvolume partition.][32]

Use the "Back" button to go to the installer main menu.

#### Disk Encryption

🚧

Disk encryption may introduce slight performance delay to the system. If your system is a casual home PC or an alternative system with no critical data, you can ignore the encryption.

Select the Disk Encryption option from the main menu. On the dialog box, select Encryption type and pick LUKS.

This will enable two other fields; Encryption password and Partition.

Fill the fields. Select the partitions that need to be encrypted using the TAB key.

![Encryption overview \(Click to expand the image\)][33]

🚧

Do not forget the encryption password. If you do, you'll lose access to the data on disk and formatting the entire operating system will be the only option for you.

#### Swap

Swap on zram is enabled by default in the installer. If needed, you can disable it.

#### Bootloader

By default, it is set to systemd-boot. This is a simple bootloader for those who expect simplicity.

If you require familar functionality, go for GRUB bootloader.

![Select Grub Bootloader][34]

#### Hostname

You can configure hostname here. By default, it is `archlinux`.

#### Root password

Next is Root password. Select it using enter key. Then enter and confirm a strong root password.

![Root Password Setting][35]

#### User creation

It is important to create a regular user account other than root account. This is for day-to-day purposes.

On User section, select "Add a user" option.

![Click on "Add a user"][36]

Here, enter the username.

![Enter username][37]

Now, enter a password.

![Password for user][38]

Confirm it by entering again when prompted. You will be asked whether the user a superuser or not.

Make the created user superuser (administrative privileges) by selecting the “Yes” option.

![Admin privileges to regular user][39]

Now, use the "Confirm and exit" option.

![Exit user creation][40]

#### Profile (Desktop selection)

The “Profile” field in the installer is where we will set desktop environments.

Select **Profile → Type**. Here, select the **Desktop** option.

![Select Desktop Option][41]

On the next screen, select a desktop (desktops) using the TAB key and press enter.

🚧

Try to avoid installing multiple heavy desktops in one system. Like KDE Plasma and GNOME in one system is not recommended.

![Select GNOME Desktop][42]

💡

You can choose one desktop like GNOME/Plasma and then choose one tiling window manager, making it install two desktop options.

Selecting a desktop and pressing enter will bring you to the driver selection settings.

For the test system, the installer automatically assigned all open-source drivers.

![Driver packages][43]

You can enter the “Graphics driver” settings and decide appropriate driver packs.

![Available drivers are listed][44]

Normally, you should not be doing anything on the greeter, as it will be automatically selected (GDM for GNOME, SDDM for KDE Plasma etc.)

#### Audio settings

For Audio settings, you can select Pipewire or pulse audio.

![Select Pipewire][45]

#### Kernel

You can either go with the default Linux kernel or select multiple kernels. Learn more about [kernel options in Arch Linux][46].

The screenshot below shows two kernels selected, `linux` and `linux-lts`.

![Kernel selection][47]

#### Network Configuration

In the Network Configuration settings, select "Use NetworkManager" option.

![Use NetworkManager][48]

#### Additional Packages

If you need to install additional packages to your system, you can do it at the installation stage itself.

Press enter key on “Additional package” option in main menu.

Now, just enter the proper name of the packages you want to install, separated with space.

In the screenshot below, packages like `firefox`, `htop`, `fastfetch`, and `starship` are added.

![Specify additional packages][49]

#### Optional Repositories

You can enable `multilib` repositories using this setting. Select items using the TAB key and press enter. Learn about [various Arch repos here][50].

![Additional Repositories][51]

#### Timezone

Search and set the timezone based on your location. Asia/Kolkata for Indian Standard Time, US/Central for central timezone etc.

![Timezone settings][52]

Automatic Time Sync with NTP will be automatically enabled, and no need to change.

#### Start the actual install

Once all the settings have been done, you can use the **Install** option to start the installation procedure.

![Use Install button][53]

You will be asked to verify the installation configurations you have set. Once satisfied, enter on “Yes” option.

![Confirm installation \(Click to expand the image\)][54]

The process will be started, and you need to wait for some time to finish all the downloads and installations.

### Step 6: Post Installation

Once the archinstall script finishes, it will ask you to chroot into the system for further settings. You can give NO to the question if you have nothing planned to do.

![No chroot enter][55]

You can now shut down the system.

```

    shutdown now

```

![Shutdown the system][56]

Once the system is shut down, remove the USB device from the port and boot the system.

This will bring you to the encryption page, if you have enabled encryption. Enter the password you have set.

![Enter encryption password][57]

You will reach the login page. Enter the password to log in to your system.

![Log in to the system][58]

Enjoy Arch Linux with BTRFS and encrypted drive.

--------------------------------------------------------------------------------

via: https://itsfoss.com/arch-linux-install-encrypted-btrfs/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.youtube.com/watch?v=WksxVLrALhg
[4]: https://www.archlinux.org/download/
[5]: https://itsfoss.com/install-etcher-linux/
[6]: https://itsfoss.com/content/images/2025/01/use-etcher-to-create-live-usb.png
[7]: https://itsfoss.com/live-usb-with-dd-command/
[8]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/s1-sysinfo-filesystems
[9]: https://itsfoss.com/disable-secure-boot-windows/
[10]: https://itsfoss.com/access-uefi-settings-windows-10/
[11]: https://itsfoss.com/content/images/2025/01/boot-screen.png
[12]: https://itsfoss.com/install-arch-linux/
[13]: https://itsfoss.com/content/images/2025/01/list-devices.jpg
[14]: https://itsfoss.com/content/images/2025/01/add-a-wifi-network.jpg
[15]: https://itsfoss.com/ping-command/
[16]: https://itsfoss.com/content/images/2025/01/ping-for-connection.png
[17]: https://itsfoss.com/content/images/2025/01/archinstall-script.png
[18]: https://itsfoss.com/content/images/2025/01/installation-language.png
[19]: https://itsfoss.com/content/images/2025/01/set-keyboard-and-locale.png
[20]: https://itsfoss.com/content/images/2025/01/inside-locale-settings.png
[21]: https://itsfoss.com/content/images/2025/01/select-mirror-region-option.png
[22]: https://itsfoss.com/content/images/2025/01/marking-mirror-countries.png
[23]: https://itsfoss.com/content/images/2025/01/mirrors-listed-country-wise.png
[24]: https://itsfoss.com/content/images/2025/01/select-partitioning.png
[25]: https://itsfoss.com/content/images/2025/01/best-effort-partition-layout.png
[26]: https://itsfoss.com/content/images/2025/01/select-the-harddisk.png
[27]: https://itsfoss.com/content/images/2025/01/select-btrfs-file-system.png
[28]: https://itsfoss.com/content/images/2025/01/subvolume-choice.png
[29]: https://itsfoss.com/content/images/2025/01/use-compression.png
[30]: https://itsfoss.com/content/images/2025/01/subvolumes-listing.png
[31]: https://itsfoss.com/content/images/2025/01/no-for-subvolumes.png
[32]: https://itsfoss.com/content/images/2025/01/simple-partition-without-subvolumes.png
[33]: https://itsfoss.com/content/images/2025/01/encryption-overview.png
[34]: https://itsfoss.com/content/images/2025/01/select-grub-bootloader.png
[35]: https://itsfoss.com/content/images/2025/01/enter-root-password-and-confiirm.png
[36]: https://itsfoss.com/content/images/2025/01/add-a-user-option.png
[37]: https://itsfoss.com/content/images/2025/01/enter-username-for-user.png
[38]: https://itsfoss.com/content/images/2025/01/enter-a-password-for-user.png
[39]: https://itsfoss.com/content/images/2025/01/new-user-super-user.png
[40]: https://itsfoss.com/content/images/2025/01/confirm-and-exit-user-creation.png
[41]: https://itsfoss.com/content/images/2025/01/select-desktop-option.png
[42]: https://itsfoss.com/content/images/2025/01/select-gnome-to-install-as-desktop.png
[43]: https://itsfoss.com/content/images/2025/01/driver-selection-automatic-suggestion.png
[44]: https://itsfoss.com/content/images/2025/01/available-drivers-listed.png
[45]: https://itsfoss.com/content/images/2025/01/select-pipewire.png
[46]: https://itsfoss.com/switch-kernels-arch-linux/
[47]: https://itsfoss.com/content/images/2025/01/kernel-selection.png
[48]: https://itsfoss.com/content/images/2025/01/use-network-manager.png
[49]: https://itsfoss.com/content/images/2025/01/specify-additional-packages.png
[50]: https://itsfoss.com/arch-linux-repos/
[51]: https://itsfoss.com/content/images/2025/01/multilib-and-testing-repo.png
[52]: https://itsfoss.com/content/images/2025/01/timezone-settings.png
[53]: https://itsfoss.com/content/images/2025/01/use-the-install-button.png
[54]: https://itsfoss.com/content/images/2025/01/confirm-installation-to-start.png
[55]: https://itsfoss.com/content/images/2025/01/no-chroot-arch-post.png
[56]: https://itsfoss.com/content/images/2025/01/shutdown-now.png
[57]: https://itsfoss.com/content/images/2025/01/enter-encryption-password-to-unlock-the-system.png
[58]: https://itsfoss.com/content/images/2025/01/log-in-to-arch-linux-gnome.png
