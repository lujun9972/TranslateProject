[#]: subject: "Announcing Fedora Linux 43 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-43-beta/"
[#]: author: "Aoife Moloney https://fedoramagazine.org/author/amoloney/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 43 Beta
======

![][1]

On Tuesday, 16 September 2025, it is our pleasure to announce the availability of Fedora Linux 43 beta! This release comes packed with the latest version upgrades of existing features, plus a few new ones too. As with every beta release, this is your opportunity to test out the upcoming Fedora Linux release and give some feedback to help us fine tune F43 final. We hope you enjoy this latest version of Fedora!

### How to get the beta release

You can download F43 beta, or our pre-release edition versions, from any of the following places:

  * [Fedora Workstation 43 Beta][2]
  * [Fedora KDE Plasma Desktop 43 Beta][3]
  * [Fedora Server 43 Beta][4]
  * [Fedora IoT 43 Beta][5]
  * [Fedora Cloud 43 Beta][6]



The Fedora CoreOS “next” stream moves to the beta release one week later, but content for F43 is still available from their current [branched][7] stream to enjoy now.

You can also update an existing system to the beta using [DNF system-upgrade][8].

The F43 beta release content is also available for Fedora [Spins][9] and [Labs][10], with the exception of the following:

  * Mate – not currently available on any architectures with F43 content
  * i3 – not currently available on aarch64 only with F43 content



### F43 Beta highlights

#### **Installer and desktop Improvements**

**Anaconda WebUI for Fedora Spins by default:** This creates a consistent and modern installation experience across all Fedora desktop variants. It brings us closer to eventually replacing the older GTK installer. This ensures all Fedora users can benefit from the same polished and user-friendly interface.

**Switch Anaconda installer to DNF5:** This change provides better support and debugging for package-based applications within Anaconda. It is a bigger step towards the eventual deprecation or removal of DNF4, which is now in maintenance mode.

**Enable auto-updates by default in Fedora Kinoite:** This change ensures that users are consistently running a system with the latest bug fixes and features after a simple reboot. Updates are applied automatically in the background.

**Set Default Monospace Fallback Font:** This change ensures that when a specified monospace font is missing, a consistent fallback font is used. Font selection also remains stable and predictable, even when the user installs new font packages. No jarring font changes should occur as appeared in previous versions.

#### **System enhancements**

**GNU Toolchain Update:** The updates to the GNU Toolchain ensures Fedora stays current with the latest features, improvements, and bug and security fixes from the upstream gcc, glibc, binutils, and gdb projects. They guarantees a working system compiler, assembler, static and dynamic linker, core language runtimes, and debugger.

**Package-specific RPM Macros For Build Flags:** This change provides a consistent and standard way for packages to add to the default list of compiler flags. It also offers a cleaner and simpler method for package maintainers to make per-package adjustments to build flags. This avoids the need to manually edit and re-export environmental variables, and prevents potential issues that could arise from the old manual method. It ensures the consistent applications of flag adjustments.

**Build Fedora CoreOS using Containerfile:** This change brings the FCOS build process under a standard container image build, moving away from the custom tool, CoreOS Assembler. It also means that anyone with Podman installed can build FCOS. This simplifies the process for both individual users and automated pipelines.

#### **Upgrades and removals**

**Deprecate The Gold Linker:** Deprecate the binutils-gold subpackage. This change simplifies the developer experience by reducing the number of available linkers from four to three. It streamlines choices for projects, and moves towards safeguarding the project against potential issues from “bitrot” where a package’s quality can decline and become unbuildable or insecure over time.

**Retire python-nose:** The python-nose package will be removed in F43. This prevents the creation of new packages with a dependency on an unmaintained test runner. Developers are encouraged to migrate to actively maintained testing frameworks such as python3-pytest or python3-nose2.

**Retire gtk3-rs, gtk-rs-core v0.18, and gtk4-rs v0.7:** This change prevents Fedora from continuing to depend on old, unmaintained versions of these bindings. It also prevents shipping obsolete software and fewer unmaintained versions of packages.

**Python 3.14:** Updating the Python stack in F43. This means that by building Fedora packages against an in-development version, critical bugs can be identified and reported before the final 3.14.0 release. This helps the entire Python ecosystem. Developers also gain access to the latest features in this release. More information is available at <https://docs.python.org/3.14/whatsnew/3.14.html>.

**Golang 1.25:** This change provides Fedora Linux 43 Beta with the latest new features in Go. These include that go build -asan now defaults to leak detection at program exit, the go doc -http option starts a documentation server, and subdirectories of a repository can now be used as a module root. Since Fedora will keep as close to upstream as possible, this means we will continue to provide a reliable development platform for the Go language and projects written in it.

**Idris 2:** Users gain access to new features in Idris 2. These include Quantitative Type Theory (QTT), which enables type-safe concurrent programming and fine-grained control over resource usage. It also has a new core language, a more minimal prelude library, and a new target to compile to, Chez Scheme.

### More information

Details and more information on the many great changes landing in Fedora Linux 43 are available on the [Change Set][11] page.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-43-beta/

作者：[Aoife Moloney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amoloney/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/09/fl43b-816x345.jpg
[2]: https://fedoraproject.org/workstation/download/?beta
[3]: https://fedoraproject.org/kde/download/?beta
[4]: https://fedoraproject.org/server/download/?beta
[5]: https://fedoraproject.org/iot/download/?beta
[6]: https://fedoraproject.org/cloud/download/?beta
[7]: https://builds.coreos.fedoraproject.org/browser?stream=branched&arch=x86_64
[8]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[9]: https://fedoraproject.org/spins/download?beta
[10]: https://fedoraproject.org/labs?beta
[11]: https://fedoraproject.org/wiki/Releases/43/ChangeSet
