[#]: subject: "Looks Like Arch Linux Is Going To Officially Support ARM/RISC-V"
[#]: via: "https://news.itsfoss.com/archlinux-arm-riscv/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Looks Like Arch Linux Is Going To Officially Support ARM/RISC-V
======
Arch Linux is making better efforts to support newer architectures.
[Arch Linux is a versatile distribution][1] for experienced users. However, officially, it only supports x86-64 architecture.

Other distributions have been making progress to support various newer architectures, including ARM and RISC-V. Whether it is Ubuntu or an Arch-based distro like Manjaro, you can find official support for ARM/RISC-V.

Unfortunately, that has been missing with Arch Linux, even if there are unofficial ports making good progress.

To change that, Arch Linux has finally decided to set up a test integration for " **Arch Linux Ports** ".

### What Does This Mean?

Simply put, unofficial ports for various architectures will get infrastructure and better community-based support until they are integrated in the main Arch Linux repositories.

Arch Linux wants to work on the unofficial ports for other architectures through a joint effort.

![][2]

To achieve this, a new proposed system was [merged][3] as the [Arch Linux Ports RFC][4], which should help Arch Linux help adapt to newer architectures without fully committing to it in its initial phase.

📋

RFC (Request For Comment) is a way where a proposal/discussion/feature idea is shared by Arch Linux contributors.

The merged RFC mentions:

> This RFC outlines a data driven process through which we can estimate how much extra maintenance effort is required, how mature the architecture is, and how much interest there is for it in the community.

So, as the work/tests progresses for an architecture, it would be easy to evaluate if an architecture can be maintained as an official port or not.

Yes, there is no guarantee that the unofficial ports for ARM/RISC-V will be promoted as official ones, nor there is an estimated time for it. But the system looks promising.

In the past, some RFCs tried to integrate newer architectures directly, but it was not a streamline process (or something that ended up working).

So, with this RFC, Arch Linux has decided to put a system in place that will help them adapt to newer architectures.

The RFC explains the process when a new port starts:

> New ports are added by proposing them in an RFC. At least two package maintainers have to lead a port to ensure it will be developed longer term.
>
> Once an introduction RFC is accepted, the work on a port may start. Initial work includes additions of port specific integration (e.g. custom pacman.conf, makepkg.conf, etc.) to the official build tooling.
>
> Port maintainers are expected to work together with relevant Arch Linux teams to enable the setup of any required infrastructure. Required changes to existing tooling should be proposed and if possible also implemented by port maintainers, to ease the workload on the existing teams.

Furthermore, the port maintainers have to be included as package maintainers in the Arch Linux team to be able to access dedicated build infrastructure (and will be expected to maintain/improve it).

### Arch Linux + Port Maintainers Work Together

The new RFC encourages the port maintainers and the Arch Linux team to work together towards supporting newer architectures.

Arch Linux says that they have taken inspiration from [Debian Ports][5], which has tried to do something similar.

I believe this is the right direction to go forward, and should help us get official ARM and RISC-V support in the near future. You can take a look at the [RFC][4] for more technical details.

💬 _What do you think about this RFC? Let me know in the comments down below!_

**Suggested Read** 📖

![][6]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/archlinux-arm-riscv/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/why-arch-linux/
[2]: https://news.itsfoss.com/content/images/2024/05/arch-linux-rfc.png
[3]: https://gitlab.archlinux.org/archlinux/rfcs/-/merge_requests/32
[4]: https://rfc.archlinux.page/0032-arch-linux-ports/
[5]: https://www.ports.debian.org/
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
