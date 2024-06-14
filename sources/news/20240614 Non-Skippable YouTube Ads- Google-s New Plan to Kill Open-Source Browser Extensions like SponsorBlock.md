[#]: subject: "Non-Skippable YouTube Ads: Google's New Plan to Kill Open-Source Browser Extensions like SponsorBlock"
[#]: via: "https://news.itsfoss.com/google-youtube-ads/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Non-Skippable YouTube Ads: Google's New Plan to Kill Open-Source Browser Extensions like SponsorBlock
======
Google's back at it again, with a new strategy for YouTube.
[![][1]][2]

Recently, [Google][3] has been pushing hard to get rid of ad-blockers and similar extensions off Chrome and their revenue-generating service YouTube.

Take for instance the upcoming switch to Manifest V3 on Chrome, which, when rolled out, would affect ad-blockers in a big way. Naturally, that move led to plenty of criticism by many developers, but, the transition is now [back on track][4] after they took in feedback from the community.

However, they do not have plans to stop there, and are going a step further by testing something quite nefarious; even [Gru][5] would be surprised by it.

Let's see what they are up to now.

### Google On The Offensive, Again

Originally discovered by [SponsorBlock][6], a popular open-source browser extension that helps people skip those sneaky sponsor segments in YouTube videos.

They found out that **YouTube was experimenting with server-side advertisement injection** , which means that an ad would be directly inserted into the video stream, making it very tricky to block such ads using ad-blockers.

For SponsorBlock, this would also mean that their extension wouldn't be able to be accurate in how it functions, as the timestamps for the videos would be offset by the ad times.

They had shared their findings in a very insightful [X thread][7]. 👇

> YouTube is currently experimenting with server-side ad injection. This means that the ad is being added directly into the video stream.
>
> This breaks sponsorblock since now all timestamps are offset by the ad times.
>
> — SponsorBlock (@[sponsorblock@fosstodon.org][8]) (@SponsorBlock) [June 12, 2024][9]

Furthermore, SponsorBlock has set up their servers to detect when someone with this in-video ad experiment is sending a submission, it will be automatically rejected to prevent erroneous submissions.

The lead developer also posted a [helpful FAQ][10] to clear up the most common questions, where they clarify that this is not the end of SponsorBlock, and the extension will not work for anyone who's part of the experiment.

If you were wondering **whether ad blockers will be affected by this**. Well, they would, definitely, but I am confident that the developers of such extensions will be able to skirt their way around this new pesky move by Google.

There's even [reports][11] that YouTube is forcing users to log in to watch videos, which would be another dubious move that will annoy people if implemented widely.

Of course, this doesn't address the main problem, which is the dominance of YouTube. It has grown to be a very useful resource for both Google, and its users. But, as we know, a service dominating its field is never good for competition.

That is why I suggest users switch to services like [PeerTube][12], where you will find many [instances][13] that cater to a wide variety of interests and activities.

_💬 Anyhow, that was the latest of Google's troubling moves. What are your thoughts on this?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-youtube-ads/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.google.com/
[4]: https://developer.chrome.com/blog/resuming-the-transition-to-mv3
[5]: https://despicableme.fandom.com/wiki/Felonius_Gru
[6]: https://sponsor.ajay.app/
[7]: https://x.com/SponsorBlock/status/1800835402666054072
[8]: mailto:sponsorblock@fosstodon.org
[9]: https://twitter.com/SponsorBlock/status/1800835402666054072?ref_src=twsrc%5Etfw
[10]: https://gist.github.com/ajayyy/f7b1807e13731c25cef4c2c057d022bc
[11]: https://www.reddit.com/r/privacy/comments/1ciat0o/youtube_is_forcing_people_to_sign_in_to_watch/
[12]: https://news.itsfoss.com/peertube-v6/
[13]: https://joinpeertube.org/instances
