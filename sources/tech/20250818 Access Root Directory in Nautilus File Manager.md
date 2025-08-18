[#]: subject: "Access Root Directory in Nautilus File Manager"
[#]: via: "https://itsfoss.com/access-root-nautilus/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Access Root Directory in Nautilus File Manager
======

[![Warp Terminal][1]][2]

Once upon a time, Nautilus allowed accessing the root directory from 'Other locations' option in the sidebar.

This tiny but useful option has disappeared in the recent versions. But **you can still access root folder in Nautilus by typing / in the address bar**.

Let's see it in a bit more detail in this quick tutorial for Linux beginners.

Nautilus is the default file explorer in GNOME desktop environment and thus it should be applicable for Ubuntu, Fedora and many other distributions that use GNOME.

### Access root directory from Nautilus

Open the Nautilus file manager. You'll notice that there is an address bar on the top that displays like Home or the current location. Click on it and you'll see that you can enter text here.

All you have to do is to enter `/` here. That's it.

![Click on the address bar and enter /][3]

If it helps, here's a video of the entire process to show things better.

0:00

/0:13

1×

Access root directory as a normal user

There is one tiny thing to note here. You'll be accessing the root directory as a normal user. So while you can read most files, you won't be able to create new or modify existing ones.

If you want that, you can easily do that. Let me show that in the next section.

### Access root directory as a root user

Open the Nautilus file explorer and type the following in the address bar:

```

    admin://

```

![][4]

You'll be asked to enter the password. That will be your own user account password.

Here's a video to show things in a better way.

0:00

/0:15

1×

When you access the root directory as an admin (sudo), you can make changes here, create new files etc. This comes handy in situations where you have to make changes to config files and you want to avoid the terminal. Files opened from here will be opened in graphical text editor, easier to modify.

This is different from [opening any file as root trick I shared earlier][5].

![][6]

### Conclusion

This is one of the [many Nautilus tweaks][7] that you can use to get more out of it.

![][8]

It's quite powerful and it is always good to explore the less obvious features of your regular tools. In that regard, you may also want to learn a thing or two about [utilizing the search feature in Nautilus][9].

![][10]

As I mentioned initially, the option to access root files used to be under the 'Other locations' in the left sidebar. It is removed and replaced by a clandestine method. I think the rational behind this decision was to avoid accidental changes to root files. That's just my guess. I let you enjoy this quick Nautilus tip.

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][11].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][12] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/access-root-nautilus/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/08/access-root-folder-as-normal-user-nautlus-1.png
[4]: https://itsfoss.com/content/images/2025/08/access-root-folder-as-root-nautilus.png
[5]: https://itsfoss.com/open-nautilus-as-administrator/
[6]: https://itsfoss.com/content/images/icon/android-chrome-192x192-606.png
[7]: https://itsfoss.com/nautilus-tips-tweaks/
[8]: https://itsfoss.com/content/images/icon/android-chrome-192x192-605.png
[9]: https://itsfoss.com/nautilus-file-search/
[10]: https://itsfoss.com/content/images/icon/android-chrome-192x192-607.png
[11]: https://itsfoss.com/plus-member-resources/
[12]: https://itsfoss.com/lifetime-membership/
