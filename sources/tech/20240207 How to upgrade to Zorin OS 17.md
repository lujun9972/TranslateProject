[#]: subject: "How to upgrade to Zorin OS 17"
[#]: via: "https://itsfoss.com/zorin-os-upgrade/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to upgrade to Zorin OS 17
======

Zorin OS 17 is a beautiful Linux distribution on top of Ubuntu 22.04 LTS.

One of the [best-looking Ubuntu-based distro][1], and provides an excellent user experience for all kinds of users.

If you are already a Zorin OS user, how can you access and upgrade your system to the latest version?

Fret not, here, I tell you more about it.

**Interesting backstory** : I tried the standard approach you follow to [upgrade Ubuntu to the latest version][2], but that does not work here:

```

    sudo apt update && sudo apt dist-upgrade

```

![][3]

Instead, you will have to use the Zorin OS upgrader GUI tool that lets you upgrade to the latest release of the Zorin OS.

### Before You Upgrade to the Zorin OS 17

Don't jump onto upgrade just yet. I know you want to get the Zorin OS 17 update, but, here are a couple of things for you to know:

  * You must be using the last iteration of Zorin OS 16 which is **16.3** to upgrade to Zorin OS 17.
  * Upgrading to Zorin OS will remove installed PPAs and data of installed software.



#### Step 1: Create a backup (optional)

While this is optional, I would suggest creating a backup before upgrading your system, as there's always a slight chance that the upgrade goes bad.

There's a utility called `Backups` pre-installed in Zorin OS 16. Start it and there you will find a button to create a backup labeled as `Back Up Now..`:

![][4]

Next, you will be asked whether you want to password-protect your backup or not.

I went with the without password option:

![][5]

Once you click the `Forward` button, it will create a backup, and you are good to go.

If you want better control over creating a backup, then you can use Timeshift, and here's [a detailed guide on how to install and use Timeshift][6]:

![][7]

#### Step 2: Choose between pro and non-pro options

Once you open the Zorin OS upgrader, it will show you the available upgrades for your current installation:

![][8]

Now, if you want to upgrade to the Zorin OS 17 Pro, you will have to purchase it on Zorin OS's official website, and then click on upgrade here.

It will give you the option for a minimal installation or a fully loaded one.

The full installation comes with office suite and other additional software, whereas the minimal installation only comes with the premium layouts and core system utilities:

![][9]

Next, you'll be asked to enter the credentials for your pro membership:

![][10]

Of course, if you do not want the extras, go with the Zorin OS core edition for free. You will not be asked for a support code with the free edition.

No matter what edition you opt for, this is how the next screen would look like:

![][11]

Press the `Upgrade` button, and it will start downloading Zorin OS 17:

![][12]

#### Step 3: Reboot into Zorin OS 17

Once the upgrade is finished, you will be asked to reboot your system to take effect of the upgrade:

![][13]

Press the `Restart` button and that's it!

### Want to Explore What's New in Zorin OS 17?

Once you boot into your upgraded machine, you might want to know the new features and changes done for a better user experience.

For that purpose, I recommend checking out more about the [changes introduced to ZorinOS 17][14] in our release coverage:

![][15]

_I hope you find this guide helpful and if you discover any issues while upgrading the system, then leave a comment or reach out to fellow users on_ [_It's FOSS Community_][16] _._

--------------------------------------------------------------------------------

via: https://itsfoss.com/zorin-os-upgrade/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/beautiful-linux-distributions/
[2]: https://itsfoss.com/upgrade-ubuntu-version/
[3]: https://itsfoss.com/content/images/2024/02/can-t-update-zorinOS-using-the-terminal.png
[4]: https://itsfoss.com/content/images/2024/02/create-a-backup-1-2.png
[5]: https://itsfoss.com/content/images/2024/02/Create-a-backup--2-1.png
[6]: https://itsfoss.com/backup-restore-linux-timeshift/
[7]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[8]: https://itsfoss.com/content/images/2024/02/Start-the-ZorinOS-upgrade-min.png
[9]: https://itsfoss.com/content/images/2024/02/Step-1-for-upgrading-to-the-ZorinOS-17-pro-min.png
[10]: https://itsfoss.com/content/images/2024/02/Step-2-for-upgrading-to-the-ZorinOS-17-pro-min.png
[11]: https://itsfoss.com/content/images/2024/02/ZorinOS-upgrader-showing-summery-of-changes-min.png
[12]: https://itsfoss.com/content/images/2024/02/Upgrading-to-ZorinOS-17-min.png
[13]: https://itsfoss.com/content/images/2024/02/Restart-your-device-to-take-efffect-from-the-upgrade-you-did-in-ZorinOS-min.png
[14]: https://news.itsfoss.com/zorin-os-17/
[15]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[16]: https://itsfoss.community/
