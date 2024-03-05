[#]: subject: "ps Command Examples"
[#]: via: "https://itsfoss.com/ps-command/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ps Command Examples
======

[![Warp Terminal][1]][2]

The ps command on Linux is used to monitor the active processes on Linux, and it is one of the most crucial command line utilities, especially for sysadmins and advanced users.

So in this tutorial, I will walk you through all the essentials you need to learn to use the ps command:

  * **The basic syntax and common flags of the ps command.**
  * **Practical examples of the command.**
  * **Practice questions to get better at using the ps command.**



### Here's how to use the ps command

Every command in Linux requires you to follow a specific syntax, and so does the ps command. This is why I always recommend to start with the syntax.

So here's the syntax of the ps command:

```

    ps [options]

```

Here,

  * `[options]`: it is used to fine-tune the output of the ps command as per your needs such as you can use the `-u` flag and append a username to it and display processes specific to that user.



Yes, the ps command only accepts one argument. So, it is not as confusing as some other commands.

Now, allow me to share some popular options of the ps command:

Option | Description
---|---
`-e` | Show all processes, including those not associated with a terminal.
`-f` | Show full process information, including arguments.
`-u <username` | Show processes owned by a specific user.
`-t <terminal_name>` | Show processes running on a specific terminal.
`-x` | Show processes without a controlling terminal.
`-o <PID/USER/CMD/%CPU/%MEM>` | Specify output format (PID, user, command, CPU usage, memory usage).
`--sort=<parameter>` | Sort output by different parameters.

When the ps command is used without any options, it will only show the processes attached to the current terminal:

```

    ps

```

![][3]

### Practical examples of the ps command

In this section, I will walk you through practical examples of using the ps command to give you an idea of how versatile it is.

#### 1\. Display active processes of the current user

To show every active process by the currently logged-in user, you use the `-x` flag with the ps command as shown here:

```

    ps -x

```

![][4]

Here,

  * `PID`: it indicates the process ID of the process.
  * `STAT`: shows [process state code][5] indicating the current status of the process.
  * `TTY`: shows the controlling terminal behind the process.
  * `TIME`: shows how much CPU time a process has utilized.
  * `COMMAND`: displays the executable that initiated the process.



But when you dwell more into the ps command, you will know that the `-x` flag is often paired with the `-u` flag to get detailed information about each process:

```

    ps -ux

```

![][6]

Here you will see more columns, so let me break it down for you:

  * `%CPU`: the amount of CPU time the process has used (in %).
  * `%MEM`: memory utilization by the process in %.
  * `VSZ`: the total amount of virtual memory allocated to a process.
  * `RSS`: the amount of physical memory (RAM) currently being used by a process.
  * `TIME`: time when the process was started.



#### 2\. Show the running processes of every user

To show the active processes of every user, all you have to do is use the `-a` flag with `-ux` for detailed output:

```

    ps -aux

```

![][7]

While the output looks mostly the same as the previous example, you will see processes from the other users as well thanks to the `-a` flag.

Alternatively, you can also [use the ps -ef command][8] to list all the active processes with additional information. Here's a detailed guide on the topic:

![][9]

#### 3\. List of the running processes of a specific user

To list the running processes of a specific user, use the `-U` flag and append the username to it as shown here:

```

    ps -U <username>

```

For example, here, I wanted to list active processes owned by the user `root` so I used the following command:

```

    ps -U root

```

![][10]

#### 4\. List of ongoing processes of a group

To list the processes of a group, you'd have to use the `-G` flag followed by the group name or group ID, as shown here:

```

    ps -G group_id/name

```

To demonstrate this, here, I have listed active processes owned by `sagar` group:

```

    ps -G sagar

```

![][11]

#### 5\. Find the PID of a process

Imagine yourself in a situation where you want to kill a stubborn process, but have no clue how to find its PID. Frustrating, right?

Well, the ps command can find you PID of the active processes all by using the `-C` flag as shown here:

```

    ps -C process_name

```

Here, **entering the correct name of the process is mandatory** , or it will show **an** empty output:

![][12]

Once you find it, you can use the [kill command][13] to get rid of the process:

![][14]

#### 6\. Get a process tree

Want to [show the process tree][15]? To identify the parent/child processes before you kill them?

The ps command can do that by using the `--forest` flag along with a combination of other flags.

I suggest you pair it with the `-aux` flag as shown here to list all active processes:

```

    ps -aux --forest

```

![][16]

You can also combine `-e` and `-f` options to display a similar output:

```

    ps -ef --forest

```

#### 7\. Sort the output

By default, the ps command output is sorted based on the PIDs and some users may not be happy with this behavior.

To solve this, you can use the `--sort` flag with the existing options and specify various parameters to sort the output:

```

    ps -<options> --sort=parameters

```

For example, here, I wanted to sort the output based on the CPU consumption, so I used the following:

```

    ps -aux --sort=-%cpu

```

![][17]

#### 8\. Find the process name from the PID

There are times when you have PID and want to know which process it belongs to. Sounds silly, but I've been there.

To find the process name through PID, use the `-p` flag as shown here:

```

    pid -p PID

```

![][18]

### Practice questions 📓

Here, I will be sharing questions that you can practice to get better at using the ps command:

  1. How do you find the target process from the output of the ps command? (Hint: pipe it with [the grep command][19])
  2. Sort the output based on memory consumption and only show the top 5 resource-hungry processes (Hint: pipe it with [the head command][20]).
  3. Find the PID of your default browser.
  4. List all the active processes owned by the currently logged-in users and sort them based on their start time in ascending order.



If you discover any difficulty solving these questions, you can post your queries on our [It's FOSS community][21] forum or leave a comment.

### Wrapping Up

The ps command comes with a wide range of options available and in this tutorial, I've tried covering the practical ones that you might use often.

If you are new to the Linux command-line, you should explore the basics:

![][14]

_💬 Did I miss a variation of the ps command important to you? How do you use it for your use-case? Please let me know in the comments._

--------------------------------------------------------------------------------

via: https://itsfoss.com/ps-command/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/03/Use-the-ps-command-without-any-flags.png
[4]: https://itsfoss.com/content/images/2024/03/Show-all-running-processes-1.png
[5]: https://gist.github.com/apbarrero/6338709
[6]: https://itsfoss.com/content/images/2024/03/Get-the-detailed-information-of-each-running-process-using-the-ps-commadn.png
[7]: https://itsfoss.com/content/images/2024/03/List-active-processes-of-every-user-using-the-ps-command.png
[8]: https://linuxhandbook.com/ps-ef-examples/
[9]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
[10]: https://itsfoss.com/content/images/2024/03/list-processes-owned-by-a-specific-user-using-the-ps-command.png
[11]: https://itsfoss.com/content/images/2024/03/List-processes-owned-by-a-specific-group-using-the-ps-command.png
[12]: https://itsfoss.com/content/images/2024/03/Find-PID-of-a-specific-process-using-the-ps-command.png
[13]: https://itsfoss.com/kill-command/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://linuxhandbook.com/show-process-tree/
[16]: https://itsfoss.com/content/images/2024/03/Show-process-tree-using-the-ps-command.png
[17]: https://itsfoss.com/content/images/2024/03/Find-the-most-CPU-hungry-processes-usign-the-ps-commadn.png
[18]: https://itsfoss.com/content/images/2024/03/find-process-name-through-PID-using-the-ps-command.png
[19]: https://linuxhandbook.com/grep-command-examples/
[20]: https://linuxhandbook.com/head-command/
[21]: https://itsfoss.com/ps-command/itsfoss.community/
