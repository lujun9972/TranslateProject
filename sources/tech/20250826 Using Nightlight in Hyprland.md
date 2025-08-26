[#]: subject: "Using Nightlight in Hyprland"
[#]: via: "https://itsfoss.com/nightlight-hyprland/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Using Nightlight in Hyprland
======

[![Warp Terminal][1]][2]

I presume that you are no stranger to the nightlight feature. It filters blue light from your screen and shifts colors to warmer, orange tones during evening hours, reducing eye strain while using computers at night.

From KDE to Cinnamon, most [Linux desktop environments][3] offer this as a bulit-in feature. Look at [GNOME Nightlight feature][4]; it is available right from the quick toggle buttons.

![GNOME Nightlight][5]

Don't get your hopes high if [you are using Hyprland][6]. You won't get a click to enable nighlight feature here. However, you can surely configure your way out of the blue light.

### hyprsunset: The Hyprland nightlight tool

[Hyprland][6] has an ecosystem of tools like [Hyprpaper][7] (wallpaper utility), hyprlock (lockscreen utility), etc. In that regard, [hyprsunset][8] is a small utility that provides nightlight in Hyprland.

🚧

hyprsunset is available from Hyprland 0.45 onwards. Since Hyprland is in a highly active state, I'll presume that most of the Hyprland users are already using the latest and greatest version.

If you are on Arch Linux, you can install hyprsunset from the official repository using:

```

    sudo pacman -S hyprsunset

```

[hyprsunset][8]

### Configure hyprsunset

Once you installed, you need to configure hyprsunset with values.

First, create a configuration file at `~/.config/hypr` called `hyprsunset.conf`.

```

    nano ~/.config/hypr/hyprsunset.conf

```

#### Set the gamma

You can set the maximum gamma in hyprsunset using the `max-gamma` keyword. This is useful for controlling hyprsunset using hyprctl. You will see that in a later section.

```

    max-gamma = 150

```

This sets the maximum gamma to 150%. The absolute maximum gamma is set at 200%. You cannot set it beyond 200. **A high value of gamma will increase the brightness beyond comfortable limits.**

#### Profiles

hyprsunset works by setting profiles of nightlight conditions. You can consider it a time-based rule for the screen settings.

The general syntax is:

```

    profile {
      option = value
    }

```

##### Day-time profile

You don't want to enable the nightlight during the day. So, create a profile for the daytime usage.

```

    max-gamma = 150

    profile {
      time = 6:00
      identity = true
      gamma = 1.0
    }

```

The above profile will be activated at 6 AM. You see, it sets three options:

  * **time** : Specifies at what time the profile should be activated.
  * **identity** : Effectively disables the temperature settings. Your display will work at normal values.
  * **gamma** : While the `identity` setting is true, you can only change the gamma values. Any temperature change is ignored. In the example, it is set to 100% (1.0). If you have a very dim monitor, set it to a higher value. Remember, it can't go above the `max-gamma` set value, here 150 (1.5).



##### Night-time profile

Let's say you want to create a warmer profile when the time is 6 o'clock in the evening.

```

    profile {
      time = 18:00
      temperature = 5500
      gamma = 0.8
    }

```

The above profile will be activated at 6 PM and apply a 5500K temperature.

You can create more profiles with hyprsunset. For example, an even dimmer and warmer temperature at 11 p.m. at night as a reminder to sleep.

```

    profile {
      time = 23:00
      temperature = 4000
      gamma = 0.7
    }

```

So, your config file (`~/.config/hypr/hyprsunset`) will look like this:

```

    max-gamma = 150

    profile {
      time = 6:00
      identity = true
      gamma = 1.0
    }

    profile {
      time = 18:00
      temperature = 5500
      gamma = 0.8
    }

    profile {
      time = 23:00
      temperature = 4000
      gamma = 0.7
    }

```

The choice is all yours. You can play with the configuration as much as you like.

📋

There are almost no screenshots or videos in this tutorial because the screenshots do not capture the effect of nightlight.

### Start hyprsunset

The best and easiest way to start hyprsunset is using the Hyprland config file (`~/.config/hypr/hyprland.conf`).

Open the config file and scroll to the location where application autostart is defined (`exec-once` statements). Then add the following line:

```

    exec-once = hyprsunset

```

### Change temperature with shortcuts

Earlier, I mentioned that you can control hyprsunset using the `hyprctl` command. This is possible because hyprsunset supports IPC (inter-process communication).

See the command below that will reduce the temperature by 500K:

```

    hyprctl hyprsunset temperature -500

```

So, in Hyprland config, you can set the keyboard shortcut to get the effect.

```

    bind = $mainMod, H, exec, hyprctl hyprsunset temperature +500
    bind = $mainMod, B, exec, hyprctl hyprsunset temperature -500

```

Restart Hyprland and you can change the temperature with the keyboard shortcuts.

When a new profile is activated, this setting adjusts to the value mentioned in the profile.

### Wrapping Up

FYI, Plus members of It's FOSS can access [our Hyprland series][9] for more organized learning.

![][10]

I feel that Nightlight is one such feature that should be enabled immediately after installing a system. Staring into the monitor late at night is never comfortable to the eyes. Even though the bluelight filter alone cannot entirely make your eyes safe, nightlight is still a welcome feature.

You should practice other measures as well, like not staring at the screen for more than 30 minutes continuously. There are apps that allow you to take frequent breaks from screen that you can rely on. I'll see if I can find some for Hyprland.

Enjoy the night light 💡

--------------------------------------------------------------------------------

via: https://itsfoss.com/nightlight-hyprland/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/best-linux-desktop-environments/
[4]: https://itsfoss.com/night-shift-flux-ubuntu-linux/
[5]: https://itsfoss.com/content/images/2025/08/gnome-nightlight.png
[6]: https://itsfoss.com/hyprland/
[7]: https://itsfoss.com/hyprpaper-hyprland/
[8]: https://github.com/hyprwm/hyprsunset
[9]: https://plus.itsfoss.com/courses/hyprland/
[10]: https://itsfoss.com/content/images/icon/favicon-21.ico
