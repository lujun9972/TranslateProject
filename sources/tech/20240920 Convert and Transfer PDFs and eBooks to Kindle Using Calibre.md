[#]: subject: "Convert and Transfer PDFs and eBooks to Kindle Using Calibre"
[#]: via: "https://itsfoss.com/calibre-convert-transfer-kindle/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Convert and Transfer PDFs and eBooks to Kindle Using Calibre
======

[![Warp Terminal][1]][2]

S,o you bought a new e-book from a platform like [Humble Bundle][3] or other online stores.

And, now you want to transfer it to your Amazon Kindle. Fret not, I got you 😉

Kindle allows you to sideload books and there are two popular ways to do so. Either use Calibre or send the book to your Kindle mail.

💡

It is easier to ****send ebooks to Kindle via email****.

You can find your Kindle email by going to ****Settings → All Settings → My Account → Send-to-Kindle Email****.

Once done, compose an email using your regular email account. Attach the ebook to the email and send it to your Kindle email address.

But, the book must be in a supported format like Mobi or PDF.

Here, we focus on Calibre, as it allows you to configure the book by letting you configure the cover, formatting, and even change a file format to supported ones.

Now, let me highlight the steps you need to follow to transfer any e-book to Kindle using Calibre. If you do not have it installed, follow our guide here to set it up first:

![][4]

### Transfer any eBook to Kindle using Calibre

When you get an eBook from third-party platforms over Amazon Marketplace, you may have to change the file format to make it work on Kindle. For example, most books outside are available in EPUB format, which is supported by other e-readers but not Kindle.

So it is essential to know the file formats first and based on that you can decide if the book you intend to transfer requires the conversion to another format or not.

#### Step 0: Know the file format

Kindle supports various eBook formats, but for the most part, you'll be dealing with the following four:

  * ePub **(not supported by Kindle and needs to be converted to supported ones)**
  * MOBI
  * azw3
  * PDF



If the file you want to transfer to Kindle is MOBI, azw3, or PDF, you can directly use it without conversion.

**But if you have an EPUB file, then you'd need to convert it to MOBI or azw3.**

Here's how to do that:

#### Step 1: Import a book to Calibre

To import a book to Calibre, first, launch the Calibre software and click on `Add books` the button, and it will open the file manager where you choose books to add:

![][5]

Soon, you will see the titles in your Calibre program:

![][6]

#### Step 2: Convert eBook to supported file format

If the book you want to send to Kindle is not supported (probably an ePub format), then you can refer to this section where I'll show you how to convert that to a supported file format.

You can identify the file format by selecting an eBook from Calibre and on the right-hand side, you will find `Formats` where the book format is mentioned:

![][7]

To convert the eBook(s), first select one or more unsupported eBooks and hit the `Convert books` option:

![][8]

Now, go to `Page setup`, choose your Kindle model from the `Output profile`, select `MOBI` in output format and finally hit the `OK` button:

![][9]

Once finished, you will see the converted file format along with the previous file format:

![][10]

#### Step 3: Send eBook(s) to Kindle

To send eBooks to your Kindle device, first, plug in your Kindle device to your system and Calibre will detect the device showing a Kindle icon on the top bar.

Now, select one or more eBooks and hit the `Send to device` button:

![][11]

That's it!

### Wrapping Up...

It is incredibly easy to convert an eBook for Kindle, or for any other device you have using the Calibre ebook program. It is an excellent open-source program that every eBook reader should have, whether you are on Linux or other platforms.

_💬 How do you convert eBooks to read it on your Kindle device? Or, do you stick to the Amazon Marketplace or perhaps a Kindle subscription? Let me know about it!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/calibre-convert-transfer-kindle/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.humblebundle.com/books?partner=itsfoss
[4]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[5]: https://itsfoss.com/content/images/2024/03/Choose-books-to-add-in-Calibre.png
[6]: https://itsfoss.com/content/images/2024/03/Books-added-to-Calibre.png
[7]: https://itsfoss.com/content/images/2024/03/Find-the-ebook-file-format-in-Calibre.png
[8]: https://itsfoss.com/content/images/2024/03/Select-books-that-needs-to-be-converted.png
[9]: https://itsfoss.com/content/images/2024/03/Conver-Kindle-books.png
[10]: https://itsfoss.com/content/images/2024/03/Convert-book-using-Calibre.png
[11]: https://itsfoss.com/content/images/2024/03/Send-eBooks-to-Kindle-using-Calibre-in-Linux.png
