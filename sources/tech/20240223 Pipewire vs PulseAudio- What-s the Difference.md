[#]: subject: "Pipewire vs PulseAudio: What's the Difference?"
[#]: via: "https://itsfoss.com/pipewire-vs-pulseaudio/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Pipewire vs PulseAudio: What's the Difference?
======

If you are active in the Linux community, you will often come across the debate on what's better: PipeWire or PulseAudio?

Some users prefer going back to PulseAudio, while others find solving their decade-old audio problems much better. So the question here is: **what is the difference between PipeWire and PulseAudio?** 🤔

Sure, PipeWire is a relatively new technology, it must have a purpose and which is why it is replacing PulseAudio for many Linux distributions. This does not mean PulseAudio doesn't work whatsoever. It has served very well to its users, but surely has its pros and cons.

Fret not, I shall highlight everything essential regarding **the** **multimedia framework PipeWire** and **the** **sound server program, PulseAudio.**

### The basics of audio on Linux

![][1]

Nowadays, every motherboard (PC/laptop) has an internal sound card, a hardware component that is used to convert analog audio signals to digital signals for recording and streaming purposes.

Sure, some can have an external sound card for audio, but that is a rare sight to see.

So, we need some sort of driver (or middleware) to interact with the hardware and work with applications like [audio editors on Linux][2], right?

And that's where the role of ALSA (Advanced Linux Sound Architecture) comes into play.

ALSA (baked into the Linux kernel) provides necessary device drives to read and write from the sound card. You will find multiple applications that directly use the ALSA such as [VLC][3] for output, and Audacity, which can directly record audio through ALSA.

The point here is many applications use ALSA API directly without the need for an audio server like PulseAudio or PipeWire.

But you can't rely on ALSA as it will take control of the entire sound device, so you can only use it to handle one application at a time. So no hardware multiplexing.

**Due to this reason, we require an audio server like PulseAudio or PipeWire.**

The arrival of **PulseAudio solved three major problems** that we had with the ALSA:

  * Play audio from multiple applications at the same time.
  * It came with advanced features like mixing multiple audio streams, audio streaming, per application volume control, etc.
  * Ease of use.



So here's what the basic audio structure looks like based on prior explanation:

![][4]

Now that we have an idea of how the audio works on Linux. Let us dive in deeper to know the difference between the two audio servers that make our Linux experience better.

**Suggested Read 📖**

![][5]

### Comparing audio servers: PipeWire vs PulseAudio

We need to know what they are, how they work, and the feature-set to understand how they differ.

Sure, the easy part is — one is newer tech and the other one is an older tech.

Let me highlight the rest of the details below, including a piece of interesting information related to audio servers.

💡

JACK (JACK Audio Connection Kit), an audio server made for professional audio artists that solved one problem with PulseAudio: redirecting output to any input. In simple terms, it worked like a physical patch panel.

An older tech to PulseAudio. The reason it didn't gain popularity is it was complex to use and was incompatible with PulseAudio.

### PulseAudio: The old guardian of Linux audio experience

![][6]

[**PulseAudio**][7] **is a super simple audio server designed for Linux systems. It was initially known as "Polypaudio", and then later renamed.**

**It was created as a modern alternative to ESD (Enlightened Sound Daemon). ESD was the sound server maintained as part of the GNOME project, as a tech to unify sound drivers for all kinds of architectures.**

If it is a POSIX-compliant operating system (distro), PulseAudio can be a sound server system for it.

Furthermore, PulseAudio comes with various plugin modules, which makes it very capable for a lot of use-cases. Not just limited to desktops, PulseAudio is also used in various mobile devices.

### PipeWire: Getting the best of PulseAudio and JACK

![][8]

[**PipeWire**][9] **is a multimedia framework (and an audio server program) that managed to provide advanced features to work with modern audio devices while being a simple utility for end-users.**

Remember, what I highlighted about JACK above?

It offered great features, but had compatibility issues with the existing PulseAudio setup. If that was not enough, using it was complex, making it difficult to recommend unless you were an audio professional. On the other hand, PulseAudio was user-friendly and had legacy support, but it had its issues.

So we needed a simple utility, compatible with other audio servers like PulseAudio, addressing all the PulseAudio issues, and offering a better feature set.

That's where PipeWire came to the rescue.

PipeWire is also designed in a way to provide better security when interacting with audio/video devices through containerized applications, supporting Flatpak primarily.

Not just providing better compatibility with newer packages, it also supports Wayland.

### How Do They Work?

![][10]

**PulseAudio** utilizes a client/server architecture to function. There can be different clients with various APIs, and local/remote PulseAudio servers.

And, all of it should work flawlessly with the help of modules. Yes, PulseAudio functions through its modules, it is not much by itself but just a daemon for API and hosting modules.

By default, PulseAudio uses the configuration available system-wide. However, you can provide a custom configuration file in the home directory, and the next time you boot up, it will utilize that.

**PipeWire** works differently without primarily relying on a module system. The daemon is responsible for processing, and a session manager uses the media graph (info on devices, port, and nodes) to decide how to link them all.

Unlike PulseAudio tailored only for consumer audio, PipeWire fulfills all kinds of low-latency requirements for everyday users and professionals (as an alternative to JACK).

I went through hundreds of community posts where users have praised PipeWire for fixing the crackling sound, or they found the perfect fit for their JACK replacement with ease of use and better reliability.

So, it works like it should. And, technically, a superior choice for many.

### Key Features

PulseAudio is still in use, even if it is being replaced by PipeWire.

Some of the best features that make PulseAudio a usable tech include:

  * Ability to adjust the volume for each software independently
  * Support for audio multiplexing, letting users play audio from multiple applications at the same time
  * Audio streaming over the TCP server
  * The zero-copy memory architecture of PulseAudio lets you transfer audio data between applications and audio devices without unnecessary copying or buffering for lower latency and better resource management
  * Provides compatibility layers for existing applications to work with it without any modifications
  * Variety of modules to provide all kinds of essential functionalities



PipeWire wins in the feature-set game, which is why it is being preferred over PulseAudio.

So, what are the things that make it stand out? Here, they are:

  * A unified solution that aims to replace PulseAudio and JACK to provide a solution for both basic and professional users
  * Better support for low latency
  * Compatible with PulseAudio and JACK APIs.
  * Virtual support for all the Bluetooth codecs by default
  * Efficient at merging devices and resampling
  * It can dynamically switch between different buffer sizes to adapt to the different latency requirements of different audio applications
  * Flatpak application support
  * Wayland desktop support



**Suggested Read 📖**

![][5]

### What's my take on PulseAudio vs. PipeWire?

I'll start with "If it ain't broke, don't fix it".😎

Not every Linux distribution has switched to the PipeWire yet, and some users are enjoying audio like they used to do with PulseAudio. I use PulseAudio as it works just fine with my 5.1 surround setup. So, I don't have any reason to make a switch.

For users with modern Bluetooth headphones or if you have a poor audio experience with PulseAudio, you can switch to PipeWire.

The easiest way to do that is to pick a Linux distribution that offers PipeWire out of the box.

If you want to try PipeWire out of curiosity, make sure to [create a snapshot of your working system][11] before manually installing it:

![][5]

--------------------------------------------------------------------------------

via: https://itsfoss.com/pipewire-vs-pulseaudio/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/content/images/2024/02/linux-audio-illustration.png
[2]: https://itsfoss.com/best-audio-editors-linux/
[3]: https://itsfoss.com/tag/vlc/
[4]: https://itsfoss.com/content/images/2023/12/How-audio-works-in-Linux.png
[5]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[6]: https://itsfoss.com/content/images/2024/02/pulseaudio-ft.png
[7]: https://www.freedesktop.org/wiki/Software/PulseAudio/
[8]: https://itsfoss.com/content/images/2024/02/pipewire-ft.png
[9]: https://www.pipewire.org/
[10]: https://itsfoss.com/content/images/2024/02/pulseaudio-pipewire-works.png
[11]: https://itsfoss.com/backup-restore-linux-timeshift/
