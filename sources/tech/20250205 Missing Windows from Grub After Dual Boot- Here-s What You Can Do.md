[#]: subject: "Missing Windows from Grub After Dual Boot? Here's What You Can Do"
[#]: via: "https://itsfoss.com/grub-os-prober/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Missing Windows from Grub After Dual Boot? Here's What You Can Do
======

[![Warp Terminal][1]][2]

One of the issues I encountered after dual booting Windows with Linux is the missing Windows entry from the grub menu.

Here's the scenario. Windows was present on the computer. I installed CachyOS alongside Windows. I selected to install [the Grub bootloader][3] that allows booting into Linux, Windows (and any other OS present on the system) along with the [option to access UEFI][4].

Only this time, Grub did not show Windows in the menu 😔

![Missing Windows from Grub bootloader][5]

That was disappointing but not surprising because I am aware that this is a feature.

Let me show you how you can fix this by enabling os-prober feature in Grub and then updating it.

### Step 1: Enable os-prober in grub

Grub config file is located at `/etc/default/grub`. If you open it via Nano or some editor, you'll see at the end of this file that os-prober is disabled by default sighting security reasons.

![][6]

**If you are familiar with any** [**terminal-based text editor**][7] **, use it to uncomment the line`# GRUB_DISABLE_OS_PROBER=false` by removing the # at the beginning of the line.**

However, if you are absolutely new to the command line, you can use this command in the terminal:

```

    echo "GRUB_DISABLE_OS_PROBER=false" | sudo tee -a /etc/default/grub

```

It will ask for your password. It should be the same account password you use to log in to the system.

🚧

When you type the password in Linux terminal, nothing is reflected on the screen. It feels as if your system is hanged, as there is no visible feedback. Don't worry. It's a security feature and most Linux terminals won't even show asterisks (*) as you enter the password. Just type it in and enter.

With os-prober enabled, Grub will look for the presence of other operating systems in EFI folder and will add them in the bootloader menu.

There is one little problem. The config changes won't take place unless you [update grub][8].

### Step 2: Update grub

On Ubuntu and some other distributions, there is a dedicated command to update grub:

```

    sudo update-grub

```

However, on Arch and some other distributions, you'll end up with update-grub command not found error.

That's because `update-grub` is not a standard command. It is just la stub for this command:

```

    sudo grub-mkconfig -o /boot/grub/grub.cfg

```

Run the above command if your system doesn't have `update-grub`.

It should show an output like this:

![][9]

And as you can see in the above output, grub is probing for other OS and has found Windows boot manager. This is an indication that when you reboot the system, grub should show Windows in the available option.

![And Windows is back in Grub][10]

### Still no Windows boot manager?

See, this method only works when dual boot succeeded properly and you have all EFI settings located in the same folder under the same ESP partition.

If that's not the case, you could try accessing the UEFI settings, go to boot order. Windows boot manager should be present there and if you move it up the order, you can boot from it into Windows.

This is not the most convenient option, I understand but it's a workaround until you figure out why Grub bootloader could not see Windows.

### 💡 Bonus tip: The time synchronization issue

Since we are discussing dual booting Windows and Linux, let me share another potential issue you'll encounter. You'll notice that [system time changes when you switch between Windows and Linux][11]. You can fix it, if you want.

![][12]

💬 I hope this little trick helps you get a better dual booting experience. Let me know in the comments if you were able to get Windows back in Grub.

--------------------------------------------------------------------------------

via: https://itsfoss.com/grub-os-prober/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/what-is-grub/
[4]: https://itsfoss.com/access-uefi-from-linux/
[5]: https://itsfoss.com/content/images/2025/02/missing-windows-from-grub-bootloader-in-dual-boot.webp
[6]: https://itsfoss.com/content/images/2025/02/grub-os-prober-disabled-by-default.png
[7]: https://itsfoss.com/command-line-text-editors-linux/
[8]: https://itsfoss.com/update-grub/
[9]: https://itsfoss.com/content/images/2025/02/updating-grub-cachy-os.png
[10]: https://itsfoss.com/content/images/2025/02/windows-back-in-grub-bootloader.webp
[11]: https://itsfoss.com/wrong-time-dual-boot/
[12]: https://itsfoss.com/content/images/icon/android-chrome-192x192-269.png
