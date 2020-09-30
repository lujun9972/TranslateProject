[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Run the Linux command line on your iPad)
[#]: via: (https://opensource.com/article/20/9/run-linux-ios)
[#]: author: (Lee Tusman https://opensource.com/users/leeto)

Run the Linux command line on your iPad
======
The Linux command line on iOS? Yes, you can.
![collection of hardware on blue backround][1]

Did you know that you can run a Linux command line on your iOS device? You might be asking, "why would I want to use text-based applications on my tiny iPhone?" OK, fair enough. That is a pretty reasonable question. But if you're reading Opensource.com, you probably know the answer: Linux users want to be able to use any device, and they also want to use their own customizations.

And most of all, they want a challenge.

I have a seven-year-old iPad 2 Mini that still works fine for reading e-books and other tasks. But I also want to use it to access the command line for applications and my suite of programs and scripts I can't seem to do without. I want the environment I'm accustomed to, as well as my standard development environment. Here's how I did it.

### Connect to a keyboard

Using the command line for programming on a phone or tablet's onscreen keyboard is not a lot of fun. I recommend connecting an external keyboard, either through Bluetooth or by using a camera connection kit adapter to connect a wired keyboard (my preference). Plugging my Kinesis Advantage split keyboard into my iPhone 6 makes for some strange optics, like a [corp's cyberdeck][2] from the classic [role-playing game][3] Shadowrun.

### Get a shell on iOS

You have two options for running a complete Linux system on iOS:

  * Secure shell (SSH) into a Linux computer
  * Run a virtualized system using Alpine Linux with iSH, which is open source, but must be installed using Apple's proprietary TestFlight app



Alternatively, there are two open source terminal emulator apps that provide open source tools within a restricted environment. This is the most limited option—it doesn't really let you run Linux, but you are running Linux tools. There are heavy restrictions on what you can do on the device with these apps, but they do get you some command-line functionality.

I'll look at the simplest approach before exploring more challenging solutions.

#### Option 1: A sandboxed shell

One of the easiest ways to get started is with the iOS app [LibTerm][4]. This is a sandboxed [open source][5] command-line shell with 80+ commands bundled in a $0 app. It ships with Python 2.7, Python 3.7, Lua, C, Clang, and more.

Along similar lines is [a-Shell][6], described as a "text-based user interface for a screen-based platform." a-Shell is [open source][7], in active development, grants access to the filesystem, and ships with Lua, Python, Tex, Vim, JavaScript, C, and C++, along with Clang and Clang++. It even allows you to install Python packages with pip.

#### Option 2: SSH anywhere

One step up from downloading an app is configuring an SSH client. For a long time now, it's been possible to use one of many SSH client apps on iOS to connect to a server running a Linux distro or BSD. The advantage of using SSH is that your server can be running any distro with any software you like. You work remotely, and your output just gets piped to your iOS device's terminal emulator.

[Blink shell][8] is a popular paid [open source][9] SSH app. Outside of the small screen, using this software is akin to connecting to a server via any other command prompt. Blink's terminal looks beautiful, with a number of included themes and the ability to create your own themes, including customizing and adding new fonts.

#### Option 3: Run Linux

Using SSH to connect to a server running Linux is a great way to access a prompt, but it does require access to an external server and a connection. This isn't the worst barrier to entry, but it's not completely negligible, and you may want to use Linux without this server requirement.

If that's your case, you'll have to break out something a bit more on the cutting edge. [TestFlight][10] is a proprietary service for deploying in-development apps before they're submitted to Apple's App Store. You can download the TestFlight app from the store, and then sign up for a number of test applications. Apps in TestFlight allow a limited number of external beta testers (generally up to 10,000) for a limited amount of time. To download a test app, you must access a link directly from your device, which is generally found on the test app developer's website.

### Run Alpine Linux with iSH

[iSH][11] is an open source TestFlight app that runs a virtual machine with the [Alpine Linux][12] distro out of the box (but you can run other distributions with a bit more tinkering).

An important caveat: _this is experimental_. Since iSH is currently a test app, don't expect permanent or robust service. TestFlight apps are time-limited. My current build lasts 60 days. This means that in 60 days, I'll be locked out and have to rejoin iSH's next testing phase. Furthermore, I'll lose my files unless I export them with Files on iOS or back them up to a Git host or [with SSH][13]. To be clear: _Don't rely on this to continue working! Don't put anything on here that is essential! Back up your work elsewhere!_

#### Install iSH

Get started by installing [TestFlight][14] through the App Store. Then install iSH by [getting the install link][15] through its website. There is another installation method that uses the AltStore, but I have not tried it. Or, if you have a paid developer account, you can download iSH's repo from GitHub and deploy it yourself.

Using the link, TestFlight installs an iSH app on your device. Like any other app, it appears on your screen with an icon.

#### Manage packages

iSH runs an x86 emulator with Alpine Linux. Alpine is a tiny, under-5MB distro. This was my first time running Alpine, and I thought I'd get frustrated with such a minimal distro, but I actually really enjoyed it.

![Alpine Linux on iOS][16]

(Lee Tusman, [CC BY-SA 4.0][17])

Alpine uses the [apk][18] package manager, which is simpler than even apt or pacman.

To install a package:


```
`apk add package`
```

To remove a package:


```
`apk del package`
```

Find other commands and info with:


```
`apk --help`
```

Update the package manager:


```
`apk update apk upgrade`
```

#### Get a text editor

Alpine's default text editor is Vi, but I prefer Vim, so I installed it:


```
`apk add vim`
```

You could install Nano or Emacs, if you prefer.

#### Change the shell

I don't know about you, but I need the [fish shell][19]. Other folks prefer [Bash][20] or [Zsh][21]. But Alpine uses ash! Ash is a fork of Dash shell, itself a fork of the original ash or [Almquist shell][22]. It is designed for speed. I decided to trade speed in favor of the built-in auto-completion, color, Vim-key control, and syntax highlighting that I know and love in fish shell.

Install fish:


```
`apk add fish`
```

If you want Bash and its completions and man pages instead, you need to install them and some extra things:


```
`apk add bash bash-doc bash-completion`
```

Alpine's minimalist ideology generally means that some programs that would be a single package in other distros are split into multiple smaller packages. This also means you can customize and slim down your system exactly how you want.

You can find more details on installing Bash in [this tutorial][23].

##### Change the default shell

After installing fish, you can temporarily switch to it and try it out by typing `fish` and dropping into the shell. But I want to make fish my default shell, and the `chsh` command I'm used to from other distros doesn't work.

First, find out where fish is installed:


```
`which fish`
```

My output:


```
`/usr/bin/fish`
```

Next, edit the login shell to use fish. You can use any editor you're comfortable with. If you're a beginner, install Nano (with `apk add nano`) so that you can edit config files and save them with CTRL+X, confirm, and quit.

But I used Vim:


```
`vim /etc/passwd`
```

My first line was:


```
`root:x:0:0:root:/root:/bin/ash`
```

To make fish the default, change that line to:


```
`root:x:0:0:root:/root:/usr/bin/fish`
```

Then save and quit.

I'm sure there is a good way to re-source the shell so that you can start using it right away. But I'm not sure, so I recommend returning to the app browser, force-quitting the shell, and for good measure, shutting down and restarting your iPad or iPhone. Reopen iSH, and now, in addition to the "Welcome to Alpine!" message and info on getting started with apk, you will see the default fish login welcome message: _Welcome to fish, the friendly interactive shell_. Hooray!

![Fish shell on Alpine Linux][24]

(Lee Tusman, [CC BY-SA 4.0][17])

#### Set up Python and pip

I decided to add [Python][25] (version 3.x), not just so I could write code but because I rely on several Python programs. Install it:


```
`apk add python3`
```

Although Python 2.x is deprecated, you can still install it:


```
`apk add python`
```

Install the Python package manager, pip, and [setuptools][26]:


```
`python3 -m ensurepip --default-pip`
```

It takes some time to install and set up the package manager, so just wait.

Then, you can download [curl][27], the networking transfer tool:


```
`apk add curl`
```

#### Read the manual

Fish uses built-in auto-completion based on man pages. Like other command-line users, I rely on the `man` manual, and Alpine doesn't come with it installed. So, I installed it along with the [less][28] pager:


```
`apk add man man-pages less less-doc`
```

In addition to man, I use the fabulous [tldr pages project][29], which provides simplified, community-driven man pages.

I installed it with pip:


```
`pip install tldr`
```

The `tldr` command connects to the web to fetch pages whenever it encounters a request for a new one. If you need to learn how to use a command, you can just type something like `tldr curl` to get a plain-English explanation and good examples of how to use the command.

You could, of course, automate all of this installation work with [dotfiles][30] or an install script, but that wouldn't really fall within the Alpine way of customizing a minimal install exactly to your specifications. Besides, it didn't take that long, did it?

### Learn more

The iSH wiki contains a "[what works][31]" page with reports on what packages currently work. Of note, [npm does not][32] appear to work at this time.

Another wiki page explains how you can [access iSH files][33] from the iOS Files app. This is one way you can move and transfer files.

You could also install Git (yep! `apk add git` ) and push your work to a remote repo or transfer it to a server over SSH. And, of course, you can download and run any number of fabulous open source projects from GitHub on your system.

For more information about iSH, consult these links:

  * [iSH website][11]
  * [Subreddit][34]
  * [GitHub issues][35]
  * [Wiki][36]



--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/run-linux-ios

作者：[Lee Tusman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/leeto
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/osdc_BUS_Apple_520.png?itok=ZJu-hBV1 (collection of hardware on blue backround)
[2]: https://www.shadowruntabletop.com/products/setting-sourcebooks/
[3]: https://opensource.com/article/20/7/free-rpg-day
[4]: https://libterm.app/
[5]: https://github.com/ColdGrub1384/LibTerm
[6]: https://holzschu.github.io/a-Shell_iOS/
[7]: https://github.com/holzschu/a-shell/blob/master/LICENSE
[8]: https://blink.sh
[9]: https://github.com/blinksh/blink/blob/raw/COPYING
[10]: https://testflight.apple.com/
[11]: https://ish.app/
[12]: https://alpinelinux.org/
[13]: https://opensource.com/article/20/9/ssh
[14]: https://apps.apple.com/us/app/testflight/id899247664
[15]: https://ish.app/#get
[16]: https://opensource.com/sites/default/files/uploads/ish-install.png (Alpine Linux on iOS)
[17]: https://creativecommons.org/licenses/by-sa/4.0/
[18]: https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management
[19]: https://opensource.com/article/20/3/fish-shell
[20]: https://opensource.com/resources/what-bash
[21]: https://opensource.com/article/19/9/getting-started-zsh
[22]: https://en.wikipedia.org/wiki/Almquist_shell
[23]: https://www.cyberciti.biz/faq/alpine-linux-install-bash-using-apk-command/
[24]: https://opensource.com/sites/default/files/uploads/ish.png (Fish shell on Alpine Linux)
[25]: https://www.python.org/
[26]: https://pypi.org/project/setuptools/
[27]: https://curl.haxx.se/
[28]: https://en.wikipedia.org/wiki/Less_%28Unix%29
[29]: https://tldr.sh/
[30]: https://opensource.com/article/19/3/move-your-dotfiles-version-control
[31]: https://github.com/ish-app/ish/wiki/What-works%3F
[32]: https://github.com/ish-app/ish/issues/874
[33]: https://github.com/ish-app/ish/wiki/View-iSH-files-in-Files-App
[34]: https://www.reddit.com/r/ish/
[35]: https://github.com/ish-app/ish/issues
[36]: https://github.com/ish-app/ish/wiki
