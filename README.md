# T470s-OpenCore-EFI
联想T470s的OC引导EFI

**无偿分享不提供小白指导，有问题请自行去远景或黑果小兵等大神的博客下面查阅资料，乱发issue我会直接关闭。**

### 机身配置
- CPU：i7 7600u 2.80GHz
- 显卡：HD620 2048MB
- 内存：12GB DDR4 2133MHz（板载4+8）
- 硬盘：西部数据SN750 NVMe SSD 1TB
- 显示器：友达B140QAN0-1.5 1440p 72%NTSC 300nits 
- 无线网卡：更换为BCM94352z（淘宝搜00JT494，也可更换BCM960CS2等免驱的白果拆机卡）

### 正常工作的组件：
- CPU变频、睿频
- 亮度和音量快捷键
-  扬声器、麦克风
-  前置摄像头
- 模拟白果拔出电源屏幕会略微变暗，也可在系统偏好设置-节能中关闭此功能
- 睡眠和唤醒（开启config中kernel部分的RTC相关patch解决RTC唤醒问题）
- 电源按键和A面呼吸灯，可正常指示唤醒或睡眠状态
- USB端口（充电口旁边的USB3.0只能工作在2.0模式）
- SD读卡器
- 触控板，可模拟白果多点触控手势
- 小红点
- Wi-Fi和蓝牙
- HDMI 4K输出
- 显示器HiDPI
- 电池电量及充电状态的显示，以及系统偏好设置中的节能选项
- 按下PrtSc键会禁用触摸板（VoodooPS2驱动定义的，我认为是个feature而非bug就没有修改它）
	
	> 启用HiDPI：终端执行```bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"```
	> 在脚本中选择与本机对应的分辨率，重启后缩放分辨率选择1440x810（或1424x802，对应1080p机型）。请勿选择更高的缩放分辨率，否则睡眠唤醒后出现显示错位或花屏。

### 有问题的组件
- 雷电3&USB-C端口，只能作为充电口（输入&输出）
- 触摸板按键（三个按键都被定义为按住显示右键菜单）
-  网卡无法连接iPhone热点，更换白果免驱网卡可解决

### 无法使用的组件
- 指纹识别模块（这个百分百无解的）
-  除音量、亮度之外的功能键（可自行用karabiner设置白果快捷键，或参考OC-little中按键映射相关内容修改映射）

>  Tips：蓝牙在睡眠唤醒后可能无法连接，手动关闭再打开蓝牙即恢复正常。

>  引导Windows10 20H2 insider版会直接绿屏，需要在开机时按F12手动选择Windows Boot Manager来启动，正式版未测试。

### Credits
- [黑果小兵](https://github.com/daliansky) 的ACPI部件补丁仓库（同时向为该仓库作出贡献的大佬们致谢）
- [Acidanthera](https://github.com/acidanthera) 维护的OpenCore引导，Lilu、WhateverGreen、AppleALC等核心驱动