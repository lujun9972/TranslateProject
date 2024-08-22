[#]: subject: "Oh, no! Windows Security Update Breaks Dual-Boot Linux Systems"
[#]: via: "https://news.itsfoss.com/windows-breaks-linux-dual-boot/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Oh, no! Windows Security Update Breaks Dual-Boot Linux Systems
======
As if Linux users weren't disappointed enough with Microsoft Windows...
[![][1]][2]

[Microsoft][3] is known for their signature, “ _my way or the highway_ ” approach when it comes to their offerings, with the Windows operating system being the most prominent one among those.

Many in the FOSS community disagree with that approach, with a [strong rejection][4] of such practices, suggesting people go for more open options for their operating systems and applications, and I agree with them.

Unfortunately, that same approach has now **affected many Linux distribution users** , who were sent scampering searching for a fix to a problem caused by a Windows update ( _who would've expected that?)_.

### Microsoft Slips Up: Linux Users Beware!

![Source: paku1234][5]

First spotted by [Ars Technica][6], a monthly Windows update pushed on August 13 that included a fix to a two-year-old vulnerability, [CVE-2022-2601][7], with an **8.6 CVSS severity rating** , caused dual-boot systems with Windows and Linux distros to **not boot**.

That **fix was meant to tackle an issue with the GRUB bootloader** , which allowed malicious actors from carrying out-of-bound writes, and possibly bypass secure boot.

But, it caused some collateral damage in the process. After updating, many users, including users of [Ventoy][8], and [Ubuntu 24.04][9], reported that they were shown the following error:

> Verifying shim SBAT data failed: Security Policy Violation
>
> Something has gone seriously wrong: SBAT self-check failed: Security Policy Violation

This update installed an [SBAT][10], which is an acronym for _Secure Boot Advanced Targeting_ , a Linux-focused method for discarding various components in the boot path using generation numbers embedded into the EFI binaries. ( _apologies for the jargon_ )

However, **this mechanism was meant to run with devices only running Windows** , and, [according to Microsoft][11], this should not have caused any issues on dual-boot systems, at least on newer Linus distributions.

But, as we know already, it did. 😑

Following these revelations, in [a statement][12], Microsoft mentioned that they were aware of “ _some secondary boot scenarios are causing issues for some customers_ ”, and that they were working with their Linux partners to investigate and address the issue.

Thankfully, **the community has come to the rescue** , with [manutheeng][13], a member of the Linux Mint forums, finding [a solution][14] for Ubuntu in an old post on the [Ubuntu forums][15].

#### The Solution

  * First, disable Secure Boot from the UEFI menu.
  * Then, log into Ubuntu with the user of your choice.
  * Now, open a terminal and execute the following command:



```

     sudo mokutil --set-sbat-policy delete

```

  * After that, reboot your PC to see the changes.
  * Now, if you'd like, you can re-enable Secure Boot from the UEFI menu.



The above steps should also work with any [Ubuntu-based][16] Linux distribution. If that doesn't work, then you might be facing what a Framework laptop user [faced][17].

#### Closing Thoughts

If dual-boot systems were more common, then this issue would've been treated with more haste, like the [CrowdStrike incident][18] that took place last month, but that was not Microsoft's fault.

So, it's better than nothing. 🙂

Ultimately, there's still the matter of [Secure Boot][19] being an absolute mess, that has left many people questioning whether this could've been implemented in a better way.

I think that it could've, the PC industry rushed its implementation before it was ready.

_💬 What about you? Were you impacted by these Windows update shenanigans? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/windows-breaks-linux-dual-boot/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.microsoft.com/
[4]: https://x.com/siptruk/status/1817411166139826540
[5]: https://news.itsfoss.com/content/images/2024/08/Windows_Dual_Boot_Error.png
[6]: https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/
[7]: https://msrc.microsoft.com/update-guide/en-US/advisory/CVE-2022-2601
[8]: https://github.com/ventoy/Ventoy/issues/2947
[9]: https://community.frame.work/t/sbat-verification-error-booting-linux-after-windows-update/56354
[10]: https://www.gnu.org/software/grub/manual/grub/html_node/Secure-Boot-Advanced-Targeting.html
[11]: https://msrc.microsoft.com/update-guide/en-US/advisory/CVE-2022-2601#:~:text=The%20SBAT%20value%20is%20not%20applied%20to%20dual%2Dboot%20systems%20that%20boot%20both%20Windows%20and%20Linux%20and%20should%20not%20affect%20these%20systems.
[12]: https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/#:~:text=This%20update%20is%20not%20applied%20when%20a%20Linux%20boot%20option%20is%20detected.%20We%20are%20aware%20that%20some%20secondary%20boot%20scenarios%20are%20causing%20issues%20for%20some%20customers%2C%20including%20when%20using%20outdated%20Linux%20loaders%20with%20vulnerable%20code.%20We%20are%20working%20with%20our%20Linux%20partners%20to%20investigate%20and%20address.
[13]: https://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=381346
[14]: https://forums.linuxmint.com/viewtopic.php?t=427297&sid=dab5f35699069b1d030e710a1eb3c793#:~:text=rev%20...%20cess/34996-,In%20case%20this%20can%20help%20anyone%2C%20here%20is%20what%20worked%20for%20me%3A,-1.%20Disable%20Secure
[15]: https://discourse.ubuntu.com/t/sbat-revocations-boot-process/34996
[16]: https://itsfoss.com/best-ubuntu-based-linux-distros/
[17]: https://community.frame.work/t/sbat-verification-error-booting-linux-after-windows-update/56354/2
[18]: https://en.wikipedia.org/wiki/2024_CrowdStrike_incident
[19]: https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-secure-boot
