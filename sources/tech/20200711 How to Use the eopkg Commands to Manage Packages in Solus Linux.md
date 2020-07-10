[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Use the eopkg Commands to Manage Packages in Solus Linux)
[#]: via: (https://itsfoss.com/eopkg-commands/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

How to Use the eopkg Commands to Manage Packages in Solus Linux
======

As a distribution built from scratch, the number of packages available in Solus repositories is limited, unlike [Arch-based distributions][1] that have [AUR][2]. But Solus compensate it with the support for [Flatpak][3] and [Snap][4] packages.

The package manager for [Solus Linux][5] is **eopkg** which is based on [PiSi][6] (Packages Installed Successfully as Intended), the package manager developed for **Pardus**, a distribution based on Debian that has support from the [Turkish government][7].

In this tutorial, I’ll show you some of the common usage of the eopkg that you can use to manage packages in Solus Linux.

### Using eopkg package manager in Solus Linux

If you prefer to use a GUI application to manage the installed software, there’s a Software Center, that you can open from the menu. I’ll briefly touch upon it in later parts of this section.

#### Installing software

You can install one or more packages with eopkg in the following way:

```
sudo eopkg install package_1 package_2
```

![][8]

#### Uninstalling software

You can remove one or more installed packages using:

```
sudo eopkg remove package_name
```

![][9]

#### Reinstalling software

If there is an issue with an installed software, you can reinstall the package using:

```
sudo eopkg install --reinstall package_name
```

#### Search for an available package

You can search whether a package is available in Solus repository.

```
sudo eopkg search term
```

![][10]

Notice that you don’t need to search for a specific software name, although you can do that. It search summaries and software names by default.

#### Get information on software (before or after installing them)

You can also get some additional information on a software, such as its description, version, installation size etc.

It is like [apt show command in Ubuntu][11].

```
sudo eopkg info package_name
```

![][12]

#### Updating a specific package or all of them together

You can update your system by using:

```
sudo eopkg upgrade
```

![][13]

If you want to **only** update a specific piece of software on your system, you can specify is like below:

```
sudo eopkg upgrade package_name
```

#### Third Party Applications

Solus has a [Third Party Repository][14], it contains applications that cannot be included in the primary repository due to licensing issues.

![Solus Third Party Apps][15]

Here’s a list of some of the applications available in this repository:

  * Google Chrome
  * Skype
  * Slack
  * Spotify
  * TeamViewer
  * Microsoft Core Fonts
  * Android Studio



### Snap and Flatpak for additional software

As mentioned earlier, Solus supports Snap packages. Commencing with Solus 3 and above, Snap is already installed and ready to go.

```
sudo snap install packagename
```

**Flatpak packages**

To install Flatpak, run the following command in the terminal:

```
sudo eopkg install flatpak xdg-desktop-portal-gtk
```

To enable Flathub repository:

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Restart your system, and you can install [flatpak packages][16].

### Bonust Tip: Installing LTS kernel in Solus

By default, Solus utilizes the [Linux current kernel][17]. If you run Solus on older hardware or stability is your priority you can install the LTS kernel as following.

Keep in mind that Solus still maintains the 4.9 LTS kernel (from 2016), not the latest 5.4 LTS.

![Solus Mate 4.1 with LTS kernel][18]

To Install the LTS kernel, use:

```
sudo eopkg install linux-lts
```

Now reboot.

By default, EFI installs will not show the boot menu and boot directly into Solus. By hitting space bar repeatedly during boot, the boot menu will appear.

After choosing the LTS kernel from the boot menu, use the following command to make the booted kernel the default boot option.

```
sudo clr-boot-manager update
```

If you cannot access Solus in a dual-boot scenario, typically applies to “legacy boot” (non-UEFI), can be resolved by accessing the other operating system and running the following command:

```
sudo update-grub
```

#### Conclusion

Solus is a simple and reliable operating system. I’m a fan of the rolling release model and Solus user for quite a long time.

If you are not willing to dive deep into every Linux system parameter like you do with [Arch Linux installation][19], then Solus is for you.

Snap and flatpak support won’t let you have limited software options, so it could be an ideal OS for the average desktop user as you won’t be bothered by point releases.

If you have tried Solus already please let me know your thoughts at the comments below.

--------------------------------------------------------------------------------

via: https://itsfoss.com/eopkg-commands/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/arch-based-linux-distros/
[2]: https://itsfoss.com/aur-arch-linux/
[3]: https://itsfoss.com/flatpak-guide/
[4]: https://itsfoss.com/use-snap-packages-ubuntu-16-04/
[5]: https://getsol.us/home/
[6]: https://github.com/examachine/pisi
[7]: https://itsfoss.com/linux-national-os/
[8]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/Solus-install-package.png?ssl=1
[9]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/Solus-remove-package.png?ssl=1
[10]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/eopkg_search.png?ssl=1
[11]: https://itsfoss.com/apt-search-command/
[12]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/eopkg_info.png?ssl=1
[13]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/Solus-system-upgrade.png?ssl=1
[14]: https://getsol.us/articles/software/third-party/en/
[15]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/Solus-third-party-apps.png?ssl=1
[16]: https://flathub.org/home
[17]: https://getsol.us/articles/troubleshooting/boot-management/en/
[18]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/Solus-mate-4.1-neofetch.png?ssl=1
[19]: https://itsfoss.com/install-arch-linux/
