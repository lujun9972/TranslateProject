[#]: subject: "EPEL 8 Modularity is going away"
[#]: via: "https://fedoramagazine.org/epel-8-modularity-is-going-away/"
[#]: author: "Troy Dawson https://fedoramagazine.org/author/tdawson/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

EPEL 8 Modularity is going away
======

![][1]

Photo by [Sigmund][2] on [Unsplash][3]

EPEL 8 Modularity was set up shortly after the main EPEL 8 release. It attempted to use the Fedora module ecosystem with RHEL modules. The strange mixture of Fedora ecosystem and RHEL modularity never worked properly. There have been routine instances of modules that wouldn’t install, modules that overwrote RHEL modules, Fedora maintainers surprised their modules were in EPEL, and the constant issue that EPEL modules couldn’t depend on RHEL modules.

Many people have attempted to fix EPEL modularity over the years but none of these attempts have worked. At this point the EPEL Steering Committee is saying that the experiment with modules in EPEL has not worked. We are decommissioning EPEL 8 modularity.

### Decommission Plan

  * October 31, 2022
    * An updated epel-release will be pushed to the epel8 repo.
      * This sets “enabled = 0” for epel-modular, if you haven’t already changed your config.
      * epel-modular full name will have “DEPRECATED” in it.
  * February 15, 2023
    * The infrastructure for building and publishing epel8 modules will be removed.
    * The EPEL 8 modules will be archived and removed.
    * The mirror manager will be pointed to the archive.



### Archive Access

Systems will still be able to access archived modules, but their use is not recommended. The modules will not receive any further security or bug fixes.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/epel-8-modularity-is-going-away/

作者：[Troy Dawson][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/tdawson/
[b]: https://github.com/lujun9972
[1]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/10/EPEL_8_modularity_going_away-816x345.jpg
[2]: https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/ending?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
