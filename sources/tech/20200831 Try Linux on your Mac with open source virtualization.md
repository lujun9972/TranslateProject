[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Try Linux on your Mac with open source virtualization)
[#]: via: (https://opensource.com/article/20/9/try-linux-mac)
[#]: author: (Bryant Son https://opensource.com/users/brson)

Try Linux on your Mac with open source virtualization
======
Take Fedora out for a test run on your macOS machine using QEMU
virtualization.
![Woman programming][1]

Virtualization opens up a wonderland of new opportunities for anyone, including ordinary computer users who want to try out a new operating system. Are you using a Mac but want to try Microsoft Windows? You can, with a virtualization solution. What about if you are using Windows but want to try a macOS or a Linux platform? This is also possible with virtualization.

Various virtualization solutions exist. Mac users typically think of Parallels, but it is proprietary software. If you are a developer, you might know about [VirtualBox][2]. While VirtualBox is an excellent tool, there is another option: [QEMU][3], which is an open source machine emulator and virtualizer available under the [GPLv2 license][4].

![QEMU home page][5]

(Bryant Son, [CC BY-SA 4.0][6])

This step-by-step tutorial explains how to use QEMU to run Fedora Linux on macOS. QEMU is also supported on pretty much every platform, including Windows and various Linux distributions.

If you prefer watching a video to reading, please see the YouTube version of this tutorial:

## Step 1: Install QEMU with Homebrew

If you're not using macOS, visit [QEMU's download page][7] to install it for your operating system.

If you're using a Mac, you can use Homebrew to install QEMU. If you don't have Homebrew yet, Matthew Broberg's [introduction to Homebrew][8] will help you install and configure it.

To install QEMU with Homebrew, enter:

```
brew install qemu
```


    This command should install all of QEMU's dependencies, utilities, and more.


```
![Install QEMU with Homebrew][9]

(Bryant Son, [CC BY-SA 4.0][6])
```

```
## Step 2: Download a Fedora ISO image for your workstation
```


    Next, download a Fedora Workstation image you can use to boot a Fedora environment through QEMU. Fedora is an open source Linux distribution, and its primary license is GPLv2. One great thing about virtualization is, if you want to use a different platform, you can.


    Get the Fedora Workstation ISO image by visiting the Fedora homepage and clicking the Download Now button under Fedora Workstation.


```
![Download Fedora][10]

(Bryant Son, [CC BY-SA 4.0][6])
```


    You want to download an ISO image, so click the Download button under x86_64. Save the file in a new directory that you can remember.


```
![Click the ISO image under x86_64][11]

(Bryant Son, [CC BY-SA 4.0][6])
```

```
## Step 3: Download a Fedora QCOW2 image for the file drive
```


    In addition to the ISO image above (which is used for booting a Fedora Workstation), you also need a QCOW2 image, which stands for QEMU Copy On Write. QCOW2 uses a disk-storage optimization strategy that delays storage allocation until it is needed. The QCOW2 format is used by QEMU, OpenStack, and KVM.


    Visit the Fedora Cloud Base images page and click the Download link next to Cloud Base Image for OpenStack. This will download the QCOW2 image; save the file in the same directory where you put your Fedora Workstation ISO image.


```
![Click Download link in Cloud Base image for Openstack][12]

(Bryant Son, [CC BY-SA 4.0][6])
```

```
## Step 4: Resize the QCOW2 image
```


    You should have two files in this directory. You can check with the ls command.


```
![an ISO file and a QCOW2 file][13]

(Bryant Son, [CC BY-SA 4.0][6])
```


    The qemu-img command will allow you to resize the downloaded QCOW2 image to any size you want to allocate. Use this command to allocate 10GB for your drive:

```

```

    qemu-img create -f qcow2 DOWNLOADED_QCOW2_FILE 10G
```

```
```

```

![Allocating 10GB for a QCOW image][14]

(Bryant Son, [CC BY-SA 4.0][6])
```

```

## Step 5: Run Fedora with QEMU

```
Run Fedora with the following qemu-system-x86_64 command:

[code]
```

 qemu-system-x86_64 \
-m 2048 \
-vga virtio \
-cdrom ./Fedora-Workstation-Live-x86_64-32-1.6.iso \
-accel hvf \
-show-cursor \
-usb \
-device usb-tablet \
-drive file=./Fedora-Cloud-Base-32-1.6.x86_64.qcow2,if=virtio

```

```


```
![Run the qemu-system-x86_64 command][15]

(Bryant Son, [CC BY-SA 4.0][6])
```


```

```

    Here is wh