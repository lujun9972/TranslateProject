[#]: subject: "The XZ Utils Backdoor in Linux: How it Happened"
[#]: via: "https://news.itsfoss.com/xz-utils-backdoor/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The XZ Utils Backdoor in Linux: How it Happened
======
It was just moments before a disastrous security incident happened.
It's not limited to Linux, or limited to open-source, cybersecurity attacks exist in every corner of the software industry. And, every day, there's someone new who sets out to target the software supply chain with their attacks.

However, when something affects Linux, or an open-source library in it, the cyberattack leaves ripple effects that can shake up the entire world.

**Why? Because Linux is almost everywhere.** So, any security flaw discovered needs timely fixes.

And, that is how it usually goes, until the XZ Utils backdoor was discovered 🤯

💡

XZ Utils is a data compression software included in Linux distributions and Unix-like operating systems. You can compress/decompress various files with it.

### The Undetected Linux Backdoor

**Andres Freund,** a Microsoft developer, [spotted][1] the backdoor when he was investigating the errors around ssh logins and connections.

He was trying to fix performance issues on his Debian sid installations, where he found something specific as the root cause of all the errors.

To his shock, he found out that a backdoor had been planted in the upstream [xz repository][2], and tarballs that lead to **ssh server compromise**.

The affected versions include:

  * **5.6.0**
  * **5.6.1**



**How did the backdoor make its way?**

The backdoor was added in the form of an obfuscated malicious script through harmless-looking commits to the project. Unlike some malicious code injection, it was not just a single commit.

The contributor (or the team behind it) started interacting with the xz repository since 2022 😲

Unfortunately, we cannot look at the commit details anymore as the repo has been disabled by GitHub.

In other words, it was a planned cyberattack with months/years of preparation to inject a malicious script to an open-source software used by major Linux distributions.

**What was the aim of the backdoor? And, how was it supposed to work?**

![][3]

Of course, disrupting systems, installing malware, or stealing something was one of the objectives of the backdoor. The malicious script was executed at the end of the configuration process, which modified certain files.

It can be triggered by a remote unprivileged system connecting to SSH ports.

Red Hat [explains][4] that the malicious script interferes with authentication in sshd via systemd. Moreover, they mention — " _Under the right circumstances this interference could potentially enable a malicious actor to break sshd authentication and gain unauthorized access to the entire system remotely._ "

The vulnerability is still being investigated.

However, it can surely affect the integrity and performance of the compromised systems.

Even though not all Linux distributions are vulnerable to it, here are the ones affected:

  * Fedora 41
  * Fedora Rawhide
  * Debian testing/unstable/experimental editions
  * openSUSE Tumbleweed and openSUSE MicroOS
  * Kali Linux
  * Fedora 40 beta



If you have recently upgraded to Fedora 40 beta to get your hands on the latest tech, you can either choose to downgrade the xz libraries to 5.4.x versions or apply the latest update. The update should automatically revert the library to an older version not impacted by the vulnerability.

You can get technical details about the vulnerability with its assigned [CVE-2024-3094][5].

### A Sophisticated Cyberattack Attempt

What if the developer did not give attention to details?

We would have never found out, and the cyberattack would probably have been a success, making a real dent in the open-source community.

And, that says a lot about dangerous cyberattacks, and the motive behind it.

A senior security researcher at Microsoft [visualized][6] his analysis to give us a better view of the entire ordeal. Here's how that looks:

![Image Credits: Thomas Roccia \(infosec.exchange\)][7]

Taking everything into account, the takeaway is, a mix of social engineering, obfuscation, and advanced knowledge of the software can let attackers sneak into the code/platform.

While some of you could point fingers at the open-source project, but that is how vulnerabilities are discovered. Sometimes, you notice it way before it does any damage, sometimes a bit later, or a little too late.

That's how the security scene goes. The cyberattacks evolve, and developers/security researchers adapt after learning something new.

There's no one to blame here, if you ask me.

However, we do have to thank the open-source nature of the code, and the developer who spotted it.

So, the open-source nature of Linux is what makes it secure, it actually allows peers to review the code, giving more eyes, and making it tougher for attackers to easily do something.

Whatever the case, you should always keep your system up-to-date, so the distro maintainers can push security updates to address vulnerabilities like these on time.

_💭What do you think about the XZ Utils backdoor? Do you think something like this could exist presently, and we would have no idea about it?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/xz-utils-backdoor/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://www.openwall.com/lists/oss-security/2024/03/29/4
[2]: https://github.com/tukaani-project/xz
[3]: https://news.itsfoss.com/content/images/2024/04/backdoor-xz.png
[4]: https://www.redhat.com/en/blog/urgent-security-alert-fedora-41-and-rawhide-users
[5]: https://access.redhat.com/security/cve/CVE-2024-3094
[6]: https://infosec.exchange/@fr0gger/112189232773640259
[7]: https://news.itsfoss.com/content/images/2024/04/xz-visual-ft.png
