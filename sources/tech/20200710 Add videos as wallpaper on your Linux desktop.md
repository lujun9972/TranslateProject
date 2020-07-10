[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Add videos as wallpaper on your Linux desktop)
[#]: via: (https://opensource.com/article/20/7/linux-wallset)
[#]: author: (Marcos Oliveira https://opensource.com/users/marcos-oliveira)

Add videos as wallpaper on your Linux desktop
======
wallset is a simple command-line utility that lets you liven up your
Linux desktop.
![Sky with clouds and grass][1]

The Linux desktop is a beautiful thing, but if you're tired of boring wallpaper, then you should try [wallset][2], a command-line utility allowing you to set a video as your wallpaper. Wallset can also help you manage your wallpaper collection so you can conveniently make changes as often as you want.

### Installation

First, you must have the following software installed on your system:

  * [ffmpeg &gt;=4.2.3][3]
  * [feh &gt;=3.4.1][4]
  * [imagemagick &gt;=7.0.10.16][5]
  * [xrandr &gt;=1.5.1][6]
  * [xdg-utils &gt;=1.1.3][7]



After that, you need [Git][8] to clone the repository and then install it. To do this, run the commands below:


```
$ git clone <https://github.com/terroo/wallset> wallset.clone
$ cd wallset.clone
$ ./install.sh
```

Enter your `sudo` password to complete the installation.

### Usage

For quick help with the commands, run the `wallset` command with the `--help` parameter, or just `-h` for short.

The first necessary task is to add images. Without images added to wallset, you won't have anything to choose from when setting your wallpaper. To add images, run this:


```
$ wallset --add image.jpg
```

You can also add multiple images at once:


```
$ wallset --add image-1.jpg image-2.jpg image-3.jpg
```

If it is in a directory with several images, you can also add it like this:


```
$ wallset --add `ls *.jpg *.png`
```

#### Setting a wallpaper

Wallpapers are saved and indexed:


```
$ wallset --use 001
```

If you want to set your current wallpaper to the image you're adding, use the `--set` parameter:


```
$ wallset --set --add imagem.png
```

When you add content to wallpaper, a copy of the file is made for wallset to use, so wallset won't break when you move your copy of an image.

#### List wallpapers

Each time you add an image to wallset, it's indexed with a three-digit number (001, 002, 003, and so on). Obviously, if you have several images, it gets difficult to remember these, so you can see a list of all images you've added with the `--count` option:


```
$ wallset --count
```

You can also browse the images in wallset with the `--display` option:


```
$ wallset --display
```

You can get the number assigned to your current wallpaper using the `--show` option:


```
$ wallset --show
```

#### Removing images

You can remove the last image added:


```
$ wallset --remove
```

This removes the image from wallset.

#### Looping images

If you love change, you can loop through all images in wallset, so your wallpaper changes at whatever interval you set. To do this, use the `--time` option, providing some number of seconds as the argument. For example, should you want your wallpaper to change every hour:


```
$ wallset --quit
$ wallset --time 3600
```

#### Adding video as wallpaper

One of the most interesting features of wallset is that you can add videos as your wallpaper. To do this, run the command:


```
$ wallset --video /path/to/your-video.mp4
```

To stop a video, the procedure is the same as the image loop: use `--quit` (or just`-q` for short).

When you quit, the video image is paused or frozen, and the current frame becomes your current wallpaper. If you want to change that, use the `--use [number]` parameter to set a new one.

After using a video once, it is automatically added to the wallset video index. To list all videos, use the `--list-videos` option:


```
$ wallset --list-videos
```

If you want to use a video in your video directory, use the `--set-video` parameter, and then enter the number displayed when listing the videos.

For example:


```
$ wallset --set-video 1
```

# Uninstall

Wallset is a relatively new script and is largely intended for window managers such as [bspwm][9], [Fluxbox][10], [Openbox][11], [Ratpoison][12], and similar. Feel free to report bugs at <https://github.com/terroo/wallset/issues>.

If you want to uninstall `wallset`, use the installer script with the `uninstall` parameter:


```
$ cd ~/wallset.clone
$ ./install.sh uninstall
```

During the uninstallation, the copies of images and videos added to wallset are also deleted.

### Demo

I've created a [video showing the main features][13] of the program and using the [examples][14] that are part of the [repository][14] directory itself.

The video is in Brazilian Portuguese, but the commands and visuals are universal.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/linux-wallset

作者：[Marcos Oliveira][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/marcos-oliveira
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/bus-cloud.png?itok=vz0PIDDS (Sky with clouds and grass)
[2]: https://github.com/terroo/wallset
[3]: https://ffmpeg.org/
[4]: https://feh.finalrewind.org/
[5]: https://www.imagemagick.org/
[6]: https://gitlab.freedesktop.org/xorg/app/xrandr
[7]: https://www.freedesktop.org/wiki/Software/xdg-utils/
[8]: https://git-scm.com/
[9]: https://github.com/baskerville/bspwm
[10]: https://opensource.com/article/19/12/fluxbox-linux-desktop
[11]: https://opensource.com/article/19/12/openbox-linux-desktop
[12]: https://opensource.com/article/19/12/ratpoison-linux-desktop
[13]: https://youtu.be/Mb0SXMft2sw
[14]: https://github.com/terroo/wallset/tree/master/examples
