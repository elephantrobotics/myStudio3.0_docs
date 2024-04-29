# User Suction Pump

> *Before the start*
>
> *1. Make sure the machine is powered on*
>
> *2. Make sure the machine connection is normal*

This chapter introduces how to use `blockly` to control the suction pump connected to the `Mercury A1` robotic arm (as shown below)

<img src="..\resources\1-blockly\images\pump\pump.png"  />

#### API display

<img src="..\resources\1-blockly\images\pump\code.png" style="zoom: 67%;" />

<img src="..\resources\1-blockly\images\pump\function.png" style="zoom: 67%;" />

The following building blocks are mainly used

- **1**: `setting IO value`: Set the IO output status at the end of the robot arm
   * Parameter introduction:
     This module has two parameters that can be adjusted:
     * IO pin: 1-2
     * IO output status: 0-low level, 1-high level

- **2**: `Functions` building blocks: modularize a set of building blocks
   * Parameter introduction:
     This module has a parameter that can be adjusted:
     *Method name: Name the method



#### Small case

1. First, you need to create two `method` building blocks and name them `pump_on` and `pump_off` respectively. At the same time, drag in the `setting IO value` and `Sleep` building blocks into these two `Functions` building blocks.

    `pump_on` method: used to open the suction pump

    `pump_off` method: used to turn off the suction pump



2、At the same time, you can find that there are two usable `pump_on` and `pump_off` building blocks in the method classification.

<img src="..\resources\1-blockly\images\pump\create_function.png" style="zoom: 67%;" />









Added code using the `pump_on` and `pump_off` building blocks. The complete code is as follows:

<img src="..\resources\1-blockly\images\pump\full_code.png" style="zoom: 67%;" />




---

[← Previous page](./10-gripperUse.md) | [Next page →](./12-dragTeach.md)
