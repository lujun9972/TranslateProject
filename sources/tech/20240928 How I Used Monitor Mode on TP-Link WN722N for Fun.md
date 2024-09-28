[#]: subject: "How I Used Monitor Mode on TP-Link WN722N for Fun"
[#]: via: "https://itsfoss.com/monitor-mode-fun/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I Used Monitor Mode on TP-Link WN722N for Fun
======

[![Warp Terminal][1]][2]

As a kid, I used to be amazed by those movie scenes where someone would tap a few keys on their computer and say, "I'm in!".

That fascination is what got me into wireless network security, back when WPA2 was the standard, and things were much easier to bypass.

I remember looking up Wi-Fi adapters, and the [Alfa models][3] were way out of my budget, especially as a student.

After some research, I went for the [TP-Link WN722N][4] V1, hoping for the Atheros chipset, only to end up with the V2/V3 version using the Realtek RTL8188EUS chipset.

The good news? **You can still enable** [**monitor mode**][5] **on it!**

📋

Monitor mode allows the device to monitor all traffic received on a wireless channel. You don't need to be connected to the access point. This can be used to get data from unsecured channels (that's why we should use https) and attempt to crack router password (I'll demo it later).

In this guide, I'll show you how to get the right driver and start monitoring wireless networks ;)

### Driver Installation

🚧

I used Raspberry Pi in this setup. And I did all this for fun to experiment with monitor mode and wifi signals. Don't try it on your main Linux system as it involves driver changes and manual installations. If things don't go your way, you may end up with broken system. And certainly don't try it for illegally snooping on your neighbor's WiFi.

To enable monitor mode, the correct drivers are needed. And the installation needs an updated system.

```

    sudo apt update && sudo apt upgrade -y

```

Next, I installed the [build essential tools][6] for building and compiling the driver from source:

```

    sudo apt install dkms build-essential linux-headers-$(uname -r) git bc

```

Here's the breakdown of the command:

  * `dkms`: Manages kernel modules.
  * `build-essential`: Includes compilation tools like `gcc` and `make`.
  * `linux-headers-$(uname -r)`: Installs the headers matching your current kernel version.
  * `git`: Used to clone repositories, essential for downloading the driver source code.
  * `bc`: A calculator language, sometimes required during driver compilation for mathematical operations.



![][7]

Now comes the important part and it is to download the 'Realtek RTL8188EUS' driver. Thankfully, Kali Linux's official repository has it:

```

    git clone https://gitlab.com/kalilinux/packages/realtek-rtl8188eus-dkms.git

```

![][8]

Once the repository is cloned, the next step is to [compile the driver from source][9].

Navigate into the cloned directory and run the following command to build the driver:

```

    cd realtek-rtl8188eus-dkms
    make && sudo make install

```

![][10]

The build process will take a few seconds depending on your CPU.

### Disabling Conflicting Drivers

Now that the driver is installed, I blocked any previously running drivers that might have interfered.

```

    echo 'blacklist r8188eu' | sudo tee -a '/etc/modprobe.d/realtek.conf'

```

  * `echo 'blacklist r8188eu'`: Creates a line of text to block the `r8188eu` driver.
  * `| sudo tee -a '/etc/modprobe.d/realtek.conf'`: Appends that text to the file `/etc/modprobe.d/realtek.conf` with superuser privileges, ensuring the driver is blacklisted.



![][11]

A **reboot** is required to apply the changes. After [restarting the Linux system][12], the new adapter should come online and be ready for use.

### Enabling Monitor Mode

At this stage, the adapter is still in **managed mode** (the default for typical Wi-Fi use).

```

    sudo iwconfig

```

![][13]

I will use [**aircrack-ng**][14] tool to enable monitor mode. It allows capturing packets from nearby networks.

Run the following command to kill any processes that might interfere:

```

    sudo airmon-ng check kill

```

Bring the interface down:

`sudo ip link set <interface> down`

Set the adapter to monitor mode:

```

    sudo iw dev <interface> set type monitor

```

Bring the interface back up:

```

    sudo ip link set <interface> up

```

![][15]

Now it is in 'monitor' mode:

![][16]

Great! The adapter is now in **monitor mode**!

But what's the fun in stopping here? Let’s test it on a live network and really see what it can do!

### Using monitor mode for to recover forgotten WiFi password

Let me share a good usecase of this monitor mode where I recovered the forgotten WiFi password.

So, here's my setup: I’m using a Raspberry Pi 3B+ and accessing it via SSH.

![][17]

And the target - my classic old DSL router (not connected to the Internet):

![][18]

Now, in a stroke of **sheer bad luck** , I’ve forgotten the Wi-Fi password, which we’ll try to recover today using [wifite2][19], one of the popular [Kali Linux tools][20].

It's a tool that automates the process of capturing WPA/WPA2 handshakes and cracking password keys.

I prefer wifite2 over aircrack-ng because of its user-friendly interface and automated features, which simplify the process significantly.

#### Quest: Finding Lost Password

I’m not covering the installation process for wifite2 here.

🚧

****Warning:**** This content is for educational purposes only. Unauthorized use of these techniques may violate laws and ethical guidelines. Please respect the privacy and security of others and follow the cyber security law of your country.

To use wifite2, run the following command:

```

    sudo wifite --kill --random-mac --dict ~/wifite2/wordlist-top4800-probable.txt

```

  * **`--kill`** : Stops interfering processes (like network managers) to ensure smooth operation.
  * **`--random-mac`** : Randomizes your MAC address for anonymity.
  * **`--dict /wifite2/wordlist-top4800-probable.txt`** : Specifies a custom wordlist for password cracking.



![][21]

You can see our VICTIM router here.

Once you’ve entered the target, wifite2 will automatically start performing a series of attacks.

Since I only have one attack installed (WPA handshake capture), wifite2 will handle everything from here.

![][22]

The image above might look a little confusing; let me explain what's happening up there:

  1. **Send Deauth Signals** : Wifite2 disconnects clients from the network to force a reconnect.
  2. **Capture Handshake** : It tries to captures the WPA handshake, which is a verification process between the router and client.
  3. **Handshake Captured** : Confirmation that the handshake data has been successfully collected.
  4. **Save Handshake** : The handshake is saved in a file named something like `handshake_DLinkVICTIM_00-00-00-00-2024.cap`.
  5. **Crack Password** : Wifite2 uses the wordlist you provided to crack the password.
  6. **Password Revealed** : The cracked Wi-Fi password **admin123**.



📋

Since this was for a demo purpose, I used word list feature and had a simple password on the router. Unsurprisingly, in a real world scenario, that is likely not to be the case.

### Conclusion

So, I shared how I enabled monitor mode on a budget TP-Link adapter and a thing or two about wireless networks and their vulnerabilities.

Remember, while this knowledge is powerful, it's crucial to use it responsibly. Always respect the privacy of others and only test networks that you have explicit permission to access.

These little experiments are a fun way to improve your knowledge. At least, that's what I think. What do you say?

--------------------------------------------------------------------------------

via: https://itsfoss.com/monitor-mode-fun/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.alfa.com.tw/collections/kali-linux-compatible
[4]: https://www.tp-link.com/in/home-networking/adapter/tl-wn722n/v3/
[5]: https://en.wikipedia.org/wiki/Monitor_mode
[6]: https://itsfoss.com/build-essential-ubuntu/
[7]: https://itsfoss.com/content/images/2024/09/tplink-prerequisites-1.png
[8]: https://itsfoss.com/content/images/2024/09/tplink-git-repo-1.png
[9]: https://itsfoss.com/install-software-from-source-code/
[10]: https://itsfoss.com/content/images/2024/09/building-driver-pi3bplus.png
[11]: https://itsfoss.com/content/images/2024/09/tplink-blacklist-driver.png
[12]: https://itsfoss.com/schedule-shutdown-ubuntu/
[13]: https://itsfoss.com/content/images/2024/09/tplink-iwconfig.png
[14]: https://www.aircrack-ng.org/
[15]: https://itsfoss.com/content/images/2024/09/tplink-aircrack.png
[16]: https://itsfoss.com/content/images/2024/09/tplink-monitor-mode.png
[17]: https://itsfoss.com/content/images/2024/09/pi3b-plus.jpeg
[18]: https://itsfoss.com/content/images/2024/09/dlink-router.jpeg
[19]: https://github.com/derv82/wifite2
[20]: https://itsfoss.com/best-kali-linux-tools/
[21]: https://itsfoss.com/content/images/2024/09/tplink-wifite2-first-look.png
[22]: https://itsfoss.com/content/images/2024/09/tplink-wifite2-cracked-password-2.png
