[#]: subject: "Proxmox Has a New Tool To Save Users From VMware"
[#]: via: "https://news.itsfoss.com/proxmox-vmware-migration/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Proxmox Has a New Tool To Save Users From VMware
======
Unhappy as a VMware customer? This makes it easy for you to switch to an
open-source virtualization solution.
Broadcom's acquisition of VMware introduced problems for its customers around the clock.

Things like:

  * [Broadcom selling VMware's end-user computing division][1]
  * [Changes to its cloud services affecting small businesses][2]
  * [Ditching perpetual licenses][3]



It has not been easy for VMware customers. Of course, unhappy customers will eventually migrate to some other service, preferably open-source ones to avoid vendor lock-in.

However, it is difficult to migrate.

Fortunately, Proxmox, an open-source alternative to VMware solutions, has introduced a **new import wizard** to make the migration easier.

### Proxmox's New Import Wizard for Migrating VMware ESXi Virtual Machines

The import wizard utilizes the storage plugin system for native integration into the API and web-based user interface.

The entire wizard will take you through the information you need to start the migration.

![][4]

To start with, you need to set up a new storage, making it the target for your import.

Your entire VMware ESXi will be mapped to all the necessary configurations for Proxmox VE's model, ensuring reduced downtime. The customers can use live-import as well, to migrate even faster.

But, the good thing is you do not have to re-configure things from scratch, which should save you some time as well.

Once the import finishes, you can tweak some advanced settings, including changing network interfaces, adding/removing CD/DVD drives, and more.

For all the technical details, you can refer to its [migration guide][5] and [documentation][6] on the import wizard.

Some important highlights include:

  * You need to update your Proxmox VE packages as per the mentioned [FAQ][7]
  * The import wizard was tested with VMware ESXi versions 6.5 through 8.0



The import wizard should be immensely useful for VMware customers who want to migrate as soon as possible with minimal downtime.

### VMware ESXi Customers Now Have an Easy Way Out

The wizard not only provides a good way to migrate, but this will help Proxmox solution to be a solid alternative to VMware, more than ever before.

It is definitely a relief for the customers who were worried about the downtime to move to another platform to continue their business and operations.

Considering it is a powerful open-source [virtualization solution][8], it is indeed good news.

_💬 What do you think of Proxmox's new import wizard? Are you migrating now? Share your thoughts in the comments below._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/proxmox-vmware-migration/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/broadcom-vmware-euc/
[2]: https://news.itsfoss.com/broadcom-vmware-continues/
[3]: https://news.itsfoss.com/vmware-broadcom-subscription/
[4]: https://news.itsfoss.com/content/images/2024/03/gui-import-wizard-general.png
[5]: https://pve.proxmox.com/wiki/Migrate_to_Proxmox_VE#Migration
[6]: https://pve.proxmox.com/pve-docs/chapter-qm.html#qm_import_virtual_machines
[7]: https://forum.proxmox.com/threads/new-import-wizard-available-for-migrating-vmware-esxi-based-virtual-machines.144023/
[8]: https://itsfoss.com/virtualization-software-linux/
