[#]: subject: "I Found Everything Search Engine Alternative for Linux Users"
[#]: via: "https://itsfoss.com/fsearch/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Found Everything Search Engine Alternative for Linux Users
======

[![Warp Terminal][1]][2]

A desktop-wide search application can be the key to speeding up your workflow by a significant amount, as anything you might look for will almost be at your fingertips at any given moment.

Today, we'll be looking at a GUI desktop application that does exactly that.

### FSearch: Fast, Feature-rich GUI Search App

[FSearch][3] is a fast file search application, inspired by [Everything Search Engine][4] on Windows.

It works in an efficient way without slowing down your system, **giving you results as you type the keywords in**. The way it does this is by indexing the files from the directories in advance, updating them at a fixed interval, and storing that information to search through whenever the application is used.

![][5]

It is written in C and based on GTK3, which is ideal for GNOME users but might not look as good on Qt based desktop environments like KDE. Let's look at some of the features this utility offers.

#### Index Inclusion/Exclusion

The first thing that you need to do after installation and the most crucial aspect of all is to specify to the utility what are the directories that you want it to search for anything in. Besides the inclusion category, you can also specify what directories you want excluded from the search. Another extremely helpful option is to exclude the hidden files from being searched which can be the case if you only want to search the files as you see them on your file explorer.

![][6]

Besides that, you can also configure how often the database needs to be refreshed and updated. This will depend on how often the relevant files on your system change, and hence should be your own choice.

#### Wildcard and RegEx Support

The search input supports the wildcard mode by default, which are often used for specifications on the command line. For example, if I want to search for all files that contain "Black" in the name, I can give the input as such:

![][7]

Here, "*" essentially means everything. So any files with anything at all before and after the word "Black" will be listed. There are many more wildcards like this such as "?" for one missing character, and "[ ]" specifying ranges. You can read more about them [here][8].

The other option is to specify the search results by the [RegEx formatting][9], which is a different style in itself. It can be activated using Ctrl+R, and switched by the same.

#### Fast Sort

You can quickly sort out the results based on name, path, size or last modification date right from the interface, as the results are shown with these details present. All it takes is one click on the right detail header (or two clicks if you want them in a descending instead of an ascending order).

#### Filetype Filter

The searched files can be of different categories defined in the utility itself, which are defined by the extensions of the files that the results yield. There is a button on the right of the search bar where the search results category can be specified, the default being "All". The categories are:

  * All
  * Files
  * Folders
  * Applications (such as .desktop)
  * Archives (such as .7z, .gzip, .bz)
  * Audio (such as .mp3, .aac, .flac)
  * Documents (such as .doc, .csv, .html)
  * Pictures (such as .png, .jpg, .webp)
  * Videos (such as .mp4, .mkv, .avi)



The excellent feature is that these categories and their list of extensions are modifiable. You can add or change any of the options if it doesn't fit your needs well.

![][10]

#### Search in Specific Path

Another interestingly important search option is to also search in the path of the filenames. This becomes relevant when you remember the approximate location of the file or part of the path or something as such. It seems like a minor detail but can be a real savior when the appropriate time arises. An example of it can be this:

![][11]

This mode can be activated using the keyboard shortcut Ctrl+U.

#### Other Features

There are other minor features that help in the customization, such as toggling the case sensitivity of the search terms (which can also be done with the Ctrl+I keyboard shortcut), single-clicking to open files, pressing Esc to exit, remembering window size on closing, etc.

### Installing FSearch on Linux

FSearch is available on various distributions in multiple different ways. First, to cover the distro-independent option, Flatpak. [FSearch exists on Flathub][12] and can be installed with a simple search on any distribution where Flathub is enabled internally in the app store such as Fedora. If not from the store, you can find the .flatpakref file [here][12] and (considering it is downloaded in the Downloads folder) install it with:

```

    sudo flatpak install io.github.cboxdoerfer.FSearch.flatpakref

```

On Ubuntu based distributions, there are two options, a stable release and a daily one. To add the repository the stable version, enter this command:

```

    sudo add-apt-repository ppa:christian-boxdoerfer/fsearch-stable

```

Whereas for the daily release:

```

    sudo add-apt-repository ppa:christian-boxdoerfer/fsearch-daily

```

In either case, then enter the following commands after to install the application:

```

    sudo apt update
    sudo apt install fsearch

```

On Arch-based distributions, use the following command:

```

    sudo pacman -S fsearch

```

On Fedora, the installation can be done by entering:

```

    dnf copr enable cboxdoerfer/fsearch
    dnf install fsearch

```

If none of these apply, you can always install from source or find instructions on the [official website][3].

### Final Thoughts

FSearch does what it claims to do without exceptions and hurdles. It is very fast, not very taxing on the hardware, has very sensible configuration options, and looks pretty good while doing its job. A huge recommendation from my side would be to add a keyboard shortcut to open FSearch (the process will depend on your distribution), something very accessible like Shift+S perhaps to easily open the utility and use it immediately.

I know that for many Linux users, nothing replaces the [find command][13] clubbed with xargs and exec but still, not all desktop Linux users are command line ninjas. That's why desktop search apps like FSearch, [ANGRYsearch][14] and [SearchMonkey][15] exist. [Nautilus' built-in file search][16] works well, too.

![][17]

Please let us know in the comments if this is an application you'd like to use, or if you have any other preferences. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/fsearch/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://cboxdoerfer.github.io/fsearch/
[4]: https://www.voidtools.com/
[5]: https://itsfoss.com/content/images/2025/10/fsearch_first-screen.png
[6]: https://itsfoss.com/content/images/2025/10/fsearch_excluded-directories.png
[7]: https://itsfoss.com/content/images/2025/10/fsearch_wildcard-example.png
[8]: https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm
[9]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Cheatsheet
[10]: https://itsfoss.com/content/images/2025/10/fsearch_category-editor.png
[11]: https://itsfoss.com/content/images/2025/10/fsearch_path-searching-mode.png
[12]: https://flathub.org/en/apps/io.github.cboxdoerfer.FSearch
[13]: https://linuxhandbook.com/find-command-examples/
[14]: https://itsfoss.com/angrysearch/
[15]: https://itsfoss.com/searchmonkey-search-text-files-linux/
[16]: https://itsfoss.com/nautilus-file-search/
[17]: https://itsfoss.com/content/images/icon/android-chrome-192x192-718.png
