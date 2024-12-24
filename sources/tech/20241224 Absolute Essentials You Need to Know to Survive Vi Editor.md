[#]: subject: "Absolute Essentials You Need to Know to Survive Vi Editor"
[#]: via: "https://itsfoss.com/vi-editor-basics/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Absolute Essentials You Need to Know to Survive Vi Editor
======

[![Warp Terminal][1]][2]

Vi is on almost every Unix and Linux distribution, so why not take advantage of it?

[VI][3], pronounced as distinct letters [/ˌviːˈaɪ/][4] it's a [terminal-based text editor][5]. One of the most common tools in Unix, VI is extremely powerful for text manipulation. Although it could be a little bit challenging. And that's why I am listing the absolute basics of the Vi editor commands in this article.

📋

Vim is a popular fork/clone of VI. It includes additional features like syntax highlighting, mouse support (yes, you read that right) and more. Basic commands and keyboard shortcuts remain the same in both VI and Vim. So if you learn Vi, you are automatically learning the basics of Vim and other descendants of Vi.

### Why you should learn Vi?

Here are five reasons why I recommend learning Vi and Vim:

  1. Vi/Vim is free and open source. And remember this is [it's foss!!][6]
  2. Vi is always available since it's required by POSIX.
  3. Vi/Vim is well documented. And it also has its own user manual; you only need to type `:h` in command mode. I'll discuss command mode later in this guide.
  4. Vi/Vim has a lot of plugins. [Vim Awesome][7] is one of the most popular websites to download extensions.
  5. It does not consume a lot of system resources, and you could do a lot of tasks, even [write novels in Vim][8].



✋

It is not uncommon for some distributions to replace Vi with Vim. Even if you are using Vi commands, it runs Vim.

### Launch Vi

To execute the program, you must type vi:

```

    vi

```

![][9]

Also, you could open a file by providing its name. It will open the file for editing if it exists, or create a new one if it does not exist.

```

    vi your_file.txt

```

![][10]

### Vi modes

You must understand that Vi has 2 different modes:

  * Normal or command mode: This is the mode you use for navigating and copy-pasting
  * Insert mode: This is the editing mode where you actually type text



#### Using Normal mode in Vi

💡

This is the default mode when VI/Vim opens.

The **Normal mode** is used for actions like navigation, copy, paste, delete, text substitution (not editing), etc. You always could go back to this mode by pressing <Esc>.

##### 1\. Movement commands

These are the movement keys:

  * `h`: Left.
  * `j`: Down.
  * `k`: Up.
  * `l`: Right.



##### 2\. Deletion commands

  * `x`: It's like the delete key. Delete the character under the cursor.
  * `dd`: Deletes the current line.



##### 3\. Copy and paste

  * `y`: Yarn (Copy) command. Copies the selected text.
  * `yy`: Yarn (Copy) command. Copies the current line.
  * `p`: Paste. After using a copy command, it pastes the content after the cursor.



#### _(Command Mode)_

💡

In fact, this is not a different mode (that's why parentheses are used), but it's important to separate it because it's where you could type orders and commands

In normal mode, you could use commands by typing `:`.

For example, if you want to [save your text and exit Vi][11], you can type:

`:wq`

![][12]

Other common Vi commands you can use in normal/command mode:

  * `:h`: Help
  * `:%`: Means all the lines
  * `:s`: Used for search (and substitutions)
  * `:/foo/` : Regex to find items to replace
  * `:/bar/`: Regex to replace items with
  * `:u`: Undo last action
  * `:w`: Save
  * `:q`: Quit
  * `!`: Forces order



I have added `:` in front of each command so that it is easier to note that you have to use `:` to use the commands.

#### Insert mode

💡

In this mode, you could edit and manipulate the text.

You could enter this mode by pressing the letter `i` in Normal Mode and start typing whatever you want.

![Look at the bottom left to check insert mode][13]

  * `i`: Enter in Insert mode. Lets you insert, before the current cursor position.
  * `I`: Lets you insert at the beginning of the line.
  * `a`: Lets you append after the cursor.
  * `A`: Lets you append at the end of the line.



#### Visual Mode (only in Vim)

💡

In this mode, you could select text visually, which is very useful when working with large paragraphs.

You could enter this mode by pressing the letter:

  * `v`: Character mode
  * `V`: Line Mode
  * `Ctrl+V`: Block mode



Learn [more about the visual mode in Vim here][14].

![][15]

### A "vi" bit of history and trivia

💡

Did you know Vi is tiny, with just 160 kB in size?

It was developed in 1976 by Bill Joy as a visual mode of the **ex** line editor, also cowritten by Bill Joy.

A 2009 survey of _Linux Journal_ readers found that vi was the most widely used text editor, beating the second [Gedit][16], by nearly a factor of two (36% to 19%).

It was not until 2002 that VI was released as an open-source program under the [BSD-style license][17].

[Vim][18] (VI Improved) it's a free and open-source clone of [Stevie (ST Editor for VI Enthusiasts)][19], developed in 1991 by [Bram Moolenaar][20]. It has a huge number of extensions.

### Conclusion

Among all the [terminal based text editors][5], I prefer the Vi ecosystem.

VI/Vim is omnipresent in Unix-like operating systems due to its POSIX syntax, and when you invest a little time to unwrap its real power, you could master one of the best text-editor.

Also, you could keep growing; you could use [NeoVim][21] and its myriad of extensions and add-ons to arrive at a full IDE. The sky (and your [Lua programming][22] knowledge) is the limit.

📜

BTW, this article has been fully written in (Neo)Vim. :)

#### Author Info

![][23]

**Jose Antonio Tenés**
A Communication engineer by education, and Linux user by passion. In my spare time, I play chess, do you dare?

--------------------------------------------------------------------------------

via: https://itsfoss.com/vi-editor-basics/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://ex-vi.sourceforge.net/
[4]: https://upload.wikimedia.org/wikipedia/commons/transcoded/4/42/En-us-vi.oga/En-us-vi.oga.mp3
[5]: https://itsfoss.com/command-line-text-editors-linux/
[6]: https://itsfoss.com/
[7]: https://vimawesome.com/
[8]: https://news.itsfoss.com/configuring-vim-writing/
[9]: https://itsfoss.com/content/images/2024/12/vim-welcome-screen.png
[10]: https://itsfoss.com/content/images/2024/12/open-file-vi.png
[11]: https://itsfoss.com/how-to-exit-vim/
[12]: https://itsfoss.com/content/images/2024/12/quit-vi.png
[13]: https://itsfoss.com/content/images/2024/12/vi-insert-mode-1.png
[14]: https://linuxhandbook.com/vim-visual-mode/
[15]: https://itsfoss.com/content/images/icon/Linux-Handbook-New-Logo.png
[16]: https://itsfoss.com/gedit-tweaks/
[17]: https://www.tuhs.org/Archive/Caldera-license.pdf
[18]: https://www.vim.org/
[19]: https://en.wikipedia.org/wiki/Stevie_(text_editor)
[20]: https://en.wikipedia.org/wiki/Bram_Moolenaar
[21]: https://neovim.io/
[22]: https://www.lua.org/
[23]: https://itsfoss.com/content/images/2024/12/gose.webp
