[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Reading about open source in French)
[#]: via: (https://opensource.com/article/20/6/open-source-french)
[#]: author: (Chris Hermansen https://opensource.com/users/clhermansen)

Reading about open source in French
======
Since 1998, LinuxFr.org has brought information about open source and
free software to a French-speaking audience, says Benoît Sibaud.
![Blue skies over the city of Paris France ][1]

English speakers have so many wonderful open source resources that it's easy to forget that communications in English aren't accessible to everyone everywhere. Therefore, I've been looking for great open source resources in Spanish and French, so I can recommend them when the need arises.

One I've been looking at recently is [LinuxFr.org][2], which seems to be a fine "[agora][3]" for all sorts of interesting conversations in French about open source specifically and open everything else as well.

Benoît Sibaud, _directeur de publication_ at LinuxFR.org, was kind enough to tell me about the organization. Here is our conversation, slightly edited for clarity.

**Chris Hermansen:** LinuxFr.org seems to have a similar orientation as Opensource.com, with all sorts of articles on open source and free software (in the Free Software Foundation sense). Can you tell me a bit about the people behind this fine and interesting site?

**Benoît Sibaud:** Launched in December 1998, LinuxFr.org was mainly the work of [Fabien Penso][4], who coded the site, wrote most of the articles, and brought together about 10 volunteers. The site was in the style of [Slashdot][5], with a lot of short news about Linux and free software (and a bit of other stuff as well). Anyone could submit a short article. Software presentations, explanatory articles, job offers, etc. were left to "friendly sites" chosen from the small galaxy of free software resources. After one year, the audience reached 4,000 visits per day.

The technical topics are still available, but more political topics have been added: free software, debates about the patentability of software, DRM [digital rights management], the use of cryptography, legislation around the internet, etc. Also, broader topics, outside of pure software, have become more frequent: free art, free hardware, Commons, open data, maps, encyclopedias, school books, etc.

Technically, the site has evolved: Fabien's first version in PHP; then [development in] content manager [daCode][6] (also in PHP), which was an official Debian package; then a system of templates named Templeet above PHP; then a rewriting in Ruby on Rails by Bruno Michel.

On the features side, first came the articles, called News or [Dépêches][7], then Blogs/Diaries or [Journaux][8], the Q&amp;A forums or [Forums][9], the addition of a karma and auto-moderation system, the addition of a collaborative editing space, then wiki pages, and more recently, the chance to simply discuss a hyperlink or [Liens][10].

More than 20 years later, LinuxFr.org is a major French-speaking community website on free and open source software and related topics: DIY, open hardware, open data, Commons, etc. It has over 100,000 articles, 1.8 million comments, and 1.2 million monthly visitors. It's a real institution managed by volunteers and financed only through donations. It can be defined as "by and for communities": contents are written by our visitors, we manage our servers and develop our content management system (published under the [AGPL][11]), and we have small teams of volunteers to help others in the collaborative editing of contents and to moderate comments and contents. Our legal structure is an association.

Nobody from the original team is still active. But more than 50 people have been part of our [teams][12], including the current 26. Each person's motivations probably vary: to do, to share, to be part of something bigger, to help others, to learn, to discover by serendipity, etc. Many of us are involved in free software and free software movements.

**CH:** Who are the readers? Who participates in producing the articles? Who is the editorial team? Is this a full-time job?

**BS:** Our audience is heterogeneous and mainly passionate. We have senior experts, young engineers, free software users, beginners, a mix of computer science people, people in the education system (teachers or students), hobbyists, makers, and people fond of the free software and open source concepts. We deduce all that from our contents and comments; we don't collect profiles or run censuses.

The articles are written by website visitors. Anybody can propose an article. Some articles come from computer science researchers or contributors from big free software to communicate about their work; others are from companies (these are not press releases); others are collaboratively written in the dedicated space—the "editorial department"; others are translations from release notes of software or distributions; and finally, a large part is from individual authors writing about a subject familiar to them.

To encourage more people to contribute, each month, we reward the best publications with books or subscriptions offered by publishers invested in free software.

Some regular authors work in the editorial department to help during collaborative writing, to fix mistakes in French syntax or Markdown code, to add pictures, tags, links, to help beginners, etc. Some are also self-organized around various regular topics like Firefox versions, Linux kernel releases, etc.

There is also a small technical team that works on the website code and manages the servers.

And finally, there is the moderation team: both the _a priori_ moderation of contents (such as News), with the usual editorial work of proofreading, and the _a posteriori_ moderation of contents and comments (removing spam, avoiding abuse, etc.).

Everybody is a volunteer. As nobody is paid, there is no editorial choice: articles are published when we are ready, [after they are] proofread and validated by the moderators.

**CH:** Do you have a particular orientation? That is, toward Linux, toward developers?

**BS:** LinuxFr.org talks about everything related to free/open stuff in general. And no, there is no objective to target a particular audience; the articles are as varied as the readers and can be oriented toward specialists in a field or giving informative content for everyone. Often the two intersect and overlap; there is no watertight seal on this, and many of us appreciate having technical and accurate articles as a source of information on a topic we are new to or know little about.

**CH:** I read an article on LinuxFr.org on how to use [Mumble][13] that seemed to be very useful and informative. How do you decide on a subject? How do you develop the article at a level that is useful for your readers?

**BS:** No selection, we take what we are offered! But the news dictates certain desires to write [about a subject]. We sometimes refuse an article—the most common reasons are that it is an advertising infomercial or a copy of an article published elsewhere (even if it is by the same person), but refusals are rare, and the proposed articles are in large majority accepted.

As our audience is very heterogeneous, the writing style is most often decided by the author of the article; however, we try to be accessible on what needs to be accessible: for example, an article on a programming language is necessarily technical, but on other subjects, the moderation team intervenes to translate the English terms, to reformulate sentences that are too technical, to remove certain biases (such as talking about a minister or a parliament without mentioning the country), or to explain certain terms through links to Wikipedia. During collaborative editing, anyone can correct an article or encourage clarity. Finally, the comments under the published articles play a great role for popularization, technical refocusing, complementing, or opening up to something else. Historically, these comments have done a lot for the quality of the site, which has published very short articles for a long time.

There are also very technical, very specialized articles that we have rewritten with their authors to make them more readable by a public of curious computer scientists (like the article on [image registration techniques][14]).

**CH:** I like the presentation of subject areas on the left side of the home page. How do you decide on the grouping of subjects? For example, Cuisine and Documentation seem fairly general, but Golang is more specific.

**BS:** There were a lot of sections at the beginning that were filled with short news. These sections were added and removed as the years went by and the computing or free movement evolved; the Amiga section was archived because these computers became rare, or the section on RC5 encryption disappeared at the same time as the world contest to break it. Or the daCode section, which talked about our PHP content manager, [which was removed] when its development stopped. And of course, some events changed their name, regrouped, or disappeared, and some distributions were renamed (Mandrake/Mandriva/Mageia, for example).

We've done some merging to reduce the number of sections. Then we've added more because of current events.

In the end, a section appears when a name and an icon are proposed and when there are people ready to write about it. And a section disappears (although the old contents of the hidden sections remain online, of course) when nobody writes about the topic anymore. The use of tags makes it possible to navigate more finely to find articles on a given topic.

**CH:** At Opensource.com, we are oriented—perhaps too oriented—toward the English-speaking world. In my experience, there are a lot of people who would rather have information in their native language. As a Francophone site, what do you think of this perspective? Have you some idea of the demand for resources on open source software in French?

**BS:** When the site went online in 1998, there were already many sites in English. The first French-speaking free software associations were new. There were few French resources on free software.

Many of us are fluent in English (and/or other languages, in fact). Others have to make an effort to understand the language, in addition to the subject. This double effort justifies the strong demand for French-language information. For some, this double effort is prohibitive. For example, when someone posts an excerpt from an article in English, disgruntled comments may appear.

It is different to be able to read information in English and be able to discuss it, to have an exchange in the comments, and feel comfortable enough to express your questions or points of view. It is also often the case that people are able to speak one sentence about their project in English, whereas they could spend hours talking about it in French.

We try to allow those who write French poorly to present their projects and ask questions, as well as those who write very well in French but would be unable to write the same thing in English. And finally, we provide an additional forum and a different audience for those who write in either French or English. But this is also true for other languages: some visitors have translated and commented on articles originally published in Japanese, Spanish, or German, for example.

Of course, we are not the only French-speaking people to publish about free software. Let's start by mentioning the friendly sites listed at the bottom of our website:

  * Associations for the promotion and defense of free software like [April][15], for popular education like [Framasoft][16], for the defense of freedoms on the internet like [La Quadrature du Net][17], for the explanation of free licenses like [Veni, Vedi, Libri][18], for mutual help like [Léa-Linux][19]
  * The site [L'Agenda du Libre][20], which announces events in the French-speaking world and beyond (and provides a list of several hundred free software actors, FSUGs [free software user groups], companies, hackerspaces, etc.) or [En Vente Libre][21], which allows them to sell their goodies and collect donations
  * Publishers that publish books or magazines, such as [Eyrolles][22], [Diamond][23], or [ENI][24]



This list is not exhaustive; many other sites are talking about free software: professional associations (e.g., [CNLL][25], competitiveness clusters, etc.), specialized press sites (e.g., [NextInpact][26] regularly talks about free software), project sites (e.g., [Ubuntu-fr][27]), and so on.

**CH:** Where is LinuxFr.org going in the future? More articles, multimedia, syndicated publication?

**BS:** The site lives solely on voluntary contributions, including the publishing software. We communicate as much as possible about the activities of the association (for the legal and financial parts) and the work of the volunteers. We want to improve the design and ergonomics of the site for new features or new services, resolve questions about datacenter centralization compared to distributing it over fiber-to-the-home access, etc. But evolution happens little by little, and only if contributors realize them. To sum up, the number of articles or the themes of the articles are decided by the visitors of the site. And the technical modifications are made according to visitors' requests or contributors' wishes.

For example, the [Links][10] section, [which is] like [Hacker News][28], appeared because we were offered the development work required to implement it.

Like many sites with user-generated content, we are either the source of information (content produced by our visitors for our site) or the relay of other information sites or journals dealing with free software, privacy, technical openness, etc. (French-speaking or not) that are of interest to our visitors (to diffuse or to discuss).

**CH:** I see several recreational topics on LinuxFr.org, like Cuisine and Sound. Do you have any other recreational activities, like hang gliding or musical composition?

**BS:** The Sound section includes technical articles on computer-assisted music (CAM), how to produce or play sound.

The Cuisine and Cinema topics have been a tradition throughout the history of the site. At first, it was to talk about something other than computers (newspaper blogs didn't exist yet); then, it became a fun tradition.

It's hard to define what a recreational activity is for our audience; it may well be games (video, recent or oldies, or tabletop), computer science and programming (personal or professional), electronics, home automation, robotics, cooking, sports such as cycling, an Easter egg hunt, or endless debates on any subject.

* * *

Thanks very much, Benoît, for taking the time to share your thoughts with us, and best wishes to you all for the continued success of LinuxFr.org!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/open-source-french

作者：[Chris Hermansen][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/clhermansen
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/nil-castellvi-paris.jpg?itok=aev54OFM (Blue skies over the city of Paris France)
[2]: https://linuxfr.org/
[3]: https://en.wikipedia.org/wiki/Agora
[4]: https://twitter.com/fabienpenso?lang=en
[5]: https://slashdot.org/
[6]: http://dacode.sourceforge.net/index.en.html
[7]: https://linuxfr.org/news
[8]: https://linuxfr.org/journaux
[9]: https://linuxfr.org/forums
[10]: https://linuxfr.org/liens
[11]: https://www.gnu.org/licenses/agpl-3.0.en.html
[12]: https://linuxfr.org/team
[13]: https://www.mumble.com/
[14]: https://linuxfr.org/news/recalage-d-images-piv-et-correlation-d-images-les-bases-theoriques
[15]: https://www.april.org/
[16]: https://framasoft.org/en/
[17]: https://www.laquadrature.net/en/
[18]: https://vvlibri.org/fr
[19]: https://lea-linux.org/
[20]: https://www.agendadulibre.org/
[21]: https://enventelibre.org/en/
[22]: https://www.editions-eyrolles.com/Recherche/?q=linux
[23]: https://boutique.ed-diamond.com/
[24]: https://www.editions-eni.fr/
[25]: https://cnll.fr/
[26]: https://www.nextinpact.com/
[27]: https://ubuntu-fr.org/
[28]: https://news.ycombinator.com/
