[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to encrypt a single Linux filesystem)
[#]: via: (https://www.linux.com/news/how-to-encrypt-a-single-linux-filesystem/)
[#]: author: (Peter Gervase https://www.redhat.com/sysadmin/encrypt-single-filesystem)

How to encrypt a single Linux filesystem
======

How to encrypt a single Linux filesystem

Sure, you can manually encrypt a filesystem. But, you can also automate it with Ansible.
Peter Gervase
Mon, 12/7/2020 at 4:52pm

Image

Photo by PhotoMIX Company from Pexels

There are a few different reasons that you might want to encrypt a filesystem, such as protecting sensitive information while it’s at rest, not having to worry about encrypting individual files on the filesystem, or other reasons. To manually encrypt a filesystem in Red Hat Enterprise Linux (RHEL), you can use the cryptsetup command. This article will walk you through how to use Ansible to do this for you for a RHEL 8 server.

Topics:  
Linux  
Linux Administration  
Security  
[Read More][1] at Enable Sysadmin

--------------------------------------------------------------------------------

via: https://www.linux.com/news/how-to-encrypt-a-single-linux-filesystem/

作者：[Peter Gervase][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.redhat.com/sysadmin/encrypt-single-filesystem
[b]: https://github.com/lujun9972
[1]: https://www.redhat.com/sysadmin/encrypt-single-filesystem
