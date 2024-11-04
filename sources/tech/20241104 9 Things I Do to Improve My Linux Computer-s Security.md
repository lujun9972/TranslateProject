[#]: subject: "9 Things I Do to Improve My Linux Computer's Security"
[#]: via: "https://itsfoss.com/improve-security-linux/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

9 Things I Do to Improve My Linux Computer's Security
======

[![Warp Terminal][1]][2]

Whether in real life or on the internet, security, and privacy are a concern for everyone.

The urban legend is that Linux as an operating system is a more secure choice than its alternatives. But that does not mean it is not vulnerable.

Hackers can find their way to exploit Linux systems as well. But it is not all bad, as there are many ways to make your system more secure than it already is.

So, I set out to find out some of the most effective, and easy options that I can enable on my Linux system to protect my data (and you can too!).

📋

What I share here is my opinion and comes from my experience. It's not that if you don't do all the mentioned points here, your system will be compromised immediately. A few points will be easy to implement, while some may not be practical for you. See what advice you can employ easily.

Another thing. What I share here is for the desktop Linux end users. Some point may be applicable to servers. If you are interested in actual security aspect of Linux, there is an [instructor-led training from Linux Foundation][3] (partner link). It costs a lot and is intended for people working on kernel development etc.

![][4]

### 1\. Encrypting the disk

A solid method to protect your data is through **Full-Disk Encryption** (FDE). The data encryption helps safeguard your information if someone gets physical access to your computer or it gets lost or stolen.

It provides full-proof protection for systems used in public or office settings. As good as FDE is, it is only possible to do it at the time of installation 😔

So, if you do not have it enabled, you need to back up your data, re-install the OS, and enable disk encryption during the setup process. It only takes a single click, and setting a passphrase. However, reinstalling is not a practical option for everyone.

Perhaps if you are doing a fresh install of Linux, you could consider encrypting the disk. Ubuntu and some other distributions provide this option in the installer.

![][5]

I did this while installing Ubuntu 24.04 and I feel more secure. Although, I have to enter two passwords while starting the system, one for decrypting the drive and the other one regular account.

📋

Encryption also has its downside. You'll have to enter one extra password when the system boots. And if you forget this disk encryption password, you cannot reset it like your regular account's password. Formatting the system with a fresh OS install is the only option while the existing data is lost.

### 2\. Updating the system regularly

![][6]

Linux is already very secure right out of the box, but it does not come without flaws. Bugs exist in every software, and Linux is no exception.

To make sure you are equipped with the latest security patches, it is necessary to keep your system updated regularly. A good habit is to set your system up so that it automatically applies all critical security updates.

Or, make a habit to manually check for updates, and apply them. I prefer the old-fashioned way of heading into the software updates, and downloading the sweet patches available.

Most Linux distributions, including Linux Mint, elementary OS, now support automatic updates in the latest releases. You just need to enable them.

It is also effortless to update and install patches on Linux, through package manager and some simple commands. You can take a look at one of our [tutorials on Ubuntu update][7] for reference:

![][8]

📋

This is a must for everyone. Keep your system updated.

### 3\. Checking logs and monitoring network

![][9]

It is intriguing for me to monitor the network or check system logs. While I may not be an expert, it is a useful thing to do if you do it the right way.

There are various command-line utilities to monitor and check logs of your system. We have a list of [system monitoring tools][10] that you can get started with. You can also [analyze the log files in your Linux system][11] using a couple of commands.

Of course, if the built-in options are insufficient for you. You can try a GUI program like [Portmaster][12] to manage and monitor network connections.

![][8]

📋

This may not be an activity everyone would like to do and you are likely not going to find anything usually. But reading logs itself is a skill and it helps in troubleshooting the system when there is an issue.

### 4\. Installing software only from trusted sources

![][13]

One of the easiest and most effective ways of safeguarding your device is through smart software management.

Installing applications only from trusted sources (and only the ones useful to you) helps you reduce the risk of malware making its way into your system.

Only downloading from official and verified sources such as [Flathub][14], [Snapcraft][15], and software's official [GitHub][16] page is a sure-shot way to know that whatever you are downloading is the real deal. I prefer sticking to the Ubuntu App Center for the moment.

Some of those platforms also mark applications that are " **Verified** ". So, you can opt for those if you would rather not trust the other ones.

When you do not know about a software, getting help from Linux's massive community is also a good way to verify whether an application is safe or not.

📋

As a rule of thumb, I prefer installing from the software center/official repository or from the software developer's project itself (if it is not in the distribution's repository).

### 5\. Using encrypted DNS

You can enhance the security of your network by adding a layer of privacy. The more private you keep your internet experience, the less data attackers get about you.

If you are using a public, untrusted network or if you are not sure of your service provider, then it is always safe to use an encrypted DNS. While it is not a replacement for a VPN, it is an easy way to protect your DNS queries from ISPs or anyone monitoring your network.

![][17]

NextDNS, and [Quad9][18] are some of the DNS services you can try for this. I like NextDNS's offering because it suits all kinds of requirements on a budget. I can also integrate it with Portmaster if I like.

You can learn more about [enhancing privacy on your system][19] in one of our other articles:

![][8]

📋

DNS are a tricky thing. If some websites start to get inaccessible, you may want to switch back to the older DNS.

### 6\. Disabling root login

The root user has total access to perform system-wide changes. So, if an unauthorized user gets the root user credentials or accidentally enters the root user mode, it can be damaging to your personal computer and in an organization as well.

Disabling the 'Root' login feature is vital if you want to stay extra safe from potential hackers. The Linux distribution you are using will determine how to disable the root account.

The [ArchWiki][20] tells you about what you have to do on Arch Linux. Similarly, you can find documentations for other distros.

Not to forget, you always have **sudo** to elevate your user's privileges to root using this.

📋

Most desktop distributions already have root login disabled.

### 7\. Using a firewall

A firewall is an indispensable network security method, not just for Linux, but for any device that connects to the internet.

A firewall works simply by monitoring and regulating incoming and outgoing network traffic. Many distros come with a built-in firewall that you can configure to add rules to allow/block certain IP ranges to prevent unauthorized attempts to your network.

Not to forget, I mentioned a program like Portmaster above. So, you can utilize that as a nice network firewall too.

A good firewall configuration can protect against various types of attacks. You can follow some of our tutorials to learn more about it:

  * [How to Set Up Firewall with GUFW GUI Tool on Linux][21]
  * [Using Firewall With UFW in Ubuntu Linux [Beginner's Guide]][22]



📋

It is debatable how much security a basic firewall offers these days as most computers sit behind the router using NAT. Still, the firewall could come in handy if you are accessing the internet over WiFi at airport, hotels and other public places.

### 8\. Making proper data backup

I always back up my data. And, you should too!

Now, I include two kinds of backup in my strategy:

  * Timeshift for system settings
  * Dejadup (default Backup tool in many distros) for user data backup



If you mess up your system while configuring it or if an update creates undesired changes, Timeshift backups save the day.

![][8]

And if the disk crashes or you accidentally delete something important, DejaDup backup helps.

Of course, you can utilize [cloud storage services][23] to store some of your extremely important data offsite. After all, data should be backed up in multiple places.

![][8]

### 9\. Setting strong authentication

One of the most basic practices for good security is to keep strong passwords and rely on two-factor authentication.

While you can easily do that for online accounts using [password managers][24] where 2FA and passkeys have become the new standard, the traditional login to your computer often has a simple password.

I think if I combine all the insights from various anime I watch, I could make a pretty unique password with a variation of numbers, uppercase/lowercase letters, and symbols. So, try using stronger passwords.

### Wrapping Up

It is evident that you can use multiple methods to secure your Linux computer. However, keep in mind that despite all of these steps, a system is never impenetrable.

![][25]

The best thing to do at all times is to stay vigilant, and proactively notice changes in your system.

I constantly look for what is different every time I boot into my system, and you should too. Of course, you do not need to overthink every change, but thinking about them should allow you to spot problems early.

#### Author Info

![][26]

Swayam Sai Das is a student exploring the realms of Linux as an **Intern Writer** at It's FOSS. He is dedicated, when trying to push ranks in FPS games and enjoys reading literature classics in an attempt of putting on an academic facade.

--------------------------------------------------------------------------------

via: https://itsfoss.com/improve-security-linux/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://tidd.ly/3YLXF0a
[4]: https://training.linuxfoundation.org/wp-content/uploads/2018/07/cropped-unnamed-270x270.png
[5]: https://itsfoss.com/content/images/2024/11/ubuntu-disk-encryption-option.png
[6]: https://itsfoss.com/content/images/2024/10/vmware.jpg
[7]: https://itsfoss.com/update-ubuntu/
[8]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[9]: https://itsfoss.com/content/images/2024/10/WhatsApp-Image-2024-10-18-at-10.47.35_f525681f.jpg
[10]: https://itsfoss.com/linux-system-monitoring-tools/
[11]: https://itsfoss.com/read-compressed-log-files-linux/
[12]: https://itsfoss.com/portmaster/
[13]: https://itsfoss.com/content/images/2024/10/WhatsApp-Image-2024-10-18-at-10.48.37_2a440175.jpg
[14]: https://flathub.org/
[15]: https://snapcraft.io/store
[16]: https://github.com/
[17]: https://itsfoss.com/content/images/2024/10/nextdns-github.jpg
[18]: https://quad9.net/
[19]: https://itsfoss.com/improve-privacy/
[20]: https://wiki.archlinux.org/title/Sudo#Disable_root_login
[21]: https://itsfoss.com/set-up-firewall-gufw/
[22]: https://itsfoss.com/ufw-ubuntu/
[23]: https://itsfoss.com/cloud-services-linux/
[24]: https://itsfoss.com/open-source-password-managers/
[25]: https://itsfoss.com/content/images/2024/11/kevin-hobbes-computer-security-meme.jpg
[26]: https://itsfoss.com/content/images/2024/06/swayam-sai-das-1.jpg
