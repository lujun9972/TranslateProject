[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Make virtual meetings better with this OBS trick)
[#]: via: (https://opensource.com/article/20/8/obs-virtual-webcam)
[#]: author: (Kirk https://opensource.com/users/iamkirkbater)

Make virtual meetings better with this OBS trick
======
Convey "yes" or "no" without turning on your microphone in a virtual
meeting.
![Two people chatting via a video conference app][1]

Have you ever been in a web meeting where someone asks, "Can you see my screen?" or "Can you hear me?" and 400 people answer "yes" at the same time? Or even worse, nobody answers at all? Have you ever wanted to show agreement or give a confirmation on a video call without having to turn on your microphone, because you feel it might be disruptive? This happens to me often. Like when someone asks, "Does anyone have anything else for the good of the order?" and I want to say, "No, I'm good," but I don't want to speak over anyone else who has something to add.

One of the biggest challenges with virtual communication is that it's a bit harder to pick up body language. Instead of sitting in the same room with your co-workers, you're looking at tiny thumbnails of them, so body language context can be lost, especially on smaller screens. I have a 13" Macbook Pro. It's a very small screen, and if I'm not docked to my monitor, I need to look extra hard to pick up subtle cues.

**[Read next: [10 ways to fight virtual meeting fatigue][2]]**

Some of my clever co-workers have solved this problem with paper signs or index cards taped to pencils, but that's far too straightforward a solution for me. So, of course, I felt the need to over-engineer this.

Here is what I did.

![GIF showing switching OBS among default, yes, and no scenes][3]

(Kirk Bater, [CC BY-SA 4.0][4])

### Install your software

Enter [Open Broadcaster Software][5] (OBS). OBS allows you to run live video processing, similar to what you would see in a live television broadcast. You can add multiple input sources, switch between them, put text on the screen similar to news broadcasts, and do much more. OBS is also used heavily by streamers in the gaming community.

OBS is the base software you'll use for this solution, so [download and install][6] it. OBS supports plugins, and for this to work correctly, you'll need to install a couple.

For Mac users, the first plugin to install is [OBS Virtual Camera for macOS][7]. This allows OBS to register a "webcam device" so that it can be used with your videoconferencing software. I've used it with Zoom, Google Meet, BlueJeans, and Jitsi without any problems. You can find the [installation instructions][8] in the plugin's GitHub repo.

For Linux users, download and install the [V4L Virtual Camera for Linux][9] plugin as described in the project's README file.

For Windows users, download and install the [Virtual Camera for Windows][10] plugin as described in the project's README file.

The next plugin to install is [Advanced Scene Switcher][11]. This plugin works on Linux, MacOS, and Windows, and it allows you to automatically cycle back to the normal webcam view after a second or two when you want to overlay a "YES" or "NO" message. You can find the [installation instructions][12] on the plugin's website. This isn't strictly necessary; you can switch scenes manually, but this is a nice feature to have.

### Set up the first scene

There are two key terms you should understand before continuing. The first is "scene." A scene is how you set up separate overlays. As you flip between the different scenes, you're flipping between different views that the people on the other side of the internet tubes see of you. In the most simple version, you'll set up three separate scenes. One is just your webcam, one is a YES scene, and one is a NO scene.

The second term to know is "source." These can be images, text, your webcam, etc. Think of these as individual layers you stack on top of each other to achieve what you want to display. 

First, set up your default scene. This should be there when you start OBS. In the bottom-right of OBS, locate the Scenes panel. Just to the right of that, you see a list of Sources.

Add your webcam input as the first source. If you click on the **+** button at the bottom of the Sources box, you get a list of the sources you can add. Select **Video Capture Device**, and then select your webcam as the device. In the box, you should see whatever your webcam sees. Click **OK** to add this source to your scene.

![Adding a source in OBS][13]

You _might_ need to adjust the size of the webcam to make it take up the entire output area.

![Resizing input video][14]

Note that your webcam input will _not_ be flipped in OBS. What you see in OBS will be exactly what the people on the other side of your call will see. You _will_ see the mirrored output in your application (as you normally do), but you won't see the mirrored output in OBS.

That's it for the first scene!

### Set up additional scenes

Now you need to set up the YES and NO scenes. To add a new scene, click on the **+** sign at the bottom of the Scenes box. Give the scene a descriptive name, I named mine **YES** because this is the scene where I—wait for it—added a "YES" overlay.

Much like you did for the default scene, add your video capture device to your Sources list, but this time you'll have the option to reuse the one you already created. To do so, select **Add Existing** and select the video capture device you created for the first scene.

Next, you need to add a text overlay. Resize the video input again (if necessary), click on the **+** sign again, and select **Text**. Give it a descriptive name (I used **yesText**), add the text "YES," and select whatever font you want. When I set this up, I had a problem if I tried to change the font size here, so I left it as the default; you can resize the text with the size controls the same way you resized the webcam input. To change the font color, scroll down below where you entered text—it's not super apparent that you can scroll there, so the ability to change the color might seem hidden.

![Yes scene][15]

Resize and position your text on the screen. That's it! Run through the same steps to create a new scene for "NO" (and any other reactions you might want to display). Feel free to experiment with image overlays or other sources.

### Automatic scene switching

The next step is to create scene automatic transitions from your secondary (yes/no) scenes back to the default webcam scene. From the menu bar, select **Tools &gt; Advanced Scene Switcher** and then navigate to the **Sequence** tab.

For my automatic transitions, I used "When 'NO' is active, switch to 'Default' after '2.00s' using 'Fade.'" To add that transition to the list, click on the **+** sign at the bottom of the screen. The key is to have your overlay scene switch _to_ your default scene after a set amount of time. I like to use the fade transition because I don't want to divert people's attention more than necessary. Do the same for each of the overlay screens you made.

To see how the transitions work, go back into the main OBS screen and click on a different scene. Your overlay should pop up and then transition back after the time you set.

### Coup de grace

Now, fire up your [video chatting software][16] of choice, and select **OBS Virtual Camera** as your webcam. Every videoconferencing software will have a different way to do that, which you should be able to find in its documentation. You might not see your webcam but rather an image that says something about a Mirrored view. This is the image that is displayed when your virtual camera is not started—even though your camera is on and OBS shows that your camera is on in the software, you still need to start your virtual camera by selecting **Tools &gt; Start Virtual Camera** in the OBS menu bar. Now you should see what your OBS is broadcasting.

For Mac users, I've written an Applescript you can run to start the virtual camera, as it's not started by default when you start OBS; you can find it [in this Gist][17]. You will need to allow this script to run in your Security and Privacy settings. Running this script will open OBS (and start it if it's not already started), start your virtual camera, and minimize OBS to your dock. I use [OBS-Websocket][18] to control my scene switching, but you can remove the line in the Applescript file to minimize it and just click on the different scenes in OBS to switch to it.

### Final thoughts

You should have at least two scenes you can switch to show a message on the screen of your next web conference. You may already be imagining how you can extend this functionality to play GIFs, videos, emojis, images, and more. Good luck!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/obs-virtual-webcam

作者：[Kirk][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/iamkirkbater
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/chat_video_conference_talk_team.png?itok=t2_7fEH0 (Two people chatting via a video conference app)
[2]: https://enterprisersproject.com/article/2020/6/zoom-fatigue-10-tips
[3]: https://opensource.com/sites/default/files/uploads/webcam.gif (GIF showing switching OBS among default, yes, and no scenes)
[4]: https://creativecommons.org/licenses/by-sa/4.0/
[5]: https://obsproject.com/
[6]: https://obsproject.com/download
[7]: https://github.com/johnboiles/obs-mac-virtualcam
[8]: https://github.com/johnboiles/obs-mac-virtualcam#installing
[9]: https://github.com/CatxFish/obs-v4l2sink
[10]: https://github.com/CatxFish/obs-virtual-cam
[11]: https://github.com/WarmUpTill/SceneSwitcher
[12]: https://obsproject.com/forum/resources/advanced-scene-switcher.395/
[13]: https://opensource.com/sites/default/files/obs-sources.jpg (Adding a source in OBS)
[14]: https://opensource.com/sites/default/files/obs-resize.jpg (Resizing input video)
[15]: https://opensource.com/sites/default/files/obs-yes.jpg (Yes scene)
[16]: https://opensource.com/article/20/5/open-source-video-conferencing
[17]: https://gist.github.com/iamkirkbater/ba6278d0ac6d695cb8c6c5fc309ba210
[18]: https://obsproject.com/forum/resources/obs-websocket-remote-control-obs-studio-from-websockets.466/
