[#]: subject: "Explicit Sync in Wayland is The Answer to NVIDIA Linux Problems!"
[#]: via: "https://news.itsfoss.com/explicit-sync-wayland/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Explicit Sync in Wayland is The Answer to NVIDIA Linux Problems!
======
Time to say goodbye to NVIDIA Wayland issues? Sounds like it!
[Wayland][1] on NVIDIA GPUs is something of a pain point for the Linux community that seems to haunt some, while others seem to be oblivious to it. You may already know what I am talking about.

Ever since the growth in Wayland's adoption, the number of random crashes, bugs, incompatibility, etc. have also increased with many users switching back to the older [X11 windowing system][2] to get a stable experience.

Many things have been tried to make [NVIDIA][3] GPUs perform better with Wayland, but, one of them stands out the most, and is closer to being implemented than ever before.

### Explicit Sync: What to Expect?

![][4]

Called “ _linux-drm-syncobj-v1_ ”, it is a new protocol for Wayland worked on by [Simon Ser][5] and a few other contributors that aim to introduce an explicit sync protocol based on DRM synchronization objects for Linux.

If it went over your head, then allow me to simplify it for you:

With this protocol in place, an application signals when rendering is complete to components such as the _driver_ , _kernel_ , _compositors_ , etc. so that they don't misbehave or perform any accidental synchronizations.

Interestingly, this is not something new that just appeared out of thin air. There used to be a [predecessor][6] to this explicit sync protocol that had to be ditched thanks to a limitation.

**In any case, for you, the end user** , you can expect a flicker-free experience in Wayland sessions when using an NVIDIA GPU, the multi-monitor experience should also be better, and the [frame pacing issues][7] should also be gone with this.

This protocol **also avoids limitations found in the implicit sync protocol** , which is widely used in open-source drivers, that enables AMD and Intel GPUs to function without the above-mentioned issues thanks to a few clever workarounds. But, NVIDIA never added support for that.

Even though there's a slight bump in performance, Xaver Hugl of KDE [adds][8] that:

> Do keep in mind though that these performance improvements are minor. While there may be some special cases where implicit sync between app and compositor was the bottleneck before, you’re unlikely to notice the individual difference between implicit and explicit sync at all.

That begs the following question...

### When will these changes arrive?

Soon is what I will say. You see, the “ _linux-drm-syncobj-v1_ ” protocol has already been [merged][9] into Wayland a few weeks back, and was introduced as a staging protocol with [_wayland-protocols 1.34_][10].

As for the others, this protocol has already been merged into [Mesa][11], GNOME's [Mutter][12], and even to NVIDIA's EGL External Platform library, [EGL-Wayland][13] with **a beta version planned on May 15 for the 555 driver release** which would include this protocol.

On the other hand, in KDE KWin's case, it is still [waiting to be merged][14]. Though, I would not worry, as it's only a matter of time before it is.

_💬 What do you think of this change? Better late than never?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/explicit-sync-wayland/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://wayland.freedesktop.org/
[2]: https://en.wikipedia.org/wiki/X_Window_System
[3]: https://www.nvidia.com/
[4]: https://news.itsfoss.com/content/images/2024/04/Explicit_Sync_Wayland.png
[5]: https://emersion.fr/
[6]: https://gitlab.freedesktop.org/wayland/wayland-protocols/-/blob/main/unstable/linux-explicit-synchronization/linux-explicit-synchronization-unstable-v1.xml
[7]: https://www.reddit.com/r/linux_gaming/comments/1b9mvzs/stutter_framepacing_issues_in_directx_games_under/
[8]: https://zamundaaa.github.io/wayland/2024/04/05/explicit-sync.html
[9]: https://gitlab.freedesktop.org/wayland/wayland-protocols/-/merge_requests/90
[10]: https://lists.freedesktop.org/archives/wayland-devel/2024-March/043537.html
[11]: https://gitlab.freedesktop.org/mesa/mesa/-/merge_requests/25709
[12]: https://gitlab.gnome.org/GNOME/mutter/-/merge_requests/3300
[13]: https://github.com/NVIDIA/egl-wayland/pull/104
[14]: https://invent.kde.org/plasma/kwin/-/merge_requests/4693
