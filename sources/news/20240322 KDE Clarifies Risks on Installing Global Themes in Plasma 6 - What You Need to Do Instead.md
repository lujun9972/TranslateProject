[#]: subject: "KDE Clarifies Risks on Installing Global Themes in Plasma 6 & What You Need to Do Instead"
[#]: via: "https://news.itsfoss.com/kde-plasma-global-theme-fiasco/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

KDE Clarifies Risks on Installing Global Themes in Plasma 6 & What You Need to Do Instead
======
KDE Store will start making some changes, meanwhile, you need to keep an
eye out of what you install!
Just a few days back, an openSUSE user had a rude awakening after they installed a [global theme][1] on their KDE Plasma-equipped system from the [KDE Store][2].

The theme called “ _Grey Layout_ ” **managed to erase all their data completely from the user-mounted drives on the system**. It did so by executing the dreaded “[ _rm -rf_][3]” command, which deleted anything that came in its path.

As you can see below, Reddit user, _JeansenVaars_ [posted][4] their predicament on the openSUSE Subreddit, where many sympathized with the situation, and [some calling][5] for the [KDE Store][2] to be completely remade from scratch.

![][6]

Another Reddit user also suggested them to make a post on the KDE Subreddit to gain some traction there; and that [it did][7].

The post got the attention of the KDE Plasma developers, with [Nate Graham][8] stating that the **theme in question had been removed from the store**.

All that commotion begged the following question.

### Global Themes on Plasma: A Double-Edged sword?

![Global Themes for Plasma 6 on the KDE Store][9]

If the situation mentioned above is any indication, then yes, installing global themes from the KDE Store on Plasma can be a tricky situation if you were to install something malicious or inherently broken by nature.

[Writing][10] about this issue, David Edmundson from KDE pointed out that this was caused due to a mistake in “ _some shell parsing_ ”, and not something that was done deliberately by the theme publisher.

However, the discussion around this got them thinking;

Allowing users to download and install stuff like themes, applets, scripts, etc. is a good thing to have, and that “ _nothing on the KDE store happens without explicit user interaction_ ”.

As a result, they have now realized that using terms like “global themes” and “Plasma applets”, doesn't necessarily signal that a piece of software may be unsafe.

Even though the store has the following disclaimer 👇, I am not convinced that it is enough.

While this theme's code may not have had malicious intent to begin with, some other themes can have a malicious intent, and without review, it is indeed a dangerous situation to think of 😲

![Source: David Edmundson][11]

### KDE's Move!

Fortunately, KDE is not going to sit idly by. David mentions that in the short term, **they intend to properly communicate the security implications** of extensions users download for their Plasma desktops.

In the long term, they plan to separate the “ _safe_ ” content from the “ _unsafe_ ” content, while also integrating curation and auditing into the store with improved sandbox support.

He also adds that:

> If you install content from the store, I would advise checking it locally or looking for reviews from trusted sources.

I agree with David, **users should always check reviews of anything they get from the KDE Store** , or even from any other software store for that matter. They could check for reviews on the store itself, or from reliable sources such as [Reddit][12].

You never know what kind of harm-causing software you may be adding to your Linux system if you are not careful.

On that note, if you are looking for Plasma themes, you could refer to our list of [gorgeous KDE Plasma themes][13] that we recommend. This time, be cautious about everything!

**Suggested Read** 📖

![][14]

_💬 Did this kind of situation ever happen to you? Do let me in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/kde-plasma-global-theme-fiasco/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://docs.kde.org/stable5/en/plasma-workspace/kcontrol/lookandfeel/index.html
[2]: https://store.kde.org/browse/
[3]: https://itsfoss.com/sudo-rm-rf/
[4]: https://www.reddit.com/r/openSUSE/comments/1biunsl/hacked_installed_a_global_theme_it_erased_all_my/
[5]: https://www.reddit.com/r/openSUSE/comments/1biunsl/comment/kvqyczs/
[6]: https://news.itsfoss.com/content/images/2024/03/KDE_Risky_Global_Theme.png
[7]: https://www.reddit.com/r/kde/comments/1bixmbx/do_not_install_global_themes_some_wipe_out_all/
[8]: https://pointieststick.com/
[9]: https://news.itsfoss.com/content/images/2024/03/KDE_Store_Global_Themes.png
[10]: https://blog.davidedmundson.co.uk/blog/kde-store-content/
[11]: https://news.itsfoss.com/content/images/2024/03/KDE_Store_Global_Themes_2.png
[12]: https://www.reddit.com/
[13]: https://itsfoss.com/best-kde-plasma-themes/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
