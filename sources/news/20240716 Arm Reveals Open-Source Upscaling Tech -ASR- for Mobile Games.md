[#]: subject: "Arm Reveals Open-Source Upscaling Tech 'ASR' for Mobile Games"
[#]: via: "https://news.itsfoss.com/arm-open-source-asr-upscaling/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Arm Reveals Open-Source Upscaling Tech 'ASR' for Mobile Games
======
The upscaling tech, for smartphones, and open-source. Sounds exciting!
[![][1]][2]

If you are a gamer, you have most likely come across the term “upscaling” in recent years. It is **a feature that allows many people to play games smoothly, even if their GPU is weak** , or has gotten old over the years.

There are two key types of upscalers in the market right now, one is spatial, which works on a frame-by-frame basis. The other is temporal, which uses multiple frames to give you a higher-quality image, compared to spatial.

For me, I have been using NVIDIA's [DLSS][3] (a temporal upscaler), when playing [Cyberpunk 2077 on Ubuntu][4], and it's been great. The performance difference between native and DLSS is quite noticeable, and the gameplay is remarkably smooth.

Now, it seems Arm is trying to get in on the upscaling action, but for smartphones. In a recent announcement, they have introduced **Arm Accuracy Super Resolution** , or Arm ASR for short, which is an open-source upscaler.

Interested? Then keep on reading. 😃

### Arm ASR: Upscaling For Smartphones

![Bistro Scene Test With Arm ASR][5]

Introduced as a temporal upscaler, Arm ASR is based on [AMD FSR 2][6], allowing developers to take advantage of their existing familiarity with the API and configuration options.

What makes it different from FSR 2 is the **highly efficient shader code** that Arm has come up with, which is tailored for mobile devices. They showed off many benchmarks using the popular Bistro scene ( _shown above_ ) to prove their claims of ASR being the “ _best-in-class open-source solution for upscaling on mobile devices_ ”.

The first one was on a device featuring the [Immortalis-G720 GPU][7], with a resolution of, _2800×1260_. As demonstrated by the bar chart below, there was a **53% increase in frame rates when compared to rendering at native** , with **FSR 2 being 17% slower** , and Qualcomm's [GSR][8] being 6% slower.

![Arm ASR Benchmarks On A Immortalis-G720][9]

When compared to FSR2 directly in terms of GPU performance on the _1920×1080_ resolution, Arm ASR was more efficient on all three presets.

![Arm ASR vs. AMD FSR 2 GPU Performance Analysis \(lower is better\)][10]

Arm even tested ASR for power consumption using a [Dimensity 9300][11]-equipped device, and the results were quite promising.

![Arm ASR Power Consumption Benchmark On A Dimensity 9300 Smartphone][12]

Furthermore, they also showcased **an in-house Unreal Engine demo** , which happens to be for future mobile GPUs. Taking advantage of its Robust Contrast-Adaptive Sharpening (RCAS) support, ASR was able to produce some pretty convincing outputs compared to others.

![Arm ASR In-House Unreal Engine Demo Comparison][13]

All in all, older smartphones, or even low-end devices, are the ones which will benefit the most by using Arm ASR. But, I am not sure how far back the support will go, maybe they will just focus on providing support for current devices and later? 🤔

### Try Arm ASR

Arm ASR is being made available in early access. Those interested will have to fill out [a form][14] for a chance to get their hands on it.

[Arm ASR (Early Access)][14]

If you can wait, then I would suggest you to keep an eye on Arm's [GitHub][15] page, where Arm ASR can be expected to show up eventually under the MIT License. For more details, you can give the [announcement blog][16] a visit.

_💬 Are you looking forward to this tech in your smartphones? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/arm-open-source-asr-upscaling/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Deep_learning_super_sampling
[4]: https://news.itsfoss.com/windows-game-on-linux-experience/
[5]: https://news.itsfoss.com/content/images/2024/07/Arm_ASR_a.jpg
[6]: https://github.com/GPUOpen-Effects/FidelityFX-FSR2
[7]: https://www.arm.com/products/silicon-ip-multimedia/immortalis-gpu/immortalis-g720
[8]: https://github.com/SnapdragonStudios/snapdragon-gsr
[9]: https://news.itsfoss.com/content/images/2024/07/Arm_ASR_b.jpg
[10]: https://news.itsfoss.com/content/images/2024/07/Arm_ASR_c.jpg
[11]: https://www.mediatek.com/products/smartphones-2/mediatek-dimensity-9300
[12]: https://news.itsfoss.com/content/images/2024/07/Arm_ASR_d.jpg
[13]: https://news.itsfoss.com/content/images/2024/07/Arm_ASR_e.jpg
[14]: https://forms.office.com/pages/responsepage.aspx?id=eVlO89lXqkqtTbEipmIYTQLm_fjbmCtLgMgj-pMtgBZUMDQ5VUhEM1dKM1ZROEowUFhFQUU0QzY2OC4u
[15]: https://github.com/ARM-software
[16]: https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/introducing-arm-accuracy-super-resolution
