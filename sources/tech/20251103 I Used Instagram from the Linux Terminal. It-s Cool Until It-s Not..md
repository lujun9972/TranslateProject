[#]: subject: "I Used Instagram from the Linux Terminal. It’s Cool Until It’s Not."
[#]: via: "https://itsfoss.com/instagram-cli/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Used Instagram from the Linux Terminal. It’s Cool Until It’s Not.
======

[![Warp Terminal][1]][2]

It is time to talk about the most important love-hate relationship that has ever been. It is Instagram and... you.

Instagram has become irreplaceable if you're in a spot where you need to reach out to the world to present your work and follow others' in any area, be it art, music, dance, science, tech, modelling, etc. Being one of the biggest platforms, you can't skip out on it if you want to keep up with the world and the lives of your friends. But on the other hand, it is also one of the most distracting apps to exist because of the possibility and addictiveness of doomscrolling your hours into nothingness.

Worry not, because we once again bring you the way to make your life better. The solution, unsurprisingly, lies in the Linux terminal (as most of them do), which will be your next Instagram Client.

Well, actually it is not, as you'll read in this article. But before you do that, [check out It's FOSS Instagram account][3] as we are killing it with some realli infotaining stuff. 92K+ people are the proof of that.

[Follow It's FOSS on Insta for daily dose of Linux Memes and News][3]

### Behold Instagram-CLI! And it's not from Meta

![][4]

Claiming to be the "ultimate weapon against brainrot", [Instagram-CLI][5] provides an exciting option to use Instagram through your terminal. Said mission is achieved by limiting possible actions to only three things: checking your messages, your notifications, and your feed (consisting only of the accounts that you have followed).

### Sliding into the DMs via CLI

The command to access the chats is:

```

    instagram-cli chat

```

The interface of which looks like this:

![][6]

The navigation is quite simple. j/k keys to scroll through the accounts you can chat with (J/K to select the absolutely first or the absolutely last chat), when you press Enter to choose the chat you want to access. When chatting with someone, you can obviously just write your texts in the chat-box and hit Enter to reply. But if you either want to reply, react or unsend a message, it all starts with the input:

```

    :select

```

After writing that and pressing Enter, you can navigate through the texts using j/k keys (again, J/K to select the absolutely first or the absolutely last text) and select one for an action. To send a reply saying "You have been replied to.", the input will look like:

```

    :reply You have been replied to.

```

0:00

/0:19

1×

To embed an emoji in a normal text, you can do it as so:

```

    You have been replied to :thumbsup:

```

To unsend the message, the input given is:

```

    :unsend

```

And to react, say with a thumbs-up emoji, the input will look like:

```

    :react thumbsup

```

To mention someone in a group chat, you can use the "@" as usual, and you can even send files using a simple hashtag. It even supports autocomplete after the hashtag, similar to how it would on the terminal itself. So to send a file called "test.png" that is in your Downloads directory alongside a message, simply write:

```

    This is image testing #Downloads/test.png

```

It does take a while for a file to be sent, though. I have demonstrated the process in this video:

0:00

/0:24

1×

However, to send the file on its own, you can use:

```

    :upload #Downloads/test.png

```

🗒️

It is worth noting that the behavior of this chat is very inconsistent. In my personal experience, I have not been able to make the emoji reactions work even though I executed it exactly as they had shown, and while the messages with emojis do get sent, they don't show up on the texting window and disappear from the Instagram official app/website after reloading. The replying function is also a hit or miss.

### Gotta check the feed

To access your feed, you can simply enter:

```

    instagram-cli feed

```

This brings up your feed, where you can scroll through the posts using j/k and through the carousel of a single post using h/l. If you do it for the first time without much configuration, the images in your feed will look something like this:

![][7]

The graphics by default are ASCII, and that might not be something you want, considering the fact that nothing is quite clear (however cool it may be). So how do you fix that? You switch the image mode with the following command:

```

    instagram-cli config image.protocol kitty

```

Now, the graphical media will look... well, graphical:

![][8]

If it doesn't work, try [using a terminal like Ghostty][9] or [Kitty][10].

If you want to switch back, replace the "kitty" in the command with "ascii". In total, there are 6 imaging options Instagram-CLI provides: "ascii", "halfBlock", "braille", "kitty", "iterm2", "sixel", or "", but knowing only these two might suffice.

🗒️

The feed is quite janky. It automatically scrolls through posts rather inconsistently and doesn't always respond well to the scrolling input. The often images don't sit well within the boxes that they are contained in, making it feel a little rough around the edges.

### Notify my terminal

This simply requires one command, and there isn't much more to it:

```

    instagram-cli notify

```

![][11]

### Authenticating in the CLI

Logging in can be done with the simple username-password combination after entering the following command:

```

    instagram-cli auth login --username

```

You can log into multiple accounts in this manner, which you can switch among through this command:

```

    instagram-cli auth switch <username>

```

In case you forget what account is currently active, you can ask it who you are:

```

    instagram-cli auth whoami

```

And to finally log out of your currently active account, simply enter:

```

    instagram-cli auth logout

```

🚧

This was is perhaps the most important warning of all. I tried to log into my personal account on Instagram-CLI and Instagram flagged it as suspicious behavior calling it scraping. I was locked out of my account for a little bit because of it, so log in at your own risk. We recommend using a dummy account that is expendable.

### Config if you can

Since it offers a bunch of configuration options, it only makes sense to have a command that can list them all at once so you can keep a track of it all:

```

    instagram-cli config

```

Any of the values can be changed with:

```

    instagram-cli config <key> <value>

```

But if you want to change multiple keys at once, you can simply edit the config file as a text file at once:

```

    instagram-cli config edit

```

### Try it (but perhaps not risking your main account)

The recommended method for installation of the program uses [npm][12], so make sure that you have that preinstalled on your system. If not, you can install it using:

```

    sudo curl -qL https://www.npmjs.com/install.sh | sh

```

And then to install Instagram-CLI on your system, enter:

```

    sudo npm install -g @i7m/instagram-cli

```

Alternatively, if you want to install it without npm, you can use Python:

```

    sudo pip3 install instagram-cli

```

🚧

The project developers have asked specifically not to use the same account if you have both the clients installed.

### 💡 Bonus Banner

If you want to recreate the banner at the beginning of the article (perhaps to show off the capabilities of your terminal), enter the command without any other parameters:

```

    instagram-cli

```

### Wrapping Up

Instagram-CLI is an interesting initiative because of the way it reduces your screentime while still giving you an option to socialize. Not to forget, it helps you avoid Meta's trackers. Helps you simultaneously improve your social media habits while also managing your FOMO.

The project is still very clearly quite rough around the edges, which has more to do with Meta's policies than the developers themselves. It is a hit or miss, but it might just work for your account, so give it a shot. But if you see your account flagged, you know what you got to do.

Let us know what you think about this it in the comments. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/instagram-cli/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.instagram.com/itsfoss/
[4]: https://itsfoss.com/content/images/2025/11/instagram-cli_banner.png
[5]: https://github.com/supreme-gg-gg/instagram-cli
[6]: https://itsfoss.com/content/images/2025/11/instagram-cli_chat.png
[7]: https://itsfoss.com/content/images/2025/11/instagram-cli_ascii-image.png
[8]: https://itsfoss.com/content/images/2025/11/instagram-cli_graphic-image.png
[9]: https://itsfoss.com/ghostty-terminal-features/
[10]: https://itsfoss.com/kitty-customization/
[11]: https://itsfoss.com/content/images/2025/11/instagram-cli_notifications-1.png
[12]: https://www.npmjs.com/package/npm
