[#]: subject: "Fedora Hummingbird: Taking the Hummingbird model to the full operating system"
[#]: via: "https://fedoramagazine.org/fedora-hummingbird-linux-taking-the-hummingbird-model-to-the-full-os/"
[#]: author: "Harrison Ripps https://fedoramagazine.org/author/nhr/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Hummingbird: Taking the Hummingbird model to the full operating system
======

![][1]

At Red Hat Summit 2026, we’re announcing Fedora Hummingbird — a new container-based rolling Fedora Linux distribution. This distribution provides access to the latest software as soon as it’s available upstream, which ensures that it’s up to date and secure.

Fedora Hummingbird primarily utilizes an image-based workflow, similar to containers, but also runs in virtual machines and even on bare metal. If you’ve been following [Project Hummingbird][2]‘s work on container images, or [Project Bluefin’s work on the operating system][3], you already know the model. Fedora Hummingbird applies this model all the way down to the host OS.

The foundation for Fedora Hummingbird already ships today from the [Hummingbird containers repository][4]. You can pull and boot it right now.

## **What is Project Hummingbird?**

The central goal of Project Hummingbird is to get as close to zero CVE reports as possible in every container image it ships, and to stay there continuously. The team made every architectural decision, including distroless images, minimal package footprints, hermetic builds, and the degree of pipeline automation, in service of that goal. “Distroless” means no package manager, no shell, just the application and what it strictly needs to run.

Why does this matter? When you pull a third-party container image today, you inherit its vulnerabilities and you’re on the hook for managing them. Pull a Hummingbird image and the team’s pipeline has already done the CVE triage, the patching, and the rebuild – you get to skip CVE hell. (If you’re curious, current CVE status across all images and variants is published live at the [Hummingbird catalog][5]).

Over the past eight months, the team has built a catalog of 49 unique minimal, hardened, distroless container images (that’s 157 variants including FIPS and multi-arch) covering Python, Go, Node.js, Rust, Ruby, OpenJDK, .NET, PostgreSQL, nginx, and dozens more. Distroless means no package manager, no shell, just the application and what it strictly needs to run.

### How it’s built

The infrastructure behind this is a [Konflux][6]-based pipeline. It uses fully isolated, reproducible builds from pinned package lists, efficient incremental updates via [chunkah][7] (a tool the Hummingbird team built to ensure the system re-downloads only changed parts of an image), and continuous vulnerability scanning via [Syft][8] and [Grype][9]. When a vulnerability is patched upstream, the pipeline finds it, rebuilds, tests, and ships.

95%+ of the packages in every Hummingbird image come straight from [Fedora Rawhide][10], unmodified. The build system pulls the remaining packages directly from upstream when Rawhide doesn’t yet carry them or isn’t new enough, and the team contributes changes back into Fedora. If that sounds like Fedora CoreOS, that’s because it’s a related idea, but serving a different use case. CoreOS is a minimal host for orchestrated workloads. Hummingbird serves developers who need to deploy multiple versions of runtimes (Python 3.11–3.14, Go 1.25–1.26, Node.js 20–25) in parallel and manage each version’s lifecycle independently.

The Hummingbird factory independently builds packages so they carry their own identity. This means each package can have a separate life cycle, patching policy, and CVE feed (specifically, a vulnerability feed that Red Hat’s Product Security team maintains). Every package ships with machine-readable vulnerability data that tells you not just which CVEs exist, but which ones actually affect your workload.

## **The OS as a container image**

The challenges that Project Hummingbird seeks to address in userspace exist at the OS level as well, so we want to apply the same approach to addressing those challenges. This is where Fedora Hummingbird comes in. This image is already live at <https://quay.io/repository/hummingbird-community/bootc-os>. The team delivers this full Linux OS as an OCI image, and they build it using the same Konflux pipeline and hermetic RPM-locking approach as the rest of the Hummingbird catalog. Multi-arch: x86_64 and aarch64.

Under the hood, Fedora Hummingbird will use the [ARK kernel][11] (Always Ready Kernel) from the [CKI project][12] (already running in Fedora today) which tracks Linus’ mainline directly. The benefit of leveraging the CKI project is the curated kernel configuration and elaborate engineering framework that includes extensive testing around a fast-moving kernel stream.

The [Fedora bootable containers][13] initiative laid out the groundwork for all of this. The idea is that the OS is an OCI image, built and distributed like any other container, and updated atomically with rollback built in. No partial update states. No configuration drift. The root filesystem is read-only. Any writeable state lives in /var and /etc, cleanly separated from the OS content.

The Hummingbird bootc OS image boots today. What’s still in progress is the integration work. The image is currently a mix of Hummingbird-built RPMs and Fedora packages, and we’re working out how to bring the two closer together. That’s exactly the kind of work we’d love to collaborate on.

## **Hummingbird in the Fedora community**

Many members of the Hummingbird team are already Fedora contributors and package maintainers – maintainers of Podman, and other container tools that Fedora and the broader Linux ecosystem depend on, as well as maintainers of Fedora CoreOS. Members of the Fedora community contributed the bootable containers work that underpins Fedora Hummingbird. Now those members are continuing the work as part of Hummingbird. Moving forward, we’d like to make Hummingbird a part of the Fedora Project so that it can benefit and grow within that same community.

The Hummingbird pipeline already builds and publishes a set of container images based entirely on Fedora Rawhide at [quay.io/organization/hummingbird-rawhide][14]. The team has already started bringing improvements back to Fedora. These include container-specific optimizations, bugs found in .spec files, and more. The vulnerability feed that ships with Hummingbird packages is something we think could benefit the broader Fedora ecosystem too.

## **Getting started**

Here are some quick-start instructions for getting a virtual machine up and running:

**1\. Create the image**

```

    sudo podman run --rm --privileged --pull=newer \
      --security-opt label=type:unconfined_t \
      -v /tmp/bib-config.toml:/config.toml:ro \
      -v /var/lib/libvirt/images:/output \
      -v /var/lib/containers/storage:/var/lib/containers/storage \
      quay.io/centos-bootc/bootc-image-builder:latest \
      --type qcow2 --rootfs ext4 \
      quay.io/hummingbird-community/bootc-os:latest

```

**2\. Rename the image**

```

    sudo mv /var/lib/libvirt/images/qcow2/disk.qcow2 \
      /var/lib/libvirt/images/fedora-hummingbird.dc2.crunchtools.com \
      && sudo rmdir /var/lib/libvirt/images/qcow2

```

**3\. Create a virtual machine**

```

    sudo virt-install --connect qemu:///system \
      --name fedora-hummingbird.dc2.crunchtools.com \
      --memory 4096 --vcpus 2 \
      --disk /var/lib/libvirt/images/fedora-hummingbird.dc2.crunchtools.com,format=qcow2 \
      --import --os-variant fedora-unknown \
      --network network=default,model=virtio \
      --graphics vnc --noautoconsole

```

## **Get involved**

When you’re ready to try it, there’s no registration form, no subscription-manager, no entitlements required. The code is already there and the pipeline is already running — we’d love more eyes on it. Here’s how to jump in:

  * **Try the image** : You can find instructions on using the image on [Q][4][u][4][ay][4]
  * **File issues and feedback** : anything broken, missing, or surprising is worth reporting at this stage
  * **Contribute** : the project currently lives at [gitlab.com/redhat/hummingbird/containers][15] — establishing a home in Fedora’s own infrastructure is part of the work ahead
  * **Join the conversation** : visit the [SIG page][16] for info on our getting-started sessions.



Fedora has always been where the community proves out new Linux ideas before they matter everywhere else. Fedora Hummingbird is an experiment for image-based, continuously-maintained operating systems, and we think it’s ready for the community to kick the tires.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-hummingbird-linux-taking-the-hummingbird-model-to-the-full-os/

作者：[Harrison Ripps][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/nhr/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/05/hummingbird-linux-816x345.jpg
[2]: https://hummingbird-project.io/
[3]: https://www.infoworld.com/article/2336653/project-bluefin-and-the-future-of-operating-systems.html
[4]: https://quay.io/repository/hummingbird-ci/bootc-os
[5]: https://catalog-hummingbird.hummingbird-project.io/
[6]: https://konflux-ci.dev/
[7]: https://github.com/coreos/chunkah
[8]: https://github.com/anchore/syft
[9]: https://github.com/anchore/grype
[10]: https://docs.fedoraproject.org/en-US/releases/rawhide/
[11]: https://gitlab.com/cki-project/kernel-ark
[12]: https://cki-project.org/
[13]: https://docs.fedoraproject.org/en-US/bootc/getting-started/
[14]: https://quay.io/organization/hummingbird-rawhide
[15]: https://gitlab.com/redhat/hummingbird/containers
[16]: https://fedoraproject.org/wiki/Hummingbird
