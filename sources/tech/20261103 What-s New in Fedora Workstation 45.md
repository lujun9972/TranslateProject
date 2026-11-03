[#]: subject: "What’s New in Fedora Workstation 45"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-workstation-45/"
[#]: author: "Aoife Moloney https://fedoramagazine.org/author/amoloney/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s New in Fedora Workstation 45
======

![][1]

Fedora Workstation features the latest six months of meticulous polish, under-the-hood responsiveness, and security hardening for F45, based on [GNOME 51][2]. Whether you are multitasking across monitors, managng daily appointments, or organizing large sets of files, GNOME 51 brings thoughtful refinements to your daily workflow on Fedora Workstation.

### [][3] Silky-Smooth Responsiveness: Reworked Frame Scheduling

One standout improvement in GNOME 51 is a reworked frame scheduling and frame delivery system in Mutter. Animations, window snapping, and desktop transitions now hold a rock-steady frame rate even when the CPU and GPU are under heavy compile or gaming loads.

In tandem with this, GNOME streamlined its graphics pipeline by retiring legacy NVIDIA proprietary interfaces in favor of the standard GBM memory management path. This makes Wayland sessions cleaner, faster, and more uniform across all hardware.

### [][4] Everyday App Polish

#### [][5] Files (Nautilus) Gets Quality-of-Life Upgrades

Files has picked up several subtle but indispensable touches:

  * **Drag-and-Drop Counter Badge:** When selecting and dragging multiple files, a small badge now shows the exact count of items you’re moving.
  * **Non-Blocking Operations:** Large or slow directory reloads no longer freeze the interface, resulting in a snappier file management experience.
  * **Notification Grouping:** Grouping status and operation notifications together now keeps your notification tray tidy.



#### [][6] Calendar Rebuilt for Speed

Calendar feels faster than ever. The entire view-rendering engine was overhauled under the hood. This dramatically cut down the lag when scrolling through dense schedules in **Month View**. Reorganization within the event editor now presents a cleaner Notes section and native recognition of modern video conference links.

#### [][7] Revamped File Previewer

The quick-look File Previewer received a top-to-bottom redesign built on modern **GTK 4 and libadwaita**. It now seamlessly matches your desktop theme, respects Dark Style, handles fractional display scaling crisper than before, and properly previews high-resolution images at their actual native size.

### [][8] Deeper Security: Next-Generation Secret Storage with

### oo7

Security underpins everything in Fedora Workstation. GNOME 51 introduces **oo7** , a modern Secret Service provider written from scratch to safely store application passwords, API tokens, and credentials.

Fedora Workstation is replacing legacy keyring daemons with a compartmentalized, sandboxed service. This provides even stronger defense against rogue applications attempting to peek at cached user credentials.

### [][9] Accessibility and Navigation Upgrades

  * **Keyboard-Driven Screenshots:** You can now adjust screenshot selection boxes entirely with your arrow keys ( Alt to move the selection, Shift / Ctrl for coarse/fine resizing, and R to reset).
  * **Extended Reduced Motion:** Toggling the **Reduced Motion** accessibility option now softens animations across more core widgets and Shell elements than ever before.
  * **Reorganized Settings:** The **About** (System Details) panel now includes a direct button to view the release notes for your running GNOME version, alongside a revamped fingerprint enrollment flow.



### [][10] Upgrade or Try Fedora Workstation

If you’re already running Fedora, upgrading through **GNOME Software** or via the terminal with

dnf system-upgrade

will bring you right into GNOME 51. For clean installs, check out the Fedora Workstation live media at [getfedora.org][11].

Share your favorite new feature or thoughts on the release over at the [Fedora Discussion][12] forum!

_**Disclaimer:** Google Gemini, using the GNOME 51 release notes, assisted in the creation of this article._ _It was reviewed by humans before publishing_. _No apparent hallucinations were noted, however ,some content was not included_.

_Please read the[GNOME 51 release notes][2] for even more cool features that you can enjoy on Fedora Workstation as part of the F45 release._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-workstation-45/

作者：[Aoife Moloney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amoloney/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/10/new_in_fedora_workstaiion_45-816x345.jpg
[2]: https://gitlab.gnome.org/Teams/Websites/release.gnome.org/-/tree/51-staging/content/gnome-51
[3]: https://forge.fedoraproject.org/workstation/tickets/issues/525#silky-smooth-responsiveness-reworked-frame-scheduling
[4]: https://forge.fedoraproject.org/workstation/tickets/issues/525#everyday-app-polish
[5]: https://forge.fedoraproject.org/workstation/tickets/issues/525#files-nautilus-gets-quality-of-life-upgrades
[6]: https://forge.fedoraproject.org/workstation/tickets/issues/525#calendar-rebuilt-for-speed
[7]: https://forge.fedoraproject.org/workstation/tickets/issues/525#revamped-file-previewer
[8]: https://forge.fedoraproject.org/workstation/tickets/issues/525#deeper-security-next-generation-secret-storage-with-oo7
[9]: https://forge.fedoraproject.org/workstation/tickets/issues/525#accessibility-and-navigation-upgrades
[10]: https://forge.fedoraproject.org/workstation/tickets/issues/525#upgrade-or-try-fedora-workstation
[11]: https://getfedora.org
[12]: https://discussion.fedoraproject.org
