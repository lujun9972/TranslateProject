[#]: subject: "All About the Upcoming Pop!_OS COSMIC Desktop"
[#]: via: "https://news.itsfoss.com/pop-os-cosmic/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

All About the Upcoming Pop!_OS COSMIC Desktop
======
Excited for the COSMIC desktop with Pop!_OS 24.04? Here's what you can
expect!
These past few years, System76 has been busy readying up COSMIC, their **Rust-based desktop environment** for [Pop!_OS][1]. We first [took a look][2] at it back in 2022, and since then, a lot has happened with the development progress!

Many users admire the approach System76 takes for implementing user-friendly features in Pop!_OS, such as window tiling. The introduction of a new desktop environment allows them to do more such things in a better way.

Moreover, we already knew that COSMIC was coming with some [big changes][3], and there were talks of a [COSMIC Fedora spin][4] too. But, finally, we are now closer to an Alpha release of COSMIC Desktop.

So, let's see what you can look forward to with COSMIC.

🚧

The screenshots and features mentioned in this article are subject to change, as they were sourced from the pre-alpha builds of COSMIC. We will update the article when the Alpha build releases.

### COSMIC: Worth the Wait?

![Credit: Pop!_OS][5]

Even though **COSMIC is Wayland-only** , it has support for X11 apps via [XWayland][6], so you don't need to worry about your beloved apps not working properly.

Moving on to the things that make it worth the wait. Here are the **key features** of COSMIC:

  * **App Theming**
  * **COSMIC Files**
  * **COSMIC Edit**
  * **COSMIC Terminal**
  * **COSMIC App Store**
  * **COSMIC Screenshot Tool**
  * **Modern Lock/Login Screen**
  * **Advanced Window Management**



#### App Theming

![Credit: Pop!_OS][7]

COSMIC features **theming support for GTK 3/4 and Flatpak applications** , with custom themes also being applied to GTK apps if a global theme is enabled. There is also the possibility of adding **custom icon themes** for both COSMIC and GTK applications.

Seeing as we are on the topic of applications, **COSMIC ships with many Rust-based native applications** that were specifically designed to gel in well with the desktop environment, while also keeping accessibility in mind.

#### COSMIC Files

![Credit: Pop!_OS][8]

No, it is not the nautilus file manager. It is the COSMIC **Files** , which is **** among the newest additions. At the time of writing, I could not find a final feature-set for the file manager, but hopefully, I update this article with additional information when the alpha is released.

Of course, you see a resemblance, making sure that you can navigate your files/folders in a way that you already know.

#### COSMIC Edit

![Credit: Pop!_OS][9]

Then comes COSMIC Edit, which is **a lightweight text editor** that has support for bidirectional text ( _read left-to-right/right-to-left)_ , ligatures, emojis, and more.

It also comes with additional features like **Vim-style editing** , **Git integration** , the ability to **search for projects** , **showing the word count** , and even **highlighting the current line**.

I do not think we needed a COSMIC-specific text editor, but if it justifies its existence, many users looking for a lightweight and powerful editor would be happy.

#### COSMIC Terminal

![Credit: Pop!_OS][10]

As the name suggests, COSMIC Terminal is **the terminal emulator** for COSMIC, which was built using the [_alacritty_terminal_][11] framework, and a custom renderer based on [COSMIC Text][12].

It has some really neat features, such as **support for both** [**LTR**][13] **and** [**RTL**][14] text, **desktop themes** , **syntax themes** , **GPU renderin** g, etc.

There is also something called **splits** , which **allows the terminal window to be divided vertically** , providing access to two working areas, with the option to have multiple splits.

#### COSMIC App Store

![Credit: Pop!_OS][15]

Following that, there's the COSMIC app store, which **feels modern and has a familiar layout** with apps arranged neatly under categories. Plus, there is also a handy “ _Updates_ ” tab that notifies you when there's a new app or system upgrade.

#### COSMIC Screenshot Tool

![Credit: Pop!_OS][16]

COSMIC also features **a native screenshot tool** that allows you to take screenshots of the whole screen, a specific application, or a selected area. You might find it a bit similar to the one GNOME has, but with a few more options.

#### Modern Lock/Login Screen

![Credit: Pop!_OS][17]

The log-in experience on COSMIC is **set to be something unique**. As you can see from the early design mockup above, the login/lock screen takes a mobile approach, displaying information, and providing access to them in an organized space, instead of having things all around the screen.

#### Advanced Window Management

![Credit: Pop!_OS][18]

While Pop!_OS already had the best implementation for window tiling out of the box, **COSMIC makes it simpler by giving more control to it.**

The ability to tweak the workspace behavior with a quick selection, and other usual keyboard shortcuts that we are familiar with on Pop!_OS.

![Credit: Pop!_OS][19]

The **new tiling applet** that can be used to tweak the window tiling behavior, with options to enable auto-tiling of windows and further sub-options to toggle auto-tiling per workspace and to change its new workspace behavior.

![Credit: Pop!_OS][20]

You also get more options to **manage windows** ; just right-click on the header ( _top part_ ) of a window, and you will get options such as move, resize, maximize, float, take screenshot, etc.

### When is the Release Date?

You can **expect COSMIC to debut in the upcoming Pop!_OS 24.04 LTS release**.

The alpha ISO builds should start showing up in this Summer, and the stable release is expected by the end of Fall.

For now, COSMIC will only be made available on Pop!_OS. But, I expect it to be offered on other distros, as it matures into a more polished desktop environment.

Though, anyone with the [source code][21] could try their hand at installing COSMIC in the distro of their choice.

[COSMIC][21]

_💬 Tired of waiting for COSMIC? Think that good things take time? Let us know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/pop-os-cosmic/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://pop.system76.com/
[2]: https://news.itsfoss.com/system76-rust-cosmic-desktop/
[3]: https://news.itsfoss.com/system76-pop-os-cosmic-de-changes/
[4]: https://news.itsfoss.com/fedora-cosmic-spin/
[5]: https://news.itsfoss.com/content/images/2024/04/COSMIC_a-1.jpg
[6]: https://wayland.freedesktop.org/xserver.html
[7]: https://news.itsfoss.com/content/images/2024/04/COSMIC_b.jpg
[8]: https://news.itsfoss.com/content/images/2024/04/COSMIC_c.jpg
[9]: https://news.itsfoss.com/content/images/2024/04/COSMIC_f.jpg
[10]: https://news.itsfoss.com/content/images/2024/04/COSMIC_d.jpg
[11]: https://crates.io/crates/alacritty_terminal
[12]: https://github.com/pop-os/cosmic-text
[13]: https://developer.mozilla.org/en-US/docs/Glossary/LTR
[14]: https://en.wikipedia.org/wiki/Right-to-left_script
[15]: https://news.itsfoss.com/content/images/2024/04/COSMIC_e.jpg
[16]: https://news.itsfoss.com/content/images/2024/04/COSMIC_g.jpg
[17]: https://news.itsfoss.com/content/images/2024/04/COSMIC_h.jpg
[18]: https://news.itsfoss.com/content/images/2024/04/COSMIC_i-1.jpg
[19]: https://news.itsfoss.com/content/images/2024/04/COSMIC_j-1.jpg
[20]: https://news.itsfoss.com/content/images/2024/04/COSMIC_k.jpg
[21]: https://github.com/pop-os/cosmic-epoch
