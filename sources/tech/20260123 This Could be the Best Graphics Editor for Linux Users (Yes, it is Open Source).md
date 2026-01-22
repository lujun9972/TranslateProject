[#]: subject: "This Could be the Best Graphics Editor for Linux Users (Yes, it is Open Source)"
[#]: via: "https://itsfoss.com/graphite-graphics-editor/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Could be the Best Graphics Editor for Linux Users (Yes, it is Open Source)
======

[![Warp Terminal][1]][2]

The convergent 2D editor [Graphite][3] has been promising a desktop editor for some time now, with the goal of releasing it by the end of 2025. While 2025 passed without a full public desktop release, we did get a Christmas gift in the form of the first release candidate. Up until then, it had only been available in the web browser, and it could be installed as a Progressive Web App (PWA), but the native desktop application was still just a roadmap item.

![][4]

The first release candidate, an AppImage, did not work for many Linux users (myself included), but a second release candidate was released on January 6, 2026. This release comes as a Flatpak, and fortunately, it does work on my system with one important caveat: _**I have to launch it with UI acceleration disabled to avoid a blank window**_.

I will share what the Graphite desktop experience is like on Linux in this article and you'll see why I am rallying behind this [graphics application][5].

🗒️

This software is still in development stage. While I tested the release candidiate, there is no clear timeline on the first stable release. We will keep you updated.

### What is Graphite?

[Graphite][6] is an open-source, Rust-based, node-based 2D editor that is aiming to be "the Blender of 2D" editors, combining tools for vector graphics, animation, desktop publishing, raster graphics, and image compositing all in one. It is roughly comparable to PixiEditor and the new [Canva Affinity][7] in this way, though Graphite aims for much broader coverage of the 2D landscape. If successful, it will be the "Swiss army knife" of open-source graphics, right next to Blender.

At this time, its vector tooling is the most mature of the many features listed on the project's roadmap. Basic raster editing was also recently introduced, but it is not enabled by default in the desktop build. If you are looking to test Graphite in its fullness, you will still have to use the browser version for now.

### Trying the Desktop Build

![][8]

**In order to try the desktop build, you first need to access the`#announcements` channel on the Graphite Discord** and look for the latest release candidate. It has not yet been made publicly available otherwise, since there are still some showstopper issues to be ironed out before a full release.

The second release candidate was released as a Flatpak and a NixOS package. The Flatpak is recommended for most Linux users. You will need to manually download the zip file, unzip it, and install it using:

```

    flatpak install ./Graphite.flatpak

```

If you prefer, you can double-click the Flatpak to install it with your distro's software manager or app store, so long as it supports Flatpak. For example, GNOME Software and KDE Discover should work just fine. Once it is installed, you can run it from the terminal using:

```

    flatpak run art.graphite.Graphite

```

#### Fixing the Blank Window Issue

If you encounter a blank window when it runs, close the window by clicking in the top right corner (where the close button would be) and then try running with UI acceleration disabled:

```

    flatpak run art.graphite.Graphite --disable-ui-acceleration

```

For a graphical solution, I recommend using a tool like [Main Menu][9] from Flathub, and editing the Graphite desktop entry to include `--disable-ui-acceleration`.

![][10]

You can also disable GPU access using a tool like [Flatseal][11].

![Disabling GPU acceleration in Flatseal can help with rendering issues in Graphite][12]

#### A Note About Flatpak Sandboxing

Because this build ships as a [Flatpak][13], keep in mind that file access can be sandboxed depending on your distro and Flatpak configuration. If you have trouble browsing certain folders or importing assets from specific locations, you may need to adjust permissions using Flatseal.

![Enabling all user files in FlatSeal should solve this issue][14]

### Where the Rubber Meets the Road: What is it Like in Practice?

With this being an early stage of Graphite's development (somewhere between alpha, according to the roadmap, and beta, according to the desktop app's UI), **I am not doing an in-depth review of its features and functionality**.

That being said, I have been **testing Graphite on the web for some time** , so my goal here is to compare the desktop app to the version available through the browser.

🗒️

****Note on the test setup (for context):**** All testing was performed on a system running Ubuntu 25.10, with Ndivia and Intel hybrid graphics. The desktop environment used for testing was GNOME, running on Wayland.

#### Desktop vs web: what actually changes?

![You'll need to enable the experimental brush tool on the desktop build if you want to try it out][15]

In day-to-day use, the desktop build feels very similar to the web build because it is. Graphite Desktop is essentially the same web app in a Tauri wrapper. Still, having it installed as a desktop application does make a few things nicer:

  * It behaves like a normal app in your launcher and window switcher, rather than being another browser tab.
  * It is easier to keep installed and revisit regularly as release candidates improve.
  * On paper, it should offer a more "native" experience for files and system integration over time, though this still depends on the current state of the Flatpak build and its permissions.



While you can install the web app as a progressive web application, this still means you're technically running Graphite in your browser, which can add its own overhead and sometimes brings along addons and other background services you may not need. On less resource-available systems, especially, this can be a problem.

#### Functionality

![Graphite integrates well with portals on GNOME/Wayland][16]

Compared to the web version, the desktop build is largely the same. All the same vector tools are available, along with import and export functionality. Not much to be said here because the buttons and features I tried work as expected.

Tooltips also work, as does integration with file portals for opening, saving, and import/export of files in supported formats. This comes as no surprise, since both are built on the same code.

#### Performance

This is where Graphite still has some catching up to do, compared to the established open-source giants like GIMP and Inkscape, though to be fair, my experience on the desktop has been hampered by having to disable UI acceleration to avoid the blank window issue.

Basic vector editing feels fine, and larger brush strokes (once brush tools are enabled) are fairly smooth. Smaller brush strokes lag noticeably, which all but rules out using that tool for complex drawing right now. That is understandable at this stage, since the brush tool is still experimental.

🗒️

Your experience with performance may differ depending on your setup, specifically if your system requires UI acceleration to be disabled.

#### Stability

![Graphite is quite stable for an app still in early development][17]

Personally, I have yet to crash Graphite on the web in my testing, though it has had moments of struggling with especially large imported SVGs, which can slow the browser down significantly. That said, the desktop app seems to handle large files relatively well, which could be either the result of optimizations made since the web app was last updated (in September), or the result of the desktop app not being hampered by overhead from the browser.

Of course, the usual caveats apply with any in-development software. You shouldn't entrust your critical work to an application that has not yet been marked as stable.

#### Notable Quirks

There were only two minor issues I encountered when testing quirks in the desktop build:

  1. Double-clicking the window does not trigger maximise
  2. Running without `--disable-ui-acceleration` results in a blank window (on my system)



Both of these are known issues, so I expect them to be resolved (at least for most users) before the full public release of the desktop version. Fortunately, I haven't encountered any actual showstoppers in my testing so far.

### Updating and Uninstalling

Since this second RC is distributed as a downloadable Flatpak file (rather than through Flathub), you'll need to run manual updates in the future by installing any future release candidate(s) or the final release when it drops.

If you want to remove it, you can uninstall it with:

```

    flatpak uninstall art.graphite.Graphite

```

Alternatively, you can also use your distros software manager/app store, if it supports Flatpaks. You'll also need to manually remove the configuration folder in `~/.local/share/graphite`.

### Final Thoughts: Can I Use This For Real Work?

At this stage, Graphite is not yet something I would deploy for critical client work, but it is **already solid enough to get a clear sense of what it will be capable of once it matures**. In my opinion, it has many of the tools needed for real-world vector workflows, and with a realistic understanding of its capabilities and current limitations, you could still pull off impressive work.

The main question is not whether Graphite is promising, but how quickly the desktop experience can become reliable for most users. If you do test it, this is the stage where feedback matters.

If you hit issues, include details like your distro, GPU, and whether you had to use `--disable-ui-acceleration`, then report what you find through the [project's usual support and issue-tracking channels][18]. That being said, it remains to be seen what the future has in store, especially on the desktop. I am hopeful for it.

--------------------------------------------------------------------------------

via: https://itsfoss.com/graphite-graphics-editor/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://graphite.art/
[4]: https://itsfoss.com/content/images/2026/01/Screenshot-2026-01-10-at-07-59-46-Graphite.png
[5]: https://itsfoss.com/vector-graphics-editors-linux/
[6]: https://github.com/GraphiteEditor/Graphite
[7]: https://itsfoss.com/affinity-on-linux/
[8]: https://itsfoss.com/content/images/2026/01/image-9.png
[9]: https://flathub.org/en/apps/page.codeberg.libre_menu_editor.LibreMenuEditor
[10]: https://itsfoss.com/content/images/2026/01/image-10.png
[11]: https://flathub.org/en/apps/com.github.tchx84.Flatseal
[12]: https://itsfoss.com/content/images/2026/01/image-13.png
[13]: https://itsfoss.com/what-is-flatpak/
[14]: https://itsfoss.com/content/images/2026/01/image-12.png
[15]: https://itsfoss.com/content/images/2026/01/Screenshot-From-2026-01-10-18-00-15-1.png
[16]: https://itsfoss.com/content/images/2026/01/Screenshot-From-2026-01-10-18-04-45.png
[17]: https://itsfoss.com/content/images/2026/01/Screenshot-From-2026-01-10-18-06-51.png
[18]: https://github.com/GraphiteEditor/Graphite/issues
