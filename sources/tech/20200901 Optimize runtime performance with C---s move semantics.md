[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Optimize runtime performance with C++'s move semantics)
[#]: via: (https://opensource.com/article/20/9/optimizing-runtime-performance)
[#]: author: (Stephan Avenwedde https://opensource.com/users/hansic99)

Optimize runtime performance with C++'s move semantics
======
Reducing copy operations is a good way to increase runtime execution
speed for performance-critical applications.
![woman on laptop sitting at the window][1]

If you are allowed to choose which programming language to use for an application, you usually pick one you know and that offers the shortest path to your goal. If you require a high runtime speed, programming languages that compile directly to machine code— like C++—are your best option.

In modern applications, the back and forth of memory addresses, jumps, loops, and the (sometimes unnecessary) copying of data areas consumes a huge share of machine code. In this article, I'll highlight the C++ `move` semantics, which enable you to avoid unnecessarily copying processes. Even if you are not a programmer, you can still analyze memory allocations with the `valgrind` heap profiler `massif`.

### Code: rvalues and lvalues

In C++ programming you have to deal with `lvalues` and `rvalues`. In the example below, `a` is on the left side of the assignment operator `=` so it is an `lvalue`. The assigned value of `5` is on the right side, so it is the `rvalue`.


```
a = 5;
```

When this line is compiled, the `lvalue` is interpreted as a symbolic address which can be altered afterwards. The `rvalue` is a pure hardcoded value. It cannot be accessed by subsequent code because `rvalues` don’t have an address. If you can determine an expression’s address or, if the compiler allows it, it is an `lvalue`. That is, if an expression survives the semicolon at the end of a line, it is an `lvalue`; otherwise, it’s an `rvalue`.

An `lvalue` can be present on the left and right side. An `rvalue` only in the right side.


```
a = 5;
b = a;
```

Since C++11, the move semantic and the possibility to deal with rvalue references found its way into the standard.
Rvalue references are marked with a double ampersand `&&`. They allows to interpret an `lvalue` as a `rvalue`. Especially when creating objects, the use of `rvalue` references can increase performance, as we will see in the example code.

There are a lot of articles in the web which cover the syntax and the correct usage. The [Chromium Project Documentation][2] offers a good introduction to the subject. In this article we will use an example to reveal the actual impact on performance.


```
`git clone https://github.com/hANSIc99/optimizing_cpp_sample.git`
```

### The default behavior

Imagine you have a class called `MyObject` that takes another class, `MyType`, as an argument in its constructor. In order to create an instance of `MyObject`, an instance of `MyType` has to be created in advance.

In code, it looks like this (`main.cpp` line 16):


```
MyType&lt;double&gt; type_1(container);
MyObject&lt;MyType&lt;double&gt; &gt; object_1(type_1);
```

`MyType` is a template class that expects a double vector in its constructor (you do not need to be concerned about this property). `MyObject`, also a template class, takes an instance of `MyType (type_1)` in its constructor.

Using `MyObject`:

  1. Invokes the constructor of `MyType` to create an instance (`type_1`)
  2. Invokes the copy constructor of `MyType` (makes a copy of `type_1`)
  3. Invokes the constructor of `MyObject` (takes the copy of `type_1` as an argument)
  4. (… do some work with **object_1** … )
  5. Invokes the destructor of `type_1`
  6. Invokes the destructor of `object_1`, which causes it to invoke the destructor of the copy of `type_1`



If the instance of `MyType` (`type_1`) exists only to create the instance of `MyObject` (`object_1`), a lot of unnecessary code will be executed.

You can try it yourself: change the directory and invoke `make`:


```
cd optimizing_cpp_sample
make CFLAGS=-DOPT1
```

After it compiles, invoke the sample program:


```
` ./memory_sample`
```

You should now see trace messages of the different constructor types:


```
MyType::MyType() contructor called
MyType::MyType(const MyType&amp;) copy constructor called
MyObject::MyObject(const T&amp; mytype) constructor called
MyType::m_data contains 32767 elements
MyType::~MyType() destructor called
MyType::~MyType() destructor called
```

### Optimizing the example

Clean the binaries, invoke `make` with different arguments, and run the program again:


```
make clean
make CFLAGS=-DOPT2
./memory_sample
```

This time, the constructors' trace messages look a bit different:


```
MyType::MyType() contructor called
MyType::MyType(MyType&amp;&amp; other) move constructor called
MyObject::MyObject(T&amp;&amp; mytype) constructor with move called
MyType::~MyType() destructor called
MyType::m_data contains 32767 elements
MyType::~MyType() destructor called
```

Instead of invoking the `MyType` copy constructor, it calls the `move` constructor, and the `MyType` destructor is called only once. As you will see below, this has a positive impact on the runtime performance.

Look at `main.cpp` line 23 in the code. It shows that `object_2` is directly created with the argument that should have been passed to the constructor of `MyType`:


```
`MyObject<MyType<double> > object_2(container);`
```

That's it: just one line invokes `MyObject`'s constructor with the arguments for `MyType`'s constructor. The compiler detects there is no need to keep an instance of `MyType` in memory. Instead of making another copy, it sets the internal pointer to an instance of `MyType` inside `object_2` to the previously created instance.

### Move with care

Using the `move` semantic requires a certain amount of caution. Run the program again:


```
make clean
make CFLAGS=-DOPT3
./memory_sample
```

The program crashes immediately:


```
MyType::MyType() contructor called.
MyType::MyType(MyType&amp;&amp; other) move constructor called
MyType::m_data contains 3 elements
Segmentation fault (core dumped)
```

What happened? Open `main.cpp` and move to line 27:


```
void case_3(){
                               
    MyType&lt;double&gt; type_3({1.2, 3.4, 5.6});
    MyObject&lt;MyType&lt;double&gt; &gt;  object_3(std::move(type_3));
    object_3.m_mytype.print();
    /* Dangerous: std::move destroys the object */
    type_3.print();
}
```

This forces using the `move` constructor to initialize `object_3` (line 30) by using `std::move` when passing `type_3` as an argument.

After moving `type_3` into `object_3`, you cannot refer to `type_3` (because you moved it). The object is destroyed and cannot be used again.

### Measuring performance impact

You may have noticed that the execution time is displayed in the output. While you won't see any effect on a single invocation (like in the examples above), there is a noticeable improvement when you run your code in an infinite loop.

#### Without a move constructor:


```
make clean
make CFLAGS=-DOPT4
./memory_sample
```

On my system, execution takes an average of 170ms:


```
Average time: 170ms - Last execution took: 160um
Average time: 170ms - Last execution took: 179um
Average time: 170ms - Last execution took: 162um
```

#### With a move constructor:


```
make clean
make CFLAGS=-DOPT5
./memory_sample
```

This time, it takes an average of 143ms to execute:


```
Average time: 143ms - Last execution took: 142um
Average time: 143ms - Last execution took: 138um
Average time: 143ms - Last execution took: 142um
```

This (constructed) example achieves a 16% reduction in runtime. Note that compiler optimizations are switched off (`-O0`). With a higher degree of optimization (`-O3`), runtime reduction would be less significant (11%).

### Analyzing memory allocations

The first choice for analyzing memory allocations on Linux-based systems is the tool `valgrind`, or to be precise, the [heap profiler `massif`][3]. In this case, executing the copy constructor causes heap memory allocations.

Run `massif` on the first example:


```
$ make clean
$ make CFLAGS=-DOPT1
$ valgrind --tool=massif ./memory_sample
```

This outputs a file called `massif.out` with a trailing process ID. This file can be read with `ms_print`:


```
`ms_print massif.out.4781`
```

It prints out a graph of memory allocation over time:

![Graph showing memory allocations over time][4]

(Stephan Avenwedde, [CC BY-SA 4.0][5])

This graph shows increasing memory allocation over time. This is consistent with the implementation. The ouput of `ms_print` also includes information about which lines of code caused the memory allocation. I won't go into detail on how to read the output because there is [excellent documentation][3] available.

### Conclusion

Regardless of the programming language you use, reducing copy operations (which results in heap memory allocations in this example) is a good way to increase runtime execution speed for performance-critical applications. When using C++, you will need a couple of prerequisites to apply these optimizations:

  * C++11, since the `move` semantics have only been available since that release
  * Availability of the `move` constructor/`move` assignment operator (see the [rule of 5][6])



On a modern x86-64 CPU, heap memory allocations are so fast you won't notice whether an application is optimized or not without precise measurement. The less powerful your CPU, the more it makes sense to optimize runtime code. For example, on mobile devices, not only can it improve the response behavior, but it can also extend battery life.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/optimizing-runtime-performance

作者：[Stephan Avenwedde][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/hansic99
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/lenovo-thinkpad-laptop-window-focus.png?itok=g0xPm2kD (young woman working on a laptop)
[2]: https://www.chromium.org/rvalue-references
[3]: https://valgrind.org/docs/manual/ms-manual.html
[4]: https://opensource.com/sites/default/files/uploads/ms_print_opt_1.png (Graph showing memory allocations over time)
[5]: https://creativecommons.org/licenses/by-sa/4.0/
[6]: https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)#Rule_of_Five
