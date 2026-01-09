[#]: subject: "I Thought This Wikipedia App for Linux was Pointless (I Was Wrong)"
[#]: via: "https://itsfoss.com/wike-wikipedia/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Thought This Wikipedia App for Linux was Pointless (I Was Wrong)
======

[![Warp Terminal][1]][2]

When I saw Wike in the GNOME Software store, I thought, "Who is so obsessed with Wikipedia that they need a dedicated app for it?" And that too when it doesn't even work offline. Why use an app instead of just accessing Wikipedia from a web browser?

Yet I decided to give it a spin. It turns out that taking Wikipedia out of a messy browser tab and putting it into its own clean, native space entirely changes the experience. And there is more to this app than it seems on the surface.

### What is Wike?

[Wike][3] is a native Wikipedia app for your desktop. It is a GNOME Circle application, which means it meets GNOME’s quality, design, and openness standards and is officially recognized by the GNOME Project.

Even though it is designed for GNOME, you can use it on other desktop environments too, at the cost of some missing features.

Some of Wike features are

  * Supports more than 300 languages
  * Simpler and distraction-free view of articles
  * Desktop searches
  * Bookmarks and List



Let me show some of the features that make Wike worth a install for a Wikipedia loving Linux user.

### Search articles from GNOME Activities

One of the best features of Wike is that it integrates into the [GNOME Activities Search][4]. You can search Wikipedia topics right from the GNOME search. No need to open a web browser or even Wike itself.

You need to enable this feature, though. Open Wike, go to the preferences and enable the "Allow Live Search on Desktop" toggle button.

![Enable Shell Search Toggle][5]

This will add an entry "Wike" to your list of search providers. Open GNOME Settings and go to the **Search** section. Here, enable the toggle button adjacent to the Wike entry.

![Enable Wike Search Provider][6]

That's it. You can now search for Wikipedia contents by hitting the Super key and entering the search term.

![Wikipedia Results in GNOME Shell Search][7]

### Enjoy link previews

Wike can give you a small preview of hyperlinks when you hover over a link. For this, you need to enable the **Link Preview** from the top-right eye button, as shown in the screenshot below:

![Link Preview in Wike][8]

Once done, hover over any link to get that cute little preview.

![Link Preview][9]

### Read content in your favorite font

You can change the font to any [installed font on the system][10]. For this, click on the eye button on top-right and select fonts.

![Click on Font Name][11]

Now, choose your favorite font from the list.

![Choose a font][12]

### Add a table of contents in the sidebar

You can get a **dismissable table of contents** in the sidebar. Enable it whenever needed. At other times, save essential screen space.

![Table of Contents in Wike][13]

### Set your favorite language

You can select a set of languages in which you can later translate the articles. For this, click on the search button in the left sidebar and click 'Pick your Languages'.

![Pick your Language][14]

From the new dialog box, search and select languages that you want. I have selected French other than English.

![Search and Select Language][15]

Now, you can see that I have two languages, English and French, available.

![English and French Language Available][16]

While you are viewing an article, click on the **Translate** button in the sidebar and select the languages from **Your Languages** list.

![Select French to Translate to French][17]

You can see that the article now appears in French.

![Content in French Language][18]

Likewise, you can set a list of languages so that a one-click change is possible.

If you don't want to set any languages, you can always select a language from the list of language that Wikipedia content is available. Just select the **All Languages** option as shown in the screenshot below, and select a language of your choice.

![Select all Languages][19]

### Copy link with highlight

You can always use `CTRL+U` keyboard shortcut to copy a Wikipedia URL. But you can also copy the link to a highlighted section of the page.

Select a text or paragraph while reading and right click on it. Now, select **Copy Link with Highlight**.

![Select Copy Link with Highlight][20]

You can share this link with others, and they, in their browser, get the exact text highlighted. Perfect for winning online arguments 😉

![Highlighted section in browser.][21]

This works in both recent Firefox and Chromium-based browsers.

### Other features I like

The ability to bookmark and create a reading list is an excellent feature for Wikipedia explorers.

![Bookmark and Reading List][22]

System theme alignment with a light, dark and sepia colored interface adds to modern feel.

![Wike Color Theme][23]

A neatly arranged history according to time of visit could be helpful, too.

![Visit History][24]

Multiple tabs support lets you enjoy prolonged Wikipedia reading sessions.

![Multiple tabs][25]

### Install Wike

If all this makes you want to try Wike, you can get it on your Linux system in Flatpak format. If your system has [Flatpak support enabled][26], use the command:

```

    flatpak install flathub com.github.hugolabe.Wike

```

### Wrapping up

I don't need to tell you that this is for the people who enjoy the free and open knowledge provided by Wikipedia.

I also think that it would have made more sense to provide the option to read the content without the internet. Sure, you can [self-host entire Wikipedia][27] or buy a [PrepperDisk that comes with all sorts of knowledge in offline mode][28]. But nothing beats the simplicity of an offline encyclopedia app of the 90s.

Your views are welcome.

--------------------------------------------------------------------------------

via: https://itsfoss.com/wike-wikipedia/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://hugolabe.github.io/Wike/
[4]: https://itsfoss.com/gnome-search/
[5]: https://itsfoss.com/content/images/2026/01/add-shell-search-enable-1.png
[6]: https://itsfoss.com/content/images/2026/01/enable-wike-as-a-search-provider.png
[7]: https://itsfoss.com/content/images/2026/01/get-wikipedia-search-in-shell-search-result.png
[8]: https://itsfoss.com/content/images/2026/01/link-preview-wike.png
[9]: https://itsfoss.com/content/images/2026/01/getting-link-preview-in-wike.png
[10]: https://itsfoss.com/install-fonts-ubuntu/
[11]: https://itsfoss.com/content/images/2026/01/click-on-fonts.png
[12]: https://itsfoss.com/content/images/2026/01/view-fonts.png
[13]: https://itsfoss.com/content/images/2026/01/table-of-contents-wike.png
[14]: https://itsfoss.com/content/images/2026/01/pick-your-language-wike-settings.png
[15]: https://itsfoss.com/content/images/2026/01/search-and-select-a-language.png
[16]: https://itsfoss.com/content/images/2026/01/english-and-french-available.png
[17]: https://itsfoss.com/content/images/2026/01/select-french-translate.png
[18]: https://itsfoss.com/content/images/2026/01/wiki-french-language.png
[19]: https://itsfoss.com/content/images/2026/01/all-languages-wike.png
[20]: https://itsfoss.com/content/images/2026/01/copy-link-to-highlight.png
[21]: https://itsfoss.com/content/images/2026/01/highlighted-section-in-browser.png
[22]: https://itsfoss.com/content/images/2026/01/bookmark-reading-list-wike-1.png
[23]: https://itsfoss.com/content/images/2026/01/sepia-color-view-wike.png
[24]: https://itsfoss.com/content/images/2026/01/history-wike.png
[25]: https://itsfoss.com/content/images/2026/01/tabbed-view-wike.png
[26]: https://itsfoss.com/flatpak-guide/
[27]: https://itsfoss.com/self-host-web-archives-kiwix/
[28]: https://www.prepperdisk.com/
