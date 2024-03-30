[#]: subject: "Turn your Raspberry Pi into a NAS using Samba (SMB) Server"
[#]: via: "https://itsfoss.com/raspberry-pi-nas-samba/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Turn your Raspberry Pi into a NAS using Samba (SMB) Server
======

[![Warp Terminal][1]][2]

Are you tired of the challenge posed by a crowded local storage, making file retrieval feel like a scavenger hunt?

Worry not! Today, we embark on the transformation of your Raspberry Pi into a **Network-Attached Storage (NAS)** solution.

Say farewell to the complexities of an overloaded local storage. Instead, envision your Raspberry Pi, equipped with a **Samba Server** , seamlessly organizing files for efficient collaboration, simultaneous access, and reliable backups.

### What is Samba?

Samba is a software suite that enables seamless file and print services interoperability using [Server Message Block (SMB) / Common Internet File System (CIFS)][3] file sharing standard which is widely supported by various operating systems like Windows, MacOS, Linux and even Android.

There are other NAS oriented solutions available for Raspberry Pi like [Open Media Vault][4]. I find SMB share to be the easiest to set up and if you are new to network storage, I think you should try this hassle-free method.

### Requirements

  * Raspberry Pi
  * SD Card (8 GB+)
  * Raspbian OS installed (commands mentioned here work on that)
  * Ethernet Cable (Optional)
  * Keyboard & Mouse (Optional)
  * External HDD/ SSD



✋

The USB ports on Raspberry Pi may not be sufficient enough to power up an External Hard Drive. So, I would suggest you to use an external power supply or buy a HDD docking station.

### Installing Samba and it's dependencies

First, make sure to [install Raspbian OS on your Raspberry Pi][5]. I won't discuss those steps here.

The first order of business when start working on Linux is to ensure that you have all the latest packages installed.

```

    sudo apt update && sudo apt upgrade -y

```

To install the Samba packages you just need to `apt-get` as they are available in the repository.

```

    sudo apt-get install samba samba-common-bin

```

The work is not done here since you need to create a folder which will be shared. This folder can be located even on external drive mounted to Pi.

### Creating a shared folder

For this tutorial, I am mounting an external drive and creating a new folder inside `/media` directory.

I am going to give this folder all the permission i.e. `read/write/execute (rwx)` so that anyone on my sub-network with the access to my server can share files easily.

```

    sudo mkdir -m 1777 /media/hdd/shared

```

### Editing the SMB Config file

Once you have created the folder, it's time to configure your SMB share. You need to do is edit `smb.conf` file to make your share visible on the network.

```

    sudo nano /etc/samba/smb.conf

```

Inside this config file, you need to add the following code at the bottom:

```

    [itsfossnas]
    path = /media/hdd/shared
    writeable=Yes
    create mask=0777
    directory mask=0777
    public=no

```

Then save and exit out of Nano using `CTRL + X` then press `Y` .

Here, `[itsfossnas]` is the name of my share and it'll be used to connect to the network share with the address like `\\localhost\itsfossnas`.

![][6]

### Creating a User for Samba share

Creating a user for Samba share is crucial for access control, security, and personalized settings.

I am going to create a user called `abhishek` in this example.

```

    sudo smbpasswd -a abhishek

```

Once you press `Enter`, it will prompt you to create a password for this user.

![][7]

Finally, you need to restart the samba service:

```

    sudo systemctl restart smbd

```

Samba will restart automatically when every time you boot up your Pi.

Now it's time to connect to your Samba share and to do that, you need to locate the Pi on the network.

The easiest method is to type `hostname -I` on the terminal or you can check the DHCP record of your router which will show the IP address assigned to your Pi.

### Mounting your Samba Server on Windows

To mount your server in Windows is quite simple. Inside the file explorer app, at the top you will need to click the menu icon `...` and a list of options will pop up on your screen from which, You have to select `Map Network drive` .

I am using Windows 11 in this tutorial.

![][8]

After that, it will ask you to set the drive letter for your share and the address of your Server. In my case, it is `\\192.168.1.11\itsfossnas` .

![][9]

Finally, it will prompt you to enter you `Login credentials` i.e. the Username and the Password we set at the above step and once you are done, just press `Ok`.

![][10]

Your drive is now mounted successfully.

![][11]

The speeds will vary based on whether you are on WiFi or connected via Ethernet cable.

### Conclusion:

I won't say that this will be your permanent storage and backup solution but it is quite impressive that how such a small device can do so much.

I think it's great for learning about Network Storage options before you go all in and buy an expensive NAS.

Hope you have learned something new. Feel free to share your experience or your DIY storage solutions with us in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-nas-samba/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://learn.microsoft.com/en-us/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview
[4]: https://itsfoss.com/raspberry-pi-nas-samba/%5Bhttps://www.openmediavault.org/%5D(https://www.openmediavault.org/)
[5]: https://itsfoss.com/tutorial-how-to-install-raspberry-pi-os-raspbian-wheezy/
[6]: https://itsfoss.com/content/images/2024/01/adding-smb-share-in-config-file-samba-tutorial-raspberrypi.png
[7]: https://itsfoss.com/content/images/2024/01/creating-username-and-password-for-samba-tutorial-raspberrypi.png
[8]: https://itsfoss.com/content/images/2024/01/file-explorer-mapping-network-drive-samba-tutorial-raspberrypi.png
[9]: https://itsfoss.com/content/images/2024/01/adding-server-address-with-smb-share-details-samba-tutorial-raspberrypi.png
[10]: https://itsfoss.com/content/images/2024/01/login-your-smb-share-samba-tutorial-raspberrypi-1.png
[11]: https://itsfoss.com/content/images/2024/01/mounted-smb-folder-in-windows-explorer-samba-tutorial-raspberrypi.png
