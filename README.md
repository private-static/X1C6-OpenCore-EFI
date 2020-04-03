# T470s-OpenCore-EFI
联想T470s的OC引导EFI

**无偿分享不提供小白指导，有问题请自行去远景或黑果小兵等大神的博客下面查阅资料，乱发issue我会直接关闭。**

### 机身配置
- CPU：i7 7600u 2.9GHz
- 显卡：intel HD620 2048MB
- 内存：12GB DDR4 2133MHz（板载4+8）
- 硬盘：西部数据SN750 NVMe SSD 1TB
- 显示器：友达B140QAN0-1.5 1440p 72%NTSC 300nits 
- 无线网卡：更换为BCM94352z（淘宝搜00JT494）

### 正常工作的组件：
- CPU变频、睿频
- 亮度和音量快捷键
- 拔出电源屏幕会略微变暗，不喜欢此功能可以在config中禁用SSDT-ALS0
- 睡眠和唤醒（目前偶发RTC XDCI唤醒，正在尝试解决）
- 电源按键和A面呼吸灯
- USB端口（充电口旁边的USB3.0只能工作在2.0模式）
- SD读卡器
- 触控板（长按可模拟Force Touch）
- 小红点
- Wi-Fi和蓝牙
- 核显HDMI输出
- 显示器HiDPI（注意选择1424x802分辨率以防止睡眠唤醒后显示错位）
	
	> 启用HiDPI：终端执行```bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"```

### 有问题的组件
- 雷电3&USB-C端口，只能作为充电口（输入&输出）
- 触摸板按键（三个按键都被定义为按住显示右键菜单）

### 无法使用的组件
- 指纹识别模块

>  Tips：蓝牙在睡眠唤醒后可能无法连接，手动关闭再打开蓝牙即恢复正常。

>  引导Windows10 insider版会直接绿屏，需要在开机时按F12手动选择Windows Boot Manager来启动，正式版未测试。