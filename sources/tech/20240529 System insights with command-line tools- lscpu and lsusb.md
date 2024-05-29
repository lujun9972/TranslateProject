[#]: subject: "System insights with command-line tools: lscpu and lsusb"
[#]: via: "https://fedoramagazine.org/system-insights-with-command-line-tools-lscpu-and-lsusb/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

System insights with command-line tools: lscpu and lsusb
======

![][1]

Photo by [Hunter Harritt][2] on [Unsplash][3]

### Introduction

Fedora (and other common Linux setups out there) offers you an array of tools for managing, monitoring, and understanding the system. Among these tools are a series of commands that begin with _ls_ (for “list”).

They provide easy insights into various aspects of the system’s hardware and resources. This article series gives you an intro and overview over many of them, starting with the simpler ones. The post will cover _lscpu_ and _lsusb_.

### _lscpu_ – Display CPU information

The _lscpu_ command gathers and displays information about the CPU architecture. It is provided by the _util-linux_ package. The command gathers CPU information from multiple sources like _/proc/cpuinfo_ and architecture-specific libraries (e.g. _librtas_ on PowerPC):

```

    $ lscpu

```

This command outputs information like the number of CPUs, threads per core, cores per socket, and the CPU family and model.

If asked, it outputs detailed CPU information in JSON format. This provides a structured view that is particularly useful for scripting and automation:

```

    $ lscpu --extended --json

```

#### **Advanced usage** example

With the machine readable JSON output, you can extract information using _jq_ (a powerful command-line tool that allows users to parse, filter, and manipulate JSON data efficiently and worth an article of its own). For example, the following command will extract the current MHz for each CPU:

```

    export LANG=en_US.UTF-8
    export LC_ALL="en_US.UTF-8"
    lscpu --json --extended \
      | jq '.cpus[] | {cpu: .cpu, mhz: .mhz}'

```

Let’s look at the single parts of the command:

  * _export LANG=en_US.UTF-8_ and _export LC_ALL=”en_US.UTF-8″_ are making sure that the output is not using localized numbers. For example, a German language setting can result in broken JSON output because of the use of commas in place of periods as floating point separators.
  * _lscpu –json –extended_ generates the detailed CPU information in JSON format.
  * _jq ‘.cpus[] |_ will iterate over each entry in the cpus array. The _{cpu: .cpu, mhz: .mhz}_ ‘ part constructs a new JSON object for each CPU entry showing the CPU number ( _cpu_ ) and its current frequency in MHz ( _mhz_ ).



Example output from a laptop operating in performance mode:

```

    $ lscpu --json --extended \
      | jq '.cpus[] | {cpu: .cpu, mhz: .mhz}'
    {
      "cpu": 0,
      "mhz": 3700.0171
    }
    {
      "cpu": 1,
      "mhz": 3700.2241
    }
    {
      "cpu": 2,
      "mhz": 3700.1121
    }
    {
      "cpu": 3,
      "mhz": 3884.2539
    }

```

and later in power saver mode:

```

    $ lscpu --json --extended \
      | jq '.cpus[] | {cpu: .cpu, mhz: .mhz}'
    {
      "cpu": 0,
      "mhz": 1200.0580
    }
    {
      "cpu": 1,
      "mhz": 1200.0070
    }
    {
      "cpu": 2,
      "mhz": 1200.5450
    }
    {
      "cpu": 3,
      "mhz": 1200.0010
    }

```

### lsusb – Display USB Devices Information

The _lsusb_ command displays detailed information about the USB buses in the system and the devices connected to them. It is provided by the _usbutils_ package and helps users and system administrators easily view the configuration and the devices attached to their USB interfaces:

```

    $ lsusb

```

This produces a list of all USB buses, devices connected to them, and brief information about each device, such as ID and manufacturer. This is particularly useful for a quick check of what devices are connected to the system and if you need the USB device ID for udev rules or the like.

#### U **sage** example and output

For those needing more detailed information about the USB devices, _lsusb_ allows listing more detailed information:

```

    $ lsusb | grep Fibocom
    Bus 001 Device 013: ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem

    $ sudo lsusb -d 2cb7:0210 -v
    Bus 001 Device 013: ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem
    Device Descriptor:
      bLength                18
      bDescriptorType         1
      bcdUSB               2.00
      bDeviceClass          239 Miscellaneous Device
      bDeviceSubClass         2 [unknown]
      bDeviceProtocol         1 Interface Association
      bMaxPacketSize0        64
      idVendor           0x2cb7 Fibocom
      idProduct          0x0210 L830-EB-00 LTE WWAN Modem
      bcdDevice            3.33
      iManufacturer           1 FIBOCOM
      iProduct                2 L830-EB-00
      iSerial                 3 004999010640000
      bNumConfigurations      1
      Configuration Descriptor:
        bLength                 9
        bDescriptorType         2
        wTotalLength       0x00a1
        bNumInterfaces          4
        bConfigurationValue     1
        iConfiguration          0
        bmAttributes         0xe0
          Self Powered
          Remote Wakeup
        MaxPower              100mA
    [ more output omitted for readability ]

```

Using the _-v_ and _-t_ options will tell _lsusb_ to dump the physical USB device hierarchy as a tree including IDs. The following shows a detailed tree of all USB devices (here using a ThinkPad T480S), their types, speeds, and device classes. This is particularly useful for troubleshooting USB device issues:

```

    $ lsusb -t -v
    /:  Bus 001.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/12p, 480M
        ID 1d6b:0002 Linux Foundation 2.0 root hub
        |__ Port 001: Dev 002, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
        |__ Port 002: Dev 003, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 046a:c098 CHERRY
        |__ Port 002: Dev 003, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
            ID 046a:c098 CHERRY
        |__ Port 003: Dev 004, If 0, Class=Chip/SmartCard, Driver=usbfs, 12M
            ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
        |__ Port 005: Dev 005, If 0, Class=Video, Driver=uvcvideo, 480M
            ID 5986:2123 Bison Electronics Inc.
        |__ Port 005: Dev 005, If 1, Class=Video, Driver=uvcvideo, 480M
            ID 5986:2123 Bison Electronics Inc.
        |__ Port 006: Dev 013, If 0, Class=Communications, Driver=cdc_mbim, 480M
            ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem
        |__ Port 006: Dev 013, If 1, Class=CDC Data, Driver=cdc_mbim, 480M
            ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem
        |__ Port 006: Dev 013, If 2, Class=Communications, Driver=cdc_acm, 480M
            ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem
        |__ Port 006: Dev 013, If 3, Class=CDC Data, Driver=cdc_acm, 480M
            ID 2cb7:0210 Fibocom L830-EB-00 LTE WWAN Modem
        |__ Port 007: Dev 007, If 0, Class=Wireless, Driver=btusb, 12M
            ID 8087:0a2b Intel Corp. Bluetooth wireless interface
        |__ Port 007: Dev 007, If 1, Class=Wireless, Driver=btusb, 12M
            ID 8087:0a2b Intel Corp. Bluetooth wireless interface
        |__ Port 008: Dev 008, If 0, Class=Video, Driver=uvcvideo, 480M
            ID 5986:2115 Bison Electronics Inc.
        |__ Port 008: Dev 008, If 1, Class=Video, Driver=uvcvideo, 480M
            ID 5986:2115 Bison Electronics Inc.
        |__ Port 009: Dev 009, If 0, Class=Vendor Specific Class, Driver=[none], 12M
            ID 06cb:009a Synaptics, Inc. Metallica MIS Touch Fingerprint Reader
    /:  Bus 002.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/6p, 5000M
        ID 1d6b:0003 Linux Foundation 3.0 root hub
        |__ Port 003: Dev 002, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
            ID 0bda:0316 Realtek Semiconductor Corp. Card Reader
    /:  Bus 003.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 480M
        ID 1d6b:0002 Linux Foundation 2.0 root hub
        |__ Port 001: Dev 002, If 0, Class=Hub, Driver=hub/5p, 480M
            ID 0451:8442 Texas Instruments, Inc.
            |__ Port 001: Dev 003, If 0, Class=Hub, Driver=hub/7p, 480M
                ID 0424:2137 Microchip Technology, Inc. (formerly SMSC)
            |__ Port 003: Dev 005, If 0, Class=Hub, Driver=hub/3p, 480M
                ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub
                |__ Port 001: Dev 006, If 0, Class=Vendor Specific Class, Driver=r8152, 480M
                    ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
            |__ Port 004: Dev 004, If 0, Class=Human Interface Device, Driver=usbhid, 480M
                ID 0451:82ff Texas Instruments, Inc.
    /:  Bus 004.Port 001: Dev 001, Class=root_hub, Driver=xhci_hcd/2p, 10000M
        ID 1d6b:0003 Linux Foundation 3.0 root hub

```

### Conclusion

Even though they are simple, both commands offer insights into the system’s configuration and status. Whether you’re troubleshooting, optimizing, or simply curious, these tools provide valuable data that can help you better understand and manage your Linux environment. See you next time when we will have a look at more useful listing and information command line tools and how to use them.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/system-insights-with-command-line-tools-lscpu-and-lsusb/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/insights_via_cli-lscpu-lsusb-816x345.jpg
[2]: https://unsplash.com/@hharritt?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/red-and-blue-lights-from-tower-steel-wool-photography-Ype9sdOPdYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
