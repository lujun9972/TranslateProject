[#]: subject: "Linux Kernel 6.19 Arrives! You Get Intel, AMD Improvements, and ASUS Armoury Support"
[#]: via: "https://itsfoss.com/news/kernel-6-19-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel 6.19 Arrives! You Get Intel, AMD Improvements, and ASUS Armoury Support
======

[![Warp Terminal][1]][2]

Like how a [canon event][3] must happen, we now have a new Linux release that brings better hardware support, improved peripheral handling, and some news on how development would continue in case the main [torvalds/linux.git][4] repository was to go away.

Needless to say, even if some key people weren't around anymore, or were preoccupied with more urgent matters, the development of Linux wouldn't come to a standstill.

Anyhow, no new Linux release goes without Linus Torvalds [having something to add][5]:

> No big surprises anywhere last week, so 6.19 is out as expected - just as the US prepares to come to a complete standstill later today watching the latest batch of televised commercials.
>
> The betting man would expect them all to be AI-generated, but maybe some enterprising company decides to buck the trend? Doubtful, but there's always a slight chance.

This coverage is based on the detailed reporting from [Phoronix][6].

### Linux Kernel 6.19: What's New?

This release ushers in [a formal continuity document][7] for the kernel project. Basically, it's a plan for what happens if Linus Torvalds' Git repository becomes unavailable for whatever reason.

Linux kernel engineer [Dan Williams][8] put this together after discussions at the [2025 Maintainer Summit][9] and says the idea is quite straightforward. If the person ( _usually Linus)_ or people handling the mainline repository can't continue, the project needs a way to move forward quickly.

Unlike last time, **Linux 6.19 is not an LTS release**. [Linux kernel 6.18][10] remains the 2025 [long-term support release][11] with maintenance upgrades until December 2027.

### Intel Changes

Intel's [Trust Domain Extensions][12] code received a major rework for KVM. These changes address issues that were causing the confidential computing feature to behave unpredictably in [virtual machines][13].

Then there's the **audio support for Intel's upcoming Nova Lake processors**. The kernel's sound drivers can now handle [Nova Lake][14] and Nova Lake S processors without needing much additional config work.

Linear Address Space Separation finally lands with this release. [Intel LASS][15] is meant to tackle specific classes of [side-channel attacks][16] that exploit processor vulnerabilities.

Similarly, Intel Xeon 6 processors get better [NUMA][17] handling. Granite Rapids and Clearwater Forest chips now have proper distance calculations when running in [Sub-NUMA Clustering 3][18] configuration.

### AMD Refinements

Virtual machines powered by AMD chips can now handle up to 4096 virtual CPUs with extended x2AVIC support. The previous limit was 512 vCPUs, so this is **a substantial jump for enterprise-grade virtualization workloads**.

[AES-GCM encryption][19] gets major speed improvements on AMD Zen 3 processors. The optimizations deliver [up to 74% faster performance][20] in some cases, with AVX-512 systems also benefiting from the work.

Then there's the **Smart Data Cache Injection support** (SDCI), where AMD EPYC 9005 Turin and newer chips **can now inject data from I/O devices directly into L3 cache** , skipping system memory entirely.

And, for users of older Radeon graphics cards ( _Radeon HD 7000 to RX 300 series_ ), the [AMDGPU driver][21] is the default for you. This should result in better performance and Vulkan support through RADV, replacing the legacy Radeon driver.

### Storage Buffs

EXT4 gets optimized online defragmentation by using folios instead of buffer heads. The file system now supports block sizes larger than the kernel page size, bringing some welcome performance improvements.

NTFS3 can now handle timestamps from before the year 1970. The driver **switched to signed 64-bit timestamps** after the issue showed up during file system testing, fixing pre-epoch date handling ([ _an example_][22]).

F2FS brings performance optimizations across multiple areas, including sysfs, debugfs, and garbage collection. The release also fixes many bugs caught by xfstests and issues related to 16KB page support.

### Better Handheld, Laptop, and Peripheral Support

ASUS gaming handheld users will be glad to know ( _or not?_ ) that **the Armoury driver is now supported** , bringing proper hardware control for ROG Ally gaming handhelds and other ASUS [gaming hardware][23] under Linux.

I said " _not"_ earlier because the Windows implementation, [Armoury Crate][24], has been a nightmare for many. It is known to trigger antivirus false positives, suffers from security vulnerabilities that can grant system-level access, and refuses to go away even after an uninstall ( _basically bloatware_ ).

Moving on, there's now **rapid charge support for Lenovo IdeaPad laptops** , with the driver handling faster USB-C charging.

Several [Logitech][25] devices get improved support too. The G Pro X Superlight 2 wireless gaming mouse works properly now, along with a new Lightspeed receiver version being included. The G13 gaming keypad also gains mainline support.

#### Miscellaneous Changes

We end this coverage with an overview of some other notable changes:

  * Removal of the " _gen*cide_ " [function][26].
  * Inclusion of the [Arm MPAM driver][27].
  * Early GPU support for the Snapdragon X2 Elite.
  * Parallel CPU hotplugging support for RISC-V chips.
  * Initial enablement work for 32-bit Loongson CPUs ( _LoongArch3_ 2).
  * The [Tenstorrent Blackhole][28] and [Black Sesame][29] series of SoCs are now supported.



### Installing Linux Kernel 6.19

For people running [rolling distros][30] like Arch Linux or distros like Fedora and [its derivatives][31], Linux 6.19 will be available very soon. Those on other distros like Debian, Ubuntu, Linux Mint, MX Linux, etc., could wait for it, but I wouldn't hold my breath on it.

There is, however, **a way to get it early** ** ( _linked below_ ) on such computers, but that involves some manual labor and a knack for risk-taking ( _if you nuke your system, we are not to blame_ ☠️).

[Linux Kernel 6.19][32]

**Suggested Read 📖:** [_Go Down the Rabbit Hole of Installing Mainline Linux Kernel_][33]

![][34]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/kernel-6-19-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.merriam-webster.com/slang/canon-event
[4]: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/
[5]: https://lore.kernel.org/lkml/CAHk-=wh0Fj7yE7iuW8awFCFt53s9T186qNbZX673E+oNCeQSFg@mail.gmail.com/
[6]: https://www.phoronix.com/review/linux-619-features-changes
[7]: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=102606402f4f5943266160e263c450fdfe4dd981
[8]: https://www.linkedin.com/in/djbw/
[9]: https://events.linuxfoundation.org/kubecon-cloudnativecon-north-america/features-add-ons/maintainer-summit/
[10]: https://itsfoss.com/news/linux-kernel-6-18/
[11]: https://itsfoss.com/long-term-support-lts/
[12]: https://www.intel.com/content/www/us/en/developer/tools/trust-domain-extensions/overview.html
[13]: https://itsfoss.com/why-linux-virtual-machine/
[14]: https://www.techspot.com/news/111047-intel-confirms-nova-lake-core-ultra-400-cpus.html
[15]: https://edc.intel.com/content/www/us/en/design/products-and-solutions/processors-and-chipsets/core-ultra-200h-and-200u-series-processors-datasheet-volume-1-of-2/linear-address-space-separation-lass/
[16]: https://en.wikipedia.org/wiki/Side-channel_attack
[17]: https://en.wikipedia.org/wiki/Non-uniform_memory_access
[18]: https://www.intel.com/content/www/us/en/developer/articles/technical/fourth-generation-xeon-scalable-family-overview.html#:~:text=from%20the%20nearest.-,Sub%2DNUMA%20Clustering,-Figure%202%20%E2%80%93%20Block
[19]: https://medium.com/@pravallikayakkala123/understanding-aes-encryption-and-aes-gcm-mode-an-in-depth-exploration-using-java-e03be85a3faa#:~:text=encryption%20and%20decryption.-,AES/GCM%20Mode,-AES%20can%20be
[20]: https://www.phoronix.com/news/Linux-6.19-AES-GCM-AVX2-Faster
[21]: https://docs.kernel.org/gpu/amdgpu/index.html
[22]: https://stackoverflow.com/questions/31708622/how-to-represent-dates-before-epoch-as-a-unix-timestamp
[23]: https://rog.asus.com/
[24]: https://rog.asus.com/content/armoury-crate/
[25]: https://www.logitech.com/
[26]: https://www.phoronix.com/news/Linux-6.19-Drops-Genocide
[27]: https://www.phoronix.com/news/Arm-MPAM-LInux-6.19
[28]: https://tenstorrent.com/en/hardware/blackhole
[29]: https://www.blacksesame.com/en
[30]: https://itsfoss.com/rolling-release/
[31]: https://itsfoss.com/best-fedora-linux-distributions/
[32]: https://www.kernel.org/
[33]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[34]: https://itsfoss.com/content/images/icon/android-chrome-512x512-237.png
