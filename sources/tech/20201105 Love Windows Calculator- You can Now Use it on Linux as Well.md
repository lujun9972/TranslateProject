[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Love Windows Calculator? You can Now Use it on Linux as Well)
[#]: via: (https://itsfoss.com/windows-calculator-linux/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

Love Windows Calculator? You can Now Use it on Linux as Well
======

In the first quarter of 2019, [Microsoft open sourced the Windows Calculator][1]. Being open source, it allows developers to use it in their own applications.

I couldn’t care less for a calculator application but as some It’s FOSS readers pointed out, they like using the Windows Calculator.

After almost a year and a half, the ‘famed’ Windows Calculator is now available on Linux but not officially.

### Windows Calculator on Linux

![][2]

The team behind [Uno Platform][3] has ported the Windows Calculator to Linux and made it [available as a Snap application][4].

Since it is not officially from Microsoft and is ported by Uno project, the application is named Uno Calculator.

Uno is a [UI platform][3] and it allows you to build native mobile, desktop, and WebAssembly apps with C# and XAML from a single code base. The UI looks the same on all devices.

Team Ubuntu has worked with the developers of Uno Platform to make it easier for developers of cross-platform applications to publish for Linux users, via the Snap Store.

If you are using Ubuntu or if you have [Snap enabled on your Linux distribution][5], you can use the following command to install Uno Calculator using the following command:

```
sudo snap install uno-calculator
```

_**Note: At the time of writing this article, Uno Calculator has not been pushed to the stable branch. If you see an error, you can install it from the beta channel using this command:**_

```
sudo snap install uno-calculator --beta
```

Once installed, you can search for Uno Calculator in application menu and start using it.

![][6]

### Do you need Windows Calculator on Linux?

That depends on you to be honest.

You have the choice of GNOME Calculator that is pretty handy for most work. If you want advanced stuff, you have [Qalculate][7].

But then if you often switch between Windows and Linux or if you have used Windows Calculator for a long time, you would find it useful.

I know some of the It’s FOSS readers don’t like Microsoft products or non-FOSS products or FOSS products from Microsoft. However, if it provides more choice for a Linux user, then why not?

Again, I have never used Windows Calculator so I cannot comment on its usefulness or superority (if any). Honestly, I hardly use calculator on the desktop. No, not because I am a [human computer like Shakuntala Devi][8] but more for the reason that I never really had the need.

What about you? Are you a fan of (now open source) Windows Calculator? Will you be using it on Linux?

--------------------------------------------------------------------------------

via: https://itsfoss.com/windows-calculator-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://blogs.windows.com/windowsdeveloper/2019/03/06/announcing-the-open-sourcing-of-windows-calculator/#thPSwqktI1JVwqab.97
[2]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/10/windows-calculator-ubuntu.png?resize=800%2C521&ssl=1
[3]: https://platform.uno
[4]: https://snapcraft.io/uno-calculator
[5]: https://itsfoss.com/enable-snap-support-linux-mint/
[6]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/10/windows-calculator-linux.png?resize=800%2C521&ssl=1
[7]: https://itsfoss.com/caligator/
[8]: https://en.wikipedia.org/wiki/Shakuntala_Devi
