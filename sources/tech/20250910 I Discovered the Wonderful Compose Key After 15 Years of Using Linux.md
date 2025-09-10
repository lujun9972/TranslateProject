[#]: subject: "I Discovered the Wonderful Compose Key After 15 Years of Using Linux"
[#]: via: "https://itsfoss.com/compose-key-gnome-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Discovered the Wonderful Compose Key After 15 Years of Using Linux
======

[![Warp Terminal][1]][2]

Sometimes you discover things by accident, even if they were probably there for years.

I had the same case when I discovered that GNOME allowed the use of a compose key and it was available right from the keyboard settings. Eureka moment? Sort of.

Allow me to share my 'discovery,' but before that, let me briefly tell you what a compose key is.

### What is a Compose Key?

A [compose key][3] followed by two or more keystrokes lets you type special characters and symbols like ® (registered), © (copyright), and à. You do it directly with your keyboard without having to hunt them down online or dig through character maps.

This is particularly helpful for people who type in European languages like French, Swedish, etc on a QWERTY keyboard.

You'll have to enable the compose key first. I am using GNOME desktop environment in this article, but a similar feature should also be available in [other desktop environments][4].

### Enable the Compose Key on GNOME

Search and open settings from the [GNOME Activities][5] overview.

![Open Settings][6]

Inside the settings, go to the **Keyboard** section. Here, you can see an option for **Compose Key**.

It is set to _Layout default_ in my Ubuntu 24.04 installation using GNOME 46 and was turned off by default in my Arch installation using GNOME 48.

![Select Compose Key][7]

In any case, go inside the compose key and either enable it (in case it is turned off) or disable the default layout.

![Set another Compose key][8]

As soon as you do this, you can see that you can now set another key as the compose key.

I set the Right CTRL key as the compose key, as shown in the screenshot above.

🚧

If you are using VirtualBox, do not assign the Right-CTRL key. Because in VirtualBox, it is the host key with some special usage.

That's it. Whenever you need to type some special symbol, first press the Compose key. This changes the cursor to a special look. **Enter the code for the character** you want to enter.

0:00

/0:17

1×

A small clip showing the working of the compose key in GNOME.

### Essential compose key codes

Yes, you need to know the character code. This may seem like an additional burden, but for frequent users, it will soon become muscle memory.

Press the compose key you had set earlier followed by the sequence of characters shown in the left column and it will output the characters in the second column in the table below:

Compose Key Plus | Types Character
---|---
' a | á
" a | ä
` a | à
a e | æ
o o | ° Degree symbol
o c | ©
o r | ®
s o | §
t m | ™ (Trade Mark)
> > | »
< < | «
# E | ♫ (Beamed Eighth notes)

You can check the [official documentation for the X11 library's compose key sequences][9] for a comprehensive list of keys and related character.

### Can't Remember? No Worries

The compose key is particularly useful for people who don't want to divert attention from typing and at the same time need to add symbols.

But this alone is not the option. Most modern desktop environments have [emoji apps like the GNOME Characters app for GNOME][10].

![][11]

If you don't use special characters frequently, you can simply search for them in the GNOME Activity overview.

For example, just search for "copyright" and if the Characters app is enabled, you can see the symbol pop up in the result. Click on it and it is copied to the clipboard and now you can paste it wherever required.

I highly recommend referring to the [X11 library's compose key sequences][9] where you can find all the key sequences, even for [typing the obscure infinity symbol][12].

Enjoy the compose key.

--------------------------------------------------------------------------------

via: https://itsfoss.com/compose-key-gnome-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://en.wikipedia.org/wiki/Compose_key
[4]: https://itsfoss.com/best-linux-desktop-environments/
[5]: https://itsfoss.com/gnome-search/
[6]: https://itsfoss.com/content/images/2025/08/gnome-compose-key-open-settings.png
[7]: https://itsfoss.com/content/images/2025/08/select-the-compose-key-ubuntu.png
[8]: https://itsfoss.com/content/images/2025/08/set-another-compose-key.png
[9]: https://www.x.org/releases/current/doc/libX11/i18n/compose/en_US.UTF-8.html
[10]: https://itsfoss.com/ubuntu-emojis/
[11]: https://itsfoss.com/content/images/icon/android-chrome-192x192-640.png
[12]: https://itsfoss.com/type-infinity-linux/
