[#]: subject: "Build custom images for Testing Farm"
[#]: via: "https://fedoramagazine.org/build-custom-images-for-testing-farm/"
[#]: author: "Ondrej Babec https://fedoramagazine.org/author/onduss/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Build custom images for Testing Farm
======

![][1]

Image by Ondrej Babec

You may know the **[Testing Farm][2]** from the article written by David Kornel and Jakub Stejskal. That article highlighted the primary advantages of this testing system. You should review the earlier **[article][3]** , as this article will not go through the basics of the Testing Farm usage. It will only delve into the reasons for utilizing your custom images and explore potential automation methods with **[Hashicorp Packer][4]**.

### AWS images

The Testing Farm automatically deploys Amazon Web Services (AWS) machines using a default set of Amazon Machine Images (AMIs) available to users. This curated subset includes popular community images such as CentOS and Fedora Linux. While these AMIs typically represent bare operating systems, they don’t have to remain in that state.

Think of these AMIs as analogous to container images. You have the flexibility to embed all installation and configuration steps directly into the image itself. By doing so, you can preconfigure the environment, ensuring that everything is ready before the actual Testing Farm job begins.

#### The Trade-Off

However, there’s a trade-off. While customizing AMIs streamlines the process, building them manually can be challenging and time-consuming. The effort involved in creating a well-prepared AMI is substantial.

In an upcoming section of this article, we’ll delve into a practical solution. We’ll explore how to use Hashicorp Packer, a powerful tool for creating machine images, and illustrate its application in the context of the **[Debezium project][5]**.

### Benefits of custom images for Testing Farm

There might be some confusion surrounding the rationale for creating custom images, especially considering the investment of time, effort, and resources. However, this question is highly relevant, and the answer lies in a straightforward concept: **time efficiency**.

Imagine you are testing web applications within containers. You must deploy the database, web server, and other supporting systems each time you perform testing. For instance, when testing against an Oracle database, the container image alone can be nearly **10 GB**. Pulling this image for every pull request (PR) takes several minutes.

By building a custom Amazon Machine Image (AMI) that includes this giant image, you eliminate the need to pull it repeatedly. This initial investment pays off significantly in the long run. Additionally, there’s another advantage: reducing unnecessary information exposure to developers. With a preconfigured system, developers can focus solely on the tests without being burdened by extraneous details.

In summary, custom images streamline the testing process, enhance efficiency, and provide a cleaner development experience for your team. Of course, this solution might not be ideal for all use cases and should be used only if it adds value to your testing scenarios. For example, if you are testing packages for Fedora Linux or CentOS and integration with it, you should always use the latest available image on Testing Farm to mitigate the risks associated with a custom image being outdated.

### Automate the process with Packer

The trade-off when considering using custom images is that you must create them. This requirement might discourage some developers from pursuing this route. However, there’s good news: Packer significantly improves this experience.

Initially developed by HashiCorp, Packer is a powerful tool for creating consistent Virtual Machine Images ****for various platforms. AWS (Amazon Web Services) is one of the supported platforms. Virtual Machine images used in an AWS environment are called AMI (Amazon Machine Images).

Descriptions of image builds are written in HCL format and provide a rich set of provisioners. These provisioners act as plugins, allowing developers to execute specific tools within the machine from which Packer generates the image snapshot.

Among the most interesting provisioners are:

  * File — Copies files from the current machine to the EC2 instance.
  * Shell — Executes shell scripts within the machine.
  * Ansible — Enables direct execution of Ansible playbooks on the machine.



In the sections that follow, we’ll explore practical examples and how Packer can enhance your image-building process.

### Debezium use-case

So far, we have discussed the reasons for using custom images and why you should automate the build, but how can you do that? Let’s showcase this on the actual project! We onboarded Testing Farm with the Debezium project last year. Debezium is the de facto industrial standard for CDC (Change Data Capture) streaming. Debezium currently supports about fourteen databases, each with a different setup and hardware needs, but if there is one common feature, it is memory consumption. Suppose those databases run in the container with a minimal amount of RAM (Random Access Memory). In that case, they tend to do things like flushing to disk, etc., and those things are very annoying for testing because you need to rerun the tests after the failures with longer wait times or other workarounds.

Because of that, we have moved part of the testing to the Testing Farm, where we ask for **[sufficient hardware][6]** to ensure databases have enough space and RAM so tests are “stable”. One of the supported databases for Debezium is Oracle DBMS. As was pointed out earlier, Oracle’s container images are quite large, so we had to build the AMI image to give our community the fastest feedback on the PRs.

Firstly, we have started working on the Ansible playbooks, installing everything necessary to run the database and our test suite. This Ansible playbook looks like this:

```

    # oracle_docker.yml

    ---

    - name: Debezium testing environment playbook
      hosts: 'all'
      become: yes
      become_method: sudo

      tasks:
      - name: Add Docker-ce repository
        yum_repository:
          name: docker-ce
          description: Repository from Docker
          baseurl: https://download.docker.com/linux/centos/8/x86_64/stable
          gpgcheck: no

      - name: Update all packages
        yum:
          name: "*"
          state: latest
          exclude: ansible*

      - name: Install dependencies
        yum:
          name: ['wget', 'java-17-openjdk-devel', 'make', 'git', 'zip', 'coreutils', 'libaio']
          state: present

      - name: Install Docker dependencies
        yum:
          name: ['docker-ce', 'docker-ce-cli', 'containerd.io', 'docker-buildx-plugin']
          state: present

      - name: Unzip oracle libs
        unarchive:
          src: /tmp/oracle-libs.zip
          dest: /root/
          remote_src: true

      - name: Install Oracle sqlplus
        shell: |
          wget https://download.oracle.com/otn_software/linux/instantclient/2113000/oracle-instantclient-basic-21.13.0.0.0-1.el8.x86_64.rpm -O sqlplus-basic.rpm
          wget https://download.oracle.com/otn_software/linux/instantclient/2113000/oracle-instantclient-sqlplus-21.13.0.0.0-1.el8.x86_64.rpm -O sqlplus-adv.rpm
          rpm -i sqlplus-basic.rpm
          rpm -i sqlplus-adv.rpm

      - name: Prepare Oracle script
        copy:
          src: /tmp/install-oracle-driver.sh
          dest: /root/install-oracle-driver.sh
          remote_src: true

      - name: Make executable
        shell: chmod +x /root/install-oracle-driver.sh

      - name: Install maven
        shell: |
          mkdir -p /usr/share/maven /usr/share/maven/ref
          curl -fsSL -o /tmp/apache-maven.tar.gz https://apache.osuosl.org/maven/maven-3/3.8.8/binaries/apache-maven-3.8.8-bin.tar.gz
          tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1
          rm -f /tmp/apache-maven.tar.gz
          ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

      - name: Start docker daemon
        systemd:
          name: docker
          state: started
          enabled: true

      - name: Pull Oracle images from quay
        shell: |
          docker pull custom.repo/oracle:{{ oracle_tag }}
          when: use_custom|bool == true

      - name: Pull Oracle images from official repository
        shell: |
          docker pull container-registry.oracle.com/database/free:23.3.0.0
        when: use_custom|bool == false

      - name: Logout from registries
        shell: |
          docker logout quay.io
        when: use_quay|bool == true

```

As you can see, this playbook does everything:

  * Docker installation
  * SQLPlus installation
  * Running some side Oracle init script
  * Installing Maven and all other test suite dependencies
  * Pulling the image



Once all those steps are finished, the machine should be fully prepared to run the test suite and start the database. We can create an image from this machine snapshot. OK, now it’s time to look at the packer descriptor.

```

    # ami-build.pkr.hcl
    packer {
        required_plugins {
            amazon = {
                source  = "github.com/hashicorp/amazon"
                version = "~> 1.2.6"
            }
            ansible = {
                source  = "github.com/hashicorp/ansible"
                version = "~> 1"
            }
        }
    }

    variable "aws_access_key" {
        type      = string
        sensitive = true
    }

    variable "aws_secret_key" {
        type      = string
        sensitive = true
    }

    variable "aws_region" {
        type      = string
        default   = "us-east-2"
    }

    variable "aws_instance_type" {
        type      = string
        default   = "t3.small"
    }

    variable "aws_ssh_username" {
        type      = string
        default   = "centos"
    }

    variable "image_name" {
        type      = string
    }

    variable "oracle_image" {
        type      = string
    }

    variable source_ami {
        type      = string
        default   = "ami-080baaeff069b7464"
    }

    variable "aws_volume_type" {
        type      = string
        default   = "gp3"
    }

    source "amazon-ebs" "debezium" {
        access_key            = var.aws_access_key
        secret_key            = var.aws_secret_key
        source_ami            = var.source_ami
        region                = var.aws_region
        force_deregister      = true
        force_delete_snapshot = true
        instance_type         = var.aws_instance_type
        ssh_username          = var.aws_ssh_username
        ami_name              = var.image_name
        ami_users             = ["125523088429"]


        # choose the most free subnet which matches the filters
        # https://www.packer.io/plugins/builders/amazon/ebs#subnet_filter
        subnet_filter {
            filters = {
                "tag:Class": "build"
            }
            most_free = true
            random = false
        }

        launch_block_device_mappings {
            device_name = "/dev/sda1"
            delete_on_termination = "true"
            volume_type = var.aws_volume_type
            volume_size = 30
        }

    }

    build {
        sources = ["source.amazon-ebs.debezium"]
        name      = "debezium-oracle-packer"

        provisioner "file" {
            source = "./provisioners/files/oracle-libs.zip"
            destination = "/tmp/oracle-libs.zip"
        }

        provisioner "file" {
            source = "./provisioners/files/install-oracle-driver.sh"
            destination = "/tmp/install-oracle-driver.sh"
        }

        provisioner "shell" {
            script            = "./provisioners/scripts/bootstrap.sh"
        }

        provisioner "ansible" {
            playbook_file      = "./provisioners/ansible/oracle_docker.yml"
            extra_arguments    = [ "-vv", "-e oracle_tag="${var.oracle_image}"" ]
            # Required workaround for Ansible 2.8+
            # https://www.packer.io/docs/provisioners/ansible/ansible#troubleshooting
            use_proxy          = false
        }
    }

```

The descriptor above contains all the information necessary for the Packer to build the AMI image. At the start you can see the definitions of all the variables. These are mostly just configuration or sensitive information. Next, you find the configuration of the Amazon plugin (this allows the AMI build). You can see that besides casual configurations like secrets and regions, you also must pass source_ami. This field defines the base image for our build. For Debezium, we are using CentOS Stream 8.

The next important field is _ssh_username_. That field can be very tricky because you can find more variants of the username for some distros. For CentOS, it is usually _centos_ or _ec2-user_. Be careful setting this because debugging during the build process is challenging.

The last important thing, specifically regarding Testing Farm, is the _ami_users_ field. This field contains an array of users with whom Packer will share the new AMI. This step is necessary to use your image in the Testing Farm environment.

The last part of the descriptor contains all the provisioners you want to run before the AMI build starts. For Debezium, we just copy some libraries and init scripts, run the bootstrap script (this script installs initial dependencies – EPEL and Ansible; you can find it below), and trigger the ansible-playbook (showcased above).

```

    # bootstrap.sh
    #!/bin/bash

    set -ex

    sudo yum install -y epel-release
    sudo yum install -y ansible

```

Once all provisioners and descriptors are complete, you put those in the correct file structure. On Debezium, we are use the following:

```

    testing-farm-build
    ├── ami-build.pkr.hcl
    └── provisioners
    ├── ansible
    │   ├── oracle_docker.yml
    │   └── variables.yml
    ├── files
    │   └── install-oracle-driver.sh
    └── scripts
    └── bootstrap.sh

```

Then, you just have to step into the root directory (testing-farm-build) and start the build. You can begin the packer build with the following command:

```

    packer build -var="aws_secret_key=${AWS_SECRET_ACCESS_KEY}" -var="aws_access_key=${AWS_ACCESS_KEY_ID}" -var="image_name=${AMI_NAME}" -var="aws_ssh_username=centos" .

```

You can pass whatever variables you want directly into the command. If you do not want to export some information as an environment variable, do not include it here, and the packer will automatically ask you for it during the build process.

Once your AMI is built, you are only one step away before you can use your image in the Testing Farm environment. You have to open the PR on the Testing Farm **[infrastructure repository][7]** and make the following additions: Add a new regex matcher for your AMI names into the image map – for **[example][8]**
Add your AWS account ID as the new image owner from which Testing Farm will gather images – for **[example][9]**.

After Testing Farm maintainers merge those PRs, your images will be available for provisioning in a couple of minutes. Once they are ready, you should be able to see them **[here][10]**.

### Conclusion

Building your custom image for the Testing Farm unlocks a world of possibilities for enhancing your testing workflow. Creating a tailored image can accelerate test runs and provide targeted feedback to your community. And best of all, the entire image build process can be seamlessly automated using Packer with minimal effort. This article should be a helpful guide for fellow Testing Farm ****users looking to optimize their experience. If you have any questions or need assistance during setup, feel free to reach out — I’m here to help!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/build-custom-images-for-testing-farm/

作者：[Ondrej Babec][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/onduss/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/03/fedora-magazine1-816x345.jpeg
[2]: https://docs.testing-farm.io
[3]: https://fedoramagazine.org/how-to-use-testing-farm-outside-of-rhel/
[4]: https://github.com/hashicorp/packer
[5]: https://github.com/debezium/debezium
[6]: https://docs.testing-farm.io/Testing%20Farm/0.1/test-request.html#hardware
[7]: https://gitlab.com/testing-farm/infrastructure
[8]: https://gitlab.com/testing-farm/infrastructure/-/merge_requests/252/diffs
[9]: https://gitlab.com/testing-farm/infrastructure/-/merge_requests/260#f4b8142718ac81418118aa84eedc3763a061f97c
[10]: https://api.testing-farm.io/v0.1/composes/public
