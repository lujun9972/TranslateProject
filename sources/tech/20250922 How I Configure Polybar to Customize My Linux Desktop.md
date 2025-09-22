[#]: subject: "How I Configure Polybar to Customize My Linux Desktop"
[#]: via: "https://itsfoss.com/configuring-polybar-linux/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I Configure Polybar to Customize My Linux Desktop
======

[![Warp Terminal][1]][2]

Most major Linux desktop environments like GNOME, KDE Plasma, and Xfce come with their own built-in panels for launching apps, switching workspaces, and keeping track of what’s happening on your system.

![Example of top panel in Xfce][3]

One of the best things about Linux is the freedom to customize, and there are plenty of alternatives out there if you want something more flexible or visually appealing for your panel.

[Polybar][4] is a standout choice among these alternatives. It’s a fast, highly customizable status bar that not only looks great but is also easy to configure.

If you’re running an X11-based setup, such as the i3 window manager or even Xfce, Polybar can really elevate the look of your desktop, help you keep essential info at your fingertips, and make better use of your screen space.

![Example of Polybar in Xfce][5]

We used Polybar in [our Xfce customization video][6] and this is from where we got the idea to do a detailed tutorial on it.

[Subscribe to It's FOSS YouTube Channel][7]

In this guide, we’ll build a sleek Polybar panel just like the one featured in our Xfce customization video above. Along the way, you’ll get a solid introduction to the basics of Polybar customization to help you tailor the panel to your own style and workflow.

🚧

This article is not trying to take over the place of [Polybar Wiki][8]. You can and should read the wiki while customizing Polybar. This article tries to act as a helper companion for beginners to get started.

### Installing Polybar

💡

Most tweaks here are done through the config file at user level. If you get easily overwhelmed and don't like to troubleshoot and fix much, you should probably create a new user account. Or, you could try these things in a fresh system on a VM or on a spare machine. This way, you won't impact your main system. Just a suggestion.

Polybar is a popular project and is available in the official repositories of most major Linux distributions, including Ubuntu, Debian, Arch Linux, Fedora, etc.

If you are a Debian/Ubuntu user, use:

```

    sudo apt install polybar

```

For Arch Linux users,

```

    sudo pacman -S polybar

```

In Fedora Linux, use the command:

```

    sudo dnf install polybar

```

Once you install Polybar, you can actually use it with the default config by using the command:

```

    polybar

```

[Add it to the list of autostart applications][9] to make the bar automatically start at system login.

### Initial configuration setups

Let's say you don't want the default config and you want to start from scratch.

First, make a directory called `polybar` in your `~/.config` directory.

```

    mkdir -p ~/.config/polybar

```

And then create a config file called `config.ini` for Polybar in this location.

```

    touch config.ini

```

Now, you have an empty config file. It's time to 'code'.

#### Config file structure

Polybar config file has a structure that makes things works easier and cleaner.

The whole config can be divided broadly intro four parts.

  * **Colors** : Define the colors to use across polybar
  * **Bar** : Define the properties of the whole bar.
  * **Modules** : Individual bar modules are defined here.
  * **Scripts** : This is not inside the config, but external shell and other scripts that enhance the Polybar functionality.



### Define the colors

Let me share how I am customizing my desktop Linux with the awesome Polybar. This could work as a beginner's guide to understanding Polybar configuration.It is not convinient to write all the colors in hex code separately. While this is good during rough coding, it will create headaches later on, when you want to change colors in bulk.

You can define a set of general colors in the beginning to make things easier.

See an example here:

```

    [colors]
    background = #282A2E
    window-background = #DE282A2E
    background-alt = #373B41
    border-color = #0027A1B9
    foreground = #C5C8C6
    primary = #88c0d0
    secondary = #8ABEB7
    alert = #A54242
    disabled = #707880
    aurora-blue = #27A1B9
    aurora-orange = #FF9535
    aurora-yellow = #FFFDBB
    aurora-green = #53E8D4
    aurora-violet = #8921C2
    nord-background = #4c566a

```

The common definition syntax is explained above. Now, to refer to any color in the list, you can use:

```

    key = ${colors.colorvariable}

```

For example, if you want to set the foreground color in a module, you will use:

```

    foreground = ${colors.foreground}

```

💡

If you intend to change the entire color palette of the bar, all you have to do is create a new color palette and paste it in the config. No need to change individual colors of all modules and sub-items.

### Setting the bar

In simple words, this is the panel appearing in the bar. The one that contains all other modules.

Polybar allows you to have multiple bars. Perhaps that's the reason why it is called 'polybar'. These bars can be named separately in the config file, with their own set of modules.

The bar is placed, defined with the syntax:

```

    [bar/<barname>]
    option = value
    option = value


    [bar/<barname2>]
    option = value
    option = value

```

Let’s say I am creating a top bar and a bottom bar, my simple syntax will be:

```

    [bar/mytopbar]
    options = values

    [bar/mybottombar]
    options = value

```

There will be plenty of options and values to use that you will see later in this tutorial.

Now, if you want to open only the top bar, use:

```

    polybar mytopbar

```

#### Configure the bar

You have seen the general syntax of the bar that mentions options and values. Now, let’s see some options.

I am giving you a code block below, and will explain with the help of that.

```

    monitor = HDMI-1
    width = 100%
    height = 20pt
    radius = 5
    fixed-center = true
    background = ${colors.window-background}
    foreground = ${colors.foreground}
    line-size = 3pt
    border-size = 2.5pt
    border-color = ${colors.border-color}
    padding-left = 0
    padding-right = 0
    module-margin = 1
    separator = "|"
    separator-foreground = ${colors.disabled}
    font-0 = "JetBrains Mono:size=10;3"
    font-1 = monospace;2
    font-2 = "FiraCode Nerd Font:size=11;2"
    font-3 = "Symbols Nerd Font:size=20;4"
    modules-left = mymenu ewmh
    modules-center = date temperature pacupdate
    modules-right = pulseaudio memory cpu eth magic-click sessionLogout
    enable-ipc = true

```

The main options that you may take a closer look are:

  * **monitor** : As the name suggests, this decides on which monitor you want the Polybar. Use the `xrandr` command to get the name of the display. If you are using a multi-monitor setup, you can define a second bar, placing it on the second monitor and so on.
  * **separator** : This is the separator used to separate the modules appearing in Polybar. You can use any item here, including Nerd font items (given the nerd font is installed on the system.).
  * **font-n** : These are fonts to be used in the bar. The number corresponding refers to fallback fonts. That is, if the one mentioned first is not available, the other is used. Take special care to the **Nerd fonts** we have set at `font-2` and `font-3`. This will be explained in a later section.
  * **modules-left, modules-center, modules-right** : Keys used to arrange the modules in the bar. Place the module names on any of this section, then that appears in that part of the bar.
  * **enable-ipc** : Enable Inter-process communication. This allows scripts or external apps to send commands (like module updates or bar reloads) to Polybar in real time.



The above-mentioned options are enough for a working bar. The rest are mostly self-explanatory. You can read more about other options and more help from the [official wiki of Polybar][10].

### Modules

Now that you have placed the bar, it's time to start adding the items.

If you have looked at the above piece of script, you would have noticed that there are some entries in the `modules-left`, `modules-center`, and `modules-right` keys. They are `mymenu ewmh`, `date temperature pacupdate`, and `pulseaudio memory cpu eth magic-click sessionLogout` respectively.

These are calling modules to the bar and placing them in the required position.

In order to call them to the bar, they need to be defined; like what to display at that position. So, our next part is defining the modules.

The general syntax for a module will be

```

    [module/MY_MODULE_NAME]
    type = MODULE_TYPE
    option1 = value1
    option2 = value2
    ...

```

Here, `MY_MODULE_NAME` can be found on the Polybar Wiki, that explains modules. For example, refer to the [CPU module wiki in Polybar][11].

![Getting Module Name][12]

The `type` here will be:

```

    type = internal/cpu

```

🚧

I will be using several modules here, that will create a fine panel for a beginner. You should read the wiki for more modules and customizations as required for your needs.

#### Add Workspaces

Workspaces is a great way to increase productivity by avoiding cluttered windows in front of you. In Polybar, we will be using the `emwh` module to get workspaces in the panel.

Let's see a sample config:

```

    [module/ewmh]
    type = internal/xworkspaces
    icon-0 = 1;
    icon-1 = 2;󰚢
    icon-2 = 3;
    icon-3 = 4;
    icon-4 = 5;
    icon-5 = 6;
    icon-6 = 7;
    icon-7 = 8;
    icon-8 = 9;
    icon-9 = 10;
    format = <label-state>
    format-font = 2
    #group-by-monitor = false
    #pin-workspaces = false
    label-active = %icon%
    label-active-background = ${colors.background-alt}
    label-active-forground = #00000000
    label-active-padding = 2
    label-occupied = %icon%
    label-occupied-padding = 1
    label-urgent = %icon%
    label-urgent-background = ${colors.primary}
    label-urgent-padding = 1
    label-empty = %icon%
    label-empty-foreground = ${colors.disabled}
    label-empty-padding = 1

```

We have already seen what `type` is in the previous section.

In `workspaces`, you should be able to see icons/numbers for each workspace. These icons are defined in the `icon-n` key. The `n` here corresponds to the workspace number.

For desktops like Xfce, the number of workspaces available is managed by the desktop. So, if you are adding icons for 5 workspaces, make sure you have created 5 workspaces in the system settings.

For example, in Xfce, you can search for `Virtual Desktops` in the menu and set the number of workspaces available in the system.

The `format` options tells the bar what to show for which workspace. We have set it as `label-state`. This means, we will define some states (active, empty, occupied, urgent) for the workspaces and the display will be according to that.

The `format-font = 3` tells the polybar to use which font. Here, I have specified `3`, that will refer to `font-3` defined in the bar section. That is `Symbols Nerd Font:size=20;4`. Since I have pasted the nerd font logo from nerd fonts, this will be better to display them properly.

Look at the code below:

```

    label-active = %icon%
    label-active-background = ${colors.background-alt}
    label-active-forground = #00000000
    label-active-padding = 2

```

This sets the value `%icon%` when the workspace is active. When Polybar sees the `%icon%`, it will swap this with the icons defined above. That is `icon-N`. The rest options are visual changes for each of the state, like background color, foreground color, etc.

If you are using nerd fonts for this, these fonts will change their color according to the set foreground color.

Similar is done as needed for other states like empty, urgent, etc. It is up to your creativity to assign what values to these states to make it visually pleasing.

0:00

/0:06

1×

Switch Workspaces in Polybar

#### What is the time now?

A panel without a date is useless! Let's add a date block to Polybar.

The type we use for a [date module][13] is:

```

    type = internal/date

```

We need to format it, so that it looks better. So, take a look at the sample code below:

```

    [module/date]
    type = internal/date
    interval = 1.0
    time = %I:%M %p
    date = %d-%m-%Y
    date-alt = "%{F#FF9535}%Y-%m-%d %I:%M:%S %p%{F-}"
    label = %date% %time%
    label-font = 5
    label-foreground = ${colors.aurora-yellow}
    format = 󱑂 <label>
    format-prefix-font = 2

```

First is the refresh rate. We set the click to refresh every second with the `interval = 1.0`. The value is in seconds.

Next, define what to show with the `time` key. It has to be in a format `strftime`. You can read the full format specification in the [man page here][14].

For now, we are using the format `%I:%M %p`, that will show the time as `12:30 PM`.

We are going a bit further to show you that there are more with `date` module.

Use the `date` key to set the date format. I am using the format `%d-%m-%Y`, which will output `25-07-2025`.

The `date-alt` key can be used to show another date format when you click on the date module in the bar.

💡

You can remember like this; if there is an `alt` in the name of a key, then it define an action that is available upon clicking that module.

The syntax `%{F#RRGGBB}` in Polybar is used to set the foreground color dynamically within the module’s label or format string. This is like `<span>` tag in the HTML codes.

So this will tell Polybar “from here on, use this foreground (text) color,” and once the `%{F-}` is spotted, reset it to general flow, or what was before.

So, according to the code, when we click on the date module, it will show the detailed date format as `%Y-%m-%d %I:%M:%S %p`, which in real world, `2025-07-25 12:30:25 PM`.

0:00

/0:07

1×

Showing date in Polybar with an alternate format

The `label = %date% %time%`, make sure the bar will show date and time properly.

The `format = 󱑂 <label>` will show the date with a preceding nerd font icon.

It is in the `format` key, you add icons/glyphs to appear on the bar most of the time.

#### How do I change the volume?

Most common way to change the volume in most system is to scroll on the volume button on panel. This is possible with Polybar as well.

Let's see a code for the module:

```

    [module/pulseaudio]
    type = internal/pulseaudio
    format-volume-prefix-foreground = ${colors.primary}
    format-volume = <label-volume> <ramp-volume>
    label-volume = %percentage%%
    use-ui-max = false
    click-right = pavucontrol
    label-muted = " Mute"
    label-muted-foreground = ${colors.disabled}
    format-muted = <label-muted>
    format-muted-prefix = 󰝟
    format-muted-prefix-font = 2
    format-muted-padding = 1

    ; Ramp settings using <ramp-volume> used for Pulseaudio
    ramp-volume-0 = 󰝟
    ramp-volume-1 = ▁
    ramp-volume-2 = ▂
    ramp-volume-3 = ▃
    ramp-volume-4 = ▄
    ramp-volume-5 = ▅
    ramp-volume-6 = ▆
    ramp-volume-7 = ▇
    ramp-volume-8 = █
    ramp-volume-font = 2

```

As you expected, `type = internal/pulseaudio` is the module type.

The next entry to look is `format-volume`. Here, we see a new item called `<ramp-volume>`. And if you look further down the code, you can see I have defined 9 levels (0 to 8) of ramp.

This `ramp-<item>` is available in some other module also. So, understanding it here is better to use them as required. For example, the [**cpu**][11] module give a `ramp-coreload`, [**memory**][15] module gives `ramp-used` and `ramp-free`, etc.

It shows a visual volume indicator (like volume bars or icons) depending on the number of ramp levels. For example, in the above volume, the 100% volume level is divided into 9 equal ranges. So, when the volume is increased, an appropriate bar is shown.

0:00

/0:10

1×

Change the volume with ramps

Another useful options are the mouse-click items. Generally, you have three of them available:

  * click-left
  * click-middle
  * click-right



It is not limited to pulseaudio, you can use it in some other modules also. For that, refer to the wiki page.

#### Tray

Many apps needs an active tray module to work. Discord, Spotify, Ksnip, Flameshot, all provides a close to tray option as well.

In Polybar, you will be using the `tray` module for this purpose.

```

    [module/tray]
    type = internal/tray

    format-margin = 8px
    tray-spacing = 8px

```

It has several option you can try, in the official wiki. Rewriting them here is not an efficient way, since a bare module serves most purposes.

🚧

In Linux systems, only one panel can take the tray. So, you only needed to add it in one tray. Similarly, in Xfce and other distros, which by default offers a panel with tray, using the `tray` module will not work properly.

### Scripts and Custom Module

This is not the scope of this article to explain bash shell scripts/ python scripts. But we will see custom modules in Polybar, that you can use to extend the function to next level.

But, with Polybar, you can create shell scripts and then use it at places in modules. For example, take a look at the code below, that defines a custom module to show any package update available in Arch Linux:

```

    [module/pacupdate]
    type = custom/script
    exec = /home/$USER/.config/polybar/pacupdates.sh
    interval = 1000
    label = %output%
    format-font = 3
    click-left = notify-send "Updates:" "$(checkupdates)"

```

As you can see, I got the `type` as `custom/script` from the [wiki for scripts][16].

Check the `exec` field. It points what to execute in the module. This can either be a simple command or point to the path to a script. Here, I pointed it to a script called `pacupdates` located on my `~/.config/polybar/` directory.

The contents of the script is available in our GitHub repo. What it does is check and tell whether any package update is available.

0:00

/0:06

1×

A custom script that will print what updates is available in the system when clicked on it

This is not an in-built module in Polybar. We have created it. With that, let's see a general syntax for custom modules:

```

    [module/MODULE_NAME]
    type = custom/script
    exec = COMMAND_OR_SCRIPT_PATH
    interval = SECONDS
    label = %output%
    format = <label>
    format-prefix = "ICON_OR_TEXT "
    format-prefix-font = FONT_INDEX
    click-left = COMMAND_ON_LEFT_CLICK
    click-right = COMMAND_ON_RIGHT_CLICK
    click-middle = COMMAND_ON_MIDDLE_CLICK

```

The `%output%` value to the label (if you remember, you have seen `%icon%` earlier) refers to the output of the exec field.

We have seen other values in various other sections above.

Before we finish, take a look at one more custom module example, which when clicked opens rofi:

```

    [module/mymenu]
    type = custom/text
    format = <label>
    format-padding = 2
    label = "%{F#1A1B26}  Menu%{F-}"
    click-left = /home/sreenathv/.config/polybar/rofi.sh
    format-background = ${colors.aurora-blue}

```

![Menu Button \(Click to enlarge the image\)][17]

Do not forget to add these to the tray after defined otherwise they won't appear.

### Wrapping Up

Apart from the modules we discussed, there are many other modules that you can use. We have provided [a ready to use Polybar config with several scripts in out GitHub page][18].

Take a look at the lines on code in that files and get a better grasp of Polybar config.

I hope you liked this detailed guide to Polybar customization. If you have any questions or suggestions, please leave a comment and I'll be happy to answer them.

--------------------------------------------------------------------------------

via: https://itsfoss.com/configuring-polybar-linux/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/09/xfce-top-panel-1.png
[4]: https://polybar.github.io/
[5]: https://itsfoss.com/content/images/2025/09/xfce-polybar-panel-1.png
[6]: https://www.youtube.com/watch?v=fw4dLnMNecE
[7]: https://www.youtube.com/@itsfoss
[8]: https://github.com/polybar/polybar/wiki/
[9]: https://itsfoss.com/manage-startup-applications-ubuntu/
[10]: https://github.com/polybar/polybar/wiki/Configuration
[11]: https://github.com/polybar/polybar/wiki/Module:-cpu
[12]: https://itsfoss.com/content/images/2025/07/module-name-in-wiki.png
[13]: https://github.com/polybar/polybar/wiki/Module:-date
[14]: https://man7.org/linux/man-pages/man3/strftime.3.html
[15]: https://github.com/polybar/polybar/wiki/Module:-memory
[16]: https://github.com/polybar/polybar/wiki/Module:-script
[17]: https://itsfoss.com/content/images/2025/07/mymenu-module.png
[18]: https://github.com/itsfoss/text-script-files/tree/master/config/polybar
