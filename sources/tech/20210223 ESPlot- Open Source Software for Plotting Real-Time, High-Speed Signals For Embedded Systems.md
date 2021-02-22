[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (ESPlot: Open Source Software for Plotting Real-Time, High-Speed Signals For Embedded Systems)
[#]: via: (https://itsfoss.com/esplot/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

ESPlot: Open Source Software for Plotting Real-Time, High-Speed Signals For Embedded Systems
======

Confronted with the need of plotting high-speed (or high number of data) signals, typically for embedded systems applications and real-time, research engineers at the [Saarland University][1], Germany have developed their own software called ESPlot.

[ESPlot][2] communicates with microcontroller boards over a custom serial protocol. In applications where the microcontroller is executing a real-time process, signals can be streamed to a computer in a synchronous way and data can be sent to the real-time process in an asynchronous way.

![][3]

ESPlot allows recording and plotting signals to screen by means of time plots, FFT plots and X/Y plots.

![][4]

ESPlot has been developed in Qt to support multi-platform and it is OpenGL hardware accelerated.

Since it has been designed to provide high performance, it needs systems with a multicore CPU with 4 GB RAM and a dedicated GPU supporting OpenGL 3.2.

<https://youtube.com/watch?v=D7N2MgAdXJA>

### Features of ESPlot

Here are the main features of ESPlot:

  * Streaming and recording of real-time signals
  * Time plots, XY-Plots, FFT plot
  * Able to send commands to the microcontroller
  * Communication over serial interfaces
  * Oscilloscope functionality, e.g. Trigger, Autoscale, Screenshot
  * Externally controllable record function
  * Export data to Matlab for further processing
  * Multimonitor-Support with fully screen capability
  * Fully personizable GUI
  * OpenGL-Acceleration
  * Multi-threading support
  * Platform independent (Library is written in C)
  * Supports Windows 10 64-bit, Linux 64-bit, Software can be compiled for ARM (e.g. Raspberry Pi)



### Installing ESPLot

At present, ESPlot is available for Windows and Linux. The macOS version is under development.

For Linux, there is a tar xz file available. You can download it, extract it and run the executable file.

The software can actually interface with the majority of microcontrollers, but code for the classic Arduino boards is also available.

All of these stuff can be downloaded from its webpage:

[Download ESPlot][2]

The software is licensed under the [AGPL 3.0][5]. You can get the [source code here][6].

### In the end …

Since most of the other 3d-hardware accelerated plots are expensive and not always customizable, ESPlot would be a good choice for people in this field if it fulfills their need.

I am not involved in this embedded system and microcontrollers, so it wasn’t possible for me to test it out. But don’t let that discourage you from trying it yourself.

--------------------------------------------------------------------------------

via: https://itsfoss.com/esplot/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://www.uni-saarland.de/en/home.html
[2]: https://www.uni-saarland.de/en/chair/nienhaus/esplot-software.html
[3]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/02/Screenshot_ESPlot2.png?resize=644%2C800&ssl=1
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/02/Screenshot_ESPlot1.png?resize=800%2C673&ssl=1
[5]: https://www.gnu.org/licenses/agpl-3.0.html
[6]: https://gitlab.com/esplot/esplot-computer-software
