[#]: subject: "Collect sudo session recordings with the Raspberry Pi"
[#]: via: "https://opensource.com/article/22/3/sudo-session-recordings-raspberry-pi"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Collect sudo session recordings with the Raspberry Pi
======
Logs and session recordings can help debug what happened on a given host
if it acts strangely. Try this setup on your Raspberry Pi.
![Vector, generic Raspberry Pi board][1]

I've used the `sudo` command for years, and one of my favorite features is how it saves a record of everything happening in a terminal while running a command. This feature has been available for over a decade. However, sudo 1.9 introduced central session recording collection, allowing you to check all administrative access to your hosts on your network at a single location and play back sessions like a movie.

I use this feature on my Raspberry Pi, and I recommend it to other Pi users. Even if you fully trust your users, logs and session recordings can help debug what happened on a given host if it acts strangely: _Oops, wrong file deleted in /etc_.

### Why sudo?

Sudo gives administrative access to users. Unless you limit access to a short list of commands, you practically provide full access to your hosts. The `pi` user can use `sudo` without even entering a password on the Raspberry Pi OS. On other operating systems, the default configuration grants members of the `wheel` group full administrative access.

### Before you begin

The new **sudo_logsrvd** application handles collection. Earlier versions of the Raspberry Pi OS only had sudo version 1.8. The latest version is based on Debian 11 and includes sudo version 1.9.5. You also need a second host with sudo 1.9, which sends recordings to sudo_logsrvd.

### Configuring sudo_logsrvd

For a production environment, I recommend using TLS encrypted connections between sudo and sudo_logsrvd. However, to simply understand how session recording works, you can go without encryption. This also means that there is nothing to configure other than creating the storage directory and starting sudo_logsrvd:


```


$ sudo mkdir /var/log/sudo-io
$ sudo chmod 700 /var/log/sudo-io
$ sudo sudo_logsrvd

```

The sudo_logsrvd is now waiting for connections.

### Configuring sudo

Configure sudo 1.9 on a host using `visudo` and append the following lines to the `sudoers` file. You will need to replace the IP address with the one of your Raspberry Pi. Note that if you do not have a second machine with sudo 1.9, you can use the same Raspberry Pi running sudo_logsrvd for testing.


```


Defaults ignore_iolog_errors
Defaults log_servers = 172.16.167.129:30343
Defaults log_output

```

The first line is your escape route while experimenting with sudo_logsrvd: It ensures that sudo works even if sudo_logsrvd is inaccessible. This configuration is not recommended for production environments as users can execute commands without proper recording.

The next two lines configure where to send recordings and enable recordings.

### Testing

For testing, do something that you cannot figure out from sudo logs in syslog: A shell session. Be aware that sudo 1.9.8 changes this, but it is not yet available in Linux distributions. In this case, the logs show only that a shell is started, but nothing about what happened inside:


```


$ sudo -s

# id
uid=0(root) gid=0(root) groups=0(root),117(lpadmin)

# cd /root/

# ls -la
total 36
drwx------  5 root root 4096 Feb 16 12:27 .
drwxr-xr-x 18 root root 4096 Jan 28 04:22 ..
-rw-------  1 root root  827 Feb 16 12:49 .bash_history
-rw-r--r--  1 root root  571 Apr 10  2021 .bashrc
drwx------  3 root root 4096 Feb 16 10:54 .cache
-rw-------  1 root root   41 Feb 16 11:12 .lesshst
drwxr-xr-x  3 root root 4096 Feb 16 12:27 .local
-rw-r--r--  1 root root  161 Jul  9  2019 .profile
drwx------  3 root root 4096 Jan 28 04:21 .vnc

# exit
$

```

Even if the logs do not show anything useful, you can still use the `sudoreplay` command to list and playback recordings:


```


$ sudo sudoreplay -l
Feb 16 12:37:54 2022 : pi : TTY=/dev/pts/1 ; CWD=/home/pi ; USER=root ; HOST=raspberrypi ; TSID=000001 ; COMMAND=/usr/bin/ls -l /etc/ssl/private/
Feb 16 12:38:14 2022 : pi : TTY=/dev/pts/1 ; CWD=/home/pi ; USER=root ; HOST=raspberrypi ; TSID=000002 ; COMMAND=/usr/bin/ls -la /etc/ssl/private/
Feb 16 12:49:21 2022 : pi : TTY=/dev/pts/1 ; CWD=/home/pi ; USER=root ; HOST=raspberrypi ; TSID=000003 ; COMMAND=/bin/bash
Feb 16 12:50:03 2022 : pi : TTY=/dev/pts/1 ; CWD=/home/pi ; USER=root ; HOST=raspberrypi ; TSID=000004 ; COMMAND=/bin/bash
Feb 16 12:50:28 2022 : pi : TTY=/dev/pts/1 ; CWD=/home/pi ; USER=root ; HOST=raspberrypi ; TSID=000005 ; COMMAND=/usr/bin/sudoreplay -l

$ sudo sudoreplay 000004
Replaying sudo session: /bin/bash

# id
uid=0(root) gid=0(root) groups=0(root),117(lpadmin)
# cd /root/
# ls -la
total 36
drwx------  5 root root 4096 Feb 16 12:27 .
drwxr-xr-x 18 root root 4096 Jan 28 04:22 ..
-rw-------  1 root root  827 Feb 16 12:49 .bash_history
-rw-r--r--  1 root root  571 Apr 10  2021 .bashrc
drwx------  3 root root 4096 Feb 16 10:54 .cache
-rw-------  1 root root   41 Feb 16 11:12 .lesshst
drwxr-xr-x  3 root root 4096 Feb 16 12:27 .local
-rw-r--r--  1 root root  161 Jul  9  2019 .profile
drwx------  3 root root 4096 Jan 28 04:21 .vnc

# exit
$

```

### What is next?

I hope you learned something new today and will try it on your own Raspberry Pi. The setup I described here is good enough for testing. For production use, I recommend creating a startup script for sudo_logsrvd, which is missing from the Debian package, and you should use TLS between sudo and sudo_logsrvd. You can learn more about configuring TLS encryption from the documentation or my [blog][2]. The nice thing is that you can also use sudo_logsrvd on the Raspberry Pi in production in your home or small office. Unless you have dozens of sudo clients all utilizing the terminal heavily (like `ls -laR /`), not even the SD card of the Pi is a bottleneck.

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/sudo-session-recordings-raspberry-pi

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/raspberrypi_board_vector_red.png?itok=yaqYjYqI (Vector, generic Raspberry Pi board)
[2]: https://www.sudo.ws/posts/2021/08/securing-the-sudo-to-sudo_logsrvd-connection/
