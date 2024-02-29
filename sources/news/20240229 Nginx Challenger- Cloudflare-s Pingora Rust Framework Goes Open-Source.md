[#]: subject: "Nginx Challenger? Cloudflare's Pingora Rust Framework Goes Open-Source"
[#]: via: "https://news.itsfoss.com/cloudflare-pingora/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Nginx Challenger? Cloudflare's Pingora Rust Framework Goes Open-Source
======
A new tech takes aim at Nginx, now that it's open-source. So, is it
better? What do you think?
Cloudflare is a popular name in the web industry. Over the years, it has grown to great heights by providing various services ranging from content delivery networks, DDoS mitigation, to providing a [free privacy-friendly replacement][1] to the annoying CAPTCHA system.

Back in September 2022, they [unveiled][2] a new HTTP [proxy server][3] called Pingora, brought in to replace their existing Nginx-powered infrastructure, with plans to open-source it.

A few years have passed since, and Cloudflare has finally made good on their claim by making Pingora open-source.

Let's see what they have to offer:

**Suggested Read** 📖

![][4]

### Pingora: What to Expect?

![][5]

Released under [Apache License version 2.0][6], Pingora is Cloudflare's **Rust-based** async multithreaded framework that allows them to build HTTP proxy services with ease at scale.

They claim that Pingora has already handled “ _nearly a quadrillion Internet requests_ ” across their global networks, and that **they are open-sourcing Pingora in a bid for a better, more secure internet** that expands beyond just their infrastructure.

To further Pingora's adoption, they are collaborating with the [Internet Security Research Group][7] (ISRG) and the [Prossimo project][8] so that the most critical Internet infrastructure out there can take advantage of it.

You are maybe wondering; **why ditch** [**Nginx**][9] **?**

Well, **Cloudflare had to switch from Nginx owing to the glaring issues** it had when they began to grow. The need for a modern, faster, and memory safe alternative to Nginx was the need of the hour back then.

That is when Cloudflare stepped up and started developing their own solution in the form of Pingora. When they introduced it to the public, they showed how it was better than their old service, which was based on Nginx equipped with various fixes and workarounds.

On production loads, **Pingora was able to consume 70% less CPU and 67% less memory** with the same traffic load compared to their previous implementation. They also found that Pingora could handle HTTP requests faster than their Nginx-based service.

Not just the performance gains, and memory-safety features of Rust, Pingora also comes with libraries that are post-quantum secure. So, plenty of benefits!

💡

Nginx handles web requests using a multiprocess approach, and Pingora handles it using multithreading. This gives an edge to the Cloudflare's solution.

### Want to check it out?

Before you do, keep in mind that Pingora is a library and toolkit that Cloudflare says is **in the early stages of development** , and is still yet to have a 1.0 release.

They also say that **they cannot guarantee the stability of the API** and they will be constantly introducing changes to improve it, with **support for non-Unix operating systems not planned** as of now.

For those who were looking for a ready-made web service solution that they could just plop into their existing infrastructure will have to wait, as it will take some time for the collaboration between ISRG and Cloudflare to bear results.

You can find source code for Pingora on its official [GitHub repo][10] to experiment with it. The repo consists of libraries and APIs that can be used to build services on top of _HTTP/1_ , _HTTP/2_ , _TLS_ , and _TCP_ / _UDP_.

[Pingora (GitHub)][10]

If you are interested in contributing to the code, you also check out the [contribution guide][11] and the [issue tracker][12].

For more details about how Pingora works, and the technical details, I strongly suggest you give the [announcement blog][13] a read.

_💬 What do you think? The good-old Nginx to be replaced with Pingora in the near future? Share your thoughts in the comments._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/cloudflare-pingora/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/cloudflare-captcha-replacement/
[2]: https://blog.cloudflare.com/how-we-built-pingora-the-proxy-that-connects-cloudflare-to-the-internet/
[3]: https://en.wikipedia.org/wiki/Proxy_server
[4]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[5]: https://news.itsfoss.com/content/images/2024/02/Pingora_Banner.jpg
[6]: https://www.apache.org/licenses/LICENSE-2.0
[7]: https://www.abetterinternet.org/
[8]: https://www.memorysafety.org/
[9]: https://www.nginx.com/
[10]: https://github.com/cloudflare/pingora
[11]: https://github.com/cloudflare/pingora/blob/main/.github/CONTRIBUTING.md
[12]: https://github.com/cloudflare/pingora/issues
[13]: https://blog.cloudflare.com/pingora-open-source
