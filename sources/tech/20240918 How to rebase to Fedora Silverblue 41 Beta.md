[#]: subject: "How to rebase to Fedora Silverblue 41 Beta"
[#]: via: "https://fedoramagazine.org/how-to-rebase-to-fedora-silverblue-41-beta/"
[#]: author: "Michal Konečný https://fedoramagazine.org/author/zlopez/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to rebase to Fedora Silverblue 41 Beta
======

![][1]

[Silverblue][2] is an operating system for your desktop built on Fedora Linux. It’s excellent for daily use, development, and container-based workflows. It offers [numerous advantages][3] such as being able to roll back in case of any problems. This article provides the steps to upgrade to the [newly released Fedora Linux 41 Beta][4], and how to revert if anything unforeseen happens.

Before attempting an upgrade to the Fedora Linux 41 Beta, apply any pending upgrades.

### Updating using terminal

Because the Fedora LInux 41 Beta is not available in GNOME Software, the whole upgrade must be done through a terminal.

First, check if the 41 branch is available, which should be true now:

```

    $ ostree remote refs fedora

```

You should see the following line in the output:

```

    fedora:fedora/41/x86_64/silverblue

```

If you want to pin the current deployment (this deployment will stay as an option in GRUB until you remove it), you can do it by running:

```

    # 0 is entry position in rpm-ostree status
    $ sudo ostree admin pin 0

```

To remove the pinned deployment use following command (2 corresponds to the entry position in the output from rpm-ostree status ):

```

    $ sudo ostree admin pin --unpin 2

```

Next, rebase your system to the Fedora 41 branch.

```

    $ rpm-ostree rebase fedora:fedora/41/x86_64/silverblue

```

Finally, the last thing to do is restart your computer and boot to Fedora Silverblue 41 Beta.

### How to revert

If anything bad happens — for instance, if you can’t boot to Fedora Silverblue 41 Beta at all — it’s easy to go back. Pick the previous entry in the GRUB boot menu (you need to press ESC during boot sequence to see the GRUB menu in newer versions of Fedora Silverblue), and your system will start in its previous state. To make this change permanent, use the following command:

```

    $ rpm-ostree rollback

```

That’s it. Now you know how to rebase to Fedora Silverblue 41 Beta and fall back. So why not do it today?

### Known Issues

  * [Incorrect check for static configs with bootupd leads to no /boot/loader/grub.cfg after reboot][5]
We advise users to hold on testing bootupd on their updated Fedora Atomic Desktops & IoT systems until this bug is resolved.



### FAQ

Because there are similar questions in comments for each blog about rebasing to newer version of Silverblue I will try to answer them in this section.

**Question: Can I skip versions during rebase of Fedora Linux? For example from Fedora Silverblue 39 to Fedora Silverblue 41?**

Answer: Although it could be sometimes possible to skip versions during rebase, it is not recommended. You should always update to one version above (39->40 for example) to avoid unnecessary errors.

**Question: I have[rpm-fusion][6] layered and I got errors during rebase. How should I do the rebase?**

Answer: If you have [rpm-fusion][6] layered on your Silverblue installation, you should do the following before rebase:

```

    rpm-ostree update --uninstall rpmfusion-free-release --uninstall rpmfusion-nonfree-release --install rpmfusion-free-release --install rpmfusion-nonfree-release

```

After doing this you can follow the guide in this blog post.

**Question: Could this guide be used for other ostree editions (Fedora Atomic Desktops) as well like Kinoite, Sericea (Sway Atomic), Onyx (Budgie Atomic),…?**

Yes, you can follow the _Rebasing using the terminal_ part of this guide for every ostree edition of Fedora. Just use the corresponding branch. For example for Kinoite use fedora:fedora/41/x86_64/kinoite

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-to-rebase-to-fedora-silverblue-41-beta/

作者：[Michal Konečný][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zlopez/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/silverblue-f41-beta-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/fedora-silverblue/
[3]: https://fedoramagazine.org/give-fedora-silverblue-a-test-drive/
[4]: https://fedoramagazine.org/announcing-fedora-linux-41-beta/
[5]: https://bugzilla.redhat.com/show_bug.cgi?id=2312453
[6]: https://rpmfusion.org/
