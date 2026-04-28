[#]: subject: "Sealed Fedora Atomic Desktop bootable container images"
[#]: via: "https://fedoramagazine.org/sealed-atomic-desktops-test-images/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Sealed Fedora Atomic Desktop bootable container images
======

![][1]

Photo by [Steve Johnson][2] on [Unsplash][3]

I’m happy to announce that we have sealed bootable container images ready for testing for the Fedora Atomic Desktops!

### What are sealed bootable container images?

Sealed bootable container images include all the components needed to create a fully verified boot chain, from the firmware to the operating system composefs image. This relies on Secure Boot and thus only supports system booting with UEFI on x86_64 & aarch64.

The components are:

  * systemd-boot as bootloader
  * a Unified Kernel Image (UKI) which includes the Linux kernel, an initrd and the kernel command line
  * a composefs repository with fs-verity enabled. This is managed by bootc.



Both systemd-boot and the UKI are signed for Secure Boot. The images are _**test images**_ so the components are not signed with the official keys from Fedora.

The main direct benefit that we will get from this support is that we will be able to enable passwordless disk unlocking using the TPM in a way that will be reasonably secure by default.

### How do I test those images?

See the instructions at [github.com/travier/fedora-atomic-desktops-sealed][4] on how to give the pre-built container and disk images a try and how to build your own.

We welcome testing and feedback! Please see the list of known issues and report new issue at [github.com/travier/fedora-atomic-desktops-sealed][4]. We’ll redirect them as needed to the right upstream projects.

_Beware_ , those are testing images. The root account does not have a password set and sshd is enabled, by default, to make debugging easier. The UKI and systemd-boot are signed for Secure Boot but, since those are test images, they are not signed with the official keys from Fedora. _Don’t use those images in production._

### Where can I get more details about how this works?

If you want to know more about how sealed images work (i.e. how we make bootable containers, UKI and composefs work together to create a verified boot chain), see the following presentations and documentation:

  * [“Signed, Sealed, and Delivered”, with UKIs and composefs, from Allison and Timothée at FOSDEM 2025][5]
  * [UKIs and composefs support for Bootable Containers, from Timothée at Devconf.cz 2025][6]
  * [UKI, composefs and remote attestation for Bootable Containers, from Pragyan, Vitaly and Timothée at ASG 2025][7]
  * [composefs backend documentation in bootc][8]



Thanks to all the contributors that made this possible, notably (but non exhaustively) from the following projects: [bootc][9] & [bcvk][10], [composefs][11] & [composefs-rs][12], [chunkah][13], [podman][14] & [buildah][15] and [systemd][16].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/sealed-atomic-desktops-test-images/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/04/sealed_atomic_bootable_images-816x345.jpg
[2]: https://unsplash.com/@steve_j?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/background-pattern-YA1J4FmBBeg?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://github.com/travier/fedora-atomic-desktops-sealed
[5]: https://archive.fosdem.org/2025/schedule/event/fosdem-2025-5191--signed-sealed-and-delivered-with-ukis-and-composefs/
[6]: https://pretalx.devconf.info/devconf-cz-2025/talk/739KGC/
[7]: https://media.ccc.de/v/all-systems-go-2025-362-uki-composefs-and-remote-attestation-for-bootable-containers
[8]: https://bootc-dev.github.io/bootc/experimental-composefs.html
[9]: https://github.com/bootc-dev/bootc
[10]: https://github.com/bootc-dev/bcvk
[11]: https://github.com/composefs/composefs
[12]: https://github.com/composefs/composefs-rs
[13]: https://github.com/coreos/chunkah
[14]: https://github.com/containers/podman
[15]: https://github.com/containers/buildah
[16]: https://github.com/systemd/systemd
