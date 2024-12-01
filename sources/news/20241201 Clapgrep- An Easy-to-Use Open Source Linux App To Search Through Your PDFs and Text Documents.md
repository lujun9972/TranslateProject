[#]: subject: "Clapgrep: An Easy-to-Use Open Source Linux App To Search Through Your PDFs and Text Documents"
[#]: via: "https://news.itsfoss.com/clapgrep/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Clapgrep: An Easy-to-Use Open Source Linux App To Search Through Your PDFs and Text Documents
======
Want to look for something in your text documents? Use Clapgrep to quick
search for it!
[![][1]][2]

Manually searching the contents of a text file can be taxing if you have to do it regularly, across many files.

That is where tools like [grep][3], [pdfgrep][4] and [ripgrep-all][5] come in, acting as a more efficient way of looking for information, allowing quick and easy searches for specific keywords, strings, or patterns.

However, all of them are CLI-based tools.

How about a GUI-based solution? I found one, and it is called **Clapgrep** , which looks appealing for its minimal, no-nonsense experience. So, join me as I take you through the latest [App Of The Week][6].

### Clapgrep: Superfast Text Searches

![][7]

As a Rust and Python-based application, Clapgrep is **a powerful, open source search tool for Linux** that can be used to search through multiple types of files in a specified directory.

It is a GUI front-end for [ripgrep][8].

If you look closely, the logo and name for the app are derived from [Claptrap][9], the big-mouth robots from the Borderlands series of games ( _the movie doesn't count_ ).

#### ⭐ Key Features

Clapgrep offers fast searches for text, PDFs, and common office document files, with relevant metadata such as page and line numbers being shown after a successful search query.

Some of its highlights include:

  * **Supports Regex**
  * **Actively Developed**
  * **Intuitive User Interface**



#### 💻 User Experience

I ran it on my [Fedora 40][10] system by using the official flatpak without any issues. The interface was easy to get acquainted with, and the search results were fairly simple to understand.

After setting a search path where some demo text files were stored, I searched for the term “ _floopy_ ” and Clapgrep found me the file and the lines where that term was mentioned. I could even directly open the file by clicking on the title and selecting one of the installed text editors.

![Clapgrep search works as expected, with the file opening dialog being useful as well.][11]

I then took things up a notch by enabling the “ _Case Sensitive_ ” search option and entered the term “ _What the dog doin?_ ”. Clapgrep showed me the exact lines where that term was mentioned in a text file.

![][12]

**Searching for code is straightforward too** , with a dedicated “ _Disable Regex_ ” option for turning off [regular expression][13] searches. As you can see below, I had to disable it to search for a specific line in a Python file for a snake game.

![][14]

In my testing, **I missed EPUB support**. It would have been great if Clapgrep could do that. It would make searching for passages in a book much easier.

I highly recommend this application for users who prefer a GUI app over a terminal app.

### ⚙️ Installing Clapgrep on Linux

The most recent release of Clapgrep can be found on [Flathub][15], with the [GitHub][16] repo containing the source code for those looking to build manually or contribute to the project.

[Clapgrep][15]

**Suggested Read** 📖

![][17]

* * *

[Get It's FOSS Plus Membership][18]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/clapgrep/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Grep
[4]: https://itsfoss.com/pdfgrep/
[5]: https://itsfoss.com/ripgrep-all/
[6]: https://news.itsfoss.com/tag/app-of-the-week/
[7]: https://news.itsfoss.com/content/images/2024/11/Clapgrep_a.png
[8]: https://github.com/BurntSushi/ripgrep
[9]: https://borderlands.fandom.com/wiki/Claptrap
[10]: https://news.itsfoss.com/fedora-40-release/
[11]: https://news.itsfoss.com/content/images/2024/11/Clapgrep_b.png
[12]: https://news.itsfoss.com/content/images/2024/11/Clapgrep_d.png
[13]: https://en.wikipedia.org/wiki/Regular_expression
[14]: https://news.itsfoss.com/content/images/2024/11/Clapgrep_e.png
[15]: https://flathub.org/apps/de.leopoldluley.Clapgrep
[16]: https://github.com/luleyleo/clapgrep
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[18]: https://itsfoss.com/#/portal/signup
