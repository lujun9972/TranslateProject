[#]: subject: "Google Chrome Will Soon Disable Extensions like uBlock Origin: Here's What You Can Do!"
[#]: via: "https://news.itsfoss.com/google-chrome-disable-extensions/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google Chrome Will Soon Disable Extensions like uBlock Origin: Here's What You Can Do!
======
Google Chrome is gearing up for Manifest v3 by phasing out legacy
extensions.
[![][1]][2]

Love it or hate it, [Google Chrome][3] is **the most used web browser in the world** , be it desktop or mobile. For users on desktop, they have the added benefit of having support for extensions to further extend what Chrome can do for them.

Lately, if you have been reading the news, you must have come across how Google is sunsetting [Manifest V2][4] extensions, making way for Manifest V3 one which are supposed to be a step towards improving privacy, security, and performance.

As for what a Manifest is, it's a [JSON file][5] that accompanies an extension which the browser can read to get important information like its name, version number, what permissions it needs, and more.

In line with their Manifest V2 [phaseout plans][6], the developers shared [earlier][7] this year that Chrome will begin the phaseout process in June 2024, starting with the _Beta_ , _Dev_ , and _Canary_ channels of Chrome.

They already removed the “ _Featured_ ” badge for Manifest V2 apps on the [Chrome Web Store][8], with uBlock Origin being one of the more popular ones being affected.

And, they aren't stopping there. Users of [uBlock Origin][9] might want to continue reading.

### End of uBlock Origin On Chrome? 😨

![][10]

Yes, and no. You see, Google Chrome has now started showing a warning on the Chrome Web Store [listing][11] for uBlock Origin that says:

> This extension may soon no longer be supported because it doesn't follow best practices for Chrome extensions.

Plus, when searching for it, the store doesn't show it on the top of the search results in the search bar, but does show it at the top of the search results page.

When I tested this on Vivaldi ( _a Chromium browser_ ), there was no warning shown on the web store, but the search behavior was the same.

I then went into the extension settings for it on Chrome, and saw a new dialog being shown. 👇

![][12]

It showed me a similar warning as before saying that this extension may soon no longer be supported, with a button to “ _Find alternative_ ”.

![][13]

After clicking on that, I was taken to [a webpage][14] which listed some alternatives that Google recommends, with a familiar name in the mix; More on that later.

When this phaseout is complete by the start of 2025, **uBlock Origin on Chrome as we know it will cease to exist**. Users will have to switch to alternatives like [Firefox][15] ( _or any of its derivatives)_ and [Brave][16] to take advantage of the advanced ad-blocking capabilities.

Google does mention that **after the extensions are disabled, they can be re-enabled by users** , but that option will be gradually removed from Chrome. They also point out that Enterprises using the [ExtensionManifestV2Availablilty][17] policy will be unaffected by this change until June 2025.

#### However, There's Still a Way! 😉

![][18]

As you might have noticed earlier in the recommended extensions page, **uBlock Origin Lite** is one of the options. Don't worry, it's **not an impostor, but an official offering** by Raymond Hill ( _gorhill_ ) and the uBlock Origin team that has already received the “ _Featured_ ” tag.

But, thanks to the limitations of Manifest V3, **uBlock Origin Lite is a stripped down version of uBlock Origin** , that doesn't feature all the firepower of the latter.

![][19]

As you can see above, the Dashboard for the lite extension is quite lacking when compared to uBlock Origin, which lets users add custom filters, tweak the appearance and behavior.

The extension doesn't even have element picker and zapper modes, which is a must for those pesky websites that try to hide ads in weird places, or pop-up a paywall.

But, it's not all bad. **When I tested uBlock Origin Lite on Chrome 127** , it was able to block ads on YouTube successfully. It should be fine for casual use cases such as browsing or streaming.

### 📥 Get uBlock Origin Lite

If you want to install it on your Chrome installation, then you can get it from the [Chrome Web Store][20].

Those seeking the source code can go to its [GitHub][21] repo, where they will also find what else [makes it different][22] from the OG uBlock Origin.

[uBlock Origin Lite][20]

I know it's a bummer to see uBlock Origin go away from Chrome, and personally speaking, I will be switching to uBlock Origin Lite on my Chrome installation on Windows ( _I don't use it on my Linux PC_ ) when the time comes.

_💬 What about you? Will you use Chrome after the phaseout is complete?_

**Suggested Read** 📖

![][23]

**Via** : **** [_Bleeping Computer_][24] **

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-chrome-disable-extensions/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.google.com/chrome/
[4]: https://developer.chrome.com/docs/extensions/mv2
[5]: https://developer.chrome.com/docs/extensions/reference/manifest
[6]: https://developer.chrome.com/docs/extensions/develop/migrate/mv2-deprecation-timeline
[7]: https://blog.chromium.org/2024/05/manifest-v2-phase-out-begins.html
[8]: https://chromewebstore.google.com/
[9]: https://github.com/gorhill/uBlock
[10]: https://news.itsfoss.com/content/images/2024/08/Chrome_ManifestV2_Phaseout_a.png
[11]: https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm
[12]: https://news.itsfoss.com/content/images/2024/08/Chrome_ManifestV2_Phaseout_b.png
[13]: https://news.itsfoss.com/content/images/2024/08/Chrome_ManifestV2_Phaseout_c.png
[14]: https://chromewebstore.google.com/detail/cjpalhdlnbpafiamejdnhcphjbkeiagm/related-recommendations
[15]: https://www.mozilla.org/en-US/firefox/
[16]: https://brave.com/
[17]: https://chromeenterprise.google/policies/#ExtensionManifestV2Availability
[18]: https://news.itsfoss.com/content/images/2024/08/Chrome_ManifestV2_Phaseout_d.png
[19]: https://news.itsfoss.com/content/images/2024/08/Chrome_ManifestV2_Phaseout_e.png
[20]: https://chromewebstore.google.com/detail/ddkjiahejlhfcafbddmgiahcphecmpfh
[21]: https://github.com/uBlockOrigin/uBOL-home
[22]: https://github.com/uBlockOrigin/uBOL-home/wiki/Frequently-asked-questions-(FAQ)
[23]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[24]: https://www.bleepingcomputer.com/news/google/google-chrome-warns-ublock-origin-may-soon-be-disabled/
