[#]: subject: "Exploring the Lightweight Alpine Linux in Virtual Box"
[#]: via: "https://itsfoss.com/alpine-linux-virtualbox/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Exploring the Lightweight Alpine Linux in Virtual Box
======

[![Warp Terminal][1]][2]

Alpine Linux is one of the few Linux distributions out there that stands out of the crowd.

First, Alpine is an [independent Linux distribution][3], not a derivative of any other popular option.

Second, it uses [OpenRC][4] as the init system. So, if you are someone who is [not a fan of systemd][5], you can surely consider this one.

Third, it uses [BusyBox][6] by default, which is an interesting choice.

Now, Alpine is immensely popular as a container distro because of its small form factor. The base docker image is hardly 5 MB, making it an attractive choice.

But it doesn't mean that you can only use Alpine with Docker or it only has to be in the the server format.

In this tutorial, I'll share how you can install Alpine Linux with Xfce desktop in VirtualBox.

Sounds exciting? Let's go.

### Step 1: Download Alpine Linux

Alpine Linux provides several options to download. Here, I downloaded the x86_64 Virt ISO that is made for virtual machine setups. It is around 60 MB in size. You may also use the standard edition which is ~200 MB, and an extended ISO, nearly 900 MB in size.

I have used the Virtual Machine edition since I am installing it in a VirtualBox VM.

[Download Alpine Linux][7]

### Step 2: Setup VirtualBox VM with Alpine ISO

Open VirtualBox and click on the “New” button to start creating a New VM.

![Click on New][8]

Now, choose the Guided Mode and Set the following:

  * Name: Alpine Linux
  * ISO: Choose the Downloaded ISO
  * Kernel: Other Linux kernel 5.x



![Name Virtual Machine][9]

Click Next. On the next screen, allocate some RAM to the VM. Usually, 2 GB is enough for Alpine, but if you could, give it 4 GB of RAM. Also, allocate some processors. Here, I have assigned 2 processors. Click Next.

![Allocate RAM and CPU][10]

On the next screen, you need to provide the storage space. You can either go with the requirement or a bit extra for efficiency. 25 GB will be more than sufficient for a test virtual machine. Change according to your need.

![Allocate Disk][11]

Clicking Next will give you an overview of the settings. Click the Finish button here.

![Click on Finish][12]

Now, select the machine, right-click on it and select the Settings option.

![Select Virtual Machine Settings][13]

Select the Display tab and put the display memory to max (128 MB). Click on OK after this.

![Allocate Display Memory][14]

Now, start the VM by double-clicking on its name.

### Step 3: Text-based Alpine installation

Alpine installation is text-based. Yeah! It gives the Arch Linux vibes, I know.

When the machine starts, you will be prompted to log in. Just type `root` and enter. The default root user has no password. You will be ready to install the system now.

![Login as root][15]

#### Start the text-based installer

Once logged in as root, enter:

```

    setup-alpine

```

This will start the installer.

#### Keyboard layout

You need to select the keyboard layout. Here, I have chosen “us”. It will ask to select the variant in US keyboard. I again enter “us” as the option.

![Keyboard Layout][16]

#### Hostname

Enter a hostname of your choice. The default was localhost. And then press enter.

![Enter Hostname][17]

#### Interface selection

Installer will ask for the network interface selection. Since, it selected the default for me, I will press Enter key. If you have other interfaces, you can select “ **?** ” for help. For VirtualBox, the default is enough.

![Select Network Interface][18]

It now asks to set the IP. I am going with the default DHCP. Also, no further manual settings.

![IP Address Settings][19]

#### Root password

As I mentioned earlier, the root account has no password. You have to set it up for the security purpose.

You need to type and retype the root password in this step. Needless to say that nothing is displayed on the screen when you type the password. Just type it and press enter.

![Set Root Password][20]

#### Timezone settings

You need to select the timezone. The default is UTC. Press “?” for listing the available timezones. As you can see, I have set it to Asia and then pressed enter.

![Select Timezone][21]

Subsequently, you have to set the region. Like before, press “?” for listing all the available area in the given timezone. I have selected Kolkata.

![Select Sub-timezone][22]

#### Proxy settings

If you have any HTTP proxy, enter it at this stage, I had nothing, so I skipped the step by pressing the Enter key.

![Proxy Settings][23]

#### NTP client

Select which NTP client to run. I am once again going with the default chrony.

![NTP Client][24]

#### Mirror selection

The next screen is about the mirrors. You can view several lines of mirror list. Press R to view all. Now, you need to press “f” and enter to automatically analyze and save the fastest mirror from the list.

![Select fastest mirror][25]

This will analyze and do the rest for you. Wait for a couple of minutes.

#### Set up a new user

You will need an additional user besides the root, for normal use cases. You can create it here, right within the installer, to avoid difficulties letter. For this, you need to enter a username (all small letters), full name for the user and type and retype the user password.

![Set up a new user][26]

#### Some SSH Settings

Next is some SSH related settings, and I have chosen all the default options, by just pressing the enter key.

![SSH Settings][27]

#### Partitioning the Disk

This step is important, as it decides the installation of the system. You need to partition the disk. It will list the available disk, and you can enter “?” for help.

Then select the disk that needs to be used by name. In my case, it is the SDA, with the storage space. This will ask how to use it. You have several options like “sys”, “data” etc. For normal use cases, you need to select the “sys” option and press enter.

It will then show a warning about erasing the data. Press “y” and enter.

After some time, you will get a notification that the installation is complete.

![Partitioning the Disk][28]

You can either reboot the system here. But I will shut down the system using:

```

    poweroff

```

Then, remove the attached ISO and start the machine again to avoid booting into the live ISO.

### Step 4: Post-install set up

Now, you have installed the base system, but there is no desktop installed. So, you will be logged into the console again. You will now set up a minimal Xfce desktop and LightDM display manager for our Alpine Linux installation.

So, after booting into the system, login as root. Just use the username as `root` and enter the root password you have set during the installation.

#### Ensure superuser privileges

You need an editor for editing some config files. Since Alpine is a minimal set up, you need to install an editor first. Install Nano editor using:

```

    apk add nano

```

💡

In Alpine Linux, you have `doas` instead of `sudo`. But that is not used here because you are running as root.

First, make sure that the default user is added to `wheel` group. For me, it was added automatically. To check, run:

```

    groups <your-username>

```

This will list the groups your user is currently in. Look for the word “wheel”.

![User in Wheel Group][29]

If not, you can add by using the command:

```

    adduser <your-username> wheel

```

Now that the user is added to the wheel group. make sure the wheel group has its privileges by checking for the following line in `/etc/doas.d/doas.conf`

```

    permit persist :wheel

```

![Superuser privileges for User][30]

If not, edit the file using:

```

    nano /etc/doas.d/doas.conf

```

#### Enable community repositories

By default, Alpine Linux does not have the community repository enabled. But you should have this to install more packages. So, edit the repositories file using:

```

    nano /etc/apk/repositories

```

![Enable Community repositories][31]

Now, uncomment the line that refers to community repositories, save and exit.

### Step 5: Install Xfce desktop

Before installing the Xfce desktop, you need to make sure that you have xorg-base set up. For this, Alpine Linux provides a neat way. Run the code below:

```

    setup-xorg-base

```

This will install the required packages for you.

#### Install Xfce and LightDM

Now, you need to install the Xfce and related packages. I am going to use the LightDM Desktop Manager. So, run the command below to install.

```

    # apk add xfce4 xfce4-terminal xfce4-screensaver lightdm-gtk-greeter dbus

```

Once installation is finished, start the `dbus` (desktop bus) service:

```

    rc-service dbus start

```

Enable dbus to start on boot:

```

    rc-update add dbus

```

![Add DBus Service][32]

💡

If dbus is not running, it leads to issues like missing icons and keyboard shortcuts

Enable udev service:

```

    setup-devd udev

```

Now start the LightDM using:

```

    rc-service lightdm start

```

If your LightDM GUI has started and prompts a login, log in as root and open a terminal. Next, run the below command to enable LightDM to start up during boot. If not started, run the command in the same prompt.

![Login as root][33]

```

    rc-update add lightdm

```

![Enable LightDM during system start][34]

#### Allow Users to shut down and reboot

If you want to allow the users to shut down the machine or reboot the system, you need to have `polkit-elogind` and `elogind` installed.

```

    apk add elogind polkit-elogind

```

Now, reboot the system:

```

    reboot

```

![Running Alpine Linux][35]

### That's the end...

I understand that it is slightly different than the usual way of installing Linux in VirtualBox. But then Alpine Linux is slightly different from most other Linux distributions.

I hope you find this quick tutorial helpful in getting started with Alpine Linux. Please let me know if you have questions or suggestions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/alpine-linux-virtualbox/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/independent-linux-distros/
[4]: https://wiki.gentoo.org/wiki/OpenRC
[5]: https://itsfoss.com/systemd-free-distros/
[6]: https://linuxhandbook.com/what-is-busybox/
[7]: https://www.alpinelinux.org/downloads/
[8]: https://itsfoss.com/content/images/2024/03/click-on-new-virtualbox-1.png
[9]: https://itsfoss.com/content/images/2024/03/initial-virtual-machine-setup.png
[10]: https://itsfoss.com/content/images/2024/03/allocate-ram-and-cpu-core.png
[11]: https://itsfoss.com/content/images/2024/03/allocate-hard-disk-memory.png
[12]: https://itsfoss.com/content/images/2024/03/click-on-finish.png
[13]: https://itsfoss.com/content/images/2024/03/right-click-on-machine-and-select-settings.png
[14]: https://itsfoss.com/content/images/2024/03/allocate-display-memory.png
[15]: https://itsfoss.com/content/images/2023/07/enter-root-as-login-name.png
[16]: https://itsfoss.com/content/images/2023/07/set-keyboard-variant.png
[17]: https://itsfoss.com/content/images/2023/07/enter-system-hostname.jpg
[18]: https://itsfoss.com/content/images/2023/07/interface-settings.png
[19]: https://itsfoss.com/content/images/2023/07/ip-and-no-further-settings.png
[20]: https://itsfoss.com/content/images/2023/07/type-and-retype-root-password.png
[21]: https://itsfoss.com/content/images/2023/07/Set-time-zone-to-asia.png
[22]: https://itsfoss.com/content/images/2023/07/set-the-timezone-subzone.png
[23]: https://itsfoss.com/content/images/2023/07/set-proxy-if-any.png
[24]: https://itsfoss.com/content/images/2023/07/which-ntp-client-to-run.png
[25]: https://itsfoss.com/content/images/2024/03/set-fastest-mirror.png
[26]: https://itsfoss.com/content/images/2023/07/setup-a-new-user-1.png
[27]: https://itsfoss.com/content/images/2023/07/SSH-settings.png
[28]: https://itsfoss.com/content/images/2023/07/partition-the-disk.png
[29]: https://itsfoss.com/content/images/2024/04/user-in-wheel-group.png
[30]: https://itsfoss.com/content/images/2024/03/superuser-privileges-for-user.png
[31]: https://itsfoss.com/content/images/2024/03/enable-community-repository.png
[32]: https://itsfoss.com/content/images/2024/03/add-dbus-service.png
[33]: https://itsfoss.com/content/images/2024/03/login-as-root-in-lightdm-prompt.png
[34]: https://itsfoss.com/content/images/2024/03/add-light-dm-to-run-level.png
[35]: https://itsfoss.com/content/images/2024/03/running-alpine-in-virtualbox.webp
