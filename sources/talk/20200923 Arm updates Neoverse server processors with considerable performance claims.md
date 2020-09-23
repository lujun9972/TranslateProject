[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Arm updates Neoverse server processors with considerable performance claims)
[#]: via: (https://www.networkworld.com/article/3576031/arm-updates-neoverse-server-processors-with-considerable-performance-claims.html)
[#]: author: (Andy Patrizio https://www.networkworld.com/author/Andy-Patrizio/)

Arm updates Neoverse server processors with considerable performance claims
======
Arm boasts the new Neoverse processor designs will deliver 50% better performance for the same power as the previous generation.
ARM

[Acquisitions][1] and [defections][2] be damned, Arm Holdings is pushing forward with its Neoverse line of server processor designs with the launch of the Neoverse V1 and N2 processor architectures.

The new chips are the successors to the Neoverse N1 and E1 designs, which are used in server processors like Ampere’s Altra, Amazon’s Graviton2, and Marvel’s ThunderX2. Arm claims these chips will deliver 40% to 50% better performance than the previous generation while consuming the same amount of power.

“The emergence of Arm in the data center is being powered by many factors—customization, efficiency, ecosystem diversity—but all of that builds on top of performance,” said Chris Bergey, senior vice president and general manager of Arm’s infrastructure business, in a briefing with journalists and analysts. “If Neoverse wasn’t delivering a significant measurable value proposition you would not see the market adoption and momentum that we are achieving,”

The V1 architecture is for CPU workloads where single-threaded performance is paramount. The V1 adds scalable vector extensions (SVE), making it ideal for high-performance compute (HPC) and AI/machine learning applications. V1 will also support bfloat16, PCIe 5.0 connectivity, DDR5, HBM2e and CCIX 1.0 for bidirectional coherent communications between chips across sockets and in-package chiplets.

SVE enables execution of SIMD integer, bfloat16, or floating-point instructions on wider vector units using a software programming model agnostic to the width of the unit. In creating its HPC Arm processor, Fujitsu [added its own SVE][3] and got the top spot on the [Top 500 supercomputer list][4] for it.

Like the N1, the N2 was built specifically for scale-out architectures. Arm is positioning it for SmartNICs, enterprise switches, and edge networks. It can support up to 192 cores, but it will run at 350 watts. That’s GPU territory.

N2 will be designed for 5nm process technologies, and those aren’t even out yet. As such the N2 won’t ship until next year, and that’s to Arm licensees. They will then need time to make their own designs. Like V1, it will support PCIe 5.0 and DDR5, along with HBM3 as well as both CCIX 2.0 and CXL 2.0 for fabrics.

Arm also said it plans to make continued investments in technologies like Compute Express Link (CXL) and Cache Coherent Interconnect for Accelerators (CCIX) in order to enable ultra-low latency fabrics and desegregated computing platforms.

Join the Network World communities on [Facebook][5] and [LinkedIn][6] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3576031/arm-updates-neoverse-server-processors-with-considerable-performance-claims.html

作者：[Andy Patrizio][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Andy-Patrizio/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3574972/chip-maker-nvidia-takes-a-40b-chance-on-arm-holdings.html
[2]: https://www.networkworld.com/article/3574013/marvell-exits-the-general-purpose-arm-server-business.html
[3]: https://www.networkworld.com/article/3535812/can-fujitsu-beat-nvidia-in-the-hpc-race.html
[4]: https://www.networkworld.com/article/3563766/the-10-fastest-supercomputers-are-led-by-one-28x-faster-than-the-rest.html
[5]: https://www.facebook.com/NetworkWorld/
[6]: https://www.linkedin.com/company/network-world
