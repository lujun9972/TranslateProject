[#]: subject: "RISC-V and Fedora: All Aboard!"
[#]: via: "https://fedoramagazine.org/risc-v-and-fedora-all-aboard/"
[#]: author: "Neil Hanlon https://fedoramagazine.org/author/neil/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RISC-V and Fedora: All Aboard!
======

![][1]

Photo by [Tommy L][2] on [Unsplash][3] (cropped)

2025 is the year of Linux on RISC-V.

No, seriously. Sit back down–you can’t get off until the next stop anyways.

Fedora is jumping on the RISC-V train as a fifth architecture. While there’s still some work to be done, we’ve hit some major milestones towards a more open computing future. By embracing RISC-V, Fedora’s doubling down on its commitments to Freedom, Friends, Features, and First. Whether you’re a developer or an enthusiast, there’s only one thing this means: It’s time to start building.

### Embracing Open-Source Hardware with RISC-V

RISC-V (pronounced “risk-five”) is an open-standard Instruction Set Architecture (ISA) based on Reduced Instruction Set Computing (RISC) principles. Unlike proprietary architectures, RISC-V is free and open. This allows anyone to design, manufacture, and sell RISC-V chips and software without licensing fees or restrictions. This openness removes barriers to innovation, fostering a collaborative, community-driven approach to hardware development similar to open-source software. Developers are empowered to customize processors for specific needs, sharing enhancements and optimizations that accelerate technological advancements.

RISC-V was developed at the University of California, Berkeley, in 2010. It was created to provide a simple, extensible ISA for computer architecture research and education. Recognizing its broader potential, the creators made it freely available to all. Since then, RISC-V has gained significant traction and evolved into a mature, competitive architecture governed by RISC-V International. With contributions from industry giants, academic institutions, and a passionate community, RISC-V represents a significant shift in the hardware industry toward an open and inclusive technological landscape.

### Fedora’s Journey with RISC-V

Fedora’s interest in RISC-V isn’t new—the Fedora Project has been experimenting with the architecture since at least 2015. Over the better part of a decade, our hands-on development and community collaboration have paved the way for exciting milestones. While RISC-V is not yet a “primary” architecture within Fedora (see [Fedora Architectures][4] for details), we’re beginning to invest in it alongside Intel/AMD (x86_64), ARM (aarch64), IBM Power (ppc64le), and IBM Z (s390x). In time, it will be accessible to all Fedora packagers to submit builds to. Today, we’re excited to announce major milestones:

  * I **ntegrated Infrastructure:** We’re excited to share that a dedicated [RISC-V Koji][5] instance is now live in our Fedora data center. This new hardware is fully integrated with Fedora’s authentication and core services. In time it will be accessible to all Fedora packagers for submitting builds.


  * **Ready-to-Boot Images:** Fedora 41-based images are available, allowing you to quickly spin up a RISC-V board—or even a virtual machine—and experience Fedora on RISC-V firsthand.



### Why This Matters for Developers and Users

Over the past year, there has been a surge of new RISC-V hardware hitting the market. The options for operating systems have been typically limited to Debian or a derivative thereof–or occasionally an older Fedora version/variant. In the RISC-V Special Interest Group (SIG), the focus has been on bringing together all the efforts to enable this emerging architecture for the wider Fedora community: keeping packages up to date with branched versions, building images for supported hardware, and integrating required package modifications upstream.

For Fedora users, this means there are now up-to-date Fedora images for a handful of popular RISC-V boards that SIG members have been running for many months to perform native builds. So, if you have any boards collecting dust, now is a great time to check out which hardware we’re working on and take Fedora on RISC-V for a spin.

For our Developers, there’s no need to worry. If you want to get involved, more information will be available in the coming months as the Koji infrastructure is deployed and configured. At the moment, a dist-git “overlay” is used for a number of packages in order to enable this new architecture. This is necessary as there are often upstream changes required which affect _only_ the new architecture. While the upstreaming work is in progress, the overlay setup allows the SIG to collaborate more effectively on the changes.

Those wishing to follow along or contribute to the SIG are encouraged to join us on [Matrix][6], and to review the [RISC-V Tracker][7] that is available to track the upstreaming progress, as well as the [SIG page.][8]

### Getting Started with Fedora on RISC-V

If you’re ready to try Fedora on RISC-V, here’s how to get started:

#### Supported Hardware

For a hassle-free Fedora experience on RISC-V, we currently offer ready-to-boot images for the following platforms:

  * [StarFive VisionFive 2 (VF2)][9]: Our flagship board running a mainline kernel. It offers a fully open experience with the generic Fedora image.
  * [QEMU][10]: Ideal for experimentation, QEMU lets you run Fedora on RISC-V in a virtual environment with the same mainline kernel support. Check out the [Fedora RISC-V QEMU guide][10] for step-by-step instructions on setting up a virtual environment.
  * [SiFive HiFive Premier P550][11]: This board boots with a provided image using a vendor kernel. While it works out of the box, please note that it relies on vendor firmware, which may limit certain features.



###### Additional Hardware

  * [Banana Pi BPI-F3][12] and [Milk-V Jupiter M1/K1][13]: Fedora on this board is possible for those who aren’t afraid of a bit of work. Although not supported out of the box, it remains an interesting option for those willing to experiment and contribute improvements.You can check out the [SpacemiT Fedora Install Guide][14] if that sounds like you.



### Installation Instructions

To get started with Fedora on RISC-V, visit the [installation guide][15] for detailed steps on flashing an image to your board or setting up a virtual machine.

### Get Involved

Want to contribute to Fedora’s RISC-V efforts? Join the conversation on [Matrix][16], track the progress in the RISC-V Tracker, and check out the SIG page for more details on how to get involved.

The future of open-source hardware is here, and Fedora is at the forefront. Whether you’re a developer looking to port software or an enthusiast eager to explore the ecosystem, there’s never been a better time to jump aboard. Let’s build the future together.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/risc-v-and-fedora-all-aboard/

作者：[Neil Hanlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/neil/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/02/RISC-V_and_Fedora-816x345.jpg
[2]: https://unsplash.com/@0x746f6d6d796a746c?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-close-up-of-a-computer-chip-l7fpTjm3ZOQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoraproject.org/wiki/Architectures
[5]: https://riscv-koji.fedoraproject.org/koji/
[6]: https://matrix.to/#/#riscv:fedoraproject.org
[7]: https://abologna.gitlab.io/fedora-riscv-tracker/
[8]: https://fedoraproject.org/wiki/SIGs/RISC-V
[9]: https://fedoraproject.org/wiki/Architectures/RISC-V/StarFive/VisionFive2
[10]: https://fedoraproject.org/wiki/Architectures/RISC-V/QEMU
[11]: https://fedoraproject.org/wiki/Architectures/RISC-V/SiFive/HiFivePremierP550
[12]: https://docs.banana-pi.org/en/BPI-F3/BananaPi_BPI-F3
[13]: https://milkv.io/jupiter
[14]: https://fedoraproject.org/wiki/Architectures/RISC-V/SpacemiT-Fedora-Install
[15]: https://fedoraproject.org/wiki/Architectures/RISC-V/Installing
[16]: https://matrix.to/#/#fedora-riscv:matrix.org
