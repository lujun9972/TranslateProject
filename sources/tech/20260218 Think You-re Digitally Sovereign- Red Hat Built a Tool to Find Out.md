[#]: subject: "Think You're Digitally Sovereign? Red Hat Built a Tool to Find Out"
[#]: via: "https://itsfoss.com/news/red-hat-digital-sovereignty-assessment-tool/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Think You're Digitally Sovereign? Red Hat Built a Tool to Find Out
======

[![Warp Terminal][1]][2]

[Red Hat][3] is best known for Red Hat Enterprise Linux (RHEL), the commercial Linux distribution that quietly runs a significant portion of enterprise and government infrastructure worldwide.

They also maintain [Fedora][4], contribute heavily to the Linux kernel, and are the people behind [Ansible][5] and [OpenShift][6].

Now they have open-sourced a tool to help organizations figure out where they stand when it comes to [digital sovereignty][7].

### For Digital Sovereignty Assessment

![][8]

Red Hat has released the _**Digital Sovereignty Readiness Assessment**_ , a self-service web tool that helps organizations figure out digital sovereignty. It is open source, released under the **Apache 2.0 license** , and available on GitHub ( _linked below_ ).

The tool is maintained by Red Hat's [Community of Practice][9] (CoP) and **is designed to be vendor-neutral** , making it useful to any organization regardless of what technology stack they run.

If you were thinking about privacy, the open source version doesn't collect anything, as all assessment data stays in the browser and is never sent to Red Hat or anywhere else.

The assessment **covers seven domains** : _Data Sovereignty_ , _Technical Sovereignty_ , _Operational Sovereignty_ , _Assurance Sovereignty_ , _Open Source Strategy_ , _Executive Oversight_ , and _Managed Services_.

It presents 21 questions, takes about 10 to 15 minutes to complete ( _if done mindfully_ ), and scores respondents across a four-level maturity scale: _Foundation_ , _Developing_ , _Strategic_ , and _Advanced_.

There are **two easy ways to test it**. The [Red Hat-branded version][10] is hosted on Red Hat's own infrastructure that conveniently ends with a prompt to [book a consultation][11]. The other is the self-hostable version that was open-sourced on [GitHub][12].

![The result of my dummy test of Red Hat's assessment tool.][13]

[Christopher Jenkins][14], Senior Principal Chief Architect at Red Hat, has the latter up on his [personal website][15], which is nearly identical but with different themeing and no nudge to contact Red Hat's sales people.

**I ran a dummy assessment** on Red Hat's version to see how the tool worked, and it was nice, I guess? I filled out the form with random answers, and the result was a 38% maturity score, with a breakdown of readiness across 7 digital sovereignty domains and some recommended moves I could take to improve the score.

I say " _I guess_ " because I am not exactly well-versed in what it actually takes for something to comfortably call itself digital sovereignty-compliant.

Via: [FOSS Force][16]

* * *

**Suggested Read 📖:** [_Session's Co-Founder Thinks You Don't Need to Ditch WhatsApp Completely_][17]

![][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/red-hat-digital-sovereignty-assessment-tool/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.redhat.com/en
[4]: https://www.fedoraproject.org/
[5]: https://github.com/ansible/ansible
[6]: https://www.redhat.com/en/technologies/cloud-computing/openshift
[7]: https://www.europarl.europa.eu/RegData/etudes/BRIE/2020/651992/EPRS_BRI(2020)651992_EN.pdf
[8]: https://itsfoss.com/content/images/2026/02/red-hat-digital-sovereignty-tool.png
[9]: https://redhat-cop.github.io/
[10]: https://www.feedback.redhat.com/jfe/form/SV_1LGSam42lrM4Ddk
[11]: https://www.redhat.com/en/products/digital-sovereignty
[12]: https://github.com/redhat-cop/viewfinder-upstream
[13]: https://itsfoss.com/content/images/2026/02/red-hat-digital-sovereignty-tool-results-1.png
[14]: https://www.linkedin.com/in/christopher-jenkins-26602025/
[15]: https://www.chrisj.co.uk/viewfinder/
[16]: https://fossforce.com/2026/02/oh-la-la-red-hat-open-sources-digital-sovereignty-readiness-tool/
[17]: https://itsfoss.com/news/session-co-founder-interview/
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-285.png
