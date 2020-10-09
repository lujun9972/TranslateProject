[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Log Out from Ubuntu Session [Beginner’s Tip])
[#]: via: (https://itsfoss.com/ubuntu-logout/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Log Out from Ubuntu Session [Beginner’s Tip]
======

How do you log out of Ubuntu?

The answer depends on whether you are using Ubuntu server or desktop. I’ll show you steps for both.

### Logout Ubuntu from terminal (for server)

**If you are using Ubuntu server** and you are confined to the terminal screen, you can use the exit command:

```
exit
```

Yes. That’s the way to logout from terminal because there is no logout command in Ubuntu or [any Linux distribution][1]. You have commands for shutdown Ubuntu but there is no separate log out command.

Why there is no logout command in Linux?

You may wonder if there is command for shutdown, command for restart then why there is no Linux command for logout?

The answer lies in the way Linux works. You probably know that Linux is only kernel and you need a shell to interact with the kernel. When you use a terminal or if you log in to an Ubuntu system via SSH, you open a shell session.

If you want to logout from your session, you simply exit the shell. This is why the exit command is equivalent to log out command in Linux.

### Log out from Ubuntu desktop (GUI method)

If you are using Ubuntu desktop, you have a graphical interface (called [desktop environment][2]). You can use your mouse here.

I am showing the screenshot for the default GNOME desktop but if you are using some [other Ubuntu desktop variants like Kubuntu, Lubuntu][3] etc, there should also be a logout button or logout option in the power menu.

To log out from Ubuntu desktop session, go to the top right corner and click to bring the system tray. You should see Power Off / Log Out option. Click on it and it will show the Log Out option.

![][4]

When you click on the Log Out button, it will open a dialogue box and ask for your conformation. If it receives no input from you, you’ll be logged out in 60 seconds.

![][5]

That’s it. Now you know how to log off from Ubuntu session.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-logout/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/what-is-linux-distribution/
[2]: https://itsfoss.com/what-is-desktop-environment/
[3]: https://itsfoss.com/which-ubuntu-install/
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/10/log-out-ubuntu.jpg?resize=798%2C428&ssl=1
[5]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/10/log-out-confirmation-ubuntu.png?resize=800%2C299&ssl=1
