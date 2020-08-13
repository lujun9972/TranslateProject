[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Our favorite open source writing tools)
[#]: via: (https://opensource.com/article/20/8/open-source-writing)
[#]: author: (Opensource.com https://opensource.com/users/admin)

Our favorite open source writing tools
======
Opensource.com correspondents share their favorite tools for churning
out words.
![Working from home at a laptop][1]

Writing is one of the primary ways we communicate, and it's endlessly fascinating to see the different ways writers work. I can hardly imagine writing before computers and their ability to instantly edit and rearrange the words I've typed onto a screen. Likewise, I wonder whether people who started out writing on a typewriter process their thoughts differently, even on a modern word processor, or whether their workflow has changed and adapted because of these new tools.

We asked some of our correspondents how they get their thoughts into comprehensible words and what open source tools they prefer while doing so. As you might expect, we got different answers from everyone who answered.

### Text editors and word processors

Many of our authors prefer text editors. Then again, Opensource.com works a lot with [Markdown][2] during preproduction, so there could be some bias. Text editors are popular choices, though, probably in part because of their relative minimalism and also due to the separation between style and content.

Word processors are popular, too, because they enable authors to keep all their work in one file. For instance, an ODT file is actually just a ZIP file containing XML documents and metadata.

#### Matthew Broberg:

I use [VSCodium][3] (or VS Code) with an amazing extension that gives shortcuts for Markdown behaviors. I keep a folder on my laptop called `writing,` and I keep articles in progress in GitLab. Write, iterate, git commit, and back up to GitLab.

Alternatively, when I want to keep everything in a cloud-based solution, I keep my work in [HackMD][4] or [Etherpad][5].

#### Jason van Gumster:

I keep myself tied to the terminal when writing.

Writing happens in [Vim][6], with a handful of plugins (e.g., my base `.vimrc` [lives there][7]).

For version control, I use Mercurial. I've used Git before for writing, but Mercurial just tastes better to me for creative work.

I use [Wdiff][8] for seeing word-level differences between versions.

When writing away from the desk (which doesn't happen much these days), I write on my phone with a Bluetooth keyboard. Using [Termux][9] on Android, I can get a full terminal and still have access to Vim and Mercurial with all my command-line toys. When interfacing with book editors, who still predominantly rely on a DOC-based workflow, I have to convert to DOC/DOCX (using Pandoc) and then work in LibreOffice to reconcile their notes.

#### Seth Kenlon:

I use [Emacs][10] and write mostly in [DocBook][11]. I use [Git for version control][12]. I maintain a custom stylesheet in XSL along with custom Makefiles to transform my DocBook source into plain text, HTML, EPUB, and PDF. When writing for Opensource.com, I often write in [CommonMark][13] for its simplicity, but for text I have to maintain, I keep the source in DocBook.

#### Joshua Allen Holm:

It varies slightly depending upon what and for whom I am writing. The basics look like this:

  * Research gets organized in [Zotero][14], where I keep full-text copies of the PDFs and websites I need to reference.
  * Writing is done either in [LibreOffice][15] for academic stuff, where I need to include citations, or [gedit][16] when I write Markdown (for Opensource.com articles and the like).
  * My works in progress are stored in a `Writing` directory, which is organized into subdirectories based on what the writing is (for example, `Writing/DistroWatch/Fedora 32 Review` or `Writing/Opensource.com/Summer Reading List`).
  * An in-progress directory is version-controlled with Git and also copied to a flash drive that I store in a fireproof case at least once a week.
  * I make a PDF copy of every web-based article I write using the finished, published article and attach it to my bibliography in Zotero. Ditto for things that are not web-based, but the process is less tedious. I export from LibreOffice to PDF, or I just take the publisher's final PDF, whenever possible.



### Planning tools

One of the most effective ways to write something with a predictable outcome is to outline it first. Not everyone outlines first, yet the end result is often just as good. The trade-off, however, is that writing organized with an outline is often completed sooner. With an outline, the logical flow of an article or paper is determined while input is still minimal. You don't have to sort through paragraphs and paragraphs of information; you only have to move headings. As you fill in the gaps between headings, the flow of the article becomes clear, and you can adjust immediately as needed.

#### Kevin Sonney:

My workflow is almost all in [Joplin][17]; research, notes, to-dos, etc., all using the built-in functionality, with sync to all my devices. I write in Markdown and submit that as a standalone document. For screenshots, I generally use the built-in OS screenshot tools, and I edit those in [GIMP][18].

#### Seth Kenlon:

I use [Org mode][19] for outlines because they're so easy to rearrange both in terms of their order and inheritance. I've been experimenting with writing entirely in Org mode, but because so much of the content I write ends up going to Markdown in the end, it seems silly to introduce any unnecessary conversion steps.

#### Jason van Gumster:

Thoughts and brainstorming happen in mindmaps with [Vym][20]. It's not terminal-based, which is unusual in my writing workflow, but it's quite handy for organizing and planning.

### Stay flexible

In all the answers we got about how people write, one common theme kept emerging: a willingness to experiment. Unsurprisingly, it seems our writers are eager to try out new technology and new systems, even if it means having to temporarily slow down personal productivity to learn something new. Sometimes, the net benefits are worth it. And when they're not, the worst thing that happens is that you've learned a new tool.

This is important for writers and for computerists in general—technology changes. Linux and open source do amazingly well to ensure backward compatibility and the ability to opt out of change, but eventually, we all have to grow.

Not only does this ensure that you're up to date on the latest tech developments, but it just may inspire you to [write your own article][21] for Opensource.com. Here's how correspondent Kevin Sonney sees it:

> Honestly, my workflow is pretty ad-hoc. Something looks interesting? I make a note that I might want to write an article on it some day. When I have time, I do so.

This is just the tip of the iceberg in terms of open source tools people use for writing. What are your favorites? Please share them in the comments.

Vim offers great benefits to writers, regardless of whether they are technically minded or not.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/open-source-writing

作者：[Opensource.com][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/admin
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/wfh_work_home_laptop_work.png?itok=VFwToeMy (Working from home at a laptop)
[2]: https://opensource.com/article/19/9/introduction-markdown
[3]: https://opensource.com/article/20/6/open-source-alternatives-vs-code
[4]: https://hackmd.io
[5]: https://pad.riseup.net
[6]: https://opensource.com/resources/what-vim
[7]: https://github.com/Fweeb/.vim
[8]: https://www.gnu.org/software/wdiff/
[9]: https://opensource.com/article/20/7/termux
[10]: https://opensource.com/article/20/3/getting-started-emacs
[11]: https://opensource.com/article/17/9/docbook
[12]: https://opensource.com/article/19/4/write-git
[13]: https://commonmark.org/
[14]: http://zotero.org
[15]: http://libreoffice.org
[16]: https://wiki.gnome.org/Apps/Gedit
[17]: https://opensource.com/article/19/1/productivity-tool-joplin
[18]: http://gimp.org
[19]: https://opensource.com/article/20/4/emacs-org-mode
[20]: https://sourceforge.net/projects/vym
[21]: https://opensource.com/how-submit-article
