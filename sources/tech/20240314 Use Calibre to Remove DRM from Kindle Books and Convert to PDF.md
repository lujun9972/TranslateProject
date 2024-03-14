[#]: subject: "Use Calibre to Remove DRM from Kindle Books and Convert to PDF"
[#]: via: "https://itsfoss.com/calibre-remove-drm-kindle/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use Calibre to Remove DRM from Kindle Books and Convert to PDF
======

[![Warp Terminal][1]][2]

So you purchased ebooks from Amazon Kindle and now you want to read it on your personal computer or some other device that doesn't have Amazon Kindle app? You are in a difficult situation.

When you purchase a book from Amazon Kindle, it is DRM-protected. Which means you cannot use it outside the Amazon ecosystem. It can only be read using Amazon Kindle app or Kindle Cloud Reader.

You cannot just export it as PDF like a regular book or document.

Fortunately, with a little effort, you can use this open source software called Calibre to handle all your Kindle needs, including converting your Kindle ebooks to PDF.

But there's a catch. This task requires a special plugin and in this tutorial, I will walk you through everything you need to know to convert Kindle books you've purchased to PDF.

### Converting Kindle books to PDF

Kindle books are DRM (Digital Rights Management) protected to stop unauthorized sharing and copying.

This means if the DRM is enabled on the book you want to convert to PDF, it won't let you so it is necessary to remove the DRM first.

For that purpose, you'd have to use the `DeDRM` plugin in Calibre and in this tutorial, I will walk you through how you can install and use the DeDRM plugin to convert your Kindle books to PDF.

So let's start with the first step.

#### Step 1: Install the latest version of Calibre (7.x)

I've tried this with various versions of Clibre and was able to get it to work with the latest version of Calibre (7.6.0).

So if you're using Linux, then you can easily install the latest version of Calibre (7.x series) using the following command:

```

    sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin

```

#### Step 2: Install DeDRM_tools plugin

🚧

****The DeDRM_tools plugin is no longer maintained**** but it works fine for the current and previous iterations of Calibre. If you face any issues, you can refer to the modern forks of the DeDRM_tools plugins on GitHub.

First, visit the download page of the [DeDRM_tools on GitHub][3] and download the zip file for the latest version:

![][4]

#### Step 3: Load the plugin

To load the plugin, the first step is to unzip the downloaded file as it contains 2 plugins so unzipping the file will let you choose the required one.

To unzip the file, you can [use the unzip command][5] or do it directly from your file manager. I'd go with the file manager where you right-click on the zip file and choose the extract option:

![][6]

Now, open the Clibre software from your system and open the preferences tab using the `Ctrl + p` shortcut. Then, follow two simple steps:

  1. Click on `plugins`
  2. Choose `Load plugin from file`.



![][7]

It will open the file manager and ask you to choose the plugin. Now, navigate to the extracted files and choose the `DeDRM_plugin.zip` file.

Once you click on the `Open` button, it will ask if you want to add this external plugin to your system or not as it may contain viruses/malware. Press the `Yes` button:

![][8]

It will show the added plugin to Calibre with a short description. To confirm this, press the `Apply` button:

![][9]

**Now, restart your Calibre to take effect from the plugin you've just added to your system.**

#### **Step 4: Add Kindle's serial number to DeDRM**

To find the serial number of your Kindle device, go to Amazon and click on `Account & Lists`:

![][10]

Scroll down and there you will find an option for `Devices` under the `Digital content and devices` category:

![][11]

Once you click on `Devices`, you will find your Kindle from the `Amazon devices`. To get the serial number for that device, click on the name of your device.

In my case, I'd have to click on `Sagar's kindle`:

![][12]

After clicking on your device name, it will show the device information including the serial number. Copy the serial number:

![][13]

Next, open Calibre, go to `Preferences` > `Plugins` > `File type` and then double-click on `DeDRM` plugin.

Now, click on `eInk Kindle ebooks`, hit the plus ➕ icon and enter the Kindle serial number:

![][14]

Hit OK and you're good to go.

#### Step 5: Download ebooks (that you want to convert)

To download ebooks that you purchased through Amazon, go to `Your Account` > `Content Library` and it will list the content you've purchased.

To download a book, look for the `More actions` button and then choose the `Download & transfer via USB` option:

![][15]

Once you proceed to download the file, choose the device from which you entered the serial number in the plugin.

I only have one Kindle device so it will only show me a single option. After choosing the device, hit the `Download` button:

![][16]

#### Step 6: Convert books to PDF

To convert downloaded books, click on `Add books` and choose one or more books that you want to convert to PDF:

![][17]

After adding books to the library, select one or more books and click on `Convert books` option:

![][18]

Next, choose `PDF` in the output format and hit OK:

![][19]

It will take a few seconds and soon you'll see the PDF format along with the default format:

![][20]

If you wish to download the PDF version of a file, right-click on the `PDF` format and choose `Save the PDF format to disk` option:

![][21]

That's it!

### Troubleshooting tips

If the shown method does not work for you and it shows you an error saying the content is DRM protected, then you have to use a different version of Calibre and DeDRM tools:

  * Install Calibre version 4.23
  * Download DeDRM version 6.8.1



To install Calibre 4.23, you can use the following command which will remove the existing Calibre and install Calibre version 4.23:

```

    sudo -v && sudo calibre-uninstall && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin version=4.23.0

```

You can [download DeDRM 6.8.1][22] from their official download page.

I hope you will find this guide helpful and if you have any queries or suggestions, leave a comment.

--------------------------------------------------------------------------------

via: https://itsfoss.com/calibre-remove-drm-kindle/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/apprenticeharper/DeDRM_tools/releases
[4]: https://itsfoss.com/content/images/2024/01/Download-the--DeDRM_tools-plugin.png
[5]: https://learnubuntu.com/unzip-file/
[6]: https://itsfoss.com/content/images/2024/03/extract-the-plugin-1.png
[7]: https://itsfoss.com/content/images/2024/03/Open-preferences-in-calibre-to-add-external-plugins.png
[8]: https://itsfoss.com/content/images/2024/03/Load-the-DeDRM-plugin-to-Calibre-1.png
[9]: https://itsfoss.com/content/images/2024/03/Confirm-adding-of-DeDRM-plugin-to-Calibre.png
[10]: https://itsfoss.com/content/images/2024/03/Click-on-accounts-and-Lists.png
[11]: https://itsfoss.com/content/images/2024/03/Click-on-devices.png
[12]: https://itsfoss.com/content/images/2024/03/Find-your-Kindle-from-Kindle-devices.png
[13]: https://itsfoss.com/content/images/2024/03/Copy-kindle-serial-number.png
[14]: https://itsfoss.com/content/images/2024/03/Enter-Kindle-serial-number.png
[15]: https://itsfoss.com/content/images/2024/03/Download-ebooks-from-Amazon.png
[16]: https://itsfoss.com/content/images/2024/03/Transfer-ebook-to-device.png
[17]: https://itsfoss.com/content/images/2024/03/Add-books-to-calibre.png
[18]: https://itsfoss.com/content/images/2024/03/Conver-books-in-Calibre.png
[19]: https://itsfoss.com/content/images/2024/03/Convert-Kindle-purchased-books-to-PDF.png
[20]: https://itsfoss.com/content/images/2024/03/Conver-DRM-protected-ebooks-to-PDF-in-calibre.png
[21]: https://itsfoss.com/content/images/2024/03/Download-the-PDF-format-of-a-book-through-Calibre.png
[22]: https://github.com/apprenticeharper/DeDRM_tools/releases/tag/v6.8.1
