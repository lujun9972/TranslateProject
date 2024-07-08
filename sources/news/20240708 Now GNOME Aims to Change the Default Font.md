[#]: subject: "Now GNOME Aims to Change the Default Font"
[#]: via: "https://news.itsfoss.com/gnome-default-font/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Now GNOME Aims to Change the Default Font
======
Ready to welcome a new default font on the GNOME desktop?
[![][1]][2]

Recently, GNOME seems to be focusing on replacing old defaults with [newer ones][3], and depending on who you ask, it is a welcome move. It helps the popular desktop environment look and feel more refined, with unified styling across apps and the interface.

They have been slowly, but surely revamping their core application stack with a modern _GTK4 + Libadwaita_ approach being adopted for newer applications.

But, this time around, the default font “[Cantarell][4]” seems to be on the GNOME developers' focus, which might be getting replaced with a newer, more maintained alternative.

### Is It Time To Say Goodbye To Cantarell?

![][5]

Initially [proposed][6] by GNOME foundation member Cassidy James Blaede seven months ago, the GNOME design time had been going back and forth with the idea of using [Inter][7] as the default font for future releases of GNOME.

Interestingly, a few days back, Jakub Steiner [successfully merged][8] a change that would switch the default font to “ _Inter Variable 11_ ”. But, that's not a final change, you will know why soon.

As expected in an open development environment, **some concerns were raised** when the initial proposal went out, with one of the key ones being the readability/accessibility aspect of Inter, compared to Cantarell.

One such issue was raised by [Maksym Hazevych][9], who mentioned that the letters _I_ and _L_ were impossible to differentiate, and a word like “ _illness_ ” would become “ _|||ness_ ”. They were also worried about Inter being broken for Ukrainian, but that issue has since been [fixed][10].

![][11]

For the _I_ and _L_ issue, the [optional feature][12] for disambiguating between similar-looking characters on Inter was floated by [Fernando Miguel Hahne][13], and that seems to have caught on with other members of the GNOME design team.

**In response to this proposal, another alternative to Cantarell was also** [**pitched**][14] **.**

[kramo][15], GNOME foundation member and the lead developer of [Cartridges][16], brought forward [Noto Sans][17] ( _commissioned by Google_ ) as a potentially better option than Inter.

On the issue tracker, [Allan Day][18] from the GNOME design team added that:

> The main reason why we've avoided Noto in the past is stylistic, and trying it again now I'm still convinced by it on that basis. I think that there's a reason why, despite having commissioned Noto, Google doesn't use by default in Android.

Weeks have passed since the above-mentioned saga unfolded, and when Jakub [committed][19] the change for switching the default font to Inter, [Jeremy Bicha][20] asked whether the initial proposal and the proposal for using Noto Sans should be closed.

To that, kramo replied:

> Not yet, neither. We're hoping to land it this cycle but a revert is definitely not off the table as this is a pretty big change.

And, that looks like this change is closer to becoming the default. But, **testing is still ongoing** , and until the initial proposal ( _linked above_ ) and related ones are set to closed, this is not a final change.

We can only wait and see, if this lands before the upcoming GNOME 47 release, which is set for a mid-September release.

### Want an early sneak peek?

![Left: Cantarell Right: Inter][21]

This is how Inter looked in comparison to Cantarell when I switched to it on a [Fedora 40][22] Workstation virtual machine running [GNOME 46][23].

_I was impressed with what Inter looked like._ 😃

**You can do it too** , just follow these steps on a GNOME-equipped system to get started:

  * Download the latest Inter release from its [GitHub][24] repo ( _.zip file_ ).
  * Extract the downloaded file; double-clicking should do the same if using the [Files][25] app.
  * Open/Install _InterVariable.ttf_ and _InterVariable-Italic.ttf_ with the “ _Fonts_ ” app.
  * Run the following command in the terminal to switch to Inter:



```

    gsettings set org.gnome.desktop.interface font-name 'Inter Variable 11'

```

  * Log out or Restart your computer, and check if the default font was changed correctly.



If you want to go back, just run:

```

    gsettings reset org.gnome.desktop.interface font-name

```

If you were looking for more insights, then the design team's [initiative][26] for this change is worth a read.

As usual, Reddit is all up and about over this fundamental change to GNOME. There are some pretty interesting opinions, and some humorous takeaways in one of the threads on the [Linux Subreddit][27].

_💬 What about you? Have any such takeaways? You are welcome to add them below!_

Via: [omg! linux!][28]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/gnome-default-font/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/gnome-showtime/
[4]: https://cantarell.gnome.org/
[5]: https://news.itsfoss.com/content/images/2024/07/Inter_On_GNOME_a.jpg
[6]: https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/issues/52
[7]: https://rsms.me/inter/
[8]: https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/merge_requests/85
[9]: https://gitlab.gnome.org/mks-h
[10]: https://github.com/rsms/inter/issues/657
[11]: https://news.itsfoss.com/content/images/2024/07/Inter_On_GNOME_d.png
[12]: https://rsms.me/inter/#features:~:text=Disambiguate%20between%20similar%2Dlooking%20characters%20with%20ss02%20or%20individual%20character%20variants
[13]: https://gitlab.gnome.org/fmhahne
[14]: https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/issues/54
[15]: https://kramo.page/
[16]: https://news.itsfoss.com/cartridges/
[17]: https://fonts.google.com/noto/specimen/Noto+Sans
[18]: https://blogs.gnome.org/aday/
[19]: https://gitlab.gnome.org/GNOME/gsettings-desktop-schemas/-/merge_requests/85/diffs?commit_id=d4965dbddbe8d361ad961472cf6955d8a0d07634
[20]: https://gitlab.gnome.org/jbicha
[21]: https://news.itsfoss.com/content/images/2024/07/Inter_On_GNOME_b-1.png
[22]: https://news.itsfoss.com/fedora-40-release/
[23]: https://news.itsfoss.com/gnome-46-release/
[24]: https://github.com/rsms/inter/releases
[25]: https://apps.gnome.org/Nautilus/
[26]: https://gitlab.gnome.org/Teams/Design/initiatives/-/issues/152
[27]: https://www.reddit.com/r/linux/comments/1dxtoo4/after_14_years_of_cantarell_gnome_is_testing_a/
[28]: https://www.omglinux.com/gnome-may-switch-to-inter-font/
