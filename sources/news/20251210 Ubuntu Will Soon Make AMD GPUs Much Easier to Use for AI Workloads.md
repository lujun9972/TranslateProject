[#]: subject: "Ubuntu Will Soon Make AMD GPUs Much Easier to Use for AI Workloads"
[#]: via: "https://itsfoss.com/news/ubuntu-rocm-support/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ubuntu Will Soon Make AMD GPUs Much Easier to Use for AI Workloads
======

[![Warp Terminal][1]][2]

Ubuntu and AMD ROCm have become keystones in the AI development landscape.

[Ubuntu][3] is one of the most widely used distributions for machine learning work, while [ROCm][4] is AMD's open source platform that enables GPU acceleration for AI and high-performance computing workloads. Both play a critical role [in the current AI boom][5].

Now, Canonical has [announced a partnership][6] with AMD to bring ROCm Software natively to Ubuntu.

### AMD ROCm Comes to Ubuntu

__Watch this for more info on AMD ROCm.__

Canonical has put together **a dedicated team of engineers** specifically to package and maintain AMD ROCm software libraries for Ubuntu. This team will handle everything from initial packaging to ongoing support and long-term maintenance.

The plan is **to have ROCm available starting with Ubuntu 26.04 LTS** , with continued availability in every Ubuntu release after that. The Canonical team will also be submitting these packages upstream to [Debian][7], which could benefit the wider ecosystem if accepted.

#### **So What Does This Actually Mean?**

Well, it makes deploying AMD AI solutions much simpler across different environments. Whether you're running data centers, workstations, laptops, Windows Subsystem for Linux, or edge setups, ROCm will just work without much fuss or effort required from your side.

It will be available as a dependency for any Debian package, snap, or Docker image you are building. Performance fixes and security patches will be pushed through automatically like any other system package.

**For you as an end-user** , if you are on Ubuntu with an AMD GPU, then installing ROCm is set to become as simple as running `sudo apt install rocm` or having it automatically pulled in as a dependency when you install projects like [ollama-amd][8].

Both stable [LTS][9] versions and [rolling][10] ROCm releases will be available for Ubuntu to ensure support for the latest hardware. Security patches and performance improvements will be delivered via the regular `sudo apt upgrade` command.

Plus, [thanks to Ubuntu Pro][11], **the ROCm LTS releases will receive up to 15 years of support**.

[Andrej Zdravkovic][12], Senior Vice President and Chief Software Officer at AMD, had this to say during the announcement:

> AMD ROCm software enables open, high-performance acceleration for AI and HPC on AMD hardware.
>
> Working with Canonical to package AMD ROCm for Ubuntu makes it easier for developers and enterprises to deploy AMD solutions on supported systems.

**Suggested Reads 📖**

![][13]

![][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ubuntu-rocm-support/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://ubuntu.com/
[4]: https://www.amd.com/en/products/software/rocm.html
[5]: https://itsfoss.com/news/ai-causes-ram-prices-skyrocket/
[6]: https://canonical.com/blog/canonical-amd-rocm-ai-ml-hpc-libraries
[7]: https://itsfoss.com/news/debian-13-release/
[8]: https://ollama.com/blog/amd-preview
[9]: https://itsfoss.com/long-term-support-lts/
[10]: https://itsfoss.com/rolling-release/
[11]: https://itsfoss.com/news/ubuntu-15-year-support-commitment/
[12]: https://www.linkedin.com/in/andrej-zdravkovic-6920191/
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-90.png
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-91.png
