[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Configure Fedora to practice and compose music)
[#]: via: (https://fedoramagazine.org/configure-fedora-to-practise-and-compose-music/)
[#]: author: (Yann Collette https://fedoramagazine.org/author/ycollet/)

Configure Fedora to practice and compose music
======

![][1]

### Introduction

Using Fedora and Linux to produce and play music is now easy. Not that long ago, it was a nightmare: configuration was a complicated task and you needed to compile some applications yourself. The compatibility with electronic devices was the real story. But, now we can see the end of the road. Playing music under Linux with Fedora is becoming user friendly.

### Configuration

Fedora has long been usable to play music because of the [CCRMA repository][2]. Moreover, there also exists a [Fedora Spin][3] dedicated version: [Fedora Jam][4]. And today, you also have a [COPR repository][5] (which I manage) with a lot of stuff in it.

To install the Fedora CCRMA repository:

```
rpm -Uvh http://ccrma.stanford.edu/planetccrma/mirror/fedora/linux/planetccrma/$(rpm -E %fedora)/x86_64/planetccrma-repo-1.1-3.fc$(rpm -E %fedora).ccrma.noarch.rpm

dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

To install the LinuxMAO Fedora COPR repository:

```
dnf copr enable ycollet/linuxmao
```

There are still some minimal steps to follow before being able to efficiently use a musical application. First, you will need to install the Jack audio connection kit and the qjackctl user interface:

```
dnf install jack-audio-connection-kit qjackctl
```

Then, as a root user, you will need to add yourself to the jackuser group:

```
sudo usermod -a -G jackuser <my_user_id>
```

To enable the changes made, you just have to logout of and log back in to your session or if you prefer reboot your machine.

### Using basic applications

Now, you can add some applications to play with like [LMMS][6] or [MuseScore][7].

![][8]

A LMMS session.

![][9]

A MuseScore session.

You can also record your voice using [Audacity][10].

All of these applications are available in the main Fedora repository:

```
dnf install lmms mscore audacity
```

### Fedora and your instrument, in real time

#### Configuration

Editors note: _A real time Kernel is necessary for audio recording on your PC, especially when doing multi track recording._

If you want to use your instrument (like an electric guitar) and use the sound of your instrument in some Fedora application, you will need to use Jack Audio Connection Kit with a real time kernel.

With the CCRMA repository, to install the real time kernel, use the following command as a root user:

```
dnf install kernel-rt
```

With the LinuxMAO Fedora COPR repository, use the following command:

```
dnf install kernel-rt-mao
```

The RT Kernel from CCRMA repository corresponds to a vanilla RT kernel with some Fedora patches applied whereas the one from the LinuxMAO repository is a pure vanilla one (a clean RT kernel without any patches).

Once this is done, we still need to perform some tuning on qjackctl to reduce the [audio latency][11] so it is negligible.

![][12]

The main QJackCtl interface.

Click on the “Setup” button and set the following values:

  * Sample rate: 48000 or 44100 (this is the sampling frequency and these values are mostly supported on all commercially available sound cards)
  * Frames / period: 256
  * Periods / Buffer: 2
  * MIDI driver: seq (this value is required is you want to use a MIDI device)



With these parameters, you can easily achieve an audio latency of around 10 ms. While this value is the limit for the human ear and is hardly noticeable, you can reach lower latency with the penalty of increased CPU load.

#### Using Guitarix

To add some effects to your instrument, we will use a rack of effects: [guitarix][13] (edit: _guitarix, the virtual guitar amplifier_).

```
dnf install guitarix
```

Now, you have to connect your instrument to the audio card (the internal one or a USB adapter). Editors note: _This normally requires an interface between the electric guitar and the audio line in of the audio card. There are also guitar to USB adapters._ Once your instrument is connected, with qjackctl, we will connect:

  * the audio input to guitarix
  * the guitarix mono rack to the guitarix stereo rack
  * the guitarix stereo rack to the stereo audio output of your audio card



![][14]

Connecting Guitarix using the QJackCtl graph window.

You do that by clicking on the Graph button of QJackCtl. Inside the Graph window, you just have to connect wires to the various elements . Each block represents an application. Guitarix is split into two blocks (preamp and rack). The preamp is where you select the amplifier characteristics, and the rack is where you apply mono and stereo effects. There are two other blocks with the system label for the audio input (the one on the left in the above figure) and the audio outputs (the one on the right).

Your instrument should be connected to the first audio input. You should test that your guitar is connected and that it’s able to be heard when played. Most of the time, we use the first two slots of audio output. But this will depend on your audio card.

Editors note: _The actual configuration of inputs and outputs depends upon the type of hardware chosen. The stereo speakers of the PC were chosen as the output in the example shown._

If the MIDI interface of the sound card is chosen, there are also two red blocks which are dedicated to MIDI inputs / outputs. _These would then be setup as the input from the instrument and the output from the rack._

Guitarix is an amp plus a rack of effects for you instrument. Mostly dedicated to guitar, but you can uses it with synthesizers too.

![][15]

The Guitarix rack effects.

#### Adding some backing tracks

Better than just playing guitar on your own, you can play guitar with a group. To do this, we will install [TuxGuitar][16].

```
dnf install tuxguitar
```

![][17]

The TuxGuitar main interface.

TuxGuitar will play [GuitarPro][18] files. These files contains several instruments scores and can be played in real time. You just have to download a GuitarPro file from this [website][19] and open it with TuxGuitar.

Start TuxGuitar and click on Tools -&gt; Plugins and check the fluidsynth plugin. Then, once fluidsynth is checked, click on Configure. Click on the Audio tab and select Jack as Audio Driver. In the Synthetizer tab, choose the same sampling frequency you chose for QjackCtl above (48000 or 44100 Hz).

In the soundfonts tab, you can add your own SF2 or SF3 file to improve the audio rendering. You can now close the Plugins window. Click on Tools -&gt; Settings -&gt; Sound. Here, you can select the king of audio used to render the score. If you have several SF2 / SF3 files, you will select the chosen one for the audio rendering here. Restart TuxGuitar after you’re satisfied with your selections. After restarting TuxGuitar, a new block will appear in the Graph window of QJackCtl.

![][20]

QJackCtl with Guitarix and TuxGuitar.

You will just have to connect the block tagged ‘fluidsynth’ to the audio output like you have done with Guitarix.

### Using MIDI devices

Using MIDI devices in real time is as easy as with audio. We will connect a virtual MIDI keyboard: vkeybd (but the same procedure applies with a real MIDI device) to a MIDI synthetizer: amsynth.

```
dnf install amsynth vkeybd
```

![][21]

The main interface of AmSynth.

![][22]

The virtual MIDI keyboard VKeyBD.

Once you have started amsynth and vkeybd, you will see new connections on the QJackCtl’s Graph window.

![][23]

Amsynth and VKeyBD in QJackCtl’s graph window.

In this window, the red slots correspond to the Jack Audio MIDI connections whereas the purple ones correspond to the ALSA MIDI connections. Jack MIDI connections talk only to Jack MIDI connections. And the same for ALSA. If you want to connect a Jack MIDI connection to an ALSA MIDI connection, you will need to use a MIDI gateway: a2jmidid. You can read some more informations in the [Ardour manual][24].

We have now covered some main topics of the audio under Fedora Linux. But there are a lot more things you can do.

### Other possibilities

You can do multitrack recording with [ardour][25], [qtractor][26] or [zrythm][27].

![][28]

QTractor for multitracks live recording.

You can do live coding using [SuperCollider][29] or [SonicPi][30].

![][31]

SonicPi in action.

Use some block connected language to perform many things: [PureData][32]

![][33]

An audio / video block language: PureData

There is also a great audio looper available: [SooperLooper][34].

![][35]

SooperLooper, a great tool to build audio loops.

You can do live rehearsal through the internet: [Jamulus][36].

![][37]

Against the COVID side effects: Jamulus for live internet rehearsal.

Want to become the new famous DJ: have a look at [Mixxx][38]

![][39]

Mixxx for DJing.

### Webography

Some links now:

Here is a [YouTube video][40] where I play guitar through Guitarix and I use TuxGuitar to play the backing tracks in real time. Both TuxGuitar and Guitarix are sent through non-mixer which is a small mixing application. To be able to record the audio of the session “on the fly”, I also use timemachine. And to avoid reconnecting everything each time I want to play guitar, I use Ray Session to start every application and connect all the Jack Audio connections.

I also made a small demonstration of the use of Jamulus for a live rehearsal. On this [YouTube video][41], I use Jamulus, QJackCtl, Guitarix mainly. The second guitarix is 30 km away. The latency was around 15 ms. It’s quite small and hardly noticable.

On this [YouTube video][42], I tried to make some comparison between various SF2 / SF3 soundfont files. I used a GuitarPro file for the Opeth’s song “epilogue”.

On this [YouTube video][43], I use MuseScore to play a GuitarPro file and I play along while my guitar sound is processed by Guitarix.

[Here][44], it’s a live performance with a dancer. TuxGuitar + Non Session Manager + Non Mixer + Guitarix. I always used this kind of combination and Linux has never hanged … Finger crossed !

[Some compositions][45] made with LMMS on Fedora 25 to 32. Using some really nice plugins like Surge, NoiseMaker from DISTRHO package and others. All these compositions are libre music and are hosted on Jamendo.

If you need some help:

  * [LinuxMusicians][46]: a great place with skilled people willing to help
  * [LinuxMAO][47]: if you speak french, this is the place to be. A lot of resources related to various software.
  * [LinuxAudio][48]: another great website with various ressources to help.



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/configure-fedora-to-practise-and-compose-music/

作者：[Yann Collette][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ycollet/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/08/music-compose-816x346.png
[2]: https://doc.fedora-fr.org/wiki/D%C3%A9p%C3%B4t_CCRMA
[3]: https://fedoraproject.org/wiki/Fedora_Jam_Audio_Spin
[4]: https://labs.fedoraproject.org/fr/jam/
[5]: https://copr.fedorainfracloud.org/coprs/ycollet/linuxmao/
[6]: https://lmms.io/
[7]: https://musescore.org/fr
[8]: https://fedoramagazine.org/wp-content/uploads/2020/08/LMMS_1.2.1_Demo-1024x555.png
[9]: https://fedoramagazine.org/wp-content/uploads/2020/08/MuseScore_1.2_running_on_Ubuntu-1024x665.png
[10]: https://www.audacityteam.org/
[11]: https://en.wikipedia.org/wiki/Latency_(audio)
[12]: https://fedoramagazine.org/wp-content/uploads/2020/08/QjackctlMainForm1.png
[13]: https://guitarix.org/
[14]: https://fedoramagazine.org/wp-content/uploads/2020/08/Screenshot_20200811_164007-1024x617.png
[15]: https://fedoramagazine.org/wp-content/uploads/2020/08/Guitarix_0.35.0.png
[16]: https://sourceforge.net/projects/tuxguitar/
[17]: https://fedoramagazine.org/wp-content/uploads/2020/08/Tuxguitar_screenshot-1024x779.png
[18]: https://www.guitar-pro.com/fr/index.php
[19]: https://www.ultimate-guitar.com/explore
[20]: https://fedoramagazine.org/wp-content/uploads/2020/08/Screenshot_20200811_164007-1-1024x640.png
[21]: https://fedoramagazine.org/wp-content/uploads/2020/08/Amsynth-141.png
[22]: https://fedoramagazine.org/wp-content/uploads/2020/08/vkeybd.png
[23]: https://fedoramagazine.org/wp-content/uploads/2020/08/Screenshot_20200811_164007-2-1024x640.png
[24]: https://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/
[25]: https://ardour.org/
[26]: https://qtractor.sourceforge.io/
[27]: https://www.zrythm.org/en/
[28]: https://fedoramagazine.org/wp-content/uploads/2020/08/qtractor-screenshot16.png
[29]: https://supercollider.github.io/
[30]: https://sonic-pi.net/
[31]: https://fedoramagazine.org/wp-content/uploads/2020/08/sonicpi-1024x576.jpg
[32]: https://puredata.info/
[33]: https://fedoramagazine.org/wp-content/uploads/2020/08/PureData-DataFlow-sendreceive2_1-en.png
[34]: http://essej.net/sooperlooper/
[35]: https://fedoramagazine.org/wp-content/uploads/2020/08/sooperlooper.png
[36]: http://llcon.sourceforge.net/
[37]: https://fedoramagazine.org/wp-content/uploads/2020/08/jamulus-prez-1024x359.png
[38]: https://www.mixxx.org/
[39]: https://fedoramagazine.org/wp-content/uploads/2020/08/Mixxx-1.11.0-Deere-1024x585.png
[40]: https://www.youtube.com/watch?v=zJk0GgWcgXE
[41]: https://www.youtube.com/watch?v=QNlsTH6ETEU
[42]: https://www.youtube.com/watch?v=p7fFXbFxLwI
[43]: https://www.youtube.com/watch?v=bCUmbctP82Q
[44]: https://www.youtube.com/watch?v=zcfJQBBnSaY
[45]: https://www.jamendo.com/artist/471813/joseph-curwen/albums
[46]: https://linuxmusicians.com/
[47]: http://linuxmao.org/Accueil
[48]: https://linuxaudio.org/
