[#]: subject: "Linux Mint is Building a New Chat App to Replace 'Hexchat'"
[#]: via: "https://news.itsfoss.com/linux-mint-jargonaut/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Mint is Building a New Chat App to Replace 'Hexchat'
======
Linux Mint's new desktop chat app. Interesting, but not the replacement
some were hoping it to be.
Unfortunately, Hexchat, a long-running IRC client, was [discontinued recently][1] owing to the project not being maintained for years.

Linux Mint included Hexchat as the default IRC client since 2014, mostly utilized by the users to get support, ask questions, and talk to other fellow distro users. And, some users utilized it as their go-to IRC client. So, what now?

Well, if you want a full-fledged substitute for the IRC client, you can use one of the [Matrix clients][2] like Element. But, if you aren't concerned about the talking to users from other IRC channels, there's something for you by Linux Mint devs.

The developers of Linux Mint are working on a new app called “ **Jargonaut** ” to replace Hexchat to provide access to support chat rooms with better functionality.

### Jargonaut: What to Expect?

![][3]

Being developed as a Linux Mint [Xapp][4], Jargonaut is a “chat room” application **designed to work on all Linux distros** and desktop environments.

Even though Jargonaut uses the IRC protocol, the developers intend this app to be more of a place where people could ask questions to other users related to Linux Mint. They plan to connect the app to _#linuxmint-help_ and _#linuxmint-chat_ from their Spotchat server to achieve that.

They also intend to add support for attaching files via [Pastebin][5]/[Imgur][6], letting users upload their system specs, ways to troubleshoot and a few more features that are not found with IRC.

Moreover, **the IRC functionality will still stay** , and users or other distro developers can change the default settings via [_GSettings_][7] to make it more tailored towards their use case.

By default, the app will work as a way to get access to support chart rooms. So, unless you customize the configuration of the app, it will not be a replacement to Hexchat.

That being said, in their to-do list, the developers mention **some interesting features** that they intend to bring to Jargonaut. Here are a few notable ones:

  * **A better app icon.**
  * **Ability to ignore users.**
  * **Support for spell check.**
  * **Implementing a tray shortcut.**
  * **Introduction of a spoiler tag for texts.**



### Want to check it out?

At this stage, **the Jargonaut app is under heavy development** , and cannot be considered for regular use. However, if you are truly interested in trying it out, you can build it from source by visiting its [GitHub repo][8].

[Jargonaut (GitHub)][8]

You can also contribute to the code if you are into that, and for more details regarding Jargonaut, go through the official [announcement blog][9].

_💬 What do you think of Jargonaut? Did you expect it to be a full-fledged IRC client instead of being tailored for support chat rooms by default? Share your thoughts in the comments._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-mint-jargonaut/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://hexchat.github.io/news/2.16.2.html
[2]: https://itsfoss.com/best-matrix-clients/
[3]: https://news.itsfoss.com/content/images/2024/03/Jargonaut_Early_Build.png
[4]: https://github.com/linuxmint/xapp
[5]: https://pastebin.com/
[6]: https://imgur.com/
[7]: https://wiki.gnome.org/HowDoI/GSettings
[8]: https://github.com/linuxmint/jargonaut/tree/master
[9]: https://blog.linuxmint.com/?p=4650
