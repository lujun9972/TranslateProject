[#]: subject: "Podman Checkpoint"
[#]: via: "https://fedoramagazine.org/podman-checkpoint-in-fedora-linux/"
[#]: author: "Ashutosh Sudhakar Bhakare https://fedoramagazine.org/author/ashutoshbhakare/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Podman Checkpoint
======

![][1]

Podman Checkpoint

Podman is a tool which runs, manages and deploys containers under the [OCI][2] standard. Running containers with rootless access and creating pods (a Pod is a group of containers ) are additional features of Podman. This article describes and explains how to use checkpointing in Podman to save the state of a running container for later use.

**Checkpointing Containers :** Checkpoint / Restore In User-space, or CRIU, is Linux software available in the Fedora Linux repository as the “criu” package. It can freeze a running container (or an individual application) and checkpoint its state to disk (Reference : <https://criu.org/Main_Page>). The saved data can be used to restore the container and run it exactly as it was during the time of the freeze. Using this, we can achieve live migration, snapshots, or remote debugging of applications or containers. This capability requires CRIU 3.11 or later installed on the system.

### Podman Checkpoint

```

    # podman container checkpoint <containername>

```

This command will create a checkpoint of the container and freeze its state. Checkpointing a container will stop the running container as well. If you do _podman ps_ there will be no container existing named <containername>.

You can export the checkpoint to a specific location as a file and copy that file to a different server

```

    # podman container checkpoint <containername> -e /tmp/mycheckpoint.tar.gz

```

### Podman Restore

```

    # podman container restore --keep <containername>

```

the _–keep_ option will restore the container with all the temporary files.

To import the container checkpoint you can use:

```

    # podman container restore -i /tmp/mycheckpoint.tar.gz

```

### Live Migration using Podman Checkpoint

This section describes how to migrate a container from client1 to client2 using the podman checkpoint feature. This example uses the <https://lab.redhat.com/tracks/rhel-system-roles> playground provided by Red Hat as it has multiple hosts with ssh-keygen already configured.

![][3]

The example will run a container with some process on client1, create a checkpoint, and migrate it to client2. First run a container on the client1 machine with the commands below:

```

    podman run --name=demo1 -d docker.io/httpd
    podman exec -it demo1 bash
    sleep 600& (run a process for verification )
    exit

```

The above snippet runs a container as demo1 with the httpd process which runs a sleep process for 600 seconds ( 10 mins ) in background. You can verify this by doing:

```

    # podman top demo1

    USER        PID         PPID        %CPU        ELAPSED          TTY         TIME        COMMAND
    root        1           0           0.000       5m40.61208846s   ?           0s          httpd -DFOREGROUND
    www-data    3           1           0.000       5m40.613179941s  ?           0s          httpd -DFOREGROUND
    www-data    4           1           0.000       5m40.613258012s  ?           0s          httpd -DFOREGROUND
    www-data    5           1           0.000       5m40.613312515s  ?           0s          httpd -DFOREGROUND
    root        88          1           0.000       16.613370018s    ?           0s          sleep 600

```

Now create a container checkpoint and export it to a specific file:

```

    # podman container checkpoint myapache2 -e /tmp/mycheckpoint.tar.gz
    # scp /tmp/mycheckpoint.tar.gz client2:/tmp/

```

Then on client2:

```

    # cd /tmp
    # podman container restore -i mycheckpoint.tar.gz
    # podman top demo1

```

You should see the output as follows:

```

    USER        PID         PPID        %CPU        ELAPSED          TTY         TIME        COMMAND
    root        1           0           0.000       5m40.61208846s   ?           0s          httpd -DFOREGROUND
    www-data    3           1           0.000       5m40.613179941s  ?           0s          httpd -DFOREGROUND
    www-data    4           1           0.000       5m40.613258012s  ?           0s          httpd -DFOREGROUND
    www-data    5           1           0.000       5m40.613312515s  ?           0s          httpd -DFOREGROUND
    root        88          1           0.000       16.613370018s    ?           0s          sleep 600

```

In this way you can achieve a live migration using the podman checkpoint feature.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/podman-checkpoint-in-fedora-linux/

作者：[Ashutosh Sudhakar Bhakare][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ashutoshbhakare/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/podman_checkpoint-1-816x345.jpg
[2]: https://opencontainers.org/
[3]: https://fedoramagazine.org/wp-content/uploads/2023/02/podman_checkpoint_orig-1024x334.png
