[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Use this cheat sheet for tmux as a terminal multiplexer)
[#]: via: (https://opensource.com/article/20/7/tmux-cheat-sheet)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)

Use this cheat sheet for tmux as a terminal multiplexer
======
Get to know tmux, an application that lets you open multiple terminals
in a single desktop window.
![Windows][1]

Whether you're starting up an elaborate Raspberry Pi [homelab][2] or you're managing a building full of workstations, sometimes you need to do the same task on multiple hosts. There are many ways to automate tasks across systems. [Ansible][3], for instance, ensures all systems are in the same state, and sometimes a simple [cron][4] job will do. But sometimes you need to run commands manually. For that, you need [tmux][5], a single terminal that puts you in control of multiple command prompts.

[tmux][6] is an open source application that adds layers (or "windows," in tmux terminology) to your terminal window so that you can open more than one terminal in a single desktop window. The result is a tabbed interface (without the physical tabs), so you can flip from one open terminal to another without having to use the mouse the way you have to when switching from one tab in Firefox to another.

This might seem redundant. After all, modern terminal applications, such as GNOME Terminal and Konsole, have tabs built-in by default, and even some very old terminals, such as [rxvt][7], have the ability to add a tabbed interface. However, tmux adds in the ability to split a window into panes, with each pane containing a separate terminal, and each terminal can be logged into a separate host. You can build an array of terminals with just a few keyboard shortcuts or a rudimentary [tmuxinator][8] script.

![][9]

### Install tmux

On Linux and BSD, you can install tmux from your software repository or [ports tree][10]. On Mac, use [Homebrew][11].

For example, on RHEL or Fedora:


```
`$ sudo dnf install tmux`
```

### Start tmux

To start tmux, open a terminal and type:


```
`$ tmux`
```

When you do this, the obvious result is that tmux launches a new shell in the same window with a status bar along the bottom. There's more going on, though, and you can see it with this little experiment. First, do something in your current terminal to help you tell it apart from another empty terminal:


```
$ echo hello
hello
```

Now press **Ctrl+B** followed by **C** on your keyboard. It might look like your work has vanished, but actually, you've created what tmux calls a _window_ (which can be, admittedly, confusing because you probably also call the terminal you launched a _window_). Thanks to tmux, you actually have two windows open, both of which you can see listed in the status bar at the bottom of tmux. You can navigate between these two windows by index number. For instance, press **Ctrl+B** followed by **0** to go to the initial window:


```
$ echo hello
hello
```

Press **Ctrl+B** followed by **1** to go to the first new window you created.

You can also "walk" through your open windows using **Ctrl+B** and **N** (for Next) or **P** (for Previous).

### The tmux trigger and commands

The keyboard shortcut **Ctrl+B** is the tmux trigger. When you press it in a tmux session, it alerts tmux to "listen" for the next key or key combination that follows. All tmux shortcuts, therefore, are prefixed with **Ctrl+B**.

You can also access a tmux command line and type tmux commands by name. For example, to create a new window the hard way, you can press **Ctrl+B** followed by **:** to enter the tmux command line. Type `new-window` and press **Enter** to create a new window. This does exactly the same thing as pressing **Ctrl+B** then **C**.

### Splitting windows into panes

Once you have created more than one window in tmux, it's often useful to see them all in one window. You can split a window horizontally (meaning the split is horizontal, placing one window in a North position and another in a South position) or vertically (with windows located in West and East positions).

  * To create a horizontal split, press **Ctrl+B** followed by **"** (that's a double-quote).
  * To create a vertical split, press **Ctrl+B** followed by **%** (percent).



You can split windows that have been split, so the layout is up to you and the number of lines in your terminal.

![tmux golden ratio][12]

(Seth Kenlon, [CC BY-SA 4.0][13])

Sometimes things can get out of hand. You can adjust a terminal full of haphazardly split panes using these quick presets:

  * **Ctrl+B** **Alt+1**: Even horizontal splits
  * **Ctrl+B** **Alt+2**: Even vertical splits
  * **Ctrl+B** **Alt+3**: Horizontal span for the main pane, vertical splits for lesser panes
  * **Ctrl+B** **Alt+3**: Vertical span for the main pane, horizontal splits for lesser panes
  * **Ctrl+B** **Alt+5**: Tiled layout



### Switching between panes

To get from one pane to another, press **Ctrl+B** followed by **O** (as in _other_). The border around the pane changes color based on your position, and your terminal cursor changes to its active state. This method "walks" through panes in order of creation.

Alternatively, you can use your arrow keys to navigate to a pane according to your layout. For example, if you've got two open panes divided by a horizontal split, you can press **Ctrl+B** followed by the **Up** arrow to switch from the lower pane to the top pane. Likewise, **Ctrl+B** followed by the **Down** arrow switches from the upper pane to the lower one.

### Running a command on multiple hosts with tmux

Now that you know how to open many windows and divide them into convenient panes, you know nearly everything you need to know to run one command on multiple hosts at once. Assuming you have a layout you're happy with and each pane is connected to a separate host, you can synchronize the panes such that the input you type on your keyboard is mirrored in all panes.

To synchronize panes, access the tmux command line with **Ctrl+B** followed by **:**, and then type `setw synchronize-panes`.

Now anything you type on your keyboard appears in each pane, and each pane responds accordingly.

### Download our cheat sheet

It's relatively easy to remember **Ctrl+B** to invoke tmux features, but the keys that follow can be difficult to remember at first. All built-in tmux keyboard shortcuts are available by pressing **Ctrl+B** followed by **?** (exit the help screen with **Q**). However, the help screen can be a little overwhelming for all its options, none of which are organized by task or topic. To help you remember the basic features of tmux, as well as many advanced functions not covered in this article, we've developed a [tmux cheatsheet][14]. It's free to download, so get your copy today.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/tmux-cheat-sheet

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/windows.jpg?itok=Q9HulPrI (Windows)
[2]: https://opensource.com/article/20/6/kubernetes-raspberry-pi
[3]: https://opensource.com/article/19/2/quickstart-guide-ansible
[4]: https://opensource.com/article/17/11/how-use-cron-linux
[5]: https://opensource.com/article/17/2/quick-introduction-tmux
[6]: https://github.com/tmux/tmux
[7]: https://opensource.com/article/19/10/why-use-rxvt-terminal
[8]: https://opensource.com/article/20/1/tmux-console
[9]: https://opensource.com/sites/default/files/uploads/productivity_15-1.png
[10]: https://opensource.com/article/19/11/pkgsrc-netbsd-linux
[11]: https://opensource.com/article/20/6/homebrew-mac
[12]: https://opensource.com/sites/default/files/uploads/tmux_golden-ratio.jpg (tmux golden ratio)
[13]: https://creativecommons.org/licenses/by-sa/4.0/
[14]: https://opensource.com/downloads/tmux-cheat-sheet
