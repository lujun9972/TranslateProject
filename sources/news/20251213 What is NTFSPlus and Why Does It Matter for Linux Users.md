[#]: subject: "What is NTFSPlus and Why Does It Matter for Linux Users?"
[#]: via: "https://itsfoss.com/ntfsplus/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What is NTFSPlus and Why Does It Matter for Linux Users?
======

[![Warp Terminal][1]][2]

NTFSPlus (often stylized as NTFSPLUS) is the name of a new NTFS driver for the Linux kernel, with the goal of producing a performant, featureful, and accurate read/write driver implementation for this notoriously tricky filesystem.

Currently an out-of-tree driver (not yet included in the mainline kernel), it is the work of long-time Linux storage and filesystem developer Namjae Jeon. Jeon also developed and maintains the in-kernel exFAT filesystem driver and the accompanying [exfatprogs][3] user-space utilities.

This driver effort aims for compatibility with NTFS 3.x filesystems, fsck-style tooling (for example, a ntfsck-style checker), well documented code, and a better maintained driver that lives in the kernel. Currently, some distributions (such as Fedora) still rely on the [NTFS-3G][4] userspace driver, which uses [FUSE][5] (Filesystem In Userspace), since the current ntfs3 kernel driver has seen limited maintenance and continues to have unresolved issues.

### NTFS support on Linux has long been messy

![Pexels/Markus Spiske][6]

Historically, the Linux ecosystem has relied on at least three separate drivers for interfacing with Microsoft's proprietary filesystem. The original in-kernel ntfs driver was generally treated as read-only (with write support considered unreliable), and after becoming unmaintained, was completely removed in [Linux kernel 6.9][7]. Another, the ntfs3 driver by Paragon Software, was added to the kernel in [Linux 5.15][8] and has both read and write support, but is now effectively in maintenance-only mode.

The userspace [NTFS-3G][9] driver was for a long time the only widely used implementation of a read/write capable NTFS driver for Linux. However, it can be noticeably slow, and tends to be more CPU-hungry (especially when moving large files or a large number of files) and less performant than in-kernel implementations, especially on large, modern drives.

The challenges faced by each of these drivers have largely been due to the fact that developers have had to rely on the limited documentation Microsoft has made publicly available for the NTFS filesystem, plus a lot of reverse engineering. This unfortunate circumstance has made it difficult to create a Linux driver with thorough coverage for the filesystem used by default on many of the computers sold around the world and hosting much of the world's data.

### What NTFSPlus seeks to change

![Pexels/RealToughCandy.com][10]

In many ways, NTFSPlus is a do-over: a fresh implementNTFSPlus is a fresh implementation of the classic in-kernel ntfs driver. Can it end the current NTFS woes for Linux users?ation that applies the lessons learned from at least two decades of NTFS work, while taking advantage of modern kernel infrastructure. Rather than attempting to modify the ntfs3 driver code (Paragon Software’s implementation), NTFSPlus builds on the foundation of the classic in-kernel ntfs driver. It refactors and extends this existing code to support modern NTFS 3.x volumes and newer kernel APIs such as iomap and folios.

In his [proposal on the Linux kernel mailing list][11], Jeon describes NTFSPlus as a “remade ntfs” implementation based on the classic driver, noting that the old code is cleaner and better commented, which makes understanding NTFS behaviour easier. That readability is a key reason for using it as a base and then layering on features like iomap, folio support, and proper utilities, rather than trying to further evolve the existing ntfs3 code. The intention this time is not only to improve performance, but also to create better documented code that is easier to navigate, test, and maintain over time.

Development has already moved on to a v2 series of patches, tracked in an `ntfs-next` [Git branch][12] that acts as a staging area while the driver moves toward potential inclusion in the mainline kernel. Recent updates add NTFS3-compatible mount options, improved ioctl support (including FITRIM for SSD discard and filesystem label handling), `$MFT` file extension support, new documentation, and currently mark the driver as experimental, as reported by [Phoronix][13].

### NTFSPlus comes bearing gifts

Jeon’s proposal to create proper tooling around the driver could be a much-needed game-changer for the Linux community, especially now as many users flock to Linux from Windows. Repairing NTFS drives on Linux is possible today, but the safest advice is often still to leave the drive alone and let Windows’ own tools do the necessary work.

Having fsck-style utilities for checking and repairing NTFS volumes from user space would be a critical step for Linux adoption, as many users will not want to replace their existing filesystems if this can be avoided. For Linux distributions, this could eventually lead to a clean, in-kernel NTFS stack with first-class support for features like idmapped mounts, standard mount options, and integration with existing filesystem tools.

### An open implementation

One of the most important aspects of this development is that the NTFSPlus driver is being developed fully in the open. Jeon posts updates directly on familiar kernel mailing lists and maintains an "ntfs-next" branch that interested users and distributions can test early. He is a well-known and trusted maintainer with a solid track record of producing reliable code for another of Microsoft's proprietary filesystems, as well as for the kernel’s [ksmbd SMB server][14].

This open development process means other developers have an opportunity to test and spot issues early in the project's lifecycle, which should lead to a stronger “finished product” if and when it lands in the mainline kernel. If this work does make it into a future kernel release and gains wide adoption, it could finally remove the need to choose between a slower FUSE driver or an effectively stagnant in-kernel implementation.

### Could this mean Linux on NTFS some day?

Perhaps, but not necessarily. It is already possible to install Linux from within Windows using disk images that are writable and do not require the creation of a new filesystem or partition. This is similar to what once powered Ubuntu's [Wubi installer][15]. However, such implementations were notably slower than running off a native Linux filesystem, and were more prone to corruption issues and other challenges.

A fully in-kernel implementation of an NTFS driver could, in theory, make “Linux on NTFS” a more realistic option, so long as the driver is considered stable enough for distribution maintainers to support it. That said, it may still require compromises where NTFS does not have support for certain Linux-standard features and permission models, and native Linux filesystems are likely to remain the better choice for most use cases.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ntfsplus/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/namjaejeon/exfatprogs
[4]: https://wiki.archlinux.org/title/NTFS-3G
[5]: https://www.kernel.org/doc/html/next/filesystems/fuse.html
[6]: https://itsfoss.com/content/images/2025/12/pexels-markusspiske-113850-1.jpg
[7]: https://www.phoronix.com/news/Linux-6.9-Dropping-Old-NTFS
[8]: https://www.paragon-software.com/paragon-software-announces-the-inclusion-of-its-ntfs3-driver-into-linux-kernel-5-15/
[9]: https://github.com/tuxera/ntfs-3g
[10]: https://itsfoss.com/content/images/2025/12/pexels-realtoughcandy-11035358-1.jpg
[11]: https://lwn.net/Articles/1042684/
[12]: https://git.kernel.org/pub/scm/linux/kernel/git/linkinjeon/ntfs.git/log/?h=ntfs-next
[13]: https://www.phoronix.com/news/NTFSPLUS-v2-Features
[14]: https://docs.kernel.org/filesystems/smb/ksmbd.html
[15]: https://help.ubuntu.com/community/Wubi
