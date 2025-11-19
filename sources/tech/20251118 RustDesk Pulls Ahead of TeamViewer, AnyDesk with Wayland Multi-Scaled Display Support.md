[#]: subject: "RustDesk Pulls Ahead of TeamViewer, AnyDesk with Wayland Multi-Scaled Display Support"
[#]: via: "https://itsfoss.com/news/rustdesk-multi-scaled-display-support/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RustDesk Pulls Ahead of TeamViewer, AnyDesk with Wayland Multi-Scaled Display Support
======

[RustDesk][1] has positioned itself as a compelling open source alternative to proprietary remote desktop solutions like TeamViewer and AnyDesk. Built with Rust and licensed under AGPL 3.0, it offers cross-platform support across Linux, Android, Windows, macOS, and iOS.

The project has now announced [a major update][2] for Linux users. RustDesk's latest nightly build introduces support for multiple monitors with different scaling factors on Wayland sessions, specifically targeting KDE and GNOME desktop environments.

### RustDesk Levels Up

![][3]

This update **addresses a well-known issue across the Linux desktop space** , where users running multiple monitors with different resolutions and scaling levels, such as a 4K display at 200% scaling alongside a standard 1080p monitor, often struggled with proper display handling.

The most common problem was pointer misalignment. Users would click in one location, but the input would register elsewhere on the remote machine. This made multi-monitor setups with mixed scaling practically unusable for remote work.

The developers claim that their implementation now makes them **the only remote desktop solution with this capability on Wayland**.

This puts RustDesk ahead of its commercial rivals. TeamViewer, AnyDesk, and Splashtop have been relatively slow to address Wayland-specific challenges, particularly around complex multi-monitor configurations.

### Get RustDesk

This improvement is currently available in RustDesk's nightly builds on [GitHub][4]. These pre-release versions get updated daily with the latest code and features for early testing.

Once testing completes, the multi-scaled display support will roll out to the stable version available on the [official website][1].

We [tested RustDesk back in 2024][5] and found it impressive even then. This latest update only solidifies its position as a serious TeamViewer alternative.

[RustDesk][1]

**Suggested Read 📖**

![][6]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/rustdesk-multi-scaled-display-support/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://rustdesk.com/
[2]: https://www.reddit.com/r/rustdesk/comments/1ozmvg9/our_biggest_wayland_update_for_remote_desktop/
[3]: https://itsfoss.com/content/images/2025/11/rustdesk-1-4-4-nightly.png
[4]: https://github.com/rustdesk/rustdesk/releases/tag/nightly
[5]: https://itsfoss.com/news/rustdesk/
[6]: https://itsfoss.com/content/images/icon/android-chrome-512x512-24.png
