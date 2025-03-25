[#]: subject: "Setting Up Ollama With Docker"
[#]: via: "https://itsfoss.com/ollama-docker/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Setting Up Ollama With Docker
======

[![Warp Terminal][1]][2]

[Ollama][3] has been a game-changer for running large language models (LLMs) locally, and I've covered quite a few tutorials on setting it up on different devices, including my Raspberry Pi.

But as I kept experimenting, I realized there was still another fantastic way to run Ollama: inside a Docker container.

Now, this isn’t exactly breaking news. The first [Ollama Docker image][4] was released back in 2023. But until recently, I always used it with a native install.

It wasn’t until I was working on an [Immich][5] tutorial that I stumbled upon [NVIDIA Container Toolkit][6], which allows you to add GPU support to Docker containers.

That was when I got hooked on the idea of setting up Ollama inside Docker and leveraging GPU acceleration.

In this guide, I’ll walk you through two ways to run Ollama in Docker with GPU support:

  1. Using a one liner `docker run` command.
  2. With Docker compose



Now, let’s dive in.

📋

Before we get started, if you haven’t installed Docker yet, check out our previous tutorials on setting up [Docker on Linux][7].

### Prerequisite: Installing Nvidia Container toolkit

The NVIDIA Container Toolkit includes the NVIDIA Container Runtime and the NVIDIA Container Toolkit plugin for Docker, which enable GPU support inside Docker containers.

Before installation, make sure that you have already installed the GPU drivers on your specific distro.

Now, to install the NVIDIA Container Toolkit, follow these steps:

  1. Enable the NVIDIA CUDA repository on your system by running the following commands in a terminal window:



```

    distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
    curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    sudo apt update

```

![If your Nvidia GPU driver is not properly installed, you might encounter some problems when installing nvidia-container-toolkit on your system just like in my case on Debian 12.][8]

  2. Install the NVIDIA Container Toolkit by running the following command in a terminal window:



```

    sudo apt install -y nvidia-container-toolkit

```

![][9]

  3. Restart the Docker service to apply the changes:



```

    sudo systemctl restart docker

```

### Method 1: Running Ollama with Docker run (Quick Method)

If you just want to spin up Ollama in a container without much hassle, this one-liner will do the trick:

```

    docker run -d --name ollama -p 11434:11434 -v ollama:/root/.ollama ollama/ollama

```

Or, if you want the GPU support:

```

    docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama

```

Here's a breakdown of what's going on with this command:

  * `docker run -d`: Runs the container in detached mode.
  * `--name ollama`: Names the container "ollama."
  * `-p 11434:11434`: Maps port 11434 from the container to the host.
  * `-v ollama:/root/.ollama`: Creates a persistent volume for storing models.
  * `ollama/ollama`: Uses the official Ollama Docker image.



![][10]

Once the container is running, you can check its status with:

```

    docker ps

```

### Method 2: Running Ollama with Docker compose

I personally find that [docker compose][11] is a more structured approach when setting up a service inside a container, as it's much easier to manage.

💡

If you're setting up Ollama with Open WebUI, I would suggest to use `docker volumes` instead of `bind mounts` for a less frustrating experience.

We'll start with creating a `docker-compose.yml` file, to manage the Ollama container:

```

    version: '3.8'

    services:
      ollama:
        image: ollama/ollama
        container_name: ollama
        ports:
          - "11434:11434"
        volumes:
          - ollama:/root/.ollama
        deploy:
          resources:
            reservations:
              devices:
                - driver: nvidia
                  count: all
                  capabilities: [gpu]
        restart: unless-stopped

    volumes:
      ollama:

```

![][12]

With the `docker-compose.yml` file in place, start the container using:

```

    docker-compose up -d

```

![][13]

This will spin up Ollama with GPU acceleration enabled.

### Accessing Ollama in Docker

Now that we have Ollama running inside a Docker container, how do we interact with it efficiently?

There are two main ways:

##### 1\. Using the Docker shell

This is really easy, you can access Ollama container shell by typing:

```

    docker exec -it ollama <commands>

```

![][14]

but typing this same command overtime can be tiring. We can create an **alias** to make it shorter.

Add this to your `.bashrc` file:

```

    echo 'alias ollama="docker exec -it ollama ollama"' >> $HOME/.bashrc
    source $HOME/.bashrc

```

and since I'm using `zsh` shell, I'll be using this command:

```

    echo 'alias ollama="docker exec -it ollama ollama"' >> $HOME/.zshrc

```

Now, instead of typing the full `docker exec` command, you can just run:

```

    ollama ps
    ollama pull llama3
    ollama run llama3

```

![][15]

This makes interacting with Ollama inside Docker feel just like using a native install.

##### 2\. Using Ollama’s API with Web UI Clients

Ollama exposes an **API** on `http://localhost:11434`, allowing other tools to connect and interact with it.

If you prefer a graphical user interface (GUI) instead of the command line, you can use several Web UI clients.

Some popular tools that work with Ollama include:

  * [**Open WebUI**][16] – A simple and beautiful frontend for local LLMs.
  * [**LibreChat**][17] – A powerful ChatGPT-like interface supporting multiple backends.



We’ve actually covered [12 different tools that provide a Web UI for Ollama][18].

Whether you want something lightweight or a full-featured alternative to ChatGPT, there’s a UI that fits your needs.

### Conclusion

Running Ollama in Docker provides a flexible and efficient way to interact with local AI models, especially when combined with a UI for easy access over a network.

I’m still tweaking my setup to ensure smooth performance across multiple devices, but so far, it’s working well.

On another note, diving deeper into NVIDIA Container Toolkit has sparked some interesting ideas. The ability to pass GPU acceleration to Docker containers opens up possibilities beyond just Ollama.

I’m considering testing it with **Jellyfin** for hardware-accelerated transcoding, which would be a huge boost for my media server setup.

Other projects, like Stable Diffusion or AI-powered upscaling, could also benefit from proper GPU passthrough.

That said, I’d love to hear about your setup! Are you running Ollama in Docker, or do you prefer a native install? Have you tried any Web UI clients, or are you sticking with the command line?

Drop your thoughts in the comments below.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ollama-docker/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/ollama/
[4]: https://ollama.com/blog/ollama-is-now-available-as-an-official-docker-image
[5]: https://immich.app/
[6]: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/index.html
[7]: https://itsfoss.com/install-docker-ubuntu/
[8]: https://itsfoss.com/content/images/2025/03/nvidia-container-toolkit-repo-add.png
[9]: https://itsfoss.com/content/images/2025/03/nvidia-container-toolkit-installation.png
[10]: https://itsfoss.com/content/images/2025/03/docker-run-method-1.png
[11]: https://linuxhandbook.com/docker-compose-quick-start/
[12]: https://itsfoss.com/content/images/2025/03/ollama-compose-stack.png
[13]: https://itsfoss.com/content/images/2025/03/docker-compose-method-for-ollama-1.png
[14]: https://itsfoss.com/content/images/2025/03/docker-exec-command-1.png
[15]: https://itsfoss.com/content/images/2025/03/ollama-alias-2.png
[16]: https://github.com/open-webui/open-webui
[17]: https://github.com/danny-avila/LibreChat
[18]: https://itsfoss.com/ollama-web-ui-tools/
