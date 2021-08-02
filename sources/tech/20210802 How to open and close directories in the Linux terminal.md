[#]: subject: (How to open and close directories in the Linux terminal)
[#]: via: (https://opensource.com/article/21/8/linux-change-directories)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

How to open and close directories in the Linux terminal
======
Learn how to use the cd command to change directories with this Linux
tutorial.
![Open a directory][1]

To open a directory on a computer with a graphical interface, you double-click on a folder. It opens, and you are now "in" that folder.

To open a directory in a terminal, you use the **cd** command to change your current directory. This essentially opens that folder and places you in it.


```
$ pwd
/home/tux

$ ls
example.txt
Documents
Downloads
Music
Pictures
Templates
Videos

$ cd Documents
$ pwd
/home/tux/Documents
```

### Close a folder

To close a directory on a computer with a graphical interface, you close the window representing that directory.

You don't have to close directories in a terminal, but you can always navigate away from a location you've made your current directory. The **cd** command, issued alone with no arguments, takes you back home.


```
bash$ cd
bash$ pwd
/home/tux
```

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/8/linux-change-directories

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/ch01s02.svg_.png?itok=wXS14qIi (Open a directory)
