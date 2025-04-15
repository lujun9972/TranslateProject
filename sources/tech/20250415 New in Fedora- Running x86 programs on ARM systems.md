[#]: subject: "New in Fedora: Running x86 programs on ARM systems"
[#]: via: "https://fedoramagazine.org/new-in-fedora-running-x86-programs-on-arm-systems/"
[#]: author: "Davide CavalcaNeal Gompa https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

New in Fedora: Running x86 programs on ARM systems
======

![][1]

The newly released [Fedora KDE Plasma Desktop 42][2] introduces out-of-box support for running x86 and x86-64 programs on ARM systems. This is accomplished by leveraging the emulation stack [originally developed][3] for Fedora Asahi Remix. This work is now [integ][4][r][4][ated][4] into Fedora Linux proper. This makes it available for all ARM systems running Fedora Linux, not just Apple Silicon Macs.

### How Is This Accomplished

To make it possible to run x86 programs via emulation, we leverage several tools, each solving a specific problem:

  * [FEX][5], a fast emulator that can run x86 and x86-64 programs on ARM Linux hosts
  * [muvm][6], a tool that can run another program inside a microVM
  * [binfmt-dispatcher,][7] a simple dispatcher that can dynamically pick the best emulator to use when an x86 or x86-64 program is started



With this setup, when a non-native program is run, the kernel invokes binfmt-dispatcher via the [binfmt_misc][8] interface. The dispatcher picks the best emulator to use. This is based on the program, the system it’s running on, and its own configuration. By default, we use the FEX emulator, which provides the best compromise between performance and compatibility for most programs. FEX only support host systems running a 4k page-size kernel. Thus, when running on a system with different page-size (such as Apple Silicon Macs running [Fedora Asahi Remix 42][9], which use a 16k page-size), the dispatcher will automatically run FEX inside muvm. This will spin up a microVM with a 4k page-size kernel for compatibility.

If the user prefers to use a different emulator (such as [box64][10] or [QEMU][11]), that can be [configured][12] globally, or on a per-program basis. The dispatcher automatically installs any missing dependencies via DNF whenever a non-native program is run for the first time that requires them. This installation requires confirmation by the user.

### Library Availablity

FEX relies on an immutable filesystem containing a large set of commonly used x86-64 and x86 libraries. However, it cannot contain _every_ library, so it is possible that a program could fail to start due to missing dependencies. Should that happen, consider submitting a pull request to the [Kiwi description][13] to get it added. It is also possible to [overlay locally][14] additional dependencies, though you should consider this as experimental at this stage. In general, this feature will work best with programs that have reduced or minimal dependencies. This is common with a lot of commercial software. While it is possible to run complex FLOSS applications with a wide dependency web, we recommend just using the native ARM version whenever that’s an option. That will always provide the best performance.

### Feature Availability

This new feature is available out of the box on Fedora KDE Plasma Desktop 42. It is also available on Fedora Asahi Remix, in both the KDE Plasma and the GNOME editions. Additionally, Fedora Asahi Remix includes a [gaming emulation stack][3] based on Steam, and has [dedicated documentation][15] for this feature. On other Fedora editions, you can run $ sudo dnf install @x86-emulation to make this feature available.

It’s also worth noting that while we have specifically targeting x86 emulation on ARM hosts, the same approach could be used for other hosts and targets in the future.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/new-in-fedora-running-x86-programs-on-arm-systems/

作者：[Davide CavalcaNeal Gompa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/running_x86_on_ARM-816x345.jpg
[2]: https://fedoramagazine.org/whats-new-for-fedora-kde-plasma-desktop-42
[3]: https://asahilinux.org/2024/10/aaa-gaming-on-asahi-linux/
[4]: https://fedoraproject.org/wiki/Changes/FEX
[5]: https://fex-emu.com/
[6]: https://github.com/AsahiLinux/muvm
[7]: https://github.com/AsahiLinux/binfmt-dispatcher
[8]: https://www.kernel.org/doc/html/latest/admin-guide/binfmt-misc.html
[9]: https://fedoramagazine.org/fedora-asahi-remix-42-is-now-available/
[10]: https://box86.org/
[11]: https://www.qemu.org/
[12]: https://github.com/AsahiLinux/binfmt-dispatcher/blob/main/docs/binfmt-dispatcher.toml.example
[13]: https://pagure.io/fedora-kiwi-descriptions/blob/rawhide/f/teams/asahi.xml
[14]: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/x86-support/#_my_x86_64_or_x86_application_is_missing_some_system_libraries_what_do_i_do
[15]: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/x86-support/
