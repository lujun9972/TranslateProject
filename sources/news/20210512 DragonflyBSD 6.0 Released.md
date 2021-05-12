[#]: subject: (DragonflyBSD 6.0 Released)
[#]: via: (https://news.itsfoss.com/dragonflybsd-version-6/)
[#]: author: (John Paul Wohlscheid https://news.itsfoss.com/author/john/)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

DragonflyBSD 6.0 Released
======

On May 10th, the DragonflyBSD team released [version 6.0][1]. Let’s take a look at what changes make up this release.

For those of you who are not aware of what [DragonflyBSD][2] is, let me enlighten you. The DragonflyBSD project began in 2004. It was created by Matthew Dillon after a falling out with the FreeBSD developers. Dillon disagreed with the [development path][3] they chose for FreeBSD 5, so he forked FreeBSD 4.

One of the biggest changes made to DragonflyBSD was an overhaul of the kernel. This included “inter-process communication via message passing.” Many of the changes were inspired by [Dillon’s work on Amiga][4]. “The Amiga kernel was designed around small but powerful APIs and messaging. Having a small, well defined API for a subsystem results in fewer bugs, easier to find bugs, and code sustainability.”

Another feature that sets DragonflyBSD apart is the fact that it has its own file system. HAMMER is designed to be a [Unix File System][5] (or UFS) replacement. UFS is a descendant of the original Unix file systems and is used in many BSDs. [HAMMER][6] has similar features to ZFS, including “instant crash recovery, multi-volume file systems, integrity checking, fine grained history/undo, networked mirroring, and historical snapshots”. HAMMER2 is the current version.

### Changes in DragonflyBSD 6.0

Here are a list of the changes that have been made for the 6.0 release:

  * Significant work was done on dsynth, which is used for building packages
  * HAMMER2 received multiple cleanups and fixes. It also received initial multi-volume support.
  * non-GPL ext2 filesystem support added.
  * Meltdown hardware is detected during boot on Intel.
  * amdsmn imported from FreeBSD
  * Support added for newer Intel I219 Ethernet controllers.
  * Multiple updates and stability fixes to the i915 driver.
  * DRM system now matches Linux 4.10.17.
  * GCC 8 now set as default.
  * A full set of new binary packages has been built for 6.0
  * Improved EFI framebuffer support
  * Significant performance enhancements for TMPFS



You can see the complete list of changes on the [announcement page][7]. You can download the latest version of DragonflyBSD [here][8].

[Download DragonflyBSD 6.0][8]

#### Big Tech Websites Get Millions in Revenue, It's FOSS Got You!

If you like what we do here at It's FOSS, please consider making a donation to support our independent publication. Your support will help us keep publishing content focusing on desktop Linux and open source software.

I'm not interested

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/dragonflybsd-version-6/

作者：[John Paul Wohlscheid][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/john/
[b]: https://github.com/lujun9972
[1]: https://www.dragonflybsd.org/release60
[2]: https://www.dragonflybsd.org/
[3]: https://web.archive.org/web/20160309021122/http://www.onlamp.com/pub/a/bsd/2004/07/08/dragonfly_bsd_interview.html
[4]: https://www.informit.com/articles/article.aspx?p=766375
[5]: https://en.wikipedia.org/wiki/Unix_File_System
[6]: https://www.dragonflybsd.org/hammer/
[7]: https://www.dragonflybsd.org/release60/
[8]: https://www.dragonflybsd.org/download/
