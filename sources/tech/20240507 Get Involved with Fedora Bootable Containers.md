[#]: subject: "Get Involved with Fedora Bootable Containers"
[#]: via: "https://fedoramagazine.org/get-involved-with-fedora-bootable-containers/"
[#]: author: "jasonbrooks https://fedoramagazine.org/author/jasonbrooks/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Get Involved with Fedora Bootable Containers
======

![][1]

Photo by [Jeremy Thomas][2] on [Unsplash][3]

For quite a while now, we’ve had image-based Fedora Linux variants—starting with [Fedora Atomic Host and Atomic Desktop][4]. The original variants evolved into [Fedora CoreOS][5], [Fedora IoT][6], a whole family of [Fedora Atomic Desktops][7], and the awesome [Universal Blue][8] project. Bootable containers make it much simpler to create and collaborate on image-based Fedora systems. Here’s how you can get involved.

If you’ve used one of these image-based Fedora systems, you know how easy they are to update, upgrade, or, if things aren’t working quite right, to roll back. However, creating your own custom image-based Fedora system has always been a bit tricky, requiring special tools, processes and infrastructure.

Over [the past couple of years][9], the tools and methods available for building image-based systems in Fedora have evolved. They now natively support OCI/Docker containers as a transport and delivery mechanism for operating system content.

With these changes, and the introduction of [bootc][10], we now have the tools to build image-based systems using ordinary Containerfiles and regular OCI-container build tools. We also have the infrastructure to define, build, deploy and manage Linux systems.

For instance, the Fedora IoT WG [has plans to deliver][11] two bootc containers for Fedora IoT users. There is a cut down minimal version for users to use as a base to build their own vision of Fedora IoT. There is also a second image to deliver the traditional Fedora IoT user experience.

### Taking the Initiative

We have a great opportunity to enhance collaboration among image-based Fedora variants, and to empower other projects and individual users to create their own Fedora-based derivatives by working together on [bootable container technologies][12].

That’s why I’m excited to announce that we’ve proposed a new [Fedora Community Initiative][13] to seize this opportunity. This initiative aims to bring together the Fedora working groups that build and promote image-based Fedora variants.

The contributors working on the [proposed initiative][14] will:

  * Identify opportunities to share base images
  * Identify and work through Fedora Infra issues
  * Document use of bootable container tools and processes
  * Promote the use of Fedora bootable containers with blog and mailing list posts, social media, and coordination with Fedora Marketing Team
  * Reach out to projects outside of Fedora proper that might want to collaborate



Check out the initiative wiki page for more information. You can learn who to reach out to if you’d like to get involved in the effort, in the context of one of the Fedora variants. You can also join the discussion on Fedora’s matrix instance in the [fedora-bootc][15] room, or on Fedora discussion by following or posting with the [bootc-initiative tag][16]. Finally, check out this [doc page][17] to kick the tires on Fedora bootc for yourself.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/get-involved-with-fedora-bootable-containers/

作者：[jasonbrooks][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jasonbrooks/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/Bootable_containers-816x345.jpg
[2]: https://unsplash.com/@jeremythomasphoto?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/blue-and-purple-galaxy-digital-wallpaper-E0AHdsENmDg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoraproject.org/wiki/Atomic_WG
[5]: https://fedoraproject.org/coreos/
[6]: https://fedoraproject.org/iot/
[7]: https://fedoraproject.org/atomic-desktops/
[8]: https://universal-blue.org/
[9]: https://fedoraproject.org/wiki/Changes/OstreeNativeContainer
[10]: https://containers.github.io/bootc/
[11]: https://fedoraproject.org/wiki/Changes/Fedora_IoT_Bootable_Container
[12]: https://containers.github.io/bootable/
[13]: https://docs.fedoraproject.org/en-US/project/initiatives/
[14]: https://discussion.fedoraproject.org/t/fedora-council-tickets-ticket-492-new-initiative-fedora-bootc/116062
[15]: https://matrix.to/#/#bootc:fedoraproject.org
[16]: https://discussion.fedoraproject.org/tag/bootc-initiative
[17]: https://docs.fedoraproject.org/en-US/bootc/
