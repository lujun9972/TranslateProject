[#]: subject: "Databricks Open Sources Unity Catalog to Help Manage AI Models and Data"
[#]: via: "https://news.itsfoss.com/databricks-open-sources-unity-catalog/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Databricks Open Sources Unity Catalog to Help Manage AI Models and Data
======
More open-source AI goodness by Databricks, in response to its
competitor, Snowflake.
[![][1]][2]

Thanks to the advent of AI-based solutions, managing data properly and securely for such implementations at scale has become a significant challenge. Many new career paths have opened up due to this, and even organizations that have been established for catering to such requirements.

[Databricks][3] is one such organization that was founded back in 2013 by the creators of Apache Spark, Delta Lake and MLflow which claims to be the “ _world’s first and only lakehouse platform in the cloud_ ”.

In a recent event, they announced their latest move toward embracing open-source that will see them opening up a very popular tool of theirs.

### A Big Announcement: What To Expect?

During their annual [Data + AI Summit][4] event, Ali Ghodsi, CEO of Databricks [announced][5] ( _16:00 timestamp_ ) that [Unity Catalog][6], their solution for governance of data and AI, was going open source under the “ **Unity Catalog OSS** ” name.

Sadly, he **never mentioned which license it would go open-source under** , but, they mentioned it includes an Apache 2.0 licensed open-source server. So, I guess, that's the one.

After its launch, Unity Catalog OSS is set to act as a “ _universal interface_ ” with support for any data format and compute engine.

The developers note that it has support to read tables with Delta Lake, Apache Iceberg, and Apache Hudi clients via Delta Lake UniForm. There's also support for the Iceberg REST Catalog and Hive Metastore (HMS) interface standards.

**In reaction to this move** , many of Databricks' customers such as AWS, AT&T, Google, Rivian, NVIDIA, and more added their views on this.

One such view was by [Jessica Hawk][7], CVP, Data, AI, Digital Applications at Microsoft, who said that:

> Microsoft is committed to the open-source community and empowering customers with choice. Databricks has been a strategic partner for years and it's great to see them open-sourcing Unity Catalog. We believe truly open standards with broad industry participation are in customers' best interests.

As for those who aren't familiar, Unity Catalog is a governance solution that is used for managing data, both structured and unstructured in any format, machine learning models, notebooks, and more.

It also provides users with helpful dashboards to better manage their stack, AI-powered monitoring, with many users around taking advantage of its “ _single permission model_ ” for straightforward access management.

### Want to Check it Out?

Well, at the time of writing, **the code for Unity Catalog OSS was still not up** on the Databricks [GitHub][8] repo.

However, the company has clarified that it will be made available as part of [Matei Zaharia][9]'s keynote during an upcoming session in the summit on Thursday, where we should be able to explore more about it.

Keep an eye out on the repo to take a look at it when it's available on their repo.

[Databricks (GitHub)][8]

If you are eager to learn more about this move, then you can refer to the official [announcement blog][10], and [documentation][11].

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/databricks-open-sources-unity-catalog/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.databricks.com/
[4]: https://www.databricks.com/dataaisummit
[5]: https://www.youtube.com/watch?v=-6dt7eJ3cMs&t=960s
[6]: https://www.databricks.com/product/unity-catalog
[7]: https://www.linkedin.com/in/jessica-hawk-0686561/
[8]: https://github.com/databricks
[9]: https://www.databricks.com/dataaisummit/speaker/matei-zaharia
[10]: https://www.databricks.com/company/newsroom/press-releases/databricks-open-sources-unity-catalog-creating-industrys-only-open
[11]: https://docs.databricks.com/en/data-governance/index.html
