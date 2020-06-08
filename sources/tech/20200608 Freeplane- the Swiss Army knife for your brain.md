[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Freeplane: the Swiss Army knife for your brain)
[#]: via: (https://fedoramagazine.org/freeplane-swiss-army-tool-your-brain/)
[#]: author: (Héctor Louzao https://fedoramagazine.org/author/hhlp/)

Freeplane: the Swiss Army knife for your brain
======

![][1]

A previous Fedora Magazine article covered [tracking your time and tasks][2]. Another introduced [some mind mapping tools][3]. There you learned that mind mapping is a visual technique for structuring and organizing thoughts and ideas. This article covers another mind mapping app you can use in Fedora: [Freeplane][4].

Freeplane is a free and open source software application that supports thinking, sharing information and getting things done. Freeplane runs on any operating system that has a current version of Java installed.

### Installing Freeplane

Freeplane is not currently packaged in the Fedora repositories, so you will need to install it from the project’s website.

  1. Go to the project’s [Sourceforge site][5] and click _Download_ to download the file
  2. Open a terminal and extract the file (note that the version you download may be different): _unzip freeplane_bin-1.8.5.zip_
  3. Move the extracted contents to the /opt directory: _sudo mv freeplane-1.8.5 /opt/freeplane_



The configuration file is located in: _~/.config/freeplane_. You can launch Freeplane by running _/opt/freeplane/freeplane.sh_ from a terminal, but if you want to launch it from the desktop environment you can create a desktop file.

Open your favorite text editor and save the contents below to _~/.local/share/applications/freeplane.desktop_.

```
[Desktop Entry]
Version=1.0
Name=Freeplane
Icon=/opt/freeplane/freeplane.svg
Exec=/opt/freeplane/freeplane.sh
Terminal=false
Icon=freeplane
Type=Application
MimeType=text/x-troff-mm;
Categories=Office;
GenericName=Freeplane
Comment=A free tool to organise your information
Keywords=Mindmaps; Knowledge management; Brainstorming;
```

Next, update the desktop file database with _update-desktop-database ~/.local/share/applications_

Now you can launch Freeplane from your desktop environment.

### Using Freeplane

At its first startup, Freeplane’s main window includes an example mind map with links to documentation about all the different things you can do with Freeplane.

![][6]

#### Start your First Mind Mapping

You have a choice of templates when you create a new mind map. The standard template works for most cases. Start typing the idea and your text will replace the center text.

Press the Insert key to add a branch (or node) off the center with a blank field where you can fill in something associated with the idea. Press Insert again to add another node connected to the first one.

Press Enter on a node to add a node parallel to that one.

All keyboard shortcuts are in the [Freeplane documentation][7].

#### Freeplane Plug-ins

Plug-ins can be used to extend and customize the use of the app. Two important ones are:

  1. [Freeplane GTD+][8]: A generic task management add-on, with a special focus in supporting the Getting Things Done (GTD) methodology
  2. [Study Planner][9]: helps organize learning



To install a new add-on to Freeplane, find the add-on you want on the [Freemind add-ons directory][10].

  * Download the desired add-on
  * In Freeplane, select _Tools_ &gt; _Add-ons_
  * Click the _Search_ button
  * Find and select the file you just downloaded
  * Click _Install_
  * Depending on the add-on, you may have additional questions to answer
  * Restart Freeplane to use the new add-on



### Integrating mind mapping in your everyday life

Mind mapping is a very powerful method that can be of great assistance in many aspects of life.

  * Learning Linux or any certification
  * Learning a computer language
  * Learning a human language
  * Even earning a degree



Whatever the objective this will always help to keep the ideas together and organized.

Personally I’m earning a few [Linux Professional Institute][11] certifications. The image below shows a mind map I am creating as I go through the systemd materials.

![][12]

### Conclusion

Now you have a start on how you can use Freeplane. Freeplane gives you all the tools you’ll need to create great, vibrant, and useful mind maps. Share how you use it in the comments.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/freeplane-swiss-army-tool-your-brain/

作者：[Héctor Louzao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/hhlp/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/05/freeplane-mind-map-816x345.png
[2]: https://fedoramagazine.org/tracking-your-time-and-tasks-on-fedora/
[3]: https://fedoramagazine.org/three-mind-mapping-tools-fedora/
[4]: https://www.freeplane.org/wiki/index.php/Home
[5]: https://sourceforge.net/projects/freeplane/
[6]: https://fedoramagazine.org/wp-content/uploads/2020/05/freeplane-1024x442.png
[7]: http://freeplane.sourceforge.net/doc/FP_Key_Mappings_Quick_Guide.pdf
[8]: https://www.itworks.hu/portfolio/freeplane-gtd/
[9]: http://sourceforge.net/apps/phpbb/freeplane/viewtopic.php?f=1&t=455
[10]: https://freeplane.sourceforge.io/wiki/index.php/Add-ons_(install)
[11]: https://www.lpi.org/
[12]: https://fedoramagazine.org/wp-content/uploads/2020/06/systemd.png
