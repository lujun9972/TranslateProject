[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Automatically Change Color Scheme of Your Linux Terminal Based on Your Wallpaper)
[#]: via: (https://itsfoss.com/pywal/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

Automatically Change Color Scheme of Your Linux Terminal Based on Your Wallpaper
======

If you are It’s FOSS newsletter subscriber, you already know that we have started a new ‘Terminal Tuesday’ series. In this, you’ll get to read about command line tools or tips/tricks to help you in terminal.

Terminal is not all about serious work, it can be fun sometimes. You can [play games in terminal][1] or use some [funny Linux commands][2] to amuse yourself, colleagues or family members.

This week’s terminal tip is a fun one. It’s about changing the color scheme of your terminal based on your wallpaper.

Why would you do that? Because it looks good and if you are sharing your Linux desktop screen, it adds a nice touch to the overall look.

### Pywal: Handy utility to automatically change Linux terminal scheme based on background wallpaper

[Pywal][3] is nifty Python-based command line tool that changes the terminal colors based on the colors of that wallpapers.

You can use it to set the wallpaper and you’ll see that the terminal colors change immediately.

Take a look at this. Looks good, isn’t it?

![][4]

Let me show you how to use Pywal properly.

#### Step 1: Install Pywal on Linux

Pywal is based on Python so you can easily install it on any Linux distribution with Python support. It is even easier for Arch/Manjaro users as they can find `python-pywal` package in their repository.

You’ll need to [install Pip][5] first. You can use your distribution’s package manager to install pip3 (for Python3). On Debian/Ubuntu based distributions, you can use the following command:

```
sudo apt install pip3
```

Now that you have pip3 on your system, use it to install Pywal for all the users on your system:

```
sudo pip3 install pywal
```

#### Step 2: Using Pywal to change the terminal color scheme

I presume that you are a bit familiar with Linux commands to use Pywal.

Download the wallpaper of your choice. Make a note of the location of the wallpaper and its file name.

Open a terminal and use the `wal` command with the location of your wallpaper file as input:

```
wal -i path_to_wallpaper_file
```

You’ll see that your system’s background is changed and the terminal changes it color immediately based on the background wallpaper:

![][6]

#### Step 3: Make new terminal use the color scheme of wallpaper

Open a new terminal and you’ll notice that it doesn’t use the new color scheme.

Weird? Not so much. By default, the changes color scheme only applies to already running terminal screens. Newly opened terminals keep on using the system’s color scheme.

This can be changed easily. You can use change your shell’s configuration file.

Normally, you should be using bash shell but if you are not sure, [check which shell you are using by default][7].

Open ~/.bashrc file in your favorite [terminal based text editor][8]. On Ubuntu, you can always [use the nano editor][9].

At the end of this ~/.bashrc file, add the following line, save and exit the file.

```
# Import colorscheme from 'wal' asynchronously
# &   # Run the process in the background.
# ( ) # Hide shell job control messages.
(cat ~/.cache/wal/sequences &)

# Alternative (blocks terminal for 0-3ms)
cat ~/.cache/wal/sequences

# To add support for TTYs this line can be optionally added.
source ~/.cache/wal/colors-tty.sh
```

Now the new color scheme will be applied to the new terminals as well.

#### Step 4: Keep the new color scheme even after reboot (if you want it)

When you reboot your system, pywal won’t run anymore and your terminal will revert to the old color scheme.

If you want to keep the color scheme based on the wallpaper, pywal provides a handy option `-R` that restores the last used color scheme.

All you have to do is to add `wal -R` command to the list of your startup programs.

This step could be different for different distributions. [On Ubuntu, you can manage startup applications][10] using the ‘Startup Applications’ program.

Add the command, give it a name and description like this:

![][11]

Now Pywal run automatically at each reboot and restore the last used color scheme. In other words, your terminal will have the colors based on your desktop background (if it was setup by pywal).

#### Take the customization to the next level by adding the color scheme to other utilities

In many Linux communities, people share the screenshots of their desktop. [It’s FOSS Facebook group][12] hosts DesktopFriday post where members share their desktops and you’ll find them using Pywal for other applications as well.

[Pywal has some plugins][13] that extend the color scheme to Vim, Emacs, Gnuplot or even CLI-Visualizer (audio visualizer).

![Credit: cli-visualizer][14]

You can also use Pywal with [window managers like i3][15], [sway][16], taskbars like polybar. [Plenty of customization][17] scope if you are interested.

#### Do you like Pywal?

I understand that not everyone is into tweaking the looks and feels of their desktop but for those who do, Pywal is an awesome utility.

How about you? Did you like Pywal? Do you know some other utility of this kind that you would like to be covered under our ‘Terminal Tuesday’ series? I welcome your feedback and suggestions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/pywal/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/best-command-line-games-linux/
[2]: https://itsfoss.com/funny-linux-commands/
[3]: https://github.com/dylanaraps/pywal
[4]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/wallpy-2.jpg?resize=800%2C442&ssl=1
[5]: https://itsfoss.com/install-pip-ubuntu/
[6]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/wallpy-3.jpg?resize=799%2C452&ssl=1
[7]: https://linuxhandbook.com/shell-using/
[8]: https://itsfoss.com/command-line-text-editors-linux/
[9]: https://itsfoss.com/nano-editor-guide/
[10]: https://itsfoss.com/manage-startup-applications-ubuntu/
[11]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/autostart-walpy.png?resize=797%2C626&ssl=1
[12]: https://www.facebook.com/groups/LinuxUsersGroupOfficial/
[13]: https://github.com/dylanaraps/pywal/wiki/Plugins
[14]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/pywal.gif?resize=800%2C394&ssl=1
[15]: https://itsfoss.com/regolith-linux-desktop/
[16]: https://itsfoss.com/sway-window-manager/
[17]: https://github.com/dylanaraps/pywal/wiki/Customization
