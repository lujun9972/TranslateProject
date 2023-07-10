[#]: subject: "Lima: a nice way to run Linux VMs on Mac"
[#]: via: "https://jvns.ca/blog/2023/07/10/lima--a-nice-way-to-run-linux-vms-on-mac/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Lima: a nice way to run Linux VMs on Mac
======

Hello! Here’s a new entry in the “cool software julia likes” section.

A little while ago I started using a Mac, and one of my biggest frustrations with it is that often I need to run Linux-specific software. For example, the [nginx playground][1] I posted about the other day only works on Linux because it uses Linux namespaces (via `bubblewrap`) to sandbox nginx. And I’m working on another playground right now that uses bubblewrap too.

This post is very short, it’s just to say that Lima seems nice and much simpler to get started with than Vagrant.

### enter Lima!

I was complaining about this to a friend, and they mentioned [Lima][2], which stands for **Li** nux on **Ma** c. I’d heard of [colima][3] (another way to run Linux containers on Mac), but I hadn’t realized that Lima also just lets you run VMs.

It was surprisingly simple to set up. I just had to:

  1. Install Lima (I did `nix-env -iA nixpkgs.lima` but you can also install it with `brew install lima`)
  2. Run `limactl start default` to start the VM
  3. Run `lima` to get a shell



That’s it! By default it mounts your home directory as read-only inside the VM

There’s a config file in `~/.lima/default/lima.yaml`, but I haven’t needed to change it yet.

### some nice things about Lima

Some things I appreciate about Lima (as opposed to Vagrant which I’ve used in the past and found kind of frustrating) are:

  1. it provides a default config
  2. it automatically downloads a Ubuntu 22.04 image to use in the VM (which is what I would have probably picked anyway)
  3. it mounts my entire home directory inside the VM, which I really like as a default choice (it feels very seamless)



I think the paradigm of “I have a single chaotic global Linux VM which I use for all my projects” might work better for me than super carefully configured per-project VMs. Though I’m sure that you can have carefully configured per-project VMs with Lima too if you want, I’m just only using the `default` VM.

### problem: I don’t know how to mount directories read-write

I wanted to have my entire home directory mounted read-only, but have some subdirectories (like `~/work/nginx-playground`) mounted read-write. I did some research and here’s what I found:

  * a comment on [this github issue][4] says that you can use [mountType: “virtiofs” and vmType: “vz”][5] to mount subdirectories of your home directory read-write
  * the Lima version packaged in nix 23.05 doesn’t seem to support `vmType: vz` (though I could be wrong about this)



Maybe I’ll figure out how to mount directories read-write later, I’m not too bothered by working around it for now.

### why not use containers?

I wanted a VM and not a Linux container because:

  1. the playground runs on a VM in production, not in a container, and generally it’s easier to develop in a similar environment to production
  2. all of my playgrounds use Linux namespaces, and I don’t know how to create a namespace inside a container. Probably you can but I don’t feel like figuring it out and it seems like an unnecessary distraction.
  3. on Mac you need to run containers inside a Linux VM anyway, so I’d rather use a VM directly and not introduce another unnecessary layer



### that’s all!

Some other notes:

  * It looks like Lima works on Linux too
  * a bunch of people on Mastodon also said [colima][3] (built on top of Lima) is a nice Docker alternative on Mac for running Linux containers
  * there’s also an new alternative Linux container runtime for Mac called [Orb Stack][6], which I know nothing about



--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2023/07/10/lima--a-nice-way-to-run-linux-vms-on-mac/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://jvns.ca/blog/2021/09/24/new-tool--an-nginx-playground/
[2]: https://lima-vm.io/
[3]: https://github.com/abiosoft/colima
[4]: https://github.com/lima-vm/lima/issues/873
[5]: https://github.com/lima-vm/lima/blob/master/docs/vmtype.md#vz
[6]: https://docs.orbstack.dev/
