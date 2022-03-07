[#]: subject: "What's new with Java 17 and containers?"
[#]: via: "https://opensource.com/article/22/3/java-17-quarkus"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What's new with Java 17 and containers?
======
Quarkus allows developers to start a new application development based
on OpenJDK 17.
![Coffee beans and a cup of coffee][1]

Container platforms and [edge computing][2] continue to grow, powering major networks and applications across the globe, and Java technologies have evolved new features and improved performance to match steps with modern infrastructure. [Java 17][3] (OpenJDK 17) was released recently (September 2021) with the following major features:

  * [Restore Always-Strict Floating-Point Semantics][4]
  * [Enhanced Pseudo-Random Number Generators][5]
  * [Strongly Encapsulate JDK Internals][6]
  * [Pattern Matching for switch (Preview)][7]
  * [Foreign Function &amp; Memory API (Incubator)][8]
  * [Vector API (Second Incubator)][9]
  * [Context-Specific Deserialization Filters][10]



Developers are wondering how to start implementing application logic using the new features of Java 17 and then build and run them on the same OpenJDK 17 runtime. Luckily, [Quarkus][11] enables the developers to scaffold a new application with Java 17. It also provides a [live coding][12] capability that allows developers to focus only on implementing business logic instead of compiling, building, deploying, and restarting runtimes to apply code changes.

**Note**: If you haven’t already installed OpenJDK 17, [download a binary][13] on your operating system.

This tutorial teaches you to use the Pseudo-Random Number Generators (PRNG) algorithms of Java 17 on Quarkus. Get started by scaffolding a new project using the [Quarkus command-line tool][14] (CLI):


```
`$ quarkus create app prng-example --java=17`
```

The output looks like this:


```


...
[SUCCESS] ✅  quarkus project has been successfully generated in:
\--&gt; /Users/danieloh/quarkus-demo/prng-example
...

```

Unlike traditional Java frameworks, Quarkus provides live coding features for developers to rebuild and deploy while the code changes. In the end, this capability accelerates inner loop development for Java developers. Run your Quarkus application using Dev mode:


```


$ cd prng-example
$ quarkus dev

```

The output looks like this:


```


...
INFO  [io.quarkus] (Quarkus Main [Thread][15]) Profile dev activated. Live Coding activated.
INFO  [io.quarkus] (Quarkus Main [Thread][15]) Installed features: [cdi, resteasy, smallrye-context-propagation, vertx]

\--
Tests paused
Press [r] to resume testing, [o] Toggle test output, [:] for the terminal, [h] for more options&gt;

```

Java 17 enables developers to generate random integers within a specific range based on the **Xoshiro256PlusPlus** PRNG algorithm. Add the following code to the `hello()` method in the `src/main/java/org/acme` directory:


```


RandomGenerator randomGenerator = RandomGeneratorFactory.of("Xoshiro256PlusPlus").create(999);

for ( int i = 0; i &lt; 10 ; i++) {
    int result = randomGenerator.nextInt(11);
    [System][16].out.println(result);
}

```

Next, invoke the RESTful API (`/hello`) to confirm that random integers are generated. Execute the following cURL command line in your local terminal or access the endpoint URL using a web browser:


```
`$ curl localhost:8080/hello`
```

Go back to the terminal where you’re running Quarkus Dev mode. There you’ll see the following ten random numbers:


```


4
6
9
5
7
6
5
0
6
10

```

**Note**: You don’t need to rebuild code and restart the Java runtime at all. You’ll also see the output Hello RESTEasy in the terminal where you ran the `curl` command line.

### Wrap up

This article shows how Quarkus allows developers to start a new application development based on OpenJDK 17. Furthermore, Quarkus increases developers’ productivity by live coding. For a production deployment, developers can make a [native executable][17] based on OpenJDK 17 and [GraalVM][18].

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/java-17-quarkus

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/java-coffee-mug.jpg?itok=Bj6rQo8r (Coffee beans and a cup of coffee)
[2]: https://opensource.com/article/17/9/what-edge-computing
[3]: https://openjdk.java.net/projects/jdk/17/
[4]: https://openjdk.java.net/jeps/306
[5]: https://openjdk.java.net/jeps/356
[6]: https://openjdk.java.net/jeps/403
[7]: https://openjdk.java.net/jeps/406
[8]: https://openjdk.java.net/jeps/412
[9]: https://openjdk.java.net/jeps/414
[10]: https://openjdk.java.net/jeps/415
[11]: https://opensource.com/article/21/8/java-quarkus-ebook
[12]: https://quarkus.io/vision/developer-joy#live-coding
[13]: https://jdk.java.net/17/
[14]: https://quarkus.io/guides/cli-tooling
[15]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+thread
[16]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+system
[17]: https://quarkus.io/guides/building-native-image
[18]: https://www.graalvm.org/
