[#]: subject: "Web-Based Remote Installation for Fedora Linux: Here’s What We’re Building"
[#]: via: "https://fedoramagazine.org/web-based-remote-installation-for-fedora-linux-heres-what-were-building/"
[#]: author: "Bruno Ciconelle https://fedoramagazine.org/author/bciconelle/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Web-Based Remote Installation for Fedora Linux: Here’s What We’re Building
======

![][1]

If you’ve ever needed to install Fedora Linux on a headless server, a Raspberry Pi, or any machine without a monitor attached, you’ve probably reached for VNC or RDP. They work – but as the installer moves to a web-based interface, there’s a new opportunity to do something more native to that model. We’re building it, and we want your input before we go too far down a path that’s hard to reverse.

### Why This Is Happening

The Anaconda installer’s Web UI first landed in Fedora Linux 42 Workstation and was extended to all Live spins in Fedora Linux 43. It’s a full graphical installer built on Cockpit tooling and using PatternFly widgets. The GUI is rendered in a fullscreen browser window – but until now, that browser had to be running on the same machine you’re installing onto.

Here’s the thing: VNC and RDP were built around the GTK interface. While RDP could technically work with the Web UI too (it operates at the display level), a remote browser is a much better fit – orders of magnitude less data and much lower UI latency. As the Web UI becomes the primary installer interface across Fedora Linux editions, it needs its own native remote access story.

On top of that, there are two more forces pushing in the same direction.

As browsers move toward Flatpak packaging – already the reality for atomic desktops and derivatives like Bazzite – remote installation opens an opportunity for shipping focused, smaller boot images that don’t need to bundle a local browser at all. A lightweight ISO aimed at headless and network install scenarios, where the assumption is that you’re connecting from another machine.

And once you have a browser-rendered installer, serving it to a remote browser is the natural next step anyway. A headless ARM SBC doesn’t need to run a GPU-accelerated browser locally just to show you a disk partitioning screen. Your laptop can do that for it.

### What It Actually Is

The concept is pretty straightforward: Anaconda’s Web UI, already built on Cockpit, gets served over HTTPS. You point a browser at the machine you’re installing, authenticate with a PIN, and you’re controlling the installation remotely. No VNC client, no RDP client, no X forwarding. Just a browser.

If you’ve used Cockpit to manage a server, you already have a feel for the experience. The difference is that the machine you’re connecting to is mid-install, not running a full OS.

### Use Cases

The ones we’ve talked through most:

**Headless servers** – You’re installing onto a server in a rack with no attached display. You expose the Web UI over the network and control everything from your workstation.

**Lightweight ARM SBCs** – Devices like Raspberry Pi have limited resources. With remote rendering, the Pi just runs the installer backend; all the UI rendering happens on whatever machine you’re connecting from.

**Remote monitoring** – Even if you’re not fully headless, being able to watch an installation from another machine is genuinely useful. Kick off a server install, go make coffee, check progress from your laptop.

### The Design Decisions So Far

We’ve had some meaty discussions about how this should work, and a few things are now settled.

**Authentication** : You set a PIN through kickstart or boot options, and type it into the browser login page. Same pattern as VNC and RDP – the user provides the password, not the system.

**TLS with self-signed certificates** : The connection is encrypted, but the certificate is generated on the fly at boot. That means your browser will show the “this certificate isn’t trusted” warning. We’ve accepted this tradeoff – shipping a private key on installation media is a security risk, and the IP address isn’t known ahead of time, so standard PKI doesn’t really apply. For environments that need proper certificates (say, a university deploying at scale), [Image Builder][2] is likely the right path to embed custom certs. That’s a later problem.

**Single connection only** : Only one browser session can connect at a time. Two concurrent sessions could genuinely conflict – one session starting installation while another changes the storage configuration. So: one connection, full stop.

**Reconnection behavior** : If you disconnect and reconnect, what happens depends on where the installation was. Before the review screen – the point of no return – you start from step one. After the review screen (installation actually running), you land on the progress view. Simple two-state model, covers the critical cases.

**Config isolation and port** : All Cockpit configuration specific to remote installation lives in /etc/anaconda/cockpit/, not the default Cockpit paths – otherwise the config could leak into the installed system. We’re leaning toward port 443 by default so you can just point your browser at the machine’s IP without specifying a port, but the port will also be configurable.

### How This Compares to VNC and RDP

VNC has been around in Anaconda for years; RDP support was added more recently. Both work by screen-sharing the GTK interface. Technically, RDP could work with the Web UI too – it operates at the display level, scraping pixels from the screen. But a remote browser is simply better: you send orders of magnitude less data and get much lower UI latency compared to streaming a full desktop.

Beyond performance, there are practical advantages. No client is required – any modern browser works. No VNC viewer to install, no RDP client to configure, no protocol quirks across platforms. And it’s the same Web UI we’re already actively developing, so features and fixes automatically benefit the remote experience. With VNC or RDP, you’re screen-sharing a separate GTK codebase – a separate maintenance burden.

VNC and RDP aren’t going away for now – they still work with the GTK legacy interface. But as the Web UI becomes the default across more Fedora Linux editions, browser-based remote access is where the investment goes.

### Where We Are Right Now

This is a developer preview. Here’s what’s working:

  * Custom login page with PIN-based authentication
  * Separate socket-activated systemd unit for auth (clean separation from the main Cockpit process)
  * Session cookies that survive tab closes, require re-login on browser close
  * Cockpit config in an isolated, anaconda-owned path



Here’s what’s still open:

  * Single-connection enforcement (this will likely require close collaboration with the Cockpit team)
  * Backend detection of whether installation is already running (this is needed for proper reconnection behavior)



If you want to see the PoC in action, there’s a draft PR at [rhinstaller/anaconda-webui#1274][3] with the authentication setup – custom login page, pin-based auth script, socket-activated systemd units, and the Cockpit config override. To try it yourself, clone the PR branch, build an updates image, and boot it with virt-install:

```

    git clone -b poc-remote https://github.com/bruno-fs/anaconda-webui.git
    cd anaconda-webui
    make create-updates.img

    virt-install \
      --name anaconda-remote-test \
      --ram 4096 \
      --vcpus 2 \
      --disk size=20 \
      --location /path/to/Fedora-Everything-netinst-x86_64-Rawhide.iso \
      --extra-arg "inst.updates=http://your-host:port/updates.img" \
      --extra-arg "inst.webui.remote"

```

**This is a proof of concept, not production-ready code.** The PIN is hardcoded to 1234, there’s no TLS, and single-connection enforcement isn’t in place yet. Don’t use this for real installations – it’s meant to show the direction and let you poke at the approach. Once the installer boots, point a browser at the VM’s IP and enter 1234 on the login page. It’s rough, but it runs.

### What We Want to Hear From You

We’re sharing this now because some of these decisions are hard to unwind once the feature ships, and community input is more useful now than after the fact. A few things we’re genuinely thinking about:

Remote installation is opt-in – you enable it through boot options or kickstart. But here’s a question we’re genuinely considering: should we ship a lightweight boot ISO without a local browser, with remote installation enabled by default? A minimal image aimed at headless and network install scenarios, where the assumption is that you’re connecting from another machine. Would that be useful to you? And if you’re using VNC or RDP for remote installation today, would this replace them? What would it need to do that it doesn’t yet?

Come talk to us on [Matrix (#anaconda:fedoraproject.org)][4], or leave a comment on this article. You can also follow the work on the [anaconda-webui GitHub repo][5]. We’re looking forward to hearing from you.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/web-based-remote-installation-for-fedora-linux-heres-what-were-building/

作者：[Bruno Ciconelle][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/bciconelle/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/06/web_remote_installation-816x345.jpg
[2]: https://osbuild.org/
[3]: https://github.com/rhinstaller/anaconda-webui/pull/1274
[4]: https://chat.fedoraproject.org/#/room/#anaconda:fedoraproject.org
[5]: https://github.com/rhinstaller/anaconda-webui
