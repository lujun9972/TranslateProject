[#]: subject: "Meet Roomy: An Open-Source Discord Alternative for the Decentralized Web"
[#]: via: "https://itsfoss.com/roomy-discord-alternative/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Meet Roomy: An Open-Source Discord Alternative for the Decentralized Web
======

[![Warp Terminal][1]][2]

[Roomy][3] is an open-source Discord alternative built on the AT Protocol ([ATProto][4]), the same protocol that powers Bluesky, with [ActivityPub][5] (the protocol behind [Mastodon][6], [Pixelfed][7], [Pleroma][8], and [others][9]) planned for the near future. Currently in alpha, it sits somewhere between Matrix and Discord in terms of its practical position in the broader chat ecosystem.

That said, it aims to fill the niche currently dominated by Discord, while remaining a free, fully federated solution for full user freedom and greater privacy. In this article, we'll look at what Roomy is today, what it’s aiming to become, and what it could bring to this space.

### So what is Roomy, exactly?

![a.room.space, the Roomy website][10]

Right now, Roomy is a browser-based group chat app. Technically, there's no sign-up process: you sign in using any existing Bluesky or ATProto account. The long-term goal is to let you bring your identity with you from any supported Fediverse platform. Once (planned) ActivityPub support is locked in, you'll be able to sign in with Mastodon, Pixelfed, or any other network that uses this protocol.

No matter what protocol you use, you'll be able to access and use the same Discord-style community chat people already understand.

💡

Note: Roomy is developed in the open. To view the source code, report issues, or view the roadmap, head over to the [project's GitHub Page][11].

#### Why does it exist?

There's a well-known, but unspoken rule in tech: if a proprietary platform exists, inevitably there will be an open-source alternative, and this isn't happenstance. Freedom isn't guaranteed when someone else holds the keys.

With Discord having become pretty much the unofficial standard among online communities, even many open-source communities depend on Discord spaces for their day-to-day needs. However, Discord is still a closed platform.

Sure, there are many open-source, third-party clients, but there's still a need for platforms that are open from the ground up. Roomy is one among many, yes, but it's targeting a critical niche that's so far been hard for other apps to crack.

#### A Decentralised Platform for Bringing People Together

![The first run experience on roomy.space, the main public instance.][12]

Roomy's basic goal is the same as any chat app: bring people together, with a stated focus on accessibility and safety. From that standpoint, once the basics are stable, you could stick a bow on it and call it done. However, Roomy’s ambition is to be way more than just an open-source Discord clone.

Its core promise is community chat on top of decentralized platforms, using open protocols to keep identity continuous without a single company being the glue. Roomy also aims to bridge a gap between social media platforms (Mastodon, Pixelfed, Bluesky, and others) and live chat - where people actually organise, collaborate, and build relationships in real time.

#### Where Roomy fits: Between Discord and Matrix

Roomy is easiest to understand when you place it beside the two reference points you’re already using:

  * **Discord:** centralised, polished, and effectively the default for communities, but closed, platform-owned, and ultimately controlled by one company.
  * **Matrix:** open protocol, federated network, and flexible in how you host and connect, but UX and onboarding vary heavily depending on server, client, and room setup.
  * **Roomy:** aiming for Discord-style community chat, but with protocol-first identity and a local-first mindset. It is still alpha and missing a lot of the essentials that make large communities viable.



### Standout idea: Portable content

![Image by Lucent_Designs_dinoson20 from Pixabay][13]

A cool feature of Roomy is that content isn’t locked into one format: Messages can be converted into threads, threads into channels, and channels into pages. Not all of these conversions are reversible, but having this feature in the first place is definitely a unique feature. It's a clear indicator that Roomy isn’t just trying to clone Discord’s interface. Rather, it's a rethink of how community knowledge and conversation evolve over time.

In theory, this feature could be useful for making chat logs available through standard federated social platforms, like Mastodon, or on (for instance), Nextcloud. This would dramatically increase the surface for community collaboration.

### Why building on open protocols matters

![Image by Heinz Schmitz from Pixabay][14]

Protocols are the backbone of network technologies, including the internet, though most are invisible to us today. Every time you type [itsfoss.com][15] into your browser, you’re using HTTP or HTTPS. Every time you send an email, you're using that protocol as well. Essentially, protocols are (typically open) standards that govern how different pieces of software communicate.

All chat apps rely on protocols, but many of the popular apps we use today use proprietary protocols that are under the control of a single entity. For many of us, this aspect of our communication doesn't seem like a big deal, but the reality is that it matters tremendously who controls the protocols we use, and what they can do with them.

Most proprietary systems use their own, private gateways, protocols, APIs, and other technologies. While some expose and/or document parts of their ecosystem, the core typically remains under their control, hidden from the public. This sounds great for security, but it comes at a major cost: You can't know what the one who holds the keys is doing with your data. This leaves communities wholly dependent on platforms they don’t control, using identities they technically don't truly own.

#### Roomy proposes to change this through open protocols

![Logging into Roomy][16]

The substantive element to Roomy's appeal is its reliance on open protocols. By using standardised identification, routing, and authentication, it eliminates the barriers that lock us out of cross-platform communication. It's a similar promise to what XMPP has done in the world of instant messaging.

Conceptually, this puts Roomy in similar territory to Matrix, but what sets it apart is portability: (in theory) you'll be able to use any existing identity on the Fediverse, and take conversations from chat, to social media timeline, and beyond.

#### How decentralisation shows up in Roomy

On the internet, decentralisation can mean very different things, depending on the project. Roomy’s developers [describe it][17] as storing data on your ATProto Personal Data Server (PDS), while also keeping a local copy in the browser and syncing changes over time. In this model, your community content doesn't live inside one company’s database. It's decentralized, because no one location holds the "ultimate data".

#### The not so small catch

![Pexels / Mido Makasardi ©️][18]

An important caveat to Roomy's model lies in how it uses ATProto PDSs. Data is in a place where anybody in the world can download it, and the ATProto PDS doesn’t let Roomy store private data. As such, Roomy is _**not**_ yet a private, secure chat solution by default.

To reduce risk, Roomy encrypts direct messages, but the developers describe this encryption as experimental and unaudited, and warn that metadata can still be visible. Until these issues are resolved, Roomy is best seen as an interesting concept, but shouldn't be trusted with sensitive data.

### Reality check: What works vs what’s planned

![Creating a space in Roomy][19]

Okay, so Roomy sounds like an ambitious idea and if successful, it would certainly be a meaningful addition to the overall community-building ecosystem. But beyond basic text chat, what's actually usable right now, given its early development?

#### What's already working:

![Editing a page in Roomy][20]

**In a nutshell:** enough to get an idea of where it's going, but not enough that you can dive into the full experience just yet.

  * **Spaces and Channels:** Both work as core organising units. Spaces can be edited after creation (name, description, and other basic properties), but channel editing isn't implemented yet.
  * **Invitations:** You can generate invite links for spaces, and anyone with a Bluesky account can login and join.
  * **Pages:** You can convert channels to pages, which still function as chat rooms, but allow for a kind of shared document space. Images don't work in pages for some reason, though the UI allows you to add them.
  * **Threads:** You can convert any message or channel into a thread (ala Slack, Mattermost, & Matrix). Threads can't be removed or edited, only converted to a channel.
  * **Media uploads:** Roomy allows you to upload common image formats (PNG, WEBP, JPEG, SVG), as well as videos in the MP4 format. I tested images only, with no issues except on pages. No file size limit is mentioned anywhere in the UI.



Roomy already leans into the promised concept of content fluidity, even if the user experience is still rough around the edges. In my testing, I was able to create and join a space, send messages and upload images.

Creating a space is simple and intuitive: Click the plus icon, enter a space name, and optionally add an avatar and description. There’s also a discoverability option, but it's currently disabled. Once you're done, you just click "Create Space", and you're in. If you'd like to try it for yourself, you can head over to [**roomy.space**][21] and sign in with your Bluesky or ATProto account.

⚠️

****Important:**** Roomy is very much __alpha quality__ software.

You can keep an eye on it, and test features, but keep in mind that it’s changing quickly, may introduce breaking changes, and shouldn't be treated as a hardened or privacy-first chat yet.

#### What’s planned, incomplete, or unclear

![You can add images to Roomy pages when editing, but they disappear the moment you save][22]

Being in alpha quality at this time, Roomy is not quite ready for mass usage, as there's still work to be done to make it solid enough for real-world usage. However, there are some important features that you may be concerned about:

  * **Robust moderation** : Currently, you can make someone an admin, and admins can remove messages from any individual, but there's no way to remove users from a room. Other moderation features like roles, granular permissions, reporting, anti-spam tools, etc, aren't implemented at this stage.
  * **Emoji support:** You can add emoji reactions, and emojis show in chat, but there's no emoji picker implemented in the chat input box as yet.
  * **Encryption:** Basic encryption exists, but with limits. See [this blog post][23] for more information on these limitations.
  * **Self-hosting:** self hosting is planned, but the current alpha is not yet in a polished, community-ready state. The [README][24] frames it as something they will “soon” support. Installing Roomy for local development is the current focus.
  * **Desktop/mobile apps:** At this time, there are no complete desktop or mobile apps for Roomy, though [GitHub activity][25] indicates that a [Tauri][26] app for Android is under development.



#### Can I use it without a Bluesky account?

Currently, not practically, unless you have an ATProto account elsewhere. The README states that Bluesky login is the default for now, with Mastodon (ActivityPub) and other options planned for the future.

🗒️

Being that this is an early alpha, it should be expected that there aren’t yet any of the bells and whistles you might expect from Discord, like Giphy integration or stickers.

Granted, even if Roomy (as a project) never implements these directly, its open-source nature means anyone could, in theory.

### Why Roomy is more than a Discord alternative

![Roomy is an ambitious undertaking, but a worthwhile effort][27]

It's clear that people want the fun and flexibility of Discord-style spaces, but in an age where privacy and ownership matter more than ever, open-source solutions are becoming nonnegotiable. Roomy has the potential to offer the Discord experience, without the vendor lock-in.

If Roomy succeeds, we won't just gain an open-source Discord clone. The real win will be proving that modern online communities can exist (and thrive) on open protocols, where identity is portable, and the community’s future doesn’t hinge on the kindness of a single company. It's a big promise, but Roomy certainly represents one of the more interesting attempts to get there.

--------------------------------------------------------------------------------

via: https://itsfoss.com/roomy-discord-alternative/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://a.roomy.space/
[4]: https://atproto.com/
[5]: https://activitypub.rocks/
[6]: https://joinmastodon.org/
[7]: https://pixelfed.org/
[8]: https://pleroma.social/
[9]: https://fediverse.party/
[10]: https://itsfoss.com/content/images/2025/12/FireShot-Capture-068---Roomy----a.roomy.space-.png
[11]: https://github.com/muni-town/roomy
[12]: https://itsfoss.com/content/images/2025/11/FireShot-Capture-055-------roomy.space--1.png
[13]: https://itsfoss.com/content/images/2025/12/fiber-4814456.jpg
[14]: https://itsfoss.com/content/images/2025/12/software-8150826.jpg
[15]: https://itsfoss.com/
[16]: https://itsfoss.com/content/images/2025/12/image-22.png
[17]: https://blog.muni.town/roomy-deep-dive/
[18]: https://itsfoss.com/content/images/2025/12/pexels-mjlo-2743739.jpg
[19]: https://itsfoss.com/content/images/2025/11/FireShot-Capture-056-------roomy.space-.png
[20]: https://itsfoss.com/content/images/2025/12/Screenshot-From-2025-12-21-18-46-08.png
[21]: http://roomy.space/
[22]: https://itsfoss.com/content/images/2025/12/image-21.png
[23]: https://blog.muni.town/roomy-chat-alpha/
[24]: https://github.com/muni-town/roomy/blob/main/README.md
[25]: https://github.com/muni-town/roomy/issues?q=is%3Aissue+state%3Aopen+android
[26]: https://v2.tauri.app/
[27]: https://itsfoss.com/content/images/2025/12/Screenshot-From-2025-12-21-19-45-23.png
