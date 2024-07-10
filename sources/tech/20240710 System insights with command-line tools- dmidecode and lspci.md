[#]: subject: "System insights with command-line tools: dmidecode and lspci"
[#]: via: "https://fedoramagazine.org/system-insights-command-line-dmidecode-lspci/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

System insights with command-line tools: dmidecode and lspci
======

![][1]

Photo by [Hunter Harritt][2] on [Unsplash][3] cropped

In our ongoing series on Fedora Linux system insights, we are looking into essential command-line utilities that provide information about the system’s hardware and status. Following our previous discussion on _lscpu_ and _lsusb_ , we now turn our attention to _dmidecode_ and _lspci_.

## **_dmidecode_ – Decoding your system’s DMI table**

_dmidecode_ is a command-line utility for retrieving detailed information about the system’s hardware. It reads the [DMI (Desktop Management Interface)][4] table, which contains data provided by the system’s firmware. This data includes details about the system’s BIOS, processor, memory, and other hardware components. Using _dmidecode_ , you can gain insights into the hardware configuration without the need to be on-site or opening the system case.

### **Basic usage**

To start with, let’s execute the basic _dmidecode_ command to get an overview of the system’s DMI table:

```

    $ sudo dmidecode

```

This command outputs a comprehensive list of DMI table entries, which can be overwhelming.

To narrow down the output to specific information, you can use various options, especially via defining a type with _-t number_ :

```

    $ sudo dmidecode -t number

```

where _number_ is an integer. The following is from _man dmidecode_ :

```

    [... output omitted for readability ...]
    The SMBIOS specification defines the following DMI types:
    Type   Information
    ────────────────────────────────────────────
      0   BIOS
      1   System
      2   Baseboard
      3   Chassis
      4   Processor
      5   Memory Controller
      6   Memory Module
      7   Cache
      8   Port Connector
      9   System Slots
      10   On Board Devices
      11   OEM Strings
      12   System Configuration Options
      13   BIOS Language
      14   Group Associations
      15   System Event Log
      16   Physical Memory Array
      17   Memory Device
      18   32-bit Memory Error
      19   Memory Array Mapped Address
      20   Memory Device Mapped Address
      21   Built-in Pointing Device
      22   Portable Battery
      23   System Reset
      24   Hardware Security
      25   System Power Controls
      26   Voltage Probe
      27   Cooling Device
      28   Temperature Probe
      29   Electrical Current Probe
      30   Out-of-band Remote Access
      31   Boot Integrity Services
      32   System Boot
      33   64-bit Memory Error
      34   Management Device
      35   Management Device Component
      36   Management Device Threshold Data
      37   Memory Channel
      38   IPMI Device
      39   Power Supply
      40   Additional Information
      41   Onboard Devices Extended Information
      42   Management Controller Host Interface

    Additionally, type 126 is used for disabled entries and type 127 is an end-of-table marker. Types 128 to 255 are for OEM-specific data. dmidecode will display these entries by default, but it can only decode them when the vendors have contributed documentation or code for them.
    [... further output omitted for readability ...]

```

### **Example 1: Retrieving BIOS information**

To fetch details about the BIOS, use the _-t_ option followed by the type number for BIOS information (type _0_ ):

```

    $ sudo dmidecode -t 0

```

This command outputs information such as the BIOS version, release date, and vendor. Example output (here using a ThinkPad T480S):

```

    $ sudo dmidecode -t 0
    # dmidecode 3.6
    Getting SMBIOS data from sysfs.
    SMBIOS 3.0.0 present.

    Handle 0x000B, DMI type 0, 24 bytes
    BIOS Information
            Vendor: LENOVO
        Version: N22ET80W (1.57 )
     Release Date: 02/27/2024
      Address: 0xE0000
      Runtime Size: 128 kB
          ROM Size: 16 MB
       Characteristics:
              PCI is supported
              PNP is supported
              BIOS is upgradeable
                   BIOS shadowing is allowed
             Boot from CD is supported
             Selectable boot is supported
                  EDD is supported
              3.5"/720 kB floppy services are supported (int 13h)
                   Print screen service is supported (int 5h)
                    8042 keyboard services are supported (int 9h)
                 Serial services are supported (int 14h)
               Printer services are supported (int 17h)
              CGA/mono video services are supported (int 10h)
               ACPI is supported
             USB legacy is supported
               BIOS boot specification is supported
                  Targeted content distribution is supported
                    UEFI is supported
     BIOS Revision: 1.57
           Firmware Revision: 1.23

```

### E **xample 2: Extracting baseboard (mainboard) and memory information**

For specific details about memory, you can query the baseboard type _2_ and memory device type _17_. This will provide details about the system’s memory modules, including size, speed, and manufacturer. This information is particularly useful when upgrading or troubleshooting system memory or if you need to buy additional, compatible RAM for a server you did not provide by yourself.

A real world example of a small labserver with four memory sticks:

```

    $ sudo dmidecode -t 2,17
    [... output omitted for readability ...]
     Manufacturer: Supermicro
      Product Name: X11SPL-F
        Version: 1.02

    [... output omitted for readability ...]
    Handle 0x0029, DMI type 17, 84 bytes
    Memory Device
        Array Handle: 0x0025
          Error Information Handle: Not Provided
        Total Width: 72 bits
          Data Width: 64 bits
           Size: 64 GB
           Form Factor: DIMM
     Set: None
     Locator: DIMMB1
       Bank Locator: P0_Node0_Channel1_Dimm0
         Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
        Speed: 2933 MT/s
      Manufacturer: Samsung
         Serial Number: 167D51E1
       Asset Tag: DIMMB1_AssetTag (date:22/38)
       Part Number: M393A8G40MB2-CVF
         Rank: 2
       Configured Memory Speed: 2400 MT/s
            Minimum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Configured Voltage: 1.2 V
     Memory Technology: DRAM
       Memory Operating Mode Capability: Volatile memory
     Firmware Version: 0000
        Module Manufacturer ID: Bank 1, Hex 0xCE
      Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
          Memory Subsystem Controller Product ID: Unknown
       Non-Volatile Size: None
       Volatile Size: 64 GB
          Cache Size: None
      Logical Size: None


    $ sudo dmidecode -t 17 | grep -E "(Manufacturer|Part Number):"
            Manufacturer: Samsung
         Part Number: M393A8G40MB2-CVF
         Manufacturer: Samsung
         Part Number: M393A8G40MB2-CVF
         Manufacturer: Samsung
         Part Number: M393A8G40MB2-CVF
         Manufacturer: Samsung
         Part Number: M393A8G40MB2-CVF

```

By using this simple command, it is easy to determine what hardware is in use. This information is particularly useful when there is a need for upgrading or replacing hardware.

## **_lspci_ : Listing PCI devices**

The _lspci_ command is used to list all PCI devices in the system. [PCI (Peripheral Component Interconnect)][5] devices include network cards, graphics cards, USB controllers, and more. This command provides a snapshot of the devices connected to the system’s PCI bus, offering a detailed view of their configuration and status.

_lspci_ does not need extended privileges, a common user is enough to determine useful information.

### Basic usage

A simple execution of the _lspci_ command lists all PCI devices:

```

    $ lspci

```

For more detailed information about a specific device, you can use the _-v_ (verbose) option:

```

    $ lspci -v

```

### **Example 1: Finding Graphics Card Information**

To find detailed information about the system’s graphics card, you can filter the _lspci_ output using _grep_. Example output (here using a ThinkPad T480S):

```

    $ lspci | grep -i vga
    00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)

```

### **Example 2: Check which Kernel driver is used by your hardware**

To see which kernel driver is being used by a specific device, you can use the _-k_ option. This lists the kernel driver in use for each PCI device, which can be useful for troubleshooting driver-related issues, especially by being able to do a web search for problems using the driver’s name and your hardware model.

Example output (here using a ThinkPad T480S):

```

    $ lspci -k

    [... output omitted for readability ...]
    00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
         Subsystem: Lenovo Device 2258
         Kernel driver in use: i915
            Kernel modules: i915

    [... output omitted for readability ...]
    00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
          Subsystem: Lenovo Device 2258
         Kernel driver in use: e1000e
          Kernel modules: e1000e

```

As you can see, the graphics card is using the [drm/i915 Intel GFX Driver][6] driver and the network card is utilizing [e1000e][7].

## **Conclusion**

The _dmidecode_ and _lspci_ commands are powerful tools for extracting detailed hardware information from a Linux system. Even though they are simple, both commands offer insights into the system’s configuration and status. Whether you’re troubleshooting, optimizing, or simply curious, these tools provide valuable data that can help you better understand and manage your Linux environment. See you next time when we will have a look at more useful listing and information command line tools and how to use them.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/system-insights-command-line-dmidecode-lspci/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/07/insights_via_cli_dmidecode_lspci-816x345.jpg
[2]: https://unsplash.com/@hharritt?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/red-and-blue-lights-from-tower-steel-wool-photography-Ype9sdOPdYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://en.wikipedia.org/wiki/Desktop_Management_Interface
[5]: https://en.wikipedia.org/wiki/Peripheral_Component_Interconnect
[6]: https://www.kernel.org/doc/html/latest/gpu/i915.html
[7]: https://www.kernel.org/doc/Documentation/networking/e1000e.txt
