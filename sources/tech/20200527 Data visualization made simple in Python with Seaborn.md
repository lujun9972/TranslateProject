[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Data visualization made simple in Python with Seaborn)
[#]: via: (https://opensource.com/article/20/5/seaborn-python)
[#]: author: (Shaun Taylor-Morgan https://opensource.com/users/shaun-taylor-morgan)

Data visualization made simple in Python with Seaborn
======
Seaborn makes complicated things uncomplicated by giving you a range of
plot types that "just work."
![Analytics: Charts and Graphs][1]

Plotting in Seaborn is much simpler than in [Matplotlib][2]. While Matplotlib makes the hard things possible, [Seaborn][3] makes complicated things uncomplicated by giving you a range of plot types that "just work."

### A one-liner… almost

In this series, I'm [comparing Python plotting libraries][4] by making the same plot in each one. It's a multi-group bar plot of UK election results.

Here's how to create this multi-group bar plot in Seaborn:


```
    ax = sns.barplot(
        data=df,
        x="year",
        y="seats",
        hue="party",
        palette=['blue', 'red', 'yellow', 'grey'],
        saturation=0.6,
    )
```

The result:

![A multi-bar plot, with \(almost\) one line of Python.][5]

A multi-bar plot, with (almost) one line of Python. (© 2019 [Anvil][6])

Seaborn has such a simple interface because it doesn't require you to manipulate your data structure in order to define how your plot looks. Instead, you get your data into [Long Form][7], and then your data manipulation is done. All you need to do is tell Seaborn which aspects of the plot to map to which variables in your data.

If you want to encode the `party` variable in the `hue` of the bars, specify:


```
`hue="party"`
```

and if you want to encode the `year` variable as position on the X-axis, specify:


```
`x="year"`
```

The way that Seaborn deals with colors is really interesting. You can specify colors using human-readable color names. I used red, blue, yellow, and grey, but you can also use colors like ugly green, dull blue, and electric purple. These are mapped to a [crowdsourced library of color-name definitions][8] created by XKCD author Randall Munroe.

![Just a few of the uncannily accurate XKCD color names][9]

Just a few of the uncannily accurate XKCD color names (© 2019 [Anvil][6])

For completeness, I must mention that there are a couple of lines of boilerplate to run before the plot statement:


```
    # A couple of lines of boilerplate
    sns.set()
    plt.figure()
```

You have to import the library and your data, of course:


```
    # Import Matplotlib and Seaborn
    import matplotlib.pyplot as plt
    import seaborn as sns

    # Import the data in Long Form so that we can treat each variable separately
    from votes import long as df
```

And since this is a wrapper around Matplotlib, you still need to cast the Matplotlib plotting spell at the end:


```
`    plt.show()`
```

### No compromise

OK, so I have this really beautiful interface that makes common plots really simple. But doesn't that take away my power? Luckily, that's not the case. Seaborn is the good kind of abstraction—it makes the common cases ridiculously easy, but it also gives you access to lower levels of abstraction. Just like Anvil, Seaborn gives you "[escape hatches][10]" to use the underlying layers when you need them.

When I called `sns.barplot`, it returned the Matplotlib `Axis` object for that plot. I can use this to add a title and grid and tweak the axis labels, just as I did in Matplotlib:


```
    ax.set_title('UK election results')

    ax.grid(color='#cccccc')

    ax.set_ylabel('Seats')
    ax.set_xlabel(None)
    ax.set_xticklabels(df["year"].unique().astype(str), rotation='vertical')
```

Here's the result:

![Seaborn plot, now with Matplotlib tweaks][11]

Seaborn plot, now with Matplotlib tweaks (© 2019 [Anvil][6])

You can copy this example as an Anvil app [here][12] (Note: Anvil requires registration to use).

### Next: Dynamic plots in client-side Python

Seaborn is one of my favorite plotting libraries, thanks to this combination of simplicity and power. But it produces static images, and if you're using them on the web, you might want a little more interactivity.

Next time, I'll look at [Plotly][13], which allows you to create dynamic plots in the browser, with a Python interface over a JavaScript core.

* * *

_This article is based on [How to make plots using Seaborn][6] on Anvil's blog and is reused with permission._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/5/seaborn-python

作者：[Shaun Taylor-Morgan][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/shaun-taylor-morgan
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/analytics-graphs-charts.png?itok=sersoqbV (Analytics: Charts and Graphs)
[2]: https://opensource.com/article/20/5/matplotlib-python
[3]: https://seaborn.pydata.org/
[4]: https://opensource.com/article/20/4/plot-data-python
[5]: https://opensource.com/sites/default/files/uploads/seaborn_0.png (A multi-bar plot, with (almost) one line of Python.)
[6]: https://anvil.works/blog/plotting-in-seaborn
[7]: https://anvil.works/blog/tidy-data
[8]: https://xkcd.com/color/rgb/
[9]: https://opensource.com/sites/default/files/uploads/xkcd-colors.png (Just a few of the uncannily accurate XKCD color names)
[10]: https://anvil.works/blog/escape-hatches-and-ejector-seats
[11]: https://opensource.com/sites/default/files/uploads/seaborn-tweaked.png (Seaborn plot, now with Matplotlib tweaks)
[12]: https://anvil.works/build#clone:JRCSWZ2NSXMX5H6D%3dLMZQ6T3E6ZKJQOI25BHBQIM5
[13]: https://plotly.com/
