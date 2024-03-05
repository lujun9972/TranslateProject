[#]: subject: "NixBSD: This Project Mixes FreeBSD and NixOS in One!"
[#]: via: "https://news.itsfoss.com/nixbsd/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

NixBSD: This Project Mixes FreeBSD and NixOS in One!
======
Wait, what? Two good things in one? What do you mean? Take a look here.
The awesomeness of open source never disappoints! Many from the community have teamed up to create something that will appeal to the _BSD_ and _Nix_ aficionados out there.

A new project called **NixBSD** has shown up that aims to combine the goodness of _FreeBSD_ with the utilitarian nature of _NixOS_.

📋

It is not an official collaborative project between NixOS and FreeBSD.

For those unfamiliar, [_FreeBSD_][1] is a Unix-like operating system based on [_BSD_][2] that supports a wide variety of hardware configurations, and is preferred by many who like a hands-on approach.

Whereas, [_NixOS_][3] is an immutable Linux distribution based on the [_Nix_][4] package manager that features a highly modular approach to carrying out important tasks related to the operating system.

For a more detailed look into NixOS, I highly suggest you take a look at our [NixOS tutorial series][5]. Now, let's move on to see what the NixBSD project is all about.

### NixBSD: What to Expect?

For starters, NixBSD is what its developers call “ **a reproducible and declarable BSD, based on NixOS** ”, it will let users take advantage of all the benefits that the Nix package manager has to offer.

So, things like atomic upgrades/rollback, absence of dependency conflict issues, multi-user package management, etc. are now a possibility on BSD 😲

The developers also add that:

> Although theoretically much of this work could be copied to build other BSDs, all work thus far has been focused on building a FreeBSD distribution.

If we go by the above, this project opens the door for other BSDs to implement Nix, and that is a great thing! 😃

At the time of writing, the NixBSD project has **three main repos** :

  * **nix** , which is the fork of the [Nix][6] package management system with modifications that allow it to run with FreeBSD.
  * **nixpkgs** , the fork of [Nix Packages][7] that works with FreeBSD, it provides access to over 80,000 packages that can be installed using Nix.
  * **NixBSD** , the main repository that acts as a stage for building variants of NixOS with the FreeBSD kernel.



All in all, this undertaking looks very promising, but, you will have to wait a bit for a proper distro release.

### Want to check it out?

In its current form, **NixBSD is in its very early stages of development** , and cannot be considered for production or even general use.

But, if you really want to try it out, or help by contributing to it, give its [GitHub repo][8] a visit.

[NixBSD (GitHub)][8]

You should find a very bare-bones setup with instructions on how to build it on a virtual machine on Linux. There's also a small section about how to contribute to the code of NixBSD.

**Suggested Read** 📖

![][9]

_💬 It will be interesting to see how this progresses. Did you expect such a project to come out?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/nixbsd/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.freebsd.org/
[2]: https://en.wikipedia.org/wiki/Berkeley_Software_Distribution
[3]: https://nixos.org/
[4]: https://en.wikipedia.org/wiki/Nix_(package_manager)
[5]: https://itsfoss.com/tag/nix-os/
[6]: https://github.com/NixOS/nix
[7]: https://github.com/NixOS/nixpkgs
[8]: https://github.com/nixos-bsd/nixbsd
[9]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
