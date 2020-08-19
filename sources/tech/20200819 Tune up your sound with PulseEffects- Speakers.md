[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Tune up your sound with PulseEffects: Speakers)
[#]: via: (https://fedoramagazine.org/tune-up-your-sound-with-pulseeffects-speakers/)
[#]: author: (Paul W. Frields https://fedoramagazine.org/author/pfrields/)

Tune up your sound with PulseEffects: Speakers
======

![][1]

Audio components for your computer don’t always produce the quality of sound you want. For instance your laptop speakers may be a bit “tinny” sounding, or a set of speakers for your desktop may be too boomy for your room. Or if you use a desk or headset microphone, you may find that recordings you make are not as high quality as you’d like. Enter PulseEffects!

### PulseAudio and Gstreamer

The [PulseAudio][2] sound server comes with [Fedora Workstation][3] by default. It’s highly flexible and easily modified. PulseAudio can deal with many different inputs and outputs. For instance, it lets you switch between different inputs known as _sources_ (such as microphones, or sound files) or outputs known as _sinks_ (such as speakers or headphones).

By default, PulseAudio manages sound as streams, digitally sampled at a specific [rate and bit depth][4] with a defined number of channels — two for most stereo streams. It handles different sample rates for you, so you don’t have to know the details of the stream. PulseAudio simply deals with moving sound from one point to another.

The [Gstreamer][5] multimedia framework, on the other hand, provides myriad ways to modify audio and video data on their way through a pipeline. Gstreamer comes with plugins that allow it to attach to PulseAudio. This means that you can use Gstreamer to make a pipeline between your inputs and outputs to change audio streams.

PulseEffects manages this process with a nice, graphical front end. It lets you select and order different effects for your sound.

### Installing PulseEffects

To install PulseEffects, use the _Software_ tool and type _pulseeffects_ to find the package. Fedora carries this software in its official repositories. So if you need to, you can switch the source from the _Flatpak_ version to the _Fedora_ one. Then click _Install_.

If you’re using a command line, you can use the _sudo_ command with _dnf_ to do the same thing:

```
$ sudo dnf install pulseeffects
```

Start playing some audio. This can come from your _Videos_ or _Rhythmbox_ media player, a website such as YouTube, a music streaming app such as Spotify, or something else. The best source to use is a full-fidelity digital audio source, like a CD or a FLAC file. (MP3 and online digital streams cut out some frequency information to reduce data size.) Ideally, it should be music that you are used to listening to in many places, and know well, like an album or playlist. Put it on repeat so you can use it while you tune your sound.

Then launch the program using either the _Software_ tool’s _Launch_ control, or your desktop’s application launcher. On Fedora Workstation, go to the _Activities_ hotspot, use the _Show Applications_ control to locate _PulseEffects_ in the list, and click to launch. You should see your application in the list of active sound streams, with color bars that show an average frequency response:

![PulseEffects initial screen with one sound stream from Videos][6]

Notice all the sound modules available on the left. None are running by default when you first start PulseEffects. Any enabled modules are applied to your sound in order from top to bottom. You can use the up/down controls next to the module names to alter the order.

### What does “better” mean?

Before we get started, realize that what constitutes “better” will usually be different based on many factors:

  * Specific hardware like the model of speakers or microphone
  * The environment the sound device is in (your room)
  * What your ears prefer



There is no magic cure for bad sound that works universally everywhere. So the examples you’ll see are based on some common problems. But you will need to use your ears to determine what’s best for your hardware, in the place you’re using it.

### Making desktop speakers sound better

Often desktop speaker sets consist of a subwoofer and small satellite speakers. These tend to be both excessively “boomy,” meaning too much very low frequency sound, and “honky” or “boxy,” meaning too much of some middle (or “mid”) frequencies. To fix frequencies that are over- or under-represented, we can use an _equalizer_.

By default, all the effects are off in PulseEffects. Since you want to modify a sound output — your speakers — make sure the “speaker” icon at the upper left is selected. Locate the _Equalizer_ control in PulseEffects and select it. Select the toggle switch at the top of the equalizer controls to turn it on.

The default equalizer appears as a 30-band graphic EQ. Older readers might be familiar with seeing physical equipment like this. Each band alters not just that specific frequency, but a fairly narrow band of frequencies around it. Think of it like a “dip” or “bump” in the frequency graph, depending on whether you lower or raise the slider.

![PulseEffects default EQ, with a roll-off of extreme low frequencies and some reduction of unpleasant “boxiness” around 450Hz][7]

If you’re not sure how to alter frequencies to get better sound, click the “tools” icon under the on/off toggle. Under _Presets_ you can select different EQ settings to find something closest to what you like. Then you can modify those settings as you like. If things get out of control, under _Settings_ use the _Flat response_ control to zero out all the EQ.

Using the “tools” icon, you can also choose a different number of bands to simplify your choices. Using the “gear” icon above each band, you can choose different types of EQ, as well as [the width and Q][8]. Additional filter types like a _low/high pass_ or _low/high shelf_ are also available. Feel free to play with the EQ to see how it works, **but be careful** not to increase EQ levels too high if your speakers are above a moderate volume, because you can damage speakers that way.

### Tips from a mix engineer

These guidelines may help you find the optimal sound for your situation.

  * It’s almost always better to reduce a problem frequency than to boost other things. If you boost too much, your music can start to distort.
  * To fix excessive boominess, apply a high pass filter somewhere between 30 and 50 Hz. You may also want to try a bell EQ reduction somewhere between 40 and 100 Hz.
  * If you want to fix a boxy sound (reminds you of a cardboard box), try a bell EQ to reduce some frequencies between 300 and 500 Hz.
  * To fix a honky or nasal sound, try reducing some frequencies between 650 and 900 Hz.
  * If guitar/keyboard solos or vocals seem a bit muffled, try a gentle boost centered somewhere between 1 and 2 kHz to make them a little more present.
  * If your speakers sound overly tinny, apply a high shelf reduction starting somewhere between 4 and 8 kHz — start at a high frequency and dial back to where it’s helpful. To fix a dull sound, apply a high shelf boost using the same approach.



Remember that a little EQ goes a long way. Try keeping your bell boosts or cuts between +4 and -4 on the sliders. The goal is not to make the music sound extreme, but to make slight corrections. Otherwise your ears will get tired more quickly, or in extreme cases you may even get headaches.

Watch the _Input_ and _Output_ meters at the bottom of every module. If you see a lot of green on one or both, the sound module is overloading at that stage. You’ll often find MP3 files, especially of modern music, have this issue. You may also see “warning” icons flashing over the check mark on enabled modules.

One way to cure this is to use the _Limiter_ module at the beginning of the chain, and simply turn the input gain on the chain down about -3dB, leaving the limit at 0dB. This simply lowers the overall signal level without any attenuation. Then you can run other modules without worrying quite as much about distortion or overload in later stages.

### Making laptop speakers sound better

While the above guidelines might be good for bigger speakers, laptops have the additional burden of being very small. Typically they lack bass response, because more and/or larger speakers, and more powerful magnets, are needed to produce those frequencies well.

However, you can correct this using the _Bass Enhancer_ module in PulseEffects. You may want to move this module downward in the stack after your EQ for best results. Rather than turning the amount up excessively, try a modest change of +3 or +4dB, and then move the _Scope_ frequency around until you find where you start to notice good results. Don’t be tempted to amplify too much because again, if it’s too high you could start to damage your laptop speakers over time.

### Storing your work

First, set PulseEffects to run whenever you login. Use the “hamburger” tool at the top right to open up the _General_ settings. Set _Start Service at Login_ to enabled, and also enable the option to _Process All Outputs_. This does not mean all devices will get the same settings. Instead, it means that PulseEffects will run a chain for any sound output device you have connected. You can apply different chains to different devices.

Next, select the _Presets_ button, and in the text box, type a name for your preset. One recommendation is to use the name of the device for which you’ve created a chain. Then click the “+” icon to add the preset. If you make changes, you can either use the “save” icon to save the changes to the selected preset, or click _Apply_ to throw them away and re-apply the saved preset.

Finally, you can click the “cycle” icon if you want the preset to be applied every time the currently used sound output is detected. This is almost always a good idea. If you want to set up different presets for other outputs, first connect the output. Then make a new preset as described above, and select that to be auto-applied.

One final note: When you close the PulseEffects application, your active chain of effects does not stop. It will stay running unless you reset or stop the service. PulseEffects will consume a few percent of CPU time (depending on processor speed). On all but the oldest systems the load should not be noticeable. However, if you are sensitive to power use such as on a laptop, you may want to stop the service using this command:

```
$ pulseeffects -q
```

### Conclusion

Remember that every environment and person’s hearing is different, so beware of the overly dogmatic. Finally, you can’t make terrible speakers into great ones. But you can usually make them sound not so terrible — and if you have decent speakers, you usually _can_ make them sound quite good!

The PulseEffects author also has both a [LiberaPay donation site][9] and a [Patreon account][10], so if you find the software useful, you might want to consider contributing.

In the next installment, you’ll learn how to set up better sound on a desktop or headset microphone, to improve your teleconference meetings or make better audio or video spoken content. Until then, enjoy your new sound possibilities.

* * *

_Photo by [Paul Esch-Laurent][11] on [Unsplash][12]_.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/tune-up-your-sound-with-pulseeffects-speakers/

作者：[Paul W. Frields][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/pfrields/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/08/pulseeffects-1-1-816x345.jpg
[2]: https://www.freedesktop.org/wiki/Software/PulseAudio/
[3]: http://getfedora.org
[4]: https://www.izotope.com/en/learn/digital-audio-basics-sample-rate-and-bit-depth.html
[5]: https://gstreamer.freedesktop.org/
[6]: https://fedoramagazine.org/wp-content/uploads/2020/08/pulseeffects-start-1024x703.png
[7]: https://fedoramagazine.org/wp-content/uploads/2020/08/pulseeffects-geq30-1024x703.png
[8]: https://www.presonus.com/learn/technical-articles/What-Is-a-Parametric-Eq
[9]: https://liberapay.com/wwmm/donate
[10]: https://www.patreon.com/wellingtonwallace?fan_landing=true
[11]: https://unsplash.com/@pinjasaur?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[12]: https://unsplash.com/s/photos/speakers?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
