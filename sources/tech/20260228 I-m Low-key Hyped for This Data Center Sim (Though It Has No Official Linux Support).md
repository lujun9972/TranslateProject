[#]: subject: "I'm Low-key Hyped for This Data Center Sim (Though It Has No Official Linux Support)"
[#]: via: "https://itsfoss.com/data-center-game/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I'm Low-key Hyped for This Data Center Sim (Though It Has No Official Linux Support)
======

[![Warp Terminal][1]][2]

The demand for data centers worldwide has shot up in recent years, with **the blind rush for AI being a big reason** behind it. I, personally, don't think we need AI shoved into every corner of our lives, but certain regimes and organizations seem to think otherwise, and they keep pushing hard for it.

So, if hearing all that makes you want to just roll up your sleeves and build one yourself, then this indie game might scratch that itch.

📋

This game is not natively available for Linux. But it does interest me as a Linux user.

### Data Center: A Work in Progress

![][3]

[Data Center][4] is an upcoming simulation game from solo developer Václav Novák, who goes by [Waseku][5] on Steam. He is based in Brno, Czech Republic, and has been building games since 2020 using the Unity engine.

The main idea here is that you **build and manage a data center from scratch**. That involves buying racks, servers, and switches; physically placing and stacking your hardware; and then running cables between ports to tie it all together.

It lets the player monitor network traffic via colored, sphere-shaped balls that move around in the cables, and any idle network cable connections are easy to spot. You earn money by serving customers according to their requirements and capacity expectations.

When you process data successfully, you get money, gain experience to unlock better hardware, and build your reputation to draw in larger clients.

### Worth Playing?

Possibly. I played the free demo on a [Nobara Linux][6] system, and the overall experience was okay _ish_.

First, I configured the graphical settings, disabling NVIDIA DLSS and cranking most settings to their highest possible states. When I went into the game, the game was capped at 50 FPS.

Turns out VSync was the culprit ( _unsurprisingly_ ), so I disabled it and set a 100 FPS limit.

![The graphical settings I used to play the demo.][7]

**But the performance woes didn't end there** , as throughout gameplay, there were visible drops in the FPS that happened intermittently; the performance graph on the top-right ( _for FPS_ ) shows it well. 👇

Even forcing the use of [Proton Experimental][8] didn’t seem to help, so I rolled with it. Plus, some reviews of the demo on Steam mention this issue, so it was probably that.

The game doesn’t have a proper new player tutorial just yet; it shows some vague objectives, and I had to find my way through the game. The closest thing to an onboarding guide is the _Tutorial_ menu found by pressing the `Esc` key.

I could read up on how to handle customers, how to configure a server, what kinds of racks and units were available, and a lot more beyond that.

![][9]

Initially, I was lost and placed [patch panels][10], [switches][11], and [servers][12] randomly, without any sense of how these are usually arranged. After a quick web search and closely following what the minuscule object tracker was saying, I was on the correct path.

First, I went to the computer at the desk and headed into the shop. Here, I could unlock some starter server hardware for 0 XP and continue building up from there.

![The online shop acts as a one-stop portal for all your server hardware needs.][13]

As you can see, I purchased a few patch panels and racks to start populating my data center. The provided utility cart for transferring items from the shipping bay to the server room is, well, _**jank**_.

It either keeps any placed items intact or it tosses them off as if it has a mind of its own. Even moving it around is a chore, as it has a habit of clipping below the floor for a quick trip to the underworld.

**Placing new racks is another story**. You just pick up a rectangular cardboard box and press `E` to install it over a designated spot on the floor. And to place network switches, patch panels, or servers, a handy yellow-colored outline is shown in the available space on a rack.

Wiring all of that up is effortless too. After purchasing 100 meters (🦅 _328 ft_ ) of CAT6E cable, I was able to connect the server hardware, with some slip-ups that I fixed later during my play.

![Configuring a server for a fictional customer in Data Center.][14]

Onboarding new customers is as simple as connecting a wire from the network switch to the outbound connection panel thingy; I am unsure what that's called. Here, you select a customer, review what they want, and then a small guide pops up on how to get them hooked up.

I then turned on the power for the servers and set the IP addresses from the individual control panel to get the connection up. I had to add a few more servers and turn on the network switches before I could serve the customer, " _Bermuda Triangle Backup_ " at 40000 IOPS speed.

📋

Hmm, I wonder if they lose all of their customers' data citing mysterious phenomena.

![Kinda borked cable management on the left; on the right is the server room expansion dialog.][15]

**If you noticed the abysmal cable management job** I did in the video above, then fret not; I have redeemed myself by fixing it ( _in the video below_ ). But before that, you have to know that there are handy cable management loops across the racks and the roof of the server room that make your job easier.

You can also increase the space of your server room by purchasing additional space for 1,000 in-game currency per block. _If you see a pile of strewn-about servers, ignore it._

Making use of the aforementioned mounts, I neatly rerouted the Ethernet cabling to clean up the spiderweb-like arrangement I had in place. As you saw, it is fairly easy to do, provided you have some patience and a little obsession with keeping things in proper alignment.

Overall, **the game needs a lot of polish before launch**. A proper tutorial would be a good start because right now new players are pretty much left to figure things out on their own.

On my wishlist for later upgrades would be multi-storey data centers, a utility cart that actually works without going into a void, and a computer portal that isn't so basic and awkward to use.

### How to Play?

A [free demo][16] with some restrictions has been available on Steam for some time now. The game is [planned to launch][4] on **March 31, 2026** , though without any pricing information yet.

There is also no mention of an [early access][17] release, so it looks like Václav is aiming for a stable 1.0 release.

[Data Center Demo][16]

--------------------------------------------------------------------------------

via: https://itsfoss.com/data-center-game/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2026/02/data-center-main-menu.jpg
[4]: https://store.steampowered.com/app/4170200/Data_Center/
[5]: https://waseku.com/
[6]: https://nobaraproject.org/
[7]: https://itsfoss.com/content/images/2026/02/data-center-graphics-settings-1.jpg
[8]: https://github.com/ValveSoftware/Proton/tree/experimental_10.0
[9]: https://itsfoss.com/content/images/2026/02/data-center-tutorial-menu.jpg
[10]: https://en.wikipedia.org/wiki/Patch_panel
[11]: https://en.wikipedia.org/wiki/Network_switch
[12]: https://en.wikipedia.org/wiki/Server_(computing)
[13]: https://itsfoss.com/content/images/2026/02/data-center-computer-portal.jpg
[14]: https://itsfoss.com/content/images/2026/02/data-center-server-config-1.jpg
[15]: https://itsfoss.com/content/images/2026/02/data-center-borked-cable-management-1.jpg
[16]: https://store.steampowered.com/app/4376050/Data_Center_Demo/
[17]: https://store.steampowered.com/genre/Early%20Access
