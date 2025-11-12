[#]: subject: "The Self-Hosting Starter Pack: 5 Simple Tools I Recommend To Get Started With Your Homelab"
[#]: via: "https://itsfoss.com/self-hosting-starting-projects/"
[#]: author: "Theena Kumaragurunathan https://itsfoss.com/author/theena/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Self-Hosting Starter Pack: 5 Simple Tools I Recommend To Get Started With Your Homelab
======

[![Warp Terminal][1]][2]

In my last column, [Ownership is an illusion, unless you self-host][3], I encouraged readers to go down the self-hosting path. My thesis was simple: ownership of digital assets (movies, music, games, books, software) is an illusion, and that the only way to move away from this make-believe was to embrace self-hosting.

For people like me, non-programmer types, this is easier said than done: Free and Open Source ([FOSS][4]) can seem intimidating because often (not always) FOSS asks you to embrace granular control over convenience and ease-of-use.

![The author's server, a repurposed 14 year old ThinkPad, ©Theena Kumaragurunathan, 2025][5]

When non-tech people see my server (an old ThinkPad T420) nestled in my book-shelf, running ‘bpytop’ of all things, they assume that I am engaged in some hackery: ‘What is this Matrix shit?’, a friend once wondered. When I told him that it was nothing more than a file-server for my media (movies, music and books), and then showed him my [Jellyfin][6] instance running inside my browser, I could see he was having a lightbulb moment:

_‘Can you do this for me?’_

Sure, I told him, but I offered him a better choice: ‘I’ll show you what you need to know in order to do this yourself, and then we will create a media server for you together.’ Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime, right?

That journey with my friend took us from basics Linux commands to installation of Plex/Jellyfin, which is well beyond the scope of this article (let us know if that is something you are interested in, non-techie/programmer readers). Instead in this column, I will offer an abdridged version.

### Ask yourself why you need this

I had a clear motivation to go down this path during the pandemic: I wanted to backup my media collection of music and run it off Plex Server. My friend wanted to self-host his movies so that he didn’t have to wade through his hard-disks when selecting a movie to watch.

What is your motivation?

### What you need to get started on the homelab bandwagon

**An old computer or laptop**. This needs to be in working order. Mine is an old ThinkPad T420 (which is 14 years old, and I am its 3rd owner). Anything from the last decade and a half ought to do. **You can also get a Raspberry Pi**. I would also prefer an older machine with an ethernet port; connection stability is better when your server has a wired connection to your network in my experience.

**Pick an operating system** : I chose Debian server. You can host many of the applications listed below on a Windows install too, but your mileage may vary. If you want an even easier way, try the [YunoHost Linux distro][7].

![The author's self-hosting stack, ©Theena Kumaragurunathan, 2025][8]

### Start your homelab by self-hosting these software

You don't have to deploy all the recommendations. Think about which one would fit your requirements the most. Select it and then deploy it. Once that is successful, try next. One project at a time.

📋

I am not going to include installation and set-up instructions. Those things may differ based on the choice of your operating system as well as hardware. These are just the recommendations to put you on the right track.

#### Jellyfin: Your own Netflix

![Enjoying local movies on TV with Jellyfin][9]

[Jellyfin][6] is your home theater. It organizes movies and shows, fetches artwork, and streams to TV, browser, and phone. I chose Jellyfin [media server software][10] because setup is simple. On Debian or Ubuntu, you can use the official guide, or run it with Docker and point it at your media folders. It has no subscriptions and no tracking.

💡

Keep your server on wired ethernet for stable playback, and enable hardware transcoding only if your CPU or GPU supports it.

#### Kavita: Your own Kindle library

![The author's instance of Kavita running on his local server, ©Theena Kumaragurunathan, 2025][11]

[Kavita][12] is a self hosted library for books, PDFs, comics, and manga. It has a fast reader, rich metadata, OPDS, and good user management. I use it to keep my EPUBs and essays in one place with clean reading progress across devices.

💡

Sort files into clear folders, let Kavita watch those folders, and enable OPDS if you read on third party apps.

#### Nextcloud: Your own Google drive

![][13]

[Nextcloud][14] is your personal file cloud. Sync your files, share links, and extend it with Notes, Calendar, and Contacts. It feels like a private Dropbox that runs on your hardware. The server has regular releases and clear upgrade docs. If you are new, use the web installer or Docker and start with Files before adding apps.

💡

Keep it simple. Install Files first, set up the desktop client, and only add one or two apps after you are comfortable.

#### Immich: Your own Google Photos

![][15]

[Immich][16] is a private photo and video backup with mobile apps on Android and iOS. It does face recognition, search, albums, and multi user support. It is fast and designed for large libraries. Installation is straightforward with Docker Compose. Begin with the official site, then the server and apps.

💡

Turn on automatic mobile backup, keep originals on the server, and use albums for curation.

#### Navidrome: Your own Spotify

![][17]

[Navidrome][18] turns your music collection into a streaming service. It indexes quickly, supports Subsonic clients, and runs well on modest hardware. You can use a single binary or Docker and attach your music folder.

💡

Install ffmpeg for transcoding, clean your tags for better library browsing, and test a few clients until one fits your flow.

### Putting It Together

A practical starter map looks like this. Jellyfin for movies and shows. Kavita for books and PDFs. Nextcloud for files and sharing. Immich for your photos. Navidrome for music. Run all five on Debian server or YunoHost or on Docker if you prefer containers. Keep your server on wired Ethernet. Back up the data folders in your home network.

Start with one service, get comfortable, then add another. The point is not perfection. It is owning your library and making it available to the people you care about, without asking permission from a platform that can lock you out at a whim.

Enjoy your home lab 🏠🥼

--------------------------------------------------------------------------------

via: https://itsfoss.com/self-hosting-starting-projects/

作者：[Theena Kumaragurunathan][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/theena/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/digital-content-ownership-illusion/
[4]: https://itsfoss.com/what-is-foss/
[5]: https://itsfoss.com/content/images/2025/10/WhatsApp-Image-2025-10-25-at-13.05.59-3-1.jpeg
[6]: https://jellyfin.org/
[7]: https://yunohost.org/
[8]: https://itsfoss.com/content/images/2025/10/Screenshot-2025-10-24-at-20.08.17-1.png
[9]: https://itsfoss.com/content/images/2025/11/image-5.png
[10]: https://itsfoss.com/media-server-software/
[11]: https://itsfoss.com/content/images/2025/10/Screenshot-2025-10-27-at-20.44.35.png
[12]: https://www.kavitareader.com/
[13]: https://itsfoss.com/content/images/2025/11/nextcloud-files.webp
[14]: https://nextcloud.com/
[15]: https://itsfoss.com/content/images/2025/11/immich-self-hosted-photos.webp
[16]: https://immich.app/
[17]: https://itsfoss.com/content/images/2025/11/navidrome-sample.webp
[18]: https://www.navidrome.org/
