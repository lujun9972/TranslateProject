[#]: subject: "How to change a hostname in Linux"
[#]: via: "https://opensource.com/article/21/10/change-hostname-linux"
[#]: author: "Seth Kenlon https://opensource.com/users/seth"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to change a hostname in Linux
======
Use the hostnamectl command to change your hostname on a Linux computer.
![Person using a laptop][1]

To change your hostname on a Linux computer, use the `hostnamectl` command.

For example, to change your computer's hostname to `myhostname`:


```
$ sudo hostnamectl --static \
\--transient \
\--pretty \
myhostname
```

### What is a hostname? 

Computers have network addresses, but they're usually difficult for humans to remember. Hostnames are labels intended to help humans refer to a specific computer. Instead of navigating to 93.184.216.34, for instance, you navigate to www . example . com.

Read Alan Formy-Duval's article [What's in a hostname?][2] for more information about hostnames.

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/10/change-hostname-linux

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/laptop_screen_desk_work_chat_text.png?itok=UXqIDRDD (Person using a laptop)
[2]: https://opensource.com/article/21/10/what-hostname
