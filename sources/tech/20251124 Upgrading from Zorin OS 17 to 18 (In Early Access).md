[#]: subject: "Upgrading from Zorin OS 17 to 18 (In Early Access)"
[#]: via: "https://itsfoss.com/zorin-os-18-upgrade/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Upgrading from Zorin OS 17 to 18 (In Early Access)
======

[![Warp Terminal][1]][2]

Last month, [Zorin OS 18][3] dropped just in time for the Windows 10 EOL, bringing about an assortment of improvements like Linux kernel 6.14, rounded corners for the desktop interface, and a new window tiling manager.

So, it didn't come as a surprise to me when [Zorin OS 18 hit the 1 million downloads milestone][4] just over a month after its release. Alongside that announcement, the developers have made available an upgrade path from [Zorin OS 17][5], which **is intended for users of Core, Education, and Pro editions**.

Let me walk you through the upgrade process. 😃

🚧

This upgrade path is currently in the testing phase. I don't recommend using it on your main computer or any production machine until the full rollout.

### Before You Upgrade to Zorin OS 18

![Zorin OS uses Déjà Dup as the backup utility.][6]

First, **ensure that you are running Zorin OS 17.3** , the last point release. Then, create a backup of your files before upgrading the system. This is **an optional step** , as Zorin OS' upgrade tool is quite reliable.

The easiest way to do so is by using the pre-installed " _Backups_ " tool. You can search for it in the Zorin Menu ( _the app launcher_ ).

![You can select the folders you want to backup and the location for their storage.][7]

After you launch it, click on " _Create My First Backup_ ," and select the folders you want saved and the ones ignored. Then, select the storage location for the backup. I suggest you store these on external storage or upload them to Google Drive.

📋

In the screenshot above, I just used a dummy folder located on-device to demonstrate the steps.

![You can choose to encrypt your Zorin OS backups.][8]

Should you choose to, there is **an option to encrypt the backup using a password** ; you will need it to update the existing backup or restore the files to the system.

For a more comprehensive backup solution, I recommend [opting for Timeshift instead][9].

![][10]

### Time for The Upgrade

Open the _Zorin Menu_ by clicking on its logo in the taskbar or pressing the `Super` key on your keyboard and search for " _Software Updater_ ". If you have any pending updates, get them by clicking on " _Install Now_ ".

![Just search for the Software Updater in the Zorin Menu.][11]

You will be prompted to enter your account password. Enter it to authenticate the upgrade and wait for the process to complete. Towards the end, you might be asked to restart your computer.

![][12]

Now, open the terminal via the Zorin Menu or by using the handy keyboard shortcut `Ctrl + Alt + T` and run the following command on it:

```

    gsettings set com.zorin.desktop.upgrader show-test-upgrades true

```

When the upgrade path comes out of testing, you won't need to run the above-mentioned command and **can directly skip over to the step below**.

![Finding the "Upgrade Zorin OS" tool is easy.][13]

Now, launch the " _Upgrade Zorin OS_ " tool and select the Zorin OS 18 edition that matches your current installation. In my case, that is Zorin OS 18 Core, going up from Zorin 17 OS Core.

You will be prompted to enter your password again. Go ahead and authenticate.

![Remember to read the disclaimers!][14]

After an upgrade requirements check, **a long list of disclaimers will be shown**. Ensure that you go through them before clicking on " _Upgrade_ " to begin the upgrade process from Zorin OS 17 to 18.

![The final stretch of the Zorin OS upgrade process.][15]

Now it is just a matter of waiting. The **upgrade time depends on your internet speed and hardware**. Once done, restart your computer when prompted, and you will boot into Zorin OS 18.

If you run into any issues, you can ask the helpful FOSSers over at [It's FOSS Community][16] for help.

**Suggested Read 📖**

![][17]

--------------------------------------------------------------------------------

via: https://itsfoss.com/zorin-os-18-upgrade/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/zorin-os-18-release/
[4]: https://blog.zorin.com/2025/11/18/test-the-upgrade-from-zorin-os-17-to-18-and-celebrating-1-million-downloads-of-zorin-os-18/
[5]: https://itsfoss.com/news/zorin-os-17/
[6]: https://itsfoss.com/content/images/2025/11/zorin-os-backups-1.png
[7]: https://itsfoss.com/content/images/2025/11/zorin-os-backups-2.png
[8]: https://itsfoss.com/content/images/2025/11/zorin-os-backups-4.png
[9]: https://itsfoss.com/backup-restore-linux-timeshift/
[10]: https://itsfoss.com/content/images/icon/android-chrome-512x512-41.png
[11]: https://itsfoss.com/content/images/2025/11/zorin-os-upgrade-1.png
[12]: https://itsfoss.com/content/images/2025/11/zorin-os-upgrade-4.png
[13]: https://itsfoss.com/content/images/2025/11/zorin-os-upgrade-5.png
[14]: https://itsfoss.com/content/images/2025/11/zorin-os-upgrade-8.png
[15]: https://itsfoss.com/content/images/2025/11/zorin-os-upgrade-10.png
[16]: https://itsfoss.community/
[17]: https://itsfoss.com/content/images/icon/android-chrome-512x512-42.png
