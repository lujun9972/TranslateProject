[#]: subject: "Microsoft Teams Alternative Zulip 9.0 Releases With Redesigned Compose Box"
[#]: via: "https://news.itsfoss.com/zulip-9-0-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft Teams Alternative Zulip 9.0 Releases With Redesigned Compose Box
======
Zulip 9.0 adds subtle improvements and a better user experience.
[![][1]][2]

Those who have used [Zulip][3] know that it's a very reliable open-source alternative to the proprietary likes of Microsoft Teams and Slack, which doesn't aim to thrive on its user's data.

Designed to be as intuitive as possible, it's meant to be built around making conversations less chaotic and stressful, while also offering flexibility and extensibility to those who need it.

In a recent announcement, the developers have introduced a new release that features a wide range of improvements and upgrades. So, let's check those out.

## 🆕 Zulip 9.0: What's New?

![A screenshot of the Zulip development community's Zulip installation][4]

Being a major release, Zulip 9.0 has arrived with **over 5,300 new commits** when compared to 8.0, and **has seen more than 120 people contribute to it** , who improved the code and added new things to it.

As for the key highlights of this release, we start with the **simplified user onboarding experience** that now has things like a new permanently dismissible banner for explaining common operating situations on Zulip.

An example would be a small prompt to direct a user to use the back button on their browser or desktop app to go back to a page when viewing a conversation, with a “ _Got it_ ” button to dismiss it permanently.

![][5]

Then there is the more obtrusive prompt to introduce users to their inbox when they first log in, with the developers updating the introductory messages to better explain the various elements of Zulip.

They have also brought about some **new integrations** for [Patreon][6], [Grafana][7], [GitHub][8], and [GitHub Sponsors][9].

![][10]

Similarly, the **message composing has received many refinements** that see a redesigned compose box being introduced, which brings improved clipboard paste behavior. This has resulted in Zulip preserving formatting for things like links, bold, italics, bulleted lists, and more.

Draft behavior sees a boost as well, with Zulip now automatically showing the most recent draft for the selected conversation.

There's also a new “[ _Reactions view_][11]” to check how other people have reacted to a message with emoji reactions.

![][12]

The **reading experience with Zulip 9.0 is a noticeable upgrade** over previous releases. Now, the fonts are larger and there's better line spacing to make reading text easier on the eyes.

Users can also choose to hide the left and right sidebars for a more focused reading experience. When those are hidden, the keyboard can be [used][13] to move around the app.

Fans of the old design can switch to the “[ _compact mode_][14]” from the settings menu. The developers have mentioned that they plan to add controls for changing font size and line spacing with the next major release.

![][15]

For admins, **the user management has been enhanced** by the combining of the user settings panel to allow for one-stop management of current users, deactivated users, and invitations.

**Channel administration sees changes** too, with the channel creation process now being more intuitive, and the channel settings showing additional details, including when it was set up.

### Other Changes & Improvements

There are a few other notable updates that you should be aware of:

  * A number of new keyboard shortcuts.
  * Redesign of all the menus for a clean look.
  * The “ _Streams_ ” feature being renamed to “ _Channels_ ”.
  * Various enhancements to improve the efficiency of the code.
  * Support for Ubuntu 24.04 being added, and Ubuntu 20.04 removed.
  * Zulip server now showing previews of uploaded images in the message feed.



The **mobile apps for Zulip are also set to receive a revamp** later this year, for information on that, and the next major Zulip release, you should go through the [release blog][16].

**Suggested Read** 📖

![][17]

## 📥 Download Zulip 9.0

For access to Zulip 9.0, you can sign up for a free organization account on the [official website][3] to host an instance on Zulip's servers, sign up for one of the [paid plans][18], or self-host it.

If you go the self-host way, then the [documentation][19] is a must-read, with the required packages being available on [GitHub][20].

[Zulip 9.0 (GitHub)][20]

However, if you simply want to see the 9.0 release in action, then you can visit Zulip's [development community][21], which is running the release. You can optionally sign up for an account if you want a more comprehensive experience.

**For existing users** , they can follow the official [upgrade guide][22] and [upgrade notes][23] to get their servers up and running with this release.

_💬 Are you looking forward to implementing this on your existing Zulip server instance?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/zulip-9-0-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://zulip.com/
[4]: https://news.itsfoss.com/content/images/2024/07/Zulip_9.0_a-1.jpg
[5]: https://news.itsfoss.com/content/images/2024/07/Zulip_9.0_b.jpg
[6]: https://zulip.com/integrations/doc/patreon
[7]: https://zulip.com/integrations/doc/grafana
[8]: https://zulip.com/integrations/doc/github
[9]: https://zulip.com/integrations/doc/githubsponsors
[10]: https://news.itsfoss.com/content/images/2024/07/Zulip_9.0_c.jpg
[11]: https://zulip.com/help/emoji-reactions#view-your-messages-with-reactions
[12]: https://news.itsfoss.com/content/images/2024/07/Zulip_9.0_d.jpg
[13]: https://zulip.com/help/keyboard-shortcuts#navigation
[14]: https://zulip.com/help/font-size
[15]: https://news.itsfoss.com/content/images/2024/07/Zulip_9.0_e.jpg
[16]: https://blog.zulip.com/2024/07/25/zulip-9-0-released/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[18]: https://zulip.com/plans/
[19]: https://zulip.readthedocs.io/en/stable/production/install.html
[20]: https://github.com/zulip/zulip/releases/tag/9.0
[21]: https://chat.zulip.org/
[22]: https://zulip.readthedocs.io/en/stable/production/upgrade.html
[23]: https://zulip.readthedocs.io/en/stable/overview/changelog.html#upgrade-notes-for-9-0
