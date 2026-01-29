[#]: subject: "A Bunch of Developers Have Come Together to Make Linux Gaming Great"
[#]: via: "https://itsfoss.com/news/open-gaming-collective-launch/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A Bunch of Developers Have Come Together to Make Linux Gaming Great
======

[![Warp Terminal][1]][2]

Made up of several Linux-focused development projects, the [Open Gaming Collective][3] (OGC) is an initiative that looks to consolidate development efforts across the Linux gaming ecosystem, focusing on improving shared components.

Bazzite's Kyle Gospodnetich shared this development via [a Discourse post][4].

More details below. 👇

### Open Gaming Collective: What's Cooking?

In terms of what's to be worked on, the collective aims to unify developmental efforts surrounding important components such as **kernel patches** , **graphics and display tooling** ( _Mesa, Vulkan, and Wayland_ ), **hardware enablement for gaming peripherals** , **** and **gaming-focused packages** like [gamescope][5].

The founding members consist of known names like [Bazzite][6] ( _as part of Universal Blue_ ), [PikaOS][7], [ASUS Linux][8], [ShadowBlip][9], and [Fyra Labs][10]. They are supported by strategic partners like [ChimeraOS][11], [Nobara][12] ( _led by GloriousEggroll_ ), and [Playtron][13].

The OGC operates under a "[ _Lazy Consensus_][14]" governance model, where proposals are made publicly and given 72 hours for community objections. If nobody raises concerns in that timeframe, the proposal moves forward. Any objections must include legitimate reasons and be open to healthy discussion.

They are also committing to an " _ **Upstream First**_ " policy, under which any code that the OGC comes up with or improves must be submitted to the original upstream projects rather than living on as a permanent patch or fork.

One example of this is the [OGC Kernel][15], **their gaming-focused Linux fork**.

Of course, custom kernels aren't something new. We already have [Liquorix][16] with Zen tuning and a 1000Hz tick rate, [XanMod][17] with ThinLTO optimizations and BBRv3 TCP, [Zen Kernel][18] providing the foundational interactive tuning patches, and [CachyOS Kernel][19] offering multiple schedulers like BORE and EEVDF with CPU-specific optimizations.

**For Bazzite users specifically** , Kyle has shared that they will be switching to [InputPlumber][20], moving away from [HHD][21] (Handheld Daemon). Features like RGB lighting and fan control will be directly integrated into the Steam UI.

The project will also adopt the OGC Kernel and contribute their patches to the collective, which will then work on getting them merged upstream.

📋

Just to clarify, InputPlumber is an open source input router and remapper daemon that handles controller input. It is already used on ChimeraOS, SteamOS and Nobara.

### My Two Cents

I was already optimistic about [Linux gaming][22] getting bigger in 2026, and this move only makes me more confident. On paper, this looks like something that brings a large group of gaming-focused projects with a very grounded approach.

It will be interesting to see how this collaborative effort plays out, especially with their commitment to pushing improvements into [mainline Linux][23] rather than keeping the work to themselves.

* * *

**Suggested Read 📖:** [_Linux Gamers Are Finally Getting Their Own Browser_][24]

![][25]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/open-gaming-collective-launch/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://opengamingcollective.org/
[4]: https://universal-blue.discourse.group/t/a-brighter-future-for-bazzite/11575
[5]: https://github.com/ValveSoftware/gamescope
[6]: https://bazzite.gg/
[7]: https://wiki.pika-os.com/
[8]: https://asus-linux.org/
[9]: https://github.com/ShadowBlip/
[10]: https://fyralabs.com/
[11]: https://chimeraos.org/
[12]: https://nobaraproject.org/
[13]: https://www.playtron.one/
[14]: https://github.com/OpenGamingCollective/organization-governance/blob/main/governance.md
[15]: https://github.com/OpenGamingCollective/linux
[16]: https://itsfoss.com/liquorix-kernel/
[17]: https://xanmod.org/
[18]: https://github.com/zen-kernel/zen-kernel
[19]: https://wiki.cachyos.org/features/kernel/
[20]: https://github.com/ShadowBlip/InputPlumber
[21]: https://github.com/hhd-dev/hhd
[22]: https://itsfoss.com/linux-gaming-guide/
[23]: https://www.kernel.org/
[24]: https://itsfoss.com/news/opera-gx-linux-announcement/
[25]: https://itsfoss.com/content/images/icon/android-chrome-512x512-248.png
