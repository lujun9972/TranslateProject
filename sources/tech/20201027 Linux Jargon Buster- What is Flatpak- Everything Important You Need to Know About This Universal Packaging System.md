[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Linux Jargon Buster: What is Flatpak? Everything Important You Need to Know About This Universal Packaging System)
[#]: via: (https://itsfoss.com/what-is-flatpak/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

Linux Jargon Buster: What is Flatpak? Everything Important You Need to Know About This Universal Packaging System
======

While reading the installation instructions of an application, you’ll often come across terms like “**Flatpak”**, “**Snap**”, and “**AppImage**”.

You might have already used some of them on Linux — but might not really know they are. Flatpak, Snap and [AppImage][1] they are ‘universal packaging systems’.

In an earlier article in the Linux Jargon Buster, you have learned about the [package manager in Linux][2]. So I won’t bother you with packaging anymore. I’ll highlight what is Flatpak and how it tries to solve problem as a universal packaging system.

### What is Flatpak?

[Flatpak][3] is a package management utility that lets you distribute, install and manage software without needing to worry about dependencies, runtime, or the Linux distribution. Since you can install software without any issues irrespective on the Linux distribution (be it a Debian-based distro or an Arch-based distro), Flatpak is called universal package.

In case you’re curious, [Alexander Larsson][4] is the one responsible to create Flatpak and the history to Flatpak dates back to the summer of 2007. You can read more about his work and Flatpak’s history on his [blog post][5].

It’s impressive to know what it is and how it came in to existence, but why was it created and how does it work?

### What problem Flatpak solves?

![][6]

With [so many Linux distributions][7] out there, managing &amp; installing software is one of the most important aspects of managing a Linux system.

If you are an experienced Linux user, you can surely figure out the best way to do it. But, for beginners or for users who don’t want a learning curve to manage packages, these are some issues when using the traditional package formats (deb/rpm):

  * Need to resolve dependencies issues (dependencies refers to other packages that a program depends on to work)
  * Find required [libraries][8] to make the software work
  * Adapt to new [package managers][9] when switching Linux distributions
  * Not the most secure way of installing/managing software



In other words, with traditional package management systems there are some potential issues that you might encounter in order to make the software work for your system. And, not everyone has the time to troubleshoot!

That’s when something like Flatpak comes in to play.

Flatpak is one such open-source utility that helps you to distribute, manage/install packages without thinking about the Linux distribution you’re using or the dependencies/libraries that the program requires to run.

Now that you have an idea on what it is all about, let’s dive in deeper to know what Flatpak is, how it works, and some background on it.

### How does Flatpak work?

![Image Credits: Flatpak Documentation][10]

Flatpak apps run in an isolated environment (often referred as a [sandbox][11]). This sandbox contains everything that’s needed to run that specific program.

Basically, the sandbox includes the runtime and bundled libraries to fulfill the requirements of a program to run. You can learn more about the technical details in their [official documentation.][12]

Also, just because Flatpak apps are isolated, it cannot make any changes to your system without explicit permission from the host (you). So, Flatpak offers enhanced security to your system by keeping the applications isolated.

### Where do you get Flatpak apps?

![Flathub][13]

Please keep in mind that in order to use Flatpak packages, your Linux distributions must have Flatpak support. Some distributions like Fedora, Solus etc come with Flatpak support by default whereas you need to [manually install Flatpak support][14] in distributions like Ubuntu.

Even though Flatpak technology allows you to not rely on a centralized source for getting software, you will find using [Flathub][15] (built by Flatpak team) to distribute and manage software.

There could be other existing Flatpak repositories but none that I’m aware for my personal use-case.

### Flatpak: Pros and Cons

No wonder that Flatpak is something impressive — it comes with its fair share of advantages and disadvantages. Here, I’ll list some of them:

#### Advantages of using Flatpak

  * Flatpak apps can run on any Linux distribution
  * They offer forward-compatibility, meaning — you don’t need to worry about the apps not working if you upgrade your Linux distro to a bleeding-edge version that’s not officially supported by the application.
  * You don’t need to rely on dependencies.
  * In some cases, you will find the latest and greatest version of a program for Flatpak.
  * Flatpak app distribution does not depend on a centralized server, meaning — you don’t get locked-in to one vendor.
  * Enhanced security for your system using sandboxed applications
  * Offers easy integration with an existing software center on your Linux distribution



#### Disadvantages of using Flatpak

  * It does not have server support yet. It’s only available for desktop Linux as of now.
  * Flatpak apps consume more disk space than you’d usually have when using deb/rpm files. And, you’d need to find ways to [free up disk space][16] eventually.
  * Just because it runs on an isolated environment, you may miss a couple of functionalities for some programs. For instance, Flatpak apps may not support your custom [GTK theme][17].



**Wrapping Up**

I hope that now you have a good idea on what Flatpak is all about. If you want to explore more on installing and using Flatpak, I’d recommend you to read our [Flatpak guide][14] to get started.

If you enjoyed reading this article, please take a moment to share it across the social media platforms!

--------------------------------------------------------------------------------

via: https://itsfoss.com/what-is-flatpak/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/use-appimage-linux/
[2]: https://itsfoss.com/package-manager/
[3]: https://www.flatpak.org/
[4]: https://github.com/alexlarsson
[5]: https://blogs.gnome.org/alexl/2018/06/20/flatpak-a-history/
[6]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/10/what-is-flatpak.png?resize=800%2C450&ssl=1
[7]: https://itsfoss.com/what-is-linux/
[8]: https://en.wikipedia.org/wiki/Library_%28computing%29
[9]: https://en.wikipedia.org/wiki/Package_manager
[10]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/flatpak-working.png?resize=800%2C558&ssl=1
[11]: https://en.wikipedia.org/wiki/Sandbox_(computer_security)
[12]: https://docs.flatpak.org/en/latest/index.html
[13]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/flathub-screenshot.jpg?resize=800%2C404&ssl=1
[14]: https://itsfoss.com/flatpak-guide/
[15]: https://flathub.org/home
[16]: https://itsfoss.com/free-up-space-ubuntu-linux/
[17]: https://itsfoss.com/best-gtk-themes/
