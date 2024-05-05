[#]: subject: "4 Tools to Share Large Files Over the Internet Securely"
[#]: via: "https://itsfoss.com/share-large-files-tool/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 Tools to Share Large Files Over the Internet Securely
======

[![Warp Terminal][1]][2]

We have various [privacy tools][3] to enhance our web browsing. All those tools available, open-source or not, make up for a safer experience.

Sure, it depends on our use-cases, on what privacy-focused tool we choose to use. But, it is good to know that we have options, right?

One such use-case we tackle here is — **sharing large files over the internet**. So, how do you do that?

Well, the good news is: **we have some suitable options** to let us securely share files over the internet 🎉

**But, what signifies as a big file?** Any file that you cannot seem to send through an encrypted messaging app like Signal or Telegram's secret chat. Ideally, it should be anything more than 1 GB.

Let me highlight the tools I picked.

**Suggested Read 📖**

![][4]

### 1\. Internxt Send

![][5]

A familiar ring to Firefox Send? Yes.

[Internxt Send][6] is a nice alternative to the short-lived Firefox Send service. It is an open-source web-based solution.

You can send files up to 5 GB at a time, and the connection is end-to-end encrypted. And, no, you do not need an Internxt account to send files. You just head to the Internxt Send page on any device and start uploading/sharing the file.

Though, I should tell you to check out Internxt cloud storage as well, they offer pretty good lifetime deals like pCloud, and as a bonus, it is end-to-end encrypted + open-source.

[Internxt Send][6]

### 2\. OnionShare

![][7]

I believe [OnionShare][8] is the best open-source tool to securely share files with anyone over the internet.

No one stores the file, you do not upload it anywhere. The tool helps you establish a P2P end-to-end encrypted connection powered by the Tor network. Unfortunately, it needs you to communicate with the receiver (opt for a secure medium) to set up OnionShare to get the file, and it is not as simple as just clicking on a link and downloading the file.

However, the little inconvenience is worth it for optimal privacy and security when sharing a file. You can utilize OnionShare for all kinds of use-cases, personal or professional.

**It is available for Linux, Windows, macOS, Android (beta), and iOS.**

[OnionShare][8]

### 3\. Gokapi (self-hosting)

![][9]

Want to build your own Firefox Send? Well, [Gokapi][10] is an interesting open-source project that lets you make one.

The only catch with this concept is: only the admin (you) can upload the files, you cannot present it as a service that others can use.

It makes sense to me. If you are a user who loves self-hosting things and wants to share a big file with end-to-end encryption, you can achieve that using Gokapi without needing to trust any third party with your data.

[Gokapi][10]

🚀

Easily run your own instance of Gokapi and many other favorite Open Source software effortlessly in the cloud with PikaPods! [Start free with $5 welcome credit][11] 😎

### 4\. Wormhole (Not FOSS)

![][12]

[Wormhole][13] is a proprietary web-based tool that you can also use as a Firefox Send alternative.

If you want to send files larger than 5 GB (which is the upper limit for Internxt Send currently), you can opt for Wormhole. It supports sending files up to **10 GB** in size.

They offer end-to-end encryption, and focus on the speed of transfers. If you are regularly using a service like this, you can compare it to Internxt Send, and pick one of them if you prioritize speed (and if it does make a difference).

[Wormhole][13]

### Don't forget your regular cloud storage service

Yes, if you have a cloud storage account (even under a free tier), you must have 5-10 GB of free space at the very least, right?

If you do, you can use the cloud storage to upload the file (that you want to share), and then make it available to the recipient through a link (or provide them with access to it through email).

Remember that if you would like to make a file available to public downloads (especially, if it's a copyright material) it goes against the terms of service, and shared file link may be removed later.

You can utilize any of the [cloud storage services][14] from our list:

![][4]

📢 It's an [affiliate][15] offer, but I don't want you to miss something like this, so I should tell you that you can get [lifetime storage on Internxt through our link here with an 80% discount][16] (we get a commission if you make a purchase):

_*Interxt is an open-source, privacy-focused cloud storage service, with end-to-end encryption, similar to Proton Drive. It also has 30-day money back gaurantee._

![][17]

### Wrapping Up

[Bitwarden Send][18] is also something that you can use (but it's not for big files), only for documents and text files and that too requires a premium subscription. So, just mentioning it here.

If you are looking to just transfer files from one device to another, we have other [file-sharing tool suggestions][19]. Considering you want to share it over the internet, I think these tools are the best you can use to get the job done.

🗨️ Let me know which service do you use for sharing files over the internet.

--------------------------------------------------------------------------------

via: https://itsfoss.com/share-large-files-tool/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/privacy-tools/
[4]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[5]: https://itsfoss.com/content/images/2024/05/internxt-send.png
[6]: https://send.internxt.com/
[7]: https://itsfoss.com/content/images/2024/05/onionshare.png
[8]: https://onionshare.org/
[9]: https://itsfoss.com/content/images/2024/05/gokapi.png
[10]: https://github.com/Forceu/Gokapi
[11]: https://www.pikapods.com/
[12]: https://itsfoss.com/content/images/2024/05/wormhole.png
[13]: https://wormhole.app/
[14]: https://itsfoss.com/cloud-services-linux/
[15]: https://itsfoss.com/affiliate-policy/
[16]: https://internxt.sjv.io/c/1995707/2001891/14378
[17]: https://internxt.sjv.io/favicon.ico
[18]: https://bitwarden.com/products/send/
[19]: https://itsfoss.com/share-files-linux-windows-mac/
