[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Provision Kubernetes NFS clients on a Raspberry Pi homelab)
[#]: via: (https://opensource.com/article/20/6/kubernetes-nfs-client-provisioning)
[#]: author: (Chris Collins https://opensource.com/users/clcollins)

Provision Kubernetes NFS clients on a Raspberry Pi homelab
======
Create dynamic persistent volumes on a Raspberry Pi Kubernetes cluster
with the NFS-client provisioner.
![Ships at sea on the web][1]

Ephemeral containers are useful, but sometimes data needs to persist between containers or be shared among multiple containers. The solution is mounting external volumes inside the containers, and this is done in Kubernetes with persistent volumes. In large, public cloud deployments, Kubernetes has integrations with the cloud providers' block-storage backends, allowing developers to create claims for volumes to use with their deployments, and Kubernetes works with the cloud provider to create a volume and mount it in the developers' pods.

You can replicate this same behavior in a "private cloud at home" Kubernetes cluster using the network filesystem (NFS)-client provisioner from the [Kubernetes Incubator][2] external storage project.

![Raspberry Pi with a USB hard drive][3]

(Chris Collins, [CC BY-SA 4.0][4])

In a previous article, I explained how to set up an [NFS server with a Raspberry Pi][5]. You can use this NFS server to back the storage provided by the NFS-client provisioner. The provisioner runs a container that mounts an NFS export from your NFS server and carves it up into "volumes" when a persistent volume claim is created, requesting volumes for a pod. [Kubernetes supports NFS volume types natively][2] and handles mounting the volumes inside the containers when a pod starts.

The NFS-client provisioner gives the benefit of dynamically provisioned volumes and makes a homelab cluster behave similarly to a Kubernetes cluster in the cloud. In addition, because these are NFS volumes, they can support multi-read/multi-write operations, so multiple pods can have the volumes mounted at the same time. This is useful for load-balanced services like a webserver, where multiple pods can be spread across multiple nodes to handle traffic and provide greater availability. NFS volumes can also be created that support only read/write-once operations. This is better for database or other instances, where the software writing to the volume does not handle multiple write operations nicely.

### Persistent volumes, persistent volume claims, and storage classes

[**Persistent volumes**][6] are volumes backed by non-ephemeral storage that can be mounted as a volume inside a container. Data written into that volume persists across container restarts and can be mounted into new pods when they replace old ones. In the case of NFS volumes, the volumes can be mounted into multiple containers at the same time, allowing the data to be shared.

Developers can request a persistent volume from Kubernetes with a [**persistent volume claim**][7] (PVC). This is exactly what it sounds like: a request for a volume that matches certain conditions, such as access mode or size, and that can be claimed and used for a project. Persistent volumes request specific volume types using storage classes.

[**Storage classes**][8] describe types of volumes that can be claimed, allowing developers to choose volume types that will work best with what they need. Administrators can create multiple types of storage classes to meet specific needs, like access mode or size (as mentioned above) or even speed/IOPS classes or different backend technologies. Storage classes can also specify a particular provisioner or software in charge of creating and managing the volumes.

Cluster administrators can maintain a large pool of pre-provisioned volumes created manually to satisfy the storage classes, but that requires hands-on work and does not scale well. With a dynamic volume provisioner, software can handle the creation of volumes on-demand when a new claim is created. By default, the NFS-client provisioner has a single storage class, and PVCs that request volumes from this storage class are fulfilled by the provisioner.

### The NFS-client provisioner

The [NFS-client provisioner][9] is part of the Kubernetes Incubator project. In a Kubernetes cluster, this provisioner runs in a container that mounts an NFS export from an _existing_ NFS server—it does not run an NFS server itself. With the container, it listens for PVCs that match its storage class, creates directories within the NFS export, and reports each directory to Kubernetes as a persistent volume. Kubernetes can then mount the volume into a container that uses the volumes from that PVC.

Installation of the NFS-client provisioner can be done with a Helm chart, as described in the project's [README][10], but both for educational reasons and because this tutorial is about running a Kubernetes cluster on Raspberry Pis and needs a few adjustments, you will install it manually on a private-cloud-at-home cluster.

### Prerequisites

There are two prerequisites before you can use the NFS-client provisioner:

  1. Find the details of the NFS server (the IP address and path to the export)
  2. Install the NFS libraries on each of the Kubernetes nodes that might run pods that need the NFS volumes



If you installed your own NFS server, such as the one in [_Turn your Raspberry Pi homelab into a network filesystem_][5], you should already know the server's IP address and the path to its exported filesystem. Make sure the export list includes all the Kubernetes nodes that might run pods with the NFS volumes.

You also need to install the NFS libraries on each of these nodes, so they will be able to mount the NFS volumes. On Ubuntu, Raspbian, or other Debian-based operating systems, you can install the `nfs-common` package using `apt`. For Red Hat-based distributions, install the `nfs-utils` package.

With the prerequisites out of the way, you can move on to installing the NFS-client provisioner onto the Kubernetes cluster.

### Installation

The NFS-client provisioner is deployed using standard Kubernetes objects. You can find these in the Kubernetes Incubator external storage project within the `nfs-client` directory. To get started, clone the `https://github.com/kubernetes-incubator/external-storage` repository:


```
# Clone the external-storage repo
# (output omitted)
$ git clone <https://github.com/kubernetes-incubator/external-storage.git>
```

The specific pieces needed to install the NFS-client provisioner are in `nfs-client/deploy`:


```
$ cd external-storage/nfs-client/deploy
$ ls
class.yaml           deployment.yaml  rbac.yaml        test-pod.yaml
deployment-arm.yaml  objects          test-claim.yaml
```

Note that the `objects` directory contains everything from its parent directory, just broken out to a single file per object.

Before doing anything else, you must create the appropriate role-based access control (RBAC) permissions to allow the NFS-client provisioner service account to mount volumes, create PVCs, etc. They can be created on the cluster with the `kubectl create` command.

If you plan to deploy the provisioner in a namespace other than the default namespace, make sure to change the namespace in the RBAC and deployment files first:


```
# Create the RBAC permissions needed by the provisioner
kubectl create -f rbac.yaml
serviceaccount/nfs-client-provisioner created
clusterrole.rbac.authorization.k8s.io/nfs-client-provisioner-runner created
clusterrolebinding.rbac.authorization.k8s.io/run-nfs-client-provisioner created
role.rbac.authorization.k8s.io/leader-locking-nfs-client-provisioner created
rolebinding.rbac.authorization.k8s.io/leader-locking-nfs-client-provisioner created
```

Next, create a deployment for the NFS-client provisioner pod. If you created your Kubernetes cluster by following the [_Build a Kubernetes cluster with the Raspberry Pi_][11] instructions or you created your own on an ARM-based system, you will need to modify and deploy using the `deployment-arm.yaml` file. If you are using an x86_64-based system, use the `deployment.yaml` file.

Edit the file with your editor of choice. You need to change four things. First, set the three environment variables from the `.spec.template.containers.env` list:

  * Change the value for `PROVISIONER_NAME` to `nfs-storage` (optional; this just makes it a little more human-friendly).
  * Change the `NFS_SERVER` value to the IP address of your NFS server.
  * Change the `NFS_PATH` value to the path of your NFS export.



Finally, under `.spec.template.spec.volumes.nfs`, change the `server` and `path` values to the same ones you set for the `NFS_SERVER` and `NFS_PATH`, respectively.

For example, in an NFS server and export path of `192.168.2.123:/srv`, the `deployment-arm.yaml` file would look like this:


```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nfs-client-provisioner
  labels:
    app: nfs-client-provisioner
  namespace: default
spec:
  replicas: 1
  strategy:
    type: Recreate
  selector:
    matchLabels:
      app: nfs-client-provisioner
  template:
    metadata:
      labels:
        app: nfs-client-provisioner
    spec:
      serviceAccountName: nfs-client-provisioner
      containers:
        - name: nfs-client-provisioner
          image: quay.io/external_storage/nfs-client-provisioner-arm:latest
          volumeMounts:
            - name: nfs-client-root
              mountPath: /persistentvolumes
          env:
            - name: PROVISIONER_NAME
              value: nfs-storage
            - name: NFS_SERVER
              value: 192.168.2.123
            - name: NFS_PATH
              value: /srv
      volumes:
        - name: nfs-client-root
          nfs:
            server: 192.168.2.123
            path: /srv
```

Once the `deployment-arm.yaml` file has been modified, create the deployment with the `kubectl create` command:


```
# Create the deployment
$ kubectl create -f deployment-arm.yaml
deployment.apps/nfs-client-provisioner created

# Check that the deployment created the provisioner pod correctly
$ kubectl get po
NAME                                      READY   STATUS    RESTARTS   AGE
nfs-client-provisioner-6ddfb9bb6d-x4zwt   1/1     Running   0          54s
```

If everything worked correctly, the NFS-client provisioner is now running in your cluster. If the pod has the status `ContainerCreating`, and it does not eventually change to `Running`, check for any relevant events using the `kubectl get events` command. Make sure that the user "nobody" has write permissions on the export directory on the NFS server. If there are no issues, move on to creating the storage class.

The `class.yaml` file needs to be modified to set the `provisioner` value to `nfs-storage` or whatever you set for the `PROVISIONER_NAME` value in the `deployment-arm.yaml`. This tells Kubernetes which provisioner needs to be used to fulfill PVCs for this storage class. Assuming you choose `nfs-storage`, the `class.yaml` file should look like this:


```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: managed-nfs-storage
provisioner: nfs-storage # or choose another name, must match deployment's env PROVISIONER_NAME'
parameters:
  archiveOnDelete: "false"
```

Create the storage class with the `kubectl create` command:


```
# Create the storage class
$ kubectl create -f class.yaml
storageclass.storage.k8s.io/managed-nfs-storage created

# Verify the storage class was created
$ kubectl get storageClass
NAME                  PROVISIONER   RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
managed-nfs-storage   nfs-storage   Delete          Immediate           false
```

Success! The NFS-client provisioner is now installed in the Kubernetes cluster and prepared to dynamically allocate persistent storage volumes for your pods in response to persistent volumes claims against the `managed-nfs-storage` storage class.

### Test your new volume provisioner

With the provisioner installed and configured, you can test it out by creating a PVC that requests a persistent volume and a pod to mount the volume. Luckily, test objects are provided with the files used for the deployment: `test-claim.yaml` and `test-pod.yaml`.

Before creating a PVC and a pod, take a look at what is already there. Unless you have already created some, there should not be any persistent volumes nor PVCs:


```
# Look for existing persistent volumes
$ kubectl get persistentvolumes
No resources found in default namespace.

# Look for existing persistent volume claims
$ kubectl get persistentvolumeclaims
No resources found in default namespace.
```

Now, create a new PVC from the `test-claim.yaml` file:


```
# Create a test PVC
$ kubectl create -f test-claim.yaml
persistentvolumeclaim/test-claim created

$ kubectl get persistentvolumeclaims
NAME         STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS          AGE
test-claim   Bound    pvc-bdf41489-abe4-4508-8adc-74e80f70c626   1Mi        RWX            managed-nfs-storage   7s
```

From the output above, you can see a PVC named `test-claim` was created and bound. This claim is tied to a volume named `pvc-bdf41489-abe4-4508-8adc-74e80f70c626` that was created automatically by the NFS-client provisioner. Also, note the `STORAGECLASS` is called `managed-nfs-storage`—the name of the storage class you created.

Do not worry about the `CAPACITY` value. The NFS-client provisioner does not have a way to enforce storage quota; NFS does not have that feature. The `1Mi` is a placeholder.

Now that the PVC and its associated persistent volume have been created by the NFS-client provisioner, log into your NFS server and check out what happened on that end:


```
# From the NFS host, with the directory used for the NFS export
$ ls -la
total 4
drwxr-xr-x  3 nobody  root      73 May 25 18:46 .
drwxr-xr-x 21 root   root    4096 May 25 17:37 ..
drwxrwxrwx  2 nobody nogroup    6 May 25 18:45 default-test-claim-pvc-bdf41489-abe4-4508-8adc-74e80f70c626
```

A new directory has been created that follows the naming convention `namespace-pvc_name-pv_name`. This directory is initially empty. You can create a test pod to mount this directory via NFS and write to it.

First, if your cluster is using Raspberry Pis or other ARM-based hosts, the `test-pod.yaml` file needs to be modified to use a busybox image created for ARM hosts. The default will pull from the `gcr.io` registry but does not have the correct architecture for the `sh` binary, resulting in "exec format" errors. If your Kubernetes cluster is running on x86_64 hosts, you can skip this step.

Change the `test-pod.yaml` file to use the `docker.io/aarch64/busybox:latest` container image. Your file should look like this:


```
kind: Pod
apiVersion: v1
metadata:
  name: test-pod
spec:
  containers:
  - name: test-pod
    image: docker.io/aarch64/busybox:latest
    # image: gcr.io/google_containers/busybox:1.24
    command:
     - "/bin/sh"
    args:
     - "-c"
      - "touch /mnt/SUCCESS &amp;&amp; exit 0 || exit 1"
    volumeMounts:
      - name: nfs-pvc
        mountPath: "/mnt"
  restartPolicy: "Never"
  volumes:
    - name: nfs-pvc
      persistentVolumeClaim:
        claimName: test-claim
```

The pod described in the file will create a busybox container, mount the NFS volume from the `test-claim` persistent volume to `/mnt` inside the container, and create a file named `SUCCESS`.


```
# Creae the test pod container
$ kubectl create -f test-pod.yaml
pod/test-pod created

# Validate the container ran without problem
$ kubectl get po
NAME                                      READY   STATUS      RESTARTS   AGE
nfs-client-provisioner-6ddfb9bb6d-x4zwt   1/1     Running     0          20m
test-pod                                  0/1     Completed   0          65s
```

If the container ran correctly and the status is `Completed`, then check the contents of the volume on your NFS server:


```
# From the NFS server, within the directory for the PVC
$ ls default-test-claim-pvc-bdf41489-abe4-4508-8adc-74e80f70c626/
SUCCESS
```

Success indeed! The pod was able to mount the NFS volume created by the NFS-client provisioner and write to it!

Clean up the test pod and PVC with the `kubectl delete` command:


```
# Cleanup the test-pod pod
$ kubectl delete po test-pod
pod "test-pod" deleted

# Cleanup the test-claim pvc
$ kubectl delete pvc test-claim
persistentvolumeclaim "test-claim" deleted
```

### Turn up the volume(s)

Thanks to the NFS-client provisioner and your NFS server, you can now request persistent volumes to use with your pods by creating PVCs, and the claims will be automatically filled with dynamically provisioned NFS volumes. This mirrors, in most aspects, how Kubernetes works with dynamic provisioners in large public clouds and allows you to use a workflow like one you would use with a public cloud provider. In fact, a benefit of storage classes is the abstraction created between the PVCs and the volume providers. This allows you to use storage classes with the same name and different providers between on-premises private clouds and any of the public cloud providers, making it easier to "lift-and-shift" workloads between them.

By using NFS, you can support multi-read and multi-write operations on the volumes, too, allowing multiple pods to use the volumes at the same time. As mentioned, this is great for load-balanced web servers or similar services and allows you to scale your services across multiple nodes at the same time.

Best of all, the NFS-client provisioner is automatic, dynamically creating volumes within the NFS export so that they do not have to be manually provisioned ahead of time!

Take your new NFS-client provisioner out for a spin, and create some projects that need persistent storage. Perhaps try (shameless plug incoming) [deploying InfluxDB and Grafana on Kubernetes to collect Twitter stats][12].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/kubernetes-nfs-client-provisioning

作者：[Chris Collins][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/clcollins
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/kubernetes_containers_ship_lead.png?itok=9EUnSwci (Ships at sea on the web)
[2]: https://github.com/kubernetes-incubator/external-storage
[3]: https://opensource.com/sites/default/files/uploads/rpi_nfs_server.jpg (Raspberry Pi with a USB hard drive)
[4]: https://creativecommons.org/licenses/by-sa/4.0/
[5]: https://opensource.com/article/20/5/nfs-raspberry-pi
[6]: https://kubernetes.io/docs/concepts/storage/persistent-volumes/
[7]: https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims
[8]: https://kubernetes.io/docs/concepts/storage/storage-classes/
[9]: https://github.com/kubernetes-incubator/external-storage/tree/master/nfs-client
[10]: https://github.com/kubernetes-incubator/external-storage/tree/master/nfs-client#with-helm
[11]: https://opensource.com/article/20/5/kubernetes-raspberry-pi
[12]: https://opensource.com/article/19/2/deploy-influxdb-grafana-kubernetes
