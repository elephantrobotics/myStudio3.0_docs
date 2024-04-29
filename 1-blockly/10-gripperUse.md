# 夹爪的使用

*开始之前*

> *1、确保机器已上电*
>
> *2、确保机器连接正常*



本章介绍如何使用 `blockly` 控制连接到 `Mercury A1` 机械臂的自适应夹爪（如下图）

<img src="..\resources\1-blockly\images\gripperUse\gripper.png"  />


#### API display

<img src="..\resources\1-blockly\images\gripperUse\blocks.png" style="zoom: 67%;" />

我们将用到以下积木块

**1**: `设置夹爪状态`：使夹爪以指定的速度进入指定的状态（张开或闭合）

  参数介绍：

  该模块有两个可以调整的参数：

  * 夹爪状态参数：闭合状态，打开状态
  * 速度参数：表示旋转的速度，取值范围0~100
  * 夹具类型参数：此处选择自适应夹爪



 **2**: `设置夹爪值`：使夹具以指定的速度到达指定的位置

  参数介绍：

  该模块有两个可以调整的参数：

  * 夹爪值参数：表示夹爪要到达的位置，取值范围为 0~100。
  * 速度参数：表示旋转的速度，取值范围0~100。
  * 夹具类型参数：此处选择自适应夹爪








#### 小案例

图形代码如下：

<img src="..\resources\1-blockly\images\gripperUse\code.png" style="zoom: 80%;" />



* 代码的执行效果：

  - 控制自适应夹爪以 20 的速度打开
- 等待 5 秒
  - 控制自适应夹爪以 20 的速度 到达 值 为 80 的位置
- 等待 5 秒
  - 控制自适应夹爪以 20 的速度 到达 值 为 20 的位置
- 等待 5 秒
  - 关闭夹爪



**注意**:

如果您无法从上面的示例中控制夹爪，也许您需要将夹爪模式设置为 透传模式

<img src="..\resources\1-blockly\images\gripperUse\3.png"  />

设置完后，然后再次运行小案例代码。








---

[← Previous page](./9-program.md) | [Next page →](./11-pumpUse.md)
