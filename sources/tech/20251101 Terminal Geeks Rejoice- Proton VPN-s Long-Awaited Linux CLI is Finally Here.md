[#]: subject: "Terminal Geeks Rejoice! Proton VPN's Long-Awaited Linux CLI is Finally Here"
[#]: via: "https://itsfoss.com/news/proton-vpn-linux-cli/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Terminal Geeks Rejoice! Proton VPN's Long-Awaited Linux CLI is Finally Here
======

[Proton VPN][1] (partner link) is one of the most trusted privacy-focused VPN services. It offers a free plan, strong no-logs policies, and open source apps for multiple platforms.

The service is known for its focus on security and transparency, making it a popular choice for people who value privacy and control over their online activity.

Linux users [have long requested][2] a proper command-line interface for it. While the earlier CLI was useful, recent development focused on GUI apps. Fortunately, their requests have now been addressed.

### Proton VPN CLI App (Beta): What to Expect?

![][3]

The new CLI app lets Linux users connect and disconnect from VPN servers and select servers by country, city, or specific server for paid plans. It is fast, lightweight, and removes the need to use the desktop GUI.

**The CLI is still in beta**. Current limitations include only supporting the [WireGuard][4] protocol, **no advanced features** such as NetShield, Kill Switch, Split Tunneling, or Port Forwarding, and settings must be edited via config files. Proton is shipping the essentials first and plans to expand features according to user feedback.

This was announced as part of the Proton VPN 2025-26 [fall and winter roadmap][5]. The update also mentions **an upcoming auto-launch feature for Linux** , allowing the VPN to start automatically at boot.

Beyond the CLI, [Proton VPN][1] ( _partner link_ ) is set to roll out **a new network architecture** designed for faster speeds, better reliability, stronger anti-censorship, and post-quantum encryption. Free-tier users gain **new server locations** in Mexico, Canada, Norway, Singapore, and more.

![][6]

#### How Does it Hold Up?

![][7]

I configured it to run on an [Ubuntu 25.10][8] system. The **initial setup was a bit tricky** , especially for a GUI-first user like me, but running `protonvpn -h` made it relatively simple to figure out how to sign in and connect to servers.

Once I was connected to their Seattle server, I ran a speed test using [fast.com][9] and got speeds close to what my usual 300 Mbps fiber connection gives me ( _I am located in India, btw_ ), which was impressive.

**You can try this early version of the Proton VPN CLI** for Linux by following one of the official guides linked below:

  * [Debian][10]
  * [Ubuntu][11]
  * [Fedora][11]



Make sure you first install the " _Beta_ " Linux app as described in the guides above. Once that’s done, **run the additional command listed below** for your specific distro to get the CLI client.

![][12]

**Debian/Ubuntu:** `sudo apt update && sudo apt install proton-vpn-cli`

**Fedora:** `sudo dnf check-update --refresh && sudo dnf install proton-vpn-cli`

**Use this command to launch** : `protonvpn`

**If you are on a different distro** , the CLI might work if it’s based on one of the above ( _e.g., an Ubuntu derivative_ ), but Proton doesn’t officially guarantee compatibility. Test it and let me know in the comments below, maybe?

[Proton VPN CLI (Beta)][13]

**Suggested Reads** 📖

![][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/proton-vpn-linux-cli/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://go.getproton.me/aff_c?offer_id=10&aff_id=1173
[2]: https://protonmail.uservoice.com/forums/932836-proton-vpn/suggestions/47439905-updated-command-line-interface-cli
[3]: https://itsfoss.com/content/images/2025/10/proton-vpn-cli-beta.png
[4]: https://www.wireguard.com/
[5]: https://protonvpn.com/blog/product-roadmap-winter-2025-2026
[6]: https://static.ghost.org/v5.0.0/images/link-icon.svg
[7]: https://itsfoss.com/content/images/2025/10/proton-vpn-cli-beta-speedtest.png
[8]: https://itsfoss.com/ubuntu-25-10-release/
[9]: https://fast.com/
[10]: https://protonvpn.com/support/official-linux-vpn-debian/#beta
[11]: https://protonvpn.com/support/official-linux-vpn-ubuntu#beta
[12]: https://itsfoss.com/content/images/2025/10/proton-vpn-cli-beta-installation.png
[13]: https://protonvpn.com/support/linux-beta
[14]: https://itsfoss.com/content/images/icon/android-chrome-192x192-314.png
[15]: https://itsfoss.com/content/images/icon/android-chrome-192x192-313.png
