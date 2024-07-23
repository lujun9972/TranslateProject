[#]: subject: "Effectively Use History Command in Linux"
[#]: via: "https://itsfoss.com/history-command/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Effectively Use History Command in Linux
======

[![Warp Terminal][1]][2]

As you start using the terminal more, you'll be continually running a variety of commands.

And then you'll find yourself in the situation where you want to know which commands you run earlier or run a particular command again.

This is why history command exists in Linux. It's a shell built-in and extremely useful for terminal dwellers.

Since it is a shell built-in, it may behave slightly differently depending on the shell you are using )bash, zsh, ksh etc) and how it was configured. Still, at the core, the basics remain the same.

In this tutorial, I'll go over the basic usage of the history command and then show some useful tips you should enjoy learning about.

### Check history of commands

You can press the up key repeatedly to go through the history of commands. But it only shows one command at a time. The `history` command lets you see all the previously run commands.

Open a terminal and run the following command:

```

    history

```

It showed commands that you have run in the past. For me, it shows the following:

![][3]

The history is usually stored in the `~/.bash_history` directory. ~ denotes the home directory, in case you didn't know.

If you are ever in doubt, you can check the `HISTFILE` variable to get the history file location of your shell.

```

    echo $HISTFILE

```

**How many commands are stored in the history**? That depends on the `HISTFILESIZE` variable. In Debian and Ubuntu, it is usually set to 2000.

```

    echo $HISTFILESIZE

```

💡

Too many lines in the history cluttering your screen? You can choose to display only the last N lines of the history with `history N`

### Running commands from history

Did you notice that the history command shows a number in front of the command entries? You can use this number to run a command from the history. For example to run the Nth entry in the command history, use:

```

    !N

```

Here's an actual example where I run the commands at 152nd entry in the history.

![][4]

### Getting more from the last run command

This is not really a direct example of the history command but it deals with the history of commands and I wanted to discuss it.

You can use the `!!` to get the last run command. This is extremely useful in the case when you forget to run a command with sudo. Instead of retyping the entire command, you could just use:

```

    sudo !!

```

It will show the full command that is being run. Here's an example:

![][5]

If you made a typo anywhere in the previous command, you can fix it in this fashion:

```

    ^foo^bar

```

This will replace the first `foo` with `bar` in the last run command.

Here's a practical example:

![][6]

💡

Another tip, which is more of a terminal shortcut and may not work everywhere but still very handy. To use the last argument of the last ran command, use the `Alt+.` keys. Viewing a deeply nested directory with ls command and would like to switch into it? Instead of typing everything, just use cd and press Alt+.

### Search through the command history

You can press up (and down) key to cycle through the command history and press enter when your desired command comes up. This works fine for the last few commands but you should not keep on pressing the up key 100 times to get the command from the history.

![][7]

One way to search in the history would be to filter it with grep command.

Let's say you want to look for the tail command you ran earlier:

```

    history | grep tail

```

**Another way is to use the reverse search feature**. Press Ctrl+R and you'll find yourself in the reverse search interface. Start typing for your search term and it starts showing matching commands from the history.

![][8]

Of course, there can be multiple matches with the same search string. Press Ctrl+R repeatedly to cycle through all the matches. Only a single match is shown at a time.

If you find the command you were looking for, press the right arrow key to exit the reverse search and start using the command.

Press Ctrl+C to come out of the reverse search without getting any commands to use.

### Delete command from history

To delete a command from the history, you can use its entry number in this way:

```

    history -d N

```

In the example below, I delete the long flatpak add command listed at number 181:

![][9]

You can also provide a range of lines to delete:

```

    history -d 160-180

```

💡

`history -c` will clear the entire bash history.

### Exclude some commands from the history

If you do not want a command to be recorded in the history, just put a space before it and run:

In the example below, I ran a random command that doesn't even exist but I out space before it. It threw an error, obviously, but it is not recorded in the history.

![][10]

Did you notice that the second `history 7` was also not recorded in the history? That's because of the `HISTCONTROL` environment variable. It can have the following values:

  * ignorespace: Run a command by putting a space before it and it won't be included in the history.
  * ignoredups: If there are two or more identical commands ran consecutively, only the first one gets recorded.
  * ignoreboth: Use both of the above two mentioned features.



💡

You can also set the HISTIGNORE variable in the bashrc file and exclude some of the common commands from history. Use it like `HISTIGNORE='pwd:echo *:clear'`

### Bonus: Why do some commands are not recorded in history?

Have you ever noticed that not all the commands you run are recorded in history? Are you running multiple terminal sessions? That could be the culprit.

Here's the thing. The history file `~/.bash_history` is not modified until you close the terminal session.

If you check the history command and the content of ~/.bash_history, you'll see that the commands you ran in the present session are not in the ~/.bash_history file.

If you have ever opened multiple terminals and tabs, you might have realized that recently run commands in one tab is not available in the other tab when you press the arrow key. That's because command history for the current session is not saved to the ~/.bash_history file yet.

Now, when you start closing the terminal sessions, only the history from the last closed session is recorded. Command history from other sessions is lost. That's the default behavior.

You may change this by using the `export PROMPT_COMMAND='history -a'` (append mode) in your bashrc file. What it does is that before showing the prompt (that $ sign on the terminal), it adds the just run command to the history file.

Some people use `export PROMPT_COMMAND='history -a; history -r'` which not records the history from each session, it also fetches command history from other terminal sessions so that you can use them with the up arrow keys. It may sound good, but it quickly gets messy. Entirely up to you if you want that.

### Conclusion

Even if don't use the history command in the sense of typing the history command, I utilize the reverse search and the up arrow key for history search all the time. But still, it is good to know the various features the history mechanism offers.

I hope you learned something new and interesting about the history command in this tutorial.

--------------------------------------------------------------------------------

via: https://itsfoss.com/history-command/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/07/history-command-examples.png
[4]: https://itsfoss.com/content/images/2024/07/run-command-from-history.png
[5]: https://itsfoss.com/content/images/2024/07/history-trick-with-sudo.png
[6]: https://itsfoss.com/content/images/2024/07/fix-typo--in-command-history.png
[7]: https://itsfoss.com/content/images/2024/07/linux-history-command-meme.png
[8]: https://itsfoss.com/content/images/2024/07/reverse-search-command-history.png
[9]: https://itsfoss.com/content/images/2024/07/delete-command-history.png
[10]: https://itsfoss.com/content/images/2024/07/exclude-command-from-history.png
