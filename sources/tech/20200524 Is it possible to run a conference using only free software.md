[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Is it possible to run a conference using only free software?)
[#]: via: (https://opensource.com/article/20/5/conference-free-software)
[#]: author: (Zoë Kooyman https://opensource.com/users/zoe1)

Is it possible to run a conference using only free software?
======
Shifting from IRL to digital on a tight timeline with the help of free
software; how we did it and lessons learned for next time.
![Working from home at a laptop][1]

The [Free Software Foundation's][2] (FSF) annual conference [LibrePlanet][3] went fully virtual in 2020 due to ongoing issues caused by the coronavirus pandemic. In our last week of preparations before the live event, increasingly disturbing news related to the virus made us realize we could not responsibly hold our usual conference on software freedom in person while protecting the safety of our participants and their communities. So we turned everything around to eventually bring 35 free software presentations to our community through the filter of a computer screen. After the conference, we had many people writing to ask us for more details about what we used to do it, so we wanted to take this opportunity to share how we were able to create a fully free interactive and educational virtual experience for the first time, but likely not the last.

LibrePlanet 2020 videos were recorded from the live stream and have been [posted online][4] for everyone to enjoy. For the sessions not entirely dependent on visual information from slides, we also provide the audio over an [RSS (Atom) feed][5] for anyone to listen to while they exercise, bake, garden, or otherwise seek distraction from stressful times.

### HUBAngl and Icecast

Because our community is an international one, we have been streaming our event online for years using entirely free software. Thankfully, the tech team could [build on this experience][6] to make sure that we delivered a smooth online conference. Previously, we used [HUBAngl][7], which was developed specifically for LibrePlanet, by Free Software Foundation (FSF) intern David Teste. It fetches audio and/or video input streams, and then streams to the [Icecast][8] streaming server. The streams that are broadcasted and stored can be audio-only, video-only, or both at once.

### Gstreamer and Jitsi

In 2016, we gained some [live streaming][9] experience when we interviewed Edward Snowden live from Moscow. To minimize the risk of failed recordings due to overly complex or error-prone software systems, we made it a priority to achieve a pipeline with low latency, good image quality, and low CPU usage. The application we used then was [Jitsi Meet][10], and the [tech info and scripts][11] we used for streaming from 2016 are available for your information and inspiration.

### Using Ansible for multimedia reliability

Naturally, for this year, with no time for researching other applications, we opted to build on our experience with Jitsi Meet. We hosted our own instance for remote speakers to connect to and enter a video call with the conference organizers. A screen capture of this call was then simultaneously recorded by the FSF tech team and streamed out to the world over Gstreamer and Icecast.

To bypass recommendations of nonfree services or software, some parts of the Jitsi Meet configuration were [set up differently with Ansible][12], rather than as suggested. In the days following the conference, we have already [improved the script][13] we used for streaming your screen or window, and it is free for you to use and adapt.

At the time of the conference, it was still considered safe to have a small number of people together, so we were able to have some of our staff and volunteers in the office. Speakers called into a dedicated digital conference room for their session, where they were assisted by a room monitor and a tech team member who coordinated the session together. The call was received on a local monitor in the office. Our three digital conference rooms all had similar streaming setups, with the local monitor being broadcast through Gstreamer to Icecast. The desktops used were [ASUS KGPE-D16][14] motherboards with [Libreboot][15]; this hardware has previously also been certified under the [Respects Your Freedom (RYF)][16] certification program.

When everyone was ready, and everything worked, they would start the stream. All speakers were asked to deliver their slides in advance. That way, if a presenter had trouble sharing their screen with Jitsi Meet, the slides could be loaded from the FSF server and controlled by the tech team member in charge of coordinating that digital conference room instead. In some exceptional cases, like major time differences or panel coordination challenges, the talk was pre-recorded. If so, it was played locally on the machine with the [MPV][17] [video player][17].

### Interactivity

We hosted interactive [IRC sessions][18] on the Freenode network. In addition to a private channel to communicate directly with the speakers about technical issues, we had a general #libreplanet channel, and additional channels for every conference "room." In these rooms, the speakers connected directly to the audience to field questions and join the conversation. We enlisted volunteers to monitor the rooms for safe space policy issues, but the audience was so great and enthusiastic that we did not have a single issue!

### Breakout rooms and hallway tracks

Each year at LibrePlanet, we've facilitated a self-organized meeting of associate members who discuss the FSF's work and opportunities and share their feedback and ideas with us afterward. We didn't want to miss out on this year's feedback, so we moved the member meeting online as well. This required more conversational communication and note-taking, so we opted for a combination of [Etherpad][19] for note-taking and written feedback, [Mumble][20] for voice communication, and the use of the dedicated IRC channel.

### Issues and improvements

We had only a week to select and optimize our streaming setup, but the experience itself taught us a lot. If given the opportunity, or for those of you now bringing your event online, some things we would do differently are:

  * We would set up a continuous stream and insert the session into it; this would relieve the need to refresh between sessions and improve the viewer experience.
  * It is important to notify speakers of bandwidth used by the streaming. Make sure they test their connection or have dedicated Internet lines. This is especially important with the international connections, as they showed to be more unreliable than local connections; this presented itself mostly via connection issues and difficulties with sharing the presentation screen.
  * For a better experience for people on the move, or to experience the event via mobile, we advise the deployment of audio-only feeds and a lower bandwidth alternative feed for the videos.
  * The FSF tech team is currently experimenting with [Big Blue Button][21] and [Canvas][22] for interactive streaming that allows for video, slide sharing, and instant chat. We will post in more detail about our work with these applications soon; they are worth considering if you are planning a conference, interactive video session, or online meeting.



### Free software tech conferences

Hosting your conference freely is absolutely possible. You do not have to compromise freedom when you want to connect to your community, and you most certainly [do not have to settle for proprietary software][23] to help you communicate.

If you have an upcoming event and are interested in a freedom-respecting setup but need a hand, you can email us at [info@fsf.org][24], and we might be able to help. In recent weeks, the FSF technical and campaigns teams have spent a lot of time working on and communicating about free communication tools. And as always, you're welcome to become a member of the [FSF][25] itself.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/5/conference-free-software

作者：[Zoë Kooyman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/zoe1
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/wfh_work_home_laptop_work.png?itok=VFwToeMy (Working from home at a laptop)
[2]: https://www.fsf.org
[3]: https://libreplanet.org
[4]: https://www.fsf.org/blogs/community/libreplanet-2020-videos-now-available-online
[5]: https://media.libreplanet.org/atom/
[6]: https://libreplanet.org/wiki/LibrePlanet:Conference/2019/Streaming
[7]: https://github.com/soonum/hubangl
[8]: https://icecast.org/
[9]: https://www.fsf.org/bulletin/2016/spring/mr-snowden-or-how-i-learned-to-stop-worrying-and-love-gstreamer
[10]: https://directory.fsf.org/wiki/Jitsi-Meet
[11]: https://libreplanet.org/wiki/LibrePlanet:Conference/2016/Streaming
[12]: https://vcs.fsf.org/?p=jitsi-ansible.git;a=summary
[13]: https://vcs.fsf.org/?p=streamdesktop.git;a=summary
[14]: https://libreboot.org/docs/hardware/kgpe-d16.html
[15]: http://libreboot.org
[16]: https://ryf.fsf.org/products/VikingsD16
[17]: https://directory.fsf.org/wiki/Mpv
[18]: https://webchat.freenode.net/
[19]: https://directory.fsf.org/wiki/Etherpad
[20]: http://mumble.info
[21]: https://bigbluebutton.org/
[22]: https://directory.fsf.org/wiki/Canvas
[23]: https://opensource.com/article/20/4/stay-touch-using-free-software
[24]: mailto:info@fsf.org
[25]: http://fsf.org
