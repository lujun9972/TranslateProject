[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Managing process accounting on Linux)
[#]: via: (https://www.networkworld.com/article/3571465/managing-process-accounting-on-linux.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

Managing process accounting on Linux
======
Process accounting can provide a lot of details that can help monitor user and system activity on Linux.
Putilich / Getty Images

Process accounting is a method of recording and summarizing commands and processes. It's an option on Linux systems, but you have to enable it and use a particular command to view the details collected. This post covers the commands involved and offers some suggestions on making the views even more useful.

To start, understand that process accounting is different than what you see when running the **ps** command. It shows details on commands that have completed –- not those that are currently running. It also shows a lot more details than you would see by looking at your users' command history files and keeps all the collected data in a single file on the system.

If you want to turn on the processing accounting, you have to use a command like this:

```
$ sudo /usr/sbin/accton on
Turning on process accounting, file set to the default '/var/log/account/pacct'.
```

On this system, the file **/var/log/account/pacct** is the file in which the data will be saved. This file is **not** a plain text file, so don't try viewing it with **more** or **tail** commands. Instead, use the **dump-acct** command to view it as shown in the example below. Anticipate a very wide and lengthy display that will wrap around in a normal terminal window unless you widen it considerably or pipe output to the tail command.

```
$ sudo dump-acct /var/log/account/pacct | tail
grotty          |v3|     0.00|     0.00|     2.00|  1000|  1000| 12000.00|     0.00|  321103|  321101|     |       0|pts/1   |Fri Aug 14 13:26:07 2020
groff           |v3|     0.00|     0.00|     2.00|  1000|  1000|  6096.00|     0.00|  321101|  321095|     |       0|pts/1   |Fri Aug 14 13:26:07 2020
nroff           |v3|     0.00|     0.00|     4.00|  1000|  1000|  2608.00|     0.00|  321095|  321087|     |       0|pts/1   |Fri Aug 14 13:26:07 2020
man             |v3|     0.00|     0.00|     4.00|  1000|  1000| 10160.00|     0.00|  321096|  321087| F   |       0|pts/1   |Fri Aug 14 13:26:07 2020
pager           |v3|     0.00|     0.00|  2018.00|  1000|  1000|  8440.00|     0.00|  321097|  321087|     |       0|pts/1   |Fri Aug 14 13:26:07 2020
man             |v3|     2.00|     0.00|  2021.00|  1000|  1000| 10160.00|     0.00|  321087|  318116|     |       0|pts/1   |Fri Aug 14 13:26:07 2020
clear           |v3|     0.00|     0.00|     0.00|  1000|  1000|  2692.00|     0.00|  321104|  318116|     |       0|pts/1   |Fri Aug 14 13:26:30 2020
dump-acct       |v3|     2.00|     0.00|     2.00|  1000|  1000|  4252.00|     0.00|  321105|  318116|     |       0|pts/1   |Fri Aug 14 13:26:35 2020
tail            |v3|     0.00|     0.00|     2.00|  1000|  1000|  8116.00|     0.00|  321106|  318116|     |       0|pts/1   |Fri Aug 14 13:26:35 2020
clear           |v3|     0.00|     0.00|     0.00|  1000|  1000|  2692.00|     0.00|  321107|  318116|     |       0|pts/1   |Fri Aug 14 13:26:45 2020
```

Don't be surprised if some of the processes shown are unfamiliar. Some may have been run by commands that you ran, rather than by you directly (e.g., **groff** and **grotty** in the output above). Many are system processes that are independent of user activity.

To better understand what you're looking at, you may want to add column headings as I have done with these commands:

```
echo "Command         vers  runtime   systime   elapsed    UID    GID   mem_use     chars      PID     PPID  ?    retcode  term     date/time" "
sudo dump-acct /var/log/account/pacct | tail -5
```

Your output will look something like this:

```
Command         vers  runtime   systime   elapsed    UID    GID   mem_use     chars      PID     PPID  ?   retcode   term     date/time
tail            |v3|     0.00|     0.00|     3.00|     0|     0|  8116.00|     0.00|  358190|  358188|     |       0|pts/1   |Sat Aug 15 11:30:05 2020
pacct           |v3|     0.00|     0.00|     3.00|     0|     0|  9624.00|     0.00|  358188|  358187|S    |       0|pts/1   |Sat Aug 15 11:30:05 2020
sudo            |v3|     0.00|     0.00|     4.00|     0|     0| 10984.00|     0.00|  358187|  354579|S    |       0|pts/1   |Sat Aug 15 11:30:05 2020
gmain           |v3|    14.00|     3.00|  1054.00|  1000|  1000|  1159680|     0.00|  358169|    3179|    X|       0|__      |Sat Aug 15 11:30:03 2020
vi              |v3|     0.00|     0.00|   456.00|  1000|  1000| 10976.00|     0.00|  358194|  354579|     |       0|pts/1   |Sat Aug 15 11:30:28 2020
```

Note that the headings are spaced out in the **echo** command so that they will more or less line up with the data columns. Your version of the command might vary. Go ahead and adjust the line if the labels don't line up properly on your screen.

The fields, in case they’'e not clear from the headings, include:

  * the command that was run
  * the version of the accounting file format
  * user time
  * system time
  * effective time
  * user ID
  * group ID
  * average memory usage
  * IO
  * process ID
  * parent process ID
  * ?
  * return code
  * terminal on which the command was run
  * date and time when the command completed



Many of the processes shown will be system processes. If you want to see only the processes for a particular user, you can pipe the output to an **awk** command to select details by userid (column 6). The number (1000) shown in the command below should be replaced with the particular user's numeric UID. Note that **dump-acct** uses the vertical bar as the field separator. The preceding blank and following **$** in the "/ 1000$" specification are required to ensure that the command matches only that userid.

```
$ sudo dump-acct /var/log/account/pacct | awk -F'|' '$6 ~ / 1000$/'
```

### Log rotation

The **pacct** files can get quite large, but should be rotated if you are using **logrotate** as evidenced in the following listing.

```
$ ls -ltr /var/log/account | tail -6
-rw-r----- 1 root adm   10229 Aug  9 08:39 pacct.4.gz
-rw-r----- 1 root adm   10020 Aug 10 08:40 pacct.3.gz
-rw-r----- 1 root adm 1190037 Aug 11 08:38 pacct.2.gz
-rw-r----- 1 root adm   10436 Aug 12 08:40 pacct.1.gz
-rw-r----- 1 root adm  110592 Aug 13 08:38 pacct.0
-rw-r--r-- 1 root adm  205056 Aug 14 13:57 pacct
```

### Turning process accounting off and back on

You can easily turn process accounting off if you don't need the data or want to free up the disk space that it uses.

```
$ sudo /usr/sbin/accton off
Turning off process accounting
```

The following command will turn it back on again. The file used is the default, so doesn’t need to be specified to start or stop the accounting.

```
$ sudo /usr/sbin/accton on
Turning on process accounting, file set to the default '/var/log/account/pacct'
```

### Not a process

One of the unusual aspects of process accounting is that is not managed by a process. You won't see a related process running when you examine processes with the **ps** command. Instead, it's managed by the Linux kernel.

### Wrap-Up

Process accounting can provide a lot of details on processes that have run on your systems. It allows you to keep detailed accounting information on both system and user activity along with the system resources used.

Join the Network World communities on [Facebook][1] and [LinkedIn][2] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3571465/managing-process-accounting-on-linux.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://www.facebook.com/NetworkWorld/
[2]: https://www.linkedin.com/company/network-world
