[#]: subject: "Kill Command Examples"
[#]: via: "https://itsfoss.com/kill-command/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Kill Command Examples
======

[![Warp Terminal][1]][2]

Found a stubborn background process eating up system resources?

You can kill it using the **kill command** 😉

But how do you use the kill command? Well, in this tutorial, I will walk you through the essentials needed to learn how to use the kill command:

  * **The basic syntax and popular flags of the kill command**
  * **Practical examples of the kill command**
  * **Practice questions to get better at using the kill command**



### Here's How to use the Kill command

To use the kill command to its full potential, it is important to know its syntax, so here's a basic syntax of the kill command:

```

    kill [options] <PID>

```

Here,

  * `[options]`: it is used to fine-tune the behavior of the command as per your needs, such as you can use the `-s` option to specify a kill signal.
  * `<PID>`: here's where you specify the process ID of a target process to kill.



Now, let's take a look at the list of the options available to you:

Option | Description
---|---
`-s ` | Specify what kill signal to send.
`-l ` | Shows the name of the signal through the signal number.
`-L` | List all the available signals.
`q ` | Sends the signal using sigqueue(3) instead of kill(2), allowing an additional integer value to be sent along with the signal.

The key option here is the `-s` flag, as you will mostly be using the kill command with specific kill signals in mind.

So here's a list of common signals used with the kill command:

**Signal Number** | **Signal Name** | **Description**
---|---|---
`1` | SIGHUP | Re-read configuration (like reloading web server settings).
`2` | SIGINT | Interrupt the process, similar to pressing `Ctrl+C`.
`3` | SIGQUIT | Quit and create a core dump (for debugging crashes).
`9` | SIGKILL | Forcefully terminate immediately (use with caution!).
`15` | SIGTERM | Politely request termination, allowing for cleanup (default).

**If you don't specify any signal number, it will use`SIGTERM` by default.**

Now, let's take a look at some practical examples of the kill command.

### Practical examples of the kill command

In this section, I walk you through practical examples of the command, so you can have a better idea of how to use the kill command on Linux:

#### 1\. List available signals

To list available signals, all you have to do is use the `-L` flag with the kill command, as shown here:

```

    kill -L

```

![][3]

As you can see, the above response repeats the termination signals. So how do you get the list of every signal available without repetition?

Easy, you can use the standalone version of the kill command by executing in the following manner:

```

    /usr/bin/kill -L

```

![][4]

#### 2\. Kill a process using the kill command

To kill a process, you require a PID (Process ID) to specify the target process. To [find the PID of a process,][5] you can use the pidof command as shown here:

```

    pidof <process_name>

```

For example, if I want to find the PID of the Firefox browser, then I use the following:

```

    pidof firefox-bin

```

![][6]

Once you have a PID, you can use the following command:

```

    kill <PID>

```

As I mentioned earlier, if you don't pass any termination signal, it will use `SIGTERM`, enough to kill most processes.

If the process is super stubborn (and has numerous child processes associated with it) and does not go away by the default signal, then you can use the `SIGKILL`.

🚧

The `SIGKILL` signal kills the child processes as well so use it with caution ⚠️.

Here's how you can use `SIGKILL` to kill a stubborn process:

```

    kill -9 <PID>

```

For example, the Spotify client was unresponsive and wasn't working as expected, so here's how I used SIGKILL to kill Spotify:

```

    kill -9 13234

```

Here, the `13234` is the PID of the Spotify desktop.

If you're curious to learn the [difference between SIGTERM (default) and SIGKILL][7] then you can refer to our detailed guide on that matter:

![][8]

#### 3\. Kill multiple processes at once

To kill multiple processes, all you have to do is append multiple PIDs to the kill command separated by spaces:

```

    kill [options] PID1 PID2 PID3 PIDN

```

For example, here, I used the PID of Firefox and Spotify to kill both of them at once:

```

    kill 10793 9758

```

#### 4\. Find the name of the signal through the number

Typically, you will stumble upon a number instead of the name of the kill signal, and you might want to know what signal was used there.

For that purpose, you can use the `-l` flag appending the number of the signal as shown here:

```

    kill -l <Signal_number>

```

For example, if I want to know what is the name of the termination signal 9, then I will use the following:

```

    kill -l 9

```

![][9]

If you notice the above output, then you realize that it only printed the `KILL` instead of `SIGKILL`.

Why do you ask? Well, it won't add `SIG` before the name of any termination signal.

**Suggested Read 📖**

![][10]

### Practice questions 🗒️

You must practice the commands to get better at them, and quickly use them when needed in day to day life.

So here I'll be sharing some practice questions for the kill command:

  1. Find the PID of your default browser and then kill it using the SIGKILL.
  2. How can you hold the process instead of killing it?
  3. What is an interactive way of sending kill signals (Hint: you can [use htop][11])
  4. What is a zombie process and how to kill it? (Hint: [guide to zombie process][12])



If you discover any difficulties solving the above problems, reach out to us through the comments or post your query in [our community forum.][13]

### Explore How You Can Use Different Kill Signals

If you are curious to learn the meaning of different kill signals, refer to our detailed guide on [using different termination signals on Linux][14]:

![][8]

Moreover, if you are new to Linux, I suggest you to also go through our [command tutorial for beginners][15].

![][10]

_💬 How often do you find yourself using the kill command? Or do you prefer the GUI?_

--------------------------------------------------------------------------------

via: https://itsfoss.com/kill-command/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/02/List-available-options-with-the-kill-command-1.png
[4]: https://itsfoss.com/content/images/2024/02/List-available-kill-signals.png
[5]: https://linuxhandbook.com/find-process-id/
[6]: https://itsfoss.com/content/images/2024/02/Find-the-PID-of-a-process.png
[7]: https://linuxhandbook.com/sigterm-vs-sigkill/
[8]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
[9]: https://itsfoss.com/content/images/2024/02/Find-the-name-of-the-termination-signal-with-the-kill-command.png
[10]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[11]: https://itsfoss.com/use-htop/
[12]: https://itsfoss.com/kill-zombie-process-linux/
[13]: https://itsfoss.community/
[14]: https://linuxhandbook.com/termination-signals/
[15]: https://itsfoss.com/tag/terminal-basics/
