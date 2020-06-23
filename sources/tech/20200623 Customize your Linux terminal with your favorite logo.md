[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Customize your Linux terminal with your favorite logo)
[#]: via: (https://opensource.com/article/20/6/customize-linux-terminal)
[#]: author: (Alan Formy-Duval https://opensource.com/users/alanfdoss)

Customize your Linux terminal with your favorite logo
======
Replace your terminal's boring green-on-black color scheme.
![Terminal window with green text][1]

I enjoyed using my terminal's green-on-black color scheme for many years. It is reminiscent of the DEC VT100/220 terminals that I used in college. I began to get bored with it earlier this year when I bought a [tenkeyless keyboard][2] from Hyper-X. The keyboard is black, and the keys are backlit in red, so I changed my terminal's colors to match. I think it looks really cool at night.

I use [GNOME][3] as my main desktop environment, and I prefer to stick with the standard GNOME Terminal. Here's how I customized its settings to achieve my new color scheme.

I always like to keep the default profile as a fallback in case I really screw things up; it's good to have a baseline. So first, I cloned the default profile and named the new clone HyperX. I did my customizations in this profile and, once I was happy, set it to be the default.

Second, under the new profile's **Colors** tab, I changed **Built-in schemes** to **Custom**. Then, for **Default color**, I set **Text** to red (#FF0000) and **Background** to black (#000000). I haven't decided my favorite colors for **Bold**, **Cursor**, and **Highlight**, but they are easy to adjust.

### Your distro logo

For beautiful screenshots of a terminal, there's no better command than **screenfetch**. Screenfetch autodetects your distribution and places an ASCII art version of the logo in your terminal window upon request. It also provides common information about your system, such as your user name, kernel version, uptime, and much more.

You can install screenfetch from your software repository, or from [source code][4].

![CC BY-SA Alan Formy-Duval][5]

### More than just a pretty effect

Cool desktop effects can be fun, but sometimes they're more than just visual treats. They can have a real benefit that alters how you work. For instance, I enable a transparent background for my terminal. I set it to a small amount, probably 10% opacity, so it doesn't interfere with my ability to read my terminal text. However, the benefit is that when my terminal is on top of another window (perhaps a browser page), I can read both. There's no need to **Alt+Tab** between the two windows.

Besides the neat effect, it is useful if you are only using one monitor.

What are your favorite terminal customizations? Please share them in the comments!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/customize-linux-terminal

作者：[Alan Formy-Duval][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/alanfdoss
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/osdc_terminals_0.png?itok=XwIRERsn (Terminal window with green text)
[2]: https://www.hyperxgaming.com/unitedstates/us/keyboards/alloy-fps-pro-mechanical-gaming-keyboard
[3]: https://www.gnome.org/
[4]: https://github.com/KittyKatt/screenFetch
[5]: https://opensource.com/sites/default/files/egon.webp (Terminal customization)
