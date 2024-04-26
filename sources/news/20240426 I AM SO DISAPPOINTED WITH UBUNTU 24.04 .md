[#]: subject: "I AM SO DISAPPOINTED WITH UBUNTU 24.04 😡"
[#]: via: "https://news.itsfoss.com/ubuntu-24-04-disappointment/"
[#]: author: "Abhishek https://news.itsfoss.com/author/root/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I AM SO DISAPPOINTED WITH UBUNTU 24.04 😡
======
The sheer audacity of not caring for its users reeks of Microsoft-esque
arrogance.
The all caps headline is deliberate. I am all enraged.

Disappoint is a sober word here. I am actually pissed at the casual arrogance of Ubuntu and its parent company Canonical.

_Please excuse the language_ , but I just cannot express my disgust any other way.

What's the issue? Well, Ubuntu 24.04 LTS is here and it will stay for more than the usual 5 years of long-term support period.

For years, Ubuntu has been promoting its 'universal packaging format' Snaps over 'Universal Operating System' Debian's deb packages.

But it has gone to the next level in the recent release of Ubuntu 24.04 LTS.

### Ubuntu's official app store won't install deb files

Actually, it started with the previous version Ubuntu 23.10.

If you download a .deb package of a software, you cannot install it using the official graphical software center on Ubuntu anymore.

When you double-click on the downloaded deb package, you'll see this error, 'there is no app installed for Debian package files'.

![Canonical's Ubuntu 24.04 pretends to not know what to do with deb files][1]

If you right-click and choose to open it with Software Center, you are in for another annoyance.

**The software center will go into eternal loading**. It may look as if it is doing something, but it will go on forever. I could even livestream the loading app store on YouTube, and it would continue for the 12 years of its long-term support period 😕

![Ubuntu app store keeps on loading without even showing any error message][2]

And this is not just a simple bug they forgot to fix. They deliberately ignored it.

### Canonical has no intention of fixing it

An [issue was opened on GitHub][3] in Sep'23 when Ubuntu 23.10 was in beta. Canonical did not fix it for Ubuntu 23.10 release.

And six months later, Ubuntu 24.04 LTS is released and Canonical has still not fixed this bug.

That's because the so-called bug for us, the public, is most likely a feature crafted by them, Canonical folks.

Otherwise, Ubuntu developer won't say that they "didn't have capacity to work on it".

> Unfortunately we didn't have the capacity to work on this for 24.04, but it will be a priority for the next cycle!

![][4]

This is a lame excuse. Who would believe that? Not me, for sure.

It's a stalling tactic. The bug was noticed by users for months and yet, it was not fixed.

The entire point of these intermediate releases in-between the LTS ones is to test things out. Clearly, there was no intent to fix it while the end users, specially the new users, kept on struggling with this error.

### Please don't say" it's not a big deal, Abhi, you could always use Gdebi, Eddy or the terminal"

Yes, I know all this. I rarely even use the graphical app store. But it's not about me who has been using Linux, primarily Ubuntu, for the last 15 years. It's about people who are new to Ubuntu, people who are escaping Microsoft Windows. People who are not technically advanced but want to use this 'free' operating system.

Imagine that you are absolutely new to Linux but want to use it on your personal computer instead of Windows. You read websites like It's FOSS where Ubuntu is recommended to beginners.

You ask me if it is possible to use popular tools like Chrome on Ubuntu. I say yes. Just download it from the official website and install it by double-clicking like you do it with exe files in Windows.

Only this time, you encounter this error, you search the web and learn that you have to install another tool or use the command line to install a simple browser.

This is not an ideal first experience for a beginner.

### Ubuntu is cleverly booting out deb in favor of Snap, one baby step at a time

By the way, before Ubuntu 20.04, you could just double-click on the deb files, and it would be opened in the software center for installation. Starting with Ubuntu 20.04, this behavior was cunningly changed.

Double-clicking the deb file would open it with Archive manager.

![Starting with Ubuntu 20.04, double clicking behavior on deb file got changed][5]

You could still double-click on it and choose to open deb file with Software Center for the current file and the future ones.

![You could still open deb file with Software Center which is not possible anymore][6]

I didn't pay enough attention to why this behavior wasn't changed back, but now it seems like this too was a deliberate move.

And then, there is also the **issue of replacing deb packages with Snap, even with the apt command line tool**. You use 'sudo apt install chromium', you get a Snap package of Chromium instead of Debian. And that's just one of several such snappily replaced applications in this way.

### Bottom line

I understand that Canonical has every right to make the decision about their product. You want to promote Snap over Deb, fine. But don't do it in a deceiving manner.

If you would like to keep your 'Snap store' deb-free, fine! At least have the decency to provide Gdebi by default for local deb file installation.

Otherwise, it is extremely disappointing to see this sheer disregard for the user experience. And this is coming from a devoted Ubuntu user for the past 15 years.

Ubuntu rose to popularity because it made Linux simpler for the end user. 'Linux for human beings' was its motto. I don't see this motto mentioned anywhere now. I wonder if that too is deliberate.

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-24-04-disappointment/

作者：[Abhishek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/root/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/content/images/2024/04/ubuntu24-deb-error.png
[2]: https://news.itsfoss.com/content/images/2024/04/ubuntu-app-store-keeps-loading.png
[3]: https://github.com/ubuntu/app-center/issues/1407
[4]: https://news.itsfoss.com/content/images/2024/04/ubuntu-dev-wont-fix-deb-issue.png
[5]: https://itsfoss.com/content/images/wordpress/2020/05/error-opening-deb-file.png
[6]: https://itsfoss.com/content/images/2023/09/deb-file-install-fix-ubuntu.webp
