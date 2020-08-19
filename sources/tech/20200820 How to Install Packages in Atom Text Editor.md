[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Install Packages in Atom Text Editor)
[#]: via: (https://itsfoss.com/install-packages-in-atom/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Install Packages in Atom Text Editor
======

[Atom][1] is undoubtedly one of the [best open source code editors][2] available for any platform. Developed by GitHub, Atom takes pride in pitching itself as the hackable text editor for the 21st century.

How is it a ‘hackable’ text editor? Because you can extend the functionality of the editor by means of installing plugins for your need.

These extensions are called packages in Atom and Atom provides a handy command line utility `apm` in Linux to manage packages. With that, installing packages in Atom is as easy as typing this simple command in the terminal:

```
apm install package_name
```

If you are not too comfortable with the terminal, don’t worry. You can also install Atom plugins graphically from within the terminal.

In this tutorial, I’ll show you both graphical and terminal ways of installing plugins/extensions/packages (whatever you want to call them) in Atom.

Before you do that, make sure to [install Atom editor on Ubuntu Linux][3] or whichever operating system you are using. You cannot install Atom packages if you don’t have Atom installed in the first place, can you?

### GUI method: Install new packages in Atom using the editor

Open Atom editor and from the top menu, go to Edit-&gt;Preferences.

![][4]

You’ll see a Settings tab now. In here, go to the Install option from the left sidebar. You’ll now see some featured packages. You can also search for packages based on the name.

Installing these packages is as simple as clicking the install button.

![][5]

To see the installed packages, from the left sidebar, choose Packages option. This will show you all installed packages in your Atom editor.

Don’t touch the Core packages. The additional plugins are listed under Community Packages. You can delete or change package configurations from here.

![][6]

It was easy, wasn’t it? Now let’s go the command line way.

### Terminal method: Installing packages in Atom using apm command

As I mentioned earlier, Atom provides a command line tool called apm (short for Atom Package Manager) that allows you to do all things you can do graphically, in the command line.

You can search for package names like this:

```
apm search search_string
```

It will show you all the packages matching your search query. As you can see in the image below, it also shows how many times a package has been downloaded and how many stars it has to indicate the popularity of a package.

![][7]

You can pick the name of the package you want and install it the following way:

```
apm install package_name
```

The package usually gets installed in .atom/packages directory in your home directory. This is why you don’t need to use sudo while installing Atom packages.

![][8]

Keep in mind that apm command doesn’t support tab completion by default so you need to know exact package name here.

There are many more arguments the apm command can take for managing the packages (installing, removing, deactivating, upgrading etc). You can see them with the help option `-h`.

**GUI or CLI? Which method do you prefer?**

I hope you find this quick little tutorial helpful in installing packages in Atom editor. If you face some issues, please feel free to ask in the comment section.

By the way, which method you prefer for installing Atom plugins? The GUI method or the command line one? Do share your preference.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-packages-in-atom/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://atom.io/
[2]: https://itsfoss.com/best-modern-open-source-code-editors-for-linux/
[3]: https://itsfoss.com/install-atom-ubuntu/
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/installing-packages-in-atom-step-1.png?resize=800%2C606&ssl=1
[5]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/install-atom-packages.png?resize=800%2C415&ssl=1
[6]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/atom-packages.jpg?resize=800%2C418&ssl=1
[7]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/08/atom-package-search-cli.png?resize=800%2C241&ssl=1
[8]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/08/install-atom-packages-cli.png?resize=798%2C189&ssl=1
