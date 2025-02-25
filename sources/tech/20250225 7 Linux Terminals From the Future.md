[#]: subject: "7 Linux Terminals From the Future"
[#]: via: "https://itsfoss.com/modern-linux-terminals/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

7 Linux Terminals From the Future
======

[![Warp Terminal][1]][2]

Every Linux system comes with a terminal application, i.e. terminal emulators in correct technical terms.

For many Linux users, it doesn't matter which terminal they use. I mean, you just run commands on it and it is the commands that matter, right?

And yet, we have a [huge number of terminals][3] available.

While the classics are focused on providing additional features like multiplexing windows, there is a new breed of terminals that offer GPU acceleration, AI and even flaunt that they are built on Rust 🦀

🚧

Modern solutions bring modern problems. Some of the options here are non-foss, some may even have telemetry enabled. I advise checking these things when you try any of the mentioned terminals here.

### 1\. Wave Terminal

![Wave terminal][4]

[Wave][5] is an open-source cross-platform terminal emulator, that offers several unique features like graphical widgets. It feels like you are using an IDE like VS Code and that is in the good sense.

Oh! It comes baked in with AI as well.

#### Features of Wave Terminal

  * Integrated AI chat with support for multiple models
  * Built-in editor for seamlessly editing local and remote files.
  * Command Blocks for isolating and monitoring individual commands with auto-close options.
  * File preview, that supports Markdown, images, video, etc.
  * Custom themes, background images, etc.
  * Inline Web browser.



Overall, this terminal is the best fit for those who are looking for serious application development projects.

Since most of the features are easily accessible, a relatively newer terminal user can also enjoy all the benefits.

#### Install Wave Terminal

Ubuntu users can install Waveterm from the snap store.

```

    sudo snap install --classic waveterm

```

The project also provides DEB, RPM and AppImage package formats.

[Download Wave Terminal][6]

### 2\. Warp

![][7]

[Warp][8] is a Rust-based terminal emulator, that offers built-in AI features and collaboration workflows.

The AI agent answers your query and can even run commands for you.

Like Wave, this too has an IDE-like feel, suitable for the new breed of developers and devops who dread the dark alleys of the command line.

The workflow feature is useful for both individuals and teams. If you have different project scenarios where you must run one command after another, you can create workflows. It improves your efficiency.

🚧

Warp is not open source software.

#### Features of Warp Terminal

  * Built-in AI features like command lookup, AI autofill, command suggestions, chat with Warp AI, etc.
  * IDE-like text editing, with mouse support.
  * Markdown viewer with embedded command execution support.
  * Collaboration workflow with Warp Drive.
  * Extensive customization possibilities.



#### Install Warp Terminal

Warp provides DEB files for Ubuntu and other Debian-based systems.

[Download Warp Terminal][9]

There are also RPM and AppImage packages.

### 3\. Cogno

[Cogno][10] is a free and open-source terminal emulator, that offers several handy features like self-learning autocomplete.

It is cross-platform and supports multiple shells, while allowing the user to customize according to individual preferences.

And there are tons of themes that can be used. Perfect for a beautiful desktop screenshot to share in the communities.

#### Features of Cogno

  * Context-aware autocompletion.
  * Configurable shortcuts.
  * Support for tabs, panes, and workspaces.
  * Theme editor with preview function.
  * Paste history, that allows to paste items that were pasted previously.



#### Install Cogno

DEB and RPM installers are available in the official project download page.

[Download Cogno][11]

### 4\. Rio

[Rio][12] is a hardware-accelerated GPU terminal emulator, written in Rust. It is intended to run as a native desktop application as well as a browser application.

![Rio Terminal][13]

#### Features of Rio Terminal

  * Hardware-accelerated, fast and written using Rust.
  * Multi-windows and Split panels
  * Image support: iTerm2 and Sixel image protocols.
  * Supports hyperlinks.
  * Vi Mode



#### Install Rio Terminal

Rio offers separate DEB files for both X11 and Wayland. SO choose according to your specific needs.

[Download Rio Terminal][14]

There are installation instruction available for other distributions like Arch Linux, NixOS, etc. You can find those in the [official installation instructions][15].

### 5\. Contour

[Contour][16] is a GPU-accelerated modern terminal emulator with high-DPI support. This cross-platform terminal emulator focuses on speed, efficiency, and productivity.

![Contour Terminal][17]

#### Features of Contour

  * GPU-Accelerated Terminal emulator with high-DPI support.
  * Font ligature support.
  * Complex Unicode support, including emojis.
  * Runtime configuration reload
  * Key binding customization
  * VT320 Host-programmable and Indicator status line support



#### Install Contour Terminal

Ubuntu and Debian-based distribution users can download the DEB file from official releases page. There is an AppImage package available as well.

[Download Contour Terminal][18]

If you are a Fedora user, you can install it directly from the official repository.

```

    sudo dnf install contour-terminal

```

There is a detailed installation instructions for other platforms on the [official documentation][19].

### 6\. Alacritty

[Alacritty][20] is a modern terminal emulator, that offers heavy configuration capabilities. It is a GPU-accelerated terminal emulator, written on Rust.

![Alacritty Terminal][21]

#### Features of Alacritty

  * GPU accelerated terminal, written in Rust.
  * Hyperlink support.
  * Supports running multiple terminal emulators from the same Alacritty instance
  * Vi mode
  * Cross-platform support.



#### Install Alacritty

Alacritty is fairly popular among Linux users. It is available in the default repositories of most distributions. For latest Ubuntu releases, you can install it using the apt command:

```

    sudo apt install alacritty

```

### 7\. Hyper

[Hyper][22] is a terminal emulator, built on open web standards. Written in Typescript, this extensible terminal focuses on speed and stability.

If nothing else, it does look good. The screenshot below may not do justice.

![Hyper Terminal][23]

#### Features of Hyper

  * Functionality can be extended with plugins available on NPM.
  * Keymap customization
  * Cross-platform support
  * Customization capabilities using JavaScript configuration file.



#### Install Hyper Terminal

Hyper offers DEB and RPM files for Debian-based and Fedora-based systems, respectively.

[Download Hyper][24]

There is also an AppImage package available.

### Bonus: Komandi

[Komandi][25] is an AI-powered terminal command manager. Komandi is different from usual terminal emulators. This piece of software allows the user to create and store command snippets and run them on your preferred terminal emulator.

🚧

Komandi is not open source software. It requires you to purchase a license. I found it interesting and hence included it here.

### Conclusion

I feel like I should have included [Ghostty][26] in this list of modern new terminal emulators. It's the talk of the terminal town, after all. However, I haven't tried it yet. I know, I am late to board the 'Ghost ship'.

For a long time, the only new feature was often multiple terminal windows on the same screen and it was hard to believe that the scenario can be changed. It is interesting to see new terminals coming up with innovative features in the last few years.

_💬 Tell me. Are you sticking with the classic terminals, or have switched to one of these modern ones?_

--------------------------------------------------------------------------------

via: https://itsfoss.com/modern-linux-terminals/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/linux-terminal-emulators/
[4]: https://itsfoss.com/content/images/2025/02/image-10.png
[5]: https://news.itsfoss.com/wave-terminal/
[6]: https://www.waveterm.dev/download
[7]: https://itsfoss.com/content/images/2025/02/image-11.png
[8]: https://app.warp.dev/referral/6N3LPK
[9]: https://app.warp.dev/referral/6N3LPK
[10]: https://cogno.rocks
[11]: https://cogno.rocks/#downloads
[12]: https://raphamorim.io/rio/
[13]: https://itsfoss.com/content/images/2025/01/rio.png
[14]: https://github.com/raphamorim/rio/releases
[15]: https://raphamorim.io/rio/docs/install/linux
[16]: https://contour-terminal.org
[17]: https://itsfoss.com/content/images/2025/01/contour.png
[18]: https://github.com/contour-terminal/contour/releases
[19]: https://contour-terminal.org/install/
[20]: https://alacritty.org
[21]: https://itsfoss.com/content/images/2025/01/alacritty.png
[22]: https://hyper.is
[23]: https://itsfoss.com/content/images/2025/01/hyper-terminal.png
[24]: https://hyper.is/#installation
[25]: https://komandi.app
[26]: https://ghostty.org/
