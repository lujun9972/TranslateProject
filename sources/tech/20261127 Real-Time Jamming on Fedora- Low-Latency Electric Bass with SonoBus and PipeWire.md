[#]: subject: "Real-Time Jamming on Fedora: Low-Latency Electric Bass with SonoBus and PipeWire"
[#]: via: "https://fedoramagazine.org/real-time-jamming-on-fedora-low-latency-electric-bass-with-sonobus-and-pipewire/"
[#]: author: "Mino Mitrugno https://fedoramagazine.org/author/minomit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Real-Time Jamming on Fedora: Low-Latency Electric Bass with SonoBus and PipeWire
======

![][1]

Photo by [Balázs Horváth][2] on [Unsplash][3] [cropped]

Thanks to **Fedora Linux** and its native adoption of the **PipeWire** architecture, real-time audio production and streaming on Linux have become extremely accessible and rock-solid. By pairing PipeWire with the open-source application **SonoBus** , you can transform your Fedora workstation into a virtual studio for ultra-low-latency remote rehearsals and jam sessions.

Remote music collaboration has always been a complex challenge: even a few milliseconds of delay (latency) can make it impossible for a bassist and a drummer to stay "in the pocket." Traditionally, configuring low-latency audio on Linux required complex setups involving the JACK audio server, specific system permissions, and custom shell scripts.

In this step-by-step guide, we will walk through setting up your gear, optimizing Fedora's system audio parameters, and managing signal routing to play in real time with musicians anywhere in the world.

> **Usage Note:** While this guide uses the **electric bass** (the author's instrument of choice) as a practical baseline, all procedures, PipeWire configuration commands, buffer optimizations, and SonoBus settings apply identically to **any other musical instrument** (guitar, keyboard, electronic drums, vocals, or synthesizers).

* * *

### 1\. Hardware and Prerequisites for a Clean Audio Chain

Before tweaking software configurations, it is essential to ensure that your physical hardware chain is up to the task. Real-time audio does not forgive hardware or network bottlenecks.

#### Hardware Requirements

  * **Electric Bass (or other instrument)** : Provide an active or passive pickup system. This is equally valid for guitars, keyboards, electronic drums, and microphones.
  * **USB Audio Interface** : Provide a high-impedance input ( **Hi-Z** or **Instrument / DI** ) for string instruments, or Line/XLR inputs for other instruments and microphones. This is essential to preserve frequency response and signal level prior to analog-to-digital conversion.
  * **Monitoring Headphones** : Use studio wired headphones plugged directly into the audio interface’s headphone jack. **Strictly avoid Bluetooth headphones or speakers** , as the wireless protocol introduces an unavoidable 50 to 200 ms of added latency.



#### Network Requirements

  * **Wired Ethernet Connection** : Connect your computer to the router via a Cat6 (or higher) Ethernet cable. **Do not use Wi-Fi** : even on high-speed wireless networks, Wi-Fi suffers from unpredictable packet delivery variations ( _jitter_ ), which result in constant pops, crackles, and audio stream dropouts.



* * *

### 2\. Software Installation on Fedora: SonoBus and qpwgraph

Fedora Linux makes installation of both SonoBus and qpwgraph possible via **dnf** or **Flatpak/Flathub**.

#### Installing SonoBus via Flatpak

**SonoBus** is an open-source peer-to-peer application for high-quality, low-latency audio streaming. The easiest and most up-to-date way to install it on Fedora is via Flathub:

```

    flatpak install flathub net.sonobus.SonoBus

```

dnf installation is similar to the process described in the following section.

#### Installing qpwgraph via DNF

To visually manage audio connections (routing channels between your interface, instrument, and effects), the official recommended graph tool for PipeWire is **qpwgraph** (developed by the author of QjackCtl):

```

    sudo dnf install qpwgraph

```

**qpwgraph** presents a graphical node matrix where you can connect physical and virtual audio inputs and outputs using your mouse.

Flatpak installation is similar to that describe for sonobus, above.

* * *

### 3\. System Latency Optimization with PipeWire

To achieve a true "real amp" feel, total round-trip latency (from picking a string to hearing it in your headphones) should ideally stay under **10–15 milliseconds**. PipeWire allows you to dynamically alter the buffer size ( _quantum_ ) and sample rate without restarting the audio daemon or system.

#### Recommended PipeWire Parameters

Parameter | Recommended Value | Description
---|---|---
**Sample Rate** | 48000 Hz (48 kHz) | Standard for digital audio and SonoBus.
**Buffer Size (Quantum)** | 128 or 256 samples | 128 gives ~2.6 ms theoretical latency; 256 gives ~5.3 ms.

#### Quick Terminal Configuration

You can temporarily set PipeWire's latency for your current session using the pw-metadata command:

```

    # Force sample rate to 48kHz
    pw-metadata -n settings 0 clock.force-rate 48000

    # Force buffer size to 128 samples (ultra-low latency)
    pw-metadata -n settings 0 clock.force-quantum 128

```

Note: if your audio interface or CPU experiences small pops or crackles ( _xruns_ ), simply raise the buffer size to 256 samples:

```

    pw-metadata -n settings 0 clock.force-quantum 256

```

#### Launching SonoBus with Forced Latency

Alternatively, you can launch SonoBus directly with PipeWire environment variables:

```

    PIPEWIRE_LATENCY="128/48000" flatpak run net.sonobus.SonoBus

```

* * *

### 4\. Audio Routing Setup and SonoBus Room Configuration

With the software installed and system latency tuned, let's configure your live session in the following three steps:

#### 4.1: Physical Connections and Gain Staging

  1. Connect your instrument to **INPUT 1** (Hi-Z/Instrument) on your audio interface.
  2. Adjust the **Gain** knob on the interface so that hard picking or slap peaks hit around **-12 dB to -6 dB** on the meter, avoiding red clipping.



#### 4.2: Visual Routing in qpwgraph

  1. Open **qpwgraph**.
  2. Locate the node for your USB audio interface (e.g., _USB Audio Interface Capture_ ).
  3. Locate the **SonoBus** nodes ( _SonoBus Input_ and _SonoBus Output_ ).
  4. Drag a virtual patch cable from **Capture 1** (where your instrument is connected) directly into **SonoBus Input L** (or mono).
  5. Ensure **SonoBus Output L/R** is connected to your headphone outputs on the interface ( _Playback 1/2_ ).



![][4]

#### 4.3: Setting Up a Room in SonoBus

  1. Open **SonoBus**.
  2. Click **Connect** in the upper left corner.
  3. Enter a group/room name ( **GroupName** ) and your display name.
  4. Once connected, share the room name with your bandmates.
  5. Under your input signal panel, set the audio format to **Opus PCM Uncompressed** or **Opus 64-96 kbps** , depending on your available internet bandwidth.



* * *

### 5\. Best Practices and Tips for Live Jamming

To ensure smooth, uninterrupted jam sessions, keep these practical tips in mind:

  * **SonoBus Jitter Buffer Management** : In the SonoBus options, set the receive buffer to **Auto** or manually adjust the buffer in milliseconds based on the network stability of your remote bandmates.
  * **Direct Monitoring (Pan & Mix)**: SonoBus allows you to adjust the volume and stereo panning for each participant in the room. Placing your own instrument in the center while panning guitars or keyboards slightly left and right can dramatically improve listening clarity.
  * **Effects and Amp Modeling (Optional)** : If you want to process your sound with an amp simulator or plugin chain before sending it to SonoBus, you can use hosts like **Carla** , **Guitarix** , or tools from **Fedora Jam**. Insert the effect node between your instrument capture node and SonoBus input in qpwgraph.



* * *

### Conclusion

Fedora Linux and PipeWire offer musicians a professional, rock-solid, and immediate audio infrastructure. By setting buffer sizes properly and leveraging SonoBus, conducting remote rehearsals with an electric bass — or any other instrument — becomes a natural, fluid, and ultra-low-latency experience.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/real-time-jamming-on-fedora-low-latency-electric-bass-with-sonobus-and-pipewire/

作者：[Mino Mitrugno][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/minomit/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/11/jamming_on_feodra-816x345.jpg
[2]: https://unsplash.com/@balage77?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/white-electric-bass-guitar-fxbR4QuuL8Y?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://fedoramagazine.org/wp-content/uploads/2026/11/Visual_Routing_qpwgraph-1024x563.png
