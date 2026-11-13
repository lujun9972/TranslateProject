[#]: subject: "Installing the official Claude Desktop Linux beta on Fedora Linux"
[#]: via: "https://fedoramagazine.org/installing-the-official-claude-desktop-linux-beta-on-fedora-linux/"
[#]: author: "Ajith Kumar Karudasevai https://fedoramagazine.org/author/ajithakdev/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing the official Claude Desktop Linux beta on Fedora Linux
======

![][1]

Original By Claude Monet. Photo by [National Gallery of Art][2] on [Unsplash][3] (cropped)

Anthropic released a Linux beta of Claude Desktop, but only as a .deb package for Debian and Ubuntu. claude-desktop-rpm is a small Bash script that installs that same package on Fedora. This article covers what the script checks, what it changes on your system, and how to remove it again.

### Before you start: what this is and what it costs

Claude Desktop is proprietary software from Anthropic, released under Anthropic’s own terms. The install script described here is MIT licensed. It is not made by Anthropic and it does not redistribute any of Anthropic’s files: it downloads the package from Anthropic’s own repository each time.

You need a Claude account to use the app. Chat works on every plan, including the free one. Claude Code and Cowork, the two features most people install the desktop app for, need a paid plan (Pro, Max, Ultra, Team or Enterprise). Anthropic’s download page lists the current plans and prices.

If you would rather use free and open source tools for this kind of work, there are good options that run on Fedora too, such as [OpenCode][4] and [Hermes Agent][5]. This article is for people who already use Claude and want the official app on Fedora.

### What the script checks before installing

Anthropic publishes the Linux beta as a signed APT repository. The script described here reads that repository the same way APT would, and stops if any check fails:

  1. Anthropic’s public key must match a fingerprint pinned in the script.
  2. The repository index (InRelease) must be signed by that key, and its Valid-Until date must not have passed.
  3. The package list’s checksum must match the signed index.
  4. The .deb’s checksum must match the package list.



Only if all these checks are passed does it unpack the .deb. A reader on Fedora Discussion found a gap in the first version (the index could be signed by any key in the key file, not only the pinned one). That is fixed, and the test suite now runs each of these checks against a tampered copy of the repository.

### Installing it

The script needs four packages that most Fedora Workstation systems already have. You might verify that these are available:

```

    sudo dnf install curl gnupg2 binutils tar

```

Next, download the Claude script from the latest release into a folder and run it as your normal user:

```

    curl -fLO https://github.com/ajithakdev/claude-desktop-rpm/releases/latest/download/claude-desktop-rpm.sh

    chmod +x claude-desktop-rpm.sh && ./claude-desktop-rpm.sh install

```

Each release also publishes a checksum file, SHA256SUMS. To check the downloaded script before running it, fetch that file into the same folder used to contain the script and compare:

```

    curl -fLO https://github.com/ajithakdev/claude-desktop-rpm/releases/latest/download/SHA256SUMS

    sha256sum -c SHA256SUMS

```

The script is a single Bash file so you can also read it before running it.

The installation does NOT use _sudo_. Everything goes into ~/.local (the app, a launcher, the menu entry and icons) and ~/.config (a systemd user timer for updates). The script also copies itself to ~/.local/bin/claude-desktop-rpm, so from then on you can run it by name.

Open Claude from the application menu and sign in. If something looks wrong, run:

```

    claude-desktop-rpm doctor

```

This checks the installation, the launcher, automatic updates, the tray icon, the keyring that stores your sign-in, and the Cowork prerequisites. Each warning comes with the command that fixes it.

### Why the app stays light in dark mode

On GNOME, the app stays light even when the desktop is set to dark. Electron apps on Linux read the GTK theme name, and GNOME’s dark style does not change that name. It sets a separate color-scheme preference that Electron ignores.

The script does not touch Anthropic’s files. Instead, the launcher created checks GNOME’s color-scheme setting when you start the app, and sets GTK_THEME=Adwaita:dark for Claude only when it is dark. If you set GTK_THEME yourself, the launcher leaves it alone.

GNOME also hides tray icons by default, and Claude’s tray menu is where Quit lives. The doctor command tells you how to turn on the AppIndicator extension if you want the icon.

### Setting up Cowork

Cowork runs tasks inside a small virtual machine, so it needs KVM, QEMU, UEFI firmware and virtiofsd. On Fedora all of these come from Fedora’s own repositories. Run this once:

```

    claude-desktop-rpm cowork

```

This is the only command that uses _sudo_. It performs the following steps:

  * installs qemu-system-x86-core, edk2-ovmf and virtiofsd with dnf
  * writes /etc/modules-load.d/vhost_vsock.conf and loads the vhost_vsock module
  * adds you to the kvm group



Log out and back in for the group change to take effect. The command does not change any file that a package owns, so rpm -V stays clean. An earlier version did replace two firmware links that edk2-ovmf ships. That was a mistake, and the current version restores the packaged links if it finds the old ones.

#### Plan for disk space

The app’s Cowork virtual machine files take about 12 GB in ~/.config/Claude.

### Updates

The script installs a systemd user timer that checks Anthropic’s repository once a day. Each update goes through the same checks as the first install. If Claude is open when an update arrives, the script downloads and verifies it but waits, and the launcher puts it in place the next time you start the app.

To turn the daily check off or on again use these commands:

```

    claude-desktop-rpm auto-update off

    claude-desktop-rpm auto-update on

```

**Note** : If the app shows its own “Update available” button, ignore it. Its link points to APT. The timer handles updates, or you can quit Claude and run claude-desktop-rpm update.

### A second account

Some people keep separate Claude accounts for work and personal use. Version 1.2.0 added profiles for that:

```

    claude-desktop-rpm profile add work

```

This adds “Claude (work)” to the app menu. It opens with its own sign-in and chats in ~/.config/Claude-work, and it can run next to your normal Claude window. The launcher passes Chromium’s –user-data-dir flag to do this. Anthropic does not document that flag for Claude Desktop, so a future version could ignore it. If that happens, both menu entries open your normal account and nothing is lost. Both tray icons also look the same; the tray menu, which shows each account’s plan, tells them apart.

### What does not work yet

  * Computer Use is not in Anthropic’s Linux build on any distribution yet.
  * The script is tested on Fedora 44 Workstation (GNOME, x86_64), and its automated install test also passes on Fedora 45. A user reported it working on KDE Plasma on Aurora, an atomic Fedora variant. Other desktops and RHEL-based systems have not been tested much.
  * Anthropic officially supports only Debian and Ubuntu for now. If something breaks after an update, the problem may be in the script, so please report it on the project’s issue tracker rather than to Anthropic. (See the project link in the Links section below)



### Removing it

```

    claude-desktop-rpm uninstall

```

This removes everything the install added to ~/.local and ~/.config, including the timer and any profile menu entries, and rebuilds the menu, file-type and icon caches.

Your chats and sign-in in ~/.config/Claude stay, in case you reinstall. Delete that folder (and any Claude-NAME folders) to erase them too.

The uninstall never uses _sudo_ , so the Cowork setup stays: remove the packages with _dnf_ and delete /etc/modules-load.d/vhost_vsock.conf if you no longer need them.

### Links

  * Project and documentation: [https://github.][6][c][6][o][6][m][6][/ajithakdev/claude-desktop-rpm][6]
  * Discussion thread: <https://discussion.fedoraproject.org/t/205947>
  * Anthropic’s Linux documentation: [https://code.claude.c][7][om/docs/en/desktop-linux][7]



### AI Use

Assisted-by: Claude (drafting help for the script and this article; the author reviewed every part and tested each command on Fedora 44).

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/installing-the-official-claude-desktop-linux-beta-on-fedora-linux/

作者：[Ajith Kumar Karudasevai][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ajithakdev/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/11/install_claude_desktop-816x345.jpg
[2]: https://unsplash.com/@nationalgallery?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/SDxGWcz1zLA?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://opencode.ai/
[5]: https://hermes-agent.nousresearch.com/
[6]: https://github.com/ajithakdev/claude-desktop-rpm
[7]: https://code.claude.com/docs/en/desktop-linux
