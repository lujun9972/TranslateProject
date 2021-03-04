[#]: subject: (How to Turn Off Automatic Brightness on Ubuntu [Quick Tip])
[#]: via: (https://itsfoss.com/automatic-brightness-ubuntu/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

How to Turn Off Automatic Brightness on Ubuntu [Quick Tip]
======

Some new laptops come with built-in integrated light sensor. Operating systems use this sensor to measure the ambient light conditions and change the screen brightness automatically. This helps in [reducing eye strain][1].

You can see that this is a useful feature. But not everyone might like it all the time. For example, while [watching Netflix on Linux][2] at night, it reduces the screen brightness at the lowest for me. This makes the movie scene quite dull.

This is one of the many cases when you probably would not want automatic brightness. Turning off automatic brightness on Ubuntu is quite simple. I’ll show that to you in this quick article.

This tutorial is valid for [GNOME desktop environment][3]. The command line method should work for [MATE desktop][4] as well. If you are not certain, check [which desktop environment you are using][5].

### Turning off automatic brightness on Ubuntu

You can find the option to toggle automatic brightness under Power settings.

Press the Windows (also known as Super or Meta key in Linux world) key. This will bring the Activities area and you can search for Settings here.

![][6]

In the Settings application, go to the **Power** settings from the left sidebar. Under the **Power Saving** option, you can see the **Automatic Brightness** option.

Toggle the button to turn it off or on.

![][7]

It’s super easy with the GUI, right? Now let’s take a look at the command line method as well.

### Alternate method: Turning off automatic brightness in Ubuntu using terminal

GNOME based desktop environments can also access the brightness settings via command line.

Open a terminal in Ubuntu and use the following command to turn off the automatic brightness:

```
gsettings set org.gnome.settings-daemon.plugins.power ambient-enabled false
```

Similarly, you can set the value to true to enable the automatic brightness again:

```
gsettings set org.gnome.settings-daemon.plugins.power ambient-enabled true
```

Automatic brightness helps in saving the battery life but it could also become an annoyance, as I had mentioned earlier. I so wish that there was a way to make the automatic brightness not go beyond a certain level.

How about you? Do you prefer using automatic brightness on Ubuntu or other Linux distributions or on your smartphone?

--------------------------------------------------------------------------------

via: https://itsfoss.com/automatic-brightness-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/reduce-computer-eye-strain-linux/
[2]: https://itsfoss.com/netflix-firefox-linux/
[3]: https://www.gnome.org/
[4]: https://mate-desktop.org/
[5]: https://itsfoss.com/find-desktop-environment/
[6]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2021/03/settings-ubuntu.png?resize=800%2C268&ssl=1
[7]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2021/03/automatic-brightness-ubuntu.png?resize=800%2C592&ssl=1
