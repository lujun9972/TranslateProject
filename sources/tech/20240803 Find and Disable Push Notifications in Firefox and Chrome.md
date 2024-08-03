[#]: subject: "Find and Disable Push Notifications in Firefox and Chrome"
[#]: via: "https://itsfoss.com/disable-push-notifications-firefox-chrome/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Find and Disable Push Notifications in Firefox and Chrome
======

[![Warp Terminal][1]][2]

Push notifications in browsers allow websites (if allowed) to display notifications for new activity on your desktop.

When you visit a website that wants you to send notification, you'll a pop-out of this sort:

![Push Notification Permission in Firefox][3]

If you allow, you'll start getting desktop notifications for new activities about that website.

For example, if you are a member of It's FOSS Community forum, you can get desktop notifications when someone replies to your posts.

Many websites also use push notifications to inform you when a new article is published. This happens even when the website is not opened in the browser.

But occasionally, this can be annoying, too 😠 Specially when a website starts sending too many or irrelevant notifications.

In this article, I will explain how to disable push notifications in Firefox and Chrome, two of the most popular web browsers on the internet.

The **process should be similar for other Chromium-based browsers** as well.

### Disable Push Notification in Firefox

Let's see how you can block push notifications for a specific website or multiple of them.

#### 1\. Disable push notifications for specific websites

While you are browsing that particular site, you can click on the website settings button on the address bar as shown below:

![Remove the Notification Permission][4]

This will list the permissions that site has. If it has notification permission allowed, click on the cross icon adjacent to " **Send notification** s" to revoke that permission.

#### 2\. Disable push notification from multiple websites

There is **another way to disable notifications for multiple websites in one go**.

First, click on the top-right hamburger menu and head to the settings.

![Select Settings in Firefox][5]

Within the settings menu, go to the **Privacy and Security** tab and scroll down to the **Permissions** section. Here, click on the Settings button adjacent to the Notification item.

![Select Notification Settings in Firefox][6]

In the resulting window, you can Allow/Block notification of individual websites, or remove permissions, for all the websites (more on that below).

![Change Individual Site Notification Settings][7]

Click on **Save Changes** to save the settings.

#### 3\. Disable push notifications from all sites & block new requests

In that same permission window that you see above, you can also choose to remove all the sites allowed for displaying notifications.

Fret not, if you skipped directly to this method, let me tell you again:

Go to **the Hamburger Menu → Settings → Privacy and Security**. Scroll down to the **Permissions** section and select the Settings button adjacent to “Notifications”.

![Notification Settings in Firefox][8]

Inside the new window, click on the **Remove All Website** button. This will revoke all the notification permissions.

![Remove all Notification Permissions][9]

💡

If you want, you can select the __Block new request asking to allow notifications__ checkbox. Doing this will prohibit websites from asking for notifications permission in the future.

Once changes are made, click on the **Save Changes** button to finish the settings.

### Disable Push Notification in Chrome

The steps applicable for Google Chrome should work on any Chromium-based browser, with slight differences, such as Microsoft Edge offers a “ **Cookies and site permissions** ” menu and Brave offers " **Site and Shield** " settings.

They all work the same way, only a tad bit different in how the options are accessible to you.

#### 1\. Disable push notification for single site

If you want to remove the permission of the site you are visiting currently, click on the **permissions** button on the address bar.

![Click on Site Settings Button on the Address Bar][10]

From the dropdown menu, disable the permission to send notifications. Either toggle off the _Notifications_ option or click on the _Reset Permission_ button under Notifications.

![Reset Site Notification Permission][11]

#### 2\. Disable notifications for Multiple sites

In Chrome, you can specify a block list with website addresses. And, you won’t receive notifications from these sites.

To do so, like in the previous step, go to **Settings → Privacy and Security → Site Settings → Notifications**.

Now, scroll down to the **Customized Behaviors** section. Here, you can use the **Add** button to add the full addresses of sites, whose notifications you want blocked by default.

![Block notifications for selected websites][12]

You can see in the above screenshots, I have blocked several sites from sending notifications.

#### 3\. Completely disable notification in Chrome

Don’t want any sites to send notifications? You can do that as well.

First, go to **Settings → Privacy and Security → Site Settings → Notifications**.

Under **Default Behavior** , select " _Do not allow sites to send notifications"_ button.

![Do not allow websites to send notifications][13]

That’s it! You won’t receive any website notifications now.

💬 _What is your default preference for push notifications on web browsers? Do you find them useful or do you keep them disabled? Let me know your thoughts!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/disable-push-notifications-firefox-chrome/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/05/push-notification-displayed-in-firefox-2.webp
[4]: https://itsfoss.com/content/images/2024/05/revoke-site-notification-permission-in-Firefox-site-settings-button-1.webp
[5]: https://itsfoss.com/content/images/2024/05/select-settings-in-firefox.png
[6]: https://itsfoss.com/content/images/2024/05/cllick-on-notification-settings-button-firefox.png
[7]: https://itsfoss.com/content/images/2024/05/change-individual-site-notification-block-firefox.png
[8]: https://itsfoss.com/content/images/2024/05/cllick-on-notification-settings-button-firefox-1.png
[9]: https://itsfoss.com/content/images/2024/05/remove-all-website-notification-permission-and-disable-further.png
[10]: https://itsfoss.com/content/images/2024/05/click-on-site-settings-button-in-the-address-bar-to-get-settings.png
[11]: https://itsfoss.com/content/images/2024/05/reset-the-notification-permission-of-a-site-in-chrome-browser.png
[12]: https://itsfoss.com/content/images/2024/05/block-selected-sites-to-not-send-notiification.png
[13]: https://itsfoss.com/content/images/2024/05/remove-site-notifications-alltogether-in-chrome.png
