[#]: subject: "How to Remove Password from PDF Files in Linux"
[#]: via: "https://itsfoss.com/remove-pdf-password-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Remove Password from PDF Files in Linux
======

The other day, I received a PDF file which was password protected. I also received the password of the file.

Now, when I open this PDF file, it asks to enter the password first. The default document viewer gives the option to save the password to avoid entering it again and again. However, the PDF will still be required if the file is to be read on some other device or if I want to transfer the file to my Kindle.

Thankfully, it is fairly easy to 'remove' password from a password protected PDF file. Actually, you create a new password-less version of the file.

I'll share two methods for getting this task done:

  * GUI method that uses Evince document viewer
  * CLI method that uses qpdf CLI tool



🚧

This tutorial is NOT about cracking a password protected PDF file. It works when you have the password of the PDF file but do not want to enter it every time you open it.

### GUI Method: Remove password from PDF using Evince document reader

Ubuntu and many other distributions come with the [Evince document reader app][1] installed. It is usually displayed as 'Document Viewer' in the GNOME desktop environment.

If you do not have it installed, please install it using the package manager or software center of your distribution.

Open the PDF file in the Document Viewer. Enter the password of the document when asked.

![][2]

The PDF document will be open for reading now. However, you have a different motive here.

Click on the hamburger menu in the top-right corner and click the print icon. You could also use the Ctrl+P keyboard shortcut.

![][3]

It will give you the option to print the document. What you have to do here is to select 'Print to file' option. This option is also available as 'Print to PDF' at times. This will save a copy of the document as PDF.

You may also choose the location and name of the unlocked output file.

![][4]

It will show a notification that it is 'printing the file' but it is actually creating the new PDF file.

![Unlocked PDF file being created but you'll see it as Printing Job][5]

Once the process is done, you can go to the output PDF file, double click on it to open it and enjoy the PDF file without password.

📋

I think that the default PDF document viewer apps in many other desktop environments are also capable of this. You are welcome to explore it in your choice of desktop environments.

### CLI Method: Remove password from PDF file using qpdf command

You can use the `qpdf` utility in the terminal to remove the password from the PDF file (if you know it). _**You may have to install it first.**_

The syntax is quite simple:

```

    qpdf --password=PDF-PASSWORD --decrypt input_pdf output_pdf

```

Here, you have to replace PDF-PASSWORD with the password of the PDF file, input_pdf with the password-protected PDF file's name and path (if required). Similarly, you should replace output_pdf with an appropriate PDF file name.

When I tested this command, its output showed me some warnings but the resulted PDF file worked just fine.

![][6]

There are many other command line utilities that can do the same job. For example, you can use the pdftk tool:

```

    pdftk input_pdf output output_pdf user_pw PDF-PASSWORD

```

### Conclusion

As you can see, it is fairly easy to remove the password from PDF files. Of course, it won't work if you do not know the password of the file in the first place. This is more for removing the annoyance of entering passwords again and again.

I hope you liked this quick tip. Let me know in the comments if you have any questions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/remove-pdf-password-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://wiki.gnome.org/Apps/Evince
[2]: https://itsfoss.com/content/images/2024/02/unlock-password-protected-pdf-linux.png
[3]: https://itsfoss.com/content/images/2024/02/print-option-in-pdf-document-viewer.png
[4]: https://itsfoss.com/content/images/2024/02/print-document-to-file-1.png
[5]: https://itsfoss.com/content/images/2024/02/saving-pdf-by-printing-it.png
[6]: https://itsfoss.com/content/images/2024/02/removing-passowrd-from-pdf-linux.png
