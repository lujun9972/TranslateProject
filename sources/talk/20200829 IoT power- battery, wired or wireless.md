[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (IoT power: battery, wired or wireless?)
[#]: via: (https://www.networkworld.com/article/3573389/iot-power-battery-wired-or-wireless.html)
[#]: author: (Jon Gold https://www.networkworld.com/author/Jon-Gold/)

IoT power: battery, wired or wireless?
======
Powering small IoT devices spread over a wide area is an important issue, and efficiency is the name of the game.
Jackie Niam / Getty Images

The term “[Internet of Things][1]” can be used to describe a huge range of different technologies, from sensors to gateways to back-end systems that organize data and keep machine-to-machine networks secure. Lots of attention is rightly paid to the way IoT systems gather data and how it moves from place to place. However, for some parts of the IoT, the issue of how to keep sensors powered may be just as important.

Particularly in the case of IoT systems that feature small sensors and sensors that might be far away from each other or from the rest of the system, energy usage is a critical concern, because traditional wired power may simply not be an option.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][2]

Agriculture, utilities, and transportation are among verticals where widely spaced, low-power deployment is important. Scientists studying a volcano might not be able to run a power cable all the way from the closest part of the grid to their vibration sensors. Soil moisture testers in a farmer’s field could face the same problem, and so on.

There are, however, other options, and choosing the best solution has everything to do with understanding what the desired business outcome and how to attain it with peak efficiency, according to Gartner vice president and analyst Al Velosa.

 “The fundamental question is ‘hat’s it cost to deploy the infrastructure?’” he said. “If you’re managing a couple thousand miles’ worth of assets…the bigger cost is sending a truck to that asset than anything else.”

That’s particularly important for the first and probably the most common option for powering small, remote IoT assets – battery cells. No battery lasts forever, so, eventually, they have to be swapped out. The current state of the art focuses on silver oxide cells akin to watch batteries and those used in hearing aids, according to Forrester vice president and principal analyst Frank Gillett,

“One of the problems you run into is that some battery chemistry won’t make it 10 years,” he said.

Silver oxide cells remain popular because their charge-to-weight ratio is comparatively very high. Even a small battery of this type can power a simple sensor outfitted with a low-power, infrequently used radio for years, potentially. They are not, however, so powerful as to free device makers from the responsibility of designing for maximum efficiency.

At its most basic level, an IoT sensor needs to be able to collect information, express that information in a digital format, and transmit it up the chain, whether that’s to a nearby edge device for collation and processing or directly to the back end. Each part of that process has an energy cost, and while advancing technology has dramatically increased power efficiency in both processing and transmission, energy is still one of the primary limiting factors in IoT device design.

“It’s figuring out how to maximize what a low-power device can do, and a lot of that is making the radios more efficient,” said Gillett. “The flipside is making the compute part of the IoT endpoint very power-efficient as well. Ideally you have them both fairly integrated.”

Battery technology, he added, advances comparatively slowly, compared to processors, chips and sensors. That’s part of why some companies are looking elsewhere to power their IoT devices.

One option is solar power. Increasingly efficient solar cells mean that it’s easy enough to add appropriately sized panels to small devices, and the cost of those panels has dropped of late, also.

That’s great in theory, according to Velosa, but in practice, many deployments using solar energy aren’t going to be that much more efficient than those using battery power. Solar is still dependent on the panels getting enough exposure to the sun, and what’s more, they’re far from maintenance-free. Dust and dirt can degrade their ability to generate power.

“We are still looking at normal deployment of an asset being 1-5 years, with some service call in the middle of that,” he said.

Another idea is fully wireless power transmission – think a Qi charging pad, but over much larger distances – but widespread usage of this technique is still years away. Startups like GuRu, Wi-Charge and others have made notable advances in wireless power, but analysts think that it’s not particularly well-suited to widely spaced IoT deployments. Most of the technologies on the current market are either too experimental, too expensive or too short-ranged to offer a real alternative to solar, batteries or wires.

“It’s such a corner case,” said Gillett. “It has to be something where you just can’t run the wire, but you still have to translate power over a short distance. And it has to be costly.”

Instead, enterprises looking to deploy IoT would be best-served by understanding the costs involved in any power option, and looking to maximize efficiency. Maintenance costs will be present in any case, but the amount involved will vary widely.

“At the end of the day, it has to be a complete analysis,” said Velosa. “What’s going to allow me to still deliver the business outcome on this?”

Join the Network World communities on [Facebook][3] and [LinkedIn][4] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3573389/iot-power-battery-wired-or-wireless.html

作者：[Jon Gold][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Jon-Gold/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3207535/what-is-iot-the-internet-of-things-explained.html
[2]: https://www.networkworld.com/newsletters/signup.html
[3]: https://www.facebook.com/NetworkWorld/
[4]: https://www.linkedin.com/company/network-world
