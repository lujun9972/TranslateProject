[#]: subject: "Zed: A Next-Gen Rust-Based Open Source Code Editor With AI"
[#]: via: "https://news.itsfoss.com/zed-editor/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Zed: A Next-Gen Rust-Based Open Source Code Editor With AI
======
From the creators of the now defunct Atom, we have Zed editor with
interesting capabilities.
[![][1]][2]

[Code editors][3] are an essential piece of equipment in the arsenal of software developers, providing them with a reliable environment for writing, editing, and debugging all kinds of code.

They are known for superior handling of code, as they feature advanced debugging tools, syntax highlighting, auto-completion, extensions, and a host of other features.

Some popular names would be [Vim][4], [**Kate editor**][5], [VS Code][6], and [Sublime Text][7].

There's also another one that's increasing in popularity; it is from the people behind [Atom][8] and [Tree-sitter][9]. Called “ **Zed Editor** ”, it is an open-source code editor that you might want to try.

### Zed Editor: A Modern Code Editor

![][10]

Put together mainly using [Rust][11], Zed Editor is an offering by Zed Industries that uses **three different licenses** for distribution.

The source code for the editor is available under [GPL 3.0][12], the server-side components under [AGPL 3.0][13], and GPUI ( _the user interface framework_ ) under [Apache License 2.0][14].

#### ⭐ Key Features

In a mixed bag of features such as support for running in CLI, diagnosing project-wide errors, support for split panes, markdown previews, and many more such features.

Here are some notable talking points of Zed Editor:

  * **Cross-Platform**
  * **Optional AI Features**
  * **Real-Time Collaboration**



#### 💻 User Experience

I tested Zed Editor on a [Fedora 40][15]-equipped laptop by installing a third-party Flatpak package and putting in Rust code for a FOSS-themed quiz ( _generated using_ [_Gemini_][16]) to see how it performed.

By default, any added content is treated as plain text, **I used the language switcher to change it to Rust** so that I would get proper syntax highlighting, indentation, error detection, and other useful language-specific functions.

![][17]

The switch highlighted all the Rust elements correctly, and I then focused on Zed Editor's user interface. The overall feel of the editor was minimal, with all the important options being laid out nicely.

![][18]

The status bar below had some interesting panels. The first one I checked was the **Terminal Panel** , which, as the name suggests, lets you run commands, scripts, and facilitates interaction with system files or processes directly from within the editor.

![Zed Editor's AI-powered features.][19]

I then moved to the **Assistant Panel** , which is home to various large language models that can be integrated into Zed Editor. There are options like **Anthropic** , **GitHub Copilot Chat** , **Ollama** , **OpenAI** , and **Google AI** 🤯

I went with Google AI and set up an API key on AI Studio to get started with the Assistant on Zed Editor. After selecting the Gemini 1.5 Pro model, I asked it if my code was correct.

It asked me for more details, so I pasted the code into the prompt window, and it confirmed that the code was indeed correct, with useful insights and suggestions about the code.

Technically, it was reviewing its code, as I had used Gemini ( _on a web browser)_ to concoct it in the first place.

The Zed Editor team has also recently introduced [Zed AI][20] in collaboration with [Anthropic][21] for assisting with coding, allowing for code generation, advanced context-powered interactions, and more.

![][22]

The **real-time collaboration features** on Zed Editor are quite appealing too. To check them out, I had to log in with my GitHub account. After logging in, the Collab Panel opened up, and I could see many channels from the official Zed community.

I could chat with others, add collaborators to existing projects, join a call with the option to share my screen and track other collaborators' cursors, add new contacts, and carry out many other collaborative tasks.

![Zed Editor extensions and themes.][23]

One can also **use extensions and themes to extend what Zed Editor can do**. There are some nice pre-installed themes as well.

If you are a developer, you can test its coding capabilities better. Overall, to me, Zed Editor feels like a polished experience, and its clean design and handy features make it a viable choice for coders who do not mind tinkering around their experience for a change.

### ⚙️ Installing Zed Editor on Linux

Zed Editor is available on Linux through a curl script. You can grab the latest stable release by running the following command:

```

    curl -f https://zed.dev/install.sh | sh

```

For other platforms, you may visit the [official website][24], and for alternative downloads ( _like_ [_Flatpak_][25]), you can refer to its [documentation][26] for all the available options.

The source code is hosted over at [GitHub][27] for you to check out.

[Zed Editor][24]

**Suggested Read** 📖

![][28]

* * *

[Get It's FOSS Plus Membership][29]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/zed-editor/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Source-code_editor
[4]: https://www.vim.org/
[5]: https://news.itsfoss.com/kate-editor/
[6]: https://code.visualstudio.com/
[7]: https://www.sublimetext.com/
[8]: https://github.blog/news-insights/product-news/sunsetting-atom/
[9]: https://tree-sitter.github.io/tree-sitter/
[10]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_a.png
[11]: https://www.rust-lang.org/
[12]: https://www.gnu.org/licenses/gpl-3.0.en.html
[13]: https://www.gnu.org/licenses/agpl-3.0.en.html
[14]: https://www.apache.org/licenses/LICENSE-2.0
[15]: https://news.itsfoss.com/fedora-40-release/
[16]: https://gemini.google.com/
[17]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_b.png
[18]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_c.png
[19]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_d.png
[20]: https://zed.dev/ai
[21]: https://www.anthropic.com/
[22]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_g.png
[23]: https://news.itsfoss.com/content/images/2024/10/Zed_Editor_h.png
[24]: https://zed.dev/download
[25]: https://flathub.org/apps/dev.zed.Zed
[26]: https://zed.dev/docs/linux
[27]: https://github.com/zed-industries/zed
[28]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[29]: https://itsfoss.com/#/portal/signup
