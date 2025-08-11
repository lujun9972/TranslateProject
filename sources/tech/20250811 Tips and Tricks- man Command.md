[#]: subject: "Tips and Tricks: man Command"
[#]: via: "https://fedoramagazine.org/tips-and-tricks-man-command/"
[#]: author: "abdulrahman mubarak https://fedoramagazine.org/author/abdulrahman-mubarak/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Tips and Tricks: man Command
======

![][1]

Photo by [Viktor Talashuk][2] on [Unsplash][3] [cropped]

The **man** command, is short for **manual**. It provides access to the various up-to-date on-board documentation pages. This helps users utilize the Linux/Unix operating systems in a better manner.

### What is man ?

The _man_ command is a manual pager which provides the user with documentation about specific functions, system calls, and commands. The _man_ command uses the _less_ pager by default. (See _man less_ for more information.)

Note that a **man** page is likely to contain better up-to-date information compared to what can be found on the internet. It is wise to compare the _man_ page usage and options with that found on the web.

### How to use man ?

To use the _man_ command effectively we have to know the **manual pages system**. The manual pages are distributed in 8 sections. Each provides documentation on particular topics.

#### What are the manual page sections ?

  1. Programs, shell commands and daemons.
  2. System calls.
  3. Library calls.
  4. Special files, drivers, and hardware.
  5. Configuration files.
  6. Games.
  7. Miscellaneous commands.
  8. System administration commands and daemons.



### Examples

To get the printf library function documentation (section 3):

```

    # man 3 printf

```

To get the printf shell builtin documentation (section 1):

```

    # man 1 printf

```

You can learn more about the man command and its options:

```

    # man man

```

### How to manage the index caches database

To update the existing database, or to create it, use the **-c** or **–create** flag with the _mandb_ command:

```

    # mandb --create

```

To do a correctness check on the documentation database use the **-t** or **–test** flag:

```

    # mandb --test

```

### How to export manual pages

To export a man page, use the **-t** flag with the _man_ command:

```

    man -t 5 dnf.conf > manual.ps

```

This will create a PostScript file with the contents of the dnf.conf man page from section 5.

Alternatively, if you want to output a PDF file, use something like this instead:

```

    man -Tpdf 5 dnf.conf > dnf.conf.pdf

```

You will need the groff-perl package installed for this command to work.

### Summary

The need to get information about **commands** , **daemon** s, **shell builtins** , etc. to make them do what they are intended to do correctly, motivates us to use the system manual to learn not everything but the required knowledge to reach our goal.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/tips-and-tricks-man-command/

作者：[abdulrahman mubarak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/abdulrahman-mubarak/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/08/man_tips_tricks-816x345.jpg
[2]: https://unsplash.com/@viktortalashuk?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/assorted-files-05HLFQu8bFw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
