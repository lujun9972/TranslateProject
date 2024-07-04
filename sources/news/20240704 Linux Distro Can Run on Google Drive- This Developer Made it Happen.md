[#]: subject: "Linux Distro Can Run on Google Drive: This Developer Made it Happen"
[#]: via: "https://news.itsfoss.com/linux-on-google-drive/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Distro Can Run on Google Drive: This Developer Made it Happen
======
While Google and Linux do not rhyme well, this developer has managed
something interesting.
[![][1]][2]

When it comes to Linux, we get to see some really cool, and sometimes quirky projects ( _read Hannah Montana Linux_ ) that try to show off what's possible, and that's not a bad thing.

One such quirky undertaking has recently surfaced, which sees a sophomore trying to one-up their friend, who had booted Linux off [NFS][3]. With their work, **they have been able to run Arch Linux on Google Drive**.

Yes, you read that right, I was also surprised when I first came across it thanks to [TechSpot][4]. Let us take a look.

### Linux on Google Drive: What Kind Of Sorcery Is This?

![Source: Ersei 'n Stuff][5]

📋

In this article, I have summarized the details of what they did so that you can get the general idea.

The brainchild of Ersei, a student of Purdue University, published a [detailed blog][6] on how they were able to accomplish this seemingly ethereal task, that was driven by one of their vices, “ _competitiveness_ ”.

They wanted to create that was something harder, better, faster, and, of course, stronger than what their friend achieved. Ersei began with an idea, which then spiraled into various stages of creative thinking ( _they mention it as being on the brink of insanity_ ).

But, they finally went with running Linux on [Google Drive][7]. They started by taking the help of Filesystem in Userspace ([FUSE][8]), that allows non-privileged users to create file systems without the need to edit the kernel code.

Thereafter, they got FUSE programs installed in the Linux kernel's [initramfs][9], while enabling networking ([Dracut][10] helped with those), and chose Arch Linux to build on top of, testing it on a local S3 bucket.

Then, they moved to implement an [existing project][11] that allows for running FUSE with Google Drive into their Arch Linux build, made many fixes along the way, and mounted the drive.

After many [rsync][12] runs, a successful pairing of Linux and Google Drive was achieved.

![][13]

Of course, everything was not all fine and dandy, Ersei noted:

  * Extremely slow boot times.
  * Relative symlinks not working.
  * [Hard links][14] were non-functional.
  * Permissions and attributes don't appear to work.
  * [Symbolic links][15] to other Symbolic links didn't work.
  * Calling for Symlinks outside of Google Drive doesn't work.



But, that didn't demotivate Ersei, they went on to fix the slow boot times with a few tweaks. They even tested their Frankenstein creation on a spare laptop they had lying around that didn't have any storage. It worked just fine on it.

Even though they admit that this is a silly project, **they are open to the idea of commercializing this** for any interested company, offering up the promise of “ _True Cloud Native Computing_ ”.

#### Interested in trying this out?

If your answer is yes, [Ersei's blog linked][6] is a must-read if you want to get your bearings on how to run Linux on Google Drive.

If you have any further questions, then you can contact them by heading to their [homepage][16], where they have linked their socials.

[Ersei 'n Stuff][16]

_💬 I didn't think I would see such a fringe use case for Linux, but, here we are. What about you?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-on-google-drive/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Network_File_System
[4]: https://www.techspot.com/news/103652-developer-somehow-got-entire-os-running-google-drive.html
[5]: https://news.itsfoss.com/content/images/2024/07/Arch_Linux_On_Google_Drive.png
[6]: https://ersei.net/en/blog/fuse-root
[7]: https://www.google.com/drive/
[8]: https://en.wikipedia.org/wiki/Filesystem_in_Userspace
[9]: https://www.linuxfromscratch.org/blfs/view/svn/postlfs/initramfs.html
[10]: https://github.com/dracutdevs/dracut
[11]: https://github.com/astrada/google-drive-ocamlfuse
[12]: https://en.wikipedia.org/wiki/Rsync
[13]: https://news.itsfoss.com/content/images/2024/07/Arch_Linux_On_Google_Drive_b.png
[14]: https://en.wikipedia.org/wiki/Hard_link
[15]: https://linuxhandbook.com/symbolic-link-linux/
[16]: https://ersei.net/
