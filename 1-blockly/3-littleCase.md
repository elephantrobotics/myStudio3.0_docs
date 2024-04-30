# 小案例

*开始之前*

> *1、确保机器已上电*
>
> *2、确保机器连接正常*

我们来写一个小案例，通过这个案例来介绍`blockly` 的基础使用。

**案例描述**：控制机械臂回零，然后控制一关节移动到 20 度的位置，然后再回到零点。



**第一步：**首先点击 `姿态` 按钮，打开姿态视图，在这里可以看到 机械臂的角度和坐标信息。



<img src="..\resources\1-blockly\images\littleCase\1.png" style="zoom:80%;" />

<img src="..\resources\1-blockly\images\littleCase\zitai.png" style="zoom:80%;" />



- 1：收起姿态面板：鼠标单击姿态视图面板的`>>`按钮可以收起面板。
- 2：机器人角度和坐标数据。





**第二步：**开始编程

打开工具箱一级分类 `运动控制`，选择二级分类`角度 & 坐标`，拖动`设置全角度`积木块到工作区。

此积木块用于控制机械臂各关节运动到给定的角度，运动速度默认为 20。

由于`Mercury A1`除了`J6` 零点角度为 `90`外，其它关节 零点角度值都为 `0`，因此需要将积木块的 `J6` 修改为 90。



<img src="..\resources\1-blockly\images\littleCase\3.png" style="zoom: 67%;" />

<img src="..\resources\1-blockly\images\littleCase\send_coords.png" style="zoom: 67%;" />





打开工具箱一级分类`基础编程`，选择二级分类 `时间`，拖动`睡眠`积木块到工作区，并设置睡眠时间为 3 秒。

睡眠时间 3 秒的意思是：程序等待 3 秒钟后再往下执行。为什么要等待 3 秒钟呢？因为需要确保机械臂先把第一个指令动作先完成后再执行后续其它动作。

<img src="..\resources\1-blockly\images\littleCase\5.png" style="zoom: 67%;" />

<img src="..\resources\1-blockly\images\littleCase\6.png" style="zoom: 67%;" />





复制`设置全角度`积木块并修改 `J1` 角度为 20：
- 鼠标点击选中工作区中`设置全角度`积木块；
- 按住键盘 Ctrl + C 复制`设置全角度`积木块；
- 按住键盘 Ctrl + V 粘贴`设置全角度`积木块
- 将新积木块 `J1` 修改为 20；
- 拖动该积木块使其与`睡眠`积木块连接；

<img src="..\resources\1-blockly\images\littleCase\7.png" style="zoom: 67%;" />



同上操作类似，复制`睡眠`积木块，并设置睡眠时间为 `3` 秒；

再次复制工作区第一个`设置全角度`积木块；



完整代码如下：

<img src="..\resources\1-blockly\images\littleCase\code.png" style="zoom: 67%;" />

> 这段代码的意思是：
>
> - 控制机械臂回到零点
>
> - 等待 3 秒钟（等待机器会零点完成）
>
> - 使 一关节（J1） 移动到 20 度的位置
>
> - 等待 3 秒钟
>
> - 控制机械臂回到零点





最后，点击`运行面板`按钮，打开面板后，点击`运行`按钮开始执行代码。

<img src="..\resources\1-blockly\images\littleCase\run.png" style="zoom: 67%;" />



代码运行完成，点击面板`X` 可关闭面板

<img src="..\resources\1-blockly\images\littleCase\run_finish.png" style="zoom: 67%;" />







**第三步：**保存 和 加载 文件（或者说保存加载工作区）



`blockly` 支持 工作区的保存和加载。



点击`文件`按钮，出现一个下拉菜单，点击其中的`保存`按钮，在`er`目录下保存当前工作区代码为`blocks.json`

<img src="..\resources\1-blockly\images\littleCase\save.png" style="zoom: 67%;" />





**第四步：** 新建工作区 操作（这个操作会清空工作区所有代码）

点击`文件`按钮，出现一个下拉菜单，点击其中的`新建工作区`按钮，会出现提示，点击`确认`按钮

<img src="..\resources\1-blockly\images\littleCase\clear_tips.png" style="zoom: 67%;" />



新建工作区完成

<img src="..\resources\1-blockly\images\littleCase\new.png" style="zoom: 67%;" />







**第五步：**加载工作区 操作，加载我们之前保存的工作区文件

点击`文件`按钮，出现一个下拉菜单，点击菜单中 `打开文件` 按钮后，在`er`目录下找到刚才我们保存的 `blocks.json`文件

<img src="..\resources\1-blockly\images\littleCase\load.png" style="zoom: 67%;" />



加载完成

<img src="..\resources\1-blockly\images\littleCase\load_finish.png" style="zoom: 67%;" />

---

[← 上一页](./2-interfaceDescription.md) | [下一页 →](./4-autofill.md)


