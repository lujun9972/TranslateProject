[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to use tmux to create a multi-pane Linux terminal window)
[#]: via: (https://www.networkworld.com/article/3545370/how-to-use-tmux-to-create-a-multi-pane-linux-terminal-window.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

How to use tmux to create a multi-pane Linux terminal window
======

[Pedro Figueras][1] [(CC0)][2]

The **tmux** tool is one of a number of Linux terminal window splitters that allow you to run commands in adjacent (up/down, right/left or both) panes so that you can easily use the output in one pane to help with work you’re doing in another. You can even disconnect a multi-pane **tmux** session and reattach to it when you need it again.

What's more, processes running within **tmux** will continue running even when you detach, making **tmux** an excellent tool to use when you’re not sure your connection to a remote server is solid and don't want to be dropped in the middle of an important task.

The “mux” in the name **tmux** stands for multiplexer. This term generally refers to sharing digital connection or an information stream. So, “tmux” stands for “terminal multiplexer”. The tool is similar to **terminator** and **konsole**. However, **tmux** is also available on some OSes other than Linux including MacOS.

The primary drawback of **tmux** is that you have to learn some mildly awkward command sequences to use it. However, if you can adjust to just about everything you need to do starting with **Ctrl-b** (hold the **Ctrl** key and press **b**), you’re off to a good start.

Starting **tmux** is easy. Just type “tmux” in a terminal window. If you plan to detach and return to a session later, it's a good idea to give the session a meaningful name.

### To start a session type:**

**

```
$ tmux
```

### To start a named session type:**

**

```
$ tmux new -s perf
```

Once **tmux** is started, a bar along the bottom of the **tmux** session will display the session name (if used), server name, and current (updating) time and date.

```
[perf] 0:bash*                         "dragonfly" 15:45 25-May-20
```

Opening new panes is quite easy with commands likes these below. You just have to remember that **%** means "to the right" and **"** means "below":

```
Ctrl-b %     open a pane to the right of the current pane
Ctrl-b “     open a pane below the current pane
```

Moving from pane to pane then requires the use of arrow keys. If you want to move to a pane to the right, use **Ctrl-b** followed by pressing the right arrow key and, if you want to move down a pane, use **Ctrl-b** following by the down arrow key. In other words, use whichever arrow key points in the direction you want to move – right, left, up or down.

To close a pane, first ensure that you're positioned in it. Then type "exit" or **Ctrl-d**. Note that there is no need for **Ctrl-b** in this step. Once you type "exit" or Ctrl-d in the last remaining pane, **tmux** will close.

You can also exit **tmux** by pressing **:** to go to the bottom bar of the **tmux** window. Then type **kill-session**. Note that the session will be gone and will not be reattachable.

If you want to detach a session instead of simply closing it, use **Ctrl-b d** (d for "detach"). You can detach with all of the panes still open.

To list detached sessions, use the command **tmux ls** on the command line or within a **tmux** session. Sessions without given names will be called 0, 1, 2 etc., in the order in which they were created. Only detached sessions will show up in the output of the **tmux ls** command.

You can rename a session with a command like this:

```
$ tmux rename-session -t 0 acct-mgt
$ tmux ls
1: 1 windows (created Sat May 23 16:10:26 2020)
acct-mgt: 1 windows (created Mon May 25 16:09:52 2020) (attached)
```

You can reattach to a session using a command like one of these that includes the session name you assigned or was automatically provided:

**$ tmux attach -t acct-mgt**

or

**$ tmux attach -t 0**.

Note that, if you reattach a session and then exit instead of detaching, it will no longer be available for reattaching.

### Recipe for a 3-pane tmux session

Want a recipe for setting up a **tmux** window like this that you can reuse any time you want?

```
+-----------------------------------------+
|                                         |
|                                         |
|                                         |
|                                         |
+--------------------+--------------------+
|                    |                    |
|                    |                    |
|                    |                    |
|                    |                    |
+-----------------------------------------+
```

Here goes. First start your session and give it a name. In this example, we're calling the session  "tmux3" because it will have three panes.

```
$ tmux new -s tmux3
```

After it opens, type these character sequences:

```
Ctrl-b “               <== open a pane below
Ctrl-b %                <== open a pane to right
Ctrl-b d                <== detach the session
```

Next, list your saved session to make sure you did everything right:

```
$ tmux ls
tmux3: 1 windows (created Mon May 25 13:46:14 2020)
```

Reattach to your session:

```
$ tmux attach -t tmux3
```

Your session will start each time with your cursor in whatever pane it was sitting in when you detached. On that note, don't forget to detach each time you use it by typing **Ctrl-b d**.

You can even create an alias to make reattaching to your session that much easier.. In the commands below, we create the alias and save it to our .bashrc file to ensure it's available each time we log in:

```
alias tmux3="tmux attach -t tmux3"; echo 'alias tmux3="tmux attach -t tmux3"' >> ~/.bashrc
```

Got that? You will have to detach every time you use the **tmux** session by typing **Ctrl-b d**. Otherwise, the session will no longer be saved. And don’t forget that the session will always pick up where you left off, displaying the output of any commands that are still running.

For example, if you left **top** running when you last used the session, it will still be running after you have detached and adding output to the pane in which it's active. If you kill that **top** process outside of **tmux** (which you can), it will no longer be running when you reattach your session. After all, **tmux** is not a separate system, just a way of splitting your terminal connection. Detaching doesn't disrupt the running processes, whick is one of the key benefits of using **tmux** in the first place.

There are lots of other options available for use with **tmux**. We've only touched on the basics in this post. Refer to the **tmux** man page for more information, but be aware that **C-b** is sometimes used to represent **Ctrl-b**.

Join the Network World communities on [Facebook][3] and [LinkedIn][4] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3545370/how-to-use-tmux-to-create-a-multi-pane-linux-terminal-window.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://www.pexels.com/photo/white-framed-glass-window-626158/
[2]: https://creativecommons.org/publicdomain/zero/1.0/
[3]: https://www.facebook.com/NetworkWorld/
[4]: https://www.linkedin.com/company/network-world
