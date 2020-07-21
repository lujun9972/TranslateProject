[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Become a root User In Linux)
[#]: via: (https://www.2daygeek.com/how-to-become-a-root-user-super-user-in-linux/)
[#]: author: (Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/)

How to Become a root User In Linux
======

The root user is a privileged user on Linux, which is similar to an administrator on Windows.

It performs all kinds of administrative operations, so do not give anyone root access because they may damage your system if they are not familiar with Linux.

Disabling root is a safe approach, UBUNTU basically does this and forces sudo instead of root access.

To deal with this situation you can allow a normal user to perform administrative tasks with the sudo command.

If you don’t know how to configure sudo access on Linux, refer the following article.

  * **[How to configure sudo access on Linux][1]**



You can accurately track user activity when you enable sudo access for a user. It records everything in the message log (**/var/log/message**).

If you do not know the **[effective ways to read log files in Linux][2]**, read this article.

The below articles will help you learn more about sudo.

  * **[How to Allow a Normal User or Group to Run Commands as root in Linux][3]**
  * **[How to Allow a Normal User to Run Commands as root in a Specific Directory in Linux][4]**



### 1) How to Become a root User In Linux Using su Command

The su (short for substitute or switch user) command allows you to run commands with the privileges of another user, by default the root user.

su is the simplest way to switch to the root account in Linux but you must have root password to use su command on Linux.

This will allow you to retrieve the root user home directory and their shell.

```
$ sudo su -
Password:
[email protected]:/root# pwd
/root
```

When you are logged in as root, the command prompt ends with **#** instead of **$**.

You may be wondering why I should use “-” when using the su command, and what’s the difference.

  * **su – :** When you use “su -” it sets the target user environment including HOME, SHELL, USER, LOGNAME and PATH.
  * **su :** It preserves the current user environment.



### 2) How to Become a root User On Linux Using the “sudo -i” Command

The sudo (short for super user do) command allows you to temporarily run other commands as root. This is the best way to execute root commands because it records everything you do with the sudo command.

The user does not need to know the root password to become root. Instead, users will enter their own password to gain temporary root access.

```
$ sudo -i
[email protected]:/root# pwd
/root
```

This will give you an interactive root shell and you fall in the the root home directory (/root).

Alternatively, you can run the command directly from your session by adding sudo before each command you run.

```
$ sudo ip a
```

### 3) How to Become a root User on Linux Using the “sudo -s” Command

This gives you root access, but protects your current environment, including shell-specific settings and the home directory.

```
$ sudo -s
[email protected]:/home/magesh# pwd
/home/magesh
```

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/how-to-become-a-root-user-super-user-in-linux/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/how-to-configure-sudo-access-in-linux/
[2]: https://www.2daygeek.com/efficient-ways-to-read-the-log-files-in-linux/
[3]: https://www.2daygeek.com/allow-permit-normal-user-group-to-run-certain-particular-commands-as-root-with-sudo/
[4]: https://www.2daygeek.com/how-to-allow-a-normal-user-to-run-commands-as-root-in-specific-directory-in-linux/
