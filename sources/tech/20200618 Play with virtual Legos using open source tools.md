[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Play with virtual Legos using open source tools)
[#]: via: (https://opensource.com/article/20/6/open-source-virtual-lego)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)

Play with virtual Legos using open source tools
======
Open source virtual Legos allow you to build anything you can imagine.
![Open Lego CAD][1]

My childhood consisted of about 20% Dungeons &amp; Dragons (D&amp;D) and 80% Legos, with a pretty strong crossover of the two. I wasn't allowed to actually play D&amp;D for a variety of reasons, but through some mental acrobatics worthy of a level 15 rogue, I determined that building AD&amp;D characters didn't count as playing, and recreating Dragonlance in Lego form was a pretty good approximation of the game.

For that reason, one of my favorite genres of Legos was the castles, and I spent hours upon hours devising gauntlet-like dungeons for my mini figurines. In order to keep track of my creations, and because I saw friends mapping dungeons at school, I mapped out my Lego creations on graph paper. I also tried to track how my creations were constructed, and using graph paper seemed a logical choice for a medium that was mostly based on rectangular bricks, but the lack of understanding of isometric illustration ultimately confounded me.

Now that I'm older, my love of Legos hasn't diminished, and while I'm not overproud of any of my own creations (or "MOC," in the lingo of Internet brick builders), I have lately felt I owe it to myself to learn how to document what I build. Because my freehand illustration skills have never been very good, I decided to use technology to solve the problem.

### CAD for Legos

I have several years working in a virtualized 3D space (even longer in actual 3D space, for what that's worth). I'm comfortable with 3D applications, but all of the ones I've used have been specific to motion graphics and film production. They are, like film itself, generally just for show. How you build something is less important than whether the thing looks good. If you have to "cheat" what's physically possible to ensure that something looks cool, that's OK, because the thing you're building only exists in a virtual space.

Computer-Aided Design (CAD) is different. CAD software replaced old-style drafting, in which specifications are created to demonstrate how something may be built, once or 100 times, in the real world. There's an expectation of precision and realism.

Because Lego fans are legion, there is a prolific community of builders creating Lego models using CAD. The advantages are obvious—you can document what pieces you need and what steps you must take to build a model. This isn't a replacement for real Lego bricks unless you love CAD more than you do Legos, but it's a great augmentation to your hobby.

To build a virtual Lego model, you need two components:

  * virtual Lego bricks
  * a CAD application



There are a few ways to satisfy each requirement, but I've found I prefer the open source, modular approach.

### Virtual Lego bricks

You can get nearly every Lego piece ever created from the open source [LDraw][2] project. LDraw is an [open standard for Lego CAD][3], which includes consistent measurements and relative dimensions, and a simple language for how bricks are oriented. As a part of LDraw's work in defining bricks, the community also provides 3D models of each brick. That means you can [download thousands of brick definitions][4] in a relatively small download (42 MB or so).

### Installing your bricks

Virtual bricks are a lot like images on a website or fonts on your computer—as long as the application using the files knows where to find them, you can keep them anywhere. On Linux, it's common to put bricks in `/usr/share/LDRAW`. On Windows, they're usually installed to `C:\Users\Public\Documents\LDraw`.

The LDraw download only provides specifications for each brick. Here's what a 1x1 brick looks like in its raw form:


```
0 ~Brick  1 x  1 without Front Face
0 Name: s\3005s01.dat
0 Author: John Riley [jriley]
0 !LDRAW_ORG Subpart UPDATE 2004-01
0 !LICENSE Redistributable under CCAL version 2.0 : see CAreadme.txt

0 BFC CERTIFY CCW

0 BFC INVERTNEXT
1 16 0 24 0 0 0 6 0 -20 0 -6 0 0 box5.dat
4 16 10 24 -10 6 24 -6 6 24 6 10 24 10
4 16 10 24 10 6 24 6 -6 24 6 -10 24 10
4 16 -10 24 10 -6 24 6 -6 24 -6 -10 24 -10
4 16 -10 24 -10 -6 24 -6 6 24 -6 10 24 -10
1 16 0 24 0 10 0 0 0 -24 0 0 0 10 box4t.dat
1 16 0 0 0 0 0 1 0 1 0 -1 0 0 stud.dat
0
```

In order to see your creations in a more familiar form, you need a brick viewer.

### LDView for Lego renders

The application [LDView][5] is a 3D renderer, much like [POVray][6] or Blender's Cycles. It's specifically designed to render `.ldr` files, which are CAD files using LDraw part definitions.

If you're on Linux, then LDview may be available in your software repository, and if not, then you can download an installer from the project website. If you're on Mac or Windows, download an installer from the project website.

### Viewing a single brick

The easiest way to get started with Lego CAD is to try viewing a single brick.

First, open your favorite text editor. It can be any text editor, but it must be able to save in plain text. Some text editors are too helpful for their own good, and try to save your text in bloated file formats (like .rtf or .docx). There are many good cross-platform text editors out there. For this, I recommend the relatively minimalist [Geany][7] editor.

Create a new file called `1brick.ldr` and enter the following text into it:


```
0 Name: 1brick.ldr
0 Author: Seth Kenlon

0 clr  x y z  a b c  d e f   g h i &lt;file&gt;
1   1  0 0 0  0 0 1  0 1 0  -1 0 0 3001.dat
```

View your humble creation:


```
$ LDView 1brick.ldr
```

![one blue brick][8]

You have just created a simple CAD file defining a single brick (part number 3001), in color index 1 (blue), located at coordinates 0 on the X-axis, 0 on the Y-axis, and 0 on the Z-axis. The rotation of the brick is controlled by a matrix transform, which admittedly isn't exactly trivial math. However, arbitrary rotation is relatively rare with Legos, because most bricks have to fit together according to a grid of studs.

Any line starting with a 0 indicates either a comment or metadata. A line starting with 1 indicates the addition of a brick.

You can practice repositioning and rotating a brick in space by adding to your CAD file. A normal brick is 24 LDraw Units (LDU) tall. Therefore, you can "stack" a brick by adjusting its Y-axis position by 24 units. You can rotate a brick by performing a matrix transform.

Try this:


```
0 Name: 1brick.ldr
0 Author: Seth Kenlon

0 clr  x y z  a b c  d e f   g h i  file
1   1  0 0 0  0 0 1  0 1 0  -1 0 0  3001.dat
1   2 0 24 0 -1 0 0  0 1 0   0 0 -1 3001.dat
```

Take a look at it in LDView, and try clicking and dragging across the window to see it from different angles. Notice that I've changed the color of the second brick from 1 (blue) to 2 (green).

![one blue and one green brick][9]

You can move the bricks along any axis, of course. The LDraw specification states that a 1x1 brick is 20 LDU in width and 20 LDU in length, so you can adjust your 2-brick design along the X by incrementing it by 20.


```
0 Name: 1brick.ldr
0 Author: Seth Kenlon

0 clr  x y z  a b c  d e f   g h i  file
1   1  0 0 0  0 0 1  0 1 0  -1 0 0  3001.dat
1   2 0 24 0 -1 0 0  0 1 0   0 0 -1 3001.dat
```

![blue and green bricks linked][10]

### Sequence of bricks

The most common use of LDraw is to demonstrate how to build a model. That implies a sequence of steps, which LDraw represents with the `STEP` metacommand.

To introduce a step in your instructions, add this line:


```
0 STEP
```

In your simple 2-brick sample file, you can add a step between the two bricks:


```
0 Name: 1brick.ldr
0 Author: Seth Kenlon

0 clr  x y z  a b c  d e f   g h i  file
1   1  0 0 0  0 0 1  0 1 0  -1 0 0  3001.dat

0 STEP

1   2 0 24 0 -1 0 0  0 1 0   0 0 -1 3001.dat
```

Your design now has two steps in it; the first displays one brick, and the second displays an additional brick. You can step through your instructions in LDView by clicking the arrows next to the "Steps" label in the top toolbar.

![Steps menu in terminal][11]

You don't have to make a new step with every brick. As with instructions for official Lego sets, you can group several additional bricks into one step, so long as their placement is obvious enough.

There are other command types in LDraw, such as the ability to draw lines to clarify brick placement, and so on. These are documented in the specification.

### Finding a brick part number

I used to keep my Lego collection in fishing tackle boxes so I could find any piece from any set quickly. As my collection grew, however, so did my need for containers, and I suffered a drop in how efficiently I was able to find a brick.

With over 11,000 unique parts, finding digital Lego bricks is equally troublesome. Every official Lego brick has a part number. For instance, the 2x4 brick used in the example CAD file is 3001. If you know a part number, you can use it in your CAD file, and the brick appears.

The LDraw distribution includes the `parts.lst` file, which you can [grep][12] through in search of a specific brick. However, the syntax isn't always consistent, and keywords (is a brick "curved" or "sloped" or "angled?") are sometimes difficult to predict.

However, there are a few online resources that can be useful:

  * [Lugnet][13] is an online Lego user group with a parts reference database constructed from LDraw.
  * [BrickLink][14] is a useful catalog of bricks.
  * [Rebrickable][15] also features an online catalog of bricks.



### Other renderers

Once you've created your masterpiece, LDView can export your model so you can get a high-quality render of it. POVray is a popular open source photo-realistic renderer, so you can get very nice images of your work. You can find POVray in your Linux distribution's repository, or download it from the [POVray website][16].


```
$ povray +I1brick.pov +Q11 +W4196 +H2160 +O1brick-high.png
```

![POVray blue and green brick render][17]

For a renderer dedicated to instructional layout, try the open source [LPub3D][18] project, which displays instructions complete with a brick list for each step.

![LPub 3d blue and green brick render][19]

### Exploring Legos

Building with Legos is fun, and making up your own models is an important part of the creativity it inspires. Your own model designs don't have to be ephemeral anymore, though. You can preserve them by creating your own instructional booklets.

In addition, playing with digital Legos allows you to create virtual Lego models and scenes using any part available, whether you own the part yet or not. You could use digital Legos to make your own animations, your own photos of complex sets, or even to design your very own bricks. There are several online communities, and many of them, like [BrickHub.org][20], post beautiful renders complete with LDraw files.

Whether you like to build models digitally, design bricks of your own, or do something entirely unique, the digital Lego scene is a fun and creative place to visit. Get started today!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/open-source-virtual-lego

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/open-lego.tiff_.png?itok=mQglOhW_ (Open Lego CAD)
[2]: https://ldraw.org
[3]: https://www.ldraw.org/article/218.html
[4]: https://ldraw.org/article/104.html
[5]: http://ldview.sourceforge.net
[6]: https://opensource.com/life/16/2/povray
[7]: https://geany.org
[8]: https://opensource.com/sites/default/files/uploads/1brick_0.jpg (one blue brick)
[9]: https://opensource.com/sites/default/files/uploads/2brick.jpg (one blue and one green brick)
[10]: https://opensource.com/sites/default/files/uploads/2brick-lower.jpg (blue and green bricks linked)
[11]: https://opensource.com/sites/default/files/uploads/steps.jpg (Steps menu in terminal)
[12]: https://opensource.com/article/17/2/command-line-tools-data-analysis-linux
[13]: https://guide.lugnet.com/partsref/
[14]: https://www.bricklink.com/catalogTree.asp?itemType=P
[15]: https://rebrickable.com/parts
[16]: http://www.povray.org/
[17]: https://opensource.com/sites/default/files/uploads/povray-brick.jpg (POVray blue and green brick render)
[18]: https://sourceforge.net/projects/lpub3d/
[19]: https://opensource.com/sites/default/files/uploads/lpub3d.png (LPub 3d blue and green brick render)
[20]: https://brickhub.org
