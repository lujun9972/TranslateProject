[#]: subject: "From Livestream To Library: Publishing Flock To Fedora’s Session Recordings"
[#]: via: "https://fedoramagazine.org/from-livestream-to-library-publishing-flock-to-fedoras-session-recordings/"
[#]: author: "Akashdeep Dhar https://fedoramagazine.org/author/t0xic0der/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

From Livestream To Library: Publishing Flock To Fedora’s Session Recordings
======

![][1]

### Intro

After months of good old fashioned struggle with Google Drive and YouTube Studio, we were finally able to prepare the video sessions from the 2025 and 2026 _Flock To Fedora_ event livestreams. These are now released to our YouTube and [PeerTube][2] communities. This article describes the details of the entire process that got us from the raw footage to the final uploads. It documents all our learnings along the way from the vendor selection to the [FFMPEG][3] configurations!

### The Famous Last Words

While I was on my way back from Prague, after participating in _Flock To Fedora_ 2026, I thought to myself – “Uploading the session recordings to YouTube should not be that difficult, right?”. I was, of course, very humbled when I instinctively reached out to (erstwhile Fedora Community Architect) [Justin Wheeler][4] to obtain the livestream files. I was very surprised to find that there indeed was an existing process, so I did not necessarily have to reinvent the wheel.

![Recording Spreadsheets – Flock 2025][5]

A couple years back, [Adrian Edwards][6] had worked on the tooling to more or less streamline slicing, thumbnailing, metadataing (are those actual words?) and uploading to our YouTube channel. There were, of course, changes to be made on the documented processes, but since the uploads for the 2025 events were partially done, that was a good starting point. We were yet to receive those from the 2026 events so I had some time to acclimate to the existing methods.

![Recording Spreadsheets – Flock 2026][7]

### Defective Detective

Of course, the first roadblock was as foundationally trivial as having wrong paths for the footage grouping. _Flock To Fedora_ 2025 occurred during four days (i.e. 04th June 2025 to 07th June 2025) and across four distinct tracks (i.e. Plenary, Topaz, Opal and Quartz). This meant I had to untangle the messily organized footage files. As we were already a year late to upload the _Flock To Fedora_ 2025 recordings, we knew that we could take some time to do it right.

![YouTube Playlist – Flock 2025][8]

I onboarded [Shounak Dey][9], a fellow Fedora Infrastructure contributor who had previously helped me with the [Fedora Badges Revamp Project][10], to help me out with this. He was able to maintain spreadsheets for the footage files and their corresponding mappings. That allowed us to quickly move to the next step. While I initially started using [SponsorBlock][11] to annotate the video timestamps, I quickly reverted back to manually eyeballing them using [VLC Media Player][12].

![Google Drive – Flock 2025][13]

### More Hands, Quick Hands

Delegation was key here. While [Shounak][9] worked on manually annotating the video timestamps, I focussed on slicing sessions from the footage files using the [LosslessCut][14] application. With [Adrian’s][6] Python scripts coming in the clutch and [Justin][4] giving the necessary access to [Shounak][9], the only thing holding us back was the network bandwidth at that time. We earmarked some changes for the documentation updates, but we had to keep those for later when the processing was complete.

![Configuring Tracks – LosslessCut Application][15]

[Justin][4] and I were planning on a phased video release model, with sessions coming out on [PeerTube][2] first, before coming to YouTube. The videos being released gradually on both the platforms would ensure that we were able to retain the audience footfall and general relevance. In between – we had to bide our time if we wanted to succeed. I was gradually getting back to my day job as I worked through my event report for the _Flock To Fedora_ 2026 conference.

![Configuring Outputs – LosslessCut Application][16]

### Where Are Those Templates?

The processing scripts and relevant documentation were available, however, I had to go looking for the thumbnail templates. It did not help that those files were on a separate repository, thus making it difficult for some contributors not as involved as us to be able to discover them organically. [Shounak][9] kept jotting down the improvements to the documentation that he would make once we were done with processing livestreams for both 2025 and 2026.

![Thumbnail Template – Flock 2026][17]

What did not help was the buggy nature of the [InkScape][18] plugin for generating thumbnails using the discovered template called NextGenerator Addon. Honestly, I was at my wits end — as I was no designer and had no idea how to tailor fit the generated templates from the flaky extension. With some help from [Emma Kidney][19] and [Madeline Peck][20], we were able to drive it home as they began working on the templates for the 2026’s edition of the _Flock To Fedora_ 2026 event.

![Thumbnail Proposal – Flock 2026][21]

### Lay of the Land

By the last week of June 2026, we had received the footage files from _Flock To Fedora_ 2026\. I had access to the Fedora Project’s YouTube channel, from back in the [Fedora Websites And Apps][22] days, and had begun uploading the sessions while marking them as unlisted. The learning ordeal from the footage processing of Flock 2025 gave us enough idea about how to proceed. This sped things up significantly once we were done with the growing pains of the required tooling.

![YouTube Playlist – Flock 2026][23]

I focused on uploading the 2025 slices on Google Drive for [Justin][4] to be able to upload them later onto [P][2][eerTube][2]. At the same time [Shounak][9] stepped up to participate in the Marketing Team as an official member. There were some missing recordings that we pursued with [Dorota Volavkova][24] for multiple weeks. This was in vain and we ultimately settled for the lower quality YouTube VODs. We were more or less gradually closing on the finish line with this entire initiative. Or at least, so we thought…

![Google Drive – Flock 2026][25]

### No Audio? No Problemo!

This week we faced a new problem! About ten of our uploaded videos from _Flock To Fedora_ 2025 did not have an audio playback in them. The audio tracks from the source files were unable to be muxed into the MP4 format. We had to losslessly convert the PCM format audio to the AAC format first. This came to our attention from a YouTube viewer’s comment message. We had to resort to unlisting the affected videos and uploading them as a separate entry.

![LosslessCut highlighting muxing exceptions][26]

With [Shounak][9] pushing his documentation changes, I worked through this problem since this had to resolve as soon as possible. Late uploads for 2025 was already bad enough. We did not want the affected videos to create a new problem. After spending almost half a day learning [FFMPEG’s][3] configs and documenting those, I was able to put it back into [Justin’s][4] hands to reschedule the release of the (now fixed) session recordings.

![Shounak’s suggested documentation changes][27]

### Outro

One of the (rather unarguably) best ways to fix a problem is to first face the problem itself before rolling up your sleeves to resolve it. What I initially thought would be a very atomic and less influential contribution method ended up touching on a wide part of Fedora Project’s community processes. Not only were we able to get these videos out for 2025 and 2026, but we were also able to mark a path forward for those who come after us wanting to do this for future events.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/from-livestream-to-library-publishing-flock-to-fedoras-session-recordings/

作者：[Akashdeep Dhar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/t0xic0der/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/Livestream-2-Library-816x346.jpg
[2]: https://peertube.tv/
[3]: https://www.ffmpeg.org/
[4]: https://fedoraproject.org/wiki/User:Jflory7
[5]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-03-12-30-44-1.png
[6]: https://fedoraproject.org/wiki/User:Moralcode
[7]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-03-12-31-29-1.png
[8]: https://fedoramagazine.org/wp-content/uploads/2026/09/image-9-1024x623.png
[9]: https://fedoraproject.org/wiki/User:Sdglitched
[10]: https://fedoramagazine.org/fedora-badges-revamp-project-from-the-ground-up/
[11]: https://chromewebstore.google.com/detail/sponsorblock-for-youtube/mnjggcdmjocbbbhaepdhchncahnbgone?hl=en
[12]: https://www.videolan.org/
[13]: https://fedoramagazine.org/wp-content/uploads/2026/09/image-8-1024x623.png
[14]: https://github.com/mifi/lossless-cut
[15]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-02-10-51-00-910x1024.png
[16]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-02-11-04-02-931x1024.png
[17]: https://fedoramagazine.org/wp-content/uploads/2026/09/yt-thumb-generate-flock-2026-1.png
[18]: https://github.com/inkscape/inkscape
[19]: https://fedoraproject.org/wiki/User:Ekidney
[20]: https://fedoraproject.org/wiki/User:Madelinepeck
[21]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-03-12-25-30-932x1024.png
[22]: https://communityblog.fedoraproject.org/tag/websites-and-apps/
[23]: https://fedoramagazine.org/wp-content/uploads/2026/09/image-7-1024x623.png
[24]: https://fedoraproject.org/wiki/User:Dvolavko
[25]: https://fedoramagazine.org/wp-content/uploads/2026/09/image-10-1024x623.png
[26]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-02-10-44-28-1-912x1024.png
[27]: https://fedoramagazine.org/wp-content/uploads/2026/09/Screenshot-From-2026-09-03-12-21-22-932x1024.png
