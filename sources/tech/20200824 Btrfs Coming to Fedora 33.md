[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Btrfs Coming to Fedora 33)
[#]: via: (https://fedoramagazine.org/btrfs-coming-to-fedora-33/)
[#]: author: (Chris Murphy https://fedoramagazine.org/author/chrismurphy/)

Btrfs Coming to Fedora 33
======

![][1]

by Chris Murphy and Langdon White

* * *

User data is the most important thing on a computer. Whether it’s source code for the next big release, family pictures, a music library, or anything else, you want it to be safe. Changing the default file system is not a change to make casually. The Fedora Project is changing the default file system for desktop variants (Fedora Workstation, Fedora KDE, etc), for the first time since Fedora 11. Btrfs will replace ext4 as the default filesystem in Fedora 33.

### What does this mean for me?

Btrfs is a stable and mature file system with modern features: data integrity, optimizations for SSDs, compression, cheap writable snapshots, multiple device support, and more.

The switch to Btrfs will use a single-partition disk layout, and Btrfs’ built-in volume management. The previous default layout placed constraints on disk usage that can be a difficult adjustment for novice users. Btrfs solves this problem by avoiding it.

As a techie, you may have heard of bit rot, and memory bit flips. Data can be corrupted by a multitude of physical factors, even cosmic rays from the sun! Before an SSD fails outright, often it will return either zeros or garbage, instead of your data. Btrfs safeguards your data with checksums, and performs verification on every read. Corrupt data is never given to your programs, and it won’t replicate into your backups to be discovered another day (or year).

Btrfs uses a “copy-on-write” model: your data and the file system itself are never overwritten. This enhances crash-safeness. When copying a file, Btrfs does not write new data until you actually change the old data, saving space.

In fact, users will save more space when using Btrfs’ transparent compression. Compressing data reduces total writes, saves space, and extends flash drive life. In many cases, it can also improve performance. Compression can be enabled on an entire file system, or per subvolume, directory, and even per file. You will be able to opt-in to using compression in Fedora 33. And it’s one of the features we’re looking forward to taking advantage of by default in future Fedora releases.

### Trusted

Facebook uses Btrfs on millions of machines in production. They compare its stability to ext4 and XFS (another file system available in Fedora). In fact, they use Btrfs to “improve” the quality of the consumer storage hardware that they use in production. Btrfs detects problems before the hardware fails.

(open)SUSE have been using Btrfs for many years now, including SUSE Linux Enterprise Server (SLES). You can’t imagine a company that provides support to customers shipping software that they don’t completely trust.

### What’s next?

The Change is code complete, and has been testable in Rawhide as the default file system since early July. Btrfs has been explicitly supported in Fedora since 2012. This is expected to be a transparent change for most users, however it is still significant. Fedora will ensure we deliver the dependable and reliable experience Fedora users have come to expect.

Special thanks to: Ben Cotton, Michael Catanzaro, and the Fedora Workstation Working Group for contributing to this article.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/btrfs-coming-to-fedora-33/

作者：[Chris Murphy][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/chrismurphy/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/08/butterfs-816x346.png
