# 积木块接口详解

本章介绍 `blockly` 中积木块的含义与输入项的解释。

> 基础编程分类中的积木块不在本章讨论范围中



**一些说明：**

1、接口解释中的 python 原型，[在这里](https://github.com/elephantrobotics/pymycobot/blob/main/pymycobot/mercury_api.py)可以找到。

2、有返回值的接口需要搭配`基础编程`分类下`文本`分类中的`输出`积木块使用。运行代码时，`输出`积木块会再打印出返回值。

比如：

**错误使用**：
![](..\resources\1-blockly\images\api\error.png)




**正确使用**：
![](..\resources\1-blockly\images\api\currect.png)






## 运动控制



### 拖动示教分类接口

![](..\resources\1-blockly\images\api\drag_teach.png)



**录制轨迹**

- **python接口原型**：`drag_tech_save()`

- **接口说明**：使用后，机械臂会放松，可以被用户拖动，并且会实时记录用户拖动的轨迹。




**播放轨迹**

- **python接口原型**：`drag_tech_execute()`

- **接口说明**：播放用户录制的轨迹




**暂停录制**

- **python接口原型**：`drag_tech_pause()`
- **接口说明**：暂停录制。机械臂会锁紧，不可被拖动。



**清除轨迹**

- **python接口原型**：`drag_teach_clean()`

- **接口说明**：清除用户录制的轨迹










### 角度 & 坐标 分类

![](..\resources\1-blockly\images\api\angle&coords.png)



![](..\resources\1-blockly\images\api\angle&coords2.png)



**设置全角度**

- **python接口原型**：`send_angles(angles,speed)`
- **接口说明**：将所有角度发送至机械臂。

- **参数**
  - `angles`：坐标值列表（`List[float]`）
  - `速度`: (`int`) 0 ~ 100



**设置坐标**

- **python接口原型**：`send_coords(coords,speed,mode)`

- **接口说明**：将所有坐标发送至机械臂。

- **参数**

  - `coords`：坐标值列表（`List[float]`）

  - `speed`: (`int`) 0 ~ 100



**获取所有角度**

- **python接口原型**：`get_angles()`

- **接口说明**：获取所有关节的度数

- **返回**：

  - 关节角度值



**读取单关节角度**

- **python接口原型**：`get_angle(id)`

- **接口说明**：获取机器人单关节角度控制

- **参数**
  - `id`：关节 ID：1-7

  - `degree`：角度值




**获取所有坐标**

- **python接口原型**：`get_coords()`

- **接口说明**：

  - 获取笛卡尔坐标



**设置单关节角度**

- **python接口原型**：`send_angle(id, degree, speed)`

- **接口说明**：机器人单关节角度控制

- **参数**

  - `id`：关节 ID：1-7

  - `degree`：角度值

  - `speed`：速度



**设置单个坐标**

- **python接口原型**：`send_coord(id, value, speed)`
- **接口说明**：机器人单坐标控制

- **参数**
  - `id`：坐标：1-6分别对应x、y、z、rx、ry、rz
  - `value`：坐标值
  - `speed`：速度



**角度是否到达位置**

- **python接口原型**：`is_in_position([j1,j2,j3,j4,j5,j6,j7],0)`

- **接口说明**：检查机器角度是否到达指定位置

- **参数**：
  - `j1`：j1角度值
  - `j2`：j2角度值
  - `j3`：j3角度值
  - `j4`：j4角度值
  - `j5`：j5角度值
  - `j6`：j6角度值
  - `j7`：j7角度值



- **返回**：

  - 0：未到达指定位置

  - 1：到达指定位置





**坐标是否到达位置**

- **python接口原型**：`is_in_position([x,y,z,rx,ry,rz],1)`

- **接口说明**：检查机器角度是否到达指定位置

- **参数**：
  - x 坐标值

  - y 坐标值

  - z 坐标值

  - rx坐标值

  - ry坐标值

  - rz坐标值



- **返回**：

  - 0：未到达指定位置
  - 1：到达指定位置



**暂停**

- **python接口原型**：`pause`
- **接口说明**：进入暂停状态，暂停机器的所有运动。





**恢复**

- **python接口原型**：`resume`
- **接口说明**：退出暂停状态，恢复机器运动。



**停止**

- **python接口原型**：`stop`
- **接口说明**：停止机器的一切运动。



**是否已暂停**

- **python接口原型**：`is_paused`
- **接口说明**：检测机器是否处于暂停状态。
- **返回**：
  - 0：不处于暂停状态
  - 1：处于暂停状态
  - -1：错误



**检测是否在运动**

- **python接口原型**：`is_moving(id, value, speed)`
- **接口说明**：检测机器是否在移动。
- **返回**：
  - 0：机器不运转
  - 1：机器正在运转
  - -1：机器数据错误







### 点动控制 分类

所谓点动控制即控制机械臂往正或反方向运动，知道运动到限位为止

<img src="..\resources\1-blockly\images\api\jog.png" style="zoom:200%;" />







**点动控制关节**

- **python接口原型**：`jog_angle（joint_id,direction,speed）`

- **接口说明**：点动控制角度。控制关节往正或反方向运动，直到运动到关节限位。

- **参数**
  - `joint_id`: (`int`) 关节id：1 ~ 7
  - `direction`：方向：1 / 0
  - `speed`: 速度：0 ~ 100





**点动控制坐标**

- **python接口原型**：`jog_coord（coord_id,direction,speed）`

- **接口说明**：点动控制坐标。控制坐标往正或反方向运动，直到运动到关节限位。

- **参数**

  - `coord_id`: 坐标id：1 ~ 6（对应 X、Y、Z、RX、RY、RZ）

  - `direction`: `0` - 减少，`1` - 增加
  - `speed`: 速度0 ~ 100





**角度步进模式**

- **python接口原型**：`jog_increment_angle(joint_id,value,speed)`

- **接口说明**：角度步进模式。控制关节在当前角度值下再加上给定的 value  值

- **参数**
  - `joint_id`: (`int`) 关节id：1 ~ 7
  - `value`：增量值
  - `speed`: 速度：0 ~ 100





**坐标步进模式**

- **python接口原型**：`jog_increment_coord(coord_id,value,speed)`

- **接口说明**：坐标步进模式。控制坐标在当前值下再加上给定的 value  值

- **参数**

  - `coord_id`: 坐标id：1 ~ 6（对应 X、Y、Z、RX、RY、RZ）

  - `value`: 增量值
  - `speed`: 速度0 ~ 100





### 坐标系设置分类

![](..\resources\1-blockly\images\api\coordsystem.png)

**获取工具坐标系**

- **python接口原型**：`get_tool_reference()`
- **接口说明**：获取工具坐标系。
- **返回**：
  - `(list)` [x，y，z，rx，ry，rz]





**设置工具坐标系**

- **python接口原型**：`set_tool_reference(coords)`
- **接口说明**：设置工具坐标系。
- **参数**：
  - `(list)` [x, y, z, rx, ry, rz]。



**获取世界坐标系**

- **python接口原型**：`get_world_reference()`
- **接口说明**：获取世界坐标系。
- **返回**：
  - `(list)` [x, y, z, rx, ry, rz]。





**设置世界坐标系**

- **python接口原型**：`set_world_reference(coords)`

- **接口说明**：设置世界坐标系。

- **参数**：
  - `coords`: (`list`) [x, y, z, rx, ry, rz]。



**获取基坐标系**

- **python接口原型**：`get_reference_frame()`
- **接口说明**：获取基础坐标系。
- **返回**：
  - 0 - 基础
  - 1 - 工具。



**设置基坐标系**

- **python接口原型**：`set_reference_frame(rftype)`

- **接口说明**：设置基础坐标系。

- **参数**：
  - `rftype`：0 - 基础 1 - 工具。



**获取移动类型**

- **python接口原型**：`get_movement_type()`
- **接口说明**：获取运动类型。
- **返回**：1 - movel，0 - moveJ。



**设置移动类型**

- **python接口原型**：`set_movement_type(move_type)`

- **接口说明**：设置运动类型。

- **参数**：
  - `move_type`：1 - movel，0 - moveJ。



**获取末端坐标系**

- **python接口原型**：`get_end_type()`
- **接口说明**：获取末端坐标系。
- **返回**：0 - 法兰，1 - 工具。



**设置末端坐标系**

- **python接口原型**：`set_end_type(end)`

- **接口说明**：设置结束坐标系。

- **参数**：
  - `end`：0 - 法兰，1 - 工具。









### 关节限位设置 分类

![](..\resources\1-blockly\images\api\joint_limit.png)



**获取关节最小角度**

- **python接口原型**：`get_joint_min_angle(joint_id)`
- **接口说明**：获取指定关节的最小运动角度
- **参数**：`joint_id`：(`int`)
- **返回**：
  - 角度值（`float`）



**获取关节最大角度**

- **python接口原型**：`get_joint_max_angle(joint_id)`
- **接口说明**：获取指定关节的最大运动角度
- **参数**：`joint_id`：(`int`)
- **返回**：
  - 角度值（`float`）



**设置关节最小值角度**

- **python接口原型**：`set_joint_min(id, angle)`
- **接口说明**：设置指定关节的最小角度。

- **参数**：
  - `关节id`

  - `角度`



**设置关节最大角度**

- **python接口原型**：`set_joint_max(id, angle)`
- **接口说明**：设置指定关节的最大角度。

- **参数**：
  - `关节id`
  - `角度`







### 设置底座IO状态分类

![](..\resources\1-blockly\images\api\basic_io.png)

**设置底座引脚输出**

- **python接口原型**：`set_basic_output(id,state)`
- **接口说明**：设置底座引脚输出
- **参数**：
  - `id`：引脚号
  - `state`：选择输出状态



**获取底座引脚输入**

- **python接口原型**：`set_basic_output(id)`
- **接口说明**：获取底座引脚输入
- **参数**：
  - `id`：引脚号
- **返回**：
  - 引脚输入状态









### 圆弧运动 分类

![](..\resources\1-blockly\images\api\circle_move.png)





**圆弧轨迹运动**

- **python接口原型**：`write_move_c(transpoint,endpoint,speed)`

- **接口说明**：圆弧轨迹运动

- **参数**：

  - `transpoint`：圆弧途径点`(list)`：[x,y,z,rx,ry,rz]
  - `endpoint`：圆弧结束点`(list)`：[x,y,z,rx,ry,rz]









### 关节电机设置 分类

![](..\resources\1-blockly\images\api\motor.png)



**关节电机是否开启**

- **python接口原型**：`is_servo_enable(servo_id)`

- **接口说明**：判断舵机是否已开启

- **参数**：`servo_id` (`int`) 1 ~ 7

- **返回**：

  - `0`：未开启

  - `1`：已启用

  - `-1`: 错误



**是否所有关节已开启**

- **python接口原型**：`is_all_servo_enable()`

- **接口说明**：判断所有舵机是否已开启

- **返回**：

  - `0`：非都已开启
  - `1`：都已启用
  - `-1`：错误



**设置关节电机零点**

- **python接口原型**：`set_servo_calibration(servo_no)`
- **接口说明**：校准关节执行器以当前位置为角度零点。

- **参数**：
  - `servo_no`：舵机序号，1 - 7。





**关节电机掉电**

- **python接口原型**：`release_servo(servo_id)`
- **接口说明**：指定关节电机断电
- **参数**：`servo_id`：1 ~ 7



**关节电机上电**

- **python接口原型**：`focus_servo(servo_id)`
- **接口说明**：指定关节电机上电
- **参数**：`servo_id`：1 ~ 7





**关节电机打开/关闭刹车**

- **python接口原型**：`joint_brake(servo_id,status)`
- **接口说明**：设置指定关节电机刹车状态
- **参数**：
  - `servo_id`：关节电机 1 ~ 7
  - `status`：打开/关闭



**读取零位编码器值**

- **python接口原型**：`get_zero_pos`
- **接口说明**：读取零位编码器值
- **返回**：
  - 零位编码器值





**是否已设置零位**

- **python接口原型**：`is_init_calibrated`
- **接口说明**：判断是否已设置零位
- **返回**：
  - `True`：已设置零位
  - `False`：未设置零位







### 关节电机状态 分类

![](..\resources\1-blockly\images\api\motor_status.png)



**获取各关节电机速度**

- **python接口原型**：`get_servo_speeds()`
- **接口说明**：获取各关节电机速度
- **返回**：
  - 各关节电机速度



**获取各关节电机的状态**

- **python接口原型**：`get_servo_status()`
- **接口说明**：获取各关节电机的状态
- **返回**：
  - 各关节电机状态



**获取各关节电机电流**

- **python接口原型**：`get_servo_currents()`
- **接口说明**：获取各关节电机电流
- **返回**：
  - 各关节电机电流





**关节电机异常恢复 重置所有关节电机**

- **python接口原型**：`servo_restore(254)`
- **接口说明**：关节异常恢复 重置所有关节电机





**关节电机异常恢复**

- **python接口原型**：`servo_restore(joint_id)`
- **接口说明**：关节电机异常恢复
- **参数**:
  - `joint_id`：关节id：1-7





## 末端工具



### 夹爪控制 分类

![](..\resources\1-blockly\images\api\gripper.png)



**设置 Pro 自适应夹爪**

- **python接口原型**：`set_gripper_enabled(flag)`
- **接口说明**：设置 Pro 自适应夹爪
- **参数**：
  - `flag`：使能  /  释放





**夹爪零位校准**

- **python接口原型**：`set_gripper_calibration()`

- **接口说明**：将当前位置设置为零，设置当前位置值为`2048`。







**设置夹爪状态**

- **python接口原型**：`set_gripper_state(flag, speed, mode)`

- **接口说明**：设置夹爪开关状态

- **参数**
  - `flag`：状态：打开 /关闭
  - `speed` ：速度: 0 ~ 100
  - `mode`：夹爪类型



**设置夹爪值**

- **python接口原型**：`set_gripper_value(值，速度，模式)`

- **接口说明**：设置夹爪值

- **参数**
  - `value`：值：0 ~ 100
  - `speed`：速度：0 ~ 100
  - `mode`：夹爪类型



**设置夹爪模式**

- **python接口原型**：`set_gripper_mode(status)`
- **接口说明**：设置夹爪模式。
- **参数**：
  - `status` ：透传模式 / 端口模式。



**获取夹爪模式**

- **python接口原型**：`get_gripper_mode()`

- **接口说明**：获取夹爪模式

- **返回**：
  - `0`：透传模式
  - `1`：端口模式





### 末端 IO 控制 分类

![](..\resources\1-blockly\images\api\atom_io.png)



**设置IO值**

- **python接口原型**：`set_digital_output(id,state)`
- **接口说明**：设置IO值
- **参数**
  * `id`：io序列号

  * `state`：选择状态0或1



**读取IO值**

- **python接口原型**：`get_digital_input(id)`
- **接口说明**：读取IO值
- **参数**
  * `id`：io序列号







### Atom 设置

![](..\resources\1-blockly\images\api\set_rgb.png)



**设置颜色**

- **python接口原型**：`set_color(red=0,green=0,blue=0)`
- **接口说明**：设置末端LED灯的颜色
- **参数**:
  - `red`：红色值 0 - 255
  - `green`：绿色值 0 -255
  - `blue`：蓝色值 （0- 255）









## 状态检测

### 设备运行状态

![](..\resources\1-blockly\images\api\system.png)

**上电**

- **python接口原型**：`power_on()`
- **接口说明**：机器上电，可以控制机器



**仅上电**

- **python接口原型**：`power_on_only()`
- **接口说明**：机器上电，机器不可控



**断电**

- **python接口原型**：`power_off()`
- **接口说明**：机器断电



**是否上电**

- **python接口原型**：`is_power_on()`
- **接口说明**：检查机械臂是否已上电

- **返回**：

  - `1`: 开机
  - `0`：关闭电源
  - `-1`: 错误



**释放所有舵机**

- **python接口原型**：`release_all_servos()`

- **接口说明**：设置机械臂为自由运动模式



**机器人打开力矩输出**

- **python接口原型**：`focus_all_servos()`
- **接口说明**：设置机械臂打开力矩输出







**上位机错误安全状态**

- **python接口原型**：`get_robot_status()`

- **接口说明**：获取上位机错误安全状态

- **返回**：

  - 状态信息





**读取关节异常次数**

- **python接口原型**：`get_comm_error_counts(joint_id,type)`
- **接口说明**：获取关节异常次数
- **参数**：
  - `joint_id`：关节id：1-7
  - `type`：异常类型
- **返回**：
  - 异常次数





**设置位置超差值**

- **python接口原型**：`set_pos_over_shoot(value)`

- **接口说明**：设置位置超差值

- **参数**：
  - `value`：超差值



**读取位置超差值**

- **python接口原型**：`get_pos_over_shoot`
- **接口说明**：读取位置超差值
- **返回**：
  - 位置超差值









### 系统与产品信息

![](..\resources\1-blockly\images\api\system_info.png)



**获取主控信息**

- **python接口原型**：`get_system_version()`
- **接口说明**：获取主控版本信息
- **返回**：
  - 返回主控版本信息



**获取末端固件版本**

- **python接口原型**：`get_atom_version()`
- **接口说明**：获取末端固件版本
- **返回**：
  - 返回末端固件版本





**获取机器人型号**

- **python接口原型**：`get_robot_type()`
- **接口说明**：获取机器人型号
- **返回**：
  - 获取机器人型号



**机器超限位回零**

- **python接口原型**：`over_limit_return_zero`
- **接口说明**：机器超限位回零



**获取错误信息**

- **python接口原型**：`get_error_information()`
- **接口说明**：获取错误信息
- **返回**：
  - 获取错误信息



**清除错误信息**

- **python接口原型**：`clear_error_information()`
- **接口说明**：清除错误信息









## 其它设置



### 零空间偏转角

![](..\resources\1-blockly\images\api\zero_space_pos.png)

**获取零空间偏转角数值**

- **python接口原型**：`get_solution_angles()`
- **接口说明**：获取零空间偏转角数值
- **返回值**：
  - `J1_angle_low`：-90  ~ +90
  - `J1_angle_high`：-90  ~ +90



**设置零空间偏转角数值**

- **python接口原型**：`set_solution_angles(J1_angle,speed)`
- **接口说明**：获取零空间偏转角数值
- **参数**：
  - `J1_angle`：-90  ~ +90
  - `speed`：1-100
















---

[← 上一页](./11-pumpUse.md) | [下一页 →](../2-quickmove/2.1-quickmovefirstuse.md)
