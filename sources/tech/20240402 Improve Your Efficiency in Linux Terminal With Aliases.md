[#]: subject: "Improve Your Efficiency in Linux Terminal With Aliases"
[#]: via: "https://itsfoss.com/linux-alias/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Improve Your Efficiency in Linux Terminal With Aliases
======

[![Warp Terminal][1]][2]

You can make yourself more productive in the Linux terminal by creating aliases of the most frequently used command combinations.

For example, to update my Ubuntu system, instead of using:

```

    sudo apt update && sudo apt upgrade -y

```

I just use `upd` and it works the same. How? Because I set an alias `upd` to the above update commands combination.

```

    alias upd="sudo apt update && sudo apt upgrade -y"

```

Seems amazing, right? That's because it is. Let's discuss aliases in detail.

### What is the alias command in Linux?

The alias command allows you to create "custom commands" from existing Linux commands. It is primarily used for creating a short form of a long Linux command combination. So instead of typing `find / -type f -name *.txt`, you create an alias like `ftext` and just use this smaller 'command'.

This is particularly helpful when you have to regularly use some command combinations. Instead of manually typing them from memory and knowledge or copying it from your script collection, you can create an alias and quickly use them.

### How to create an alias in Linux?

To create an alias for the currently logged-in session, you can use the alias command in the following manner:

```

    alias short_name="your custom command here"

```

The quotes become mandatory if your command has more than one 'word'. I mean you can alias `gg=grep` but you cannot do `gg=grep --color=auto`. It has to be `gg='grep --color=auto`.

You can use either [single or double quotes][3] depending on your need.

💡

There should not be any space around `=` while using the alias command.

I'll take a simple example here.

Let's say you are someone who uses `ls -la` frequently. In that case, you can create an alias for the ls command which will execute the ls -la when you only type `ls`.

Yes, you can replace an existing command with an alias of the same name.

```

    alias ls="ls -la"

```

![][4]

As you can see when I executed `ls`, it automatically executed `ls -la`.

This is only temporary. If you log out of the terminal session, your alias will not work the next time.

#### Make alias permanent

If you want to create a permanent alias, then, you'd have to make changes in your `.bashrc` file.

So first, open the `.bashrc` file for editing:

```

    nano ~/.bashrc

```

[Go to the end of the file in the nano][5] text editor using `Alt + /` and add the lines as shown:

```

    alias short_command='custom command here'

```

For example, here, I created an alias for `ls -lah` which will be executed when I use `ls`:

```

    alias ls='ls -lah'

```

![][6]

Once done, [save changes and exit from the nano][7] text editor.

To take effect from the changes, source the file:

```

    source ~/.bashrc

```

That's it!

### How to list all the aliases?

To list existing alias, you can simply execute the following command:

```

    alias

```

![][8]

As you can see, there's already one alias set for `--color=auto` which is the reason why the ls command uses different colors to indicate files, directories, and symlinks by default.

### Do you alias?

Trust me, aliases are super handy, specially if you have to work regularly in the terminal. I know a few sysadmins keep a long list of aliases that saves them the trouble of finding and typing complicated commands.

How about you? Do you use aliases on your Linux system? Which ones are you are proud of? Share them in the comments if they are not too sensitive?

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-alias/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://linuxhandbook.com/quotes-in-bash/
[4]: https://itsfoss.com/content/images/2023/07/create-temporary-alias-for-the-ls-command.png
[5]: https://linuxhandbook.com/beginning-end-file-nano/
[6]: https://itsfoss.com/content/images/2023/07/create-Permanent-alias-for-the-ls-command-in-Linux.png
[7]: https://linuxhandbook.com/nano-save-exit/
[8]: https://itsfoss.com/content/images/2023/07/list-existing-alias-in-Linux.png
