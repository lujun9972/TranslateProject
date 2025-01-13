[#]: subject: "Running Stable Diffusion with AUTOMATIC1111 locally"
[#]: via: "https://fedoramagazine.org/running-stable-diffusion-with-automatic1111-locally/"
[#]: author: "Sumantro Mukherjee https://fedoramagazine.org/author/sumantrom/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running Stable Diffusion with AUTOMATIC1111 locally
======

![][1]

Generative AI continues to make strides, enabling developers and enthusiasts to create everything from realistic images to intricate artworks using AI models. Stable Diffusion, one of the leading image generation models, allows users to generate high-quality images from text prompts. AUTOMATIC1111 provides a powerful and user-friendly interface for running Stable Diffusion locally, offering a range of customization options and extensions.

In this article, we will cover:

  1. Setting up Stable Diffusion with AUTOMATIC1111 on Fedora.
  2. Running Stable Diffusion on localhost.
  3. Integrating Stable Diffusion with OpenWebUI.
  4. Generating images using prompts and interacting with LLaMA 3.3.



### What is Stable Diffusion?

[Stable Diffusion][2] is a state-of-the-art text-to-image generation model developed by Stability AI. It is designed to take natural language prompts and generate corresponding images with impressive fidelity and diversity. Unlike cloud-based solutions, running Stable Diffusion locally ensures greater control, privacy, and flexibility.

### What is AUTOMATIC1111?

[AUTOMATIC1111][3] is a popular web-based interface for Stable Diffusion, designed for ease of use while offering extensive features for customization, fine-tuning, and extension support. With a clean UI and powerful backend, it has become the go-to solution for those looking to run Stable Diffusion locally.

### Setting Up Stable Diffusion with AUTOMATIC1111

Before starting, ensure your Fedora system meets the following requirements:

  * Python 3.10 or later installed (I’ve tested with 3.10.14 and 3.10.16)
  * NVIDIA GPU with CUDA support (for GPU-based inference) or AMD
  * Sufficient disk space for model files (at least 10GB)
  * Podman installed (for OpenWebUI integration)



#### **Installing Dependencies**

```

    $ sudo dnf install make gcc openssl-libs zlibrary-devel bzip2-devel readline-devel sqlite3pp-devel wget
    curl llvm ncurses* xz-devel tk-devel libffi-devel zlib* liblzma* openssl*

```

#### **Setting Up Python with pyenv**

To manage different Python versions efficiently, we recommend using pyenv. Follow these steps to install and configure Python 3.10 using pyenv:

  1. **Install pyenv** : curl <https://pyenv.run> | bash
  2. **Install Python 3.10 using pyenv** : pyenv install 3.10
  3. **Set Python 3.10 as the global version** : pyenv global 3.10



![][4]

It is now necessary to export $PATH to bashrc and reload bashrc to complete the pyenv setup. The following commands will help.
**Pyenv will prompt** : export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init - bash)"
**Reloading .bashrc** : source .bashrc

### Cloning the AUTOMATIC1111 Repository

AUTOMATIC1111 provides a GitHub repository that contains all necessary scripts for running Stable Diffusion locally. Let’s start by creating a directory.

$ mkdir stable-diffusion && cd stable-diffusion

Clone the repository using the following command:

```

    wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

```

Making the webui.sh : chmod +x webui.sh
Running ./webui.sh

![][5]

Note : if you are getting this error:

_RuntimeError: Torch is not able to use GPU; add –skip-torch-cuda-test to COMMANDLINE_ARGS variable to disable this check_

executing the command .webui.sh as follows should help!

```

    export COMMANDLINE_ARGS="--medvram --opt-split-attention --skip-torch-cuda-test"
    ./webui.sh

```

Once the interface is running, open your browser and navigate to <http://localhost:7860> to start generating images using text prompts.

### Integrating Stable Diffusion with OpenWebUI

OpenWebUI provides a unified graphical interface for interacting with multiple AI models, including LLMs like LLaMA. Integrating Stable Diffusion with OpenWebUI allows users to interact with both text and image generation models from a single interface.

#### Running OpenWebUI with Stable Diffusion Support

To enable Stable Diffusion in OpenWebUI, we need OpenWebUI to run locally with models loaded the appropriate container configuration. The process is explained in my previous article for [running Open WebUI and Llama locally][6]. Once everything is set, we need to kill all instances of webui.sh and relaunch it with two switches as follows:

```

    ./webui --listen --api

```

![][7]

Loading OpenwebUI’s setting for any Admin/User profile will have a section for Images and one should be able to add the Automatic1111’s base URL in my case it’s 127.0.0.1:7860.

### Interacting with LLaMA 3.3 and Generating Images

Once OpenWebUI is up and running with Stable Diffusion integrated, you can start interacting with LLaMA 3.3. Here’s how you can generate an image using a prompt:

  1. Input a creative text prompt.
  2. Allow LLaMA 3.3 to process the prompt and pass it to Stable Diffusion.
  3. View the generated image directly in the OpenWebUI interface.



![][8]

In my case, Llama3.3 gave me an elaborate prompt for my rudimentary string. The image icon can be used to generate the image.

### Conclusion

By following this guide, you can set up Stable Diffusion with AUTOMATIC1111 on Fedora and enhance your experience by integrating it with OpenWebUI. This setup provides a powerful local environment for both text and image generation, offering flexibility, privacy, and impressive results. Whether you’re a developer, artist, or AI enthusiast, running these models locally opens up new possibilities for creativity.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/running-stable-diffusion-with-automatic1111-locally/

作者：[Sumantro Mukherjee][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sumantrom/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/01/running_stable_diffusion-816x345.jpg
[2]: https://github.com/Stability-AI/stablediffusion
[3]: https://github.com/AUTOMATIC1111/stable-diffusion-webui
[4]: https://fedoramagazine.org/wp-content/uploads/2025/01/pyenv-setup-complete-1024x640.png
[5]: https://fedoramagazine.org/wp-content/uploads/2025/01/stable-diff-webui-exe-1024x640.png
[6]: https://fedoramagazine.org/running-generative-ai-models-locally-with-ollama-and-open-webui/
[7]: https://fedoramagazine.org/wp-content/uploads/2025/01/integration-936x1024.png
[8]: https://fedoramagazine.org/wp-content/uploads/2025/01/final-result-904x1024.png
