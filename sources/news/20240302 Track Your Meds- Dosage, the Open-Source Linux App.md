[#]: subject: "Track Your Meds: Dosage, the Open-Source Linux App"
[#]: via: "https://news.itsfoss.com/dosage/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Track Your Meds: Dosage, the Open-Source Linux App
======
This app makes it easy to keep up with your medications.
There have been days in my life where I have forgotten to take important medication and dietary supplements due to being caught up with my daily chores.

But, I know that skipping medications that are essential to one's physical and mental wellbeing is not a great idea, and constantly forgetting to take your meds will most likely worsen your condition.

That stops now! I came across a nice reminder app called “ **Dosage** ” for Linux that is geared towards managing and tracking one's medications. Let's dive in!

🚧

Before we begin, please keep in mind that the medications listed below are only for illustrative purposes. These do not represent medical advice.

### Dosage: Overview ⭐

![][1]

With a primarily JavaScript foundation, Dosage is **an open-source app** that lets you keep track of your various medications with the option to receive timely reminders according to the frequency and dosage time you select.

It also **comes with support for plenty of languages** that include, _English_ , _Spanish_ , _Hindi_ , _Turkish, Italian, Russian_ and more. It is made possible with the help of [Weblate][2], a web-based translation tool.

Some **key features** include:

  * **Medication History**
  * **Medication Frequency**
  * **Inventory Management**



#### Initial Impressions 👨‍💻

I installed the official Flatpak package, and upon first launch I was staring at a blank page that said, “ _No treatments added yet_ ”.

![][3]

The “ _One-time entry_ ” options allows you to quickly add a medicine dosage for a particular day. However, I don't think you would want to use this option for the most part, as you do not get an option to set notifications, and set a schedule for the medication.

So, I set out to fill the app up by going into the “ _Treatments_ ” tab, which had a button called “Add” to start adding new medicines.

![][4]

When I clicked on that, **a neat medication editor** popped up with useful options such as adding the name of the medication, what unit to follow ( _pill, ml, gm)…_

A note that could be set to say _After/Before meal_ or really anything you want, option to set a color/icon to better distinguish between meds, the dosage time and amount.

![][5]

Then there was the frequency of taking the medication, with options like every day, specific days, cycle, and when necessary.

![][6]

I could also set notifications to reoccur until it was either confirmed or rejected. This can help you if you forget things easily.

You can **also manage a virtual inventory** of meds by putting in what you have, and when you want to be reminded of low stock. There was also the option to tweak the start and end dates for the treatment.

![][7]

Nonetheless, after I was done adding a few medicines and supplements, this is how the app looked like. 👇

![][8]

Beautiful, isn't it? The different colors make it so much easier to manage medication. Combine that with the ability to select multiple medicines to either confirm or skip them for the day, **you have a very intuitive way of keeping track of your medication**.

![][9]

Forgot whether you took a specific medicine? Fret not, you can head over to the “ _History_ ” tab to see which medicines you have already taken or skipped, and at what time.

![][10]

The “ _Treatments_ ” tab also is practical to keep track of how much medication is still in stock, just remember to keep the virtual inventory updated by clicking on the edit button to edit a medicine.

![][11]

There is also a handy “ _Preferences_ ” option that I could access from the three-ribbon header menu which allowed me to enable auto-start at login, clear the history automatically, and change the notification behavior.

![][12]

When I was testing on my Ubuntu 22.04 LTS system, Dosage never showed me any notifications, but, when I tested it on a [virtual machine][13] equipped with Ubuntu 23.10, it showed me notifications without a fuss.

Maybe **older versions of GNOME/Ubuntu do not play nice with Dosage** , or a bug I encountered in my case? If you face the same issue, I suggest you go for newer versions of distributions with [GNOME 45][14] at least to receive timely notifications.

### 📥 Get Dosage

You can grab the latest release of Dosage from the [Flathub store][15] or the [Snap store][16]. If you are interested in the source code, you can give its [GitHub repo][17] a visit.

[Dosage (Flathub)][15]

You can also run _one_ of the following commands below to get it installed via your terminal:

```

    sudo snap install dosage-tracker #snap package

```

OR

```

    flatpak install flathub io.github.diegopvlk.Dosage #flatpak package

```

_💬 That was about it for this first look. Do let me know if you have used similar apps in the past._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/dosage/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/content/images/2024/03/Dosage_a-1.png
[2]: https://hosted.weblate.org/projects/dosage/dosage/
[3]: https://news.itsfoss.com/content/images/2024/03/Dosage_b.png
[4]: https://news.itsfoss.com/content/images/2024/03/Dosage_c.png
[5]: https://news.itsfoss.com/content/images/2024/03/Dosage_d.png
[6]: https://news.itsfoss.com/content/images/2024/03/Dosage_e.png
[7]: https://news.itsfoss.com/content/images/2024/03/Dosage_f.png
[8]: https://news.itsfoss.com/content/images/2024/03/Dosage_g.png
[9]: https://news.itsfoss.com/content/images/2024/03/Dosage_h.png
[10]: https://news.itsfoss.com/content/images/2024/03/Dosage_i.png
[11]: https://news.itsfoss.com/content/images/2024/03/Dosage_j.png
[12]: https://news.itsfoss.com/content/images/2024/03/Dosage_k-1.png
[13]: https://itsfoss.com/virtual-machine/
[14]: https://news.itsfoss.com/gnome-45-release/
[15]: https://flathub.org/apps/io.github.diegopvlk.Dosage
[16]: https://snapcraft.io/dosage-tracker
[17]: https://github.com/diegopvlk/Dosage
