[#]: subject: "Reverse Engineering Linux Distro REMnux Marks 15 Years With Major v8 Release Featuring AI Agent Support"
[#]: via: "https://itsfoss.com/news/remnux-v8-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Reverse Engineering Linux Distro REMnux Marks 15 Years With Major v8 Release Featuring AI Agent Support
======

[![Warp Terminal][1]][2]

Linux has become [a lucrative target for bad actors][3], making specialized security tools more essential than ever. [REMnux][4] is a Linux distribution built specifically for such scenarios, helping researchers understand malware.

While [Kali Linux][5] is the go-to for penetration testing, REMnux specializes in reverse-engineering and analyzing malware. Both are essential security tools, but they serve different purposes.

The [new v8 release][6] brings many improvements, with some [agentic AI][7] support sprinkled in.

### REMnux v8: What's New?

![REMnux v8 desktop view \(left\) and its tool list \(right\).][8]

Featuring an [Ubuntu 24.04 LTS][9] base, REMnux v8 comes with a new [Cast][10]-based installer that is said to be more reliable and better for handling upgrades.

**Several new tools** also make it into this release, with additions like [YARA-X][11], which is a Rust rewrite of the popular [YARA][12] pattern matching tool. [GoReSym][13] and [Redress][14] are here for Go binary analysis, while [Manalyze][15] and [LIEF][16] handle PE, ELF, and MachO file parsing.

For Android analysis, there's [APKiD][17]. PDF files get [origamindee][18], and QR codes get [ZBar][19] for decoding. Python malware analysis gains [pyinstxtractor-ng][20] for unpacking PyInstaller executables and [uncompyle6][21] for decompiling bytecode. [AutoIt-Ripper][22] handles AutoIt scripts.

### The AI Buff

REMnux v8 adds a [new MCP server][23] that connects AI assistants like Claude or ChatGPT to the distro's analysis tools. The MCP server knows which tools work for different file types and how to interpret their output.

The AI can automatically run multiple tools in sequence. At standard depth, analyzing a Windows executable triggers about 16 different tools in one go. It plans how to analyze, selects the relevant tools, understands the output, and correlates the results.

When standard tools don't work, the AI can write custom Python scripts for things like reconstructing PE files or decoding obfuscated data.

[Lenny Zeltser][24], the creator of REMNux, demonstrated this with real malware samples [on his blog][25]. In addition, REMnux v8 also ships with [OpenCode][26], a terminal AI coding assistant that [works with the MCP server][27]. There are also AI plugins for tools like [Ghidra][28] and [Radare2][29].

### Install REMnux v8

The developers provide quite a few ways to get this release of REMnux. The most straightforward way is to import the [virtual appliance][30] into the [hypervisor][31] of your choice.

If that doesn't work for you, you can [install REMnux from scratch][32] on a dedicated system or run it as [a Docker container][33]. The source code for REMnux can be found on [GitHub][34].

[REMnux v8][30]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/remnux-v8-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/xz-utils-backdoor/
[4]: https://remnux.org/
[5]: https://www.kali.org/
[6]: https://zeltser.com/remnux-v8-release
[7]: https://en.wikipedia.org/wiki/AI_agent
[8]: https://itsfoss.com/content/images/2026/02/remnux-v8-desktop-view.png
[9]: https://itsfoss.com/ubuntu-24-04-lts-review/
[10]: https://github.com/ekristen/cast
[11]: https://github.com/VirusTotal/yara-x
[12]: https://github.com/VirusTotal/yara
[13]: https://github.com/mandiant/GoReSym
[14]: https://github.com/goretk/redress
[15]: https://github.com/JusticeRage/Manalyze
[16]: https://lief.re/
[17]: https://github.com/rednaga/APKiD
[18]: https://github.com/mindee/origamindee
[19]: https://github.com/mchehab/zbar
[20]: https://github.com/pyinstxtractor/pyinstxtractor-ng
[21]: https://github.com/rocky/python-uncompyle6
[22]: https://github.com/nazywam/AutoIt-Ripper
[23]: https://github.com/REMnux/remnux-mcp-server
[24]: https://zeltser.com/
[25]: https://zeltser.com/ai-malware-analysis-remnux
[26]: https://opencode.ai/
[27]: https://docs.remnux.org/discover-the-tools/use+artificial+intelligence
[28]: https://github.com/NationalSecurityAgency/ghidra
[29]: https://github.com/radareorg/radare2
[30]: https://docs.remnux.org/install-distro/get-virtual-appliance
[31]: https://linuxhandbook.com/what-is-hypervisor/
[32]: https://docs.remnux.org/install-distro/install-from-scratch
[33]: https://docs.remnux.org/run-tools-in-containers/remnux-containers
[34]: https://github.com/REMnux/distro
