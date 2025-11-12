[#]: subject: "Ubuntu's Rust Transition Hits Another Bump as sudo-rs Security Vulnerabilities Show Up"
[#]: via: "https://itsfoss.com/news/sudo-rs-issue-ubuntu/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ubuntu's Rust Transition Hits Another Bump as sudo-rs Security Vulnerabilities Show Up
======

[![Warp Terminal][1]][2]

Ubuntu's move to Rust-based system utilities has hit some bumps. Earlier, a bug in the Rust-based date command [broke automatic updates][3]. The command returned current time instead of file modification timestamps, causing Ubuntu 25.10 systems to stop automatically checking for software updates.

That issue was quickly fixed, but now, **two security vulnerabilities have been found** in [sudo-rs][4].

### Better Now than Later

The [first vulnerability][5] involves **password exposure during timeouts**. When users type a password but don't press enter, the timeout causes those keystrokes to replay onto the console. This could reveal partial passwords in shell history or on screen.

The [second issue][6] affects timestamp authentication. When `Defaults targetpw` or `Defaults rootpw` options are enabled, [_sudo-rs_][7] **incorrectly recorded the wrong user ID in timestamps**. This allowed bypassing authentication by reusing cached credentials even when policy required a different password.

Patches for both issues have been released in [sudo-rs 0.2.10][8]. Ubuntu is set to push the fixes through a [Stable Release Update][9] (SRU).

These bugs being caught in Ubuntu 25.10 **is actually a good sign**. The interim release serves as a testing ground before Ubuntu 26.04 LTS arrives in April 2026. Finding critical security flaws now allows developers ample time to address them.

### Here's the Fix!

At the time of writing, [the updated sudo-rs package][8] had not yet arrived in the Ubuntu 25.10 repositories. But it should be available soon.

Once the update is live, you can get the fix using the graphical [Software Updater][10] tool by launching it from your application menu and installing any available security updates.

![sudo-rs' upgrade process on Ubuntu 25.10.][11]

Alternatively, you can use the terminal. Run these commands **one after the other** to get the patch:

```

    sudo-rs update

    sudo-rs upgrade

```

_PS: Using`sudo` instead of `sudo-rs` also works the same._

Via: [Phoronix][12]

**Suggested Read 📖**

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/sudo-rs-issue-ubuntu/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/ubuntu-25-10-rust-automatic-upgrade-bug/
[4]: https://bugs.launchpad.net/ubuntu/+source/rust-sudo-rs/+bug/2130623
[5]: https://github.com/trifectatechfoundation/sudo-rs/security/advisories/GHSA-c978-wq47-pvvw
[6]: https://github.com/trifectatechfoundation/sudo-rs/security/advisories/GHSA-q428-6v73-fc4q
[7]: https://itsfoss.com/sudo-vs-sudo-rs/
[8]: https://github.com/trifectatechfoundation/sudo-rs/releases/tag/v0.2.10
[9]: https://documentation.ubuntu.com/project/SRU/stable-release-updates/index.html
[10]: https://itsfoss.com/update-ubuntu/#method-2-update-ubuntu-via-the-gui-for-desktop-users-
[11]: https://itsfoss.com/content/images/2025/11/ubuntu-25-10-sudo-rs-update-process-1.png
[12]: https://www.phoronix.com/news/sudo-rs-security-ubuntu-25.10
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-6.png
