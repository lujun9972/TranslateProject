[#]: subject: "Check Rockchip NPU Usage on Linux"
[#]: via: "https://itsfoss.com/monitor-npu-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Check Rockchip NPU Usage on Linux
======

[![Warp Terminal][1]][2]

These days, newer devices have started coming with onboard AI chips. The correct technical term for the 'AI chip' is NPU, which stands for neural processing units.

If you have got an NPU on-board, you may wonder whether your system is utilizing it.

In this tutorial, I'll share how I monitor NPU usage on my Rockchip processor.

🚧

This method discussed here is only valid for NPU that comes integrated into Rockchip processor. I tested it with my [ArmSoM Sige7][3] device which has a RK3588 processor.

You can check if your system has npu with this command:

```

    dmesg | grep -i npu

```

Analyze the output to figure out if there is an NPU or not.

### Checking Rockchip NPU utilization

Thankfully, Rockchip utilizes the [debugfs][4] feature. Debugfs is a special type of virtual filesystem that provides debug information in real time, similar to what you get with proc.

The file that will give you the NPU usage at any given time is:

```

    /sys/kernel/debug/rknpu/load

```

Here's what it shows when I ran it on my [ArmSoM][5] device. It shows the usage for all three cores of the NPU:

```

    abhishek@armsom:~$ sudo cat /sys/kernel/debug/rknpu/load
    NPU load:  Core0:  0%, Core1:  0%, Core2:  0%,
    abhishek@armsom:~$

```

As you can see, it just gives the NPU usage at the moment and ends it. Not very useful if you want to monitor the NPU usage.

An alternative can be to combine it with the watch command which will run the same command as above but every two seconds (by default):

```

    watch sudo cat /sys/kernel/debug/rknpu/load

```

Here's a screenshot I was running a LLM locally that utilized the NPU:

![][6]

To stop the running watch command, press Ctrl+C.

📋

To actually see the NPU usage, you should run a program that is supposed to use NPU. Otherwise, it will always be 0 for all cores.

There is another way of monitoring NPU usage. I found it when I was experimenting with the [ezrknpu project][7] to run LLMs with Rockchip NPU.

The project has a [ntop.sh script][8] that shows the NPU usage in a top command like manner. Which is not entirely true because the top command doesn't pollute the screen. The ntop.sh script, on the other hand, floods the screen with all those lines and they don't go away after you press Ctrl+C.

The content of the script is:

```

    #!/bin/bash
    # Title: ntop.sh
    # Author: Pelochus
    # Brief: A very basic 'top' style program that shows the status of the NPU in Rockchip's SoCs

    # Variables
    CLEAR=""

    # Parameters check
    if [[ $1 = '-h' ]]
    then
        echo
        echo "ntop Help"
        echo
        echo "-c: Clears output every refresh"
        echo "-h: Shows this help screen"
        echo
        echo "For more information visit https://github.com/Pelochus/ezrknpu"
        echo
        exit
    elif [[ $1 = '-c' ]]
    then
        CLEAR="clear"
    fi

    while true; do
        eval $CLEAR # If empty, will not clear
        cat /sys/kernel/debug/rknpu/load
        sleep 0.5
    done

```

The important part is the while loop at the end. Here's an example of NPU usage check with this script.

![][9]

### Conclusion

As you can see, there is no standard top like command that shows the NPU usage for various manufacturers. At present, I only have Rockchip so my exploration was limited and thus this tutorial was limited to Rockchip NPU. If I get access to more such hardware, I'll write about them too.

--------------------------------------------------------------------------------

via: https://itsfoss.com/monitor-npu-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/arosom-sige7-review/
[4]: https://linuxlink.timesys.com/docs/wiki/engineering/HOWTO_Use_debugfs
[5]: https://www.armsom.org/
[6]: https://itsfoss.com/content/images/2024/07/npu-usage.png
[7]: https://github.com/Pelochus/ezrknpu
[8]: https://github.com/Pelochus/ezrknpu/blob/main/ntop.sh
[9]: https://itsfoss.com/content/images/2024/07/ntop-script-for-cpu-usage.png
