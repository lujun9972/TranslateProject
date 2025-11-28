[#]: subject: "Self-Hosting is Rising and Linux Users are Leading This Revolution"
[#]: via: "https://itsfoss.com/self-hosting-rising/"
[#]: author: "Theena Kumaragurunathan https://itsfoss.com/author/theena/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Self-Hosting is Rising and Linux Users are Leading This Revolution
======

[![Warp Terminal][1]][2]

In a previous column, I argued that [self-hosting is resistance][3] in an age where ownership is increasingly illusory.

There is increasing [evidence][4] that self-hosting is becoming popular among a certain kind of user, say the typical readership of ItsFoss.

There is a simple explanation for this shift: people want their data, dollars, and destiny back. Centralized platforms optimized for engagement and extraction are colliding with real-world needs — privacy, compliance, predictability, and craft. Linux, containers, and a flood of polished open-source apps have turned what used to be an enthusiast’s project into a practical step for tech‑savvy users and teams.

The demand and supply of self-hosting is headed in the [right direction][5].

### The Economics of Self-Hosting

![Photo by Chris Briggs / Unsplash][6]

I spoke about the demand side of the equation in [a preivous column][3]. Today, I would like to talk about the supply side.

Put simply, self-hosting got easier: Dockerized services, one‑click bundles, and opinionated orchestration kits now cover mail, identity, storage, media, automation, and analytics. And the hardware needed is trivial: a mini‑PC, a NAS, or a Pi can host most personal stacks comfortably.

![Click and deploy OS and interfaces make it so easy][7]

An increasing portion of these users are also conscious of the environmental impact of unchecked consumerism: recycling older hardware for your home-lab is an easy way to ensure that you aren't contributing to mountainous e-waste that pose risks to communities and the environment.

The numbers reinforce the vibe. The [2025 selfh.st community survey][8] (~4081 respondents) shows more than four in five self‑hosters run Linux, and Docker is the dominant runtime by a wide margin. While this hasn't become mainstream yet, it highlights one of my arguments: there are costs to trusting big tech with your most important data and services, financial and otherwise. Once such costs outweigh the costs of self-hosting, once the vast majority of users can no longer deny such costs are draining their wallets and their sense of agency, we can expect this shift to become mainstream.

### Self-Hosting is Independence from Big Tech

![Photo by Jonathan Borba / Unsplash][9]

  * When your calendar, contacts, photo library, and documents sit on your own box behind your own reverse proxy, you remove third‑party analytics, shadow data enrichment, and surprise policy drift. You also reduce the surface area for “account lockouts” that nuke access to life‑critical records. [For users][10] burned by sudden platform changes — forced accounts, feature removals, data portability barriers—self ‑ hosting is an antidote.
  * Cost predictability over time. Cloud convenience is real, but variable charges accumulate as you scale storage, bandwidth, and API calls. With self‑hosting, you pay upfront (hardware + power), then amortize. For steady, continuous workloads—backups, photo libraries, media servers, home automation, docs, password vaults—the math is often favorable.
  * Reliability through ownership. Services die. Companies pivot. APIs change. By running key utilities yourself — RSS, password vaults, photo libraries, file sync, smart‑home control — you guarantee continuity and can script migrations on your timeline. That resilience matters when consumer vendors sunset features or shove core capabilities behind accounts and subscriptions.
  * Curiosity and capability‑building. There’s a practical joy in assembling a stack and knowing how each layer works that I can attest. For Linux users, self‑hosting is an ideal next step: you practice containerization, networking, monitoring, backups, and threat modeling in a low‑risk environment.



### The Linux‑first baseline

![Photo by Hc Digital / Unsplash][11]

Linux dominates self‑hosting because it’s stable, well‑documented, and unfussy (in the context of servers; I am aware Linux desktop has some ways to go before mainstream users will flock towards Linux).

Package managers and container runtimes are mature. Community tutorials cover everything from Traefik/Caddy reverse proxies to WireGuard tunnels and PostgreSQL hardening. The selfh.st survey shows Docker adoption near 90 percent, with Proxmox, Home Assistant OS, and Raspberry Pi OS widely used. It’s not gatekeeping; it’s pragmatism. Linux is simply the easiest way to stitch a small, reliable server together today.

### Where the rubber meets the road

Most start with a single box and a few services: identity and secrets (Vaultwarden, Authelia, Keycloak); files and backups (Nextcloud, Syncthing, Borgmatic); media (Jellyfin, Navidrome, Photoprism/Immich); home (Home Assistant); networking (Nginx/Traefik/Caddy, WireGuard); knowledge (FreshRSS, Paperless‑ngx, Ghost). The payoff is a system where each function is yours.

### AI is accelerating the trend

![][12]

[Self‑hosted AI][13] moved from novelty to necessity for teams with sensitive workloads. Local inference avoids model‑provider data policies, reduces latency, and stabilizes costs. Smaller models now run on consumer hardware; hybrid patterns route easy requests locally and escalate only high‑uncertainty tasks to cloud. For regulated data, self‑hosting is often the only sane route.

### The economics are getting clearer

“Is self‑hosting cheaper?” depends on workload shape and rigor. Cloud Total Cost of Ownership (TCO) includes convenience and externalized maintenance; self‑hosting TCO includes your time, updates, and electricity. But for persistent, predictable personal workloads—photo/video storage, backups, calendars, private media—self‑hosting tends to win.

### What self‑hosting doesn’t fix

  * You still need to operate. Patching, backups, monitoring, and basic security hygiene are on you. Automated update pipelines and off‑site backups reduce pain, but they require setup and discipline. ​
  * Internet constraints exist. Residential ISPs throttle uploads or block SMTP; dynamic IPs complicate inbound routes; power outages happen. In practice, most personal stacks work fine with dynamic DNS, tunneling, and a small VPS for exposed services, but know your constraints. ​⁠
  * Some services are better bought. Global‑scale delivery, high‑throughput public sites, and compliance‑heavy email sending can be more efficient with a trustworthy provider. “Self‑host everything” isn’t the point—“self‑host what’s sensible” is.



### The cultural angle

**Self‑hosting isn’t anti‑cloud; it’s pro‑agency.** It’s choosing the right locus of control for the things you care about. For FOSS communities, it’s consistent with the ethos: own your stack, contribute upstream, and refuse enshittification through slow, patient craft. For Linux users, it’s the obvious next rung: turn your knowledge into durable systems that serve people you love, not just platforms that serve themselves.

If you value predictability, privacy, and the quiet confidence of owning the tools you rely on, self‑hosting stops being a hobby and starts being common sense. The shift is already underway. It’s not loud. It’s steady. And Linux is where it happens.

--------------------------------------------------------------------------------

via: https://itsfoss.com/self-hosting-rising/

作者：[Theena Kumaragurunathan][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/theena/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/digital-content-ownership-illusion/
[4]: https://arstechnica.com/gadgets/2025/05/self-hosting-is-having-a-moment-ethan-sholly-knows-why/
[5]: https://www.marketresearchfuture.com/reports/homelab-market-21555
[6]: https://images.unsplash.com/photo-1587403335644-fa8fef06b261?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDQ1fHxlY29ub21pY3N8ZW58MHx8fHwxNzY0MzE0Mzc2fDA&ixlib=rb-4.1.0&q=80&w=2000
[7]: https://itsfoss.com/content/images/2025/11/image-54.png
[8]: https://linuxiac.com/self-hosters-confirm-it-again-linux-dominates-the-homelab-os-space/
[9]: https://images.unsplash.com/photo-1667543241882-962c812ff19e?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDN8fGFsZXhhfGVufDB8fHx8MTc2NDMxNDU2MXww&ixlib=rb-4.1.0&q=80&w=2000
[10]: https://itsfoss.com/p/d2f53e9d-4422-4ab9-865b-abf5b2030a9b/%E2%80%8B%E2%81%A0https://romanzipp.com/blog/why-a-homelab-why-self-host
[11]: https://images.unsplash.com/photo-1575677935416-510b781932af?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDIyfHxwZW5ndWluc3xlbnwwfHx8fDE3NjQzMTQ2MTl8MA&ixlib=rb-4.1.0&q=80&w=2000
[12]: https://itsfoss.com/content/images/2025/11/image-55.png
[13]: https://itsfoss.com/ollama-setup-linux/
