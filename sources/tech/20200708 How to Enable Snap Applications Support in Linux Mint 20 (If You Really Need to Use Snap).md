[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Enable Snap Applications Support in Linux Mint 20 (If You Really Need to Use Snap))
[#]: via: (https://itsfoss.com/enable-snap-support-linux-mint/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Enable Snap Applications Support in Linux Mint 20 (If You Really Need to Use Snap)
======

The newly [released Linux Mint 20][1] doesn’t have Snap support enabled by default.

Sooner or later, you may encounter a situation where an application version is only available as Snap package and then you need to enable Snap support.

If you go about [enabling Snap][2] in Mint 20 like you do in other Linux distributions, you’ll encounter an error like this:

```
E: Package 'snapd' has no installation candidate
```

![Snap installation needs slight extra effort in Linux Mint 20][3]

Normally, this error means that the package is not available in the repository but that’s not the case here. Snap is explicitly blocked here and you have to remove this block by removing the /etc/apt/preferences.d/nosnap.pref file.

If you are comfortable with Linux command line, you can easily delete this file and enable snap support.

If you are not comfortable with the terminal, I discuss a slightly safer way of doing it and that is to move the file instead of removing it.

### Enable snap support in Linux Mint 20

In a terminal, type the following command to move the nosnap preference file to your home directory:

```
sudo mv /etc/apt/preferences.d/nosnap.pref ~
```

Now you can go on and install the snapd daemon like always:

```
sudo apt install snapd
```

![][4]

Once the snap support is enabled in Linux Mint, you can use the snap commands to install applications in Snap format.

You can use the Nemo file browser and delete the file you copied in the home directory. Safer this way, if you are afraid of the rm command in terminal.

### Why Linux Mint explicitly disabled Snap support?

[Snap][5] is a universal package format that can be installed in any distribution that supports snapd. This is one of the biggest advantage of snap packages.

These snap packages are ‘containerized’ meaning that these packages contain all the dependency within the package and they don’t rely on and interact with the system’s installed packages and libraries (mostly). Snap packages are automatically updated to newer versions.

But snap packages have some negative points as well. They are huge in size. If an apt package is 100MB in size, the snap package of the same application may have 1 GB of size.

Apart from that, snap applications take longer to load and they also take more disk spaces.

But that’s not the reason why snaps are banished from Linux Mint 20.

[Linux Mint][6] team took a hard decision of blocking Snap by default after Ubuntu went on to blurring the line between apt packaging system and snap packaging system.

When you use apt to install an application, you expect an apt package to be installed. But that’s not the case in Ubuntu 20.04 (Mint 20 is based on this Ubuntu version). In Ubuntu 20.04, if you use apt to [install Chromium browser][7], it installs a snap version of this browser.

Mint team is clearly not happy with this violation:

> A year later, in the Ubuntu 20.04 package base, the Chromium package is indeed empty and acting, without your consent, as a backdoor by connecting your computer to the Ubuntu Store. Applications in this store cannot be patched, or pinned. You can’t audit them, hold them, modify them or even point snap to a different store. You’ve as much empowerment with this as if you were using proprietary software, i.e. none. This is in effect similar to a commercial proprietary solution, but with two major differences: It runs as root, and it installs itself without asking you.

And hence they decided to explicitly blocked snap support from Mint 20.

### To snap or not snap, that is the question

As always, there is a way in Linux to get what you want. So, you can bypass this blockage and enable snap package support in Linux Mint 20.

As I mentioned in the beginning, you may face certain situations where an application is only available as Snap and then you may need Snap support. But till then, you can enjoy Linux Mint 20 without snap.

What about you? Are you going to use snap or not? What do you think of the overall ‘no snap in my distro’ approach?

--------------------------------------------------------------------------------

via: https://itsfoss.com/enable-snap-support-linux-mint/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/linux-mint-20-download/
[2]: https://itsfoss.com/install-snap-linux/
[3]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/snap-support-linux-mint-20.png?ssl=1
[4]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/enable-snap-support-linux-mint-20.png?ssl=1
[5]: https://snapcraft.io/
[6]: https://www.linuxmint.com/
[7]: https://itsfoss.com/install-chromium-ubuntu/
