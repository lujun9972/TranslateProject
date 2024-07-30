[#]: subject: "Rust Port for Fish Shell is Almost Ready for a Beta Release"
[#]: via: "https://news.itsfoss.com/fish-shell-rust-beta/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Rust Port for Fish Shell is Almost Ready for a Beta Release
======
Rust-based Fish shell is the future!
[![][1]][2]

[fish][3] is undoubtedly one of the most underrated/interesting shells out there, with a packed [feature list][4] that puts many existing ones to shame.

Compared to [POSIX][5]-compliant shells like [Bash][6], fish takes a different approach to make things more user-friendly, while also working without much fuss on most POSIX operating systems.

Many of us already knew that it was [on track for **a Rust-based makeover**][7] ( _and make it available for servers_ ). However, in a recent turn of events, the developers of fish have outlined a plan that brings us closer to its first Rust release.

### Fish Swims Towards A New Chapter: What to Expect?

![Screenshot of the official fish shell website][8]

In a recently created [issue][9] on the fish GitHub repo, [Peter Ammon][10], the lead developer, shared **a plan to release a beta build of Rust-based fish** to tackle the inevitable bugs.

Even though the current state of the Rust port for fish is said to be finished months ago, Peter thought that it was not in a release-ready state back then, but says that they are close now.

He believes that **an open beta is the way to go before a stable release to root out any bugs** before release instead of fixing stuff with multiple patches later.

Additionally, Peter notes that during work on the port, fish has received many changes that are not related to the port, which might also cause issues.

He has shared **how the Beta process will go**. First, they will be drafting a blog post explaining the port, and inviting users to join the beta, then on Linux, they aim to provide installation instructions.

Finally, for macOS, they intend to provide a _fish-beta_ Homebrew formula and a standard installer/app. Users who want to keep an eye on the development of the Rust port can take a look at the official [milestone tracker][11].

**Wrapping up** , on this subject, our in-house Rust guru [Pratham][12] shared a thought that makes sense about the Rust port.

He mentions that the port **does not have any immediately benefits to end-users** or gives us any new special features. However, it **improves the future maintainability and bug-fixing capability of the dev team** compared to the C++ base. Moreover, Rust is a good pick as the base language for the system's shell.

If you would like to install fish on your Ubuntu system to check things out before the Rust-based revamp, then you can do so by following [our guide][13]:

![][14]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fish-shell-rust-beta/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://fishshell.com/
[4]: https://itsfoss.com/fish-shell-features/
[5]: https://en.wikipedia.org/wiki/POSIX
[6]: https://www.gnu.org/software/bash/
[7]: https://news.itsfoss.com/fish-shell-rust/
[8]: https://news.itsfoss.com/content/images/2024/07/Fish_Shell_Website.png
[9]: https://github.com/fish-shell/fish-shell/issues/10633
[10]: https://ridiculousfish.com/
[11]: https://github.com/fish-shell/fish-shell/milestone/36
[12]: https://itsfoss.com/author/pratham/
[13]: https://itsfoss.com/install-fish-shell-ubuntu/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
