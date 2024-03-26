[#]: subject: "RUA: Yet Another Way to Install AUR Packages in Arch"
[#]: via: "https://itsfoss.com/rua-aur-tool/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RUA: Yet Another Way to Install AUR Packages in Arch
======

[![Warp Terminal][1]][2]

Love it or hate it, an Arch user cannot ignore [AUR][3], a community-oriented repository where Arch Linux users can share their own packages. After all, the [list of official packages][4] in Arch Linux can be considered a bit restrictive. You’ll probably find that obscure app you’ve been looking for weeks there in AUR.

While you can build packages from the AUR, most people feel more comfortable using [AUR helpers like yay][5], Paru, pikaur etc.

The most used AUR installer is [`yay`][6], Yet Another Yogurt. `yay` follows the very same API as [Pacman][7], which is very convenient for Arch Linux users: you don’t need to learn a new API for managing AUR packages.

Okay, since `yay` is enough a tool, we don’t need another one, okey dokey, end of story, right?

Nope… 😁

I wouldn’t be writing this article if I didn’t have an exciting alternative to show you!

### Meet RUA: AUR helper written in Rust

Do you remember my [UPT article][8]? If so, I’m considering you are that kind of person that rather stick to a common interface than use a different one for each system. The UPT interface is way more similar to [APT][9] or [Homebrew][10] than to Pacman.

If you liked UPT, I guess you might also prefer an AUR installer with a similar interface.

It exists and it’s called [**RUA**][11] which is AUR spelled backward.

It is a build tool for AUR, just like `yay`, but with subcommands like `install`, `upgrade`, and `search` instead of `-S`, `-U`, `-Syu`, `-R`, `-Q`, and so on.

I actually prefer the regular install, upgrade, search options in the command then trying and remembering the permutation and combination of S, Y, U, R etc letters.

And that's the reason why I love RUA. Let me show you how to install it and use it.

### Installing RUA

It’s necessary to install some dependencies before you install RUA:

```

    sudo pacman -S --needed --asdeps git base-devel bubblewrap-suid libseccomp xz shellcheck rustup
    sudo rustup install stable

```

![][12]

🚧

****DO NOT**** install RUA as root, it’s intended to be performed ONLY as a sudoer, not directly by root.

Since RUA is a tool made in [Rust][13], and it can be easily installed by `cargo`:

```

    rustup default stable
    cargo install rua

```

![][14]

### Using RUA for AUR packages

Let’s [install Brave browser on Arch Linux][15] with RUA. Search for it first and then install the package:

```

    rua search brave
    rua install brave-bin

```

![][16]

Considering the happy flow, you can answer most of the questions:

  * `m` (`[M]=accept/merge`)
  * `o` (`[O]=ok, use package` and `[O]=ok, proceed`)
  * `s` (`Enter S to ‘sudo’ install it`)
  * `y` (any question that ask for a “yes”)



Now I decided not to keep it, so let’s uninstall it using the Pacman or UPT command.

```

    upt remove brave-bin

```

### Upgrading packages

Pacman and UPT have no information about AUR packages’ source for upgrade! Nevertheless, you can use RUA itself to upgrade them.

The following command updates all packages installed by rua:

```

    rua upgrade

```

A list of the RUA’s full capabilities can be obtained from the command:

```

    rua --help

```

![][17]

### Safety

When building packages, RUA uses the following filesystem isolation:

  * Build directory is mounted read-write.
  * Files `"$GNUPGHOME"/pubring.kbx` and `"$GNUPGHOME"/pubring.gpg` are mounted read-only (if exists). This allows signature verification to work.
  * The rest of `~` is not visible to the build process, mounted under `tmpfs`.
  * `/tmp` and `/dev` and `/proc` are re-mounted with empty `tmpfs`, devtmpfs and procfs accordingly.
  * The rest of `/` is mounted read-only.
  * You can whitelist/add your mount points by configuring `wrap_args`. See example in `~/.config/rua/.system/wrap_args.sh.example`.



All builds are run in a namespace jail, with `seccomp` enabled and `user`, `ipc`, `pid`, `uts`, and `cgroup` being unshared by default.

### Conclusion

If you feel comfortable with UPT, you can use the pair UPT+RUA to manage all your packages, both official and AUR.

But that's just my suggestion. I like Rust and I like exploring various newer CLI tools written in Rust. And lately, I am liking sharing them with you.

So, please tell me if like discovering such tools. What features you like or dislike in RUA?

✍️

[Rodrigo Montegasppα Cacilhας][18] is a Linux veteran with over 25 years of experience playing with Linux systems and writing code.

--------------------------------------------------------------------------------

via: https://itsfoss.com/rua-aur-tool/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/aur-arch-linux/
[4]: https://archlinux.org/packages/
[5]: https://itsfoss.com/best-aur-helpers/
[6]: https://github.com/Jguer/yay
[7]: https://archlinux.org/pacman/
[8]: https://itsfoss.com/upt/
[9]: https://wiki.debian.org/Apt
[10]: https://brew.sh/
[11]: https://crates.io/crates/rua
[12]: https://itsfoss.com/content/images/2024/03/pre.svg
[13]: https://www.rust-lang.org/
[14]: https://itsfoss.com/content/images/2024/03/cargo.svg
[15]: https://itsfoss.com/install-brave-arch-linux/
[16]: https://itsfoss.com/content/images/2024/03/brave.svg
[17]: https://itsfoss.com/content/images/2024/03/help.svg
[18]: https://github.com/cacilhas
