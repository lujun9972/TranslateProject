[#]: subject: "ObsidianOS Review: A New, Innovative Linux Distro Built Around A/B Partitioning"
[#]: via: "https://itsfoss.com/obsidianos-review/"
[#]: author: "Neville Ondara https://itsfoss.com/author/neville/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ObsidianOS Review: A New, Innovative Linux Distro Built Around A/B Partitioning
======

[![Warp Terminal][1]][2]

Most new Linux distributions tend to follow a familiar formula: take a well-known base, add a desktop environment, sprinkle in some theming, and call it a day.

Sometimes it works; sometimes the distro disappears in six months. What you don’t often see, however, is a distro trying to rethink how updates, rollbacks, and system integrity fundamentally work.

[ObsidianOS][3] is one of those unusual projects that immediately caught my attention for exactly that reason. It’s Arch-based, yes, but the defining feature isn’t Arch at all; it’s the implementation of an **A/B partitioning layout** using good old **ext4** , not btrfs, snapshots, or any of the usual suspects.

I’ll admit, when I first heard about ObsidianOS, I had the same confused grin many Reddit users did: “Wait… A/B partitions? On a traditional Linux desktop? Without btrfs?” But after digging into the documentation, installing it on a virtual machine, and exploring it for a bit, I walked away genuinely impressed! ✨

Let’s break things down.

### ObsidianOS: Doing things a bit differently

![][4]

At its core, ObsidianOS is a UEFI‑only, systemd‑based operating system for x86_64 **** systems, designed with an A/B partition layout for reliability. The A/B partition scheme means your root filesystem exists twice, partition A and partition B. When you update, the system writes to the inactive slot. If something goes wrong, you reboot into the previously working one.

So, no complex snapshot rolling, no broken bootloaders, no “reinstall Arch because [Pacman][5] broke at 2 AM.” Just a simple flip back to the other partition. **It’s very similar to how ChromeOS, Android, and some embedded systems work, but brought to the broader Linux desktop.**

The project originally launched with a single edition, but now it offers:

  * **Base Edition** (minimal, TUI installer)
  * **KDE Edition** (the recommended one)
  * **COSMIC Edition** (beta, but functional)
  * **Void Edition** (for experts who want a [Void][6] base with Obsidian’s tooling)



This is already more variety than I expected for a distro still considered “early.”

### Minimum system requirements

From my experience and the project’s own documentation, ObsidianOS is quite modest in its hardware needs but add more than what it says.

  * 2 GB RAM (yeah. we definitely need more)
  * 20+ GB storage
  * UEFI firmware
  * 64-bit CPU



🚧

ObsidiaOS is in the early stages of development. I would consider it experimental. For this reason, either try it in a virtual machine or spare test system. Don't replace your stable Ubuntu/Debian/Mint/Fedora with Obsidian yet.

### Installing ObsidianOS

![][7]

Installation depends on the edition. The **Base Edition** sticks to a TUI installer, which is a bit old-school, and familiar to anyone who has [installed Arch Linux][8].

The KDE and COSMIC editions, on the other hand, come with a **Qt6 + Python GUI installer** built by the project itself. I tested the KDE version, and honestly, it’s refreshing to see an independent project ship its own installer instead of relying on Calamares.

It walks you through:

Selecting the target disk.

![][9]

Setting up the A/B partitions automatically.

![][10]

Selecting System Image.

![][11]

Selecting Timezone.

![][12]

Selecting Keyboard layout.

![][13]

Bootloader setup.

![][14]

The layout still feels young, a few dialogs could be clearer, but it works, and more importantly, it handles the A/B scheme seamlessly without throwing technical jargon at the user.

### First impressions of ObsidianOS

Booting into ObsidianOS for the first time feels much like entering a polished Arch environment. KDE is clean and mostly vanilla, without unnecessary patches or wild theming choices.

![][15]

The application launcher provides quick access to system settings, utilities, and installed applications, keeping everything organized and easily reachable. It feels intuitive, responsive, and minimalistic, much like what you’d expect from a well-curated Arch-based environment, no clutter, just efficiency at your fingertips.

![][16]

But the interesting parts aren’t immediately visible. They show up once you open the **ObsidianOS Control Center** , a Qt6 GUI frontend for the `obsidianctl` command-line tool. This is where the distro starts to feel like its own thing rather than “Arch with an unusual partition setup.”

The Control Center shows you:

  * Which slot (A or B) you’re currently running
  * Available updates
  * Rollback options
  * Logs and system information



For a project its size, the amount of infrastructure built around these tools is impressive. 😎

![][17]

#### User-Mode Overlays: Probably the most intriguing feature

This is where ObsidianOS goes beyond just A/B partitions.

The distro introduces **user-mode overlays** , an experimental system written in [Rust][18] that intercepts libc calls to create layered filesystem behavior, without touching kernel modules or requiring special filesystems.

📝 To simplify: it adds an overlay on top of the root filesystem, but entirely in user space.

This gives you:

  * Layered modifications
  * Reversible changes
  * A “sandboxed” feel for certain operations
  * No risk to the base system unless you commit changes



It’s clever, experimental, and absolutely the kind of thing that appeals to tinkerers. The overlay mechanism also powers another new component.

#### opm: Overlaid packages

`opm` is the **ObsidianOS Package Manager** , also written in Rust, that works alongside pacman. When you install a package with opm:

  * It downloads the package from pacman.
  * It creates an overlay image of that package.
  * The overlay is applied on top of the system.



This is miles away from how most distros handle packaging, and while it’s still experimental, it hints at a future where package changes have a much smaller chance of trashing your root system.

Arch fans might raise eyebrows, but power users will probably be curious. 😎

#### ObsidianOS Plugins

This is another [Rust-powered system that lets scripts respond to system events][19], like:

  * battery changes
  * connection/disconnection events
  * hardware triggers



Not entirely new in the Linux world, but ObsidianOS wraps it in a clean, unified framework instead of leaving users to dig through systemd units and acpi handlers.

#### Daily usage and performance

Being Arch-based, the performance story is exactly what you’d expect:

  * Fast boot times
  * Responsive KDE experience
  * Recent kernels
  * Access to the entire Arch repository



The difference is that ObsidianOS doesn’t try to be flashier or heavier than necessary. It stays lean, even in the KDE edition. The COSMIC edition is still in beta, so I’ll reserve judgment until the desktop hits maturity.

The only thing I noticed is that some experimental components, overlays and opm are still evolving. They work, but occasionally feel like tools intended for people who enjoy digging into logs and understanding what’s happening under the hood. That’s not a criticism; it’s simply the current reality of the project. 🤷

### Too much reliance on experiments?

To keep things realistic, it’s important to mention some concerns that other people (and I) have:

**Small team and young project** : Several users on Reddit said they avoid distros with very small maintainer counts. It’s a fair point, longevity matters.

**Experimental components:** The overlays, opm, and plugin system are fascinating, but still in the “early tech demo but highly functional” stage.

**A/B partitioning is unusual for the desktop** : Not bad, just unfamiliar. Some users will love it; others may feel unsure.

But none of these are dealbreakers if you know what you’re walking into.

### Final Thoughts

ObsidianOS is one of the rare Arch-based distributions that genuinely tries to solve a long-standing problem instead of repackaging Arch with a new desktop theme. The A/B partitioning approach makes system updates dramatically safer, and the Rust-based overlay tools point toward a future where system state is much more predictable and much less prone to accidental breakage.

Is it ready for absolute beginners? Probably not yet.

Is it suitable for people who install Arch manually for fun? Absolutely.

And for users who love the idea of transactional updates but don’t want to commit to [NixOS][20], Fedora Silverblue, or OpenSUSE MicroOS, ObsidianOS hits a very interesting middle ground.

It’s ambitious, clever, and while still young, it’s doing something bold that most distros simply don’t attempt. I’ll be keeping an eye on how it develops and **if the team keeps pushing features like overlays and opm, it might end up becoming one of the more innovative Linux projects to come out of the Arch ecosystem in a while**.

🏅

These are the reasons why ObsidianOS is It's FOSS's Distro of the Month.

What do you think of bringing A/B partitioning to desktop Linux and other unusual features in ObsidianOS? I’m curious to hear other experiences.

--------------------------------------------------------------------------------

via: https://itsfoss.com/obsidianos-review/

作者：[Neville Ondara][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/neville/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://files.obsidianos.xyz/
[4]: https://itsfoss.com/content/images/2025/12/obsidianos.webp
[5]: https://itsfoss.com/pacman-command/
[6]: https://itsfoss.com/void-linux/
[7]: https://itsfoss.com/content/images/2025/11/itsfoss4.png
[8]: https://itsfoss.com/install-arch-linux/
[9]: https://itsfoss.com/content/images/2025/11/itsfoss8.png
[10]: https://itsfoss.com/content/images/2025/11/itsfoss10.png
[11]: https://itsfoss.com/content/images/2025/11/itsfoss11.png
[12]: https://itsfoss.com/content/images/2025/11/itsfoss13.png
[13]: https://itsfoss.com/content/images/2025/11/itsfoss14.png
[14]: https://itsfoss.com/content/images/2025/11/itsfoss15.png
[15]: https://itsfoss.com/content/images/2025/11/itsfoss5-1.png
[16]: https://itsfoss.com/content/images/2025/11/itsfoss17.png
[17]: https://itsfoss.com/content/images/2025/11/itsfoss16.png
[18]: https://itsfoss.com/tag/rust-basics/
[19]: https://github.com/Obsidian-OS/plugind
[20]: https://itsfoss.com/tag/nix-os/
