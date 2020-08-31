[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Enhancing the Linux command line with aliases)
[#]: via: (https://www.networkworld.com/article/3573074/enhancing-the-linux-command-line-with-aliases.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

Enhancing the Linux command line with aliases
======
Using bash aliases in Linux can save time and having to remember complex commands - and it can be fun, too.
electravk / Getty Images

Want to get work done a little faster, spend less time remembering commands and maybe even show your coworkers how clever you are? Easy. Set up several dozen bash aliases.

Your days will get easier and a tad less stressful. You might even have some fun. In this post, we'll look at the various types of aliases that you can set up, and what you need to know to manage them.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

### Why use aliases?

Using aliases helps you to avoid having to type a lot of command details, especially those that are hard to remember or require a lengthy string of options that might have to be entered in some particular order before they'll spit out just the output that you're waiting to see.

### Types of aliases

Some aliases will be complete commands. Others will include everything in a command up to whatever filename, username or other argument that you will be supplying when you use them. Some aliases are simple abbreviations – like using "c" instead of "clear". Others are so complex that, unless you consult a man page, you won't even remember what each of the letters in the command it runs represents.

### The alias syntax

The syntax for creating an alias is easy. You type the word "alias", followed by the name you want to give the alias, stick in an **=** sign and then add the command you want it to run – generally enclosed in single or double quotes. Single word commands like "alias c=clear" don't require quotes.

```
$ alias aliasname='some command that you use'
$ alias haha="echo stop laughing at me"
```

The only time you need to be a little more careful is when you're using single or double quotes within your aliases. In this case, you'll have to take a little extra care to make sure the extra quotes don't confuse the parsing. An unmatched quote will make **bash** think you're not finished.

```
$ alias fixme='echo this isn't what I meant'
>     <== continuation prompt from bash
```

If the command you want the alias to run requires quotes, you can "escape" them using a backslash. This tells **bash** not to interpret them as delimiters, but simply as additional characters. Here are some examples:

```
$ alias now="echo It\'s now `date +%T`"
$ now
It's now 09:41:20
$ alias warning='echo Type \"bye\" before you log off tonight'
$ warning
Type "bye" before you log off tonight
```

### Aliases with variables

It's quite straightforward to incorporate variables into aliases.

```
$ alias hi='echo Hello there, $USER'
$ hi
Hello there, shs
$ alias wmi='echo I am in $PWD'
$ wmi
I am in /home/shs
$ cd /tmp
$ wmi
I am in /tmp
```

Of course, typing "wmi" is no more convenient than typing "pwd". Still  you might sometimes want to set up an alias just to assign a different name to a command.

### Conditional aliases

You can include some logic in aliases, but aliases generally include only a single command even if the command is an **if** command as with this example. Get any more complicated than this and you're probably better off writing a script.

```
$ alias warn='if [ "$USER" != "shs" ]; then cat riot-act; fi'
$ warn
BEHAVE YOURSELF! You have been warned.
```

### Aliases with arguments

It is possible to create aliases that can handle a string of arguments that you provide to them on the command line when you use them. Here are a couple examples:

```
$ alias show_args='f(){ echo You entered "$@" in that order; unset -f f; }; f'
$ show_args Linux is fun
You entered Linux is fun in that order
$ alias rev_args='f(){ if [ $# -ge 3 ]; then echo "$3 $2 $1"; fi; unset -f f; }; f'
$ rev_args Linux is fun
fun is Linux
```

Note that in these examples, we are setting up a couple aliases that include a function. The final "f" in each alias is the call to the alias after it is defined in the portion that begins with "f()".

### Saving your aliases

Once you're pleased with an alias, be sure to save it in your .bashrc file so it'll be available whenever you log in want to use it. You should probably add aliases by editing the .bashrc file, not by redirecting the output to it or you'll lose the required quotes. On the other hand, you can add escape characters to the alias while appending it so this doesn't happen like this:

```
$ echo alias wmi=\'echo I am in $PWD\' >> .bashrc
```

If you add aliases to your .bashrc file and then want to make them active right away, you can "source" your .bashrc file using a command like this:

```
$ . ~/.bashrc
```

This command will read your .bashrc file and make all of its aliases active. It could affect other settings, but only if any have been changed since your login.

### Disabling aliases

To disable an alias, you can use the **unalias** command (maybe to try a different version?). Just don't forget that if you've saved the alias, the copy in your .bashrc file will not be affected by the **unalias** command.

```
$ unalias wmi
```

### Aliases and shells

Many shells support aliases (not just bash), but some use their own startup files (i.e., not .bashrc). For example, **zsh** uses a .zshenv file. Make sure you add your aliases to the proper startup file.

Whether you borrow, share or simply create your own aliases for your personal use, you will probably find that they serve important purposes by capturing some of the more tedious or tricky commands that you use.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3573074/enhancing-the-linux-command-line-with-aliases.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/newsletters/signup.html
[2]: https://www.facebook.com/NetworkWorld/
[3]: https://www.linkedin.com/company/network-world
