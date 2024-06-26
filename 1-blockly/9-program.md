# 程序控制

*开始之前*

> *1、确保机器已上电*
>
> *2、确保机器连接正常*

本章介绍如何通过`运行面板`来调试积木块代码，实现程序的 暂停、单步执行、停止。

编辑一段控制 机械臂末端 LED 灯颜色变化的程序

<img src="..\resources\1-blockly\images\program\block.png"  />

<img src="..\resources\1-blockly\images\program\code.png"  />



点击`运行`按钮，当运行面板弹出后，马上点击 `暂停`按钮，程序会在执行完第一条指令`time.sleep(5)` 后暂停

<img src="..\resources\1-blockly\images\program\run.png"  />

程序已暂停。出现下一条要执行的指令`mc.set_color(255,0,0)

此时：

- 如果点击`恢复`按钮，程序将会自动往下执行；

- 如果点击`单步执行`按钮，程序会执行下一条指令，即`mc.set_color(255,0,0)`；
- 如果点击`停止`按钮，程序会被终止；



至于接下来如何操作，由您自己决定吧！


---

[← 上一页](./8-singleStep.md) | [下一页 →](./10-gripperUse.md)
