# 积木块详解



## 系统信息

![](..\resources\1-blockly\images\api\system\1.png)



**获取末端固件版本**

- **原型**：`get_atom_version()`

- **接口说明**：获取末端固件版本

- **返回**：返回末端固件版本



**获取主控信息**

- **原型**：`get_system_version()`

- **接口说明**：获取主控版本信息

- **返回**：返回主控版本信息









## 底座

![](..\resources\1-blockly\images\api\basic\1.png)



**设置底座引脚输出**

- **原型**：`set_basic_output(id,state)`
- **接口说明**：设置底座引脚输出
- **参数**：

    - `id`：引脚号
    - `state`：选择输出状态



**获取底座引脚输入**

- **原型**：`set_basic_output(id)`
- **接口说明**：获取底座引脚输入
- **参数**：
    - `id`：引脚号
- **返回**：
    - 引脚输入状态







## Atom 末端IO

![](..\resources\1-blockly\images\api\atom\1.png)

**设置颜色**

- **原型**：`set_color(red=0,green=0,blue=0)`
- **接口说明**：设置末端LED灯的颜色
- **参数**

* `red`：红色值 0 - 255
    * `green`：绿色值 0 -255
* `blue`：蓝色值 （0- 255）



**设置 PWM 输出**

- **原型**：`set_pwm_output(v1=0,v2=0,v3=0)`
- **接口说明**：设置PWM输出
- **参数**
    * **v1** (_int_)

    * **v2** (_int_)

    * **v3** (_int_)



**设置结束引脚模式**

- **原型**：`set_pin_mode(id,state)`
- **接口说明**：设置尾针模式
- **参数**
    * `id`：引脚号
    * `state`：选择模式



**设置IO值**

- **原型**：`set_digital_output(id,state)`
- **接口说明**：设置IO值
- **参数**
    * `id`：io序列号

    * `state`：选择状态0或1



**读取IO值**

- **原型**：`get_digital_input(id)`
- **接口说明**：读取IO值
- **参数**
    * `id`：io序列号







## 状态

![](..\resources\1-blockly\images\api\status\1.png)



**上电**

- **原型**：`power_on()`
- **接口说明**：Atom开启通信（默认开启）



**断电**

- **原型**：`power_off()`
- **接口说明**：Atom 关闭通信



**上位机错误安全状态**

- **原型**：`get_robot_status()`

- **接口说明**：获取上位机错误安全状态

- **返回**：

  - 状态信息



**是否上电**

- **原型**：`is_power_on()`
- **接口说明**：检查机械臂是否已上电

- **返回**：

    - `1`: 开机
    - `0`：关闭电源
    - `-1`: 错误



**末端led按钮是否按下**

- **原型**：`is_power_on()`
- **接口说明**：检查末端led按钮是否按下

- **返回**：
  - `1`: 按下
  - `0`：未被按下



**释放所有舵机**

- **原型**：`release_all_servos()`

- **接口说明**：设置机械臂为自由运动模式



**机器人打开力矩输出**

- **原型**：`focus_all_servos()`
- **接口说明**：设置机械臂为自由运动模式



**关节异常恢复，重置所有伺服电机**

- **原型**：`servo_restore(254)`
- **接口说明**：关节异常恢复，重置所有伺服电机




**关节异常恢复**

- **原型**：`servo_restore(id)`
- **接口说明**：关节异常恢复
- **参数**
  * `id`：关节id（1 - 7）



**检查 Atom 是否已连接**

- **原型**：`is_controller_connected()`
- **接口说明**：检查Atom是否连接
- **返回**：
    - `0`：未连接
    - `1`：已连接











## 角度和坐标

![](..\resources\1-blockly\images\api\mid\1.png)

![](..\resources\1-blockly\images\api\mid\2.png)

**获取所有角度**

- **原型**：`get_angles()`
- **接口说明**：获取所有关节的度数
- **返回**：

    - 关节角度值



**获取所有坐标**

- **原型**：`get_coords()`

- **接口说明**：

  - 获取笛卡尔坐标



**设置单关节角度**

- **原型**：`send_angle(id, degree, speed)`

- **接口说明**：机器人单关节角度控制

- **参数**

   - `id`：关节 ID：1-7

   - `degree`：角度值

   - `speed`：速度



**设置单个坐标**

- **原型**：`send_coord(id, value, speed)`
- **接口说明**：机器人单坐标控制

- **参数**
   - `id`：坐标：1-6分别对应x、y、z、rx、ry、rz
   - `value`：坐标值
   - `speed`：速度



**角度是否到达位置**

- **原型**：`is_in_position([j1,j2,j3,j4,j5,j6,j7],0)`

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

- **原型**：`is_in_position([x,y,z,rx,ry,rz],1)`

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





**检测是否在运动**

- **原型**：`is_moving(id, value, speed)`
- **接口说明**：检测机器是否在移动。
- **返回**：
   - 0：机器不运转
   - 1：机器正在运转



**设置全角度**

- **原型**：`send_angles(angles,speed)`
- **接口说明**：将所有角度发送至机械臂。

- **参数**
   - `angles`：坐标值列表（`List[float]`）
   - `速度`: (`int`) 0 ~ 100



**设置坐标**

- **原型**：`send_coords(coords,speed,mode)`

- **接口说明**：将所有坐标发送至机械臂。

- **参数**
- `coords`：坐标值列表（`List[float]`）
   - `speed`: (`int`) 0 ~ 100







## 点动控制

![](..\resources\1-blockly\images\api\jog\1.png)





**点动控制关节**

- **原型**：`jog_angle（joint_id,direction,speed）`

- **接口说明**：点动控制角度

- **参数**

   - `joint_id`: (`int`) 1 ~ 7

   - `direction`: `0` - 减少，`1` - 增加

   - `speed`: 0 ~ 100




**关节绝对控制**

   - **原型**：`jog_absolue（coord_id,direction,speed）`

   - **接口说明**：步进模式

   - **参数**

     - `coord_id`: (`int`) 1 ~ 6
     - `direction`：
     - `speed`: 0 ~ 100



**点动控制坐标**

- **原型**：`jog_coord（coord_id,direction,speed）`
- **接口说明**：点动控制坐标

- **参数**
- `coord_id`: (`int`) 1 ~ 6
   - `direction`: `0` - 减少，`1` - 增加
   - `speed`: 0 ~ 100





**步进模式**

- **原型**：`jog_increment（coord_id,direction,speed）`

- **接口说明**：步进模式

- **参数**

   - `coord_id`: (`int`) 1 ~ 6
   - `方向`：
   - `速度`: 0 ~ 100



**设置伺服编码器值**

- **原型**：`set_encoder（joint_id,encoder）`

- **接口说明**：将单个关节旋转设置为指定的电位值。

- **参数**

  - `joint_id`: (`int`) 1 ~ 7

  - `encoder`: 0 ~ 4096



**获取伺服编码器值**

- **原型**：`get_encoder(joint_id)`
- **接口说明**：获取指定的关节电位值。
- **参数**: `joint_id`: (`int`) 1 ~ 6
- **返回**：
  - `编码器`：0 ~ 4096





**暂停**

- **原型**：`pause()`
- **接口说明**：暂停移动



 **恢复**

- **原型**：`resume()`
- **接口说明**：恢复动作



**停止**

- **原型**：`jog_stop()`
- **接口说明**：停止点动





## CCADA

![](..\resources\1-blockly\images\api\ccada\1.png)





**获取零空间偏转角数值**

- **原型**：`get_solution_angles()`
- **接口说明**：获取零空间偏转角数值
- **返回值**：
  - `J1_angle_low`：-90  ~ +90
  - `J1_angle_high`：-90  ~ +90



**设置零空间偏转角数值**

- **原型**：`set_solution_angles(J1_angle,speed)`
- **接口说明**：获取零空间偏转角数值
- **参数**：
  - `J1_angle`：-90  ~ +90
  - `speed`：1-100







## 设置

![](..\resources\1-blockly\images\api\setting\1.png)



**获取关节最小角度**

- **原型**：`get_joint_min_angle(joint_id)`
- **接口说明**：获取指定关节的最小运动角度
- **参数**：`joint_id`：(`int`)
- **返回**：角度值（`float`）



**获取关节最大角度**

- **原型**：`get_joint_max_angle(joint_id)`

- **接口说明**：获取指定关节的最大运动角度

- **参数**：`joint_id`：(`int`)

- **返回**：角度值（`float`）



**设置关节最小值角度**

- **原型**：`set_joint_min(id, angle)`
- **接口说明**：设置指定关节的最小角度。

- **参数**：
   - `关节id`

   - `角度`



**设置关节最大角度**

- **原型**：`set_joint_max(id, angle)`
- **接口说明**：设置指定关节的最大角度。

- **参数**：
   - `关节id`
   - `角度`





## 伺服电机

![](..\resources\1-blockly\images\api\servos\1.png)



**伺服电机是否开启**

- **原型**：`is_servo_enable(servo_id)`

- **接口说明**：判断所有舵机是否连接

- **参数**：`servo_id` (`int`) 1 ~ 7

- **返回**：
- `0`：禁用
   - `1`: 启用

   - `-1`: 错误



**是否所有伺服电机已开启**

- **原型**：`is_all_servo_enable()`

- **接口说明**：判断是否连接指定舵机

- **返回**：

   - `0`：禁用
   - `1`: 启用
   - `-1`: 错误



**设置伺服电机配置参数**

- **原型**：`set_servo_data(servo_no, data_id, value)`
- **接口说明**：设置舵机指定地址的数据参数。

- **参数**：
   - `servo_no`：铰接式舵机的序列号，1 - 7。
   - `data_id`：数据地址。
   - `value`：0 - 4096



**获取伺服电机配置参数**

- **原型**：`get_servo_data(servo_no, data_id)`
- **接口说明**：读取舵机指定地址的数据参数。
- **参数**：

   - `servo_no`：铰接式舵机的序列号，1 - 7。
   - `data_id`：数据地址。
- **返回**：
- `值`：0 - 4096



###

**设置伺服电机零点**

- **原型**：`set_servo_calibration(servo_no)`
- **接口说明**：校准关节执行器当前位置为角度零点，对应电位值为2048。

- **参数**：
   - `servo_no`：铰接式舵机的序列号，1 - 7。



**刹车单个伺服电机**

- **原型**：`joint_brake(servo_id)`
- **接口说明**：指定舵机上电
- **参数**：`servo_id`：1 ~ 7





**释放单个伺服电机**

- **原型**：`release_servo(servo_id)`
- **接口说明**：指定舵机断电
- **参数**：`servo_id`：1 ~ 7



**固定伺服电机**

- **原型**：`focus_servo(servo_id)`
- **接口说明**：指定舵机上电
- **参数**：`servo_id`：1 ~ 7





## 夹具

![](..\resources\1-blockly\images\api\gripper\1.png)



**设置 Pro 自适应夹爪**

- **原型**：`set_gripper_enabled(flag)`
- **接口说明**：设置 Pro 自适应夹爪
- **参数**：`flag`：1  |  0





**夹爪零位校准**

- **原型**：`set_gripper_calibration()`
- **接口说明**：将当前位置设置为零，设置当前位置值为`2048`。





**设置夹爪状态**

- **原型**：`set_gripper_state(flag, speed, mode)`

- **接口说明**：设置夹爪开关状态

- **参数**

   - `flag` (`int`)：0 - 打开，1 - 关闭
   - `速度` (`int`): 0 ~ 100
   - `模式`：夹具



**设置夹爪值**

- **原型**：`set_gripper_value(值，速度，模式)`

- **接口说明**：设置夹爪值

- **参数**

   - `值`（整数）：0 ~ 100
   - `速度`（整数）：0 ~ 100
   - `模式`：夹具



**获取夹爪值**

- **原型**：`get_gripper_value(mode)`
- **接口说明**：获取夹具值
- **返回**：夹具值（int）





**夹爪是否在运动**

- **原型**：`is_gripper_moving()`

- **接口说明**：判断夹具是否在移动

- **返回**：

   - `0`：不移动
   - `1`：正在移动
   - `-1`: 错误数据





**设置夹爪模式**

- **原型**：`set_gripper_mode(status)`
- **接口说明**：设置夹爪模式。
- **参数**
- `status` (`int`): 0 - 透明传输。 1 - 端口模式。





**获取夹爪模式**

- **原型**：`get_gripper_mode()`

- **接口说明**：获取抓手模式。

- **返回**
- `status` (`int`): 0 - 透明传输。 1 - 端口模式。





## 坐标控制

![](..\resources\1-blockly\images\api\coords\1.png)



**获取工具坐标系**

- **原型**：`get_tool_reference()`
- **接口说明**：获取工具坐标系。
- **返回**：`列表` [x，y，z，rx，ry，rz]





**设置工具坐标系**

- **原型**：`set_tool_reference(coords)`

- **接口说明**：设置工具坐标系。

- **参数**：
   - `coords`: (`list`) [x, y, z, rx, ry, rz]。



**获取世界坐标系**

- **原型**：`get_world_reference()`
- **接口说明**：获取世界坐标系。
- **返回**：`列表` [x，y，z，rx，ry，rz]。





**设置世界坐标系**

- **原型**：`set_world_reference(coords)`

- **接口说明**：设置世界坐标系。

- **参数**：
   - `coords`: (`list`) [x, y, z, rx, ry, rz]。



**获取基坐标系**

- **原型**：`get_reference_frame()`
- **接口说明**：获取基础坐标系。
- **返回**：
  - 0 - 基础
  - 1 - 工具。



**设置基坐标系**

- **原型**：`set_reference_frame(rftype)`

- **接口说明**：设置基础坐标系。

- **参数**：
   - `rftype`：0 - 基础 1 - 工具。



**获取移动类型**

- **原型**：`get_movement_type()`
- **接口说明**：获取运动类型。
- **返回**：1 - movel，0 - moveJ。



**设置移动类型**

- **原型**：`set_movement_type(move_type)`

- **接口说明**：设置运动类型。

- **参数**：
   - `move_type`：1 - movel，0 - moveJ。



**获取末端坐标系**

- **原型**：`get_end_type()`
- **接口说明**：获取末端坐标系。
- **返回**：0 - 法兰，1 - 工具。



**设置末端坐标系**

- **原型**：`set_end_type(end)`

- **接口说明**：设置结束坐标系。

- **参数**：
   - `end`：0 - 法兰，1 - 工具。







## 伺服电机状态

![](..\resources\1-blockly\images\api\servos_status\1.png)





**获取关节速度**

- **原型**：`get_servo_speeds()`

- **接口说明**：获取关节速度



**获取各关节的状态**

- **原型**：`get_servo_status()`

- **接口说明**：获取各关节的状态




**获取关节电流**

- **原型**：`get_servo_currents()`
- **接口说明**：获取关节电流





## 485

![](..\resources\1-blockly\images\api\485\1.png)





**485恢复出厂设置**

- **原型**：`tool_serial_restore()`

- **接口说明**：485恢复出厂设置





**设置485通信**

- **原型**：`tool_serial_ready()`
- **接口说明**：设置485通信
- **返回**：
  - 0：未设置
  - 1：设置成功





**读取485缓冲区长度**

- **原型**：`tool_serial_available()`
- **接口说明**：读取485缓冲区长度
- **返回**：
  - data





**读取固定长度的数据**

- **原型**：`tool_serial_read_data(id)`
- **接口说明**：读取485缓冲区长度
- **参数**：
  - `id`:1-45
- **返回**：
  - data





**发送数据**

- **原型**：`tool_serial_write_data(data)`
- **接口说明**：发送数据
- **参数：**
  - data
- **返回**：
  - 数据长度





**清空缓冲区**

- **原型**：`tool_serial_peek()`

- **接口说明**：清空缓冲区







**查看缓冲区的第一个数据**

- **原型**：`get_servo_speeds()`
- **接口说明**：查看缓冲区的第一个数据
- **返回**：数据







**设置485波特率**

- **原型**：`tool_serial_set_baud(baud)`
- **接口说明**：设置485波特率
- **参数**：
  - `baud`：波特率





**设置485超时**

- **原型**：`tool_serial_set_timeout(timeout)`
- **接口说明**：设置485超时
- **参数**：
  - `timeout`：超时时间




---

[← Previous Page](./11-pumpUse.md) | [Next Page →](./13-Q%26A.md)