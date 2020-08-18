[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Shrink PDF size with this command line trick)
[#]: via: (https://opensource.com/article/20/8/reduce-pdf)
[#]: author: (Greg Pittman https://opensource.com/users/greg-p)

Shrink PDF size with this command line trick
======
Use Ghostscript to compress PDF files on Linux.
![Files in a folder][1]

My wife tutors students throughout the year, and recently she wanted to assign homework by scanning some workbook pages into a file and emailing them to her students. She asked for my help, so I used [Simple Scan][2], a document scanning application for GNOME.

Simple Scan has two resolution settings, Images and Text, and saves files as PDFs. Unfortunately, the quality of the scans—the words, numbers, and graphics—is unsuitable using the Text setting, but the files are quite large—up to 5MB for just a few pages—using the Image setting. I found an answer to the latter problem using the commands `pdf2ps` and `ps2pdf`, which are part of the [Ghostscript][3] package. This solution shrinks the size of PDF files, making them easier to share via email.

The man pages for these commands are terse, and it was challenging to find good documentation for them and their settings. So I pieced together the following by combining information from the man pages with various other bits of advice I found on the internet.

### How to shrink a PDF

First, make a backup of the original PDF file with a different name (in case you make an error somewhere).

In this example, I'll show you how to shrink a file named **Lesson5.pdf**. The first step is to convert it to a PostScript file by entering:


```
`pdf2ps -dLanguageLevel=3 Lesson5.pdf`
```

This creates a file named `Lesson5.ps`, and if you look at its size, you might be alarmed. For example, this example file was 3.1MB as a PDF and ballooned to 29MB as a PS file! Have faith.

Next, enter:


```
`ps2pdf -dPDFSETTINGS=/ebook Lesson5.ps`
```

This overwrites your previous Lesson5.pdf with a smaller file (a good reason for making a backup). If you want, you can specify another name for the new PDF with:


```
`ps2pdf -dPDFSETTINGS=/ebook -sOutputFile=Lesson5b.pdf Lesson5.ps`
```

I find using the `/ebook` setting for the compression is a good compromise between file size and quality. In this example, the compressed PDF was 715KB, about one-fourth the size of the original.

### Use Ghostscript to compress a PDF

I also learned that I can use the `gs` command to accomplish everything in one go:


```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook \
-dNOPAUSE -dBATCH -dColorImageResolution=150 \
-sOutputFile=output.pdf someBigFile.pdf
```

But, looking at the `gs man` page, I don't think there is any way I would have come up with this on my own. To learn about the parameters not included in the man page, refer to the [Ghostscript online documentation][4].

I think I'll stick with the two much shorter commands that are easier for me to remember.

Explore the open source alternatives to Adobe Acrobat for reading, creating, and editing PDF files.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/reduce-pdf

作者：[Greg Pittman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/greg-p
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/files_documents_paper_folder.png?itok=eIJWac15 (Files in a folder)
[2]: https://gitlab.gnome.org/GNOME/simple-scan
[3]: https://www.ghostscript.com/
[4]: https://www.ghostscript.com/doc/current/Use.htm
