[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How Open Source Is Transforming The Energy Industry)
[#]: via: (https://www.linux.com/news/how-open-source-is-transforming-the-energy-industry/)
[#]: author: (Swapnil Bhartiya https://www.linux.com/author/swapnil/)

How Open Source Is Transforming The Energy Industry
======

In this interview Swapnil Bhartiya, creator of TFiR, sat down with Shuli Goodman, Executive Director of LF Energy to discuss the role open source and the foundation is playing in helping the energy sector to embark on its own digital transformation and cloud-native journey.

_Here is a lightly edited transcript of the interview:_

**Swapnil Bhartiya: Shuli, first of all, welcome to the show once again. When we look at the energy sector – we see power lines and grids. It creates the image of an ancient system to move electrons and protons from one place to another. Are we still talking about the same power lines and grids or we’re also talking about a modern infrastructure?**

Shuli Goodman: Well, we’re definitely talking about modern infrastructure. One of the defining features of the grid that we’re moving from is you have centralized energy generation that is being pushed out over high voltage to distribution systems. We lose nearly 60% of the electrons. There’s a tremendous opportunity for optimization and being able to reduce the amount of electron loss.

The digitalization of energy, in terms of the metadata and the data, enables system operators to be able to work much more effectively. It’s going to be critical in ensuring that we actually are able to balance supply and demand in a different way than we’ve been balancing supply and demand for the last 150 years.

**Swapnil Bhartiya: What role is LF Energy playing in helping address these problems?**
Shuli Goodman: We’re at the beginning of a period of accelerated innovation, which will be addressing these issues. The Digital Substation project, for example, is addressing the ability to have torrents of data being managed from the edge, and to be able to provide grid intelligence out at the edge, and have a mechanism for being able to bring that in and then to be able to orchestrate, choreograph, and to even have control or shared control mechanisms that enable us to manage the grid.

What we’re working on now is blocking and tackling at a very fundamental level. You have utilities who have always thought of themselves as hardware guys – dealing with power lines. It’s been a very manual, highly intensive industry.

We are moving towards network operators, almost carriers like approach. Kind of an amalgamation of electricity, telecommunications and the internet. This whole new process of being able to orchestrate energy and digitalization is essential in that paradigm. It could even be up to 50% of that. And then there’s other stuff that’s happening both at the chip-level and at the hardware-level that is going to enable that intelligence at the edge and the ability to choreograph that through market signals.

What we’re doing is shifting to a price-based grid coordination model. In other words, that price signals that will shift and change based on the amount of sun, or the amount of wind, or the availability of energy. We’ll actually begin getting pushed out to the edge and enable coordination between assets at the edge.

**Swapnil Bhartiya: You mentioned the Digital Substation Project. Tell us more about it.**

Shuli Goodman: So, for those of you who are watching, who’ve been along the journey with LF Networking or have seen what’s happened with 5G, the revolution of 5G was the virtualization and the dis-aggregation. The shift from purely hardware-centric to really moving to 75% virtualization.

The Digital Substation, the DSAS project, is an umbrella of four different projects that are addressing the digitalization at the substation. The Substation is the critical infrastructure that separates high, medium, and low voltage between the generation and then moving it, stepping it down before it goes out into your house. I refer to them as edge node routers, which may or may not be exactly the right term, but we’re moving into a territory where we’re inventing things.

I think of the edge node and the DSAS project is really about virtualizing hardware, abstracting the complexity of hardware and software so that we begin to have really software-defined environments. And perhaps in the future, we’ll have increasingly software-defined substations, transformers. All kinds of things that we considered to be de facto the standard today, may in fact move more and more towards software-defined. And the DSAS project is really the start of that.

**Swapnil Bhartiya: What kind of collaboration is there around DSAS?**

Shuli Goodman: It’s a great project. It really started with [RTE][1]. Last summer we had a series of meetings and we opened it up to all of the OEMs, vendors, suppliers, such as, GE, ABB, Schneider Electric and all the network operators, utilities all over the world that wanted to participate.

We have a core group, from RTE, France, and then we have Alliander and TenneT, which are the distribution and the transmission system operators in the Netherlands. TenneT also operates in Germany. We have General Electric, which is driving it from a vendor, OEM perspective. And then Schneider Electric is also participating, and we hope that others will join us.

**Swapnil Bhartiya: You also have something called CoMPAS or Configuration Modules for Power Industry Automation System. What is that?**

Shuli Goodman: So, CoMPAS is the first of the four projects in the DSAS umbrella. It’s essentially a configuration model. One of the problems that end-users – the utilities – have is that when they think about their portfolio of hardware and software there are tremendous interoperability challenges. 61850, which is an IEC Standard, was created precisely in order to facilitate interoperability. The [CoMPAS][2] project is leveraging 61850 to enable interoperability between various different vendors so that we can have a more heterogeneous environment for things like a substation. There are millions of substations on the planet so any single player managing at the transmission level could be managing thousands of these. And if you are at the distribution level, you would be managing many thousands of thousands.

So if you don’t have that interoperability, then you have vendor lock-in. And if you have vendor lock-in, it’s not just that it’s bad for the utility, it’s also really bad for the OEM, because it slows innovation. It keeps the vendor and the supplier sort of focused on a portfolio as opposed to really looking ahead. Right now, solving this interoperability problem is ground zero, and that’s where CoMPAS comes in.

**Swapnil Bhartiya: How has Open Source made your life easier to not only convince these stakeholders, these players, to collaborate with each other but also to innovate at a much faster rate than it would take traditional companies to do in a proprietary manner?**

Shuli Goodman: So, if just for a moment, you just imagined in your mind, a pie, and each of the wedges in the pie represented parts of the stack that you need to build and support in order to go to market. What Open Source does is it allows us to identify what are the commodity parts of that pie, and can we agree on working on those together. That then frees up engineers and resources and facilitates interoperability. It does really great things to accelerate innovation because instead of, let’s say, Siemens, GE, ABB or Schneider Electric, putting in 30% of their resources to supporting the 61850 integration, or something like that, they can put in a quarter of those engineers and then relocate those resources somewhere else. The same thing is true with the utilities, because, for the most part, utilities have given responsibility for their network operations at a digital level.

Vendors need to become Digital Native and Cloud Native, because to get to where we need to go, it is going to be so digitally intensive, perhaps 50% of the problem is going to be digital. So, we need to really build that capacity.

--------------------------------------------------------------------------------

via: https://www.linux.com/news/how-open-source-is-transforming-the-energy-industry/

作者：[Swapnil Bhartiya][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linux.com/author/swapnil/
[b]: https://github.com/lujun9972
[1]: https://www.linkedin.com/pulse/europes-two-largest-tsos-discuss-open-source-joining-goodman-ph-d-/
[2]: https://www.lfenergy.org/projects/compas/
