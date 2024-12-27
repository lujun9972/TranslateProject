[#]: subject: "How to Create Users using Shell Script in Linux"
[#]: via: "https://www.2daygeek.com/how-to-create-users-using-shell-script-in-linux/"
[#]: author: "Jayabal Thiyagarajan https://www.2daygeek.com/author/jayabal/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Create Users using Shell Script in Linux
======

Creating users in Linux/Unix is ​​a straightforward task. However, adding multiple users across multiple servers can be a time-consuming task, so you can automate this with a **[shell script][1]** to save time or avoid manual administrative intervention.

In this bash script, we will show you how to automate user creation in Linux/Unix.

### What does this script?

This script creates the below three users on multiple systems (Based on your list of servers), set password, add users to **‘2gadmins’** group and shows their password on the screen.

  * mageshm
  * tanisha
  * renusha



**Make a Note:**

  * **Inventory:** It’s dynamic, and you can Enter any number of servers, when its pops-up.
  * **User Input:** It’s dynamic, and you can add any number of users to the **`'user_info'`** list.
  * **Additional Switch:** This is dynamic, you can add other switches if you need them. For example, the user is mapped to the **`'/bin/bash'`** shell by default, as it is already defined in the **`'/etc/default/useradd'`** file, so to change this behavior, you need to add the required shell to **`'user_info'`** , and then call it wherever needed in the script.
  * **Remote Execution:** This script works fine on a remote server as well. For Local implementation, use the **`'user_add.sh'`** script on the specific server.



#### **Source Bash Script for User Addition:**

```

    vi /home/daygeek/shell-script/user_add.sh

    #!/bin/bash
    user_info=$(cat << EOF
    mageshm:2gadmins:Local User | L3 Engineer (Magesh Maruthamuthu)
    tanisha:2gadmins:Local User | L2 Engineer (Tanisha)
    renusha:2gadmins:Local User | L1 Engineer (Renusha)
    EOF
    )
    echo "$user_info" | while IFS=':' read -r user_ name group_name u_comments
      do
        id $user_name
          if [ $? -eq 0 ]
            then
              echo "User $user_name is already exist in system..."
            else
              echo "Creating $user_name....User"
              useradd -m -g "$group_name" -c "$u_comments" "$user_name"
              echo P@ssw0rd@`date +%d%b%Y` | passwd --stdin "$user_name"
              echo "$user_name Password is: P@ssw0rd@`date +%d%b%Y`"
              echo -e "\n"
          fi
      done

```

#### Remote call Bash Script:

```

    vi /home/daygeek/shell-script/user_add_PUSH.sh

    #!/bin/bash
    echo -e '\n'
    echo "Please ENTER a list of HostName or IP to create a user, and press 'ctrl+d' to execute the script."
    for server in `cat`
      do
        echo -e "\n$server\n=============>>"
        ssh -q -o StrictHostKeyChecking=no -o ConnectTimeout=5 -o "BatchMode yes" $server 'bash -s' < /home/daygeek/shell-script/user_add.sh
      done

```

**Output:**

```

    CentOS7.2daygeek.com
    ====================>>
    Creating mageshm...User
    Changing password for user mageshm.
    passwd: all authentication tokens updated successfully.
    mageshm Password is: P@ssw0rd27Dec2024

    Creating tanisha...User
    Changing password for user tanisha.
    passwd: all authentication tokens updated successfully.
    tanisha Password is: P@ssw0rd27Dec2024

    Creating renusha...User
    Changing password for user renusha.
    passwd: all authentication tokens updated successfully.
    mageshm Password is: P@ssw0rd27Dec2024

    CentOS8.2daygeek.com
    ====================>>
    Creating mageshm...User
    Changing password for user mageshm.
    passwd: all authentication tokens updated successfully.
    mageshm Password is: P@ssw0rd27Dec2024

    Creating tanisha...User
    Changing password for user tanisha.
    passwd: all authentication tokens updated successfully.
    tanisha Password is: P@ssw0rd27Dec2024

    Creating renusha...User
    Changing password for user renusha.
    passwd: all authentication tokens updated successfully.
    mageshm Password is: P@ssw0rd27Dec2024

```

##### Final Thoughts

I hope this Bash script automating user account creation in Linux, which save time and reduce manual administrative intervention. This article has provided a step-by-step guide on how to automate user account creation using Bash script.

If you have any questions or feedback, feel free to comment below.

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/how-to-create-users-using-shell-script-in-linux/

作者：[Jayabal Thiyagarajan][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/jayabal/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/category/shell-script/
