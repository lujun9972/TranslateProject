[#]: subject: "Calibre Now Lets You Chat About Your E-Books Using Local AI"
[#]: via: "https://itsfoss.com/news/calibre-lm-studio-support/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Calibre Now Lets You Chat About Your E-Books Using Local AI
======

[![Warp Terminal][1]][2]

A few months ago, [Calibre introduced its first AI feature][3], letting users highlight text and ask questions directly in the eBook reader. It was a good start but relied entirely on cloud-based AI providers.

Now, [Calibre 8.16.2][4] has arrived with some pretty handy upgrades to those capabilities, adding support for running AI models completely offline on-device. There are plenty of other new refinements too!

### 🤖 Calibre Can Now Run AI Locally

![][5]

Thanks to [LM Studio][6] integration, Calibre can tap into AI models running locally on your machine instead of needing to rely on [user data-hungry cloud services][7]. If you didn't know, LM Studio is a desktop application that lets you run large language models on your own hardware without much technical know-how.

Beyond that, this release introduces two additional AI-powered features. The first one is **a book discussion feature** where Calibre can answer questions about any book in your library through a simple right-click menu, and the second is **a reading recommendation system** that suggests similar books based on your selection.

Both of these work locally or via any configured cloud providers.

**In terms of bug fixes and improvements** , Calibre 8.16.2 addresses several issues from the previous release. The " _Ask AI what to read next"_ feature that broke in 8.16.0 now works properly, and the crash when clicking the " _Close_ " button in the Ask AI page has been fixed.

The update also corrects HTML markup escaping in the PDF input engine, updates the Amazon Italy store plugin, and fixes incorrect series indexing from Amazon Japan.

Additionally, the case-change menu returns to the comments editor after going missing in the last release.

### A Quick Test Drive

I tested out two of the new AI-powered features, and I must say, they work really well. First up was **the book discussion feature** , which can be accessed from the " _View_ " menu either by right-clicking and selecting " _Discuss selected book(s) with AI_ " or the keyboard shortcut: `Ctrl + Alt + A`.

I told it to summarize [Dracula][8], a book by Bram Stoker, and the output it provided was pretty good; I got a quick rundown of the happenings in the book without needing to fully read it. This could be handy if you have forgotten how a book ended or when you are deciding whether to commit to reading something.

Next, I tested **the paragraph explanation feature** on a section from the book. The AI broke down the text clearly and provided useful context. Keep in mind that results will vary depending on which model you use. A more capable model will give better explanations, while smaller ones might be hit or miss.

![][9]

For any AI features to work on Calibre, you need to configure an AI provider first. In my case, I used [LM Studio][10] with the [DeepSeek-R1-0528-Qwen3-8B][11] model loaded for testing. The setup is quite straightforward. I started the LM Studio server with a model loaded, entered the URL in Calibre's AI provider settings, and clicked " _Ok_ ".

### 📥 Get Calibre

Being a cross-platform eBook reader, Calibre is available for **Linux** , **Windows** , and **macOS**. The [official website][12] hosts all the relevant binaries for these platforms.

![][13]

**If you are on a Linux distribution** , then you can run the following command to get it installed:

```

    sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin

```

**Suggested Reads 📖**

![][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/calibre-lm-studio-support/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/ai-comes-to-calibre/
[4]: https://calibre-ebook.com/whats-new#:~:text=Release%3A%208.16.2%20%5B04%20Dec%2C%202025%5D
[5]: https://itsfoss.com/content/images/2025/12/calibre-8-16-2-library-view.png
[6]: https://itsfoss.com/lm-studio-linux/
[7]: https://itsfoss.com/news/privatim-declares-international-cloud-unsuitable/
[8]: https://www.goodreads.com/book/show/17245.Dracula
[9]: https://itsfoss.com/content/images/2025/12/calibre-ai-provider-lm-studio-configuration.png
[10]: https://lmstudio.ai/
[11]: https://huggingface.co/deepseek-ai/DeepSeek-R1-0528-Qwen3-8B
[12]: https://calibre-ebook.com/download
[13]: https://itsfoss.com/content/images/2025/12/calibre-linux-terminal-install-method-1.png
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-87.png
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-88.png
