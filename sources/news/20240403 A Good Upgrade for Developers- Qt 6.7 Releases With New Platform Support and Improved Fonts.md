[#]: subject: "A Good Upgrade for Developers: Qt 6.7 Releases With New Platform Support and Improved Fonts"
[#]: via: "https://news.itsfoss.com/qt-6-7-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A Good Upgrade for Developers: Qt 6.7 Releases With New Platform Support and Improved Fonts
======
The Qt 6.7 release includes significant improvements.
[Qt][1] ( _pronounced “cute”_ ) is a popular cross-platform software suite used to create graphical user interfaces (GUIs) for things such as applications and [desktop environments][2].

You have most likely come across it while using any one of the popular Linux distros or applications across Linux, Windows, and macOS, without even realizing that it was made possible with Qt.

That being said, let's move on to the matter at hand. The developers of Qt have introduced a new release, **Qt 6.7** , with many improvements on offer. So, shall we dive into this?

### Qt 6.7: What to Expect?

As this is a jam-packed release that arrived just before the upcoming Qt 6.8 LTS release, we will focus on the **key highlights** :

  * **Expanded Platform Support**
  * **Better Fonts and Icons**
  * **Enhanced Qt Graphs**



#### Expanded Platform Support

Starting off with this, Qt 6.7 features support for newer builds of various operating systems across platforms. Now, there's support for **macOS 14,** **iOS 17** , and **Windows 11 23H2**.

On the Linux side, there's support for **Android 14** , **Red Hat Enterprise Linux 9.2** , **OpenSUSE Leap 5.15** , and **SUSE Linux Enterprise Server 15**.

For Ubuntu, the latest supported version is still the older 22.04 LTS release because 24.04 LTS is still not out.

You can refer to the [supported platforms page][3] for more info.

#### Better Fonts and Icons

With this release, **Qt now has support for variable fonts** , which makes it possible to combine various renditions of the same typeface into a single font file, allowing applications to select any values for “weight” or “cursiveness”.

Furthermore, the icons have also benefited from the work on fonts, with Qt now having support for native icon libraries.

For more font-specific info, you can refer to [Eskil's blog][4].

#### Enhanced Qt Graphs

Qt Graphs on Qt 6.7 includes **new 2D bar, line, and scatter graphs** ; these join the existing 3D visualizations that were already available since the previous release.

Additionally, the newly inducted graphs work with Qt Quick animations/effects, support theming, and integrate with handler-based interaction APIs.

However, **you have to keep in mind that Qt Graphs is still undergoing development** , and, as a result, is offered as a technology preview under the Qt 6.7 release. The developers expect that additional work needs to be done before the Qt 6.8 LTS release.

#### 🛠️ Other Changes and Improvements

There are a few other notable changes too:

  * Initial support for C++20.
  * Various improvements to Qt SVG.
  * Support for embedding native windows into a Qt Quick scene
  * Introduction of three new classes for REST-specific use cases.
  * Support for embedding native windows into a Qt Quick scene.
  * Inclusion of [_QNativeInterface::QWaylandScreen_][5] for the Wayland client on Linux.
  * The included examples and demo apps with Qt have been updated with better UI and improved code; there are a few new examples too.



What you read above was just the tip of the iceberg. I highly suggest you give the [announcement blog][6] and the [release notes][7] a thorough read to learn more about this release.

### 📥 Download Qt 6.7

If you didn't figure it out already, this is **a developer-focused piece of software, not meant for use by end users**. So, if you want to see it in action, you will have to wait for your favorite applications or desktop environments to implement it.

But, for the developers in the house, they can head over to the [official website][8] or their [Qt Account][9] page to get started with this release of Qt.

[Qt 6.7][8]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/qt-6-7-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.qt.io/
[2]: https://itsfoss.com/what-is-desktop-environment/
[3]: https://doc.qt.io/qt-6/supported-platforms.html
[4]: https://www.qt.io/blog/text-improvements-in-qt-6.7
[5]: https://doc-snapshots.qt.io/qt6-6.7/qnativeinterface-qwaylandscreen.html
[6]: https://www.qt.io/blog/qt-6.7-released
[7]: https://code.qt.io/cgit/qt/qtreleasenotes.git/about/qt/6.7.0/release-note.md
[8]: https://www.qt.io/download
[9]: https://login.qt.io/login
