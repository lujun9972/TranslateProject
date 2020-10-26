[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Update Firefox on Ubuntu [Beginner’s Tip])
[#]: via: (https://itsfoss.com/update-firefox-ubuntu/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Update Firefox on Ubuntu [Beginner’s Tip]
======

The other day, one It’s FOSS reader asked me, “Abhishek, How do I Update Firefox on Ubuntu”.

The question surprised me because there are no specific steps for updating Firefox. When you [update Ubuntu][1], [Firefox][2] is updated with it. Just keep your system updated to get the latest Firefox.

As you can see, there is an update available for Firefox among other system updates.

![Firefox update on Ubuntu][3]

Then I understood the context behind the question. On Windows, Firefox prompts for updating the browser. Or, you go to settings menu -&gt; Help -&gt; About Firefox to see the current version and if there is an update available.

But that’s not the case in Linux. No notifications for the availability of a Firefox update here. Probably this is the reason why people switching to Linux from Windows wonder about updating Firefox on Ubuntu.

### Update Firefox on Ubuntu

If you are new to Ubuntu then let me tell you something about the updates. If you install applications from the software center or use the apt or [apt-get command][4] for installing any software, it is Ubuntu’s responsibility to provide you software updates.

Ubuntu often prompts for the availability of new updates. If you expand it a bit, you can see what kinds of updates are there. You’ll notice that apart from the system and kernel updates, Ubuntu also provides updates on some installed software.

Firefox is no different. It comes preinstalled on Ubuntu. Even if it doesn’t and you install Firefox in Ubuntu on your own, even in that case you can update Firefox with the regular system update.

![][5]

Just check for the system updates and see if Ubuntu is providing an upgrade on Firefox.

![][3]

If you specifically want to update Firefox, you can [use the apt command][6] in the following fashion:

```
sudo apt install --only-upgrade firefox
```

If there are any updates available for Firefox from Ubuntu, it will install that update.

![][7]

Please keep in mind that you have to rely on Ubuntu for updating Firefox. Just because there is a new major release of Firefox, you won’t get it immediately like you did in Windows. You’ll have to wait for the update to come from Ubuntu repositories and it may take a couple of days.

I hope it cleared the air for you and now you know how to update Firefox on Ubuntu Linux and why a new Firefox version is not immediately available.

--------------------------------------------------------------------------------

via: https://itsfoss.com/update-firefox-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/update-ubuntu/
[2]: https://www.mozilla.org/en-US/firefox/new/
[3]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/10/update-firefox-ubuntu.png?resize=800%2C519&ssl=1
[4]: https://itsfoss.com/apt-get-linux-guide/
[5]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/04/software-updater-ubuntu-20-04.jpg?resize=800%2C220&ssl=1
[6]: https://itsfoss.com/apt-command-guide/
[7]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/10/updating-firefox-ubuntu.png?resize=800%2C459&ssl=1
