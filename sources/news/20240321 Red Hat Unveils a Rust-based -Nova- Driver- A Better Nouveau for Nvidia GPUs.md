[#]: subject: "Red Hat Unveils a Rust-based 'Nova' Driver: A Better Nouveau for Nvidia GPUs"
[#]: via: "https://news.itsfoss.com/red-hat-nova-driver/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Red Hat Unveils a Rust-based 'Nova' Driver: A Better Nouveau for Nvidia GPUs
======
A Rust-based Nvidia driver? Sounds exciting!
Nouveau driver's future looked promising after NVIDIA released open-source GPU kernel modules.

While that was reflecting on Nouveau's progress, the development has slowed down, especially, with the maintainer of Nouveau [resigning last year][1] right after enabling GSP (GPU System Processor) support with Nvidia.

And, it seems now that the Red Hat display driver team is back on track with something more interesting: **Nova** , a modern replacement to Nouveau. Danilo Krummrich, a software engineer from Red Hat, announced the project on a [mailing list][2].

So, what is it?

### Nova: Rust-based Driver for the Green Team

Nova is a Rust-based GSP-only driver for Nvidia GPUs. It is aimed to be the successor to Nouveau when it is ready.

Of course, one of the reasons for Red Hat to think of a successor is because the primary maintainer for Nouveau resigned.

Danilo mentioned that with this project they want to work towards a simplified (but modern) driver when compared to Nouveau:

> With Nova we see the chance to significantly decrease the complexity of the driver compared to Nouveau for mainly two reasons. First, Nouveau's historic architecture, especially around nvif/nvkm, is rather complicated and inflexible and requires major rework to solve certain problems (such as locking hierarchy in VMM / MMU code for VM_BIND currently being solved with a workaround) and
>  second, with a GSP-only driver there is no need to maintain compatibility with pre-GSP code.

Furthermore, Red Hat seems to be constantly working on more Rust code and optimizations across their Linux offerings.

So, it is not a surprise for them to want the driver built with Rust now that the Linux kernel is adding slowly adding Rust components.

Of course, considering it as an ambitious project, it has its hiccups, the big one is:

> With the choice of Rust the first problem to deal with are missing C binding abstractions for integral kernel infrastructure (e.g. device / driver abstractions). Since this is a bit of a chicken and egg problem - we need a user to upstream abstractions, but we also need the abstractions to create a driver - we want to develop Nova upstream and start with just a driver stub that only makes use of some basic Rust abstractions.

So, the approach for the project will be through three primary branches where the Nova stub driver (a module) depends on PCI and device branches.

![][3]

You can take a look at the [repository][4] hosted within Freedesktop's kernel's graphic development section.

While all of this sounds cool, it is a challenging task for the developers to offer a full-fledged Rust-based driver. Sure, the memory safety benefits, security, and performance benefits will be the result with such projects.

However, when and how that happens (without any inconvenience for adoption) remains a deciding factor.

Whatever happens, Nvidia GPU users getting a better compatibility with Linux is all I want because I have had a fair share of display issues because of RTX 3000 series graphics card. And, it would be really convenient for a modern Nvidia display driver for Linux 😎

Until then, Nouveau driver is here to stay. And, it will exist for older Nvidia GPUs even when the Nova driver arrives as a successor.

_What do you think about the Nova driver? Share your thoughts in the comments below!_

_Via:_ [_Phoronix_][5]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/red-hat-nova-driver/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://lists.freedesktop.org/archives/nouveau/2023-September/043239.html
[2]: https://lore.kernel.org/dri-devel/Zfsj0_tb-0-tNrJy@cassiopeiae/
[3]: https://news.itsfoss.com/content/images/2024/03/nova-driver.jpg
[4]: https://gitlab.freedesktop.org/drm/nova
[5]: https://www.phoronix.com/news/Red-Hat-Nova-Rust-Abstractions
