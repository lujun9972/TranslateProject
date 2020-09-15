[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (3 open source alternatives to Confluence)
[#]: via: (https://opensource.com/article/20/9/open-source-alternatives-confluence)
[#]: author: (Martin Loschwitz https://opensource.com/users/martinloschwitzorg)

3 open source alternatives to Confluence
======
BlueSpice, XWiki, and DokuWiki give you all the features of more popular
knowledge-management software without the proprietary limitations.
![Business woman on laptop sitting in front of window][1]

One of the most important things to do well in a modern enterprise is to collect company knowledge. Organizations need shared workspaces where individuals and teams can collaborate and share their experience and knowledge. This makes knowledge-management systems essential in today's agile environments.

Some companies use Confluence, others use GSuite, and still others use SharePoint. But they're all proprietary software, which means they don't offer their source code for you to audit or modify. If you are uncomfortable entering your company's shared knowledge into software that you don't own or control, the open source projects [BlueSpice][2], [XWiki][3], and [DokuWiki][4] are excellent alternatives.

There are many factors to consider when choosing an intranet. You want knowledge consolidated so that there's a single source of truth, and you want it to be available to everyone who requires access to it. Here are some of the most important things to look for in an intranet platform.

### Internal structure

Knowledge-management systems need to provide structure for internal content. A tool that randomly shuffles text and files together is nothing but a waste of time. Confluence supports _Spaces_ for individual topics and uses _Categories_ and _Subcategories_ within these spaces. Documents can be organized in a tree-like hierarchy, and there's access control for individual spaces, even down to individual documents.

BlueSpice follows a different approach. It's based on MediaWiki (the software that's been running Wikipedia for almost two decades now) and relies on _Namespaces_ for specific types of content. This can be confusing if you like to see the structure of your data, but it can be liberating if you prefer to classify data and leave the structure to interpretation. _Categories_ can be implemented easily to improve the visible structure for those that need it, but namespaces do not force a page into a certain area (as a Space in Confluence does).

XWiki's design somewhat combines the Confluence and BlueSpice approaches. The basic assumption is that all content resides in the same namespace within the wiki. The data is organized with _Nested Pages_, which are equivalent to Spaces in Confluence. But XWiki also supports sub-wikis for certain topics, which the administrator may not want to have at the top level.

DokuWiki relies on what it calls _Namespaces_, which resemble Categories in BlueSpice.

The difference in how data is stored on the hard drive and how it's presented to users is largely a matter of presentation. A well-organized workspace provides the same result from the user's perspective: easy-to-find data in a logical, domain-specific structure.

### Discoverability

A vital feature in knowledge-management software is the ability to search existing content.

BlueSpice relies on open source software for search and discoverability. One of the central differences between BlueSpice and its noble ancestor MediaWiki is that BlueSpice delivers [ElasticSearch][5] for internal content identification.

XWiki follows a similar path but with different components. It relies on [Apache Solr][6], which incorporates Apache's powerful, Java-based search and indexing engine [Lucene][7].

DokuWiki follows the KISS ("keep it super simple") principle. It stores its content in text files (rather than in a database) and uses an indexing application to keep track of updated content.

### Compliance

If you've ever worked at a large or regulated company, you know compliance is a vital part of infrastructure design. No enterprise can afford for its confidential material to fall into competitors' hands. Failure to protect customer-specific information may not only lead to a damaged reputation—in many parts of the world, including the European Union, it can also lead to fines that endanger the business. So the issue is establishing a basic ruleset to protect your data—and ensuring your knowledge-management tools support the numerous possible ways of accomplishing that.

Take user management, for instance. Most companies have a centralized user directory to ensure that access rights are automatically deleted when colleagues leave the company. Knowledge-management software must support such directories.

Another matter is corporate identity and design. This isn't directly related to security, but it's important to provide visual cues to users that a site is an authentic internal website. This makes themeability a requirement.

BlueSpice has full integration into LDAP and Active Directory. Groups and group membership can be (and in BlueSpice, actually must be) managed through the directory service. Themeability in BlueSpice allows the admin to change the look and feel of the platform, more or less completely (depending on how much time you want to spend customizing it). If BlueSpice's ancestry makes you imagine MediaWiki's austere design, have a look, because even the default theme is modern and appealing.

![BlueSpice][8]

(Markus Feilner, [CC BY-SA 4.0][9])

The same goes for XWiki, where LDAP and Active Directory support have been around for quite a while. New themes can be installed in XWiki through its Extension manager. They mostly allow you to adapt the colors that the software uses, which might be enough for many companies. If you need a full UI adaption, skins can help. They allow you to change CSS and velocity templates.

![XWiki][10]

DokuWiki is even easier to adapt to corporate identity guidelines. It uses a very simple site structure, so the look of your wiki can be adapted directly by editing its template. Its Secure LDAP (LDAPS) plugin enables it to connect to LDAP and Active Directory services.

![Slackermedia, a DokuWiki site][11]

Slackermedia uses DokuWiki (Markus Feilner, [CC BY-SA 4.0][9])

### Editors

The text editor people use to insert content into a knowledge-management system has a strong influence on the tool's overall acceptance among users, whether they're in a company or a community. People tend to prefer an editor that's versatile, mostly WYSIWIG ("what you see is what you get"), and intuitive.

BlueSpice comes with two editors. The first is the one people might know from Wikipedia. Some users will appreciate this, but people not familiar with wiki markup might find it underwhelming. For those users, BlueSpice has a visual editor available through the MediaWiki extension interface.

XWiki follows a similar path and features the basic XWiki editor, a WYSIWYG editor, and an inline-form editor.

DokuWiki is also up to the task with an editor plugin called [ProseMirror][12]. It features a WYSIWIG editor specifically written for DokuWiki using the ProseMirror framework, which is an online framework for writing editors, so DokuWiki's editor is not only beautiful but also highly functional.

### Extensions

A good solution gives the vast majority of what users need. A _great_ solution is extensible with plugins so that you can customize it to be what your users want.

BlueSpice comes with an extension store. It can also use plugins available for MediaWiki.

XWiki uses extensions for a number of things, such as installing themes or providing additional features, and it also has a separate extension store.

DokuWiki can be extended by the site administrator through its more than 1,300 plugins. This suggests to me that DokuWiki has the strongest ties to its open source community (although BlueSpice and XWiki are also perfectly valid open source projects).

### Use an open source intranet

BlueSpice and XWiki have a solid set of features and provide a user experience that enables users to share knowledge and collaborate in an intranet. DokuWiki follows a "back to the roots" approach by staying true, in form and function, to a typical wiki environment.

All three open source options include the major features supported by their proprietary alternatives. You can get support for running BlueSpice and XWiki from their respective vendors, and many companies provide third-party support for DokuWiki.

One way or another, open source software fulfills all the requirements to build a solid, well-working knowledge-management suite.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/open-source-alternatives-confluence

作者：[Martin Loschwitz][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/martinloschwitzorg
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/lenovo-thinkpad-laptop-concentration-focus-windows-office.png?itok=-8E2ihcF (Woman using laptop concentrating)
[2]: https://bluespice.com/products/bluespice-free
[3]: https://www.xwiki.org/xwiki/bin/view/Main/WebHome
[4]: https://www.dokuwiki.org/dokuwiki
[5]: https://opensource.com/life/16/6/overview-elastic-stack
[6]: https://lucene.apache.org/solr
[7]: https://lucene.apache.org
[8]: https://opensource.com/sites/default/files/uploads/bluespice.jpg (BlueSpice)
[9]: https://creativecommons.org/licenses/by-sa/4.0/
[10]: https://opensource.com/sites/default/files/xwiki.jpg (XWiki)
[11]: https://opensource.com/sites/default/files/uploads/dokuwiki.jpg (Slackermedia, a DokuWiki site)
[12]: https://prosemirror.net
