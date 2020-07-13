[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (espanso: An Open Source Cross-Platform Text Expander That Will Help You Type Faster and be More Productive)
[#]: via: (https://itsfoss.com/espanso/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

espanso: An Open Source Cross-Platform Text Expander That Will Help You Type Faster and be More Productive
======

_**Brief: espanso is a cross-platform text expander tool written in Rust. A text expander lets you use shortcuts instead of typing long words and sentences.**_

If you’re using keyboard [macros][1] or mouse macros, you’re probably already saving a lot of time to get things done.

But, you can’t just use macros to type everything. Yes, maybe a thing or two, but not a lot of things. And, for that very reason, a text expander should come in very handy.

In this article, I’ll take a look at [espanso][2], which is an open-source text expander.

### espanso: Open Source Text Expander

![][3]

espanso is an interesting open-source text expander tool with cross-platform support that’s written in [Rust programming language][4].

It doesn’t offer a GUI (Graphical User Interface) to customize or control. You’ll have to resort to terminal or changing YML files for any configuration change. The default settings make it pretty easy to use it.

Basically, it lets you utilize short codes or keywords to quickly write a piece of text. To start with, it offers one basic short code to type the date.

For instance, when you type “**:date**”, espanso will replace quickly replace it by adding the date as “**07/13/2020**“. By default, the date format is in the form of MM/DD/YYYY — but you can easily change it (we’ll take a look at it later in this article).

Similarly, you can have any custom keywords or short codes like “**:sayhello**” to type “**Hi there! My name is Ankush Das”**

### Features of espanso

![][5]

Here’s what espanso offers to get you more productive:

  * Supports text expansions when using a shell to help you keep things faster
  * Execute custom scripts with the help of espanso’s keywords
  * Supports adding emojis (needs additional installation)
  * Save code snippets and re-use them with espanso
  * System-wide integration
  * Application-specific configuration option
  * Cross-platform support



In addition to the features I’ve listed, you can actually get a lot more things done if you explore more use-cases and try it out on your system.

### Installing espanso on Linux

You can get the **DEB** package from its [GitHub releases section][6] to install it on any Ubuntu-based distribution. Even though most of you know how to install a **.deb** package, if you’re new, you may take a look at the [ways to install DEB files in Ubuntu][7].

For Ubuntu-based distros, if you encounter an error to launch it from the terminal, make sure to type in the command below to ensure that you have the necessary packages for it to work:

```
sudo apt update
sudo apt install libxtst6 libxdo3 xclip libnotify-bin
```

You can also install it on your Arch system / Manjaro distribution through [AUR][8].

For other Linux distribution, you can use the [snap package][9] to get it installed.

If you didn’t know about installing snaps, I’d recommend you to refer our guide on [installing and using snaps on Linux.][10]

For installation and download instructions, you can refer to espanso’s [official installation instructions.][11]

[Download Espanso][12]

### How To Use espanso?

Because there’s no GUI, some of you may need some time to figure out how it works. So, to save you the trouble, let me share a few tips to get started using espanso.

#### Launching &amp; Setting it up

Once you’ve successfully installed espanso, you need to launch it to set it up.

To do that, simply type in the following in the terminal:

```
espanso start
```

It should ask you to add the process to launch when your computer boots up, you can allow it to proceed if you want it that way. If you hit **no**, you will have to manually start espanso manually every time you log in to your system.

You can always register the service to systemd later by typing the following command:

```
espanso register
```

To verify if it’s running, you may want to type in:

```
espanso status
```

Sometimes the shortcodes might conflict with your regular usage. So, when you need to stop it, just hit the following in the terminal:

```
espanso stop
```

You can explore more commands and options for espanso by typing “**espanso**” or “**espanso -h**” in the terminal to get the details.

#### Basic Configuration of Expanded Texts

You might want to refer the [official documentation][13] if you’re using Windows or macOS. Here, I’ll show you how to customize or add custom expanded texts on Linux.

To get started, navigate your way through the home directory (by [enabling the hidden files][14]) and head into the **/.config/espanso** folder.

![][15]

Once you’re here, you’ll find a **default.yml** file as shown in the screenshot above. This is the default configuration file of espanso.

You have to open it with your default text editor. It should look something like this:

![][16]

If you look close enough, you can notice the preset texts and the short codes or keywords for it.

You can choose to edit the existing ones (just like I modified the format of the date in the screenshot above) or add new ones as required.

When you want to add a new keyword for text expansion, you can do that by simply copy-pasting the following format right below the existing matches:

```
- trigger: ":YourKeywordHere"
  replace: "Text That You Want To Be Replaced With The Keyword"
```

You need to add your custom keywords and text as needed and save the modifications to the file and it’s done!

You may get a notification of a successful configuration re-load. If you don’t, simply head to the terminal and restart espanos to see refresh the new configuration.

If it gives you an error, you might want to adjust the spacing of what you wrote and make sure it’s correct. To give you an idea, here’s how it looks after adding new keywords:

![Espanso Modified Configuration file][17]

Here, I’ve pointed out an example of basic customization. You can also perform application-specific matches and other advanced configuration by following the [official documentation][13].

### Wrapping Up

While I didn’t know about this amazing tool before covering it – but now that I do, it’s proving to be a very useful tool that could save me a lot of time.

What do you think about espanso? Let me know your thoughts in the comments below!

--------------------------------------------------------------------------------

via: https://itsfoss.com/espanso/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://en.wikipedia.org/wiki/Macro_(computer_science)
[2]: https://espanso.org
[3]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/espansos-demo-1.gif?ssl=1
[4]: https://www.rust-lang.org
[5]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/espanso-running.png?ssl=1
[6]: https://github.com/federico-terzi/espanso/releases/tag/v0.6.3
[7]: https://itsfoss.com/install-deb-files-ubuntu/
[8]: https://itsfoss.com/aur-arch-linux/
[9]: https://snapcraft.io/espanso
[10]: https://itsfoss.com/use-snap-packages-ubuntu-16-04/
[11]: https://espanso.org/install/linux/
[12]: https://espanso.org/
[13]: https://espanso.org/docs/
[14]: https://itsfoss.com/hide-folders-and-show-hidden-files-in-ubuntu-beginner-trick/
[15]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/espanso-customizing.png?ssl=1
[16]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/espanso-default-config.png?ssl=1
[17]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/espanso-modified-config.png?ssl=1
