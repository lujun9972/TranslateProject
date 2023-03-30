[#]: subject: "Use sysfs to restart failed PCI devices (WiFi cards, sound cards, etc.)"
[#]: via: "https://fedoramagazine.org/use-sysfs-to-restart-failed-pci-devices/"
[#]: author: "Mateus Rodrigues Costa https://fedoramagazine.org/author/mateusrodcosta/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use sysfs to restart failed PCI devices (WiFi cards, sound cards, etc.)
======

![][1]

Photo by [Malachi Brooks][2] on [Unsplash][3]

This article describes one method of restarting PCI devices. It demonstrates restarting a wireless device. But the concept should work on any device whose device driver has adequate hotplug support.[[1]][4]

Computers typically consist of several interconnected devices. Some devices can be physically disconnected and reconnected with ease (for example, most USB devices). Others might require a specific interaction with the operating system or specific software. And others will require a full reboot.

Built-in laptop wireless cards are PCI devices that could fail at runtime but might not be easy to physically disconnect and reconnect without a full reboot. In many cases these devices can be restarted through Linux’s _sysfs_ interface without having to do a full reboot of the computer.

This article will specifically demo how to restart an Atheros wireless card which has locked up.

### How to restart PCI devices

Depending on your particular desktop environment and hardware, it may be possible to switch the PCI card off and back on using a GUI or hardware switch or button. But if none of those options exist or work, the following CLI method of restarting the PCI card might prove useful.

To restart a wireless card you will need its PCI _domain_ , _bus_ , _device_ and _function_ address. Run the _lspci_ command, as shown below, and search its output to find your wireless card’s PCI address.

```

    $ lspci
    <snip>
    3d:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

```

In the above example, the PCI address of the Atheros card is **3d:00.0**. If the address shown does not include a domain part (that is, the number at the start of the line contains only one colon character), then the computer has only one PCI domain and it is **0000**.

The following commands, with the capital letters substituted with the device’s PCI address, can be used to restart a PCI device on a running system.[[2]][4]

```

    # echo "1" > /sys/bus/pci/devices/DDDD\:BB\:DD.F/remove
    # sleep 1
    # echo "1" > /sys/bus/pci/rescan

```

In the above example, the placeholders DDDD, BB, DD, and F are for the PCI device domain, bus, device, and function respectively.

Substituting the values from the example output of the _lspci_ command shown above gives the command that would need to be run to restart the Atheros wireless card on this example system.

```

    $ sudo /bin/sh -c "echo '1' > /sys/bus/pci/devices/0000\:3d\:00.0/remove"
    $ sleep 1
    $ sudo /bin/sh -c "echo '1' > /sys/bus/pci/rescan"

```

If required, the above commands could be automated by putting them in a script.

```

    $ nano restart-wireless-card.sh
    #!/bin/bash
    echo "1" > /sys/bus/pci/devices/0000\:3d\:00.0/remove
    sleep 1
    echo "1" > /sys/bus/pci/rescan

```

Enable executable permissions with, for example, _chmod +x restart-wireless-card.sh_ and run _sudo ./restart-wireless-card.sh_ whenever you need to restart your PCI device.

### Final notes

Not all PCI devices can be restarted using this method. But the real-life example demonstrated above does work to get the WiFi card running again without requiring a full reboot of the PC.

### References

  1. [stackexchange.com: Does PCIe hotplug actually work in practice?][5]
  2. [stackexchange.com: How to Reset/Cycle Power to a PCIe Device?][6]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/use-sysfs-to-restart-failed-pci-devices/

作者：[Mateus Rodrigues Costa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mateusrodcosta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/pci-devices-816x345.jpg
[2]: https://unsplash.com/@mebrooks01?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/pcie?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: tmp.DB93Qy0XGW#references
[5]: https://electronics.stackexchange.com/a/208796
[6]: https://unix.stackexchange.com/questions/73908/how-to-reset-cycle-power-to-a-pcie-device/245184#245184
