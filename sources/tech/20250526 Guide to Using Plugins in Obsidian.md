[#]: subject: "Guide to Using Plugins in Obsidian"
[#]: via: "https://itsfoss.com/obsidian-use-plugin/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Guide to Using Plugins in Obsidian
======

[![Warp Terminal][1]][2]

[Obsidian][3] has emerged as a powerful and flexible [knowledge management tool][4], despite NOT being an open source product.

Using plugins is just one of the many [tips that you can follow to get the most out of Obsidian][5].

However, there is a small catch when it comes to compatibility. If you have used several Obsidian-specific plugins, then your notes may not be fully compatible in [other plain markdown editors][6].

In this article, we will take a look at Plugins in Obsidian, how you can install it, and also some essential plugins that can make your learning more effective.

But first, a quick heads-up: Obsidian offers two types of plugins:

  * **Core Plugins** : These are officially developed and maintained by the Obsidian team. While limited in number, they are stable and deeply integrated.
  * **Community Plugins** : Created by users in the Obsidian community, these plugins offer a wide variety of features, although they aren’t officially supported by the core team.



🚧

Note that some plugins may make your Markdown notes fully readable only in Obsidian. This can be a vendor lock in. Use plugins only according to your needs.

### Using the core plugins

Core plugins are officially built by Obsidian. They will come pre-installed. So, naturally, that is the recommended method of installation when it comes to plugins.

Core plugins are displayed in Obsidian settings page. Click on the settings gear icon at the bottom of the Obsidian app window to go to the settings.

![Click on the Settings gear][7]

In the settings, select **Core Plugins** to view the Core plugins.

![Select Core Plugins][8]

Most of the core plugins are enabled when you install the Obsidian app. But some plugins will be disabled by default.

I have included a brief description under each plugin to know what the plugin does and enable/disable as needed.

**Suggested Read 📖**

![][9]

### Using the community plugins

I’ve found that community plugins are one of the best ways to boost Obsidian’s capabilities. There’s a massive collection to choose from, and at the time of writing this, there are 2,430 community plugins available for installation.

These plugins are built by third-party developers and go through an initial review process before being listed.

However, since they have the same level of access as Obsidian itself, it’s important to be cautious. If privacy and security are essential for your work, I suggest doing a bit of homework before installing any plugin, just to be safe.

#### Disable the restricted mode

To protect you from unofficial plugins, Obsidian starts with a restricted mode, where the community plugins are disabled. To install community plugins, you need to disable the restricted mode first, just like the auto blocker in some Android phones to block app installations from unauthorized sources.

Go to the Obsidian settings and select **the Community Plugins** option. Here, click on the "Turn on community plugins" button.

![Turn on community plugins][10]

This will disable the restricted mode. And, you are all set! 😄

#### Install community plugins

Once the restricted mode is disabled, you can browse for community plugins and get them installed.

![Click on the Browse button][11]

Use the **Browse** button to go to the plugins page, as shown in the screenshot above. You will reach the plugins store, that lists 2000+ plugins.

Do not worry about the numbers, just search for what you need, or browse through some suggested options, just like I did.

![Plugins Store][12]

When you have spotted a plugin that matches your need, click on it. Now, to install that plugin, use the **Install** button.

![Click on the Install button][13]

Once installed, you can see two additional buttons called **Enable** and **Uninstall**. As the name suggests, they are for enabling a plugin or uninstalling a plugin.

![Enable/Uninstall a plugin][14]

This can be done more efficiently from the Obsidian settings. For this, go to the **Settings → Community plugins → Installed plugins**. Here, use the toggle button to enable a plugin.

![Enable Plugins in Settings][15]

This section lists all the installed community plugins. You can enable/disable, uninstall, access plugin settings, assign a keybinding, or donate to that particular plugin.

#### Manually install plugins

🚧

I do not recommend this method, since most of the plugins are available in Obsidian store and have gone through an initial review.

Even though not recommended, if you want to install a plugin, manually, for version compatibility or other personal reasons, make sure to source it from the official repositories or websites.

If it is on GitHub, go to the release page of the plugin GitHub repository and download `main.js`, `manifest.json`, and `style.css` files.

![Download Plugin files][16]

Now, create a directory with the name of the project in the `<Your-obsidian-vault>/.obsidian/plugins` directory. Press CTRL+H to view hidden files.

![Paste plugin contents][17]

In my case, I tried `Templater`. Next, I transfer the downloaded files to this project directory. Now, open Obsidian and go to the Settings → Community plugins and enable the new plugin.

![Enable manually installed plugin][18]

#### Install beta version of plugins

This is not for regular users, but for those who want to be testers and reviewers of beta plugins. I usually do this to test interesting things or help with the development of plugins I believe in.

We are using the BRAT (Beta Reviewers Auto-Update Tool) to install and update beta versions of Obsidian plugins.

First, install the BRAT plugin from the Obsidian plugins store and enable it.

![Install BRAT Plugin][19]

Now, go to the GitHub repository of the plugin you want to install the beta version of. Copy the URL of the repository.

Select the BRAT plugin from **Settings → Community plugins** and click on the “Add beta plugin” button.

![Click on the "Add beta plugin" button][20]

Here, add the GitHub URL, select a version from the list, and click on the Add Plugin button.

![Add URL and select version][21]

You can see that the plugin has been added with BRAT. Since we selected a specific version, it is shown as frozen and cannot be updated. Select **Latest** as version to get updates.

![Beta plugin added using BRAT][22]

#### Update plugins

To update community plugins, go to Obsidian settings and select Community plugins.

Here, click on the **Check for updates** button.

![][23]

If there is an update available, it will notify you.

![There is an update available for one plugin.][24]

Click on **Update All** to update all the plugins that have an update available. Or, scroll down and update individual plugins by clicking on the **Update** button.

![][25]

#### Move community plugins

You can copy selected or all plugins from your directory to another vault to avoid installing everything from scratch.

Go to the `<your-obsidian-vault>/.obsidian/plugins` directory. Now, copy directories of those plugins you want to use in another vault.

Copy those directories to your new plugin directory for your other vault (or the newer vault) `<your-new-vault>/.obsidian/plugins` directory.

If there is no plugins directory in the new vault, create one. Once you open the new vault, you will be asked to trust the plugins.

If it is you, who copied all the folders and no others are involved, click on the "Trust author and enable plugins" button.

Or you can use the "Browse Vault in restricted mode" and then enable the plugins by going to **Settings → Community plugins → Turn on Community plugins → Enable plugins**.

![Plugin security notification][26]

In both cases, you don't have to install the plugin from scratch.

Don't forget to enable the plugins through **Settings → Community plugins** to start using them.

#### Remove a plugin

Removing a plugin is easy. Go to the community plugins in settings and click on the delete button (bin icon) adjacent to the plugin you want to remove.

![Remove a plugin][27]

Or, if you just want to disable all community plugins, you can turn on the restricted mode. Click on the **Turn on and reload** button in community plugins settings.

![Turn on restricted mode][28]

So, if you turn off the restricted mode, all the installed plugins will be enabled. Pretty easy, I know, right?

Another way to remove plugins is to delete specific folders in the plugins directory, but it is unnecessary unless you are testing something specific.

🚧

Don't use this method for everything since it is safer to do so from within Obsidian.

Go to the `<your-obsiidian-vault>/.obsidian/plugins` directory and remove the directory that has the name of the plugin you want to remove.

Now open Obsidian and you won't see that plugin. Voila!

### Enjoy using Obsidian

I have shared many [more Obsidian tips][5] to improve your experience with this wonderful too.

![][29]

Plugin is just part of how you can go beyond the obvious and default Obsidian offering. I hope you found this tutorial helpful. Enjoy.

--------------------------------------------------------------------------------

via: https://itsfoss.com/obsidian-use-plugin/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/obsidian-markdown-editor/
[4]: https://itsfoss.com/open-source-second-brain-apps/
[5]: https://itsfoss.com/obsidian-tips/
[6]: https://itsfoss.com/best-markdown-editors-linux/
[7]: https://itsfoss.com/content/images/2025/05/click-on-settings-gear.png
[8]: https://itsfoss.com/content/images/2025/05/select-core-plugins-in-settings.png
[9]: https://itsfoss.com/content/images/icon/android-chrome-192x192-454.png
[10]: https://itsfoss.com/content/images/2025/05/click-on-turn-on-community-plugins.png
[11]: https://itsfoss.com/content/images/2025/05/click-on-browse-to-browse-plugins.png
[12]: https://itsfoss.com/content/images/2025/05/community-plugins-store.png
[13]: https://itsfoss.com/content/images/2025/05/click-on-install-to-install-a-community-plugin.png
[14]: https://itsfoss.com/content/images/2025/05/community-plugin-installed-enable-or-uninstall.png
[15]: https://itsfoss.com/content/images/2025/05/enable-plugins-from-settings.png
[16]: https://itsfoss.com/content/images/2025/05/download-files.png
[17]: https://itsfoss.com/content/images/2025/05/paste-plugin-contents-obsidian.png
[18]: https://itsfoss.com/content/images/2025/05/enable-manually-installed-plugin.png
[19]: https://itsfoss.com/content/images/2025/05/install-brat.png
[20]: https://itsfoss.com/content/images/2025/05/click-on-add-a-beta-plugin-button-brat-1.png
[21]: https://itsfoss.com/content/images/2025/05/add-url-and-select-version.png
[22]: https://itsfoss.com/content/images/2025/05/plugin-added-with-brat.png
[23]: https://itsfoss.com/content/images/2025/05/click-on-check-for-updates.png
[24]: https://itsfoss.com/content/images/2025/05/one-plugin-has-update.png
[25]: https://itsfoss.com/content/images/2025/05/update-individual-plugins.png
[26]: https://itsfoss.com/content/images/2025/05/trust-the-author.png
[27]: https://itsfoss.com/content/images/2025/05/remove-a-plugin.png
[28]: https://itsfoss.com/content/images/2025/05/turn-on-restricted-mode.png
[29]: https://itsfoss.com/content/images/icon/android-chrome-192x192-470.png
