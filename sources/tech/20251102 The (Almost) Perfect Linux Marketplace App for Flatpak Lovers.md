[#]: subject: "The (Almost) Perfect Linux Marketplace App for Flatpak Lovers"
[#]: via: "https://itsfoss.com/bazaar-app/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The (Almost) Perfect Linux Marketplace App for Flatpak Lovers
======

[![Warp Terminal][1]][2]

Do we need a separate, dedicated software center application for [Flatpaks][3]? I don't know and I don't want to go in this debate anymore. For now, I am going to share this new marketplace that I have come across and found intriguing.

[Bazaar][4] is a modern Flatpak app store designed with GNOME styles. It focuses on discovering and installing Flatpak apps, especially from Flathub. In can se you did not know already, bazaar means market or marketplace. A suitable name, I would say.

![][5]

### Bazaar: More than just a front end for Flathub

As you'll see in the later sections, Bazaar is not perfect. But then nothing is perfect in this world. There are scopes for improvement but overall, it provides a good experience if you are someone who frequently and heavily use Flatpaks on GNOME desktop. There is a [third-party KRunner plugin for KDE Plasma users][6].

Let's explore this Bazaar and see what features it offers. If you prefer videos, you can [watch its features in our YouTube video][7].

[Subscribe to It's FOSS YouTube Channel][8]

#### Apps organized into categories

Like GNOME software, several app categories are available in Bazaar. You can find them on the homepage itself. If you are just exploring new apps of your interest, this helps a little.

![App categories][9]

#### Search and install an app

Of course, you can search for an application, too. Not only you can search with its name, you can also search for its type. See, Flathub allows tagging apps and this helps 'categorizing' apps in a way. So if you search for text editor, it will show the applications tagged with text editor.

![Search Apps][10]

When you hit the install button, you can see a progress bar on the top-right. Click on it to open the entire progress bar as a sidebar.

![Progress bar][11]

It shows what items and runtimes are being installed. You can scroll down the page of the package to get more details, screenshots of the project, and more.

#### Accent colors

The progress bar you saw above can be customized a little. Click the hamburger menu to access preferences and then go to the Progress Bar section. You'll find the options to choose a theme for the progress bar. These themes are accent colors represent LGBTQ and their sub-catrgories.

![Progress bar style settings][12]

You can see an Aromantic Flag applied for the progress bar in the screenshot below.

![Progress bar style applied][13]

#### Show only open source apps

Flathub has both open source and proprietary software available. The licensing information is displayed on an individual application page.

![Non-free apps in search result][14]

Now, some people don't want to install proprietary software. For them, there is the option to only show open source software in Bazaar.

You can access this option by going to preferences from the hamburger menu and toggle on the button, "Show only free software".

![Show only free software settings][15]

📋

Repeated reminded. [Free in FOSS means free as in freedom][16], not free as in beer.

Refresh the content using the shortcut `CTRL + R` and you should not see proprietary software anymore.

![No non-free software in results][17]

#### Application download statistics

In an app page, you can click on the _Monthly Downloads_ section to get a chart view and a map view.

![][18]

The map view shows the download per region of that app.

![Download per location][19]

The chart view gives you an overview of the download stats.

![Download overview chart][20]

Other than that, if you click on the download size of an application in the app page:

![Click on download size][21]

You can see a funny download size table, comparing the size of the Flatpak applications with some facts.

![Funny download size chart][22]

#### Easily manage addons

Some apps, like OBS Studio, have optional add-on packages. Bazaar indicates the availability of add-ons in the Installed view. Of course, the add-ons have to be in Flatpak format. This feature comes from Flathub.

![][23]

When you click the add-ons option, it will show the add-ons available for installation.

![Manage add-ons][24]

### Removing installed Flatpak apps

You can easily remove installed Flatpak apps from the Installed view.

![Remove applications][25]

This view shows all the installed Flatpak packages on your system, even the ones you did not install via Bazaar.

#### More than just Flathub

By default, Bazaar includes applications from Flathub repository. But if you have added additional remote Flatpak repositories to your system, Bazaar will include them as well.

It's possible that an application is available in more than one remote Flatpak repositories. You can choose which one you want to use from the application page.

![Select an installation repository][26]

Although, I would like to have the ability to filter applications by repositories. This is something that can be added in the future versions.

### Installing Bazaar on Linux

No prizes for guessing that Bazaar is available as a Flatpak application from Flathub. Presuming that you have already added Flathub remote repo to your system, you can install it quickly with this command:

```

    flatpak install flathub io.github.kolunmi.Bazaar

```

If you are using Fedora or Linux Mint, you can install Bazaar from the software center of respective distributions as well.

![][27]

### Wrapping Up

Overall, this is a decent application for Flatpak lovers. There is also a 'curated' option available for distributors. Which means if some new distros want to package Bazaar as ist software center, they can have a curated list of applications for specific purpose.

Is it worth using it? That is debatable and really up to you. Fedora and Mint already provide Flatpak apps from their default software center. This could, however, be a good fit for obscure window managers and DEs. That's just my opinion and I would like to know yours. Please share yours in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/bazaar-app/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/what-is-flatpak/
[4]: https://github.com/kolunmi/bazaar
[5]: https://itsfoss.com/content/images/2025/11/bazaar-flatpak-app.png
[6]: https://github.com/ublue-os/krunner-bazaar
[7]: https://www.youtube.com/watch?v=Pod_KQE7VIU
[8]: https://www.youtube.com/@itsfoss
[9]: https://itsfoss.com/content/images/2025/11/bazaar-app-categories.png
[10]: https://itsfoss.com/content/images/2025/10/bazaar-search-apps.png
[11]: https://itsfoss.com/content/images/2025/10/bazaar-progress-bar.png
[12]: https://itsfoss.com/content/images/2025/10/bazaar-progress-bar-style-in-settings.png
[13]: https://itsfoss.com/content/images/2025/10/bazaar-progress-bar-style-in-action.png
[14]: https://itsfoss.com/content/images/2025/10/bazaar-non-free-app-search.png
[15]: https://itsfoss.com/content/images/2025/10/bazaar-show-only-free-apps-settings.png
[16]: https://itsfoss.com/what-is-foss/
[17]: https://itsfoss.com/content/images/2025/10/bazaar-no-spotify-in-results.png
[18]: https://itsfoss.com/content/images/2025/11/application-details-bazaar-1.png
[19]: https://itsfoss.com/content/images/2025/10/bazaar-location-download-number.png
[20]: https://itsfoss.com/content/images/2025/10/bazaar-download-chart.png
[21]: https://itsfoss.com/content/images/2025/10/bazaar-click-on-download-size.png
[22]: https://itsfoss.com/content/images/2025/10/bazaar-fun-download-size-chart.png
[23]: https://itsfoss.com/content/images/2025/11/manage-add-ons-in-bazaar-1.png
[24]: https://itsfoss.com/content/images/2025/10/bazaar-manage-addons.png
[25]: https://itsfoss.com/content/images/2025/11/bazaar-remove-an-app.png
[26]: https://itsfoss.com/content/images/2025/10/bazaar-choose-installation-repo.png
[27]: https://itsfoss.com/content/images/2025/11/bazaar-in-software-center.png
