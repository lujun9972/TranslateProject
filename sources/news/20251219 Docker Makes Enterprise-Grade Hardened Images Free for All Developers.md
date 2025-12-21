[#]: subject: "Docker Makes Enterprise-Grade Hardened Images Free for All Developers"
[#]: via: "https://itsfoss.com/news/docker-hardened-images-open-sourced/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Docker Makes Enterprise-Grade Hardened Images Free for All Developers
======

[![Warp Terminal][1]][2]

[Docker][3] is the platform that [made containers mainstream][4]. It lets developers package applications with dependencies into standardized units that run consistently across different environments.

Earlier this year, they launched [Docker Hardened Images][5] (DHI), a collection of secure, minimal container images. These images include complete Software Bill of Materials (SBOM), SLSA Build Level 3 provenance, and transparent vulnerability reporting.

But DHI **was previously enterprise-only**. Docker has now [made it free and open source][6].

### DHI for Everyone

The images are released under [Apache License 2.0][7], with hardened versions of popular images built on **Alpine** and **Debian** freely available. According to Docker, these images have **up to 95% smaller attack surfaces** compared to standard images.

Alongside this, they also released **Hardened MCP Servers** for AI applications. The [MCP][8] servers include hardened versions for MongoDB, Grafana, GitHub, and other commonly used services.

Moreover, **Docker now offers DHI in three tiers**. The **free open source version** gives everyone access to hardened images with SBOM and provenance.

**DHI Enterprise** adds a 7-day [SLA][9] for critical CVE remediation, [FIPS][10]-enabled images, [STIG][11]-ready configurations, and image customization. With this, organizations can modify images, add certificates, and build on Docker's infrastructure while maintaining compliance.

**DHI Extended Lifecycle Support** (ELS) is a paid add-on for the above that extends security patches up to five years beyond upstream _end-of-life_. This addresses the problem of maintaining legacy systems that still need security updates after official support ends.

Announcing this move, [Christian Dupuis][12], Senior Principal Engineer at Docker, added that:

> Today’s announcement marks a watershed moment for our industry. Docker is fundamentally changing how applications are built-secure by default for every developer, every organization, and every open-source project.

> This moment fills me with pride as it represents the culmination of years of work: from the early days at Atomist building an event-driven SBOM and vulnerability management system, the foundation that still underpins Docker Scout today, to unveiling DHI earlier this year, and now making it freely available to all.

You can get started with Docker Hardened Images at the [official portal][13] ( _needs an account_ ). For the source, visit [GitHub][14], and for instructions, check the [documentation][15].

[Docker Hardened Images (GitHub)][14]

* * *

**Suggested Read 📖:** [The First Rust CVE in Linux Kernel][16]

![][17]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/docker-hardened-images-open-sourced/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.docker.com/
[4]: https://linuxhandbook.com/courses/docker/
[5]: https://www.docker.com/products/hardened-images/
[6]: https://www.docker.com/blog/docker-hardened-images-for-every-developer/
[7]: https://www.apache.org/licenses/LICENSE-2.0
[8]: https://modelcontextprotocol.io/docs/getting-started/intro
[9]: https://en.wikipedia.org/wiki/Service-level_agreement
[10]: https://en.wikipedia.org/wiki/Federal_Information_Processing_Standards
[11]: https://en.wikipedia.org/wiki/Security_Technical_Implementation_Guide
[12]: https://www.linkedin.com/in/christiandupuis/
[13]: https://hub.docker.com/hardened-images/catalog
[14]: https://github.com/docker-hardened-images
[15]: https://docs.docker.com/dhi/get-started/
[16]: https://itsfoss.com/news/first-linux-kernel-rust-cve/
[17]: https://itsfoss.com/content/images/icon/android-chrome-512x512-137.png
