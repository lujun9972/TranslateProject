[#]: subject: "Announcing Fedora Linux 44 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-44-beta/"
[#]: author: "Jef Spaleta https://fedoramagazine.org/author/jspaleta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 44 Beta
======

![][1]

Madeline Peck, Justin Wheeler © CC BY-SA 4.0

On Tuesday, 10 March 2026, it is our pleasure to announce the availability of Fedora Linux 44 Beta! As with [every beta release][2], this is your opportunity to contribute by testing out the upcoming Fedora Linux 44 Beta release. Testing the beta release is a vital way you can contribute to the Fedora Project. Your testing is invaluable feedback that helps us refine what the final F44 experience will be for all users.

We hope you enjoy this latest beta version of Fedora!

### How to get the Fedora Linux 44 Beta release

You can download Fedora Linux 44 Beta, or our pre-release edition versions, from any of the following places:

  * [Fedora Workstation 44 Beta][3]
  * [Fedora KDE Plasma Desktop 44 Beta][4]
  * [Fedora Server 44 Beta][5]
  * [Fedora IoT 44 Beta][6]
  * [Fedora Cloud 44 Beta][7]



The Fedora CoreOS “next” stream moves to the beta release one week later. Content for F44, however, is still available from their current [branched][8] stream to enjoy now.

You can also update an existing system to the beta using [DNF system-upgrade][9].

The Fedora Linux 44 Beta release content may also be available for Fedora [Spins][10] and [Labs][11].

### Fedora Linux 44 Beta highlights

Like every Beta release, the Fedora Linux 44 Beta release is packed with changes. The following are highlights from the full set of [changes][12] for F44. They are ready for you to test drive in the Fedora Linux 44 Beta.

#### **Installer and desktop Improvements**

**Goodbye Anaconda Created Default Network Profiles:** This change impacts how Anaconda populates network device profiles. Only those devices configured during installation (by boot options, kickstart or interactively in UI) become part of the final system install. This behavior change addresses some long standing issues caused by populating network profiles for all network devices. These made it difficult to correctly reconfigure devices post-install.

**Unified KDE Out of the Box Experience:** This change introduces the post-install Plasma Setup application for all [Fedora KDE][13] variants. In the variants making use of this new setup application, the Anaconda configuration will be adjusted to disable redundant configuration stages that duplicate the functionality exposed in the setup application.

**KDE Plasma Login Manager:** This change introduced the Plasma Login Manager (PLM) for [Fedora KDE][13] variants instead of SDDM for the default login manager.

**Reworked Games Lab:** This change modernizes the Games Lab deliverable by leveraging the latest technologies. This offers a high quality gaming and game development experience. It includes a change from Xfce to [KDE Plasma][13] to take advantage of the latest and greatest Wayland stack for gaming.

**Budgie 10.10:** Budgie 10.10 is the latest release of Budgie Desktop. Budgie 10.10 migrates from X11 to Wayland. This ensures a viable long-term user experience for Fedora Budgie users and lays groundwork for the next major Budgie release.

#### LiveCD Improvements

**Automatic DTB selection for aarch64 EFI systems:** This change intends to make the aarch64 Fedora Live ISO images work out of the box on Windows on ARM (WoA) laptops. This will automatically select the right DTB at boot.

**Modernize Live Media:** This change modernizes the live media experience by switching to the “new” live environment setup scripts provided by livesys-scripts and leverage new functionality in dracut to enable support for automatically enabling persistent overlays when flashed to USB sticks.

#### System Enhancements

**GNU Toolchain Update:** The updates to the GNU Toolchain ensure Fedora stays current with the latest features, improvements, and bug and security fixes from the upstream gcc, glibc, binutils, and gdb projects. They guarantee a working system compiler, assembler, static and dynamic linker, core language runtimes, and debugger.

**Reproducible Package Builds:** Over the last few releases, we changed our build infrastructure to make package builds reproducible. This is enough to reach 90%. The remaining issues need to be fixed in individual packages. With this change, all package builds are expected to be reproducible in the F44 final release. Bugs will be filed against packages when an irreproducibility is detected. The goal is to have no fewer than 99% of package builds reproducible.

**Packit as a dist-git CI:** This change continues down the path of modernizing the Fedora CI experience by moving forward with the final phase of the plan to integrate Packit as the default CI for Fedora dist-git.

**Remove Python Mock Usage:** python-mock was deprecated with Fedora 34. However, it is still in use in many packages. We plan to go through the remaining usages and clean them up, with the goal of retiring python-mock from Fedora.

**Adoption of new R Packaging Guidelines:** This change introduces new rpm macros to help standardize and automate common R language packaging tasks resulting in a simplification of the rpm spec files.

**Introduction of Nix Developer Tool:** This change adds the nix package manager developer tool to Fedora.

**Hardlink identical files in packages by default:** With this change, all fedora packages will automatically hardlink files under /usr by default as a post install action. The mechanism introduced in this change is designed specifically to address reproducibility validation race conditions found in use by traditional hardlinking approaches.

#### Fedora Linux 44 Beta upgrades and removals

**Golang 1.26:** Fedora users will receive the most current and recent Go release. Being close to upstream allows us to avoid security issues and provide more updated features. Consequently, Fedora will provide a reliable development platform for the Go language and projects written in it.

**MariaDB 11.8 as Distribution Default Version:** The distribution default for MariaDB packaging will switch to 11.8. Multiple versions of the MariaDB packages will continue to be available. This change only impact which of the versioned packages presents itself as the unversioned “default”

**IBus 1.5.34:** Fedora users will benefit from better support of Wayland and Emoji features.

**Django 6.x:** Fedora Users can make use of the latest Django version; users who use Django add-ons that are not ready for 6.0 yet should be able to switch it out for python3-django5

**TagLib 2:** This change puts Fedora on the latest supported version, and it will benefit from improvements in future minor releases with a simple update.

**Helm 4:** Helm 4 has been released upstream with intentional backwards-incompatible changes relative to Helm 3. To ensure a smooth transition for Fedora, this Change introduces Helm 4 as the default helm package, while providing a parallel-installable helm3 package for users and tooling that still rely on Helm 3.

**Ansible 13:** Update from Ansible 11 and Ansible Core 2.18 to Ansible 13 and Ansible Core 2.20. This includes major robustness and security fixes to the templating engine which might break existing playbooks that had incorrect behavior. This was silently ignored in previous releases.

**TeXLive 2025:** With this change, we update to the latest version of TeXLive (2025). We also move to a modularized packaging system, which splits the “texlive” SPEC into a set of collection and scheme packages. This reflects the categorization that TeXLive upstream defines. Each collection package will package the immediate component dependencies as subpackages.

**Drop QEMU 32-bit Host Builds:** Fedora will stop building QEMU on i686 architecture. This change brings Fedora inline with the QEMU upstream project decision to deprecate support for 32-bit host builds. Upstream intends to start removing 32-bit host build support code in a future release and will assume 64-bit atomic ops in all builds.

**Drop FUSE 2 libraries in Atomic Desktops:** Remove FUSE 2 binaries and libraries from all Atomic Desktops

**Drop compatibility for pkla polkit rules in Atomic Desktops:** Remove support for deprecated pkla polkit rules from all Fedora Atomic Desktops

### More information about Fedora Linux 44 Beta

Details and more information on the many great changes landing in Fedora Linux 44 are available on the [Change Set][12] page.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-44-beta/

作者：[Jef Spaleta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jspaleta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/03/announcing-fedora-linux-44-beta-1890x799-1-816x345.jpg
[2]: https://fedoramagazine.org/tag/beta/
[3]: https://fedoraproject.org/workstation/download/?beta
[4]: https://fedoraproject.org/kde/download/?beta
[5]: https://fedoraproject.org/server/download/?beta
[6]: https://fedoraproject.org/iot/download/?beta
[7]: https://fedoraproject.org/cloud/download/?beta
[8]: https://builds.coreos.fedoraproject.org/browser?stream=branched&arch=x86_64
[9]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[10]: https://fedoraproject.org/spins?beta
[11]: https://fedoraproject.org/labs?beta
[12]: https://fedoraproject.org/wiki/Releases/44/ChangeSet
[13]: https://fedoramagazine.org/tag/kde/
