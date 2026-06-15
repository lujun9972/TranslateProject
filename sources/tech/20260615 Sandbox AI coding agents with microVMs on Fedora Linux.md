[#]: subject: "Sandbox AI coding agents with microVMs on Fedora Linux"
[#]: via: "https://fedoramagazine.org/sandbox-ai-coding-agents-with-microvms-on-fedora-linux/"
[#]: author: "Martin Sehnoutka https://fedoramagazine.org/author/msehnout/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Sandbox AI coding agents with microVMs on Fedora Linux
======

![][1]

Photo by [Immo Wegmann][2] on [Unsplash][3]

AI coding agents such as Claude code or Codex get more capable every month. This is great for productivity, but approving all commands gets annoying really quickly. On the other hand, allowing agents to run any command on your work machine is not a great idea. They are really good at exploring your production cluster using kubectl or running remote commands at your production servers over SSH.

Fortunately, Linux distributions come with plenty of options for process isolation. You can run agents as a completely different user, in a container, or in a VM. This article shows how to use microVMs to run coding agents.

### Security concerns

Running AI agents in unattended mode is like running untrusted code. Companies behind these agents, such as Anthropic or Google, are not trying to steal credentials, but people keep coming up with new attack vectors like [Slopsquatting][4] or prompt injections [virtually anywhere][5].

The coding agents themselves ship with built-in mitigations that try to refuse prompt injections as described, for example, [here][6].

[Lightweight sandboxing][7] technologies are another layer of defense in coding agents. On Linux, [bwrap][8] is one of the possible implementations. This raises the bar, yet sandbox escapes are still a problem. Take a look at [CVE-2026-39861][9] as an example of multi-platform sandbox escape.

You could use containers to isolate the agent in their own namespace, but they still share the host kernel. Some of the the recent kernel vulnerabilities resulted in [privilege escalation][10] (switching from regular user to root) suggesting that containers are not enough as a [security boundary][11].

In the rest of this article, I describe how to use microVMs to easily sandbox coding agents on your Fedora Linux.

### Exploring microVMs

First of all, let’s take a look at what microVMs are. Just like any VM, they have their own kernel, one per each microVM. Compared to traditional VMs they start in very short time (hundreds of milliseconds) but don’t offer [all the features][12] of full VMs.

This article explains usage of [krun][13] runtime for podman. This approach offers the same well-known workflow as containers, but simply runs every container as a microVM.

Start by installing the runtime:

```

    dnf install crun-krun

```

To run a microVM, simply run _podman_ with _–runtime=krun_ in your terminal:

```

    podman run --runtime=krun --rm -it fedora:44 /bin/bash

```

### Things to watch out for

A microVM is not a regular container, so a few things might behave differently. First, allocate enough CPU and RAM with krun annotations. The defaults are too small and might result in OOM (Out Of Memory) kills. Second, make sure you have libkrun version >= 1.8. Older versions have a [bug][14] which prevents you from pressing Enter in your coding agent. Third, the microVM ignores the USER set in the Dockerfile and always boots as root. Either switch to the correct user manually or put the switch into an entrypoint script.

### Case study: sandboxing Claude Code for a Python project

This section outlines a simple setup for a Python project managed by [uv][15]. It uses podman-compose to mount the project into the microVM. Compared to containers, this podman compose needs additional annotations for UID/GID translation, SELinux labeling, and HW resources. The final setup is very similar to what you would need for containers.

To install podman compose from official Fedora repositories, run:

```

    dnf install podman-compose

```

The setup has 3 parts:

  * Dockerfile
  * docker-compose.yaml
  * entrypoint.sh



#### Dockerfile

As mentioned above, podman with krun runtime still runs containers, but spawns each of them in a microVM. This example container includes uv package manager, claude code and a few additional RPM packages. Define your own container based on your project dependencies and programming language.

Make sure to create an unprivileged user and use it for running the agent.

```

    FROM fedora:44

    ARG HOST_UID=1000
    ARG HOST_GID=1000

    # Create group and user matching host UID/GID
    RUN groupadd -g ${HOST_GID} appuser && \
        useradd -u ${HOST_UID} -g ${HOST_GID} -m appuser

    RUN mkdir -p /venv && chown appuser:appuser /venv
    RUN mkdir -p /home/appuser/.claude && chown appuser:appuser /home/appuser/.claude

    USER appuser

    # Rarely-changing tooling. Kept above the dnf layer so editing the RPM list
    # below does not invalidate (and re-run) these installs.
    RUN curl -LsSf https://astral.sh/uv/install.sh | sh && \
        curl -fsSL https://claude.ai/install.sh | bash
    USER root

    # Frequently-changing RPMs. Kept last so adding a package only rebuilds from here down.
    RUN dnf install git make vim free libpq-devel python3-devel gcc -y && \
        dnf clean all

    COPY --chown=appuser entrypoint.sh /entrypoint.sh
    RUN chmod +x /entrypoint.sh

    USER appuser
    WORKDIR /app

    # This is needed because entrypoint does not have .local/bin in the PATH
    ENV PATH="/home/appuser/.local/bin:$PATH"
    ENTRYPOINT ["/entrypoint.sh"]
    CMD ["/bin/bash"]

```

#### docker-compose.yaml

The compose file defines how to mount the project directory into the microVM. This is where most of the magic happens, because podman needs to translate UID/GID and manage SELinux labels, otherwise the files would not be accessible inside of the microVM or they would end up being owned by a different user.

```

    services:
      claude:
        container_name: project-name-claude
        annotations:
          run.oci.handler: krun
          krun.ram_mib: "4096"
          krun.cpus: "4"
        user: "${HOST_UID}:${HOST_GID}"
        userns_mode: keep-id  # optional, for rootless host
        build:
          context: .
          args:
            HOST_UID: "${HOST_UID}"  # use UID and GID from the host so that files created in the container have correct permissions
            HOST_GID: "${HOST_GID}"
        volumes:
          - ../:/app:U,z  # bind mount your project
          - project-name-venv-cache:/venv:U,z
          - claude-config:/home/appuser/.claude:U,z  # persistent claude credentials/config
        working_dir: /app
        stdin_open: true
        tty: true
        environment:
          - CLAUDE_CONFIG_DIR=/home/appuser/.claude
          - UV_LINK_MODE=copy
          - UV_PROJECT_ENVIRONMENT=/venv/env  # This is inside the cached volume
          - UV_PYTHON_INSTALL_DIR=/venv/python  # So that uv-managed python installations are not in home but cached in /venv
          - TERM=xterm-256color
          - COLORTERM=truecolor

    volumes:
      project-name-venv-cache:
      claude-config:
        external: true
        name: claude-config

```

There are 3 key parts:

  * annotations – these select krun as a runtime and specify HW requirements
  * [user and userns_mode][16] – this tells podman to translate UID/GID so that the files created in the microVM end up owned by your user on the host
  * [volume labels][17] – z tells podman to relabel the files with a shared SELinux label. Otherwise SELinux would prevent the process inside the microVM from touching the files in the volume. U tells podman to recursively chown all files.



#### entrypoint.sh

The entrypoint creates a virtual environment for the Python project, because we don’t want dynamic dependencies baked into the container image. It also runs the switch from root to regular user because podman with krun runtime ignores the USER directive from the container.

```

    #!/bin/bash
    set -e

    echo "Sandbox started as user: $(id -un) in directory: $(pwd)"

    if [ "$(id -un)" != "appuser" ]; then
      runuser -u appuser -- uv sync
      echo "Running ${@} as appuser"
      exec runuser -u appuser -- "$@"
    fi

    uv sync
    exec "$@"

```

#### Run the setup

First, build the container:

```

    $ HOST_UID=$(id -u) HOST_GID=$(id -g) podman-compose -f .agent-sandbox/docker-compose.yaml build
    STEP 1/18: FROM fedora:44
    ...
    Successfully tagged localhost/agent-sandbox_claude:latest

```

Then create the external volume and run the claude container interactively:

```

    $ podman volume create claude-config
    $ HOST_UID=$(id -u) HOST_GID=$(id -g) podman-compose -f .agent-sandbox/docker-compose.yaml run --rm claude
    Sandbox started as user: root in directory: /app
    Resolved 3 packages in 6ms
    Checked 3 packages in 1ms
    Running /bin/bash as appuser
    tty: ttyname error: Inappropriate ioctl for device
    [appuser@3bd1234b9a77 app]$

```

You can now check that the kernel is different by running uname -a inside of the microVM.

### Putting it together: single script to create the whole setup

Creating the same setup manually for every project is not the greatest user experience, but you can automate the setup using a simple script like [this][18]. It installs a new sbx command that wraps the setup described above into 3 simple command options: init, build, and run.

### A word of caution — microVM is not a bulletproof boundary

A microVM raises the bar considerably, but it is not perfect isolation, and it would be irresponsible to present it as such. Take a look at the [libkrun git repository][13] to read more about the [security model][19].

If you want to run software that might be dangerous, prefer using a full VM or even cloud VM.

### Conclusion

MicroVMs seem like a sweet spot for running AI Agents. They provide a familiar workflow of containers, but the agents run on their own kernel behind a hypervisor. This article describes workflow based on podman and krun runtime because Fedora Linux ships both of them natively, but there are plenty of other options available for any platform (for example [docker][20][sandbox][20]).

_**Note about AI usage:** I wrote this article myself. I used Claude (Anthropic) to significantly refine the grammar, wording, and sentence structure; the technical content and all claims are my own and tested._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/sandbox-ai-coding-agents-with-microvms-on-fedora-linux/

作者：[Martin Sehnoutka][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/msehnout/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/06/sandbox_AI-816x345.jpg
[2]: https://unsplash.com/@tinkerman?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/a-close-up-of-a-word-written-in-sand-LtqT12DQpt4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://en.wikipedia.org/wiki/Slopsquatting
[5]: https://snyk.io/blog/cline-supply-chain-attack-prompt-injection-github-actions/
[6]: https://blog.tomecek.net/post/claude-code-prompt-injection-feb-2026/
[7]: https://code.claude.com/docs/en/sandboxing
[8]: https://github.com/containers/bubblewrap
[9]: https://www.sentinelone.com/vulnerability-database/cve-2026-39861/
[10]: https://fedoramagazine.org/how-fedora-is-responding-to-recent-kernel-vulnerabilities/
[11]: https://emirb.github.io/blog/microvm-2026/
[12]: https://www.qemu.org/docs/master/system/i386/microvm.html
[13]: https://github.com/containers/libkrun
[14]: https://github.com/containers/podman/issues/28067
[15]: https://docs.astral.sh/uv/
[16]: https://www.redhat.com/en/blog/rootless-podman-user-namespace-modes
[17]: https://oneuptime.com/blog/post/2026-03-17-selinux-volume-options-podman/view
[18]: https://github.com/msehnout/agent-sandbox
[19]: https://github.com/containers/libkrun/discussions/538
[20]: https://www.docker.com/products/docker-sandboxes/
