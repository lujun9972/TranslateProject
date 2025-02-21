[#]: subject: "Installing Add-ons and Builds in Kodi"
[#]: via: "https://itsfoss.com/install-kodi-build-add-on/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing Add-ons and Builds in Kodi
======

[![Warp Terminal][1]][2]

Kodi is a versatile media player that can be customized to fit your needs, and one of the best ways to personalize your experience is by installing a Kodi build.

These builds come pre-configured with skins, addons, and settings that make your Kodi experience even better.

In this guide, I’ll walk you through the steps of installing a Kodi build, using the Diggz Xenon Build as an example. The same method is used for installing add-ons to Kodi.

Whether you're using Kodi on a Raspberry Pi, PC, or even an Android Box, these steps will work across all devices.

### Step 1: Enable unknown sources

Before we can install third-party builds, we need to allow Kodi to install from unknown sources. Here's how:

**Go to Kodi's Home Screen** and click the **Settings Cog** (top-left corner).

![][3]

Select **System** from the options.

![][4]

Scroll down and choose **Add-ons**. On the right side, toggle the **Unknown Sources** option to **On**. A warning message will pop up; click **Yes** to confirm.

![][5]

We’re enabling this because Kodi doesn’t allow third-party sources by default for security reasons, but since we trust the source, we’ll proceed.

### Step 2: Add the repository source

Now, we’ll add the source for the Team Crew Repository. This is where the HomeFlix and many other [amazing Kodi builds][6] reside.

Go back to the Kodi home screen and open **Settings** again. Select **File Manager**.

![][7]

Click on **Add Source**.

![][8]

In the window that appears, click on **< None>**.

![][9]

Enter the build URL, in our case: `https://team-crew.github.io` and click **OK**.

![][10]

Name the source with any name you prefer), then click **OK**.

![][11]

### Step 3: Install the build repository

Now that the source is added, we’ll install the build repository.

Return to the **Kodi Settings** page and click **Add-ons**.

![a][12]

Choose **Install from Zip File**.

![][13]

Select the source you just added.

![][14]

Click on the zip file named **repository.thevrew-X.zip** (X will be the version number).

![][15]

Wait for the notification that says **The Crew Repository Add-on Installed**.

![][16]

### Step 4: Install the build wizard

The next step is to install the build Wizard, which will allow us to install the specific build that we want.

From the **Add-ons** menu, click **Install from Repository**.

![][17]

Open the **Build Repository** i.e Crew repo in my case.

![][18]

Select **Program Add-ons**.

![][19]

Click on b **uild wizard** i.e. The Crew Wizard

![][20]

and then select **Install**.

![][21]

A prompt will appear asking you to confirm the installation of dependent addons. Click **OK**.

![][22]

Wait for the installation to complete. This may take a couple of minutes.

![][23]

### Step 5: Install the actual build

Now we’re ready to install the actual build itself. I like Homeflix because if its familiar interface with Netflix, thus I'll be installing that.

Return to the **Kodi home screen** and go to **Add-ons**.

![][24]

Select **Program Add-ons**

![][25]

and click on **Chef Wizard**

![][26]

Click on **Build Menu**.

![][27]

Find and select your preffered build, I'm selecting Homeflix.

![][28]

  1. Click **Continue** and wait for the build to download and install. This may take a few minutes, so be patient.



![][29]

Once the installation is complete, click **OK** to force close Kodi.

### Step 6: Restart Kodi and Enjoy!

After the installation, simply reopen Kodi, and you’ll be greeted with the HomeFlix Build. The interface will be customized with a sleek new look, and you’ll have access to a range of addons and features.

![][30]

### Conclusion

Personally, I love the Homeflix Build by Team-Crew because it gives me that Netflix-like experience, which I find really comfortable.

It’s clean, visually appealing, and comes with tons of addo-ns pre-installed, including some premium ones like [Debrid][31].

If you’re using premium services, you might need to configure those, but the build itself is a great starting point for anyone looking to get a smooth Kodi experience.

There are plenty of builds out there, each catering to different preferences. Whether you’re into movies, TV shows, live sports, or even gaming, there’s likely a Kodi build that fits your style.

I’ve already listed [my favorite Kodi builds][6] in a separate article, so be sure to check that out for more recommendations.

![][32]

Explore a few options, experiment with different builds, and find the one that enhances your Kodi experience the most.

Now that you’ve got your build installed, sit back, relax, and enjoy a fully customized Kodi setup. Happy streaming!

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-kodi-build-add-on/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/01/kodi-settings-menu.png
[4]: https://itsfoss.com/content/images/2025/01/accessing-system-settings-1.png
[5]: https://itsfoss.com/content/images/2025/01/enabling-unknown-sources-toggle.png
[6]: https://itsfoss.com/best-kodi-builds/
[7]: https://itsfoss.com/content/images/2025/01/accessing-file-manager.png
[8]: https://itsfoss.com/content/images/2025/01/adding-source-inside-file-manager.png
[9]: https://itsfoss.com/content/images/2025/01/add-file-source-menu.png
[10]: https://itsfoss.com/content/images/2025/01/adding-build-source.png
[11]: https://itsfoss.com/content/images/2025/01/saving-the-source-with-name.png
[12]: https://itsfoss.com/content/images/2025/01/getting-back-to-addons-to-install-build.png
[13]: https://itsfoss.com/content/images/2025/01/install-from-zip-option-inside-addons.png
[14]: https://itsfoss.com/content/images/2025/01/select-the-source-saved-earlier.png
[15]: https://itsfoss.com/content/images/2025/01/selecting-the-zip-file-inside-the-source.png
[16]: https://itsfoss.com/content/images/2025/01/build-repo-added-banner.png
[17]: https://itsfoss.com/content/images/2025/01/installing-from-repository.png
[18]: https://itsfoss.com/content/images/2025/01/the-crew-repo.png
[19]: https://itsfoss.com/content/images/2025/01/program-addons.png
[20]: https://itsfoss.com/content/images/2025/01/selecting-chef-wizard.png
[21]: https://itsfoss.com/content/images/2025/01/installing-chef-wizard.png
[22]: https://itsfoss.com/content/images/2025/01/options-to-enable-in-team-crew-build.png
[23]: https://itsfoss.com/content/images/2025/01/build-install-popup.png
[24]: https://itsfoss.com/content/images/2025/01/getting-back-to-addons-to-install-build-1.png
[25]: https://itsfoss.com/content/images/2025/01/program-addons-1.png
[26]: https://itsfoss.com/content/images/2025/01/selecting-chef-wizard-1.png
[27]: https://itsfoss.com/content/images/2025/01/accessing-build-menu.png
[28]: https://itsfoss.com/content/images/2025/01/homeflix-build-install.png
[29]: https://itsfoss.com/content/images/2025/01/homeflix-downloading.png
[30]: https://itsfoss.com/content/images/2025/01/homeflix-build-ui.png
[31]: https://real-debrid.com/
[32]: https://itsfoss.com/content/images/icon/android-chrome-192x192-295.png
