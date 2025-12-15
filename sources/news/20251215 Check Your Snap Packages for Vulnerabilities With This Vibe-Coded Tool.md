[#]: subject: "Check Your Snap Packages for Vulnerabilities With This Vibe-Coded Tool"
[#]: via: "https://itsfoss.com/news/check-snap-packages-vulnerabilities/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Check Your Snap Packages for Vulnerabilities With This Vibe-Coded Tool
======

[![Warp Terminal][1]][2]

[Snap][3] packages have been a topic of contention in the Linux space for a while now. Some complain about slower startup times. Others dislike the proprietary Snap Store backend. Then there are concerns about bundled dependencies sitting around without updates.

All of that hasn't stopped [Canonical][4] from working on it, though. They have been busy making it faster and more secure, while shipping Snap versions of popular applications like Firefox on Ubuntu.

Now there is **a new tool that might actually help** with one of the major concerns surrounding Snaps. [Alan Pope][5], a known voice in the Ubuntu community, has built a tool called [SnapScope][6] that scans Snap packages for security vulnerabilities.

### SnapScope: Checking Snaps for CVEs

The website works both on desktop and mobile and is straightforward to use. You type a Snap package name or publisher into the search bar, and Snapscope scans it for known vulnerabilities. The results [are broken down][7] by severity: _KEV_ , _CRITICAL_ , _HIGH_ , _MEDIUM_ , and _LOW_.

Currently, Snapscope **only supports x86_64 packages** ( _with the possibility of other platforms being supported_ ), and the vulnerability data comes from [Grype][8], an open source scanner for container images and filesystems.

Each vulnerability entry shows the [CVE ID][9], severity rating, and relevant links to learn more about it. The homepage also has two charts that show recently scanned packages and packages with the highest vulnerability counts.

![I searched for the ONLOFFICE Desktop Editors Snap.][10]

Alan mentions that **he vibe-coded this** for Chainguard's [Vibelympics][11], a competition where developers throw together creative projects to win $1,000 that goes to a charity of the winner's choice.

The tool itself takes a " _no judgement, just facts_ " approach. It doesn't tell you whether Snaps are good or bad. It just shows what vulnerabilities exist in the packages you search for.

If you are wondering: **Who's this for?**

Well off the top of my head, **sys admins** who need to audit their Snap installations, **developers maintaining Snap packages** who want to know what CVEs they need to tackle, and **security-conscious users** who intend to check what they are installing before it touches their system.

Via: [OMG! Ubuntu][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/check-snap-packages-vulnerabilities/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://snapcraft.io/about
[4]: https://canonical.com/
[5]: https://www.linkedin.com/in/alan-pope-uk/
[6]: https://snapscope.popey.com/
[7]: https://snapscope.popey.com/about#:~:text=Vulnerability%20Severities
[8]: https://github.com/anchore/grype/
[9]: https://en.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures
[10]: https://itsfoss.com/content/images/2025/12/snapscope-onlyoffice-desktop-editors-scan.png
[11]: https://vibelympics.splashthat.com/
[12]: https://www.omgubuntu.co.uk/2025/12/snapscope-snap-security-vulnerability-checker
