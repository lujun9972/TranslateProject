[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How a local government migrated to open source)
[#]: via: (https://opensource.com/article/20/8/linux-government)
[#]: author: (Hüseyin GÜÇ https://opensource.com/users/hguc)

How a local government migrated to open source
======
Eyüpsultan Municipality in Turkey gained flexibility, cost savings,
performance, and independence by transitioning its entire workforce to
GNU Linux and other open source software.
![A government building.][1]

In 2015, the Eyüpsultan Municipality in Istanbul, Turkey, began a bold migration to adopting open source software. This involved several major changes: [Linux][2] on the desktop and major changes to the IT infrastructure, including a transition to the [Zimbra][3] email server and the [PostgreSQL][4] database.

This was a big decision, and it wasn't made lightly. Open source technologies provide an important opportunity for our country to have an independent and secure information infrastructure. There are uncertainties about future terms and costs of using licensed software that connects users to a particular brand ecosystem. The more connected to these technologies we are, the harder it is to switch to alternative products. The commercial nature of key companies, to say nothing of pricing and licensing policies, poses significant risks.

As Eyüpsultan Municipality, we aimed to reduce service costs as well as external technology dependencies by using open source software, including the [Pardus GNU/Linux][5] operating system. Pardus was developed by the Turkish government as a desktop Linux distribution focused on graphical users in office settings. We wanted a solution that gave us an independent developer and increased sustainability, flexibility, and fiscal savings. In this respect, we consider our migration project to be a social responsibility. We are trying to create awareness of this goal by pioneering the use of Pardus in public institutions throughout Turkey.

### Educating users

We knew from the start that this migration to open source would be a major undertaking. People were used to the systems they'd been using for years, but we wanted to make the move easy and painless.

Therefore, we didn't change things without warning and communicating with our workers about our plans. We began our migration to open source in 2015 by training all our users on [LibreOffice][6] on Linux, as office productivity formed the bulk of the software they use on a daily basis. We considered this the first phase.

After the trainings, administrators installed the open source LibreOffice software to replace the licensed Microsoft Office software on all client computers. This decision to train users before installing the software minimized the problems they experienced when migrating from familiar software (including the operating system).

We didn't stop there, though. We let people settle in with LibreOffice for a year, and in 2016, we repeated the training on Linux and LibreOffice. Once users passed an exam at the end of the training, we installed Linux on their computers. We provided re-education to those who didn't pass the exam and then installed Linux upon success. So, the migration of the operating system began!

Providing training throughout the migration was one of our key strategies. We did not stop after delivering training; we checked back with our users to verify that the training produced the expected results. It took us a year to uncover all the things people struggled with after switching from Office to LibreOffice, but we welcomed these issues and helped to solve them whenever they arose.

In Eyüpsultan Municipality, we have always valued education in all areas of what we do. Migrating software was no different, and education was an integral part of the plan. I believe that regular training during our open source migration project was the _single most significant reason for its success_.

### Migration steps

We took a stepwise approach to the migration:

  * Analysis
  * Planning
  * ISO creation
  * Test
  * Pilot
  * Production



These steps may sound familiar, but there are two elements that were critical in making our project successful.

The first is **analysis**. We didn't just do technical analysis at this stage; we did psychological analysis at the same time. By talking to people, we tried to find out their anxiety points. We learned that there was a common fear of an "encounter with the unknown." We determined that if we could not calm this fear, the resistance to change would rise, even with the support of management behind us. After we realized this, we started to discuss how we could overcome this situation, and we decided to put a recognizable interface in front of users. During our research, we found a Windows-style theme and turned it into our default Linux window manager. The reaction we got on the first day of training was amazing, and I still smile when I think about it. Just a little bit of familiarity warmed people to the idea of what was technically, but not necessarily functionally, a change in the interface.

The second key element was creating a **custom ISO image file** of Pardus Linux. Pardus does have an ISO that you can download and install, but it includes many applications that we didn't need. It would waste time if we had to remove unnecessary applications and install our preferred enterprise applications after installation. Therefore, we reconfigured the Pardus GNU/Linux ISO to include our suite of enterprise applications. This reduced installation time to 15 minutes and made all the required enterprise applications ready for use immediately upon installation.

### Finishing touches

As the project matured, our management and monitoring requirements became clear. We installed the [Lider/Ahenk server][7] to manage our Pardus Linux clients. To monitor servers and clients, we installed the open source [Zabbix][8] application.

We wanted to ensure that the migration project was manageable and sustainable. So far, we've done a good job of it. We can now update hundreds of Pardus clients from a single point, provide remote support, implement policies, and detect problems early with alarms from Zabbix, which helps us develop solutions quickly.

### Introduce open source to your organization

Open source software has many advantages, including flexibility, high performance, major savings on licensing fees, independence from any particular company, and compliance with open standards. The benefits of open source software are recognized all over the world, especially in the European Union member countries, and similar action plans and studies are being used all over for transitioning to open source software.

Take what lessons you can from our experience, which is ongoing. Introduce open source as a viable option for your workplace. Take on the responsibility of delivering education on the knowledge required to use open source solutions. With open source, you never know what will become possible.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/linux-government

作者：[Hüseyin GÜÇ][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/hguc
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/government_building_sky.jpg?itok=-jSyhGAm (A government building.)
[2]: https://opensource.com/resources/linux
[3]: http://zimbra.org
[4]: https://www.postgresql.org/
[5]: https://en.wikipedia.org/wiki/Pardus_%28operating_system%29
[6]: https://www.libreoffice.org/
[7]: https://github.com/Pardus-LiderAhenk
[8]: https://www.zabbix.com/
