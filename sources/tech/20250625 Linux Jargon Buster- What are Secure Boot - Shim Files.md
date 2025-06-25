[#]: subject: "Linux Jargon Buster: What are Secure Boot & Shim Files?"
[#]: via: "https://itsfoss.com/secure-boot-shim-file/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Jargon Buster: What are Secure Boot & Shim Files?
======

[![Warp Terminal][1]][2]

If you’re a Linux user, you might have found yourself tangled in boot issues while installing your favorite distro especially if "Secure Boot is" in the picture.

Secure Boot is meant to add an extra layer of protection to our systems, preventing unverified software from running at boot. Sounds like a win, right?

Well, not always. For Linux users, Secure Boot can often feel like more of a hassle than a help, leading to issues, failed installations, and troubleshooting headaches.

Take, for instance, the [Ubuntu 21.04 release fiasco][3], where the latest shim files (used to enable Secure Boot on Linux) had compatibility issues with early EFI firmware, causing some users’ systems to become unbootable after an upgrade.

Ubuntu eventually released a fix, but not before many users found themselves troubleshooting or even downgrading to older shims just to get their systems to boot.

But what exactly is Secure Boot, how do shim files play a role, and when should you consider disabling it?

In this guide, I’ll break down Secure Boot in simple terms and explain how it affects Linux installations, including what you can do if it gets in the way.

### What is Secure Boot?

Imagine your computer as a castle with a strong gatekeeper who checks the ID of anyone trying to enter.

[Secure Boot][4] is like that gatekeeper, making sure only trusted, safe programs get to run during the initial phase of starting up your computer, also known as the What are Secure Boot & Shim Files? **boot process**.

Secure Boot is a security standard developed to keep your computer safe from malware that could sneak in and start doing harmful things even before the operating system (OS) fully loads.

It is part of what's called the [**Unified Extensible Firmware Interface (UEFI)**][5], which replaced the older BIOS system. UEFI is a modern way for your computer to boot up and check everything is working as expected.

When Secure Boot is turned on, your computer will only load software/operating system with a special signature or “stamp” of approval.

If something without this signature tries to load, Secure Boot stops it, protecting your computer from potential harm.

### How does Secure Boot work?

Secure Boot uses a **chain of trust** with different types of cryptographic keys (think of them as digital ID cards) to verify each step of the boot process. Here’s a simple breakdown:

**Platform Key (PK)** : This is like the master key, usually held by the device maker (like Dell, HP, etc.). It’s the root of the verification process.

**Key Exchange Key (KEK)** : This key confirms whether other keys can be trusted, acting as a bridge between the platform key and bootloaders.

**Allowed Database (DB)** : Contains a list of approved signatures for software that’s allowed to load.

**Forbidden Database (DBX)** : Stores signatures of known, unsafe programs. If something tries to load from this list, Secure Boot blocks it.

During startup, Secure Boot checks each program that tries to load against these keys and databases. Only programs that have valid, signed keys will run, making sure your system stays secure.

![Image Credit: RedHat][6]

### What are Shim files?

Now, let’s say you’re trying to run Linux on a Secure Boot-enabled computer. Linux doesn’t always have the same pre-approved signatures as Windows, so that’s where **Shim** files come in.

A **Shim** is a small program that acts like a translator between Secure Boot and the Linux OS. The Shim file is signed with a key that Secure Boot recognizes (often by Microsoft), so it’s allowed to load.

The Shim then verifies the signature of the Linux bootloader (like [GRUB][7]) and passes control to it if everything checks out.

This process creates a “chain of trust” from Secure Boot to Linux, so the OS can load securely even on a Secure Boot-enabled system.

### Why Secure Boot is important?

Secure Boot is crucial because it provides a defense against one of the most dangerous kinds of malware: **bootkits and rootkits**.

These are malicious programs that try to hide themselves in the boot process, allowing them to run before the OS is fully up and running. They can be hard to detect and even harder to remove.

With Secure Boot:

  * **Bootkits** and **rootkits** are blocked from loading by the signature check.
  * **Tampered or unauthorized programs** are prevented from affecting the boot process.
  * **Users are alerted** if something is wrong, so they can address potential issues before they become serious problems.



### When you might need to disable Secure Boot

Secure Boot is great for security, but there are times when it can cause issues:

  * **Installing unsigned operating systems** : Some operating systems, especially certain Linux distributions, may not have the required signatures to pass Secure Boot verification. If your OS isn’t recognized, Secure Boot will prevent it from loading.
  * **Using custom drivers or bootloaders** : Certain drivers or bootloaders might not be signed, which can cause compatibility issues.
  * **Advanced Configurations** : For power users who want to customize their systems, Secure Boot’s restrictions can feel limiting. Disabling it allows for greater flexibility, especially in homelab or development environments.



However, turning off Secure Boot also removes that extra layer of security, so it’s essential to proceed carefully.

### Which distros support Secure Boot?

While Secure Boot has posed compatibility challenges for Linux, many popular distributions have adapted to work smoothly with it.

These distros include signed bootloaders and shim binaries that allow them to run without issues on systems with Secure Boot enabled.

Most major Linux distributions now support Secure Boot. I can think of these at least:

  * Ubuntu
  * Fedora
  * openSUSE/SUSE
  * Zorin
  * Linux Mint
  * Debian
  * Red Hat



🚧

This is not an extensive list of all distros with secure boot support. There are many more distros out there that support secure boot. Please check their official websites for information.

Not all distributions offer Secure Boot support, so it’s worth verifying before installation if you plan to keep Secure Boot enabled.

For distros that don’t support Secure Boot directly, you can still disable it in the BIOS settings or manually add a trusted bootloader, though it requires some technical knowledge.

### How to disable Secure Boot (and why you should be careful)

If you decide that you need to [disable Secure Boot][8], here’s a simple guide:

🚧

Disabling Secure Boot makes your system more vulnerable to boot-level attacks. Ensure that you have other security measures in place, like keeping your OS up-to-date and using antivirus software.

  1. **Restart your computer** and enter the UEFI/BIOS settings (this usually involves pressing a key like `F2`, `F10`, or `DEL` during startup).
  2. **Find the Secure Boot option** : In the settings, look for “Secure Boot” under Security or Boot options.
  3. **Disable Secure Boot** : Set it to “Disabled.” Be sure to save changes and exit.



![][9]

### Final Thoughts

The discourse around Secure Boot is polarizing, and for good reason.

While it’s designed to enhance system security, it often imposes limitations on Linux users, especially those who rely on proprietary drivers or use less mainstream distributions.

The need for Microsoft-signed shims raises valid concerns about vendor lock-in and compatibility.

In my experience, especially with a dedicated graphics card on my gaming laptop, keeping Secure Boot off is almost a necessity.

With Secure Boot enabled, proprietary drivers tend to fail during installation, as I’ve seen firsthand on Pop!_OS. It’s a compromise I choose for compatibility, though it shouldn’t have to be this way.

This article is for those interested in understanding Secure Boot’s quirks and why your favorite distro might not boot up smoothly.

The debate is nuanced: is it a crucial security layer or an unnecessary barrier for Linux users? I’d love to hear where you stand on this discourse, let me know in the comments!

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][10].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][11] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][11]

--------------------------------------------------------------------------------

via: https://itsfoss.com/secure-boot-shim-file/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://news.itsfoss.com/ubuntu-21-04-upgrade-bug/
[4]: https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-secure-boot
[5]: https://uefi.org
[6]: https://itsfoss.com/content/images/2024/11/secure_boot_diagram_1-1.png
[7]: https://itsfoss.com/what-is-grub/
[8]: https://itsfoss.com/disable-secure-boot-windows/
[9]: https://itsfoss.com/content/images/icon/android-chrome-192x192-508.png
[10]: https://itsfoss.com/plus-member-resources/
[11]: https://itsfoss.com/lifetime-membership/
