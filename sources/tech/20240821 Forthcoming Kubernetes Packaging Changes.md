[#]: subject: "Forthcoming Kubernetes Packaging Changes"
[#]: via: "https://fedoramagazine.org/forthcoming-kubernetes-packaging-changes/"
[#]: author: "Brad Smith https://fedoramagazine.org/author/buckaroogeek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Forthcoming Kubernetes Packaging Changes
======

![][1]

Image by Kate Efimova, @kefimochi on twitter.

Starting with Fedora Linux 41 (currently rawhide, late October 2024 release target), Kubernetes RPMs will transition from a single Kubernetes version for each Fedora Linux release to multiple versions for each release. The planned versioned Kubernetes RPMs will include all versions currently supported by the Kubernetes team.

### Repackaging

The initial release of the versioned RPMs in Rawhide will include the following:

  * Kubernetes 1.31 (RPM named as kubernetes1.31)
  * Kubernetes 1.30 (kubernetes1.30)
  * Kubernetes 1.29 (kubernetes1.29)



This change uncouples the link between Fedora Linux releases and Kubernetes versions. This allows Kubernetes cluster administrators, using Fedora Linux as their machine operating system, to update Kubernetes or update Fedora Linux without a forced change to the other component.

The unversioned RPMs for Kubernetes in rawhide (v1.29) will continue to receive updates until February 2025.

The Kubernetes team has three (3) releases each year, along with monthly patch updates. Fedora Linux 41 goes live with Kubernetes 1.31, 1.30, and 1.29. Kubernetes 1.28 will be close to end-of-life and Kubernetes 1.27 will no longer be supported.

Each Kubernetes release in Fedora has 4 rpms (Kubernetes v1.31 as an example):

  1. kubernetes1.31 – contains the kubelet runtime present on each machine in the cluster.
  2. kubernetes1.31-client – contains the kubectl command line client used by cluster administrators.
  3. kubernetes1.31-kubeadm – contains the optional kubeadm command line client used to initialize or upgrade machines that are part of a cluster.
  4. kubernetes1.31-systemd – contains Kubernetes systemd units that are used in manually initialized clusters. If kubeadm is used to initialize the cluster then this rpm is not needed.



Kubernetes is developed using the [Go language][2] with each Kubernetes release developed with a specific version of Go. This can constrain the releases of Kubernetes available for a specific Fedora version. Fedora 39, for example went live with Go v1.21 which excludes Kubernetes 1.30 and 1.31 which rely on Go v1.22.

Kubernetes v1.29 is the last version deployed using the original, unversioned kubernetes rpm name. Plain kubernetes-1.29 rpms will be available with updates in Fedora 40 and 41 until Kubernetes v1.29 goes end-of-life in late February 2025. The unversioned Kubernetes rpm will be retired in Fedora 42.

### Internal changes

The versioned Kubernetes rpms have several internal changes worth noting since they may change how a cluster is configured by an administrator.

First, these rpms no longer create the kube sysuser that was the user identity for a some kubelet related files. This change brings the default user and group ownership of kubelet files and directories in line with the standard set by the Kubernetes developers.

Second, when using kubeadm to initialize a machine to join a cluster, kubelet is configured by a kubelet configuration file. Older Fedora Kubernetes rpms use command line configuration parameters which are now mostly deprecated. This change brings kubelet configuration in line with recommendations from the Kubernetes team. See the [Quick Doc][3] referenced below for more detailed information on configuration options and recommendations for Fedora machines.

Third, the default settings of the kubelet related systemd service files found in the kubernetesX.XX and kubernetesX.XX-kubeadm rpms are now consistent with the same files from the Kubernetes team. These changes are needed to enable the adoption of the kubelet configuration file standard.

In addition to versioned Kubernetes rpms, the CRI-O and CRI-Tools rpms are also versioned for Fedora. Both CRI-O and CRI-Tools are designed to version match the Kubernetes cluster they are used with. Version matching happens at the ‘minor’ level of the semantic versioning standard (semver.org) used by all three products. A version of 1.31.1, for example, has a MAJOR version of 1, a MINOR version of 31, and a PATCH version of 1. Patch version updates for Kubernetes, CRI-O, or CRI-Tools should not cause any issues – provided that you follow general [Kubernetes node upgrade guidelines (https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/upgrading-linux-nodes/)][4].

### Further information

More information on Kubernetes RPMs and versions in Fedora Linux is available at <https://docs.fedoraproject.org/en-US/quick-docs/using-kubernetes/>.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/forthcoming-kubernetes-packaging-changes/

作者：[Brad Smith][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/buckaroogeek/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/06/Kubernetes_Packaging_Changes-816x345.jpg
[2]: https://go.dev
[3]: https://docs.fedoraproject.org/en-US/quick-docs/using-kubernetes/
[4]: https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/upgrading-linux-nodes/
