[#]: subject: "Better Than Original? 14 Rust-based Alternative CLI Tools to Classic Linux Commands"
[#]: via: "https://itsfoss.com/rust-alternative-cli-tools/"
[#]: author: "Neville Ondara https://itsfoss.com/author/neville/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Better Than Original? 14 Rust-based Alternative CLI Tools to Classic Linux Commands
======

[![Warp Terminal][1]][2]

If you’re like me, you probably grew up with the classic Linux command-line tools such as `ls`, `cat`, `du`. These commands have carried me through countless scripts and late-night debugging sessions.

Here's the thing. While these tools do their job, they can be plain looking and difficult to use for certain tasks.

Take the [du command][3] for example. It shows the disk usage on the system but use it without any option, and it is a mess.

Terminals today support color, Unicode icons, live previews, all things our old favorites weren’t designed for. And the Rust revolution has quietly reshaped the command-line landscape. So there is a wave of Rust-based CLI tools that don’t just replicate the traditional ones; they modernize them. They’re fast, (claim to be) memory-safe, polished, and often come with thoughtful UX touches that make daily terminal work noticeably smoother.

I’ve been tinkering with these tools lately, and I thought it’d be fun to share a list of my favorites.

🚧

If you are a sysadmin, managing servers, you should not rely on alternatives. You might not get these fancy new tools on every system and installing them on every Linux server you log in is not feasible. The alternative tools are good when you are using a personal computer and have full control over the development environment.

### exa: Alternative to ls

![][4]

If there’s one tool that convinced me Rust CLI apps were worth exploring, it’s [`exa`][5]. It feels familiar but adds what the original `ls` has always lacked: sensible colors, icons, and Git awareness.

**Highlights:**

  * Beautiful color themes
  * Git integration
  * Optional tree view
  * Clearer permissions formatting



**Installation:**

```

    cargo install exa

```

**Usage:**

```

    exa -al --git

```

You can instantly see which files are new, which are modified, and which are pure chaos.

### bat: Alternative to cat

![][6]

`cat` is great for quick checks, but reading config files or code in raw plain text gets tedious. `bat` fixes that with syntax highlighting, Git integration, and line numbers, automatic paging, without losing cat compatibility.

Installation:

```

    cargo install bat

```

Example Usage:

```

    bat ~/.bashrc

```

It’s basically `cat` with a glow-up ✨. When I first used it, I found myself opening random config files just to admire the colors.

### dust: Alternative to du

![][7]

`du` always dumps a mountain of numbers on your screen. `dust` turns that into a compact, visual representation of disk usage that you can parse at a glance.

It’s instantly more readable than the old command. The output is clean, easy to parse, and shows relative sizes visually. I swear my hard drive has never looked this friendly. 😎

Install dust:

```

    cargo install du-dust

```

Usage:

```

    dust

```

### fd: Alternative to find

![][8]

Remember spending 10 minutes crafting the perfect `find` command? Yeah… me too. `fd` makes this easier. It has simple syntax, ignores hidden files by default and it is super-fast.

**Install fd:**

```

    cargo install fd-find

```

Example:

```

    fd main.rs
    fd fossnews

```

Its speed and simplicity make `find` feel outdated. After switching, you’ll rarely look back.

### ripgrep (rg): Alternative to grep

![][9]

Rust-based [`ripgrep`][10] has become a must-have for developers. It’s dramatically faster and gives clear, highlighted search results.

Install ripgrep:

```

    cargo install ripgrep

```

Example usage:

```

    rg TODO src/

```

It respects your `.gitignore` and outputs results with color highlighting. I use it every day for searching TODOs, bug reports.

### duf: Alternative to df

![][11]

`df` is useful, but let’s be honest: the output looks like something printed from a 90s dot-matrix printer😆. [`duf`][12] fixes that. It takes the same disk-usage information and turns it into a clean, colorful, structured table you can actually understand at a glance.

`duf` gives you a clean dashboard with grouped filesystems, readable sizes, clear partition labels, and a quick view of what’s healthy vs. what’s nearly full.

Installation:

```

    sudo apt install duf

```

Usage:

```

    duf

```

### procs: Alternative to ps

![][13]

While `ps aux` works, it can feel visually overwhelming. [`procs`][14] **** gives you a more structured, color-coded view of your system processes, letting you quickly see what’s running without the need to launch a full TUI tool like `htop` **.**

It’s like a personal dashboard for your processes. I use it every day to keep tabs on what’s running without feeling buried in a wall of text.

**Installation:**

```

    cargo install procs

```

Usage:

```

    procs

```

### tldr: Alternative to man

![][15]

[`tldr`][16] makes navigating manual pages painless by offering clear examples, highlighting essential flags, and keeping things short (no scrolling forever).

Installation:

```

    cargo install tldr

```

Usage:

```

    tldr tar

```

Honestly, I wish this existed when I was learning Linux, it's a lifesaver for newbies and veterans alike.

### broot: Alternative to tree

![][17]

If you’ve ever used `tree` **,** you know it can quickly becomes overwhelming in large directories. `broot` upgrades the concept: it lets you navigate directories interactively, collapse or expand folders on the fly, and search as you go.

Installation:

```

    cargo install broot

```

Usage:

```

    broot

```

I’ve ditched my old `ls -R` habit entirely, `broot` makes exploring directories feel interactive and satisfying, turning a messy filesystem into something you can actually enjoy navigating.

### zoxide: Alternative to cd

![][18]

How many times have you typed `cd ../../../../some/long/path`? Too many, right? `z` (or `zoxide`) solves that by tracking your most visited directories and letting you jump to them with a single command, saving your fingers and making navigation effortless.

Installation:

```

    cargo install zoxide

```

You also need to initialize it in your shell:

```

    # Bash
    eval "$(zoxide init bash)"
    # Zsh
    eval "$(zoxide init zsh)"
    # Fish
    zoxide init fish | source

```

Usage:

```

    z code

```

It keeps track of your frequently used directories and lets you jump to them instantly.

### lsd: Alternative to ls

![][19]

If you’re tired of the plain, monochrome output of `ls`, `lsd` is here to make your directory listings not just readable, but enjoyable. With built-in icons and vibrant colors, it instantly helps you distinguish between files, directories, and executables at a glance.

Installation:

```

    cargo install lsd

```

You can run it just like a normal `ls` command:

```

    lsd -la

```

`lsd` organizes information clearly and highlights key file attributes, making navigation faster and more intuitive.

### bottom: Alternative to top

![][20]

The classic `top` command shows system usage, but let’s face it, it can feel like you’re looking at a terminal snapshot from 1995 😆. `bottom` (or `btm`) brings a modern, clean, and highly visual experience to monitoring your system. It provides:

  * Color-coded CPU, memory, and disk usage
  * Real-time graphs directly in the terminal
  * An organized layout that’s easy to read and navigate



Installation:

```

    cargo install bottom

```

You can launch it simply with:

```

    btm

```

Once you start using bottom, it’s hard to go back. Watching CPU spikes, memory usage, and disk activity while compiling Rust projects feels strangely satisfying. It’s both functional and fun, giving you the insights you need without the clutter of older tools.

### hyperfine: Alternative to time and other benchmarking commands

Ever wondered which of your commands is truly the fastest? Stop guessing and start measuring with `hyperfine`. This Rust-based benchmarking tool makes it effortless to compare commands side by side.

`hyperfine` runs each command multiple times, calculates averages, and gives you a clear, color-coded comparison of execution times. Beyond simple comparisons, it also supports warm-up runs, statistical analysis, and custom command setups, making it a powerful addition to any developer’s toolkit.

Installation:

```

    cargo install hyperfine

```

Usage example:

```

    hyperfine "exa -al" "ls -al"

```

Watching `exa` obliterate `ls` in mere milliseconds is oddly satisfying⚡. If you love optimization, efficiency, and a little nerdy satisfaction, hyperfine is your new best friend.

### xplr: Alternative to nnn

![][21]

Now, I don't know if I can call nnn a classic Linux tool but I liked xplr so much that I decided to include it here.

`xplr` takes the idea of a [terminal file explorer][22] to the next level. If you loved `broot`, `xplr` will blow your mind with these features:

  * Navigate directories using arrow keys or Vim-style bindings
  * Preview files directly inside the terminal
  * Launch commands on files without leaving the app
  * Fully customizable layouts and keybindings for power users



Installation:

```

    cargo install xplr

```

Usage:

```

    xplr

```

### Wrapping Up

Switching to new commands might feel like extra effort at first, but Rust-based CLI tools are often more than just a trend, they’re fast, modern, and designed to make your workflow enjoyable.

  * They handle colors, syntax highlighting, and Git integration right out of the box.
  * They save keystrokes, reduce frustration, and make complex tasks simpler.
  * They make your terminal feel alive and engaging.



On top of that, using them makes you look extra cool in front of fellow Linux nerds. Trust me, it’s a subtle flex 💪

Start small, maybe install `exa` and `bat` first, and gradually expand your toolkit. Soon, your terminal will feel futuristic, your workflow smoother, and your projects easier to manage.

--------------------------------------------------------------------------------

via: https://itsfoss.com/rust-alternative-cli-tools/

作者：[Neville Ondara][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/neville/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://linuxhandbook.com/find-directory-size-du-command/
[4]: https://itsfoss.com/content/images/2025/11/image1-1.png
[5]: https://itsfoss.com/exa/
[6]: https://itsfoss.com/content/images/2025/11/image2-1.png
[7]: https://itsfoss.com/content/images/2025/11/image3-1.png
[8]: https://itsfoss.com/content/images/2025/11/image4-1.png
[9]: https://itsfoss.com/content/images/2025/11/image5.png
[10]: https://itsfoss.com/ripgrep-all/
[11]: https://itsfoss.com/content/images/2025/11/image6.png
[12]: https://itsfoss.com/duf-disk-usage/
[13]: https://itsfoss.com/content/images/2025/11/image7.png
[14]: https://itsfoss.com/procs/
[15]: https://itsfoss.com/content/images/2025/11/image8.png
[16]: https://itsfoss.com/tldr-linux-man-pages-simplified/
[17]: https://itsfoss.com/content/images/2025/11/image9-1.png
[18]: https://itsfoss.com/content/images/2025/11/image10-1.png
[19]: https://itsfoss.com/content/images/2025/11/image11-1.png
[20]: https://itsfoss.com/content/images/2025/11/image12.png
[21]: https://itsfoss.com/content/images/2025/11/image14.png
[22]: https://itsfoss.com/file-managers-linux/
