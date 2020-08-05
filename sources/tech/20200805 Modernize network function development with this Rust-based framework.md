[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Modernize network function development with this Rust-based framework)
[#]: via: (https://opensource.com/article/20/8/capsule-networking)
[#]: author: (Zeeshan Lakhani https://opensource.com/users/zeeshanlakhani)

Modernize network function development with this Rust-based framework
======
Capsule is a framework for packet processing and writing network
functions that aims to lower the bar of entry for network function
development.
![computer servers processing data][1]

The world of networking has undergone monumental shifts over the past decade, particularly in the ongoing move from specialized hardware into software defined [network functions][2] (NFV) for data plane1 and packet processing. While the transition to software has fashioned the [rise of][3] SDN (Software-defined networking) and programmable networks, new challenges have arisen in making these functions flexible, efficient, easier to use, and _fast_ (i.e. little to no performance overhead). Our team at Comcast wanted to both leverage what the network does best, especially with regards to its transport capacity and routing mechanisms, while also being able to develop network programs through a modern software lens—stressing _testing_, swift iteration, and deployment. So, with these goals in mind, we developed [Capsule][4], a new framework for network function development, written in Rust, inspired by Berkeley's [NetBricks][5] research, and built-on Intel's [Data Plane Development Kit][6] (DPDK).

![][7]

Many networks today are still programmed using low-level languages that may lack safeguards against logic errors. [Studies have even shown][8] that logic errors are the most commonly found errors in packet-processing programs including failing to check expected branching conditions, forgetting conditional checks or validations, and getting checksums wrong. While there's been an influx of higher-level language frameworks and programming models entering the space, especially from research and academia, many tend to be difficult for application developers to get started with, extend for their own purposes, unit-test, and/or run in a production setting.

With Capsule, we set out with a goal to offer an ergonomic framework for network function development that traditionally has high barriers of entry for developers. We've created a tool to _build_ and _run_ network functions, efficiently manipulating network packets while being type-safe, memory-safe, and thread-safe. Building on DPDK and Rust, Capsule provides:

  * a fast packet processor that uses minimum number of CPU cycles.
  * a rich packet type system that guarantees memory-safety and thread-safety.
  * a declarative programming model that emphasizes simplicity.
  * an extensible and testable framework that is easy to develop and maintain.



### Getting started

The easiest way to start developing Capsule applications is to use Capsule's [Vagrant virtual machine][9] (VM) and [Docker sandbox][10]. The sandbox is preconfigured with all the necessary tools and libraries for Capsule development, including:

  * [DPDK 19.11][11]
  * [Clang][12] and [LLVM][13]
  * [Rust 1.43][14]
  * [rr 5.3][15]



First, install [Vagrant][16] and [VirtualBox][17] on your system. Also, install the required Vagrant plugins with:


```
`host$ vagrant plugin install vagrant-reload vagrant-disksize vagrant-vbguest`
```

Next, clone Capsule's sandbox repository, then start and `ssh` into the Vagrant VM:


```
host$ git clone <https://github.com/capsule-rs/sandbox.git>
host$ cd sandbox
host$ vagrant up
host$ vagrant ssh
```

Once you're inside the created Debian VM with Docker installed, run the sandbox with:


```
vagrant$ docker run -it --rm \
    --privileged \
    --network=host \
    --name sandbox \
    --cap-add=SYS_PTRACE \
    --security-opt seccomp=unconfined \
    -v /lib/modules:/lib/modules \
    -v /dev/hugepages:/dev/hugepages \
    getcapsule/sandbox:19.11.1-1.43 /bin/bash
```

Remember to also mount the working directory of your project as a volume for the sandbox. Then you can use Rust [Cargo][18] commands inside the container as usual.

Finally, add Capsule as a dependency to your `Cargo.toml`, and start writing your application:


```
[dependencies]
capsule = "0.1"
```

If you want to develop Capsule without using Docker in Vagrant, please check out the [Capsule sandbox][19] repo for instructions on running our Vagrant VM environment, as well as other options that do not rely on either Vagrant or Docker. The Capsule Rust crate is available on [crates.io][20].

### Getting involved

The Capsule project is looking for contributors to help further develop and enhance the framework, including new protocols, features, and optimizations. If you are interested in participating, please see the [contributing guide][21] to get involved. We'd also love to see what use-cases and applications are explored with the framework. To see what Capsule programs look like, check out our [examples][22], including a [ping utility][23], and network functions that exercise [network address translation][24] and forwarding, [TCP SYN flood][25] generation with exposed metrics, and our general [declarative approach][26] to packet-processing.

The project and everyone participating in it agrees to and is governed by the [Capsule Code Of Conduct][27].

The current maintainers with roles to merge pull requests are:

  * [Peter Cline][28]
  * [Daniel Jin][29] (co-lead maintainer)
  * [Zeeshan Lakhani][30] (co-lead maintainer)
  * [Andrew Wang][31]



You can contact the team through [Discord][32] or [email][33].

1_Refers to the forwarding and modifying of network traffic. Please read [Programmable Network Data Planes][34] for a contemporary view on data plane programmability industry projects and research._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/capsule-networking

作者：[Zeeshan Lakhani][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/zeeshanlakhani
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/server_data_system_admin.png?itok=q6HCfNQ8 (computer servers processing data)
[2]: https://www.sciencedirect.com/topics/computer-science/network-function
[3]: https://twitter.com/cisco/status/1012108281165373440
[4]: https://github.com/capsule-rs/capsule
[5]: https://www.usenix.org/system/files/conference/osdi16/osdi16-panda.pdf
[6]: https://www.dpdk.org/
[7]: https://opensource.com/sites/default/files/capsule.png (Capsule)
[8]: https://arxiv.org/abs/1909.06344
[9]: https://github.com/capsule-rs/sandbox/blob/master/Vagrantfile
[10]: https://hub.docker.com/repository/docker/getcapsule/sandbox
[11]: https://doc.dpdk.org/guides-19.11/rel_notes/release_19_11.html
[12]: https://clang.llvm.org/
[13]: https://www.llvm.org/
[14]: https://blog.rust-lang.org/2020/04/23/Rust-1.43.0.html
[15]: https://rr-project.org/
[16]: https://www.vagrantup.com/
[17]: https://www.virtualbox.org/
[18]: https://doc.rust-lang.org/book/ch01-03-hello-cargo.html
[19]: https://github.com/capsule-rs/sandbox/blob/master/README.md
[20]: https://crates.io/crates/capsule
[21]: https://github.com/capsule-rs/capsule/blob/master/CONTRIBUTING.md
[22]: https://github.com/capsule-rs/capsule/tree/master/examples
[23]: https://github.com/capsule-rs/capsule/tree/master/examples/ping4d
[24]: https://github.com/capsule-rs/capsule/tree/master/examples/nat64
[25]: https://github.com/capsule-rs/capsule/tree/master/examples/syn-flood
[26]: https://github.com/capsule-rs/capsule/blob/master/examples/pktdump/main.rs
[27]: https://github.com/capsule-rs/capsule/blob/master/CODE_OF_CONDUCT.md
[28]: https://github.com/clinedome
[29]: https://github.com/drunkirishcoder
[30]: https://github.com/zeeshanlakhani
[31]: https://github.com/awangc
[32]: https://discord.gg/sVN47RU
[33]: mailto:capsule-dev@googlegroups.com
[34]: http://www.justinesherry.com/papers/antichi-dagstuhl19.pdf
