# NUC8I5BEH EFI for Catalina

## [English](./README_EN.md)

## 硬件配置

| 硬件          | 型号                  | 备注                                 |
| ------------- | --------------------- | ------------------------------------ |
| 主机型号      | NUC8I5BEH             |                                      |
| BIOS 版本     | 75                    |                                      |
| 网卡          | 原生 Intel            |                                      |
| 蓝牙          | 原生 Intel            |                                      |
| 内存          | 协德 DDR4 2666 16G x2 | 虽然内存是 2666 德，但只支持 2400    |
| 硬盘          | 三星 970 Evo 500G     |                                      |
| 显示器 HDMI   | HKC T7000 2K          | 老显示器，接 HDMI 口                 |
| 显示器 USBC-C | 15.6 便携显示器       | 供电和信号都使用 USB-C（简称一线通） |
| 键盘          | Filco Minila air 67   | BT3.0                                |
| 鼠标          | 罗技 Logitech M720    | BT4.0 + USB                          |

## BIOS 设置

~~1. 禁用内置的蓝牙/WIFI~~  
2. 禁用 Secure Boot  
3. 禁用 Legacy Boot  
4. 禁用 LAN / WIFI Boot  

## OpenCore Version

0.5.9

## 支持特性

1. 兼容至 10.15.6
2. 支持 WIFI 和 蓝牙 (Intel 原生)
3. 支持 USBC + HDMI 双显示器 (可以随意切换，插拔)
4. 支持 DP HDMI 声音输出
5. USB 正常
6. 声卡驱动正常
7. CPU 变频支持
8. 休眠唤醒正常
9. 根据 [非常感谢，已使用，问题反馈](https://github.com/altjz/NUC8I5BEH-EFI/issues/3)用户反馈，雷电3支持热插拔

## 已知问题

1. 读卡器

   基本不用读卡器，所以也没有刻意去修复，试了 Switch 的 TF 卡，的确用不了

   可以使用以下指令，关闭任务栏上的读卡器图标

   ```shell
    fn=".`date +%s`" && sudo mv /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu$fn && sudo touch /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu
    ```

2. HandOff Airdrop， Intel 网卡走的其实是以太网的，所以不支持

3. 网络速度监控，由于走以太网之后，下行的网络速度无法监控，解决方案是，增加一个桥接接口，可以参照这里 [网速监控下载速度一直是0](https://github.com/OpenIntelWireless/itlwm/issues/172)

4. 网速问题，目前只支持 20Mhz，请参照 [performance-sucks](https://openintelwireless.github.io/itlwm/FAQ.html#performance-sucks)

5. 蓝牙 4.0 不支持 （我测试了 罗技 Master 2s 用蓝牙无法连接，但是键盘蓝牙 3.0 和 音箱 2.0可以连接）

## 补充说明

- Wifi/蓝牙：使用的是[itlwm](https://github.com/OpenIntelWireless/itlwm)，是走以太网协议，Wifi 客户端请下载 [HeliPort](https://github.com/OpenIntelWireless/HeliPort)，可以支持界面选择无线网络，（记得在 BIOS 把蓝牙 和 WIFI 打开）
- 序列号：请自行更改序列号，可以直接使用 Clover Configurator 生成
- 其他型号支持：NUC8I7 除了 CPU 以外，其他都一样，所以应该也是能用的
- 电源可以使用 PD 转 DC，但是我的小米 65W PD TYPE-C 单口充电器，进入系统的时候会关机，没试过联想的口红充电器

## 更新

### 2020-09-14

    1. 修复蓝牙无法关闭

### 2020-08-15

    1. 使用 OC 引导
    2. 使用 原生 wifi 和 蓝牙
    3. 硬盘移除 SATA ，使用 970 Evo

### 2019-12-28

    1. 解决了开机有几率无法开机的情况，并兼容了 Catalina 10.15

### 2019-12-24

    1. 解决休眠秒醒，并且蓝牙不可用的问题（解决方案是：使用 hackintool 禁用板载蓝牙的USB口 HS10 ）

### 2019-12-25

    1. 开机有几率卡住的问题，越来越频繁，也找不到原因修复，我重新用别的 EFI 修改，现在完美解决

## 参考链接

1. [NUC8（豆子峡谷）黑苹果新手指南Q&A](https://www.jianshu.com/p/b298da6afef3)
2. [NUC8BEX 黑苹果维护教程](https://www.jianshu.com/p/2b8516276147)
3. [Open Intel Wifi](https://github.com/OpenIntelWireless/itlwm)
4. [Intel Bluetooth Firmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
5. [csrutil/NUC8I5BEH](https://github.com/csrutil/NUC8I5BEH)
