[#]: subject: "11 Terminal File Managers for Superior File Organization"
[#]: via: "https://itsfoss.com/terminal-file-managers/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

11 Terminal File Managers for Superior File Organization
======

[![Warp Terminal][1]][2]

The Graphical User Interface (GUI) tools for Linux have evolved significantly over the years. You can find some of the [best file managers for Linux][3] as GUI tools.

But when it comes to the command line, most Linux users resort to the [ls command to look for files present on the system][4].

Few users are aware of [TUI][5]-based file explorers that make it more convenient to browse files in a terminal.

Let's take a look at some neat terminal-based file management utilities that work just as easily as a GUI file manager. I have selected a couple of minimal and feature-rich tools, so feel free to pick what works best for you.

📋

This list is in no particular order.

### 1\. Vifm

Vifm or Vi-file manager is a terminal-focused utility which is one of the [best file managers for Linux][3]. As the name suggests, Vifm provides a Vim-like environment for managing objects within the file system.

0:00

/0:28

1×

Vifm File Manager

If you are familiar with Vi or Vim, this file manager will make you feel right at home with the keyboard shortcuts. But, you can use it for day to day purpose, even if you are not a Vi expert.

**Key features of Vifm:**

  * Vim-like user mappings
  * Directory tree comparison
  * Operation undoing/redoing/back grounding
  * FUSE file systems support
  * Color schemes, which can also be applied to specific subtrees
  * Advanced file filtering and renaming capabilities
  * Named bookmarks (tags)
  * Sessions
  * Built-in integration with GNU Screen and tmux



**Installing Vifm**

Since it is a popular file manager, it is available in the default repository of many Linux distributions. On Ubuntu, you can install Vifm using:

```

    sudo apt install vifm

```

Vifm, when invoked from the terminal, opens in the current working directory using the following command:

```

    vifm

```

### 2\. Ranger

Another command-line based popular file manager, inspired by Vim, is Ranger. It is a minimalistic file manager, with a similar interface. Ranger has a file launcher, called Rifle, that can open files based on its type.

![Ranger File Manager][6]

Apart from that, it offers a multi-pane view mode and all the essentials.

**Key features of Ranger:**

  * UTF-8 Support (if your Python copy supports it)
  * Multi-column display
  * Preview of the selected file/directory
  * Common file operations (create/chmod/copy/delete/…)
  * Renaming multiple files at once
  * VIM-like console and hotkeys
  * Automatically determine file types and run them with correct programs
  * Change the directory of your shell after exiting ranger
  * Tabs, bookmarks, mouse support, and more



**Install Ranger**

Ranger is available to install on the default repos of Ubuntu. Open a terminal and run the following command to get it installed:

```

    sudo apt install ranger

```

### 3\. Midnight Commander

GNU Midnight Commander is a feature-rich file manager, that can do most of the important file management operations in a full-screen text-mode.

It also comes with an internal viewer and editor.

0:00

/0:34

1×

Midnight Commander

**Key features of GNU Midnight Commander:**

  * Built-in virtual file system: manipulate remote file systems, browse archive files
  * Mouse support on most terminal emulators for X Window System as well as on the Linux console
  * Text and hex editors available
  * Hotlist allows you to keep a list of common visited locations
  * Command completion with Alt-Tab shortcut
  * Subshell support
  * Linux file recovery
  * Built-in editor supports syntax highlighting and external actions, such as spell checking and formatting
  * FTP proxy support



**Install GNU Midnight Commander**

Midnight Commander uses the package name `mc` in most system. So, in a terminal, run the command below to get it installed:

```

    sudo apt install mc

```

[Midnight Commander][7]

### 4\. Superfile

[Superfile][8] is a modern terminal file manager written in Go. It offers an eye candy user interface with powerful multi panel workflow.

![Superfile File Manager][9]

**Key features of Superfile:**

  * Beautiful user interface
  * Fully customizable from basic hotkey to theming and styling
  * Almost complete functions of a file manager are available
  * Plugin support
  * Linux and macOS support, with a possible Windows installation
  * Sudo and Local installation
  * Offers file preview



**Install Superfile**

Before installing Superfile, make sure you have any Nerd Fonts installed. If not, [install any Nerd Font][10] of your choice.

Now, for all Linux users, run the command below to install Superfile.

```

    bash -c "$(curl -sLo- https://superfile.netlify.app/install.sh)"

```

Additionally, there are packages for Arch Linux in official repositories:

```

    sudo pacman -S superfile

```

You can check additional [installation options on the official documentation][11].

Once installed, you may need to reopen your terminal. To start Superfile, use the command:

```

    spf

```

[Superfile][12]

### 5\. xplr

[xplr][13] is an intuitive and hackable file explorer with a focus on increased productivity by utilizing the command-line file-system utilities.

0:00

/0:27

1×

xplr file explorer working in a terminal

This is not a file manager in the sense that you can do what a GUI file manager lets you do. But, it works more as a file explorer, offering some powerful tools.

**Key features of xplr:**

  * Fast and minimal
  * Customizable layouts with built-in panels
  * Switchable recover mode that saves you from doing unwanted things when rushing
  * Embedded LuaJIT for portability and extensibility
  * Custom file properties with custom colors can be displayed in the table
  * Plugins and integrations
  * Different quit options
  * Custom file properties with custom colors can be displayed in the table



**Install xplr**

If you are an Arch Linux user, use the following command to install it:

```

    sudo pacman -S xplr

```

Another way to install is by using the Crates. Make sure you have `rust toolchain`, `gcc`, and `make`packages ready. And, then run:

```

    cargo install --locked --force xplr

```

For all other users, you can always download the compiled binaries from the [official releases page][14].

[xplr][15]

### 6\. Yazi

[Yazi][16] is a rust-based file manager for your terminal, which is exceptionally fast. It is based on non-blocking async I/O and aims to provide an efficient, user-friendly, and customizable file management experience.

![Yazi File Manager][17]

**Key features of Yazi:**

  * Full Asynchronous Support
  * Powerful Async Task Scheduling and Management
  * Built-in Support for Multiple Image Protocols
  * Built-in Code Highlighting and Image Decoding
  * Plugin system with package manager for plugins and themes management
  * Multi-tab with scrollable preview
  * Integration with ripgrep, fd, fzf, and zoxide
  * Data Distribution Service



**Install Yazi**

For Arch Linux, use:

```

    sudo pacman -S yazi ffmpegthumbnailer p7zip jq poppler fd ripgrep fzf zoxide imagemagick

```

📋

For Yazi, a nerd-font is recommended to have installed.

For all other distributions, download the [compiled binary from the official release page][18].

More installation methods including rust cargo are explained in the [official documentation of the project][19].

[Yazi][20]

**Suggested Read 📖**

![][21]

### 7\. CliFM

[CliFM][22] is a simple terminal file manager, that works a bit differently from the other tools. Instead of a Terminal User Interface (TUI), CliFM, as in the name, follows a CLI design principle.

0:00

/0:48

1×

CliFM File Manager basic working.

**Key features of CliFM:**

  * Can run on the kernel built-in console, SSH, or any other remote session.
  * Wide terminal support (even 8 colors and no Unicode support terminals).
  * Extended color codes for file-types and -extensions.
  * Supports operations like bookmarks, tags, filters, etc.
  * Up to 8 workspaces.
  * File permissions/ownership editor via the `pc` and `oc` commands respectively.
  * Autosuggestions, syntax highlighting, TAB completion, etc. are available.
  * A Stealth mode, also known as incognito or private mode.



**Install CliFM**

Arch Linux users can [install CliFM from AUR][23].

There are binary packages for major Linux distributions like Arch, Debian, Ubuntu, etc. You can also [download the binary][24] from the openSUSE build system.

[CliFM][25]

### 8\. nnn

[n3 or nnn][26] is a full-featured terminal file manager, that is nearly 0-config. While this minimalism does not affect the capabilities of this utility.

0:00

/0:31

1×

nnn file manager working

**Key features of nnn:**

  * POSIX-compliant, follows Linux kernel coding style
  * Typically needs less than 3.5 MB resident memory
  * Minimal library deps, easy to compile
  * Touch enabled, handheld-friendly shortcuts
  * Basic support for screen readers and braille displays
  * Run plugins and custom commands with hotkeys
  * Launch apps, run commands, spawn a shell, etc



**Install nnn**

nnn is available in the repos of most distribution. In Ubuntu, run the following command to install it:

```

    sudo apt install nnn

```

You can also get statically linked binary from the [releases page of the project][27].

[n3 or nnn][26]

### 9\. lfm

[lfm or Last File Manager][28] is a UNIX console file manager written in Python. It offers a two-pane interface by default with a neat dark color scheme.

0:00

/0:31

1×

lfm file manager

**Key features of lfm:**

  * Support tabs, file filters, bookmarks, history, etc
  * VFS for compressed files
  * Direct integration of find/grep, df and other tools
  * Color files by extension
  * Fully customizable themes (colors) and key bindings
  * Support for filenames with wide chars



**Install lfm**

lfm is available in the default repositories of most major Linux distributions. Ubuntu users can install it using the command:

```

    sudo apt install lfm

```

🚧

Ensure the version of lfm is 3 or higher in the repository. You also need Python 3.4+ to run this.

[lfm][28]

### 10\. lf

lf is a simple file manager, heavily inspired from Ranger file manager. Its specialty is being a straightforward and minimal utility.

0:00

/0:24

1×

lf file manager

**Key features of lf:**

  * Cross-platform
  * Single binary without any runtime dependencies
  * Fast startup and low memory footprint
  * Asynchronous IO operations to avoid UI locking
  * Server/client architecture and remote commands to manage multiple instances
  * Extendable and configurable with shell commands
  * Customizable keybindings



**Install lf**

[lf][29] is available in the default repositories of major Linux distribution. For Ubuntu and Debian-based, install it using:

```

    sudo apt install lf

```

There are prebuilt binaries available in the [project releases page][30] for all distributions.

[lf][29]

### 11\. Ytree

[Ytree][31] is a classic-looking file manager for browsing filesystem and archives.

0:00

/0:23

1×

Ytree file manager

**Key features of Ytree:**

  * Supports external programs to view/edit files
  * An internal hex viewer and editor are available
  * Configurable and supports different architectures



**Install Ytree**

On Ubuntu, you can install it from the official repository.

```

    sudo apt install ytree

```

Arch Linux users can [find it in AUR][32].

[Ytree][31]

**Suggested Read 📖**

![][21]

### Wrapping Up

Terminal-based file managers help you efficiently work with files without worrying about the performance, regardless of what utility you choose from the list.

If you want simple operations, and just explore the filesystem, you can go with any of the choices. But, if you are looking for a performance-focused, easy-to-use, and feature-rich program, I suggest superfile and yazi. Just two of my personal picks.

You should give all of them a try if one doesn't work good enough for your use-case.

_💬_ _What is your favorite on the list? Anything I missed here? Do share your thoughts in the comments below._

--------------------------------------------------------------------------------

via: https://itsfoss.com/terminal-file-managers/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/file-managers-linux/
[4]: https://itsfoss.com/ls-command/
[5]: https://itsfoss.com/gui-cli-tui/
[6]: https://itsfoss.com/content/images/2024/08/ranger-file-manager.gif
[7]: https://www.midnight-commander.org/
[8]: https://github.com/yorukot/superfile
[9]: https://itsfoss.com/content/images/2024/08/superfile-file-manager.gif
[10]: https://itsfoss.com/install-fonts-ubuntu/
[11]: https://superfile.netlify.app/getting-started/installation/
[12]: https://superfile.netlify.app/
[13]: https://github.com/sayanarijit/xplr
[14]: https://github.com/sayanarijit/xplr/releases
[15]: https://xplr.dev/
[16]: https://github.com/sxyazi/yazi
[17]: https://itsfoss.com/content/images/2024/08/yazi-file-manger.gif
[18]: https://github.com/sxyazi/yazi/releases
[19]: https://yazi-rs.github.io/docs/installation
[20]: https://yazi-rs.github.io/
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[22]: https://github.com/leo-arch/clifm
[23]: https://aur.archlinux.org/packages/clifm
[24]: https://software.opensuse.org//download.html?project=home%3Aarchcrack&package=clifm
[25]: https://github.com/leo-arch/clifm/wiki
[26]: https://github.com/jarun/nnn
[27]: https://github.com/jarun/nnn/releases/latest
[28]: https://inigo.katxi.org/devel/lfm/
[29]: https://github.com/gokcehan/lf
[30]: https://github.com/gokcehan/lf/releases
[31]: https://www.han.de/~werner/ytree.html
[32]: https://aur.archlinux.org/packages/ytree
