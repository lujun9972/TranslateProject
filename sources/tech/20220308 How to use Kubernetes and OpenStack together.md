[#]: subject: "How to use Kubernetes and OpenStack together"
[#]: via: "https://opensource.com/article/22/3/kubernetes-openstack"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to use Kubernetes and OpenStack together
======
Work is done collaboratively on both sides and there are support systems
in place for both OpenStack and Kubernetes.
![Gears above purple clouds][1]

In OpenStack's [2021 User Survey][2], the majority of respondents said they use Kubernetes as the container orchestration or Platform-as-a-Service (PaaS) tool to manage their OpenStack applications. Simply put, OpenStack and Kubernetes work together to benefit sysadmins, developers, and users alike.

It's one thing to say that users rely on these two technologies, but I wanted to know how. I've found several typical use cases.

### Kubernetes on OpenStack

Kubernetes needs to run somewhere, and that somewhere can be in an OpenStack virtual machine. Because OpenStack was designed and implemented to be run at scale, it enables a Kubernetes cluster to do the same. OpenStack's APIs provide a consistent abstraction layer for Kubernetes to integrate with.

### OpenStack in a Kubernetes container

Kubernetes containers provide independence and a relatively lightweight scaffolding for running a highly available infrastructure. One reason to use containers is that they provide quick infrastructure deployment and teardown with a lot of flexibility. Running a containerized OpenStack gives you the benefits of containers, along with all of the power and scalability of OpenStack.

This is a startup script I've seen in use that demonstrates the ease with which one can create a new host and Kubernetes instance on OpenStack:


```


#!/usr/bin/env bash
CWD="$(pwd)"
${OSH_INFRA_PATH:="../openstack-helm-infra"}
pushd ${OSH_INFRA_PATH}
make dev-deploy setup-host
make dev-deploy k8s
popd

```

### Standalone OpenStack with Kubernetes

Maybe you have another infrastructure provider for running your Kubernetes cluster, but you want to capitalize on how you're storing data and you don't like the provider's solutions. Well, several OpenStack services have been adapted to run without Nova for compute. The SIG cloud provider has a variety of plugins available for integration with a Kubernetes cluster. There are plugins not just for storage but also for controlling ingress, auto-healing, webhook authentication authorization, and key management. If you don't need all of what OpenStack brings to the table but still want to leverage some of its services with Kubernetes, you're able to do that, as well.

![API information][3]

(Kendall Nelson, CC BY-SA 4.0)

### Kubernetes on Ironic-provisioned hardware

[Ironic][4], OpenStack's bare metal provisioning service, configures the infrastructure required to run containers. This gives the Kubernetes containers the advantage of directly integrating with compute, network, and storage resources. Usually, container runtimes obfuscate this from users as a matter of security, but in deployments where users don't need separation, the operators can interact with the cluster and make changes more rapidly. Running Kubernetes containers directly on top of hardware that has been provisioned by Ironic allows the agility of containers to alleviate daily operator struggles like deployment and upgrades.

For more detail on the various ways Kubernetes and OpenStack work together, check out [this PyCon presentation][5].

### Next step: Try it out!

So what now? Now that you know how to use OpenStack and Kubernetes together, dig in! Try them out with a local DevStack install, and see if there is a combination that works for you. Depending on the use case, there may be a fusion of the two communities that brings value to your efforts. Or, if you see a gap that needs to be bridged, get involved and call it to the attention of the communities!

### Two open source communities, one world of open infrastructure

While there are many technical ways these projects fit together, the real message is that your infrastructure can be even better and solve more of your users' problems when you use the advantage of _two_ open source communities that work together.

Work is done collaboratively on both sides and there are support systems in place for both OpenStack and Kubernetes.

OpenStack's project teams work to make their services stand alone and on upgrading deployment services to integrate with Kubernetes. They grow and enhance projects like Kuryr to bridge containers and OpenStack's networking. The OpenStack services teams are always looking for help. Got some feedback or hit a roadblock? Reach out on the [openstack-discuss mailing list][6].

On the Kubernetes side, SIG Cloud Provider works on developing and growing the list of plugins available in [Cloud Provider OpenStack][7] to supplement and integrate Kubernetes containers. They test the integration points to ensure their project runs on an OpenStack infrastructure. Not sure how to configure the plugin or wondering what some option enables? Join the [#provider-openstack k8s][8] Slack channel, and ask away!

The people who make up the Kubernetes and OpenStack communities actively go out of their way to collaborate. For a long time in the tech community, a commonly held misconception was that the two projects would be pitted against each other forever, vying for dominance, but the narrative has changed. Kubernetes and OpenStack work together. They integrate just about any way needed to make operators' lives easier and the user capabilities more flexible and fast.

Considering the number of developers, documentation writers, users, and operators all working on making the two software projects better and more synergistic, why wouldn't you use them together? Two separate communities might support Kubernetes and OpenStack, but we're all working together to further the progress and success of _one_ world of open infrastructure.

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/kubernetes-openstack

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/chaos_engineer_monster_scary_devops_gear_kubernetes.png?itok=GPYLvfVh (Gears above purple clouds)
[2]: https://openinfra.dev/user-survey/
[3]: https://opensource.com/sites/default/files/k8s-openstack.png
[4]: https://wiki.openstack.org/wiki/Ironic
[5]: https://www.youtube.com/watch?v=v3cbX2C4fdc
[6]: http://lists.openstack.org/cgi-bin/mailman/listinfo/openstack-discuss
[7]: https://www.youtube.com/watch?v=ZHYUGmlSs-s
[8]: http://slack.kubernetes.io/
