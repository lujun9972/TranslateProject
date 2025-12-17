[#]: subject: "Easier Than Nano! Fresh is a Fresh New Rust-based Terminal Editor for Linux"
[#]: via: "https://itsfoss.com/fresh-terminal-text-editor/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Easier Than Nano! Fresh is a Fresh New Rust-based Terminal Editor for Linux
======

[![Warp Terminal][1]][2]

Terminal text editors are everywhere in the Linux ecosystem. **Vim and GNU Emacs are the most popular choices** , while something like Nano is the go-to for many people ( _including me_ ) for its easy-to-use nature.

Most of these require learning new keybindings or [modal editing][3]. The learning curve can be steep for beginners or casual users ( _like me_ ).

Fresh is **a new Rust-based terminal text editor** that takes a different approach. It uses standard keybindings like _Ctrl+S_ for saving, _Ctrl+F_ for searching, and _Ctrl+Z_ for undoing. It works like a GUI editor but runs in your terminal.

### What's so "Fresh" About This?

![][4]

Fresh has **full mouse support**. You can click to place the cursor and drag to select text. The editor includes a **command palette** ; just press `Ctrl+P` to search for any command.

If you press `Ctrl+E`, **the built-in file explorer** appears on the left side. You can navigate directories and open files with this, and the split-pane layout makes navigating easy.

[LSP][5] support is also provided, with features like go to definition, hover documentation, and diagnostics working without extra setup. Plus, **Fresh can handle files over 10 GB** , and it includes niceties like line numbers, word wrap, an embedded terminal, and a built-in markdown preview.

There is **plugin support** too; these use [TypeScript][6] and run in a sandboxed [Deno][7] environment.

### A Quick Spin

I tested Fresh on [Ubuntu 25.10][8], and it was nice. Editing files worked as expected. Standard shortcuts like `Ctrl+S` for saving and `Ctrl+Z` for undoing mistakes work without issues. Mouse navigation works well for interacting with the text and the interface.

The file manager was very responsive, appearing on the left side and letting me navigate directories quickly. The command palette was handy for searching specific commands, and the menu bar at the top has the usual options you'd see in a GUI text editor.

Quitting Fresh is easy with `Ctrl+Q`, and the pre-installed themes accessible via the command palette and the menu bar were good too. I liked the " _Dark_ " one.

### Freshen Up Your System

![The aforementioned Dark theme on the left, the terminal installation method for Fresh on the right.][9]

You can get Fresh for **Debian** , **Ubuntu** , and **other derivatives** by following these steps. First, download the latest `.deb` package from the [releases page][10] for your computer ( _the amd64 one if you aren't on Arm_ ).

Then, run the following command in the terminal to get it installed:

```

    sudo dpkg -i fresh-editor_*.deb

```

Alternatively, you could double-click on the DEB file and get it installed through the App Center on Ubuntu. To launch the editor, run the `fresh` command.

You can find instructions for **other Linux distributions** and **macOS** on the [official website][11]. If you feel lost, then [the documentation][12] is a handy resource to have by your side.

[Fresh][13]

**Suggested Read 📖:** [Best Text Editors for the Linux Command Line][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/fresh-terminal-text-editor/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://carlosbecker.com/posts/ed/#:~:text=A%20modal%20text%20editor%20has%20multiple%20modes%20of%20operation%2C%20and%20the%20keys%E2%80%99%20functions%20change%20depending%20on%20which%20mode%20it%20is%20in.%20While%20TurboC%20and%20nano%20aren%E2%80%99t%20modal%20text%20editors%2C%20Vi%20and%20Vim%20are.
[4]: https://itsfoss.com/content/images/2025/12/fresh-terminal-editor-manual-page.png
[5]: https://en.wikipedia.org/wiki/Language_Server_Protocol
[6]: https://www.typescriptlang.org/
[7]: https://deno.com/
[8]: https://itsfoss.com/news/ubuntu-25-10-release/
[9]: https://itsfoss.com/content/images/2025/12/fresh-terminal-editor-themes-1.png
[10]: https://github.com/sinelaw/fresh/releases
[11]: https://sinelaw.github.io/fresh/
[12]: https://github.com/sinelaw/fresh/blob/master/docs/USER_GUIDE.md
[13]: https://sinelaw.github.io/fresh/#install
[14]: https://itsfoss.com/command-line-text-editors-linux/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-120.png
