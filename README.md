# X1C6-OpenCore-EFI

[![OpenCore](https://img.shields.io/badge/OpenCore-0.6.4-blue)](https://github.com/acidanthera/OpenCorePkg)[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)

Thinkpad X1 Carbon 2018的OC引导EFI（需要T470s版本请自行checkout）

**无偿分享不提供小白指导，有问题请自行去远景或黑果小兵等大神的博客下面查阅资料。**

**本EFI已经支持引导macOS 11.0 Big Sur。**

### 机身配置
- CPU：i7 8550U 2.0GHz
- 显卡：UHD620 1536MB
- 内存：16GB LPDDR3 2133MHz
- 硬盘：西部数据SN750 NVMe SSD 1TB
- 显示器：友达B140HAN02.0 1440p 500nits 
- 无线网卡：intel AX200

### 正常工作的组件/功能：
- 核心硬件
  - CPU变频、睿频
  - intel核显，HEVC编解码
  - 有线网卡
  - 无线网卡（Wi-Fi、蓝牙）
  - 显示器（可开启HiDPI）
- 多媒体设备
  - 扬声器、麦克风、耳机接口
  - 前置摄像头
  - HDMI输出（1080p 60fps）
  - Type-C视频输出（应该是走DP通道，可以到4k 60fps）
- 输入输出设备
  - 触摸板（含实体三键）、小红点
  - USB3.0、USB3.1（Type-C）、microSD读卡器
- 重要功能
  - 亮度和音量快捷键
  - 睡眠和唤醒
  - 电量显示、节能五项
  - 触摸板多指手势（使用VoodooRMI驱动，更流畅）
  - 电源按键和A面呼吸灯，可正常指示唤醒或睡眠状态
  - Apple watch解锁（依赖白果拆机网卡实现）
  - F4、F7、F8、F9、F10、F11、F12键对应功能（使用[zhen-zen](https://github.com/zhen-zen)编写的[YogaSMC](https://github.com/zhen-zen/YogaSMC)，无需额外的SSDT和ACPI更名）

### 有问题的组件/功能

- ~~雷电3&USB-C端口，只能作为充电口（输入&输出）~~
- ~~网卡无法连接iPhone热点，更换白果免驱网卡可解决~~
- ~~蓝牙在睡眠唤醒后可能无法连接，手动关闭再打开蓝牙即恢复正常。（使用DW1820A时出现）~~
- 使用intel网卡时，Wi-Fi只支持802.11n速率，隔空投送、接力、Apple Watch解锁不可用

### 无法使用的组件/功能
- 指纹识别模块

### 未经测试

- WWAN（4G）模块（低配机型没有天线）
- 雷电3热插拔

### 提示
- 一些SSDT文件名与config中添加的文件名有少许不同，可能导致引导OC失败，请自行核对
- 启用HiDPI：终端执行```bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"```
- ~~在macOS Big Sur上，HiDPI脚本需要删掉```/System```才能正常生效~~

### Credits
- [黑果小兵](https://github.com/daliansky) 的ACPI部件补丁仓库（同时向为该仓库作出贡献的大佬们致谢）
- [Acidanthera](https://github.com/acidanthera) 维护的OpenCore引导，Lilu、WhateverGreen、AppleALC等核心驱动
- [MSzturc](https://github.com/MSzturc) 编写的[ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant)和ACPI补丁
- [zhen-zen](https://github.com/zhen-zen)编写的[YogaSMC](https://github.com/zhen-zen/YogaSMC)和SSDT sample
- [tylernguyen](https://github.com/tylernguyen)维护的[x1c6-hackintosh](https://github.com/tylernguyen/x1c6-hackintosh)项目
