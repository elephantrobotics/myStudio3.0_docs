# Program Control

> *Before the start*
>
> *1. Make sure the machine is powered on*
>
> *2. Make sure the machine connection is normal*

This chapter introduces how to debug the building block code through the `Run Panel` and realize the pause, single-step execution and stop of the program.

Edit a program that controls the color change of the LED light at the end of the robotic arm



use `Set Color`block：

<img src="..\resources\1-blockly\images\program\block.png"  />



Full code:

<img src="..\resources\1-blockly\images\program\code.png"  />



Click the `Run` button. When the run panel pops up, click the `Pause` button immediately. The program will pause after executing the first instruction `time.sleep(5)`

<img src="..\resources\1-blockly\images\program\run.png"  />

The program has been paused. The next instruction to be executed appears `mc.set_color(255,0,0)

at this time:

- If you click the `Recover` button, the program will automatically execute;

- If you click the `One-Step` button, the program will execute the next instruction, which is `mc.set_color(255,0,0)`;
- If you click the `Stop` button, the program will be terminated;



As for what to do next, it’s up to you!


---

[← Previous page](./8-singleStep.md) | [Next page →](./10-gripperUse.md)

