[#]: subject: "System insights with command line tools: lsof and lsblk"
[#]: via: "https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

System insights with command line tools: lsof and lsblk
======

![][1]

Photo by [Hunter Harritt][2] on [Unsplash][3] cropped

In our ongoing series on Linux system insights, we have a look into essential command-line utilities that provide information about the system’s hardware and status. Following our previous discussions on [_lscpu_ , _lsusb_][4], [_dmidecode_ and _lspci_][5], we now turn our attention to _lsof_ and _lsblk_. These tools are particularly useful for investigating open files, active network connections, and mounted block devices on your Fedora Linux system.

### Exploring open files with lsof

_lsof_ (list open files) is a powerful command-line tool. Since [almost everything in Linux is treated as a file][6], _lsof_ provides detailed insight into many parts of your system by listing what files are being used, which processes are accessing them, and even which network ports are open (see e.g. Wikipedia on [Network socket][7] for more information).

#### **Basic usage**

To start with, execute the basic _lsof_ command to get an overview of the system’s open files:

```

    $ sudo lsof

```

_sudo_ was used for extended privileges. This is needed to get information about files not opened by processes started by your user. The command outputs a lot of information which can be overwhelming. We are going to narrow down the output to specific information about some common use cases in the following examples.

#### Example 1: Finding open files by user or process

To identify which files a specific user or process has open, lsof can be very helpful.

To list all files opened by a specific user:

```

    $ sudo lsof -u <username>

```

This will return a list of open files owned by the given user. For example:

```

    $ sudo lsof -u johndoe

```

You’ll see details such as the process ID (PID), the file descriptor, the type of file, and the file’s path.

To filter by process, use the _-p_ flag:

```

    $ lsof -p <PID>

```

This is particularly useful for troubleshooting issues related to specific processes or when you need to check which files a service is holding open. Use _sudo_ if the process is not owned by your user.

Example output:

```

    $ lsof -p 873648
    COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
    bash    873648 user  cwd    DIR   0,39     8666      257 /home/user
    bash    873648 user  rtd    DIR   0,35      158      256 /
    bash    873648 user  txt    REG   0,35  1443376 12841259 /usr/bin/bash
    bash    873648 user  mem    REG   0,33          12841259 /usr/bin/bash (path dev=0,35)
    bash    873648 user  mem    REG   0,33          14055145 /usr/lib/locale/locale-archive (path dev=0,35)
    bash    873648 user  mem    REG   0,33          14055914 /usr/lib64/libc.so.6 (path dev=0,35)
    bash    873648 user  mem    REG   0,33          13309071 /usr/lib64/libtinfo.so.6.4 (path dev=0,35)
    bash    873648 user  mem    REG   0,33          14059926 /usr/lib64/gconv/gconv-modules.cache (path dev=0,35)
    bash    873648 user  mem    REG   0,33          14055911 /usr/lib64/ld-linux-x86-64.so.2 (path dev=0,35)
    bash    873648 user    0u   CHR  136,3      0t0        6 /dev/pts/3
    bash    873648 user    1u   CHR  136,3      0t0        6 /dev/pts/3
    bash    873648 user    2u   CHR  136,3      0t0        6 /dev/pts/3
    bash    873648 user  255u   CHR  136,3      0t0        6 /dev/pts/3

```

#### Example 2: identifying open network connections via sockets

With its ability to list network connections, _lsof_ also becomes a handy tool for diagnosing network-related issues as it is usually even available on hardened, minimal systems.

To display all open network connections (TCP/UDP [sockets][7]), run:

```

    $ sudo lsof -i

```

This will list active Internet connections along with the associated protocol, port, and process details.

You can filter for specific protocols (like TCP or UDP), include or exclude IPv4 and v6 and combine several values (the example section of _man lsof_ provides a lot of useful information, including negation):

```

    $ sudo lsof -i tcp
    $ sudo lsof -i udp
    $ sudo lsof -i 4tcp
    $ sudo lsof -i 6tcp
    $ sudo lsof -i 4tcp@example.com

```

For connections associated with a particular port:

```

    $ sudo lsof -i :<port_number>

```

For example, to list connections to port 22 (SSH):

```

    $ sudo lsof -i :22
    COMMAND    PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
    sshd    904379 root    3u  IPv4 5622530      0t0  TCP *:ssh (LISTEN)
    sshd    904379 root    4u  IPv6 5622532      0t0  TCP *:ssh (LISTEN)

```

This information can be critical for identifying unauthorized connections or simply monitoring network activity on a system for debugging.

### Investigating block devices with lsblk

Another useful tool is _lsblk_ , which displays information about all available [block devices][8] on your system. Block devices include hard drives, SSDs, and USB storage. This command provides a tree-like view, helping you understand the relationships between partitions, devices, and their mount points.

#### **Basic usage**

Running _lsblk_ without any options provides a clean hierarchical structure of the block devices:

```

    $ lsblk

```

This shows all block devices in a tree structure, including their size, type (disk, partition), and mount point (if applicable).

#### Examples

For a deeper look into the file systems on your block devices, use the _-f_ flag:

```

    $ lsblk -f

```

This will display not just the block devices, but also details about the file systems on each partition, including the type (e.g., ext4, vfat, swap), the UUID, and the current mount points.

If you want less information about the devices themselves (without showing partitions or mount points), the _-d_ option is useful:

```

    $ lsblk -d

```

There is also a _-J_ or _–json_ option. If used, the command outputs the information in JSON format. This provides a structured view that is particularly useful for scripting and automation.

Example outputs from my laptop (some long information like UUIDs stripped for readability):

```

    $ lsblk
    NAME                     MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
    sda                        8:0    1     0B  0 disk
    sdb                        8:16   1     0B  0 disk
    sdc                        8:32   1     0B  0 disk
    zram0                    252:0    0     8G  0 disk  [SWAP]
    nvme0n1                  259:0    0 931,5G  0 disk
    ├─nvme0n1p1              259:1    0   600M  0 part  /boot/efi
    ├─nvme0n1p2              259:2    0     1G  0 part  /boot
    └─nvme0n1p3              259:3    0 929,9G  0 part
      └─luks-84257c20[...]   253:0    0 929,9G  0 crypt /home


    $ lsblk -d
    NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
    sda       8:0    1     0B  0 disk
    sdb       8:16   1     0B  0 disk
    sdc       8:32   1     0B  0 disk
    zram0   252:0    0     8G  0 disk [SWAP]
    nvme0n1 259:0    0 931,5G  0 disk

    $ lsblk -f
    NAME                FSTYPE [...]LABEL    UUID           FSAVAIL FSUSE% MOUNTPOINTS
    sda
    sdb
    sdc
    zram0                                                                  [SWAP]
    nvme0n1
    ├─nvme0n1p1         vfat                 4C5B-4355      579,7M  3%     /boot/efi
    ├─nvme0n1p2         ext4                 30eff827[...]  605M    31%    /boot
    └─nvme0n1p3         crypto_LUKS          84257c20[...]
      └─luks-84257[...] btrfs       fe[...]  666f9d6f[...]  303,1G  67%    /home
                                                                           /

    $ lsblk -f -J
    {
       "blockdevices": [
       [...],{
             "name": "nvme0n1",
             "fstype": null,
             "fsver": null,
             "label": null,
             "uuid": null,
             "fsavail": null,
             "fsuse%": null,
             "mountpoints": [
                 null
             ],
             "children": [
                {
                   "name": "nvme0n1p1",
                   "fstype": "vfat",
                   "fsver": "FAT32",
                   "label": null,
                   "uuid": "4C5B-4355",
                   "fsavail": "579,7M",
                   "fsuse%": "3%",
                   "mountpoints": [
                       "/boot/efi"
                   ]
                },{
                   "name": "nvme0n1p2",
                   "fstype": "ext4",
                   "fsver": "1.0",
                   "label": null,
                   "uuid": "30eff827-[...]",
                   "fsavail": "605M",
                   "fsuse%": "31%",
                   "mountpoints": [
                       "/boot"
                   ]
                },{
                   "name": "nvme0n1p3",
                   "fstype": "crypto_LUKS",
                   "fsver": "2",
                   "label": null,
                   "uuid": "84257c20-[...]",
                   "fsavail": null,
                   "fsuse%": null,
                   "mountpoints": [
                       null
                   ],
                   "children": [
                      {
                         "name": "luks-[...]",
                         "fstype": "btrfs",
                         "fsver": null,
                         "label": "fedora_localhost-live",
                         "uuid": "666f9d6f-[...]",
                         "fsavail": "303,1G",
                         "fsuse%": "67%",
                         "mountpoints": [
                             "/home", "/"
                         ]
                      }
                   ]
                }
             ]
          }
       ]
    }

```

### Conclusion

The _lsof_ and _lsblk_ commands are providing insights into file usage, network activity, and block device structures. Whether you’re tracking down open file handles, diagnosing network connections, or reviewing storage devices; whether you’re troubleshooting, optimizing, or simply curious; these tools provide valuable data that can help you better understand and manage your Fedora Linux environment. See you next time when we will have a look at more useful listing and information command line tools and how to use them.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/insights_via_cli_lsof_lsblk-816x345.jpg
[2]: https://unsplash.com/@hharritt?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/red-and-blue-lights-from-tower-steel-wool-photography-Ype9sdOPdYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/system-insights-with-command-line-tools-lscpu-and-lsusb/
[5]: https://fedoramagazine.org/system-insights-command-line-dmidecode-lspci/
[6]: https://en.wikipedia.org/wiki/Everything_is_a_file
[7]: https://en.wikipedia.org/wiki/Network_socket
[8]: https://en.wikipedia.org/wiki/Device_file#Block_devices
