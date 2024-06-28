[#]: subject: "This SBC Puts Raspberry Pi 5 to Shame"
[#]: via: "https://itsfoss.com/arosom-sige7-review/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This SBC Puts Raspberry Pi 5 to Shame
======

[![Warp Terminal][1]][2]

Raspberry Pi started the single board computer (SBC) revolution. It started as a tiny, low-end spec device for hobbyists but that was in the past.

The success of Raspberry Pi birthed many similar devices. While the form factor remains tiny, the devices are getting powerful in terms of specification.

[Armsom Sige7][3] is one such tiny computer that has got some heavy hardware muscles on it.

An octa-core processor, Mali-G610 GPU, 6 TOPS NPU, and 8K display support are specifications that Raspberry Pi can only wish for.

![ArmSoM Sige7 is a tiny device. Tux for reference ;\)][4]

Before I share my experience and impression of the AroSoM Sige7, let's take a look at the hardware offering in more detail.

📋

[ArmSoM][5] sent me the device for review. The views expressed are entirely my own.

### ArmSoM Sige7 specification

[ArmSoM Sige7 is available][6] in two models:

  * Basic: 8 GB RAM, 64 GB eMMC
  * Pro Max: 32 GB RAM, 128 GB eMMC



Apart from that, both models have the same specifications as detailed below.

  * **SOC** : RockChip RK3588
  * **CPU** : RK3588 Quad-Core Cortex-A76@ 2.4GHz+Quad-CoreCortex-A55@ 1.8GHz，8nm process
  * **GPU** : GPU Mali-G610 MP4 (4x256KB L2 Cache) Supports OpenGL ES3.2/OpenCL2.2/Vulkan1.1
  * **NPU** : 6 TOPS@INT8(3 NPU core), Supports frameworks like TensorFlow, MXNet, PyTorch, Caffe, Tflite, Onnx NN, Android NN, etc
  * **VPU** : **Decode** : 8K@60fps H.265/VP9/AVS2, 8K@30fps H.264 AVC/MVC, 4K@60fps AV1, 1080P@60fps MPEG-2/-1/VC-1/VP8 **Encode** : Encode:8K@30fps H.265 / H.264
  * **ISP** : Integrated 48MP ISP with HDR&3DNR
  * **RAM** : 8GB/32GB, 64bit LPDDR4/LPDDR4x
  * **Disk storage** : 64GB/128GB **eMMC** , **microSD** expansion, M.2 PCIe **SSD**
  * **Networking** : 2x 2.5G Ethernet, IEEE 802.11a/b/g/n/ac/ax **WIFI6** , **Bluetooth 5**
  * **Ports** : 1 HDMI 2.1 (supports 8K @60FPS), 1x MIPI DSI (up to 4K@60fps), 2x 2-lane MIPI CSI, Type C DP 1.4, Type C power delivery, 1x USB 3.1, 1x USB 2.0
  * **40-pin** : **Fully compatible with Raspberry Pi 40-pin header** (thus plenty of Pi add-on modules already available in the market will also work with Sige7)
  * **Buttons** : Power on button, reboot button and Maskrom button for maskrom burn-in mode



![ArmSoM hardware at a glance][7]

Impressive specification, right? That's a lot of things on the tiny device. No wonder it feels crowded even on the bottom side of the board.

![Don't ignore the bottom][8]

📋

The specifications are way too similar to the Banana Pi BPI M7, right? That's because it's a co-branded device and is available under both Banana Pi and ArmSoM brands. Lion Wang, CEO of Banana Pi is one of the angel investors in ArmSoM. Note that [ArmSoM is a completely independently operated brand][9] in the future and they design and manufacture the products by themselves.

![ArmSoM and Banana Pi collaborated to give you Sige7 \(or Banana Pi BPI M7\)][10]

### What could it be used for?

A lot of things actually. It is a powerful device in a small form factor. You can run embedded system projects like you do with Raspberry Pi 5. The **40-pin allows the use of Raspberry Pi add-on modules for your projects**.

The NPU and GPU make it a good choice for AI projects.

Dual Ethernet ports allow it to work like a router or firewall.

Thanks to its powerful video encoder and decoder, you can use Sige7 for digital signage and media servers. You may also use it for gaming, although I wouldn't prefer it for this purpose.

You can put it at the center of your homelab. It has strong processor, good RAM size and plenty of ways to get more disk storage.

Of course, it can be used in edge computing for real-time, low-latency data processing.

### My experience with ArmSoM Sige7

![][11]

ArmSoM has 4 official operating system offerings: Debian, Android, Ubuntu and Armbian.

I went with [Armbian][12]. It's an excellent project that runs on several ARM boards. Armbian offers Ubuntu and Debian variants, and for some reason, I used the Ubuntu version.

Armbian has Platinum support for the Banana Pi M7 (ArmSoM Sige7) but instead of getting it from the Armbian website, I used the [custom version provided by ArmSoM][13].

It was when I booted for the first time into Armbian and encountered my first major issue.

#### WiFi needs antenna (lesson learned the hard way)

I noticed that the WiFi signal was too weak. Although it could (barely) see the signal, the strength was so poor that it could not connect to the router, which was 15 feet away.

Sometimes I take unnecessary challenges. This one was one of them. I thought it was a software issue. Perhaps Armbian had some known issues with the wireless networking.

I went on a forum-hopping spree and tried to use one suggestion after another. But nothing materialized. I hung my head in shame and contacted the ArmSoM support on their Discord channel.

It was then that I learned that the device needed an external IPEX antenna. This was news to me. I was under the impression that a device that flaunts WiFi6 on its website should have a better wireless experience out of the box.

I have used a few single-board computers in the past and have never had to use external antennas, so this came as a surprise to me.

I am using wired networking right now; there are no connection issues with that. Perhaps I'll order the external antenna to get the flexibility of

**I believe that this fact should be well highlighted on the website: you need an external antenna for the WiFi to work.**

#### AI and NPU

I already have a [home lab setup with the awesome ZimaBoard][14]. So, I did not even try using ArmSoM for a media server.

I was more interested in its AI capabilities. However, I don't have enough AI development capability to test them.

**The onboard NPU supports PyTorch, TensorFlow, etc., and** I can see people making good use of their Banana Pi M7 (i.e. Sige7) board for AI projects. **** Unfortunately, I don't have any experience with them. I plan to, but at the moment, I am not into AI development.

But I do use generative AI as the end user. I am [trying LLMs locally with Ollama][15] and other such projects.

At present, most LLMs do not run on NPU and thus testing this part became a challenge. Spoiler alert, I won this challenge thanks to the [Ubuntu Rockchip][16] and [ezrknpu][17] projects.

Ubuntu Rockchip is a modified Ubuntu version for Rockchip RK3588 devices. ezrknpu converts some LLMs for the [Rockchip][18] devices.

After some experiments and trial and error, I did manage to run a couple of LLMs. As you can see in the image below, all 3 cores of NPU were utilized:

![Click to expand][19]

I'll share detailed experience of using Rockchip NPU in a separate article perhaps.

#### Decent support and documentation which should surely be improved

The biggest problem with a new gadget is the support. Thankfully, ArmSoM is not too lagging in this department but it has plenty of room for improvement.

**Their** [**patch was recently integrated into the mainline Linux kernel**][20] **, which shows the ArmSoM project's commitment to its users**. As the newer Linux kernel version starts supporting Sige7, you should be able to install more Linux distributions instead of relying on the customized distros provided by ArmSoM.

They also have plenty of source code available on its [GitHub repo][21].

ArmSoM has [official Discord channel][22] and [Discourse forum][23] where you can seek support.

Armbian also has Platinum level support for this device so Armbian forum is also a good place to seek help if you encounter any issues.

Other than that, RK3588 is a popular processor and you can find [plenty of chit-chat on Reddit][24]. If nothing else, you can search Banana Pi M7 on the web as Banana Pi is the more popular brand.

That's how I navigated when I faced the WiFi issue and when I wanted to test the NPU.

Sure, it is nowhere close to Raspberry Pi that has much wider community around it but you won't be lurking all alone on the internet for ArmSoM either.

ArmSoM also has [official documentation portal][25] but it's minimal at this stage. We need more on things like booting from eMMC or SSD and other seemingly basic stuff. [Banana Pi's own documentation portal][26] is also pretty basic in my opinion.

Nothing beats Raspberry Pi when it comes to documentation and the tools they have created to provide an out-of-the-box experience. That's something everyone should learn from them.

### Overall experience

I have a [Raspberry Pi 5 which I am using as my secondary desktop system][27]. ArmSoM Sige7 clearly outperforms Pi 5, thanks to its massive hardware configuration. It is much more smoother to play 4K videos, use the system with tons of tabs and application open.

Like any other SBC out there, the SoC and other components start heating as soon as you start using CPU-intensive tasks.

ArmSoM does have a [dedicated case for the Sige7 device][28] with internal bulge for heat dissipation. It may not look as cool as the [Pironman case][29] but it should do the job. I don't have this case and I am ordering some universal heat sinks to keep the temperature under control.

![][30]

I like that Sige7 provides a Raspberry Pi-compatible 40-pin header. You can use the wide variety of Raspberry Pi add-ons available in the market.

**ArmSoM Sige7 costs $165 for the Basic 8 GB version and $260 for the 32 GB Pro Max**. I would prefer going for the Pro Max to future-proof your SBC (to some extent). Of course, it should suit your budget.

[Explore ArmSoM Sige7][6]

✅ Best in terms of hardware specification
✅ Wide variety of usage from AI projects to homelab setup
✅ Plenty of ports for storage and peripheral devices
✅ Compatibility with Raspberry Pi add-ons
✅ Device included in latest Linux kernel version
✅ Reasonably priced for its offering
❎ Need to improve documentation

### Conclusion

It is interesting to see how far the single board computers have come. 32 GB of RAM on the tiny board? Who would have thought of that a few years ago.

In my opinion, [Sige7][3] is the best SBC hardware-wise that money can buy at the moment. It costs $260 but it provides a well-packed device that can be used in a variety of situations, from desktop to AI development, from server hosting to edge computing.

However, you should have a positive attitude towards troubleshooting and doing things on your own.

The idea of making it compatible with Raspberry Pi is also an excellent move. In fact, their upcoming AI development-focused [AIM 7][31] board will be compatible with NVIDIA Jetson devices. That's something interesting to lookout for as well.

I also like the fact that in order to rapidly establish a mature distribution channel, Armsom has authorized Banana Pi to co-sell some of its products, while retaining all intellectual property rights with ArmSoM. This way, they utilize the existing Banana Pi community while building their own in the process.

Focus a little bit more on building community around their products and providing better, comprehensive documentation, and ArmSoM Sige7 will definitely make its mark.

--------------------------------------------------------------------------------

via: https://itsfoss.com/arosom-sige7-review/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.armsom.org/sige7
[4]: https://itsfoss.com/content/images/2024/06/armsom-sige7.webp
[5]: https://www.armsom.org/
[6]: https://www.armsom.org/product-page/sige7
[7]: https://itsfoss.com/content/images/2024/06/armsom-sige7-specs-1.webp
[8]: https://itsfoss.com/content/images/2024/06/armsom-sige7-specs-2.webp
[9]: https://www.armsom.org/about-us
[10]: https://itsfoss.com/content/images/2024/06/armsom-banana-pi-m7.webp
[11]: https://itsfoss.com/content/images/2024/06/armsom-sige7-device.webp
[12]: https://www.armbian.com/
[13]: https://www.armsom.org/download
[14]: https://itsfoss.com/zimaboard-review/
[15]: https://itsfoss.com/ollama-setup-linux/
[16]: https://github.com/Joshua-Riek/ubuntu-rockchip
[17]: https://github.com/Pelochus/ezrknpu
[18]: https://www.rock-chips.com/
[19]: https://itsfoss.com/content/images/2024/06/rockchip-llm-running-on-npu.jpg
[20]: https://lore.kernel.org/all/20240420034300.176920-4-liujianfeng1994@gmail.com/
[21]: https://github.com/armsom
[22]: https://discord.com/invite/THfTEatpfK
[23]: https://forum.armsom.org/
[24]: https://www.reddit.com/r/RockchipNPU/
[25]: https://docs.armsom.org/
[26]: https://docs.banana-pi.org/en/BPI-M7/BananaPi_BPI-M7
[27]: https://itsfoss.com/raspberry-pi-5-review/
[28]: https://www.armsom.org/product-page/sige7-metal-shell
[29]: https://itsfoss.com/pironman-5-review/
[30]: https://itsfoss.com/content/images/2024/06/armsom-sige7-case-1.png
[31]: https://www.armsom.org/aim7
