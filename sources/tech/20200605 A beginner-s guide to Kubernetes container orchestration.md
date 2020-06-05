[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (A beginner's guide to Kubernetes container orchestration)
[#]: via: (https://opensource.com/article/20/6/container-orchestration)
[#]: author: (Jiaqi Liu https://opensource.com/users/jiaqi216)

A beginner's guide to Kubernetes container orchestration
======
Understanding the building blocks of container orchestration makes it
easier to get started with Kubernetes.
![Shipping containers stacked in a yard][1]

Last fall, I took on a new role with a team that relies on [Kubernetes][2] (K8s) as part of its core infrastructure. While I have worked with a variety of container orchestrators in my time (e.g., Kubernetes, Apache Mesos, Amazon ECS), the job change sent me back to the basics. Here is my take on the fundamentals you should be familiar with if you're working with Kubernetes.

![Kubernetes logo with a crown][3]

[Container orchestration][4] refers to the tools and platforms used to automate, manage, and schedule workloads defined by individual containers. There are many players in this space, both open source and proprietary, including Hashicorp's [Nomad][5], [Apache Mesos][6], Amazon's [ECS][7], and let's not forget Google's home-grown [Borg][8] project (from which Kubernetes [evolved][9]). There are pros and cons with each technology, but Kubernetes' rising popularity and strong community support make it clear that Kubernetes is currently the king of the container orchestrators.

I also consider Kubernetes to have clear advantages when you're working with open source software. As an open source platform, it is cloud-agnostic, and it makes sense to build other open source software on top of it. It also has a dedicated following with over [40,000 contributors][10], and because a lot of developers are already familiar with Kubernetes, it's easier for users to integrate open source solutions built on top of K8s.

### Breaking down Kubernetes into building blocks

The simplest way to break down Kubernetes is by looking at the core concepts of container orchestrators. There are containers, which serve as

foundational building blocks of work, and then there are the components built on top of each other to tie the system together.

Components come in two core types:

  1. **Workload managers:** A way to host and run the containers
  2. **Cluster managers:** Global ways to make decisions on behalf of the cluster



In Kubernetes lingo, these roles are fulfilled by the worker nodes and the control plane that manages the work (i.e., [Kubernetes components][11]).

#### Managing the workload

Kubernetes worker nodes have a nested layer of components. At the base layer is the container itself.

![A cluster and its components][12]

Technically, containers run in pods, which are the atomic object type within a Kubernetes cluster. Here's how they relate:

  * **Pod:** A pod defines the logical unit of the application; it can contain one or more containers and each pod is deployed onto a node.
  * **Node:** This is the virtual machine serving as the worker in the cluster; pods run on the nodes.
  * **Cluster:** This consists of worker nodes and is managed by the control plane.



Each node runs an agent known as the [kublet][13] for running containers in a pod and a [kube-proxy][14] for managing network rules.

#### Managing the cluster

The worker nodes manage the containers, and the Kubernetes control plane makes global decisions about the cluster.

![The control plane and its components][15]

The control plane consists of several essential components:

  * **Memory store ([etcd][16]):** This is the backend store for all cluster data. While it's possible to run a Kubernetes cluster with a different backing store, etcd, an open source distributed key-value store, is the default.
  * **Scheduler ([kube-scheduler][17]):** The scheduler is responsible for assigning newly created pods to the appropriate nodes.
  * **API frontend ([kube-apiserver][18]):** This is the gateway from which the developer can interact with Kubernetes—to deploy services, fetch metrics, check logs, etc.
  * **Controller manager ([kube-controller-manager][19]):** This watches the cluster and makes necessary changes in order to keep the cluster in the desired state—such as scaling up nodes, maintaining the correct number of pods per replication controller, and creating new namespaces.



The control plane makes decisions to ensure regular operation of the cluster and abstracts away these decisions so that the developer doesn't have to worry about them. Its functionality is highly complex, and users of the system need to have awareness of the logical constraints of the control plane without getting too bogged down on the details.

### Using controllers and templates

The components of the cluster dictate how the cluster manages itself—but how do developers or (human) operators tell the cluster how to run the software? This is where [controllers][20] and templates come in.

Controllers orchestrate the pods, and K8s has different types of controllers for different use cases. But the key ones are [Jobs][21], for one-off jobs that run to completion, and [ReplicaSets][22], for running a specified set of identical pods that provide a service.

Like everything else in Kubernetes, these concepts form the building blocks of more complex systems that allow developers to run resilient services. Instead of using ReplicaSets directly, you're encouraged to use [Deployments][23] instead. Deployments manage ReplicaSets on behalf of the user and allow for rolling updates. Kubernetes Deployments ensure that only some pods are down while they're being updated, thereby allowing for zero-downtime deploys. Likewise, [CronJobs][24] manage Jobs and are used for running scheduled and repeated processes. The many layers of K8s allow for better customization, but CronJobs and Deployments suffice for most use cases.

Once you know which controller to pick to run your service, you'll need to configure it with templating.

#### Anatomy of the template

The Kubernetes template is a [YAML][25] file that defines the parameters by which the containers run. Much like any kind of configuration as code, it has its own specific format and requirements that can be a lot to learn. Thankfully, the information you need to provide is the same as if you were running your code against any container orchestrator:

  * Tell it what to name the application
  * Tell it where to look for the image of the container (often called the container registry)
  * Tell it how many instances to run (in the terminology above, the number of ReplicaSets)



![Deployment Template][26]

Flexibility in configuration is one of the many advantages of Kubernetes. With the different resources and templates, you can also provide the cluster information about:

  * Environment variables
  * Location of secrets
  * Any data volumes that should be mounted for use by the containers
  * How much CPU and memory each container or pod is allowed to use
  * The specific command the container should run



And the list goes on.

### Bringing it all together

![Ship sailing at sea][27]

Combining templates from different [resources][28] allows the user to interoperate the components within Kubernetes and customize them for their own needs.

In a bigger ecosystem, developers leverage Jobs, [Services][29], and Deployments with [ConfigMaps][30] and [Secrets][31] that combine to make an application—all of which need to be carefully orchestrated during deployment.

Managing these coordinated steps can be done manually or with one of the common package-management options. While it's definitely possible to roll your own deployment against the Kubernetes API, it's often a good idea to package your configuration—especially if you're shipping open source software that might be deployed and managed by someone not directly on your team.

The package manager of choice for Kubernetes is [Helm][32]. It doesn't take a lot to [get started with Helm][33], and it allows you to package your own software for easy installation on a Kubernetes cluster.

### Smooth sailing!

The many layers and extensions sitting on top of containers can make container orchestrators difficult to understand. But it's actually all very elegant once you've broken down the pieces and see how they interact. Much like a real orchestra, you develop an appreciation for each individual instrument and watch the harmony come together.

Knowing the fundamentals allows you to recognize and apply patterns and pivot from one container orchestrator to another.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/container-orchestration

作者：[Jiaqi Liu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jiaqi216
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/bus-containers2.png?itok=idd8duC_ (Shipping containers stacked in a yard)
[2]: https://kubernetes.io/
[3]: https://opensource.com/sites/default/files/styles/medium/public/uploads/kuberneteslogo.png?itok=7MO2UZW2 (Kubernetes logo with a crown)
[4]: https://www.redhat.com/en/topics/containers/what-is-container-orchestration
[5]: https://www.nomadproject.io/
[6]: http://mesos.apache.org/
[7]: https://www.nomadproject.io/intro/vs/ecs/
[8]: https://research.google/pubs/pub43438/
[9]: https://medium.com/containermind/a-new-era-of-container-cluster-management-with-kubernetes-cd0b804e1409
[10]: https://kubernetes.io/blog/2020/04/21/contributor-communication/
[11]: https://kubernetes.io/docs/concepts/overview/components/
[12]: https://opensource.com/sites/default/files/styles/medium/public/images/cluster-kubernetes-opensourecom2.png?itok=p81LYPp3 (A cluster and its components)
[13]: https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/
[14]: https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/
[15]: https://opensource.com/sites/default/files/styles/medium/public/images/cluster-kubernetes-control-plane-opensourecom.png?itok=zfraf-6Q (The control plane and its components)
[16]: https://etcd.io/docs/
[17]: https://kubernetes.io/docs/reference/command-line-tools-reference/kube-scheduler/
[18]: https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/
[19]: https://kubernetes.io/docs/reference/command-line-tools-reference/kube-controller-manager/
[20]: https://kubernetes.io/docs/concepts/architecture/controller/
[21]: https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/
[22]: https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
[23]: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
[24]: https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/
[25]: https://yaml.org/
[26]: https://opensource.com/sites/default/files/uploads/deployment-template.png (Deployment Template)
[27]: https://opensource.com/sites/default/files/styles/medium/public/uploads/shipsailing.png?itok=0XhvMF7n (Ship sailing at sea)
[28]: https://kubernetes.io/docs/reference/kubectl/overview/#resource-types
[29]: https://kubernetes.io/docs/concepts/services-networking/service/
[30]: https://kubernetes.io/docs/concepts/configuration/configmap/
[31]: https://kubernetes.io/docs/concepts/configuration/secret/
[32]: https://helm.sh/
[33]: https://opensource.com/article/20/5/helm-charts
