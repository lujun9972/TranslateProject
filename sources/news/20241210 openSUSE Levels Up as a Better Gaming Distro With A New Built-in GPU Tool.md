[#]: subject: "openSUSE Levels Up as a Better Gaming Distro With A New Built-in GPU Tool"
[#]: via: "https://news.itsfoss.com/opensuse-gaming-gpu-tool/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

openSUSE Levels Up as a Better Gaming Distro With A New Built-in GPU Tool
======
So, are you ready to try openSUSE for gaming?
[![][1]][2]

Known for its robustness and versatility, [openSUSE][3] is a popular Linux distribution choice for those who prioritize stability, flexibility, and reliability over anything else. It is offered in two main editions: **Tumbleweed** , which is the [rolling release][4] variant, and **Leap** , the stable release variant.

Both editions appeal to a broad audience, serving diverse needs such as everyday computing, gaming, office tasks, server management, AI development, and much more.

Now, in a [recent announcement][5], they've introduced a significant change that promises to enhance the user experience. Let’s dive in and explore the details. 😃

### A Great Upgrade For Multi-GPU Systems

![openSUSE Tumbleweed 20241208 features switcherooctl 2.6.][6]

openSUSE's GNOME and KDE Plasma-equipped editions now come equipped with [switcherooctl][7], **a tool for handling GPU switching on systems with multiple graphics cards**. When in use, it facilitates seamless switching between the integrated and dedicated GPUs of a computer ( _typically for laptops, but not limited to_ ).

This implementation has become **the recommended solution by openSUSE for handling multi-GPU systems** , with the developers urging users to move away from outdated tools like [SUSEPrime][8], [Bumblebee][9], and [bbswitch][10].

With switcherooctl, users can expect things like **improved performance** , **better power management** , **compatibility with Wayland and X11 sessions** , and seamless integration with both the [Nouveau][11] and NVIDIA [proprietary drivers][12].

On the hardware side of things, it works on computers with multiple GPUs and laptops with Intel + NVIDIA/AMD + NVIDIA ( _CPU+GPU_ ) configurations.

For you, as the user, **GPU switching should happen automatically when launching applications** ( _even the XWayland ones_ ) that need the extra horsepower to drive GPU-intensive tasks.

**If the switch doesn't happen** , then you can always use GNOME's “ _Launch using Discrete Graphics Card_ ” option when right-clicking on an application. Just keep in mind that GNOME doesn't remember that for subsequent app launches.

For KDE Plasma, right-click on an application and select “ _Edit Application…_ ”, then go into the “ _Application_ ” tab and click on “ _Advanced Options_ ”. Here, you should have a “ _Run using dedicated graphics card_ ” checkbox, click on it, then hit “ _Ok_ ” ( _on both dialogs_ ) to confirm.

![This is how it should look like \(Source: CachyOS using switcherooctl\)][13]

There are also many helpful switcherooctl commands that you can make use of to get more control over the GPU switching behavior of your computer. You can refer to the [Arch manual pages][14] and [negativo17's blog][15] to learn more.

This is a great addition to openSUSE as other popular Linux distributions like [Ubuntu][16] and [Fedora][17] already employ switcherooctl to handle systems with multiple GPUs. It is great to see that openSUSE's developers implemented this.

**Suggested Read** 📖

![][18]

* * *

[Get It's FOSS Plus Membership][19]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/opensuse-gaming-gpu-tool/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.opensuse.org/
[4]: https://itsfoss.com/rolling-release/
[5]: https://news.opensuse.org/2024/12/09/gpu-switching-game-changing/
[6]: https://news.itsfoss.com/content/images/2024/12/openSUSE_Tumbleweed_20241208_switcherooctl.png
[7]: https://gitlab.freedesktop.org/hadess/switcheroo-control
[8]: https://github.com/openSUSE/SUSEPrime
[9]: https://github.com/Bumblebee-Project/Bumblebee
[10]: https://github.com/Bumblebee-Project/bbswitch
[11]: https://nouveau.freedesktop.org/
[12]: https://www.nvidia.com/en-us/drivers/
[13]: https://news.itsfoss.com/content/images/2024/12/plasma-cachyos.jpg
[14]: https://man.archlinux.org/man/switcherooctl.1.en
[15]: https://negativo17.org/prime-optimus-laptops-and-multi-gpu-systems/
[16]: https://itsfoss.com/intel-nvidia-graphics-switch-ubuntu/
[17]: https://fedoraproject.org/
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[19]: https://itsfoss.com/#/portal/signup
