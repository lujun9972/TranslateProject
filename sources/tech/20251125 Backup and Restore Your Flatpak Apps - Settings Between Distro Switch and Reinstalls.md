[#]: subject: "Backup and Restore Your Flatpak Apps & Settings Between Distro Switch and Reinstalls"
[#]: via: "https://itsfoss.com/back-up-restore-flatpak-apps/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Backup and Restore Your Flatpak Apps & Settings Between Distro Switch and Reinstalls
======

[![Warp Terminal][1]][2]

[Flatpak][3] has pretty much become the de-facto standard for universal packages on the Linux desktop, with an increasing number of distros supporting the format in their default installs. Yet, even with how easy it is to install and update Linux apps with Flatpak, moving them to a new system can be tricky, especially if you’ve installed dozens over time.

Sure, you _could_ list and reinstall everything manually, but that’s tedious work, and easily prone to human error. Fortunately, there’s a simple way to export your Flatpak apps, remotes, and even overrides so you can recreate your setup on another machine with just a few commands.

You can even backup and restore your settings on another system.

### 1\. Exporting your Flatpak apps

On the system where you've got all your apps, you'll first want to save a list of your installed apps as [Flatpak "refs"][4], including where each one is installed. [Flatpaks][5] can be installed either system-wide (and thus available to all users) or per-user. The process is different depending on whether you're running a single-user set up, or if you have to back up and restore for multiple users.

#### For single-user systems

_**This assumes you have no other users on your system**._ Backup both user and system apps you have access to.

```

    flatpak list --app --columns=installation,ref > flatpak-apps.txt

```

#### For a multi-user setup

First, you'll need to copy any system-level installations:

```

    # Backup only system-installed apps
    flatpak list --system --app --columns=ref > flatpak-apps-system.txt

```

❗

This will __not__ copy any user-installed Flatpaks.

Next, copy any user-installed Flatpaks. You'll need to do this for every user individually. Have each user run this to backup their personal installations.

```

    flatpak list --user --app --columns=ref > flatpak-apps-user-$USER.txt

```

Then, back up your Flatpak remotes (the repositories your apps came from):

```

    flatpak remotes --columns=name,url > flatpak-remotes.txt

```

Each Flatpak app has a unique “ref” (short for "reference") that identifies its source, branch, and architecture. Saving these ensures you reinstall the _exact_ same apps later.

#### Exporting your overrides (optional)

Overrides are the individual settings that you can modify for each Flatpak with an app like Flatseal. By exporting all overrides together at once, you can preserve your settings across installs.

To do this, you can run the following command:

```

    # Export Flatpak overrides to a file
    flatpak override --show > flatpak-overrides.txt

```

You can later restore these overrides on your target system.

#### Exporting your app data

Flatpak app data, like configuration files and saved sessions, is stored in `~/.var/app/`. You can copy this folder to your target system any time you want to transfer your app settings. For individual apps, you can copy their individual folders.

For example, for GIMP, you can copy `~/.var/app/org.gimp.GIMP`.

### 2\. Preparing the target system (optional)

ℹ️

I assume that you're transferring your apps to another system. If that's not the case, you can skip this step.

It goes without saying, but if you're going to transfer your Flatpak apps to another system, you should ensure that the target system has Flatpak support. To check this, you can run:

```

    # Check if Flatpak is installed
    flatpak --version

```

![Checking that Flatpak is installed and working][6]

If you got a version number, you’re good to go. Most popular distros, including Fedora, Mint, and Pop!_OS, have Flatpak preinstalled.

If you're planning on migrating to a fresh installation of Ubuntu, you'll need to install Flatpak first:

```

    # Install Flatpak
    sudp apt -y install flatpak

```

### 3\. Recreating your setup on the new system

On your new Linux install, the first step is to re-add your Flatpak remotes:

```

    # Add saved Flatpak remotes
    while read -r name url; do
      flatpak remote-add --if-not-exists "$name" "$url"
    done < flatpak-remotes.txt

```

Remember to run this command in the same directory where you have your flatpak-remotes.txt saved.

#### Reinstalling your apps

Once you've added your Flatpak remotes, you can now reinstall all your apps to their original locations:

```

    # Restore Flatpaks:
    while read -r inst ref; do
      if [ "$inst" = "user" ]; then
        flatpak install -y --user "$ref"
      else
        flatpak install -y --system "$ref"
      fi
    done < flatpak-apps.txt

```

Once this process completes, you can confirm that everything worked by running:

```

    flatpak list --app

```

You can compare this output with your original `flatpak-apps.txt` file to verify all your apps are back.

#### Restoring overrides (optional)

If you've saved your Flatpak overrides, you can restore them by running:

```

    # Restore your Flatpak Overrides
    while read -r line; do
      # Skip empty lines and comments
      [[ -z "$line" || "$line" =~ ^# ]] && continue

      flatpak override $line
    done < flatpak-overrides.txt

```

### Optional bonus for advanced users: Automating your setup

If you frequently install or test new Flatpak apps, you can automate this process so your backups stay up to date, and you can quickly move your apps to a new system at any time.

Create a simple script (e.g., `~/bin/flatpak-backup.sh`):

```

    #!/bin/bash
    flatpak list --app --columns=installation,ref > ~/flatpak-apps.txt
    flatpak remotes --columns=name,url > ~/flatpak-remotes.txt
    flatpak override --show > ~/flatpak-overrides.txt
    echo "Flatpak backup completed on $(date)" >> ~/flatpak-backup.log

```

Then, make the shell script executable:

```

    chmod +x ~/bin/flatpak-backup.sh

```

Then schedule it to run weekly with `cron`:

```

    crontab -e

```

Add this line (runs every Sunday at 10 AM):

```

    0 10 * * SUN ~/bin/flatpak-backup.sh

```

This way, your Flatpak list and overrides stay current without any manual work.

### **Wrapping up**

You now know how to quickly back up and migrate your Flatpak apps between systems in a clean, scriptable. It’s lightweight, doesn’t require extra tools, and makes distro hopping or system rebuilds much easier.

If you'd like to take this to the next level, here's another quick tip: you can keep your Flatpak backup files in a version control system like git or a personal storage solution like Nextcloud. This way, if disaster strikes, you’ll be able to rebuild your app environment in minutes.

You can also [backup and restore Snap packages][7] in similar function.

![][8]

I hope you find it useful 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/back-up-restore-flatpak-apps/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/what-is-flatpak/
[4]: https://itsfoss.com/no-remote-ref-found-flatpak/
[5]: https://flatpak.org/
[6]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-09-22-47-28--Edit-.png
[7]: https://itsfoss.com/snap-app-back-up-restore/
[8]: https://itsfoss.com/content/images/icon/android-chrome-512x512-44.png
