[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Backup and restore Toolboxes)
[#]: via: (https://fedoramagazine.org/backup-and-restore-toolboxes-with-podman/)
[#]: author: (joefidler https://fedoramagazine.org/author/joefidler/)

Backup and restore Toolboxes
======

![][1]

[Toolboxes][2] started life often described as disposable containers – and that is still one of their major uses: install stuff, then try it out in the relative safety of a container, and lastly, cleanly dispose of it. Minimal risk, fuss and without pesky residual libraries and applications hanging around on the host long after you have finished.

So — why would you backup a Toolbox? Sometimes, they have more permanent uses, contain complex and lengthy installs, or are being used for critical applications. For example, Toolboxes can be used as a development environment, containing hardware associated drivers and applications. Or they could be used for an application you want to run in a container for which there is no [Flatpak][3], or one that has requirements a Flatpak doesn’t satisfy. While they can be handy to use on [Fedora Workstation][4], toolbox containers are often essential for [Silverblue][5] users since they offer an easy solution to installing applications that can’t successfully be installed by rpm-ostree. Or for applications that may not have a Flatpak version readily available. In the above situations a busted Toolbox can be a major headache. But if a backup exists, you can quickly restore a Toolbox or move it to another workstation.

The backup process uses [Podman][6] to create an image of an existing toolbox container, and save that image to an archive file. To restore the toolbox container, load the image from the archive file and then create a Toolbox from that image. The new toolbox container will be an identical copy of your backed up toolbox container.

It is important to note this process **does not backup data**, just what you have installed in the toolbox container. This includes packages installed from repositories or from a local rpm file using dnf. If you need to backup data, Podman’s [commit command][7] that will be used to capture an image of the toolbox container, has an option to include volumes attached to the container.

### Creating a backup

To backup a toolbox container you will need it’s name and container ID which can be gotten by using _toolbox list_. For this example I am going to backup my golang development toolbox container, imaginatively named _go_.

```
$ toolbox list

CONTAINER ID  CONTAINER NAME  CREATED      STATUS   IMAGE NAME
00ff783a102f  go              5 weeks ago  exited   registry.fedoraproject.org/f32/fedora-toolbox:32
```

If the container’s status shows as running , you should stop it using _podman container stop container_name._ Although the commit command has a -p for pause option, make sure that the Toolbox is not running, which helps it initialize correctly when restored from backup.

```
$ podman container stop go
```

To create an image of the toolbox container use

podman container commit -p container_ID backup-image-name

Depending on the complexity of the Toolbox, this can take a little while.

```
$ podman container commit -p 00ff783a102f  go-backup
```

Now to confirm the image has been created type…

```
$ toolbox list
```

You should get output similar to what is below…

```
IMAGE ID IMAGE NAME CREATED
cfcb13046db7 localhost/go-backup:latest About a minute ago

CONTAINER ID CONTAINER NAME CREATED STATUS IMAGE NAME
00ff783a102f go 5 weeks ago exited registry.fedoraproject.org/f32/fedora-toolbox:32
```

Now to save the backup image to a tar archive file using _podman save -o backup-filename.tar backup-image-name_.

```
$ podman save -o go.tar go-backup
```

Confirm the archive file, our toolbox container backup, was created.

```
$ ls

go.tar
```

Do some tidying up, remove the backup image and, if needed, remove the original Toolbox.

```
$ podman rmi go-backup

$ toolbox rm go
```

### Restore a backup

To create an image from the backup file that was made above, you do it with the command _podman load -i backup_filename_.

```
$ podman load -i go.tar
```

Then you can confirm the image was created with…

```
$ toolbox list

IMAGE ID      IMAGE NAME                  CREATED
cfcb13046db7  localhost/go-backup:latest  17 minutes ago
```

Now create a toolbox container from the restored image, with _toolbox create –_–_container container_name_ ––_image image_name_, specifying the full repository and version tag as the image name.

```
$ toolbox create --container go --image localhost/go-backup:latest
```

Confirm that the toolbox was created.

```
$ toolbox list

IMAGE ID      IMAGE NAME                CREATED
cfcb13046db7 localhost/go-backup:latest 20 minutes ago

CONTAINER ID CONTAINER NAME CREATED STATUS IMAGE NAME
34cef6b7e28d go 21 seconds ago configured localhost/go-backup:latest
```

Finally, you can test that the restored Toolbox works…

```
$ toolbox enter --container go
```

If you can enter the newly created toolbox container, you will see the toolbox prompt and will have successfully backed up and restored your Pet toolbox container.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/backup-and-restore-toolboxes-with-podman/

作者：[joefidler][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/joefidler/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/07/toolbox-backup-816x346.png
[2]: https://fedoramagazine.org/a-quick-introduction-to-toolbox-on-fedora/
[3]: https://www.flatpak.org/
[4]: https://getfedora.org/en/workstation/
[5]: https://silverblue.fedoraproject.org/
[6]: https://podman.io/
[7]: http://docs.podman.io/en/latest/markdown/podman-commit.1.html
