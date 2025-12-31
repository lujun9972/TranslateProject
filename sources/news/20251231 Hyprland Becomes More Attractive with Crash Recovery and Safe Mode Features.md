[#]: subject: "Hyprland Becomes More Attractive with Crash Recovery and Safe Mode Features"
[#]: via: "https://itsfoss.com/news/hyprland-0-53-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Hyprland Becomes More Attractive with Crash Recovery and Safe Mode Features
======

[![Warp Terminal][1]][2]

[Hyprland][3] is a dynamic tiling Wayland compositor known for its eye candy and extensive customization options. It is particularly popular among Linux users who prefer keyboard-driven workflows and want a visually appealing desktop without the added complexity of traditional desktop environments.

_If you are new to Hyprland, then you might want to check out our guide on_ [_getting started with Hyprland_][4] _!_

Anyhow, **a new point release of Hyprland has arrived** , bringing significant changes to the table. The [0.53 release][5] introduces features that improve both stability and user experience, though it also brings breaking changes that will require some behind-the-scenes work.

### Hyprland 0.53: What's There to Be Hyped About?

__This is one of the easiest ways to get Hyprland, BTW.__

The most significant change in this release is **the complete overhaul of the _windowrule_ syntax**. All existing _windowrules_ will need to be rewritten using the new syntax. The developers have updated [the wiki documentation][6] to help users migrate their configurations.

Another breaking change involves the fullscreen behavior setting. The `misc:new_window_takes_over_fs` option now replaces both `misc:new_window_takes_over_fullscreen` and `master:inherit_fullscreen`. Users will need to update their configurations accordingly.

**But it's not all breaking changes** ; there are many new additions too. First-time users will be greeted by a **welcome app** that introduces Hyprland's features and setup. This requires the [hyprland-guiutils][7] package to be installed, which developers recommend as a hard dependency.

[Hyprpaper][8] brings its own set of changes. The wallpaper manager has been migrated to [Hyprtoolkit][9] and [Hyprwire][10], changing its [IPC][11] protocol. The configuration syntax has been simplified, but existing configs will break and [need to be updated][12].

There's also **a new launcher script called start-hyprland**. This replaces the previous method of launching Hyprland directly. **The wrapper provides crash recovery and a safe mode, making it easier to recover from configuration errors or crashes.**

We wrap this up with some other changes like a universal submap bind flag for more flexible keybinding configurations, localization frameworks for GUI elements making Hyprland more accessible to non-English speakers, and the ability to blur groupbars.

You can go through the changelog for this release on [GitHub][13].

'Tis the season for gifting. If you think It's FOSS is doing a great work, please support us by opting for a Plus membership. ****You also get 5 eBooks on Linux, Docker and Bash scripting****.

Our lifetime membership option is available for $89 (instead of $149). This special price is applicable until 31st December only.

[Lifetime Membership at $89 (instead of $149)][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/hyprland-0-53-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://hypr.land/
[4]: https://itsfoss.com/hyprland/
[5]: https://hypr.land/news/update53/
[6]: https://wiki.hypr.land/Configuring/Window-Rules/
[7]: https://github.com/hyprwm/hyprland-guiutils
[8]: https://github.com/hyprwm/hyprpaper
[9]: https://github.com/hyprwm/hyprtoolkit
[10]: https://github.com/hyprwm/hyprwire
[11]: https://en.wikipedia.org/wiki/Inter-process_communication
[12]: https://wiki.hypr.land/Hypr-Ecosystem/hyprpaper/
[13]: https://github.com/hyprwm/Hyprland/releases/tag/v0.53.0
[14]: https://buy.stripe.com/fZeaI16cKgEfcfK3cc
