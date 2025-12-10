[#]: subject: "Find out how your Fedora system really feels (with the linux-mcp-server!)"
[#]: via: "https://fedoramagazine.org/find-out-how-your-fedora-system-really-feels-with-the-linux-mcp-server/"
[#]: author: "Máirín DuffyBrian Smith https://fedoramagazine.org/author/duffy/https://fedoramagazine.org/author/briansmith/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Find out how your Fedora system really feels (with the linux-mcp-server!)
======

![][1]

Generative AI systems are changing the way people interact with computers. MCP (model context protocol) is a way that enables generate AI systems to run commands and use tools to enable live, conversational interaction with systems. Using the new [linux-mcp-server][2], let’s walk through how you can talk with your Fedora system for understanding your system and getting help troubleshooting it!

### Introduction

Large language models (LLMs) can be an invaluable tool when investigating an issue on a Linux system. However, this can involve a lot of copy/pasting of information from the Linux terminal into a web based interface to an LLM model.

The model context protocol (MCP) acts as a bridge, enabling LLMs to interact with external tools and data sources. The linux-mcp-server utilizes this protocol to give LLMs the ability to interact with a Fedora Linux system. Instead of you manually copying and pasting terminal output, the linux-mcp-server enables the LLM to directly query system information and log entries.

By enabling an LLM direct access to system information and logs, it is transformed into an active part of the investigation process when troubleshooting an issue. It empowers an LLM to directly query the system state, allowing it to help identify performance bottlenecks, and identify important log entries that might be missed by a manual review.

### What is the model context protocol (MCP)?

[Anthropic introduced MCP in November 2024][3] as an open standard for LLM tool use. This provides a way for LLMs to interact with outside systems and data sources.

Prior to MCP, there wasn’t as strong a standard and ecosystem for LLM systems to call tools. LLMs were thus frequently limited to have only the information contained in their training. They were isolated from the outside world. For example, if you asked an LLM “ _what is the weather going to be next week_ ”, the LLM would respond with a message indicating that it doesn’t know what the weather will be, as it doesn’t have access to that information. MCP helps solve this problem by enabling a standardized way for an LLM to access an outside data source, such as the weather forecast.

At a high level, users can use an AI agent application, such as [Goose][4] (open source), or Claude Desktop, and specify which MCP servers they would like to use. The AI agent application informs the LLM that there are tools available via these MCP servers that can be used to help answer the requests from the user. The LLM model can then decide when to invoke these tools.

MCP is an open standard. You have the flexibility to use MCP servers, such as [linux-mcp-server][2], with either open source-licensed LLM models, or hosted proprietary LLM models.

### What is the linux-mcp-server?

The [linux-mcp-server][2] is a project started by Red Hat’s RHEL Engineering team. It provides a number of tools that enable an LLM to query information from a Linux system, such as system info, service information and logs, process information, journald and other logs, network information, and storage and disk information. For a full list of the tools provided, refer to the [project’s Github page][2].

These tools, provided by [linux-mcp-server][2], are focused on providing the LLM access to read-only information. In the future, we’ll be exploring expanding past these read-only use cases.

The linux-mcp-server can be used to interact with the local Fedora Linux system that it is running on. It can also be used to interact with remote Fedora Linux systems over SSH. For example, if you have SSH key authentication setup with the remote systems, you could make a request to your AI agent application such as “ _Determine the current memory usage on the fedora1.example.com, fedora2.example.com, and fedora3.example.com servers_ ”.

### Prerequisites

The main components needed are an AI agent application, access to LLM model inference, and the linux-mcp-server.

There are a number of options for the AI agent application, both open source and proprietary. An example of an open source AI agent is [Goose][4], which provides an RPM that can be installed on Fedora.

There are several LLM model inference options, ranging from locally hosted open source models, to proprietary hosted LLM models. If hosting a model locally, you generally need to have GPU/accelerator hardware available. Open source tools that can be used to locally host LLM models include [RamaLama][5], [llama.cpp][6], and [Ollama][7]. There are a number of open source LLM models capable of tool calling. These include models such as [gpt-oss-20b][8] and [Granite 4 small][9].

Once you’ve installed your preferred AI agent application, the next step is to install the linux-mcp-server and configure your AI agent application to use it. The [linux-mcp-server Github page][2] includes installation instructions, and configuration details for Goose and Claude Desktop.

### Use cases for linux-mcp-server

#### Dear Fedora, why are you so slow today?

Has this happened to you? Time to hop on a call and give a demo. You’re pumped. It’s your go-time aaaaand… your system starts lagging. Folks on the call say your video is choppy or they can’t understand you. OH NO.

You’ve got to assess what’s up, quickly. Run `top`, check `dmesg`, check your network connection (read the man page for `netstat` because you can’t remember the flag you want), check `journalctl`, cross-reference what you’re seeing, then start killing processes, restarting services, reloading kernel modules willy-nilly based on hastily-crafted theories, see if it improves…

This is a case where you could actually ask the system to tell you why it’s slow and give it the ability to do the analysis via linux-mcp-tools. The LLM you connect with won’t just run the commands through the MCP server; it will understand what the numbers it gets means in context and be able to explain in human terms.

So let’s start working with a relatively new laptop. It’s a Thinkpad T14S with the AMD Ryzen™ AI Pro 7 ( Ryzen™ AI 360 chip.) Recently one of the wifi networks it must connect to regularly was upgraded. It now has issues with the network connection stability. So let’s talk to Goose + gpt-oss:20b + linux-mcp-server about it. Here’s the initial prompt I used:

```

    My Wifi doesn't work very well. It cuts out after a few minutes. Help me fix it. Can you find the error messages in the system logs and diagnose the problem?

```

It responded with the following:

```

    I'll help you diagnose your WiFi connectivity issues by examining the system logs for error messages related to your network interfaces and wireless connectivity. Let me start by gathering information about your system and checking the relevant logs.

```

It then made a series of tool calls, including Get System Information, Get Network Interfaces, Get Journal Logs, Get Hardware Information, Get Service Status service_name:NetworkManager, Get Service Status service_name:wpa_supplicant, Read Log File. The result was this analysis, which is the actual problem I was hoping it could find!

* * *

### ⚡ Problem Summary

Your ATH12K PCI (Qualcomm 802.11ax) wireless card repeatedly reports
```

```

ath12k_pci 0000:c2:00.0: failed to enqueue rx buf: -28
```

```

every few minutes, which triggers a drop of the wireless link. The driver is trying to enqueue an **RX buffer** for the hardware but fails with errno **‑28**.

> **‑28** →
>
> -ENOMEM
>
> (out‑of‑memory for the driver buffer); the kernel cannot allocate a DMA‑coherent RX descriptor.

### ✅ Likely Root Causes

Cause | Evidence / Typical Scenario | Fix / Work‑around
---|---|---
Driver bug or missing patch | The kernel’s ath12k driver has had a long‑running issue with RX ring management in older 5.15/5.4 series. | Update the kernel or apply the latest patch from the linux tree (5.18+ or the ath12k backports).
Out‑of‑memory in the driver | The error itself is “‑28” – a memory‑allocation failure inside the driver. | Reduce the number of RX descriptors, or enable **fast‑RX** disabled mode ( modprobe ath12k_pci ath12k_pci_disable_fast_rx=1 ).
Firmware mismatch / corruption | Old firmware ( ath12k_hwgen files) don’t match the driver version. | Reinstall firmware from your distro ( sudo apt‑install --reinstall linux‑firmware ) or copy the latest from kernel source.
System memory pressure | If many big processes run, DMA‑coherent memory pool can be exhausted. | Free RAM, close memory‑heavy apps, or add swap.
ACPI/PCIe power‑management quirk | Some laptops throttle the Wi‑Fi device after idle, resetting the buffer queue. | Add pci_bus_reset = off or set ath12k_pci_disable_ps=1 in a modprobe conf.
Hardware issue (e.g., faulty PCIe slot or NIC) | Persistent failure after multiple driver/kernel upgrades. | Test on another machine/PCIe slot or replace the card.

### 🔎 Diagnostic Checklist

  1. **Kernel & Driver Version**
```

```
 uname -r
modinfo ath12k_pci | grep ^version:
```

```
   2. **Driver Parameters**
```

```
 cat /sys/module/ath12k_pci/parameters/*
```

```
 – See if

ath12k_pci_disable_fast_rx

or similar is already set.

  3. **Firmware Location**
```

```
 ls /lib/firmware/ath12k/ath12k/ar9009/ | grep wlan0 | head
```

```
 – If the files are missing or older than the driver, copy newer ones from

/lib/firmware

of a newer kernel.

  4. **Kernel Log Around the Error**
```

```
 sudo dmesg --ctime | grep -A3 'ath12k_pci 0000:c2:00.0'
```

```
 – Observe if there are any other “-ENOMEM” or “resource exhaustion” messages.

  5. **Memory Usage Stats**
```

```
 free -h
vmstat 1 5
```

```
   6. **PCIe Latency / Link State**
```

```
 sudo lspci -vvv -s c2:00.0 | grep -iE "link|latency"
```

```



### 🚀 Quick‑Fix Path (Try in this order)

Step | Command | What it does
---|---|---
1 |
```

```

sudo apt update && sudo apt upgrade linux-firmware
```

```

| Refresh firmware to the latest distro version.
2 |
```

```

sudo apt upgrade linux-image-$(uname -r)
```

```

| Apply latest kernel with patched ath12k driver (or switch to 5.18+ if still on 5.15).
3 |
```

```

echo "ath12k_pci ath12k_pci_disable_fast_rx=1" | sudo tee /etc/modprobe.d/ath12k.conf
```

```

| Force the driver to use a more conservative RX scheme.
4 | Reboot and monitor: dmesg -T | grep ath12k_pci | Verify the error disappears.
5 | Optional: test on another machine or use a USB‑WiFi dongle (USB 802.11ax / 802.11ac) as a temporary workaround. | Ensure the issue is not hardware‑specific.

**Tip:** After reboot, you can also verify driver parameters:

cat /sys/module/ath12k_pci/parameters/ath12k_pci_disable_fast_rx

### 📺 Advanced Debugging (if basic fixes don’t help)

  1. **Enable debug logs**
```

```
 sudo bash -c 'echo 1 > /sys/module/ath12k_pci/parameters/debug'
sudo dmesg -T | grep ath12k
```

```
   2. **Check PCIe device state**
```

```
 sudo lspci -vv -s c2:00.0
```

```
   3. **Use**

* * *

**ethtool**

**on the Wi‑Fi interface**
```

```
 sudo ethtool -S wlp4s0
```

```
   4. **Look for firmware logs**
```

```
 grep -i 'ath12k' /var/log/syslog
```

```



### 📌 Bottom Line

The “failed to enqueue rx buf: –28” is an **internal driver allocation failure** that typically follows one of two paths:

  1. The driver or firmware is out of date → upgrade kernel/firmware.
  2. The driver configuration is too aggressive for your system’s memory budget → tweak module parameters or free RAM.



If you're still stuck after following the quick‑fix path, it's worth capturing more detailed logs with the above diagnostic commands and sharing them. We can then cross‑reference the exact kernel version/driver commit to see if a known patch exists.

Feel free to let me know which step you’ve tried or if you encounter any new log messages, and we’ll dig deeper!

* * *

Not too bad an analysis and set of debugging steps! I’ll follow up in the comments and let you know if the solution works.

#### Where’d my disk space go, Fedora?

Trawling through `du` on the command line, converting the numbers in your head, sorting them – it can be tedious. We even have graphical tools like `baobab`, but it takes time to load in the results and explore the data. And sometimes you might have questions it can’t answer in terms of the risk of deleting a specific directory, or the age of a specific file. It’s easier to be sloppy and just let the disk fill up. But there comes a time where that is no longer an option.

You can ask the system using the linux-mcp-server to analyze your disk usage, give you a hitlist of the top space-eating places on the file system, and give you advice with a risk analysis of how to clean it up.

Here’s my prompt:

```

    I need help analyzing disk usage on my system. Can you:

    1. Show me the current disk usage across all filesystems using get_disk_usage
    2. Use list_directories_by_size to show me the 10 largest directories (this will help identify where disk space is being consumed)
    3. Check if there are any large log files consuming space using get_journal_logs or read_log_file
    4. Review running processes with list_processes to see if any are consuming excessive resources or creating temporary files

    After gathering this information, help me identify potential space-saving opportunities and assess the safety of cleaning up specific directories. Please don't only examine top-level directories. I want you to go deep if needed to find out where the largest files are!

```

I ran this prompt on my Fedora 42 system using linux-mcp-server with Goose connected to locally-served gpt-oss:20b, and here’s the output I got:

* * *

**Disk‑space overview (as of Nov 24 2025 15:21)**

**Filesystem** | **Size** | **Used** | **Avail** | **Use %** | **Mounted on**
---|---|---|---|---|---
/dev/mapper/luks‑61cedb0e… | 952.3 GB | 548.9 GB | 399.6 GB | **57.9 %** | /
/dev/mapper/luks‑61cedb0e… | 952.3 GB | 548.9 GB | 399.6 GB | 57.9 % | /home
/dev/nvme0n1p2 | 973.4 MB | 462.8 MB | 443.4 MB | 51.1 % | /boot
/dev/nvme0n1p1 | 598.8 MB | 19.3 MB | 579.6 MB | 3.2 % | /boot/efi

_Overall usage is comfortably below 60 % of a 952 GB volume, so immediate capacity pressure isn’t a concern. The biggest contributors to disk space today are in the_ _~/._ _hierarchy._

* * *

#### **1\. Biggest directories on the system**

**Path (relative to the mount point)** | **Size (≈)** | **Notes**
---|---|---
~/ – User home (2 mounts: /home + /) | 1 TB total | 57 % used; the bulk of the space is in ~/

| ~/duffy/.local/share | **238 GB** | Containers sub-dir, followed by Trash (7GB) – typical podman/docker container images |
| ~/duffy/.local/share/containers | **238 GB** | Container layers, images, root filesystems – the prime candidate for cleanup |
| ~/duffy/.local | 266 GB | share (237 GB) dominates it |
| ~/duffy/.local/share/containers (inside share) | 238 GB | Same as above – just a different view |
| ~/duffy/.local/lib | 13 GB | Likely a virtual‑environment library set |
| ~/duffy/.local/bin | 4 GB | Helper binaries |
| ~/duffy/.local/share/Trash | 7 GB | User‑deleted items still resident on disk |
| ~/duffy/.local/share/containers (nested) | 238 GB | Same as above; redundant listings from recursive depth‑1 scans |
| ~/duffy/.local/share (top‑level) | 238 GB | containers is the absolute largest item |

**Take‑away** – 75 % of the 238 GB live inside three nested directories:

  * ~/duffy/.local/share/containers (238 GB) → _Rooted in Podman/Container‑Store_
  * ~/duffy/.local/share (238 GB) → _Same data exposed at a higher level_
  * ~/duffy/.local/share/Trash (7 GB)



* * *

#### **2\. Possible space savers**

**Category** | **Recommendation** | **Rationale**
---|---|---
**Containers** | podman system prune -a (or docker system prune -a if Docker is in use) | Removes **unreferenced images, containers, and caches**. This can reclaim 200–250 GB if most containers are outdated or no longer referenced.
**Trash** | gio trash –empty | The 7 GB in Trash is still taking physical space; simply emptying it will free that amount.
**Large libs/binaries** | Check ~/duffy/.local/lib – 13 GB, and ~/duffy/.local/bin – 4 GB | If these are not actively used by a project, consider uninstalling or moving them to a secondary, less‑frequented store.
**Ramalama & UV** | 9 GB (ramalama), 8 GB (uv) | Possibly temporary files or caches from development tools. Inspecting the contents of these directories (du -h) can reveal if they are still needed.
**Other caches** | pnpm store prune, virtualenv or pip cache purge | Development tool caches often accumulate; they’re usually safe to delete once you’re done with the current development sessions.
**Logs** | The system journal shows normal activity, and syslog access is blocked by policy. | Systemd journal stores are rotated automatically; no urgent action required.
**Boot partitions** | Not relevant – they’re low‑usage (boot/efi only 3 % used). | No action needed.

* * *

#### **3\. Disk‑IO perspective**

  * Reads: **111.8 GB** ; Writes: **85.6 GB** since boot (≈ 1.2 TB total).
  * If writes are high relative to free space, consider enabling a **tmpfs** overlay for temporary files or moving large data to a separate, faster SSD. But in this case, writes are not approaching the 399 GB free.



* * *

#### **4\. Suggested cleanup workflow**

_# 1. Empty Trash_

```

    gio trash --empty

```

_# 2. Prune unused containers/images_

```

    podman system prune -a   # or docker system prune -a

```

_# 3. Remove leftover caches_

```

    pnpm store prune         # if pnpm is installed

```

```

    pip cache purge          # for Python

```

```

    virtualenv --clean       # optional

```

_# 4. Inspect large “RAM” directories manually if you need deeper cleanup_

```

    du -h --max-depth=1 ~/duffy/.local/share/containers

```

**Tip:** After each step run df -h /home or du -sh ~/duffy/.local/* to see the impact.

* * *

#### **5\. Safety checklist**

**Action** | **Why it’s safe (or risk)**
---|---
**Emptying Trash** | Deletes only user‑deleted files; confirm you don’t need the content.
**podman system prune -a** | Deletes container _images_ , _containers_ , and _volumes_ that are not referenced by any running or stopped container. Verify with podman ps -a before pruning.
**Removing lib/bin from** **.local** | Only safe if you’re sure those libraries/bin files aren’t part of a running application.
**Caution with** **tmpfs** **or moving large directories** | If you move a directory on‑the‑fly, ensure no running application depends on that path.

* * *

##### **Bottom line**

  * **Current free space:** ≈ 400 GB on both / and /home.
  * **Largest consumptions:** User‑space under ~/duffy/.local/share/containers (≈ 238 GB).
  * **Actionable clean‑ups:** Empty Trash, prune unused container images, and review large libraries/binaries. This should reclaim **over 200 GB** and bring the usage from **57.9 %** down to roughly **40‑45 %** – plenty of headroom for the future.



Feel free to ask what next steps you’d like to dig into (e.g., detailed contents of the containers dir, specific application logs, or targeted pruning commands).

* * *

#### Upgrade planning

So you may have noticed a little detail above – the system is a Fedora 42 system… and Fedora 43’s been out a month now! 😅 So, time to upgrade.

This example shows where we have some tools missing from the set provided in the linux-mcp-server. We’re including it for two reasons:

  * **So you can see how this works manually
**You can see that even when specific tools you might not need are available in the MCP server, you can have the response give you instructions on commands to run on your own, and copy/paste the command output back into your chat to get analysis alongside the data the system is able to pull via the MCP tool calls;
  * **To encourage you to submit additional tools to our project!**
We would love your additions to the project! Here’s where to get started: <https://github.com/rhel-lightspeed/linux-mcp-server/blob/main/docs/CONTRIBUTING.md>



Here’s the prompt I started with, with the same Goose + gpt-oss:20b + linux-mcp-server combination:

```

    You are a Linux system administrator assistant analyzing a Fedora system for upgrade readiness.

    TASK: Examine this Fedora 42 system and provide a comprehensive upgrade readiness report for Fedora 43.

    ANALYSIS CHECKLIST:
    1. Check current Fedora version: cat /etc/fedora-release
    2. Review system updates status: dnf check-update
    3. Identify third-party repositories: dnf repolist
    4. List installed packages from non-Fedora repos: dnf list installed | grep -v @fedora
    5. Check for broken dependencies: dnf check
    6. Review disk space on root partition: df -h /
    7. Check for unsupported or deprecated packages
    8. Identify custom kernel modules: lsmod | grep -v "^Module"
    9. Review SELinux status: sestatus
    10. Check for pending system updates: dnf upgrade --refresh --assumeno

    REPORT FORMAT:

    # Fedora 43 Upgrade Readiness Report

    ## Current System Status
    - Fedora version: [version]
    - Kernel: [kernel version]
    - Updates status: [current/outdated]

    ## Potential Issues
    [List blocking issues with HIGH/MEDIUM/LOW severity]

    ## Third-Party Software
    [List non-Fedora packages that may need attention]

    ## Recommendations
    [Specific pre-upgrade steps needed]

    ## Overall Readiness: [READY/NEEDS ATTENTION/NOT READY]
    Run the necessary commands and provide this analysis. Be specific about any issues found and give actionable recommendations.

```

Now, right away the model came back to me to complain it doesn’t have access to `dnf`, `cat`, etc. And that’s expected here. What it did was give me a list of homework to run for it to complete the analysis… for example, `dnf check-update` and `cat /etc/fedora-release`. I had a little back and forth in Goose with the model where it would ask me to run a command and I’d copy the output into the context. This resulted, finally, in the following report:

* * *

### **Fedora 43 Upgrade Readiness Report**

**Analyzed System** – Fedora 42 (Kernel 6.17.7‑200.fc42.x86_64)
**Date** – 2025‑11‑24

* * *

#### **1\. Current System Status**

**Item** | **Value**
---|---
**Fedora release** | 42 (Adams)
**Kernel** | 6.17.7‑200.fc42.x86_64
**Root filesystem** | 953 GB LUKS, 58 % used (411 GB free) – **> 15 % free**
**/var /usr** | Same as root partition (mounted the same LUKS device)
**SELinux** | **enabled** (policy _targeted_ ), **currently permissive**
**System‑wide packages** | No held packages (dnf versionlock list empty)
**System modules** | No modules held.

**TL;DR** – The base system is clean; the kernel is up‑to‑date for 42, there is ample disk space, and there are no version‑locked packages.

* * *

#### **2\. Third‑Party Repos & Packages**

**Repository** | **Description** | **Current** **dnf repolist** **status**
---|---|---
rpm-fusion-free, rpm-fusion-nonfree, rpm-fusion-updates | Widely used RPM‑Fusion components | **Enabled**
google-cloud-cli | Google Cloud SDK (RPM built for EL 10) | **Enabled**
visual-studio-code | Microsoft VS Code RPMs | **Enabled**
command‑line‑assistant, google‑chrome, PyCharm, unsupported‑fedora‑packages, goose, leaktk | Various Copr builds (mostly Fedora‑42 based) | **Enabled**

**What we need to verify**

  1. **Is a Fedora 43 build available** for each of the non‑Fedora repos above?
  2. **Does** **google-cloud-cli** **have a Fedora 43‑compatible package?** (EL 10 build may not be usable).
  3. **Are there any** **el10‑specific dependencies** that could surface during the upgrade?
  4. **Any custom kernel modules** that will require re‑compilation against the 43 kernel.



* * *

#### **3\. Potential Issues & Severity**

**Issue** | **Severity** | **Why it matters** | **Immediate Remedy**
---|---|---|---
**Non‑Fedora packages (e.g., google‑cloud‑cli)** | MEDIUM | May contain packages built for EL 10; could conflict with Fedora 43 libs. | Verify if a Fedora 43 build exists or plan to remove/re‑build it.
**Third‑party repos without 43 builds** | MEDIUM | dnf system-upgrade pulls all _enabled_ repos; lacking 43 packages causes transaction failure. | Disable such repos temporarily (dnf config-manager –set-disabled <repo>) or enable the 43 stream when available.
**Custom kernel modules** | LOW | Modules compiled against 42 kernel won’t load on 43; services may drop. | Re‑compile or patch modules after upgrade.
**Broken dependencies reported by** **dnf check** | HIGH | Would block the upgrade transaction. | Run sudo dnf check now; fix any reported issues.
**Insufficient disk space** | HIGH | Upgrade scripts need > 15 % free. | Not an issue (58 % free).

**Current High‑Risk Items** – None detected yet.
**Next Action** – Confirm each third‑party repo has 43‑compatible packages and set SELinux to enforcing.

* * *

#### **4\. Recommendations (Pre‑Upgrade Checklist)**

**Step** | **Command** | **Purpose**
---|---|---
**Confirm 43‑stream packages** | `dnf list –available * | grep <repo-id>`
**Verify SELinux enforcement** | sestatus | Should show _enforcing_.
**Check for broken dependencies** | sudo dnf check | No errors should appear.
**Refresh all repos** | sudo dnf upgrade –refresh | Pull latest metadata.
**Dry‑run upgrade** | sudo dnf system-upgrade download –releasever=43 –allowerasing | Detect any missing packages or conflicts.
**Optional: Disable problematic repos** | sudo dnf config-manager –set-disabled <repo> | Prevent upgrade crash if a repo has no 43 build.
**Persist SELinux config** | sudo sed -i ‘s/SELINUX=permissive/SELINUX=enforcing/’ /etc/selinux/config | Make enforcement permanent.

* * *

#### **5\. Post‑Upgrade Actions**

  1. **Reboot into the new kernel** (dnf system-upgrade reboot).
  2. **Re‑compile any custom kernel modules** against the new kernel (yum install kernel-devel-$(uname -r) then rebuild modules).
  3. **Re‑enable any disabled repos** once the upgrade completes.
  4. **Verify critical services** (systemctl status <service>) and check logs.
  5. **Run** **sudo dnf distro-sync** to ensure all packages are the latest from Fedora 43.



* * *

#### **6\. Overall Readiness**

**Criteria** | **Status** | **Comment**
---|---|---
**Disk space** | **Ready** | 58 % free
**Package health** | **Ready** | No held or broken packages
**Third‑party repos** | **Conditional** | Verify 43‑compatibility
**Custom modules** | **Pending** | Need to identify modules and re‑compile
**Final verdict** | **READY** (after addressing above points) |

**Next step** – Run the three **verification** commands below and share the output with me:

```

    sudo dnf check

```

```

    sudo dnf repolist

```

```

    dnf list installed | grep -v @fedora

```

With those outputs I can pinpoint any remaining blockers and give you a final, ready‑to‑proceed plan.

Happy upgrading!

* * *

### Give it a try, let us know what you think!

![][10]

You can see from these few examples that tool calling with LLMs is a valuable tool for troubleshooting Linux systems. We could use your help building this and making it awesome! How can you help?

  * Give it a try, let us know what you think, [file any bugs you find, and let us know what tools are missing][11] that you could use! You can respond in the comments here, [file a bug][11], or [chat with us on Fedora matrix][12].
  * We’re primarily working with [Goose][4] as our client, but if you have another preferred client and want to help us support it better, we’d love to work with you!
  * Get involved in the [linux-mcp-project][11] generally, we’d love to see your PRs!
  * Let us know what you’d like to see in the future. What workflows would you like to see supported? How do you see this making your Fedora or overall Linux experience better? What larger workflows do you see this plugging into?



Join us upstream at **<https://github.com/rhel-lightspeed/linux-mcp-server>**! And come chat with us in the [Fedora AI/ML SIG chat room][12] on Matrix!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/find-out-how-your-fedora-system-really-feels-with-the-linux-mcp-server/

作者：[Máirín DuffyBrian Smith][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/duffy/https://fedoramagazine.org/author/briansmith/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/12/Linux-mcp-server-816x346.jpg
[2]: https://github.com/rhel-lightspeed/linux-mcp-server
[3]: https://www.anthropic.com/news/model-context-protocol
[4]: https://github.com/block/goose
[5]: https://github.com/containers/ramalama
[6]: https://github.com/ggml-org/llama.cpp
[7]: https://github.com/ollama/ollama
[8]: https://huggingface.co/openai/gpt-oss-20b
[9]: https://huggingface.co/ibm-granite/granite-4.0-h-small
[10]: https://fedoramagazine.org/wp-content/uploads/2025/11/image.png
[11]: https://github.com/rhel-lightspeed/linux-mcp-server/issues
[12]: https://matrix.to/#/#ai-ml:fedoraproject.org
