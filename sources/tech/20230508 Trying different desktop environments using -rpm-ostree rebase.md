[#]: subject: "Trying different desktop environments using “rpm-ostree rebase”"
[#]: via: "https://fedoramagazine.org/trying-different-desktop-environments-using-rpm-ostree/"
[#]: author: "Jakub Sierżęga https://fedoramagazine.org/author/kuba3351/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Trying different desktop environments using “rpm-ostree rebase”
======

![][1]

Photo by [NordWood Themes][2] on [Unsplash][3]

Fedora Linux Workstation features a GNOME desktop environment which is an easy to use, intuitive, and efficient desktop environment. But this is not the only option if you would like to use Fedora Linux. There are other spins that provide alternative desktop environments like KDE, XFCE, Cinnamon, etc. This article describes how you can try different desktop environments if you are using an OSTree based Fedora Linux spins.

### Main version of Fedora Workstation

If you installed a non-OSTree Fedora Workstation or one of the Spins and would like to try different desktop environment, you have some possibilities:

  * install different desktop environment using _dnf_
  * dual boot multiple spins of Fedora



If you choose the first option, you have to install another desktop environment by using the _dnf install_ command. This technique enables you to select which desktop environment you would like to use on the login screen after system boots. Using this method will pull in a lot of dependencies. This is especially true when you have a GTK based desktop environment (like GNOME) and install a QT based (like KDE), or vice-versa. It can be difficult to completely uninstall one of the installed desktop environment if you are not satisfied with them.

Another issue with this is that system apps may be doubled in the application menu on each environment. For example, if you have installed GNOME and install KDE, you have Nautilus and Dolphin for browsing files, GNOME Terminal and Konsole for terminal emulation, etc. You have to remember which app to use on which environment, because apps from KDE behave worse on GNOME and vice-versa.

If you choose the second option, you have to make some free unpartitioned space on your hard drive to install another Fedora spin alongside one you are currently using. In this way, the systems are separated from each other and the system apps will not be doubled. You can decide to share the _/home_ partition between them. This technique enables you select the system to use in the bootloader menu before system boots. But if you use this method, you have to maintain these systems separately (for example installing updates) and it consumes a lot of free space on the hard drive.

### OSTree based version of Fedora Workstation

Some variants of Fedora Linux are OSTree based. OSTree provides immutability and transactional upgrades with the possibility of rollback in case something goes wrong. You can read more about it in [this great article.][4] Right now, we have three OSTree based Fedora Workstation variants:

  * Silverblue – provides GNOME desktop environment
  * Kinoite – provides KDE Plasma desktop environment
  * Sericea – provides Sway window manager (not recommended for beginners)



If you are running one of these variants of Fedora Linux, you can easily switch your system to another OSTree compatible one to try different desktop environment. This process is similar to doing a system upgrade. OSTree guarantees that the operation is transactional (finishes successfully or nothing is changed) and you are able to rollback if you are not satisfied with the change. The operation does not consume much space on the hard drive, and system apps are not doubled.

#### How to use OSTree rebase to switch to a new variant

To start, I recommend executing the following command to pin the current deployment. This makes certain it will not be deleted automatically in the future and provides the ability to roll back to it.

```

    $ sudo ostree admin pin 0

```

If you have a pending update, the command may fail with the message:

```

    error: Cannot pin staged deployment

```

In this case, reboot your system to apply pending updates, and try again.

After pinning the deployment, execute:

```

    $ ostree remote refs fedora

```

It outputs a list of all available branches that you can rebase into. Every branch has an architecture, version, and the name of the variant. Select carefully. In the following examples I assume you would like to rebase into the current stable version of Fedora for x86_64 (version 38).

  * for Fedora Silverblue, use fedora:fedora/38/x86_64/silverblue
  * for Fedora Kinoite, use fedora:fedora/38/x86_64/kinoite
  * for Fedora Sericea, use fedora:fedora/38/x86_64/sericea



Choose the branch you wish to rebase into and execute the following command (change the branch name provided in the example if necessary):

```

    $ rpm-ostree rebase fedora:fedora/38/x86_64/kinoite

```

When this command succeeds, restart the system to begin using the new desktop environment. If it fails, the system should continue to work unmodified thanks to transactional updates provided by OSTree.

#### Undo the rebase into an OSTree variant

If you are not satisfied with the new environment the following command will return you to your original variant:

```

    rpm-ostree rollback

```

Restart your system once again to switch back to the previous variant of Fedora.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/trying-different-desktop-environments-using-rpm-ostree/

作者：[Jakub Sierżęga][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/kuba3351/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/05/try_de_using_ostree_rebase-816x345.jpg
[2]: https://unsplash.com/@nordwood?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/E9tFH39iRPE?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://fedoramagazine.org/pieces-of-fedora-silverblue/
