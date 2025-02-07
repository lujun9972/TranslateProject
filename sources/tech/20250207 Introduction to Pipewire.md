[#]: subject: "Introduction to Pipewire"
[#]: via: "https://fedoramagazine.org/introduction-to-pipewire/"
[#]: author: "Roman Gherta https://fedoramagazine.org/author/romangherta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introduction to Pipewire
======

![][1]

Photo by [Michel Didier Joomun][2] on [Unsplash][3] (cropped)

[Pipewire][4] is a multimedia server and framework available as the default sound server in the latest Fedora versions. It is, by design, for low-latency audio and video routing and processing. It is capable of multiplexing multimedia streams to multiple clients – an important feature of modern operating systems.

### General considerations

The evolution of the Linux sound subsystem happened in layers. The lowest layer is the hardware layer with various audio devices. To interact with hardware drivers, Linux has a standardized API called Advanced Linux Sound Architecture ([ALSA][5]). Another layer above ALSA, a sound server, should handle interactions with userspace applications. Initially, that layer was Pulseaudio and Jack, but it was recently replaced by Pipewire. This is an outsider’s first steps with Pipewire. The current version is 1.2.7 on Fedora 41 Workstation.

Pipewire is a socket-activated systemd user service. Note that the session manager is an alias for _wireplumber.service_.

```

    rg@f41:~$ systemctl --user list-unit-files "pipewire*"
    UNIT FILE                        STATE    PRESET
    pipewire.service                 disabled disabled
    pipewire.socket                  enabled  enabled
    pipewire-session-manager.service alias    -

```

#### Permissions and Ownership

The current user owns the process. However, each logged in user has its instance of pipewire.

```

    rg@f41:~$ ps -eo pid,uid,gid,user,comm,label | grep pipewire
    2216  1000  1000 rg pipewire unconfined_t

```

Most multimedia device files to be accessed by this process are located at _/dev/snd_ and _/dev/video_ .

```

    rg@f41:~$ ls -laZ /dev/video* /dev/media* /dev/snd/*
    crw-rw----+ root video system_u:object_r:v4l_device_t:s0   /dev/video0
    crw-rw----+ root video system_u:object_r:v4l_device_t:s0   /dev/media0
    crw-rw----+ root audio system_u:object_r:sound_device_t:s0 hwC0D0
    crw-rw----+ root audio system_u:object_r:sound_device_t:s0 pcmC0D0c
    ...

```

Permissions are [660][6] and restricted to owners that are _root:video_ and _root:audio_. Notice the extra + that indicates ACL permissions. Systemd-logind is the Fedora login manager. This service will, as part of the login process, execute a binary at _/usr/lib/systemd/systemd-logind_. It will create a session and assign a seat. It will change, at login, the file access control list of multimedia devices to the current user. This is how Pipewire has access to device files otherwise owned by _root:audio_ or _root:video_. To check the current file ACL:

```

    rg@f41:~$ getfacl /dev/video0
    # file: dev/video0
    # owner: root
    # group: video
    user::rw-
    user:rg:rw-  # current user
    group::rw-
    mask::rw-
    other::---

```

The command [lsof][7] can show all the processes accessing our sound and video devices:

```

    rg@f41:~$ lsof | grep -E '/dev/snd|/dev/video*|/dev/media*'
    COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
    pipewire  53799 rg     44u   CHR  116,9      0t0  913 /dev/snd/controlC0
    pipewire  53799 rg     83u   CHR   81,0      0t0  884 /dev/video0
    wireplumb 53801 rg     24u   CHR  116,9      0t0  913 /dev/snd/controlC0
    ...

```

Your should expect to see only Pipewire and its session manager (wireplumber) accessing our multimedia devices. Legacy apps accessing these subsystems directly will show up here as well.

#### Configuring

Configuration file _/usr/share/pipewire/pipewire.conf_ is owned by _root:root_ and contains system defaults. Be sure to check the comments; you will find, among other things, the list of loaded modules. The service is configurable with homedir drop-in configuration files. The process is lightweight with only 3 threads. The following demonstrates increasing the number of data loops as a small test.

```

    rg@f41:~$ cat <<EOF > ~/.config/pipewire/pipewire.conf.d/loops.conf
    context.properties = {
       context.num-data-loops = -1
    }
    EOF

    rg@f41:~$ systemctl --user daemon-reload
    rg@f41:~$ systemctl --user restart pipewire.service
    rg@f41:~$ ps -eLo pid,tid,command,comm,pmem,pcpu | grep pipewire
    PID     TID   COMMAND                   COMMAND        PMEM PCPU
    40187   40187 /usr/bin/pipewire         pipewire       0.3  0.0
    40187   40193 /usr/bin/pipewire         module-rt      0.3  0.0
    40187   40194 /usr/bin/pipewire         data-loop.0    0.3  0.0
    40187   40195 /usr/bin/pipewire         data-loop.1    0.3  0.0
    40187   40196 /usr/bin/pipewire         data-loop.2    0.3  0.0
    ...

```

With _pw-config_ you can check the new state of our updated configuration:

```

    rg@f41:~$ pw-config
    {
      "config.path": "/usr/share/pipewire/pipewire.conf",
      "override.config.path": "~/.config/pipewire/pipewire.conf.d/loops.conf"
    }

```

### Some architectural considerations

Pipewire consists of around 30k lines of code in the C programming language. The architecture resembles an event-driven producer-consumer pattern. The control structures are graph-like structures with producer and consumer nodes. One reason for achieving low latency and low CPU utilization is taking advantage of a concept called zero-copy via _memfd_create_. Signaling among the loosely coupled components is achieved using _eventfd_. The code is extensible and modular.

The entire Pipewire state is a graph with the following main elements:

  * Nodes (with input/output ports)
  * Links (edges)
  * Clients (user processes)
  * Modules (shared objects)
  * Factories (module libraries)
  * Metadata (settings)



The graph has nodes and edges/links. Nodes with only input ports are called _sinks_ , and those with only output ports are called _sources_. Nodes with both are usually called _filters_.

#### Modules

Each module provides a specific server functionality. Spend some time screening the module names. There is a module that manages access among graph components, a module managing thread priorities, a module that emulates former Pulseaudio, a module for XDG Portal, a module for profiling, and even a module implementing streaming over the network via RTP.

```

    rg@f41:~$ ls -la /usr/lib64/pipewire-0.3/
    -rwxr-xr-x. 1 root root  28296 Nov 26 01:00 libpipewire-module-access.so
    -rwxr-xr-x. 1 root root  98808 Nov 26 01:00 libpipewire-module-avb.so
    ...

```

#### Plugins

Plugins handle communication with devices, including the creation of ring buffers, used heavily in multimedia processes. There is a plugin that handles communication with ALSA, a plugin that manages communication with Bluetooth, libcamera, etc.

```

    rg@f41:~$ ls -la /usr/lib64/spa-0.2/
    drwxr-xr-x. 1 root root     28 Dec 11 12:13 alsa
    drwxr-xr-x. 1 root root    420 Dec 11 12:13 bluez5
    ...

```

Plugins extend a generic API called SPA, or Simple Plugin API. These self-contained shared libraries provide factories containing interfaces. Because they are self-contained, some of these plugins are used by the session manager. Utility _spa-inspect_ allows querying the shared objects for factories and interfaces.

### Useful Commands

We can see (R)unning nodes with _**pw-top**_. In the following example, there are 3 nodes currently running. Any streaming performed via Pipewire will appear in this output table.

```

    rg@f41:~$ pw-top
    S   ID  QUANT   RATE    WAIT    BUSY  FORMAT         NAME
    R   90    512  48000 139.8us  23.0us  S16LE 2 48000  bluez_output..
    R   99    900  48000  66.7us  37.7us  F32LE 2 48000  + Firefox
    R  112   4320  48000 105.5us  11.4us  S16LE 2 48000  + Videos

```

Quantum (QUANT) can be thought of as the number of audio samples (buffer size) to be processed each graph cycle. This varies depending on the device type and can be configured or negotiated via configuration files. For example, the Videos application has a buffer size of 4320 samples, while the Bluetooth output node has only 512.

Rate (RATE) is the graph processing frequency. In the above output, the graph operates at 48 kHz, meaning each second the graph can process 48,000 samples.

The ratio between Quantum and Rate is the latency in seconds. In the case of Bluetooth headsets, the latency is 11 ms, while for the Videos app it is 90 ms. The _pw-top_ man page provides links to better explanations. Understanding these indicators can help boost performance.

Another powerful utility is _**pw-cli**_ . It opens a shell and allows you to operate interactively on the Pipewire graph at runtime. For permanent changes, you need to amend the configuration files.

```

    rg@f41:~$ pw-cli h
    Available commands:
            help | h                Show this help
        load-module | lm        Load a module.
       unload-module | um      Unload a module.
     connect | con           Connect to a remote.
         disconnect | dis        Disconnect from a remote.
            list-remotes | lr       List connected remotes.
       switch-remote | sr      Switch between current remotes.
       list-objects | ls       List objects or current remote.
      info | i                Get info about an object.
            create-device | cd      Create a device from a factory.
       create-node | cn        Create a node from a factory.
        destroy | d             Destroy a global object.
     create-link | cl        Create a link between nodes.
         export-node | en        Export a local node
           enum-params | e         Enumerate params of an object
        set-param | s           Set param of an object
       permissions | sp        Set permissions for a client
         get-permissions | gp    Get permissions of a client
          send-command | c        Send a command <object-id>
      quit | q                Quit

```

For example, we can print the above streaming nodes with _pw-cli info <id>_ and inspect all the properties.

#### Graph visualization

All the derived utilities are processing the same large JSON graph that represents the Pipewire state. With _**pw-dump**_ we will get this state. But the output is hard to read. Another utility _**pw-dot**_ will give us a user-friendly graph. Take note of the following 3 steps, as you will need to repeat them during this tutorial. The dot utility used in the following example are available with _**Graphviz**_ installation.

```

    rg@f41:~$ pw-dot --detail --all
    rg@f41:~$ dot -Tpng pw.dot -o pw.png
    rg@f41:~$ loupe pw.png

```

It is a large graph. Take a minute to look at the various nodes, the node types distinguished by different colors, and some meaningful properties like the ports, the media class, and the links. You can find a description of these properties in _man 7 pipewire-props_. Observe the _media.name_ property that indicates the current song playing in Firefox.

![][8]

Most of the streams you will see here will be Source/Audio streams.

Fedora 41 Workstation’s new default camera app is [Snapshot][9]. Start the app and you will notice it is visible to Pipewire. Let’s keep Snapshot running and open another camera app. Don’t forget to install _ffmpeg-free_ for the following steps.

```

    rg@f41:~$ ffplay -f v4l2 -i /dev/video0
    /dev/video0: Device or resource busy

```

_**ffplay**_ is trying to access /dev/video0 directly. According to kernel docs, shared data streams should be implemented by a userspace proxy and not by the v4l2 drivers. Pipewire is already using the [libcamera api][10], as you have seen in the plugins list, and offers _pw-v4l2_ as a compatibility wrapper. Let’s use the same command again.

```

    rg@f41:~$ pw-v4l2 ffplay -f v4l2 -i /dev/video0

```

This time it worked, and we have 2 apps that share the same camera stream. This is the added value brought by a high-performing multimedia server. We also see both Source/Video streams in the graph. The same is valid for the browser. In your browser configuration you should be able to choose whether to use Pipewire or v4l2 devices.

You can also use [Helvum][11] or [Qpwgraph][12]. Go ahead and test any of these apps. You will find a simplified graph with only certain node types and drag-and-drop features. You will appreciate the ease of use, but sometimes you will need the full graph and the full set of node properties. In such cases, you will revert to _pw-dump_ , _pw-cli_ , and _pw-dot_.

#### Managing nodes

One way to manage temporary graph nodes is to use _pw-cli_. For example, here we are creating a temporary test node, valid for as long as the session is open. For factory names, check the [source code][13] and some useful examples in the conf page comments.

```

    rg@f41:~$ PIPEWIRE_DEBUG=2 pw-cli
    pipewire-0>> create-node spa-node-factory factory.name=support.node.driver node.name=mynewnode

```

Another way to create nodes, but this time in our permanent configuration, is as described in the configuration comments:

```

    rg@f41:~$ cat <<EOF > ~/.config/pipewire/pipewire.conf.d/mynewnode.conf
    context.objects = [{
    factory = adapter
    args = {
        factory.name           = api.alsa.pcm.source
        node.name              = "alsa-testnode"
        node.description       = "PCM TEST"
        media.class            = "Audio/Source"
        api.alsa.path          = "hw:0"
        api.alsa.period-size   = 1024
        audio.format           = "S16LE"
        audio.channels         = 2
        audio.position         = "FL,FR" }
    }]
    EOF
    rg@f41:~$ systemctl --user daemon-reload
    rg@f41:~$ systemctl --user restart pipewire.service

```

A faster and easier way to create nodes is to use helper utilities _**pw-record**_ and _**pw-play**_ to create sinks and sources. We will make a small example in the last paragraph.

### Security considerations

The binary is owned by root and can be executed by other users.

```

    rg@f41:~$ ls -la /usr/bin/pipewire
    -rwxr-xr-x. 1 root root 20104 Nov 26 01:00 /usr/bin/pipewire

```

The protocol used for socket communication is called [native protocol][14]. Sockets have larger permissions, as do other systemd temporary files. It’s good to remember that _/run_ is a tmpfs in-memory filesystem.

```

    rg@f41:~$ ls -laZ /run/user/1000/pipewire*
    srw-rw-rw-. rg rg object_r:user_tmp_t:s0 pipewire-0
    -rw-r-----. rg rg object_r:user_tmp_t:s0 pipewire-0.lock
    srw-rw-rw-. rg rg object_r:user_tmp_t:s0 pipewire-0-manager
    -rw-r-----. rg rg object_r:user_tmp_t:s0 pipewire-0-manager.lock

```

The systemd sockets create the stream structures; afterwards, the audio nodes will communicate directly via memfd. According to the man page, _memfd_create_ creates an anonymous, in-memory file, vital for performance. Pipewire source code uses these calls with certain flags like MFD_HUGETLB and also flags like MFD_ALLOW_SEALING, MFD_CLOEXEC, etc. to seal and prevent memory leaks to other processes.

Pipewire comes with a module called _protocol-pulse_. The module has a separate systemd socket-activated user service. This emulates a PulseAudio server for compatibility with a large range of clients still using the PulseAudio libraries.

```

    rg@f41:~$ ls -laZ /run/user/1000/pulse/native
    srw-rw-rw-. rg rg user_tmp_t:s0 /run/user/1000/pulse/native

```

Systemd offers ways to analyze and sandbox services. Some recommendations are available in the following but they do not assure system-level protection.

```

    rg@f41:~$ systemd-analyze --user --no-pager security pipewire.service

```

Any userspace application can view the graph, access the socket, and create nodes. The node properties carry, in some cases, information that might be private. The _media.name_ property is an example. This does not happen for private Firefox tabs. This property might be useful for certain GUI features, like Gnome tray notifications.

You may have noticed a node called _speech-dispatcher_ randomly connected to your speaker. This accessibility feature may be requested by various programs, including your browser. Try to understand this behavior in your favorite multimedia apps.

### Example

As a small example, let’s try to create an audiobook – voice recognition stream with Pipewire source and sink nodes. Let’s create the source node using _pw-play_. In other scenarios, _pw-play_ can read from stdin (-).

```

    rg@f41:~$ curl https://ia600707.us.archive.org/8/items/alice_in_wonderland_librivox/wonderland_ch_10_64kb.mp3 --output test.mp3

    rg@f41:~$ ffmpeg -i test.mp3 -ar 48000 -ac 1 -sample_fmt s16 test.wav

    rg@f41:~$ pw-play --target=0 --format=s16 \
    --quality=14 --media-type=Audio --channels=1 \
    --properties='{node.name=mytestsource}' test.wav

```

Auto-connection of the process to the speakers did not occur because of the target argument. Let’s create the sink node. For simplicity we will use the _pocketsphinx_ package to test voice recognition.

```

    rg@f41:~$ dnf install pocketsphinx
    rg@f41:~$ pw-record --media-type=Audio --target=0 --rate=16000 \
     --channels=1 --quality=14 --properties='{node.name=mytestsink}' - \
     | pocketsphinx live -

```

As you can see, we created a sink node. Auto-connection did not occur to any source node, as indicated by the target argument. The other arguments, like the number of channels, are recommendations from Pocketsphinx man pages. We will create the links manually. Use _pw-dot_ to find the source and sink node and port ids. Alternatively, you can use any of the two flatpak apps to create the links by drag-and-drop.

```

    rg@f41:~$ PIPEWIRE_DEBUG=2 pw-cli
    pipewire-0>> create-link <nodeid> <portid> <nodeid> <portid>

```

We created a stream between a source and a sink and can already see some output in the Pocketsphinx terminal. The processes involved are visible to Pipewire and can take advantage of all its capabilities. In a similar way, you can interface with your favorite Flatpak. Many of these apps exist in a sandbox and interact with the underlying system using the XDG Portal APIs.

### Another example

Let’s try to make another example, involving filters. We have previously seen that Pipewire has a module called _filter-chain_. First of all, we will need to install the desired filter plugins. There is a large variety of LADSPA and LV2 filter plugins in DNF repos. Pipewire also has a few _built-in filters_ made available by the _audiomixer_ plugin.

```

    rg@f41:~$ dnf install ladspa ladspa-rev-plugins
    rg@f41:~$ rpm -ql ladspa-rev-plugins
    /usr/lib64/ladspa/g2reverb.so

```

As we can see, the package installed a shared object. For LADSPA plugins we can extract metadata using the _analyseplugin_ utility. Important information is visible in the following output:

```

    rg@f41:~$ analyseplugin /usr/lib64/ladspa/g2reverb.so
    Plugin Name: "Stereo reverb"
    Plugin Label: "G2reverb"
    Ports:       ...
           "Room size" input, control, 10 to 150
         "Reverb time" input, control, 1 to 20
         "Input BW" input, control, 0 to 1
     "Damping" input, control, 0 to 1
      "Dry sound" input, control, -80 to 0
          "Reflections" input, control, -80 to 0
        "Reverb tail" input, control, -80 to 0

```

Based on this we can create the filter file. Make sure the plugin name, location, label, and type are correct.

```

    rg@f41:~$ cat <<EOF > ~/.config/pipewire/pipewire.conf.d/myfilter.conf
    context.modules = [
    {
         name = libpipewire-module-filter-chain
         args = {
             node.description =  "My filter"
             media.name =  "My filter"
             filter.graph = {
                 nodes = [
                     {
                         type = ladspa
                         name = "Stereo reverb"
                         plugin = "/usr/lib64/ladspa/g2reverb.so"
                         label = "G2reverb"
                         control = {
                            "Reverb time" = 2
                         }
                     }
                    ]
              }

              audio.channels = 2
              audio.position = [ FL FR ]

              capture.props = {
                  node.name =  "myfilter"
                  media.class = Audio/Sink
                  node.target = 0
              }

              playback.props = {
                  node.name =  "myfilter"
                  media.class = Audio/Source
                  node.target = 0
              }
         }
    }
    ]
    EOF

    rg@f41:~$ systemctl --user restart pipewire.service

```

Check the graph, for example with Qpwgraph, to show the filter sink/source pair. Note that the sink node also has monitor ports. These ports allow inspection of the stream before processing. Now create the source node as before:

```

    rg@f41:~$ pw-play --target=0 --format=s16 --media-type=Audio \
    --properties='{node.name=mytestsource}' test.mp3

```

Connect the nodes manually by drag-and-drop to your Audio Controller Speaker. Your setup should appear as below:

![][15]

Confirm the narrator’s voice has a reverb effect. Now feel free to experiment with your favorite plugins or more nodes in your filter. The [filter-chain][16] folder contains other useful examples. Remember to delete the test configurations from the _.config_ folder when you complete you exploration.

### Conclusions

Pipewire is an interesting piece of low-level, high-performing software. We have discussed the main commands and configuration options and filesystem interactions. Reading the Pipewire [docs][17] is highly recommended. Hopefully you will have enough context to better understand the encountered terms. Thanks to the people maintaining the mentioned packages.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introduction-to-pipewire/

作者：[Roman Gherta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/romangherta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/02/intro_to_pipewire-816x345.jpg
[2]: https://unsplash.com/@didierjoomun?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/black-and-gray-audio-mixer-zPo9pPnUNdA?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://github.com/PipeWire/pipewire
[5]: https://kernel.org/doc/html/latest/sound/index.html
[6]: https://fedoramagazine.org/command-line-quick-tips-more-about-permissions/
[7]: https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/
[8]: https://fedoramagazine.org/wp-content/uploads/2025/01/pw.png
[9]: https://flathub.org/apps/org.gnome.Snapshot
[10]: https://libcamera.org/introduction.html
[11]: https://flathub.org/apps/org.pipewire.Helvum
[12]: https://flathub.org/apps/org.rncbc.qpwgraph
[13]: https://github.com/PipeWire/pipewire/blob/master/spa/include/spa/utils/names.h
[14]: https://github.com/PipeWire/pipewire/blob/master/doc/dox/internals/protocol.dox
[15]: https://fedoramagazine.org/wp-content/uploads/2025/01/qpwgraph.png
[16]: https://github.com/PipeWire/pipewire/tree/master/src/daemon/filter-chain
[17]: https://docs.pipewire.org/
