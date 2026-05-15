[#]: subject: "How Fedora is responding to recent Kernel vulnerabilities"
[#]: via: "https://fedoramagazine.org/how-fedora-is-responding-to-recent-kernel-vulnerabilities/"
[#]: author: "Daniel Milnes https://fedoramagazine.org/author/thebeanogamer/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How Fedora is responding to recent Kernel vulnerabilities
======

![Banner showing a drawing of a padlock and the text "How Fedora is responding to recent Kernel vulnerabilities".][1]

[Illustration][2] by [Boxicons][3] on [Unsplash][4]

The last few weeks have seen a significant spike in reports of security vulnerabilities in the Linux Kernel. [CopyFail][5], [DirtyFrag][6], and [Fragnesia][7] have all exposed a path for a malicious user to escalate their privileges on a system from a standard user to root, and it’s possible there are more vulnerabilities that will be found. The Fedora Project is committed to keeping its users secure and patched against vulnerabilities as quickly as possible when they are disclosed, so let’s talk about how we try to do that.

Recent developments in machine learning have lead to a veritable gold rush for security researchers who can now rely on LLMs to analyze massive code bases like the Linux Kernel and find vulnerabilities at a rate well above what was previously possible. LLMs are also being used to weaponize these vulnerabilities once they’ve been found, allowing attackers to significantly shorten the gap between vulnerability disclosure and exploitation in the wild ([source][8]). All this means that it’s more important than ever for Fedora to have a robust process for tracking these vulnerabilities and distributing fixes for them.

### What Fedora is doing

There are a number of ways the Fedora Package Maintainers get notified of new security vulnerabilities, the simplest of which is through security bulletins. Many projects post about their security updates on places like the _oss-security_ mailing list and several Fedora contributors monitor these mailing lists for relevant vulnerabilities. The [Red Hat Product Security][9] team will also often raise Bugzilla bugs against Fedora packages for CVEs they are tracking, allowing Fedora to take advantage of the work being done to support RHEL customers.

Often security updates will flow through the usual Fedora package update process. Fedora uses tools like [Anitya][10] and [Packit][11] to monitor for new releases of upstream packages and automatically prepare updates for them. This automation helps across all updates with achieving [Fedora’s “First” foundation][12], but they’re especially helpful for security updates which can be extremely time-sensitive to publish. If everything works as designed, by the time a human gets involved in preparing the update, there could already be a pull request and scratch build ready for testing.

Once the Fedora Package Maintainers are aware of a security vulnerability in a package we distribute, we’ll evaluate the best way to make the patch available to users of supported Fedora releases. Often this just means publishing the latest version of the package, but sometimes this isn’t possible. If the fix has not yet been merged in the upstream project (as happened with the recent kernel vulnerabilities) or if the latest version is too far from the current package version in that Fedora release ([more information][13]), the fix may be applied as a standalone patch. This can lead to a situation where a fixed version of the package is available but the version number still shows the vulnerable version, so you can use the _dnf changelog_ command to check the update history for the package and see if a patch has been applied.

### Keeping your system secure

It may sound cliché, but for most users the best thing you can do to keep your system secure is regularly updating it. Security package updates in Fedora are tagged with their severity and CVE numbers, so you can keep track of when security updates are published into Bodhi ([for example][14]). You can also apply all the pending security updates on your system using the following command:

```

    dnf update --security

```

Some desktop environments will proactively notify users if there are pending security updates for their system. For example, GNOME Software will periodically check for pending updates and send the user a toast notification like the one below prompting to install the updates.

![][15]

If you’d like to automate patching vulnerable packages, _dnf-automatic_ can be configured to automatically download and apply security updates on a schedule, although applying kernel upgrades will require rebooting the system. You can learn more about this in the documentation [here][16].

### Getting involved

If this kind of Open Source security sounds interesting to you, why not consider becoming a Fedora contributor? We’re always looking for more people to get involved with projects like the [Security SIG][17] and [Kernel Maintenance][18]!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-fedora-is-responding-to-recent-kernel-vulnerabilities/

作者：[Daniel Milnes][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/thebeanogamer/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/05/fedorablog-816x345.jpg
[2]: https://unsplash.com/illustrations/an-open-black-padlock-icon-on-a-white-background-MWCbAefWxlc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/@boxicons/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://unsplash.com/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[5]: https://access.redhat.com/security/cve/cve-2026-31431
[6]: https://access.redhat.com/security/cve/cve-2026-43284
[7]: https://access.redhat.com/security/cve/cve-2026-43500
[8]: https://zerodayclock.com/
[9]: https://www.redhat.com/en/solutions/security-approach
[10]: https://release-monitoring.org/
[11]: https://packit.dev/
[12]: https://docs.fedoraproject.org/en-US/fesco/Updates_Policy/#_fedoras_first_foundation
[13]: https://docs.fedoraproject.org/en-US/fesco/Updates_Policy/#stable-releases
[14]: https://bodhi.fedoraproject.org/updates/FEDORA-2026-4462efc052
[15]: https://fedoramagazine.org/wp-content/uploads/2026/05/image-4.png
[16]: https://dnf5.readthedocs.io/en/stable/dnf5_plugins/automatic.8.html
[17]: https://docs.fedoraproject.org/en-US/security/
[18]: https://docs.fedoraproject.org/en-US/quick-docs/kernel-overview/#community
