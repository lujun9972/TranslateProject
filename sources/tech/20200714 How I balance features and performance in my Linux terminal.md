[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How I balance features and performance in my Linux terminal)
[#]: via: (https://opensource.com/article/20/7/performance-linux-terminal)
[#]: author: (Ricardo Gerardi https://opensource.com/users/rgerardi)

How I balance features and performance in my Linux terminal
======
Customize a feature-rich terminal that's easy on system resources.
![Terminal command prompt on orange background][1]

I am a big fan of command-line applications, and I spend a lot of time working in a terminal. Terminal-based applications are, in many cases, faster, more flexible, and more intuitive than their graphical user interface (GUI) counterparts.

Having a flexible and powerful terminal with many command-line tools makes me more productive. This is one of the main reasons I moved to Linux several years ago and never looked back.

Because I spend so much time in the terminal, I invested some time to make it a pleasant environment to work in. My goal is to find a balance between having a feature-rich terminal without wasting too many system resources.

### My computers

I use two laptops daily: a business laptop running Fedora 32 and a personal laptop running Arch Linux.

Here's what my Fedora 32 terminal looks like:

![Fedora running zsh with the Powerlevel10k theme][2]

(Ricardo Gerardi, [CC BY-SA 4.0][3])

And this is my Arch Linux terminal:

![Arch Linux running zsh with the Powerlevel10k theme][4]

(Ricardo Gerardi, [CC BY-SA 4.0][3])

The system information is provided by the excellent [ufetch][5] system-info tool with a few personal tweaks. And the weather report is powered by [wttr.in][6].

### My terminal apps

On the business laptop, I use [Terminator][7] as my terminal app. On Arch Linux, I've been using [Alacritty][8], which is a fast GPU-accelerated terminal emulator. However, I am no longer happy with it because it uses too much memory. I will move to Terminator on that laptop soon.

You can find Terminator in the default repository of many Linux distributions, including Fedora and Arch Linux.

### My favorite theme

For the visual part of the terminal, I use the Ambience color scheme with a transparent background shaded to 80%. This makes my terminal a little darker to avoid confusion, especially when the background is a "busy" image.

### My favorite prompt

My favorite shell is [zsh][9], which I customize using [Oh My Zsh][10] with the [Powerlevel10k][11] theme. Powerlevel10k allows you to customize your prompt to provide useful information, including the status of your Git repository, active Python virtual environment, programming-language compiler or interpreter version, command execution time, and much more.

If you want more information about customizing zsh, read my article [_5 tips to improve productivity with zsh_][12].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/performance-linux-terminal

作者：[Ricardo Gerardi][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/rgerardi
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/terminal_command_linux_desktop_code.jpg?itok=p5sQ6ODE (Terminal command prompt on orange background)
[2]: https://opensource.com/sites/default/files/uploads/fedora_zsh_small_1.png (Fedora running zsh with the Powerlevel10k theme)
[3]: https://creativecommons.org/licenses/by-sa/4.0/
[4]: https://opensource.com/sites/default/files/uploads/arch_zsh_small_1.png (Arch Linux running zsh with the Powerlevel10k theme)
[5]: https://gitlab.com/dawidpotocki/ufetch
[6]: http://wttr.in/
[7]: https://gnome-terminator.org/
[8]: https://github.com/alacritty/alacritty
[9]: https://opensource.com/article/19/9/getting-started-zsh
[10]: https://github.com/ohmyzsh/ohmyzsh
[11]: https://github.com/romkatv/powerlevel10k
[12]: https://opensource.com/article/18/9/tips-productivity-zsh
