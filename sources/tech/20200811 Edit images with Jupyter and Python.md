[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Edit images with Jupyter and Python)
[#]: via: (https://opensource.com/article/20/8/edit-images-python)
[#]: author: (Moshe Zadka https://opensource.com/users/moshez)

Edit images with Jupyter and Python
======
Who needs to learn an image-editing application when you can do the job
with open source tools you already know?
![Polaroids and palm trees][1]

Recently, my kid wanted to make a coloring page from a favorite cartoon. My first thought was to use one of the open source programs on Linux that manipulate images, but then I remembered I have no idea how to use any of them. Luckily, I know how to use Jupyter and [Python][2].

How hard can it be, I figured, to use Jupyter for that?

To follow along, you need to have a modern version of Python (if you're a macOS user, you can follow this [guide][3]), then install and open Jupyter Labs, which you can learn more about [here][4], and [Pillow][5], a friendly fork of the Python Imaging Library (PIL), with:


```
$ python -V
Python 3.8.5
$ pip install jupyterlab pillow
# Installation process ommitted
$ jupyter lab
```

Imagine you want to make a coloring page with an image of a deer. The first step is probably to download a picture of a deer and save it locally. Beware of images with dubious copyright status; it's best to use something with a [Creative Commons][6] or other open access license. For this example, I used an openly licensed image from [Unsplash][7] and named it `deer.jpg`.

Once you're in Jupyter Lab, start by importing `PIL`:


```
`from PIL import Image`
```

With these preliminaries out of the way, open the image then look at the image size:


```
`pic = Image.open("deer.jpg")`[/code] [code]`pic.size`[/code] [code]`(3561, 5342)`
```

Wow, this is a bit of sticker shock—high-resolution pictures are fine if you want to make a delightful book about deer, but this is probably too big for a homemade coloring book page. Scale it waaaaaaay down. (This kindness is important so that this article loads fast in your browser, too!)


```
x, y = pic.size
x //= 10
y //= 10
smaller = pic.resize((x, y))
```

This reduced the scale of the image by 10. See what that looks like:


```
`smaller`
```

![Full-color deer image][8]

(Max Saeling, [Unsplash License][7])

Beautiful! Majestic and remote, this deer should be a breeze for an edge-detection algorithm. Speaking of which, yes, that's the next step. You want to clean up the image so coloring will be is a breeze, and thankfully there's an algorithm for that. Do some edge detection:


```
from PIL import ImageFilter

edges = smaller.filter(ImageFilter.FIND_EDGES)

[/code] [code]`edges`
```

![Deer image reduced by 10][9]

(Moshe Zadka, [CC BY-SA 4.0][10])

This is probably the most important step. It removes all the extraneous details and leaves clear lines. The color is a little weird, but this is not a hard problem to solve. Split the image into its color bands, and choose the one where the lines are crispest:


```
`bands = edges.split()`[/code] [code]`bands[0]`
```

![Deer image with edge detection][11]

(Moshe Zadka, [CC BY-SA 4.0][10])

The lines are clear now, but this is not a good image to print because your printer will run out of ink, and your kid will not be happy coloring on black. So invert the colors. While you're at it, snap the colors to max-black or max-white to make the lines even crisper by using a [lambda function call][12]:


```
`outline = bands[0].point(lambda x: 255 if x<100 else 0)`[/code] [code]`outline`
```

![Deer image split into color bands][13]

(Moshe Zadka, [CC BY-SA 4.0][10])

The original image had a lot of nature that I mercilessly cleared. Now there's a lot of empty space, so crop the picture to the essentials:


```
`outline.crop((10, 200, 300, 400))`
```

![Deer image cropped for coloring page][14]

(Moshe Zadka, [CC BY-SA 4.0][10])

All that's left is to save the picture as something easy to print, like a PDF:


```
`outline.save("deer.pdf")`
```

I'll let you figure out how to [print from Linux][15].

Have fun making homemade coloring books for your kids!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/edit-images-python

作者：[Moshe Zadka][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/moshez
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/design_photo_art_polaroids.png?itok=SqPLgWxJ (Polaroids and palm trees)
[2]: https://opensource.com/resources/python
[3]: https://opensource.com/article/19/5/python-3-default-mac
[4]: https://opensource.com/article/19/5/jupyterlab-python-developers-magic
[5]: https://pillow.readthedocs.io/en/stable/installation.html
[6]: https://creativecommons.org/
[7]: https://unsplash.com/photos/Xu1xO3mpr1I
[8]: https://opensource.com/sites/default/files/images/jupyter-image_7_0.png (Full-color deer image)
[9]: https://opensource.com/sites/default/files/uploads/jupyter-image_10_0.png (Deer image reduced by 10)
[10]: https://creativecommons.org/licenses/by-sa/4.0/
[11]: https://opensource.com/sites/default/files/uploads/jupyter-image_13_0.png (Deer image with edge detection)
[12]: https://opensource.com/article/19/10/python-programming-paradigms
[13]: https://opensource.com/sites/default/files/uploads/jupyter-image_16_0.png (Deer image split into color bands)
[14]: https://opensource.com/sites/default/files/uploads/jupyter-image_18_0.png (Deer image cropped for coloring page)
[15]: https://opensource.com/article/18/11/choosing-printer-linux
