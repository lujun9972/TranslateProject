[#]: subject: "An X11 Thing! Your Favorite Middle-Click Paste is Likely to be Disabled in Future GNOME Releases"
[#]: via: "https://itsfoss.com/news/gnome-firefox-middle-click-paste-removal/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

An X11 Thing! Your Favorite Middle-Click Paste is Likely to be Disabled in Future GNOME Releases
======

[![Warp Terminal][1]][2]

Jordan Petridis, a GNOME developer, [recently submitted proposals][3] to both GNOME and Mozilla Firefox. Both aim to disable middle-click paste functionality by default and were sent in within days of each other.

For GNOME, he opened [merge request #119][4] on the _gsettings-desktop-schemas_ repository, saying that:

> This is an X11ism, originally an xsetting [1][5] which frequently results is in unexpected behavior when people pressing the middle mouse button.

> It's commonly used for other actions or more often getting clicked by accident, and dumping your entire clipboard while having no indication that this will happen is nothing short of a dumpster fire.

He ended this with a bold sign-off, " _ **Goodbye X11**_."

The Firefox proposal was posted on [Phabricator][6], outlining that the feature is little known and confuses users. Most of the time, people click the middle mouse button accidentally, having the clipboard dump content without any warning.

Jordan further added that **the feature isn't discoverable at all** , and that [the Freedesktop wiki][7] calls the `PRIMARY` selection an " _easter egg_ " for expert users and suggests that regular users can just ignore it.

### My Two Cents

I actually welcome this move. Being the clumsy Penguin I am, I have accidentally hit the middle mouse button more times than I can count. This usually happens to me when I am quickly switching between browser tabs and the file manager.

Having random clipboard content suddenly appear is one thing. But imagine pasting sensitive material like passwords while livestreaming or sharing your screen. Not everyone watching has good intentions.

**But there's another side to this**. Power users who have relied on middle-click paste for years won't be happy. The responses to these merge requests show many people still use this functionality.

If these proposals get accepted, you can still re-enable the feature. For GNOME users, they can run this command:

```

    gsettings set org.gnome.desktop.interface gtk-enable-primary-paste true

```

Alternatively, you can use [GNOME Tweaks][8] to toggle it through a familiar graphical interface if you prefer that.

The final decisions rest with GNOME's design team and Mozilla's reviewers. **Neither project has approved the changes yet**. Until then, middle-click paste works exactly as it always has.

![][9]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/gnome-firefox-middle-click-paste-removal/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://mastodon.social/@alatiera/115832011216789958
[4]: https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/merge_requests/119
[5]: https://bugzilla.gnome.org/show_bug.cgi?id=775844
[6]: https://phabricator.services.mozilla.com/D277804
[7]: https://www.freedesktop.org/wiki/Specifications/ClipboardsWiki/#:~:text=The%20correct%20behavior%20can%20be%20summarized%20as%20follows%3A%20CLIPBOARD%20works%20just%20like%20the%20clipboard%20on%20Mac%20or%20Windows%3B%20it%20only%20changes%20on%20explicit%20cut/copy.%20PRIMARY%20is%20an%20%22easter%20egg%22%20for%20expert%20users%2C%20regular%20users%20can%20just%20ignore%20it%3B%20it%27s%20normally%20pastable%20only%20via%20middle%2Dmouse%2Dclick.
[8]: https://itsfoss.com/gnome-tweak-tool/
[9]: https://itsfoss.com/content/images/icon/android-chrome-512x512-190.png
