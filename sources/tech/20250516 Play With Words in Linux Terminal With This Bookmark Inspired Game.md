[#]: subject: "Play With Words in Linux Terminal With This Bookmark Inspired Game"
[#]: via: "https://itsfoss.com/sausage/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Play With Words in Linux Terminal With This Bookmark Inspired Game
======

[![Warp Terminal][1]][2]

[Sausage][3] is a word forming game, inspired by the classic [Bookworm][4]. Written in bash script, you can use it on any Linux distribution.

![Playing Sausage][5]

The goal of the game is simple.

  * Earn points by spotting words.
  * Longer word spotting results in coloured letters. Using coloured letters give more points.
  * Smaller words introduces red letters, which when reached bottom, you lose the game.



### Installation

✋

Since it's a terminal-based game, it requires a few commands for installation. I advise learning the command line essentails from our [terminal basics series][6].

You need to have git installed on your system.

Use git to clone the official Sausage repository:

```

    git clone https://gitlab.com/christosangel/sausage.git

```

Switch to the clone directory:

```

    cd sausage

```

Give execution permission to the `install.sh` shell script.

```

    chmod +x install.sh

```

Run the script:

```

    ./install.sh

```

Once the installation is finished, open Sausage in the same location using:

```

    ./sausage.sh

```

### Essential commands and shortcuts

📋

Sausage needs a 60 Column x 34 Lines terminal to work properly.

The interface has all the key combinations described properly. Even the direction of motion is displayed.

To move without selecting any word, use the arrow key.

Once a starting word is decided, press the Space/Enter key to select that letter. Now, use the navigation keys to continue selection.

Navigation | Key
---|---
↑ (Up) | k or Up Arrow
↓ (Down) | j or Down Arrow
↗ (Right and Up) | L or Shift + Right Arrow
↘ (Right and Down) | l or Right Arrow
↖ (Left and Up) | H or Shift + Left Arrow
↙ (Left and Down) | h or Left Arrow

To show all the words, press the `b` key in the game.

![Show all words][7]

To undo a letter select, press the Backspace key. Undo a word selection with the Delete key.

![Select/Unselect letters][8]

Press `r` key in game to reshuffle. Each reshuffle loses a turn and introduces multiple red cells. Existing red cell drop one cell down.

![Reshuffle in Sausage][9]

### Configuration

Limited configuration is possible here. Either manually edit `~/.config/sausage/sausage.config` file or use the `c` key in the game start page.

![Sausage Config][10]

You can find more gameplay details on its [official GitLab page][3].

### Removing Sausage

Technically, you run Sausage from the script itself. Still, initially, it has created a few directories. This screenshot from the official repository shows them:

![][11]

So, to 'uninstall' Sausage, you have to remove the cloned repository and if you want to remove the game related files, check the screenshot above and remove them.

### Up for a (word) game?

If you ever played the classic Bookworm, Sausage will be pure nostalgia. And if you never played that before, it could still be fun to try it f you like these kinds of game.

It's one of those amusing things you can do in the terminal.

I let you leave a few words in the comments 😉

--------------------------------------------------------------------------------

via: https://itsfoss.com/sausage/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://gitlab.com/christosangel/sausage
[4]: https://en.wikipedia.org/wiki/Bookworm_(video_game)
[5]: https://itsfoss.com/content/images/2025/04/playing-sausage-1.gif
[6]: https://itsfoss.com/tag/terminal-basics/
[7]: https://itsfoss.com/content/images/2025/04/show-all-words.gif
[8]: https://itsfoss.com/content/images/2025/04/select-unselect-words.gif
[9]: https://itsfoss.com/content/images/2025/04/reshuffle-and-game-over.gif
[10]: https://itsfoss.com/content/images/2025/04/config-sausage.gif
[11]: https://itsfoss.com/content/images/2025/05/install-sausage.png
