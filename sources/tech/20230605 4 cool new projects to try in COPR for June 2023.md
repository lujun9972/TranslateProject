[#]: subject: "4 cool new projects to try in COPR for June 2023"
[#]: via: "https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-june-2023/"
[#]: author: "Jakub Kadlčík https://fedoramagazine.org/author/frostyx/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in COPR for June 2023
======

![][1]

[Copr][2] is a build-system for anyone in the Fedora community. It hosts thousands of projects for various purposes and audiences. Some of them should never be installed by anyone, some are already being transitioned to the official Fedora Linux repositories, and the rest is somewhere in between. Copr gives you the opportunity to install 3rd party software that is not available in Fedora Linux repositories, try nightly versions of your dependencies, use patched builds of your favorite tools to support some non-standard use-cases, and just experiment freely.

If you don’t know [how to enable a repository][3] or if you are concerned about whether [is it safe to use Copr][4], please consult the [project documentation][5].

This article takes a closer look at interesting projects that recently landed in Copr.

## [][6] chatGPT-shell-cli

This year it seems that anywhere you look, [ChatGPT][7] is there. This time we have a lightweight ChatGPT and [DALL-E][8] client, written in Bash, called [chatGPT-shell-cli][9]. Look for the “Commands” section at [chatGPT-shell-cli][10] for usage. This Bash script can be especially useful for systems without standard dependencies such as Python or Node.js.

![][11]

### [][12] Installation instructions

The [repo][13] currently provides _chatgpt-shell-cli_ for Fedora 37, 38, Fedora Rawhide, RHEL8, RHEL9, and others. To install it, use these commands:

```

    sudo dnf copr enable kylegospo/chatGPT-shell-cli
    sudo dnf install chatgpt-shell-cli

```

Note that an OpenAI API key is required to use this script. You may create an account and get a free API Key at [OpenAI][14].

## [][15] Hyprland

[Hyprland][16] is a beautiful looking compositor for Wayland. It provides dynamic tiling with multiple layouts, smooth animations, and endless customization options. Similarly to [Sway][17] or [i3][18], it has a simple configuration file that doesn’t require you to know the programming language it was written in.

![][19]

### [][20] Installation instructions

The [repo][21] currently provides Hyprland for Fedora 37, 38, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable carlwgeorge/hyprland
    sudo dnf install hyprland

```

## [][22] Wezterm

[Wezterm][23] is a modern terminal emulator that runs on all the major operating systems. It has built-in support for terminal multiplexing, rendering images, emojis, GPU acceleration, and many more features.

![][24]

### [][25] Installation instructions

The [repo][26] currently provides Wezterm for Fedora 37, 38, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable zjlin/majesty-dubbed-skyline
    sudo dnf install wezterm

```

## [][27] htpdate

[htpdate][28] is a time synchronization client for the HTTP Time Protocol (HTP). Is it better than Network Time Protocol (NTP) which is used in Fedora by default? It is not! [You should use NTP if you can][29]. However, NTP sometimes doesn’t work because of proxy or firewall restrictions. That’s when HTP and _htpdate_ become very useful.

![][30]

### [][31] Installation instructions

The [repo][32] currently provides _htpdate_ for Fedora 37, 38, Fedora Rawhide, Fedora ELN, RHEL8, RHEL9, and others. To install it, use these commands:

```

    sudo dnf copr enable whitehara/htpdate
    sudo dnf install htpdate

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-june-2023/

作者：[Jakub Kadlčík][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/frostyx/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/copr-magazine-816x345.jpg
[2]: https://copr.fedorainfracloud.org/
[3]: https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo
[4]: https://docs.pagure.org/copr.copr/user_documentation.html#is-it-safe-to-use-copr
[5]: https://docs.pagure.org/copr.copr/user_documentation.html
[6]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#chatgpt-shell-cli
[7]: https://openai.com/product/chatgpt
[8]: https://openai.com/product/dall-e-2
[9]: https://github.com/0xacx/chatGPT-shell-cli
[10]: http://github.com/0xacx/chatGPT-shell-cli
[11]: https://fedoramagazine.org/wp-content/uploads/2023/05/chatgpt.png
[12]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#installation-instructions
[13]: https://copr.fedorainfracloud.org/coprs/kylegospo/chatGPT-shell-cli/
[14]: https://beta.openai.com/account/api-keys
[15]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#hyprland
[16]: https://hyprland.org/
[17]: https://swaywm.org/
[18]: https://i3wm.org/
[19]: https://fedoramagazine.org/wp-content/uploads/2023/05/hyprland.png
[20]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#installation-instructions-1
[21]: https://copr.fedorainfracloud.org/coprs/carlwgeorge/hyprland/
[22]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#wezterm
[23]: https://wezfurlong.org/wezterm/
[24]: https://fedoramagazine.org/wp-content/uploads/2023/05/wezterm.png
[25]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#installation-instructions-2
[26]: https://copr.fedorainfracloud.org/coprs/zjlin/majesty-dubbed-skyline/
[27]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#htpdate
[28]: http://www.vervest.org/htp/
[29]: https://www.vervest.org/htp/?FAQ
[30]: https://fedoramagazine.org/wp-content/uploads/2023/05/htpdate.png
[31]: https://github.com/frostyx/fedora-magazine/blob/main/2023-june.md#installation-instructions-3
[32]: https://copr.fedorainfracloud.org/coprs/whitehara/htpdate/
