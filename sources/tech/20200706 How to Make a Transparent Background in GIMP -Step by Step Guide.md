[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Make a Transparent Background in GIMP [Step by Step Guide])
[#]: via: (https://itsfoss.com/remove-image-background-gimp/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

How to Make a Transparent Background in GIMP [Step by Step Guide]
======

Removing the background is one of the most used graphic design procedures. There could be many reasons why you would want to do that.

For example, you don’t like the background, you want to add the image to another background, or you simply want to make the image transparent.

When you make the image background transparent, you can use the colour according to the background of the new image. If you put a transparent image on top of a blue image, the image will now have a blue background. This is quite handy in graphic designing.

You can use [GIMP][1] to remove the background from an image. I am going to show you how to do that step-by-step in this GIMP tutorial.

### How to Make a Transparent Background in GIMP

![][2]

#### Step 1: Open up the image as a layer

As I have mentioned before, you need to get used to isolate different images and actions as layers. This tutorial is so simple that if you just open your image, it will still be fine. Although I want to maintain a good habit and open my image as following.

**File -&gt; Open as Layers**

![Open As Layers][3]

#### Step 2: Use the Fuzzy select tool

The Fuzzy Select tool is designed to select areas of the current layer or image based on colour similarity. This tool will help us to select the unwanted background with one click.

![][4]

#### Step 3: Add Transparency

An alpha channel is automatically added into the Channel Dialog as soon as you add a second layer to your image. It represents the transparency of the image.

If your image has only one layer (like our example), this background layer has no Alpha channel. In this case, to Add an Alpha channel.

**Layer -&gt; Transparency -&gt; Add Alpha Channel**

![][5]

#### Step 4: Delete the background

Press the Delete keyboard button to remove the background.

If you have other different coloured regions that you need to remove, click on them and delete them.

**You might have to repeat the steps 2 to step 4 if necessary**. I have to remove the blue background in this example.

![][6]

#### Step 5: Export the image

To export the image go to File -&gt; Export As, choose PNG file format and click on Export. All done!

![][7]

#### Did it work for you?

I took a simple example in this case. If your image background has lots of colors, you may have to repeat step 2 to step 4, deleting each color one by one.

This was another tutorial in our GIMP series to help you accomplish common editing image editing tasks. We, at It’s FOSS, will be sharing more such tutorials. Stay tuned and [do subscribe to our weekly newsletter][8].

--------------------------------------------------------------------------------

via: https://itsfoss.com/remove-image-background-gimp/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/gimp-2-10-release/
[2]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/remove-background-gimp.jpg?ssl=1
[3]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/06/open-as-layers.png?ssl=1
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/06/fuzzy-select-tool.png?ssl=1
[5]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/06/add-alpha-channel.png?ssl=1
[6]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/06/delete.png?ssl=1
[7]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/06/Its_FOSS_transparent.png?ssl=1
[8]: https://itsfoss.com/subscribe-to-newsletter/
