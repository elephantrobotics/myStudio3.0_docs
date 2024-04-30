# small case

_before the start_

> _1. Make sure the machine is powered on_
>
> _2. Make sure the machine connection is normal_

Let's write a small case to introduce the basic use of `blockly`.

**Case description**: Control the robotic arm to return to zero, then control a joint to move to a position of 20 degrees, and then return to zero.

**Step 1:** First click the `Posture` button to open the attitude view, where you can see the angle and coordinate information of the robotic arm.

<img src="..\resources\1-blockly\images\littleCase\1.png" style="zoom:80%;" />

<img src="..\resources\1-blockly\images\littleCase\zitai.png" style="zoom:80%;" />

- 1: Collapse the attitude panel: Click the `>>` button of the attitude view panel to collapse the panel.
- 2: Robot angle and coordinate data.

**Step 2:** Start programming

Open the first-level category `Motion control` in the toolbox, select the second-level category `Angle & Coord`, and drag the `Send Angles` building block to the workspace.

This building block is used to control the movement of each joint of the robotic arm to a given angle. The default movement speed is 20.

Since `Mercury A1` except `J6` has a zero point angle of `90`, the zero point angle values of other joints are `0`, so the `J6` of the building block needs to be modified to `90`.

<img src="..\resources\1-blockly\images\littleCase\3.png" style="zoom:80%;" />

<img src="..\resources\1-blockly\images\littleCase\send_coords.png" style="zoom: 80%;" />



Open the first-level category `Basic Programming` in the toolbox, select the second-level category `Time`, drag the `Sleep` building block to the workspace, and set the sleep time to `3` seconds.

The sleep time of 3 seconds means: the program waits for 3 seconds before continuing. Why wait 3 seconds? Because it is necessary to ensure that the robot arm completes the first command action before executing other subsequent actions.

<img src="..\resources\1-blockly\images\littleCase\5.png" style="zoom: 80%;" />



<img src="..\resources\1-blockly\images\littleCase\6.png" style="zoom: 80%;" />

Copy the `Sent Angles` block and change the `J1` angle to 20:

- Click with the mouse to select the `Sent Angles` building block in the workspace;
- Hold down Ctrl + C on the keyboard to copy the `Sent Angles` building block;
- Press Ctrl + V on your keyboard to paste the `Sent Angles` block
- Modify the new building block `J1` to 20;
- Drag the building block to connect it with the `Sleep` building block;

<img src="..\resources\1-blockly\images\littleCase\7.png" style="zoom: 67%;" />



Similar to the above operation, copy the `Sleep` building block and set the sleep time to `3` seconds;

Copy the first `Sent Angles` block in the workspace again;

The complete code is as follows:

<img src="..\resources\1-blockly\images\littleCase\code.png" style="zoom: 67%;" />

> This code means:
>
> - Control the robotic arm to return to zero point
>
> - Wait 3 seconds (the machine will finish at zero)
>
> - Move joint 1 to a position of 20 degrees
>
> - wait 3 seconds
>
> - Control the robotic arm to return to zero point

Finally, click the `Run Panel` button. After opening the panel, click the `Run` button to start executing the code.

<img src="..\resources\1-blockly\images\littleCase\open_run_plane.png" style="zoom: 67%;" />

<img src="..\resources\1-blockly\images\littleCase\run.png" style="zoom: 67%;" />

After the code is completed, click the panel `X` to close the panel

<img src="..\resources\1-blockly\images\littleCase\run_finish.png" style="zoom: 67%;" />

**Step 3:** Save and load the file (or save and load the workspace)

`blockly` supports saving and loading workspaces.

Click the `File` button, a drop-down menu will appear, click the `Save` button, and save the current workspace code as `blocks.json` in the `er` directory.

<img src="..\resources\1-blockly\images\littleCase\save.png" style="zoom: 67%;" />

**Step 4:** Create a new workspace operation (this operation will clear all codes in the workspace)

Click the `File` button, a drop-down menu will appear, click the `New Workspace` button, a prompt will appear, click the `Confirm` button

<img src="..\resources\1-blockly\images\littleCase\clear_tips.png" style="zoom: 67%;" />

New workspace completed

<img src="..\resources\1-blockly\images\littleCase\new.png" style="zoom: 67%;" />

**Step 5:**Load workspace operation, load the workspace file we saved before

Click the `File` button and a drop-down menu will appear. After clicking the `Open File` button in the menu, find the `blocks.json` file we just saved in the `er` directory.

<img src="..\resources\1-blockly\images\littleCase\load.png" style="zoom: 67%;" />

Loading completed

<img src="..\resources\1-blockly\images\littleCase\load_finish.png" style="zoom: 67%;" />

---

[← Previous page](./2-interfaceDescription.md) | [Next page →](./4-autofill.md)
