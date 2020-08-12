[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (8 free Wi-Fi stumbling and surveying tools for Windows and Mac)
[#]: via: (https://www.networkworld.com/article/2924320/8-free-wi-fi-stumbling-and-surveying-tools-for-windows-and-mac.html)
[#]: author: (Eric Geier )

8 free Wi-Fi stumbling and surveying tools for Windows and Mac
======
Measuring signal strength, channels, MAC addresses and security status of Wi-Fi networks is essential to monitoring Wi-Fi networks, and here are free tools – some for Windows, some for Macs – that can do just that.
Thinkstock

There is enterprise-level software for surveying Wi-Fi networks, but even in large wireless networks, simple freeware tools are handy for a quick peek at the airwaves during design, deployment or troubleshooting.

Here is a look at eight free tools – some for Windows and some for Mac OS X – that provide basic details about nearby Wi-Fi signals: SSIDs, signal strength, channels, MAC addresses and security status.

**Learn about 5G and Wi-Fi 6**

  * [What is 5G? How is it better than 4G?][1]
  * [How to determine if WiFi 6 is right for you][2]
  * [What is MU-MIMO? Why do you need it in your wireless routers?][3]
  * [When to use 5G, when to use WiFi 6][4]
  * [How enterprises can prep for 5G networks][5]



Some can even reveal “hidden” or non-broadcasted SSIDs, display the noise levels, or display statistics on successful and failed packets of your wireless connection. One of them includes Wi-Fi password-cracking tools that are useful for educational or penetration testing purposes.

Most of these tools are the free versions of for-pay tools made by the same vendors, and lack some of the features included in the commercial versions.

## **Acrylic Wi-Fi Home 3.1 (Windows)**

Tarlogic Security offers [Acrylic Wi-Fi Home][6], a Wi-Fi stumbler that is a scaled down version of their [commercial offering][7]. The 3.1 version looked at here offers some great wireless details and graphs.

The free edition has a simple but attractive GUI. You always see the list of SSIDs and their details on the top portion of the application. It shows negative dBm values for RSSI, can name the 802.11 standard (including 802.11ac), recognizes larger bandwidths and displays the multiple channels that are utilized. It does not reveal the actual hidden SSIDs, but does show the other network details of hidden SSIDs.

The application has an inventory feature to assign and save names of detected SSIDs and/or clients. The free edition has a five-entry limit.

By default, the bottom portion of the application shows the network ratings of the selected SSID, and one graph showing each SSID’s signal strength. Though a bit hidden, there’s an advanced mode that displays two additional graphs, one for 2.4GHz and one for 5GHz. Is displays channel usage, including channel-bonding, and signal strength at the same time.

For exporting or saving the captured data, the application is limited to copying up to one row of data to the clipboard and pasting the plain text into a text document or spreadsheet. There’s also a Tweet feature to post a screenshot to Twitter.

Overall, Acrylic Wi-Fi Home Free is a solid Wi-Fi stumbler given that it costs nothing. It displays both textual and graphical details, which is great for simple Wi-Fi surveying needs. It would be nice if they offered better data exporting, however.

## **Cain &amp; Abel (Windows)**

[Cain &amp; Abel][8] is a multi-purpose password recovery and cracking application that also features Wi-Fi stumbling, sniffing and cracking tools. Like Acrylic WiFi, it also has a monitor or promiscuous mode to capture more traffic.

Its GUI has an older, simplistic look and feel. It has an old-style toolbar on the top with icons to bring up different utilities. The main portion of the application is tabbed; clicking the tabs shows the different utilities.

The Wireless tab is where the Wi-Fi stumbler resides. In addition to the typical SSID and signal info, it shows a list of and details for the connected clients. For SSIDs and clients the stumbler provides numbers of certain packets detected: all packets, unique WEP IVs and ARP requests. Like Acrylic WiFi, any hidden SSIDs discovered from packets are revealed in the GUI as well. Most of status and data captured can be exported into a simple text file.

Due to lacking graphs and inability to distinguish 802.11ac APs and larger channel-widths, Cain &amp; Abel might not be a great choice for general Wi-Fi stumbling and surveying. But it certainly would be useful when performing penetration testing.

## **Ekahau HeatMapper (Windows)**

[Ekahau HeatMapper][9] is a free map-based site survey tool for home-use, a slimmed down version of their [professional product][10]. It shows similar network details as a Wi-Fi stumbler, but also generates a heatmap of the Wi-Fi so you can visualize the signal levels. Version 1.1.4 is reviewed here.

The app offers the option to create a floorplan or layout of the building being surveyed or a grid layout for a rough guideline.

The left side of the main screen displays a listing of the SSIDs and their details that is sortable by signal, channel, SSID, MAC address and security method. It includes the main network details, but lacks the signal levels in dBm and percentage values. It only shows signal bars on the list. The app shows 802.11ac networks as 802.11n.

Like other map-based survey tools, you click your location on the map as you walk around the building so it can generate the heatmap. It will automatically estimate access point (AP) locations and place them onto the map. After it captures some data, hovering over the AP icons shows their individual coverages. When hovering over the heatmap areas, it shows a tooltip pop-up with the signal level range in negative dBm values. The only export or saving functionality of the app is taking a simple screenshot of the heatmap.

We found Ekahau HeatMapper to be a very simplistic map-based Wi-Fi survey tool. Though it lacks any advanced features, it could be used for small networks or to give an idea of how these map-based tools work.

## **Homedale (Windows)**

[Homedale][11] is a relatively simple and portable Windows-based stumbler with an optional command-line interface. Other than showing basic network and signal details, it supports GPS and other geolocation detection. This is a review of version 1.7.

This utility has a simple GUI that resembles more of a multi-tabbed dialog box than a full application. The first tab, Adapter Overview, displays a listing of all the network adapters and their IP gateway and MAC addresses.

The Access Points tab shows many essential details. It doesn’t display the 802.11 standard of each SSID, but it does show the supported data rates and the multiple channels used by any SSIDs with larger channel-widths. Additionally, it does not reveal the actual hidden SSIDs, but does show the other network details of hidden SSIDs. One feature we liked allows saving notes to individual SSIDs, which are then included in any data exports.

The Access Point Signal Graph tab shows a line graph of the signal levels for each SSID selected. The Frequency Usage tab displays channel visualizations for the 2.4GHz band and each sub-set of the 5GHz band. They do the job of showing channel usage (including channel-bonding) and signal strength, but it would be nice if they had a single view of the entire 5GHz band instead of dividing it into four different graphs.

For a free application, Homedale offers great exporting capabilities. It supports saving the network list as a CSV, logging networks from every scan (useful if moving while scanning), and saving an image of each graph.

Although the GUI is very simple, Homedale provides some advanced functionality. We were impressed with its exporting, logging and location-aware features.

## **LizardSystems Wi-Fi Scanner (Windows)**

LizardSystems offers a free edition of their [Wi-Fi Scanner][12] application for non-commercial use, which has the same features and functionality as their paid product. This is a review of version 3.4. In addition to the Wi-Fi stumbling, it offers some great analysis and reporting capabilities.

The application has a modern-looking GUI that’s easy to get around and understand. On the Scanner tab is a list of detected SSIDs. Along with the typical details, it shows signal strength in both negative dBm values and percentages. It even shows the number of clients connected to each SSID. Along with specifying the 802.11 standards, it shows the multiple channels used by any SSIDs with larger channel-widths.

You can use a list on the left to filter the SSIDs shown based upon the signal level, 802.11 standard, security method and frequency band. On the bottom of the Scanner tab, you can flip between several graphs. In addition to the typical signal level and channel usage graphs, there are visualizations for the data rates, channel utilization and the number of clients. The Network Details on the bottom shows details of the current connection. The Advanced Details tab shows details down to raw packets.

The Current Connection tab displays more details about the current wireless connection. It enables accessing and managing the list of wireless network profiles saved in Windows 10, which can be useful since Windows doesn’t allow native access to or management of that list anymore. On the Wireless Statistics tab are graphs and statistics on many different MAC layer and PHY layer packets types, useful for advanced network analysis.

Wi-Fi Scanner offers great exporting and reporting features. The basic export feature can save the network list to a plain text file. Additionally, it can generate a report showing a summary of the types of networks found along with all the captured SSID details, any comments you’ve added and snapshots of the graphs. It’s quite impressive for a free stumbler.

Wi-Fi Scanner would be a great one to add to your Wi-Fi surveying tool chest, while remembering that the free edition is licensed for personal use only. We were impressed with the filtering, advanced packet details and the reporting feature.

## **NetSpot (Windows &amp; Mac OS X)**

[NetSpot][13] is a Wi-Fi stumbler and map-based survey tool, but for the free home edition we reviewed, the map-based survey tool is disabled. However, this is the only tool reviewed here that’s available for both Windows and Mac OS X. It’s a slimmed down version of their paid home and professional editions. We reviewed version 2.6.1.

The Netspot Discover tab is their Wi-Fi stumbler. Though a simple GUI, it’s got a modern look and feel, and the network details of the SSIDs are shown bold and clear. The signal levels are shown in negative dBm values (current, minimum, and maximum) and percentages. However, it does not show hidden networks at all on the network list. Although there’s an export button, it doesn’t work in the free edition.

Clicking on the Details button on the bottom of the app reveals a combined signal graph and channel usage graph for each band, which conveniently highlights the SSID on the graphs based upon which is selected from the network list. Plus, there’s a tabular or table view of the signal details of each SSID to see the exact levels from each scan of the app.

We found the free edition of NetSpot provides a good Wi-Fi stumbler even though it does not supporting hidden networks. The app shows non-working features in the app that’s for paid users only, but it does give you a better idea of the functionality available with the paid version. For instance, the Survey tab opens a sample survey and allows playing with the visualizations to demonstrate what it can do.

## **WirelessNetView (Windows)**

The [WirelessNetView][14] utility is freeware from NirSoft, offered for personal or commercial purposes. It’s a very simple Windows-based Wi-Fi stumbler, available as an installable or portable download. We reviewed version 1.75.

The GUI of WirelessNetView is very simple, it’s basically just a single window with the list of networks. For the signal strength, it shows negative dBm values and for percentages, it shows values for the last signal received and the average over time. But it would be even better if it showed average signal over time in the negative dBm value, too. Another unique detail it offers is how often each SSID has been detected, which could be useful in certain situations.

Double-clicking a network pops up a dialog box with all that particular network’s details, which is useful since seeing all the details on the main list requires a lot of horizontal screen space. Right-clicking on a network on the list enables exporting details for that particular network or all networks to a text or HTML file. The Options toolbar menu shows some settings and additional features, such as filtering, MAC address formatting and display preferences.

Keep in mind, this utility lacks advanced features, like graphs, full 802.11ac support and recognizing all channels for APs utilizing larger channel-widths. However, it still might be useful for simple Wi-Fi stumbling, especially if you find some of their unique features valuable.

## **Wireless Diagnostics (Mac OS X Lion and later)**

In Mac OS X Mountain Lion v10.8.4 and later, Apple provides the Wireless Diagnostics tool. It’s more than just a stumbler; it can help detect and fix Wi-Fi issues as well. Best of all, it’s a native tool included with the OS. We reviewed the tool in Mac OS X High Sierra 10.13.

To get started, hold the Option key and then click the Airport/Wi-Fi icon on the top of Mac OS X. This displays some more details on your current Wi-Fi connection while also making the Wireless Diagnostics shortcut available.

Opening Wireless Diagnostics pops up a wizard called the Assistant that may ask for additional details such as the location of the router and the router brand and model. Then it starts running tests to detect issues. It shows a summary of the results, and clicking the icon for each result shows further details and suggestions.

Although not really apparent, there are more tools than the wizard. While the wizard dialog box is open, clicking Window on the toolbar up top reveals additional utilities.

The Scan utility is a simple Wi-Fi stumbler, showing the usual details of detected networks along with a summary of network types and best channels. One major advantage is that it shows the noise levels of the Wi-Fi channels, which most Windows stumblers don’t show. However, it would be nice if it would show all the channels used by SSIDs that are utilizing larger channel-widths instead of just showing the channel-widths and center channel.

The Info utility shows current network connection and signal details. The Logs utility allows configuring Wi-Fi, EAPOL and Bluetooth diagnostic logging. The Performance utility shows line graphs of the signal and noise, signal quality and data rate of the current connection. The Sniffer utility allows capturing the raw wireless packets, and can export into a third-party packet analyzer.

The Wireless Diagnostics utilities of Mac OS X is quite impressive compared to the wireless tools provided by Microsoft in the Windows OSes. You always have a Wi-Fi stumbler (which even shows noise levels) and packet-capture abilities, and their Assistant troubleshooting wizard seems smart. However, it’s lacking a channel usage graph to visualize the Wi-Fi channels.

For more info, Apple provides a great [tour and tutorial][15] on Wireless Diagnostics.

 

Join the Network World communities on [Facebook][16] and [LinkedIn][17] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/2924320/8-free-wi-fi-stumbling-and-surveying-tools-for-windows-and-mac.html

作者：[Eric Geier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3203489/what-is-5g-how-is-it-better-than-4g.html
[2]: https://www.networkworld.com/article/3356838/how-to-determine-if-wi-fi-6-is-right-for-you.html
[3]: https://www.networkworld.com/article/3250268/what-is-mu-mimo-and-why-you-need-it-in-your-wireless-routers.html
[4]: https://www.networkworld.com/article/3402316/when-to-use-5g-when-to-use-wi-fi-6.html
[5]: https://www.networkworld.com/article/3306720/mobile-wireless/how-enterprises-can-prep-for-5g.html
[6]: https://www.acrylicwifi.com/en/wlan-software/wlan-scanner-acrylic-wifi-free/
[7]: https://www.acrylicwifi.com/en/wlan-software/wifi-analyzer-acrylic-professional/
[8]: http://www.oxid.it/cain.html
[9]: https://www.ekahau.com/products/heatmapper/overview/
[10]: https://www.ekahau.com/products/ekahau-site-survey/overview/
[11]: http://thesz.diecru.eu/content/homedale.php
[12]: http://lizardsystems.com/wi-fi-scanner/
[13]: https://www.netspotapp.com
[14]: http://www.nirsoft.net/utils/wireless_network_view.html
[15]: https://support.apple.com/en-us/HT202663
[16]: https://www.facebook.com/NetworkWorld/
[17]: https://www.linkedin.com/company/network-world
