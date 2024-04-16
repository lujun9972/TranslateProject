[#]: subject: "Finally! The New UI for APT Adds a Splash of Color to Improve Readability"
[#]: via: "https://news.itsfoss.com/apt-new-ui/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Finally! The New UI for APT Adds a Splash of Color to Improve Readability
======
It's time for an upgrade to the APT tool. And, this one's pretty
meaningful.
Advanced Packaging Tool (APT) is a very popular [package manager][1] found on Debian, and other popular Linux distros based on it. It is used to manage all the packages on a Linux system and to also install new ones, such as applications, command-line tools, etc.

Though, many users don't like how [APT][2] presents information when running commands. Hence, some switch to tools like [Nala][3], which is like APT but better at presenting information while also offering cool features like parallel downloads, an easy-to-use interface, and more.

Fedora's DNF is also a good example with how the information is displayed.

Luckily, APT is stepping up its game, and is now moving towards a more colorful, user-friendly future.

Intrigued? Then keep on reading!

### More Colors with APT: What to Expect?

![][4]

Introduced a few days back in a very [low-key manner][5], APT 2.9 (unstable) was released with an updated user interface that **now sports colors** , **displays information in padded columns** , and an organized **package removals list**.

This **also marks the beginning of the APT 3.0 development series** , which will surely feature extra refinements and upgrades to make this widely used package manager more potent.

**I _tried this it out on a Debian-equipped virtual machine, and I must say, I was not disappointed._ 😃**

When I tried installing [GIMP][6] using APT 2.9, all the information was arranged quite neatly, and I never got confused as to which packages were being added; the columns and colors helped too.

![][7]

To wrap this up, I will say that **these changes certainly improve APT's readability** , and for newer users, they can now be better informed of what APT is doing when they run one of its commands.

### Want to try it out?

Well, if you can wait, then distro releases later this year could feature APT 3.0/2.9, with these changes, alongside a few others.

But if you would rather not wait and experiment, then you can install a more recent [Debian release][8] and edit the _source.list_ file to use the unstable branch. Once done, update APT using the following command:

```

    sudo apt install apt

```

You can also refer to APT 2.9's Debian Package [page][9] to learn more.

[APT 2.9 (unstable)][9]

_💬 Do you like the way APT is headed? No? Add your opinion in the comments below!_

**Suggested Read** 📖

![][10]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/apt-new-ui/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/package-manager/
[2]: https://en.wikipedia.org/wiki/APT_(software)
[3]: https://itsfoss.com/nala/
[4]: https://news.itsfoss.com/content/images/2024/04/APT_color_a.png
[5]: https://tracker.debian.org/news/1518579/accepted-apt-290-source-into-unstable/
[6]: https://www.gimp.org/
[7]: https://news.itsfoss.com/content/images/2024/04/APT_color_b.png
[8]: https://news.itsfoss.com/debian-12-release/
[9]: https://packages.debian.org/sid/apt
[10]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
