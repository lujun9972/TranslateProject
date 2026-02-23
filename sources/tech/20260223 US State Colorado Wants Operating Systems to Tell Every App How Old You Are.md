[#]: subject: "US State Colorado Wants Operating Systems to Tell Every App How Old You Are"
[#]: via: "https://itsfoss.com/news/colorado-age-attestation-bill/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

US State Colorado Wants Operating Systems to Tell Every App How Old You Are
======

[![Warp Terminal][1]][2]

Age verification online [is regrettably becoming the norm][3]. Platforms are increasingly asking users to prove their age before accessing certain content or services. That usually means handing over personal data, sometimes even biometric data, to a third-party provider, **then hoping they do not sell it, suffer a breach** , _or both_.

Now, the U.S. state of [Colorado][4] is mulling over a bill to implement age reporting for installing apps on computers and mobile devices.

### Age Attestation, What?

![][5]

Senator [Matt Ball][6] and Representative [Amy Paschal][7] presented this bill, _**Age Attestation on Computing Devices**_ ([SB26-051][8]), to the Colorado Senate, where it was assigned to the [Business, Labor, and Technology Committee][9].

Currently **only a proposal** , the bill calls for operating system providers like Microsoft, Google, Apple, and Canonical to present an interface during device account setup that asks the account holder ( _a person in Colorado_ ) to specify the birth date/age of the device's user.

That age data is then translated into an " _age signal_ ," which apps can call on via an API when a user downloads or launches them. The bill claims that this refers to non-personally identifiable data taken from a user's birth date or age.

The age signal **does not hand over a specific birthdate to developers**. It works in four age ranges — under 13, 13 to under 16, 16 to under 18, and 18 and above.

The bill also explicitly states that only the minimum amount of information necessary should be shared. Neither the OS provider nor developers are allowed to pass the age signal to third parties for purposes outside of what the bill requires.

On paper, **the fines for violations sound like a serious deterrent**. Up to $2,500 per minor affected for a negligent violation and up to $7,500 per minor for an intentional one. For a platform with millions of minor users, those numbers could stack up fast.

But the penalty is only triggered if the state [Attorney General][10] chooses to bring a civil action, which means enforcement is entirely dependent on the political will of whoever holds that office at a given time.

Given the [sad state of things][11] currently, where minors' rights are violated routinely without any accountability or real punishment, these fines sound more like a slap on the wrist than a genuine consequence.

📋

It is also unclear how this rule will apply to operating systems that do not need an online account.

### The Flaws

The most immediate problem with SB26-051 is that **it never specifies how age is actually determined**. The bill says account holders must " _indicate_ " the birth date or age of the user.

That's it; no verification mechanism, no ID check, or anything else is mentioned. Any so-called " _account holder_ " could just straight up lie, and the system would take it as is.

I understand the need for the moderation of what applications minors install and use. But such legislation can't be a substitute for parental oversight, and when such a thing is imposed, it usually ends up being both ineffective and overreaching.

**Personally** , I still think parents' or guardians' oversight ( _provided it is grounded_ ) of what their children consume is the single most important thing that can prevent harmful content from influencing these young minds.

If passed, **the bill would take effect on January 1, 2028**. That said, if a [referendum petition][12] is filed against it within ninety days of the [General Assembly][13] adjourning, it would go to Colorado voters in November 2026 to decide its fate.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/colorado-age-attestation-bill/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://discord.com/press-releases/discord-launches-teen-by-default-settings-globally
[4]: https://en.wikipedia.org/wiki/Colorado
[5]: https://itsfoss.com/content/images/2026/02/colorado-age-attestation-bill-summary.png
[6]: https://leg.colorado.gov/legislators/matt-ball
[7]: https://leg.colorado.gov/legislators/amy-paschal
[8]: https://leg.colorado.gov/bills/SB26-051
[9]: https://leg.colorado.gov/committees/2026A/senate/BusinessLaborTechnology
[10]: https://coag.gov/
[11]: https://itsfoss.com/news/bash-manual-in-epstein-files/
[12]: https://www.sos.state.co.us/pubs/elections/referendumPetitions.html
[13]: https://leg.colorado.gov/
