[#]: subject: "Update on hibernation in Fedora Workstation"
[#]: via: "https://fedoramagazine.org/update-on-hibernation-in-fedora-workstation/"
[#]: author: "Zbigniew Jędrzejewski-Szmek https://fedoramagazine.org/author/zbyszek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Update on hibernation in Fedora Workstation
======

![][1]

Photo by [Ruiqi Kong][2] on [Unsplash][3] (cropped)

### Goals and rationale

Hibernation stores the state of the whole operating system — the contents of memory used by the kernel and all programs — on disk. The machine is then completely powered off. Upon next boot, this state is restored and the old kernel and all the programs that were running continue execution.

Hibernation is nowadays used less often, because “suspend” — the state where CPU is powered down, but the contents of memory are preserved, works fine on most laptops and other small devices. But if the suspend is implemented poorly and it drains the battery too quickly, or if the user needs to completely power off the device for some reasons, hibernation can still be useful.

We need a storage area for hibernation. The kernel allows two options:
– either a single large-enough **swap device** , usually a partition,
– or a single large-enough **swap file** on some file system.

Fedora Linux installations by default do not use a normal swap device or file. Instead, a zram device is created, which is an in-memory compressed swap area. It is not suitable for hibernation. This means that hibernation does not work out-of-the-box on Fedora Linux. This guide describes how to create a swap file to enable hibernation.

### Limitations

This method only works on UEFI!

To check that the system uses UEFI:

```

    bootctl

```

If this commands prints “Not booted with EFI”, then the method described below won’t work. Refer to the original [Hibernation in Fedora Workstation][4] (for Fedora Linux 36) instead.

Another severe limitation is that SecureBoot must be disabled. The kernel does not allow hibernation with SecureBoot! Disabling SecureBoot reduces the security of the machine somewhat. Thus, do this only if you think that hibernation is more worth it.

### Implementation

First, check whether Secure Boot is on:

```

    bootctl

```

If this prints “Secure Boot: disabled” then SB is off. Otherwise, reboot the machine, go into UEFI settings, and disable Secure Boot.

Second, create and enable a swap file:

```

    SWAPSIZE=$(free | awk '/Mem/ {x=$2/1024/1024; printf "%.0fG", (x<2 ? 2*x : x<8 ? 1.5*x : x) }')
    sudo btrfs subvolume create /var/swap
    sudo mkswap --file -L SWAPFILE --size $SWAPSIZE /var/swap/swapfile
    sudo bash -c 'echo /var/swap/swapfile none swap defaults 0 0 >>/etc/fstab'
    sudo swapon -av

```

This should print a message that swap was enabled on _/var/swap/swapfile_. The swap file is added to fstab, so it’ll be permanently active. This is a good thing, it should make the system more reliable in general.

Now we are ready to test hibernation:

```

    systemctl hibernate

```

After the system has shut down, boot it again and let one of the kernels start. The machine should return to the previous state from before hibernation.

This method does not require further configuration because systemd automatically stores the location of the swap file before entering hibernation in an UEFI variable, and then after the reboot, reads that variable and instruct the kernel to resume from this location. This only works on UEFI systems, but is otherwise quite simple and robust.

### Reverting the changes

```

    sudo swapoff -v /var/swap/swapfile
    sudo sed -r -i '/.var.swap.swapfile/d' /etc/fstab
    sudo btrfs subvolume rm /var/swap

```

After that, reenable SecureBoot if appropriate.

### Troubleshooting

This process mail fail in two ways:

  * either going into hibernation fails, i.e. the kernel does not save the state and the machine does not actually power off,
  * or loading of saved state fails, and we end up with a fresh boot.



In both cases, the first step is to look at _journalctl -b_ , in particular any error lines.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/update-on-hibernation-in-fedora-workstation/

作者：[Zbigniew Jędrzejewski-Szmek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zbyszek/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/01/hybernation-1-816x345.jpg
[2]: https://unsplash.com/@sakamotomari?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-cat-sitting-on-top-of-a-wooden-bench-poKfZXJfmqI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/hibernation-in-fedora-36-workstation/
