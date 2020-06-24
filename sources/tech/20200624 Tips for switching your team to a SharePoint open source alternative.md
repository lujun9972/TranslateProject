[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Tips for switching your team to a SharePoint open source alternative)
[#]: via: (https://opensource.com/article/20/6/mediawiki)
[#]: author: (Will Kelly https://opensource.com/users/willkelly)

Tips for switching your team to a SharePoint open source alternative
======
The open source wiki platform behind Wikipedia is a compelling
alternative to Confluence, SharePoint, and other proprietary
collaboration solutions.
![Teamwork starts with communication across silos][1]

[MediaWiki][2] is many IT professionals' first exposure to wikis. By virtue of being the platform behind Wikipedia, MediaWiki's familiarity makes it a compelling open source alternative to proprietary technology like Atlassian Confluence, which is common with developers, and SharePoint, the default corporate collaboration platform.

If you would like to bring MediaWiki into your organization but aren't sure how to begin, I hope the following best practices I've learned as a regular MediaWiki user will help you get started.

### Tips for introducing MediaWiki to the organization

There are multiple angles to approach a team about a new technology. Here are two points to keep in mind.

#### Sell the value of MediaWiki

Email inboxes and group chat aren't made for managing information and content—even if some teams aren't aware of or refuse to admit it. The gaps between team members' knowledge (and the "pockets" of knowledge it creates) inevitably lead to collaboration pitfalls. This makes it a good time to sell enterprises on the value of MediaWiki and other open source collaboration alternatives. Think about an email inbox: if I have some information I want others to have, I have to email every person who may ever need it. That is impractical as people join and leave the organization. There has to be a better solution, and the first step is acknowledging the problem.

#### Pitch the low cost of open source software

Make sure to sell the value of open source to your IT and security stakeholders. Given the budget crisis some enterprises are in, no-subscription contracts are very alluring. Strained IT budgets make a no-subscription collaboration solution mighty handy when you need a solution _now,_ not after waiting through a lengthy procurement cycle. And MediaWiki can provide an immediate solution to collaboration challenges for newly remote workforces.

Open source software is certainly more than the price tag, and it's not free to manage in the long run, but I have had good success with this pitch in getting my team to try it out. Being able to try Mediawiki for free can be enough to get it into consideration. Doubly so, if you have your own staff administering the wiki for your users. If you've come to Mediawiki to satisfy an immediate need you'll still need to plan for long term operations and maintenance of the wiki.

Also, informing management and other stakeholders that you already have MediaWiki in-house but aren't yet using it shows you're trying to make the most of your company's resources.

### Making MediaWiki work for your team

There are some key features to keep in mind as you adopt MediaWiki. Here are my top picks. 

#### 1\. Install MediaWiki in the cloud

If you're moving to MediaWiki as a collaboration option for your newly remote workforce, it's best to install the wiki in the cloud infrastructure your organization already owns or uses. If you expect your wiki will be image-heavy, look into the [extensions][3] that enable MediaWiki to use cloud resources to store images.

There's also a version of MediaWiki [certified by Bitnami][4] available in the AWS Marketplace. The benefit of using this version is AWS and Bitnami have set it up so you can figure out operating costs based on your configuration. That's a win for corporate adoption.

Finally, if your IT security team is pushing back against installing MediaWiki from the public web, MediaWiki support is available from the Azure Marketplace. Although it's not open source, it enables Active Directory on MediaWiki, which allows your organization's administrators to easily sync its users and control permissions.

#### 2\. Enable file uploads prior to launch

Enterprise teams often store and version-control project documents in collaboration platforms. But MediaWiki is best known for content creation and not as a file repository. Although file uploads are a commonly used feature in MediaWiki, the feature is disabled by default in all current release versions. However, MediaWiki can be used as a file repository by [enabling manual file uploads][5] before you make your wiki live for your users.

#### 3\. Note that ability to view page history

MediaWiki makes it easy to track your wiki pages' editing history. Click on **View History** on the top-right of any page, and it will display the page's revision history.

![MediaWiki revision history][6]

(Will Kelly, [CC BY-SA 4.0][7])

Knowing a wiki page's revision history—and being able to roll back changes—can be helpful. If you or a co-worker makes a mistake, it's easy to recover from an error.

#### 4\. Keep Summaries of changes

Wikis can take on a life of their own when people start creating content. Wikis for remote teams can be all-hours affairs for prolific project teams, and changes can take place any time of day or night on an active wiki. It's helpful for users to enter a short (less than 255 characters) summary of any change in the **Summary** box below the editing pane before clicking **Save Changes**. The summary appears alongside the edit. This best practice helps keep an audit trail of content changes, even if the summary is something as simple as "Updated links."

![MediaWiki change summary][8]

(Will Kelly, [CC BY-SA 4.0][7])

#### 5\. Watch important pages

Project team members can update wiki pages any time of day, even if teams are in the same time zone. That's great for remote collaboration, but it can be a challenge to keep up with changes. Be sure to choose to watch important pages, so updates are clearly visible to you. You can also get emails on every update to see the wiki evolve over time.

### MediaWiki to the rescue

Deploying MediaWiki as a complete collaboration solution (or using it to augment SharePoint for your remote team) is an economical option, but it takes some planning and forethought to make it an effective solution. What MediaWiki best practices do you recommend?

Reid Serozi ( @reidserozi ), founder of TriangleWiki , explains how the project was created from...

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/mediawiki

作者：[Will Kelly][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/willkelly
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/happy-team-sticker-laptop.png?itok=91K77IgE (Teamwork starts with communication across silos)
[2]: https://www.mediawiki.org/wiki/MediaWiki
[3]: https://www.mediawiki.org/wiki/Extension:AWS#Why_is_this_needed
[4]: https://bitnami.com/stack/mediawiki
[5]: https://www.mediawiki.org/wiki/Manual:Configuring_file_uploads
[6]: https://opensource.com/sites/default/files/uploads/mediawiki_revisions.png (MediaWiki revision history)
[7]: https://creativecommons.org/licenses/by-sa/4.0/
[8]: https://opensource.com/sites/default/files/uploads/mediawiki_summary.png (MediaWiki change summary)
