[#]: subject: "Launch Fedora 40 in Microsoft Azure"
[#]: via: "https://fedoramagazine.org/launch-fedora-40-in-microsoft-azure/"
[#]: author: "Jeremy Cline https://fedoramagazine.org/author/jcline/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Launch Fedora 40 in Microsoft Azure
======

![][1]

Photo by [Mighty Commander][2] on [Unsplash][3]

In Fedora 40, Cloud images for Microsoft Azure are directly available in Azure via its new Community Gallery feature. This article will describe how to use these.

### Introduction

Starting in Fedora 39, the Fedora Project began producing Cloud images for Microsoft Azure which could be manually uploaded to an Azure tenant. In Fedora 40, these images are available directly in Azure via its new Community Gallery feature.

To use Microsoft Azure, you will need a Microsoft account. New users get [12 months of several services free][4], including virtual machines, so you can try everything covered in this article without needing to pay for anything. These virtual machines have 1-2 vCPUs and 1 GiB of RAM, which is enough for development or testing, low traffic web servers, small databases, etc.

### Using the web portal

To get started, go to the [Community images service][5] in the [Azure Portal][6]. Add a filter on Public gallery names and select Fedora’s public gallery name, _Fedora-5e266ba4-2250-406d-adad-5d73860d958f_.

![][7]

Select a Fedora 40 x64 image in a location near you, then click _Create VM_.

![][8]

Alternatively, you can go to the The Fedora Project’s [Cloud section][9], click [Launch in public cloud][10], and select the Azure region to jump directly to the _Create VM_ blade.

#### Configure the VM

Click _Create new_ under the _Resource group_ field. Resource groups are buckets of arbitrary resources (virtual machines, storage accounts, public IP addresses, etc.) which are related. Next, give your virtual machine a name. The name you choose becomes the host name as well as the virtual machine resource name in Azure. After that, you should set the virtual machine size. Click _See all sizes_ and type “B2ats_v2” into the search bar, click on the only result, and click _Select_ at the bottom of your screen.

![][11]

Finally, click _Review + create_ at the bottom of your screen, and then click _Create_.

Download the SSH key it generates for you. Afterwards, you will be taken to a page where you can see your resources being created. Once they’ve all completed, click on _Go to resource_. This will take you to the overview page for your new virtual machine running Fedora 40. Under _Essentials_ you’ll find the public IP address assigned to your instance which you can use to SSH to the virtual machine.

![][12]

Open a terminal, ensure the SSH key you downloaded has proper permissions, and log in to your new machine:

```

    chmod 600 ~/Downloads/<key name>
    ssh -i ~/Downloads/<key name> azureuser@<pubic IP address>

```

![][13]

Finally, if you decide you don’t need the machine anymore, you can clean everything up by deleting the resource group. From the virtual machine overview page, click on the resource group name you created under _Essentials_ , then click _Delete resource group_ and confirm you want to delete it. Everything you created in the resource group is destroyed with it.

### Launch a virtual machine via azure-cli

You may prefer to manage your resources from the command line. The downside of the CLI is it doesn’t guide you through all the options available. The upside is that, if you know what you want, it’s much quicker than clicking through all the options available. This section covers using the CLI to create the exact same virtual machine as the first section.

#### Prerequisites

Install the Azure command-line interface and log in:

```

    sudo dnf install azure-cli
    az login

```

#### Find the Image ID

We need the Fedora 40 image ID in Microsoft Azure to launch the virtual machine from the CLI. Each Fedora release has an _image definition_ for each hardware architecture. Each image definition contains one or more _image versions_. We add new image versions with the latest updates on a regular basis.

First, list all available image definitions in Fedora’s public gallery:

```

    az sig image-definition list-community --public-gallery-name Fedora-5e266ba4-2250-406d-adad-5d73860d958f --location eastus --query '[].name'

```

Optionally, you can list the versions available using an image definition’s name:

```

    az sig image-version list-community --public-gallery-name Fedora-5e266ba4-2250-406d-adad-5d73860d958f --gallery-image-definition "Fedora-Cloud-40-x64" --location eastus --query '[?!excludeFromLatest].uniqueId'

```

Typically, you should use the latest available version of an image definition, which you can reference by replacing the version number in the image version’s _uniqueId_ with _latest_. For example, the image ID for the latest _x86_64_ Fedora 40 image is _/CommunityGalleries/Fedora-5e266ba4-2250-406d-adad-5d73860d958f/Images/Fedora-Cloud-40-x64/Versions/latest_.

#### Create the VM

Begin by creating the resource group:

```

    az group create --location eastus --resource-group fedora-in-azure

```

Next, create the virtual machine using the image ID we found:

```

    az vm create --location eastus --name fedora40 --resource-group fedora-in-azure --image /CommunityGalleries/Fedora-5e266ba4-2250-406d-adad-5d73860d958f/Images/Fedora-Cloud-40-x64/Versions/latest --size Standard_B2ats_v2 --security-type TrustedLaunch --generate-ssh-keys

```

Finally, you can delete everything with:

```

    az group delete --resource-group fedora-in-azure

```

### Conclusion

We have covered the basics for creating Fedora virtual machines in Microsoft Azure. For more in-depth coverage of virtual machine features you can refer to the [virtual machine documentation][14] for Azure. The Azure CLI documentation is also available [online][15].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/launch-fedora-40-in-microsoft-azure/

作者：[Jeremy Cline][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jcline/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/Launch_F40_in_Azure-816x345.jpg
[2]: https://unsplash.com/@mightycommander?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/blue-sky-over-sea-during-daytime-L9yDemsNK0E?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://azure.microsoft.com/en-us/free/
[5]: https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Compute%2Flocations%2FcommunityGalleries%2Fimages
[6]: https://portal.azure.com/
[7]: https://fedoramagazine.org/wp-content/uploads/2024/05/Screenshot-2024-05-01-150951-1024x830.png
[8]: https://fedoramagazine.org/wp-content/uploads/2024/05/Screenshot-2024-05-01-152026-1024x826.png
[9]: https://fedoraproject.org/cloud/
[10]: https://fedoraproject.org/cloud/download#cloud_launch
[11]: https://fedoramagazine.org/wp-content/uploads/2024/05/Screenshot-2024-05-01-152714-1024x827.png
[12]: https://fedoramagazine.org/wp-content/uploads/2024/05/Screenshot-2024-05-01-153339-1024x830.png
[13]: https://fedoramagazine.org/wp-content/uploads/2024/05/Screenshot-2024-05-01-153631-1024x712.png
[14]: https://learn.microsoft.com/en-us/azure/virtual-machines/
[15]: https://learn.microsoft.com/en-us/cli/azure/
