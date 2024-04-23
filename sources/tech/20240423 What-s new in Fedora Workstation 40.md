[#]: subject: "What’s new in Fedora Workstation 40"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-workstation-40/"
[#]: author: "Roseline Bassey https://fedoramagazine.org/author/roseline-bassey/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new in Fedora Workstation 40
======

![][1]

Image by Consolation Obazee

Fedora Workstation, the flagship open source Linux desktop OS from the Fedora Project, has reached a new milestone with the release of Fedora Workstation 40. This release has been made possible due to the contributions of our global community, including your contributions! Fedora Workstation 40 comes packed with new features and performance enhancements that promise a smoother and more responsive computing experience. Read on to learn about the latest features and improvements in the sections below. You can download Fedora Workstation 40 from the [Fedora Workstation webpage][2], or upgrade your existing install within the Software app or with _[dnf system-upgrade][3]_ in your favorite terminal emulator.

### GNOME 46

Fedora Workstation 40 features GNOME 46, the latest version of the GNOME desktop environment. Key updates include a notable upgrade of the Files app, introducing new features and enhancements. Additionally, many aspects of accessibility have received improvements, ensuring a more inclusive user experience. The Settings app and other core apps have been refined for better usability. More details can be found in the [GNOME 46 release notes][4].

Many other improvements have been made throughout GNOME 46, such as:

  * Grouping of notifications by app. Now, each notification has a header. It shows the app’s name and icon. This makes it possible to see which app sent an alert. Notification now also has an expand button.


  * You can now open a new window for apps pinned to the dash by adding the _Ctrl_ modifier. For example: _Super_ + _Ctrl_ + _1_ opens a new window for the first app in the dash, complementing the existing shortcut of _Super_ + _< Number>_ that launches the app itself.


  * By default, Tap to Click is now enabled for touchpad.


  * GNOME 46 now features Remote Login option. You can remotely connect using RDP to a new dedicated desktop session when there isn’t an active session.



### Core apps

GNOME’s core applications have had significant improvements in the new version. Some of these include:

##### Settings

GNOME 46 comes with exciting updates to the Settings app, making it more user-friendly than ever. The latest version has more keyboard mnemonics which make navigation easier. It also has a sleek modern interface. The appearance settings load faster than before and with sharper previews. This new release provides more precise control of Wacom stylus pressure.

In addition to the upgrades mentioned above, the Settings app has received major improvements that are worth mentioning:

  * The Settings app has a new system panel. It groups _Region & Language_, _Date & Time_, _Remote Desktop_ , and* About* into one settings pane. This new design makes the app easier to navigate.


  * GNOME 46 has updated touchpad settings with two new options. The first, called Secondary Click, lets you choose how to perform a right-click on the touchpad: either with two fingers or by clicking in a corner. The second option allows you to keep the touchpad active while typing, which helps in some apps and games where you need to use the keyboard and touchpad at the same time.



##### Files

  * One of the notable upgrades to Files is the introduction of a new global search feature. The global search feature lets you search files across all configured locations. You can search the contents of files, filter files by type and modification date, and search multiple locations at once. Click the icon next to the file path field to activate this feature.


  * In GNOME 46, the sidebar dynamic progress section at the bottom allows you to monitor file operations more effectively with more details on their progress.


  * Switching between list and grid views in Files now happens quickly. This fixes the lag noticed in prior versions.



Other changes to the Files app include a new search field within the Files preferences. It helps find specific settings. There’s now also an option to show date and time in a consistent format, and improved network discovery. These refinements make managing files more efficient.

##### **Other core applications have also received upgrades**

  * The Software app now displays verified badges for trusted Flathub apps, ensuring software authenticity.


  * Maps app offers a new editing experience, support for dark mode, and expanded public transit routing.


  * The Extensions and Calendar apps boast modernized designs and usability improvements.


  * GNOME 46 upgrades Clocks and Contacts apps. It lets you set a timer quickly in Clocks. And, import multiple VCard files at once in Contacts.


  * The Disks app has a new I/O resource graph for monitoring disk usage.



### Performance Improvements

GNOME 46 provides substantial under-the-hood improvements for a more efficient and polished experience. Key improvements include:

  * Reduced memory usage in search.


  * Significant speed boosts in terminal apps.


  * More appealing visuals as app interfaces appear sharper, text on the screen clearer, and UI elements more defined, particularly when using fractional display scales due to GTK’s new renders.


  * Experimental support for Variable Refresh Rate (VRR) for smoother video performance. You can enable this feature with the command:
_gsettings set org.gnome.mutter experimental-features "['variable-refresh-rate']"_
Once enabled, the refresh rate can be set in the display settings.



### Under-the-hood changes in Fedora Linux 40

Fedora Linux 40 features many under-the-hood changes. Here are some notable ones:

  * IPV4 Address Conflict Detection is enabled by default in NetworkManager to address conflicts caused by duplicate IPV4 addresses in the same physical network.


  * Fedora 40 integrates PyTorch directly into its software repository. This makes it easier for users to access the open source machine learning framework for their projects. Installation is now a breeze through a single command:
_sudo dnf install python3-torch_


  * Starting with Fedora Linux 40, the term “immutable” will no longer be used to describe all rpm-ostree based variants of Fedora Linux (Silverblue, Kinoite, Sway and Budgie). Instead, they will be referred to as “Atomic” desktops with Sericea now known as Fedora Atomic Sway. This change is part of a rebranding aimed at simplifying the naming conventions for Fedora spins. [More information on this change may be found here.][5]



### Also check out…

Cool happenings throughout the Fedora Project!

Stay tuned and get ready to engage with the Fedora community at some upcoming events! In June, join us in Brno, Czechia, for the DevConf CZ conference — a gathering filled with insightful discussions, workshops, and the chance to meet fellow enthusiasts.

Then, mark your calendars for August, when our flagship contributor conference, Flock, takes place. For more details on Flock 2024, check out this [post][6].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-workstation-40/

作者：[Roseline Bassey][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/roseline-bassey/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/03/F40-image-816x345.jpg
[2]: https://fedoraproject.org/workstation/
[3]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[4]: https://release.gnome.org/46/
[5]: https://fedoramagazine.org/introducing-fedora-atomic-desktops/
[6]: https://fedoramagazine.org/flock-2024-rochester-new-york/
