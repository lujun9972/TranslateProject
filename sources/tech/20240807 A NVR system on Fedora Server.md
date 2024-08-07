[#]: subject: "A NVR system on Fedora Server"
[#]: via: "https://fedoramagazine.org/a-nvr-system-on-fedora-server/"
[#]: author: "Carlos Rodriguez-Fernandez https://fedoramagazine.org/author/carlosrodrifernandez/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A NVR system on Fedora Server
======

![][1]

Photo by [Kelly Sikkema][2] on [Unsplash][3] cropped

Fedora Server can be used as a home or business lab server for many applications. One of the apps that can be run on it is a Network Video Recorder (NVR) to implement a Closed-Circuit TV for surveillance with IP cameras. [Viseron][4] is a NVR application that is simple to set up with virtually no dependencies (e.g., in-memory or storage databases). It is highly customizable with a variety of components to choose from. It can also leverage hardware such as Intel VAAPI and Google Coral Edge TPU for the video processing. Some features that make it ideal for CCTV are motion, object, license plate, and face detection. In this post, I will be showing how to set up Viseron on Fedora Server, utilizing Kubernetes.

### Preparing the Platform to host our NVR app

The rest of this post assumes you are starting with a fresh Fedora Server install, the server’s hostname is _server_ , and there is a user called _user_ with _sudo_ privileges.

#### Setting Up a Single Node Kubernetes

First, configure the firewall for the Kubernetes and Viseron installs:

```

    # firewall-cmd --permanent --add-port=6443/tcp #apiserver
    # firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16 #pods
    # firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16 #services
    # firewall-cmd --permanent --add-port=30888/tcp #node port we will use for viseron
    # firewall-cmd --reload

```

Starting with the fresh Fedora Linux installation, install [K3s][5], which is a lightweight certified Kubernetes that is ideal for single nodes. Run the following command in your server to install the latest stable version of K3s.

```

    $ curl -sfL https://get.k3s.io | sh -

```

To verify a successful install, run the following command:

```

    $ sudo k3s kubectl get node

    NAME     STATUS   ROLES                  AGE    VERSION
    server   Ready    control-plane,master   2m   v1.29.6+k3s2

```

We would like to access our Kubernetes nodes from our own machine. In order to do so, we will copy the file _/etc/rancher/k3s/k3s.yaml_ , on the server, to our local machine. The _k3s.yaml_ file is not world-readable on the server for security reasons. In order to copy it over, we will need to _sudo_ to copy it first to our server _user_ home directory and then use _scp_ to transfer it to our local machine. You can also use the following command snippet from our local machine to do it in one shot:

```

    $ ssh -q user@server "sudo --stdin cat /etc/rancher/k3s/k3s.yaml" <<(read -s && echo $REPLY) > k3s.yaml

```

The command does the following:

  * runs _sudo_ to _cat_ the _k3s.yaml_ file
  * redirects the output to a local _k3s.yaml_ file
  * tells _sudo_ to display the prompt for password on _stderr_ so the _stdout_ redirect excludes it
  * tells _ssh_ to run in quiet mode to not add anything to the _stdout_ redirect
  * uses _read -s_ to read the _sudo_ password without displaying it to the console
  * redirects the _sudo_ password to the _stdin_ of the _ssh_ command



There are a couple more things you will need to do to use the _k3s.yaml_ file to access the cluster. The K3s install generated a TLS cert for several local hostnames, including the name of our node: _server_. The _k3s.yaml_ file contains the Kubernetes endpoint as _<https://127.0.0.1:6443>_. Therefore, let’s change it to _<https://server:6443>_ so we can access it from the local machine. We can do this using our favorite editor, or simply _sed_.

```

    $ sed -i.bak 's/127.0.0.1/server/g' k3s.yaml

```

Finally, let’s place our file in the directory _~/.kube_ and change its permissions:

```

    $ mkdir ~/.kube
    $ mv k3s.yaml ~/.kube/k3s.yaml
    $ chmod 0600 ~/.kube/k3s.yaml

```

As our last step to access the cluster, we will need to install _kubectl_ in our local machine:

```

    $ sudo dnf install kubernetes-client

```

Now, we should be able to list our server node with the following commands:

```

    $ export KUBECONFIG=$HOME/.kube/k3s.yaml
    $ kubectl get nodes

    NAME     STATUS   ROLES                  AGE    VERSION
    server   Ready    control-plane,master   10m   v1.29.6+k3s2

```

#### Setting Up a LVM Storage Provider

We will need to set up volumes for our NVR app to store the videos and configs. K3s comes with _local-path_ as the default storage provider:

```

    $ kubectl get storageclass

    NAME                 PROVISIONER             (cut for brevity)
    local-path (default) rancher.io/local-path

```

This means that the volume we define will be mounted on the existing file system inside _/var_. The problem with that approach is that _local-path_ does not enforce any limits, so when you define a volume of 10Gi, that limit is actually ignored, and the disk usage can just grow and use all the space available on the disk, which can crash the entire system. Less than ideal.

The Fedora Server installation creates an LVM volume group called _fedora_ with the _root_ logical volume in it. For example, if our system had a 1TiB disk, it would look like this:

```

    # vgs

    VG     #PV #LV #SN Attr   VSize   VFree
    fedora   1   7   0 wz--n- 952g    937g

```

```

    # lvs

    LV     VG     Attr       LSize   (cut for brevity)
    root   fedora -wi-ao---- 15.00g

```

Notice that the _root_ logical volume doesn’t use all the space available. We will be using the extra space to provision Kubernetes volumes.

So, we could create logical volumes with specific limits, mount them on the local file system, and mount them into the Kubernetes containers with the _local-path_ storage provider! But, wouldn’t it be nice if Kubernetes itself creates and manages those logical volumes for us? This is where the [OpenEBS LocalPV-LVM project][6] comes into play. LocalPV-LVM is a storage provider for LVMs on local nodes.

To set up the storage provider, we apply the following Kubernetes manifest to our Kubernetes cluster:

```

    $ kubectl apply -f https://openebs.github.io/charts/lvm-operator.yaml

```

That manifest will install all the necessary artifacts in our cluster to implement the LVM storage provider.

After running the above command and waiting for a little bit, we can verify that everything is in place as expected:

```

    $ kubectl -n kube-system get pod | grep openebs

    openebs-lvm-controller-0      5/5     Running     0   1m
    openebs-lvm-node-8mxj5        2/2     Running     0   1m

    $ kubectl get crd | grep openebs

    lvmnodes.local.openebs.io         2024-07-30T04:00:00Z
    lvmsnapshots.local.openebs.io     2024-07-30T04:00:00Z
    lvmvolumes.local.openebs.io       2024-07-30T04:00:00Z

```

As the last step, we will set up our own Kubernetes storage class with our new OpenEBS storage provider.

Let’s create a _fedora-vg-openebs-sc.yaml_ file containing the following:

```

    apiVersion: storage.k8s.io/v1
    kind: StorageClass
    metadata:
      name: openebs-lvmpv #arbitrary storage class name
    allowVolumeExpansion: true #allows for volume expansion
    parameters:
      storage: "lvm"
      volgroup: "fedora" #name of the volume group in the server
    provisioner: local.csi.openebs.io

```

Then, deploy it:

```

    $ kubectl apply -f fedora-vg-openebs-sc.yaml

```

We can verify that it is in place with the following command:

```

    $ kubectl get storageclass

    NAME                  PROVISIONER          (cut for brevity)
    local-path (default)  rancher.io/local-path
    openebs-lvmpv         local.csi.openebs.io

```

### Installing the Viseron NVR application

The maintainer of Viseron and I worked to create a [Helm chart][7] to facilitate the install and management of Viseron in Kubernetes. [Helm][8] is like a package manager for Kubernetes.

For the next steps, we need to install Helm following the official documentation or with _dnf install helm_.

Let’s assume our server hardware is an Intel with VAAPI. We will first install the Viseron Helm repository and then install the app in our cluster with specific configurations.

```

    $ helm repo add viseron https://roflcoopter.github.io/viseron-helm-chart
    $ helm repo update

```

Let’s now create the following _viseron-values.yaml_ file:

```

    securityContext:
      privileged: true # Privileges to use the /dev/dri device

    service:
      type: NodePort
      nodePort: 30888 # The port where the app will be available in our server, opened with firewall-cmd in steps above


    storage:
      config:
        className: "openebs-lvmpv" # Our storageclass
        size: 50Mi # Not a lot of space needed to store configs
      data:
        className: "openebs-lvmpv" # Our storageclass
        size: 200Gi # Here we set plenty of space for videos storage. See the official viseron documentation to change the retention periods default of 7 days.

    volumes:
      - name: dev-dri
        hostPath:
          path: /dev/dri # To make this device available as a volume to the app container

    volumeMounts:
      - name: dev-dri
        mountPath: /dev/dri # To mount the dev-dri volume on the same /dev/dri path.

```

Then let’s install the chart:

```

    $ helm -n nvr upgrade --create-namespace --install --values viseron-values.yaml viseron viseron/viseron

```

The following is an explanation of the arguments used in the _helm_ command:

  * _-n nvr_ : specifies the Kubernetes namespace to use for our application
  * _upgrade_ : specifies that we want to upgrade our release (“release” is the Helm terminology for the installed apps)
  * _–create-namespace_ : creates the _nvr_ namespace if it does not exist.
  * _–install_ : installs (instead of upgrading) the release if it does not exist
  * _–values viseron-values.yaml_ : specifies the values file to use (our specific configurations)
  * _viseron_ : the name of the release
  * _viseron/viseron_ : the Helm chart we are using



If we want to update our app later, we would first refresh our helm repo ( _helm repo update_ ) and then re-run the command above.

If everything went well, our install should look like this:

```

    $ helm -n nvr history viseron

    REVISION UPDATED     STATUS   CHART         APP VERSION
    1        Tue Jul...  deployed viseron-0.1.2 2.3.1

    $ kubectl -n nvr get pod

    NAME                       READY   STATUS    RESTARTS   AGE
    viseron-5745654d57-9kcbz   1/1     Running   0          2m

    $ kubectl -n nvr get pvc

    NAME             STATUS   VOLUME (cut for brevity)
    viseron-config   Bound    pvc-0492f99d-1b35-42e5-9725-af9c50fd0d63
    viseron-data     Bound    pvc-4230c3fe-ae9d-471c-b0a7-0c0645e1449b

```

The Viseron logs will also inform us if the hardware acceleration platforms were detected. In our case, Viseron detected that VAAPI and OpenCL were available for use:

```

    $ kubectl -n nvr logs viseron-5745654d57-9kcbz

    (cut for brevity)
    ************** Setting EdgeTPU permissions ***************
    Coral Vendor IDs:
    "1a6e"
    "18d1"
    No EdgeTPU USB device was found
    No EdgeTPU PCI device was found
    ************************** Done **************************

    ****** Checking for hardware acceleration platforms ******
    OpenCL is available!
    VA-API is available!
    CUDA cannot be used
    (cut for brevity)

```

If we had not mounted _/dev/dri_ on the container, the logs would have said _VA-API cannot be used_.

If we ssh into our server, we should be able to see those Kubernetes volumes as logical volumes:

```

    # lvs

    LV                                       VG     Attr       LSize (cut for brevity)
    pvc-0492f99d-1b35-42e5-9725-af9c50fd0d63 fedora -wi-ao----  52.00m
    pvc-4230c3fe-ae9d-471c-b0a7-0c0645e1449b fedora -wi-ao---- 200.00g
    root                                     fedora -wi-ao----  15.00g

```

The Viseron app will be available at _<http://server:30888/>_. When you visit it for the first time, it will say that it is waiting for the cameras. This is because the system comes with a default configuration, which is merely an example pointing to non-existent cameras. The configuration can be changed by going to Menu / Administration / Configuration.

### Conclusion

In this post, we have followed steps to set up the Viseron NVR app on a Fedora server with Kubernetes. The following components were used:

  * [Fedora Server][9]
  * [K3s][5]
  * [OpenEBS LocalPV-LVM][6]
  * [Viseron][4]
  * [Viseron Helm Chart][10]



The next step is to add the cameras, configure the video processing features we’ll be using, and program the recorder to begin recording automatically whenever it finds something interesting.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/a-nvr-system-on-fedora-server/

作者：[Carlos Rodriguez-Fernandez][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/carlosrodrifernandez/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/08/NVR_System-816x345.jpg
[2]: https://unsplash.com/@kellysikkema?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-set-of-four-white-buttons-on-a-brown-surface-XSWi1oJA8ik?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://viseron.netlify.app/
[5]: https://k3s.io
[6]: https://github.com/openebs/lvm-localpv
[7]: https://github.com/roflcoopter/viseron-helm-chart
[8]: https://helm.sh/
[9]: https://fedoraproject.org/server/
[10]: https://roflcoopter.github.io/viseron-helm-chart
