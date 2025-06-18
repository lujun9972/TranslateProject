[#]: subject: "Making sense of software licensing with FSFE REUSE: A beginner’s guide for open source developers"
[#]: via: "https://fedoramagazine.org/beginners-guide-for-open-source-developers-for-software-licensing-with-fsfe-reuse/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Making sense of software licensing with FSFE REUSE: A beginner’s guide for open source developers
======

![][1]

Logo: Copyright © 2025 Free Software Foundation Europe e.V.

Among the many details developers juggle, software licensing is often treated as an afterthought. We know we need it. However, faced with choosing the right license, tracking inherited code, and keeping things consistent, license management can feel like a bureaucratic burden.

Licensing is what makes the [REUSE project][2], maintained by the [Free Software Foundation Europe (FSFE),][3] such an interesting and important effort. It does not try to replace the legal work involved in choosing a license or deciphering obligations. Instead, **REUSE focuses on the mechanics of software licensing.** It addresses **how we communicate licensing clearly, unambiguously, and reliably in the code itself**. REUSE has been adopted by a [lot of projects already][4]. These include [SAP][5], [Nextcloud][6] and numerous Ansible community roles and collections.

I recently went down the licensing and supply chain rabbit hole myself. I had to figure out how to apply it to [open source projects I work on][7] and explain it to others. Thus, I had the unique experience of learning it from scratch while also teaching it. That process gave me insight into what makes REUSE helpful. I learned where the roadblocks are, and how you can start using it in your own open source work. So this article aims to give additional reasoning and insights for every day usage beyond the scope of a quick start tutorial.

### Why licensing still feels broken

If you’ve ever tried to make sense of licensing in a codebase with contributions from half a dozen sources, or tried to package software only to find ambiguous or conflicting license declarations, you’ve seen the brokenness first hand. It’s a common pain point.

You start coding. A _LICENSE_ file goes in the root. Maybe it’s [MIT][8], maybe [Apache 2.0][9], maybe [GPLv3-or-later][10]. We figure that’s enough. For the most part, tools like [Licensee][11] (which Github uses) will scan that file and report the project as single-licensed under whatever it finds.

But that is only part of the picture.

Real-world projects grow messy over time. Files come in from various places. Pull requests, upstream forks, old backups. Someone pastes in a script from Stack Overflow. Someone else uploads a code generator output. Over time, the repository becomes a tangle of files with unclear origins. The top-level _LICENSE_ file can’t speak for all of it any more. But the tools like licensee don’t know that, and often neither do the maintainers.

**If you provide code without clear licensing information, you make it hard for the open source ecosystem to collaborate with or consume your work**. Unfortunately, approaches to **automatic license detection can’t deliver the needed certainty**. They rely on fuzzy matching, heuristics, and assumptions (like there is “one license for the project”). This just does not cut it when legal clarity is required. Automatic license heuristics are complicated and will never deliver reliable results for all the possible use cases.

### FSFE REUSE to the rescue

Rather than trying to detect or infer licensing, REUSE asks developers to be explicit in a machine-readable, auditable way:

  1. [**There has to be a text copy of every used license**][12] below a _LICENSES/_ directory[1][13] in the root of the project.
  2. **Each file in your project must have[machine-readable copyright and licensing information associated][14] with it**.



Again: This matters. It means anyone—an auditor, a packager, a contributor, or a compliance team—can look at any file in your repository and immediately understand its legal status. There is no guessing, no cross-referencing, no “well maybe this falls under the MIT license because the rest of the project does.” It’s explicit. It’s standardized. And it is quickly [lintable][15] which is great for teams with [Continuous Integration][16].

Following REUSE, adding machine-readable copyright and licensing information can be done in the following ways:

  * **[Comment headers][17] or _< filename>.license_** for uncommentable files.
  * **[REUSE.toml][18]** , **a machine-readable copyright file** to address file and directory names. This is especially handy to define:
    * a default license for your project.
    * deviant licenses for third party artefacts residing in a sub-directory.



REUSE backs up its [specification][19] with a simple, focused, [_reuse_ command-line tool][20]. This makes adoption relatively painless (even though all can also be done manually). [REUSE fits nicely into the ecosystem][21], especially by relying on [Software Package Data Exchange (SPDX)][22] and [SPDX license identifiers][23].

### Usage

The [official REUSE tutorial][24] and the [tool usage section][25] is really good so I will just reproduce a quick start here:

  1. Put your licenses in the _LICENSES/_ directory.

  2. Add a comment header to each file that says something like

_SPDX-License-Identifier: GPL-3.0-or-later_
_SPDX-FileCopyrightText: $YEAR $NAME_

You can be flexible with the format, just make sure that the line starts with _“SPDX-License-Identifier:_ “ and/or _“SPDX-FileCopyrightText:_ “




#### Comment headers

[REUSE][26], and many organizations like [GNU][27], recommend including license header comments in source files as it helps to prevent confusion or errors. So even if the _REUSE.toml_ copyright file exists as the central place for licensing information, sometimes files get copied or forked into new projects and third parties might not have a well organized repository bureaucracy. Without a statement about what their license is, moving single files into another context might eliminate all trace of that information.

Example of a header comment:

```

    # SPDX-FileCopyrightText: Andreas Haerter, ACME Corp (https://example.com)
    # SPDX-License-Identifier: CC-BY-SA-4.0

```

One with [dual-licensing][28]:

```

    /*
      SPDX-FileCopyrightText: Jane Doe <j.doe@example.com>
      SPDX-License-Identifier: Apache-2.0 OR LGPL-2.1-or-later
    */

```

#### REUSE.toml

You might come to the conclusion that to skip adding headers to every file and only using a _REUSE.toml_ is better for your project … fair enough and that will still be compliant. It is also possible to [bulk-license whole directories][29] using this technique. The file format is [specified][18], but a simple example helps to get started:

```

    version = 1
    SPDX-PackageName = "Foo bar project"
    SPDX-PackageDownloadLocation = "https://git.example.com/foobar"
    SPDX-PackageSupplier = "ACME Inc. (https://example.com)"

    [[annotations]]
    path = "**"
    precedence = "closest"
    SPDX-FileCopyrightText = "ACME Inc."
    SPDX-License-Identifier = "LGPL-2.1-or-later"

```

#### Verification

Now verify your work using _[reuse lint][15]_ :

```

    $ reuse lint
    [...]
    Congratulations! Your project is compliant with version 3.4 of the REUSE Specification :-)

```

### Demo

The FSFE created a small screencast[2][30], which follows the [tutorial][31], making the [REUSE example repository][32] compliant:

![][33]

### Tips and tricks

#### Needed vocabulary when you start learning or teaching

To follow documentation and communication in the licensing space, it is important to know about the meaning of:

  * **[Software Package Data Exchange (SPDX)][22]** and [**SPDX license identifiers**][23]: A standard for identifying licenses using short, consistent identifiers (like _MIT_ or _GPL-3.0-only_ ). It simplifies license tracking and automation.
  * [**Software Bill of Materials (SBOM)**][34] **:** A structured list of all software components and their licenses in a project. It helps with transparency, security audits, and legal compliance.
  * **[Copyleft][35] (license):** A type of open source license that ensures derivative works remain under the same license. It protects user freedoms by requiring shared modifications. The GPL is a well-known example.
  * **Permissive (license):** A license that allows code to be reused with minimal conditions, including in proprietary software, without giving back modifications. Common examples include MIT, BSD, and Apache 2.0.
  * **TOML** : A configuration [file format][36]. _REUSE.toml_ (a machine-readable file in your project’s root directory) uses it to declare licensing information based on filename patterns.
  * **DEP5** : A machine-readable [debian/copyright file][37] which was [used before _REUSE.toml_][38]. DEP5, while still supported, has been deprecated since the introduction of REUSE.toml. This is important to know when hitting older documentation or tutorials.



#### My personal killer feature: Additional comments in REUSE.toml

It might sound trivial, but it was always cumbersome for me to keep track of the originally used download URLs and other common data around simple third-party files, like “this small icon there“. From my point of view, the _RESUE.toml_ file is the ideal place to keep additional data on third party files by using _SPDX-FileComment_ without cluttering the repository or the end-user documentation. If there is at least one example, in my experience, maintaining source information and reasoning for third-party files is quickly adopted even in teams without many regulations:

**Example 1:** [REUSE.toml with sections tracking the original download URLs or notes][39]

```

    [...]
    [[annotations]]
    path = "assets/images/window.svg"
    precedence = "closest"
    SPDX-FileCopyrightText = "2022 Refactoring UI Inc."
    SPDX-License-Identifier = "MIT"
    SPDX-FileComment = "https://github.com/tailwindlabs/heroicons/blob/master/optimized/24/outline/window.svg"

    [[annotations]]
    path = ["extensions/Find-WindowHandle.ps1", "extensions/Helper.ps1"]
    precedence = "closest"
    SPDX-FileCopyrightText = "2018 Grégoire Geis (https://github.com/71/Focus-Window/)"
    SPDX-License-Identifier = "MIT"
    SPDX-FileComment = "Slightly adapted for this project by foundata GmbH (https://foundata.com)"
    [...]

```

**Example 2:** The [REUSE.toml from SAP/openui5][40] which uses the file patterns and comments to keep track of single files copied from other projects:

```

    [...]
    [[annotations]]
    path = "src/sap.ui.integration/test/sap/ui/integration/demokit/cardExplorer/webapp/thirdparty/CfWorkerJsonSchemaValidator.js"
    precedence = "aggregate"
    SPDX-FileCopyrightText = "2020 Jeremy Danyow"
    SPDX-License-Identifier = "MIT"
    SPDX-FileComment = "these files belong to: @cfworker/json-schema"

    # Library: sap.ui.webc.common:
    [[annotations]]
    path = [
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/base/**",
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/theming/**",
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/localization/**",
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/icons/**",
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/icons-tnt/**",
        "src/sap.ui.webc.common/src/sap/ui/webc/common/thirdparty/icons-business-suite/**"
    ]
    precedence = "aggregate"
    SPDX-FileCopyrightText = "SAP"
    SPDX-License-Identifier = "Apache-2.0"
    SPDX-FileComment = "these files belong to: UI5 Web Components"
    [...]

```

#### README section template about licensing and copyright for humans

I find it useful to have a generic, easy to adapt text snippet for the _README.md_ or a comparable central place which is easy for humans to notice and read. I created and use the following template, taking advantage of the existing REUSE information to make the section basically maintenance free without being useless:

```

    ## Licensing, copyright

    <!--REUSE-IgnoreStart-->
    Copyright (c) YYYY, ACME Inc.

    This project is licensed under the GNU General Public License v3.0 or later (SPDX-License-Identifier: `GPL-3.0-or-later`), see [`LICENSES/GPL-3.0-or-later.txt`](LICENSES/GPL-3.0-or-later.txt) for the full text.

    The [`REUSE.toml`](REUSE.toml) file provides detailed licensing and copyright information in a human- and machine-readable format. This includes parts that may be subject to different licensing or usage terms, such as third-party components. The repository conforms to the [REUSE specification](https://reuse.software/spec/). You can use [`reuse spdx`](https://reuse.readthedocs.io/en/latest/readme.html#cli) to create a [SPDX software bill of materials (SBOM)](https://en.wikipedia.org/wiki/Software_Package_Data_Exchange).
    <!--REUSE-IgnoreEnd-->

```

Replace _YYYY_ with the year of the first release or [code contribution][41] and adapt the mentioned license, filenames and links as needed. The HTML comments prevent REUSE linting errors when e.g. listing multiple licenses.

The wording is already pointing to the copyright file ( _REUSE.toml_ ) and mentions that parts of the project might be subject to different licensing than the main one. If this is not good enough, feel free to adapt the wording of the main “licensed under” sentence to highlight the main licensing rules without the need to maintain every single bit outside of the copyright file. Examples (adapt as needed):

```

    The project is dual-licensed under the

    * GNU General Public License v3.0 or later (SPDX-License-Identifier: `GPL-3.0-or-later`), see [`LICENSES/GPL-3.0-or-later.txt`](./LICENSES/GPL-3.0-or-later.txt) for the full text.
    * Apache License 2.0 (SPDX-License-Identifier: `Apache-2.0`), see [`LICENSES/Apache-2.0.txt`](./LICENSES/Apache-2.0.txt) for the full text.

    [... usual template follows ...]

```

#### License detection on Github or Gitlab

If you follow REUSE, you will notice that Github and Gitlab are no longer able to detect licensing information for your repository.

Even if automatic licensing is broken _by design_ for the reasons outlined above, it is understood that it would be nice if all the broken license detection tools spit out _something_ , even unreliable but working, for indexes and searches (for the sole reason of not having a disadvantage if inexperienced users are searching for projects and filter by often broken meta data).

If you need this, put the stated “license with the highest freedom protections” just for search-indexes and GitHub in a _LICENSE_ or _COPYING_ file in the root directory of your project:

  1. [GitHub uses Licensee][42] to attempt to identify the license of a project and [Licensee does not support the REUSE specification][43].
  2. A workaround to fix the automatic license detection of GitHub and [others][44] is to place an _additional_ _LICENSE_ or _COPYING_ file in the root directory of your project. This is [allowable by REUSE][45]. These files are explicitly [ignored by the toolset][46] and do not need an additional *.license *****file or header.
  3. If you want to prevent a duplication of License texts, beware of another issue with Licensee: You can place a symlink at _LICENSES/ <your license>.txt_ pointing to the _LICENSE_ or _COPYING_ file in the project’s root directory. _reuse lint_ will follow that link. [Licensee sadly does not even support symlinks][47], so a more logical symlink from _LICENSE_ or _COPYING_ pointing to _LICENSES/ <your license>.txt_ is not solving the issue. I therefore recommend a real _copy_ instead of a symlink to keep things accessible when using the workaround.



I, for myself, would use this workaround _only_ if a single license is used for all of the project’s files. This would prevent misunderstandings or conflicts and simply ignore GitHub’s limited behavior in all other cases.

#### Years in copyright texts

This is not exactly a REUSE topic but I noticed it is discussed quite a lot when a project starts adopting REUSE. [IANAL][48], but it is not _necessary_ to update the copyright year since the main legal intention is to state the year of the first public release or code contribution. But it is common to do so anyway, especially since it shows third parties that a project is still alive.

I usually propose the following which might also be a useful technique for your project:

  * Update the copyright data but maintain the copyright year only at central places like a project’s _README.md_ reduce the maintenance effort.
  * Simply add each year with a release or updates separated by commas. You can use a timespan ( _yearX-yearY_ ) for multiple subsequent years.
  * Example:
    * The first release and copyright statement was _Copyright (c) 2013._
    * There were releases or updates in several but not all years afterwards:
      * 2023 → Copyright (c) 2013, 2015, 2018-2021, 2023.
      * 2015 → Copyright (c) 2013, 2015.
      * 2018 → Copyright (c) 2013, 2015, 2018.
      * 2019 → Copyright (c) 2013, 2015, 2018, 2019.
      * 2020 → Copyright (c) 2013, 2015, 2018-2020.
      * 2021 → Copyright (c) 2013, 2015, 2018-2021.



### Conclusion

Licensing clarity is needed for sustainable collaboration in open source. The REUSE specification doesn’t try to replace legal frameworks or licensing decisions, but it makes the messy practicalities of license management predictable, explicit, and automatable.

Adopting REUSE can feel like extra effort at first, especially for existing codebases. But once in place, it pays off by making your project easier to understand, maintain, package, and … reuse… 🙂 . REUSE helps you express the legal structure of your project in a way that machines and humans can agree on. And that’s worth a lot.

  1. Using the _LICENSES/_ directory is also recmmended by the [CII best practices][49], and implemented by the [Linux Kernel][50]. [↩︎][51]
  2. Source: <https://download.fsfe.org/videos/reuse/screencasts/reuse-tool.gif>, Copyright © 2001-2025 [Free Software Foundation Europe][3], Verbatim copying and distribution is permitted in any medium, provided this notice is preserved. [↩︎][52]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/beginners-guide-for-open-source-developers-for-software-licensing-with-fsfe-reuse/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/06/FSFE_REUSE-816x345.jpg
[2]: https://reuse.software/
[3]: https://fsfe.org/
[4]: https://api.reuse.software/projects
[5]: https://github.com/SAP/openui5/blob/master/REUSE.toml
[6]: https://github.com/nextcloud/server/blob/cf1eed2769d928f4a7fe4543d51994331701f2d9/.reuse/dep5
[7]: https://github.com/foundata/
[8]: https://choosealicense.com/licenses/mit/
[9]: https://choosealicense.com/licenses/apache-2.0/
[10]: https://foundata.com/en/blog/2024/use-gpl-or-later/
[11]: https://github.com/licensee/licensee
[12]: https://reuse.software/spec-3.3/#license-files
[13]: tmp.dGQMH96QkL#1704ca3d-15ad-43cf-a89b-45678a103fed
[14]: https://reuse.software/spec-3.3/#licensing-information
[15]: https://reuse.readthedocs.io/en/stable/man/reuse-lint.html
[16]: https://en.wikipedia.org/wiki/Continuous_integration
[17]: https://reuse.software/spec-3.3/#comment-headers
[18]: https://reuse.software/spec-3.3/#reusetoml
[19]: https://reuse.software/spec/
[20]: https://github.com/fsfe/reuse-tool
[21]: https://reuse.software/comparison/
[22]: https://spdx.dev/
[23]: https://github.com/david-a-wheeler/spdx-tutorial/blob/master/README.md#spdx-license-identifiers
[24]: https://reuse.software/tutorial/
[25]: https://github.com/fsfe/reuse-tool#usage
[26]: https://github.com/fsfe/reuse-docs/issues/117#issuecomment-1306963966
[27]: https://www.gnu.org/licenses/gpl-howto.html.en#why-license-notices
[28]: https://reuse.software/faq/#multi-licensing
[29]: https://reuse.software/faq/#bulk-license
[30]: tmp.dGQMH96QkL#45e4848d-f6a1-416b-b55a-a9a6de444074
[31]: https://reuse.software/tutorial
[32]: https://github.com/fsfe/reuse-example/
[33]: https://fedoramagazine.org/wp-content/uploads/2025/06/reuse-tool.gif
[34]: https://about.gitlab.com/blog/2022/10/25/the-ultimate-guide-to-sboms/#what-is-an-sbom%3F
[35]: https://en.wikipedia.org/wiki/Copyleft
[36]: https://toml.io/en/v1.0.0
[37]: https://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
[38]: https://reuse.software/faq/#dep5-history
[39]: https://github.com/foundata/chocolatey-usewindow.extension/blob/78f22260526a319e83e62456922bb482564f1e41/REUSE.toml#L22-L34
[40]: https://github.com/SAP/openui5/blob/7ff18ab1ded47570228b5fc6c3da1ad135d6bc3e/REUSE.toml#L539-L561
[41]: https://reuse.readthedocs.io/en/latest/scripts.html#starting-point-of-the-codebase
[42]: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository#detecting-a-license
[43]: https://github.com/licensee/licensee/issues/490
[44]: https://forum.openmod.org/t/reuse-incompatible-to-auto-detection-of-license-s/3590
[45]: https://reuse.software/faq/#tradition
[46]: https://github.com/fsfe/reuse-tool/blob/0e111c423ccf927f73a9ae7b39d3f88268b015b9/src/reuse/__init__.py#L66-L77
[47]: https://github.com/licensee/licensee/pull/42
[48]: https://en.wikipedia.org/wiki/IANAL
[49]: https://github.com/coreinfrastructure/best-practices-badge/blob/main/docs/criteria.md#license_location
[50]: https://github.com/torvalds/linux/tree/master/LICENSES
[51]: tmp.dGQMH96QkL#1704ca3d-15ad-43cf-a89b-45678a103fed-link
[52]: tmp.dGQMH96QkL#45e4848d-f6a1-416b-b55a-a9a6de444074-link
