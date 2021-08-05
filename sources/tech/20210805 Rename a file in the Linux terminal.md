[#]: subject: "Rename a file in the Linux terminal"
[#]: via: "https://opensource.com/article/21/8/rename-file-linux-terminal"
[#]: author: "Seth Kenlon https://opensource.com/users/seth"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Rename a file in the Linux terminal
======
To rename a file in the terminal, move the file with mv from itself to
itself with a new name. Here's an example.
![rename files][1]

To rename a file on a computer with a graphical interface, you open a window, find the file you want to rename, click on its name (or right-click and select the option to rename), and then enter a new name.

To rename a file in the terminal, you actually [move the file][2] with **mv**, but you move the file from itself to itself with a new name.

This example renames **example.txt** to **file.txt**:


```
`$ mv example.txt file.txt`
```

Because they both use the same command, you can combine rename with a move. For instance, when moving **example.txt** to **Documents**, you could also rename it:


```
`$ mv example.txt ~/Documents/file.txt`
```

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/8/rename-file-linux-terminal

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/ch01s06.svg_.png?itok=a6cyO7Db (rename files)
[2]: https://opensource.com/article/21/7/terminal-basics-moving-files-linux-terminal
