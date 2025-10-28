[#]: subject: "What’s New in Fedora Workstation 43"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-workstation-43/"
[#]: author: "Gregory Bartholomew https://fedoramagazine.org/author/glb/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s New in Fedora Workstation 43
======

![][1]

Below are a few noteworthy changes in the latest release of Fedora Workstation that we think you will love. Upgrade today from [the official website][2], or upgrade your existing install using GNOME Software or through the terminal with [dnf system-upgrade][3].

### GNOME 49

Fedora Linux 43 Workstation also ships with the brand-new GNOME 49 release, bringing a host of refinements to your desktop. This update introduces significant enhancements for multiple display setups, an improved and streamlined workflow for taking screenshots and screen recordings, and a new “Focus Mode” to help you minimize distractions. Under the hood, resource-smart background throttling improves performance and battery life, while the Settings app has been polished with a refined UI. These are just the highlights. Check out [the official GNOME 49 release notes][4] to find more information about all the new features.

### Wayland-only GNOME

One significant change we want to forewarn you about is that Fedora Linux 43 is [removing the GNOME X11 packages][5] from the Fedora repositories. All users of the GNOME X11 session will be migrated to the GNOME Wayland session with the upgrade to Fedora Workstation 43.

The transition to the GNOME Wayland session in Fedora Workstation 43 has been in the works for nearly a decade. There have been several prior steps toward this goal, such as the work in Fedora Linux 41 to remove legacy X11 dependencies from core media components.

Wayland has been the default GNOME session on Fedora Workstation for many years, but this release completes the change. The legacy gnome-session-xsession packages have been removed from the Fedora Linux 43 repositories.

This change will unlock a new level of performance and hardware compatibility. You’ll immediately notice smoother, cleaner visuals thanks to triple buffering, which dramatically reduces screen tearing. This change also improves support for a range of hardware, including enhanced drivers for Intel Xe graphics and improvements for systems using NVIDIA Optimus and Hybrid Mode.

### A new default video player — Showtime

The default video player has been changed from Totem to Showtime. Showtime is built on the newer GTK 4 and Libadwaita libraries.

### Use COLR for Noto Color Emoji

The Noto Color Emoji fonts have released some new files with the COLRv1 format. The COLRv1 format is a color scalable font compared with the previous color bitmap fonts. This new scalable font format should have better or similar rendering results compared to the old bitmap font format. See the [change notes][6] for more details.

### Peas 2.0

If you are an app developer, you might be interested in the upgrade to [Peas 2][7]. Peas is a gobject-based plugins engine that is used by several GNOME applications.

### Wrap-up

Be sure to check out [the Fedora Linux 43 Change Set wiki][8] for even more details about all the features and changes that went into Fedora Linux 43. Use [the Fedora Discussion forum][9] or [Fedora’s Matrix chat server][10] if you want to converse with the Fedora community about this new release!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-workstation-43/

作者：[Gregory Bartholomew][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/glb/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/10/whats-new-workstation-43-816x345.jpg
[2]: https://fedoraproject.org/workstation/download
[3]: https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/
[4]: https://release.gnome.org/49/
[5]: https://fedoraproject.org/wiki/Changes/WaylandOnlyGNOME
[6]: https://fedoraproject.org/wiki/Changes/Use_COLR_for_Noto_Color_Emoji
[7]: https://gnome.pages.gitlab.gnome.org/libpeas/libpeas-2/migrating-1to2.html
[8]: https://fedoraproject.org/wiki/Releases/43/ChangeSet
[9]: https://discussion.fedoraproject.org/
[10]: https://chat.fedoraproject.org/#/room/#fedora:fedoraproject.org
