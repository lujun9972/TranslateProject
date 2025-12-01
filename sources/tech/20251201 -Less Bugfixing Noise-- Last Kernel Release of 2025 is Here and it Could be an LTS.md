[#]: subject: ""Less Bugfixing Noise": Last Kernel Release of 2025 is Here and it Could be an LTS"
[#]: via: "https://itsfoss.com/news/linux-kernel-6-18/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

"Less Bugfixing Noise": Last Kernel Release of 2025 is Here and it Could be an LTS
======

More than two months since the [last version][1], a new Linux release has been introduced, offering, as usual, better hardware support and many new additions covering a broad range of subsystems.

As with every development cycle, work from thousands of contributors has brought incremental improvements across CPUs, GPUs, storage, networking, and security.

Linus Torvalds [had this to say][2] about the release:

> So I'll have to admit that I'd have been happier with slightly less bugfixing noise in this last week of the release, but while there's a few more fixes than I would hope for, there was nothing that made me feel like this needs more time to cook. So 6.18 is tagged and pushed out.

📋

This coverage is based on the detailed reporting from [Phoronix][3].

### Linux Kernel 6.18: What's New?

If things go as planned, **Linux kernel 6.18 is expected to become 2025’s long-term support (LTS) release**. Users can expect [longer maintenance][4], steady security fixes, and a stable base that many distributions could rely on for years.

This release continues the kernel’s longstanding focus on supporting the latest hardware from vendors like Intel, AMD, Arm, NVIDIA, and others. Many architecture-specific tweaks, driver updates, and power-management refinements land in this cycle.

### Intel Upgrades

We kick things off with display support for Intel’s upcoming [Wildcat Lake][5] series of CPUs, which targets budget laptops and mini PCs and includes an integrated GPU for handling graphics and video tasks.

The release also adds the Panther Lake SoC Power Slider, allowing users of this platform to choose from one of three power profiles: " _low-power_ ", " _balanced_ ", and " _performance_ ".

The Intel [P-State][6] driver has been updated, allowing it to enable Hardware P-States (HWP) without Energy Performance Preference (EPP) when the new Dynamic Efficiency Control (DEC) hardware feature is enabled.

There's also support for [Intel TDX][7] with `kexec`, with the kernel now handling memory correctly for TDX workloads. Some early [Xeon Sapphire Rapids][8] processors with known hardware issues are not supported.

### New Device Tree Inclusions

Linux 6.18 adds [device trees][9] for [Arm C1][10], Apple M2 Pro, M2 Max, and M2 Ultra chips. The Apple-related work is tied to [Asahi Linux][11]'s efforts and brings better support for high-end Apple Silicon Macs into the mainline kernel.

Several Snapdragon X1 laptops now have mainline support: Dell Inspiron 14 Plus, Dell Latitude 7455, HP OmniBook X14, and Lenovo ThinkBook T16. Owners of these machines should see improved Linux compatibility.

The [SiFive HiFive Premier P550][12] RISC-V development board finally gets mainline support too.

### AMD Refinements

Similarly, this kernel release adds support for what's most likely [AMD EPYC Venice][13] processors with 16-channel memory support. The _AMD64 EDAC_ driver now recognizes these chips along with what appears to be the EPYC 8004 successor.

Virtualization improvements include Secure AVIC for [SEV-SNP][14] virtual machines, providing better security and performance.

And, to round out this section, the firmware bug affecting VMs with more than 255 vCPUs is fixed. CPU topology detection now works correctly for large virtual machines on AMD EPYC servers.

### Tyr Driver for ARM Mali GPUs

Linux kernel 6.18 gets the [Tyr][15] driver, bringing Rust-based GPU support for Arm Mali CSF GPUs. Jointly developed by Collabora, Google, and Arm, it is a Rust port of the [Panthor][16] driver.

The driver remains experimental. It can power up the GPU, query hardware metadata through MMIO, and provide metadata to userspace via the DRM device [ioctl][17]. Future releases are set to expand functionality toward becoming a full Panthor replacement.

![][18]

### Storage Improvements

[As expected][19], Bcachefs is out of the mainline kernel. After marking it " _externally maintained_ " in 6.17, Linus Torvalds has now removed the code entirely. Users need the [DKMS][20] module going forward.

Btrfs gets a nice speed boost for read-heavy workflows. The file system avoids locking contention when searching checksums, cutting sync times from minutes to seconds in some cases. Initial support for block sizes larger than kernel page size also arrives, though it is experimental with several limitations.

XFS enables online filesystem checking by default. The feature has been tested for a year without problems, so it is now standard. Some old deprecated mount options are also gone.

![][21]

#### Miscellaneous Changes

Rounding out this kernel release are the following additions:

  * [Initial support][22] for those fancy haptic touchpads found on newer laptops.
  * The kernel can now [detect and use MIPS vendor extensions][23] for RISC-V chips.
  * The Loongson Security Engine chip [is now supported][24], along with its associated driver stack.
  * UDP receive performance [has been improved][25] under heavy load, especially during high-rate or DDoS-like traffic.
  * Starting with this release, the [nouveau][26] driver now defaults to using [the GSP firmware][27] on supported NVIDIA GPUs.



### Installing Linux Kernel 6.18

Those on [rolling release][28] distributions ( _like Arch Linux_ ), Fedora, and any of its derivatives will be able to take advantage of this kernel very soon.

**For those on other distributions** , you have two options: wait for your distro's official release of Linux kernel 6.18, or [manually install the latest mainline kernel][29] yourself.

That said, **I don't recommend this for new or regular users** , as it carries a certain degree of risk. If you do choose this route, backing up your data beforehand is essential.

[Linux Kernel 6.18][30]

**Suggested Read 📖**

![][31]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/linux-kernel-6-18/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/news/linux-kernel-6-17/
[2]: https://lkml.org/lkml/2025/11/30/341
[3]: https://www.phoronix.com/review/linux-618-features
[4]: https://itsfoss.com/long-term-support-lts/
[5]: https://www.tomshardware.com/pc-components/cpus/intel-panther-lake-and-wildcat-lake-cpu-specs-break-cover-leak-suggests-up-to-16-cpu-cores-and-180-total-ai-tops
[6]: https://www.intel.com/content/www/us/en/docs/vtune-profiler/user-guide/2024-2/p-state.html
[7]: https://www.intel.com/content/www/us/en/developer/tools/trust-domain-extensions/overview.html
[8]: https://www.intel.com/content/www/us/en/support/articles/000094327/processors/intel-xeon-processors.html
[9]: https://en.wikipedia.org/wiki/Devicetree
[10]: https://www.arm.com/products/silicon-ip-cpu/#:~:text=Results%3A%2063%20Items-,C1%20CPUs,-C1%2DNano
[11]: https://asahilinux.org/
[12]: https://www.sifive.com/boards/hifive-premier-p550
[13]: https://wccftech.com/amd-next-gen-zen-6-cpus-over-70-percent-performance-efficiency-improvement/
[14]: https://www.amd.com/en/developer/sev.html#:~:text=AMD%20Secure%20Encrypted%20Virtualization%2DSecure%20Nested%20Paging%20(SEV%2DSNP)
[15]: https://itsfoss.com/news/tyr-gpu-driver/
[16]: https://www.collabora.com/news-and-blog/news-and-events/release-the-panthor.html
[17]: https://en.wikipedia.org/wiki/Ioctl
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-48.png
[19]: https://itsfoss.com/news/linux-kernel-bcachefs-drop/
[20]: https://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support
[21]: https://itsfoss.com/content/images/icon/android-chrome-512x512-49.png
[22]: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=54ba6d9b1393a0061600c0e49c8ebef65d60a8b2
[23]: https://lore.kernel.org/lkml/2c804359-3d43-0fba-7173-a87f9aec4bd2@kernel.org/
[24]: https://lore.kernel.org/lkml/20251001135934.GU8757@google.com/
[25]: https://lore.kernel.org/netdev/20250916160951.541279-1-edumazet@google.com/
[26]: https://nouveau.freedesktop.org/
[27]: https://lore.kernel.org/dri-devel/20250811213843.4294-2-mhenning@darkrefraction.com/
[28]: https://itsfoss.com/rolling-release/
[29]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[30]: https://www.kernel.org/
[31]: https://itsfoss.com/content/images/icon/android-chrome-512x512-47.png
