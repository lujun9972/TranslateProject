[#]: subject: "13 Popular Software That Feel Like Open Source But They Are Not"
[#]: via: "https://itsfoss.com/popular-software-open-source-feel/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

13 Popular Software That Feel Like Open Source But They Are Not
======

[![Warp Terminal][1]][2]

As Linux users, most of us prefer open-source software. But if you’ve been using Linux for a while, you know this truth too: in daily workflows, you may have to rely on proprietary software**.**

And sometimes, you use software that feels like open source projects but they actually are not. I am going to list some of those applications that are popular among Linux users but often we don't realize that they are not open source. I'll also suggest their open source alternatives for you.

### Obsidian: Personal knowledge base

![][3]

[Obsidian][4] has become incredibly popular among developers, researchers, and anyone who takes their notes seriously. Its local-first approach, Markdown support, and graph view make it ideal for building a [personal knowledge base][5].

While it supports community plugins and customization, **the core application itself is proprietary**. This may come as a surprise because it always feels like Obsidian is open source. Alas! It is not.

🐧

The most suitable open source alternative to Obsidian is [Logseq][6]. You can also try Joplin for its simplicity.

### Termius: Modern SSH client

![][7]

[Termius][8] is a sleek, cross-platform SSH client used by sysadmins and developers, specially the ones who manage multiple servers.

It offers synchronization across devices, organized host management, and secure key handling. However, it’s a fully **closed-source commercial product.** How I wish it was open source.

🐧

[Tabby][9] could be somewhat of an open source alternative here.

### MobaXterm: Accessing Linux servers from Windows

![][10]

[MobaXterm][11] is primarily a Windows tool, but many Linux users interact with it while managing remote Linux servers from work or university environments. At least that's what I used around 12 years ago at work.

It combines SSH, X11 forwarding, and remote desktop features under one roof. And it does the job very effectively and offers a lot more than PuTTY.

🐧

Not sure if there is a single application that has same features as MobaXterm. Perhaps PuTTY and X2Go or Remmina could be used.

### Warp: The AI-powered terminal

![][12]

[Warp][13] is a new-age terminal focused on modern developer and devops workflows. It offers command blocks, AI suggestions and AI agents, team sharing features, and a highly polished interface.

But it’s completely **closed-source**. I would have appreciated it if they offered it as open source and used their proprietary AI offering as optional add-on.

🐧

I believe [Wave][14] is the most suitable open source alternative to Warp. Similar features and you can also use local AI.

### Docker Desktop: For easy container management

![][15]

Docker itself is open source, but [**Docker Desktop**][16] **is not**.

It provides a GUI, system integration, container management tools and additional features that simplify your container-based workflows on personal machines. After all, not everyone is a command line champion.

Despite the [licensing controversies][17], many people still use it because of convenience and integration with development environments.

🐧

[Rancher Desktop][18] is worth looking at as an alternative here.

### Visual Studio Code: Microsoft's not so open offering

![][19]

[VS Code][20] sits in a slightly grey area:

  * The base project ( **Code – OSS** ) is open source.
  * The official **Microsoft build of VS Code is proprietary** due to licensed components and telemetry.



Nevertheless, it remains the most popular code editor for developers, including Linux users, thanks to its extensions, easy GitHub integration, and huge plugin ecosystem.

🐧

[Code - OSS][21] is available in the official repositories of many Linux distributions. Think of it as Chromium browser which is open source version of Chrome.

### Discord: The developer community hub

![][22]

There was a time when developers used to dwell in IRC servers. That was 20 years ago. These days, Discord seems to have taken over all other instant messaging services.

Surprisingly, [Discord][23] started as a gaming platform but has become a central communication tool for tech communities, open source projects, and developer groups.

Many open source project communities now live there, even though Discord itself is fully proprietary.

🐧

Matrix-based [Element][24] can be an alternative here.

### Vivaldi: Chrome alternative browser

![][25]

[Vivaldi][26] is a popular web browser among Linux users. It is based on open-source Chromium, but its UI, branding, and feature layer are proprietary.

Its deep customization, built-in tools (notes, mail, calendar), and privacy-focused philosophy make it a suitable choice for many Linux users.

Wondering why it is not open source? They have a [detailed blog post about it][27].

🐧

You may consider Brave web browser.

### VMWare Workstation: Enterprise-level virtualization

![][28]

But since it is 'enterprise' level stuff, how can it be open source?

Despite all the [licensing controversy][29], [VMware’s Workstation and Fusion products][30] are still heavily used for virtualization in both personal and enterprise environments.

They’re well-optimized, reliable, and offer features that are sometimes ahead of open-source alternatives. But yes, they are completely proprietary.

🐧

GNOME Boxes is my preferred way of managing virtual machines.

### Ukuu: Easy kernel management on Ubuntu

![][31]

[Ukuu][32] stands for Ubuntu Kernel Upgrade Utility. It allows you to [install mainline Linux kernel on Ubuntu][33]. You can also use it for installing a kernel of your choice, add, delete kernels from the comfort of GUI.

A few years ago, Ukuu switched to a paid license, unfortunately.

🐧

[Mainline][34] is an actively maintained open source fork of Ukuu.

### Plex: Media server for self-hosting enthusiasts

![][35]

[Plex][36] is extremely popular among Linux users who build homelabs and/or [media servers][37].

What started as a self-hosted media server, Plex gradually moved to become a streaming platform of its own. Oh! The irony.

Not just that, most of its ecosystem is closed-source and cloud-dependent. Recently, they have started [cracking down on free remote streaming of personal media][38].

🐧

Forget Plex, go for [Jellyfin][39]. Emby and Kodi are also [good open source media servers][40].

### Tailscale – Easy remote access for self-hosters

![][41]

[Tailscale][42] uses the open-source WireGuard protocol but offers a proprietary product and service on top of it.

It makes secure networking between your devices ridiculously easy. This is perfect for self-hosters, and homelabbers as you can securely access your self-hosted services from outside your home network.

This simplicity is why several users accept the closed-source backend.

🐧

You can go for [Headscale][43] as an alternative.

### Snap Store: Open front, closed backend

![][44]

Ubuntu's Snap-based software center, Snap Store, is closed source software.

Snapd, the package manager, is open source. But the Snap Store backend is proprietary and controlled by Canonical. This has sparked debate in the Linux community for years.

Still, most Ubuntu users rely on it daily for installing and managing applications. It comes by default, after all.

🐧

As an Ubuntu user, you can [get the actual GNOME Software back][45].

### Steam: The backbone of Linux gaming

![][46]

Surprised? Yes, our beloved Steam client is not open source software. Yet we use it. None of us can deny that Steam has been crucial for improving the [state of gaming on Linux][47].

From [Proton][48] to native Linux support for thousands of games, Steam has played a huge role in improving Linux as a gaming platform, even though the platform itself is proprietary.

🐧

If you must, you could try [Lutris][49] or Heroic Games Launcher.

### Conclusion

Using open-source software is about freedom, not necessarily forced purity.

Many Linux users aim to replace proprietary software whenever possible but they also value productivity, reliability, and workflow efficiency. If a closed-source tool genuinely helps you work better today, well use them but keep on supporting open alternatives alongside.

The good thing is that for almost every popular proprietary tool, the open-source ecosystem continues to offer strong alternatives.

To me, the important thing isn’t whether your entire stack is open source. It’s that **you’re aware of your choices and the trade-offs behind them.**

And that awareness is where true freedom begins.

###

--------------------------------------------------------------------------------

via: https://itsfoss.com/popular-software-open-source-feel/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/11/image-44.png
[4]: https://obsidian.md/
[5]: https://itsfoss.com/open-source-second-brain-apps/
[6]: https://itsfoss.com/logseq/
[7]: https://itsfoss.com/content/images/2025/11/termius.webp
[8]: https://termius.com/
[9]: https://tabby.sh/
[10]: https://itsfoss.com/content/images/2025/11/mobaxterm.webp
[11]: https://mobaxterm.mobatek.net/
[12]: https://itsfoss.com/content/images/2025/11/image-45.png
[13]: https://www.warp.dev/
[14]: https://itsfoss.com/news/wave-terminal/
[15]: https://itsfoss.com/content/images/2025/11/docker-desktop.webp
[16]: https://www.docker.com/products/docker-desktop/
[17]: https://www.infoworld.com/article/2268969/docker-desktop-is-no-longer-free-for-enterprise-users.html
[18]: https://rancherdesktop.io/
[19]: https://itsfoss.com/content/images/2025/11/image-46.png
[20]: https://code.visualstudio.com/
[21]: https://github.com/microsoft/vscode
[22]: https://itsfoss.com/content/images/2025/11/discord.webp
[23]: https://discord.com/
[24]: https://itsfoss.com/element/
[25]: https://itsfoss.com/content/images/2025/11/image-47.png
[26]: https://vivaldi.com/
[27]: https://vivaldi.com/blog/technology/why-isnt-vivaldi-browser-open-source/
[28]: https://itsfoss.com/content/images/2025/11/image-49.png
[29]: https://itsfoss.com/news/vmware-broadcom-subscription/
[30]: https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion
[31]: https://itsfoss.com/content/images/2025/11/gtk4.webp
[32]: https://teejeetech.com/ukuu/
[33]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[34]: https://github.com/bkw777/mainline
[35]: https://itsfoss.com/content/images/2025/11/image-51.png
[36]: https://www.plex.tv/
[37]: https://itsfoss.com/media-server-software/
[38]: https://arstechnica.com/gadgets/2025/11/plexs-crackdown-on-free-remote-streaming-access-starts-this-week/
[39]: https://jellyfin.org/
[40]: https://itsfoss.com/best-linux-media-server/
[41]: https://itsfoss.com/content/images/2025/11/tailscale.webp
[42]: https://tailscale.com/
[43]: https://github.com/juanfont/headscale
[44]: https://itsfoss.com/content/images/2025/11/image-53.png
[45]: https://itsfoss.com/ubuntu-gnome-software-center/
[46]: https://itsfoss.com/content/images/2025/11/image-52.png
[47]: https://itsfoss.com/linux-gaming-guide/
[48]: https://itsfoss.com/steam-play/
[49]: https://itsfoss.com/epic-games-lutris-linux/
