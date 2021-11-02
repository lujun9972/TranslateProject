[#]: subject: "What you need to know about containers for Python"
[#]: via: "https://opensource.com/article/21/11/containers-python"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What you need to know about containers for Python
======

![Parts, modules, containers for software][1]

Python is a popular language for many applications. Those that run as backend services, now in the 2020s, are often run inside containers. For that to work, though, you have to build a container.

Often, with microservice architectures, it makes sense to build a "root" base image, which all of your services get built on. Most of this article focuses on that base image since this is where it is easiest to make mistakes. However, I also cover the applications themselves because a good base without good applications isn't of much use.

### What makes a good container?

Before talking about _how_ to build good containers, you need to understand what good containers are. What distinguishes good containers from bad ones? You might turn to some obvious measurements you hear about in the world of containers:

  * Fast
  * Small
  * Safe
  * Usable



This is pretty high-level and maybe too general. What does "fast" mean? Fast at what? How small is "small?" What does it mean to be "safe" or "secure?"

So something more concrete is probably better. Containers have certain requirements. Here are a few common ones:

  * Ability to keep it up to date
  * Reproducible builds
  * No compilers in production
  * Stay reasonably small



I'll start with "up to date." What that usually means, first and foremost, is that security updates from the upstream distribution get installed on a regular cadence. However, this directly conflicts with the next goal of reproducible builds. The abstract theory of reproducible builds says that giving the same source must result in a bit-for-bit identical result. This has many advantages, but it's non-trivial to achieve.

If you lower the bar a bit, the same source must also lead to equivalent results. While this removes some advantages, it maintains the most important one. _Changing_ the source by some amount only results in _commensurate_ changes. This is the main benefit of reproducible builds. It allows pushing small fixes with confidence that there are no unrelated changes. This allows less testing for small fixes and faster delivery of hot patches.

The next criterion sounds almost trivial: "No compilers in production." That's easy: Compile ahead of time, and store results in the image. This criterion is here because it's surprisingly easy to get wrong without careful thought and implementation. Many containers were shipped with `gcc` because someone did not write their `Dockerfile` carefully enough.

On the matter of size, however, it's possible to spend a near-infinite amount of time. For every byte, you can debate whether it's worth it or not. In practice, after getting into the low hundreds of megabytes, this quickly becomes a game of diminishing returns. Hours of work can go into carefully trimming a few hundred extra kilobytes. The point at which to stop depends on the cost structure. Do you pay per gigabyte? If so, how much? How many different images use the base image? Is there something more valuable you can do with your time?

In practice, getting images down to low hundreds of megabytes (200 or 300) is pretty straightforward. Getting them below 200 is possible with a little more work.

That's usually a good stopping point.

### When to use binary packages in your containers

One way to make building a container image faster and more reliable is to use _binary wheels_ for packages with native code. Binary wheels are a useful tool, whether you get the wheels from PyPI, building wheels into an internal package index, or even building the wheels as part of a multistage container build.

### Container user identity

It's important to add a dedicated user for the container to run applications as. This is important for several reasons, but the overarching themes are that it is an important intervention to reduce risk.

In most setups, root inside the container is the same as root outside the container. This makes it much more likely that root can find a "container escape."

While a regular user can find a privilege escalation bug and then escape as root, this increases the complexity of such an attack. Forcing attackers to use complex attacks by frustrating less dedicated ones and increasing the chances that a persistent attacker will trip an auditing alarm.

The other big reason is more mundane: A root user can do anything _inside_ the container. Limiting those abilities is both a smart bug avoiding strategy and reduces the attack surface.

Running as root is also a necessary component for the next good idea: Running with minimal privileges. Most importantly, it is a good idea to avoid write permissions as much as possible. The most important thing to avoid write permissions for is the virtual environment from which the application is running.

Avoiding such write permissions again lowers the attack surface by preventing code modifications at runtime.

### Container performance

The next thing to optimize for is performance. The most important speed-up criterion here is _rebuild_ time.

Modern BuildKit-based builds try to be smart about which steps prevent which cache invalidations. In a multistage build, they also try to run steps that are provably independent of each other in parallel.

Writing a `Dockerfile` to take advantage of this technique is a non-trivial skill to master but well worthwhile. It's especially useful to think about which files change less than others.

One example trick: First copying `requirements.txt` and using it as an argument to `pip install -r`, before copying the source code and installing it.

This means that downloading and installing (and sometimes even compiling) the dependencies will only be cache-invalidated by the `requirements.txt` file. This allows faster rebuilds for the more common use-case the local source code changes.

### Bases

To make an apple pie from scratch, first, create the universe. Creating the universe is a lot of thankless work, and there are probably more valuable ways to spend your workday.

All this is to say that you'll probably start your image definition with `FROM <some distro>`. But which distro? One thing that's more important for containers than traditional uses of operating systems is that they are more sensitive to size overhead. This is because container images tend to be in 1:1 correspondence with applications.

Suppose an application builds a test build on every pull request (PR) and stores it in a registry for a while so that you can run tests on different environments on this PR—this stores a lot of versions of the OS in the registry.

Some of this is alleviated by containers sharing base layers, but probably less than is often naively assumed in practice. It turns out that images get built to accept the security and critical bug patches, which tends to perturb the base OS often enough that caching, while helpful, is no substitute for a smaller size.

Because applications get built on top of the base image, it's useful for a bump to the base version to be relatively rare. Any time application teams have to spend moving to a new base is time they're not developing useful customer-facing features.

This means it's good to find a base that has a long-term support (LTS) version. Having a base with around five years of LTS allows proper planning for upgrades without making it a frequent exercise.

Together with LTS, the update policy of the base matters—significantly. Does it update for general bugs? Only critical bugs? Security fixes? Does it do backports or try to upgrade to new upstream versions?

I find that Alpine is not a good choice for Python-based applications since it uses `musl` (not `glibc`) and it's not `manylinux` compatible. This makes a lot of binary wheel issues unnecessarily complicated. This might change in the future with `musllinux` potential support, but this is not the best choice for now.

Popular choices include Debian. It has a conservative policy on updates and a five-year LTS.

Another popular choice is Ubuntu. It has slightly more liberal policies (for example, it only allows backports for sufficiently good reasons). Those policies also depend on subtle differences between "universe" and "multiverse," which are beyond the scope of this article.

### What about rolling releases for containers?

Some distributions have so-called "rolling releases." Instead of having a scheduled release updating to new upstream versions of all packages, new upstream versions get added as they get released and integrated. This works well for desktops, where using up-to-date versions is fun. It can even work well for non-ephemeral servers, where being able to do in-place upgrades, long term, allows minimization of the need to do complete machine rebuilds.

For containers, though, rolling releases are a poor match. The main benefit of updating incrementally is wholly lost, as each image gets built from scratch. Containers get built for wholesale replacement.

The biggest downside of rolling releases for containers is there is no way to get security updates without, potentially, getting new versions of upstream software. This can mean an expensive, immediate need to support a new version of an upstream dependency to push out a security fix.

### Installing Python

Now that there's an operating system installed in the container, it's time for the _pièce de résistance_: A Python interpreter. Running Python applications requires the interpreter and the standard library. Somehow, the container needs to include them.

Some third-party repositories are packaging Python for use in distributions as an OS package. The most famous one is `deadsnakes` for Ubuntu, which precompiles Python packages. This is a popular choice. It means waiting for the right version to appear in the repository, but this usually happens with little delay.

Another option is to use `pyenv`. This is particularly useful if a single dev Python container image needs to have multiple versions of Python. You can build the runtime versions from it through careful copying, and it allows some flows which require multiple versions of Python at build time to work. Even without the need for multiple versions of Python, `pyenv` can be a popular choice. It's a trusted tool that can build Python inside a container.

### Python build

One way to get the most significant benefit of `pyenv` without needing some of the overhead that's less useful in containers (like shims and the ability to switch versions) is to use `python-build`. This is the engine inside `pyenv`, which builds Python. Using it directly not only allows skipping redundancies but also configuring build details on a more granular basis. These are possible in `pyenv`, but the need to do a pass-through to `python-build` makes them more awkward, especially when there are a lot.

Finally, or maybe initially, it is possible to do it like the people in the before-times. The `configure/make/make install` flow works and removes any barriers between the developer and the build. You can set and adjust any build parameters. The main downside is the need to securely grab the source code's tarball and avoid supply-chain attacks.


```
RUN configure [...]
RUN make
RUN make install
```

There are inherent trade-offs when choosing this:

  * How much control the local build has over the result
  * How much work it is to implement
  * The potential for issues



Ultimately, each team must decide for itself what trade-offs are right for it.

It's usually a good idea to build several versions of your "base level" Python containers to allow dependent containers to move to a new version at different times. The minimum needed for this to work is two. While more than three are possible, in practice, this is usually unnecessary. Python releases yearly, so three versions give two years to upgrade to a new, mostly backward compatible version of Python.

If a team does not have slack over the course of two years, the problem is not one of Python versions. In practice, this means the choice is between supporting two or three versions of Python.

### Thinking in stages

Containers are built in _multiple stages_. By default, only one stage is output—the last one. You can output a different stage by selecting it on the command line.

The other stages can _help_ that stage get built in two different ways. One way is to use a previous stage in a `FROM` command within a new stage. This is the same as `FROM` an external image: It starts from the previous image and runs the next steps as additional layers.

Another way to use a non-output stage is to `COPY` files from it. This is similar to `COPY` from the Docker build context, but instead of using the build context, it uses a previous stage. The semantics of `COPY` (as far as recursion, files, and directories) remain the same.

The `FROM <stage>` technique allows you to use stages as "common modules" in a Docker build file. If two images need several initial steps in common, you can add those to an internal "base" stage, and then both images use it as their starting point.

The downside is that common modules (and all their dependents) must be in the same file. In general, as unpleasant as it is, projects should keep their Docker logic in one file and not split it into several.


```
FROM ubuntu as security-updates
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update
RUN apt-get upgrade

FROM security-updates as with-38
RUN apt-get install python3.8

FROM security-updates as with-39
RUN apt-get install python3.9
```

One of the most significant benefits of stages is that they allow separating build and runtime dependencies. The build time dependencies get installed in one stage, the build logic is executed, and the build artifacts are copied to the next stage, which starts from a pristine image, without any of the build dependencies.


```
FROM ubuntu as builder
# install build dependencies
# build Python into /opt/myorg/python

FROM ubuntu as as runtime
COPY --from=builder \
      /opt/myorg/python \
      /opt/myorg/python
```

Especially for runtime images, there is a benefit in reducing the number of layers. One way to accomplish that is to have a stage of "preparing" a directory like `/opt/myorg` using several commands and file manipulations.

You can do the next stage in only one additional layer on the base:


```
`COPY --from=prep-stage /opt/myorg/ /opt/myorg`
```

If you build Python locally, remove (in the runtime image) the big things you won't need—the static library, tests, various temporary build artifacts, and so on. Often you can do this in a preparation stage, with the minimalistic Python build output copied to the next stage.

### Use in applications

Sometimes an application has some parts written in native code. More often, the application needs third-party dependencies with native code. If you need to build those locally, you should build them in a separate stage from the runtime.

A popular technique is to build all dependencies and then copy them to the runtime image you install in a virtual environment.

  * Build with a builder
  * Copy to runtime
  * Install in a virtual environment



Alternatively, you can keep the runtime image even smaller by installing it in a virtual environment and then copying over the virtual environment as one big directory. This does need careful matching of the precise Python versions, and so, it depends on how you created the base system.

If building wheels is necessary, it is sometimes helpful to make them self-contained. For that, you need a few dependencies.

The `patchelf` command is a tool to manipulate Executable and Linkable Format (ELF) files, especially shared libraries. I find it's usually best to compile `patchelf` from recent sources so you're sure to have all the latest features.

The `patchelf` command provides the low-level part. It is non-trivial to install, but does need a little wrapping. The tool that makes wheels self-contained is `auditwheel`. Luckily, once `patchelf` is properly installed, you can get `auditwheel` done as long as you properly configure Python and `pip`. You can use `auditwheel` to create self-contained binary wheels. Such binary wheels have all binary dependencies directly patched into them. This requires you to install the "runtime" version of the library in the runtime image.

This reduces layers and complexity but does require a high degree of fidelity between the runtime and dev images.


```
`$ auditwheel repair --platform linux_x86_64`
```

The need for this degree of fidelity can be an inconvenient requirement. Moreover, it could be nice to build the wheels once, not on every `docker build`. You can arrange this if you have an internal package index (like `devpi` or any of the commercial alternatives).

### Portable wheels

To build portable binary wheels, decide what the oldest GNU C Library (glibc) you need to support is. After building a wheel on that platform, use `auditwheel` with portable tags to create an uploadable wheel.

You can use this wheel only on compatible systems, and you can upload more than one wheel.

Regardless of what the end-game of the binary wheel is, somehow, you need to build it. The actual build is simple: `python -m build`. The problem is what comes before. For some wheels, this is enough.

A few `apt` or `dnf` install of `-dev` libraries should do for other wheels. For yet others, building them requires installing the Fortran or Rust toolchains.

Some require installing Java and then getting a custom build tool written in Java. Unfortunately, this is not a joke.

The instructions are, hopefully, in the package's documentation. At least encoding the instructions in a container build file is concrete, computer-readable, and repeatable, regardless of how long it takes to translate the documentation to these instructions.

### Runtime images

Now that Python _and_ the PyPI packages are ready, you must copy them to the runtime image. One way to reduce the layers is by reducing the copy instructions. Properly prepping directories in the dev image is better than copying bits and pieces to the runtime image. Carefully think about caching. Put time-consuming steps as early as possible. Copy files from the context as late as possible. This means copying files _separately_ if only some are needed.

The local Python sources change the fastest. Copy them last. If done right, the bottleneck is usually the final copy to the runtime image. One way to speed up things is to have the dev image usable as a runtime image for debugging locally.

### Final thoughts

There are many factors to consider when building a container for Python applications. While there are no objectively correct answers, there are a lot of objectively wrong answers. There are more ways to be wrong than right, so carelessly doing things can lead to regrets.

It is worth it to think about these things and plan. The hours you spend planning and thinking can repay themselves many times over by giving high-quality images that are simpler to build, run, and audit.

Container build files are sometimes an afterthought, done haphazardly after "the code is done." This can hurt you. Spend time thinking before you implement container builds.

### Learn more

I have only touched on the surface of the things you need to know. Itamar Turner-Trauring has written [a series of articles][2], diving deeper into many of these issues.

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/11/containers-python

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/containers_modules_networking_hardware_parts.png?itok=rPpVj92- (Parts, modules, containers for software)
[2]: https://pythonspeed.com/docker/
