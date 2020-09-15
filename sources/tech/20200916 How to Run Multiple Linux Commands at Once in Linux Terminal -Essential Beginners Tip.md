[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Run Multiple Linux Commands at Once in Linux Terminal [Essential Beginners Tip])
[#]: via: (https://itsfoss.com/run-multiple-commands-linux/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Run Multiple Linux Commands at Once in Linux Terminal [Essential Beginners Tip]
======

Running two or more commands in one line can save you a good deal of time and help you become more efficient and [productive in Linux][1].

There are three ways you can run multiple commands in one line in Linux:

; | Command 1 ; Command 2 | Run command 1 first and then command 2
---|---|---
&amp;&amp; | Command 1 &amp;&amp; Command 2 | Run command 2 only if command 1 ends sucessfully
|  |

Let me show you in detail how you can chain commands in Linux.

![][2]

### Using ; to run multiple Linux commands in one line

The simplest of them all is the semicolon (;). You just combine several commands that you want to run using ; in the following fashion:

```
cmd1; cmd2; cmd3
```

Here, cmd1 will run first. Irrespective of whether cmd1 runs successfully or with error, cmd2 will run after it. And when cmd2 command finishes, cmd3 will run.

Let’s take an example you can practice easily (if you want to).

```
mkdir new_dir; cd new_dir; pwd
```

In the above command, you first create a new directory named new_dir with mkdir command. Then you switch to this newly created directory using cd command. Lastly you print your current location with pwd command.

![Running Multiple Commands Linux with ;][3]

The space after semicolon (;) is optional but it makes the chain of commands easily readable.

### Using &amp;&amp; to run multiple Linux commands

Some times you want to ensure that the in the chain of Linux commands, the **next command only runs when the previous command ends successfully**. This is where the logical AND operator &amp;&amp; comes into picture:

```
cmd1 && cmd2 && cmd3
```

If you use Ubuntu or Debian based distributions, you must have come across this command that utilizes &amp;&amp; concept:

```
sudo apt update && sudo apt upgrade
```

Here the first command (sudo apt update) first refreshes the package database cache. If there is no error, it will then upgrade all the packages that have newer versions available.

Let’s take earlier example. If the new_dir already exists, mkdir command will return error. The difference in the behavior of ; and &amp;&amp; can be see in the screenshot below:

![][4]

Did you see how commands separated by &amp;&amp; stopped when the first command resulted into error?

### Using || to run several Linux commands at once

You can use the logical OR operator (||) to run a chain of commands but the **next command only runs when the previous command ends in error**. This is opposite to what you saw with &amp;&amp;.

```
cmd1 || cmd2 || cmd3
```

If cmd1 fails, cmd2 runs. If cmd2 runs successfully, cmd3 won’t run.

![][5]

In the screenshot above, mkdir new_dir command fails because new_dir already exists. Since this command fails, the next command cd new_dir is executed successfully. And now that this command has run successfully, the next command pwd won’t run.

### Bonus Tip: Combine &amp;&amp; and || operators

You may combine the operators to run two or more Linux commands.

If you combine three commands with &amp;&amp; and ||, it will behave as the [ternary operator in C/C++][6] ( condition ? expression_true ; expression_false).

```
cmd1 && cmd2 || cmd3
```

For example, you can [check if file exists in bash][7], and print messages accordingly.

```
[ -f file.txt ] && echo "File exists" || echo "File doesn't exist"
```

Run the above command before and after creating the file.txt file to see the difference:

![][8]

Like [copy-paste in Linux terminal][9], running multiple commands at once is also one of the many [Linux command line tips for saving time][10]. Though elementary, it is an essential concept any Linux terminal user should know.

You can also use ;, &amp;&amp; and || to run multiple commands in bash scripts as well.

I hope you liked this terminal trick. Stay tuned for more Linux command tips and tools published every Tuesday under the #TerminalTuesday series.

--------------------------------------------------------------------------------

via: https://itsfoss.com/run-multiple-commands-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/productivity-tips-ubuntu/
[2]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/09/run-multiple-commands-in-linux.png?resize=800%2C450&ssl=1
[3]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/09/running-multiple-commands-linux.png?resize=755%2C277&ssl=1
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/09/multiple-linux-commands-one-line.png?resize=768%2C277&ssl=1
[5]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/09/linux-chain-commands.png?resize=768%2C277&ssl=1
[6]: https://www.w3schools.com/cpp/cpp_conditions_shorthand.asp
[7]: https://linuxhandbook.com/bash-check-if-file-exists/
[8]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/09/combine-multiple-commands-linux.png?resize=800%2C300&ssl=1
[9]: https://itsfoss.com/copy-paste-linux-terminal/
[10]: https://itsfoss.com/linux-command-tricks/
