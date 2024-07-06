[#]: subject: "Running One of My Favorite Windows Game on Linux: Here's How It Went"
[#]: via: "https://news.itsfoss.com/windows-game-on-linux-experience/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running One of My Favorite Windows Game on Linux: Here's How It Went
======
Curious to know how it looks like to run your favorite Windows game on
Linux? We share our experience here.
[![][1]][2]

I vividly remember the day back in 2018, when CD Projekt RED showed off the trailer for [Cyberpunk 2077][3]. I was super excited about it, the world, the lore, the characters, and the best part, an open-world to play around in.

All this was thanks to the hard work [Mike Pondsmith][4] had put in over the years, creating a unique dystopian world.

When it came out for pre-order, I immediately got it for PC, in the hopes of getting early access, playing it before any spoilers started popping up. Since then, **I have learned to never pre-order a game again**.

As many of you might already know, its [launch was a disaster][5], with performance issues across all platforms, and Sony even delisting it from their game store.

Luckily, in the months following the launch, **the developers were able to turn this sinking ship over** , with timely updates, and clear communication. Slowly, but surely, the game became what it was originally intended to be, and the [Netflix series][6] spinoff just helped it become more mainstream.

For me, I have been playing it on my Windows PC since early access ( _December 2020_ ), completing all the side-quests and the main quests, even the recently introduced [Phantom Liberty][7] DLC.

A few months ago, I got a new laptop, got rid of Windows 11, and went with an Ubuntu setup on it. As expected, the gamer in me wanted to play games on it, so I installed Steam, and got started with a few native, and non-native games.

Join me as I take you through my experience with Cyberpunk 2077.

🚧

This is an “M” ( _ _USA__ ) rated video game intended for mature audiences.

### Cyberpunk 2077 on Ubuntu: How Did It Turn Out?

![][8]

If you were wondering, **Cyberpunk 2077 is not a native game for Linux** , but the [Proton][9] compatibility layer makes it possible to run it on distributions which have the necessary utilities. Thanks to that, any benchmark I ran showed that I was running Windows 10 Pro as the operating system.

The test system used in this article has the following specifications:

  * **RAM:** 16 GB
  * **CPU:** Intel Core i5-13450HX
  * **GPU:** NVIDIA GeForce RTX 3050 6 GB
  * **Driver:** NVIDIA 535.183.01
  * **OS:** Ubuntu 24.04.4 LTS
  * **DE:** GNOME 42.9
  * **Session:** X11
  * **Mods:** No



Initially, when I ran the game, I was surprised to see that the save games from my previous play through on Windows ( _~170 hours of gameplay_ ) were synced, meaning that I could pick up where I left off.

I then turned all the graphical settings to their maximum settings ( _except a few RT-related ones_ ) by using the “ _Ray Tracing: Ultra_ ” graphical preset and ran a benchmark.

As expected, the game performed bad on this entry-level card. See for yourself. 👇

![][10]

So, I proceeded to tweak the settings to make the game more playable. I completely did away with any kind of Ray Tracing, kept DLSS on the Auto setting, changed the _Hybrid CPU Utilization_ setting to prioritize P-cores by default, and disabled VSync.

![][11]

And, to my surprise, the game was running smoothly, fluctuating between ~50-60 fps, with the occasional micro stutter and FPS drop when I moved through the game world too fast.

One more thing I noticed was that when I turned on V-Sync @60 FPS, the game felt slightly less smooth, compared to when it was off.

![][12]

Plus, when I tried using the 30 FPS setting for it, the game would still run with the FPS unlocked, even when I turned on the dedicated “Maximum FPS” setting on, and the benchmarking tool would start reporting erroneous FPS numbers.

#### As for my gameplay experience… 🎮 🐧

Only screenshots can't do justice to the wonderful experience I had. But, I have attached some fairly eye-catching ones in the gallery below to give you an idea. 👇

![][13]

I did all kinds of shenanigans, be it angering the cops, or going into a scav base guns blazing, the game didn't bug out, even the photo mode was working as expected; _Don't ask me what I did to anger the police._ ☠️

Before I wrap this up, **a note for users of multiple monitors** , there's a chance that the game will run slightly slowly in terms of FPS ( _it did for me_ ) when an external/additional monitor is connected.

For entry-level GPUs, you may face an FPS drop issue, for high-end GPUs, I doubt that will be a problem. Another thing that **slightly soured the experience** for me was that when I alt-tabbed in/out of the game, the game would sometimes crash, without an error.

It would happen more frequently if I aggressively switched between multiple workspaces with a few applications open. So, that's something to keep in mind when playing.

**Suggested Read** 📖

![][14]

### Try Gaming On Linux!

I was very delighted to see that Cyberpunk 2077 was running so good on Ubuntu, even better than on my Windows PC, which couldn't pass the ~45 FPS mark on all settings turned up to the max, without Ray Tracing.

Although, I admit my gaming PC has an older GTX 1070 Ti GPU, but I still liked what I saw on Ubuntu.

Many users, who want to switch to Linux, I tell you, [gaming on Linux][15] has improved a lot, and my experience here is a proof of that. You should definitely give your favorite game a try on Linux!

_⭐ Lastly, stay tuned, as I have a few more such gaming-centric articles lined up where I will take you through my experience on Ubuntu._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/windows-game-on-linux-experience/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.cyberpunk.net/
[4]: https://en.wikipedia.org/wiki/Mike_Pondsmith
[5]: https://www.vox.com/culture/22187377/cyberpunk-2077-criticism-ps4-xbox-one-bugs-glitches-refunds
[6]: https://www.netflix.com/title/81054853
[7]: https://www.cyberpunk.net/us/en/phantom-liberty
[8]: https://news.itsfoss.com/content/images/2024/07/Cyberpunk_2077_Ubuntu_a.jpg
[9]: https://github.com/ValveSoftware/Proton
[10]: https://news.itsfoss.com/content/images/2024/07/Cyberpunk_2077_Ubuntu_b.jpg
[11]: https://news.itsfoss.com/content/images/2024/07/Cyberpunk_2077_Ubuntu_c.jpg
[12]: https://news.itsfoss.com/content/images/2024/07/Cyberpunk_2077_Ubuntu_c2.jpg
[13]: https://news.itsfoss.com/content/images/2024/07/Cyberpunk_2077_Ubuntu_d.jpg
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://itsfoss.com/linux-gaming-guide/
