[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to kill all user sessions on Linux using shell script)
[#]: via: (https://www.2daygeek.com/shell-script-kill-all-user-sessions-linux/)
[#]: author: (Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/)

How to kill all user sessions on Linux using shell script
======

There are multiple ways to automate the system administrator task on Linux.

It drastically reduces human efforts and saves reasonable time.

shell script is one of the methods to automate frequent jobs.

For a scenario, you want to run a weekly job or EOD job to populate some data for reporting purposes.

To do so, you need to kill all ssh sessions that are currently accessing the application on the system before beginning the job.

Please refer the following article which was written in the past to **[kill a particular user session on Linux][1]**.

The below shell script will help you to delete all of them. This script takes tty value of the user sessions and kill them using the **pkill** command.

```
$ sudo vi /opt/script/kill-user-sessions.sh

#!/bin/bash
usession=$(w | awk '{if (NR!=1) {print $2 }}' | tail -n +2)
for i in $usession
do
pkill -9 -t $i
done
```

Set an executable permission to **“kill-user-sessions.sh”** file.

```
$ sudo chmod +x /opt/script/kill-user-sessions.sh
```

Finally add a **cronjob** to automate this. It runs daily at 3AM.

```
$ sudo crontab -e

0 3 * * * /bin/bash /opt/script/kill-user-sessions.sh
```

If you want to execute the above script manually in a single line, use the blow one.

```
$ sudo for i in $(w | awk '{if (NR!=1) {print $2 }}' | tail -n +2); do pkill -9 -t $i; done
```

### How to exclude few users on the system

Use the below script, if you want to exclude any users on the system. I will be excluding the **“root”** and **“ansible”** users, but you can replace the user name that you want to exclude.

```
$ sudo vi /opt/script/kill-user-sessions-1.sh

#!/bin/bash
usession=$(w | grep -v "root|ansible" | awk '{if (NR!=1) {print $2 }}' | tail -n +2)
for i in $usession
do
pkill -9 -t $i
done
```

Set an executable permission to **“kill-user-sessions-1.sh”** file.

```
$ sudo chmod +x /opt/script/kill-user-sessions-1.sh
```

Finally add a **cronjob** to automate this. It runs daily at 3AM.

```
$ sudo crontab -e

0 3 * * * /bin/bash /opt/script/kill-user-sessions-1.sh
```

If you want to execute the above script manually in a single line, use the blow one.

```
$ sudo for i in $(w | grep -v "root" | awk '{if (NR!=1) {print $2 }}' | tail -n +2); do pkill -9 -t $i; done
```

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/shell-script-kill-all-user-sessions-linux/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/how-to-kill-user-sessions-on-linux/
