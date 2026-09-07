[#]: subject: "Framework Laptop 12 Arrives with Fedora Pre-installed"
[#]: via: "https://fedoramagazine.org/framework-laptop-12-arrives-with-fedora-pre-installed/"
[#]: author: "Shaun McCance https://fedoramagazine.org/author/shaunm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Framework Laptop 12 Arrives with Fedora Pre-installed
======

![][1]

Photo by [Akif Waseem][2] on [Unsplash][3] [edited]

Recently, [Framework announced their new Laptop 12][4], which optionally comes with the KDE Edition of Fedora Linux pre-installed. Framework’s modular hardware has long captured the hearts of tinkerers, and many Framework users were already running Fedora Linux. Giving community members the option to unbox a hardware-validated, pre-installed Fedora KDE system is the culmination of months of effort from both Framework and dedicated Fedora community members. I’d like to take a moment to reflect on the hard work of the Fedora community that’s made this possible

### The Perfect Match: Fedora KDE Plasma & Convertible Hardware

The Framework Laptop 12 is a 12.2” 2-in-1 convertible laptop complete with a touchscreen and stylus support. Delivering a seamless experience on a form factor like this requires an interface that excels across traditional, touch, and pen modes.

Enter **Fedora KDE Plasma Desktop**.

Over recent release cycles, the Fedora KDE Special Interest Group (SIG) and upstream KDE contributors have poured immense effort into refining the user interface. This includes touch navigation, gesture support, virtual keyboards, and digital pen input under Wayland. Combined with the brand-new Intel Core Series 3 architecture, Thunderbolt 4, Wi-Fi 7, and options for a backlit keyboard and fingerprint reader, the hardware and software form a cohesive unit.

> _“The Fedora KDE Plasma Desktop contributors work hard to make the Fedora KDE Plasma Desktop edition the premier KDE experience for users. It’s great to see Framework customers have the choice to have it pre-installed.”_
>
> **— Jef Spaleta, Fedora Project Lead**

### Community Collaboration at its Finest

Bringing a brand-new hardware platform with bleeding-edge components (like Intel’s Core Series 3 chips and BE213 Wi-Fi 7 modules) to pre-built availability doesn’t happen by accident. It takes rigorous testing, community bug hunting, and close collaboration.

Long before today’s announcement, Framework provided pre-release hardware to Fedora QA and SIG contributors to ensure day-one hardware enablement:

  * **Kernel 7.1 Integration:** Core Series 3 and Wi-Fi 7 R2 radios rely on recent upstream kernel drivers. Fedora contributors verified boot stability, power states, and Wi-Fi throughput on early builds to ensure seamless out-of-the-box performance.
  * **Fingerprint Sensor Support via libfprint:** The new power-button fingerprint reader required driver verification and early integration into libfprint. This work allows users to instantly set up biometrics during the initial Plasma setup wizard.
  * **Display, Touch, and Stylus Calibration:** Fedora QA and KDE community testers ran extensive Test Day scenarios to validate palm rejection, active stylus pressure sensitivity, and automatic screen rotation when flipping the device into tablet mode.
  * **Open-Source Firmware (ZMK):** The updated backlit keyboard uses a reprogrammable controller running open-source ZMK firmware. This firmware aligns perfectly with Fedora’s “Four Foundations” (Features, Friends, Freedom, First).



### What This Means for the Linux Desktop

Starting at **$699 USD** for the Fedora pre-built configuration, the Framework Laptop 12 demonstrates that a fully modular, repairable, open-source-friendly laptop can be accessible, performant, and ready to go from day one.

Thank you to every member of the Fedora Quality Assurance team, the Fedora KDE SIG, and the broader upstream community who submitted test reports, verified kernel patches, and helped make this launch a massive success!

_Disclosure: We used generative AI to outline and draft this post, but real humans shaped, verified, and reviewed it._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/framework-laptop-12-arrives-with-fedora-pre-installed/

作者：[Shaun McCance][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/shaunm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/Framework_12_Fedora_Preinstalled-816x345.jpg
[2]: https://unsplash.com/@akif_waseem?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/a-glowing-teal-curved-line-pattern-on-a-black-background-flV_A1gdSr8?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://frame.work/blog/framework-laptop-12-now-with-core-series-3
