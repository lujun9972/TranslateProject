[#]: subject: "Eclipse Plans to Challenge Microsoft's VS Code Dominance With Theia Code Editor"
[#]: via: "https://news.itsfoss.com/theia-ide/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Eclipse Plans to Challenge Microsoft's VS Code Dominance With Theia Code Editor
======
A powerful open-source IDE appears.
[![][1]][2]

The [Eclipse foundation][3] is well-known for their Eclipse project, which has transformed into one of the most popular integrated development environments ([IDE][4]) around.

But, many might've forgotten that among their vast range of [projects][5], there's also the [Eclipse Theia][6] platform which was introduced back in 2017. It was meant to be a stable base to develop new IDEs, and IDE-like products for both cloud and desktop.

In a [recent announcement][7] by EclipseSource, a long-awaited cross-platform IDE based on Theia has been introduced under the “ **Theia IDE** ” name, which marks a new chapter in the development of IDEs at Eclipse.

During the launch, they added that:

> Theia IDE is not only open, flexible and powerful from a technology point of view, but it is also created by one the most successful and innovative ways of software development: a vendor-neutral open source community.

All that got you intrigued? Well, then keep on reading to see what it's all about. 😃

### Theia IDE: Overview ⭐

![][8]

Theia IDE is powered by the Language Server Protocol ([LSP][9]), the Debug Adapter Protocol ([DAP][10]), and the [Monaco Editor][11] that powers VS Code. It is being offered under the Eclipse Public License 2.0 ([EPL][12]), which allows for distribution and commercial use.

The developers also mention that **no proprietary or closed-source components have been used in Theia IDE** , touting it to be a practical option for both individuals and enterprises.

Its **development is backed by an expansive coalition of stakeholders** that include big names such as _SAP_ , _ARM_ , _Arduino_ , _Red Hat_ , _Samsung_ , etc., many of whom are also contributing to the project, taking its development forward.

If you were wondering, **the governance is being handled in a vendor-neutral way** , with a focus on open-source governance, ensuring no one entity has control over the tool, making decisions on a whim.

With that said, here are some **key features** of Theia IDE:

  * **Cloud Hostable**
  * **Highly Extensible**
  * **Telemetry Disabled by Default**



To expand on those, **Theia IDE has support for detachable views** , similar to what we see on other IDEs, and has something called a “ **dynamic toolbar** ”, that has many niceties.

![][13]

It allows users to access the most commonly used commands from the top-right of the toolbar, buttons to go back/forward in a page, and has an option to split editors towards the right-hand side.

![][14]

There's also **support for color themes** to customize the interface, with many great ones already pre-installed. As you can see above, the one called “Abyss” totally changed the way Theia looked and felt.

You can also add file icon themes to further rice up your Theia IDE experience.

![][15]

The developers also stress on the fact that telemetry is disabled by default, and when I checked, it was indeed disabled by default, with **telemetry data being sent to Red Hat servers when enabled**.

For **those who like expanding their code editor** , Theia IDE has support for four main ways of doing the same:

  * The first is by **installing Theia plugins** , which are similar to VS Code extensions, with limited access.
  * The second is by **using native Theia extensions** , which can be installed at compile time, that have full access to the internals of Theia, without any limitations.
  * The third is by **making use of headless plugins** which are simple to write and can be installed at runtime, they are meant to interact/extend only the Theia backend services.
  * The final one is by **installing VS Code extensions** , as Theia IDE has support for those. Users can also take advantage of the [Open VSX Registry][16] for downloading extensions.



**To wrap this up** , at first glance, Theia IDE appears to be a solid open-source alternative to Microsoft's [VS Code][17], and **companies looking to escape their dependence on Microsoft now have another solid replacement** to switch to.

### 📥 Get Theia IDE

The developers have made Theia IDE available on the [official website][18] for **Linux** , **Windows** , and **macOS** , with the source code being hosted over at their [GitHub][19] repo.

Before you get started with those, the [official documentation][20] is a must-read.

[Theia IDE][18]

There's also a [cloud-hosted demo][21] ( _GitHub login required_ ) of Theia IDE that users can take for a run before committing to using it in their project workflows, and the devs have mentioned that **live collaboration features are coming soon** 😁

**For those who want to build new IDEs** using the Theia platform, they can refer to [Eclipse's blog][22] on it.

_💬 Will you be giving this a try on your Linux system? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/theia-ide/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.eclipse.org/
[4]: https://en.wikipedia.org/wiki/Integrated_development_environment
[5]: https://projects.eclipse.org/
[6]: https://projects.eclipse.org/projects/ecd.theia
[7]: https://eclipsesource.com/blogs/2024/06/27/introducing-the-theia-ide/
[8]: https://news.itsfoss.com/content/images/2024/07/Theia_IDE_a.png
[9]: https://en.wikipedia.org/wiki/Language_Server_Protocol
[10]: https://microsoft.github.io/debug-adapter-protocol/
[11]: https://microsoft.github.io/monaco-editor/
[12]: https://www.eclipse.org/legal/epl-2.0/
[13]: https://news.itsfoss.com/content/images/2024/07/Theia_IDE_b.png
[14]: https://news.itsfoss.com/content/images/2024/07/Theia_IDE_c.png
[15]: https://news.itsfoss.com/content/images/2024/07/Theia_IDE_d.png
[16]: https://open-vsx.org/
[17]: https://code.visualstudio.com/
[18]: https://theia-ide.org/
[19]: https://github.com/eclipse-theia/theia
[20]: https://theia-ide.org/docs/
[21]: https://try.theia-cloud.io/
[22]: https://eclipsesource.com/blogs/2019/09/25/how-to-launch-eclipse-theia/
