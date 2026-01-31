[#]: subject: "Your eBooks Don't Have to Look Boring, Calibre 9.0 Now has Shelves"
[#]: via: "https://itsfoss.com/news/calibre-9-0-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Your eBooks Don't Have to Look Boring, Calibre 9.0 Now has Shelves
======

[![Warp Terminal][1]][2]

Many of you might already be users of [Calibre][3]. If you don't know what that is, it is a very capable eBook manager that has many handy features like format conversion, news fetching, metadata editing, and a built-in viewer that supports most eBook formats.

It recently gained support [for running AI locally][4] via LM Studio, and during my use of it, everything worked as expected. I was able to ask questions about books in my library and get personalized reading recommendations without needing to send any data to cloud services.

Now, a [new release][5] is here, bringing with it some neat upgrades.

### Calibre 9.0: What's New?

![][6]

The brand-new bookshelf view, for starters. If you click on the " _Layout_ " button on the bottom-right of the Calibre app, you will find the new view. Click on it to activate a virtual shelf of neatly arranged eBooks.

This should be useful if you have a large library of books and want to get the look and feel of a physical bookshelf but on a monitor. **A quick tip for you here** : you can hide the " _Book details_ " dialog that's on the right and resize the sidebar menu on the left to fill your entire screen with the shelf visible.

_It would've been even cooler if we could hide the top menu bar too!_ 😅

Anyhow, moving on, the viewer now **lets you type in a page number directly to jump to it** instead of making you scroll through the entire list of page numbers. It also has a new " _Edit book_ " button that allows editing the currently opened book, provided it is in formats such as _EPUB_ , _AZW3_ , or _KEPUB_.

**For Linux users with touchpads** , Calibre now supports momentum-based scrolling in the book list. This means you can flick through your library, and the list will keep moving smoothly instead of stopping immediately when you lift your finger.

On the bug-fixing side of things, EPUB3 metadata handling has been improved to work with identifiers that use HTTP URLs without the `url:` prefix, SVG export has been improved, and GPU acceleration for Qt WebEngine is now disabled by default to prevent crashes on older systems.

### 📥 Get Calibre

Users on **Linux** , **Windows** , and **macOS** can get this Calibre release from the [official website][7]. For Linux users specifically, they can use the following command to grab a fresh copy of Calibre or update their existing installation:

```

    sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin

```

[Calibre][7]

The source code for the app can be found on [GitHub][8].

* * *

**Suggested Read 📖:** [_Calibre Now Lets You Chat About Your E-Books Using Local AI_][4]

![][9]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/calibre-9-0-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://calibre-ebook.com/
[4]: https://itsfoss.com/news/calibre-lm-studio-support/
[5]: https://calibre-ebook.com/whats-new#:~:text=Release%3A%209.0%20%5B30%20Jan%2C%202026%5D
[6]: https://itsfoss.com/content/images/2026/01/calibre-9-0-bookshelf-view.png
[7]: https://calibre-ebook.com/download
[8]: https://github.com/kovidgoyal/calibre
[9]: https://itsfoss.com/content/images/icon/android-chrome-512x512-253.png
