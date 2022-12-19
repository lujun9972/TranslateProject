[#]: subject: "Setting up Fedora IoT on Raspberry Pi and rootless Podman containers"
[#]: via: "https://fedoramagazine.org/setting-up-fedora-iot-on-raspberry-pi-and-rootless-podman-containers/"
[#]: author: "gpoy92 https://fedoramagazine.org/author/gpoy92/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Setting up Fedora IoT on Raspberry Pi and rootless Podman containers
======

![][1]

Photo by [Harrison Broadbent][2] on [Unsplash][3]

### Introduction

Fedora IoT is a foundation for Internet of Things (IoT) and Device Edge ecosystems. It’s a secure, immutable, and image-based operating system that supports the deployment of containerized applications. We’ll discuss how you can run Fedora IoT on a Raspberry Pi to deploy a rootless Podman container.

### Running Fedora IoT on Raspberry Pi

Prerequisites:

  * PC (with Fedora)
  * SD-Card and SD-Card Reader
  * Raspberry Pi 3 or 4



Download the IoT image &amp; CHECKSUM for your CPU from [getfedora.org][4].

![][5]

After you download your Fedora IoT image, click _Verify your Download_ to download the CHECKSUM file.

![][6]

Place the CHECKSUM file in the same location where you downloaded your Fedora IoT image.

Then, install gnupg and the arm image installer:

```

    dnf install gnupg2 arm-image-installer

```

Next, import Fedora’s GPG keys to verify the image you downloaded:

```

    $ curl -O https://getfedora.org/static/fedora.gpg

```

Then, verify the CHECKSUM file has a good signature:

```

    $ gpgv --keyring ./fedora.gpg *-CHECKSUM

```

You should see something similar to the following in the output:

```

    $ gpgv --keyring ./fedora.gpg *-CHECKSUM
    gpgv: Signature made Fri 19 Mar 2021 10:10:28 AM EDT
    gpgv:                using RSA key 8C5BA6990BDB26E19F2A1A801161AE6945719A39
    gpgv: Good signature from "Fedora (34) <fedora-34-primary@fedoraproject.org>"

```

Lastly, verify the checksum of your download to verify that the signature matches:

```

    $ sha256sum -c *-CHECKSUM

```

Now, find the name of the SD-Card. You can use various tools, but in this article, we recommend using udisks command line tool udiskctl. First, verify that you have NOT inserted your SD-Card into your SD-Card reader.

Then, enter the following command:

```

    udisksctl status

```

The output displays all the connected devices on your machine. Review what devices are currently displayed. Next, plug in your SD-Card and enter the command again. Write down the name of the device that’s been added to the previous list.

**Use caution when flashing your SD-Card. If you choose the wrong device, you might overwrite your hard drive.**

Flash the image onto the SD-Card.

```

    $ arm-image-installer --image=</path/to/fedora_image> \
          --target=<RPi_Version> --media=/dev/<sd_card_device> \
          --addkey=/path/to/pubkey \
          --resizefs

```

  * _Image_ – File path to the image you downloaded.
  * _target_ – Type of arm board you are using (in this example it would be either the Raspberry Pi 3 or 4).
  * _media_ – SD-Card path you identified.
  * _addkey_ – Your SSH key.
  * _resizefs_ – Resizes the image to the full SD-Card unless you have another partition to add.



The image won’t have a per-configured user or password.

[Zezere][7] is a provisioning service that can deploy devices without a physical console. Use Zezere to set up and deploy your device.

Navigate to [provision.fedoraproject.org][8], then click the _Claim Unowned Devices_ tab, and claim your device (i.e. your SD-Card). Click the _Home_ tab to view your claimed device, then click the SSH Key Management tab to add your SSH key. This allows you to copy your SSH key to any of your Fedora IoT devices. The keys generated in the _SSH Key Management_ tab are public, so they can be shared without risk to the security of your devices.

![][9]

Return to the _Home_ tab and click _Submit provision request_ on your SD-Card to set up a provisioning request. Select _fedora-iot-stable_ from the drop-down and click _Schedule_ to copy your SSH Key onto your Fedora IoT device.

You’re now ready to run your applications.

### Setting up rootless Podman containers

Fedora IoT uses Podman to develop, manage, and run Open Container Initiative (OCI) containers. Rootless containers can be run by unprivileged users, adding security against hackers to ensure they’re safe to share between machines.

Install _slirpfnetns_ and _fuse-overlays_ to begin setup of a rootless Podman container:

```

    sudo dnf -y install slirp4netns fuse-overlayfs shadow-utils

```

Rootless Podman containers require the root user to have a range of UIDs/GIDs listed in the _/etc/subuid_ and _/etc/subgid_ files*.* Update the _/etc/subuid_ and _/etc/subgid_ for each non-root user.

```

    sudo usermod --add-subuids START-RANGE --add-subgids START-RANGE USERNAME

```

  * _START_ – Starting UID (ex. 1000)
  * _RANGE_ – Range for you UID (ex. if you put 100, then your UID will range from 1000 to 1100)
  * _USERNAME_ – The username you’re updating.



Podman is now set up to run rootless containers.

### More setup recommendations

View the following resources for additional ways you can improve the setup of your containers:

  * [Using Ansible to configure Podman containers][10]
  * [Auto-updating Podman containers with systemd][11]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/setting-up-fedora-iot-on-raspberry-pi-and-rootless-podman-containers/

作者：[gpoy92][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/gpoy92/
[b]: https://github.com/lujun9972
[1]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/12/Fedora-IoT-Rasp-pi-Podman-816x345.jpg
[2]: https://unsplash.com/@harrisonbroadbent?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/raspberry-pi?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://getfedora.org/en/iot/download/
[5]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/12/image-1024x416.png
[6]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/12/image-2.png
[7]: https://docs.fedoraproject.org/en-US/iot/ignition/
[8]: http://provision.fedoraproject.org
[9]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/12/image-4.png
[10]: https://fedoramagazine.org/using-ansible-to-configure-podman-containers/
[11]: https://fedoramagazine.org/auto-updating-podman-containers-with-systemd/
