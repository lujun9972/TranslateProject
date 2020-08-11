[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Better Than Top: 7 System Monitoring Tools for Linux to Keep an Eye on Vital System Stats)
[#]: via: (https://itsfoss.com/linux-system-monitoring-tools/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

Better Than Top: 7 System Monitoring Tools for Linux to Keep an Eye on Vital System Stats
======

No matter whether you’re a system administrator or just a casual desktop user, you may have heard about one of the most popular terminal-based system monitoring tool “**[top][1]**“. To many, it’s the [task manager on Linux][2].

In case you didn’t know, the “Top” utility helps display all the running processes and gives you some important information on the performance of your personal computer or server. It also gives you the ability to [kill processes][3] that you don’t need.

But, what alternatives do you have? Do you need any? Let’s find out.

### Why do you need “Top” Alternatives?

![][4]

Considering that you’ll find it baked in on most of the Linux distribution by default, top isn’t going anywhere.

However, you won’t find any mouse support, scroll support, no colors to highlight things, and a few other cons. For these reasons, [using top command][5] to its fullest is not easy for everyone.

There are alternatives which provide you more information on the running processes and lets you manage them easily.

### Useful system monitoring tools like top (but better than top)

Hence, in this article, I’ll mention a few good alternatives to the top command utility that are potentially better.

I have included installation commands for Debian/Ubuntu based distributions. Almost all the tools mentioned here should be available via the package manager of other distributions as well.

**The list is in no particular order of ranking**. Try what’s best for you!

#### 1\. htop

![][6]

[htop][7] is an interactive system monitor that supports scrolling and mouse interaction as well.

Not just limited to the advanced features — but it also highlights the processes and information using some color codes which makes it look more organized and easy to work with.

In fact, I personally prefer using htop over top to keep an eye on the system resources and the processes. It lets you kill processes, filter them, offers tree view of processes (press F5), and a couple of other features.

##### How to install htop?

For Ubuntu-based distros, you just have to head to the terminal and type in:

```
sudo apt install htop
```

You can also find RPM/DEB packages from the links on their [official website][8] for other Linux distributions. In either case, you can also download the [source][9] if you want.

[htop][7]

#### 2\. atop

![][10]

If you want more details on the running processes or the ones that were previously running, [atop][11] is a useful utility for that.

It also supports permanent logging of resource utilization if you want it for long-term analysis. Even though I’m not a professional system administrator, it’s easy to say how useful it is to see the critical resource being highlighted.

In my case, I’d prefer htop over this — but it depends on what information you’re looking to monitor and what are the extra features that you want. You can learn more about it on its [official website.][11]

##### How to install atop?

If you’re on a Debian-based distro, you just have to type in:

```
sudo apt install atop
```

You can also find .rpm packages listed for every version on their [official download page][12]. In case you’re looking to install it on other Linux distros, you should refer to its [official web page][11].

[atop][11]

#### 3\. nmon

![][13]

[nmon][14] is yet another useful utility that lets you monitor system resources and processes.

Unlike some other options, it gives you control to break down the information and display them one by one (toggle them) as needed

![][15]

As you can observe in the screenshots above, you have to press specific keys to toggle stats and look through them. The stats are color-coded as well, which makes them easy to go through.

##### How to install nmon?

For Ubuntu-based distros, you can simply type in:

```
sudo apt install nmon
```

In either case, you can head to its [official download page][14] and look for packages for other Linux distros.

#### 4\. vtop

![][16]

[vtop][17] is an interesting utility to monitory system resources while having the ability to manage them as well.

Unlike others, it is written using node.js. So, you’ll need to [install node.js and npm packages][18].

It does offer mouse support and it looks like a GUI in a terminal. You can disable the mouse control if you don’t need it. So, it makes things easier to understand and monitor. Also, you can customize the vtop theme pretty easily.

##### How to install vtop?

For Ubuntu-based distros, you need to enter the following commands in the terminal

```
sudo apt install nodejs
sudo apt install npm
sudo npm install -g vtop
```

Here, you’re installing nodejs and its package manager npm first. Next, with the third command, you’re actually installing vtop.

If you want to install it on other Linux distributions, you can refer to its [GitHub page][17].

#### 5\. bashtop

![][19]

An impressive top alternative which potentially needs more resources to run — but easy-to-use and looks better in my opinion.

I’m starting to think that I should use bashtop instead of htop for monitoring.

In addition to the information it offers by default, you can also add more modules if you also want CPU temperatures and other stats using bashtop.

You can get all the details on it at its [GitHub page][20].

##### How to install bashtop?

For some reason, it isn’t available in the default repository of Ubuntu 20.04 – but if you have Ubuntu 20.10 or later, you can simply type in:

```
sudo apt install bashtop
```

For Ubuntu 20.04 or lower (any Ubunty-based distro), you can simply add the PPA and get it installed using the following commands:

```
sudo add-apt-repository ppa:bashtop-monitor/bashtop
sudo apt update
sudo apt install bashtop
```

To get installation isntructions for other Linux distributions, you can check out the [GitHub page][20].

[bashtop][21]

#### 6\. gtop

![][22]

Yet another impressive top alternative. It looks somewhat similar to vtop and also needs nodejs to be installed.

You don’t get much to customize here — but it’s easy to use and provides all the necessary information.

##### How to install gtop?

Similar to vtop, you need to install nodejs and npm package manager to get started on Ubuntu-based distros.

Just type in the following commands in the terminal to get it installed:

```
sudo apt install nodejs
sudo apt install npm
sudo npm install -g gtop
```

If you need to install it on any other Linux distro, you can refer to its [GitHub page][23].

[gtop][23]

#### 7\. Glances

![][24]

Glances is an amazing system monitoring tool for folks who need to have more information at a single place.

The information you’ll have on your screen will depend on the size of the window. So, you should expect all the essential stats for disk I/O, network, kernel version, sensors, and other information.

You can also export the stats to an external database and use a web interface to monitor remotely. This is particularly useful for the system administrators making a custom web dashboard of sorts.

##### How to install Glances?

For Ubuntu-based distros, you can simply type in:

```
sudo apt install glances
```

If you’re looking to install it on other Linux distributions, you can refer to its [official website][25] where you should find an auto install script or just explore its [GitHub page][26].

[Glances][25]

**Wrapping Up**

Now that you know about some of the amazing top alternatives – what would you pick to monitor your system?

Do you use some other tools for system monitoring in Linux? Which one is it? Do share your it with us in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-system-monitoring-tools/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://linux.die.net/man/1/top
[2]: https://itsfoss.com/task-manager-linux/
[3]: https://itsfoss.com/how-to-find-the-process-id-of-a-program-and-kill-it-quick-tip/
[4]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/top-command-linux.png?ssl=1
[5]: https://linuxhandbook.com/top-command/
[6]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/htop-command.png?ssl=1
[7]: http://hisham.hm/htop/
[8]: http://hisham.hm/htop/index.php?page=downloads
[9]: http://hisham.hm/htop/index.php?page=downloads#sources
[10]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/atop-command-linux.png?ssl=1
[11]: https://www.atoptool.nl/index.php
[12]: https://www.atoptool.nl/downloadatop.php
[13]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/nmon-command-2-1.jpg?ssl=1
[14]: http://nmon.sourceforge.net/pmwiki.php?n=Main.HomePage
[15]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/nmon-command.png?ssl=1
[16]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/vtop-command.png?ssl=1
[17]: https://github.com/MrRio/vtop
[18]: https://itsfoss.com/install-nodejs-ubuntu/
[19]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/bashtop.png?ssl=1
[20]: https://github.com/aristocratos/bashtop#installation
[21]: https://github.com/aristocratos/bashtop
[22]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/gtop.jpg?ssl=1
[23]: https://github.com/aksakalli/gtop
[24]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/glances.png?ssl=1
[25]: https://nicolargo.github.io/glances/
[26]: https://github.com/nicolargo/glances
