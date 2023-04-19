[#]: subject: "New playground: integer.exposed"
[#]: via: "https://jvns.ca/blog/2023/04/19/new-playground-integer-exposed/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

New playground: integer.exposed
======

Hello! For the last few months we’ve been working on a zine about how integers and floating point numbers work. Whenever I make a zine I like to release a playground to go with it, like [mess with dns][1] for the DNS zine or the [sql playground][2].

For this one, I made a simple playground called [integer.exposed][3], inspired by Bartosz Ciechanowski’s [float.exposed][4].

It’s a lot less elaborate than Mess With DNS, so I’ll keep this blog post short.

### the inspiration: float.exposed

I did a couple of talks about how integers and floating point work last month, and in the talk about floating point I found myself CONSTANTLY referring to this site called [Float Exposed][5] by Bartosz Ciechanowski to demonstrate various things. (Aside: If you haven’t seen Ciechanowski’s incredible [interactive explainers][6] on bicycles, mechanical watches, lenses, the internal combustion engine, and more, you should check them out!)

Here’s what it it looks like:

![][7]

Things I’ve done with it:

  * Increment the significand of a float (to show people how close together successive floats are)
  * Show special values like [NaN][8] and [infinity][9], and show how if you change the bits in NaN, it’s still NaN
  * Go to a [large integer value][10] and show how the distance between floats is very large
  * Show how you get drastically different precision for [one million as a 32-bit float][11] and as a [64-bit float][12] (try incrementing the significand for each one!)



and lots more! It’s an incredible way to get hands on with floats and improve your intuition around how they work.

### float.exposed, but for integers

Integers aren’t as complicated as floats, but there are some nonobvious things about them: you have signed integers and unsigned integers, you have endianness, and there are some weird operations like right/left shift. So when I was talking about integers, I found myself wanting a similar website to [float.exposed][4] to demonstrate things.

So with permission, I put one together at [integer.exposed][3]. Here’s a screenshot:

![][13]

The UI is a little different: integers don’t have many different parts the way floating point numbers do, so there’s a single row of buttons that you can use to do various operations on the integer.

A note on byte order: Like float.exposed, it uses a big endian byte order, because I think it’s more intuitive to read. But you do have to keep in mind that on most computers the bytes will actually be in the reverse order.

### some interesting things to try

Here are some things I think are fun to try:

  1. **signed integers** : Look at how [-1][14] is represented. Increment and decrement it a few times and see how the signed and unsigned values change. Do the same with [-128][15]. Also look at how -1 is represented as a 16/32/64-bit integer.
  2. **signed/unsigned right shift** : Similarly with [-1][16]: try out signed right shift (also known as “arithmetic right shift”) and see how the result is different from unsigned right shift (aka “logical right shift”).
  3. **counting in binary** : Start at [0][17] and increment a bunch of times and watch the binary value count up.
  4. **not** : Take any number (like [123][18]) and NOT it. See how `NOT` is almost exactly the same as negation, but not quite.
  5. **swap the byte order**. Take a number like [12345678][19] and see how if you swap the byte order, the result is an unrecognizably different number.
  6. look at how [powers of 2 are represented][20]



### the tech stack

As usual for me it uses Vue.js. If you want to see how it works you can just view source – it’s only two files, `index.html` and `script.js`.

I took a bunch of the CSS from [float.exposed][4].

### that’s all!

Let me know if you notice any bugs! I might add more features, but I want to keep it pretty simple.

I’ve also built another more involved playground that I’m hoping to release and write up soon.

--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2023/04/19/new-playground-integer-exposed/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://messwithdns.net/
[2]: https://sql-playground.wizardzines.com/
[3]: https://integer.exposed
[4]: https://float.exposed
[5]: https://float.exposed/
[6]: https://ciechanow.ski/archives/
[7]: https://jvns.ca/images/float-exposed.png
[8]: https://float.exposed/0x7ff8000000000000
[9]: https://float.exposed/0x7ff0000000000000
[10]: https://float.exposed/0x43abc16d674ec801
[11]: https://float.exposed/0x4b189680
[12]: https://float.exposed/0x416312d000000000
[13]: https://jvns.ca/images/int-exposed.png
[14]: https://integer.exposed/#0xff
[15]: https://integer.exposed/#0x80
[16]: https://integer.exposed/#0xffff
[17]: https://integer.exposed/#0x00
[18]: https://integer.exposed/#0x7b
[19]: https://integer.exposed/#0x4e61bc00
[20]: https://integer.exposed/#0x00000800
