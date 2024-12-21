[#]: subject: "Betterbird: A Thunderbird Fork That Promises Better Features"
[#]: via: "https://news.itsfoss.com/betterbird/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Betterbird: A Thunderbird Fork That Promises Better Features
======
A better Thunderbird? Let's take a look!
[![][1]][2]

📜

Must-Know Bits 👇
— Features many long-requested features.
— A more streamlined alternative to Thunderbird.
— Highly customizable, thanks to Add-ons and Themes.

* * *

Handling emails is an important task if your business or work depends on it. No matter how many [messaging apps][3] take over official/unofficial communication channels, emails will always be a thing.

[Email clients][4] are particularly useful if you interact with emails regularly, acting as a one-stop solution that allows a user to manage and organize their email accounts from a single application. Plus, having offline access to one's emails is always a good thing.

For this week's app, we have **Betterbird** , an open source email client that's a fork of [Thunderbird][5]. It aims to offer an improved experience with extra features and performance enhancements under the hood. Let’s dive in! 😃

### Betterbird: An Email Client On Steroids

![][6]

Based on the [Thunderbird ESR releases][7] for its security and stability, Betterbird is **a soft fork that makes it a point to avoid mistakes that other Thunderbird forks do** by staying close to the patches in upstream.

Its founder, [Jörg Knobloch][8], **was once a key member of the Thunderbird development team** who moved away from the project [due to differences][9] over policy and management.

If you look at the [privacy policy][10] Betterbird software, there is a paragraph where it is explicitly stated that **some user data may be collected by Mozilla** , but it is less than what is collected when using Thunderbird.

**Betterbird itself does not collect or send any data** , including telemetry or crash reports. However, it does download add-on updates and blocklists from Mozilla sites.

#### ⭐ Key Features

When compared with Thunderbird, Betterbird has many extra goodies like expanded window layout options, superior message thread handling, and many customization options for power users.

Some notable features include:

  * **System Tray Icon** ( _Linux_ )
  * **Accent Colors** ( _for folders_ )
  * **Multi-line Inbox View** ( _disabled by default_ )



You can refer to the [feature table][11] to get a better overview of the upgrades.

#### 💻 User Experience

I ran Betterbird 128.5.0esr-bb18 on my Fedora 40-equipped laptop and started account setup on an [Outlook][12] email ID to test things out, focusing only on the basics ( _email and calendar_ ).

The **new account configuration was just about what I expected** , with a new web browser window opening up after I entered my credentials. After I confirmed the login with the authenticator app on my smartphone, I had to provide access to the verified “ _Mozilla Thunderbird_ ” app on my Outlook account before it could be added to Betterbird.

![Betterbird's new account configuration flow.][13]

📋

Many screenshots have been edited to hide [PII][14].

Following that, **Betterbird fetched all the relevant email configuration settings automatically from Mozilla's database** ( _IMAP for incoming, SMTP for outgoing_ ), with an option for manual configuration of hostnames, ports, authentication settings, etc.

![Betterbird's new account configuration flow.][15]

After everything was set, Betterbird started fetching all the mails ( _2000+_ ) from my Outlook account, showing **helpful progress status at the bottom of the app**. The mail reading experience is a familiar one, with Betterbird using a horizontally split view by default to show mail contents.

![][16]

Like Thunderbird, **Betterbird blocks the loading of remote content by default** , with the “ _Preferences_ ” button housing options to allow the display of such content. As for the rest of the screen layout, there is a **familiar search bar at the top** , **a sidebar menu with quick-access buttons and folders** , and the “ _Today Pane_ ” (at the bottom-left) that **displays any upcoming events**.

The three-ribbon menu has **handy options to tweak the layout** with many views like _Classic_ , _Wide_ , _Vertical_ , _Wide Thread_ , and _Multi-line_. It also houses toggles to tweak the density and font size of the interface.

Composing an email is routine, too. Just click on the big blue “ _New Message_ ” button to get started. I composed a humorous tale of a cat to send to a friend, and the editing experience was seamless.

![][17]

Similarly, **the Calendar integration worked flawlessly** , allowing me to add new events and tasks with a great deal of control. I could play around with options to Invite Attendees, set the Privacy, add a Category, change the Progress status, and much more.

![Betterbird's calendar tab and task creation feature.][18]

During my testing, **I used Thunderbird 128.5.2esr alongside Betterbird** , and I was surprised to see how alike yet different they were from one another. The default view on Thunderbird is a vertical layout, with the mail opening up on the right-hand side.

However, **Betterbird has a cool system tray icon** that, when enabled, allows me to minimize the app to the tray. This helps reduce clutter while still keeping Betterbird running in the background, allowing me to track emails without the app taking up valuable screen space.

**One thing I’d love to see Betterbird do** is fully embrace its red/orange [Phoenix][19] identity by integrating those vibrant colors into the user interface, replacing the blue accents of Thunderbird.

While I typically don’t use email clients to manage my emails, Betterbird has made me reconsider my approach and sounds like a consideration for an email client on my Linux-powered laptop.

### ⚙️ Installing Betterbird

Users on **Linux** can get the latest Betterbird release from [Flathub][20]. Others can visit the [official website][21] for **Windows** and **macOS** packages.

**Existing Thunderbird users** can follow the official [migration guide][22] to make their transition easy. Additionally, you can find [all the patches][23] that make Betterbird different from Thunderbird on the project's [GitHub][24] repo.

[Betterbird (Flathub)][20]

* * *

[Get It's FOSS Plus Membership][25]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/betterbird/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/best-messaging-apps-linux/
[4]: https://itsfoss.com/best-email-clients-linux/
[5]: https://www.thunderbird.net/
[6]: https://news.itsfoss.com/content/images/2024/12/Betterbird_a.png
[7]: https://enterprise.thunderbird.net/explore/thunderbird-release-cycle#:~:text=Thunderbird%27s%20regular%20yearly,your%20communication%20system.
[8]: https://www.linkedin.com/in/jorgk/
[9]: https://www.betterbird.eu/faq/former.html
[10]: https://www.betterbird.eu/legal/index.html
[11]: https://www.betterbird.eu/#featuretable
[12]: https://www.microsoft.com/en-us/microsoft-365/outlook/email-and-calendar-software-microsoft-outlook
[13]: https://news.itsfoss.com/content/images/2024/12/Betterbird_b.png
[14]: https://en.wikipedia.org/wiki/Personal_data
[15]: https://news.itsfoss.com/content/images/2024/12/Betterbird_e.png
[16]: https://news.itsfoss.com/content/images/2024/12/Betterbird_h.png
[17]: https://news.itsfoss.com/content/images/2024/12/Betterbird_j.png
[18]: https://news.itsfoss.com/content/images/2024/12/Betterbird_k.png
[19]: https://www.deviantart.com/genzoman/art/Phoenix-202798063
[20]: https://flathub.org/apps/eu.betterbird.Betterbird
[21]: https://www.betterbird.eu/downloads/index.php
[22]: https://www.betterbird.eu/support/index.html#switch-tb-bb
[23]: https://www.betterbird.eu/faq/full-changes.txt
[24]: https://github.com/Betterbird/thunderbird-patches
[25]: https://itsfoss.com/#/portal/signup
