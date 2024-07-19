[#]: subject: "Firefox's New Controversial Feature: Is it a problem?"
[#]: via: "https://news.itsfoss.com/firefox-ppa-ad/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Firefox's New Controversial Feature: Is it a problem?
======
The feature may be a necessary evil, but what do you think?
[![][1]][2]

[Mozilla][3]'s Firefox is unmistakably one of the last-standing forces against the onslaught of [Chromium][4]-based browsers, and many people rely on it to get things done, without sacrificing their privacy.

Sure, there are some fascinating projects such as the [revived Servo][5], and the increasingly popular [Ladybird][6], but, these are still under heavy development, and we will have to wait a bit before we start seeing some tangible results.

Unfortunately, with a [recent release][7], Firefox has found itself in the middle of a controversy, that has struck a rather fiery conversation across the internet.

### Firefox Under Fire: What Have They Done?

![Privacy-Preserving Attribution enabled by default on Firefox 128][8]

Many people over the past few days have been [lashing out][9] at Mozilla for enabling [Privacy-Preserving Attribution][10] (PPA) by default on Firefox 128, and the lack of publicity surrounding its introduction.

There are even [reports][11] that **the “Distributed Aggregation Protocol” (DAP) used underneath is not private by design**. Provided Mozilla and [ISRG][12], the ones behind this protocol, were to collude, trying to breach privacy. If that happened, it would allow advertisers to identify the behavior of individual browsers.

If you were wondering what PPA is, it is **a bare-bones, experimental feature** that is supposed to serve as a privacy-focused approach for collecting limited user data and serving ads on a website.

When a website detects that a user clicked on an ad, it can ask the browser for a report. The browser will then encrypt it, and then anonymously submit it to an “aggregation service” ( _not the website_ ) using DAP. After which, the report is combined with other similar reports by the aggregation service, and the website receives periodic reports with a collection of such data.

Even though Mozilla mentioned that PPA would be enabled by default on Firefox 128 in a few of its past blogs, they failed to communicate this decision clearly, to a wider audience.

There's also a discussion going on [Mozilla Connect][13] calling for PPA to be removed from Firefox, with many supporters joining in.

### Other Side Of The Coin

In response to the public outcry, Firefox CTO, [Bobby Holley][14], had to [step in][15] to clarify what was going on. He started with how the internet has become a massive cesspool of surveillance, and doing something about it was the primary reason many people are part of Mozilla.

He then expanded on their approach with Firefox, which, historically speaking, has been to ship a browser with anti-tracking features baked in to tackle the most common surveillance techniques.

But, there were two limitations with this approach, one was that advertisers would try to bypass these countermeasures.

The second, **most users just accept the default options that they are shown** , and that Mozilla doesn't believe in modal consent dialogs as they find such dialogs to be a “ _user-hostile distraction from better defaults_ ”.

📋

The kind of dialogs seen on most websites these days, where the user has to give their consent for cookies on their browser.

Similarly, [Bas Schouten][16], Principal Software Engineer at Mozilla, made it clear at the end of a heated Mastodon [thread][17] that:

> This is making privacy a privilege for the people that work to inform and educate themselves on the topic. People shouldn't need to do that, everyone deserves a more private browser. Privacy features, in Firefox, are not meant to be opt-in.

> They need to be the default.

> If you are 'completely anti-ads' (i.e. even if their implementation is private), you probably use an ad blocker. So are unaffected by this.

As expected, this move has also generated a great deal of misunderstandings and mob-like reaction across social media, with some taking shots at Mozilla's [acquisition of Anonym][18], an advertisement tech company.

[Andrew Moore][19], a Solutions Architect out of Montreal, tried his best to demystify some common misconceptions with a [detailed blog][20], where he shed light on the inner workings of PPA.

He shared that the goal of this API was to study the viability of such implementations, so that one day, existing ad networks could start moving away from invasive individual tracking.

Even one of our reader's had something [to add][21] on this topic, and I do agree with what they said:

> When you condemn Mozilla's attempt to introduce adtech in Firefox (with an option to turn it off), please note that Mozilla is fighting a life-and-death battle for the survival of Firefox.

> If Firefox goes away, so do its alternatives such as LibreWolf, Waterfox and the most secure web browser currently available, Floorp. Support Firefox, because if not, you will be even more vulnerable to global tech companies.

In today's age, **advertising has become a necessary evil for an Internet-focused organization to stay in business** , and what Mozilla seems to be trying to, is pushing for “better defaults”, that can hopefully be the standard one day.

The standard right now is to harvest user data in any way possible, a user's right to privacy doesn't matter, authority over their data doesn't matter, what matters are the metrics.

As they say, “ _It's a numbers game_ ”, so it's refreshing to see someone try something different.

However, as mentioned earlier, **I do feel that Mozilla should have communicated this decision more adequately**. Just a few blog posts obviously can't help convey such a major change, that too in an age where a user's attention span is a rare commodity.

When users updated to the 128 release, they should have shown a pop-up or opened up a new tab with an easy-to-understand description of PPA. Showing how it is enabled by default, and with an option for the user to disable it, and some reassuring text sprinkled about.

Anyhow, what's done is done. For users who don't want this, they can **follow these steps to disable PPA** :

  * Go into the three-ribbon/hamburger menu at the top-right.
  * Select “ _Settings_ ”.
  * Under the “ _Privacy & Security_” menu, scroll down to the “ _Website Advertising Preferences_ ” section.
  * Uncheck the box called “ _Allow websites to perform privacy-preserving ad measurement_ ”.



_💬 Which side of the discussion do you fall in? Let me know in the comments below._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/firefox-ppa-ad/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.mozilla.org/
[4]: https://www.chromium.org/
[5]: https://news.itsfoss.com/servo-rust-web-engine/
[6]: https://ladybird.org/
[7]: https://news.itsfoss.com/firefox-128-release/
[8]: https://news.itsfoss.com/content/images/2024/07/Firefox_128_Privacy_Preserving_Ad.png
[9]: https://gladtech.social/@cuchaz/112775302929069283
[10]: https://support.mozilla.org/en-US/kb/privacy-preserving-attribution
[11]: https://blog.privacyguides.org/2024/07/14/mozilla-disappoints-us-yet-again-2/
[12]: https://www.abetterinternet.org/
[13]: https://connect.mozilla.org/t5/discussions/remove-quot-privacy-preserving-attribution-quot-ad-measurement/td-p/61874
[14]: https://www.linkedin.com/in/bobbyholley
[15]: https://www.reddit.com/r/firefox/comments/1e43w7v/a_word_about_private_attribution_in_firefox/
[16]: https://www.linkedin.com/in/baschouten/
[17]: https://mastodon.social/@Schouten_B/112802704468632176
[18]: https://blog.mozilla.org/en/mozilla/mozilla-anonym-raising-the-bar-for-privacy-preserving-digital-advertising/
[19]: https://ca.linkedin.com/in/andrewmoore
[20]: https://andrewmoore.ca/blog/post/mozilla-ppa/
[21]: https://news.itsfoss.com/firefox-128-release/?ht-comment-id=15410373
