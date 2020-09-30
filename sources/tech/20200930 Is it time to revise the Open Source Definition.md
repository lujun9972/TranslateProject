[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Is it time to revise the Open Source Definition?)
[#]: via: (https://opensource.com/article/20/9/open-source-definition)
[#]: author: (Richard Fontana https://opensource.com/users/fontana)

Is it time to revise the Open Source Definition?
======
Recent developments may strengthen the case for exploring improvements
to the OSD.
![A gavel.][1]

The [Open Source Definition][2] (OSD), maintained by the [Open Source Initiative][3] (OSI), is a foundational pillar of the open source movement. The OSI's view is that software validly labeled "open source" must be made available in a manner that satisfies the 10 criteria set forth in the OSD, all but one of which pertain to licensing terms.

Through its [license review process][4], the OSI determines whether a submitted license is OSD-conformant. Widely recognized as authoritative, the OSD is commonly invoked in contractual language and has been referenced in statutes and regulations. The OSD was drafted and adopted by the OSI shortly after its founding in 1998. It is essentially a rebranding of the [Debian Free Software Guidelines][5] (DFSG) with relatively minor changes. It has been amended only once, in 2002, with the addition of a tenth plank ("License must be technology-neutral").

The stability of the OSD text reflects a more general conservatism in the treatment of important legal texts in the open source community. Widely adopted open source licenses, which have been called "[constitutions of communities][6]," are seldom revised, in part because of practical and political obstacles. The OSD seems more analogous to a true constitutional text than any given OSD-conformant license, and of course, constitutions are revised less often than the ordinary laws they authorize. The difficulty of revising open source licenses is problematic—it arguably raises the costs of [adverse judicial interpretation][7] in license-enforcement litigation, for example—but it would not seem that there are any comparable costs to infrequent revision of the OSD. One could justifiably say of the OSD, "if it ain't broke, don't fix it."

However, recent developments may strengthen the case for it being an opportune time to explore improvements to the OSD. There has been a rise in attempts to "game" the OSD in the license-approval process and elsewhere. The OSI's authority to say what open source means and the continuing relevance of the OSD have been called into question by a number of critics, including entrepreneurs and [venture capitalists][8] promoting business-model-protective "source-available" licenses, advocates of the nascent "[ethical source][9]" movement, and general iconoclasts who seem to view the OSI and OSD as products of a past era associated with a discredited set of values. While there is no urgent need to revise the OSD, the OSI might benefit from undertaking a tactical revision effort aimed at preserving and enhancing the OSD's status as something legitimate, authoritative, and consistent with contemporary perspectives.

### What a revamp might look like

There are a few directions that a hypothetical revamp of the OSD might take. A case can be made for a major stylistic reformulation. While the DFSG may have proved to be a successful organic document for guiding Debian packaging policy, I would argue that the OSD's DFSG foundation is not well suited to the OSI's rather different policy focus on non-project-specific license review. The OSD incorporates some references to 1990s Linux distribution licensing controversies, and some parts of it are clearly written with the concerns of a multi-package distribution in mind. (See, for example, OSD 1, 4, and 9.) In the past, I have wondered whether the OSI might be better off scrapping the current form of the OSD in favor of the comparatively elegant [Free Software Definition][10] (FSD) maintained by the [Free Software Foundation][11] (often referred to as the "four freedoms"). But it seems unlikely that the OSI would ever make such a radical change, or even relatively minor, piecemeal textual revisions, for reasons primarily going to style.

One can also imagine the OSI seeking to make substantive policy changes to the OSD—to admit some category of license previously treated as forbidden or to reject some category previously assumed to be allowed. Consider an entirely unrealistic but timely example: The OSI could embrace the licenses promoted by the ethical source movement or the various recent source-available licenses championed by some "open source companies" by amending the anti-discrimination provisions of OSD 5 and 6 to specifically authorize the kinds of classifications made in those licenses. I do not believe the OSI actually views the OSD as having any substantive policy deficiency worth addressing through OSD revision, however, so this form of OSD reform also seems highly unlikely.

A third kind of OSD revision would involve efforts to clarify or make more explicit the OSI's existing understanding of the requirements and limits of open source licenses. As I noted in a [previous article][12], in 2019, the OSI clarified that the purpose of its license-approval process was to ensure that approved licenses not only conform to the OSD but also provide software freedom. This was motivated by attempts to "game" the OSD in the license-review process by exploiting coverage gaps or vagueness in text. Attention to the software freedom question provides a way of correcting against this problem without departing from the OSI's practical interpretation of the OSD. Revising the OSD to fill those gaps or disambiguate the OSD text is an alternative—and preferable—means of addressing the same problem. A clarification-oriented form of OSD revision seems most likely to be entertained by the OSI.

### Things to consider

Here are a few specific issues the OSI might wish to consider:

#### 1\. Patents

Not surprising, given its 1990s origins, the OSD says nothing about patents. Certain controversies relating to OSD interpretation have centered on the relationship between open source licensing and patent licensing. For example, the submission of [CC0][13] in 2012 sparked debate over whether an open source license could expressly exclude the grant of a patent license.

More recently, and outside the context of license approval, some companies with business models based on [FRAND][14] licensing of [standard essential patents][15] have (for reasons that are actually not clear) expended considerable resources advancing the view that validly labeled open source licenses can be "copyright only." The OSI has strongly [opposed][16] this viewpoint. In license-review discussions, OSD 7 ("The rights attached to the program must apply to all to whom the program is redistributed without the need for execution of an additional license by those parties") has been cited as a basis for the view that "copyright only" licenses cannot be considered open source, but that plank was most likely not written with patents in mind. It would be challenging to satisfactorily address the patent question through a revision to the OSD, but the resulting certainty could be very beneficial.

#### 2\. Copyleft and unrelated software

Some recent license submissions have raised the issue of how extensive copyleft license conditions can be without running afoul of the OSD. The [License Zero Reciprocal Public License][17] (L0-R) effectively required software created or executed by L0-R-licensed tools, but otherwise unrelated to those tools, to be published under an open source license. Somewhat similarly, the [Server Side Public License][18] (SSPL) requires publication under the SSPL of the source code of the entire stack used to implement MongoDB as a service. (Both L0-R and SSPL were subjected to heavy criticism on license review but were withdrawn before the OSI could reach a decision on them.)

While it is possible to argue that these kinds of licenses violate the anti-discrimination provisions of the OSD, this is not very satisfactory since any nontrivial FOSS license will contain classifications susceptible to being characterized as discrimination against persons or groups or fields of endeavor. OSD 9 ("License must not restrict other software") addresses the kind of problem at issue here, but it is written in a way that is specific to a distribution context. The OSI conceivably could generalize the language of OSD 9, perhaps adapting the GPL's [mere aggregation][19] clause, to address future submitted licenses that extend copyleft to unrelated software.

#### 3\. Freedom 0

A good example of an unintended coverage gap in the OSD is the absence of any counterpart to "Freedom 0" in the FSD: "The freedom to run the program as you wish, for any purpose." The accompanying commentary on the FSD suggests that Freedom 0 embodies a kind of privacy right: the user enjoys the freedom "without being required to communicate about [the software] with the developer or any other specific entity." I suspect that anyone who considers the OSD authoritative would assume that the OSD somehow encompasses the equivalent of Freedom 0, implicitly or as an emergent property or otherwise. It is not clear why it is absent from the DFSG text, but it may well have been thought too obvious to the Debian community to be worth mentioning.

At least one license submitted for OSI approval in recent years, L0-R, arguably violates Freedom 0. But Kyle Mitchell, the author of L0-R, pointed out that an [obscure license][20] approved by the OSI earlier in its history (and regarded as non-free by the FSF and Debian) had similar characteristics. In 2017, McCoy Smith [observed][21] that the view that Freedom 0 is not inherent in the OSD leads to bizarre conclusions. It would seem desirable, and perhaps relatively straightforward, for the OSI to adapt the simple language of Freedom 0 in the FSD as a new explicit criterion in the OSD.

### Risks vs. benefits

An effort by the OSI to undertake revisions to the OSD can be expected to be a substantially public process, open to community observation and participation. The views of the OSI's network of affiliate open source-related organizations, which have declared their commitment to the OSD, might become particularly important in such a process.

Given the prominence of the OSI and the significance of the OSD, the process would likely receive significant visibility and scrutiny. In an activity of this sort, it is likely that some individuals and groups would seek to distort or exert undue influence over its direction, but careful attention to governance and procedure could guard against this problem. I believe the potential benefits for open source and the OSI would outweigh the risks.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/open-source-definition

作者：[Richard Fontana][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/fontana
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/law_legal_gavel_court.jpg?itok=tc27pzjI (A gavel.)
[2]: https://opensource.org/osd
[3]: https://opensource.org/
[4]: https://opensource.org/approval
[5]: https://www.debian.org/social_contract
[6]: https://meshedinsights.com/2015/12/21/faq-license/
[7]: https://youtu.be/y-OFK__uolY?t=1235
[8]: https://techcrunch.com/2019/05/30/lack-of-leadership-in-open-source-results-in-source-available-licenses/
[9]: https://ethicalsource.dev/
[10]: https://www.gnu.org/philosophy/free-sw.en.html
[11]: https://www.fsf.org/
[12]: https://opensource.com/article/20/6/api-copyright
[13]: https://creativecommons.org/publicdomain/zero/1.0/deed.en
[14]: https://en.wikipedia.org/wiki/Reasonable_and_non-discriminatory_licensing
[15]: https://en.wikipedia.org/wiki/Essential_patent
[16]: https://opensource.org/node/906
[17]: https://licensezero.com/licenses/reciprocal
[18]: https://www.mongodb.com/licensing/server-side-public-license
[19]: https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html#section2
[20]: https://en.wikipedia.org/wiki/Reciprocal_Public_License
[21]: http://lists.opensource.org/pipermail/license-review_lists.opensource.org/2017-November/003256.html
