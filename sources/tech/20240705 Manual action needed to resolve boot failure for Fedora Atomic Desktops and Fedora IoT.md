[#]: subject: "Manual action needed to resolve boot failure for Fedora Atomic Desktops and Fedora IoT"
[#]: via: "https://fedoramagazine.org/manual-action-needed-to-resolve-boot-failure-for-fedora-atomic-desktops-and-fedora-iot/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Manual action needed to resolve boot failure for Fedora Atomic Desktops and Fedora IoT
======

![][1]

Photo by [Growtika][2] on [Unsplash][3] (cropped)

Since the 39.20240617.0 and 40.20240617.0 updates for Atomic Desktops and the 40.20240617.0 update for IoT, systems with Secure Boot enabled may fail to boot if they have been installed before Fedora Linux 40. You might see the following error:

```

    error: ../../grub-core/kern/efi/sb.c:182:bad shim signature.
    error: ../../grub-core/loader/i386/efi/linux.c:258:you need to load the kernel first.

    Press any key to continue...

```

### Workaround

In order to resolve this issue, you must first boot into the previous version of your system. It should still be functional. In order to do this, reboot your system and select the previous boot entry in the selection menu displayed on boot. Its name should be something like:

```

    Fedora Linux 39.20240610.0 (Silverblue)  (ostree:1)

```

Once you have logged in, search for the terminal application for your desktop and open a new terminal window. On Fedora IoT, log in via SSH or on the console. Make sure that you are not running in a toolbox for all the commands listed on this page.

If you are running a Fedora Atomic Desktop based on Fedora 39 and have not yet updated to Fedora 40, you first need to update to the latest working Fedora 39 version with those commands:

```

    $ sudo rpm-ostree cleanup --pending
    $ sudo rpm-ostree deploy 39.20240616.0

```

If you are running Fedora IoT, then first update to the latest working version with this command:

```

    $ sudo rpm-ostree cleanup --pending
    $ sudo rpm-ostree deploy 40.20240614.0

```

Then reboot your system.

Once you are logged in again on the latest working version, proceed with the following commands:

```

    $ sudo -i
    $ cp -rp /usr/lib/ostree-boot/efi/EFI /boot/efi
    $ sync

```

Once completed, reboot your system. You should now be able to update again, as normal, using the graphical interface or the command line:

```

    $ sudo rpm-ostree update

```

### Why did this happen?

On Fedora Atomic Desktops and Fedora IoT systems, the components that are part of the boot chain (Shim, GRUB) are not (yet) automatically updated alongside the rest of the system. Thus, if you have installed a Fedora Atomic Desktop or a Fedora IoT system before Fedora 40, it uses an old versions of the Shim and bootloader binaries to boot your system.

When Secure Boot is enabled, the EFI firmware loads Shim first. Shim is signed by the Microsoft Third Party Certificate Authority so that it can be verified on most hardware out of the box. The Shim binary includes the Fedora certificates used to verify binaries signed by Fedora. Then Shim loads GRUB, which in turn loads the Linux kernel. Both are signed by Fedora.

Until recently, the kernel binaries where signed two times, with an older key and a newer one. With the 6.9 kernel update, the kernel is no longer signed with the old key. If GRUB or Shim is old enough and does not know about the new key, the signature verification fails.

See the initial report in the [Fedora Silverblue issue tracker][4].

### What are we doing to prevent it from happening again?

We have known for a while that not updating the bootloader was not a satisfying situation . We have been working on enabling bootupd for Fedora Atomic Desktops and Fedora IoT. bootupd is a small application that is responsible only for bootloader updates. While initially planned for Fedora Linux 38 (!), we had to delay enabling it due to various issues and missing functionality in bootupd itself and changes needed in Anaconda.

We are hoping to enable bootupd in Fedora Linux 41, hopefully by default, which should finally resolve this situation. See the [Enable bootupd for Fedora Atomic Desktops and Fedora IoT][5] Fedora Change page.

Note that the root issue also impacts Fedora CoreOS but steps have been put in place to force a bootloader update before the 6.9 kernel update. See the [tracking issue for Fedora CoreOS][6].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/manual-action-needed-to-resolve-boot-failure-for-fedora-atomic-desktops-and-fedora-iot/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/06/grub-failure-816x345.jpg
[2]: https://unsplash.com/@growtika?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-close-up-of-a-key-h12YQzsuFdc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://github.com/fedora-silverblue/issue-tracker/issues/543
[5]: https://fedoraproject.org/wiki/Changes/FedoraSilverblueBootupd
[6]: https://github.com/coreos/fedora-coreos-tracker/issues/1752
