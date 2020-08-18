[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (The surprising thing you can do in the D programming language)
[#]: via: (https://opensource.com/article/20/8/nesting-d)
[#]: author: (Lawrence Aberba https://opensource.com/users/aberba)

The surprising thing you can do in the D programming language
======
Nesting makes it easier for collaborators to understand a codebase. Here
is an example of nesting in D to create clean, reusable code.
![Bird nest in nature][1]

Software development can be a very complex process. As the code you write increases in size and complexity, it is important to keep it readable and easy to understand. In [open source software][2] development, many people collaborate on code with several interconnected and, quite often, frequently moving parts. This can make it hard for potential contributors to understand the codebases.

The effort required to wrap your head around a codebase may have a direct impact on contributions, as a lot of people have a limited window for contributing, many doing it in their free time. This makes it essential for a codebase to be easy to understand for both seasoned and new contributors.

### The problem of complexity

Consider the example of a function that implements an algorithm to bake bread called `bakeBread`. Baking bread involves several steps, so it is helpful to break the code into multiple helper functions:


```
string bakeBread()
{
        mixIngredients();
        kneadDough();
        riseDough();
        punchDough();
        riseDough();
        bakeInOven();
}

void mixIngredients() { /* code here */ }

void kneadDough() { /* code here */ }

void riseDough() { /* code here */ }

void punchDough() { /* code here */ }

void bakeInOven() { /* code here */ }
```

As you can see from the sample code above, baking bread is quite a process, and implementing it in multiple functions breaks the problem down into easy-to-understand steps. However, one downside to this approach is there are several functions outside `bakeBread` that are used only within that function.

### Nesting to the rescue

[Nesting][3] helps alleviate some of this complexity in terms of how to structure code. It enables all the functions above to be declared _within_ the scope of `bakeBread` where they are used:


```
string bakeBread()
{
        mixIngredients();
        kneadDough();
        riseDough();
        punchDough();
        riseDough();
        bakeInOven();

        void mixIngredients() { /* code here */ }

        void kneadDough() { /* code here */ }

        void riseDough() { /* code here */ }

        void punchDough() { /* code here */ }

        void bakeInOven() { /* code here */ }
}
```

Nesting helps clean up the code by providing a form of [encapsulation][4]. The functions are defined where they are used without cluttering the global scope. This also prevents name collisions with other functions that use the same name without resorting to strange function names to differentiate them. Nesting also helps collaborators easily identify where functions are defined, how they are used, and how to make improvements quickly.

### Powerful nesting in D

[Nesting in D][5] goes beyond functions. You can nest [classes][6] within classes, [structs][7] within structs, structs within classes, and classes within structs, and even import [modules][8] locally within functions or any other scope. This concept is dubbed "[turtles all the way down][9]."

If the `bakeBread` example (or any of its now-nested functions) needs to import an external module, it can be imported within its scope where it's being used:


```
string bakeBread()
{
        import std.stdio: writeln;

        void mixIngredients() {
                import std.array: split;

                // more code here
        }
       
        /* the rest of code which may include
        * functions, classes or structs goes here
        */
}
```

This makes it easy to keep track of where things are coming from and to prevent name clashes with symbols (functions, classes, structs, etc.) from different modules with the same name. A function implemented like this can be moved around during refactoring without breaking code because it does not depend on any globally imported module. This minimizes the amount of work required to make major changes to a large codebase—which is a good thing for collaborative development.

### Time to try D

D is a great language for development. It's easy to [install a D compiler][10], write some example code, and [run it][11] to experience D for yourself. You can also run your code in the [online D editor][12]. The book [_Programming in D_][13] by Ali Çehreli provides a great introduction to D and offers a free online version.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/nesting-d

作者：[Lawrence Aberba][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/aberba
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/bird-nest-nature-luke-brugger-unsplash.jpg?itok=wKhYcqeZ (Bird nest in nature)
[2]: https://opensource.com/resources/what-open-source
[3]: https://en.wikipedia.org/wiki/Nested_function
[4]: https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)
[5]: http://ddili.org/ders/d.en/nested.html
[6]: http://ddili.org/ders/d.en/class.html
[7]: http://ddili.org/ders/d.en/struct.html
[8]: http://ddili.org/ders/d.en/modules.html
[9]: https://en.wikipedia.org/wiki/Turtles_all_the_way_down
[10]: https://tour.dlang.org/tour/en/welcome/install-d-locally
[11]: https://tour.dlang.org/tour/en/welcome/run-d-program-locally
[12]: https://run.dlang.io/
[13]: http://ddili.org/ders/d.en/
