[#]: subject: "Hey Fedora! Listen to This Developer and Make Managing Shell Extensions Better For All of Us"
[#]: via: "https://itsfoss.com/news/fedora-gnome-extension-manager-proposal/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Hey Fedora! Listen to This Developer and Make Managing Shell Extensions Better For All of Us
======

[![Warp Terminal][1]][2]

A new issue has been raised on Fedora's [issue tracker][3] by a first-time contributor, who calls upon the [Fedora Workstation Working Group][4] to endorse **Extension Manager as the official tool for managing GNOME Shell extensions**. She also proposes shipping it as a Flatpak by default on [Fedora Silverblue][5].

This is not a new idea, but a proposition that is looking to revive an older one and adds another ask into it.

[Purva Sharma][6], the person behind this proposal, found [an older issue][7] from January 2023 that proposed shipping Extension Manager by default on Fedora Silverblue. It had been sitting dormant for about two years now.

In fact, my teammate Abhishek made similar arguments in a recent video:

[Subscribe to It's FOSS YouTube Channel][8]

If you are a Fedora Workstation user, then you know [how useful Shell Extensions are][9]. These add functionality to the [GNOME][10] desktop, ranging from utilities like weather widgets to fully-fledged system monitors.

Sadly, getting them installed is a bit of work that could be made simpler.

### Can't We Have a Better Way to Manage Extensions?

![Extension Manager on Fedora 43!][11]

The official way to install [GNOME extensions][12] requires multiple steps. You need to install a browser extension for either [Firefox][13] or [Chrome][14], and then you install [a native connector][15] called `gnome-browser-connector` on your system.

Only after going through the above can you start installing extensions. In 2026, **the process feels very out-of-place and archaic** seeing how GNOME has matured as a [desktop environment][16].

[Extension Manager][17] offers a simpler approach. It is a standalone application that handles everything. You can search for extensions directly in the app, view extension ratings and comments, compatibility information for your GNOME version, and it even handles updates for any installed extensions.

The project itself **is actively developed by a dedicated group of open source contributors** and is released under the [GPL 3.0][18] license. This makes it in line with Fedora's [open source requirements][19].

### Am I Being Too Optimistic?

I might be biased as I use Extension Manager on my Fedora Workstation daily driver, but doesn't it seem like a logical choice? People don't need to jump through hoops to customize their desktop to their own liking now, do they?

The browser method works but adds unnecessary complexity. Extension Manager removes that hurdle. **For Fedora Silverblue specifically, having it as a default Flatpak makes sense**. Silverblue aims for a minimal base system with apps as Flatpaks after all.

Apart from that, I like how this first-time contributor has taken the opportunity to propose something that could potentially improve the experience of many Fedora users. Finding dormant issues and reviving them like this shows initiative.

**The decision now sits with the Fedora Workstation Working Group**. They can evaluate the proposal and decide whether to move it forward. If they endorse it, the next step would be creating a formal change proposal. That change proposal would then go to [FESCo][20] for voting.

Regardless of whether Fedora acts on this or not, [Extension Manager][21] is available now. You can install it via [Flathub][22] or your distribution's package manager. It works on any Linux distribution running GNOME.

Support independent Linux journalism! If you think we are doing a good job at helping people use Linux on their personal computers, support us by opting for Plus membership.

Here's what you get with It's FOSS Plus membership:

✅ 5 Free eBooks on Linux, Docker and Bash
✅ Ad-free reading experience
✅ Badges in the comment section and forum
✅ Support creation of educational Linux materials

[Join It's FOSS Plus][23]

* * *

**Suggested Read 📖:** [_This Handy App Helps You Install and Manage GNOME Shell Extensions_][17]

![][24]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/fedora-gnome-extension-manager-proposal/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://pagure.io/fedora-workstation/issue/499
[4]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[5]: https://fedoraproject.org/atomic-desktops/silverblue/
[6]: https://github.com/purvas2005
[7]: https://github.com/fedora-silverblue/issue-tracker/issues/399
[8]: https://www.youtube.com/@itsfoss
[9]: https://itsfoss.com/gnome-shell-extensions/
[10]: https://www.gnome.org/
[11]: https://itsfoss.com/content/images/2026/01/extension-manager-on-fedora-workstation-43.png
[12]: https://extensions.gnome.org/
[13]: https://addons.mozilla.org/firefox/addon/gnome-shell-integration/
[14]: https://chromewebstore.google.com/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep
[15]: https://wiki.gnome.org/Projects/GnomeShellIntegration/Installation
[16]: https://itsfoss.com/what-is-desktop-environment/
[17]: https://itsfoss.com/extension-manager/
[18]: https://www.gnu.org/licenses/gpl-3.0.en.html
[19]: https://docs.fedoraproject.org/en-US/legal/allowed-licenses/
[20]: https://docs.fedoraproject.org/en-US/fesco/
[21]: https://github.com/mjakeman/extension-manager
[22]: https://flathub.org/en/apps/com.mattjakeman.ExtensionManager
[23]: https://itsfoss.com/membership/
[24]: https://itsfoss.com/content/images/icon/android-chrome-512x512-207.png
