[#]: subject: "Testing the Surfshark VPN GUI App on Linux"
[#]: via: "https://itsfoss.com/surfshark-vpn-linux-review/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Testing the Surfshark VPN GUI App on Linux
======

[![Warp Terminal][1]][2]

Surfshark VPN is a popular name in the VPN provider space.

They are known for their insane discounts available across their offerings, making it a competitive alternative to other VPN services. Like every other VPN, they have their pros and cons. So, you might want to explore all the [privacy-focused VPN services][3] before you settle with one.

With Surfshark, something stands out: **its Linux client.** Surfshark VPN offers a beautiful GUI app for Linux, offering an enhanced user experience compared to many VPN solutions available.

Naturally, many Linux users prefer using it for the GUI. Here, I test the Surfshark VPN with the Linux client and share my experience with you to decide better.

✋

****Non-FOSS Warning!**** Surfshark VPN is covered here only because it has a desktop client available for Linux and is a privacy-focused tool. It is not open-source.

### Surfshark VPN: What About It?

![][4]

📋

The article contains affiliate links. Please read our [affiliate policy][5].

Surfshark VPN is an interesting solution geared towards **privacy, speed, and online security.**

It costs you less than **$3/month** and about **$5/month** for all the bells and whistles for better privacy. Safe to say, it is one of the most affordable options on the internet.

The **Surfshark Starter plan** provides you with access to **the VPN, tracker blocking tech, masked email generator ( _ **email aliases**_ ), and personal detail generator ( _ **generating random name/address info**_ ).**

💡

Surfshark VPN offers a 30-day money-back guarantee if you do not like the service.

[Surfshark (partner link)][6]

And, if you are willing to spend more, you can get access to the following features:

  * **Credit card and ID breach alerts**
  * **Email breach alerts**
  * **Private search tool**
  * **Antivirus protection**
  * **Data removal service (only available for certain countries)**



Before I start sharing my VPN experience, I also did a quick background check on the audits available on Surfshark VPN services. The last available [2021 security audit report by Cure53][7] tells me that Surfshark proactively works on security issues, and a [2022 Deloitte independent audit][8] checked for the claims for its “No log” policies.

Sure, they could use presenting a recent audit report. However, one of the competitors, Proton VPN, also showcases its [2021 audit report][9] as its latest (at the time of writing this). So, no big complaints.

📋

Surfshark VPN shares the same parent company as Nord VPN.

In addition to the audits, you have to trust the VPN provider for whatever they claim. You can't take my word or anyone else'.

I believe Surfshark VPN makes a decent effort to provide independent audits/assurances for its users.

Moving on from the essentials, let me highlight my experience with it.

### The Linux User Experience With Surfshark

![][10]

**I found it impressive in terms of look and feel.**

I tested it on **Ubuntu 24.04 LTS** , and it worked fine with it added as a startup app every time I reboot the system.

It officially supports **Ubuntu 20.04 or above, Debian 11, and Mint 20** **or above.** You can try installing the .deb package on any Ubuntu-based distro. However, it is best to stick to the supported distros for the VPN.

You can install the Linux client using a couple of commands in the terminal:

```

    curl -f https://downloads.surfshark.com/linux/debian-install.sh --output surfshark-install.sh #gets the installation script
    cat surfshark-install.sh #shows script's content
    sh surfshark-install.sh #installs surfshark

```

If you do not need the GUI, you can always [set it up manually using OpenVPN][11].

But, of course, looking at the pretty GUI doesn't cut it — you need it to perform well, right?

### VPN Performance

Before I enable the VPN, I must mention that I have a **200 Mbps internet connection plan**. With the plan, I get download speeds up to **230–240 Mbps** and upload speed of **150–200 Mbps**.

So, what happens when I enable the Surfshark VPN?

I went with the fastest/nearest location suggested by Surfshark VPN (i.e, UAE), and connected to the server. And, then performed a speed test, here's how it looked:

![][12]

I tested this a couple of times throughout the day, the download speed was consistent, with upload speed getting affected (sometimes a little less or more).

Just as a reference, I switched on Proton VPN connection to a server in the same location (UAE), and see how it fares:

![][13]

Overall, the average speeds recorded were:

  * 220 Mbps — download
  * 80 Mbps — upload



Of course, if you utilize a MultiHop connection (through two different servers), the connection speed will get impacted.

📋

Unfortunately, I wasn't able to make MultiHop connections work ( _ _every selection was failing to have an exit location__ ) using WireGuard. It worked with OpenVPN protocol.

The same was the case for "Static IP" servers, supposedly, they have a particular IP address assigned to the server, which you can use. Additionally, you can opt for a dedicated IP address (for extra charges) if that is something you need.

Overall, the standard VPN connection mode (using WireGuard) is good to recommend.

However, if you experience connection failures, you can try changing the protocol within the app:

![][14]

### Extra Features and Privacy

With Surfshark VPN, you can choose to get rid of the trackers and protect against malware using your VPN. No need for special add-ons for your web browser; the VPN does the job.

![][15]

As you can notice, by default, the protocol is automatically selected for you. WireGuard is the one you will find for most use-cases. You can change it to your required selection.

You can also enable the " **Kill Switch** ", an essential/common feature seen across all VPNs. It disables internet access if a VPN connection has dropped, so your IP/DNS isn't accidentally leaked.

You do not get access to other features like [alternative ID][16], private search, breach alert, and others on the Linux app ( _even if you have them on your subscription_ ). But, if you download the browser extension, you can access them.

Here's how it looks:

![][17]

Of course, the **antivirus feature is limited to scanning malware/threats on websites** through the extension. When it comes to device scanning, it should work with mobile devices and Windows/macOS.

Now, coming to the privacy part, I tested if there's an IP/DNS leak:

📋

I do not use the test pages provided by the VPN providers, as when you go for an IP leak test, it always says that you are unprotected (unless they detect an IP from their service).

[IPleak.net][18] is a good web tool that I use to test both IP/DNS leaks. And, everything looks good here, no leaks:

![][19]

I also test DNS leaks using another tool — [DNS Leak Test][20].

![][21]

Everything looks as it should, which is a good thing 😃

### Wrapping Up

Surfshark VPN is a good for the most part, except for some connection drops using WireGuard (which was fixed by switching to the OpenVPN protocol).

The speeds are on par with competing VPNs and the GUI for Linux is a plus with all the features included with the extension.

[Learn more about Surfshark (partner link)][6]

_What are your thoughts on using Surfshark VPN Linux client? Let me know in the comments down below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/surfshark-vpn-linux-review/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/best-vpn-linux/
[4]: https://itsfoss.com/content/images/2024/05/surfshark-vpn-login.png
[5]: https://itsfoss.com/affiliate-policy/
[6]: https://get.surfshark.net/aff_c?offer_id=926&aff_id=13591
[7]: https://surfshark.com/blog/surfshark-server-infrastructure-undergoes-independent-audit
[8]: https://surfshark.com/blog/deloitte-audit-nologs
[9]: https://proton.me/community/open-source
[10]: https://itsfoss.com/content/images/2024/05/surfshark-vpn-1.png
[11]: https://support.surfshark.com/hc/en-us/sections/4414393364754-Manual-setup
[12]: https://itsfoss.com/content/images/2024/05/surfshark-speed-test-1.png
[13]: https://itsfoss.com/content/images/2024/05/protonvpn-speed-test.png
[14]: https://itsfoss.com/content/images/2024/05/surfshark-protocols.png
[15]: https://itsfoss.com/content/images/2024/05/surfshark-vpn-clean-web.png
[16]: https://get.surfshark.net/aff_c?offer_id=1421&aff_id=13591
[17]: https://itsfoss.com/content/images/2024/05/surfshark-vpn-alternative-id.png
[18]: https://ipleak.net/
[19]: https://itsfoss.com/content/images/2024/05/surfshark-vpn-ipleak-net.png
[20]: https://www.dnsleaktest.com/
[21]: https://itsfoss.com/content/images/2024/05/dns-leak-test-surfshark.png
