# 吸泵的使用

*开始之前*

> *1、确保机器已上电*
>
> *2、确保机器连接正常*

本章介绍如何使用 `blockly` 控制连接到 `Mercury A1` 机械臂的吸泵（如下图）

<img src="..\resources\1-blockly\images\pump\pump.png"  />

#### API display

<img src="..\resources\1-blockly\images\pump\code.png" style="zoom: 64%;" />

<img src="..\resources\1-blockly\images\pump\function.png" style="zoom: 67%;" />

主要用到以下积木块

- **1**: `设置IO值`：设置机械臂末端IO输出状态

  * 参数介绍：
    该模块有两个可以调整的参数：
    *  IO 引脚：1-2
    *  IO输出状态：0-低电平，1-高电平

- **2**: `方法`积木块：将一组积木块模块化

  * 参数介绍：
    该模块有一个可以调整的参数：
    *  方法名：给该方法命名



#### 小案例

1、首先需要创建两个`方法`积木块，并分别命名为`pump_on`和`pump_off`，同时在这两个`方法`积木块中拖入`设置IO值`和`睡眠`积木块

​	`pump_on`方法：用于打开吸泵

​	`pump_off`方法：用于关闭吸泵



2、同时可以发现，在方法分类中出现了两个可以使用的`pump_on`和`pump_off`积木块

<img src="..\resources\1-blockly\images\pump\create_function.png" style="zoom: 67%;" />









添加使用`pump_on`和`pump_off`积木块代码。完整代码如下：

<img src="..\resources\1-blockly\images\pump\full_code.png" style="zoom: 67%;" />




---

[← 上一页](./10-gripperUse.md) | [下一页 →](./12-dragTeach.md)
