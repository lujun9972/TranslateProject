[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Open source cross-platform development with TotalCross)
[#]: via: (https://opensource.com/article/20/7/totalcross-cross-platform-development)
[#]: author: (Bruno Muniz https://opensource.com/users/brunoamuniz)

Open source cross-platform development with TotalCross
======
Opinions to the contrary, TotalCross Virtual Machine is not another Java
Virtual Machine.
![Person drinking a hot drink at the computer][1]

There's a question that pops up quite frequently at [TotalCross][2]—in our day-to-day work, after presentations, in Reddit discussions, and sometimes even in our Telegram channel. Let's answer it once and for all: _No, TotalCross Virtual Machine is not another Java Virtual Machine_. This article explains the differences between the two, how TotalCross interacts with Java, and how to know which is best for your application.

### A bit of history

TotalCross Virtual Machine (TCVM) was conceived by Guilherme Hazan, who also created one of the first cross-platform tools in the world, [SuperWaba][3], before he started working on TotalCross. Fabio Sobral joined the team to start the TotalCross SDK, an ambitious project to create a cross-platform tool to run applications with maximum performance even on low-computing power devices (including the ones with only 32MB RAM and 312MHz CPUs that were common at the time).

### TotalCross' goals

During development, the project had three main goals:

  1. Optimize the most used Java bytecodes
  2. Write a register-based VM
  3. Build an easy-to-use API to create applications



#### Optimizing the most used Java bytecodes

While studying for his Master's degree, Guilherme realized that some of the most used bytecodes could be optimized to reduce the number of operations the VM executes. That optimization could also reduce the size of the compiled package (up to 39% compared to Java). This led to the birth of TotalCross' bytecode, which still runs in every app made with TotalCross. If you want to know more about TotalCross' bytecode, take a look at [Guilherme's thesis][4].

#### Writing a register-based VM

The second challenge was to write a VM in C that executed compiled bytecodes better, especially in low-computing power devices.

Java Virtual Machine (JVM) uses a stack-based approach, which uses a stack data structure to store operands. Operations are carried out by popping data from the stack, processing it, and pushing back the results. In this architecture, the simple operation of adding two numbers requires executing four instructions.

In contrast, TCVM uses a register-based architecture, which resembles the architecture used by most hardware, where the operands are stored in a structure based on the registers of the CPU. This architecture is more complex to code than a stack-based architecture, as the instructions must address the operands directly instead of just popping the last operand from the stack. However, adding two numbers is performed in a single instruction (vs. four), saving CPU cycles and resulting in a smaller bytecode.

![TCVM vs JVM comparison][5]

(Bruno Muniz, [CC BY-SA 4.0][6])

Two other differences between JVM and TCVM are arrays and the native interface.

##### Arrays

Arrays in Java are not necessarily mapped to a single, contiguous memory space. To use a native function that requires a contiguous memory space (such read or write I/O functions), the programmer must allocate a second memory space for the Java heap, lock the array object, and then copy data to/from both structures. That's a lot of steps and memory juggling for I/O operations.

To address this, Java added [ByteBuffer][7], which can encapsulate a Java array or a direct pointer to off-heap memory. This solution greatly reduces the overhead of using primitive arrays but still requires a lot of structure management and is often a source of trouble for less seasoned developers. Adding this structure has no effect on previous implementations that relied on primitive arrays.

In TotalCross, arrays are _always_ contiguous, which means native code can directly access and use Java primitive arrays with no extra steps required.

##### TotalCross Native Interface

In TotalCross, native code is written using the TotalCross Native Interface (TCNI), which binds a Java method to a function implemented in native code. It may look similar to Java's JNI at first glance, but its implementation is quite different.

In Java, handling objects can be troublesome. The programmer has to handle a lot of locks to make sure objects are not moved around or broken when they're accessed natively.

In TotalCross, objects can be directly accessed using memory addresses most of the time, with no locks or memory searches required.

#### Building an easy-to-use API to create applications

Finally, to allow developers to build nice applications, Fabio and Guilherme needed to provide an API of components, and the obvious choice was to use Java. Java is still one of the most popular programming languages among developers, and even though the TCVM is not a JVM, using Java brings many benefits, like code interoperability between applications running on the JVM, a large number of design patterns available, and more.

They decided to use a subset of the Java SDK and write all the UI components from scratch because [Swing and AWT][8] didn't have massive adoption. Thus, the TotalCross API was born.

### How TotalCross works in practice

![TotalCross architecture][9]

(Bruno Muniz, [CC BY-SA 4.0][6])

To explain the relationship of Java, the Java Development Kit (JDK), and JVM to TotalCross, I'll divide the process into two main stages: development and runtime.

In the development stage, a developer needs the TotalCross API (`tc.jar`) with a JDK to write the application's source code and to compile the code into Java bytecode. Any other language supported by the JVM can be used, as they are already converted to Java bytecode.

To convert from Java bytecode to TotalCross bytecode, the developer must use a class called `tc.Deploy` (TC converter), which translates from one bytecode to the other (there are several ways to use this class, including a [Visual Studio Code plugin][10] that includes Maven integration).

This `tc.Deploy` class will also package everything needed to run the application on the target device, including TCVM, application bytecodes, TotalCross API bytecodes, assets (images, fonts, etc.), SQLite, and more.

The runtime stage enables the application to run on multiple operating systems, including Android, iOS, Linux, Windows, Windows CE, and Linux ARM. In this stage, there are no requirements for Java, JVM, or JDK. The application runs entirely with the TCVM. TCVM is embedded with the application, and the end user never knows whether a VM is running or not, making the process completely seamless.

### Which should you use?

TotalCross VM and Java VMs have different approaches. Not only their bytecodes and architecture differ; they also have different uses. While TotalCross is geared toward applications on the edge, Java's best uses are in things like web applications, server-side applications, and middleware.

Being detached from a JVM is very useful for TotalCross, both technically and strategically, because it greatly improves application footprints (TCVM uses 4MB, and a lot of research is being done to reduce it even further). As there are no strings attached to maintain compliance with a JVM and TotalCross' architecture is register-based, TotalCross VM provides native performance for running applications on both low-computing power and high-end devices, all while keeping the benefits of a high-level programming language like Java or Kotlin.

To decide whether to use a "pure" Java application or a TotalCross application, look at the requirements of your application and target devices. The two technologies have different approaches and aim to solve different issues, but in the end, you are the winner, as you can leverage your code and share it between them.

You should check out the [source code on GitHub][11] and draw your own conclusions. And let us know what you think =)

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/totalcross-cross-platform-development

作者：[Bruno Muniz][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/brunoamuniz
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/coffee_tea_laptop_computer_work_desk.png?itok=D5yMx_Dr (Person drinking a hot drink at the computer)
[2]: https://totalcross.com
[3]: https://en.wikipedia.org/wiki/SuperWaba
[4]: https://www.maxwell.vrac.puc-rio.br/colecao.php?strSecao=resultado&nrSeq=9953@2
[5]: https://opensource.com/sites/default/files/uploads/tcvmvjvm.png (TCVM vs JVM comparison)
[6]: https://creativecommons.org/licenses/by-sa/4.0/
[7]: https://docs.oracle.com/javase/7/docs/api/java/nio/ByteBuffer.html
[8]: https://en.wikipedia.org/wiki/Swing_(Java)#Relationship_to_AWT
[9]: https://opensource.com/sites/default/files/uploads/totalcross-architecture.png (TotalCross architecture)
[10]: https://marketplace.visualstudio.com/items?itemName=totalcross.totalcross
[11]: https://github.com/TotalCross/totalcross
