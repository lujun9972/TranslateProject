[#]: subject: "Simplifying Container Management with Podman Pods on Fedora Linux"
[#]: via: "https://fedoramagazine.org/simplifying-container-management-with-podman-pods-on-fedora-linux/"
[#]: author: "Yazan Monshed https://fedoramagazine.org/author/yazanalmonshed/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Simplifying Container Management with Podman Pods on Fedora Linux
======

![][1]

This article, will introduce **Podman Pods** and demonstrate how to use them with a simple application built using Node.js. The app will be lightweight and easy to set up, showcasing the power of running multiple containers in a pod.

### **What is a Podman Pod?**

**Podman pod** is a group of containers that share the same network, storage, and process namespace. Kubernetes pods inspires it. Pods allow you to run multiple containers that need to work closely together, like a web server and a caching service, in a single isolated unit.

Pods in Podman provide a native way to group containers without needing a full Kubernetes setup. This makes them ideal for development and small-scale applications.

### Install Podman

Podman is included by default in Fedora Linux, but if it’s not installed for any reason, you can add it with the following command:

```

    $ sudo dnf install podman -y

```

For Fedora Linux Silverblue users, Podman is already installed in your system. To verify your installation, you can run a quick hello-world container:

```

    $ podman pull hello-world
    $ podman run hello-world

```

If everything is set up correctly, you’ll see output similar to:

```

    Hello from Docker!

```

This shows that Podman is up and running, and ready for the next steps.

### Starting with a Simple Node.js App in a Pod

To start this example, create a simple web application using **Node.js**. First, create a directory for the app:

```

    $ mkdir webapp && cd webapp

```

Inside the webapp directory, create a _package.json_ file that lists the dependencies your project needs:

```

    {
    "dependencies": {
    "express": "*"
    },
    "scripts": {
    "start": "node index.js"
    }
    }

```

Next, create an _index.js_ file that will serve a basic _“Hello World”_ response:

```

    const express = require('express');
    const app = express();

    app.get('/', (req, res) => {
        res.send("Hello World!");
    });

    app.listen(8080, () => {
        console.log("Listening on port 8080");
    });

```

### Create a Dockerfile for the App

Now, create a _Dockerfile_ in the same directory to build the container image for your app:

```

    FROM node:alpine
    WORKDIR /usr/app
    COPY ./ ./
    RUN npm install
    CMD ["npm", "start"]

```

This _Dockerfile_ will pull a lightweight Node.js image, install the necessary dependencies, and start the app.

### Build the Image Using Podman

To build the container image for your app, use the following command:

```

    $ podman build -t webapp .

```

The -t flag names the image _webapp_ , and the **.** specifies the current directory as the build context.

### Create and Run a Pod with Podman

Now that the image is ready, it’s time to create a pod and run the container inside it. First, create a pod:

```

    $ podman pod create --name mypod -p 8080:8080

```

This creates a pod named _mypod_ and maps port 8080 on the host to port 8080 inside the pod.
Next, run the Node.js container inside the pod:

```

    $ podman run -d --pod mypod --name webapp-container webapp

```

The _–pod_ flag specifies that the container should run inside _mypod_.

### Add Another Container to the Pod

One of the key features of pods is the ability to run multiple containers that share resources. For example, let’s add a Redis container to the same pod:

```

    $ podman run -d --pod mypod --name redis-container redis

```

Now, both the _webapp_ and _redis_ containers are running inside the same pod, sharing the network namespace. This means the _webapp_ can communicate with _redis_ over localhost.

### Check Pod and Container Status

The status of the pod and its containers can be verified using:

```

    $ podman pod ps
    $ podman ps --pod

```

These commands will show you the pod’s status and its running containers.

### Stopping and Removing the Pod

To stop the pod and all its containers:

```

    $ podman pod stop mypod

```

To remove the pod and all its containers:

```

    $ podman pod rm mypod

```

### Conclusion

Podman pods offer an easy way to group and manage containers, making it simple to run applications that require multiple containers that must work together. With Podman’s built-in pod support, it is possible to use Kubernetes-like functionality without the complexity.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/simplifying-container-management-with-podman-pods-on-fedora-linux/

作者：[Yazan Monshed][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/yazanalmonshed/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/podman-2-816x389.jpg
