[#]: subject: "Snapdragon X Elite, The Apple Silicon Killer Readies Support for Linux"
[#]: via: "https://news.itsfoss.com/snapdragon-x-elite-linux/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Snapdragon X Elite, The Apple Silicon Killer Readies Support for Linux
======
Worried about why Apple ARM chips don't play nice with Linux? Qualcomm
has you covered.
Back in the day, the CPU market was dominated by the likes of Intel and AMD. However, the advent of smartphones gave rise to ARM-based chips from the likes of [Qualcomm][1], [MediaTek][2], and even [Apple][3], who is the most recent company to break into this space.

But competition always prevails. Last year, Qualcomm [introduced][4] the Snapdragon X Elite platform, which was geared towards providing fast performance in a compact form factor, with a focus on AI.

The first PCs powered by that platform are expected sometime in mid-2024, and as it turns out, **they are not treating Linux as a second-class citizen** with this launch.

### Snapdragon X Elite: Getting Ready for Linux

Based on Qualcomm's [Oryon][5], the Snapdragon X Elite features **12 cores** , a clock speed of **up to 3.8 GHz** ( _boosts up to 4.3 GHz_ ), an Adreno GPU capable of up to **4.6 TFLOPS** for conventional GPU tasks, and an NPU capable of **45 TOPS** for AI-specific tasks.

Qualcomm teamed up with [Lenovo][6], [ARM][7], and [Linaro][8] on the [AArch64 laptops][9] project to develop Linux support for several generations of their SoCs, both current and past.

Additionally, they mentioned that:

> It’s been our priority not only to support Linux on our premium-tier SoCs, but to support it pronto. In fact, within one or two days of publicly announcing each generation of Snapdragon 8, we’ve posted the initial patchset for Linux kernel support.

They also went a step further, and started posting patch sets to the Linux kernel right after they announced the Snapdragon X Elite series; You don't see such commitment too often 😀

So far, they have merged some important features with Linux kernels [6.8][10] and [6.9][11], with some highlights being:

  * **SSD-NVMe over PCIe**
  * **Phy (PCIe/eDP/USB)**
  * **Sound machine driver**
  * **PMC8380 PMIC**
  * **Pinctrl (TLMM)**



Currently, Qualcomm is working with the community to address an issue during boot with devicetrees on their UEFI-based BIOS. They also revealed that they use [GRUB][12] to boot into Debian, and to dual-boot it with Windows.

In the next six months, they want to complete work on adding **support for end-to-end hardware video decoding** on Firefox and Chrome, and carry out various **GPU and CPU performance optimizations.**

In addition, they aim to provide **access to easy installers** for Ubuntu as well as Debian.

For the upcoming Linux kernel 6.10 and 6.11 releases, Qualcomm intends to implement support for things like GPU, Camera, Video, Battery, On-board display (eDP), CPUFreq, and more.

**Overall,** I like the direction Qualcomm is headed, seeing that some chip manufacturers _(e.g., Apple_ ), for obvious reasons, forget that Linux is a significant platform that deserves the latest and greatest.

**But, wait. There's more! 😎**

Qualcomm has also [released][13] **an experimental raw disk image for Debian** that they have been using internally to test things out on their compute reference devices ( _not sure which ones those are_ ).

[Experimental Raw Disk Image (Debian)][13]

If you are interested in contributing or want to see the progress, then you can search for “ _X1E80100_ ” on the [Linux Kernel Mailing List archive][14] (LKML).

If you would like to learn more about how Qualcomm has been pulling this off, you can refer to [the video][15] linked below, or you could go through the [announcement blog][16].

_💬 What do you think of super powerful ARM laptops running Linux? Sounds good? And, that sounds like a reality! Share your thoughts in the comments down below._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/snapdragon-x-elite-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.qualcomm.com/
[2]: https://www.mediatek.com/
[3]: https://www.apple.com/
[4]: https://www.qualcomm.com/news/releases/2023/10/qualcomm-unleashes-snapdragon-x-elite--the-ai-super-charged-plat
[5]: https://www.qualcomm.com/news/onq/2022/11/qualcomm-oryon-custom-cpu-at-center-of-next-gen-premium-experiences-on-snapdragon-platforms
[6]: https://www.lenovo.com/
[7]: https://www.arm.com/
[8]: https://www.linaro.org/
[9]: https://github.com/aarch64-laptops
[10]: https://news.itsfoss.com/linux-kernel-6-8-release/
[11]: https://news.itsfoss.com/linux-kernel-6-9-release/
[12]: https://www.gnu.org/software/grub/
[13]: https://git.codelinaro.org/linaro/qcomlt/demos/debian-12-installer-image
[14]: https://lkml.org/
[15]: https://www.youtube.com/watch?v=_TEBKEhhcqM
[16]: https://www.qualcomm.com/developer/blog/2024/05/upstreaming-linux-kernel-support-for-the-snapdragon-x-elite
