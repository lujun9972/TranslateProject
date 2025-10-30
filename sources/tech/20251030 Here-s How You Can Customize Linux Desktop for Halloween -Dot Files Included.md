[#]: subject: "Here's How You Can Customize Linux Desktop for Halloween [Dot Files Included]"
[#]: via: "https://itsfoss.com/hyprland-halloween-customization/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Here's How You Can Customize Linux Desktop for Halloween [Dot Files Included]
======

[![Warp Terminal][1]][2]

Halloween is here. Some people carve pumpkins, I crafted a special set up for my Arch Linux 🎃

0:00

/0:30

1×

In this tutorial, I'll share with you all the steps I took to give a Halloween-inspired dark, spooky makeover with Hyprland. Since it is Hyprland, you can relatively easily replicate the setup by getting the [dot files from our GitHub repository][3].

🚧

This specific setup was done with Hyprland window compositor on top of Arch Linux. If you are not [using Hyprland][4] and still want to try it, I advise [installing Arch Linux in a virtual machine][5].

If videos are your thing, you can watch all the steps in action in [this video on our YouTube channel][6].

[Subscribe to It's FOSS YouTube Channel][7]

### Step 1: Install Hyprland and necessary packages

First, install all the essential Hyprland packages to get the system up and running:

```

    sudo pacman -S hyprland xdg-desktop-portal-hyprland hyprpolkitagent kitty

```

The above will install Hyprland and necessary packages. Now, install other utility packages.

```

    sudo pacman -S hyprpaper hyprpicker hyprlock waybar wofi dunst fastfetch bat eza starship nautilus

```

What do these packages do? Well, here are some info:

  * `hyprpaper`: [Hyprland Wallpaper][8] utility
  * `hyprpicker`: Color picker
  * `hyprlock`: Lock screen utility
  * `waybar`: [Waybar][9] is a Wayland panel
  * `wofi`: Rofi launcher alternative, but for Wayland. Rofi can be used. In fact, we have some preset config for Rofi in our GitHub repository. But Wofi was selected for this video.
  * `dunst`: Notification daemon.
  * `fastfetch`: [fastfetch][10] is a system information display utility.
  * `bat`: [Modern alternative][11] for `cat` command.
  * `eza`: Modern `ls` command alternative
  * `starship`: [Starship][12] is a prompt customization tool.
  * `nautilus`: Nautilus is the file manager from GNOME.



### Step 2: Install and enable display manager

You need a [display manager][13] to login to the system. We use SDDM display manager. GDM also works fine with Hyprland.

```

    sudo pacman -S sddm

```

Once SDDM package is installed, enable the display manager on boot time.

```

    sudo systemctl enable sddm.service

```

![Enable SDDM][14]

Now, reboot the system. When login prompt appears, login to the system.

![Login to Hyprland][15]

### Step 3: Install other utility packages

Once [essential Hyprland packages][16] are installed and you are logged in, open a terminal in Hyprland using `Super + Q`. Now install Firefox browser using:

```

    sudo pacman -S firefox

```

It's time to install theme packages. Hyprland is not a desktop environment in the sense of what GNOME or KDE is. Yet you may still use some apps developed for GNOME (GTK apps) or Qt apps.

To theme, you need to install theme managers for respective system:

  * `nwg-look`: To apply theme to GTK apps.
  * `qt5ct`: To apply theme to Qt5 apps.



Install these packages using the command:

```

    sudo pacman -S qt5ct nwg-look

```

🚧

If you are using a minimal installation of Arch Linux, you may need to install an editor like `nano` to edit file in terminal.

### Step 4: Change the monitor settings

In most cases, Hyprland should recognize the monitor and load accordingly. But in case you are running it in a VM, it will not set the display size properly.

Even though we give full configuration at a later stage, if you want to fix the monitor, use the command:

```

    monitor=<Monitor-name>,1920x1080,auto,auto

```

![Monitor settings][17]

It is important to get the name of the monitor. Use this command:

```

    hyprctl monitors

```

Remember the name of your monitor.

![Get monitor name][18]

### Step 5: Download our custom Hyprland dot files

Go to It's FOSS GitHub page and download the `text-script-files` repository.

![Download config files][19]

[Download Config Files][20]

You can also clone the repo, if you want using the command:

```

    git clone https://github.com/itsfoss/text-script-files.git

```

But the above needs [git installed][21].

If you have downloaded the zip file, extract the archive file. **Inside that, you will find a directory`config/halloween-hyprland`. This is what we need in this article**.

### Step 6: Copy wallpaper to directory

Copy the images in the `wallpapers` folder to a directory called `~/Pictures/Wallpapers`. Create it if it does not exist, of course.

```

    mkdir -p ~/Pictures/Wallpapers

```

![Copy wallpapers][22]

### Step 7: Download GTK theme, icons and fonts

Download the **Everforest GTK theme dark borderless macOS buttons**.

![Download GTK theme][23]

[Download Everforest GTK Theme][24]

Download Dominus Funeral icon theme dark style.

![Download Icon theme][25]

[Download Dominus Funeral Icon theme][26]

Download the "Creepster" font from Google Fonts website.

[Download Creepster font][27]

Next, create `~/.themes`, `~/.icons`, and `~/.fonts` respectively:

```

    mkdir -p ~/.themes ~/.icons ~/.fonts

```

And we need to paste theme, icon, and font files in their respective locations:

  * Extract the "Creepster" font file and place it at `~/.fonts`.
  * Extract the theme file and paste it at `~/.themes`.
  * Extract the icon file and paste it at `~/.icons`



![Paste thems, icons, and fonts][28]

### Step 8: Install other nerd fonts

Install Nerd fonts like:

  * Firacode Mono Nerd Font and Caskaydia Nerd font: [Download from Nerd Fonts website][29].
  * [Font awesome free desktop fonts][30]
  * [JetBrains Mono][31]



If you are in Arch Linux, open a terminal and run the command:

```

    sudo pacman -S ttf-firacode-nerd ttf-cascadia-code-nerd ttf-cascadia-mono-nerd woff2-font-awesome ttf-jetbrains-mono

```

### Step 9: Verify Waybar and Hyprland config

Open the `config.jsonc` file on the downloaded directory and replace any occurrence of `Virtual-1` with your monitor name.

For GNOME Box VM, it is **Virtual-1**. On my main system, I have two monitors connected. So, the names for my monitors are HDMI-A-1 and HDMI-A-2. Note the name of the monitors as we saw in Step 4:

```

    hyprctl monitors

```

Now in the Waybar config, change the monitor name from **Virtual-1** to the name of your monitor. Change all such occurrences.

📋

You can use any editor's find and replace feature. Find complete word `Virtual-1` and replace it with your monitor name. If you are using nano, follow this [guide to learn search and replace in nano editor][32].

Also, **take a look at the panel item**. If you see any item that is not needed in the panel, you can remove it from the `[modules-<position>]` part.

👉 Similarly, open the hyprland config in the downloaded directory. Change all reference to `Virtual-1` to your monitor name. Similarly, replace monitor name in the **hyprlock** and **hyprpaper** config files.

### Step 10: Copy and paste config files

Copy the following directories (in the downloaded GitHub files) and paste it to the `~/.config` folder.

  * `waybar`: Waybar panel configs and styles.
  * `wofi`: Application launcher config
  * `dunst`: Customized dunst notification system.
  * `starship.toml`: Customized starship prompt.



If you are using a GUI file manager, copy all file/folders except `hypr`, `wallpaper`, and `README`.

![Copy except hypr and wallpaper][33]

### Step 11: Replace Hyprland config

We did not copy `hypr` folder, because there is already a folder called `hypr` in every Hyprland system, which contains the minimal config.

I don't want to make it vanish. Instead, keep it as a backup.

```

    cp ~/.config/hypr/hyprland.conf ~/.config/hypr/hyprland.conf.bak

```

Now, exchange the content of the `hyprland.conf` in your system with the customized content. Luckily, the `mv` command has a convenient option called `-exchange`.

```

    mv --exchange ~/.config/hypr/hyprland.conf /path/to/new/hyprland/config

```

🚧

What the above command does is swap the contents of your default hyprland config with the one we created.

![Backup and replace Hyprland config][34]

### Step 12: Paste hyprlock and hyprpaper configs

Now, copy the `hyprlock.conf` and `hyprpaper.conf` file to `~/.config/hypr` directory.

![Copy hyprlock and hyprpaper config files][35]

### Step 13: Change themes

Open the NWG-Look app and set the GTK theme and font (Creepster font) for GTK apps:

![Set GTK Theme and font][36]

Now, change icon theme:

![Set icon theme for GTK apps][37]

This app automatically adds necessary file links in the `~/.config/gtk-4.0`. Thanks to this feature, you don't need to apply theme manually to the GTK4 apps.

Open the Qt5ct app and change the theme to darker.

![Apply Qt Darker theme][38]

Now, apply icon theme:

![Qt icon theme][39]

And change the normal font to "Creepster":

![Qt font style][40]

### Step 14: Set Starship and aliases

First, paste some cool command aliases for the normal `ls` and `cat` command, using the modern alternatives `eza` and `bat` respectively. **This is optional, of course**.

Open `~/.bashrc` in any editor and paste these lines at the bottom of this file:

```

    alias ls='eza -lG --color always --icons'
    alias la='eza -alG --color always --icons'
    alias cat='bat --color always --theme="Dracula"'

```

Now, to enable [Starship prompt][12], paste the starship `eval` line to the `~/.bashrc` and source the config.

![Edit bashrc][41]

```

    eval "$(starship init bash)"

    source ~/.bashrc

```

![Customized starship prompt][42]

Once all this is done, restart the system, and log back in to see the Halloween themed Hyprland.

Hyprland Halloween Makeover

Enjoy the spooky Hyprland set up. Happy Halloween 🎃

--------------------------------------------------------------------------------

via: https://itsfoss.com/hyprland-halloween-customization/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/itsfoss/text-script-files/tree/master/config/halloween-hyprland
[4]: https://itsfoss.com/hyprland/
[5]: https://itsfoss.com/install-arch-linux-virtualbox/
[6]: https://www.youtube.com/watch?v=TOTZedtb_d8
[7]: https://www.youtube.com/@itsfoss
[8]: https://itsfoss.com/hyprpaper-hyprland/
[9]: https://itsfoss.com/configure-waybar/
[10]: https://itsfoss.com/fine-control-fastfetch/
[11]: https://itsfoss.com/legacy-linux-commands-alternatives/
[12]: https://itsfoss.com/starship/
[13]: https://itsfoss.com/display-manager/
[14]: https://itsfoss.com/content/images/2025/10/enable-sddm.png
[15]: https://itsfoss.com/content/images/2025/10/login-to-hyprland.png
[16]: https://itsfoss.com/configuring-hyprland/
[17]: https://itsfoss.com/content/images/2025/10/monitor-settings-initial.png
[18]: https://itsfoss.com/content/images/2025/10/hyprctl-monitors.png
[19]: https://itsfoss.com/content/images/2025/10/download-the-zip-files.png
[20]: https://github.com/itsfoss/text-script-files
[21]: https://itsfoss.com/install-git-ubuntu/
[22]: https://itsfoss.com/content/images/2025/10/copy-wallpapers-to-folder.png
[23]: https://itsfoss.com/content/images/2025/10/download-gtk-theme.png
[24]: https://www.gnome-look.org/p/1695467
[25]: https://itsfoss.com/content/images/2025/10/download-icon-theme.png
[26]: https://www.gnome-look.org/p/1273980
[27]: https://fonts.google.com/specimen/Creepster?query=creepster
[28]: https://itsfoss.com/content/images/2025/10/paste-theme-icon-and-fonts.png
[29]: https://www.nerdfonts.com/font-downloads
[30]: https://fontawesome.com/download
[31]: https://fonts.google.com/specimen/JetBrains+Mono
[32]: https://itsfoss.com/nano-search-replace/
[33]: https://itsfoss.com/content/images/2025/10/copy-config-to-location.png
[34]: https://itsfoss.com/content/images/2025/10/backup-hypr-config-and-replace.png
[35]: https://itsfoss.com/content/images/2025/10/copy-hyprlock-and-hyprpaper.png
[36]: https://itsfoss.com/content/images/2025/10/set-theme-and-font.png
[37]: https://itsfoss.com/content/images/2025/10/set-icon-theme.png
[38]: https://itsfoss.com/content/images/2025/10/apply-qt-darker-theme.webp
[39]: https://itsfoss.com/content/images/2025/10/apply-qt-icon-theme.png
[40]: https://itsfoss.com/content/images/2025/10/apply-qt-font-creepster.png
[41]: https://itsfoss.com/content/images/2025/10/edit-bashrc-and-add-lines.webp
[42]: https://itsfoss.com/content/images/2025/10/starship-prompt.png
