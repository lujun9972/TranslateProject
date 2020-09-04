[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Copy Paste in Linux Terminal [For Absolute Beginners])
[#]: via: (https://itsfoss.com/copy-paste-linux-terminal/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

How to Copy Paste in Linux Terminal [For Absolute Beginners]
======

I have been using Linux for a decade now and this is why sometimes I take things for granted.

Copy pasting in the Linux terminal is one of such things.

I thought everyone already knew this until one of the It’s FOSS readers asked me this question. I gave the following suggestion to the Ubuntu user:

**Use Ctrl+Shift+C for copying and Ctrl+Shift+V for pasting text in the terminal in Ubuntu. Right click and selecting the copy/paste option from the context menu is also an option.**

I thought of elaborating on this topic specially when there is no single universal way of copy and paste in the Linux terminal.

### How to copy paste text and commands in the Linux terminal

![][1]

There are several ways to do this.

#### Method 1: Using keyboard shortcuts for copy pasting in the terminal

On Ubuntu and many other Linux distributions, you can use Ctrl+shift+C for copying text and Ctrl+shift+V for pasting text in the terminal.

![][2]

The copy pasting also works for the external sources. If you copy a command example from It’s FOSS website (using the generic Ctrl+C keys), you can paste this command into the terminal using the Ctrl+Shift+V into the terminal.

Similarly, you can use Ctrl+shift+C to copy text from the terminal and then use it to paste in a text editor or web browser using the regular Ctrl+V shortcut.

Basically, when you are interacting with the Linux terminal, you use the Ctrl+Shift+C/V for copy-pasting.

#### Method 2: Using right click context menu for copy pasting in the terminal

Another way of copying and pasting in the terminal is by using the right click context menu.

Select the text in the terminal, right click and select Copy. Similarly, to paste the selected text, right click and select Paste.

![][3]

#### Method 3: Using mouse to copy paste in Linux terminal

Another way to copy paste in Linux terminal is by using only the mouse.

You can select the text you want to copy and then press the middle mouse button (scrolling wheel) to paste the copied text.

Please keep in mind that these methods may not work in all the Linux distributions for a specific reason that I explain in the next section.

### There is no universal key shortcuts for copy paste in the Linux terminal. Here’s why!

The keybindings for copy-pasting are dependent on the terminal emulator (commonly known as terminal) you are using.

If you didn’t know that already terminal is just an application and you can install other terminals like [Guake][4] or Terminator.

Different terminal applications may have their own keybindings for copying and pasting like Alt+C/V or Ctrl+Alt+C/V.

Most Linux terminals use the Ctrl+Shift+C/V keys but if it doesn’t work for you, you may try other key combinations or configure the keys from the preferences of the terminal emulator.

Quick word about Putty

If you [use Putty on Linux][5] or Windows, it uses an entire different keybindings. In Putty, selecting a text automatically copies it and you can paste it using right click.

### Why Linux terminals do not use the ‘universal’ Ctrl+C and Ctrl+V for

No Linux terminal will give you Ctrl+C for copying the text. This is because by default Ctrl+C keybinding is used for sending an interrupt signal to the command running in foreground. This usually stops the running command.

![Using Ctrl+C stops a running command in Linux terminal][6]

This behavior has been existing long before Ctrl+C and Ctrl+V started being used for copy-pasting text.

Since the Ctrl+C keys are ‘reserved’ for stopping a command, it cannot be used for copying.

Used Ctrl+S and hanged the terminal?

Most of us use Ctrl+S keys to save changes made to text, images etc. This key is almost universal for saving same as Ctrl+C is for copying.
However, if you enter Ctrl+S in Linux terminal, it will freeze the terminal. No need to close the terminal and start it again. You can use Ctrl+Q to unfreeze the terminal.
Ctrl+S and Ctrl+Q are shortcut keys for [flow control][7].

I know this is elementary for the Sherlock Holmes of the Linux world but it could still be useful to the Watsons.

New or not, you may always use [shortcuts in Linux terminal][8] to make your life easier.

--------------------------------------------------------------------------------

via: https://itsfoss.com/copy-paste-linux-terminal/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/09/copy-paste-linux-terminal.png?resize=800%2C450&ssl=1
[2]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/09/copy-paste-linux-terminal.gif?resize=478%2C292&ssl=1
[3]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/09/copy-paste-terminal-ubuntu.png?resize=799%2C412&ssl=1
[4]: http://guake-project.org/
[5]: https://itsfoss.com/putty-linux/
[6]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/09/ctrl-c-linux.png?resize=703%2C303&ssl=1
[7]: https://www.gnu.org/software/screen/manual/html_node/Flow-Control-Summary.html
[8]: https://linuxhandbook.com/linux-shortcuts/
