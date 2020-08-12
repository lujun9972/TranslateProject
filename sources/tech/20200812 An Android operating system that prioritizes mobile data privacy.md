[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (An Android operating system that prioritizes mobile data privacy)
[#]: via: (https://opensource.com/article/20/8/privacy-android)
[#]: author: (Don Watkins https://opensource.com/users/don-watkins)

An Android operating system that prioritizes mobile data privacy
======
Meet /e/, a privacy-focused, Android operating system independent of
Google.
![Android security and privacy with a lock][1]

Android and iOS devices are notorious for uploading your personal data to their cloud services without your permission. If you are concerned about your mobile data privacy, you have another option to consider for your next smartphone: the [/e/ operating system][2], a free and open source, Android-based operating system. The eFoundation community is led by [Gaël Duval][3], a legacy Linux developer and entrepreneur who founded Mandrake Linux in 1998.

Gaël has been passionate about computers since he was 10 years old. He has a degree in software engineering and started his career by creating Mandrake (which later became [Mandriva][4]) as a Linux distribution that catered to end users. Mandrake was a Red Hat Linux-based distribution that featured a graphical user interface by default, was easy to use, and focused on the desktop experience.

I recently communicated with Gaël to learn more about why he created /e/ and what it offers that mainstream mobile operating systems don't.

### How /e/ came to be

Gaël says Android sends 12MB of personal data per day to Google servers, and iOS sends 6MB per day to Google servers. Personal data is harvested from billions of users around the world and is used to market services back to them.

His motivation to create /e/ was "very simple: a few years ago, I realized that I had no other real choice than Android and iOS on smartphones," he says. He believes users need a privacy-oriented alternative that better reflects their values and offers a more ethical arrangement. The [unusual spelling][5] aims to mimic the company's logo symbol in text and means “my data is MY data.”

He continues, "I started to figure out all the bricks we could use to recreate a credible and consistent mobile ecosystem that would include a mobile OS and various online services without sending any data to Google or any other 'net giant." This was extremely difficult, he says, because Android is full of dependencies to Google services, and creating a consistent user experience takes a lot of time and energy.

The result of his efforts is [/e/ OS][6], an open source, Android-based mobile operating system that is currently in [beta][7]. It is a fork of [LineageOS][8] and Android, and the custom firmware was developed by the eFoundation. According to Gaël, "/e/ OS is truly [de-Googled Android][9] with all the associated online services of an email address, cloud, metasearch engine, and more."

### How to get /e/ OS

Gaël says /e/ is currently supported on more than 90 [smartphones][10], and "you can install /e/ OS on your smartphone as soon as it is supported." For some time, the eFoundation has been selling refurbished smartphones with /e/ OS pre-installed, and it expanded its lineup in May 2020 with the [Fairphone 3][11], a brand-new device that comes with /e/OS installed. Presently, it is available only in [Europe][12]. However, there is a strong possibility that two different models will be available in the US by the end of the year. According to Gaël, "the constraints are LTE bands support" and to find a partner that can source enough devices to meet the high demand.

The /e/ OS includes a selection of pre-installed applications, including mail, messaging, web browsing, file access, office tools, calendar, notes, and more. In some instances, these apps are modified to provide a better user experience on /e/ and make them run more consistently with other applications on the phone. "Most of the applications are open source, except the Maps app," Gaël says. Also, "/e/ OS can run most Android applications, and we have an app installer with about 80,000 applications available."

Data is stored on the smartphone and in the cloud at ecloud.global. The cloud service, which currently has more than 15,000 user accounts, provides up to 1GB of free storage and uses Nextcloud, OnlyOffice, Postfix, and Dovecot. Regarding the privacy of users' data in the cloud, Gaël says, "our business model doesn't rely on users' data, so we would have no interest in accessing /e/ users' data. That is based on confidence." He says /e/ plans to introduce more end-to-end encryption options for the cloud once some technical challenges are solved. Users are also free to host their own cloud setups if they're concerned about ecloud's trustworthiness.

### Get involved

Many people are participating in the /e/ community, and the foundation is actively looking for more developers for the project. Gaël says new projects are underway that are linked to mobile applications and independent notification frameworks.

All of /e/'s [source code][13] is available, and there have already been several thousand downloads of /e/ OS. To learn more, you can participate in the [community forums][14], follow eFoundation on [Twitter][15], and follow Gaël Duval on [Twitter][16] and [Mastodon][17].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/privacy-android

作者：[Don Watkins][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/don-watkins
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/android_security_privacy.png?itok=MPHAV5mL (Android security and privacy with a lock)
[2]: https://e.foundation/
[3]: https://www.linkedin.com/in/gaelduvalprofile/
[4]: https://en.wikipedia.org/wiki/Mandriva_Linux
[5]: https://www.indidea.org/gael/blog/leaving-apple-and-google-e-is-the-symbol-for-my-data-is-my-data/
[6]: https://en.wikipedia.org/wiki//e/_(operating_system)
[7]: https://doc.e.foundation/faq#is-e-stable
[8]: https://lineageos.org/
[9]: https://ecloud.global/s/ERdy6A5d8PSQjbC#pdfviewer
[10]: https://doc.e.foundation/devices/#smartphones-list
[11]: https://esolutions.shop/shop/e-os-fairphone-3/
[12]: https://www.indidea.org/gael/blog/why-dont-e-smartphones-ship-yet-to-the-usa/#more-1408
[13]: https://gitlab.e.foundation/e
[14]: https://community.e.foundation/
[15]: https://twitter.com/e_mydata
[16]: https://twitter.com/gael_duval
[17]: https://mastodon.social/@gael
