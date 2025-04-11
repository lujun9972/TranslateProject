[#]: subject: "Introduction to Wireplumber"
[#]: via: "https://fedoramagazine.org/introduction-to-wireplumber/"
[#]: author: "Roman Gherta https://fedoramagazine.org/author/romangherta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introduction to Wireplumber
======

![][1]

Photo by [Michel Didier Joomun][2] on [Unsplash][3] (cropped)

Wireplumber is the session and policy manager for Pipewire. It has its own systemd user service. It is a separate [project][4], with separate concerns. Current version is 0.5.8 on Fedora Workstation 41.

> _Session managers save the current state of open audio applications along with their connections, allowing sessions to be easily restored without having to manually open each application, load individual settings files, and reconnect all connections_ – [LinuxAudio][5]

As you have seen in the [previous article,][6] we can add nodes via Pipewire configuration files or arbitrary CLI commands. But the operating system is a complex dynamic system. A lot of things can happen; for example, you can plug in your headphones any time, or you can switch between video and audio streaming. There appears to be a need for a separate controller to react to the various multimedia events. This controller or manager is Wireplumber.

### What is included with Wireplumber

Let’s look at the installed files before moving to documentation. There are some utilities, like _wpctl_ and _wpexec_ , a few configuration files, and quite a lot of Lua files in the scripts folder.

```

    rg@f41:~$ rpm -ql wireplumber
    /usr/bin/wireplumber
    /usr/bin/wpctl
    /usr/bin/wpexec
    /usr/share/wireplumber/wireplumber.conf
    /usr/lib/systemd/user/wireplumber.service
    /usr/share/wireplumber/scripts/client/access-default.lua
    ...

```

Wireplumber comes with shared libraries. Take a moment to review the module names.

```

    rg@f41:~$ ls -l /usr/lib64/wireplumber-0.5/
    -rwxr-xr-x. root libwireplumber-module-dbus-connection.so
    -rwxr-xr-x. root libwireplumber-module-logind.so
    -rwxr-xr-x. root libwireplumber-module-standard-event-source.so
    ...

```

As an example, the logind module, shown in this list, is used to check some logic involving bluetooth and logind active seat.

### Utility Programs

Two utilities are available in the wireplumber package.

  * _Wpexec_ contains the execution context; you will see it in use in some Lua executable files.


  * _Wpctl_ allows the dynamic modification of settings. To check all available settings, use wpctl settings.



```

    rg@f41:~$ wpctl
    Usage:
      wpctl [OPTION…] COMMAND [COMMAND_OPTIONS] - WirePlumber Control CLI

    Commands:
      status
      get-volume ID
      inspect ID
      set-default ID
      set-volume ID VOL[%][-/+]
      set-mute ID 1|0|toggle
      set-profile ID INDEX
      set-route ID INDEX
      clear-default [ID]
      settings [KEY] [VAL]
      set-log-level [ID] LEVEL

```

### Configuring

The configuration file is similar, to some degree, to the Pipewire configuration file:

```

    rg@f41:~$ less /usr/share/wireplumber/wireplumber.conf
    context.spa-libs = { ... }
    context.modules = [ ... ]
    wireplumber.profiles = { ... }
    wireplumber.components = [ ... ]
    wireplumber.components.rules = [ ... ]
    wireplumber.settings.schema = { ... }

```

Sections _spa-libs_ and _modules_ import a few audio and Pipewire libraries. The _profiles_ section defines a few basic profiles in terms of the offered features (audio/video/bluez). The _components_ section loads a list of various functional parts from the modules. These can range from logging to Lua scripting engine and event hooks. Each component provides a specific feature. The _settings_ section contains well-known multimedia settings with a detailed description. Configuration can be changed using _wpctl_ or homedir drop-in configuration files.

### Example

In the following example, we disable a specific feature of the _main_ profile. Don’t forget to revert the change once tested.

```

    cat <<EOF > ~/.config/wireplumber/wireplumber.conf.d/50.conf
    wireplumber.profiles = {
      main = {
        hardware.video-capture = disabled
      } }
    EOF

    rg@f41:~$ systemctl --user restart wireplumber.service

```

### Interaction with Pipewire

Wireplumber interacts with Pipewire via metadata objects. Let’s use _wpctl settings_ to change one of the well-known settings, like the default sink volume.

```

    rg@f41:~$ wpctl settings device.routes.default-sink-volume 0.23
    rg@f41:~$ pw-metadata -n sm-settings 0 device.routes.default-sink-volume
    Found "sm-settings" metadata 36
    update: id:0 key:'device.routes.default-sink-volume' value:'0.23' type:'Spa:String:JSON'
    ...

```

Notice that using _pw-metadata_ shows Pipewire has the updated value for this setting. To make the setting persistent across restarts, we can save it in the Wireplumber persistent state.

```

    rg@f41:~$ wpctl settings --save device.routes.default-sink-volume 0.23
    rg@f41:~$ cat ~/.local/state/wireplumber/*
    device.routes.default-sink-volume=0.23
    ...

```

It is worth your time to investigate all the other saved properties. You will find the current sink volume. You will also find some client or application-specific settings. The same is true for interaction with gnome-sound-panel. When you change the GUI volume, you should see the updated value saved in the state folder. When you change the default sink from speaker to headset, you should see this reflected in the _wpctl status_ output.

It would also be beneficial to look over the Lua scripts to understand the logic behind their actions and perhaps to find templates that you can use as examples for your own configurations.

### Lua Scripting

It is worth mentioning a little bit about the scripts. Lua is a simple and easy-to-learn scripting language. The scripts, in many cases, are importing some shared objects (i.e. spa-plugins) that provide the ability to orchestrate the Pipewire graph. In this way, a more complex logic is achievable. Check [media-role-nodes.conf][7] for an example of such logic. There media streams are grouped by roles and assigned to virtual sinks with different priorities for gaming, multimedia, voice assistant, navigation, emergency alarms, etc.

In the [previous article,][6] whenever we chose the --target argument for pw-play, the logic of creating the necessary node links was implemented by Wireplumber in the _find-defined-target.lua_ file provided by this package.

### Example

Here we demonstrate creating a simple script to list all streaming nodes.

```

    cat <<EOF > ~/.local/share/wireplumber/scripts/10-medialog.lua
    log = Log.open_topic("logger-media")

    node_om = ObjectManager {
      Interest {
        type = "node",
        Constraint { "media.class",
                     "matches",
                     "Stream/Output/Audio", type = "pw-global"
                   }
      }
    }

    node_om:connect("object-added", function (om, node)
      log:notice(node, "Process [" .. node.properties["application.process.binary"] ..
      "] -- [" .. node.properties["media.name"] .. "]"
    )
    end)

    node_om:activate()
    EOF

```

We can include this as a separate Wireplumber feature and then restart the _wireplumber.service_ and verify using _journalctl_ :

```

    cat <<EOF > ~/.config/wireplumber/wireplumber.conf.d/70-media.conf
    wireplumber.components = [
      {
        name = "10-medialog.lua", type = script/lua
        provides = logger-media
      }
    ]

    wireplumber.profiles = {
      main = {
        logger-media = required
      }
    }
    EOF


    rg@f41:~$ systemctl --user restart wireplumber.service
    rg@f41:~$ journalctl --user -u wireplumber.service -g logger-media

    12:38:00 logger-media: <WpNode:99:0x564>
    Process [gnome-shell] -- [bell-window-system]
    12:38:00 logger-media: <WpNode:87:0x564>
    Process [firefox] -- [The Woods in Lorn]

```

Alternatively, you can execute the lua scripts individually by including the shebang _#!/usr/bin/wpexec_ as the first line.

### Conclusions

In this article we investigated the capabilities offered by a powerful media session manager and demonstrated implementing our own session logic. Wireplumber [docs][8] are well written and describe this topic, and much more, in greater detail. Thanks to the people and organizations maintaining all the above-mentioned packages.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introduction-to-wireplumber/

作者：[Roman Gherta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/romangherta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/intro_to_wireplumber-816x345.jpg
[2]: https://unsplash.com/@didierjoomun?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/black-and-gray-audio-mixer-zPo9pPnUNdA?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/wireplumber-the-new-pipewire-session-manager/
[5]: https://wiki.linuxaudio.org/wiki/session_management
[6]: https://fedoramagazine.org/introduction-to-pipewire/
[7]: https://github.com/PipeWire/wireplumber/blob/master/src/config/wireplumber.conf.d.examples/media-role-nodes.conf
[8]: https://pipewire.pages.freedesktop.org/wireplumber/
