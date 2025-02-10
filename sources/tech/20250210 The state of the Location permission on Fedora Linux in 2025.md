[#]: subject: "The state of the Location permission on Fedora Linux in 2025"
[#]: via: "https://fedoramagazine.org/the-state-of-the-location-permission-on-fedora-linux-in-2025/"
[#]: author: "Mateus Rodrigues Costa https://fedoramagazine.org/author/mateusrodcosta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The state of the Location permission on Fedora Linux in 2025
======

![][1]

Photo by [José Martín Ramírez Carrasco][2] on [Unsplash][3] (cropped)

This article will discuss the state of finding your current geographical location in the Fedora Linux environment.

### Background

For many mobile devices it is useful to get the current location. This is usually done using a GPS sensor, where the coordinates (latitude and longitude as given by the satellites) allow for step-by-step directions to the desired destination.

However, sometimes using the GPS isn’t desirable. This may be due to the high battery usage, or sometimes the device doesn’t have a GPS sensor at all. Even more interesting, the user might hit a GPS sensor limitation (such as being indoors) meaning there is a need for a secondary way to detect location to either replace or augment the GPS data.

But, what would that secondary source of data be? The alternative source needs to be some public data that is available for everyone, and we do have those! There are Wifi network identifiers, mobile cell towers data, and Bluetooth beacons. All of these are broadcast constantly, or almost constantly.

Using these alternative sources the user accepts the service of a location service provider (for example, Google Location Services provided by Google on Android). The provider has their own database of the specified device identifiers along with their approximate location. When making a location request the Wifi, Bluetooth, and cell identifiers are sent with the request and the location provider sends back coordinates. In addition they provide the precision of the coordinates based on an average of the locations available from the data in the database.

Of course, there is always the third option of combining both approaches in a way that fits the precision needed for the task. As an example, Google calls this combined approach [Fused Location][4] which is provided in their proprietary Google Play Services.

Ok, that is how it generally works and how mobile devices do it. But what about Linux?

### So, how does it work on Linux?

In Linux, the software responsible for handling the location requests is Geoclue. As [the Geoclue project][5] puts it:

> Geoclue is a D-Bus service that provides location information. The goal of the Geoclue project is to make creating location-aware applications as simple as possible.

Geoclue is capable of, among other things:

  * Support for location data based on Wifi (via wpa_supplicant integration. This uses Mozilla Location Service (MLS) by default)
  * Support for location data using GPS (if available)
  * Support for location data using mobile modems (via ModemManager integration)
  * GeoIP support (fallback mode)



Previously the Mozilla Location Service (MLS) was the default location service used under Linux. Unfortunately, in March 2024, [Mozilla announced the project was being discontinued][6], making it necessary to switch to an alternative.

### Mozilla Location Services and Ichnaea

Mozilla’s no longer available service called “Mozilla Location Services” (MLS) utilized the open source [Ichnaea software][7]. The service was capable of both receiving submitted user-data as well as responding with the approximate location based on user requests.

For submitting new data, users could use use a “stumbler” application. This was able to collect cell data, Wifi data and Bluetooth beacons, associate them with their location, and submit them to MLS or another Ichnea-compatible service.

Users would utilize the collected data by having their system (in the case of Linux or some Android ROMs using MLS) send the info about the radio devices in range and receive back info about the approximate location.

### MLS alternatives and setup

Although there are many possible MLS alternatives (As long as they maintain Ichnaea compatibiltiy), the main alternative those days is [beaconDB][8].

To set up beaconDB set the URL to

<https://api.beacondb.net/v1/geolocate>

.

Or as adapted from their website:

```

    $ sudo mkdir /etc/geoclue/conf.d
    $ sudo nano /etc/geoclue/conf.d/99-beacondb.conf
    [wifi]
    enable=true
    url=https://api.beacondb.net/v1/geolocate
    $ sudo systemctl reload geoclue

```

After restarting Geoclue you should have access to beaconDB.

A future article will focus on submitting new data, this might require an Android phone.

### Notes

  * If there’s not enough data for your region yet, you might not have a very good experience. Consider looking at [the beaconDB map][9] before making the switch or submitting data for your region.


  * The Geoclue integration with Wifi networks requires wpa_supplicant, since currently only a wpa_supplicant backend exists. This means [iwd][10] users won’t be able to use Geoclue correctly since there is no Geoclue iwd support and no Wifi data will be sent. Instead fall back to beaconDB’s GeoIP implementation will occur.


  * There is a chance beaconDB’s implementation of GeoIP might be potentially worse than Geoclue’s own implementation. This could be explained by [geoclue currently relying on Google][11], although in the future it will [switch to using reallyfreegeoip][12]. This will be noticed if city-level locations are not precise, such as showing the location a few cities away from the user actual location.



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/the-state-of-the-location-permission-on-fedora-linux-in-2025/

作者：[Mateus Rodrigues Costa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mateusrodcosta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/02/geolocation_2025-816x345.jpg
[2]: https://unsplash.com/@martinirc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/person-holding-white-printer-paper-yhNVwsKTSaI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://developers.google.com/location-context/fused-location-provider
[5]: https://gitlab.freedesktop.org/geoclue/geoclue/-/wikis/home
[6]: https://discourse.mozilla.org/t/retiring-the-mozilla-location-service/128693
[7]: https://github.com/mozilla/ichnaea
[8]: https://beacondb.net/
[9]: https://beacondb.net/map/
[10]: https://archive.kernel.org/oldwiki/iwd.wiki.kernel.org/
[11]: https://gitlab.freedesktop.org/geoclue/geoclue/-/issues/204
[12]: https://gitlab.freedesktop.org/geoclue/geoclue/-/merge_requests/195
