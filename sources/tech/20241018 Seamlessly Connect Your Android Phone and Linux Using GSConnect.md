[#]: subject: "Seamlessly Connect Your Android Phone and Linux Using GSConnect"
[#]: via: "https://itsfoss.com/gsconnect/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Seamlessly Connect Your Android Phone and Linux Using GSConnect
======

[![Warp Terminal][1]][2]

Smartphones are an inseparable part of our technical life these days. The thing is that you'll spend part of your time on the smartphone and part of it on the computer.

And that also creates some inconvenience. When you keep on switching between the two devices, you'll feel the need to connect the two.

Transfer files between the devices, share clipboards, see some phone notifications on the phone etc.

Apple has an excellent ecosystem that connects an iPhone with Mac. Windows also provides features to connect your Android smartphone with the PC.

For Linux, KDE has developed a solution called [KDE Connect][3]. It works better in the KDE environment and hence we have the GSConnect extension for GNOME desktop users.

GSConnect is an implementation of KDE Connect itself. While KDE Connect may already work on GNOME, GSConnect gives a better experience for GNOME users in my opinion.

✋

Please [check which desktop environment you are using][4] and ensure that it is GNOME. It would be better if you are familiar with the [concept of GNOME Extensions][5].

### Setting Up GSConnect on your Linux system

🚧

Even though GSConnect is based on KDE Connect, you MUST NOT have KDE Connect installed on your laptop/desktop system, if you want to use GSConnect. If it is installed already, remove it please.

As said earlier, [GSConnect][6] is a GNOME extension. So, you need to install this extension first.

#### Install GSConnect extension

To install, either use the [GNOME Shell Extension Manager app][7] or [use the extensions' website][5].

[GSConnect Extension][8]

![GSConnect in Extension Manager][9]

Once you install the extension, you can see the extension active in the System tray quick buttons.

![GSConnect Extension in system tray][10]

💡

If you want to use the GSConnect inside a guest in VirtualBox, change the guest network settings from NAT to Bridged Adapter.

#### Allow KDE Connect over the firewall

🚧

Never turn off or disable firewall, if the service you need can be run with Firewall enabled. Just configure the firewall accordingly so that the program works.

Many distributions come with a firewall setup. But KDE Connect, on which GSConnect is based, needs to communicate with the other system over the firewall. This is because there are many features like remote input, notification sharing, etc., that need incoming and outgoing communication. The default policy for the Firewall in most system is to block incoming communications entirely.

So, you need to allow KDE Connect to communicate over Firewall.

The KDE Connect protocol uses ports 1714-1764 for UDP and TCP. We need to open these ports. The steps for UFW and Firewalld are mentioned here, since these are the most popular Firewall solution on desktop Linux systems.

✋

Check if you have a firewall set up and which one it is. Use the appropriate commands to enable the required port.

##### Open necessary ports in UFW (Ubuntu)

On Ubuntu, the default Firewall provider is UFW. So, open a terminal and run the command below:

```

    sudo ufw allow 1714:1764/udp
    sudo ufw allow 1714:1764/tcp
    sudo ufw reload

```

![UFW Firewall Settings][11]

##### Open necessary ports in Firewalld (Fedora)

Fedora comes with Firewalld as the Firewall provider. In this case, use the command:

```

    sudo firewall-cmd --permanent --zone=public --add-service=kdeconnect
    sudo firewall-cmd --reload

```

That's it. You have configured the firewall settings needed for GSConnect.

#### Install KDE Connect on Android smartphone

Once you have Linux system ready, install KDE Connect on your Android phone. This app is available on Google Play.

[KDE Connect in Google Play][12]

After installation, open KDE Connect on your phone.

📋

If you didn't set up the firewall properly in the previous step, the devices won't be detected.

#### Identify the device name

If you are not sure about the name of the mobile device, you can click on the top-left hamburger menu and select settings.

![Get Mobile Device Name][13]

Here, you can see the name of your device under “Device name” field.

📋

For Linux, the name of the device will be shown in the title of GSConnect window.

#### Pair the devices

Once you set up GSConnect on Linux and KDE Connect on Android, let's connect them.

Click on the system tray button on your GNOME panel. From the dropdown menu adjacent to GSConnect, select the **Mobile Settings** option as shown in the screenshot below.

![Click on Mobile Settings][14]

In the GSConnect settings window, you can see that the mobile is detected. Click on it.

![Mobile device detected][15]

Alternatively, you can see the Linux system detected in the KDE Connect mobile app. Click on the computer name to start connecting to it.

Here, I clicked the detected PC on mobile. Then click on “Request Pairing”. This will ask me to accept the pairing request on the GNOME desktop.

![Accept Pairing Request from Phone][16]

Click on Accept, and your devices will be paired.

🚧

You should verify the key displayed on both devices. If it does not match, do not connect. The phone will only show the first 8 characters of the verification key.

To start a pairing request from Linux, you can click on the detected mobile device in GSConnect desktop app and click on the Pair button.

![Click on Pair][17]

Now, you need to accept the request inside KDE Connect Mobile app to pair the devices.

🚧

You may not get a pairing request in Phone notifications. So, it is advised to open the KDE Connect app while sending request to accept it before timeout.

That's it. The devices are now connected.

Most of the settings are available from the system tray.

![Mobile Settings in Tray][18]

#### Permission settings

Now that the devices are connected, you can do basic things like Send files, remote input, send clipboard, etc.

You can see the what you can do by going to the **Advanced** tab in the GSConnect window.

![GSConnect Advanced Tab][19]

💡

In mobile, this advanced settings can be found at Top-right menu → Plugin Settings.

Here, you can enable and disable things.

On the phone, you can give more permissions like Notification Sync, Telephony Notification, contacts sync, etc. Do this from the KDE Connect home page and on your mobile device.

### Using GSConnect

Now, let's see some use cases of GSConnect.

#### Send files between devices

To send a file from PC to your mobile device, expand the GSConnect button in the system tray and select **Share**.

![Select Share from GSConnect Tray][20]

This will open the File Chooser from where you can select the files.

💡

On phone, select the ****Send Files**** option in the KDE Connect home page to select the files and send selected items.

#### Mount an Android folder

Sometimes, it would be better if you could mount a local Android folder in the system for better file transfer and sync.

To do that, first, give filesystem permission for the KDE Connect app on your phone.

Click on the Filesystem Expose button and then allow KDE Connect to access in system settings.

![Select Folder Location][21]

Depending on the Android version, you may need to give KDE Connect some permissions when asked. Just follow the onscreen instructions, and it will land you automatically on all needed settings pages.

📋

Newer Android versions won't allow you to share the home directory or some other directories like Downloads to be shared.

Once the location is selected in Android device, you can click on the Mount option in GSConnect System Tray button.

![Click on Mount][22]

When you go to the File Manager, you can see that the directory you selected has been mounted using the SFTP protocol.

![Android File system is mounted in GNOME][23]

#### Lock or shutdown the remote system

With the KDE Connect mobile app, you can lock the computer system or shutdown from the mobile. To do this, click on the **Run Command** option and then select the required action.

![Run Command][24]

🚧

Save all important works before shutting down or restarting the system.

#### Use phone as a mouse

You can use your phone display as a trackpad instead of mouse. This helps in a few cases. For example, you have connected the computer to TV to play a movie and then you can use the phone to play/pause the movie.

Use the **Remote Input** option in KDE Connect.

It supports all the useful functions and some are mentioned in the table below.

Function | Action
---|---
Move the mouse | Swipe across the screen with one finger
Scroll | Swipe with two fingers
Left-click | Either tap the screen or use the left-click button
Right-click | Either tap with two fingers or use the right-click button
Middle-click | Either tap with three fingers or use the middle-click button

Some other notable remote input functions are:

  * Use the keyboard button on the topbar to use mobile keyboard with the system.
  * Use the Compose Send button on the top bar to type a text and then send it to the system instead of live typing.
  * On the settings, you can enable the gyroscope mouse



### Conclusion

I would like to list a few more KDE Connect use cases that I didn't cover in detail:

  * Notification Sync to get phone notification in PC.
  * Telephony notification to get phone call notification in desktop.
  * Get phone battery charge details from system tray.



I let you explore it and enjoy a seamless connection between your Linux computer and Android smartphone.

I also invite you to share your views and experience in the comment system.

_With inputs from Abhishek Prakash._

--------------------------------------------------------------------------------

via: https://itsfoss.com/gsconnect/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://kdeconnect.kde.org/
[4]: https://itsfoss.com/find-desktop-environment/
[5]: https://itsfoss.com/gnome-shell-extensions/
[6]: https://github.com/GSConnect/gnome-shell-extension-gsconnect
[7]: https://itsfoss.com/extension-manager/
[8]: https://extensions.gnome.org/extension/1319/gsconnect/
[9]: https://itsfoss.com/content/images/2024/10/gsconnect-extension-in-extension-manager.png
[10]: https://itsfoss.com/content/images/2024/10/GSConnect-extension-active-GNOME-system-tray.png
[11]: https://itsfoss.com/content/images/2024/10/firewall-rules-settings.png
[12]: https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp
[13]: https://itsfoss.com/content/images/2024/10/get-mobile-device-name.png
[14]: https://itsfoss.com/content/images/2024/10/GSConnect-in-system-tray-click-on-mobile-settings.png
[15]: https://itsfoss.com/content/images/2024/10/mobile-device-detected-in-pc.png
[16]: https://itsfoss.com/content/images/2024/10/accept-pairing-request-from-phone.png
[17]: https://itsfoss.com/content/images/2024/10/click-on-pair-in-gsconnect-settings.png
[18]: https://itsfoss.com/content/images/2024/10/Mobile-settings-in-system-tray.png
[19]: https://itsfoss.com/content/images/2024/10/advanced-tab-in-gsconnect.png
[20]: https://itsfoss.com/content/images/2024/10/select-share-from-gsconnect-button.png
[21]: https://itsfoss.com/content/images/2024/10/allow-folder-location.png
[22]: https://itsfoss.com/content/images/2024/10/click-on-mount-to-mount-the-file-system.png
[23]: https://itsfoss.com/content/images/2024/10/file-system-mounted.png
[24]: https://itsfoss.com/content/images/2024/10/run-command-option-and-select-the-command.png
