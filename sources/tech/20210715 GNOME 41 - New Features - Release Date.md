[#]: subject: (GNOME 41 – New Features & Release Date)
[#]: via: (https://www.debugpoint.com/2021/07/gnome-41/)
[#]: author: (Arindam https://www.debugpoint.com/author/admin1/)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

GNOME 41 – New Features & Release Date
======
We summarize the available information for GNOME 41 release here and
brief you about the new features, schedules.
This post includes information about ongoing development. The information may change frequently, and this page is regularly updated until the final release.

The upcoming GNOME 41 release development is in full swing. The prior [GNOME 40][1] release was a significant one with fundamental change of desktop workflow. Following that change, the GNOME 41 release plans to fix the issues uncovered since GNOME 40 taking care of all point release of 40 series. Also promised certain new features and native application updates.

Don’t bring your hope up. There is not much yet planned for this (as of writing this), so I believe it is going to be a moderate release considering the new features.

![][2]

### GNOME 41 – Top New Features

  * Probably the important item in this release is [inclusion][3] of [**libadwaita**][4] in GNOME. Libadwaita is based on the libhandy user interface library while being a GTK4 port. Libadwaita will now ship the Adwaita stylesheet along with its variants. This successor of libhandy will define the UI/UX experience of GNOME GTK4 apps in coming days.


  * So, for extension developers, it would easier to port to GTK4 with libadwaita library. And eventually all extensions needs to link to libadwaita for better experience, theming.


  * GNOME **Software** gets a makeover in GNOME 41. The new design brings a left sidebar with categories (much like Settings dialog). No more categories in the homepage as per earlier design. The left sidebar have the software categories such as Work, Play, Socialize etc. And you get to choose and install them.



![GNOME Software 41 Responsive Animation][5]

  * The top carousal for featured apps in the home page is more slick with rounded corners and wider featured image. The left section also contains separate menu entries for installed apps and apps that require updates.


  * The Software app is responsive and hides the left bar intelligently when resized.


  * The app grid page sees an improvement when used a pointing device such as mouse rather than touch. The grid page start dragging immediately when used a pointing device.


  * You can now use long swipes in workspace animation.


  * Nautilus file manager did small improvements as well. Code changes are done in properties window to prevent accidental change in file name. And the file not found dialog now shows the file name.


  * GNOME Calculator is completely overhauled. It now features bright color buttons for equal sign and removing the numbers. The UI menu also changed to show the calculator modes from the hamburger menu



![GNOME Calculator – old and new side by side \(advanced mode\)][6]

![GNOME Calculator – old and new side by side \(basic mode\)][7]

### GNOME 41 – Schedule

GNOME 41 final release planned on September 22, 2021. Here’s a summary of the schedule.

Milestone | Planned date
---|---
GNOME 41.Alpha | July 10, 2021
GNOME 41.Beta | August 14, 2021
GNOME 41.RC | September 4, 2021
GNOME 41 | September 22, 2021

### Distro Availability

Looking at the timeline, I do not think that [Ubuntu 21.10 Impish Indri][8], and Fedora 35 would be able to match up their schedule with GNOME. So, Ubuntu 21.10 won’t feature for sure. But Fedora 35 still tentative which is due on Oct 26, 2021.

For Arch Linux, Manjaro and other rolling release based distributions, it should be available when released. And for Ubuntu and Fedora – folks needs to wait until 2022 for this as per my best guess.

### Closing Notes

It is normal to have a moderate release after a big one. And I believe, adding libadwaita is a big decision. Also, it is important to fix the bugs those left out after a major release – that is GNOME 40. Stability and bug free GNOME is always preferable than many new features.

I will keep this page updated with additional information when it is available.

* * *

--------------------------------------------------------------------------------

via: https://www.debugpoint.com/2021/07/gnome-41/

作者：[Arindam][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.debugpoint.com/author/admin1/
[b]: https://github.com/lujun9972
[1]: https://www.debugpoint.com/tag/gnome-40
[2]: https://www.debugpoint.com/blog/wp-content/uploads/2021/07/GNOME-41-Alpha.jpeg
[3]: https://gitlab.gnome.org/GNOME/gnome-build-meta/-/merge_requests/1198
[4]: https://gitlab.gnome.org/GNOME/libadwaita
[5]: https://www.debugpoint.com/blog/wp-content/uploads/2021/07/GNOME-Software-41-Responsive-Animation.gif
[6]: https://www.debugpoint.com/blog/wp-content/uploads/2021/07/GNOME-Calculator-old-and-new-side-by-side-advanced-mode-1024x415.jpg
[7]: https://www.debugpoint.com/blog/wp-content/uploads/2021/07/GNOME-Calculator-old-and-new-side-by-side-basic-mode-1024x415.jpg
[8]: https://www.debugpoint.com/2021/07/ubuntu-21-10/
