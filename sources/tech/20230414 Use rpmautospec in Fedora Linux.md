[#]: subject: "Use rpmautospec in Fedora Linux"
[#]: via: "https://fedoramagazine.org/use-rpmautospec-in-fedora-linux/"
[#]: author: "Zbigniew Jędrzejewski-Szmek https://fedoramagazine.org/author/zbyszek/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use rpmautospec in Fedora Linux
======

![][1]

Image of gears excerpted from [Aconcagua][2], [CC BY-SA 3.0][3], via Wikimedia Commons

Use the %autorelease and %autochangelog tags simplify package maintenance and make it easier to contribute packages to the Fedora Project. These rpmautospec tags cause no noticeable difference in the packages from the end user’s perspective. As of the Fedora Linux 38 release, package maintainers should use these new tags.

### Information about package history

Every package in a distribution carries identifying information. For example, the latest version of Firefox is available as _firefox-110.0-3.fc38.x86_64_. This can be unpacked as:

  * a name ( _firefox_ ),
  * a version ( _110.0_ ),
  * a “release tag”, consisting of a packaging release version + a distribution marker + an architecture tag ( _3.fc38.x86_64_ ).



In modern practice, the name and the version are supplied directly by the project upstream and unambiguously identify what was built. The release tag describes the downstream distro build (where, which distro, build count). This may sound natural, but in the past packagers would split parts of the upstream version into the release tag according to some rather complicated rules.

A package also contains useful information in its changelog.

Continuing with the Firefox example:

```

    $ rpm -q --changelog firefox-110.0-3.fc38.x86_64 | head -n5
    * Tue Feb 14 2023 Martin Stránský <stransky@redhat.com>- 110.0-3
    - Updated to 110.0 build 3

    * Mon Feb 13 2023 Martin Stránský <stransky@redhat.com>- 110.0-2
    - Added fix for orca

```

The changelog is created by package maintainers. It describes changes to the package that are relevant to a user. New software versions, modified file paths, and important bugfixs are examples of things that would be mentioned in the changelog. Whitespace changes in packaging scripts and other cleanups are examples of things that would _not_ be mentioned in the changelog. When things go well, users generally do not look at the changelog. However, the changelog is useful when a bug is found and people need to track down what changed, when, and why.

All this changelog information must be provided by the maintainer. When the maintainer builds a rpm package, they must provide this information in the appropriate fields of the package’s spec file.

For example, the _firefox.spec_ might look like this:

```

    Name: firefox
    Version: 110.0
    Release: 3%{dist}
    ...
    %changelog
    * Tue Feb 14 2023 Martin Stránský <stransky@redhat.com>- 110.0-3
    - Updated to 110.0 build 3

    * Mon Feb 13 2023 Martin Stránský <stransky@redhat.com>- 110.0-2
    - Added fix for orca
    ...

```

This is the traditional way. Every time the maintainer makes a new build, they update the number in the Release field and add a corresponding entry in the %changelog section. For example, for the 110.0-3.fc38 build, Martin would have changed Release: 2%{dist} → Release: 3%{dist} and added the first paragraph under %changelog.

Packages in Fedora are maintained using _git_. This means that after making changes to the package, and adding some text to the changelog, the maintainer would _also_ write a description of the changes in the git commit message. Often this is _exactly_ the same text as the changelog. For example, for the 110.0-3.fc38 build, Martin wrote “Updated to latest 110.0 upstream build” in the git commit message. It should be noted that every commit in git also contains a name, the email address of the author, and a timestamp for the change. If this sounds a bit repetitive, that’s because it is. Thankfully, some of this can now be automated.

### rpmautospec

The rpmautospec method takes advantage of the fact that the spec file is maintained in a _git_ repository:

```

    Name: firefox
    Version: 110.0
    Release: %autorelease
    ...
    %changelog
    %autochangelog

```

The purpose of the Release field is to identify the distro build number for a specific upstream Version. The Release field should be set to %autorelease and never changed again. The %autorelease macro provides a count of commits since the last commit that changed the Version field. This is nifty. Every time the packager changes the spec file, they have to make a commit to “save” the changes and do a build and the number in %autorelease will be incremented. When the Version is changed, the autorelease number is reset to 1.

The purpose of the git commit message is to summarize changes to the contents of the repository. The purpose of the %changelog section is to summarize changes to the package. The %autochangelog macro takes a git commit message, the author name, and the commit timestamp, and formats them in a way that is suitable for the %changelog section.

If Martin were to do another build, let’s say with a patch added, he would adjust the spec file adding a Patch line, and create a commit with:

```

    $ git commit -a -m 'Add patch to fix rhbz#1000002'

```

The %autorelease field would be automatically increased by one, and the %autochangelog text would now start with:

```

    * Thu Mar 23 2023 Martin Stránský <stransky@redhat.com>- 110.0-4
    - Add patch to fix rhbz#1000002

```

### What are the effects of the new workflow?

It is easiest to consider the effect **for the users** : **no change**. %autorelease and %autochangelog get replaced by “real” content _before_ the package is built, and the binary package downloaded by users looks exactly the same.

For the packager, there is less busywork. The Release field is constant and the git commit text is reused for the changelog. I’ve glossed over the details here, but the git commit text can contain parts which are not included in the changelog text. It can even have commits that are completely elided from the changelog.

This automation also makes some mistakes less likely. For example:

  * The maintainer makes changes, but forgets to bump Release, and the build fails because a previous build with the same version-release already exists.
  * The maintainer makes changes, but forgets to describe them in %changelog, and users don’t know what changed.
  * The maintainer makes a changelog entry, but writes Tue instead of Thu, and _rpm_ complains about an invalid date.



On the other hand, the packager has to be more disciplined. The text in the git commit message ends up visible to users. So it must be formatted accordingly. Every commit in git bumps the number in the release tag. The changelog is now formatted in the same specific style in all packages. Arguably, those are not huge limitations, but some adjustment of packager habits is required.

Using rpmautospec has a positive effect for external contributors. In Fedora, anyone who wants to contribute a change to the package is encouraged to open a pull request.

Unfortunately, for changes that touch the spec file, with traditional Release and %changelog, we have a conundrum. If the contributor _does not_ update those in their commit, the maintainer has to do this before the build, and effectively the contribution is incomplete. If the contributor _does_ update those in their commit, and the pull request is not merged immediately, it is likely that by the time it is merged
the Release number will be out of date, the date in the %changelog will be in the past, and the spec file may even already have entries with later dates, and git will _always_ show a merge conflict in the %changelog section.

With rpmautospec, all these problems go away. The release number is counted automatically. The date in the changelog is derived from the timestamp of when the patch was merged. And the changelog is generated from the stream of commits so there is no conflict to be had.

A specific variant of this contributor workflow occurs when the maintainer wants to copy (cherry-pick in git parlance) a commit to another branch. For example, because the important bugfix that was necessary in F38 also needs to be applied in F37, it is likely that, with rpmautospec, the commit can be applied without any changes to a different packaging branch.

### Wrap-up

%autorelease and %autochangelog have been available for a while, but have now reached a level where they work nicely for common maintenance patterns and a great majority of packages; even if some some complicated corner cases are not yet supported. With Fedora 38, rpmautospec is now the recommended method. Hopefully, we will have happier maintainers and contributors with no negative changes noted by the users.

For more information, see: [Changes/Rpmautospec_by_Default][4] and [Rpmautospec documentation][5]. For an example package that uses rpmautospec, see [python-sphinxcontrib-programoutput][6].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/use-rpmautospec-in-fedora-linux/

作者：[Zbigniew Jędrzejewski-Szmek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zbyszek/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/03/differential-816x345.jpg
[2]: https://commons.wikimedia.org/wiki/File:BAUMA_2004_ZF_Differentialgetriebe.jpg
[3]: https://creativecommons.org/licenses/by-sa/3.0
[4]: https://fedoraproject.org/wiki/Changes/Rpmautospec_by_Default
[5]: https://docs.pagure.org/fedora-infra.rpmautospec/
[6]: https://src.fedoraproject.org/rpms/python-sphinxcontrib-programoutput/commits/rawhide
