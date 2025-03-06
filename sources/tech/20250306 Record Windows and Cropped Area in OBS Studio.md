[#]: subject: "Record Windows and Cropped Area in OBS Studio"
[#]: via: "https://itsfoss.com/obs-record-window-area/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Record Windows and Cropped Area in OBS Studio
======

[![Warp Terminal][1]][2]

When it comes to [screen recording in Linux][3] or any other operating system, OBS Studio becomes he go-to choice.

It offers all the features baked in for users, ranging from casual screen recorders to advanced streamers.

One such useful feature is to record a part of the screen in OBS Studio. I'll share the detailed steps for Linux users in this tutorial.

🚧

The method mentioned is based on a Wayland session. Also, this is a personal workflow, and if readers have better options, feel free to comment, so that I can improve the article for everyone.

### Record an application window in OBS Studio

Before starting, first click on File → Settings from OBS Studio main menu. Here, in the Settings window, go to the Video section and note the **Canvas resolution** and **Output scale** resolution for your system.

![Note Canvas and Output Scale values][4]

This will be helpful when you are reverting in a later step.

#### Step 1: Create a new source

First, let's create a new source for our recording. Click on the “+” icon on the OBS Studio home screen as shown in the screenshot below. Select “Screen Capture (Pipewire)” option.

📋

For X11 system, this may be __Display Capture (XSHM)__.

![Click on "+" to add a new source][5]

On the resulting window, give a name to the source and then click OK.

![Give a name to the source][6]

Once you press OK, you will be shown a dialog box to select the record area.

#### Step 2: Select the window to record

Here, select the **Window** option from the top bar.

![Select the window to be recorded.][7]

Once you click on the Window option, you will be able to see all the open windows listed. Select a window that you want to record from the list, as shown in the screenshot above.

This will give you a dialog box, with a preview of the window being recorded.

Enable the cursor recording (if needed) and click OK.

![Selected window in preview][8]

#### Step 3: Crop the video to window size

Now, in the main OBS window, you can see that the application you have selected is not filling the full canvas, in my case 1920×1080.

![Empty space in canvas][9]

The output will contain this window and the rest of the canvas in black if you keep recording with this setting.

You need to crop the area so that only the necessary part is present on the output file.

For this, right-click on our source and select **Resize Output (Source Size)** option, as shown below:

![Resize output source size][10]

Click on Yes, when prompted.

![Accept Confirmation][11]

As soon as you click Yes, you can see that the canvas is now reduced to the size of the window.

![Canvas Resized][12]

#### Step 4: Record the video

You can now start recording the video using the Record button.

![Start video recording][13]

Once finished, stop recording, and the saved video file won't contain any other part, except the window.

#### Step 5: Delete the video source

Now that you have recorded the video, let's remove this particular source.

Right-click on the source and select **Remove**.

![Remove the source][14]

#### Step 6: Revert the canvas and output scale

While we were resizing the canvas to the window, the setting has been also changed on your OBS Studio video settings. If left unchanged, your future videos will also be recorded with the reduced size.

So, click on _File_ in the OBS Studio main menu and select _Settings_.

![Click on File → Settings][15]

On the Settings window, go to **Videos** and revert the **Base Canvas Resolution** and **Output Scaled Resolution** to your preferred normal values. Then click **Apply**.

![Revert Canvas Size to normal][16]

### Record an area on the screen in OBS Studio

This is the same process as the one described above, except for the area selection.

#### Step 1: Create a new source

Click on the plus button on the Sources section in OBS Studio and select Screen Capture.

![Select Screen Capture][17]

Name the source and click OK.

#### Step 2: Select a region

On the area selection dialog box, click on **Region**. From the section, select **Select Region** option.

![Select Region][18]

Notice the cursor has now changed to a plus sign. Drag the area you want to record.

![Select Area to Record][19]

You can see that the preview now has the selected area. Don't forget to enable the cursors, if needed.

It is normal that the canvas is way too big and your video occupies only a part of it.

![Canvas Size Mismatch][20]

#### Step 3: Resize the source

Like in the previous section, right-click on the source and select Resize output option.

![Resize Output to Area Capture][21]

#### Step 4: Record and revert the settings

Start recording the video. Once it is completed, save the recording and remove the source. **Revert the canvas and output scale settings, as shown in _step 6_ of the previous section**.

💬 _Hope this guide has helped you record with OBS Studio. Please let me know if this tutorial helped you or if you need further help._

--------------------------------------------------------------------------------

via: https://itsfoss.com/obs-record-window-area/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/best-linux-screen-recorders/
[4]: https://itsfoss.com/content/images/2025/01/revert-the-size-to-normal.png
[5]: https://itsfoss.com/content/images/2025/01/click-on-plus-to-add-a-new-source.webp
[6]: https://itsfoss.com/content/images/2025/01/give-a-name-to-the-source.png
[7]: https://itsfoss.com/content/images/2025/01/select-the-window-to-be-recorded.png
[8]: https://itsfoss.com/content/images/2025/01/the-selected-window-is-in-the-preview.png
[9]: https://itsfoss.com/content/images/2025/01/canvas-is-not-full-with-the-selected-window.webp
[10]: https://itsfoss.com/content/images/2025/01/resize-output-source-size.png
[11]: https://itsfoss.com/content/images/2025/01/accept-confirmation.png
[12]: https://itsfoss.com/content/images/2025/01/canvas-resized-to-window-size.webp
[13]: https://itsfoss.com/content/images/2025/01/start-recording-by-clicking-on-record-button.png
[14]: https://itsfoss.com/content/images/2025/01/remove-the-source-after-recording.png
[15]: https://itsfoss.com/content/images/2025/01/click-on-file-and-settings.png
[16]: https://itsfoss.com/content/images/2025/01/revert-the-size-to-normal-1.png
[17]: https://itsfoss.com/content/images/2025/01/click-on-plus-to-add-a-new-source-1.webp
[18]: https://itsfoss.com/content/images/2025/01/click-on-region-select-region.png
[19]: https://itsfoss.com/content/images/2025/01/select-the-area-to-record.webp
[20]: https://itsfoss.com/content/images/2025/01/the-canvas-size-mismatch.webp
[21]: https://itsfoss.com/content/images/2025/01/resize-output-to-area-capture.png
