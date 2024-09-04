[#]: subject: "Introducing SyncStar"
[#]: via: "https://fedoramagazine.org/introducing-syncstar/"
[#]: author: "Akashdeep Dhar https://fedoramagazine.org/author/t0xic0der/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introducing SyncStar
======

![][1]

Photo of kiosk by [Bryan Dijkhuizen][2] modified and overlaid on photo by [GENERAL BYTES][3] on [Unsplash][4]

SyncStar lets users create bootable USB storage devices with the operating system of their choice. This application is intended to be deployed on kiosk devices and electronic signage where conference guests and booth visitors can avail themselves of its services. Install the _syncstar_ package from the [Fedora Linux repositories][5] or the _syncstar_ project from the [Python Package Index][6] to get started.

```

    $ sudo dnf install syncstar

```

```

    (venv) $ pip install syncstar

```

* * *

### Inspiration

The idea of building SyncStar came from the original concept of the [Fedorator][7] project. This was a kiosk device for writing a Live image of Fedora Linux onto USB flash drives intended to be used on Fedora Project [conference booths][8]. While the scheme was innovative as it allowed visitors at our booths to consider using Fedora Linux, the adoption could not spread widely due to the pause in in-person conferences due to the [COVID-19 pandemic][9]. The rise in prices of [Raspberry Pi devices][10] and supporting peripherals due to the [global semiconductor shortage][11] was also detrimental to the usability of the project. The foundational hardware elements of the project were now difficult to acquire and access to a 3D printer was still difficult in some parts of the world — thereby greatly heightening the entry barrier for booth organizers. Anyone wanting to run a [Fedora Project][12] booth in their neighborhood conference in the hopes of increasing the adoption of Fedora Linux could not easily do so.

### Objective

The goal behind building [SyncStar][13] was to achieve what [Fedorator][14] set out to do while providing solutions to its shortcomings along the way. Questions like “How can we significantly reduce the dependency on specific kinds of external hardware while retaining similar functionality of the project?”, “How can we improve the self-service user interaction experience if we were not to include touchscreen hardware?”, “How can we ensure a lower entry barrier for someone wanting to represent Fedora Project in their local [FOSS][15] conference happening a week from now?” and many more arose. To address concerns like these, SyncStar was fabricated as a [headless service][16] by design — thus no longer necessitating the user interactions to happen on the same device on which the bootable USB devices are created. Instead, a responsive web interface was developed to be conveniently accessible on browsers across devices as long as they are connected to the same network as the device running the service.

![SyncStar not only supports Fedora Linux but also other operating system images from our friends][17]

### Features

  * Asynchronous multiprocessing allows for flashing multiple storage devices simultaneously
  * Programming standards and engineering methodologies are maintained as much as possible
  * Frontend is adaptive across various viewport types and browser-side assistive technologies
  * Detailed documentation for both consumption and development purposes are readily provided
  * Minimal command line interface based configuration with wide range of customizable options
  * Stellar overall codebase quality is ensured with 100% coverage of functional backend code
  * Over 46 checks are provided for unit based, end-to-end based integration based codebase testing
  * GitHub Actions and Pre-Commit CI are enabled to automate maintenance of codebase quality



### Scenarios

  1. Set up the SyncStar service on the Fedora Linux promoting booth laptop or Raspberry Pi
  2. Open up the SyncStar dashboard either on the booth laptop or on a smartphone
  3. Lay over the swags like Fedora Project branded USB flash drives on the booth desk
  4. Let a conference attendee ask if the USB flash drives on the booth table are for taking
  5. Tell them that they are as long as they use SyncStar to get themselves a copy of Fedora Linux
  6. Have them start the live bootable media creation and strike up a conversation with them
  7. Allow other attendees to use their own USB flash drives with [discretion][18] in parallel
  8. Advertise for sidestream communities by keeping their offerings in the collection



![Select a USB flash drive, select an operating system and strike a conversation][19]

### Nomenclature

You might be curious about where this fancy name comes from. [Sync][20] is a standard system call in the Unix operating system, which commits all data from the kernel filesystem buffers to non-volatile storage. This functionality is also made available in the similarly named command line utility that is used to persist a file read/write operation. While the project might not necessarily make direct use of the said system call, the functionality it tries to achieve is similar i.e. writing operating system images on the USB storage devices to make them into Live bootable media. What’s more, it has a bunch of bells and whistles like [asynchronous task queues][21] and [responsive web interfaces][22] atop the previous functionality and is that not what stars do? **😜** So that is where the fancy name “SyncStar” came from.

### Appeal

If you like the efforts made here and want to support the development of the project, please consider giving a [star][23] to the project and [forking][24] it your namespace. I appreciate all kinds of contributions — ranging from small sized bug fixes to major sized feature additions as well as from trivial [documentation][25] changes to awesome [codebase][26] refactoring. Even if you do not have the capacity to take the development for a spin, you can help me out by testing out the project and getting in touch with me on the [issue tracker][27] with the things that must be fixed and the things that should be introduced. SyncStar is far from perfect right now, but with all our efforts combined, it can most definitely get closer to being great. With that mentioned, I thank you for reading through the entirety of this article 🎉.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introducing-syncstar/

作者：[Akashdeep Dhar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/t0xic0der/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/fedora-kiosk-in-room-816x345.jpg
[2]: https://unsplash.com/photos/a-ticket-machine-sitting-on-the-side-of-a-train-station-wIVfJ0CPwjw?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-person-sitting-on-a-bench-in-a-room-NtvHjru4jdI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://unsplash.com/
[5]: https://src.fedoraproject.org/rpms/syncstar
[6]: https://pypi.org/project/syncstar/
[7]: https://fedoraproject.org/wiki/Fedorator
[8]: https://fedoraproject.org/wiki/Fedorator#Fedorator_holders
[9]: https://en.wikipedia.org/wiki/COVID-19_pandemic
[10]: https://www.raspberrypi.com/news/supply-chain-shortages-and-our-first-ever-price-increase/
[11]: https://en.wikipedia.org/wiki/2020%E2%80%932023_global_chip_shortage
[12]: https://fedoraproject.org/
[13]: https://github.com/gridhead/syncstar
[14]: https://github.com/Sanqui/fedorator
[15]: https://en.wikipedia.org/wiki/Free_and_open-source_software
[16]: https://en.wikipedia.org/wiki/Headless_computer
[17]: https://fedoramagazine.org/wp-content/uploads/2024/09/image-930x1024.png
[18]: https://en.wikipedia.org/wiki/USB_killer
[19]: https://raw.githubusercontent.com/gridhead/syncstar/main/data/expo.png
[20]: https://en.wikipedia.org/wiki/Sync_(Unix)
[21]: https://docs.celeryq.dev/en/stable/
[22]: https://flask.palletsprojects.com/en/3.0.x/
[23]: https://github.com/gridhead/syncstar/stargazers
[24]: https://github.com/gridhead/syncstar/forks
[25]: https://github.com/gridhead/syncstar/wiki
[26]: https://github.com/gridhead/syncstar.git
[27]: https://github.com/gridhead/syncstar/issues
