[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (The Enterprise Content Management System)
[#]: via: (https://theartofmachinery.com/2019/12/29/enterprise_cms.html)
[#]: author: (Simon Arneaud https://theartofmachinery.com)

The Enterprise Content Management System
======

A few years ago I worked on the version 2 of some big enterprise’s internal website. A smaller company had the contract, and I’d been subcontracted to deal with deployment and any serverside/backend changes.

The enterprise side had a committee to figure out lists of requirements. Committees are famously bad at coming up with simple and clear specs, and prone to bikeshedding. Thankfully, the company I was contracting with had a project manager who had the job of engaging with the committee for hours each day so that the rest of us didn’t have to. However, we still got a constant stream of inane change requests. (One particular feature of the site changed name three times in about two months.)

It was pretty obvious early on what was happening, so I integrated the existing website backend with a content management system (CMS) that had an admin panel with a friendly WYSIWYG editor. New features got implemented as plugins to the CMS, and old features got migrated as needed. We couldn’t make everything customisable, but eventually we managed to push back on several change requests by saying, “You can customise that whenever you want through the admin panel.”

So, we got things done to satisfaction and delivered, but there was one complication: using the admin panel and WYSIWYG editor. The committee members wouldn’t use it because they were ideas people and didn’t implement anything. The company had IT staff who managed things like websites, but they were hired as technical staff, not for editing website content. On the other hand, they had staff hired for writing copy, but they weren’t hired as website administrators.

So here’s how they ended up using the CMS: CMS data would get rendered as HTML by the website backend, which would then be exported to PDF documents by IT staff. The PDF documents would be converted to Word documents and sent to the writers via email. The writers would edit the documents and send them back to the IT staff, who would do a side-by-side comparison with the originals and then manually enter the changes through the graphical editor in the admin panel. All of the stakeholders were delighted to have a shiny version 2 of the website that had a bunch of new features, was highly customisable, integrated well with their existing processes and was all within budget.

Nowadays, when I’m designing something and I think it’s obvious how it will be used, I remind myself about that CMS and its user-friendly, graphical editor.
--------------------------------------------------------------------------------

via: https://theartofmachinery.com/2019/12/29/enterprise_cms.html

作者：[Simon Arneaud][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://theartofmachinery.com
[b]: https://github.com/lujun9972
