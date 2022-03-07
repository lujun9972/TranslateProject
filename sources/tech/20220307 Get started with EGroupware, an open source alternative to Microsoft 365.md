[#]: subject: "Get started with EGroupware, an open source alternative to Microsoft 365"
[#]: via: "https://opensource.com/article/22/3/open-source-egroupware"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Get started with EGroupware, an open source alternative to Microsoft 365
======
EGroupware is an open source groupware solution that runs in your
favorite web browser.
![Working on a team, busy worklife][1]

A groupware solution is a must-have, whether you're working in a small organization, a medium-sized company, or a large enterprise. It promotes collaboration and glues teams together. Are you looking for an open source alternative to the big players? Maybe [EGroupware][2] can replace Microsoft 365 or Google Workspace in your team soon.

This article shows how to install EGroupware on your own server and how to set up the groupware solution for your organization. It also gives a brief introduction to EGroupware's modules and applications. I'll provide tips and tricks for the administration of EGroupware in a future article.

### Smart online office

The software by the German company of the same name has been around for more than 20 years. Apart from its own modules, EGroupware integrates other well-known open source applications, including [Collabora Online][3], [Rocket.Chat][4], [Guacamole][5], [Jitsi][6], and [BigBlueButton][7]. The groupware also supports computer telephony integration (CTI) with [Asterisk/Placetel][8].

**[ Read also: [5 open source alternatives to Zoom including Jitsi and BigBlueButton][9] ]**

![EGroupware calendar][10]

(Heike Jurzik, CC BY-SA 4.0)

EGroupware offers two editions:

  * The free Community Edition (CE) is developed under the GPLv2 and contains basic functions without limitations.
  * The Enterprise Line (EPL) offers additional features and applications, especially for companies or large organizations, and extended vendor support.



It's not complicated to set up EGroupware on your own server. In fact, the EGroupware installer does all the work for you. The software doesn't require a lot of hardware resources, either. For example, 2 GB RAM and 32 GB disk space on a dual-core machine are acceptable for 80 simultaneous users. EGroupware also runs nicely on virtual servers, a local VM, or a NAS.

If you're not too keen on hosting the software yourself, EGroupware provides a SaaS solution hosted in German data centers. Are you living abroad and outside of Europe? No problem, [contact][11] the EGroupware team for ideas and help.

### Install EGroupware

Let's get started! You don't need much to [install EGroupware][12] yourself—a Linux system and basic Linux knowledge are sufficient. You should at least be familiar with your package manager, which you can use to install the `egroupware-docker` package. The install scripts provided by EGroupware are for the open source Docker components specifically, so while other container engines (such as Podman, LXC, or CRI-O) should work, they're not officially supported.

The post-installation scripts take care of the actual install, pulling in dependencies like Docker, Nginx (once as a reverse proxy, once as a web server running EGroupware), and MariaDB. Various configuration and log files also end up on the server. If you'd like to replace Nginx with Apache as a reverse proxy, you can add the `apache2` package instead.

Almost all components, including the EGroupware web server (not the [reverse proxy][13]), the database server, the EGroupware push server (web socket for real-time updates in the browser window), Watchtower (automatic updates for containers), Collabora Online, Guacamole, Rocket.Chat, and so on, are stored in separate containers. This design allows the developers to ensure that installing and upgrading EGroupware is as painless as possible.

**Note**: Please take the time to set up SSL certificates for EGroupware to ensure the communication between the web browser and the EGroupware server is encrypted. If you want to synchronize data between the groupware and an iOS device, SSL encryption is mandatory. Likewise, SSL is required by some external applications such as Collabora Online.

![Reverse proxy encryption][14]

(Heike Jurzik, CC BY-SA 4.0)

### Access EGroupware

Right, so you've installed EGroupware—how can you access the software? Well, that's easy, as EGroupware works in most modern web browsers, including Firefox, Chrome/Chromium, Safari, and Microsoft Edge. In fact, it also looks good on mobile devices.

![EGroupware on a mobile device][15]

(Heike Jurzik, CC BY-SA 4.0)

Apart from that, the EGroupware team offers a special [mobile template][16]. Then again, if you're anything like me and don't like fiddling with a smartphone browser, you'll probably be glad to hear that it's easy to sync your data between EGroupware and your mobile devices. EGroupware supports [several protocols][17], such as ActiveSync, CardDAV, CalDAV, and WebDAV.

### EGroupware modules and applications

Are you ready to get to work and look into the single EGroupware modules and applications? After logging in, you'll see all available modules and applications in the left sidebar, such as Mail, Calendar, Address Book, InfoLog Project Manager (to-dos/tasks), Time Sheet, Tracking System, Kanban, File Manager, and more.

My favorite application is the InfoLog module. This is EGroupware's Swiss Army Knife. It's where you define simple to-do lists, complex tasks, set due dates, and delegate tasks to other users. The InfoLog also helps you stay up-to-date as it can notify you and your colleagues about changes. The InfoLog is fully customizable and lets you create your own data fields, task types, categories, and templates. Furthermore, you can control who has access to tasks and define permission to read, edit, or delegate. If required, it's possible to encrypt the contents.

![EGroupware InfoLog][18]

(Heike Jurzik, CC BY-SA 4.0)

A click on one of the modules in the left sidebar opens a new tab inside the browser window with the application itself. In almost all modules, you can access a context menu (right mouse button) which offers additional functions and sometimes connections to other EGroupware modules. For example, the File Manager's context menu shows entries for creating new documents and folders and converting documents to PDF or PNG. Additionally, you can send documents via email or create links for collaborative editing in the submenu Share.

The top right corner shows a button to switch between light and dark mode, icons for printing, and Quick Add (shortcut for adding new entries to the calendar, address book, etc.). Next to the Notifications icon is your User menu, which opens the Home screen, your personal Preferences, a dialog for changing your password, and a button to log out. Finally, the right sidebar shows avatars for other users. Right-click on one of the icons to open another context menu that offers to call someone or invite the user to a new or existing call (Jitsi or BigBlueButton), send a message (Rocket.Chat) or an email, and so on.

![EGroupware InfoLog context menu][19]

(Heike Jurzik, CC BY-SA 4.0)

### Explore EGroupware

Finally, I want to finish this introduction with a pointer to the EGroupware [community forum][20]. Here you'll find announcements, technical guides, quick howtos, and discussions in various languages.

In another article, I'll look into the administration side of EGroupware: How to configure administrative access to your EGroupware installation, how to adjust its look and feel, and how to manage users and groups.

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/open-source-egroupware

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/team_dev_email_chat_video_work_wfm_desk_520.png?itok=6YtME4Hj (Working on a team, busy worklife)
[2]: https://www.egroupware.org/
[3]: https://www.collaboraoffice.com/collabora-online/
[4]: https://opensource.com/article/22/1/rocketchat-data-privacy
[5]: https://guacamole.apache.org/
[6]: https://meet.jit.si/
[7]: https://bigbluebutton.org/
[8]: https://github.com/EGroupware/egroupware/wiki/CTI---Computer-Telephone-Integration
[9]: https://opensource.com/article/21/9/alternatives-zoom
[10]: https://opensource.com/sites/default/files/egroupware-calendar.png
[11]: https://www.egroupware.org/en/contact
[12]: https://github.com/EGroupware/egroupware/wiki
[13]: https://www.redhat.com/sysadmin/setting-reverse-proxies-nginx
[14]: https://opensource.com/sites/default/files/reverseproxy-encrypt.png
[15]: https://opensource.com/sites/default/files/egroupware-mobile.png
[16]: https://www.egroupware.org/en/mobil-access
[17]: https://www.egroupware.org/en/synchronisation
[18]: https://opensource.com/sites/default/files/egroupware-infolog.png
[19]: https://opensource.com/sites/default/files/infolog-context-menu.png
[20]: https://help.egroupware.org/
