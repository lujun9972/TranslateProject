[#]: subject: "TerraMaster D1 SSD Plus Review: Experience a Faster External SSD"
[#]: via: "https://itsfoss.com/terramaster-d1-ssd-plus-review/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

TerraMaster D1 SSD Plus Review: Experience a Faster External SSD
======

[![Warp Terminal][1]][2]

Transferring large files via typical USB thumb drives is a pain. Try it with a 20 GB file and it will take an hour just for copying the files.

That's why external, portable SSDs are the new normal these days, especially when we have to deal with 4K video files that go in multiple GBs.

Another player in this domain is an external SSD enclosure that allows you to use your typical, internal NVMe SSD like a portable, external SSD.

One of the latest such devices is [TerraMaster's D1 SSD Plus][3]. If you did not know already, [TerraMaster][4] manufactures NAS, DAS and other storage equipment. D1 SSD Plus is their latest offering.

📋

TerraMaster sent me this device for review. The views expressed are my own and come from experience with time spent on it.

### TerraMaster D1 SSD Plus Enclosure

The TerraMaster D1 SSD Plus is a high-speed, portable M.2 NVMe SSD enclosure that supports up to 8 TB drives and connects via USB4 (40 Gbps), delivering near-desktop performance with read/write speeds close to 4 GB/s (or so it claims).

Weighing at 250 grams, TerraMaster D1 SSD Plus is a heavy device for a portable SSD. But that's by choice and by design. The enclosure is made of aerospace-grade aluminum, and it is certainly a lot bulkier than your usual external SSD. Although it keeps the SSD safe and also adds the passive cooling features thanks to the dual-sided fins.

![][5]

It looks like the white colored aluminum casing is getting popular. [ZimaBoard 2][6] and some other gadgets in the homelab niche also use this styling these days. I prefer dark, black looks, but let the color not be a judge of this device.

🚧

TerraMaster D1 SSD Plus is just an enclosure. It does NOT include NVMe SSD.

#### Set up

![][7]

Please note that the enclosure does NOT come with an NVMe SSD. You have to use your own NVMe SSD and it cannot be SATA SSD.

The box contains the enclosure, a high-speed cable, a screwdriver, manual, and a pouch for the device.

There is a tiny screw at the bottom of the device. You have to use the provided screwdriver to unscrew it and open the enclosure. The screw doesn't come out entirely but stays fixed on it. This is good thinking, as you don't want to lose the tiny screw. At the same time, you wouldn't want to use an unsuitable device on the screw because if the screw loses its shape, you may have a hard time with it.

![][8]

Once the enclosure is opened, you'll see the option to add the NVMe SSD on one part. The other part has a thermal pad with a sticker on it that should be removed before the first use.

The entire setup doesn't take long and is certainly not complicated.

#### Data safety and SSD supports

D1 SSD Plus is compatible with double sided SSDs too. This is another plus.

Another plus point is the data safety. TerraMaster claims that D1 SSD Plus incorporates additional protective components to ensure stable data transmission, safeguarding against short circuits, voltage surges, and electrostatic discharge (ESD).

As [noted by Gizmochina][9], the large amount of SMD capacitors used here are the same as you see with enterprise SSDs to stabilize the voltage, provide power failure protection, and thus ensure data safety.

#### Technical specifications

Specification | Details
---|---
Interface | USB4 (40 Gbps), TB5/4/3, USB 3.x/2.0
Max Speeds | Read up to ~3,853 MB/s, Write up to ~3,707 MB/s
SSD Slot | M.2 NVMe 2280
Max Capacity | 8 TB
Enclosure | Aluminum, fanless, heat-dissipating
Dimensions (mm) | 112.5 × 60 × 33
Weight | 246 g (without SSD)
Power Consumption | ~7.5 W active, ~5.5 W hibernation
File Systems Supported | NTFS, APFS, HFS+, exFAT, FAT32, EXT4
Extras | Backup apps (TDAS & TPC), screwdriver, pouch
Price (enclosure) | Approximately $110

[Get TerraMaster D1 SSD Plus on Amazon][10]

### Speed matters

Since one of the main points of having a TerraMaster external SSD enclosure is to use it as a better alternative of regular external SSDs, I tested it against my SanDisk Extreme Portable Disk (model SDSSDE60-1T00).

This SanDisk SSD has been with me for the past few years. In fact, I have three of them. One of them stores important data and is not used much and the other two are more portable in nature. I have almost stopped using USB drives even for data transfer after these SSDs.

Let me share how the TerraMaster SSD enclosure compares with my SanDisk Extreme portable disk.

![][11]

To summarize, this is my test kit:

  * [ASUS Zenbook S14][12] with Thunderbolt 4 port
  * [SanDisk Extreme Portable Disk SDSSDE60-1T00][13] (USB 3.2 interface with advertised speed of 1050 MB/s).
  * [TerraMaster D1 SSD Plus][10] with WD Blue SN5000 (PCIe 4.0 interface with advertised speed of 2853 MB/s)



📋

My tests are more from a casual, end-user's perspective. I am sure these tests can be performed at a more expert level with dedicated speed testing software but I wanted to test it the way I use them in my day-to-day activities.

In the test screenshots, **Data-SSD is TerraMaster and Backup-SSD is SanDisk**.

The first test I did was with a folder containing photos of around 5.5 GB in size. Surprisingly, SanDisk nearly took the same time (6.6 sec) as TerraMaster (5.32 sec).

![][14]

I was not expecting this, to be honest. Then I [created a file of 10 GB in size with fallocate][15] and used it to test the two external disks. This time TerraMaster was around two times faster than SanDisk.

![][16]

Next, I copied a folder with some huge video files. The folder was around 96 GB in size. And as expected, TerraMaster finished copying under one third of the time than SanDisk.

TerraMaster took 1 minute, 28 seconds for 96 GB of file transfer. Which should be roughly around 1.1 GB/s.

![TerraMaster D1 SSD Plus][17]

SanDisk took 4 minutes and 10 seconds, which should amount to a speed of 380 MB/s.

![SanDisk][18]

Basically, the larger the file size, the better it performs.

Of course, the SanDisk uses USB 3.2 interface and is a few years older, but most of the external SSDs use the same interface and have a similar performance range. In my opinion, it is only fair to keep the comparison with these external disks as the external SSD enclosure is supposed to replace them in your setup.

### Backup your PC and smartphone data easily

![TerraMaster has dedicated software to backup Windows PC][19]

TerraMaster also provides [dedicated software to backup your Windows PC easily][20] to your external SSD. I don't use Windows and there is no such application for Linux so I didn't test it.

There are also [dedicated mobile apps for iOS and Android][21]. I was actually excited about the idea of automatically backing up smartphone data to the SSD.

I have a Galaxy S23 Ultra with 1 TB storage and 2 children. Which means that I have tons of photos and videos of my children. I keep an automatic backup on pCloud as I have their 2 TB lifetime storage. Having data locally is a plus as I prefer keeping multiple copies of the data.

Unfortunately, at present, my Galaxy S23 is suffering from 'foreign particle and moisture' in the charging port and thus I could not test it on my phone. I'll update this section when this problem goes away and the USB port is functional again.

I used my wife's iPhone,but the WD Blue SN5000 probably required more power because I saw a 'Cannot use accessory. This accessory uses too much power' error.

I am sure these apps have been created to add more versatility to the overall offering of TerraMaster devices. I wish I could test them but it didn't happen.

### Advantages of an external SSD enclosure

I learned a thing or two about using an external SSD enclosure.

  * Speed: By using the Thunderbolt port, these SSD enclosures are equal or faster than your regular external SSDs.
  * Reusability: If you have internal NVMe SSDs that are not being used, you can put them in the enclosure and use them as external SSDs. You are not fixed to a single brand of SSD as well.
  * Cost-effective in long run: You have the option to 'upgrade' your external SSD by changing the NVMe SSD.
  * Robust: In some unfortunate case if the USB connector breaks on the external SSD, your data is pretty much lost. In case of SSD enclosure, your SSD can be taken out anytime and put into another device.



### A device worth having

I was skeptical at first, unsure of the usability of such a device. But when I looked closely and tested it, I could see its potential and why external SSD enclosures are gaining popularity specially among homelab users who have multiple NVMe SSDs in their setup. It gives the option to reuse your internal SSDs into a portable, external SSD.

TerraMaster D1 SSD Plus is a robust device. It is bulky, but it ensures safe SSD operation. The all almunium chassis gives it a rugged look and at the same time, it provides passive cooling.

With 4K being the new normal, it's not uncommon to have video files in 100s of GBs. USB 3 is certainly not adequate for data transfer of such large files. External SSDs are the way to go. Even there, the speed matters, and as you saw, TerraMaster D1 SSD Plus was easily more than 3 times faster than portable SSD.

The ability to transfer photos and videos directly from your smartphones into the SSD is another plus for TerraMaster D1 SSD Plus, given that you use the correct SSD.

My biggest gripe is perhaps its bulky outfit. Now, I understand that it is important to secure the SSD against jerks and falls for a longer and smoother operation and hence it makes sense to have a military grade enclosure. Plus, it handles the heat pretty well so I should not complain about the size.

[Get it from official website][22]

[Order it from Amazon][10]

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][23].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][24] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][24]

--------------------------------------------------------------------------------

via: https://itsfoss.com/terramaster-d1-ssd-plus-review/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.terra-master.com/global/d1-ssd-plus.html
[4]: https://www.terra-master.com/global/
[5]: https://itsfoss.com/content/images/2025/08/terramaster-d1-ssd-plus.webp
[6]: https://news.itsfoss.com/zimaboard-2-review/
[7]: https://itsfoss.com/content/images/2025/08/terramaster-d1-ssd-plus-box.webp
[8]: https://itsfoss.com/content/images/2025/08/terramaster-d1-ssd-plus-ssd-fitting.webp
[9]: https://youtu.be/ZlvV36D6oCE?si=LCXRp8MR330gvSCX&t=146
[10]: https://amzn.to/4mpL6kP
[11]: https://itsfoss.com/content/images/2025/08/terramaster-sandisk-test.webp
[12]: https://amzn.to/4fJubqF
[13]: https://amzn.to/3HHVg0P
[14]: https://itsfoss.com/content/images/2025/08/terramaster-speed-test-several-image-files-1-1.png
[15]: https://linuxhandbook.com/fallocate-command/
[16]: https://itsfoss.com/content/images/2025/08/terramaster-speed-test-single-big-file-1.png
[17]: https://itsfoss.com/content/images/2025/08/terramaster-speed-with-huge-data-transfer.png
[18]: https://itsfoss.com/content/images/2025/08/sandisk-speed-with-huge-data-transfer.png
[19]: https://itsfoss.com/content/images/2025/08/terramaster-tpc.webp
[20]: https://www.terra-master.com/global/terramaster-tpc
[21]: https://www.terra-master.com/global/terramaster-tdas-application
[22]: https://www.terra-master.com/global/products/homesoho-das/d1-ssd-plus.html
[23]: https://itsfoss.com/plus-member-resources/
[24]: https://itsfoss.com/lifetime-membership/
