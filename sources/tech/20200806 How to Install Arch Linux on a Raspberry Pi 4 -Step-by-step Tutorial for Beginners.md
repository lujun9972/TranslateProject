[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Install Arch Linux on a Raspberry Pi 4 [Step-by-step Tutorial for Beginners])
[#]: via: (https://itsfoss.com/install-arch-raspberry-pi/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

How to Install Arch Linux on a Raspberry Pi 4 [Step-by-step Tutorial for Beginners]
======

Raspberry Pi has been undoubtedly the way to go for inexpensive single-board computing. You can create [Raspberry Pi projects][1] for powering everything from robots to smart home devices.

When the [Raspberry Pi 4][2] launched in 2019, the performance amazed the Raspberry Pi enthusiasts. A more powerful CPU, USB 3.0 support, native Gigabit Ethernet, plus the ability to output 4K video at 60 Hz on dual monitors are the major improvements. The intent was to pitch Raspberry Pi as an entry-level desktop computer.

More recently, the Raspberry Pi 4 offers an 8 GB RAM model, which is better not only as a desktop but also for hosting databases and servers.

There are many [operating systems that can be installed on a Raspberry Pi][3]. Apart from the official Raspberry Pi OS (previously known as [Raspbian][4]), we have covered [installation of Ubuntu MATE on Raspberry Pi][5]. And in this tutorial I will cover a step by step Arch Linux installation.

### Installing Arch Linux on a Raspberry Pi 4

![][6]

Note

Arch Linux doesn’t support [ARM architecture][7] (used by [devices like Raspberry Pi][8]) officially. But there is a separate project called Arch Linux ARM that ports Arch Linux to ARM devices. But it is only available in 32-bit format.

I am going to use it for getting Arch on Raspberry Pi.

You’ll need the following things for this tutorial:

  * A microSD card of 8 GB at least.
  * A Linux system with card reader slot for preparing the microSD card for Arch installation.
  * Active internet connection.
  * A [Raspberry Pi device with essential accessories][9], of course.



Since the installation procedure is purely terminal-based, _**you should have intermediate knowledge of the Linux command line and you should be comfortable in using terminal**_.

#### Step 1: Insert the microSD card in your card reader

When you insert you microSD card in your card reader, open the terminal, get **root /sudo** access and list the block devices to identify the card. **The installation process needs to be done using root priviledges.**

```
fdisk -l
```

My block device is the mmcblk0, your device may be **different**.

![][10]

#### Step 2: Format and create the partitions

Partition the SD card using fdisk command. Keep in mind to replace the device name with your sd card’s name.

```
fdisk /dev/mmcblk0
```

At the fdisk prompt, the existing partitions have to be deleted and a new one should be created.

  1. Type o. This will purge any partitions on the drive.
  2. Type p to list partitions. To check if any partition is still present.
  3. **To create the boot partition**: Type n, then p for primary, 1 for the first partition on the drive, press ENTER to accept the default first sector, then type +100M for the last sector.
  4. Type t, then c to set the first partition to type W95 FAT32 (LBA).
  5. **To create the root partition**: Type n, then p for primary, 2 for the second partition on the drive, and then press ENTER twice to accept the default first and last sector.
  6. Write the partition table and exit by typing w.



![][11]

#### Create and mount the FAT &amp; ext4 filesystems

At this point, I will create the filesystem for the boot and root partition [using mkfs command][12] and then mount it. If in doubt about the partition names, list again the partitions as you did in the first step.

```
mkfs.vfat /dev/mmcblk0p1
mkdir boot
mount /dev/sdX1 boot
mkfs.ext4 /dev/mmcblk0p2
mkdir root
mount /dev/sdX2 root
```

![][13]

#### Download and extract Arch Linux for Raspberry Pi 4

Make sure that you have root access (otherwise the process may fail), and run the following commands (with sudo, if you are not root).

```
wget http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-4-latest.tar.gz
bsdtar -xpf ArchLinuxARM-rpi-4-latest.tar.gz -C root
sync
```

![][14]

Now move the boot files to the boot partition you had created:

```
mv root/boot/* boot
umount boot root
```

You might see _**“Failed to preserve ownership”**_ errors. That’s normal because the boot partition isn’t owned by anyone.

#### Step 3: Insert the microSD card into the Raspberry Pi and, connect the power supply and to the Internet.

At this step Arch Linux is installed on the SD card, and the rest of the configurations will be done from the Raspberry pi.

You can either follow the rest of the tutorial, either directly on the Raspberry Pi by connecting a monitor and a keyboard set, or you can connect remotely to the Raspberry Pi via SSH (if you don’t have a spare monitor, you need to connect via Ethernet to your local network).

I will connect to my Raspberry Pi via SSH for this tutorial. To get the IP address of the Raspberry Pi, check the [devices connected to your network][15] and see which one is the Raspberry Pi.

**Connect via WiFi**

If an Ethernet connection is not an option, you can access your WiFi network after you login as **root** using the following command. **Please note that you need a keyboard set and a monitor to initially connect on your WiFi.**

Note: I am aware that wifi-menu is being discontinued in the original Arch Linux. For the moment, it works in Arch Linux ARM.

```
wifi-menu
```

Once you find the IP address of your Raspberry pi, type the following command at your computer’s terminal using your IP address:

```
ssh [email protected]_pi_ip_address
```

Please note the **default user name is alarm and the default user password is alarm**. The default root password is **root**.

![][16]

To complete the installation process, you need to initialize the pacman keyring and populate the Arch Linux ARM [package signing][17] keys:

```
pacman-key --init
pacman-key --populate archlinuxarm
```

At this point the installation process has been completed and you can upgrade the system packages as root using the same [pacman commands][18] as you do with an x86 architecture machine.

```
pacman -Syu
```

If you want to reboot your Raspberry pi after a system upgrade, simply type **reboot** in the terminal and connect again via SSH.

### Bonus tips after installing Arch Linux on Raspberry Pi

To make the use of Arch Linux on a Raspberry Pi 4 more convenient I will show you a few tweaks/additions that you can do.

  * Connect directly as root via SSH
  * Change the default username and password
  * Add a user to the sudoers
  * Change the default root password
  * Change your hostname
  * Install an AUR Helper



#### Connect directly as root via SSH

In order to change the default username you have to logoff and login as root only.

By default it is not permitted to directly login as root via SSH, but you can change that.

As a root user, edit the sshd_config file found in _/etc/ssh/sshd_config_:

```
nano /etc/ssh/sshd_config
```

Uncomment the PermitRootLogin and next to it type yes, or add the following line to the file. You can add it anywhere but it’s good practice to find the authentication block and add it there.

![][19]

Save and exit the file, and restart the SSH server.

```
systemctl restart sshd
```

Now type exit twice, to exit root and exit the SSH remote connection.

To connect to your raspberry pi as root, use the root name instead the default username and your ip address.

```
ssh [email protected]_pi_ip_address
```

Remember that the default root password is **root**.

![][20]

#### Change the default username and password and the default root password

To change the default username and password type the following commands at your terminal

```
usermod -l new_username old_username
passwd username
usermod -d /home/new_username -m new_username
```

To change the default root password type the following command at your terminal

```
passwd
```

![][21]

#### Give sudo privileges for your user

To be able to give sudo privileges to a user, you need to install the sudo package as a prerequisite.

```
pacman -S sudo
```

The configuration file for sudo is /etc/sudoers. It should always be edited with the visudo command.

```
EDITOR=nano visudo
```

Once you open the configuration file, add your username in a similar way as I do, preferably under the root user. Then save the file and exit.

![][22]

#### Change the default hostname

To [change system hostname][23] on **Systemd** based distributions, you need to use **hostnamectl** command as shown:

```
hostnamectl set-hostname New_Hostname
```

Now type exit, to terminate the SSH session and login again with your new username, and your new user password.

```
ssh [email protected]_pi_ip_address
```

#### Install an AUR Helper

Many users prefer Arch Linux or an [Arch Linux based distribution][24] for the large Arch User Repository. You can use the [AUR packages][25] on an ARM instruction set machine but, not all of them are compatible with this architecture.

To begin with, make sure that you have the git package and base-devel group installed.

```
sudo pacman -S git base-devel
```

You can now install whichever package from the AUR you like or via an [AUR Helper][26] in a similar manner which is a package in AUR too. My personal choice is yay, but you can install whichever you prefer.

```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

#### Conclusion

Although I’m an Arch Linux user and a rolling release distribution is my way to go, you may want to choose another distribution for the Raspberry pi 4 with 8GB RAM, as at the moment that this tutorial is written, this image is a 32bit OS (armv7).

An alternative solution but with a desktop environment could be the [Manjaro ARM][27] distribution which supports 64bit (armv8). If you want a 64bit OS, other than the official Raspberry Pi OS, without a desktop environment the Ubuntu Server is also a good choice and the [installation][28] is insanely easy.

That said, I will keep the Arch Linux on my Raspberry Pi 4, as I bought the 2 GB model, to use it for a very specific purpose.

Are you curious about what I will do with my Raspberry Pi and Arch Linux? Make sure you [subscribe to our newsleter][29] and I will reveal it in my future articles!

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-arch-raspberry-pi/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/raspberry-pi-projects/
[2]: https://itsfoss.com/raspberry-pi-4/
[3]: https://itsfoss.com/raspberry-pi-os/
[4]: https://itsfoss.com/raspberry-pi-os-desktop/
[5]: https://itsfoss.com/ubuntu-mate-raspberry-pi/
[6]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/13.png?ssl=1
[7]: https://www.allaboutcircuits.com/technical-articles/arm-architecture-explained/
[8]: https://itsfoss.com/raspberry-pi-alternatives/
[9]: https://itsfoss.com/things-you-need-to-get-your-raspberry-pi-working/
[10]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/1.png?ssl=1
[11]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/2.png?ssl=1
[12]: https://linuxhandbook.com/mkfs-command/
[13]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/4.png?ssl=1
[14]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/5.png?ssl=1
[15]: https://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/
[16]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/6.png?ssl=1
[17]: https://archlinuxarm.org/about/package-signing
[18]: https://itsfoss.com/pacman-command/
[19]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/8.png?ssl=1
[20]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/9.png?ssl=1
[21]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/10.png?ssl=1
[22]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/11.png?ssl=1
[23]: https://itsfoss.com/change-hostname-ubuntu/
[24]: https://itsfoss.com/arch-based-linux-distros/
[25]: https://itsfoss.com/aur-arch-linux/
[26]: https://itsfoss.com/best-aur-helpers/
[27]: https://manjaro.org/download/#raspberry-pi-4
[28]: https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-ubuntu#2-on-your-ubuntu-machine
[29]: https://itsfoss.com/subscribe-to-newsletter/
