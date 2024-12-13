[#]: subject: "My Experience With SimpleX Chat: Is It The Ultimate Open Source Private Messaging App?"
[#]: via: "https://news.itsfoss.com/simplex-chat/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

My Experience With SimpleX Chat: Is It The Ultimate Open Source Private Messaging App?
======
An impressive decentralized open source messaging app that does not
require any user ID.
[![][1]][2]

[Privacy-focused messaging apps][3] are a boon in today's increasingly [authoritarian][4] world, where people's rights are constantly under threat from those in power. Having a secure messaging app ensures that nobody can easily snoop in your private conversations.

Of course, **if your phone is infected with spyware, using such apps won't really help** , but it is still significantly better to go for such options instead of relying on the likes of WhatsApp.

Sadly, many of those privacy-focused messaging apps require you to hand over a phone number or email address to sign up for an account, resulting in [personally identifiable information][5] ( _PII_ ) being transmitted to the service's servers.

That is where **SimpleX Chat** comes in. 🤓

### SimpleX Chat: Overview

![][6]

Thanks to the implementation of one-time use SimpleX addresses, anyone can start using SimpleX Chat without the risk of exposing sensitive PII. **Messages are protected with quantum-resistant end-to-end encryption** , and all user data is stored locally on the user's device.

In terms of networking, **SimpleX Chat relies on a decentralized network of proxy servers** , with messages being routed through SimpleX relay servers, where they are stored temporarily during transmission and deleted after delivery.

There is also **** the option to **enable Tor routing to further enhance privacy**. SimpleX Chat and the protocol behind it are supported by an active community of open source contributors who work on improving the SimpleX ecosystem.

You can learn more about how SimpleX works by reading the [whitepaper][7].

### Here's My Initial Impression

I tested the mobile client for SimpleX Chat on an Android 12 smartphone, with [Ankush][8] helping me out on the other end. I got started by creating a new local account, giving it a name, and generating a SimpleX address so that I could share my account with others ( _which was optional_ ).

![Adding a new contact on SimpleX Chat is easy.][9]

Following that, I added Ankush as a new contact by pasting his SimpleX address into the search bar at the bottom of the app. As he had a feature “Auto-accept” enabled, a generic message automatically popped up that said “ _Thanks for connecting!_ ” when I sent a request.

The Auto-accept option ( _shown in screenshot above_ ) can be accessed from the “ _Your SimpleX address_ ” entry inside the SimpleX Chat menu, which can be found by tapping on the user profile at the bottom-left.

![After adding a contact, using SimpleX Chat feels straightforward.][10]

**Sending messages on SimpleX Chat is easy** , with there being support for sending emojis, reactions, images, videos, and other kinds of files. Tapping and holding on messages shows handy action buttons like reply, share, copy, save, forward, delete, and a specific revoke file option when handling added attachments.

Accepting new connection requests is simple too. Just click on _Accept_ to add the contact into your current account, or use the _Accept incognito_ option for adding the contact to a freshly created SimpleX account. You can reject connection requests too.

Audio calls work well, but **video calls can be a bit buggy** , with no audio coming from one side and the video quality being terrible. Of course, your experience might differ, so be sure to test it out.

![SimpleX Chat has a cool private notes feature, and the chat preferences are very handy.][11]

SimpleX Chat also **allows private note-taking** , similar to what many other messaging apps provide, and I really like that. **I could further tweak my chat preferences** from the app's menu that allowed me to tweak things like disappearing messages, delete for everyone, message reactions, voice messages, etc.

![Adding a new profile picture in SImpleX Chat is straightforward.][12]

Similarly, **adding a profile picture and name to a SimpleX Chat account is possible** , with the app notifying contacts when such changes are made to an account. You can also manage any added contacts by clicking on their name when the chat is open.

There are options to view/verify the end-to-end encryption status ( _via security cod_ e), change contact preferences, change the chat theme, clear the chat, delete the contact, and more.

All the essentials exist.

![SimpleX Chat has a well-equipped settings menu.][13]

When tapping on the Wi-Fi icon at the bottom of the app, **one can see important data related to the connected SimpleX servers** , both current and past. The same section has useful pointers like total messages sent/received, files uploaded/downloaded, and any errors that might have occurred.

The Settings menu houses useful settings like _Appearance_ to personalize the app theme, many privacy settings to further safeguard one's SimpleX Chat experience, and controls for handling import/export of the locally stored chat database.

![SimpleX Chat desktop client running on Fedora 40.][14]

The **desktop client also works well to sync with the mobile client**. I tested it on a Fedora 40 system, and it worked as expected, delivering messages without any delay. You do need an active internet connection on your mobile though.

**I can confidently conclude that SimpleX Chat is everything** [**Signal**][15] **should have been and more**. Its features, usability, and focus on privacy set a new standard for secure communication.

### Install SimpleX Chat

SimpleX Chat is available for Android via [F-Droid][16] and the [Play Store][17]. The desktop and terminal clients for Linux, Windows, and macOS can be downloaded from the [official website][18].

[SimpleX Chat][17]

For the source code, you can visit the project's [GitHub][19] repo, and for the most recent audit of SimpleX Chat, you can refer to the [official blog][20].

* * *

[Get It's FOSS Plus Membership][21]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/simplex-chat/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/private-whatsapp-alternatives/
[4]: https://en.wikipedia.org/wiki/Authoritarianism
[5]: https://en.wikipedia.org/wiki/Personal_data
[6]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat.png
[7]: https://github.com/simplex-chat/simplexmq/blob/stable/protocol/overview-tjr.md
[8]: https://news.itsfoss.com/author/ankush/
[9]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_a.jpg
[10]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_e.jpg
[11]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_g.jpg
[12]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_j.jpg
[13]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_m.jpg
[14]: https://news.itsfoss.com/content/images/2024/12/SimpleX_Chat_p.png
[15]: https://signal.org/
[16]: https://f-droid.org/en/packages/chat.simplex.app/
[17]: https://play.google.com/store/apps/details?id=chat.simplex.app
[18]: https://simplex.chat/downloads/
[19]: https://github.com/simplex-chat/simplex-chat
[20]: https://simplex.chat/blog/20241014-simplex-network-v6-1-security-review-better-calls-user-experience.html
[21]: https://itsfoss.com/#/portal/signup
