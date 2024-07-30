[#]: subject: "Copy Files Between Remote Systems in the Linux Command Line"
[#]: via: "https://itsfoss.com/ssh-copy-remote-local/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Copy Files Between Remote Systems in the Linux Command Line
======

[![Warp Terminal][1]][2]

Here's the scenario. You can connect to a remote Linux system over SSH and you find yourself in a situation where you have to copy some files from the remote server to your local system.

How do you do that? You can use the good old scp command in the following manner:

```

    scp remote_username@remote_server_IP:/dir/location/filename local_dir_path

```

If you want to copy some files from local to remote system:

```

    scp local_dir_path/filename remote_username@remote_server_IP:/dir/location

```

**Pay attention to the use of colon (:) between the remote server details and the path**.

You can also use the rsync command here. Let me go over these steps in detail in this tutorial.

✋

This tutorial assumes you can connect to the remote system using SSH. You need to know the password for the remote user and the remote user should have read/write access to the folder where you want to copy the file.

My environmental setup consists of a Raspberry Pi working as the remote server. I [can SSH into the Pi][3] easily from my TUXEDO laptop.

### Using scp command

The [scp command][4], short for secure copy, uses the SSH connection to transfer files between remote systems. I like it because its syntax is similar to [the cp command][5].

💡

I keep a separate terminal session open with SSH connection into the remote server. This gives me the ability to view and copy the file locations on the remote server. This is important because you won't get tab completion over SCP.

#### Copy files from local machine to remote server

I have a sample.txt file in the Documents directory. I want to send this file to the remote server in its Template directory.

Do you remember the syntax:

```

    scp local_dir_path/filename remote_username@remote_server_IP:/dir/location

```

It will ask for a password which is the password for the user on the remote server.

Let's use it in the example here:

```

    scp Documents/sample.txt [email protected]:~/Templates

```

And here is the output for the command:

![][6]

I used the `~` notation for the home directory of the user as it is shorter to write than /home/username.

You can verify it by connecting to the remote server via SSH. This is why I keep a separate terminal session open.

![][7]

**Copying multiple files**

Use the same logic as the cp command:

```

    scp file1 file2 fileN remote_username@remote_server_IP:/dir/location

```

**Copy a folder to remote system**

Like you do with the cp command, use the recursive option `-r`:

```

    scp -r Dir1 remote_username@remote_server_IP:/dir/location

```

#### Copy files from remote server to local machine

Let's turn the tables now. Let's copy files from the remote server to the local machine. Here's the syntax:

```

    scp remote_username@remote_server_IP:/dir/location/filename local_dir_path

```

Let's say I have a few screenshots on the Pi and I want them on my laptop.

```

    scp [email protected]:~/Pictures/sd-card-copy.png .

```

I copied the remote file to my current working directory.

![][8]

**Copying multiple files?**

This gets tricky as copying multiple files will mean providing full path (including user name and IP address) for all the files. If you can use wild card matching, go for it otherwise, copy the desired files in a new temp directory and copy this temp directory to the local system.

```

    scp -r remote_username@remote_server_IP:/dir_location local_dir_path

```

### Using rsync command

rsync is another powerful command that gives you the ability to copy files between remote systems. Unlike scp, rsync is more than just a simple transfer command, it has more powerful features that make it a good backup tool when used in combination with cron jobs.

Here, I'll only show you how to use it for simple file transfers.

#### Copy files/directories from local to remote

To copy a file from local system to the remote server, you can use rsync command in this fashion:

```

    rsync local_file_path remote_username@remote_server_IP:/dir/location

```

Let's take an example where I want to copy a local directory `NewDir` into the Documents directory of the remote Raspberry Pi:

```

    rsync -r Documents/NewDir [email protected]:~/Documents

```

![][9]

#### Copy files/directories from remote to local

To copy a file or directory from the remote machine to the local, use rsync in this fashion:

```

    rsync remote_username@remote_server_IP:/file_location local_dir_path

```

Let's say I want to copy rpdiags.txt from the home directory of the remote system to my current working directory on the local:

```

    rsync [email protected]:~/rpdiags.txt .

```

![][10]

### Conclusion

If you have an SFTP server setup, you can use a GUI tool like [FileZilla][11].

![][12]

I prefer using the scp command for quick file transfer over SSH connection. I use rsync when I have to make a backup of a folder that consists of numerous files. More on that in some other article. Enjoy 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/ssh-copy-remote-local/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/ssh-into-raspberry/
[4]: https://itsfoss.com/scp-command/
[5]: https://itsfoss.com/cp-command/
[6]: https://itsfoss.com/content/images/2024/07/scp-copy-files-from-local-to-remote-system.png
[7]: https://itsfoss.com/content/images/2024/07/verify-local-to-remote-copy.png
[8]: https://itsfoss.com/content/images/2024/07/scp-copy-remote-file-to-local.png
[9]: https://itsfoss.com/content/images/2024/07/rsync-copy-local-to-remote.png
[10]: https://itsfoss.com/content/images/2024/07/rsync-copy-from-remote-to-local.png
[11]: https://filezilla-project.org/
[12]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
