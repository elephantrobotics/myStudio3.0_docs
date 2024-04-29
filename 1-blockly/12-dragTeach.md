# Use of drag teaching

> *Before the start*
>
> *1. Make sure the machine is powered on*
>
> *2. Make sure the machine connection is normal*



This chapter introduces how to use the drag teaching function in `blockly`.

It means that under the traction of the operator (pulling the end or pulling a certain operating arm), the operating arm will move along the direction of the human force.

This function can easily plan trajectories (a task with low process trajectory accuracy), so that operators can record and reproduce trajectories without manual programming, which lowers the threshold for operators and improves efficiency.



#### API display

<img src="..\resources\1-blockly\images\drag_teach\blocks.png" style="zoom: 64%;" />





#### Small case

We will achieve such an effect: drag the robotic arm to perform some actions at will. After the drag is completed, the robotic arm will perform the action just now. Equivalent to track recording and playback.

The complete code is as follows:

<img src="..\resources\1-blockly\images\drag_teach\code.png" style="zoom: 64%;" />

Code explanation:

- Recording track: After executing this block, the robot arm joint brake is relaxed and the robot arm can now be dragged
- Wait 10 seconds (equivalent to 10 seconds of recording)
- Pause recording: The robot arm joints are braked and locked and cannot be dragged by humans.
- Wait 5 seconds
- Play track: The robot arm starts executing the track just recorded
- Wait 10 seconds (equivalent to playing the 10-second track just recorded)


---

[← Previous page](./11-pumpUse.md) | [Next page →](./13-api.md)
