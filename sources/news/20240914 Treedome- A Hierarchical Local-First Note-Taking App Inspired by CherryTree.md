[#]: subject: "Treedome: A Hierarchical Local-First Note-Taking App Inspired by CherryTree"
[#]: via: "https://news.itsfoss.com/treedome/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Treedome: A Hierarchical Local-First Note-Taking App Inspired by CherryTree
======
An interesting open-source app to securely take notes.
[![][1]][2]

If you are into taking notes on your computer, having a solution that doesn't mine your data to serve you with obnoxious ads is an important requirement, one that cannot be compromised on.

In my case, I have used many note-taking apps on Linux, with some of the [best ones][3] being Joplin, Standard Notes, and Notesnook. Of course, I always keep an eye out for new ones that do something different from the rest.

This time for _App Of The Week_ , we have Treedome, a **new secure note-taking app that focuses on being local-first and organizes notes in tree-like structures**.

🚧

Treedome is still under development; some features are yet to be implemented.

### Treedome: Secure Note-Taking Made Simple

![][4]

Powered by a robust TypeScript and Rust base, Treedome is a note-taking application that has just a single developer, [Tengku Izdihar][5], working on it, delivering essential fixes and upgrades.

Treedome is distributed as libre software, or “[libreware][6]”, which is a very permissive way of distributing software. It got its name from the tree-like structure it uses to store notes, with the dome bit being the encryption that secures the notes.

#### ⭐ Key Features

One of the main highlights of Treedome is the [XChaCha20-Poly1305][7] encryption it employs for securing notes, which has not been professionally audited yet, but the developer is open to that.

More on encryption can be found in the [documentation][8]. As for the other key highlights of Treedome:

  * **Uses SQLite**
  * **Cross-Platform**
  * **Rich Text Editor**



#### 💻 User Experience

I installed the latest .deb for Treedome on an Ubuntu 22.04.4 LTS [virtual machine][9], and it started right up without any issues.

On the first launch, Treedome asked me to open an existing document, but I didn't have one.

![][10]

So, I went into the “Create” tab and created a new folder with a file named “test.note”, I had to manually name it with that suffix; otherwise, document creation wouldn't proceed.

I then put in a password for the document and proceeded to create and open it.

![][11]

I populated the Treedome document with some funky cat-themed notes, during which I felt that the interface was quite easy to use. If you have used [rich-text][12] editors in the past, then you will feel right at home.

![][13]

You can add various types of formatting to text, like making it bold or italic, adding a strike-through, highlighting specific parts, turning it into a heading, and more.

You can also add blockquotes, lists, horizontal lines, align text, make use of subscript/superscript, and add emojis.

When you are done changing the note, you can either click on the big save button on the top-right of the editor or use the _Ctrl + S_ keyboard shortcut.

If you click on the downward arrow on the new note button, you will find that **you can create three types of notes** : a sibling note, a child note, and a diary note. The last one automatically creates a new parent note with the relevant year, with child notes being the month and date.

![][14]

To delete any note, you can click on the big delete button after selecting it. Do keep in mind that **deleting parent notes will result in child notes being gone too** , unless you drag and drop them under another note.

As you can see below, I dragged a note called “ _How Cats Can Be Mean and Well-Mannered_ ” under the “ _What Did The Cat Say?_ ” note, making it the child note for the latter.

![][15]

Of course, the “ _What Did The Cat Say?_ ” note is still a sibling note of the existing “ _Welcome to Treedome!_ ” note, which appeared after I created a new document. If you notice, I could also add emojis to the title of a note by using the handy emoji button.

I could further arrange my notes by adding tags to them. It was quite easy to do from the editor, I just added a “ _cat_ ” tag to test things out, and the “ _welcome_ ” tag came with the welcome note.

Another thing I noticed was that **if I left a note open for too long, the document would get closed due to inactivity** , which is a nice thing to have.

But, the default timeout time was too short.

![][16]

Luckily, that can be changed by going into the three-ribbon menu ( _when a document is open_ ) and going into “ _Configure_ ”. The same menu also features options to change the password of a document, show the sizes of notes, and a few other things.

![][17]

At the end of my testing, I was pretty impressed with Treedome; it did what it was meant to do and never crashed. What more do I need from a note-taking app?

### ⚙️ Installing Treedome on Linux

You can grab the _.deb_ file for use on Debian-based Linux distributions from the Codeberg [releases page][18] for Treedome. For other Linux distributions and users on Windows/macOS, they will have to refer to the official [installation guide][19].

Oddly enough, it doesn't list steps for Windows; maybe they forgot to add them?

[Treedome (Codeberg)][18]

On the other hand, if you want to contribute to the development of Treedome, you should give its [Codeberg repo][20] a visit.

_💬 Have you used encrypted note-taking apps such as this? How has your experience been with those?_

**Suggested Read** 📖

![][21]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/treedome/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/note-taking-apps-linux/
[4]: https://news.itsfoss.com/content/images/2024/09/Treedome_a.png
[5]: https://codeberg.org/tengkuizdihar
[6]: https://www.libreware.org/
[7]: https://en.wikipedia.org/wiki/ChaCha20-Poly1305#:~:text=%5Bedit%5D-,XChaCha20%2DPoly1305,-%E2%80%93%20extended%20nonce%20variant
[8]: https://codeberg.org/solver-orgz/treedome/src/branch/master/docs/development/encryption.md
[9]: https://itsfoss.com/virtual-machine/
[10]: https://news.itsfoss.com/content/images/2024/09/Treedome_b.png
[11]: https://news.itsfoss.com/content/images/2024/09/Treedome_c.png
[12]: https://en.wikipedia.org/wiki/Rich_Text_Format
[13]: https://news.itsfoss.com/content/images/2024/09/Treedome_d.png
[14]: https://news.itsfoss.com/content/images/2024/09/Treedome_e.png
[15]: https://news.itsfoss.com/content/images/2024/09/Treedome_f.png
[16]: https://news.itsfoss.com/content/images/2024/09/Treedome_g.png
[17]: https://news.itsfoss.com/content/images/2024/09/Treedome_h.png
[18]: https://codeberg.org/solver-orgz/treedome/releases
[19]: https://codeberg.org/solver-orgz/treedome/src/branch/master/docs/user/installation.md
[20]: https://codeberg.org/solver-orgz/treedome
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
