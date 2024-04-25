[#]: subject: "Fixing update-grub command not found Error in Arch Linux"
[#]: via: "https://itsfoss.com/update-grub-command-not-found/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fixing update-grub command not found Error in Arch Linux
======

[![Warp Terminal][1]][2]

In Ubuntu, I use the `update-grub` command to [update grub][3]. Recently, I made a switch to Arch Linux for new adventures and there I encountered the error saying "sudo: update-grub: command not found":

![][4]

I remember choosing GRUB [while installing Arch][5] and the [GRUB][6] screen appeared too while booting the system. This is why I got confused when I saw the above error.

If you are in the same situation, let me share my findings with you.

### Why do you see 'update-grub' command not found error?

You see the error because `update-grub` is not a standard command like ls, cd etc. It's not even a standard command that is installed with grub.

In Ubuntu, the command is just an alias and when you run the update-grub command, it runs the following command instead:

```

    sudo grub-mkconfig -o /boot/grub/grub.cfg

```

The `grub-mkconfig` is the command for managing grub. But the above command is difficult to remember so the aliased shortcut `update-grub` was created.

📋

You can either run the above grub-mkconfig command or create a custom update-grub command to run the same.

### How to fix the update-grub command not found error

You can put some effort and create a custom `update-grub` command the same way it is implemented on Ubuntu and Debian.

It is a four-step process and I will assist you with every step.

##### Step 1: Create a new file

To create the `update-grub` command, the first step is to create a new file.

So open your terminal and use the following command:

```

    sudo nano /usr/sbin/update-grub

```

What the above command will do is create a new file named `update-grub` in the `/usr/sbin/` directory.

If you notice, there's a `nano` command used which is a text editor which is responsible for creating an opening the file just after executing the command.

It will open an empty file looking like this:

![][7]

#### Step 2: Write new lines to the file

(secret: you don't have to write but paste those lines 😉)

Once you execute the previous command, it will open the file where you have to add lines.

Simply select the following lines and [paste them into the terminal][8] using `Ctrl + Shift + V`:

```

    #!/bin/sh
    set -e
    exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

```

![][9]

Now, [save changes and exit from the nano][10] editor using `Ctrl + O`, press the `Enter` key and then `Ctrl + X`.

#### Step 3: Change ownership of the file

Once you are done creating the file, you have to assign the ownership to the root user of that file.

For that purpose, you'd have to [use the chown command][11] in the following manner:

```

    sudo chown root:root /usr/sbin/update-grub

```

![][12]

#### Step 4: Change file permissions

In the last step, you have to [change the read-write permissions][13] using the chmod command as shown here:

```

    sudo chmod 755 /usr/sbin/update-grub

```

![][14]

What the above command will do is only the file owner can read, write, and execute the file whereas others can only read and execute.

Once done, use the `update-grub` command it should work like you expect:

```

    sudo update-grub

```

![][15]

### What's next? How about customizing GRUB?

Well, there's a perception that everything related to GRUB is difficult but it is not and customize the GRUB bootloader as per your liking without any complex steps.

For that purpose, you'd have to install grub customizer, a GUI utility to customize grub easily.

Sounds interesting? Here's a [detailed guide on how to install and use grub customizer on Linux][16]:

![][17]

I hope you will find this guide helpful.

--------------------------------------------------------------------------------

via: https://itsfoss.com/update-grub-command-not-found/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/update-grub/
[4]: https://itsfoss.com/content/images/2024/01/image-19.png
[5]: https://itsfoss.com/install-arch-linux/
[6]: https://itsfoss.com/what-is-grub/
[7]: https://itsfoss.com/content/images/2024/01/image-20.png
[8]: https://itsfoss.com/nano-cut-copy-paste/
[9]: https://itsfoss.com/content/images/2024/01/image-21.png
[10]: https://itsfoss.com/nano-save-exit/
[11]: https://learnubuntu.com/change-file-ownership/
[12]: https://itsfoss.com/content/images/2024/01/image-22.png
[13]: https://learnubuntu.com/chmod-command/
[14]: https://itsfoss.com/content/images/2024/01/image-23.png
[15]: https://itsfoss.com/content/images/2024/01/image-24.png
[16]: https://itsfoss.com/customize-grub-linux/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
