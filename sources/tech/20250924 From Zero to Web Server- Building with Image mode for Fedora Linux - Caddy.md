[#]: subject: "From Zero to Web Server: Building with Image mode for Fedora Linux & Caddy"
[#]: via: "https://fedoramagazine.org/from-zero-to-web-server-building-with-image-mode-for-fedora-linux-caddy/"
[#]: author: "Clément Verna https://fedoramagazine.org/author/cverna/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

From Zero to Web Server: Building with Image mode for Fedora Linux & Caddy
======

![][1]

Photo by [Sardar Faizan][2] on [Unsplash][3]

Image mode for Fedora Linux leverages [bootable containers][4]. This technology enables [OCI containers to serve as a transport and delivery mechanism for operating system content][4]. This article will guide you through how to use that technology to quickly create a Web Server using [Caddy][5]

### Introduction

Bootable containers leverage existing OCI container tools (like Podman and Docker) and transport protocols for operating system management. This streamlines the configuration and distribution of operating systems through Containerfiles and container registries. The [Universal Blue (ublue) community][6] has embraced this technology, offering diverse operating systems. They also provide a [project template][7] to simplify the creation of custom operating systems.

### Using the image-template repository

We will begin by using the image-template GitHub repository to create our own repository. For this guide I have named it _fedora-web-server._

![][8]

If you don’t have a GitHub account, you can simply clone the repository to your local machine and rename it to reflect your project’s name.

```

    $ git clone git@github.com:<username>/fedora-web-server.git
    $ cd fedora-web-server

```

### Using Fedora Bootc 42 as base image

Image-template simplifies custom OS creation by providing a pre-built structure and essential files. To begin building our web server, we need to choose a base image. While image-template defaults to the ublue Bazzite image, we’ll switch to _quay.io/fedora/fedora-bootc:42_. Make this change by editing the Containerfile (see immediately below) and replacing the default _Base Image_.

```

    # Allow build scripts to be referenced without being copied into the final image
    FROM scratch AS ctx
    COPY build_files /

    # Base Image
    FROM quay.io/fedora/fedora-bootc:42

    RUN --mount=type=bind,from=ctx,source=/,target=/ctx \
       --mount=type=cache,dst=/var/cache \
       --mount=type=cache,dst=/var/log \
       --mount=type=tmpfs,dst=/tmp \
       /ctx/build.sh

    ### LINTING
    ## Verify final image and contents are correct.
    RUN bootc container lint

```

_fedora-bootc_ is a minimal image designed for customized installations. For this project, I’ll install _cloud-init_ to facilitate deployment and testing both in the cloud and locally. I’ll modify the _build_files/build.sh_ script, which is executed from within the _Containerfile_ , to incorporate _cloud-init_ into our customized OS.

The _build.sh_ file will appear as follow:

```

    #!/bin/bash

    set -ouex pipefail

    ### Install packages
    dnf5 install -y --setopt=install_weak_deps=0 cloud-init

```

Since I want to keep my OS minimal I am not installing weak dependencies.

### Installing Caddy

Caddy is an open-source, modern web server known for its simplicity, security, and automatic configuration—it “just works.” For our Fedora Bootc server, we’ll run Caddy using its container image, _docker.io/caddy_. We’ll leverage quadlet for seamless integration with systemd, allowing our Caddy container to operate like any other systemd service. Create the following file:

```

    $ cd build_files
    $ touch caddy.container

```

and enter the following text into _caddy.contatiner_ :

```

    [Unit]
    Description=Caddy Web Server
    After=network-online.target

    [Container]
    Image=docker.io/caddy:2-alpine
    PublishPort=80:80
    PublishPort=443:443
    Memory=512m
    Volume=/var/caddy-data/:/data:Z
    Volume=/var/caddy-config/:/config:Z
    Volume=/var/log/caddy/:/var/log/caddy:Z
    Volume=/etc/caddy:/etc/caddy:Z
    Volume=/var/www/:/var/www:Z

    [Service]
    Restart=always

    [Install]
    # Start by default on boot
    WantedBy=multi-user.target

```

For those familiar with systemd services, the syntax and directives will be recognizable. The [Container] section declares the image to be used, the ports to be published, and the volumes to be shared between the host and the container.

We can now modify the _build.sh_ to copy that file in our custom OS, as shown here:

```

    #!/bin/bash

    set -ouex pipefail

    ### Install packages
    dnf5 install -y --setopt=install_weak_deps=0 cloud-init

    # Copy caddy.container to /etc/containers/systemd/caddy.container
    cp /ctx/caddy.container /etc/containers/systemd/caddy.container

```

### Configuring Caddy

The final step to create a working Caddy server is to add the configuration file. Let’s create a Caddyfile:

```

    $ touch Caddyfile

```

and enter the text shown below:

```

    # Caddy configuration with automatic Let's Encrypt certificates
    # Replace 'your-domain.com' with your actual domain name

    # For automatic HTTPS with Let's Encrypt, use your domain name instead of :80
    # your-domain.com {
    #    root * /var/www
    #    file_server
    #    log {
    #        output file /var/log/caddy/access.log
    #    }
    # }

    # For local development (HTTP only)
    :80 {
         root * /var/www
         file_server
         log {
             output file /var/log/caddy/access.log
         }
    }

```

We can now copy that file in our OS, by editing _build.sh_

```

    #!/bin/bash

    set -ouex pipefail

    ### Install packages
    dnf5 install -y --setopt=install_weak_deps=0 cloud-init

    # Copy caddy.container to /etc/containers/systemd/caddy.container
    cp /ctx/caddy.container /etc/containers/systemd/caddy.container


    # Create /etc/caddy directory and copy Caddyfile
    mkdir -p /etc/caddy
    cp /ctx/Caddyfile /etc/caddy/Caddyfile

```

To complete the setup, we’ll use systemd.tmpfiles to create Caddy’s necessary internal directories. This approach is essential because /var in bootable containers is mutable through overlayfs, meaning it’s only created at runtime and isn’t part of the container build process. Systemd.tmpfiles provides a straightforward solution to this limitation. Modify your _build.sh_ file as follow:

```

    #!/bin/bash
    set -ouex pipefail

    ### Install packages
    dnf5 install -y --setopt=install_weak_deps=0 cloud-init

    # Copy caddy.container to /etc/containers/systemd/caddy.container
    cp /ctx/caddy.container /etc/containers/systemd/caddy.container

    # Create /etc/caddy directory and copy Caddyfile
    mkdir -p /etc/caddy
    cp /ctx/Caddyfile /etc/caddy/Caddyfile

    # Create tmpfiles.d configuration to set up /var directories at runtime
    cat > /usr/lib/tmpfiles.d/caddy.conf << 'EOF'
    # Create Caddy directories at runtime
    d /var/log/caddy 0755 root root -
    d /var/caddy-data 0755 root root -
    d /var/caddy-config 0755 root root -
    EOF

```

That’s it. We now have a _Containerfile_ using fedora-bootc:42 as base image, a build script installing cloud-init and installing Caddy via quadlet and copying the Caddy configuration as well as setting up Caddy’s internal directories.

We can now build our custom operating system. The process involved a _Containerfile_ based on fedora-bootc:42, a build script that installed cloud-init and Caddy (configured via quadlet), and the necessary Caddy configuration and directory setup.
If you want your Caddy web server to serve a custom html page, you can copy the following files <https://github.com/cverna/fedora-web-server/tree/main/build_files/web> and edit the build.sh script as follows:

```

    #!/bin/bash

    set -ouex pipefail

    ### Install packages
    dnf5 install -y --setopt=install_weak_deps=0 cloud-init

    # Copy caddy.container to /etc/containers/systemd/caddy.container
    cp /ctx/caddy.container /etc/containers/systemd/caddy.container

    # Create /etc/caddy directory and copy Caddyfile
    mkdir -p /etc/caddy
    cp /ctx/Caddyfile /etc/caddy/Caddyfile

    # Copy web content to /usr/share for the base image
    mkdir -p /usr/share/caddy/web
    cp -r /ctx/web/* /usr/share/caddy/web/

    # Create tmpfiles.d configuration to set up /var directories at runtime
    cat > /usr/lib/tmpfiles.d/caddy.conf << 'EOF'
    # Create Caddy directories at runtime
    d /var/log/caddy 0755 root root -
    d /var/caddy-data 0755 root root -
    d /var/caddy-config 0755 root root -

    # Copy web content from /usr/share to /var at runtime
    d /var/www 0755 root root -
    C /var/www/index.html 0644 root root - /usr/share/caddy/web/index.html
    C /var/www/fedora-logo.png 0644 root root - /usr/share/caddy/web/fedora-logo.png
    C /var/www/caddy-logo.svg 0644 root root - /usr/share/caddy/web/caddy-logo.svg
    EOF

```

### Building the bootable container

The image-template repositories equip you with the necessary tools for local image construction. Let’s begin by verifying that all dependencies are in place.

```

    $ sudo dnf install just git jq podman

```

Then we can run _just_ to build the container. The following shows the just command and subsequent output:

```

    $ just build fedora-web-server latest
    [1/2] STEP 1/2: FROM scratch AS ctx
    [1/2] STEP 2/2: COPY build_files /
    --> Using cache 94ec17d1689b09a362814ab08530966be4aced972050fedcd582b65f174af3a3
    --> 94ec17d1689b
    [2/2] STEP 1/3: FROM quay.io/fedora/fedora-bootc:42
    [2/2] STEP 2/3: RUN --mount=type=bind,from=ctx,source=/,target=/ctx     --mount=type=cache,dst=/var/cache     --mount=type=cache,dst=/var/log     --mount=type=tmpfs,dst=/tmp     /ctx/build.sh &&     ostree container commit
    --> Using cache 8cac20d690bda884b91ae2a555c4239a71f162fbd4ff36a1e2ed5f35f5dfb05a
    --> 8cac20d690bd
    [2/2] STEP 3/3: RUN bootc container lint
    --> Using cache 5cb978e3db5a2bcd437018a6e97e1029d694180002f5fa098aaf540952941dd4
    [2/2] COMMIT fedora-web-server:latest
    --> 5cb978e3db5a
    Successfully tagged localhost/fedora-web-server:latest

```

[Just][9] is a useful tool for running project-specific commands, similar to Makefiles, and uses a ‘justfile’. As the image functions like any other container image, we can inspect it using Podman.

```

    $ podman images
    REPOSITORY                   TAG         IMAGE ID      CREATED      SIZE
    localhost/fedora-web-server  latest      5cb978e3db5a  4 hours ago  1.95 GB
    quay.io/fedora/fedora-bootc  42          586b146c456e  2 days ago   1.88 GB

```

### Building a Disk Image

The disk image for our server is built using _just_ as follows:

```

    $ just build-vm localhost/fedora-web-server latest

```

This will use the [bootc-image-builder][10] project to build a disk image of our bootable container. Once the command has finished, we have a qcow2 image in the output directory

```

    $ ls output/qcow2
    disk.qcow2

```

We can now use that qcow2 image to start a Virtual Machine and run our webserver.

### Running the Web Server

To run the server we can use any virtualization software. In this case I am using virt-install:

```

    $ sudo dnf install virt-install libvirt
    $ virt-install --cloud-init root-ssh-key=/path/to/ssh/public.key --connect qemu:///system --import --name fedora-web-server --memory 2048 --disk output/qcow2/disk.qcow2 --os-variant fedora41
    Starting install...
    Creating domain...
    ...
    Fedora Linux 42 (Adams)
    Kernel 6.16.5-200.fc42.x86_64 on x86_64 (ttyS0)

    enp1s0: 192.168.100.199
    fedora login:

```

Once the virtual machine is up and running, you can use ssh to login as root, using the local IP address of the virtual machine.

```

    $ ssh root@192.168.100.199
    $ bootc status
    ● Booted image: localhost/fedora-web-server:latest
           Digest: sha256:a813a8da85f48d8e6609289dde87e1d45ff70a713d1a9ec3e4e667d01cb470f2 (amd64)
          Version: 42.20250911.0 (2025-09-12T07:36:05Z)

```

Currently, the server’s update capability is limited because the images point to the localhost/fedora-web-server:latest container image. This can be resolved by building and pushing these container images to a container registry such as [quay.io][11] or [ghcr.io][12]. Detailed instructions for these steps are available in the README file of the [ublue-os/image-template repository][13].

To verify that the web server is running successfully, access that same ip address from your web browser and you should get the following web page.

![][14]

### Summary

This guide demonstrates the power of image mode for Fedora Linux using bootc and Caddy to build a lightweight, custom web server. By leveraging container technologies for OS delivery and Caddy for simplified web serving, users can efficiently deploy and manage web applications, setting a strong foundation for future customization. Make sure to check the library of [examples][15] to get ideas on how to use bootc.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/from-zero-to-web-server-building-with-image-mode-for-fedora-linux-caddy/

作者：[Clément Verna][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/cverna/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/09/Image_mode_n_Caddy-816x345.jpg
[2]: https://unsplash.com/@nexio?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-close-up-of-a-green-surface-with-lots-of-lines-MZAofbegXNg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://containers.github.io/bootable/
[5]: http://caddyserver.com
[6]: https://github.com/ublue-os
[7]: https://github.com/ublue-os/image-template
[8]: https://fedoramagazine.org/wp-content/uploads/2025/09/image-1024x115.png
[9]: https://github.com/casey/just
[10]: https://github.com/osbuild/bootc-image-builder
[11]: http://quay.io
[12]: http://ghcr.io
[13]: https://github.com/ublue-os/image-template?tab=readme-ov-file#step-2-initial-setup
[14]: https://fedoramagazine.org/wp-content/uploads/2025/09/image-1-1024x698.png
[15]: https://gitlab.com/fedora/bootc/examples/
