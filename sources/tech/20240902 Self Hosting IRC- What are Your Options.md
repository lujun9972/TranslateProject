[#]: subject: "Self Hosting IRC: What are Your Options?"
[#]: via: "https://itsfoss.com/self-hosted-web-irc/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Self Hosting IRC: What are Your Options?
======

[![Warp Terminal][1]][2]

**IRC** (Internet Relay Chat) might no longer be in the trend. But, it will always be a part of the communication platform, even when you read this article in 2050 or more.

It was popular back in the 2000s, and some still prefer it over modern chat clients like Slack and Discord. Several open-source project developers utilize IRC for real-time communication over proprietary options.

It just works and has performance benefits; you do not need to sign up for a company's specific terms and conditions to use it. Moreover, with some web IRC clients, you can expect some modern features like link previews.

You can always use an IRC desktop/mobile client and connect to a server. But, what if you want more control and host it yourself so you can access it on the web for your community and friends?

For such use cases, let me highlight the IRC web clients that offer self-host options. I have **tried to keep the list limited to actively maintain projects**.

### The Lounge

![][3]

[The Lounge][4] is a modern web IRC client that packs in useful features like push notifications, file uploads, link previews, and multi-user support. Regarding the user experience, I find it similar to the Rocket.Chat experience, which is an [open-source Slack alternative][5].

You get support for plugins to extend functionality and add features as per your requirements. Furthermore, there are themes available to customize the look and feel of the client.

It can run on any platform that supports Node.js like Linux, Windows, and macOS. For self-hosting, you can utilize the Docker image, which would let you access it on the web browser. You can explore more details on its [GitHub page][6] and official documentation.

**Key Features:**

  * Public/Private server mode
  * Cross-platform client support
  * File uploads, link previews
  * Plugin support
  * Theme support



### Convos

![][7]

[Convos][8] is a unique chat application with IRC support that lets you make video calls as well. It manages to keep you online even when you have closed the web browser. So you can still get all the messages, and activities logged.

It supports rich text formatting, and themes for you to customize the look and feel of the web IRC client experience. There is also Pastebin integration, and file upload functionality along with other features.

You can set it up on your home server, cloud service, or using Docker. So, you have multiple ways to set it up.

Interestingly, Convos can also be used as a generic CMS. Of course, you will be better off with the [best open-source CMS options][9] out there. But, it is still an option.

Explore more about it on its [GitHub page][10].

**Key Features:**

  * Always online
  * Video call
  * Use as a CMS
  * Theme support
  * File upload and rich text formatting



🚀

You can effortlessly deploy Convos in the cloud with PikaPods for just $1 per month! [Start free with $5 welcome credit][11] 😎

### Kiwi IRC

![][12]

[Kiwi IRC][13] is a more traditional-looking web IRC client with versatile features, and plugin support to extend functionality. The good thing about it is, you get static files, so it should be a hassle-free and reliable experience to host it. You get it with a default IRC network, but you can always use your own.

It also supports themes for you to customize the look and multiple users in the network. While it is actively developed, the official website seems like it hasn't been updated in a long time.

It may not be the most modern option on the list, but it is a decent candidate for simple static use-cases. Explore more about it on its [GitHub page][14].

**Key Features:**

  * Traditional UI for a web IRC
  * Theme support
  * Plugin support



![Sign up to get $200 free credits][15]

### WeeChat

![][16]

If you want a feature-rich support, and a traditional experience at the same time, [WeeChat][17] can be a nice pick. It is also incredibly small and lightweight to use.

It looks like a terminal-based user interface, and it supports IRC and other chat protocols (if you wish not to use IRC). You can host your instance of WeeChat and access it from your phone, or computer through the web browser.

There are scripts that you can utilize and functionalities to help you enhance the experience.

### Conclusion

Matrix is often considered the spiritual successor to IRC, not that IRC is dead. If you are not satisfied with IRC and want something similar in open source domain, take a look at [Matrix][18].

![][19]

There is a popular meme on the internet that states IRC as Discord for old people.

![][20]

Whether you agree to it, that's up to you. What I believe is that we are a diverse group of people. Some people will feel at home with IRC and some will find comfort in Discord, Matrix, etc.

--------------------------------------------------------------------------------

via: https://itsfoss.com/self-hosted-web-irc/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/08/thelounge-screenshot.png
[4]: https://thelounge.chat
[5]: https://itsfoss.com/open-source-slack-alternative/
[6]: https://github.com/thelounge/thelounge
[7]: https://itsfoss.com/content/images/2024/08/convos-chat--1-.jpg
[8]: https://convos.chat
[9]: https://itsfoss.com/open-source-cms/
[10]: https://github.com/convos-chat/convos
[11]: https://www.pikapods.com/
[12]: https://itsfoss.com/content/images/2024/08/kiwilrc-screenshot.png
[13]: https://kiwiirc.com
[14]: https://github.com/kiwiirc/kiwiirc
[15]: https://static.ghost.org/v5.0.0/images/link-icon.svg
[16]: https://itsfoss.com/content/images/2024/08/weechat.el.png
[17]: https://weechat.org/
[18]: https://matrix.org/
[19]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[20]: https://itsfoss.com/content/images/2024/09/irc-discord-meme.webp
