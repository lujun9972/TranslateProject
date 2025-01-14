[#]: subject: "I Feel Like a Hacker Using These Cool Linux Terminal Tools"
[#]: via: "https://itsfoss.com/hacker-like-linux-terminal-tools/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Feel Like a Hacker Using These Cool Linux Terminal Tools
======

[![Warp Terminal][1]][2]

I found it cool enough to watch someone, often portrayed as a hacker, use the Linux terminal, especially in the movies. What if I try to become one of the super cool hackers from the Hollywood movies? 😎

Now that I'm older, I'm no longer fooled by those movie skits 😌 But, I'm still a kid at heart, and I want others to think that I am a secretive hacker when they see me using the terminal.

To pursue that, I started exploring a list of cool Linux terminal tools that I can use for the job.

If I can feel like a hacker with these tools, you can too! Let's give them a try!

💡

You can use CTRL+C to exit the terminal after running these tools.

### 1\. genact

Do you often feel like all you do in the terminal is run update commands, with nothing impressive to show off? Don’t worry—genact is here for you!

0:00

/1:02

1×

Running genact in a terminalRunning genact in a terminal

This little command will fill package download, network and other entries to your terminal. Those watching will think you are compiling some great programs.

You can install this from the [Ubuntu Snap store][3] or grab the prebuilt binary for genact from the [official GitHub repository][4] as per your CPU architecture.

If you downloaded the binary, open a terminal in the downloaded directory, and give the file execution permission with the following command:

```

    chmod +x ./genact-file-name

```

The file name will look like _genact-1.4.2-x86_64-unknown-linux-gnu_

Next, execute it using:

```

    ./genact-file-name

```

[genact][5]

### 2\. Cmatrix

Anyone who has seen _The Matrix_ movie cannot forget the iconic effect of characters raining down the screen. With CMatrix, you can recreate this mesmerizing display right in your terminal.

0:00

/0:09

1×

Cmatrix command running in terminal.

You can install Cmatrix from the official repository of most Linux distributions. For instance, here's the command for Ubuntu-based distributions:

```

    sudo apt install cmatrix

```

Now, just run it using the command:

```

    cmatrix

```

For more fun, you can pair it with other fun terminal tools like lolcat, [one of the fun ASCII art tools][6].

### 3\. Hollywood

[Hollywood][7] is that command which will make others think that your system has been hacked my someone.

It will burst a huge text and animation effects on your terminal, where regular keyboard entries will do nothing. For a minute, I forgot I had to stop it to continue writing the article, it looked so cool! 😎

To install hollywood on Ubuntu, use the command:

```

    sudo apt install hollywood

```

[Hollywood][8]

### 4\. TEXTREME

Do you want a text editor that will show all types of fancy animation for character entry and deletion?

Textreme is for you.

This is not a regular text editor, where you will code swiftly, but a cool fancy text editor, that gives a festive party vibe while you write something.

You can grab an executable binary from the [official website][9]. And, extract the tar file and double-click on the file to start the editor.

[TEXTREME][9]

### 5\. No More Secrets

No More secrets will show an encrypt/decrypt effect for everything piped into it. It tries to [recreate the famous data decryption effect][10] seen on screen in the 1992 hacker movie Sneakers.

There are no release files for this package. So, you need to [compile it][11] from GitHub.

Make sure you have git and essential build tools like make installed. Then use the following commands to proceed:

```

    git clone https://github.com/bartobri/no-more-secrets.git
    cd ./no-more-secrets
    make nms
    make sneakers
    sudo make install

```

This will install two tools, no-more-secrets or nms and sneakers.

#### Sneakers

Sneakers recreates the movie clip for you. Once the command completes printing encrypted characters, press any key to start the decrypting effect.

#### No More Secrets

Pipe any text output to this command and see the effect for yourself. If you would rather not press a key to start decryption, use:

```

    cat agatha.txt | nms -a

```

This will print the contents of the file in encrypted form and then automatically start to decrypt it and show the original content.

You can experiment with it to show different colors as well!

[No More Secrets][12]

### 6\. Cool Retro Term

Sometimes the feeling of a hacker or a whiz comes from retro tools. This is one of the super [cool terminal emulators][13] that helps achieve what we want here.

You can install the Cool Retro Term terminal emulator application on Ubuntu using the command:

```

    sudo apt install cool-retro-term

```

Next, open the terminal from your Activities Overview or app menu:

Do not forget to right-click on the terminal and explore the settings. There are more effects waiting!

![Cool Retro Term Settings][14]

[Cool Retro Term][15]

### 7\. gping

Did you ever use the [Ping command][16] to check whether you have an active internet connection? Or to check whether a site is up and running?

The ping command is just a text command, where you need to look at the values to get the picture. You can do the same, but have some aesthetically pleasing outputs (graph) using `gping`.

Install GPing on Ubuntu using the command:

```

    sudo apt install gping

```

0:00

/0:43

1×

Gping command

[gping][17]

### 8\. Bpytop

Bpytop is a [htop alternative][18] that prints system information neatly. You can use this command to make someone think that you're monitoring super serious aspects of your computer.

To install it, use the command:

```

    sudo apt install bpytop

```

0:00

/0:30

1×

Bpytop command with options

[Bpytop][19]

When it comes to Linux terminal tools, there are endless options from various individual developers.

Here, I have shared the ones that I tried to make myself look like a hacker to anyone who observes me when I use the computer 😄

You can also choose to explore some terminal emulators or [system monitoring tools][20] to have fun with:

![][21]

_💬 What is your favorite on the list? Do you have some fun tools that I missed listing here? Do share your thoughts in the comments below._

--------------------------------------------------------------------------------

via: https://itsfoss.com/hacker-like-linux-terminal-tools/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://snapcraft.io/install/genact/ubuntu
[4]: https://github.com/svenstaro/genact/releases
[5]: https://github.com/svenstaro/genact/
[6]: https://itsfoss.com/ascii-art-linux-terminal/
[7]: https://itsfoss.com/hollywood-hacker-screen/
[8]: https://github.com/dustinkirkland/hollywood
[9]: https://ash-k.itch.io/textreme
[10]: https://itsfoss.com/sneakers-movie-effect-linux/
[11]: https://itsfoss.com/install-software-from-source-code/
[12]: https://github.com/bartobri/no-more-secrets
[13]: https://itsfoss.com/linux-terminal-emulators/
[14]: https://itsfoss.com/content/images/2024/12/cool-retro-term-settings.png
[15]: https://github.com/Swordfish90/cool-retro-term
[16]: https://linuxhandbook.com/ping-command/
[17]: https://github.com/orf/gping
[18]: https://itsfoss.com/htop-alternatives/
[19]: https://github.com/aristocratos/bpytop
[20]: https://itsfoss.com/linux-system-monitoring-tools/
[21]: https://itsfoss.com/content/images/icon/android-chrome-192x192-214.png
