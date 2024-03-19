[#]: subject: "procs is a Better Alternative to the ps Command for Handling Process in Linux"
[#]: via: "https://itsfoss.com/procs/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

procs is a Better Alternative to the ps Command for Handling Process in Linux
======

[![Warp Terminal][1]][2]

One can find tons of replacements for [`top`][3], a CLI tool that provides a dynamic real-time view of a running system. There is the famous [`htop`][4], the asynchronous [`atop`][5], which forces the kernel to write a record of running processes, and some lesser known alternatives, such as [`btop`][6], the [Node.js][7]-based [`gtop`][8], and [`gotop`][9], built with [Go][10].

But what about the good ol’ [`ps`][11]?

`ps` (Process Status) is an ancient Unix command that displays a snapshot of running processes. It supports Unix options (preceded by one dash, like `ps -ef`), BSD options (no dash, like `ps aux`), and GNU options (preceded by two dashes, like `ps --deselect`), and it’s the most classical CLI tool for monitoring system processes.

`ps` is a very well established and reliable command. Nonetheless, it’s an ancient tool, and deserves a modern sibling.

Here’s where [procs][12] comes into the picture: `procs` is a replacement for `ps` written in [Rust][13], and it works on GNU/Linux, BSD, macOS, and Windows.

I found **procs** a couple of years ago and started using it back then, and I’ve never regretted it since.

📋

Although I myself have tested it only on GNU/Linux (Arch Linux and Debian GNU/Linux) and macOS, I took a look at [the code][12], and I’ve found nothing weird anywhere (yet), the code’s pretty clean and readable. That’s one of the greatest advantages of FOSS. 😎

### What does procs do better?

Let’s do it the other way around. Instead of showing you how to install it and then how to use it, let me first try to convince you to adopt `procs.` And then, if you’re convinced, I’ll show you how to install – which is straightforward, trust me.

Running `procs` out of the box, you get a nice colourful output:

![][14]

The default columns are PID, user, TTY, CPU percentage, memory percentage, CPU time, and command line. **To close the pager, press the letter Q; arrows, page up, and page down to navigate**.

It’s possible to tell `procs` to group process together by process tree using the flag `--tree` or `-t`:

![][15]

Another cool feature is searching for a process by name. For instance, searching for `dnsmasq`:

![][16]

It’s possible to use boolean operations `--and` (or `-a`), `--or` (or `-o`), `--nand` (or `-d`), and `--nor` (or `-r`) to combine multiple search strings:

![][17]

The flag `-W` allows to combine other options with a [`watch`][18] fashion presentation:

![][19]

You can still control whether colors should be applied (`--color`), which pager you want (`--pager`), sort ascending (`--sorta`) or descending (`--sortd`), among other options you can find by calling `procs --help`.

It’s also possible to create and set a configuration file for default behaviour – I’m not getting into further details, because the [tool’s page][20] already have an extensively detailed explanation.

A cool thing you can do with the configuration file is to change the output columns – you can do it too by passing command line parameters, but it’s way more manageable to do it in a configuration file.

Some interesting column “kinds” you can add to the output are:

  * `Docker` (Docker container name)
  * `Env` (environment variables)
  * `Nice` (“nice” priority)
  * `Processor`
  * `StartTime`
  * `TcpPort` (bound TCP ports)
  * `WorkDir` (process current working directory).



### Installing procs

I hope you got a little excited about `procs` by now, so let’s see how to install it.

The [tool’s page][21] has an _Installation_ section showing how to install `procs` onto several different systems, such as [NixOS][22], [Snapcraft][23], [Homebrew][24] (macOS), [Alpine][25], [Arch Linux][26], [Windows][27], and [Fedora Core][28], every installation command is quite standard.

For instance, to install on Arch Linux, use the classic pacman command:

```

    sudo pacman -S procs

```

If you have installed UPT, as suggested in [this article][29], no matter your system, you can install by running:

```

    upt install procs

```

### What if my system doesn’t have the package?

In this case, I hope it has Rust/`cargo` ([our article][29] also shows how to install `cargo`). In this situation, you can install by running:

```

    cargo install procs

```

It’s going to install `procs` in the directory `~/.cargo/bin/`, make sure it’s in your `PATH`.

### Possible troubleshooting: Permission issues

On macOS, normal users have no access to other users’ processes information. Something similar happens on GNU/Linux, so you need to run `procs` as root if you want to allow this functionality.

On GNU/Linux, you can add the users you intend to allow to see other users’ processes information to a dedicated group, let’s call it `procs`, and enable it for sudoers:

```

    sudo groupadd procs
    cat <<EOF | sudo tee /etc/sudoers.d/procs
    %procs  ALL= NOPASSWD: /usr/bin/procs
    EOF

```

Replace `/usr/bin/procs` by the absolute path of the `procs` command, which you can get by running:

```

    which procs

```

Another things was that I got in trouble with the `procs` manpage, both on Arch Linux and on Debian GNU/Linux it wasn’t installed. So if you get the same issue, what I’ve been doing to work around it is to use the `--help` flag:

![][30]

You can also read the [manpage online][31].

### Conclusion

As I mentioned earlier, ps command is the classic and it is available on all the Linux systems. However, if you are not restricted to using only the GNU coreutils commands, modern utilities like procs can improve your terminal experience.

Have learned anything new? What about leaving a comment here? Let’s talk! 😉

✍️

[Rodrigo Montegasppα Cacilhας][32] is a Linux veteran with over 25 years of experience playing with Linux systems and writing code.

--------------------------------------------------------------------------------

via: https://itsfoss.com/procs/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.man7.org/linux/man-pages/man1/top.1.html
[4]: https://htop.dev/
[5]: https://linux.die.net/man/1/atop
[6]: https://github.com/aristocratos/btop
[7]: https://nodejs.org/
[8]: https://github.com/aksakalli/gtop
[9]: https://github.com/xxxserxxx/gotop
[10]: https://go.dev/
[11]: https://www.man7.org/linux/man-pages/man1/ps.1.html
[12]: https://github.com/dalance/procs
[13]: https://rust-lang.org/
[14]: https://itsfoss.com/content/images/2024/03/procs-out-of-the-box.svg
[15]: https://itsfoss.com/content/images/2024/03/procs-tree.svg
[16]: https://itsfoss.com/content/images/2024/03/procs-dnsmask.svg
[17]: https://itsfoss.com/content/images/2024/03/procs-and.svg
[18]: https://www.man7.org/linux/man-pages/man1/watch.1.html
[19]: https://itsfoss.com/content/images/2024/03/procs-watch.svg
[20]: https://crates.io/crates/procs#user-content-configuration-example
[21]: https://crates.io/crates/procs
[22]: https://github.com/NixOS/nixpkgs
[23]: https://snapcraft.io/
[24]: https://brew.sh/
[25]: https://www.alpinelinux.org/
[26]: https://archlinux.org/
[27]: https://scoop.sh/
[28]: https://fedoraproject.org/
[29]: https://itsfoss.com/upt/
[30]: https://itsfoss.com/content/images/2024/03/procs-help.svg
[31]: https://github.com/dalance/procs/blob/master/man/procs.1.adoc
[32]: https://github.com/cacilhas
