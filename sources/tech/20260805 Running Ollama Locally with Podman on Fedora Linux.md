[#]: subject: "Running Ollama Locally with Podman on Fedora Linux"
[#]: via: "https://fedoramagazine.org/running-ollama-locally-with-podman-on-fedora-linux/"
[#]: author: "Yazan Monshed https://fedoramagazine.org/author/yazanalmonshed/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running Ollama Locally with Podman on Fedora Linux
======

![][1]

Photo by [Mark Hofman][2] on [Unsplash][3]

Running Large Language Models (LLMs) locally has become increasingly popular for development, privacy, and offline testing. Ollama makes this incredibly straightforward, allowing you to run models like Llama 3 or Mistral directly on your machine.

By leveraging Podman on Fedora Linux, you can isolate Ollama inside a container. This approach keeps your host system clean while making it effortless to spin up, manage, and tear down your AI development environment.

### What is Ollama?

Ollama is an open-source framework designed for running, creating, and sharing large language models. It packages model weights, configuration, and data into a unified management system. Running it inside a container means you don’t have to deal with complex local dependencies, Python environments, or complex GPU driver configurations on your base OS.

### Verify or Install Podman

Podman is available by default in Fedora Workstation. It can be easily install, if missing, using DNF:

```

    $ sudo dnf install podman -y

```

For Fedora Linux Silverblue users, Podman is natively available in the immutable base system and no extra steps are necessary.

To verify your installation and ensure everything is running smoothly, execute a quick check:

```

    $ podman --version

```

### Step 1: Create a Persistent Volume for Your Models

LLM weights can be huge—often ranging from 4 GB to over 40 GB, depending on the model size. To avoid downloading these models every time you restart your container, create a persistent Podman volume to store them safely on your host disk:

```

    $ podman volume create ollama_storage

```

### Step 2: Run the Ollama Container

Next, spin up the Ollama container. The following command pulls the official image, attaches the volume we just created, and maps the communication port (

11434

) to your host machine.

```

    $ podman run -d \
      -v ollama_storage:/root/.ollama \
      -p 11434:11434 \
      --name ollama \
      ollama/ollama

```

#### Note on Hardware Acceleration

The command above runs Ollama using your CPU. If you are on Fedora Workstation or Silverblue and want to pass through an Nvidia GPU for fast hardware acceleration, make sure you have the Nvidia Container Toolkit installed and append the GPU flag:

```

    --device nvidia.com/gpu=all

```

### Step 3: Download and Run an AI Model

With the container running in the background, you can interact with it using Podman’s execution command. Let’s pull and run **Llama 3** , a highly capable, lightweight model perfect for local development:

```

    $ podman exec -it ollama ollama run llama3

```

The first time you execute this, Podman will download the model weights into your

ollama_storage

volume. Once the download completes, you will be dropped directly into an interactive terminal prompt:

```

    >>> Send a message (/? for help)
    >>> Tell me a fun fact about Fedora Linux.
    Fedora Linux is named after the iconic felt hat worn by the Red Hat shadowman logo! It started as a community project to provide extra packages for Red Hat Linux.

    >>>
    To exit the interactive prompt, simply type /exit.

```

### Step 4: Interact with the Local API

Because we mapped port 11434 to our host system, you can also interact with your local Ollama instance via its built-in REST API. Open a standard terminal window and send a curl request:

```

    curl http://localhost:11434/api/generate -d '{
      "model": "llama3",
      "prompt": "Why use containers?",
      "stream": false
    }'

```

This returns a structured JSON payload containing your answer, allowing you to easily hook your local model up to web apps, scripts, or IDE extensions.

#### Checking Container Status

To monitor your running local AI instance, use the classic Podman management commands, perhaps starting with:

```

    $ podman ps

```

You can also inspect the logs to make sure the API server is listening properly:

```

    $ podman logs ollama

```

When you are done with your development session and want to free up system memory, stop the container:

```

    $ podman stop ollama

```

If you ever need to completely remove the container environment, use:

```

    $ podman rm ollama

```

Note: Your downloaded models are completely safe inside the ollama_storage volume and will instantly reattach the next time you spin up the container.

### Conclusion

Using Podman to manage Ollama on Fedora Linux or Fedora Silverblue offers a clean, containerized way to build and test applications with LLMs completely offline. It bypasses host environment pollution, isolates large model storage cleanly into a named volume, and treats your AI stack exactly like any other microservice.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/running-ollama-locally-with-podman-on-fedora-linux/

作者：[Yazan Monshed][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/yazanalmonshed/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/07/Ollama_w_Podman-816x346.jpg
[2]: https://unsplash.com/@mzgfsz?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/yellow-and-black-road-sign-on-gray-asphalt-road-during-daytime-TyFPBhn1El0?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
