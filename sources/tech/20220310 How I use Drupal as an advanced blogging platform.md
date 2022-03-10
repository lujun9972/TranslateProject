[#]: subject: "How I use Drupal as an advanced blogging platform"
[#]: via: "https://opensource.com/article/22/3/drupal-advanced-blogging-platform"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I use Drupal as an advanced blogging platform
======
Drupal is a flexible and powerful blogging platform that I enjoy
customizing to suit my needs.
![Digital images of a computer desktop][1]

A couple of years ago, I decided I wanted a place to post my thoughts and play around with some emerging web technologies.

### Why Drupal?

I make my living working with and evangelizing Drupal. So there's definitely some applicability to the saying, "when your only tool is a hammer, every problem looks like a nail."

In truth, I had considered using some [static site solutions][2] like Gatsby or [Jekyll][3] and then using free hosting options from GitHub or GitLab.

However, one of the things I enjoy about Drupal is how quickly I can create and adapt content structures and have the ability to draw on the considerable library of community-provided modules to extend its capabilities, all of which you can use for free.

Let me use a specific example to illustrate its flexibility. Initially, I wanted my site to be a blog, and there are a ton of options for that, including pure SaaS offerings like Medium. As I was working on it, however, it occurred to me that I could also use the site as a place to keep track of my various public speaking engagements.

### Speaking of Drupal

I maintain several Drupal modules that I share with the community. I have also had the privilege of working with some very smart people, so I regularly have specific ideas around how you can use Drupal for some everyday use cases in easy and powerful ways.

When I submit a session proposal to an open source conference, the organizers often want to see a list of my recent public speaking engagements. I used to keep track of that in various ways, including a Google Doc. Then I have to remember to keep the list up to date (invariably, I don't). Then if a particular conference wants the information in a different format, I have to adapt all the content myself: Add longer descriptions, video links, and more.

I added a content type (a customizable template for structured storage) on my Drupal site called Talk. By default, it had a title and description, so I added fields for the schedule, location, and a link to the video.

![Add a talk in Drupal][4]

(Martin Anderson-Clutz, [CC BY-SA 4.0][5])

Drupal has robust media handling out of the box, so when a video of one of my talks gets posted online, all I have to do is copy and paste the URL into my site. I can display that as a link or an embedded video player. For better performance, I also added a community module that allows the site to lazy load the video players.

I recently realized that I often post the slides from my talks to SlideShare, so I added a field to keep track of those links. That change took less than a minute to implement. Now, if someone wants to revisit the content, they can find a page on my site with all the information: When it happened, the description, a video, and the slides.

![Add a recording and slides][6]

(Martin Anderson-Clutz, [CC BY-SA 4.0][5])

Drupal also includes a powerful visual query builder called Views, great for generating content lists to meet specific needs in a point-and-click interface. I used Views to create lists of upcoming and past talks, including small video players for the past talks and full-sized players if visitors click through to the details. If a conference requires my speaking experience in a specific format, I can easily create a new View to provide precisely the information they need, in the format they need it, with just a few clicks.

### Key Drupal features

Another great thing about creating a site with Drupal is that you get to build on the work of one of the most engaged open source communities in the world. And they've built in some impressive capabilities, which my site benefits from.

#### Performance

They built Drupal to use multiple layers of caching for better performance. It also supports [BigPipe][7] progressive rendering, allowing even complex pages to start rendering in the browser right away.

#### Accessibility

The Drupal community put a ton of work into the spiffy new Olivero theme. It not only looks beautiful but got built for easy navigation by screen readers and other assistive technologies. Upon review, the National Federation of the Blind gushed that the team "knocked it out of the park." For my site, I worked out a way to override Olivero and make some minor stylistic changes without directly editing the theme. That allowed me to give my site some unique flavor while ensuring I can update it painlessly as Drupal continues to evolve.

### My favorite Drupal modules

While Drupal is incredibly flexible out of the box, the possibilities are endless when you start to add from the immense library of modules available from the community, all for free. Here are a few that make my site better.

#### [Smart Date][8]

This provides an intuitive, easy-to-use widget for entering dates, designed to align with the UX of typical calendar applications. It handles timezones elegantly. And it also allows for the natural language formatting of date ranges: Outputting "9-10AM on Tuesday, Feb 15" instead of "9:00AM Tuesday, Feb 15 - 10:00AM Tuesday, Feb 15" for example.

#### [Blazy][9]

By default, Drupal adds the `loading="lazy"` HTML attribute to `img` tags, but all browsers don't support this. Also, my site loads multiple video players on the home page, which can cause a performance hit. The Blazy module adds support for multiple lazy loading libraries and can lazy load video players.

#### [Pathauto][10]

Drupal long could create SEO-friendly URLs like `/node/123` based on the numerical ID of a piece of content. Pathauto expands the sophistication of the automatically generated URLs to include text, such as the type of content, how you categorized it, and the title (`/articles/blog/composable-date-formatter-drupal`). You can use this for creating breadcrumbs as well.

If I wanted to get serious about SEO, I could add the automatic generation of various meta tags using the [Metatag][11] module, and also add meta tags so content looks better when shared on social media. If I wanted to get _really_ serious about SEO, I could also add the [Real-time SEO][12] module to help me aggressively optimize for specific keywords. But, I doubt I'll ever take it that seriously.

### Final thoughts

Are you interested in giving Drupal a try? There are one-click demos available at [Simplytest.me][13] or [DrupalPod][14] you can use to test out Drupal with a cloud-hosted IDE (if you want to get your hands dirty). In another article, I'll discuss a low-cost (basically free, once it's up and running) way to host your Drupal site.

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/drupal-advanced-blogging-platform

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/computer_browser_web_desktop.png?itok=Bw8ykZMA (Digital images of a computer desktop)
[2]: https://opensource.com/article/18/3/start-blog-30-minutes-hugo
[3]: https://opensource.com/article/21/9/build-website-jekyll
[4]: https://opensource.com/sites/default/files/pictures/first_image_for_the_drupal_blogging_platform_article_form_to_add_a_talk.png (Add a talk in Drupal)
[5]: https://creativecommons.org/licenses/by-sa/4.0/
[6]: https://opensource.com/sites/default/files/pictures/adding_a_recording_and_slides.png (Add a recording and slides)
[7]: https://github.com/bigpipe/bigpipe
[8]: https://www.drupal.org/project/smart_date
[9]: https://www.drupal.org/project/blazy
[10]: https://www.drupal.org/project/pathauto
[11]: https://www.drupal.org/project/metatag
[12]: https://www.drupal.org/project/yoast_seo
[13]: https://simplytest.me/
[14]: https://github.com/shaal/DrupalPod
