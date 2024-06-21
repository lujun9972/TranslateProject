[#]: subject: "Accent Color and VR Support for GNOME is Ready"
[#]: via: "https://news.itsfoss.com/gnome-accent-color-vr/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Accent Color and VR Support for GNOME is Ready
======
Accent colors making a debut on GNOME along with future-ready VR
support.
[![][1]][2]

GNOME is a very widely used [desktop environment][3] which is the default one on many prominent Linux distributions like Debian, Ubuntu, Red Hat Enterprise Linux and Fedora.

In a recent set of moves, GNOME received two very significant changes that will take it into newer horizons, making it a more versatile desktop environment.

### A Crucial Moment for GNOME: What's Happening?

![Source: Alice Mikhaylenko][4]

The first of those moves is the **introduction of support for accent colors** , which we had heard of [last year][5]. Back then, I had thought that this would land just in time for the [GNOME 45][6] release, but, that never happened.

Even Ubuntu has featured this since the 22.04 LTS release, it was surprising to see that GNOME didn't have such functionality.

![Source: Alice Mikhaylenko][7]

Luckily, after lots of fixing, tweaking, and sharing of mockups like this☝️ We finally have what many users were wishing for.

You can take a look at the original [merge request][8] (MR) by Alice Mikhaylenko ( _formerly known as Alexander Mikhaylenko_ ) for learning more about this change.

Compared to that, [the MR][9] for **adding Wayland DRM lease protocol support** is newer at just a month old, but, the issue [has existed][10] for more than 3 years ago now.

![][11]

Fortunately, it didn't take much time to close the MR, which has been successfully merged into the main branch for GNOME.

What this makes possible is **support for VR devices when using a Wayland session** , [Charlie Le][12] confirmed that when they tested this patch with their [HTC Vive][13] on a Fedora GNOME installation. They confirmed that the Monado OpenXR runtime worked as expected, and even a few VR games.

This upgrade has also made way for **supporting GPU hot-unplugs**. You can learn more about the protocol on [Wayland Explorer][14].

After reading all that, a question arises; **When will we get to see these in action?**

Well, these changes are available as patches on the [GitLab][15] repo. Those who know their way around can try testing these out.

For the rest of us, **the upcoming GNOME 47 release is expected to feature these improvements** , which, according to the GNOME [release schedule][16], is planned to be introduced on 14 September 2024.

_💬 What do you think of this move? Better late than never? Add your thoughts below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/gnome-accent-color-vr/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/what-is-desktop-environment/
[4]: https://news.itsfoss.com/content/images/2024/06/GNOME-Accent_VR_c.png
[5]: https://news.itsfoss.com/gnome-accent-colors/
[6]: https://news.itsfoss.com/gnome-45-release/
[7]: https://news.itsfoss.com/content/images/2024/06/GNOME-Accent_VR_a.png
[8]: https://gitlab.gnome.org/GNOME/gnome-shell/-/merge_requests/2715
[9]: https://gitlab.gnome.org/GNOME/mutter/-/merge_requests/3746
[10]: https://gitlab.gnome.org/GNOME/mutter/-/issues/1743
[11]: https://news.itsfoss.com/content/images/2024/06/GNOME-Accent_VR_b-1.png
[12]: https://gitlab.gnome.org/CharlieQLe
[13]: https://www.vive.com/
[14]: https://wayland.app/protocols/drm-lease-v1
[15]: https://gitlab.gnome.org/GNOME
[16]: https://release.gnome.org/calendar/
