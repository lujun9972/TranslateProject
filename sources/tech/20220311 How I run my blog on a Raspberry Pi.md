[#]: subject: "How I run my blog on a Raspberry Pi"
[#]: via: "https://opensource.com/article/22/3/run-drupal-raspberry-pi"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I run my blog on a Raspberry Pi
======
I set up a Raspberry Pi to act as a web server to host my personal blog
on Drupal.
![Raspberries with pi symbol overlay][1]

Like a lot of folks who enjoy tinkering with technology, I now have a small but growing collection of Raspberry Pi boxes around my house. I've used them for various projects: A PiHole network ad blocker, an OctoPi 3D print server, and a Minecraft server, among others.

However, the most custom project I've done is setting up a Raspberry Pi to act as a web server to host my own blog site, mandclu.com. I got the idea while researching for an interview I did a couple of years ago.

The project has evolved significantly since it started, so I thought it would be interesting to share.

### Why run my own web server?

I started building websites a little over two decades ago. I used various hosting solutions at that time, including a (nearly) bare-metal Linode instance where I had to install and configure all the software myself.

I recently had a small account at a major hosting company that I used to serve a couple of personal projects. Over time, I've found that I'm less interested in using my time for freelance projects, so the cost was getting harder to justify. Because of the security measures built into their hosting platform, I also felt frustrated being limited by what tools I could use and how I could use them.

In short, I wanted to run my own server because it would be free, in the sense of free speech, free beer, and, as I would soon learn, free puppies.

Would I recommend that everyone host their own website? Absolutely not. It's been a fun project, and I've learned a ton along the way, but if my website was down for a few hours (or potentially longer) because of local power or network outage, I could live with that.

In a [previous article][2], I discussed why I chose Drupal for my site. While I think it's a powerful and infinitely flexible solution, the steps below largely apply to any PHP-based CMS or development framework you might want to host.

### A Raspberry Pi web server: The maiden voyage

I bought a Raspberry Pi 4 with 4Gb of RAM for the project. I had seen some documentation that the quality of the MicroSD card you use with a Pi makes a significant difference for performance, so I also tried to source a decent card. All told, I was probably getting close to US$ 100, including a case and power adapter.

The first decision was what OS to use. CentOS seemed like the best choice for something exposed to the internet, so I decided to go with that. As it turns out, CentOS had some marked differences from any other flavor of Linux I've used, especially because it wanted to reset the permissions of all the server logs on every reboot. I eventually figured out how to handle that gracefully, but it added to the adventure.

Next, it was time to get the Pi set up to act as a web server. I know some super-smart DevOps folks who prefer to use Nginx as a web server for their projects, but I'm personally a lot more familiar with Apache. Also, Drupal implements some security controls using `.htaccess` files, so if going with Nginx, you would need to manage equivalent restrictions in the server configuration. But the truth is that more than anything else, I wanted to go with the devil I knew.

Fortunately, a quick search can bring up a variety of tutorials on how to install the remaining parts of a LAMP stack on CentOS (or your preferred flavor of Linux). Even better, modern package managers like Yum make the process relatively painless. Drupal also has a few [PHP requirements][3] of its own, so there was an extra step to make sure I met those. Finally, I like to use [APCu][4] as a PHP-native data cache to help speed up the delivery of PHP sites, so I made sure that it got installed and the PHP extension enabled.

While searching for answers for the miscellaneous hiccups, I came across an interesting add-on that made managing the Pi as a web server much easier: [Cockpit][5]. It provides an easy-to-use graphical interface to see the status of the machine and all its software: How it's running (or if it isn't). You can see when updates are available and run them, access logs, and more. It even includes its own command-line interface, so you can completely manage pretty much everything from the one interface.

![Cockpit UI][6]

(Martin Anderson-Clutz, [CC BY-SA 4.0][7])

### Installing Drupal on Raspberry Pi

Getting Drupal itself installed is pretty straightforward if you know the intended process. If you haven't already, [install the Composer PHP dependency manager][8]. Then you can install Drupal in a couple of steps:


```
`composer create-project drupal/recommended-project my_site_name_dir`
```

Configure your web server to use the web directory within that install location (`my_site_name_dir` in the example above) as the document root for a [virtual host][9] (or a server block in Nginx).

If you try to access the virtual host, Drupal triggers the rest of the installation process for you.

![Drupal installer screen][10]

(Martin Anderson-Clutz, [CC BY-SA 4.0][7])

I decided to create the site on my laptop, then push the site code to a Git repo on GitLab, and pull it down to the server from there, but that isn't strictly necessary if you're just looking to try out Drupal on your Pi.

### Getting the word out (of the network)

I now had my Raspberry Pi working as a web server and my Drupal site running well on top of it. Great! But no one outside my network could access it.

I went into my router's web UI and used port forwarding to make sure incoming web requests (ports 80 and 443) would get directed to the Pi. I did that in a couple of minutes. But how would people find the site?

I bought a domain name, and my registrar had its own utility for dynamic DNS, which is great because a drawback of using your home's internet connection is that home users typically don't have a static IP. After installing their utility and waiting for the DNS setup to resolve, users could reach my new website at [mandclu.com][11].

Of course, the site also needed to allow for secure connections, so I also needed to add an SSL certificate. It used to be that this meant purchasing a certificate that would have cost more than the Pi itself and paying that again every year on renewal. Fortunately, [Let's Encrypt][12] achieves a similar result for free. You can even install the [certbot][13] to renew the certificate automatically.

### My own Raspberry Pi web server

I was really happy with the result. Was it as fast as expensive, enterprise-grade hosting? Nope. But I could host my own site for free (or, more accurately, for the cost of the electricity to power the Pi), and I had complete freedom to configure the server any way I wanted.

It did seem like the site started to show occasional slowdowns over time, but it was fast enough for the meager traffic I was getting (almost none), so it met my needs.

I enjoyed playing with the site styling and posting content when I felt inspired to write it. And then, the move came.

I moved homes at the end of 2020 (literally the last day of the year). One of the downsides of having your website hosted from a Pi box in your living room is that moving house means your website goes down for a while. In my case, a few weeks since having my pet project website back online wasn't a major priority.

Eventually, I got my web server Pi hooked up and plugged in again and was ready to add some new content. I was surprised to find that the site was running noticeably slower than I remembered. A great thing about being a web developer is that you make friends with lots of smart people, so I reached out to a friend who mentioned that MicroSD cards sometimes slow down over time under regular use.

### Speeding up my web server

I decided it was time to to rebuild the server, so I made several changes. For starters, I had since bought an 8GB Pi 4 to use as a Minecrafter server, but then my son's interest in the game had fallen off, so I decided to use that hardware for the new version. Instead of a MicroSD for storage, I bought a low-capacity NVMe SSD and a USB 3 enclosure for it. Those two elements probably cost as much as I had previously spent on the Pi, MicroSD card, power supply, and case, but the server is still running really well nearly a year later.

![Fast but ugly Pi with SSD][14]

(Martin Anderson-Clutz, [CC BY-SA 4.0][7])

Instead of just copying over everything I had previously installed, I decided to reinstall the software. Moving to the 8GB Pi 4 meant that I needed a 64-bit OS, which meant that Ubuntu server was my best option. There are more options today, but I've been really happy with Ubuntu, even though there was a new learning curve. Some directories are in different places. I had to get used to Apt instead of Yum for installing new packages, and so on. But the overall process was really the same, with a few minor differences in the steps themselves.

Another significant change I decided to make during the rebuild was to add Cloudflare as a content delivery network (CDN) to speed up the delivery of the site. In its most basic form, a CDN speeds up a website's delivery by keeping cached versions of the site's files at various local points of presence (PoP) distributed worldwide. Fortunately, Cloudflare has a [free plan][15], so I decided to put that in front of my Pi-hosted website.

### The result

The upgraded version of the Pi web server clocks in fast. Like, really fast:

![Desktop Lighthouse score][16]

(Martin Anderson-Clutz, [CC BY-SA 4.0][7])

![Mobile Lighthouse score][17]

(Martin Anderson-Clutz, [CC BY-SA 4.0][7])

I've run speed tests on many different websites (admittedly, most of them were Drupal), and these are some of the best scores I've seen. It does help that the site is simple by design. If there were more images on the site, it would probably score a little lower, especially for mobile (where the Lighthouse test throttles bandwidth to simulate a slow 4G connection).

It's worth pointing out the accessibility scores as well—with no effort on my part. Another advantage of running my site on Drupal is being able to build on top of a framework already rigorously tested to be easily used on screen readers and other assistive technologies.

The only work I had to do to hit the best practices score was installing and configuring the free [Security Kit][18] module.

### Build your own Raspberry Pi server

If you've wanted to try Drupal for a personal web project, and especially if you happen to have an extra Raspberry Pi gathering dust, then I hope you'll try setting up your own server.

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/run-drupal-raspberry-pi

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/life-raspberrypi_0.png?itok=Kczz87J2 (Raspberries with pi symbol overlay)
[2]: https://opensource.com/article/22/2/drupal-advanced-blogging-platform
[3]: https://www.drupal.org/docs/system-requirements/php-requirements
[4]: https://www.php.net/manual/en/book.apcu.php
[5]: https://opensource.com/article/21/5/raspberry-pi-cockpit
[6]: https://opensource.com/sites/default/files/pictures/the_cockpit_ui.png (Cockpit UI)
[7]: https://creativecommons.org/licenses/by-sa/4.0/
[8]: https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos
[9]: https://linuxize.com/post/how-to-set-up-apache-virtual-hosts-on-ubuntu-20-04/
[10]: https://opensource.com/sites/default/files/pictures/drupal_installer_screen.png (Drupal installer screen)
[11]: https://www.mandclu.com/
[12]: https://letsencrypt.org/
[13]: https://certbot.eff.org/
[14]: https://opensource.com/sites/default/files/pictures/the_fast_but_ugly_pi_with_an_ssd.jpeg (Fast but ugly Pi with SSD)
[15]: https://www.cloudflare.com/plans/applicationservices/#overview
[16]: https://opensource.com/sites/default/files/uploads/desktop-lighthouse-score.png (Desktop Lighthouse score)
[17]: https://opensource.com/sites/default/files/uploads/mobile-lighthouse-score.png (Mobile Lighthouse score)
[18]: https://www.drupal.org/project/seckit
