[#]: subject: "Fedora Badges Revamp Project: From The Ground Up"
[#]: via: "https://fedoramagazine.org/fedora-badges-revamp-project-from-the-ground-up/"
[#]: author: "Akashdeep Dhar https://fedoramagazine.org/author/t0xic0der/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Badges Revamp Project: From The Ground Up
======

![][1]

.

After years of [technical research][2] and [foundational work][3], the [Fedora Badges application service][4] has been rebuilt from the ground up, and it is heading to production. Whether you have been collecting badges for years or you are brand new to the Fedora Project community, here is what is waiting for you there.

### Completely modernized user interface

The archaic server rendered pages are now gone. The Fedora Badges application service now runs on a modern single page application. This provides you with a much faster and more responsive experience, while functioning across various screen sizes and devices types, all without full refreshes or front-end reloads.

![][5]

Navigations have been revamped as well. But do not worry at all – if you have bookmarked any old service links, they should redirect you to the right place.

### Colour schemes, Dark mode

You can now customize the look of the Fedora Badges application service choosing from eight colour schemes. Your choice flows through the various elements of the front-end – from navbar to borders, from charts to accents, etc. The dark mode and light mode switch respects your system preference and can also be toggled.

![][6]

Your choices are persistent across visits residing in your session storage. As long as the same session is used, the colour schemes and dark mode settings stay.

### Revitalized badges collectathon experience

Not only does the profile page show your precious badges, it also shows a _radar chart_ that maps your collection across categories. This is a rudimentary method to gauge your progress and discover the areas you have not explored yet. Giving a means to diversify the activities, this encourages more people to join in.

![][7]

![][8]

The refreshed history page also adds a _collection time-line_ chart showing yours (and your friends’) contribution activities over months and years at a glance.

### Compare (or compete) with your friends

The renewed _difference page_ lets you compare your badges collection with those of your friends’ possessions. See which badges you both share, which ones only you have, and most importantly, which ones they have earned that you have not yet. It’s a fun way to discover new badges and unearth new ways to contribute.

![][9]

You can also reach out to your fellow community members for potential _mentoring opportunities_ , based on their contribution activities and collected badges.

### Explore badges by rarities

Every active badge now has a _rarity tier_ based on how many users currently hold it:

  * **Fedorable** — Unobtanium stuff
  * **Legendary** — Mythical prestige
  * **Epic** — Serious bragging
  * **Rare** — Principled hustle
  * **Uncommon** — Striving future
  * **Common** — Warm greeting



![][10]

You can now browse active badges by their rarity tiers, making it easy to hunt down the ones that fewer people have earned. Not only does it allow you to find new pathways for contribution, you also get a sense of the _impactful work_ and relevant tracks that are waiting for you in your community activities.

### Involved semantic collective lookup

Departing from different searches for badges and users, the search bar now helps _unified lookup_ across both badges and users. Start typing and results start appearing immediately after – with better lookup results. These will appear when the query is general enough to return more than eight results.

![][11]

To save server resources, the _asynchronous search_ request begins only when at least four characters are entered into the search bar for the query.

### Leaderboards with time navigation

Departing from the restricted _rankings page_ , it is now possible to request custom period filtering on the leaderboards page. Filters can be based on days, weeks, months, and years. One can see who has been earning most badges in those times, and generally look back at the community’s evolving progress over a time period.

![][12]

The rankings are deterministic and can be shared with others, using the sharing link that inherently applies the same filters. This creates a _reproducible resource_.

### Clearer badge activity lifecycle

Badges can now be _manually marked_ as legacy (retired, unobtainable) after they should no longer be awarded to the users. For instance, the badges for joining the Fedora Linux Release Party 42 should no longer be available to new users in 2026. Hence, they should not be accounted for while computing rarity tiers.

![][13]

And nope — we are not taking awarded badges away from users who have already earned them. These retired badges are still going to be visible in the history.

### Stronger foundational supports underneath

You see, the revamp was not just about the front-end. The data layer that powers the application service got a _major overhaul_ as well. The [Database Library][14] project, which handles all database operations, saw 105 commits across 7 contributors during the same period, pushing from version 1.4.1 to 1.5.5.

![][15]

Here’s what changed under the hood, and why it matters to you:

  * **Faster queries** — Redundant database lookups were eliminated, foreign key indexes were added, and pagination now happens at the database level instead of in the application code. Pages that list badges or users load significantly faster, especially as the count of badges or users grow.
  * **Effective lookup** — The search you use from the navbar section is powered by new search methods added to the API. This covers both badges and users. This not only makes the search noticeably faster, but the actual process is also more efficient on a synchronous database accessing layer.
  * **Rarity calculation** — The rarity tiers you see on badge pages are computed every day by an updated algorithm in the API code. Various edge cases are now handled too. The fall-back is set to the common tier on zero available users who own the said badges at that particular time.
  * **Legacy support** — A schema level change was made to introduce a new legacy column to the badges table to distinguish active badges from the retired ones. Filtering is built into the API code so the front-end shows them on separate pages when requested by the users.
  * **Categories normalization** — Badge tags are now stored in their own tables instead of as raw comma separated strings. This makes category browsing reliable.
  * **Cascading deletions** — Removing a badge when done in exigent circumstances now properly cleans up its assertions in the database purging orphaned data.
  * **Removing invitations** — Invitations are soft deleted and not hard removed. This preserves access history while preventing accidental assertions.
  * **Quality assurance** — Nearly every new feature ships with its test cases. Python < 3.9 support was dropped in favor of Python > 3.13.



### Overall smoother authentication events

Authentication has been reworked. The old session-based login has been replaced completely with a modern token-based flow using [OpenID Connect][16]. The application service now has its own dedicated authentication client so logging in through [Fedora Accounts][17] is more consistent across other things.

![][18]

If you are visiting for the first time, like it has been for years, your user account is automatically created without requiring any further steps.

### Your privacy really matters

Email addresses are no longer visible across various API responses. They are hashed before being sent as an _asynchronous response_ , for use by [Libravatar][19]. Users have the choice to opt out of the Fedora Badges application service entirely. In that case they will stop receiving badge awards for their community tasks.

![][20]

RSS feeds are now limited to _recent entries_ for performance and efficiency, so you can still stay informed about the latest incoming activities on the app.

### For badge creators, maintainers, and administrators

If you are a part of the team, the new interface gives you a full set of tools.

  * Advanced database management front-end
  * Creating and revoking awards from your users
  * Creating and expiring invitations for the badges
  * Creating and revoking authorizations from your users
  * Creating and updating badges
  * Creating and updating users



![][21]

Access control is tiered — community members see the _service experience_ , while authorized team members get the _administrative controls_ they need.

### Progress by the numbers

This [revamp][22] (codenamed [**स्वातंत्र्य**][23] or [**Svātantrya**][23]) represents a year of active work across the two repositories. These comprised **165 commits** in [Tahrir][24] and **105 commits** in [Tahrir API][14]. This occurred after many years of [technical research][2] and [foundational work][3] resulting in a leaner codebase with a _net reduction_ of **13,320 lines of code**.

### Thank you to our amazing contributors

I mean it when I say, this revamp would have been dead in the water without the help of the following folks (in the alphabetical order):

  * Akashdeep Dhar
  * Aurelien Bompard
  * Awwal Adetomiwa
  * Chibuezem Marvinrose
  * Daniel Mungai Chege
  * Emma Kidney
  * Gregory Sutcliffe
  * John Iweh
  * Joy Aruku
  * Kevin Fenzi
  * Michael Scherer
  * Michal Konecny
  * Olamide Peter Ojo
  * Payal Sumbhe
  * Shounak Dey
  * Vanshikha Shri
  * Yash Sheorey
  * Xavier Lamien



And those, of course, from Flock 2026’s workshop on the [Fedora Badges Revamp Project][25].

  * Ankur Sinha
  * Cornelius Emase
  * Emmanuel Seyman
  * Guillermo Leiro
  * Jakub Jelen
  * Jona Azizaj
  * Jonáš Hubený
  * Justin Wheeler
  * Mat Holmes
  * Matthew Miller
  * Misia Mary
  * Shawn Dunn
  * Vít Smolík
  * Vittorio Cioe



This revamp project was in a [development hell][26] for quite some time. It was able to come out of it thanks to those listed above and countless others who have helped maintain the project for the past _fourteen years_ or so. It is now time for me to _pass this torch on_ to others who can help maintain this.

The project codebase currently lives on the [Fedora Infrastructure’s GitHub namespace][27]. Please consider [providing feedback][28] and [contributing changes][29] to help maintain the projects. You can also hang out with us in the [Fedora Badges chat room][30] on Fedora Project’s Matrix server to learn more.

### Go on – give it a try!

The production deployment should be live by the time this article is publicly available. Head over to [Fedora Badges][4] to explore the refreshed experience. As it might be a little rough around the edges in the starting days, please bear with us while we hammer down the oddities with your useful reports.

![][31]

Your input influences what comes next to the Fedora Badges application service. Please consider giving it a try right now and let us know what you think!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-badges-revamp-project-from-the-ground-up/

作者：[Akashdeep Dhar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/t0xic0der/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/08/Badge_Revamp-816x345.jpg
[2]: https://fedora-arc.readthedocs.io/en/latest/badges/
[3]: https://gridhead.net/update-on-fedora-badges-revamp-project/
[4]: https://badges.fedoraproject.org/
[5]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-932x1024.png
[6]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-4-932x1024.png
[7]: https://fedoramagazine.org/wp-content/uploads/2026/08/Screenshot-From-2026-08-18-13-19-59-2-932x1024.png
[8]: https://fedoramagazine.org/wp-content/uploads/2026/08/Screenshot-From-2026-08-18-13-20-18-1-932x1024.png
[9]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-11-932x1024.png
[10]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-6-932x1024.png
[11]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-7-932x1024.png
[12]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-8-932x1024.png
[13]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-9-932x1024.png
[14]: https://github.com/fedora-infra/tahrir-api
[15]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-10-932x1024.png
[16]: https://openid.net/developers/how-connect-works/
[17]: https://id.fedoraproject.org/
[18]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-14-932x1024.png
[19]: https://libravatar.org/
[20]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-15-932x1024.png
[21]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-12-932x1024.png
[22]: https://github.com/fedora-infra/tahrir/milestone/2
[23]: https://en.wikipedia.org/wiki/Svatantrya
[24]: https://github.com/fedora-infra/tahrir
[25]: https://cfp.fedoraproject.org/flock-to-fedora-2026/talk/ZKUX8D/
[26]: https://en.wikipedia.org/wiki/Development_hell
[27]: https://github.com/fedora-infra
[28]: https://github.com/fedora-infra/tahrir/issues
[29]: https://github.com/fedora-infra/tahrir/pulls
[30]: https://chat.fedoraproject.org/#/room/#badges:fedoraproject.org
[31]: https://fedoramagazine.org/wp-content/uploads/2026/08/image-13-932x1024.png
