[#]: subject: "Decentralized YouTube Alternative PeerTube Adds Creator Mode"
[#]: via: "https://itsfoss.com/news/peertube-8-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Decentralized YouTube Alternative PeerTube Adds Creator Mode
======

[![Warp Terminal][1]][2]

[PeerTube][3] is a free and open source video hosting platform that serves as an alternative to YouTube. Unlike centralized platforms, it allows anyone to create their own video hosting instance while connecting with others through [federation][4].

It is developed by [Framasoft][5], a French non-profit organization focused on digital freedom. Before you ask, the organization keeps itself afloat on donations rather than advertising or scraping people's data.

The project **recently hit two milestones** : [PeerTube v8][6] was released, bringing collaborative features and design improvements. Just a week later, the mobile app received its long-awaited [Creator Mode][7].

### PeerTube v8: What's Fresh?

![PeerTube V8's team collaboration feature and theme selector. \(Source: Framasoft\)][8]

The biggest addition is **team collaboration for PeerTube channels**. You can now add editors to your channel who can help manage content. This was one of the most requested features. Organizations with multiple people handling videos will surely benefit from this.

People with _Editors_ access can publish videos, edit existing ones, manage playlists and comments, handle channel synchronizations, and update channel info. They can't mess around with adding/removing editors or delete the channel though.

**The video player got a fresh coat of paint**. Say hello to the " _Lucide_ " theme. The old chunky buttons are gone, replaced by a more minimal design that keeps the viewer's focus on the content.

Video imports work better now too. If an import fails, you can manually retry it instead of starting over. It also works during [channel synchronization][9]. PeerTube now automatically tries importing the video again at the next check interval ( _the default value is 1 hour_ ).

### The Mobile App Got Some Love Too!

![][10]

The mobile app now has a _Creator_ page. This was promised during the May 2025 crowdfunding. You **can upload videos straight from your phone** by either pulling a video from your gallery or recording something new.

When you begin an upload, it happens in the background, with a handy notification letting you know of its progress. These videos live in the new page ( _located at the bottom-right_ ) that allows you to edit stuff, download videos, move them into playlists, or delete any unwanted content.

Besides that, **live streaming and URL imports aren't here yet** , but they are coming!

### 📥 Get PeerTube v8

You will find the source code and all necessary self-hosting files on [GitHub][11]. The [documentation][12] will take you through the entire setup and configuration process.

[PeerTube v8][11]

* * *

**Suggested Read 📖:** [YouTube’s AI is Breaking the Creator Ecosystem][13]

![][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/peertube-8-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://joinpeertube.org/
[4]: https://en.wikipedia.org/wiki/Fediverse
[5]: https://framasoft.org/en/
[6]: https://framablog.org/2025/12/09/peertube-v8-manage-your-videos-with-your-team/
[7]: https://framablog.org/2025/12/16/publish-your-videos-with-peertube-for-mobile/
[8]: https://itsfoss.com/content/images/2025/12/peertube-8-team-collaboration-1.png
[9]: https://docs.joinpeertube.org/use/channel-sync
[10]: https://itsfoss.com/content/images/2025/12/peertube-mobile-app-creator-mode.png
[11]: https://github.com/Chocobozzz/PeerTube/releases/
[12]: https://docs.joinpeertube.org/install/any-os
[13]: https://itsfoss.com/news/youtubes-ai-mod-enshittification/
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-138.png
