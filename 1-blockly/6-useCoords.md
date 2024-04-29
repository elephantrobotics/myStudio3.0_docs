# Learn to use coordinate control

_before the start_

> _1. Make sure the machine is powered on_
>
> _2. Make sure the machine connection is normal_
>
> _3. Make sure the machine is in zero position_

This chapter introduces how to use coordinates to control the robotic arm.

### Mainly involved APIs:

<img src="..\resources\1-blockly\images\useCoords\send_coords.png" style="zoom: 80%;" />

**Set Coord**

- **Prototype**: `send_coords(values,speed)`
- **Interface Description**: Set multiple coordinates of the robotic arm
- **Parameters**:
  - values: [X,Y,Z,RX,RY,RZ]
  - speed: speed, range is 1-100

### Small case

#### Before using coordinate movement for the first time, some operations need to be performed:

- To return the robotic arm to the zero position, please refer to [Controlling the robotic arm to return to zero](3-littleCase.md)

- Set the initial attitude of the robot arm coordinate movement (the machine `J7` needs to be parallel to the ground)

  -As shown in the code below:

     <img src="..\resources\1-blockly\images\useCoords\init_pos.png" />

  Open the `Run Panel` and run the code.

#### Coordinate movement

Drag a `Set Coordinates' building block to the workspace, and click the `Quick Fill`button in the building block to fill in the data, and change the`Z`axis data to`400`

<img src="..\resources\1-blockly\images\useCoords\auto_fill.png" style="zoom:67%;" />

The complete code is as follows:

<img src="..\resources\1-blockly\images\useCoords\full_code.png" style="zoom: 80%;" />

Execute the code and observe the robot arm moving up and down throughout the process

<img src="..\resources\1-blockly\images\useCoords\run_finish.png" style="zoom: 80%;" />

---

[← Previous page](./5-quickMove.md) | [Next page →](./7-chatGPT.md)
