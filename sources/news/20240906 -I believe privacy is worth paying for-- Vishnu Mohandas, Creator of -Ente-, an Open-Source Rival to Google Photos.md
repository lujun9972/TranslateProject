[#]: subject: ""I believe privacy is worth paying for": Vishnu Mohandas, Creator of 'Ente', an Open-Source Rival to Google Photos"
[#]: via: "https://news.itsfoss.com/vishnu-ente-founder-interview/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

"I believe privacy is worth paying for": Vishnu Mohandas, Creator of 'Ente', an Open-Source Rival to Google Photos
======
Meet the founder of Ente, building a privacy alternative to Google
Photos.
[![][1]][2]

![][3]

Earlier this year, **Ente** dropped on our radar when its [developers decided to open-source the project][4] (including the server code).

If you are curious, **Ente is a privacy-focused alternative to Google Photos**. You get a free starter plan to experience the platform and store some of your memories. And, if you are serious about backing up all your photos and videos, opt for its paid pricing plans.

I think it is a unique offering, as a hosted platform, but also manages to be a [self-hosted alternative to Google Photos][5].

![][6]

Fast-forward to the present, I got the chance to ask the founder of [Ente][7] a couple of questions to understand their vision to build an open-source replacement to Google Photos or iCloud Photos.

Read on to find out more about it...

### _1\. Ente is an impressive alternative to Google Photos. When did you conceptualize it, and how did it all happen?_

![][8]

**A** : I was working at Google in 2019, when I realized that the amount of information Google can infer out of my photos is scary.

Since I’m sentimentally attached to my photos, I was creeped out, and I looked around for alternatives.

I eventually ended up buying an iPhone and moving my photos to iCloud for privacy.

But then I had the expensive realization that Apple locks all of our data to their ecosystem. So my wife could no longer access my library on her Android device, and I could no longer view my own photos on my Linux machine.

Then I looked around more and to my surprise **I realized that there’s no one out there building an alternative for photos that is private and accessible**.

Given my obsession with photographs, and my unhappiness with my work at Google, I realized this was a good project to get started on.

So **I quit and moved back from Switzerland to India in 2020** , right when COVID hit, to start this project which has since evolved into Ente.

[Ente (Website)][7]

### _2\. The term "Ente" has an interesting meaning as per the FAQs. How did you end up picking the name for this?_

![][9]

**A:** Credits to my wife for suggesting the name. **In Malayalam (our mother tongue) “Ente” means “mine”.**

I was obsessed with 4 letter domain names, and “ente.io” was available at that point, so we went ahead with Ente.

There’s a slightly more elaborate version of this story available here:

![][10]

### _3\. It's tough to compete against Google's dominance. What made you think that Ente can stand out for its users?_

![][11]

**A:** **I believe privacy is worth paying for** and that we can beat Google at their game in the long run by focusing on building a beautiful place to store, share and pass down memories.

There will be an inflection point where the world will realize that Google is an advertising company with a photos app. At that point, Ente will be the best alternative out there.

### _4\. We recently saw a new pricing plan, making it easy and affordable for new users to try out. Do you have any plans to share with us for Ente's future?_

![][12]

**A:** Our current focus is on delivering **v1.0 of Ente Photos**.

This means getting to a point where there’s **some amount of feature parity with Google / Apple Photos.**

A lot of our work over the last 2 years has been in perfecting and delivering private AI — **where we run machine learning locally on your device** , to enable features like **face recognition** and **search**.

This has taken a massive amount of engineering effort to pull off, but we’re almost there. **Both face recognition and semantic search are now in beta**. Now we’re working towards launching this to the general public.

Once v1.0 is out, we’d like to work on some features to ensure posterity, where in **Ente can make sure that my partner or kids get access to my data when I’m not around anymore**. We’d also like to explore how we can make discovery and auto curation more seamless, and sharing more delightful.

There are also some other technically challenging bits we’re working on, like **end-to-end encrypted video streaming**.

With a product around photos, the roadmap is infinitely long. So we have a lot of exciting things to look forward to.

### _5\. Ente Auth is a separate product that I love. Can we expect more products like that under Ente's umbrella?_

![][13]

**A** : Not in the near future because right now, we want to do one thing, and one thing well — **building a better alternative to Google Photos.**

Customers have very high benchmarks for a photos app. This means we’ve to deliver a better experience than Google or Apple or Instagram, while playing within the confines of end-to-end encryption. **Given that our engineering bandwidth is extremely limited compared to our competitors, it's important for us to focus, to prioritize and execute well.**

So no more new products _for now_.

[**Ente Auth**][14] **was a weekend hack that Neeraj (Ente’s CTO) pulled off simply to cure his own itch** — he wanted a cross-platform app that could back up his 2FA secrets.

In the long run, once our photos app is reasonably mature, I’m sure there’ll be more such weekends 😄

**Suggested Read** 📖

![][15]

### _6\. While we know that Ente is open-source and end-to-end encrypted, would you like to add any exciting details on measures your team takes to secure the photos?_

**A** : Ente stores **3 copies of your data** , in **3 locations**. One of these copies comes with a lock that makes us immune to ransomware attacks. Another is stored in a fallout shelter, 25m under the ground in Paris, to make us immune to natural disasters. You can find more details about our replication strategy here:

![][16]

**We’ve also been at the receiving end of DDoS attacks over the years**. So our infrastructure has organically matured to handle such unfortunate events as well.

In general, we’re very paranoid as engineers, and **we believe a healthy amount of paranoia is necessary to build a company like Ente**.

### _7\. Tell us a little about yourself and your life goals for the future._

**A** : **I’m primarily** **a programmer, who started building Ente to solve my own problems** and is now having to deal with the variety of non-engineering problems that come with running a company.

I grew up in Kerala, and took a liking to computers in high school. I was (still am) amused by how we can paint pixels on screens. I was introduced to FOSS in college, when I had to port newer versions of Android to my low end device. Furthermore, I got pulled into the rabbit hole and ended up as the maintainer of a few Sony device kernels.

All this work helped me get a job in this startup called Directi in 2012. I met a bunch of exceptional programmers there (some of whom are now building Ente with me). We got to build and scale a few impactful products together, some of which, like Zeta, are now worth over a billion dollars.

In 2019, I moved to Zurich to work for Google, and that stint did not go well. There was nothing impactful to build, and the amount of bureaucracy was mind numbing. **So I quit after a few months and returned home to work on something that would make me happy, which turned out to be Ente.**

![Ente's engineers discussing at office][17]

I’m not someone who sets life goals, I try my best to take things one day at a time. So life is about growing as a human being, and getting better at handling the stress that comes with building a company and taking care of myself, so I can better take care of those around me.

### _8\. What do you find yourself doing in your spare time?_

**A:** I’m not great at balancing work and life because Ente is practically my life. Of late, I’ve been trying to get better at disconnecting. I have a daughter who is 2 years old, and she helps with this. **I spend a healthy amount of time playing and listening to music with her.**

At other times I lurk on forums, and passively watch Counter Strike matches.

**I also enjoy spending time with friends**. Since some of them are already helping build Ente, I thankfully don’t have to go out of my way for this.

![][18]

I’ve started going to the gym in the last few months, and I’m happy that it has become a hobby.

### _9\. What are some of your favorite open-source tools?_

![][19]

**A:** A lot of Ente has been built on top of open source software, so it's hard to pick a favorite.

I’ll start with **Firefox** because that’s where I’m typing this.

I use **Notesnook** for taking notes, **VS Code** for building things.

**Libsodium** is what the entirety of Ente’s cryptography ([ente.io/architecture][20]) is based on. We enjoy using **Grafana** and **Metabase** for monitoring system and product metrics.

**Listmonk** has worked out great for us for sending out newsletters in a privacy-friendly way.

This answer is heavily influenced by recency bias, the actual list would be endless.

### _10\. A message to our readers who want to switch away from Google Photos, and potentially contribute to Ente's open-source development._

**A** : **The amount of information Google can derive from your photos is crazy**. They can see how happy you are, who you hang out with, who / what makes you the happiest, … **It’s incredible how most folks don’t realize the implications of giving their memories away to a company that is designed to maximize their shareholder value.**

So congratulations on wanting to give yourself some privacy! We have extensive migration guides at [help.ente.io][21]

You can check us out on [GitHub][22]:

![][23]

If you’re interested in contributing, please check out our contribution guidelines [here][24]. Do note that the best way to help would be by spreading the word about Ente 😊

* * *

_🗨️ What do you think about Vishnu's vision for Ente? Do you think you will switch away from Google Photos to Ente Photos?_ _Who do you want us to interview next? Let us know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/vishnu-ente-founder-interview/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/content/images/2024/09/ente-founder-interview-feat-1.png
[4]: https://news.itsfoss.com/ente-open-source/
[5]: https://itsfoss.com/google-photos-alternatives/
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[7]: https://ente.io/
[8]: https://news.itsfoss.com/content/images/2024/09/ente-photos-feature.png
[9]: https://news.itsfoss.com/content/images/2024/09/ente-name-illustration.png
[10]: https://ente.io/icons/icon-192x192.png?v=c793f4813855040bddb3ac4003f640db
[11]: https://news.itsfoss.com/content/images/2024/09/ente-competition.png
[12]: https://news.itsfoss.com/content/images/2024/09/ente-v-1.png
[13]: https://news.itsfoss.com/content/images/2024/09/ente-auth-1.png
[14]: https://ente.io/auth/
[15]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[16]: http://ente.io/icons/icon-192x192.png?v=c793f4813855040bddb3ac4003f640db
[17]: https://news.itsfoss.com/content/images/2024/09/ente-office.JPG
[18]: https://news.itsfoss.com/content/images/2024/09/ente-office-celebration.jpg
[19]: https://news.itsfoss.com/content/images/2024/09/ente-fav-tools.png
[20]: http://ente.io/architecture
[21]: https://help.ente.io/
[22]: https://github.com/ente-io/ente
[23]: https://github.githubassets.com/assets/pinned-octocat-093da3e6fa40.svg
[24]: https://github.com/ente-io/ente/blob/main/CONTRIBUTING.md
