# T470s-OpenCore-EFI
联想T470s的OC引导EFI

**无偿分享不提供小白指导，有问题请自行去远景或黑果小兵等大神的博客下面查阅资料。**

**本EFI已经支持引导macOS 11.0 Big Sur，但仍有许多不完美的地方。**

### 机身配置
- CPU：i7 7600U 2.80GHz
- 显卡：HD620 1536MB
- 内存：12GB DDR4 2133MHz（板载4+8）
- 硬盘：西部数据SN750 NVMe SSD 1TB
- 显示器：友达B140QAN0-1.5 1440p 72%NTSC 300nits 
- 无线网卡：已更换为白果拆机卡BCM94360CS2（原来是DW1820A联想版）

### 正常工作的组件/功能：
- CPU变频、睿频
- 亮度和音量快捷键
- 扬声器（layout-id：47）、麦克风
- 前置摄像头
- 模拟白果拔出电源屏幕会略微变暗，也可在系统偏好设置-节能中关闭此功能
- 睡眠和唤醒（开启config中kernel部分的RTC相关patch解决RTC唤醒问题）
- 电源按键和A面呼吸灯，可正常指示唤醒或睡眠状态
- USB端口（充电口旁边的USB3.0只能工作在2.0模式）
- SD卡读卡器
- 触控板手势（从VoodooPS2改为VoodooRMI驱动，更流畅）、三个实体键、小红点
- Wi-Fi和蓝牙
- 显示器HiDPI
- Apple watch解锁（依赖白果拆机网卡实现）
- 电池电量及充电状态的显示，以及系统偏好设置中的节能选项
- 按下PrtSc键会禁用触摸板（VoodooPS2定义的，我认为是个feature而非bug就没有修改它）
- 功能键F7-F12（使用[MSzturc](https://github.com/MSzturc)的[ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant)，配套的SSDT和二进制更名已经添加好）
- USB-C热插拔（感谢[truongtam-fudosan](https://github.com/truongtam-fudosan)在issue中提供的[教程](https://www.elitemacx86.com/threads/guide-how-to-enable-thunderbolt-3-hotplug.462/)）	
	
	> 启用HiDPI：终端执行```bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"```
	> 建议先在Windows下提取显示器EDID并填入config。在脚本中选择分辨率的第2个选项，否则睡眠唤醒后可能出现显示错位、花屏或只有背光。
	> 10.16下请下载脚本到本地并删掉脚本中的“/System”。

### 有问题的组件/功能
- ~~雷电3&USB-C端口，只能作为充电口（输入&输出）~~
- ~~网卡无法连接iPhone热点，更换白果免驱网卡可解决~~
- ~~蓝牙在睡眠唤醒后可能无法连接，手动关闭再打开蓝牙即恢复正常。~~
- ~~触摸板按键（三个按键都被定义为按住显示右键菜单，使用VoodooRMI时则被屏蔽）~~
- 核显HEVC解码和HDMI输出（10.15下可用，11.0不行，也许是beta1更新不完整导致的，本机已回退10.15.6）

### 无法使用的组件/功能
- 指纹识别模块

### 未经测试
- WWAN（4G）模块
- 雷电3热插拔

### 提示
- 一些SSDT文件名与config中添加的文件名有少许不同，可能导致引导OC失败，请自行核对。

### Credits
- [黑果小兵](https://github.com/daliansky) 的ACPI部件补丁仓库（同时向为该仓库作出贡献的大佬们致谢）
- [Acidanthera](https://github.com/acidanthera) 维护的OpenCore引导，Lilu、WhateverGreen、AppleALC等核心驱动
- [MSzturc](https://github.com/MSzturc) 编写的[ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant)和ACPI补丁
