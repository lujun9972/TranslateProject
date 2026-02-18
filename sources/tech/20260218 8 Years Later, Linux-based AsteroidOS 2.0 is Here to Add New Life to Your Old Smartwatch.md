[#]: subject: "8 Years Later, Linux-based AsteroidOS 2.0 is Here to Add New Life to Your Old Smartwatch"
[#]: via: "https://itsfoss.com/news/asteroidos-2-release/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

8 Years Later, Linux-based AsteroidOS 2.0 is Here to Add New Life to Your Old Smartwatch
======

[![Warp Terminal][1]][2]

It's been 8 years... since we last covered [AsteroidOS on It's FOSS][3]. The promising project kind of stalled, or so I thought, until the recent announcement of AsteroidOS version 2.0 release. I am happy to see the project progress.

### What is AsteroidOS?

AsteroidOS is a free, open-source operating system designed specifically for smartwatches. It is a Linux-based OS built as an alternative to proprietary smartwatch platforms like Wear OS (Google) or watchOS (Apple). It's completely community-driven and focuses on user freedom and privacy.

Under the hood, AsteroidOS is [built on top of OpenEmbedded][4] and uses Qt/QML for its user interface, along with BlueZ for Bluetooth connectivity.

The project is built around three core principles:

  * Privacy first: No telemetry, no forced cloud services, full user control over data.
  * Environmental responsibility: Extending the life of existing smartwatches long after manufacturers drop support.
  * Education & contribution: Helping every interested user become a contributor. With code in QML/Qt, JavaScript, or C, users can modify the OS to suit their preference and need.



### What's new in AsteroidOS 2.0?

![][5]

The main new features are **Always-on Display** (the screen stays visible at all times), **Tilt-to-wake** (raise your wrist to wake the screen), and **Palm-to-sleep** (cover the screen to turn it off). These features give AsteroidOS a modern smartwatch experience.

Other than that, here are some other features worth looking at.

#### New sensors & apps

![][6]

A dedicated **heart rate monitor** app and **initial step counting support** have been added, along with a **compass app** and **Bluetooth HID and Audio** support. There's also a new Flashlight **** app and a game called Diamonds (a twist on the [2048][7] concept).

#### Design & usability overhaul

The old QuickSettings menu has been replaced by a fully redesigned, highly customizable QuickPanel with more toggles, app shortcuts, and a power-off timer. Seven new app **l** auncher **** styles have been added, selectable from a new settings page.

A **Nightstand mode** lets you use the watch as a bedside clock with a large charging indicator. The watchface gallery now previews faces alongside the selected wallpaper, and both pages received significant performance improvements. New triangulated wallpapers and a reworked animated background round out the visual refresh.

#### App improvements

Several existing apps have been redesigned. The Weather app is overhauled for better legibility, the Timer app now runs in the background and was optimized for round displays, and the Calculator got an improved button layout. Music volume control was also added.

#### System & performance

The release brings smoother UI animations through optimized rendering, battery life improvements, and numerous stability fixes. The system font was switched to Noto Sans for better multilingual support, and color emoji was updated to Twemoji. Over 20 new languages were added, bringing the total to 49 supported languages.

#### Support for more watches

Support is added for 15 new watch models since version 1.0, including multiple Fossil Gen 4/5/6 devices, Huawei Watch 1 & 2, TicWatch Pro 3, OPPO Watch, Polar M600, and more. [This page helps][8] users see exactly what's supported on their device.

#### Other features

The Android companion app AsteroidOS Sync gained call detection/display, a new Bluetooth library for better stability, and custom API key support for weather. This sync app basically syncs your watch data in your Android phone. AsteroidOS support is also now added to Gadgetbridge, and new sync clients are now available for SailfishOS and Ubuntu Touch (Telescope).

You can read the full release note [here][9] and watch the video demo of all the new features.

I have not tried AsteroidOS personally yet. I have a Galaxy Watch, which doesn't seem to be supported yet. Perhaps in a year or two, when the watch is obsolete and AsteroidOS starts supporting it, I'll give it a try. For now, I am happy to see that this project not only exists but is also seeing active development.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/asteroidos-2-release/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/asteroidos-watch-os/
[4]: https://wiki.asteroidos.org/index.php/OpenEmbedded
[5]: https://itsfoss.com/content/images/2026/02/AsteroidOS-smartwatch.webp
[6]: https://itsfoss.com/content/images/2026/02/asteroidOS-smartwatch-2-features.webp
[7]: https://itsfoss.com/2048-game/
[8]: https://asteroidos.org/watches/features/
[9]: https://asteroidos.org/news/2-0-release/
