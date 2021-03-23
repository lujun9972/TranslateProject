[#]: subject: (Start programming in Deno, an alternative to Node.js)
[#]: via: (https://opensource.com/article/21/3/deno-programming)
[#]: author: (Bryant Son https://opensource.com/users/brson)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

Start programming in Deno, an alternative to Node.js
======
Get to know Deno's CLI, permissions, and how to write a Hello World
program.
![Woman sitting in front of her laptop][1]

[Deno][2] is a simple, modern, and secure runtime for JavaScript and TypeScript. It is an open source project created by Ryan Dahl, who developed Node.js. In [_Try Deno as an alternative to Node.js_][3], I introduced Deno's features and explained how to install and run it.

Here, I will help you quickly get started with Deno by explaining:

  * Deno's command-line interface (CLI)
  * Permissions in Deno
  * Hello World in Deno



### Deno's CLI

Deno is a command-line program, and mastering its CLI can help you use its features. For example, you can type `deno help` to see all the help options from 25,000 feet.

![Deno's CLI][4]

(Bryant Son, [CC BY-SA 4.0][5])

Watch this video to learn more about the tricks that Deno's CLI can do:

### Permissions in Deno

When Ryan Dahl created Node.js, it proved to be wildly popular among not only web developers but programmers from many industries and hobbies. However, there are critiques about its security model. Ryan has designed Deno with security in mind, so a Deno module does not have file, network, or environment access unless you specifically enable it.

For example, in the following script, `hello-deno.js` is given only `allow-read` access:


```
`deno run --allow-read hello-deno.ts`
```

Permission might not be an easy subject to grasp, but Deno makes it simpler. If you are interested in learning more about how Deno handles permissions, please watch this video.

### Say "Hello, World" in Deno

When learning a new programming language, it's common to start by writing a "hello, world" program. Here's how to do that in Deno.

Deno supports JavaScript and TypeScript. In JavaScript, create a file named `hello-world.js` with:


```
/**
 * hello-world.js
 */

console.log("Hello, World");
```

In TypeScript, the file contents will be exactly the same, but the file has a different extension.


```
/**
 * hello-world.ts
 */

console.log("Hello, World");
```

However, as the script gets more complicated, you will begin to see some differences. This video offers a more complex example of how you can say "hello, world" in Deno:

That's it for now! I'll share more articles covering more advanced Deno uses on Opensource.com in the future.

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/3/deno-programming

作者：[Bryant Son][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/brson
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/OSDC_women_computing_4.png?itok=VGZO8CxT (Woman sitting in front of her laptop)
[2]: https://deno.land/
[3]: https://opensource.com/article/21/2/deno
[4]: https://opensource.com/sites/default/files/uploads/1_denocommand.jpg (Deno's CLI)
[5]: https://creativecommons.org/licenses/by-sa/4.0/
