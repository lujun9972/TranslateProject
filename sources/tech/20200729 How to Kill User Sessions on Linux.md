[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Kill User Sessions on Linux)
[#]: via: (https://www.2daygeek.com/how-to-kill-user-sessions-on-linux/)
[#]: author: (Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/)

How to Kill User Sessions on Linux
======

Sometimes you may need to kill multiple user sessions on Linux.

For example, you have to run a month job, for which all users have to be logged out of the system.

Another example is that you watch a lot of ssh sessions on your system and want to kill everyone.

If so, how to do it?

There are a few ways you can achieve this.

I will show you one by one and you can pick the one that suits your needs.

If you want to **[kill inactive or idle ssh sessions on Linux][1]**, refer the following article.

You can see the active ssh sessions by running the w command on Linux.

```
[[email protected] ~]# w
00:34:21 up 48 days, 23:38, 4 users, load average: 0.79, 0.58, 0.56
USER TTY FROM [email protected] IDLE JCPU PCPU WHAT
magesh pts/0 192.168.1.101 19:47 4:45m 0.04s 0.00s sh /opt/scripts/disk-usage.sh
renush pts/1 192.168.1.102 20:35 3:54m 2:23 0.00s sh bash
thanis pts/2 192.168.1.103 00:27 5.00s 0.08s 0.04s ssh
root pts/4 192.168.1.104 00:34 1.00s 0.02s 0.01s w
```

### 1) How to Kill User Sessions on Linux Using pkill Command

You can directly kill a specific user ssh session using the tty session number. You can see the tty session number from the W command output.

In my case, I’m going to kill the “magi” user session, this user is connected to the server with pts/5, so the command will be as follows.

```
# pkill -9 -t pts/2
```

Do you want to understand the difference between tty and pts? Here is the details.

  * **TTY:** tty stands for Teletypewriter. This is directly connected to the system as a keyboard/mouse or a serial connection to the device (for instance, the console on your system).
  * **PTS:** pts Stands for the pseudo terminal slave. It is a terminal device, which is emulated by another program (for instance, ssh session to your system).



### 2) How To Kill User Sessions in Linux Using Killall Command

You can kill the user session as follows with the help of the killall command. In my case, I’m killing the “magesh” user session with the help of the “-u” switch.

```
# killall -u magesh
```

### 3) How to Kill User Sessions on Linux Using the Kill Command

Alternatively, you can kill the user session using the kill command. This requires a few extra steps compared to the above two methods because you can’t kill them directly.

First find the user tty session number from the w command output.

```
[[email protected] ~]# w
00:34:21 up 48 days, 23:38, 4 users, load average: 0.79, 0.58, 0.56
USER TTY FROM [email protected] IDLE JCPU PCPU WHAT
magesh pts/0 192.168.1.101 19:47 4:45m 0.04s 0.00s sh /opt/scripts/disk-usage.sh
renush pts/1 192.168.1.102 20:35 3:54m 2:23 0.00s sh bash
thanis pts/2 192.168.1.103 00:27 5.00s 0.08s 0.04s ssh
root pts/4 192.168.1.104 00:34 1.00s 0.02s 0.01s w
```

Once you have it, locate the PID of the corresponding tty session using the PS command.

```
ps -ft [tty]
```

```
[[email protected] ~]# ps -ft pts/4
UID PID PPID C STIME TTY TIME CMD
root 155183 155092 0 00:34 pts/4 00:00:00 -bash
root 163015 155183 0 00:35 pts/4 00:00:00 ps -ft pts/4
```

Finally kill the process id of the session.

```
kill -9 PID
```

```
# kill -9 155183
```

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/how-to-kill-user-sessions-on-linux/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/kill-terminate-inactive-idle-ssh-session-on-linux/
