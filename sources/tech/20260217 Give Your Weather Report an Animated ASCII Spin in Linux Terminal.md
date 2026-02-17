[#]: subject: "Give Your Weather Report an Animated ASCII Spin in Linux Terminal"
[#]: via: "https://itsfoss.com/weathr/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Give Your Weather Report an Animated ASCII Spin in Linux Terminal
======

[![Warp Terminal][1]][2]

One of the most underrated things that comes with open source projects that isn't talked about enough is the whimsy. The developers make anything they like, unshackled by any bonds of a boring format, and the result of this kind of freedom is a program like weathr.

[weathr][3] is a CLI tool written in Rust that gives you a full weather report, complete with a general category, temperature, wind speed and precipitation.

What separates it from other weather utilities is that it shows you what the weather looks like in ASCII graphics, with a little house and shrubbery, featuring absolutely adorable animations.

0:00

/0:07

1×

weathr

weathr retrieves the weather data from [Open-Meteo][4], and it has several modes and configurations that you can play around with.

### Different animation for different kind of weather

📋

Weathr allows you to simulate a few weather conditions. This lets you see how the terminal would appear if the weather were the same where you are.

I understand that monsoon is not a season experience in many parts of the world but let's say it's raining outside.

```

    weathr --simulate rain

```

This is what it would look like in weathr:

0:00

/0:04

1×

weathr rain simulation

I have never experienced snowfall in real but at least I can simulate it ;)

```

    weathr --simulate snow

```

0:00

/0:04

1×

weathr snow simulation

If not snow, for sure I have witnessed fog in winters:

```

    weathr --simulate fog

```

0:00

/0:06

1×

weathr fog simulation

There are several more options you can simulate, listed on the help page, which are put into four categories:

  * **Clear Skies:** clear, partly-cloudy, cloudy, overcast
  * **Precipitation:** fog, drizzle, rain, freezing-rain, rain-showers
  * **Snow:** snow, snow-grains, snow-showers
  * **Storms:** thunderstorm, thunderstorm-hail



💡

There are also frequent passages of airplanes. Glad that they don't make noise ;)

#### Different animation for different time of the day

Weathr takes care of the time of the day. The daytime animations include the sun, gliding clouds, v-shaped birds, and bright colors. Nighttime comes with animations of the moon, twinkling stars, gliding clouds, and fireflies and shooting stars.

To simulate the weather at nighttime, you have to choose a simulation condition first and add an -n flag to signify the time of day:

```

    weathr --simulate clear -n

```

0:00

/0:11

1×

weathr nighttime simulation

You can simulate any of the weather conditions mentioned before. You can also choose to make the leaves fall as if it was autumn within the window with the -l flag. I guess -l stands for leaves here.

```

    weathr --simulate clear -l

```

0:00

/0:07

1×

weathr fall simulation

### Units of your choice

There are two broad categories you can choose from, obviously being imperial and metric units:

```

    weathr --imperial
    weathr --metric

```

You can also specify specific units for all the different fields, with the options being:

  * **Temperature:** celsius, fahrenheit
  * **Wind Speed:** kmh, ms, mph, kn (knots)
  * **Precipitation:** mm, inch



This can be added to the configuration file at ~/.config/weathr:

```

    [units]
    temperature = "celsius"
    wind_speed = "kmh"
    precipitation = "mm"

```

💡

While the default view gives all the available options, you can choose to hide the location coordinates or the entire heads-up-display (HUD) entirely to only see the ASCII animation:

`weathr --hide-location`
`weathr --hide-hud`

### Set the location manually and accurately (if you want to)

If you run weathr as it is, it will track your public IP and show the weather for that location. Now, we all know that public IP is not an accurate measure of location. And if you [use VPN on your Linux system][5], you won't want to see the weather of Australia when you are in America.

The good thing is that weathr allows you to configure your location. It requires some config file editing but that's not overly complicated.

First thing first, use a map on your smartphone to get the coordinates of your location. You can also use a website like [GPS Coordinate][6] for this purpose.

To start with, for an accurate weather report without being intrusive, weathr takes in the exact coordinates input by the user to provide a weather report. It can be updated in the configuration file for a permanent setting of the location or change of the same. To do it, you need to first create the configuration file using:

```

    mkdir -p ~/.config/weathr

```

To enter the location, given that you know your coordinates, access the newly created configuration file at ~/.config/weathr and add the following:

```

    [location]
    # Location coordinates (overridden if auto = true)
    latitude = 40.7128
    longitude = -74.0060

```

Other than that, you can choose an auto-location option that gets the location from your IP address.

```

    weathr --auto-location

```

### Installing weathr

🚧

****It is a Rust-based tools so you need to**** [****install Cargo first****][7]. Cargo is a command-line tool that is used for installing Rust-based utilities from the Rust Package Registry ([Crates][8]) or from a locally downloaded Rust program.

Installing weathr needs Rust and Cargo, after which you can enter the following commands:

```

    git clone https://github.com/veirt/weathr.git
    cd weathr
    cargo install --path .

```

If you wish to check the help page for quick peak at the available commands:

```

    weathr --help

```

[Get weathr][3]

💡

If you liked this nifty tool, perhaps star their GitHub repo. Developers like that.

### Wrapping Up

While "necessary" isn't the word that can be used to describe an app like weathr, it still stands as a testament to how fun and innovative open source applications can be. With a minimal system load, weathr adds a touch of delightful playfulness. I mean, we should surely add it to our [list of fun ASCII tools][9].

Please let us know what you think about weathr in the comments, and if you would use it for your daily weathr report needs. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/weathr/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/veirt/weathr
[4]: https://open-meteo.com/
[5]: https://itsfoss.com/best-vpn-linux/
[6]: https://www.gps-coordinates.net/
[7]: https://itsfoss.com/install-rust-cargo-ubuntu-linux/
[8]: https://crates.io/
[9]: https://itsfoss.com/ascii-art-linux-terminal/
