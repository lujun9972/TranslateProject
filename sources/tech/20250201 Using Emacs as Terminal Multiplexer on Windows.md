[#]: subject: "Using Emacs as Terminal Multiplexer on Windows"
[#]: via: "https://itsfoss.com/emacs-as-terminal-multiplexer-windows/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Using Emacs as Terminal Multiplexer on Windows
======

[![Warp Terminal][1]][2]

If you're a developer or a power user, you probably understand the importance of having an efficient and organized workflow.

Whenever I get to work with a Windows-based system, I really miss the terminal emulator along with the ability to quickly switch between different terminal sessions. Not to mention, sometimes I need to gather 2-3 command sessions in a single view. There are many scenarios where I need to run multiple commands simultaneously.

Sure, we have the command prompt, or Windows terminal to use, but it is not enough for a similar experience.

💡

Windows 11 Terminal does provide you the ability to create multiple panes within a tab. You can use the shortcut ****Alt + Shift + -**** and ****Alt + Shift**** \+ ****+**** to create horizontal and vertical panes, respectively.

With Linux, I had access to terminal multiplexers like **tmux** and **screen.**

But, wait, there is a solution on Windows 10 and Windows 11 that can work as a terminal multiplexer and a text editor – all in one!

Enter **Emacs** 🤩

### Why Use Emacs as a Terminal Multiplexer?

While I have already mentioned why we are looking at a solution like Emacs, let me give highlight some more reasons you want to try this out (apart from the fact that it is open source and super awesome):

#### 1\. Less is More

Emacs is an all-in-one solution. It can work as a terminal, text editor, file manager, email client, calculator, a text-based web browser. All these features are packed in a 150 MB zipped file. Pretty crazy, right? You won't know all this until you give it a try!

#### 2\. Powerful Customization

Emacs is famously customizable. You can tweak almost everything: keybindings, window layouts, themes, and even the behavior of your terminal sessions. This allows you to tailor the environment to your exact needs, providing a highly efficient experience.

#### 3\. Integrated Shell Support

Emacs allows you to open a shell session inside a buffer, and with its support for **eshell** , **shell** , you can run shell commands, manipulate files, and perform operations right alongside your text editing.

#### 4\. Flexibility with Windows

Emacs is great at handling multiple buffers in a single window. You can split your window into multiple panes (or "windows," as Emacs calls them), just like with tmux, enabling you to work on different tasks simultaneously without feeling cluttered.

### Using Emacs as Terminal Multiplexer

Now that you know the benefits, to help you use it, let me give you a walkthrough on using Emacs as a terminal multiplexer.

#### Step 1: Install Winget

Winget comes as a part of the **App Installer** package. So, you need to first install the App Installer from [Microsoft Store][3]:

![][4]

#### Step 2: Install Emacs on Windows 11 or Windows 10

Winget makes it super simple to install Emacs. Simply run this command:

```

    winget install emacs

```

#### Step 3: Open Emacs

Open Emacs from the Windows 11 Start menu.

#### Step 4: Run shell

Within emacs, press **Alt + X** , and type **shell** and hit **Enter** to get the interactive user interface.

![][5]

💡

In Emacs terminology, the Alt key is often referred to as M, and Ctrl is referred to as C. I have used C, and M to represent the same throughout the article.

Now, with Emacs, you will realize the following benefits:

  * A nice auto-completion system
  * Ability to edit any previous command at a point
  * Quickly jump between different command sessions.



![Autocomplete selection][6]

To see autocomplete in **shell** buffer, simply type in 'a' and then hit Tab, you’ll be presented with a list of options. You can select one of the options with a mouse click as shown above.

![][7]

📋

If you see terms like C-s, or C-u, or Alt-x, read it as Ctrl + s/u or Alt + x.

To search for previous commands and outputs, hit C-s < _your-term_ >. This is what I referred to when I mentioned consistent keybindings for all of your workflow. Within your Emacs environment, C-s will do a forward search everywhere unless you modify it.

![][8]

To edit your previous commands, move your cursor to the previous command or do a quick search, make the necessary adjustments, and hit enter.

If you want to open another shell, press **C-u** keys, and then **Alt-x** to open another shell.

By default, this buffer will be named “Shell 2”. And you can navigate between these different shells by C-x b and Tab. Use the mouse for selection. We’ll make it more efficient in the next section.

### Terminal Multiplexing

Now here comes the magic. If you want to create two vertical layouts, simply use the keybinding **C-x + 3**. Then, if you want two horizontal layouts, use the shortcut **C-x + 2**.

![][9]

For navigation to other panes, you can use your mouse or use Emacs shortcut
**C-x + o**

### Auto-completion and multi-window layouts

Another quick tip. With just one line configuration, Emacs can provide useful completions based on your action with **ido-mode**.

Save the line below in a new _.emacs_ file usually located at your user `C:/Users/YourUser/AppData/Roaming`. After saving, you don’t need to restart Emacs.

```

    (ido-mode 1)

```

Let’s enable winner-mode as well to undo and redo multi-window layouts. Add the line below to the config file like you did above:

```

    (winner-mode 1)

```

Finally, save this two-line configuration

Simply, do Alt + x and then type **eval-buffer.**

![][10]

Now with ido-mode, you can simply switch to shell 2 buffer using C-x b 2.

![][11]

With winner-mode in place, if you want to get a full preview of a single pane, press **C-x + 1** , and then to go back to the previous layout, run

```

    winner-undo

```

You can save yourself time by mapping a keybinding for winner-undo and winner-redo commands.

### Keybindings Cheatsheet

Here’s a list of all keybindings we used throughout this tutorial.

Keybinding Shortcut | What it does
---|---
C-x C-s | Saves the file
Alt-x | Opens mini prompt to enter interactive commands
C-s | Forward Search
C-u Alt-x | Run another instance of the command
C-x b | Navigates between the buffer
C-x 2 | Splits into two horizontal layouts
C-x 3 | Splits into two vertical layouts
C-x o | Move to another pane
C-x 1 | Get a full view of a particular pane

💬 _Do you love having multiple terminal sessions as well? Let me know your thoughts in the comments!_

#### Author Info

![][12]

Bhuwan Mishra is a Fullstack developer, with Python and Go as his tools of choice. He takes pride in building and securing web applications, APIs, and CI/CD pipelines, as well as tuning servers for optimal performance. He also has passion for working with Kubernetes.

--------------------------------------------------------------------------------

via: https://itsfoss.com/emacs-as-terminal-multiplexer-windows/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://apps.microsoft.com/detail/9nblggh4nns1?ocid=webpdpshare
[4]: https://itsfoss.com/content/images/2025/01/app-installer-windows.png
[5]: https://itsfoss.com/content/images/2025/01/run-shell.gif
[6]: https://itsfoss.com/content/images/2025/01/auto-completion.gif
[7]: https://itsfoss.com/content/images/2025/01/shell-buffer.gif
[8]: https://itsfoss.com/content/images/2025/01/forward-search.gif
[9]: https://itsfoss.com/content/images/2025/01/terminal-multiplexing.gif
[10]: https://itsfoss.com/content/images/2025/01/eval-buffer.gif
[11]: https://itsfoss.com/content/images/2025/01/shell-2-buffer.gif
[12]: https://itsfoss.com/content/images/2025/01/bhuban.jpg
