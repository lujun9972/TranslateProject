[#]: subject: "For Fun Sake, I Installed macOS on Linux in a VM"
[#]: via: "https://itsfoss.com/macos-linux-vm/"
[#]: author: "Pranav Krishna https://itsfoss.com/author/pranav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

For Fun Sake, I Installed macOS on Linux in a VM
======

[![Warp Terminal][1]][2]

Getting macOS to work on a non-Apple machine requires very selective hardware and countless hours configuring EFI, disks, and more. Using [virtual machines][3] can help overcome hardware nitpicking and focus on the experience.

If enough system resources are allocated for the VM, you might get a smooth experience out of macOS.

With the Quickemu project, virtualising macOS in Linux has never been easier. It uses Qemu/KVM under the hood to run virtual machines. MacOS versions from Mojave to Sonoma are supported.

### Hardware Requirements

To virtualise macOS in your system, your system must satisfy the minimum configuration required:

  * **Processor:** Intel Core i5/AMD Ryzen 5 or above with 4 cores minimum (with virtualisation support)
  * **RAM:** 8 GB or more (macOS needs at least 4 gigs of memory)
  * **Disk Space:** at least 40 GB of free space



📋

Right from macOS Catalina, a fresh usable installation takes up 30+ GB of disk space and needs 8 GB of memory.

### Quickemu installation

I am utilising the [Quickemu project][4] to install macOS. Based on qemu and KVM, it manages the downloading and execution of virtual machines within the command line.

You can find installation instructions on their GitHub repo. I am sharing the steps for Ubuntu, the distro I used in this tutorial.

#### Installing via PPA

[The PPA method][5] can be used for Ubuntu versions, including and above 22.04. Run the following commands in the terminal:

```

    sudo apt-add-repository ppa:flexiondotorg/quickemu
    sudo apt update
    sudo apt install quickemu

```

#### Manual Installation from the repository

To install quickemu manually, obtain the dependencies (Debian-based distribution):

```

    sudo apt install git qemu jq mesa-utils pciutils procps python3 genisoimage usbutils util-linux sed socat spice-client-gtk libtss2-tcti-swtpm0 xdg-user-dirs zsync unzip

```

You could get a specific version of the project from the releases page, or obtain the latest one by cloning the official repository:

```

    git clone https://github.com/quickemu-project/quickemu/

```

### Installing macOS

Within this project, a tool called `quickget` is used to download installation disc files from the official sources, which will be used to obtain a bootable configuration of macOS.

I am installing the BigSur version to demonstrate. Here are the steps:

#### Get the installation files via quickget

Change the directory to the repository, and run the following command:

```

    cd quickemu

    ./quickget macos big-sur

```

![Downloading macOS BigSur via Quickget][6]

#### Launch the virtual machine

Now the virtual machine can be spun up, where the following will be the boot screen:

```

    ./quickemu --vm macos-big-sur.conf

```

Command to launch the virtual machine

![First boot - EFI Screen][7]

Select ' _macOS Base system'_ to get into the installation medium.

📋

If the allocation of system resources has to be modified, check how to [edit the quickemu config][8].

#### Create a partition from Disk Utility

The disk has to be partitioned in order to start with the installation. Hence, start with opening the _Disk Utility_ from the menus:

![Choosing disk utility from the recovery menu][9]

Format the drive "VirtIO Block Media" by selecting and erasing it. Enter a preferred name for your filesystem (for which I conveniently chose "macOS" 😛)

![Erasing the virtual hard disk][10]

and choose the filesystem as APFS.

![Enter a filesystem name and erase disk][11]

#### Start the installer

Quit the disk utility and get to the second option: **Reinstall macOS BigSur**

![Select "Reinstall macOS Big Sur"][12]

![Installation Welcome screen][13]

Agree to the license terms and proceed further.

![License Agreement page][14]

After the license agreement, select the disk that you had already formatted. If you don't see the disk, quit the installer and check with the disk utility.

![Selecting the disk for installation][15]

And so the installation begins!

![Progress of Installation][16]

**This page took around half an hour to complete (do not get confused by the ETA here). After a reboot, the installation continued for yet another half an hour:**

![Second installation progress screen][17]

Once the installation is complete, you will be greeted with a welcome page. You can start configuring your system from there.

### Setting up your macOS instance

The setup screen greets you after a successful installation. Here is what I followed throughout the setup, which you can follow too:

#### Choose the country

Selecting the country of residence when the VM boots up:

![Select country][18]

#### License agreement

Apart from the setup, the license has to be agreed to even in the setup.

![License agreement][19]

#### User account creation

Create a user account by specifying a username and password.

![][20]

An Apple ID is required to use Apple services such as the store. Apple can suspend your ID for running macOS on non-recognised hardware, so beware.

![Setting up an Apple ID][21]

#### Timezone

Choose the appropriate timezone for the system by entering your nearest city of residence.

![Choosing the timezone][22]

#### Appearance

Here, choose either a constant light/dark mode or let the system choose for you:

![Appearance - light/dark mode][23]

And voila! You just successfully installed a fresh copy of macOS in your Linux system.

![First boot of macOS][24]

### Tips for a seamless experience

Now that you have macOS installed in a VM, let me share a few tips and tweaks to enhance your experience.

#### Keyboard tweaks

If you are already used to macOS keyboard shortcuts, this is a tip to remap the _command_ key near the spacebar:

Navigate to _System Preferences_ ➡️ _Keyboard_ ➡️ _Modifier Keys_ , and swap the mapping of command and option keys.

![Swap Option and Command Keys][25]

This helps to emulate the macOS-like keybindings since the alt key now functions as the command key.

#### Editing the quickemu configuration

Quickemu supports a default conf file to accommodate configuration changes (the same file used for launching).

For instance, to change the amount of RAM allocated, add the following line to `macos-big-sur.conf`:

```

    ram="4G"

```

Here's a demonstration of how the configuration is changed:

0:00

/0:38

1×

Change memory of macOS VM

Quickemu supports more such tweaks. You may check [their official documentation][26] for more such tweaks.

#### Change display resolution

For macOS Catalina, the resolution set at boot will be taken as the default. It is done by passing width and height tags to the command. Here's a sample:

```

    quickemu --vm macos-catalina.conf --width 1920 --height 1080

```

For BigSur and above, you need tools like SwitchResX (freemium application) to set a resolution manually.

#### Create a desktop shortcut

Creating the desktop shortcut might be the best option if you won't actively work in the terminal debugging the virtual machine. Here's the template that I used for the shortcut:

```

    [Desktop Entry]
    Name=macOS BigSur # change name according to the version
    Exec=/home/username/quickemu/macos-big-sur.conf # change your config path
    Type=Application
    Terminal=false # to open only the VM window
    Comment="Shortcut to run a macOS VM by Quickemu"
    StartupNotify=true
    Icon=

```

Save this as `macos-big-sur.desktop` in your desktop folder. Double-clicking it should automatically launch the VM.

0:00

/0:14

1×

Desktop shortcut to launch virtual machine

Alternatively, you can create an application icon in your app drawer with the `--shortcut` tag, like:

```

    ./quickemu --vm ./macos-big-sur.conf --shortcut

```

### Conclusion

After a journey with multiple tools to get an instance of macOS running, this method is comparatively easier since it provides an out-of-the-box experience without having to meddle with configurations.

The macOS installation itself takes almost an hour, which is another reminder of how blessed we are with Linux that gets installed in under ten minutes.

_Why would you install macOS in your system as a virtual machine? Let me know in the comments below._

--------------------------------------------------------------------------------

via: https://itsfoss.com/macos-linux-vm/

作者：[Pranav Krishna][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pranav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/virtual-machine/
[4]: https://github.com/quickemu-project/quickemu
[5]: https://itsfoss.com/ppa-guide/
[6]: https://itsfoss.com/content/images/2024/07/quickget_download-2.png
[7]: https://itsfoss.com/content/images/2024/07/boot-screen---pre-installation.png
[8]: https://itsfoss.com/p/dbed387c-e788-4242-ae92-84a41a623f75/#editing-the-quickemu-configuration
[9]: https://itsfoss.com/content/images/2024/07/recovery-screen---choose-disk-utility.png
[10]: https://itsfoss.com/content/images/2024/07/disk-utlity.png
[11]: https://itsfoss.com/content/images/2024/07/disk-utility---format-disk.png
[12]: https://itsfoss.com/content/images/2024/07/recovery-screen-1-1.png
[13]: https://itsfoss.com/content/images/2024/07/installation-welcome-screen.png
[14]: https://itsfoss.com/content/images/2024/07/installation---agreement-1.png
[15]: https://itsfoss.com/content/images/2024/07/installation-disk-selection.png
[16]: https://itsfoss.com/content/images/2024/07/installation-process.png
[17]: https://itsfoss.com/content/images/2024/07/installation-process---29-more-minutes.png
[18]: https://itsfoss.com/content/images/2024/07/welcome-screen---country.png
[19]: https://itsfoss.com/content/images/2024/07/welcome-screen---license-agreement.png
[20]: https://itsfoss.com/content/images/2024/07/welcome-screen---user-account-creation.png
[21]: https://itsfoss.com/content/images/2024/07/welcome-screen---apple-ID.png
[22]: https://itsfoss.com/content/images/2024/07/welcome-screen---timezone.png
[23]: https://itsfoss.com/content/images/2024/07/welcome-screen---appearance.png
[24]: https://itsfoss.com/content/images/2024/07/macos-first-boot-2.png
[25]: https://itsfoss.com/content/images/2024/07/alt-to-command-1-1.png
[26]: https://github.com/quickemu-project/quickemu/wiki/05-Advanced-quickemu-configuration#cpu-ram--disks
