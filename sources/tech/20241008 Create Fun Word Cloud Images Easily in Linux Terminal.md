[#]: subject: "Create Fun Word Cloud Images Easily in Linux Terminal"
[#]: via: "https://itsfoss.com/wordcloud/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Create Fun Word Cloud Images Easily in Linux Terminal
======

[![Warp Terminal][1]][2]

Did you see cool wallpapers like the one below on communities and wallpaper websites?

![Sample wordcloud wallpaper][3]

I am sure many of you have seen such wallpapers.

In this tutorial, I will show how you can make such wallpapers and images in a very short time. Trust me, you don't need to be a Photoshop or GIMP Pro to do this!

### Wordcloud, the wordcloud generator

[Wordcloud][4] is a Python program for creating word cloud images. The project has been there for a long time and has been used in many other projects as dependencies.

Thanks to the developers of wordcloud, we can now generate our own images.

[Wordcloud][5]

By the way, if you are [new to the Linux terminal and command line][6], check out our tutorial series which is written for the absolute beginners.

![][7]

### Install wordcloud

Wordcloud is available in default repositories of Ubuntu. To install it, use the command:

```

    sudo apt install python3-wordcloud

```

🚧

This will install several packages with some considerable disk spaces. So, keep caution, a large download size is expected.

Wordcloud is available to install as a Python package. So you can install it either [using pip][8] or pipx. I prefer pipx to avoid some [possible headaches][9]. Once [pipx is installed][10], install wordcloud using the command:

```

    pipx install wordcloud

```

That's it. You have installed wordcloud, and it can be used with the command `wordcloud_cli`.

📋

Either way, ensure that matplotlib, pillow, and numpy are installed. These are also available in the Ubuntu repos by the names `python3-matplotlib`, and `python3-numpy`.

### Using wordcloud

Wordcloud offers several options and features that you can use to create unique images. Let's see some cool items!

📋

Before creating all wordcloud images, you need to have some collection of words. In usual case, you can store words in a text file. Other cases will be described below.

#### Create a simple image with words

Let's say you have 100 random words saved to a file called `words.txt`. To create an image from this file, use the command:

```

    wordcloud_cli --text </path/to/words.txt> --imagefile wallpaper.png

```

This will create a 400×200 PNG with the given words.

![Default Wordcloud Image][11]

#### Create an image with custom dimensions

Now, imagine you have created a text file with hundreds of words using ChatGPT or some AI clients. In this case, a higher resolution image will do better. Let's see how to create a bigger image!

```

    wordcloud_cli --text </path/to/words.txt> --width 1920 --height 1080 --imagefile highres.png

```

Now, it will create a high-resolution image (1920×1080 in this case).

#### Use a custom font

By default, wordcloud uses DroidSansMono font. If you need to create an image with a custom font, use the `--fontfile` option.

📋

You should specify the font file location to the `--fontfile` option. So you should have the required file in hand.

I am going to use the Comic Neue font to create the image. You can download fonts from [Google Fonts][12] website.

![Download a Font][13]

Extract the file and make the particular font file in an easily accessible location.

Now, run the command:

```

    wordcloud_cli --text </path/to/words.txt> --width 800 --height 400 --fontfile </path/to/font/file> --imagefile customfont.png

```

Now, you have a wordcloud image with a custom font!

![Custom Font][14]

#### Custom background color

Not interested in the black background? Don't worry, you can apply a different color.

📋

Wordcloud supports several color specifications. You can [check here][15] to know which format of colors will work, and use accordingly.

I am using a Nord type background color, so use the command:

```

    wordcloud_cli --text </path/to/words.txt> --background '#313744' --imagefile nord-background.png

```

![New background color][16]

#### Work with mask images

If you want to print images inside a particular frame, you can do that in wordcloud as well.

First, create a black image of the frame that you want to use. Here, I am using a black penguin image as the frame.

![Penguin Frame][17]

Now, use the `--mask` option to get the masked image.

```

    wordcloud_cli --text </path/to/words.txt> --mask </path/to/mask/image> --imagefile maskedimage.png

```

📋

Remember to make the mask image as wide as the required final image resolution.

![Masked Image wordcloud][18]

##### Use prebuilt examples

The project page has several examples available. Click the button below to check those.

[Check Examples][19]

Here, you can click on a particular design and download the corresponding Python script.

Once the script is downloaded, you can rename your words file as mentioned in the script. If you are using the mask, rename the mask file also according to the script.

For example, I am using [this example][20], where the words file is called `alice.txt` and the mask file is called `alice_mask.png`. So, I will rename my _words.txt_ as _alice.txt_ and mask image as _alice_mask.png_. This way it is easier than renaming variables and items inside the script.

Now, I will use the command:

```

    python3 masked.py

```

This will create an image called _alice.png_ , the result I require.

![Using prebuilt scripts][21]

### Possible image ideas

You can create several images unique to your system. Let's see some examples:

#### Installed packages

If you are using Debian/Ubuntu-based distributions, you can list the installed packages of your system and then make a text file of it.

```

    dpkg --get-selections > packages.txt

```

Now, use this `packages.txt` to create a wallpaper that lists all the package names you installed on your system.

#### Your bash command history ;)

If you are ok with exposing your bash history, save all the commands to a text file and then use this text to create an image.

```

    history > my_bash_history.txt

```

#### Other ideas

  * You can list the names of some programs that you cannot forget and then use it to create a wallpaper.
  * Use AI tools to create random word lists.
  * All Linux distro names.



### Wrapping Up

Even though wordcloud offers command line options for many tasks, this is used as a dependency for other Python projects. For that purpose, there are [API references][22] you can check.

One such project is [Process-wallpaper][23]. The project itself is a bit old, so it won't automatically apply wallpaper. But it does work creating a wallpaper based on the most resource-intensive processes presently running on your system.

On a similar note, you may want to use this handy CLI tool to [convert images into ASCII art][24]:

![][25]

--------------------------------------------------------------------------------

via: https://itsfoss.com/wordcloud/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/09/transperant.png
[4]: https://github.com/amueller/word_cloud
[5]: https://amueller.github.io/word_cloud/
[6]: https://itsfoss.com/linux-terminal-basics/
[7]: https://itsfoss.com/content/images/icon/android-chrome-192x192-46.png
[8]: https://itsfoss.com/install-pip-ubuntu/
[9]: https://itsfoss.com/externally-managed-environment/
[10]: https://itsfoss.com/install-pipx-ubuntu/
[11]: https://itsfoss.com/content/images/2024/09/wallpaper-1.png
[12]: https://fonts.google.com/
[13]: https://itsfoss.com/content/images/2024/09/download-a-font-file-from-google-fonts.png
[14]: https://itsfoss.com/content/images/2024/09/customfont.png
[15]: https://pillow.readthedocs.io/en/stable/reference/ImageColor.html
[16]: https://itsfoss.com/content/images/2024/09/newbackgroundcolor.png
[17]: https://itsfoss.com/content/images/2024/09/penguin-mask.png
[18]: https://itsfoss.com/content/images/2024/09/maskedimage-final.png
[19]: https://amueller.github.io/word_cloud/auto_examples/index.html
[20]: https://amueller.github.io/word_cloud/auto_examples/masked.html#sphx-glr-auto-examples-masked-py
[21]: https://itsfoss.com/content/images/2024/09/using-prebuilt-script.png
[22]: https://amueller.github.io/word_cloud/references.html
[23]: https://github.com/anirudhajith/process-wallpaper
[24]: https://itsfoss.com/ascii-image-converter/
[25]: https://itsfoss.com/content/images/icon/android-chrome-192x192-32.png
