[#]: subject: "Gaming on Fedora: 2024"
[#]: via: "https://fedoramagazine.org/gaming-on-fedora-linux-2024/"
[#]: author: "Kevin Degeling https://fedoramagazine.org/author/eonfge/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Gaming on Fedora: 2024
======

![][1]

Photo by [Igor Karimov][2] on [Unsplash][3], font is [Orbitron][4]

Gaming is going strong. This beautiful hobby is growing constantly and new games are being released all the time. Technology is also advancing, making games more demanding while also offering more integrated and connected experiences. This in turn creates a social space were people can collaborate, compete and relax. And best of all, Fedora Linux will empower you to do so. Keep reading to find out how you can play the latest video games on Fedora Linux, in 2024.

### Previously on…

Before we kick off, you should check out our [previous article from 2021][5]. This article contains many useful tips, and most of its information is still relevant today. That said, three years in the Linux community is a long time, and many things have changed.

#### Disclaimer

> This guide will help you play the latest video games. But a notice is in order. Most commercial games are proprietary and they often require commercial online services. While using any of these services and games, you can be subjected to all kinds of bad software practices: You may be subject to aggressive monetization, privacy-disrespecting anti-tamper tools, and user analytics. This guide will focus on the prerequisites of non‑FLOSS gaming using Fedora Linux. The choice is yours.

### Launchers

To start, it would be worth emphasizing that there are more community tools that allow you to game on Linux. While we previously focused on Steam, let’s talk about a few other applications.

#### Minigalaxy

[GOG.com][6] has been a staple in Linux gaming. They provide native Linux packages for a large series of games since 2014. They’ve also focused on selling games without DRM. Sadly, while they have made steps in supporting Fedora Linux and other distributions, their official desktop application is not available on Linux.

[Minigalaxy][7] is the answer. This community made tool allows you to download games from GOG.com, update them automatically, and more. Minigalaxy is available as a traditional package or as a Flatpak.

```

    $ sudo dnf install minigalaxy

```

```

    $ flatpak install flathub io.github.sharkwouter.Minigalaxy

```

![][8]

#### Bottles

Perhaps you’re old enough to own certain games on physical media. You could buy them again on Steam or GOG, but that would be a wasteful. Lutris might support a disk-installation, but you’ll not always be that lucky. If all previous options fail, you’ll have to get your hands dirty with Wine.

Luckily, there is [Bottles][9]. This modern application allows you to configure Wine or Proton without too much hassle. You can create a ‘bottle’ per application, tweaking the configuration depending on what you need. While it’s the most involved of all possible scenarios, it does give you another option in case you really want to run a specific piece of old software.

Finally, Bottles also has build-in scripts to install Battle.net, Epic Game Store and others. It even supports Steam, if you want your computer to mimic a matryoshka doll. Either way, Bottles is the best way of managing Wine nowadays. The recommended way of installing Bottles is with Flatpak, although a traditional package is also available.

```

    $ flatpak install flathub com.usebottles.bottles

```

```

    $ sudo dnf install bottles

```

![][10]

### Tweaking

Besides all the possible launchers, there are also some major changes in the software that we mentioned three years ago. [Discord][11] and [Open Broadcast Software (OBS)][12] now officially support Flathub! This is a major achievement for Flathub and it makes it the recommended way to use these applications.

#### Proton versions

Proton, as a tool, has also come a long way. Valve bundles official versions of Proton with Steam, but you can also download custom versions of Proton. The most popular community maintained version of Proton is [Proton Glorious Eggroll][13], or Proton GE for short. This version contains more bleeding edge patches and additions that Valve can’t offer on the Steam Deck.

For easy management of Proton versions, [ProtonUp-Qt][14] is recommended. This simple UI application allows you to easily download the latest version of Proton GE, as well as other versions that various volunteers provide online.

```

    $ flatpak install flathub net.davidotek.pupgui2

```

![][15]

#### Gamescope

Another tool that can really help you out is [Gamescope][16]. This tool was also developed by Valve and it allows you to upscale games in a variety of different ways. It also integrates well with Wayland, addressing some ‘auto-scaling’ problems that you can experience when migrating away from the X-window manager.

In combination with Steam, you can render a game at 1080p and output it at 1440p. This could help you if your hardware would otherwise not be able to run a certain title.

```

    $ gamescope -f -h 1080 -H 1440 -- %command%

```

You can also use Gamescope with older titles, rendering at 320p and outputting the game at 1440p, with advanced up-scaling.

```

    $ gamescope -F fsr -f -h 320 -H 1440 -- /usr/bin/application

```

Gamescope can fill a niche for those who sometimes have trouble running older titles, or it can give you more legroom on less powerful hardware. Either way, it’s a powerful tool when gaming on Fedora Linux. Note that you can install the Flathub and traditional package side-by-side.

```

    $ sudo dnf install gamescope

    $ flatpak install flathub org.freedesktop.Platform.VulkanLayer.gamescope

```

### Challenges

Not everything is perfect though, and while gaming on Fedora Linux is great, you should remain realistic.

#### Drivers

Driver support for gaming hardware is mostly the same from a consumer’s point of view. Technically, Nvidia has made a big step in open-sourcing their proprietary drivers. But sadly, this is a large project and consumers will not see any benefits from it for some time. As such, Nvidia users should still follow the [setup guide from the original article][5]. Other hardware, like those from AMD and Intel work almost perfectly.

#### Anti-cheat

In a twisted sense of irony, what the Linux community might gain in the future with Nvidia’s support we might lose in terms of game support. Many developers use anti-tamper and anti-cheat tools that run afoul with Linux. While some developers do invest some effort in supporting Linux, this is still a drawback. Volunteers maintain a list online, [Are We Anti-Cheat Yet?][17], listing all incompatible games. You should check this website before you spend money on a game or its content.

![A breakdown of all anti-cheat equipped games, and their support for Linux in general.][18]

But, the challenge does not stop there. A new wave of anti-cheat technology focuses on kernel-level access. This is the story of Nvidia’s closed source drivers all over again, but worse. Even when we ignore the ethical discussion about closed source drivers for a moment, it’s unlikely that these game developers and their publishers will ever release the tools to make a custom proprietary anti-cheat driver possible.

### Summary

Just like last time, this is a lot to take in. There are still more tools and applications that couldn’t be featured. Emulation is a topic for another day, and streaming services like [GeForce NOW][19] are also making gaming easier on Fedora Linux.

It’s impressive what three years can do in terms of gaming on Fedora Linux. Proton has matured and with the corporate backing of Valve, many things have improved throughout the entire gaming ecosystem. The Steam Deck is also not to be underestimated. It makes gaming on Linux frictionless and most of its innovations end up in Fedora Linux and other distributions.

Should you switch to Fedora Linux for your gaming needs? Just like last time, it depends. Anti-cheat for competitive games is becoming a bigger problem and there will always be companies that consider the market-share of Linux too small, to warrant serious attention. Your expectations and/or willingness to compromise remain the determining factor. That said, existing Fedora Linux users will have plenty of games to play.

![][20]

_Author’s comment. In the past three years, I’ve never been bored playing video games on Fedora Linux. I already own more games then I have free time. Also, there is the Steam Deck. While it is in no way affiliated with Fedora Linux or its partners… it’s certainly the device I use most for gaming nowadays. With that device in hand, I have good confidence in the future of gaming on Linux._

_Got any video game recommendations? Feel free to place them in the comments below._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/gaming-on-fedora-linux-2024/

作者：[Kevin Degeling][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/eonfge/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/06/cover-2-816x345.png
[2]: https://unsplash.com/photos/white-and-black-game-controller-9AmKnNZw3GA
[3]: https://unsplash.com
[4]: https://fonts.google.com/specimen/Orbitron
[5]: https://fedoramagazine.org/gaming-on-fedora/
[6]: https://www.gog.com/
[7]: https://sharkwouter.github.io/minigalaxy/
[8]: https://fedoramagazine.org/wp-content/uploads/2024/06/Screenshot-from-2024-06-08-14-11-47-1024x730.png
[9]: https://usebottles.com/
[10]: https://fedoramagazine.org/wp-content/uploads/2024/06/Screenshot-from-2024-06-08-14-10-48-1024x730.png
[11]: https://flathub.org/apps/details/com.discordapp.Discord
[12]: https://flathub.org/apps/details/com.obsproject.Studio
[13]: https://github.com/GloriousEggroll/proton-ge-custom
[14]: https://davidotek.github.io/protonup-qt/
[15]: https://fedoramagazine.org/wp-content/uploads/2024/06/Screenshot-from-2024-06-08-14-09-30-1024x730.png
[16]: https://github.com/ValveSoftware/gamescope
[17]: https://areweanticheatyet.com/
[18]: https://fedoramagazine.org/wp-content/uploads/2024/06/Screenshot-from-2024-06-08-14-13-15-1024x318.png
[19]: https://play.geforcenow.com/
[20]: https://fedoramagazine.org/wp-content/uploads/2024/06/Screenshot-from-2024-06-08-14-39-05-1024x651.png
