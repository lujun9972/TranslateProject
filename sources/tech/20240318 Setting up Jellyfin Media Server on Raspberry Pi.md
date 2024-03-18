[#]: subject: "Setting up Jellyfin Media Server on Raspberry Pi"
[#]: via: "https://itsfoss.com/jellyfin-raspberry-pi/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Setting up Jellyfin Media Server on Raspberry Pi
======

[![Warp Terminal][1]][2]

Got a large digital media library thanks to your old DVD and Blue Ray collection? A media server will enhance your movie watching experience.

sFirst, your media library gets displayed like Netflix and other streaming services. You get to resume your playback or add titles to your watchlist.

![Streaming services like interface in Jellyfin][3]

Other than that, you also get a dedicated page for each title that shows movie synopsis, cast, ratings and more.

![Display movie information][4]

That's not it. You can also 'stream' the movies and TV shows to your TV or other computers easily if they are connected to the same network.

There are [several media servers available for Linux][5], but [Jellyfin][6] is my favorite open source tool for self-hosting media. Apart from being the media server, it also has the functionality of DVR and live TV ( _may require some additional configuration_ ).

Hosting a media server is also one of the [easiest projects you can build with Raspberry Pi][7].

In this tutorial, I'll show you how I set up Jellyfin media server on my Raspberry Pi to stream content to other devices connected to my home network. You should be able to achieve the same following the steps mentioned here.

### Requirements

I am using a Raspberry Pi 4 for this project. It has 4 GB of RAM but you can use any Raspberry Pi model, although the performance might vary.

During my testing, there was not much difference between Pi 3 and 4 performance while playing a file locally on the network without any hardware transcoding. However, if you do want to transcode, then I think a Pi 4 will be a good fit for this.

  * Raspberry Pi with Raspbian OS (or other Debian/Ubuntu based distro)
  * Ethernet cable (optional but provides faster speed)
  * Keyboard & mouse (it's optional as you can [SSH into your Raspberry Pi][8] and set up from your regular computer)
  * External HDD/SSD (this is where you'll have your media files stored)



### Installing Jellyfin on Raspbian OS

📋

You should already have a [Raspberry Pi running Raspbian OS][9]. This tutorial is about setting up Jellyfin, not Raspberry Pi.

Before you begin adding the Jellyfin repository, make sure your Raspbian OS is updated

```

    sudo apt update && sudo apt full-upgrade -y

```

First you need to install a package called `apt-transport-https` as the apt package manager does not come default with the support of repositories running behind HTTPS.

```

    sudo apt install apt-transport-https lsb-release

```

Next, you need to import the **GPG signing key** of the repo:

```

    curl https://repo.jellyfin.org/debian/jellyfin_team.gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/jellyfin-archive-keyring.gpg >/dev/null

```

Now you can add the Jellyfin repository to your system using this command:

```

    echo "deb [signed-by=/usr/share/keyrings/jellyfin-archive-keyring.gpg arch=$( dpkg --print-architecture )] https://repo.jellyfin.org/debian $( lsb_release -c -s ) main" | sudo tee /etc/apt/sources.list.d/jellyfin.list

```

Since a new repository has been added, you need to run the update command once more to ensure that your system knows about the packages available from this new repo:

```

    sudo apt update

```

Now it is the time to install Jellyfin.

```

    sudo apt install jellyfin

```

It will take some time to finish installation as Jellyfin will set up a few things in the background, such as a new user called `jellyfin` and this user can execute and need access to read your files.

If everything was set up correctly, you will see something like this:

![][10]

Nice. Let's set up Jellyfin and make it streaming ready.

### Setting up Jellyfin media server

Once Jellyfin has been installed, it will run automatically and to interact with it, you need to access its web UI.

#### Step 1: Access Jellyfin via web interface

If you are using it locally on the Raspberry Pi itself, then you can simply type `localhost:8096` and it will work.

But the whole purpose of setting up a server is to access it from other devices. For that, you need to know the IP address of your Pi.

The easiest way to [know the IP Address][11] of your Pi is to just type `hostname -I` in the terminal and once you know the IP, just type it in the browser:

```

    http://[YOUR IP ADDRESS]:8096

```

![Access Jellyfin server in web browser][12]

#### Step 2: Start Jellyfin configuration

You must set up Jellyfin before you start using it. When you first access Jellyfin, it will ask you to configure it.

![][13]

#### Step 3: Create user account

Then you have to set up user and password to protect your server from unauthorized access.

![][14]

#### Step 4: Add your media library

Next, tt will ask you to select the media library i.e. the folder where you have stored your movies, shows and media files. You can mount your external drive as well. I suggest enabling auto-mount for external USB.

![][15]

As you can see in the above screenshot, you have to first select the "Content type" which could be "Movies, TV Shows, Videos" etc.

Then you need to add folders where your media files are located, to do that just press the `+` icon. (my media is located in `/mnt/usb/movies` folder). There are other settings that you can fiddle with below but I prefer to let them as default.

When you are done with it just press `Next`.

![][16]

#### Step 5: Set up metadata language

On the next page, Jellyfin will prompt you again to select your preferred language for the metadata, as it maintains the metadata of the media you own locally. Press `Next` when done.

![][17]

#### Step 6: Allow remote connection for streaming to other devices

This step is is important as here you have to select whether you want to `Allow remote connections to this server` i.e. accessing jellyfin from other devices and `Enable automatic port mapping`.

It already comes selected by default in my case and then press `Next`.

![][18]

🚧

I DID NOT opt for port mapping that allows accessing the Pi from outside your local network. If not setup securely, port forwarding can be a security risk for all your devices connected to the network.

#### Step 7: Verify your Jellyfin set up

You are done setting up our Jellyfin and now just press `Finish` on the next page.

![][19]

On the home screen, you are welcomed with all the movie/ TV collections you have added.You can play them either from the browser or from the official app Jellyfin app for your smart TV (needs to download app and use the same URL and port you used to access it via wbe browser).

![][20]

Although this should be enough for you to enjoy movies and TV series but I think you can still improve a lot here by enabling hardware acceleration.

### Optional: Using hardware acceleration for streaming on Jellyfin

If you want to stream your content on multiple devices, you don't always have to [stress out your CPU][21], which might throttle if not cooled properly. It would be a good idea to let Jellyfin uses Pi's in-built GPU.

#### Step 1: Set up Raspberry Pi for hardware acceleration

On your Raspberry Pi, first add Jellyfin to `video` user group.

```

    sudo usermod -aG video jellyfin

```

Then you need to increase our Video memory as transcoding can be a pretty hefty task. You have to edit a `config.txt` file:

```

    sudo nano /boot/config.txt

```

Go to the end of the file and add the following code:

💡

If you are using Pi 4 then 320 MB is good enough but if you are using a Pi 3 then set the video memory to 256MB.

```

    gpu_mem=320

```

![][22]

In the above picture, I am increasing Pi's default GPU memory, which is generally set around 76 MB to 320 MB

[Save and exit Nano editor][23] by using `CTRL+X` then pressing `Y`.

You also need to restart the Pi for the changes to take effect:

```

    sudo reboot now

```

To verify the changes to the allocated GPU memory, run:

```

    vcgencmd get_mem gpu

```

and the output should look like this:

![][24]

#### Step 2: Enabling hardware acceleration in Jellyfin

You have to go back to our Jellyfin's web interface and on the home page, at the top right click the User icon and it will take us to the user settings page.

![][25]

Here, click on the `Dashboard` option:

![][26]

Within the dashboard settings pane, on the left side, click on the `Playback` option.

![][27]

In the playback tab, you can find all the settings related to how media files are played on Raspberry Pi.

Under the **Transcoding** section, you should see a select box with the heading of **Hardware Acceleration**. Here you have to set the value to `Video4Linux2 (V4L2)`.

V4L2 is the only supported option for the Raspberry Pi hardware. Once done, just scroll to the bottom and hit **Save**.

![][28]

### Enjoy local media streaming

To sum it up, turning your Raspberry Pi into a media wizard with Jellyfin isn't just a tech upgrade – it's like giving your little single board computer a superhero cape!

Picture this: smoother streaming, snappy performance, and all the fun of hardware transcoding. It's not just a setup; it's a playful adventure into making your Raspberry Pi the coolest entertainment sidekick ever.

Get ready for a joyride into the world of media magic on your pint-sized powerhouse!

--------------------------------------------------------------------------------

via: https://itsfoss.com/jellyfin-raspberry-pi/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/03/jellyfin-interface.webp
[4]: https://itsfoss.com/content/images/2024/03/jellyfin-movie-page.webp
[5]: https://itsfoss.com/best-linux-media-server/
[6]: https://jellyfin.org/
[7]: https://itsfoss.com/raspberry-pi-projects/
[8]: https://itsfoss.com/ssh-into-raspberry/
[9]: https://itsfoss.com/tutorial-how-to-install-raspberry-pi-os-raspbian-wheezy/
[10]: https://itsfoss.com/content/images/2024/01/apt-install-jellyfin.png
[11]: https://itsfoss.com/check-ip-address-ubuntu/
[12]: https://itsfoss.com/content/images/2024/01/browser-ip-login-jellyfin-raspberrypi.png
[13]: https://itsfoss.com/content/images/2024/01/welcome-to-jellyfin-raspberrypi.png
[14]: https://itsfoss.com/content/images/2024/01/first-user-creation-jellyfin-raspberrypi.png
[15]: https://itsfoss.com/content/images/2024/01/selecting-content-type-in-jellyfin-raspberrypi.png
[16]: https://itsfoss.com/content/images/2024/01/selecting-folder-where-media-is-stored-jellyfin-raspberrypi.png
[17]: https://itsfoss.com/content/images/2024/01/selecting-metadata-language-in-setup-jellyfin-raspberrypi.png
[18]: https://itsfoss.com/content/images/2024/01/remote-access-permission-jellyfin-raspberrypi.png
[19]: https://itsfoss.com/content/images/2024/01/finish-setup-jellyfin-raspberrypi.png
[20]: https://itsfoss.com/content/images/2024/01/homepage-after-setup-jellyfin-raspberrypi.png
[21]: https://itsfoss.com/stress-test-cpu-linux/
[22]: https://itsfoss.com/content/images/2024/01/nano-config-for-vram-jellyfin-raspberrypi.png
[23]: https://itsfoss.com/nano-save-exit/
[24]: https://itsfoss.com/content/images/2024/01/running-command-to-check-vram-after-reboot-jellyfin-raspberrypi.png
[25]: https://itsfoss.com/content/images/2024/01/homepage-user-settings-icon-jellyfin-raspberrypi.png
[26]: https://itsfoss.com/content/images/2024/01/dashboard-settings-jellyfin-raspberrypi.png
[27]: https://itsfoss.com/content/images/2024/01/playback-settings-for-hw-acceleration-jellyfin-raspberrypi.png
[28]: https://itsfoss.com/content/images/2024/01/saving-hw-playback-profile-jellyfin-raspberrypi.png
