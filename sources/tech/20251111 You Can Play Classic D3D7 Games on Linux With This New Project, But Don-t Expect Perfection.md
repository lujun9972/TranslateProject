[#]: subject: "You Can Play Classic D3D7 Games on Linux With This New Project, But Don’t Expect Perfection"
[#]: via: "https://itsfoss.com/news/play-d3d7-games-on-linux/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

You Can Play Classic D3D7 Games on Linux With This New Project, But Don’t Expect Perfection
======

[![Warp Terminal][1]][2]

D7VK is **a new Vulkan-based translation layer for Direct3D 7**. It relies on DXVK’s Direct3D 9 backend and works with [Wine][3] on Linux. The project is open source and actively maintained.

The developer behind it is [WinterSnowfall][4], who has also worked on [D8VK][5] between 2023 and 2024. That project has since been merged into the larger [DXVK][6] project that's extensively used by Linux users.

You have to understand that **D7VK is not meant to run every Direct3D 7 game**. Titles that mix D3D7 with older [DirectDraw][7] or [GDI][8] calls may fail to launch or show graphical glitches. So, compatibility is experimental and limited.

It works by translating Direct3D 7 calls to Direct3D 9 through DXVK, allowing Vulkan-based 3D application rendering on Linux. Sadly, **there is no official list of supported games yet**.

Some games work well, others have issues. Missing textures, crashes, and black screens are common. The [issues][9] page on the project's GitHub repo shows which games are behaving poorly. It is a good way to see what currently works.

📋

PCGamingWiki's [list of Direct3D 2-7 games][10] is also a handy resource to have if you want to test a specific Direct3D 7 game.

**What’s nice is how the developer sets expectations right from the start**. They are upfront about the experimental nature of the project. This clarity makes it easier to test games without getting disappointed.

For fans of late 90s and early 2000s games, D7VK could be handy. It won’t fix everything, but it opens the door to running older Direct3D 7 games on Linux.

### Want to Check it Out?

The D7VK [GitHub][11] repository has the source code. You can manually compile it and place it in your [Wine prefix directory][12] to try it out. D7VK **supports a HUD overlay and frame rate limiting** through DXVK.

These features will help you track performance and debug graphical issues.

[D7VK (GitHub)][11]

**Suggested Read 📖**

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/play-d3d7-games-on-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.winehq.org/
[4]: https://github.com/WinterSnowfall
[5]: https://github.com/AlpyneDreams/d8vk
[6]: https://github.com/doitsujin/dxvk
[7]: https://en.wikipedia.org/wiki/DirectDraw
[8]: https://en.wikipedia.org/wiki/Graphics_Device_Interface
[9]: https://github.com/WinterSnowfall/d7vk/issues
[10]: https://www.pcgamingwiki.com/wiki/List_of_Direct3D_2-7_games
[11]: https://github.com/WinterSnowfall/d7vk
[12]: https://wiki.archlinux.org/title/Wine#:~:text=By%20default%2C%20Wine%20stores%20its,%22%20or%20%22Wine%20bottle%22.
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-3.png
