[#]: subject: "Spacedrive: A Dreamy Rust-Based Open-Source File Manager to Fix Your File Mess"
[#]: via: "https://news.itsfoss.com/spacedrive/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Spacedrive: A Dreamy Rust-Based Open-Source File Manager to Fix Your File Mess
======
My search for the perfect file manager ends with Spacedrive.
[![][1]][2]

If you are someone who primarily uses a graphical user interface on Linux, a [file manager][3] is a handy thing to have, as such tools make managing files and folders an effortless task.

On the other hand, if you are a terminal enthusiast, you are better off with one of the [many terminal file managers][4] that can be wielded for powerful file organization.

Here, I test out **Spacedrive** , a privacy-focused open-source next-gen file manager aimed at the creative types such as filmmakers, streamers, musicians, and designers.

Of course, it is not limited to them; anyone can use it if they like what it has to offer. Let's check it out. 😃

🚧

This application is under heavy development, and features are bound to be added or removed.

### Spacedrive: Overview ⭐

![Spacedrive's overview page.][5]

Powered by a Virtual Distributed Filesystem (VDFS), **Spacedrive makes use of a decentralized database** that emulates a filesystem, resulting in efficient organization and searching of files.

Offered under the [AGPL-3.0 License][6], Spacedrive has a PRRTT stack, with technologies like [Prisma][7], [Rust][8], [React][9], [TypeScript][10], and [Tauri][11] making it all happen.

Interestingly, the project is funded by many well-known investors and is supported by a dedicated [team][12] of professionals, along with **more than 100 open-source contributors**.

The project **intends to make money by offering a range of optional services** , like hosting, in the near future, while keeping the Spacedrive app free and open-source forever.

As for the **key features** of Spacedrive, they include:

  * **Unified Search**
  * **Cross-Platform**
  * **Tabbed Browsing**
  * **Intuitive Interface**



### Initial Impressions 👨‍💻

On a [Linux Mint 22][13] config, I installed the .deb package for Spacedrive 0.4.2, and only tested the local features of Spacedrive.

📋

There are many device-to-device and server/cloud-focused features that I could not test at the moment.

On the first launch, a quick setup wizard started up, welcoming me into Spacedrive. When I proceeded, I was prompted to create [a library][14] **** that would store information about the files, but not the files themselves.

This helps with organizing and finding files quickly, even across multiple devices.

![Spacedrive's quick setup wizard.][15]

I then added the locations I wanted Spacedrive to show, and proceeded to **the telemetry section, which was compulsory**. I could either choose “ _Share anonymous usage_ ”, which would send all the relevant data over to the developers, or “ _Share the bare minimum_ ”, which would send limited data back to them.

Both of those are governed by Spacedrive's [privacy policy][16].

![Spacedrive's grid and list view layouts.][17]

After I was done setting it up, Spacedrive showed me my files in the default “ _Grid View_ ” layout, which is what I usually go with. The second one was “ _List View_ ” layout, which, as the name suggests, lists out all the files and folders.

![Spacedrive's media viewer.][18]

There is also a cool-looking “ _Media View_ ” layout, which focuses on showing only media files like photos, videos, music, etc. It comes with an easy-to-use media viewer that allows quick viewing of media files.

![Spacedrive's file viewing controls.][19]

At the top, there are controls to search for files, sort the arrangement of files/folders, change the item size, the gap between them, modify the double-click behavior, and toggle some interface elements.

![Spacedrive's file/folder tagging feature.][20]

I could also **add tags to files or folders** for easy organization, with the thumbnails that Spacedrive shows for files being quite helpful. The right-click menu is filled with many other useful options too.

![Spacedrive's file deletion dialog and recent jobs list.][21]

The file deletion dialog was something different, with it asking me if I wanted to permanently delete something, or just move it to the Trash. There is also **a “Recent Jobs” dialog** , which can be accessed from the button at the bottom-left of the app. It shows all the recent actions taken with Spacedrive.

When **I went into the settings** , I found an entry for **Spacedrive Cloud** , which was not fully functional, as the disclaimer shows. In the [release notes][22] for the 0.4.2 release, the developers mention that cloud sync and peer-to-peer (P2P) capabilities are in the works with an upcoming release.

![Spacedrive settings menu.][23]

There were other settings that I didn't really touch, except the Appearance menu, which had handy options to switch between light and dark mode, with toggles for language, date/time format, and the default Explorer view.

In my use of Spacedrive, I was **impressed with how refined it felt, and the organization options it offers,** at such an early stage in development.

And, I can't wait for its stable release to start using it over my distribution's default file manager! 🤩

💡

The developers have confirmed that ****they are working on bringing Spacedrive to smartphones**** , with Alpha releases for Android and iOS set to be introduced with the upcoming Spacedrive 0.5 release.

### 📥 Get Spacedrive

Currently, Spacedrive is available for **Linux** , **Windows** , and **macOS** ( _Intel & Apple Silicon_). You can grab the latest release from the [official website][24] or from its GitHub [releases][25] page.

I would've liked it if the developers provided additional packages for Linux like Flatpak, RPM, etc. instead of only DEB. But, that is okay for now, as the app is still under development.

[Spacedrive][24]

If you are more into the code side of things, you should consider visiting the project's [GitHub][26] repo, where you will find an active community of contributors working on making Spacedrive the best it can be.

**Suggested Read** 📖

![][27]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/spacedrive/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/file-managers-linux/
[4]: https://itsfoss.com/terminal-file-managers/
[5]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_a-1.png
[6]: https://www.gnu.org/licenses/agpl-3.0.en.html
[7]: https://prisma.io/
[8]: https://rustlang.org/
[9]: https://reactjs.org/
[10]: https://typescriptlang.org/
[11]: https://tauri.app/
[12]: https://www.spacedrive.com/team
[13]: https://news.itsfoss.com/linux-mint-22-release/
[14]: https://www.spacedrive.com/docs/product/guides/library-setup
[15]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_b-1.png
[16]: https://www.spacedrive.com/docs/product/resources/privacy
[17]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_f.png
[18]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_h-1.png
[19]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_i-1.png
[20]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_k.png
[21]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_l-1.png
[22]: https://www.spacedrive.com/docs/changelog/alpha/0.4.2
[23]: https://news.itsfoss.com/content/images/2024/09/Spacedrive_n.png
[24]: https://www.spacedrive.com/
[25]: https://github.com/spacedriveapp/spacedrive/releases
[26]: https://github.com/spacedriveapp/spacedrive
[27]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
