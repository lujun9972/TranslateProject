[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Improve your focus and productivity with this Python tool)
[#]: via: (https://opensource.com/article/20/8/python-concentration)
[#]: author: (Sudeshna Sur https://opensource.com/users/sudeshna-sur)

Improve your focus and productivity with this Python tool
======
Concentration offers a quick way to filter out distractions and focus on
coding.
![woman on laptop sitting at the window][1]

Limiting distractions helps you focus on your work so you can increase productivity. Prioritizing your tasks, especially when you have too much on your plate, is one way to help you focus on the most important or high-attention things on your list. 

Another way to focus on tasks is Python [Concentration][2], a helpful tool I found a few years ago for improving my time-management skills and increasing my focus. It is a simple Python 3 console utility that reduces distractions by blocking things like gaming, news sites, YouTube, and Netflix when I need to pay attention to work, but it also allows me to take timed breaks when I need them.

![Concentration][3]

(Timothy Crosley, [CC BY-SA 4.0][4])

### Getting started with Concentration

Concentration uses pip, the Python Package Installer, for installation. If needed, install pip with:

  * Fedora: `$ dnf install pip`
  * RHEL/CentOS: `$ yum install pip`
  * Debian: `$ apt install pip`



Then use pip to install Concentration with either:


```
`$ pip3 install concentration`
```

or, if pip is already set to use Python 3:


```
`$ pip install concentration`
```

You can install Concentration as a regular user or as a privileged user (root).

### Block distracting sites

Concentration uses your `/etc/hosts` file as the mechanism to block sites. It also comes with a default list of blocked sites, called `DISTRACTORS`. You can check the list with:


```
`$ sudo concentration blocked`
```

You can add sites to this list under `DISTRACTORS` in your `settings.py` file. The path will depend on your installation (mine is `/usr/local/lib/python3.8/site-packages/concentration/settings.py`).

![Concentration distractors list][5]

(Sudeshna Sur, [CC BY-SA 4.0][4])

If you're on a site you want to block, enter:


```
`$ sudo concentration improve`
```

### Take a break

It may sound counterintuitive, but taking short breaks during your workday can help you focus on your work better. Concentration allows you to take time-limited breaks so you can clear your head while helping you get back on task when your break time is over.

To take a short, five-minute break, which is counted in seconds:


```
`$ sudo concentration break`
```

To take a long, 60-minute break:


```
`$ sudo concentration break -m 60`
```

To pause Concentration so you can access all sites (like when you're not at work):


```
`$ sudo concentration lose`
```

### Give it a try

Concentration is a simple, very useful tool that will help you focus throughout your day and take breaks to relax when you need them.

If you think this tweak is interesting, give it a try and report what you think in the comments below. And, if you know of other cool tricks to improve your focus and avoid distractions, please share them in the comments, as well.

Share your favorite music for coding by taking our poll. If none of these artists represent music...

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/python-concentration

作者：[Sudeshna Sur][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/sudeshna-sur
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/lenovo-thinkpad-laptop-window-focus.png?itok=g0xPm2kD (young woman working on a laptop)
[2]: https://pypi.org/project/concentration/
[3]: https://opensource.com/sites/default/files/uploads/concentration.gif (Concentration)
[4]: https://creativecommons.org/licenses/by-sa/4.0/
[5]: https://opensource.com/sites/default/files/uploads/concentration_distractors-list.png (Concentration distractors list)
