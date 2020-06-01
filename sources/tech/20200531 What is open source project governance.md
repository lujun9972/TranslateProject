[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (What is open source project governance?)
[#]: via: (https://opensource.com/article/20/5/open-source-governance)
[#]: author: (Josh Berkus https://opensource.com/users/jberkus)

What is open source project governance?
======
Clearly defining roles and responsibilities is essential to effective
open source community management. Here are some ways to help you
organize.
![Collaboration starts with communication amongst teams and across silos][1]

In many discussions of open source projects and community governance, people tend to focus on activities or resources like "speaking for the project" or "ownership of the web domain." While documenting these things is useful, they aren't truly governance matters. Alternately, others focus exclusively on technical matters like election rules, codes of conduct, and release procedures. While these might be the tools of governance, they're not governance itself.

So what exactly is open source project governance?

In short, governance is the rules or customs by which projects decide who gets to do what or is supposed to do what, how they're supposed to do it, and when.

This definition of governance can prompt important questions for open source communities seeking to evolve their governance models. Let's explore how.

### Defining governance

The above definition of governance is still a bit general, though, so let's get more specific. When you define governance for a project, you need to identify the following five things:

  1. What roles can contributors play in the project?
  2. What qualifications, duties, privileges, and authority are associated with each role?
  3. How do people get assigned to (and removed from) roles?
  4. How can role definitions be changed?
  5. What are the project's collected policies and procedures?



A good deal of activity in open source communities hinges on project roles. Every community has roles its contributors play, but, unfortunately, many projects don't formally define those roles and their responsibilities. Think of roles as the "jobs" each project participant has. One contributor can have more than one role, and many roles are shared by multiple contributors.

For example, "Lead Code Maintainer" is a role, as is "New Contributor" or "Meetup Organizer." While these roles are not written down, they're implicit in activities people are already engaged in (and potentially a source of argument). So the process of defining governance for a project is mostly the process of documenting roles, both the existing ones and the ones that the project should/will create.

### Know your role

As an example, a governance document might define the role of "Documentation Maintainer," which could be generally described this way:

  * Qualifications: several years contributing to documentation
  * Duties: write documentation and review other people's documentation
  * Privileges: speak for the documentation team, participate in development meetings
  * Authority: decide on document content, production toolchain, and strategy
  * Change procedure: all existing Documentation Maintainers vote on role changes



In reality, written role descriptions are much more detailed and explicit than that (some projects' formal role descriptions can run a dozen pages or more).

Additionally, some roles are collective—more about groups than individuals—and certain policies and procedures might apply to those collective roles. For example, there might be a "steering committee election procedure" that defines duties and privileges. And, of course, a code of conduct usually applies to all roles in the project.

This is where policies and procedures become important. Documented well, they explain how specific activities are supposed to be carried out by groups of roles. But they don't stand on their own; they require role descriptions in order to make sense. For example, imagine you want to write the election procedure for your steering committee. Before you can do that, you need to define both who is a voting member of the project and what steering committee members do.

Large open source projects can feature dozens or hundreds of potentially defined roles, particularly since each role will often have sub-roles as well. In Kubernetes, for instance, the role of Code Contributor is subdivided by Special Interest Group (SIG) and by contributor level (member, reviewer, approver, and owner). So someone's actual role is going to be "SIG-Network Approver," not just Code Contributor. Smaller projects, on the other hand, should define fewer roles and make their descriptions more general.

### Getting started

If your open source project or community's governance model is evolving—or if you're documenting or formalizing it for the first time—the community should ask itself the following questions to generate productive discussion:

  * What roles do project contributors play in this community?
  * Are these roles clearly defined or described?
  * Are those role definitions or descriptions accessible to everyone working on the project?
  * Do these role descriptions also explain how contributors can take on or leave the roles?



The questions seem straightforward—but the answers you'll receive are likely more complex than you anticipated.

_This article is adapted from_ [_The Open Source Way project_][2]_._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/5/open-source-governance

作者：[Josh Berkus][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jberkus
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/team-discussion-brainstorm-conference.png?itok=kb985JbR (Collaboration starts with communication amongst teams and across silos)
[2]: https://github.com/theopensourceway
