[#]: subject: "Stop Manually Checking GitHub Releases — These Tools Automatically Install & Update Apps on Linux"
[#]: via: "https://itsfoss.com/github-binaries-tools/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Stop Manually Checking GitHub Releases — These Tools Automatically Install & Update Apps on Linux
======

[![Warp Terminal][1]][2]

[Package managers][3] are essential tools on Linux systems. They help you install, update, and remove software packages with simple commands. Most distributions come with their own package managers, like `apt`, `dnf`, or `pacman`.

However, **many modern tools are distributed as pre-compiled binaries via GitHub releases**. Developers using languages like Go, Rust, and Deno often release their software this way. New projects that are not included in the official distro repository yet have to opt for this method.

This creates a gap between traditional package managers and these GitHub-hosted releases.

Recently we covered [Eget][4], a command utility that fetches appropriate binary from the given GitHub repo. You don't have to manually visit the release page of the application's GitHub repo, look for the available binary files and then install it. Eget does all that from the comfort of the command line.

But Eget is not unique. There are many more such package management tools. They let you install binaries, also handle updates, letting you track new releases without having to manually checking repositories.

Let's take a look at some of these package managers for you to explore.

### GitHub Binary Download Tools

Tool | Primary Focus | Language | GitHub Stars
---|---|---|---
deb-get | Debian/Ubuntu packages | Bash | 1.5k
Autonomix | GUI package manager | Rust | 6
Eget | Simple binary installer | Go | 1.8k
Install Release | Good Git support | Python | 104
bin | Multi-source manager | Go | 1k
stew | Install binaries from URL | Go | 309
AFX | Shell plugins + binaries | Go | 179

### 1\. deb-get

![][5]

[deb-get][6] brings [apt-get][7] functionality to third-party `.deb` packages. It **works specifically with Debian and Ubuntu-based distributions**. The tool handles packages from GitHub releases, PPAs, and direct downloads. It is developed by Martin Wimpress, the creator of Ubuntu MATE.

The project maintains a curated repository of supported software. This includes popular applications not available in official repositories. Installation is straightforward with commands similar to apt.

deb-get works better with a GitHub Personal Access Token for updates. This avoids rate-limiting issues when checking for new releases. The tool also supports external repositories for custom package definitions.

You can install deb-get on Debian, Ubuntu, or any derivatives by using this command:

```

    sudo apt install curl lsb-release wget
    curl -sL https://raw.githubusercontent.com/wimpysworld/deb-get/main/deb-get | sudo -E bash -s install deb-get

```

Run this to learn the standard commands to use deb-get:

```

    deb-get help

```

### 2\. Autonomix

![][8]

[Autonomix][9] is **the only GUI-based option in this list**. It uses _GTK4_ and _libadwaita_ for a modern interface. The tool works similarly to [Obtainium][10], which Android users might recognize.

The application supports multiple package formats, including `.deb`, `.rpm`, `AppImage`, `Flatpak`, and `Snap`. It stores package information in a local database. You can track releases and install updates with a single click.

Autonomix is a relatively new one with active development. It handles system-level packages using `pkexec` for privilege elevation. The tool can also manage user packages like `Flatpak` and `AppImage` without requiring root access.

You can get Autonomix for Debian, Ubuntu, and their derivatives by downloading the `.deb` from [GitHub][11] and running the following command while being in the same directory:

```

    sudo dpkg -i autonomix_*.deb
    sudo apt-get install -f  # Fix any dependency issues

```

You can do the same for Fedora or RHEL by downloading the `.rpm` and running this command:

```

    sudo dnf install autonomix-*.rpm

```

[][12]

### 3\. Eget

![][13]

[Eget][14] focuses on simplicity and minimal configuration. The tool **downloads pre-built binaries from GitHub repositories and extracts them automatically**. It works across Linux, BSD, and macOS.

The project requires no setup files or complex configuration. You provide a repository URL, and Eget handles the rest. It supports version-specific installations using tags. You can also download pre-releases if needed. The tool includes options for hash verification and custom installation paths.

You can [learn how to install it in our guide][4] here. 👇

[][12]

![][15]

### 4\. Install Release

![][16]

[Install Release][17] uses Python and provides a CLI tool named `ir`. It supports both GitHub and GitLab releases. The tool stores state information in JSON format for tracking installed packages.

A major feature is state file synchronization. You can push your configuration to a repository and pull it on other machines. This makes it easy to maintain consistent tools across multiple systems.

The tool handles architecture detection automatically. It provides commands for listing, updating, and holding specific packages.

You can get Install Release using pip:

```

    pip install -U install-release

```

### 5\. bin

![][18]

[bin][19] is a cross-platform binary manager without much configuration work. It **supports multiple sources** , including GitHub, GitLab, Codeberg, Docker images, and Hashicorp releases. The tool even handles Go install packages.

The project works without requiring root privileges. Binaries install to user directories by default. bin includes version tracking and rollback capabilities for all managed packages.

It maintains a configuration file to track installations. The tool supports GitHub Enterprise for private repositories.

You can download the package for your platform from [GitHub][20], then follow the instructions [listed in the repository][21].

### 6\. stew

![][22]

[stew][23] introduces declarative package management through Stewfiles. These files define your binary installations with optional version pinning.

The tool provides headless installation from a `Stewfile.lock.json` file. This enables reproducible setups across different machines. It also includes an interactive terminal UI for browsing and selecting releases.

You will find the necessary files and instructions to get stew running on Linux on the GitHub repo linked above.

### 7\. AFX

![][24]

[AFX][25] manages both CLI binaries and shell plugins. It uses YAML configuration files for package definitions. The tool works with bash, zsh, and fish shells.

Packages can include environment variables, aliases, and build steps. AFX supports conditional installation based on system properties. You can define dependencies between different packages.

The tool handles GitHub releases, Gist, HTTP downloads, and local files. It provides shell integration through an `init` command.

The files and instructions to get AFX are in the GitHub repo linked above.

--------------------------------------------------------------------------------

via: https://itsfoss.com/github-binaries-tools/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/package-manager/
[4]: https://itsfoss.com/eget/
[5]: https://itsfoss.com/content/images/2025/12/deb-get.png
[6]: https://github.com/wimpysworld/deb-get
[7]: https://itsfoss.com/apt-get-linux-guide/
[8]: https://itsfoss.com/content/images/2025/12/autonomix.png
[9]: https://github.com/PlebOne/autonomix
[10]: https://github.com/ImranR98/Obtainium
[11]: https://github.com/PlebOne/autonomix/releases
[12]: https://itsfoss.com/content/images/2025/11/foss1-3.png
[13]: https://itsfoss.com/content/images/2025/12/eget.png
[14]: https://github.com/zyedidia/eget
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-143.png
[16]: https://itsfoss.com/content/images/2025/12/install-release.png
[17]: https://github.com/Rishang/install-release
[18]: https://itsfoss.com/content/images/2025/12/bin-1.png
[19]: https://github.com/marcosnils/bin
[20]: https://github.com/marcosnils/bin/releases
[21]: https://github.com/marcosnils/bin?tab=readme-ov-file#-installation
[22]: https://itsfoss.com/content/images/2025/12/stew-2.png
[23]: https://github.com/marwanhawari/stew
[24]: https://itsfoss.com/content/images/2025/12/afx.png
[25]: https://github.com/babarot/afx
