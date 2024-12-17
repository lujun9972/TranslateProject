[#]: subject: "How to Backup Configuration Files on Remote Linux System"
[#]: via: "https://www.2daygeek.com/linux-bash-script-backup-configuration-files-remote-linux-system-server/"
[#]: author: "Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Backup Configuration Files on Remote Linux System
======

It is a best practice to backup a configuration file before performing any activity on a Linux system, which helps you to compare the configuration files in case of any issue occur.

You can automate this **[bash script][1]** by creating a cronjob, which can be scheduled based on your needs. However, we recommending to enable a cronjob once in a week nor month.

This script is very important for an environment where server restarts are not done frequently.

Also, as everything is a file in Linux, so it recommends running this script before fixing any VA/CR’s.

### What does this script?

This script backs up the output of multiple commands and configuration files into a single file, and finally moves it to another server (aka jump server nor central server).

**System details are as follows:**

  * **Server-A:** Central Server / JUMP Server (local.2daygeek.com)
  * **Server-B:** Remote System-1 (CentOS7.2daygeek.com)
  * **Server-C:** Remote System-2 (CentOS8.2daygeek.com)



### Bash Script to Backup Configuration files on Remote Linux Server

It consists of two scripts, one is the actual script and the other is a helper script, which helps execute the actual script from the JUMP/Central server, and it pulls the output file from the remote server once the script execution is complete.

**Make a Note:** Both scripts must be on the central server and you must have enabled passwordless authentication for client systems for seamless operation.

Actual Script:

```

    # vi /home/daygeek/shell-script/configuration_files_backup.sh

    #!/bin/bash
    echo -e "Hold on...Server Configuration Check is running on..."
    echo "========================================================"
    touch /tmp/$(hostname)-configuration_output-$(date +%d%b%Y).txt
    OUTPUT_FILE=$(ls  /tmp/$(hostname)-configuration_output-$(date +%d%b%Y).txt)
    if [ -f $OUTPUT_FILE ]
    then
    cat /dev/null > $OUTPUT_FILE
    echo -e "==================================General Commands OutPut==================================" >> $OUTPUT_FILE
    echo "HOSTNAME-------: `hostname`" >> $OUTPUT_FILE
    echo "IP-------------: `hostname -i`" >> $OUTPUT_FILE
    echo "DATE-----------: `date`" >> $OUTPUT_FILE
    echo "KERNEL---------: `uname -r`" >> $OUTPUT_FILE
    echo -e "----------------------------/etc/hosts File OutPut----------------------------" >> $OUTPUT_FILE
    cat /etc/hosts >> $OUTPUT_FILE

    echo -e "\n==================================Disk Commands/Config File OutPut==================================" >> $OUTPUT_FILE
    echo -e "\n----------------------------df -hT Command OutPut----------------------------" >> $OUTPUT_FILE
    df -hT >> $OUTPUT_FILE
    echo -e "\n----------------------------blkid Command OutPut-----------------------------" >> $OUTPUT_FILE
    blkid >> $OUTPUT_FILE
    echo -e "\n----------------------------lsblk Command OutPut-----------------------------" >> $OUTPUT_FILE
    lsblk >> $OUTPUT_FILE
    echo -e "\n----------------------------PVS Command OutPut-------------------------------" >> $OUTPUT_FILE
    pvs >> $OUTPUT_FILE
    echo -e "\n----------------------------VGS Command OutPut-------------------------------" >> $OUTPUT_FILE
    vgs >> $OUTPUT_FILE
    echo -e "\n----------------------------LVS Command OutPut-------------------------------" >> $OUTPUT_FILE
    lvs >> $OUTPUT_FILE
    echo -e "\n----------------------------PVdisplay Command OutPut-------------------------" >> $OUTPUT_FILE
    pvdisplay >> $OUTPUT_FILE
    echo -e "\n----------------------------VGdisplay Command OutPut-------------------------" >> $OUTPUT_FILE
    vgdisplay >> $OUTPUT_FILE
    echo -e "\n----------------------------LVdisplay Command OutPut-------------------------" >> $OUTPUT_FILE
    lvdisplay >> $OUTPUT_FILE
    echo -e "\n----------------------------lsscsi Command OutPut----------------------------" >> $OUTPUT_FILE
    lsscsi --scsi --size >> $OUTPUT_FILE
    echo -e "\n----------------------------mount Command OutPut-----------------------------" >> $OUTPUT_FILE
    mount >> $OUTPUT_FILE
    echo -e "\n----------------------------/dev/mapper Devices OutPut-----------------------" >> $OUTPUT_FILE
    ls -ltr /dev/mapper >> $OUTPUT_FILE
    echo -e "\n----------------------------/proc/partitions OutPut--------------------------" >> $OUTPUT_FILE
    cat /proc/partitions >> $OUTPUT_FILE
    echo -e "\n----------------------------/etc/fstab File OutPut---------------------------" >> $OUTPUT_FILE
    cat /etc/fstab >> $OUTPUT_FILE
    echo -e "\n----------------------------/etc/sudoers File OutPut-------------------------" >> $OUTPUT_FILE
    cat /etc/sudoers >> $OUTPUT_FILE

    echo -e "\n==================================Network Commands/Config File OutPut==================================" >> $OUTPUT_FILE
    echo -e "\n----------------------------ip Command OutPut--------------------------------" >> $OUTPUT_FILE
    ip a >> $OUTPUT_FILE
    echo -e "\n----------------------------ip Command Customized OutPut---------------------" >> $OUTPUT_FILE
    ip a | grep -i inet | grep -v inte6 >> $OUTPUT_FILE
    echo -e "\n----------------------------ip Command Customized OutPut-1-------------------" >> $OUTPUT_FILE
    ip -br a >> $OUTPUT_FILE
    echo -e "\n----------------------------ip route Command OutPut--------------------------" >> $OUTPUT_FILE
    ip r >> $OUTPUT_FILE
    echo -e "\n----------------------------ifconfig Command OutPut--------------------------" >> $OUTPUT_FILE
    ifconfig -a >> $OUTPUT_FILE
    echo -e "\n----------------------------netstat -ni Command OutPut-----------------------" >> $OUTPUT_FILE
    netstat -ni >> $OUTPUT_FILE
    echo -e "\n----------------------------netstat -nr Command OutPut-----------------------" >> $OUTPUT_FILE
    netstat -nr >> $OUTPUT_FILE
    echo -e "\n----------------------------netstat Command OutPut with Ports----------------" >> $OUTPUT_FILE
    netstat -tplugn | grep -i LISTEN >> $OUTPUT_FILE
    echo -e "\n----------------------------List Network Script Files------------------------" >> $OUTPUT_FILE
    ls -ltrh /etc/sysconfig/network-scripts/ifcfg-* >> $OUTPUT_FILE
    echo -e "\n----------------------------Print each Network Script file OutPut------------" >> $OUTPUT_FILE
    for inet_file in `ls /etc/sysconfig/network-scripts/ifcfg-*`
    do
    echo "----------$inet_file----------" >> $OUTPUT_FILE
    cat $inet_file >> $OUTPUT_FILE
    done

    echo -e "\n==================================Kernel Commands/Config File OutPut==================================" >> $OUTPUT_FILE
    echo -e "\n----------------------------sysctl Command OutPut----------------------------" >> $OUTPUT_FILE
    sysctl -p >> $OUTPUT_FILE
    echo -e "\n----------------------------/etc/sysctl.conf File OutPut---------------------" >> $OUTPUT_FILE
    cat /etc/sysctl.conf >> $OUTPUT_FILE

    ps -ef | egrep 'pmon|LISTENER' | grep -v grep > /dev/null 2>&1
    if [ $? -eq 0 ]
    then
    echo -e "\n==================================Oracle DB Commands/Config File OutPut==================================" >> $OUTPUT_FILE
    echo -e "\n----------------------------Oracle Processes OutPut--------------------------" >> $OUTPUT_FILE
    ps -ef | egrep 'pmon|LISTENER' | grep -v grep >> $OUTPUT_FILE
    echo -e "\n----------------------------oracleasm Command OutPut-------------------------" >> $OUTPUT_FILE
    oracleasm listdisks >> $OUTPUT_FILE
    echo -e "\n----------------------------Oracle Device file OutPut------------------------" >> $OUTPUT_FILE
    ls -ltr /dev/oracleasm/disks >> $OUTPUT_FILE
    else
    echo -e "\nThis is not an Oracle DB server..." >> $OUTPUT_FILE
    fi

    systemctl status multipathd | grep -i running > /dev/null 2>&1
    if [ $? -eq 0 ]
    then
    echo -e "\n==================================Multipath Command OutPut==================================" >> $OUTPUT_FILE
    echo -e "\n----------------------------multipath -ll Command OutPut---------------------" >> $OUTPUT_FILE
    multipath -ll >> $OUTPUT_FILE
    else
    echo -e "\nThis is not a Physical server, so no multipath is configuared.." >> $OUTPUT_FILE
    fi

    echo -e "Configuration file backup has been completed and the OutPut file will be placed at '/home/daygeek/backup/' directory..."
    echo "============================================Configuration file backup Script Completed====================================" >> $OUTPUT_FILE
    else
    echo "OutPut file isn't found, So exit the script" >> $OUTPUT_FILE
    fi

```

Supporting nor helper script.

```

    # vi configuration_files_backup_PUSH.sh

    #!/bin/bash
    echo -e '\n'
    echo "Please ENTER the list of HostName or IP to take a configuration file backup, and press 'ctrl+d' to execute the script."
    for server in `cat`
      do
        echo -e "\n$server\n=============>>"
            ssh -q -o StrictHostKeyChecking=no -o ConnectTimeout=5 -o "BatchMode yes" $server 'bash -s' < /home/daygeek/shell-script/configuration_files_backup.sh
            scp -pr "$server:/tmp/*-configuration_output-$(date +%d%b%Y).txt" "/home/daygeek/backup/"
      done

```

Finally run the supporting script that pushes the actual script to the given target servers.

```

    # sh /home/daygeek/shell-script/configuration_files_backup_PUSH.sh

```

### Final Thoughts

I hope this shell script very useful for backup your configuration files on remote Linux system.

If you have any questions or feedback, feel free to comment below.

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/linux-bash-script-backup-configuration-files-remote-linux-system-server/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/category/bash-script/
