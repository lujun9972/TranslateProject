[#]: subject: "Installing Navidrome on Fedora Linux using Podman"
[#]: via: "https://fedoramagazine.org/installing-navidrome-on-fedora-linux-using-podman/"
[#]: author: "Nico Shetty https://fedoramagazine.org/author/nicoshetty/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing Navidrome on Fedora Linux using Podman
======

![][1]

Photo by [Patrick Fore][2] on [Unsplash][3] [modified]

**Navidrome** is an open-source music server that lets you stream your personal audio collection anywhere. It gives you freedom to listen to your music collection from any browser or mobile device. It’s like your personal Spotify!

In this guide, we will explore how to get Navidrome up and running securely using **Podman** on Fedora Linux. Best of all, because **Navidrome** builds official multi-architecture container images including, _linux/amd64_ , l _inux/arm64_ , and _linux/arm/v6/v7_ , this setup is highly portable. Whether your hardware is a standard _x86 PC server_ or a low-powered _ARM-based Raspberry Pi,_ this walk-through has you covered.

For the official image for Navidrome Music Server go to:

![][4]

### [deluan/navidrome – Docker Image][5]

## [][6]

### Using the official container images with Podman and Podman Compose

[Container images][5] are available for the _linux/amd64_ , _linux/arm/v6_ , _linux/arm/v7_ and _linux/arm64_ platforms. They include everything needed to run Navidrome

```

    [nico@stamfordbridge navidrome\]$ podman pull deluan/navidrome
    ✔ docker.io/deluan/navidrome:latest
    Trying to pull docker.io/deluan/navidrome:latest…
    Getting image source signatures
    Copying blob 75c0824146ea done |
    Copying blob 4f4fb700ef54 done |
    Copying blob 4f4fb700ef54 done |
    Copying blob e1dbf20ea67c done |
    Copying blob 1cc3d825d8b2 done |
    Copying config 0c9bad3bd7 done |
    Writing manifest to image destination
    0c9bad3bd7305815d56fe588a64f9172a8bb6aa2bfef3ad77e764c8694e7e860

```

If you have SELinux enabled on your Fedora Linux server, then add the container_file_t SELinux context to the Data and Music directories and its contents.

```

    [nico@stamfordbridge navidrome]$ sudo semanage fcontext -a -t container_file_t  '/home/nico/navidrome/Data(/.\*)?'

    [nico@stamfordbridge navidrome]$ sudo semanage fcontext -a -t container_file_t  '/home/nico/navidrome/Music(/.\*)?'

```

Apply the SELinux policy to the Data and Music directories.

```

    [nico@stamfordbridge navidrome]$  sudo restorecon -R /home/nico/navidrome/Data

    [nico@stamfordbridge navidrome]$  sudo restorecon -R /home/nico/navidrome/Music

```

Change the owner of the /home/nico/navidrome/Data and /home/nico/navidrome/Music to 1000.

```

    [nico@stamfordbridge navidrome]$ podman unshare chown 1000:1000 /home/nico/navidrome/Data

    [nico@stamfordbridge navidrome]$ podman unshare chown 1000:1000 /home/nico/navidrome/Music

```

### **Using podman-compose :**

Create a podman-compose.yml file with the following content (or add the navidrome service below to your existing file):

```

    [nico@stamfordbridge navidrome]$ cat podman-compose.yml
    version: "3"
    services:
      navidrome:
        image: deluan/navidrome:latest
        user: 1000:1000 # should be owner of volumes
        ports:
          - "4533:4533"
        restart: unless-stopped
        environment:
          # Optional: put your config options customization here. Examples:
          ND_SCANSCHEDULE: 1h
          ND_LOGLEVEL: info
          ND_SESSIONTIMEOUT: 24h
          ND_BASEURL: ""
        volumes:
          - "/home/nico/navidrome/Data:/data"
          - "/home/nico/navidrome/Music:/music:ro"

```

Start the navidrome container with podman-compose up -d.

```

    [nico@stamfordbridge navidrome]$ podman-compose up -d

```

Note that the environment variables above are just an example and are not required. The values in the example are already the defaults

### Using podman command line tool:

```

    [nico@stamfordbridge navidrome]$ podman run -d - name navidrome - restart=unless-stopped - user $(id -u):$(id -g) -v /home/ec2-user/navidrome/Music:/music -v /home/ec2-user/navidrome/Data:/data -p 4533:4533 -e ND_LOGLEVEL=info deluan/navidrome:latest
    c00c31d49ec5e0f0a0141aef9e2b69abf6a1b5f0604515bc7111f3e0ef398237

    [nico@stamfordbridge navidrome]$ podman ps -a
    CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
    c00c31d49ec5 docker.io/deluan/navidrome:latest 9 seconds ago Up 9 seconds 0.0.0.0:4533->4533/tcp navidrome

```

### Customization

  * The user argument should ideally reflect the UID:GID of the owner of the music library to avoid permission issues. For testing purposes you could omit this directive, but as a rule of thumb you should not run a production container as root.
  * Remember to change the volumes paths to point to your local paths. /data is where Navidrome will store its DB and cache, /music is where your music files are stored.
  * Configuration options can be customized with environment variables as needed. For podman-compose just add them to the environment section or the yml file. For podman CLI use the -e parameter. e.g.: -e ND_SESSIONTIMEOUT=24h.
  * If you want to use a configuration file with Navidrome running in Podman, you can create a navidrome.toml config file in the /data folder and set the option ND_CONFIGFILE=/data/navidrome.toml.



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/installing-navidrome-on-fedora-linux-using-podman/

作者：[Nico Shetty][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/nicoshetty/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/install_navidrom_using_podman-816x345.jpg
[2]: https://unsplash.com/@patrickian4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/selective-focus-photo-of-alphabet-and-latter-tile-cPDH2ChdBps?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://us1.discourse-cdn.com/fedoraproject/original/3X/3/4/3411c1e20a9e54eb9fddf736c94decb90f825aa1.png
[5]: https://hub.docker.com/r/deluan/navidrome
[6]: https://discussion.fedoraproject.org/t/installing-navidrome-using-podman/202608#p-532684-installing-with-podman-1
