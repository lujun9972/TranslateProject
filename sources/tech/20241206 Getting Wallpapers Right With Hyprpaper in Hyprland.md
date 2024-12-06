[#]: subject: "Getting Wallpapers Right With Hyprpaper in Hyprland"
[#]: via: "https://itsfoss.com/hyprpaper-hyprland/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Getting Wallpapers Right With Hyprpaper in Hyprland
======

[![Warp Terminal][1]][2]

A beautiful wallpaper enhances the aesthetic appeal of a desktop.

In desktop environments like GNOME and KDE, all you have to do is a right-click to set wallpaper.

However, that's not how we roll in the Hyprland. We do all sort of configuration to make it work.

But that's the fun of it, right? Let's see how to utilize Hyprpaper in Hyprland for your wallpaper setup.

### What is Hyprpaper?

[Hyprpaper][3] is a Wayland wallpaper utility, which works on Hyprland and other wlroots-based compositors. This means that you can use this in other desktops like [Sway][4], even though it is a Hyprland program.

Let's take a look at some of its features.

  * Per-output wallpapers
  * Fill, tile or contain modes
  * Fractional scaling support
  * IPC for blazing fast wallpaper switches
  * Preloading targets into memory



### Install Hyprpaper on your Linux distribution

Since Hyprpaper is an important part of Hyprland, it should be present in the default repositories of distributions that have Hyprland present.

In Arch Linux, you can install Hyprpaper using the command:

```

    sudo pacman -S hyprpaper

```

Fedora users can use:

```

    sudo dnf install hyprpaper

```

openSUSE users can install it using the zypper package manager:

```

    sudo zypper install hyprland

```

📋

For other distributions, you may need to [build it from source code][5] manually. In that case, keep an eye on the dependencies.

### Using Hyprpaper

Unlike usual wallpaper managers, Hyprpaper does not have a GUI. This should not surprise you, as you are in Hyprland now.

Here, you need to tweak the configuration file of Hyprpaper for necessary changes.

✋

Hyprpaper expects its configuration file at `.config/hypr/hyprpaper.conf`. You need to create this file to configure the program.

#### Simple Hyprpaper configuration

A basic configuration of Hyprpaper should contain the following two lines:

```

    preload=path/to/wallpaper/image
    wallpaper=<monitor-name>,path/to/wallpaper/image

```

Here, the `preload` tag is used to load the images to RAM, so that Hyprland can set that wallpaper.

To set separate wallpapers in a dual monitor setup, you must preload both the images in the configuration.

```

    preload=path/to/image_one
    preload=path/to/image/two

    wallpaper=<monitor_1-name>,path/to/image_one
    wallpaper=<monitor_2-name>,path/to/image_two

```

📋

You probably already know this. When you see `<XYZ>` in a command example, it means that you have to replace entire <XYZ> with the actual value.

![Dual monitor, different wallpapers][6]

Thus, for any wallpaper to appear in Hyprland, you should preload it with the `preload` tag.

💡

You should limit the number of images you preload. A lot of preloaded images will affect the RAM usage. Only load images that are currently in use.

##### Wait, how to get monitor name?

In the above section, you need the name of the monitors to set wallpaper to that particular monitor.

On Hyprland, you can use the command below to get the name of your monitor/monitors.

```

    hyprctl monitors

```

![Get monitor name][7]

From the above screenshot, the monitor name is `Virtual-1` as this is a Virtual machine. Your name can be HDMI-1, DP-1 etc.

#### Add the splash text

You can add a splash text over the wallpaper using the `splash` option.

Open the Hyprpaper config file and add the line at the end:

```

    splash = true

```

Now, when you reload the Hyprpaper, you will get a splash text displayed.

![Splash Text][8]

Other than that, you can adjust the spacing of this text by using the `splash_offset` percentage variable. The value is relative to the bottom. So, a 50.0 means 50% above the bottom of the monitor.

```

    splash = true
    splash_offset = 50.0

```

📋

From what I checked, the splash text was not editable. Please correct me if I am wrong in the comments.

#### Switch wallpaper with shortcuts

Until now, you must have observed that for each wallpaper change, you need to restart Hyprpaper to get the effect. However, Hyprpaper utilizes IPC or [Inter-Process Communication][9] to switch between wallpapers quickly and without reloading the entire program each time a wallpaper is changed.

Here, we will use the `hyprctl` command of Hyprland to manage the Hyprpaper wallpapers.

We will look into two cases:

  * Preload wallpapers in Hyprpaper config and then switch fast (impacts RAM)
  * Use a script to preload wallpaper and then unload when not needed.



##### Method 1: Preload a wallpaper and apply to workspaces

As we have seen in the first section, it is necessary to preload all the images you want to use in the Hyprpaper config file `.config/hypr/hyprpaper.conf`. Also, enable `ipc`.

```

    preload = /path/to/image_one.png
    preload = /path/to/image_two.png
    preload = /path/to/image_three.png
    preload = /path/to/image_four.png
    preload = /path/to/image_five.png

    ipc = true

```

🚧

In this preloading, if each wallpaper is 500KB, then a total 2.5MB of RAM will be used for preloading all this wallpaper. If you are a laptop user and IPC results in battery drain, turn it off in config using `ipc = false`.

To change the wallpaper, use the general syntax:

```

    hyprctl hyprpaper wallpaper "<monitor_name>,/path/to/wallpaper"

```

But before that, open your Hyprland config:

```

    vim .config/hypr/hyprland.conf

```

Now, let's say you have stored the images as _1.png to 5.png_ in the `~/Pictures/Wallpapers` directory.

So, for each wallpaper, create a variable. This is not necessary, and we are doing it for convenience with the keyboard shortcuts.

```

    $wall_1 = hyprctl hyprpaper wallpaper "Virtual-1,~/Pictures/Wallpapers/1.png"

    $wall_2 = hyprctl hyprpaper wallpaper "Virtual-1,~/Pictures/Wallpapers/2.png"

    $wall_3 = hyprctl hyprpaper wallpaper "Virtual-1,~/Pictures/Wallpapers/3.png"

    $wall_4 = hyprctl hyprpaper wallpaper "Virtual-1,~/Pictures/Wallpapers/4.png"

    $wall_5 = hyprctl hyprpaper wallpaper "Virtual-1,~/Pictures/Wallpapers/5.png"

```

To assign a keyboard shortcut, the general syntax in Hyprland is:

```

    bind = modifier_key,desired_key,action,value

```

Look at the sample Hyprland key bind config shown below:

```

    bind = SUPER, H, exec, $wall_1
    bind = SUPER, J, exec, $wall_2
    bind = SUPER, K, exec, $wall_3
    bind = SUPER, B, exec, $wall_4
    bind = SUPER, N, exec, $wall_5

```

Shortcuts like **Super + H** are assigned to the respective wallpaper change command. The result will be, when you press that shortcut, the related wallpaper will be loaded.

##### Method 2: Using a script to load the image

The process above is pretty fast since you are using a preloaded image. But this speed comes with a small impact on your physical memory.

If you can accept a small delay, use a script to load the image and then unload when not needed.

Let's see the script and then identify included components.

```

    #!/bin/bash

    WALLPAPER_DIRECTORY=~/Pictures/Wallpapers

    WALLPAPER=$(find "$WALLPAPER_DIRECTORY" -type f | shuf -n 1)

    hyprctl hyprpaper preload "$WALLPAPER"
    hyprctl hyprpaper wallpaper "Virtual-1,$WALLPAPER"

    sleep 1

    hyprctl hyprpaper unload unused

```

Here, in this script, we define a variable for wallpaper directory `WALLPAPER_DIRECTORY`. This should contain only images.

📋

Remember, if you are preloading images in the Hyprpaper config, then there is no need to use the preload and unload commands in the above script.

Now, using a `WALLPAPER` variable, we select a random image from the directory.

With Hyprpaper IPC feature, we use the `hyprctl` command to preload a wallpaper. Now, the preloaded wallpaper is the one selected at random from our wallpaper directory.

Once it is preloaded, we will apply it to a monitor using the `hyprctl` command. If you have to change the wallpaper for another monitor, include that as well. Like:

```

    hyprctl hyprpaper wallpaper "Virtual-1,$WALLPAPER"

```

Now, wait for one second and then unload all the unused images. This is to ensure that there are no adverse effects on RAM.

Once the script is ready, save it as `change_wallpapers.sh`. Give the script execution permission.

```

    chmod +x change_wallpapers.sh

```

Now, for convenient access, we save this file inside the `~/.config/hypr` directory.

After that, open the Hyprland config and add a key binding to change the wallpaper at random.

```

    bind SUPER, I, exec, ~/.config/hypr/change_wallpapers.sh

```

Restart Hyprland to make the changes permanent. Now, when you press the key combination, a wallpaper is applied at random.

#### Set different wallpapers to workspaces

This is the same as the previous section, except for key binding settings.

##### Preset wallpapers per workspace

Let's say you have preloaded all the wallpapers in Hyprpaper config and assigned the wallpaper changing commands to variables in Hyprland config, i.e. the first method in the previous section.

Now, to change wallpaper per workspace, all you have to do is make the wallpaper key binding same as the workspace switch key binding.

So, in Hyprland, to switch to Workspace One, you will use the shortcut **SUPER + 1**. So, we set this same keybinding for a wallpaper variable.

```

    bind = SUPER, 1, exec, $wall_1

```

📋

The `$wall_1` is the same variable used in the previous section.

Similarly, for other workspaces too:

```

    bind = SUPER, 2, exec, $wall_2
    bind = SUPER, 3, exec, $wall_3
    bind = SUPER, 4, exec, $wall_4
    bind = SUPER, 5, exec, $wall_5

```

That's it. Now, each workspace has its own wallpapers.

🚧

Remember that other programs like Waybar workspace switcher won't work because they need different settings, which aren't covered in this article.

![Different Wallpapers per workspace][10]

##### Random wallpapers for different workspaces

Now, if you want to get a random wallpaper for workspace switch, use:

```

    bind = SUPER, 1, exec, ~/.config/hypr/change_wallpapers.sh
    bind = SUPER, 2, exec, ~/.config/hypr/change_wallpapers.sh
    bind = SUPER, 3, exec, ~/.config/hypr/change_wallpapers.sh
    bind = SUPER, 4, exec, ~/.config/hypr/change_wallpapers.sh
    bind = SUPER, 5, exec, ~/.config/hypr/change_wallpapers.sh

```

Here, you don't need to preload images in Hyprpaper config as the scripts loads and unloads them.

Once saved, you can get a different wallpaper per workspace randomly.

#### Set day-night wallpapers

Now, it's time to set wallpapers according to day and night timing. Here, we use [the cron job concepts][11].

First, you need to create a script, called `day_night.sh`. You can create this inside the `.config/hypr/` folder for easy access.

Inside this file, add these lines:

```

    #!/bin/bash

    # Wait for 5 seconds to start the script.
    sleep 5

    # Define daytime and nighttime image to respective variables
    DAYTIME_WALLPAPER=~/Pictures/Wallpapers/3.png
    NIGHTTIME_WALLPAPER=~/Pictures/Wallpapers/4.png

    # Calculate the present hour and save it to a variable
    PRESENT_TIME=$(date +%H)

    # In an if loop, check if current time is between 6 am and 6 pm
    # and assign day wallpaper to wallpaper variable.
    # Else, if time is between 6 pm and 6 am,
    # assign night time wallpaper to wallpaper variable.
    if [ $PRESENT_TIME -ge 6 ] && [ $PRESENT_TIME -lt 18 ]; then
        WALLPAPER=$DAYTIME_WALLPAPER
    else
        WALLPAPER=$NIGHTTIME_WALLPAPER
    fi

    # Preload the wallpaper in the wallpaper variable.
    hyprctl hyprpaper preload "$WALLPAPER"

    # Sleep 5 secconds to make sure that everything has time.
    sleep 5

    # Apply the wallpaper to current display.
    hyprctl hyprpaper wallpaper "Virtual-1,$WALLPAPER"

    # Sleep for a second
    sleep 1

    # Exit with success.
    exit 0

```

This simple bash script, saved as `day_night.sh`, checks the current hour. If it is greater than 6 and less than 18 (6 PM), a pre-defined daytime wallpaper is applied. In other case, a night wallpaper is applied. **Don't forget to make it executable**!

Now, we don't need this script to run all the time. So, using cron, we will set this to run exactly at 6 and 18 hours.

On a terminal. Run the command:

```

    crontab -e

```

Here, in the editor, enter the lines as below:

```

    0 6 * * * /home/team/.config/hypr/day_night.sh
    0 18 * * * /home/team/.config/hypr/day_night.sh

```

Save and exit. You can use `crontab -l` to check whether our job is running.

![Listing cron jobs][12]

Now, if you restart the system, there is a chance that you end up with no wallpaper. To avoid that, you can autostart your script at Hyprland startup.

Add these line in your Hyprland config:

```

    exec-once hyprpaper
    exec-once /home/team/.config/hypr/day_night.sh

```

That's it. Enjoy your day/night wallpapers!

### Conclusion

This much trouble for something as simple as wallpapers? Well, things are vastly different in the Hyprland and to the enthusiasts, this is the fun part. Doing things in a complicated manner teaches things you probably would not have learned on your own.

Do let me know if you have questions or suggestions on this topic.

--------------------------------------------------------------------------------

via: https://itsfoss.com/hyprpaper-hyprland/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/hyprwm/hyprpaper
[4]: https://itsfoss.com/sway-window-manager/
[5]: https://itsfoss.com/install-software-from-source-code/
[6]: https://itsfoss.com/content/images/2024/12/hyprland-hyprpaper-different-wallpaper-for-different-monitor.jpg
[7]: https://itsfoss.com/content/images/2024/11/get-the-monitor-name.png
[8]: https://itsfoss.com/content/images/2024/11/splash-text-in-hyprpaper.png
[9]: https://learn.netdata.cloud/docs/collecting-metrics/linux-systems/ipc/inter-process-communication
[10]: https://itsfoss.com/content/images/2024/12/wallpaper-1.jpg
[11]: https://itsfoss.com/cron-job/
[12]: https://itsfoss.com/content/images/2024/11/crontab-job-hyprpaper.png
