[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Switch Users in Ubuntu and Other Linux Distributions [Quick Beginner Tip])
[#]: via: (https://itsfoss.com/switch-users-ubuntu/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Switch Users in Ubuntu and Other Linux Distributions [Quick Beginner Tip]
======

It is really simple to switch users in [Ubuntu][1] or any other Linux distribution using the terminal.

All you need to do is to know the unsername and its account password and you can switch users with su command:

```
su another_username
```

You’ll be asked to enter the password of the user you want to switch to.

![][2]

As you can see in the screenshot above, I changed to user _prakash_ from user _abhishek_ in the terminal.

There are some minor details with this method that I’ll share with you in a moment. I’ll also share the graphical way of switching users in Linux if you are using desktop Linux.

Switching to root user

If you want to switch to the [root user in Ubuntu][3], you can use the following command:
**sudo su
**You’ll have to enter your own user password here.

### Change user in Linux command line

![][4]

Let’s see things a bit in detail. To switch users, you need to first know the exact username because tab competition doesn’t work here. You can [list all the users in Linux command line][5] by viewing the content of the /etc/passwd file.

You’ll also need to know the password of the user account you want to switch to. This is for security reason, of course.

```
su another_username
```

If you are the admin user or have sudo access, you can change account password with [passwd command][6].

You’ll notice that some people use a `-` between su and the username. There is a specific reason for that.

```
su - another_username
```

When you use -, -l or –login option, you start the shell as a login shell. This means that it will initialize the environment variables like PATH and changes to the home directory of the changed user. It will be as if you logged into the terminal as the second user.

![][7]

Note: though `-`is more popular, it is advised to use –login option.

### Change users in Linux graphically (for desktop Linux)

If you are using desktop Linux, the above method may not be sufficient for you. Why? Because you switch the user in the terminal only. It is confined to the terminal. Nothing is changed outside the terminal.

If you want to switch users so that you can log in as another user and use all the system (browser, applications etc) graphically, you’ll have to log out and then log back in.

Now the screenshots may look different but the steps remain the same. Here’s how to switch users in Ubuntu Linux.

Go to the top right corner and click the Power Off/Log out option to open the dropdown and you can **choose either of Switch User or Log Out**.

  * **Switch User**: You get to keep your session active (applications keep on running) for current user. Good for temporarily switching users as you won’t lose your work.
  * **Log out**: Current session ends (all applications are closed). Good when you want to switch to the other user for a long time.



You can choose whichever option is more suited for your need.

![][8]

Now, you’ll be at the login screen with all the available users for your system. Choose the user account of your choice.

Clearly, you need to know the password of the user account you want to use.

That’s it. I hope you find this quick beginner tip helpful in changing users in Ubuntu and other Linux distributions. Questions and suggestions are always welcome.

--------------------------------------------------------------------------------

via: https://itsfoss.com/switch-users-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://ubuntu.com/
[2]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/switching-user-ubuntu-linux.png?resize=796%2C268&ssl=1
[3]: https://itsfoss.com/root-user-ubuntu/
[4]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/switch-users-linux.png?resize=800%2C450&ssl=1
[5]: https://linuxhandbook.com/linux-list-users/
[6]: https://linuxhandbook.com/passwd-command/
[7]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/switch-user-ubuntu-linux.png?resize=800%2C462&ssl=1
[8]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/switch-user-ubuntu.png?resize=800%2C500&ssl=1
