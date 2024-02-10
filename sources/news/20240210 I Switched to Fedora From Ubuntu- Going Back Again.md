[#]: subject: "I Switched to Fedora From Ubuntu: Going Back Again!"
[#]: via: "https://news.itsfoss.com/fedora-ubuntu-switch/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Switched to Fedora From Ubuntu: Going Back Again!
======
Here's how it went with the switch to Fedora.
In the past few years, I have tried using various popular distributions as my daily driver to share with you some insights on it.

While I find myself using an Ubuntu-based distro (or Ubuntu itself) in the end, I have given my fair share of time to Manjaro, and then recently Fedora (as non-Ubuntu distros).

If you are curious, you might want to check out my old blog post to see what happened when I switched to Manjaro Linux, an Arch-based distro.

Here, I am going to talk about the switch to Fedora.

**Spoiler alert! The switch was exciting, and a bummer at the same time.**

📋

This is entirely my opinion. You can totally have a different experience. So, I do not intend to discourage you from trying Fedora (if you read the conclusion).

### The Fedora Experience: Comfortable Yet Different

![][1]

Fedora ships with the GNOME desktop. So, it was a pretty comfortable switch for me, as I felt right at home with the GNOME desktop environment.

💡

Fedora packs in the latest and greatest Linux kernel, and newer technologies like Wayland support, and more. This can be a good thing and a bad thing at the same time. I'll tell you more about it as you read on.

Of course, unlike some other Ubuntu-based distributions, here, you get a vanilla GNOME experience (with no special tweaks out of the box).

You can try [Fedora spins][2] with a different desktop environment.

If you are someone who always wanted to try the latest GNOME without any customizations, Fedora is a good pick.

![][3]

Now, coming to my initial impressions with Fedora...🤔

If you are switching from Pop!_OS/Ubuntu like myself, **you will feel the absence of the tweaks**. That's the first noticeable thing.

I liked the Fedora-specific wallpapers, and I experienced the distribution with the dark mode for a couple of months before sharing my experience here.

![][4]

It is a tricky situation for some users who are not aware of the GNOME extensions that made some behavior possible. You would need to look around, search for the right GNOME extension if you want a dock locked-in to your home screen, tiling windows, or anything else.

You cannot go wrong with our list of the [best GNOME extensions][5] (to experiment). Let me give you a quick heads up — [**Dash-to-Dock**][6] is one of the extensions that you will need.

**What's next?** _The utilities and the goodies inside Fedora._

Well, Fedora comes baked in with the Nautilus file manager. So, you do not have to worry about file management, it will be business as usual.

The Fedora team retains the "Cheese" app around for now instead of [GNOME's new snapshot app][7].

So, you might want to install it separately if you require.

Not to forget something important: **Fedora comes with Flatpak support enabled out of the box.** You just need to enable Flathub repo (via **GNOME Software** ) to access all the packages you need:

![][8]

Therefore, if you hate Snaps, you have a good reason to continue your experience with Fedora instead of Ubuntu.

![][9]

In addition to the Flathub repo, I would suggest you to go through our handy guide on [things to do after installing Fedora][10] for the best experience:

![][9]

### The Hiccups I Hated!

Recall the mention above where I said Fedora's trait of featuring the latest tech can be troublesome?

Well, before I start documenting the bad experiences, let me tell you the good part of it:

If you have newer hardware, and want to experience the latest technologies in action, Fedora is a safe bet.

That being said, it is not smooth sail. Sure, for some, it can be, but not for everyone.

I had a sour user experience with applications like Discord and Chrome-based browsers.

**I had to turn off hardware acceleration** **on Discord** to make it responsive. It could be Wayland, or it could be Nvidia graphics (I had the latest driver installed, available in the RPM Fusion repo).

![][11]

If it is enabled, there is a delay between me typing and the text appearing on the screen. Weird, right? :/

Next up, you do not have fractional scaling enabled by default. Considering I have a two-monitor setup with different resolutions, I needed it.

Sure, I found a way to enable fractional scaling support using a command in the terminal:

```

    gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"

```

But, that's when things started to go south. I fiddled with the settings, but then could not log back in to my next session.

Not just that, with fractional scaling enabled, Vivaldi browser looked blurry. I tried to enable native Wayland support using the [ozone-platform flag][12]. But, it did not help much.

It was still an issue for [Fedora 40][13] (which is in the testing phase at the time of writing this).

I had to switch to X.org session, and then disable fractional scaling to use the desktop again.

So, no fractional scaling — a big let-down.

![][14]

I did not give up, I was ready to see tiny texts on one screen, and normal size fonts on the other screen to continue using Fedora (as I still do now) 😎

But, then another issue crept in, randomly, the Fedora session would just exit. It is still happening to me with all the GNOME extensions disabled, and no other customizations in place.

In other words, it logs out after a while of inactivity, instead of showing up the lock screen.

With this issue, I finally gave up.

I am going back to any other Ubuntu-based distribution (based on my distro hopping mood swings at the time).

_If you have a solution to my problems, feel free to comment. And, if you are considering Fedora for a switch, I would still recommend you to try it out if you do not need fractional scaling._

💬 _Hopefully, my experience helps someone out there! What do you want me to try switching to next as my daily driver for a challenge? Let me know your thoughts._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fedora-ubuntu-switch/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/content/images/2024/02/fedora-39-home.png
[2]: https://fedoraproject.org/spins/
[3]: https://news.itsfoss.com/content/images/2024/02/fedora-neofetch.png
[4]: https://news.itsfoss.com/content/images/2024/02/fedora-gnome-experience.png
[5]: https://itsfoss.com/best-gnome-extensions/
[6]: https://extensions.gnome.org/extension/307/dash-to-dock/
[7]: https://news.itsfoss.com/gnome-snapshot/
[8]: https://news.itsfoss.com/content/images/2024/02/flathub-repo.png
[9]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[10]: https://itsfoss.com/things-to-do-after-installing-fedora
[11]: https://news.itsfoss.com/content/images/2024/02/discord-hardware-acceleration.png
[12]: https://wiki.archlinux.org/title/Chromium#Native_Wayland_support
[13]: https://discussion.fedoraproject.org/t/f40-fractional-scaling-in-fedora-40-workstation-makes-some-applications-blurry/90393
[14]: https://news.itsfoss.com/content/images/2024/02/fractional-scaling-no.png
