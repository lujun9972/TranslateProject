[#]: subject: "Mozilla Stands Against Google's New Advertising Tech"
[#]: via: "https://news.itsfoss.com/mozilla-google-ads/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Mozilla Stands Against Google's New Advertising Tech
======
Google and privacy, relevant keywords, isn't that right?
Ah, online advertising.. 😅

Big corporations cannot stop profiting from it, and small businesses cannot afford not to invest in it. It is a kind of unsavory relationship that usually benefits the parties involved; such as the advertiser ( _sometimes the product owner too_ ) and a potential customer ( _user_ ).

But, occasionally, this relationship goes too much into the gray, when a user is targeted because of their online activity to be served with targeted advertisements on the various sites they visit.

Depending on who you ask, the consensus is that too much targeted ads is a sign of aggressive tracking practices that don't belong in this age of digital privacy awareness.

That is partly why Google has been trying so hard to clean up their act, with many major moves recently. One such move related to their Protected Audience API has got Mozilla at odds with the search engine giant.

So, let's dive in and see what's happening.

📋

I am using the term “Advertisers” to generalize all kinds of online advertisement-related service providers.

### Google's Protected Audience: Why the Fuss?

Formerly known as the FLEDGE API, the [Protected Audience][1] API is part of Google's [Privacy Sandbox][2] initiative that is supposed to facilitate a more privacy-friendly way of serving advertisements to users.

It works by having a separate secure space on the browser ( _Chrome, for example_ ), where the user's interests are stored, and the advertisers would have to go through an ad auction run by the user's browser to serve relevant ads.

As a result of that, **the user's interests and browsing activity on different sites is kept away from the prying eyes of advertisers** , who would typically track users across multiple sites.

This came about after Google got started with their Privacy Sandbox initiative, and revealed that they would completely disable third-party [cookies][3] on Chrome in the second half of 2024. Doing that would lock out all cookies except the ones from the site a user was visiting.

As one might imagine, **this became an issue**. Many advertisers were concerned that blocking third-party cookies would give Google the upper hand, as their services ( _including Chrome_ ) are some of the most used ones across the globe.

Nonetheless, amid mounting pressures from competition regulatory bodies like the UK's [Competition and Markets Authority][4], Google appears to be fast-tracking the implementation of Protected Audience.

But, Mozilla is [not convinced][5], saying that this “ _fails to meet its own privacy goals_ ”. And, they are backing up their claim with some pretty convincing reasoning.

They present an example where they show that Protected Audience creates an “ _alternative information dimension_ ” where any site a user visits could send information related to how they interacted with it.

📋

This is not limited to just one, but multiple sites can do the same.

![Credit: Mozilla][6]

Subsequently, sites could then process that data to decide on the advertisements that they would serve.

However, only the user can see into this dimension, with advertisers/websites being able to open so-called “windows” inside this for the users to peek into ( _read as being shown relevant ads_ ).

Mozilla agrees that something like this could be a good thing for users. But, they think that Protected Audience fails in two key ways.

The first is that **Protected Audience has too many leaks**.

Google, in an attempt to please advertising companies, had to loosen many important protections that resulted in a design that Mozilla claims has “ _ **no privacy**_ ”.

Even though Google plans to work on many of these leaks, Mozilla thinks that there exist information leaks **** with no actual fix in sight.

That leads us to the second issue; Protected Audience might get stronger, sure, but **targeted advertising is also a key factor**.

Even though information collection was made harder, advertisers still have enough access to run targeted advertisements to better manipulate a user's decision-making.

Mozilla also [added][7] that:

> The positive vision of the effect that Protected Audience might have on competition in advertising is one that focuses on market imbalance. However, it takes an
>  advertising-centric view of the system that is narrow.

> In a sense, Protected Audience is the product of the conjunction of competitive pressure on privacy and antitrust fears, so this is a natural conclusion.

And I agree.

I feel that this move is targeted towards appeasing the various competition regulatory authorities, while also being on the good side of the many advertisers who aim to capitalize on the huge user base of Google services such as [Chrome][8].

Sadly, in all of this, you as the user have to trade in your data for seeing some targeted ad that may or not benefit your daily life, irrespective of Protected Audience being implemented.

_💭 What are your thoughts on Google's new ad tech? Please let me know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/mozilla-google-ads/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://developers.google.com/privacy-sandbox/relevance/protected-audience
[2]: https://privacysandbox.com/
[3]: https://www.cloudflare.com/learning/privacy/what-are-cookies/
[4]: https://www.gov.uk/government/organisations/competition-and-markets-authority
[5]: https://blog.mozilla.org/en/privacy-security/googles-protected-audience-protects-advertisers/
[6]: https://news.itsfoss.com/content/images/2024/04/Protected_Audience_Diagram_Mozilla-1.png
[7]: https://mozilla.github.io/ppa-docs/protected-audience.pdf
[8]: https://www.google.com/chrome/
