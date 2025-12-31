[#]: subject: "NTFSPlus Becomes "NTFS" as Driver Moves Closer to Kernel Integration"
[#]: via: "https://itsfoss.com/news/ntfsplus-becomes-ntfs-linux/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

NTFSPlus Becomes "NTFS" as Driver Moves Closer to Kernel Integration
======

[![Warp Terminal][1]][2]

If you have been [staying up-to-date][3] on the happenings of Linux, then you most likely know about [NTFSPlus][4], the fresh [NTFS][5] driver implementation for Linux, built by kernel developer [Namjae Jeon][6]. He is known for his work on the exFAT driver and ksmbd SMB server.

The driver has been steadily improving, with each patch iteration bringing new features and performance gains.

Now there's a new development worth talking about.

### Same Function, New Name

Yesterday, Namjae submitted [the v3 patch series][7] for NTFSPlus to the Linux kernel mailing list, renaming NTFSPlus to just " _ **NTFS**_ " in the kernel. This has been done in a bid to restructure everything, using the old read-only NTFS driver as a base and applying changes on top of it.

According to [Phoronix][8], **this makes code review easier** , and maintainers can focus on what's new instead of treating everything as fresh code.

Further explaining [how this new NTFS implementation would work on Linux][9], Namjae mentions that the remade NTFS supports _**write operations**_ plus essential features like _**iomap**_ , _**no buffer-head usage**_ , _**utilities**_ , and _**xfstests**_.

Beyond the rename, **this patchset brings many important improvements**. New generic helpers handle cluster-to-folio conversions and byte-to-sector operations. The driver now allows readahead for the $MFT file, and the 2TB filesystem limitation on 32-bit systems has been removed.

**Performance-wise** , this NTFS adaptation is 3-5% faster than [NTFS3][10] in single-threaded writes, but multi-threaded scenarios show 35-110% improvements. File listing is 12-14% quicker, and mount times are dramatically better: under a second for 4TB partitions versus 4+ seconds with NTFS3.

Do keep in mind that there are some features missing like full [journaling][11] support. Only journal replay exists right now, and even that doesn't work correctly according to Namjae. He plans to add proper journaling after the driver gets upstreamed.

The driver **is currently marked as experimental** , which makes sense given its development stage.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ntfsplus-becomes-ntfs-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/newsletter/
[4]: https://itsfoss.com/ntfsplus/
[5]: https://en.wikipedia.org/wiki/NTFS
[6]: https://github.com/namjaejeon
[7]: https://lore.kernel.org/lkml/CAEg-Je9nZbN8LkjX2n9MqobXBv91NYZk5v08u1ptufn=hSXnCg@mail.gmail.com/t.atom
[8]: https://www.phoronix.com/news/Linux-NTFS-v3-Patches
[9]: https://lore.kernel.org/lkml/20251229105932.11360-1-linkinjeon@kernel.org/
[10]: https://docs.kernel.org/filesystems/ntfs3.html
[11]: https://en.wikipedia.org/wiki/Journaling_file_system
