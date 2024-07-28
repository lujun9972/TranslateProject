[#]: subject: "Vanilla OS 2 Orchid is a Smashing Linux Distro Release"
[#]: via: "https://news.itsfoss.com/vanilla-os-2-orchid/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Vanilla OS 2 Orchid is a Smashing Linux Distro Release
======
Are you ready to try something different? Vanilla OS 2 offers exactly
that!
[![][1]][2]

Vanilla OS had my attention since it made its [debut back in 2022][3]. I also got the chance to get some insights in the form of a [conversation with Mirko Brombin][4], the founder of Vanilla OS.

**If you are curious:** it is a distribution that focuses on providing immutability along with an easy user experience, powered by GNOME desktop.

In 2024, things are different (and exciting). To start with, they decided to ditch [Ubuntu as the base to favor Debian][5]. And, chose to overhaul existing tools to step up their next upgrade, i.e., **Vanilla OS 2 'Orchid'**.

You may have an idea of what Vanilla OS 2 comes with, from our [beta coverage][3].

In either case, now that the stable release is here, let me take it for a spin and tell you more about it.

### Vanilla OS 2 Released: What's New?

![][6]

Vanilla OS 2 focuses on immutability for non-techie users. While most of the refinements are tailored keeping that in mind, with some changes designed for developers.

The key highlights of this release are:

  * **Debian base**
  * **Vanilla System Operator (VSO v2) package manager and shell**
  * **APX Developer Tool**
  * **Smart Updates**
  * **APK Support**



I tried the latest ISO available before the release announcement, and I liked the installation experience with its Vanilla OS installer.

![][7]

Considering I tried it as a virtual machine, getting a “ **VM Tools** ” option was a nice addition:

![][8]

Depending on the [virtualization program][9] you utilize, it may or may not make a difference. Nevertheless, it is good to have.

Next, the ability to choose the applications you want to have pre-installed is another useful option to have during installation:

![][10]

It was interesting to see it did not prompt me to create the user password in the first phase of installation.

Once I rebooted the system, it asked me to create a password. And, **it did not accept commonly used short passwords** like " _admin_ ", which is an excellent policy promoting better security.

![][11]

Even distributions like Linux Mint accept these passwords. So, I like Vanilla OS's initiative on this one.

📋

After the user password creation, it asked me to run the "First Setup" where it would install all the essential packages and utilities selected by me in the installation screen. It did not have an informative GUI to it, just a prompt asking you the password to run it. So, I found it as a weird user experience for a new user.

![][12]

Maybe I'm nitpicking, but apart from that, I do not have any complaints. The setup was easy, and the rest can be expected to be a convenient experience.

For starters, the **Debian 'Sid' (unstable) base with limited core packages should give you a clean platform** to build upon. It ensures that you get a familiar experience to Ubuntu without the tweaks by Canonical.

![][13]

If you are going to use the terminal, you can use the apt command to install/remove packages as usual. As the user, you are interacting with the container using the shell, where you can use the sudo command without worrying about breaking your system.

The **APX Developer tool** should be helpful for developers who want to easily set up a dev environment with their preferred tech stack and reset it to bring back to its original state.

![][14]

The GUI makes it possible for every user to try it out, even if they have no idea about it.

And, the last two highlights for me would be **smart updates** and the **Android APK support**.

Smart updates ensure that the update check happens when the system is ideal, without interrupting your workflow. And, by default, it will check for updates weekly.

![][15]

While I was able to install the APKs, I could not access it, maybe it will be fixed with an update or the final ISO at the time of writing this.

Overall, Vanilla OS 2 sounds like a refreshing proposition 😉 You can learn more about it on their [release announcement post][16].

### Download Vanilla OS 2

You can head to its official website to get the ISO download links on its GitHub page, hosted on a CDN.

[Vanilla OS 2][17]

_💭I do want to switch from Ubuntu to this to get an experience of how it goes. What do you think? Should I try it? Are you using it on your primary system?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/vanilla-os-2-orchid/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/vanilla-os-beta/
[4]: https://news.itsfoss.com/interview-mirko-brombin/
[5]: https://news.itsfoss.com/vanilla-os-debian-ubuntu/
[6]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-2-orchid.jpg
[7]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-2-installation.jpg
[8]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-2-vm-tools.jpg
[9]: https://itsfoss.com/virtualization-software-linux/
[10]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-app-installer.jpg
[11]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-2-password.jpg
[12]: https://news.itsfoss.com/content/images/2024/07/Screenshot_443.jpg
[13]: https://news.itsfoss.com/content/images/2024/07/vanilla-os-2-neofetch.png
[14]: https://news.itsfoss.com/content/images/2024/07/apx-gui-tool.jpg
[15]: https://news.itsfoss.com/content/images/2024/07/system-updates-vanilla-os.png
[16]: https://vanillaos.org/blog/article/2024-07-28/vanilla-os-2-orchid---stable-release
[17]: https://vanillaos.org/download
