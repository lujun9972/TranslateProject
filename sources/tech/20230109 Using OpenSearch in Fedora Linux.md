[#]: subject: "Using OpenSearch in Fedora Linux"
[#]: via: "https://fedoramagazine.org/using-opensearch-in-fedora-linux/"
[#]: author: "Jeffrey Choi https://fedoramagazine.org/author/gpoy92/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Using OpenSearch in Fedora Linux
======

![][1]

Photo by [Markus Winkler][2] on [Unsplash][3]

OpenSearch is Amazon’s open-source search engine and analytics suite. Individuals, businesses, and organizations can use the service to search for a wide range of information and use visualization tools to better understand user behavior and search trends. This article will discuss how you can use OpenSearch in Fedora Linux.

### Prerequisites

  * A Linux Distribution ([Fedora OS][4])
  * [Amazon Web Services (AWS) Account][5]
  * [OpenSearch and OpenSearch Dashboards][6]



### What can OpenSearch do?

OpenSearch provides several features and tools. These are:

  * Applications that monitor and debug your cluster.
  * Manage security and event information.
  * Enable seamless, personalized search results.
  * A web-based user interface for searching and browsing search results.
  * The ability to search for specific terms or phrases within a document or webpage.
  * The ability to filter search results by date, relevance, or other criteria.
  * The ability to create and save searches for later use.
  * The ability to customize the appearance and functionality of the search results page.
  * Advanced analytics and reporting tools to help users understand and analyze search traffic and user behavior.



The following sections will guide you through the basics of creating a domain, uploading test data, and visualizing your information with OpenSearch Dashboards.

### What is an OpenSearch Service domain?

An OpenSearch Service domain is a service provided by AWS that allows you to create, manage, and configure your cluster(s) using either the AWS console or the AWS command-line interface (CLI). This tutorial, will use the AWS console to create and configure your domain.

### Getting started

To begin the domain setup, launch your preferred browser and log in to your AWS console. Navigate to the Amazon OpenSearch Service page, then click _Create domain_.

![][7]

Choose your domain name and leave the _Enable custom endpoint_ box unmarked.

![][8]

OpenSearch is a fork of Elasticsearch version 7.10. You can choose any version up to Elasticsearch version 7.10 in addition to OpenSearch versions.

Choose _Development and testing_ for your deployment type, the most recent OpenSearch version, and enable compatibility.

![][9]

Leave _Auto-Tune_ enabled and _Add maintenance window_ unmarked.

![][10]

The _Data nodes_ options allows you to customize your nodes based on the needs of your applications:

  * _Availability Zones_ (AZ)
    * Amazon Web Services (AWS) Availability Zones are physically separate and isolated data center locations within an AWS region. Each Availability Zone is designed to be fault-tolerant, with redundant power, networking, and cooling infrastructure.
  * _Instance type:_
    * Refers to the type of virtual server you’d like to use for your application.
  * _Number of nodes:_
    * The number of nodes you’d like to allocate to each of your AZs.



Since we’re running in a small development setting, set your AZ to 2, your _Instance type_ to _t3.small.search_, and _Number of nodes_ to 2. Don’t change the default settings for your _Storage type_, _EBS volume type_, and _EBS storage size per node_.

![][11]

Ignore these options for now, but read on for more information:

  * _Warm and cold data storage_:
    * For use cases that require a cost effective solution for storing large amounts of non-mutable data.
  * _Dedicated master nodes_
    * Allows you to choose how many master nodes you’d like to use for your domain.
  * _Snapshot configuration_:
    * Set to hourly by default.



![][12]

VPC access is recommended for production environments. You’ll also need to create a master user login to access OpenSearch Dashboards, OpenSearch’s data visualization tool. We’ll discuss how to use OpenSearch dashboards after you configure your domain.

Select _Public access_ and _Create master user_, and set up your login.

![][13]

Leave _Prepare SAML authentication_ and _Enable Amazon Cognito authentication_ option boxes unchecked and select _Only use fine-grained access control_ for your access policy.

![][14]

![][15]

Select _Use AWS owned key_, ignore the optional configurations, click _Create_ to create your domain, then wait for your domain to activate.

### Using OpenSearch Dashboards

OpenSearch Dashboards is a tool that allows you to create and customize interactive dashboards to visualize the data your site receives from user interaction. These dashboards are visual representations of data from various sources such as logs, metrics, and security events, which can be customized to meet your specific needs, including:

  * Dragging and dropping different types of visualizations, such as graphs, maps, and tables, onto a dashboard.
  * Filtering and manipulating data to highlight specific trends or patterns.
  * Sharing dashboards with other users or embedding them in other applications.
  * Collaborating with other users in real-time on the same dashboard.



Navigate to domains and select it from the list.

![][16]

Click _OpenSearch Dashboards URL_ to access your OpenSearch Dashboard.

![][17]

You’ll be presented with one of the following screens after you’ve logged into your dashboard:

![Upon first login][18]

![Upon subsequent logins][19]

### Visualization options

Click _Add sample data_ to add sample data provided by AWS.

![][20]

You may select any of the three options. The _Sample web logs_ option will be used, here, to view examples of types of visualization options you can use to analyze your data.

![][21]

![][22]

![][23]

![][24]

![][25]

![][26]

Click _Create new_ to add more visualization options:

![][27]

### **Analyze your own data to analyze**

You can upload one or more of your documents by entering commands through a CLI.

### **Add a single document**

```

    curl -XPUT -u 'master-user:[master-user-password]' 'domain-endpoint/[domain name]/_doc/1' -d '{"field1": "string1", "field2": ["string3","string4"]}' -H 'Content-Type: application/json'

```

### **Add multiple documents**

Create a JSON file with your documents and run a command to add multiple documents:

##### JSON file format:

```

    { "index" : { "_index": "indexname", "_id" : "2" } }
    {"field1": "string1", "field2": ["string2", "string3", "string4"], "field3": 1234, "field4": ["String, 5", "String, 6"]}
    { "index" : { "_index": "indexname", "_id" : "3" } }
    {"field5": "string7", "field6": ["string8", "string9", "string10"], "field7": 5678, "field8": ["String, 11", "String, 12"]}
    { "index" : { "_index": "indexname", "_id" : "4" } }
    {"field9": "string13", "field10": ["string14", "string15", "string16"], "field11": 1011, "field12": ["String, 17", "String, 18"]}

```

##### JSON file naming restrictions:

  * All letters must be lowercase.
  * Index names cannot begin with _ or – .
  * Index names can’t contain spaces, commas, : , ” , * , + , / , \ , | , ? , # , > , or < .



##### Command to run:

```

    curl -XPOST -u 'master-user:[master-user-password]' 'domain-endpoint/_bulk' --data-binary @bulk_[domain name].json -H 'Content-Type: application/json'

```

You can now create and configure your own domain and use OpenSearch Dashboards to visualize the data your domain receives.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/using-opensearch-in-fedora-linux/

作者：[Jeffrey Choi][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/gpoy92/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/01/open_search-816x345.jpg
[2]: https://unsplash.com/es/@markuswinkler?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/afW1hht0NSs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://docs.fedoraproject.org/en-US/fedora/f36/install-guide/
[5]: https://aws.amazon.com/
[6]: https://opensearch.org/docs/latest/install-and-configure/index/
[7]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-9.png
[8]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-8.png
[9]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-10.png
[10]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-12.png
[11]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-18.png
[12]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-21.png
[13]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-22.png
[14]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-23.png
[15]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-9.png
[16]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-24-1024x145.png
[17]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-25-1024x314.png
[18]: https://fedoramagazine.org/wp-content/uploads/2022/12/image-26.png
[19]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-1024x671.png
[20]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-1-1024x581.png
[21]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-2-1024x305.png
[22]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-3-1024x244.png
[23]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-4-1024x227.png
[24]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-5.png
[25]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-6.png
[26]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-7.png
[27]: https://fedoramagazine.org/wp-content/uploads/2023/01/image-8.png
