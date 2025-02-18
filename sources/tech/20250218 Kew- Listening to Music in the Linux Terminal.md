[#]: subject: "Kew: Listening to Music in the Linux Terminal"
[#]: via: "https://itsfoss.com/kew-terminal-player/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Kew: Listening to Music in the Linux Terminal
======

[![Warp Terminal][1]][2]

A new (or perhaps old) way of enjoying music for the command-line enthusiasts.

[I've seen things][3]... seen things that you people wouldn't believe... [Linux developed by governments][4], [Linux on mobiles][5], and terminal audio players.

Yes, it could be funny, but it's real, you could play music from your command-line.

And that's just one of the many [unusual things you can do in the terminal][6].

[Subscribe to It's FOSS YouTube Channel][7]

### Meet Kew

When you use the terminal more often than the graphical tools, you would perhaps enjoy playing music from the terminal.

I came across [Kew][8], a terminal music player fully written in C. It's small (not more than 1 MiB), with a low memory profile. You can create and play your own playlists!

![Kew music player running in the terminal][9]

### First things go first: Installation

It's straightforward to install Kew because it's available in the repositories of the common Linux Distributions like [Arch Linux][10], [Debian][11], [Gentoo][12]., etc.

For Debian and Ubuntu-based distros, use:

```

    sudo apt install kew

```

You can use an [AUR helper][13] for Arch-based distros. Let's you [use yay][14]:

```

    sudo yay -S kew

```

For openSUSE, use zypper:

```

    sudo zypper install kew

```

### Exploring music with Kew

One of the most interesting and surprising things it's that kew can search in your music directory (usually ~/Music, or you could change it) only with one word:

```

    kew bruce

```

And you're immediately listening to the Boss!!

![][15]

You can see the album cover while you're listening to it.

You can make a playlist based on the content of a directory (and the others inside it recursively). The playlist can be edited/modified inside Kew in the Playlist view.

You can play the songs from the playlist using:

```

    kew kew.m3u

```

### Direct Functions

Kew provides some direct functions that you can type with kew:

  * <none>: You go straight to the music library.
  * dir <album name>: Play a full directory.
  * song <song name>: Play only a song.
  * list <playlist name>: Play a playlist that you could define.
  * shuffle <album name>|<playlist name>: shuffles the album or playlist
  * artistA:artistB:artistC: shuffles all 3 artists.
Just to mention some of their fantastic functions. You could get all the commands [here][16].



#### Views

There are different views for different functions that can be accessed via a function key.

F2 : Current Playlist

![][17]

F3 : Library view

![][18]

F4 : Track View

![Kew music player running in the terminal][9]

F5 : Search view

![][19]

F6 : Help

![Press F6 to get the keyboard shortcuts info][20]

#### Key bindings

If you decided to use Kew regularly, it would be much better to use and remember various keyboard shortcuts. You can surely configure your own.

Press F6 and it will show the key bindings:

  * \+ (or =), keys to adjust the volume.
  * ←, → or h, l keys to switch tracks.
  * space, p to toggle pause.
  * F2 or Shift + z to show/hide the playlist.
  * F3 or Shift + x to show/hide the library.
  * F4 or Shift + c to show/hide the track view.
  * F5 or Shift + v to search.
  * F6 or Shift + b to show/hide key bindings.
  * u to update the library.
  * v to toggle the spectrum visualizer.
  * i to switch between using your regular color scheme or colors derived from the track cover.
  * b to toggle album covers drawn in ascii or as a normal image.
  * r to repeat the current song.
  * s to shuffle the playlist.
  * a to seek back.
  * d to seek forward.
  * x to save the currently loaded playlist to a m3u file in your music folder.
  * Tab to switch between views.
  * gg go to first song.
  * number + G, g or Enter, go to specific song number in the playlist.
  * g go to last song.
  * . to add current song to kew.m3u (run with "kew .").
  * Esc to quit.



### Conclusion

There are several terminal audio players like [Cmus][21], [MOC - Music on Console][22], [Musikcube][23], etc. Kew can be placed in this list of terminal tools.

Written in C, with a small memory blueprint, Kew is worth trying for a terminal dweller.

If you give it a try, do share its experience in the comments.

#### Author Info

![][24]

**Jose Antonio Tenés**
A Communication engineer by education, and Linux user by passion. In my spare time, I play chess, do you dare?

--------------------------------------------------------------------------------

via: https://itsfoss.com/kew-terminal-player/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.youtube.com/watch?v=NoAzpa1x7jU&pp=ygUOdGVhciBtb25vbG9ndWU%3D
[4]: https://archiveos.org/tens/
[5]: https://github.com/dreemurrs-embedded/Pine64-Arch/releases
[6]: https://www.youtube.com/watch?v=0Er8D7RR5l8
[7]: https://www.youtube.com/@itsfoss
[8]: https://github.com/ravachol/kew
[9]: https://itsfoss.com/content/images/2025/02/kew07.png
[10]: https://archlinux.org/
[11]: https://www.debian.org/
[12]: https://www.gentoo.org/
[13]: https://itsfoss.com/aur-arch-linux/
[14]: https://itsfoss.com/install-yay-arch-linux/
[15]: https://itsfoss.com/content/images/2025/02/kew04.png
[16]: https://github.com/ravachol/kew#some-examples
[17]: https://itsfoss.com/content/images/2025/02/kew05.png
[18]: https://itsfoss.com/content/images/2025/02/kew06.png
[19]: https://itsfoss.com/content/images/2025/02/kew08.png
[20]: https://itsfoss.com/content/images/2025/02/kew09.png
[21]: https://cmus.github.io/
[22]: https://moc.daper.net/about
[23]: https://musikcube.com/
[24]: https://itsfoss.com/content/images/2024/12/gose.webp
