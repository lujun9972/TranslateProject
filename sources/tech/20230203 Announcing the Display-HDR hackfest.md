[#]: subject: "Announcing the Display/HDR hackfest"
[#]: via: "https://fedoramagazine.org/announcing-the-display-hdr-hackfest/"
[#]: author: "Carlos Soriano https://fedoramagazine.org/author/csoriano/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing the Display/HDR hackfest
======

![][1]

Graphics by Jakub Steiner (Free license, no copyright)

Hi all,

This is Carlos Soriano, Engineering Manager at the GPU team at Red Hat. I’m here together with Sebastian Wick, primary HDR developer at Red Hat, and Niels de Graef, GPU team Product Owner at Red Hat, to announce that we’re organizing the [Display/HDR hackfest][2] in Brno in the Czech Republic, April 24-26! The focus will be on planning and development of the technical infrastructure needed for various display technologies, specifically those that need GNOME Shell to work in tandem with the GPU stack. One of the main examples of this is HDR support, which we know you have all been waiting for!

### Details

The purpose of the hackfest is to bring together contributors from across the display/GPU stack. Attendees will include those from projects such as Freedesktop, GNOME, KDE, Mesa, Wayland and the Linux kernel. This is going to be a great opportunity to meet and collaborate on the holistic approach necessary to make these technologies work well across various vendors and projects. 

The proposed length of the hackfest is 2 full days, and a third day for wrapping up during the morning and doing a local activity during the afternoon.

Now, you might be asking why are these technologies, such as HDR, important for us? And what is the plan to integrate them in Fedora? Well, let’s take HDR as a primary example, and start by explaining what HDR is.

### What is HDR? – By Sebastian Wick

When most people talk about High Dynamic Range (HDR) they often refer not only to HDR but also to Wide Color Gamut (WCG). Both of these terms describe an improvement of display technologies.

The dynamic range of a display describes the ratio of the lowest luminance to the highest luminance it can produce at the same time. A high dynamic range thus means an increase in the highest luminance (colloquially called brighter whites) or a decrease of the lowest luminance (darker blacks), or both.

The color gamut of a display describes the colors it is able to reproduce. If a gamut is “wide”, it means the display is able to reproduce more chromaticities compared to a small gamut. To put it colloquially, it can show more colors.

We humans are able to perceive images which have up to a certain dynamic range and color gamut. The closer displays get to those capabilities the more immersive the resulting images are. HDR, in its broader meaning, is therefore all about being able to show more colors, and we can use HDR modes on displays to unlock their full potential.

From a technical perspective, enabling those modes and presenting content is not hard, as long as the display only has to show a single source. While this may work for some use cases, a general purpose desktop requires composition of various [Standard Dynamic Range (SDR)][3] signals, color managed SDR signals and various HDR signals to various SDR displays, color managed displays and HDR displays at the same time. You can take a look at [Apple’s EDR concept][4] if you want to see how this looks when done right.

There are no industry standards yet for this kind of composition and most HDR modes, unfortunately all the common modes, are also not designed for this use case. Instead they focus on presenting a single HDR source.

With the increase in composition complexity, offloading the composition and achieving a zero-copy direct-scanout scenario becomes much harder. But this is required to keep power consumption in check and thus improve battery life.

### Wow, that sounds complex

Yeah, this all sounds more complex than someone could imagine, but we’re confident we can get there. Now, why is HDR important for us, and what is our plan for integrating it in Fedora once it is ready? Niels de Graef has been working as the primary HDR feature owner at Red Hat for a couple of months now and can help us understand that.

### Why is HDR important for us, and what is our plan for integrating it in Fedora? – By Niels de Graef

By adding support for HDR, we want to be an enabler for several key groups.

On one hand, we want to support content creators who see HDR as a very interesting feature. It allows them to present their work to people the way they intend it to be seen, eliminating the effect of “washed down” colors due to the monitor only supporting a relatively small color space. For example: as an artist, you might want to specify exactly how bright the sun in a desert scene should look while making sure the rest of the scene does not degrade in detail.

As content creators go, an important stakeholder is the VFX industry, which consists of big players like Disney. Red Hat closely collaborates with the industry, which also [recommends][5] Red Hat Enterprise Linux (RHEL) as their choice of distribution. We want to make certain we get the industry’s feedback so we can incorporate it in this story and make sure we get this right from the start.

On the other hand, we want to enable Linux _users_. Hardware that supports HDR is becoming more commonplace and is becoming more affordable as of late. HDR is becoming more supported, and an increasing amount of content is making use of it. As long as we don’t have HDR support, Linux users will have a degraded experience compared to Windows and Mac users.

Finally, supporting HDR fits into the [foundations of Fedora][6], where we want to do the right thing, making sure everyone is free to enjoy the latest innovations and features. This follows our move to Wayland, which, as a modern graphics stack, allows us to build new features like this.

### Wrapping up

We hope that you enjoy the work we’re doing to enable the Linux ecosystem and users to make use of the latest technologies. We’re definitely excited with what we are aiming to achieve. Thanks to everyone who is contributing to this effort, and the organization of the hackfest.

We hope to see you all in Brno in April!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-the-display-hdr-hackfest/

作者：[Carlos Soriano][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/csoriano/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/HDR-Display_Hacker_fest-816x345.jpg
[2]: https://wiki.gnome.org/Hackfests/ShellDisplayNext2023
[3]: https://en.wikipedia.org/wiki/Standard-dynamic-range_video
[4]: https://prolost.com/blog/edr
[5]: https://drive.google.com/file/d/12k-YZVHuxJs0LVKH_l6l9nf_qcYLfaLJ/view
[6]: https://docs.fedoraproject.org/en-US/project/
