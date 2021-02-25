[#]: subject: (How the oc debug command works in OpenShift)
[#]: via: (https://www.linux.com/news/how-the-oc-debug-command-works-in-openshift/)
[#]: author: (Kedar Vijay Kulkarni https://www.redhat.com/sysadmin/how-oc-debug-works)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

How the oc debug command works in OpenShift
======

How the oc debug command works in OpenShift

Try a new way to connect to and debug your Red Hat OpenShift Container Platform cluster nodes.
Kedar Vijay Kulkarni
Wed, 2/17/2021 at 12:40am

Image

Image by Dr StClaire from Pixabay

If you have used relatively recent versions of OpenShift, you must have come across the oc debug command (or you can check this man page). One of the interesting things about the new OpenShift is that it suggests not to use SSH directly (you can see this in sshd_config on the nodes because they have PermitRootLogin no set on them). So if you were to run oc debug node/node_name, it will create a pod for you and drop you in the shell (TTY) of this pod.

Topics:  
Linux  
Openshift  
[Read More][1] at Enable Sysadmin

--------------------------------------------------------------------------------

via: https://www.linux.com/news/how-the-oc-debug-command-works-in-openshift/

作者：[Kedar Vijay Kulkarni][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.redhat.com/sysadmin/how-oc-debug-works
[b]: https://github.com/lujun9972
[1]: https://www.redhat.com/sysadmin/how-oc-debug-works
