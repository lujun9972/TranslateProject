[#]: subject: "Finding the Fastest Arch Linux Mirrors"
[#]: via: "https://itsfoss.com/fast-arch-linux-mirrors/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Finding the Fastest Arch Linux Mirrors
======

[![Warp Terminal][1]][2]

So, you [installed Arch Linux][3], but find downloading updates/packages a bit slow. Well, unless you have a network issue, it is an easy fix by selecting the fastest mirror.

Unlike Ubuntu, where you get a GUI utility to find and enable the fastest mirrors, things are a bit different in the Arch universe.

In this tutorial, I will walk you through multiple ways you can find the fastest mirrors in Arch Linux.

### Getting the fastest mirrors in Arch Linux

For those who do not know, the mirrors are copies of the official Arch Linux repositories hosted on a server closer to your location.

This way, you can download packages faster through a mirror closer to you.

The mirror list is stored inside the `/etc/pacman.d/mirrorlist` file (in case you're curious).

To ensure that you use the fastest mirrors, there are two ways to go about it:

  * **Using the rate-mirrors utility**
  * **Using the Reflector utility**



Before start changing the mirrors file, it is always good to save a backup of the current file. Thus, if anything unexpected happens, you can easily revert.

```

    cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak

```

So let's start with the first one.

#### Method 1: Using the rate-mirrors utility

The first step is to install the rate-mirrors utility which can be done using any AUR helper.

I am going with yay here:

```

    yay -S rate-mirrors-bin

```

This is the only command where you have to specify the name of your distro to proceed as it is crafted for each Arch-based distro separately.

For that, once installed, execute the `rate-mirrors` command, and it will show you the list of the distros under the `commands` section:

```

    rate-mirrors

```

![The rate-mirrors utility commands][4]

Find the name of your distro, and type in the same through the command in the following format:

```

    rate-mirrors <distro-name>

```

For example, here, I'm using Arch, I will be using the following:

```

    rate-mirrors arch

```

![Listing mirrors by the rate-mirrors utility][5]

If you notice the output carefully, it only prints the actual server list without comments, so you can redirect the entire output to the file without any errors.

By default, it will also include the `http` mirrors which you may not want due to security reasons.

You can filter the protocol and show the HTTPS servers only using the `--protocol` flag:

```

    rate-mirrors --protocol https <distro_name>

```

My command would look like this:

```

    rate-mirrors --protocol https arch

```

Finally, to add the mirrors to the `/etc/pacman.d/mirrorlist` file, you will have to use the `--allow-root` flag as you need superuser privileges to change the file.

Furthermore, you have to pipe it with the tee and [grep command][6].

The grep command will only add lines that do not start with the hashtag (to keep the file neat) and [the tee command][7] will send the output to the file:

```

    rate-mirrors --allow-root --protocol https <distro_name> | grep -v '^#' | sudo tee /etc/pacman.d/mirrorlist

```

Here's how it will look like:

```

    rate-mirrors --allow-root --protocol https arch | grep -v '^#' | sudo tee /etc/pacman.d/mirrorlist

```

Once done, use the cat command to print the contents of the `/etc/pacman.d/mirrorlist` to verify whether the fastest mirrors are added or not:

```

    cat /etc/pacman.d/mirrorlist

```

![Contents of mirrorlist file][8]

And, it is done! Now, moving on to the second method!

#### Method 2: Using reflector utility

The major benefit of using reflector over the rate-mirrors is the options you get to choose. So if you want more control over how you want to select mirrors, then you cannot go wrong with a reflector.

First, install `reflector` in Arch using the following command:

```

    sudo pacman -S reflector

```

Once done, there are two ways to get the fastest mirrors using the reflector: either specify the **geographical location** or **let the reflector decide for you**.

###### Adding mirrors based on geographical location

To specify the geographical location, use the `-c` flag, and you can do that multiple times if you want to add multiple nations:

```

    sudo reflector -c <country_name> -l <number of mirrors> -p <protocol> --save /etc/pacman.d/mirrorlist

```

Here,

  * `-c <country_name>`: specify the name of the country, closest to you.
  * `-l <number of mirrors>`: here you specify the number of the most recently synchronized mirrors.
  * `-p <protocol>`: specify the protocol you want to use.
  * `--save /etc/pacman.d/mirrorlist`: saves the generated mirrors to the target file.



📋

You can also add multiple nations by using the `-c <country_name>` multiple times.

For example, here, I will add 20 mirrors for India using the HTTPS protocol:

```

    sudo reflector -c india -l 20 -p https --save /etc/pacman.d/mirrorlist

```

![Get the fastest mirrors using the geographical location][9]

If you notice, it only added 3 mirrors because no other mirrors exist for India.

So if you want more mirrors, you will have to specify more countries, like I did here by adding mirrors for the US and China:

```

    sudo reflector -c india -c us -c cn -l 20 -p https --save /etc/pacman.d/mirrorlist

```

![Add fastest mirrors from multiple countries in Arch Linux][10]

💡

It is good to add more than one closest country to the mirrors list.

To get the list of countries and their respective codes, you can use the command:

```

    reflector --list-countries

```

![List of countries in reflector][11]

##### Adding mirrors irrespective of country

Here, you don't use the `-c` flag to specify the country but add the most recent mirrors irrespective of your geographical location.

In simple terms, you skip the `-c` flag and add global mirrors as shown here:

```

    sudo reflector -l <number of mirrors> -p <protocol> --save /etc/pacman.d/mirrorlist

```

It is an automatic selection of mirrors that may/may not be the closest.

For example, here, I added the 20 most recently synced mirrors over the HTTPS protocol:

```

    sudo reflector -l 20 -p https --save /etc/pacman.d/mirrorlist

```

![Reflector automatic mirror selection][12]

### New Arch user? Explore more!

If you are here, I assume that you are new to Arch Linux (or just looking for a refresher). Nevertheless, I recommend you to keep exploring if you are an Arch Linux user.

Maybe, you can start with trying interesting [alternatives to AUR][13]:

![][14]

Or, want to [install a GUI package manager like Pamac][15]?

![][14]

If you feel a little adventurous and up for a challenge, you can [change kernels in Arch Linux][16]:

![][14]

_💬 Any thoughts? Share them in the comments down below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/fast-arch-linux-mirrors/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/install-arch-linux/
[4]: https://itsfoss.com/content/images/2024/01/image-25.png
[5]: https://itsfoss.com/content/images/2024/01/image-27.png
[6]: https://linuxhandbook.com/what-is-grep/
[7]: https://linuxhandbook.com/tee-command/
[8]: https://itsfoss.com/content/images/2024/01/image-28.png
[9]: https://itsfoss.com/content/images/2024/01/image-29.png
[10]: https://itsfoss.com/content/images/2024/01/image-30.png
[11]: https://itsfoss.com/content/images/2024/04/reflector-list-the-countries-to-get-codes-2.png
[12]: https://itsfoss.com/content/images/2024/01/image-31.png
[13]: https://itsfoss.com/best-aur-helpers/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://itsfoss.com/install-pamac-arch-linux/
[16]: https://itsfoss.com/switch-kernels-arch-linux/
