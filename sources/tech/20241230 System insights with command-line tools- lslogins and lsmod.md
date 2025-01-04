[#]: subject: "System insights with command-line tools: lslogins and lsmod"
[#]: via: "https://fedoramagazine.org/system-insights-command-line-lslogins-lsmod/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

System insights with command-line tools: lslogins and lsmod
======

![][1]

Photo by [Hunter Harritt][2] on [Unsplash][3] cropped

Continuing our [exploration][4] [of][5] [commands][6] that provide insights into the inner workings of your Fedora Linux system, we turn our focus to more simple ones like _lslogins_ and _lsmod_. These tools offer information about user accounts and [kernel modules][7], respectively.

## **_lslogins_ : Look into User Accounts**

_lslogins_ is a command that extracts and displays detailed information about user accounts on your system. It pulls data from _/etc/passwd_ and _/etc/shadow_ files, along with system logs, to give you a comprehensive overview. It is especially useful to look for login failures and to list group memberships.

### **Basic Usage**

Run the command without arguments to display a summary of all user accounts:

```

    lslogins

```

This provides an overview including UID (User ID), GID (Group ID), user name, and last login details.

### **Common options** and usage example

  * _-u_ : Display only user accounts and root (filtering out system accounts with UIDs below 1000).
  * _-G_ : Display information about exiting groups
  * _-g <group>_: Show users of a specific group (e.g. _wheel_ which usually has _sudo_ -permissions on a Red Hat system).
  * _-e_ : Display in an export-able key-value output format, separated by space.
  * _-L_ : List last logins and password information (empty, logged, nologin).



Examples, listing the last logins and password information (empty, logged, nologin) of non-system user accounts on my laptop as well as group memberships:

```

    $ lslogins -L -p -u
     UID USER      LAST-TTY LAST-HOSTNAME LAST-LOGIN PWD-EMPTY PWD-LOCK PWD-DENY NOLOGIN HUSHED PWD-METHOD
       0 root                                                                          0
    1000 ahaerter  tty2     tty2               01:16                                   0      0

    $ lslogins -G -u
     UID USER       GID GROUP     SUPP-GIDS  SUPP-GROUPS
       0 root         0 root
    1000 ahaerter  1000 user      971,10,977 docker,wheel

```

## _lsmod_ : **Listing Kernel modules for further inspection**

The Linux kernel is [fundamentally monolithic][8] in design, but it also provides the capability to load and unload modules at runtime. A kernel module is generally understood as a component or an extension of the kernel. For example, hardware drivers (e.g., Wi-Fi cards, sound cards, etc.) are usually implemented as modules. The _lsmod_ command provides a nice overview of all currently loaded kernel modules.

### Basic usage

Simply type:

```

    lsmod

```

This displays a table with three columns:

  1. Module: The name of the kernel module.
  2. Size: The memory size (in bytes) the module occupies.
  3. Used By: Lists the dependent modules or kernel features.



Example output:

```

    $ lsmod
    Module                  Size  Used by
    overlay               241664  0
    tun                    73728  2
    snd_usb_audio         614400  0
    snd_usbmidi_lib        57344  1 snd_usb_audio
    snd_ump                49152  1 snd_usb_audio
    snd_rawmidi            57344  2 snd_usbmidi_lib,snd_ump
    hid_jabra              16384  0
    uinput                 20480  0
    rfcomm                102400  16
    snd_seq_dummy          12288  0
    snd_hrtimer            12288  1
    wireguard             122880  0
    curve25519_x86_64      36864  1 wireguard
    libcurve25519_generic    45056  2 curve25519_x86_64,wireguard
    ip6_udp_tunnel         16384  1 wireguard
    udp_tunnel             36864  1 wireguard
    nf_conntrack_netbios_ns    12288  1
    nf_conntrack_broadcast    12288  1 nf_conntrack_netbios_ns
    nft_fib_inet           12288  1
    nft_fib_ipv4           12288  1 nft_fib_inet
    nft_fib_ipv6           12288  1 nft_fib_inet
    nft_fib                12288  3 nft_fib_ipv6,nft_fib_ipv4,nft_fib_inet
    [...]

```

### Usage examples

While _lsmod_ doesn’t have options, pairing it with other commands enhances its utility:

  * Combine with _modinfo_ : Get detailed information about a specific module, including its author, license, and description.
  * Debug with _dmesg_ : Correlate kernel log messages with loaded modules to diagnose boot-time issues.



```

    modinfo <module_name>
    sudo dmesg | grep <module_name>

```

## Conclusion

Commands like _lslogins_ and _lsmod_ can give you easy insights into user management and kernel behavior. Try them out today, and think about [combining][9] their output with other tools to appreciate their capabilities.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/system-insights-command-line-lslogins-lsmod/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/12/insights_via_cli_lslogins_and_lsmod-816x345.jpg
[2]: https://unsplash.com/@hharritt?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/red-and-blue-lights-from-tower-steel-wool-photography-Ype9sdOPdYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/system-insights-with-command-line-tools-lscpu-and-lsusb/
[5]: https://fedoramagazine.org/system-insights-command-line-dmidecode-lspci/
[6]: https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/
[7]: https://en.wikipedia.org/wiki/Monolithic_kernel#Loadable_modules
[8]: https://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate
[9]: https://en.wikipedia.org/wiki/Pipeline_(Unix)
