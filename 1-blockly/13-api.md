# Detailed explanation of building block interface

This chapter introduces the meaning of building blocks and the explanation of input items in `blockly`.

> The building blocks in the basic programming classification are beyond the scope of this chapter



**Some notes:**

1、Python Prototypes in interface explanation, [here](https://github.com/elephantrobotics/pymycobot/blob/main/pymycobot/mercury_api.py)can be found.

2、Interfaces with return values need to be used with the `Print` building block in the `Text` category under the `Basic Program` category. When running the code, the `Print` block will print out the return value.



**for example:**

**Wrong way to use**:
![](..\resources\1-blockly\images\api\error.png)




**Correct way to use**:
![](..\resources\1-blockly\images\api\currect.png)






## Motion control category



### Drag & Teach category

![](..\resources\1-blockly\images\api\drag_teach.png)



**Recording track**

- **Python Prototype**: `drag_tech_save()`

- **Interface Description**: After use, the robotic arm will relax and can be dragged by the user, and the user's drag trajectory will be recorded in real time.



**Execute track**

- **Python Prototype**: `drag_tech_execute()`

- **Interface Description**: Play user-recorded tracks



**Pause recording**

- **Python Prototype**: `drag_tech_pause()`
- **Interface Description**: Pause recording. The robotic arm will be locked and cannot be dragged.



**Track clear**

- **Python Prototype**: `drag_teach_clean()`

- **Interface Description**: Clear user-recorded tracks










### Angle & Coord category

![](..\resources\1-blockly\images\api\angle&coords.png)



![](..\resources\1-blockly\images\api\angle&coords2.png)



**Send Angles**

- **Python Prototype**: `send_angles(angles,speed)`
- **Interface Description**: Send all angles to robot arm.

- **Params**
  - `angles`: coords(`List[float]`)
  - `speed`: (`int`) 0 ~ 100



**Set Coord**

- **Python Prototype**: `send_coords(coords,speed,mode)`

- **Interface Description**: Send all coordinates to the robot arm.

- **Params**

  - `coords`: coords(`List[float]`)

  - `speed`: (`int`) 0 ~ 100



**Get Angles**

- **Python Prototype**: `get_angles()`

- **Interface Description**: Get the degrees of all joints

- **Return**:

  - joint angle value



**Get Joint Angle**

- **Python Prototype**: `get_angle(id)`

- **Interface Description**: Obtain robot single joint angle control

- **Params**
  - `id`: joint id: 1-7

  - `degree`: degree




**Get Coords**

- **Python Prototype**: `get_coords()`

- **Interface Description**:

  - Get Cartesian coordinates



**Set Joint Angle**

- **Python Prototype**: `send_angle(id, degree, speed)`

- **Interface Description**: Robot single joint angle control

- **Params**

  - `id`: joint id: 1-7

  - `degree`: degree

  - `speed`: speed



**Send Coord**

- **Python Prototype**: `send_coord(id, value, speed)`
- **Interface Description**: Robot single coordinate control

- **Params**
  - `id`: Coordinates: 1-6 correspond to x, y, z, rx, ry, rz respectively
  - `value`: coord value
  - `speed`: speed



**Angles is in position**

- **Python Prototype**: `is_in_position([j1,j2,j3,j4,j5,j6,j7],0)`

- **Interface Description**: Check whether the machine angle reaches the specified position

- **Params**:
   - `j1`: j1 angle value
   - `j2`: j2 angle value
   - `j3`: j3 angle value
   - `j4`: j4 angle value
   - `j5`: j5 angle value
   - `j6`: j6 angle value
   - `j7`: j7 angle value


- **Return**:

  - 0: Did not reach the specified location

  - 1: Arrive at designated location





**Coords is in position**

- **Python Prototype**: `is_in_position([x,y,z,rx,ry,rz],1)`

- **Interface Description**: Check whether the machine coord reaches the specified position

- **Params**:
   - x coordinate value

   - y coordinate value

   - z coordinate value

   - rx coordinate value

   - ry coordinate value

   - rz coordinate value



- **Return**:

  - 0: Did not reach the specified location
  - 1: Arrive at designated location



**Pause**

- **Python Prototype**: `pause`
- **Interface Description**: Enter the pause state, suspending all movements of the machine.





**Resume**

- **Python Prototype**: `resume`
- **Interface Description**: Exit the pause state and resume machine movement.



**Stop**

- **Python Prototype**: `stop`
- **Interface Description**: Stop all movement of the machine.



**Is Paused**

- **Python Prototype**: `is_paused`
- **Interface Description**: Detect whether the machine is in paused state.
- **Return**:
   - 0: Not in pause state
   - 1: In paused state
   - -1: Error



**Is Moving**

- **Python Prototype**: `is_moving(id, value, speed)`
- **Interface Description**: Detect whether the machine is moving.
- **Return**:
  - 0: The machine is not running
  - 1: The machine is running
  - -1: Machine data error







### Jog control category

The so-called jog control is to control the mechanical arm to move in the forward or reverse direction until the movement reaches the limit.

<img src="..\resources\1-blockly\images\api\jog.png" style="zoom:200%;" />







**Jog Angle**

- **Python Prototype**: `jog_angle（joint_id,direction,speed）`

- **Interface Description**: Jog control angle. Control the joint to move in the forward or reverse direction until the movement reaches the joint limit.

- **Params**
   - `joint_id`: (`int`) joint id: 1 ~ 7
   - `direction`: direction: 1 / 0
   - `speed`: speed: 0 ~ 100





**Jog Coord**

- **Python Prototype**: `jog_coord（coord_id,direction,speed）`

- **Interface Description**: Jog control coordinates. Control the coordinates to move in the forward or reverse direction until the movement reaches the joint limit.

- **Params**
   - `coord_id`: coordinate id: 1 ~ 6 (corresponding to X, Y, Z, RX, RY, RZ)
   - `direction`: `0` - decrease, `1` - increase
   - `speed`: speed0 ~ 100





**Jog Angle Increment**

- **Python Prototype**: `jog_increment_angle(joint_id,value,speed)`

- **Interface Description**: Angle step mode. Control the joint to add the given value to the current angle value

- **Params**
   - `joint_id`: (`int`) joint id: 1 ~ 7
   - `value`: incremental value
   - `speed`: speed: 0 ~ 100





**Jog Coord Increment**

- **Python Prototype**: `jog_increment_coord(coord_id,value,speed)`

- **Interface Description**: Coordinate stepping mode. Controls the coordinates to be added to the current value by the given value

- **Params**

   - `coord_id`: coordinate id: 1 ~ 6 (corresponding to X, Y, Z, RX, RY, RZ)

   - `value`: incremental value
   - `speed`: speed0 ~ 100





### Coord. system category

![](..\resources\1-blockly\images\api\coordsystem.png)

**Get Tool coordinate system**

- **Python Prototype**: `get_tool_reference()`
- **Interface Description**: Get the tool coordinate system.
- **Return**:
  - `(list)` [x，y，z，rx，ry，rz]





**Set Tool Coord**

- **Python Prototype**: `set_tool_reference(coords)`
- **Interface Description**: Set the tool coordinate system.
- **Params**:
  - `(list)` [x, y, z, rx, ry, rz]。



**Get World Coord**

- **Python Prototype**: `get_world_reference()`
- **Interface Description**: Get world coordinate system
- **Return**:
  - `(list)` [x, y, z, rx, ry, rz]。





**Set World Coord**

- **Python Prototype**: `set_world_reference(coords)`

- **Interface Description**: Set world coordinate system

- **Params**:
  - `coords`: (`list`) [x, y, z, rx, ry, rz]。



**Get Reference Frame**

- **Python Prototype**: `get_reference_frame()`
- **Interface Description**: Get the base coordinate system.
- **Return**:
  - 0 - Base
  - 1 - Tool。



**Set Reference Frame**

- **Python Prototype**: `set_reference_frame(rftype)`

- **Interface Description**: Set the base coordinate system.
- **Params**:
  - `rftype`: 0 - Base 1 - Tool。



**Get Movement Type**

- **Python Prototype**: `get_movement_type()`
- **Interface Description**: Get the motion type.
- **Return**: 1 - movel，0 - moveJ。



**Set Movement Type**

- **Python Prototype**: `set_movement_type(move_type)`

- **Interface Description**: Set the motion type.

- **Params**:
  - `move_type`: 1 - movel，0 - moveJ。



**Get End Coord**

- **Python Prototype**: `get_end_type()`
- **Interface Description**: Get the end coordinate system.
- **Return**: 0 - flange, 1 - tool.



**Set End Coord**

- **Python Prototype**: `set_end_type(end)`

- **Interface Description**: Set the end coordinate system.

- **Params**:
  - `end`: 0 - flange, 1 - tool.









### Set joint limits category

![](..\resources\1-blockly\images\api\joint_limit.png)



**Get Joint Min Angle**

- **Python Prototype**: `get_joint_min_angle(joint_id)`
- **Interface Description**: Get the minimum motion angle of the specified joint
- **Params**: `joint_id`: (`int`)
- **Return**:
  - angles(`float`)



**Get Joint Max Angle**

- **Python Prototype**: `get_joint_max_angle(joint_id)`
- **Interface Description**: Get the maximum motion angle of the specified joint
- **Params**: `joint_id`: (`int`)
- **Return**:
  - angles`float`)



**Set Joint Min Angle**

- **Python Prototype**: `set_joint_min(id, angle)`
- **Interface Description**: Sets the minimum angle of the specified joint.

- **Params**:
  - `joint id`
  - `angle`



**Set Joint Max Angle**

- **Python Prototype**: `set_joint_max(id, angle)`
- **Interface Description**: Sets the maximum angle of the specified joint.

- **Params**:
  - `joint id`
  - `angle`






### Base IO status category

![](..\resources\1-blockly\images\api\basic_io.png)

**Set basic pin output**

- **Python Prototype**: `set_basic_output(id,state)`
- **Interface Description**: Set base pin output
- **Params**:
   - `id`: pin number
   - `state`: select output state



**Get basic pin output**

- **Python Prototype**: `set_basic_output(id)`
- **Interface Description**: Get base pin output
- **Params**:
  - `id`: pin
- **Return**:
  - Pin input status









### Circular motion category

![](..\resources\1-blockly\images\api\circle_move.png)





**Arc**

- **Python Prototype**: `write_move_c(transpoint,endpoint,speed)`

- **Interface Description**: Arc trajectory motion

- **Params**:

  - `transpoint`: Arc way point`(list)`: [x,y,z,rx,ry,rz]
  - `endpoint`: Arc end point`(list)`: [x,y,z,rx,ry,rz]









### Joint motor setting category

![](..\resources\1-blockly\images\api\motor.png)



**Is Joint Motor Enable**
- **Python Prototype**: `is_servo_enable(servo_id)`
- **Interface Description**: Determine whether the servo is turned on
- **Params**: `servo_id` (`int`) 1 ~ 7
- **Return**:
   - `0`: not enabled
   - `1`: enabled
   - `-1`: error



**Is All Joint Motors Enable**
- **Python Prototype**: `is_all_servo_enable()`
- **Interface Description**: Determine whether all servos are turned on
- **Return**:
   - `0`: Not all are enabled
   - `1`: both are enabled
   - `-1`: error



**Set Joint Motor Calibration**

- **Python Prototype**: `set_servo_calibration(servo_no)`
- **Interface Description**: Calibrate the joint actuator with the current position as the angle zero point.
- **Params**:
  - `servo_no`: Servo number, 1 - 7.





**Release Joint Motor**

- **Python Prototype**: `release_servo(servo_id)`
- **Interface Description**: The specified joint motor is powered off
- **Params**: `servo_id`: 1 ~ 7



**Focus Joint Motor**

- **Python Prototype**: `focus_servo(servo_id)`
- **Interface Description**: Power on the specified joint motor
- **Params**: `servo_id`: 1 ~ 7





**Joint Motor Close/Open brake**

- **Python Prototype**: `joint_brake(servo_id,status)`
- **Interface Description**: Set the brake state of the specified joint motor
- **Params**:
   - `servo_id`: joint motor 1 ~ 7
   - `status`: open/closed



**Read zero encoder value**

- **Python Prototype**: `get_zero_pos`
- **Interface Description**: Read the zero encoder value
- **Return**:
  - Zero encoder value





**Whether the zero position has been set**

- **Python Prototype**: `is_init_calibrated`
- **Interface Description**: Determine whether zero position has been set
- **Return**:
   - `True`: zero bit set
   - `False`: zero bit not set







### Joint motors status category

![](..\resources\1-blockly\images\api\motor_status.png)



**Get Joint Motors Velocity**

- **Python Prototype**: `get_servo_speeds()`
- **Interface Description**: Get Joint Motors Velocity
- **Return**:
  - speeds



**Get Joint Motors Status**

- **Python Prototype**: `get_servo_status()`
- **Interface Description**: Get the status of each joint motor
- **Return**:
  - status of each joint motor



**Get Joint Motor Currents**

- **Python Prototype**: `get_servo_currents()`
- **Interface Description**: Get the motor current of each joint
- **Return**:
  - Motor current of each joint





**Restore All Joint Motor**

- **Python Prototype**: `servo_restore(254)`
- **Interface Description**: Joint motor abnormality recovery Reset all joint motors





**Restore Joint Motor**

- **Python Prototype**: `servo_restore(joint_id)`
- **Interface Description**: Joint motor abnormal recovery
- **Params**:
  - `joint_id`: Joint id: 1-7





## End-Effector Tool category



### Gripper Control category

![](..\resources\1-blockly\images\api\gripper.png)



**Set Pro Adaptive Gripper**

- **Python Prototype**: `set_gripper_enabled(flag)`
- **Interface Description**: Setting up the Pro Adaptive Gripper
- **Params**:
  - `flag`: Enabled  /  Release





**Set Gripper Calibration**
- **Python Prototype**: `set_gripper_calibration()`
- **Interface Description**: Set the current position to zero and set the current position value to `2048`.







**Set Gripper State**
- **Python Prototype**: `set_gripper_state(flag, speed, mode)`
- **Interface Description**: Set the gripper switch state
- **Params**
   - `flag`: status: open/closed
   - `speed` : speed: 0 ~ 100
   - `mode`: gripper type



**Get Gripper Value**
- **Python Prototype**: `set_gripper_value(值，speed，模式)`
- **Interface Description**: get gripper value
- **Params**
   - `value`: value: 0 ~ 100
   - `speed`: speed: 0 ~ 100
   - `mode`: gripper type



**Set Gripper Mode**

- **Python Prototype**: `set_gripper_mode(status)`
- **Interface Description**: Set the gripper mode.
- **Params**:
  - `status` : Transparent Transmission / Port Mode.



**Get Gripper Mode**

- **Python Prototype**: `get_gripper_mode()`

- **Interface Description**: get gripper mode

- **Return**:
  - `0`: Transparent Transmission
  - `1`: Port Mode





### Atom IO category

![](..\resources\1-blockly\images\api\atom_io.png)



**setting IO value**

- **Python Prototype**: `set_digital_output(id,state)`
- **Interface Description**: Set IO value
- **Params**
   * `id`: io serial number
   * `state`: select state 0 or 1



**Get IO value**

- **Python Prototype**: `get_digital_input(id)`
- **Interface Description**: Read IO value
- **Params**
  * `id`: io serial number







### Atom settings category

![](..\resources\1-blockly\images\api\set_rgb.png)



**Set Color**

- **Python Prototype**: `set_color(red=0,green=0,blue=0)`
- **Interface Description**: Set the color of the end LED light
- **Params**:
  - `red`: Red 0 - 255
  - `green`: Green 0 -255
  - `blue`: Blue （0- 255）









## Status Monitor category

### Operation Status category

![](..\resources\1-blockly\images\api\system.png)

**Power On**

- **Python Prototype**: `power_on()`
- **Interface Description**: The machine is powered on and can be controlled



**Power on only**

- **Python Prototype**: `power_on_only()`
- **Interface Description**: When the machine is powered on, the machine is uncontrollable



**Power Off**

- **Python Prototype**: `power_off()`
- **Interface Description**: the machine is powered off



**Is Power On**

- **Python Prototype**: `is_power_on()`
- **Interface Description**: Check whether the robot arm is powered on

- **Return**:
   - `1`: power on
   - `0`: power off
   - `-1`: error



**Release All Servos**

- **Python Prototype**: `release_all_servos()`

- **Interface Description**: Set the robot arm to free motion mode



**Focus all servos**
- **Python Prototype**: `focus_all_servos()`
- **Interface Description**: Robot opens torque output







**Obtain the host computer error status**
- **Python Prototype**: `get_robot_status()`
- **Interface Description**: Obtain the error safety status of the host computer
- **Return**:
  - status information





**Read joint exception times**

- **Python Prototype**: `get_comm_error_counts(joint_id,type)`
- **Interface Description**: Get the number of joint abnormalities
- **Params**:
   - `joint_id`: joint id: 1-7
   - `type`: exception type
- **Return**:
   - Number of exceptions





**Set the position deviation value**

- **Python Prototype**: `set_pos_over_shoot(value)`

- **Interface Description**: Set the position deviation value

- **Params**:
  - `value`: position deviation value



**Read position out of tolerance value**

- **Python Prototype**: `get_pos_over_shoot`
- **Interface Description**: Read position out-of-tolerance value
- **Return**:
  - Position out of tolerance value









### System Information category

![](..\resources\1-blockly\images\api\system_info.png)



**Get Master Control Info**

- **Python Prototype**: `get_system_version()`
- **Interface Description**: Get Master Control Info
- **Return**:
  - Master Control Info



**Get End Firmware Info**

- **Python Prototype**: `get_atom_version()`
- **Interface Description**: Get the terminal firmware version
- **Return**:
   - End firmware version





**Get robot type**

- **Python Prototype**: `get_robot_type()`
- **Interface Description**: Get the robot model
- **Return**:
   - Get the robot model



**Go zero when joints over limit**

- **Python Prototype**: `over_limit_return_zero`
- **Interface Description**: The machine returns to zero after exceeding the limit



**Get Error Information**

- **Python Prototype**: `get_error_information()`
- **Interface Description**: Get error message
- **Return**:
  - Get error message



**Clear Error Information**

- **Python Prototype**: `clear_error_information()`
- **Interface Description**: Clear error message









## Other category



### Deflection angle category

![](..\resources\1-blockly\images\api\zero_space_pos.png)

**Get the value of deflect angle in null space**

- **Python Prototype**: `get_solution_angles()`
- **Interface Description**: Get the zero space deflection angle value
- **Return值**:
  - `J1_angle_low`: -90  ~ +90
  - `J1_angle_high`: -90  ~ +90



**Set the value of deflect angle in null space**

- **Python Prototype**: `set_solution_angles(J1_angle,speed)`
- **Interface Description**: Get the zero space deflection angle value
- **Params**:
  - `J1_angle`: -90  ~ +90
  - `speed`: 1-100
















---

[← Previous page](./11-pumpUse.md) | [Next page →](../2-quickmove/2.1-quickmovefirstuse.md)
