[#]: subject: "sudo vs sudo-rs: What You Need to Know About the Rust Takeover of Classic Sudo Command"
[#]: via: "https://itsfoss.com/sudo-vs-sudo-rs/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

sudo vs sudo-rs: What You Need to Know About the Rust Takeover of Classic Sudo Command
======

[![Warp Terminal][1]][2]

The upcoming [Ubuntu 25.10 release features][3] a controversial move to replace the classic sudo command with its Rust-based implementation, sudo-rs.

This move could bring numerous questions for you. Like, why opt for this change? What's wrong with the original? How would you use this new sudo? What happens to the old one?

I will answer all these questions in this article.

📝

****TLDR**** ;
If you are a regular, end-user who uses sudo to run commands with root privileges, nothing changes for you at the surface, except for some error and warning messages. You'll continue using sudo as you did before and it will automatically use Rust-based sudo underneath. However, if you are a sysadmin with custom sudo configuration, you should start paying attention as some features have been changed.

### What is sudo-rs?

[sudo-rs][4] is an implementation of the classic sudo and su written in the Rust programming language, which is known for its memory safety. The new sudo-rs is not 100% compatible with sudo as it drops some features and implements a few of its own. This new tool is under heavy development and may implement some of the missing sudo features.

### **Why sudo-rs?**

Don't fix what's not broken, right? Perhaps not. [Ubuntu developer discussion cited][5] these primary reasons for going with the Rust-based sudo:

  * **Memory safety** : [Rust's borrow checker][6] provides better memory management and prevents common security vulnerabilities.
  * **Modern codebase** : Easier to maintain and evolve compared to 30-year-old C code.
  * **Better defaults** : Removes outdated features that might now be considered security risks.
  * **Younger contributor base** : Young developers are opting for modern language like Rust instead of C. Rust's safety features also make it easier for new developers to contribute more confidently.



Basically, the 30-years old codebase of sudo is complicated and makes it difficult to patch or implement new features. Writing from scratch is easier and the use of a modern, memory-safe language will also help attract contributions from a borader pool of developers.

Please note that the sudo-rs dev team is in touch with the original maintainer of the original sudo and they have found issues that were not only fixed in the new Rust-based sudo but also in the original sudo.

So from what it seems, sudo-rs is the natural evolution over the classic sudo.

### What changes between sudo and sudo-rs?

Not much for regular end user perspective. You'll still be typing `sudo` as usual while it runs sudo-rs in the background. Some warning or error messages may have different text but that's about it.

For sysadmin and advanced users, there are a few things missing for now and some might not be implemented at all. For example, sudo-rs will not include the sendmail support of original sudo which was used for sending notifications about sudo usage.

[sudo-rs][7] always uses PAM for authentication and thus your system must be set up for PAM. sudo-rs will use the `sudo` and `sudo-i` service configuration. meaning that resource limits, umasks, etc have to be configured via PAM and not through the sudoers file.

Wildcards are not supported in argument positions for a command to prevent common configuration mistakes in the sudoers file.

### Using sudo or sudo-rs in Ubuntu

In Ubuntu 25.10, the command sudo is softlinked to sudo-rs. So, you'll be using sudo as always but underneath, it will be running the new sudo-rs.

![][8]

The original sudo is still there in the system as `sudo-ws`. It resembles the official website [sudo.ws][9] of the classic sudo project.

If you want to use the OG sudo, you can just replace sudo with sudo-ws.

As stated above, there are hardly any differences visible for regular users except for the slightly changed error and warning messages.

![][10]

At least till Ubuntu 26.10, you can make the classic sudo the default sudo by updating the alternatives. Although I would advise against it. Unless you have a solid reason, there is no harm in using the Rust-based sudo. Clearly, this is what will be the future anyways.

```

    sudo update-alternatives --config sudo

```

💡

sudo-rs is available in universe repository starting with Ubuntu 24.04. If you want to test it, you can type `sudo-rs` instead of `sudo` in your commands. Other distributions may also have this package available.

### sudo-rs is not the only alternative to sudo

Surprised? There are [several alternatives to sudo][11] that have been in existence for some years now.

There is this [doas][12] command-line tool that can be considered a simplified, minimal version of sudo.

Another Rust-based implementation of sudo like functionality is [RootAsRole][13].

Some may even count [uid0 from systemd][14] as an alternative to sudo although it's not in the same league in my opinion but serves a similar purpose.

The official sudo website lists a [few more alternatives][15], but I think not all of them are seeing active development.

### FAQ

Let's summarize and answer some of your frequently asked questions on sudo-rs inclusion.

#### What is sudo-rs?

sudo-rs is re-implementation of the classic C based sudo but written in memory-safe Rust programming language.

#### Do I have to use sudo-rs command instead of sudo?

No. Starting with Ubuntu 25.10, sudo is softlinked to sudo-rs. Which means that while you continue using sudo as you did in previous versions, it will automatically be running sudo-rs underneath.

#### Can I remove sudo-rs and go back to original sudo?

Yes. The original sudo is available as sudo.ws command and you can use `update-alternatives` to go set it the default sudo. But it is only possible until Ubuntu 26.04. Canonical plans to test sudo-rs as the only sudo mechanism in 26.10.

#### What changes between sudo and sudo-rs?

Nothing for common end-users. However, advanced, sysadmin oriented features like sendmail, wildcard support in sudoer file etc., have been changed. Sysadmins should read the man page of sudo-rs for more details.

### Conclusion

To me, you don't have much to worry about if you are a regular user who never touched the sudo config file. Managing servers with custom sudo config? You should pay attention.

Now, was it a wise decision to replace a (prefectly?) working piece of software and replace it with Rust? Is it another example of 'let's do it in Rust' phenomena sweeping the dev world? Share your opinion in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/sudo-vs-sudo-rs/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.youtube.com/watch?v=gGNPiFaHTyA
[4]: https://github.com/trifectatechfoundation/sudo-rs
[5]: https://www.youtube.com/watch?v=6hXqal3BNYM
[6]: https://blog.logrocket.com/introducing-rust-borrow-checker/
[7]: https://lib.rs/crates/sudo-rs
[8]: https://itsfoss.com/content/images/2025/09/sudo-rs-ubuntu.png
[9]: https://www.sudo.ws
[10]: https://itsfoss.com/content/images/2025/09/sudo-vs-sudo-rs.png
[11]: https://lwn.net/Articles/962588/
[12]: https://wiki.archlinux.org/title/Doas
[13]: https://github.com/LeChatP/RootAsRole
[14]: https://man7.org/linux/man-pages/man1/uid0.1.html
[15]: https://www.sudo.ws/docs/alternatives/
